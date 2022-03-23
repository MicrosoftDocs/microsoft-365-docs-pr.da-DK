---
title: Forespørge om indholdet i et korrektursæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om, hvordan du opretter og kører en forespørgsel i et gennemsynssæt for at organisere indhold til en mere effektiv gennemgang Advanced eDiscovery en sag.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ebcb129241565321297b78072a5d02d173552ee1
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63588967"
---
# <a name="query-and-filter-content-in-a-review-set"></a>Forespørg og filtrer indhold i et korrektursæt

I de fleste tilfælde kan det være nyttigt at grave dybere ned i indholdet i et korrektursæt og organisere det for at muliggøre en mere effektiv gennemgang. Brug af filtre og forespørgsler i et korrektursæt hjælper dig med at fokusere på et undersæt af dokumenter, der opfylder kriterierne i din gennemgang.

## <a name="default-filters"></a>Standardfiltre

I et korrektursæt er der fem standardfiltre, der er forudinstalleret i korrektursættet:

- Nøgleord
- Dato
- Afsender/forfatter
- Emne/titel
- Mærker

![Standardfiltertyper.](../media/DefaultFilterTypes.png)

Klik på hvert filter for at udvide det og tildele en værdi. Klik uden for filteret for automatisk at anvende filteret på korrektursættet. Følgende skærmbillede viser det datofilter, der er konfigureret til at vise dokumenter inden for et datointerval.

![Standardfilter udvidet.](../media/ExpandedFilter.png)

## <a name="add-or-remove-filters"></a>Tilføje eller fjerne filtre

Hvis du vil tilføje eller fjerne filtre, der vises for korrektursættet,  skal du vælge Filtre for at åbne filterpanelet, som vises på en side med pop op-vinduer. 

![Filterpanel.](../media/FilterPanel.png)

De tilgængelige filtre er organiseret i fire sektioner:

- **Søg**: Filtre, der giver forskellige søgefunktioner.

- **Analyseværktøjer & forudsigelig** kodning: Filtre for egenskaber, der genereres og føjes til dokumenter, når du kører **dokumentanalysejobbet &** eller bruger forudsigelige kodningsmodeller.

- **Id'er**: Filtrerer for alle dokumenters id-egenskaber.

- **Elementegenskaber**: Filtre til dokumentegenskaber. 

Udvid hver sektion, og vælg eller fravælg filtre for at tilføje eller fjerne dem i filtersættet. Når du tilføjer et filter, vises det i filtersættet. 

![Liste over filters sektioner og egenskaber i filterpanelet.](../media/FilterPanel2.png)

> [!NOTE]
> Når du udvider en sektion i filterpanelet, vil du bemærke, at standardfiltertyperne er valgt. Du kan beholde disse valgte eller fjerne markeringen af dem og fjerne dem fra filtersættet. 

## <a name="filter-types"></a>Filtertyper

Alle søgbare felter i et korrektursæt har et tilsvarende filter, som du kan bruge til at filtrere elementer baseret på et bestemt felt.

Der findes flere typer filtre:

- **Freetext**: Der anvendes et freetext-filter på tekstfelter som f.eks. "Emne". Du kan få vist flere søgeord ved at adskille dem med et komma.

- **Dato**: Der bruges et datofilter til datofelter som f.eks. "Dato for seneste ændring".

- **Søgeindstillinger**: Et filter for søgeindstillinger indeholder en liste over mulige værdier (hver værdi vises med et afkrydsningsfelt, som du kan vælge) for bestemte felter i anmeldelsen. Dette filter bruges til felter, f.eks. "Afsender", hvor der er et begrænset antal mulige værdier i korrektursættet.

- **Nøgleord**: En betingelse for nøgleordet er en bestemt forekomst af freetext-betingelse, som du kan bruge til at søge efter ord. Du kan også bruge KQL-lignende forespørgselssprog i denne type filter. Du kan finde flere oplysninger i afsnittene Forespørgselssprog og Avanceret forespørgselsgenerator i denne artikel.

## <a name="include-and-exclude-filter-relationships"></a>Medtag og udelad filterrelationer

Du kan ændre relationen medtag og udelade for et bestemt filter. I mærkefilteret kan du f.eks. udelade elementer, der er mærket med et bestemt mærke, ved  at vælge Er lig med ingen i rullefilteret. 

