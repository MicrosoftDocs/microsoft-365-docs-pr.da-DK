---
title: Avancerede bedste praksisser for jagtforespørgslen i Microsoft 365 Defender
description: Få mere at vide om, hvordan du konstruerer forespørgsler om hurtig, effektiv og fejlfri trusselsjagt med avanceret jagt
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skema, kusto, undgå timeout, kommandolinjer, proces-id, optimere, bedste praksis, fortolke, joinforbinde, opsummere
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
ms.openlocfilehash: 505308bec005811e174b90cde9e872532ccacdfe
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739477"
---
# <a name="advanced-hunting-query-best-practices"></a>Avancerede bedste praksisser for jagtforespørgslen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Anvend disse anbefalinger for at opnå resultater hurtigere og undgå timeout under kørsel af komplekse forespørgsler. Hvis du vil have mere hjælp til at forbedre ydeevnen af forespørgsler, skal du læse [Bedste praksis for Kusto-forespørgsler](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>Forstå kvoter for CPU-ressourcer
Afhængigt af størrelsen har hver lejer adgang til en bestemt mængde CPU-ressourcer, der er allokeret til kørsel af avancerede jagtforespørgsler. Du kan finde detaljerede oplysninger om forskellige forbrugsparametre ved [at læse om avancerede jagtkvoter og forbrugsparametre](advanced-hunting-limits.md).

Når du har kørt din forespørgsel, kan du se udførelsestiden og dens ressourceforbrug (Lav, Mellem, Høj). High angiver, at forespørgslen tog flere ressourcer at køre og kunne forbedres for at returnere resultater mere effektivt.

:::image type="content" source="../../media/resource-usage.png" alt-text="Forespørgselsdetaljerne under fanen **Resultater** på Microsoft 365 Defender-portalen" lightbox="../../media/resource-usage.png":::

Kunder, der kører flere forespørgsler regelmæssigt, bør spore forbruget og anvende optimeringsvejledningen i denne artikel for at minimere afbrydelse som følge af overskridelse af kvoter eller forbrugsparametre.

## <a name="general-optimization-tips"></a>Generelle optimeringstip

