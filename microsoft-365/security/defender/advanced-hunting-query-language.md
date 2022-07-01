---
title: Få mere at vide om sproget for forespørgsler om avanceret jagt i Microsoft 365 Defender
description: Opret din første trusselsjagtforespørgsel, og få mere at vide om almindelige operatorer og andre aspekter af det avancerede forespørgselssprog for jagt
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, sprog, lære, første forespørgsel, telemetri, hændelser, telemetri, brugerdefinerede registreringer, skema, kusto, operatorer, datatyper, powershell-download, eksempel på forespørgsel
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
ms.openlocfilehash: 8c650e639d1a4629ed25bcc3a7f3a8c28df4b8e8
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603464"
---
# <a name="learn-the-advanced-hunting-query-language"></a>Få mere at vide om det avancerede forespørgselssprog for jagt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**

- Microsoft 365 Defender
- Microsoft Defender for Endpoint

Avanceret jagt er baseret på [Kusto-forespørgselssproget](/azure/kusto/query/). Du kan bruge Kusto-operatorer og -sætninger til at oprette forespørgsler, der finder oplysninger i et specialiseret [skema](advanced-hunting-schema-tables.md). 

Se denne korte video for at lære nogle praktiske grundlæggende oplysninger om Kusto-forespørgselssprog.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
Hvis du vil have en bedre forståelse af disse begreber, skal du køre din første forespørgsel.

## <a name="try-your-first-query"></a>Prøv din første forespørgsel

I Microsoft 365 Defender-portalen skal du gå til **Jagt** for at køre din første forespørgsel. Brug følgende eksempel: 

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

Der er føjet en kort kommentar til starten af forespørgslen for at beskrive, hvad den er beregnet til. Denne kommentar hjælper, hvis du senere beslutter at gemme forespørgslen og dele den med andre i din organisation. 

```kusto
// Finds PowerShell execution events that could involve a download
```

Selve forespørgslen starter typisk med et tabelnavn efterfulgt af flere elementer, der starter med en pipe (`|`). I dette eksempel starter vi med at oprette en forening af to tabeller  `DeviceProcessEvents` og `DeviceNetworkEvents`og tilføje pipede elementer efter behov.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```

### <a name="set-the-time-range"></a>Angiv tidsinterval

Det første pipe-element er et tidsfilter, der er beregnet til de forrige syv dage. Hvis du begrænser tidsintervallen, hjælper det med at sikre, at forespørgslerne fungerer godt, returnerer resultater, der kan administreres, og at der ikke opstår timeout.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>Kontrollér bestemte processer

Tidsintervallet efterfølges straks af en søgning efter procesfilnavne, der repræsenterer PowerShell-programmet.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>Søg efter bestemte kommandostrenge

Derefter søger forespørgslen efter strenge i kommandolinjer, der typisk bruges til at downloade filer ved hjælp af PowerShell.

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

Nu, hvor din forespørgsel tydeligt identificerer de data, du vil finde, kan du definere, hvordan resultaterne skal se ud. `project` returnerer bestemte kolonner og `top` begrænser antallet af resultater. Disse operatorer er med til at sikre, at resultaterne er velformateret og forholdsvis store og nemme at behandle.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

Vælg **Kør forespørgsel** for at se resultaterne.

>[!TIP]
>Du kan få vist forespørgselsresultater som diagrammer og hurtigt justere filtre. Du kan få vejledning ved [at læse om at arbejde med forespørgselsresultater](advanced-hunting-query-results.md)



## <a name="learn-common-query-operators"></a>Få mere at vide om almindelige forespørgselsoperatorer

Du har lige kørt din første forespørgsel og har en generel idé om dens komponenter. Det er tid til at bakke lidt op og lære nogle grundlæggende. Det Kusto-forespørgselssprog, der bruges af avanceret jagt, understøtter en række operatorer, herunder følgende almindelige.

| Operatør | Beskrivelse og anvendelse |
|--|--|
| `where` | Filtrer en tabel til delsættet af rækker, der opfylder et prædikat. |
| `summarize` | Producere en tabel, der samler indholdet af inputtabellen. |
| `join` | Flet rækkerne i to tabeller for at danne en ny tabel ved at matche værdierne for de angivne kolonner fra hver tabel. Se [Sammenføjning-tabeller i KQL](https://www.youtube.com/watch?v=8qZx7Pp5XgM) for at få mere at vide.|
| `count` | Returner antallet af poster i inputpostsættet. |
| `top` | Returner de første N-poster sorteret efter de angivne kolonner. |
| `limit` | Vend tilbage til det angivne antal rækker. |
| `project` | Vælg de kolonner, der skal medtages, omdøbes eller slippes, og indsæt nye beregnede kolonner. |
| `extend` | Opret beregnede kolonner, og føj dem til resultatsættet. |
| `makeset` |  Returnerer en dynamisk matrix (JSON) af sættet af entydige værdier, som Udtryk tager i gruppen. |
| `find` | Find rækker, der matcher et prædikat på tværs af et sæt tabeller. |

Hvis du vil se et live eksempel på disse operatorer, skal du køre dem fra afsnittet **Kom i gang** i avanceret jagt.

## <a name="understand-data-types"></a>Forstå datatyper

Avanceret jagt understøtter Kusto-datatyper, herunder følgende almindelige typer:

| Datatype | Beskrivelse og konsekvenser for forespørgsler |
|--|--|
| `datetime` | Data- og tidsoplysninger, der typisk repræsenterer hændelsestidsstempler. [Se understøttede formater for dato/klokkeslæt](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | Tegnstreng i UTF-8 omsluttet af enkelte anførselstegn (`'`) eller dobbelte anførselstegn (`"`). [Læs mere om strenge](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | Denne datatype understøtter `true` eller `false` tilstande. [Se understøttede konstanter og operatorer](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32-bit heltal  |
| `long` | 64-bit heltal |

