---
title: Avancerede bedste fremgangsmåder til forespørgsel på Microsoft 365 Defender
description: Få mere at vide om, hvordan du konstruerer hurtige, effektive og fejlfri trusselsforespørgsler med avanceret jagt
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skema, kusto, undgå timeout, kommandolinjer, proces-id, optimer, bedste praksis, parse, deltag, opsummer
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: d797fb8843bdf5d29e9af43cac152461eb379e5f
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/30/2021
ms.locfileid: "63591188"
---
# <a name="advanced-hunting-query-best-practices"></a>Bedste fremgangsmåder for avanceret forespørgselsforespørgsel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Anvend disse anbefalinger for at få resultater hurtigere og undgå timeouts, mens du kører komplekse forespørgsler. Du kan finde flere vejledninger til forbedring af ydeevnen for forespørgsler ved at læse [Bedste fremgangsmåder for Kusto-forespørgsler](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Forstå CPU-ressourcekvoter
Afhængigt af størrelsen har hver lejer adgang til en bestemt mængde CPU-ressourcer, der er allokeret til at køre avancerede forespørgselsforespørgsler. Du kan få detaljerede oplysninger om forskellige forbrugsparametre ved [at læse om avancerede kvote- og forbrugsparametre](advanced-hunting-limits.md).

Når du har kørt forespørgslen, kan du se eksekveringstiden og dets ressourceforbrug (Lav, Mellem, Høj). Høj angiver, at forespørgslen tog flere ressourcer at køre og kunne forbedres for at returnere resultater mere effektivt.

:::image type="content" source="../../media/resource-usage.png" alt-text="Forespørgselsdetaljerne under fanen **Resultater** i Microsoft 365 Defender portal" lightbox="../../media/resource-usage.png":::

Kunder, der kører flere forespørgsler regelmæssigt, bør registrere forbrug og anvende optimeringsvejledningen i denne artikel for at minimere afbrydelser, der opstår som følge af, at kvoter eller brugsparametre overskrides.

## <a name="general-optimization-tips"></a>Generelle tip til optimering