![Udelad kodefilter.](../media/TagFilterExclude.png)

## <a name="save-filters-as-queries"></a>Gemme filtre som forespørgsler

Når du er tilfreds med dine filtre, kan du gemme filterkombinationen som en filterforespørgsel. Dette giver dig mulighed for at anvende filteret i fremtidige gennemgangssessioner.

Hvis du vil gemme et filter, skal **du vælge Gem forespørgslen og** navngive den. Du eller andre korrekturlæsere kan køre tidligere gemte filterforespørgsler ved  at vælge rullelisten Gemte filterforespørgsler og vælge en filterforespørgsel, der skal anvendes til at gennemse sæt dokumenter. 

![Gemme en filterforespørgsel.](../media/SaveFilterQuery.png)

Hvis du vil slette en filterforespørgsel, skal du åbne filterpanelet og vælge ikonet for papirkurven ud for forespørgslen.

![Slette en filterforespørgsel.](../media/DeleteFilterQuery.png)

## <a name="query-language"></a>Forespørgselssprog

Ud over at bruge filtre kan du også bruge et KQL-lignende forespørgselssprog i filteret Nøgleord til at opbygge din søgeforespørgsel for korrektursæt. Forespørgselssproget for gennemsynssætforespørgsler understøtter standard booleske operatorer, f.eks. **OG**, **ELLER**, **IKKE** og **NEAR**. Den understøtter også et jokertegn (?) med et enkelt tegn og et jokertegn med flere tegn (*).

## <a name="advanced-query-builder"></a>Avanceret forespørgselsgenerator

Du kan også oprette mere avancerede forespørgsler til at søge efter dokumenter i et korrektursæt.

1. Åbn filterpanelet, vælg **Filtre**, og udvid **sektionen** Søg.

  ![Tilføj et KQL-filter.](../media/AddKQLFilter.png)

2. Vælg **KQL-filteret** , og klik på **Åbn forespørgselsgenerator**.

   I dette panel kan du oprette komplekse KQL-forespørgsler ved hjælp af forespørgselsgeneratoren. Du kan tilføje betingelser eller tilføje betingelsesgrupper, der består af flere betingelser, der er logisk forbundet **med OG** - **eller ELLER-relationer** .

   ![Brug forespørgselsgenerator til at konfigurere komplekse filterforespørgsler.](../media/ComplexQuery.png)

## <a name="filter-partially-indexed-items"></a>Filtrere delvist indekserede elementer

Hvis du har valgt at tilføje delvist indekserede elementer fra flere datakilder, når du har forpligtet kladdesamlingen til et gennemsynssæt. Du vil sandsynligvis identificere og få vist disse elementer for at afgøre, om et element kan være relevant for din undersøgelse, og om du er nødt til at løse den fejl, der resulterede i, at elementet blev delvist indekseret.

På nuværende tidspunkt er der ikke en filterindstilling i et korrektursæt, der viser delvist indekserede elementer. Men vi arbejder på det. Indtil da er her en metode til at filtrere og få vist de delvist indekserede elementer, du har føjet til et korrektursæt.

1. Opret en samling, og bestil den til et nyt *korrektursæt uden* at tilføje delvist indekserede elementer fra de ekstra datakilder.

2. Opret en ny samling ved at kopiere samlingen fra trin 1.

3. Bestil den nye samling til det samme korrektursæt. Men denne gang skal du tilføje de delvist indekserede elementer fra de ekstra datakilder. Da elementer fra samlingen, du oprettede i trin 1, allerede er blevet føjet til korrektursættet, er det kun de delvist indekserede elementer fra den anden samling, der føjes til gennemsynssættet.

4. Når begge samlinger er føjet til korrektursættet, skal du gå til korrektursættet og vælge **ManageLoad-sæt** > .

5. Kopiér eller notér **indlæsnings-id'et** for den anden samling (det, du oprettede i trin 2). Navnet på samlingen identificeres i **kolonnen Kildeoplysninger** .

6. Tilbage i korrektursættet skal du **klikke på Filter**, udvide sektionen **Id'er** og derefter markere **afkrydsningsfeltet Indlæs** id.

7. Udvid **filteret Indlæs** id, og markér derefter afkrydsningsfeltet for det indlæsnings-id, der svarer til den anden samling, for at få vist de delvist indekserede elementer.
