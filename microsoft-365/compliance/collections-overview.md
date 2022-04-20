---
title: Oversigt over samlinger i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Brug samlinger i eDiscovery (Premium) til at søge efter og indsamle indhold, der er i forhold til din sag eller undersøgelse.
ms.openlocfilehash: 8831508260d48dc270a5e4b7a15cecf894656ff6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940263"
---
# <a name="learn-about-collections-in-ediscovery-premium"></a>Få mere at vide om samlinger i eDiscovery (Premium)

Når organisationer står over for at indsamle den kommunikation og det indhold, der kan være relevant for en undersøgelse eller potentiel procesførelse, står de over for en betydelig udfordring under de bedste omstændigheder. På nutidens moderne arbejdsplads muliggør indholdsmængden, variationen og hastigheden innovation og fjernarbejde, samtidig med at kravene til og processen til administration af samlinger til eDiscovery-undersøgelser udvides.

Arbejdsprocessen for samling udgør betydelige tekniske udfordringer i forbindelse med udtrækning af indhold fra oprindelige placeringer og kilder. Det er også et kritisk punkt i vurderingen og strategien for almindelige retssager eller efterforskningsscenarier. I takt med at organisationer begynder at vurdere en undersøgelse, er de første spørgsmål, der blev stillet, hvem der var involveret? Efter at have identificeret, hvem der var involveret, kan disse tilsynsførende hurtigt sættes i venteposition for at bevare relevant indhold. Det næste spørgsmål er, hvad der fandt sted? For at besvare dette andet grundlæggende spørgsmål om enhver undersøgelse skal ledere henvende sig til dataene. For hurtigt at vurdere det mest relevante indhold i spørgsmålet om, hvad der fandt sted, begynder lederne at finjustere målet for spørgsmålet for at sikre, at indsamlingsresultaterne er omfattende uden at være for brede.

Samlinger i eDiscovery (Premium) hjælper eDiscovery-ledere med hurtigt at søge efter indhold på tværs af mail, dokumenter og andet indhold i Microsoft 365. Samlinger giver ledere et estimat af det indhold, der kan være relevant for sagen. Dette giver ledere mulighed for hurtigt at træffe velunderbyggede beslutninger om størrelsen og omfanget af indhold, der er relevant for en sag. eDiscovery-ledere kan oprette en samling til at søge i datakilder med frihedsberøvelse (f.eks. postkasser og SharePoint websteder) og ved hjælp af specifikke søgekriterier (f.eks. nøgleord og datointervaller) for hurtigt at definere omfanget af deres samling.

Når samlingen er defineret, kan eDiscovery-ledere gemme samlingen som en kladde og hente estimater, herunder estimater for datamængde, de indholdsplaceringer, der indeholder resultater, og antallet af forekomster for betingelsen for søgeforespørgslen. Disse indsigter kan hjælpe med at informere om, om samlingen skal revideres for at indsnævre eller udvide omfanget af samlingen, før du går videre med gennemgangs- og analysefaserne i eDiscovery-arbejdsprocessen.

Når lederen er tilfreds med omfanget af samlingen og den anslåede indholdsmængde, der sandsynligvis vil være dynamisk, kan lederen tilføje eller *bekræfte* indholdet til et korrektursæt. Når en samling bindes til et anmeldelsessæt, har denne leder også mulighed for at inkludere chatsamtaler, vedhæftede filer i skyen og dokumentversioner. Indholdet i samlingen gennemgår også et andet niveau af behandling under indtagelse i anmeldelsessættet. og samlingen opdateres med den endelige samlingsoversigt. Når indhold er føjet til korrektursættet, kan eDiscovery-ledere fortsætte med at forespørge, gruppere og tilpasse indholdet i for at hjælpe med minimering og gennemsyn. Derudover opdateres samlingen med oplysninger og statistikker om det indhold, der er anvendt i korrektursættet. Dette indeholder en historisk reference om indholdet i samlingen.