- **Tilpas størrelsen på nye forespørgsler** – Hvis du har mistanke om, at en forespørgsel vil returnere et stort resultatsæt, skal du først vurdere det ved hjælp af [antalsoperatoren](/azure/data-explorer/kusto/query/countoperator). Brug [begrænsning eller](/azure/data-explorer/kusto/query/limitoperator) dens synonym `take` for at undgå store resultatsæt.
- Anvend filtre tidligt – Anvend tidsfiltre og andre filtre for at reducere datasættet, især før du bruger transformations- og parsingfunktioner som f.eks. understreng[()](/azure/data-explorer/kusto/query/substringfunction), [erstat()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction) eller [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). I eksemplet nedenfor bruges fortolkningsfunktionen [extractjson(),](/azure/data-explorer/kusto/query/extractjsonfunction) når filtreringsoperatorer har reduceret antallet af poster.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Har beats indeholder** – Brug operatoren i stedet for at undgå at søge unødvendigt på `has` understrenge i ord `contains`. [Få mere at vide om strengoperatorer](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Se i bestemte kolonner –** Se i en bestemt kolonne i stedet for at køre fuld tekstsøgninger på tværs af alle kolonner. Brug ikke til at `*` markere alle kolonner.
- **Der er brug for hastighedsbaseret brug** af store og små bogstaver til at tage hensyn til store og små bogstaver – søgninger med store og små bogstaver er mere specifikke og generelt mere præcise. Navnene på strengoperatorer [med store og små bogstaver](/azure/data-explorer/kusto/query/datatypes-string-operators), f.eks`contains_cs`. `has_cs` og , slutter generelt med `_cs`. Du kan også bruge operatoren til at svare til store og små bogstaver i stedet `==` for `=~`.
- **Fortolkning, udtræk** ikke – når det er muligt, skal du bruge [parseoperatoren](/azure/data-explorer/kusto/query/parseoperator) eller en fortolkningsfunktion som [f.eks. parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). Undgå strengoperatoren `matches regex` eller [funktionen Extract(](/azure/data-explorer/kusto/query/extractfunction)), som begge bruger regulære udtryk. Reservere brugen af regulære udtryk til mere komplekse scenarier. [Læs mere om fortolkningsfunktioner](#parse-strings)
- **Filtrer tabeller ikke udtryk –** Filtrer ikke på en beregnet kolonne, hvis du kan filtrere på en tabelkolonne.
- **Ingen tretegnsudtryk** – Undgå at sammenligne eller filtrere med ord med tre tegn eller færre. Disse udtryk indekseres ikke, og det vil kræve flere ressourcer at matche dem.
- **Project selektivt – Gør** det nemmere at forstå resultaterne ved kun at projicere de kolonner, du skal bruge. Hvis du projicere bestemte kolonner, før du [kører joinforbindelse](/azure/data-explorer/kusto/query/joinoperator) eller lignende handlinger, kan det også forbedre ydeevnen.

## <a name="optimize-the-join-operator"></a>Optimere operatoren `join`
[Joinoperatoren](/azure/data-explorer/kusto/query/joinoperator) fletter rækker fra to tabeller ved at matche værdier i angivne kolonner. Anvend disse tip for at optimere forespørgsler, der bruger denne operator.

- **Mindre tabel til venstre –** Operatoren `join` matcher poster i tabellen i venstre side af joinsætningen til poster i højre side. Ved at have den mindre tabel til venstre skal færre poster matches, hvilket gør forespørgslen hurtigere.

    I tabellen nedenfor reducerer vi den venstre tabel `DeviceLogonEvents` , så den kun dækker tre specifikke enheder, før de sluttes til den `IdentityLogonEvents` med konto-SID'er.

    ```kusto
    DeviceLogonEvents
    | where DeviceName in ("device-1.domain.com", "device-2.domain.com", "device-3.domain.com")
    | where ActionType == "LogonFailed"
    | join
        (IdentityLogonEvents
        | where ActionType == "LogonFailed"
        | where Protocol == "Kerberos")
    on AccountSid
    ```

- **Brug indre join-smag** – Standard [join-smagen](/azure/data-explorer/kusto/query/joinoperator#join-flavors) eller [innerunique-join](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) dedubleerer rækker i venstre tabel med join-tasten, før du returnerer en række for hvert match til den højre tabel. Hvis den venstre tabel har flere rækker med samme værdi for `join` nøglen, bliver disse rækker dedubleret, så der efterlades en enkelt tilfældig række for hver entydige værdi.

    Denne standardfunktionsmåde kan indeholde vigtige oplysninger fra den venstre tabel, som kan give nyttig indsigt. For eksempel viser nedenstående forespørgsel kun én mail, der indeholder en bestemt vedhæftet fil, selvom den samme vedhæftede fil blev sendt ved hjælp af flere mails:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    For at løse denne begrænsning anvender vi [indre join-smag](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) `kind=inner` ved at angive, at alle rækker i den venstre tabel skal vises med matchende værdier i højre side:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Sammenlæg poster fra en tidsperiode – Når** der undersøger sikkerhedshændelser, leder analytikere efter relaterede hændelser, der forekommer omkring den samme tidsperiode. At anvende den samme fremgangsmåde, når du `join` også bruger fordelsydeevne ved at reducere antallet af poster, der skal kontrolleres.

    Forespørgslen nedenfor kontrollerer, om der er logonhændelser inden for 30 minutter efter modtagelse af en skadelig fil:

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where ThreatTypes has "Malware"
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **Anvend tidsfiltre** på begge sider – Selvom du ikke undersøger en bestemt periode, `join` kan du reducere antallet af poster for at kontrollere og forbedre ydeevnen ved at anvende tidsfiltre både i venstre og højre tabel. Forespørgslen nedenfor gælder for `Timestamp > ago(1h)` begge tabeller, så den kun joinforbindelse poster fra den seneste time:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Brug tip til ydeevnen – Brug** tip `join` sammen med operatoren til at instruere backend'en om at fordele belastningen, når du kører ressourcekrævende handlinger. [Få mere at vide om jointip](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Bland f.eks **[](/azure/data-explorer/kusto/query/shufflequery)**. hjælper med at forbedre ydeevnen for forespørgsler, når du sætter tabeller sammen ved hjælp af en nøgle med høj kardinalitet – `AccountObjectId` en nøgle med mange entydige værdier– f.eks. i forespørgslen nedenfor:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[Udsendelsestippet](/azure/data-explorer/kusto/query/broadcastjoin)** hjælper, når tabellen til venstre er lille (op til 100.000 poster), og den højre tabel er meget stor. For eksempel forsøger forespørgslen nedenfor at deltage i et par mails, der har bestemte emner med _alle meddelelser_ , der indeholder links i `EmailUrlInfo` tabellen:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optimere operatoren `summarize`
[Summeringsoperatoren](/azure/data-explorer/kusto/query/summarizeoperator) aggregerer indholdet af en tabel. Anvend disse tip for at optimere forespørgsler, der bruger denne operator.

- **Find særskilte værdier –** generelt kan det bruges til `summarize` at finde særskilte værdier, der kan gentages. Det kan være unødvendigt at bruge det til at sammenlægge kolonner, der ikke har gentagne værdier.

    Selvom en enkelt mail kan være en del af flere hændelser,  `summarize` er eksemplet nedenfor ikke en effektiv brug af, fordi et netværksmeddelelses-id for en enkelt mail altid leveres med en entydig afsenderadresse.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    Operatoren `summarize` kan nemt erstattes med `project`, hvilket potentielt giver de samme resultater, mens der forbruges færre ressourcer:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Det følgende eksempel er en mere effektiv `summarize` brug af, fordi der kan være flere forskellige forekomster af en afsenderadresse, der sender mails til den samme modtageradresse. Sådanne kombinationer er mindre forskellige og vil sandsynligvis have dubletter.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Bland forespørgslen – mens** det `summarize` bedst bruges i kolonner med gentagne værdier, kan de samme kolonner _også have høj_ kardinalitet eller et stort antal entydige værdier. Ligesom operatoren `join` kan du [](/azure/data-explorer/kusto/query/shufflequery) `summarize` også anvende omkredsen med til at fordele behandlingsbelastningen og potentielt forbedre ydeevnen, når du arbejder på kolonner med høj kardinalitet.

    Forespørgslen nedenfor bruger til at `summarize` tælle forskellige modtagermailadresser, som kan køre i hundreder af tusinder i store organisationer. For at forbedre ydeevnen indeholder den `hint.shufflekey`:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

## <a name="query-scenarios"></a>Forespørgselsscenarier

### <a name="identify-unique-processes-with-process-ids"></a>Identificer entydige processer med proces-id'er

Proces-id'er (PID'er) genbruges i Windows og genbruges til nye processer. De kan ikke selv fungere som entydige identifikatorer for bestemte processer.

For at få et entydig identifier til en proces på en bestemt computer skal du bruge proces-id'et sammen med tidspunktet for oprettelse af processen. Når du joinforbindelse eller opsummerer data om processer, skal du medtage kolonner til computer-id'et (`DeviceId`enten eller ), proces-id'et ( `InitiatingProcessId``ProcessId` eller ) og procesoprettelsesstiden (`ProcessCreationTime` eller `InitiatingProcessCreationTime`)`DeviceName`

I følgende eksempel finder forespørgslen processer, der har adgang til mere end 10 IP-adresser over port 445 (SMB), muligvis scanning for filshares.

Eksempelforespørgsel:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Forespørgslen opsummeres ved begge, og `InitiatingProcessId` så `InitiatingProcessCreationTime` den ser på en enkelt proces uden at blande flere processer med det samme proces-id.

### <a name="query-command-lines"></a>Forespørgselskommandolinjer
Der er mange måder at oprette en kommandolinje på for at udføre en opgave. En hacker kan f.eks. referere til en billedfil uden en sti, uden filtypenavn, ved hjælp af miljøvariabler eller med anførselstegn. Hackeren kan også ændre rækkefølgen af parametre eller tilføje flere anførselstegn og mellemrum.

Hvis du vil oprette mere robuste forespørgsler omkring kommandolinjer, skal du anvende følgende fremgangsmåder:

- Identificer de kendte processer (f.eks *.net.exe* eller *psexec.exe*) ved at matche på felterne med filnavne i stedet for at filtrere på selve kommandolinjen.
- Fortolke kommandolinjesnit ved hjælp af parse_command_line [()](/azure/data-explorer/kusto/query/parse-command-line)
- Når du forespørger efter kommandolinjeargumenter, skal du ikke se efter et nøjagtigt match for flere ikke-relaterede argumenter i en bestemt rækkefølge. Brug i stedet regulære udtryk, eller brug flere separate indeholder operatorer.
- Brug store og små bogstaver til ikke at tage hensyn til matches. Du kan f.eks `=~`. bruge `in~`, og `contains` i stedet for `==`, `in`og `contains_cs`.
- For at reducere teknikker til fjernelse af kommandolinjen bør du overveje at fjerne anførselstegn, erstatte kommaer med mellemrum og erstatte flere efterfølgende mellemrum med et enkelt mellemrum. Der er mere komplekse obskønationsteknikker, der kræver andre metoder, men disse finjusteringer kan hjælpe med at håndtere almindelige teknikker.

Følgende eksempler viser forskellige måder at konstruere en forespørgsel på, der søger efter filennet.exe *at* stoppe firewalltjenesten "MpsSvc":

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on file name, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc"

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc"
```

### <a name="ingest-data-from-external-sources"></a>Ngest data from external sources
Hvis du vil inkorporere lange lister eller store tabeller i din forespørgsel, skal du bruge [den eksterne dataoperator](/azure/data-explorer/kusto/query/externaldata-operator) til at ingeste data fra en angivet URI. Du kan hente data fra filer i TXT, CSV, JSON eller [andre formater](/azure/data-explorer/ingestion-supported-formats). Eksemplet nedenfor viser, hvordan du kan udnytte den omfattende liste over malware SHA-256-hashes, der leveres af MalwareBazaar (abuse.ch) til at kontrollere vedhæftede filer i mails:

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string)
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo
| where Timestamp > ago(1d)
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,ThreatTypes,DetectionMethods
```

### <a name="parse-strings"></a>Fortolke strenge
Der findes forskellige funktioner, du kan bruge til effektivt at håndtere strenge, der skal fortolkes eller konverteres.

| String | Funktion | Brugseksememem |
|--|--|--|
| Kommandolinjer | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Udtræk kommandoen og alle argumenter. |
| Stier | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Udtræk sektionerne i en fil- eller mappesti. |
| Versionsnumre | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Dekonstruer et versionsnummer med op til fire sektioner og op til otte tegn pr. sektion. Brug fortolkede data til at sammenligne versionens alder. |
| IPv4-adresser | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Konvertér en IPv4-adresse til et langt heltal. Hvis du vil sammenligne IPv4-adresser uden at konvertere dem, [skal ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| IPv6-adresser | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Konvertér en IPv4- eller IPv6-adresse til den ved canonical IPv6-notation. For at sammenligne IPv6-adresser skal [du ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Du kan få mere at vide om alle understøttede fortolkningsfunktioner [ved at læse om Kusto-strengfunktioner](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Kusto-forespørgselssprogdokumentation](/azure/data-explorer/kusto/query/)
- [Kvoter og brugsparametre](advanced-hunting-limits.md)
- [Håndter avancerede jagtfejl](advanced-hunting-errors.md)
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)