- **Tilpas størrelsen på nye forespørgsler** – Hvis du har mistanke om, at en forespørgsel returnerer et stort resultatsæt, skal du først vurdere det ved hjælp af [optællingsoperatoren](/azure/data-explorer/kusto/query/countoperator). Brug [grænse](/azure/data-explorer/kusto/query/limitoperator) eller synonymet `take` for at undgå store resultatsæt.
- **Anvend filtre tidligt** – Anvend tidsfiltre og andre filtre for at reducere datasættet, især før du bruger transformations- og fortolkningsfunktioner, f.eks [. understreng()](/azure/data-explorer/kusto/query/substringfunction), [erstat()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction)eller [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). I eksemplet nedenfor bruges fortolkningsfunktionen [extractjson(),](/azure/data-explorer/kusto/query/extractjsonfunction) når filtreringsoperatorer har reduceret antallet af poster.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Har beats indeholder**. Hvis du vil undgå unødvendigt at søge efter understrenge i ord, skal du bruge operatoren `has` i stedet for `contains`. [Få mere at vide om strengoperatorer](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Søg i bestemte kolonner** – Søg i en bestemt kolonne i stedet for at køre fuldtekstsøgninger på tværs af alle kolonner. Brug ikke `*` til at kontrollere alle kolonner.
- **Forskel på store og små bogstaver i forbindelse med hastighed** – Søgninger med forskel på store og små bogstaver er mere specifikke og generelt mere udførligt. Navne på [strengoperatorer](/azure/data-explorer/kusto/query/datatypes-string-operators) med forskel på store og små bogstaver, f.eks `has_cs` . og `contains_cs`, slutter normalt med `_cs`. Du kan også bruge operatoren `==` equals i stedet for `=~`.
- **Opspar, udtræk ikke** – Når det er muligt, skal du bruge [fortolkningsoperatoren](/azure/data-explorer/kusto/query/parseoperator) eller en fortolkningsfunktion, [f.eks. parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). `matches regex` Undgå strengoperatoren eller [funktionen extract(),](/azure/data-explorer/kusto/query/extractfunction) som begge bruger regulært udtryk. Forbeholder dig brugen af regulære udtryk til mere komplekse scenarier. [Læs mere om fortolkningsfunktioner](#parse-strings)
- **Filtrer tabeller ikke udtryk – Filtrer** ikke efter en beregnet kolonne, hvis du kan filtrere på en tabelkolonne.
- **Ingen ord med tre tegn** – undgå at sammenligne eller filtrere ved hjælp af ord med tre tegn eller færre. Disse ord er ikke indekseret, og matchning af dem kræver flere ressourcer.
- **Project selektivt** – gør dine resultater nemmere at forstå ved kun at projektere de kolonner, du har brug for. Projektering af bestemte kolonner, før der køres [joinforbindelser](/azure/data-explorer/kusto/query/joinoperator) eller lignende handlinger, hjælper også med at forbedre ydeevnen.

## <a name="optimize-the-join-operator"></a>Optimer operatoren `join`
[Joinoperatoren](/azure/data-explorer/kusto/query/joinoperator) fletter rækker fra to tabeller ved at matche værdier i angivne kolonner. Anvend disse tip til at optimere forespørgsler, der bruger denne operator.

- **Mindre tabel til venstre** – operatoren `join` matcher poster i tabellen i venstre side af joinsætningen med poster til højre. Når den mindre tabel er til venstre, skal der matches færre poster, så forespørgslen bliver hurtigere.

    I nedenstående tabel reducerer vi den venstre tabel `DeviceLogonEvents` , så den kun dækker tre specifikke enheder, før den forbindes med `IdentityLogonEvents` konto-SID'er.

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

- **Brug den indre joinforbindelsessmag** – [standardjoinsmagen](/azure/data-explorer/kusto/query/joinoperator#join-flavors) eller den [innerunique-joinforbindelse](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) deduplikerer rækker i venstre tabel ved joinnøglen, før der returneres en række for hver forekomst af den højre tabel. Hvis den venstre tabel indeholder flere rækker med den samme værdi for `join` nøglen, deduplikeres disse rækker for at efterlade en enkelt tilfældig række for hver entydige værdi.

    Denne standardfunktionsmåde kan udelade vigtige oplysninger fra den venstre tabel, som kan give nyttig indsigt. Forespørgslen nedenfor viser f.eks. kun én mail, der indeholder en bestemt vedhæftet fil, selvom den samme vedhæftede fil blev sendt ved hjælp af flere mails:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    For at løse denne begrænsning anvender vi [den indre joinforbindelsessmag](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) ved at angive `kind=inner` , at alle rækker i tabellen til venstre skal vises med tilsvarende værdier til højre:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Joinforbind poster fra et tidsvindue** – Når analytikere undersøger sikkerhedshændelser, søger de efter relaterede hændelser, der forekommer omkring samme tidsperiode. Anvendelse af den samme tilgang, når du bruger `join` , gavner også ydeevnen ved at reducere antallet af poster, der skal kontrolleres.

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
- **Anvend tidsfiltre på begge sider** – Selvom du ikke undersøger et bestemt tidsvindue, kan anvendelse af tidsfiltre på både venstre og højre tabeller reducere antallet af poster for at kontrollere og forbedre `join` ydeevnen. Forespørgslen nedenfor gælder for `Timestamp > ago(1h)` begge tabeller, så den kun joinforbinder poster fra den seneste time:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Brug tip til ydeevne** – Brug tip med operatoren `join` til at instruere backend til at distribuere belastningen, når der køres ressourcetunge handlinger. [Få mere at vide om jointip](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    **[Shuffle-tip hjælper](/azure/data-explorer/kusto/query/shufflequery)** f.eks. med at forbedre forespørgslens ydeevne, når tabeller forbindes ved hjælp af en nøgle med høj kardinalitet – en nøgle med mange entydige værdier – f.eks`AccountObjectId`. i forespørgslen nedenfor:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[Udsendelsestip hjælper](/azure/data-explorer/kusto/query/broadcastjoin)**, når den venstre tabel er lille (op til 100.000 poster), og den højre tabel er meget stor. Forespørgslen nedenfor forsøger f.eks. at joinforbinde et par mails, der har specifikke emner med _alle_ meddelelser, der indeholder links i tabellen `EmailUrlInfo` :

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>Optimer operatoren `summarize`
[Opsummeringsoperatoren](/azure/data-explorer/kusto/query/summarizeoperator) samler indholdet af en tabel. Anvend disse tip til at optimere forespørgsler, der bruger denne operator.

- **Find entydige værdier** – Generelt kan du bruge `summarize` til at finde entydige værdier, der kan gentages. Det kan være unødvendigt at bruge det til at aggregere kolonner, der ikke har gentagne værdier.

    Selvom en enkelt mail kan være en del af flere hændelser, er eksemplet nedenfor _ikke_ en effektiv brug af `summarize` , fordi et netværksmeddelelses-id for en individuel mail altid leveres med en entydig afsenderadresse.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    Operatoren `summarize` kan nemt erstattes med , som potentielt giver de samme resultater, samtidig med `project`at der bruges færre ressourcer:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Følgende eksempel er en mere effektiv brug af `summarize` , fordi der kan være flere forskellige forekomster af en afsenderadresse, der sender mail til den samme modtageradresse. Disse kombinationer er mindre entydige og vil sandsynligvis have dubletter.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Bland forespørgslen** – Selvom `summarize` den bedst bruges i kolonner med gentagne værdier, kan de samme kolonner også have _høj kardinalitet_ eller et stort antal entydige værdier. Ligesom operatoren `join` kan du også anvende [shuffle-tip](/azure/data-explorer/kusto/query/shufflequery) til `summarize` at distribuere behandlingsbelastningen og muligvis forbedre ydeevnen, når du arbejder på kolonner med høj kardinalitet.

    Forespørgslen nedenfor bruger `summarize` til at tælle særskilt modtagermailadresse, som kan køre i hundredtusindvis i store organisationer. For at forbedre ydeevnen omfatter `hint.shufflekey`den :

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

Se denne [korte video](https://www.youtube.com/watch?v=ceYvRuPp5D8) for at få mere at vide om, hvordan du kan optimere Kusto-forespørgselssproget.  

## <a name="query-scenarios"></a>Forespørgselsscenarier

### <a name="identify-unique-processes-with-process-ids"></a>Identificer entydige processer med proces-id'er

Proces-id'er genbruges i Windows og genbruges til nye processer. De kan ikke alene fungere som entydige identifikatorer for bestemte processer.

Hvis du vil hente et entydigt id for en proces på en bestemt computer, skal du bruge proces-id'et sammen med processens oprettelsestid. Når du joinforbinder eller opsummerer data om processer, skal du inkludere kolonner for computer-id'et (enten `DeviceId` eller `DeviceName`), proces-id'et (`ProcessId` eller `InitiatingProcessId`) og tidspunktet for oprettelse af processen (`ProcessCreationTime` eller `InitiatingProcessCreationTime`)

Følgende eksempelforespørgsel finder processer, der har adgang til mere end 10 IP-adresser via port 445 (SMB), og som muligvis søger efter filshares.

Eksempelforespørgsel:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Forespørgslen opsummeres af begge `InitiatingProcessId` , så `InitiatingProcessCreationTime` den ser på en enkelt proces uden at blande flere processer med det samme proces-id.

### <a name="query-command-lines"></a>Forespørgselskommandolinjer
Der er mange måder at oprette en kommandolinje på for at udføre en opgave. En hacker kan f.eks. referere til en billedfil uden en sti, uden et filtypenavn, ved hjælp af miljøvariabler eller med anførselstegn. Hackeren kan også ændre rækkefølgen af parametre eller tilføje flere anførselstegn og mellemrum.

Hvis du vil oprette mere holdbare forespørgsler omkring kommandolinjer, skal du anvende følgende fremgangsmåder:

- Identificer de kendte processer (f.eks *.net.exe* eller *psexec.exe*) ved at matche felterne med filnavne i stedet for at filtrere på selve kommandolinjen.
- Fortolk kommandolinjesektioner ved hjælp af [funktionen parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- Når du forespørger efter kommandolinjeargumenter, skal du ikke søge efter et nøjagtigt match på flere ikke-relaterede argumenter i en bestemt rækkefølge. Brug i stedet regulære udtryk, eller brug flere separate indeholder operatorer.
- Brug match, hvor der ikke skelnes mellem store og små bogstaver. Brug f.eks. `=~`, `in~`og `contains` i stedet for `==`, `in`og `contains_cs`.
- Hvis du vil afhjælpe teknikker til tilsløring af kommandolinjer, kan du overveje at fjerne anførselstegn, erstatte kommaer med mellemrum og erstatte flere efter hinanden følgende mellemrum med et enkelt mellemrum. Der er mere komplekse tilsløringsteknikker, der kræver andre metoder, men disse justeringer kan hjælpe med at løse almindelige.

Følgende eksempler viser forskellige måder at konstruere en forespørgsel, der søger efter filen *net.exe* til at stoppe firewalltjenesten "MpsSvc":

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

### <a name="ingest-data-from-external-sources"></a>Indfødning af data fra eksterne kilder
Hvis du vil inkorporere lange lister eller store tabeller i din forespørgsel, skal du bruge [operatoren externaldata](/azure/data-explorer/kusto/query/externaldata-operator) til at indtage data fra en angivet URI. Du kan hente data fra filer i TXT-, CSV-, JSON- eller [andre formater](/azure/data-explorer/ingestion-supported-formats). Nedenstående eksempel viser, hvordan du kan bruge den omfattende liste over malware SHA-256-hashen leveret af MalwareBazaar (abuse.ch) til at kontrollere vedhæftede filer på mails:

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

### <a name="parse-strings"></a>Fortolkningsstrenge
Der er forskellige funktioner, som du kan bruge til effektivt at håndtere strenge, der skal analyseres eller konverteres.

| String | Funktion | Eksempel på anvendelse |
|--|--|--|
| Kommandolinjer | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Udpak kommandoen og alle argumenter. |
| Stier | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Udpak sektionerne i en fil- eller mappesti. |
| Versionsnumre | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Dekonstruer et versionsnummer med op til fire sektioner og op til otte tegn pr. sektion. Brug de analyserede data til at sammenligne versionens alder. |
| IPv4-adresser | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | Konvertér en IPv4-adresse til et langt heltal. Hvis du vil sammenligne IPv4-adresser uden at konvertere dem, skal du bruge [ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| IPv6-adresser | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | Konvertér en IPv4- eller IPv6-adresse til den kanoniske IPv6-notation. Hvis du vil sammenligne IPv6-adresser, skal [du bruge ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Hvis du vil vide mere om alle understøttede fortolkningsfunktioner, kan [du læse om Kusto-strengfunktioner](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender for Endpoint. [Slå Microsoft 365 Defender](m365d-enable.md) til for at jagte trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser for jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i [Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Dokumentation til Kusto-forespørgselssprog](/azure/data-explorer/kusto/query/)
- [Kvoter og brugsparametre](advanced-hunting-limits.md)
- [Håndter avancerede jagtfejl](advanced-hunting-errors.md)
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)