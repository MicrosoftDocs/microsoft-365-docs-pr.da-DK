---
title: Forespørg om indholdet i et korrektursæt
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvordan du opretter og kører en forespørgsel i et korrektursæt for at organisere indhold for at få en mere effektiv korrektur i en Microsoft Purview eDiscovery-sag (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 44f4b9d6aed92a6593f5c6c70322656e4c770c3d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090911"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Forespørg om og filtrer indhold i et valideringssæt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I de fleste tilfælde vil det være nyttigt at gå dybere ned i indholdet i et anmeldelsessæt og organisere det for at lette en mere effektiv korrektur. Brug af filtre og forespørgsler i et korrektursæt hjælper dig med at fokusere på et undersæt af dokumenter, der opfylder kriterierne i din anmeldelse.

## <a name="default-filters"></a>Standardfiltre

I et korrektursæt er der fem standardfiltre, der forudindlæses i korrektursættet:

- Søgeord
- Dato
- Afsender/forfatter
- Emne/titel
- Tags

![Standardfiltertyper.](../media/DefaultFilterTypes.png)

Klik på hvert filter for at udvide det og tildele en værdi. Klik uden for filteret for automatisk at anvende filteret på korrektursættet. På følgende skærmbillede kan du se filteret Dato, der er konfigureret til at vise dokumenter inden for et datointerval.

![Standardfilteret er udvidet.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Tilføj eller fjern filtre

Hvis du vil tilføje eller fjerne filtre, der vises for korrektursættet, skal du vælge **Filtre** for at åbne filterpanelet, som vises på en pop op-side. 

![Filterpanel.](../media/FilterPanel.png)

De tilgængelige filtre er organiseret i fire afsnit:

- **Søg**: Filtre, der indeholder forskellige søgefunktioner.

- **Analyse & forudsigende kodning**: Filtre for egenskaber, der genereres og føjes til dokumenter, når du kører **& mailanalysejob** eller bruger forudsigende kodningsmodeller.

- **Id'er**: Filtre for alle id-egenskaber for dokumenter.

- **Elementegenskaber**: Filtre for dokumentegenskaber. 

Udvid hver sektion, og vælg eller fjern markeringen af filtre for at tilføje eller fjerne dem i filtersættet. Når du tilføjer et filter, vises det i filtersættet. 

![Liste over filtersektioner og egenskaber i filterpanelet.](../media/FilterPanel2.png)

> [!NOTE]
> Når du udvider en sektion i filterpanelet, kan du se, at standardfiltertyperne er valgt. Du kan beholde disse markerede eller fravælge dem og fjerne dem fra filtersættet. 

## <a name="filter-types"></a>Filtertyper

Alle søgbare felter i et korrektursæt har et tilsvarende filter, som du kan bruge til filterelementer, der er baseret på et bestemt felt.

Der er flere typer filtre:

- **Fritekst**: Der anvendes et tekstfilter på tekstfelter, f.eks. "Emne". Du kan angive flere søgeord ved at adskille dem med et komma.

- **Dato**: Der bruges et datofilter til datofelter, f.eks. "Dato for seneste ændring".

- **Søgeindstillinger**: Et filter til søgeindstillinger indeholder en liste over mulige værdier (hver værdi vises med et afkrydsningsfelt, som du kan markere) for bestemte felter i gennemsynet. Dette filter bruges til felter, f.eks. "Afsender", hvor der er et begrænset antal mulige værdier i korrektursættet.

- **Nøgleord**: En nøgleordsbetingelse er en bestemt forekomst af fritekstbetingelse, som du kan bruge til at søge efter ord. Du kan også bruge KQL-lignende forespørgselssprog i denne filtertype. Du kan få flere oplysninger i afsnittene Forespørgselssprog og Avanceret forespørgselsgenerator i denne artikel.

## <a name="include-and-exclude-filter-relationships"></a>Medtag og udelad filterrelationer

Du kan ændre relationen "include" og "udelad" for et bestemt filter. I kodefilteret kan du f.eks. udelade elementer, der er mærket med en bestemt kode, ved at vælge **Er lig med ingen af** i rullelistefilteret. 

![Udelad kodefilter.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Gem filtre som forespørgsler

Når du er tilfreds med dine filtre, kan du gemme filterkombinationen som en filterforespørgsel. Dette giver dig mulighed for at anvende filteret i fremtidige gennemgangssessioner.

Hvis du vil gemme et filter, skal du vælge **Gem forespørgslen** og navngive den. Du eller andre korrekturlæsere kan køre tidligere gemte filterforespørgsler ved at vælge rullelisten **Gemte filterforespørgsler** og vælge en filterforespørgsel, der skal anvendes til at gennemse sæt dokumenter. 

![Gem en filterforespørgsel.](../media/SaveFilterQuery.png)

Hvis du vil slette en filterforespørgsel, skal du åbne filterpanelet og vælge skraldespandsikonet ud for forespørgslen.

![Slet en filterforespørgsel.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Forespørgselssprog

Ud over at bruge filtre kan du også bruge et KQL-lignende forespørgselssprog i filteret Nøgleord til at oprette søgeforespørgslen for dit korrektursæt. Forespørgselssproget for forespørgsler, der er angivet til gennemsyn, understøtter booleske standardoperatorer, f.eks. **AND**, **OR**, **NOT** og **NEAR**. Den understøtter også et jokertegn med et enkelt tegn (?) og et jokertegn med flere tegn (*).

## <a name="advanced-query-builder"></a>Avanceret forespørgselsgenerator

Du kan også oprette mere avancerede forespørgsler for at søge efter dokumenter i et korrektursæt.

1. Åbn filterpanelet, vælg **Filtre**, og udvid sektionen **Søg** .

  ![Tilføj et KQL-filter.](../media/AddKQLFilter.png)

2. Vælg **KQL-filteret,** og klik på **Åbn forespørgselsgenerator**.

   I dette panel kan du oprette komplekse KQL-forespørgsler ved hjælp af forespørgselsgeneratoren. Du kan tilføje betingelser eller tilføje betingelsesgrupper, der består af flere betingelser, som er logisk forbundet af **RELATIONER AF TYPEN AND** eller **OR** .

   ![Brug Forespørgselsgenerator til at konfigurere komplekse filterforespørgsler.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Filtrer delvist indekserede elementer

Hvis du har valgt indstillingen for at tilføje delvist indekserede elementer fra flere datakilder, når du har gemt kladdesamlingen i et gennemsynssæt. Du vil sandsynligvis gerne identificere og få vist disse elementer for at afgøre, om et element kan være relevant for din undersøgelse, og om du skal afhjælpe den fejl, der resulterede i, at elementet blev delvist indekseret.

På nuværende tidspunkt er der ikke en filterindstilling i en korrektur, der er angivet til at vise delvist indekserede elementer. Men vi arbejder på det. Indtil da kan du filtrere og få vist de delvist indekserede elementer, som du har føjet til et korrektursæt.

1. Opret en samling, og send den til et nyt korrektursæt *uden* at tilføje delvist indekserede elementer fra de yderligere datakilder.

2. Opret en ny samling ved at kopiere samlingen fra trin 1.

3. Send den nye samling til det samme korrektursæt. Men denne gang skal du tilføje de delvist indekserede elementer fra de yderligere datakilder. Da elementer fra den samling, du oprettede i trin 1, allerede er føjet til korrektursættet, er det kun de delvist indekserede elementer fra den anden samling, der føjes til korrektursættet.

4. Når begge samlinger er føjet til korrektursættet, skal du gå til korrektursættet og vælge **AdministrerIndlæs** >  sæt.

5. Kopiér eller notér **indlæsnings-id'et** for den anden samling (den, du oprettede i trin 2). Samlingens navn identificeres i kolonnen **Kildeoplysninger** .

6. Tilbage i korrektursættet skal du klikke på **Filter**, udvide sektionen **Id'er** og derefter markere afkrydsningsfeltet **Indlæs id** .

7. Udvid filteret **Indlæs id** , og markér derefter afkrydsningsfeltet for det indlæsnings-id, der svarer til den anden samling, for at få vist de delvist indekserede elementer.
