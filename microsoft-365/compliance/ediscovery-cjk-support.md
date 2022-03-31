---
title: Understøttelse af CJK/Double Byte til Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Lær, Advanced eDiscovery sprog Microsoft 365 sprog i Microsoft 365 og Koreansk (CJK), der bruger et dobbelt-byte-tegnsæt.
ms.openlocfilehash: 4c1871eb49754ba93d762989e3cff9c53950d2c6
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63601704"
---
# <a name="cjk-language-support-for-advanced-ediscovery"></a>Understøttelse af CJK-sprog til Advanced eDiscovery

Advanced eDiscovery understøtter dobbelt-byte tegnsætsprog (herunder forenklet kinesisk, traditionelt kinesisk, japansk og koreansk, som under ét er kendt som *CJK-sprog*) til følgende avancerede scenarier i et korrektursæt:

- Når du [forespørger på dataene i et gennemsynssæt](review-set-search.md).

- Når du [mærker dokumenter i et korrektursæt](tagging-documents.md).

- Når du [analyserer sagsdata i et gennemsynssæt](analyzing-data-in-review-set.md) ved hjælp af næsten registrering af dubletter, mailtrådning og temaanalyser.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvordan opretter jeg en søgning for at indsamle elementer, der indeholder CJK-tegn?**

Du kan bruge CJK-tegn [til nøgleordssøgninger](building-search-queries.md#keyword-searches), [nøgleordsforespørgsler](keyword-queries-and-search-conditions.md) og søgebetingelser, når du søger efter indhold Advanced eDiscovery. Søgning efter CJK-tegn understøttes også, når du søger efter indhold i Core eDiscovery og indholdssøgning.

Vi leverer CJK-understøttelse til alle [søgeoperatorer](keyword-queries-and-search-conditions.md#search-operators) og søgebetingelser [, herunder](keyword-queries-and-search-conditions.md#search-conditions) booleske operatorer **AND**, **OR**, **NOT** og **NEAR**.

Hvis du er sikker på, at indholdsplaceringer eller elementer indeholder CJK-tegn, men søgninger ikke returnerer nogen resultater, skal du klikke på ikonet for sprog/område for forespørgslen ![Ikonet Forespørg sprog/område i Indholdssøgning.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) og vælg den tilsvarende sprog-land-kulturkodeværdi for søgningen. Standardsproget/området er neutralt.

**Kan jeg søge efter flere sprog på én gang?**

Det afhænger af dit søgescenarie.

- Når du [forespørger efter data i et](review-set-search.md) gennemsynssæt i Advanced eDiscovery, kan du søge efter flere sprog.

- Når du [opretter en søgning for at indsamle data](create-draft-collection.md), skal du oprette separate samlinger for hvert sprog, du målretter. Hvis du f.eks. søger efter et dokument, der indeholder både kinesisk og koreansk, skal du vælge kinesisk for den første samling og vælge koreansk for den anden samling.

**Jeg kan ikke se forespørgselsikonet sprog/område for at vælge et sprog til forespørgsler i et korrektursæt. Hvordan kan jeg angive et forespørgselssprog i en søgning i et korrektursæt?**

Ved forespørgsler med gennemsynssæt behøver du ikke at angive et dokumentsprog. Advanced eDiscovery registrerer automatisk dokumentsprog, når du føjer indhold til et korrektursæt. Dette hjælper dig med at optimere dine forespørgselsresultater i et korrektursæt.

**Kan jeg se registrerede sprog i [filmetadata](view-documents-in-review-set.md#file-metadata)?**

Nej, du kan ikke se registrerede sprog i filmetadata.

**Kan jeg filtrere efter dokumentsprog i et korrektursæt**?

Nej, du kan ikke filtrere, sortere eller søge efter dokumentsprog i et korrektursæt.

**Vil denne CJK-udgivelse til gennemsynssæt påvirke nogle af mine eksisterende søgninger og korrektursæt?**

Nej, ingen af dine eksisterende søgninger og korrektursæt ændres. Du behøver ikke at genindsøge eksisterende data, og søgeresultater for engelsk tekst vil være de samme.

**Hvordan ændrer jeg visningssproget til kinesisk, japansk eller koreansk?**

Du kan finde oplysninger om, hvordan du ændrer visningssprog og tidszone, under Sådan angives [indstillinger for sprog og område for Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Kendte problemer

- OCR understøtter ikke CJK-tegn fra billedfiler

- Mailfiler (f.eks. *.eml og *.msg) i [visningen Anmærkninger](view-documents-in-review-set.md#annotate-view) understøttes ikke for CJK-sprog.

- Fremhævning af søge [hit i tekstvisning](view-documents-in-review-set.md#text-view) understøttes ikke for CJK-sprog.

- Det [relevansmodul,](using-relevance.md) der bruges til at analysere data, understøtter ikke CJK-sprog.

- [Forespørgselsbaserede ventende](managing-holds.md#manage-non-custodial-holds) funktioner understøttes ikke for CJK-sprog.