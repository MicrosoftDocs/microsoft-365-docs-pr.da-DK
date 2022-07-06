---
title: CJK/Double Byte-understøttelse af eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan Microsoft Purview eDiscovery (Premium) i Microsoft 365 understøtter sprogene kinesisk, japansk og koreansk (CJK), som bruger et dobbeltbytetegnsæt.
ms.openlocfilehash: a16f1f63deee7cbc77b105c9c49431a8eeda0e71
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636199"
---
# <a name="cjk-language-support-for-ediscovery-premium"></a>CJK-sprogunderstøttelse til eDiscovery (Premium)

Microsoft Purview eDiscovery (Premium) understøtter sprog med dobbeltbytetegnsæt (disse omfatter forenklet kinesisk, traditionelt kinesisk, japansk og koreansk, som tilsammen kaldes *CJK-sprog*) for følgende avancerede scenarier i et korrektursæt:

- Når du [forespørger dataene i et korrektursæt](review-set-search.md).

- Når du [mærker dokumenter i et korrektursæt](tagging-documents.md).

- Når du [analyserer sagsdata i en anmeldelse, der er angivet](analyzing-data-in-review-set.md) ved hjælp af næsten registrering af dubletter, mailtråde og temaanalyser.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvordan gør jeg oprette en søgning for at indsamle elementer, der indeholder CJK-tegn?**

Du kan bruge CJK-tegn til [nøgleordssøgninger](building-search-queries.md#keyword-searches), [nøgleordsforespørgsler og søgebetingelser](keyword-queries-and-search-conditions.md) , når du søger efter indhold i eDiscovery (Premium). Søgning efter CJK-tegn understøttes også, når du søger efter indhold i Microsoft Purview eDiscovery (Standard) og indholdssøgning.

Vi understøtter CJK for alle [søgeoperatorer](keyword-queries-and-search-conditions.md#search-operators) og [søgebetingelser](keyword-queries-and-search-conditions.md#search-conditions), herunder de booleske operatorer **AND**, **OR**, **NOT** og **NEAR**.

Hvis du er sikker på, at indholdsplaceringer eller elementer indeholder CJK-tegn, men søgninger ikke returnerer nogen resultater, skal du klikke på ikonet sprog/land/område for forespørgslen ![Ikonet Forespørg om sprog-land/område i Indholdssøgning.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) og vælg den tilsvarende kodeværdi for sprog/land-kultur for søgningen. Standardsproget/-området er neutralt.

**Kan jeg søge efter flere sprog på én gang?**

Det afhænger af dit søgescenarie.

- Når du [forespørger om data i et korrektursæt](review-set-search.md) i eDiscovery (Premium), kan du søge efter flere sprog.

- Når du [opretter en søgning for at indsamle data](create-draft-collection.md), skal du oprette separate samlinger for hvert sprog, du målretter mod. Hvis du f.eks. søger efter et dokument, der indeholder både kinesisk og koreansk, skal du vælge Kinesisk for din første samling og vælge Koreansk for din anden samling.

**Jeg kan ikke se ikonet for forespørgselssprog-land/område for at vælge et sprog til forespørgsler i et korrektursæt. Hvordan kan jeg angive et forespørgselssprog i en søgning i et gennemsynssæt?**

I forbindelse med forespørgsler, der er angivet for gennemsyn, behøver du ikke at angive et dokumentsprog. eDiscovery (Premium) registrerer automatisk dokumentsprog, når du føjer indhold til et korrektursæt. Dette hjælper dig med at optimere dine forespørgselsresultater i et korrektursæt.

**Kan jeg se registrerede sprog i [filmetadata](view-documents-in-review-set.md#file-metadata)?**

Nej, du kan ikke se registrerede sprog i filmetadata.

**Kan jeg filtrere efter dokumentsprog i et korrektursæt**?

Nej, du kan ikke filtrere, sortere eller søge efter dokumentsprog i et korrektursæt.

**Vil denne CJK-version til scenarier med gennemgangssæt påvirke nogen af mine eksisterende søgninger og korrektursæt?**

Nej, ingen af dine eksisterende søgninger og korrektursæt ændres. Du behøver ikke at omdexere eksisterende data, og søgeresultater for engelsk tekst vil være de samme.

**Hvordan gør jeg ændre mit visningssprog til kinesisk, japansk eller koreansk?**

Du kan få oplysninger om, hvordan du ændrer visningssprog og tidszone, under [Sådan angiver du indstillinger for sprog og område for Office 365](/office365/troubleshoot/access-management/set-language-and-region).

## <a name="known-issues"></a>Kendte problemer

- OCR understøtter ikke CJK-tegn fra billedfiler

- Mailfiler (f.eks. *.eml og *.msg) i [Anmærk visning](view-documents-in-review-set.md#annotate-view) understøttes ikke for CJK-sprog.

- Fremhævning af søgeresultat i [tekstvisning](view-documents-in-review-set.md#text-view) understøttes ikke for CJK-sprog.

- Det [relevansmodul](using-relevance.md) , der bruges til at analysere data, understøtter ikke CJK-sprog.

- [Forespørgselsbaserede ventepositioner](managing-holds.md#manage-non-custodial-holds) understøttes ikke for CJK-sprog.