Du kan få mere at vide om disse datatyper ved at [læse om Kusto-skalardatatyper](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>Få hjælp, når du skriver forespørgsler

Benyt følgende funktionalitet til at skrive forespørgsler hurtigere:
- **Autosuggest** – når du skriver forespørgsler, kommer avanceret jagt med forslag fra IntelliSense. 
- **Skematræ –** en skemarepræsentation, der indeholder listen over tabeller og deres kolonner, er angivet ud for dit arbejdsområde. Du kan få flere oplysninger ved at holde markøren over et element. Dobbeltklik på et element for at indsætte det i forespørgselseditoren.
- **[Skemareference](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** – reference i portalen med tabel- og kolonnebeskrivelser samt understøttede hændelsestyper (`ActionType` værdier) og eksempelforespørgsler

## <a name="work-with-multiple-queries-in-the-editor"></a>Arbejd med flere forespørgsler i editoren

Du kan bruge forespørgselseditoren til at eksperimentere med flere forespørgsler. Sådan bruger du flere forespørgsler:

- Adskil hver forespørgsel med en tom linje.
- Placer markøren på en del af en forespørgsel for at vælge den pågældende forespørgsel, før du kører den. Dette kører kun den valgte forespørgsel. Hvis du vil køre en anden forespørgsel, skal du flytte markøren tilsvarende og vælge **Kør forespørgsel**.

:::image type="content" source="../../media/multiple-queries.png" alt-text="Et eksempel på udførelse af flere forespørgsler på siden **Ny forespørgsel** på Microsoft 365 Defender-portalen" lightbox="../../media/multiple-queries.png":::

Hvis du vil have et mere effektivt arbejdsområde, kan du også bruge flere faner på den samme jagtside. Vælg **Ny forespørgsel** for at åbne en fane til den nye forespørgsel.

:::image type="content" source="../../media/multitab.png" alt-text="Åbning af en ny fane ved at vælge Opret ny i avanceret jagt på Microsoft 365 Defender portalen" lightbox="../../media/multitab.png":::

Du kan derefter køre forskellige forespørgsler uden at åbne en ny browserfane. 

:::image type="content" source="../../media/multitab-examples.png" alt-text="Kør forskellige forespørgsler uden at forlade den avancerede jagtside på Microsoft 365 Defender-portalen" lightbox="../../media/multitab-examples.png":::

>[!NOTE] 
> Hvis du bruger flere browserfaner med avanceret jagt, kan det medføre, at du mister dine forespørgsler, der ikke er gemt. Hvis du vil forhindre dette, skal du bruge fanefunktionen i avanceret jagt i stedet for separate browserfaner.

## <a name="use-sample-queries"></a>Brug eksempelforespørgsler

Afsnittet **Introduktion** indeholder nogle få enkle forespørgsler, der bruger almindeligt anvendte operatorer. Prøv at køre disse forespørgsler og foretage små ændringer af dem.

:::image type="content" source="../../media/get-started-section.png" alt-text="Afsnittet **Introduktion** på siden **Avanceret jagt** på Microsoft 365 Defender-portalen" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>Ud over de grundlæggende forespørgselseksempler kan du også få adgang til [delte forespørgsler](advanced-hunting-shared-queries.md) for specifikke trusselsjagtscenarier. Udforsk de delte forespørgsler i venstre side eller [i GitHub-forespørgselslageret](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>Få adgang til dokumentation til forespørgselssprog

Du kan få flere oplysninger om Kusto-forespørgselssprog og understøttede [operatorer i dokumentationen til Kusto-forespørgselssprog](/azure/kusto/query/).

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender for Endpoint. [Slå Microsoft 365 Defender](m365d-enable.md) til for at jagte trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser for jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i [Overfør avancerede jagtforespørgsler fra Microsoft Defender for Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)