Med udgivelsen af samlinger i en eDiscovery -sag (Premium) er fanen **Søgninger** blevet omdøbt til **Samlinger** i en eDiscovery-sag (Premium) på Microsoft Purview-overholdelsesportalen. Trinnene til at definere omfanget og størrelsen af samlingen følger samme proces som søgning for at definere placeringer og betingelser. Gem som kladde, og få eksempelestimater giver mulighed for hurtig validering af målrettet omfang af samlinger, før der indgås en komplet søgning og samling i korrektursættet. Dette giver mulighed for forbedret jobstyring og målrettede gentagelser, så du begynder at minimere indholdet under søge- og samlingsprocessen.

## <a name="collections-workflow"></a>Arbejdsproces for samlinger

Her er en grundlæggende arbejdsproces og beskrivelser af hvert trin i processen for at komme i gang med at bruge samlinger i eDiscovery (Premium).

![Arbejdsproces for samlinger i eDiscovery (Premium).](../media/CollectionsWorkflow.png)

1. **Opret og kør en kladdesamling**. Det første trin er at oprette en kladde til indsamling og definere de datakilder med frihedsberøvelse og ingen frihedsberøvelse, der skal søges efter. Du kan også søge i andre datakilder, der ikke er føjet til sagen. Når du har tilføjet datakilderne, kan du konfigurere søgeforespørgslen til at søge i datakilderne efter indhold, der er relevant for sagen. Du kan bruge nøgleord, egenskaber og betingelser til at oprette søgeforespørgsler, der returnerer indhold, der sandsynligvis er mest relevant for sagen. Du kan få flere oplysninger under [Opret en kladdesamling](create-draft-collection.md).

2. **Gennemse estimater og statistikker**. Når du har oprettet en kladdesamling og kørt den, er det næste trin at få vist statistik for samlingen for at hjælpe dig med at kontrollere, om der findes relevant indhold, og om indholdsplaceringerne med flest forekomster. Du kan også få vist et eksempel på søgeresultaterne for yderligere at hjælpe dig med at afgøre, om indholdet er inden for rammerne af din undersøgelse. Du kan få flere oplysninger under [Statistik og rapporter for kladdesamlinger](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).

3. **Rediger og kør en kladdesamling igen**. På baggrund af de estimater og statistikker, der returneres af samlingen, kan du redigere kladdesamlingen ved at ændre de datakilder, der søges i, og søgeforespørgslen for at udvide eller indsnævre samlingen. Du kan opdatere og køre kladdesamlingen igen, indtil du er sikker på, at samlingen indeholder det indhold, der er mest relevant for din sag.

4. **Send en kladdesamling til et korrektursæt**. Når du er overbevist om, at samlingen returnerer det typeindhold, der er relevant for sagen, kan du bekræfte samlingen til korrektursættet. Når du sender en samling, har du mulighed for at føje samtaletråde, vedhæftede filer i skyen og dokumentversioner til korrektursættet, hvilket alt sammen kan være relevant for sagen.

   Når du sender en samling, udtrækkes underordnede elementer, f.eks. mailsignaturer og billeder, fra et overordnet element (f.eks. en mail, en chatbesked eller et dokument) og behandles derefter af OPTISK tegngenkendelse (OCR) for at udtrække tekst fra det underordnede element. Tekst, der er udtrukket fra underordnede elementer, føjes derefter til det overordnede element, så du kan få den vist i korrektursættet. Hvis du ikke føjer underordnede elementer til korrektursættet som en separat fil, hjælper eDiscovery (Premium) med at begrænse antallet af potentielt immaterielle elementer, der føjes til korrektursættet. Du kan få flere oplysninger om, hvordan underordnede elementer håndteres, under [Indsamlingsstatistik og -rapporter](collection-statistics-reports.md#collection-contents).

   Du kan få flere oplysninger under [Send en kladdesamling til et gennemsynssæt](commit-draft-collection.md).

5. **Gennemse oversigt over samlinger og statistikker**. Når du har sendt en samling til et gennemsynssæt, bevares oplysninger om samlingen, f.eks. statistikker om udtrukne elementer, dyb indeksering, den søgeforespørgsel, der bruges til samlingen, og de indholdsplaceringer, som elementer blev indsamlet fra. Bekræftede samlinger kan heller ikke redigeres eller køre igen. Du kan kun kopiere eller slette dem. Bevarelse af samlinger giver en oversigtspost over de indsamlede elementer, der blev føjet til et korrektursæt. Du kan få flere oplysninger under [Statistik og rapporter for bekræftede samlinger](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).
