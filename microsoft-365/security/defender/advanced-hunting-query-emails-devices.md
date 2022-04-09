---
title: Jagt efter trusler på tværs af enheder, mails, apps og identiteter med avanceret jagt
description: Undersøg almindelige jagtscenarier og eksempelforespørgsler, der dækker enheder, mails, apps og identiteter.
keywords: avanceret jagt, Office365-data, Windows enheder, Office365-mails normaliseres, mails, apps, identiteter, trusselsjagt, jagt på cybertrusler, søgning, forespørgsel, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 099ba7abe53be6269c1d01c0d39d9e5cfbe3557d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731686"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Jagt efter trusler på tværs af enheder, mails, apps og identiteter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

[Avanceret jagt](advanced-hunting-overview.md) i Microsoft 365 Defender giver dig mulighed for proaktivt at jage efter trusler på tværs af:
- Enheder, der administreres af Microsoft Defender for Endpoint
- Mails, der behandles af Microsoft 365
- Aktiviteter i cloudapps, godkendelseshændelser og aktiviteter for domænecontrollere, der spores af Microsoft Defender for Cloud Apps og Microsoft Defender for Identity

Med dette synlighedsniveau kan du hurtigt jage efter trusler, der gennemgår afsnit af dit netværk, herunder avancerede angreb, der ankommer via mail eller på internettet, hæver lokale rettigheder, får privilegerede legitimationsoplysninger til domænet og flytter lateralt til på tværs af dine enheder. 

Her er generelle teknikker og eksempelforespørgsler, der er baseret på forskellige jagtscenarier, som kan hjælpe dig med at udforske, hvordan du kan konstruere forespørgsler, når du jagter sådanne sofistikerede trusler.

## <a name="get-entity-info"></a>Hent enhedsoplysninger
Brug disse forespørgsler til at få mere at vide om, hvordan du hurtigt kan få oplysninger om brugerkonti, enheder og filer. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Hent brugerkonti fra mailadresser
Når du opretter forespørgsler på tværs af [tabeller, der dækker enheder og mails](advanced-hunting-schema-tables.md), skal du sandsynligvis hente brugerkontonavne fra afsender- eller modtagermailadresser. Du kan generelt gøre dette for enten modtager- eller afsenderadressen ved hjælp af den *lokale vært* fra mailadressen.

I kodestykket nedenfor bruger vi funktionen [tostring()](/azure/data-explorer/kusto/query/tostringfunction) Kusto til at udtrække den lokale vært lige før `@` fra modtagermailadresserne i kolonnen `RecipientEmailAddress`.

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
Forespørgslen nedenfor viser, hvordan dette kodestykke kan bruges:

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>Flet tabellen IdentityInfo

Du kan hente kontonavne og andre kontooplysninger ved at flette eller forbinde [tabellen IdentityInfo](advanced-hunting-identityinfo-table.md). Forespørgslen nedenfor henter listen over phishing- og malwareregistreringer fra [tabellen EmailEvents](advanced-hunting-emailevents-table.md) og joinforbinder derefter disse oplysninger med `IdentityInfo` tabellen for at få detaljerede oplysninger om hver modtager. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where ThreatTypes has "Malware" or ThreatTypes has "Phish"
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, ThreatTypes, 
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

### <a name="get-device-information"></a>Hent enhedsoplysninger
Det [avancerede jagtskema](advanced-hunting-schema-tables.md) indeholder omfattende enhedsoplysninger i forskellige tabeller. [Tabellen DeviceInfo](advanced-hunting-deviceinfo-table.md) indeholder f.eks. omfattende enhedsoplysninger baseret på hændelsesdata, der aggregeres regelmæssigt. Denne forespørgsel bruger tabellen `DeviceInfo` til at kontrollere, om en potentielt kompromitteret bruger (`<account-name>`) er logget på en hvilken som helst enhed, og viser derefter de beskeder, der er blevet udløst på disse enheder.

