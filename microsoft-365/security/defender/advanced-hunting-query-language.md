---
title: Lær sproget for avanceret forespørgsel om Microsoft 365 Defender
description: Opret din første trusselsforespørgsel, og få mere at vide om almindelige operatorer og andre aspekter af det avancerede forespørgselssprog til forespørgsel om trusler
keywords: avanceret jagt, trusselssporing, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, sprog, lær, første forespørgsel, telemetri, begivenheder, telemetri, brugerdefinerede registreringer, skema, kusto, operatorer, datatyper, download af powershell, eksempel på forespørgsel
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
ms.openlocfilehash: 7092b4ed30400fb559751d4d939801c1982407f8
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63599312"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Lær det avancerede forespørgselssprog

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Avanceret jagt er baseret på [Kusto-forespørgselssproget](/azure/kusto/query/). Du kan bruge Kusto-operatorer og -sætninger til at oprette forespørgsler, der finder oplysninger i et specialiseret [skema](advanced-hunting-schema-tables.md). 

Se denne korte video for at lære nogle praktiske grundlæggende oplysninger om Kusto-forespørgselssprog.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Kør din første forespørgsel for bedre at forstå disse begreber.

## <a name="try-your-first-query"></a>Prøv din første forespørgsel

I portalen Microsoft 365 Defender skal du gå til **På jagt for** at køre din første forespørgsel. Brug følgende eksempel: 

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[Kør denne forespørgsel i avanceret jagt](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>Beskriv forespørgslen, og angiv de tabeller, der skal søges i
En kort kommentar er blevet føjet til starten af forespørgslen for at beskrive, hvad den bruges til. Denne kommentar hjælper dig, hvis du senere beslutter dig for at gemme forespørgslen og dele den med andre i organisationen. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Selve forespørgslen starter typisk med et tabelnavn efterfulgt af flere elementer, der starter med et pipe (`|`). I dette eksempel starter vi med at oprette en forening af to tabeller og  `DeviceProcessEvents` `DeviceNetworkEvents`og tilføjer piperede elementer efter behov.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>Angive tidsintervallet
Det første pipedelement er et tidsfilter, der er begrænset til de foregående syv dage. At begrænse tidsintervallet er med til at sikre, at forespørgsler fungerer godt, returnerer håndterbare resultater og ikke får time out.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Kontrollér bestemte processer
Tidsintervallet efterfølges straks af en søgning efter procesfilnavne, der repræsenterer PowerShell-programmet.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Søge efter bestemte kommandostrenge
Bagefter søger forespørgslen efter strenge i kommandolinjer, der typisk bruges til at downloade filer ved hjælp af PowerShell.

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>Tilpas resultatkolonner og -længde 
Nu hvor forespørgslen tydeligt identificerer de data, du vil finde, kan du definere, hvordan resultaterne skal se ud. `project` returnerer bestemte kolonner og begrænser `top` antallet af resultater. Disse operatorer hjælper med at sikre, at resultaterne er korrekt formateret og rimeligt store og nemme at behandle.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Vælg **Kør forespørgsel for** at se resultaterne.

>[!TIP]
>Du kan få vist forespørgselsresultater som diagrammer og hurtigt justere filtre. Du kan få vejledning [ved at læse om at arbejde med forespørgselsresultater](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>Få mere at vide om almindelige forespørgselsoperatorer

Du har lige kørt din første forespørgsel og har en generel ide om dens komponenter. Det er tid til at gå en smule tilbage og lære nogle grundlæggende ting. Det kusto-forespørgselssprog, der bruges af avanceret jagt, understøtter en række operatorer, herunder følgende almindelige.

| Operator | Beskrivelse og anvendelse |
|--|--|
| `where` | Filtrer en tabel til undersættet af rækker, der opfylder et prædikat. |
| `summarize` | Fremstille en tabel, der samler indholdet af inputtabellen. |
| `join` | Flet rækkerne i to tabeller for at danne en ny tabel ved at matche værdierne for de angivne kolonner fra hver tabel. |
| `count` | Returner antallet af poster i inputpostsættet. |
| `top` | Returner de første N poster, der er sorteret efter de angivne kolonner. |
| `limit` | Gå tilbage til det angivne antal rækker. |
| `project` | Markér de kolonner, der skal medtages, omdøbes eller slippes, og indsæt nye beregnede kolonner. |
| `extend` | Opret beregnede kolonner, og føj dem til resultatsættet. |
| `makeset` |  Returner en dynamisk (JSON) matrix af det sæt af særskilte værdier, som Udtryk tager i gruppen. |
| `find` | Find rækker, der svarer til et prædikat på tværs af et sæt tabeller. |

Hvis du vil se et direkte eksempel på disse operatorer, skal du køre dem **fra sektionen Kom** i gang under Avanceret jagt.

## <a name="understand-data-types"></a>Forstå datatyper

Avanceret jagt understøtter Kusto-datatyper, herunder følgende almindelige typer:

| Datatype | Beskrivelse og forespørgsels konsekvenser |
|--|--|
| `datetime` | Data- og klokkeslætsoplysninger repræsenterer typisk tidsstempler for begivenheder. [Se understøttede datetime-formater](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Tegnstreng i UTF-8 omsluttet af enkelte anførselstegn (`'`) eller dobbelte anførselstegn (`"`). [Læs mere om strenge](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Denne datatype understøtter `true` eller `false` tilstande. [Se understøttede konstanter og operatorer](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32-bit heltal  |
| `long` | 64-bit heltal |

Du kan få mere at vide om disse [datatyper ved at læse om Kusto-skalardatatyper](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Få hjælp, mens du skriver forespørgsler
Udnyt følgende funktioner til at skrive forespørgsler hurtigere:
- **Autosuggest –** mens du skriver forespørgsler, giver avanceret jagt forslag fra IntelliSense. 
- **Skematræ** – en skemarepræsentation, der omfatter listen over tabeller og deres kolonner, findes ud for arbejdsområdet. Hold markøren over et element for at få flere oplysninger. Dobbeltklik på et element for at indsætte det i forespørgselseditoren.
- **[Skemareference](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** – i-portalens reference med tabel- og kolonnebeskrivelser samt understøttede hændelsestyper (`ActionType` værdier) og eksempelforespørgsler

## <a name="work-with-multiple-queries-in-the-editor"></a>Arbejd med flere forespørgsler i editoren
Du kan bruge forespørgselseditoren til at eksperimentere med flere forespørgsler. Sådan bruger du flere forespørgsler:

- Adskild hver forespørgsel med en tom linje.
- Placer markøren på en del af en forespørgsel for at vælge forespørgslen, før du kører den. Dette vil kun køre den valgte forespørgsel. Hvis du vil køre en anden forespørgsel, skal du flytte markøren i overensstemmelse hermed og **vælge Kør forespørgsel**.

:::image type="content" source="../../media/learn-work-with-multiple.png" alt-text="Et eksempel på udførelse af flere forespørgsler på siden **Ny forespørgsel** i Microsoft 365 Defender-portalen" lightbox="../../media/learn-work-with-multiple.png":::

## <a name="use-sample-queries"></a>Brug eksempelforespørgsler

Afsnittet **Introduktion indeholder** et par enkle forespørgsler, der anvender ofte anvendte operatorer. Prøv at køre disse forespørgsler og foretage mindre ændringer af dem.

:::image type="content" source="../../media/get-started-section.png" alt-text="Sektionen **Introduktion** på siden **Avanceret jagt** på Microsoft 365 Defender portal" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Ud over de grundlæggende forespørgselseksempler kan du også [få adgang til delte forespørgsler](advanced-hunting-shared-queries.md) til bestemte scenarier med trusselsfang. Udforsk de delte forespørgsler i venstre side af siden eller på GitHub [forespørgselslager.](https://aka.ms/hunting-queries)

## <a name="access-query-language-documentation"></a>Sprogdokumentation til Access-forespørgsel

Du kan finde flere oplysninger om Kusto-forespørgselssprog og understøttede operatorer under [Kusto-forespørgselssprogdokumentation](/azure/kusto/query/).

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)