>[!Tip]
> Denne forespørgsel bruger `kind=inner` til at angive en [indre joinforbindelse](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor), hvilket forhindrer deduplikering af værdier på venstre side for `DeviceId`.

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```


### <a name="get-file-event-information"></a>Hent oplysninger om filhændelse

Brug følgende forespørgsel til at hente oplysninger om filrelaterede hændelser. 

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceFileEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="get-network-event-information"></a>Hent oplysninger om netværkshændelser

Brug følgende forespørgsel til at få oplysninger om netværksrelaterede hændelser.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-agent-version-information"></a>Hent versionsoplysninger for enhedsagent

Brug følgende forespørgsel til at få den version af agenten, der kører på en enhed.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="example-query-for-macos-devices"></a>Eksempelforespørgsel til macOS-enheder

Brug følgende eksempelforespørgsel for at se alle enheder, der kører macOS med en version, der er ældre end Catalina.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OSPlatform == "macOS" and  OSVersion !contains "10.15" and OSVersion !contains "11."
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-status-info"></a>Hent oplysninger om enhedsstatus

Brug følgende forespørgsel til at få status for en enhed. I følgende eksempel kontrollerer forespørgslen, om enheden er onboardet.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OnboardingStatus != "Onboarded"
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


## <a name="hunting-scenarios"></a>Jagtscenarier

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Liste over logonaktiviteter for brugere, der har modtaget mails, som ikke blev zapped korrekt
[Zap (automatisk fjernelse) på nul timer](../office-365-security/zero-hour-auto-purge.md) adresserer ondsindede mails, efter de er blevet modtaget. Hvis ZAP mislykkes, kan skadelig kode i sidste ende køre på enheden og efterlade konti kompromitteret. Denne forespørgsel kontrollerer, om der er logonaktivitet foretaget af modtagerne af mails, der ikke blev håndteret korrekt af ZAP.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Få logonforsøg efter domænekonti, der er målrettet efter identitetstyveri af legitimationsoplysninger
Denne forespørgsel identificerer først alle beskeder om adgang til legitimationsoplysninger i tabellen `AlertInfo` . Den fletter eller joinforbinder `AlertEvidence` derefter tabellen, som den fortolker for navnene på de målrettede konti og filtre kun for domænetilsluttede konti. Til sidst kontrollerer den tabellen `IdentityLogonEvents` for at få alle logonaktiviteter fra de domænetilsluttede målrettede konti.

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Kontrollér, om filer fra en kendt ondsindet afsender findes på dine enheder
Hvis du kender en mailadresse, der sender skadelige filer (`MaliciousSender@example.com`), kan du køre denne forespørgsel for at afgøre, om der findes filer fra denne afsender på dine enheder. Du kan f.eks. bruge denne forespørgsel til at identificere enheder, der er påvirket af en malwaredistributionskampagne.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256, DeviceName, DeviceId
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Gennemse logonforsøg efter modtagelse af skadelige mails
Denne forespørgsel finder de 10 seneste logon, der er udført af mailmodtagere inden for 30 minutter, efter at de har modtaget kendte skadelige mails. Du kan bruge denne forespørgsel til at kontrollere, om kontiene for mailmodtagerne er blevet kompromitteret.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where ThreatTypes has "Malware" 
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Gennemse PowerShell-aktiviteter efter modtagelse af mails fra kendt ondsindet afsender
Ondsindede mails indeholder ofte dokumenter og andre særligt udformede vedhæftede filer, der kører PowerShell-kommandoer for at levere yderligere nyttedata. Hvis du er opmærksom på mails, der kommer fra en kendt ondsindet afsender (`MaliciousSender@example.com`), kan du bruge denne forespørgsel til at få vist og gennemse PowerShell-aktiviteter, der fandt sted inden for 30 minutter, efter at der blev modtaget en mail fra afsenderen.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
