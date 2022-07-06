---
title: Afhjælpning af fejl med et enkelt element
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.assetid: ''
description: Du kan rette en behandlingsfejl i et dokument i et gennemsynssæt i eDiscovery (Premium) uden at skulle følge massefejlafhjælpningsprocessen.
ms.openlocfilehash: cb1b7248ff02a4aafce529b764efdf7408a05386
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622167"
---
# <a name="single-item-error-remediation-in-ediscovery-premium"></a>Afhjælpning af fejl i enkelt element i eDiscovery (Premium)

Fejlafhjælpning giver Microsoft Purview eDiscovery (Premium) brugere mulighed for at rette dataproblemer, der forhindrer eDiscovery (Premium) i at behandle indholdet korrekt. Filer, der er beskyttet med adgangskode, kan f.eks. ikke behandles, fordi disse filer er låst eller krypteret. Tidligere kunne du kun løse flere fejl ved hjælp af [denne arbejdsproces](error-remediation-when-processing-data-in-advanced-ediscovery.md). Men nogle gange giver det ikke mening at afhjælpe fejl i flere filer, når du er usikker på, om nogen af disse filer reagerer på den sag, du undersøger. Det giver muligvis heller ikke mening at afhjælpe fejl, før du har haft mulighed for at gennemse filmetadata (f.eks. filplacering, eller hvem der havde adgang) for at hjælpe dig med at træffe de første beslutninger om svartid. En ny funktion, der kaldes *afhjælpning af fejl med enkelt element* , giver eDiscovery-ledere mulighed for at få vist metadataene for filer med en behandlingsfejl og om nødvendigt afhjælpe fejlen direkte i korrektursættet. I artiklen beskrives det, hvordan du identificerer, ignorerer og afhjælper filer med behandlingsfejl i et korrektursæt.

## <a name="identify-documents-with-errors"></a>Identificer dokumenter med fejl

Dokumenter med behandlingsfejl i et korrektursæt identificeres nu (med et banner). Du kan afhjælpe eller ignorere fejlen. På følgende skærmbillede vises banneret med behandlingsfejl for et Word-dokument i et korrektursæt, der er beskyttet med adgangskode. Bemærk også, at du kan få vist filmetadata for dokumenter med behandlingsfejl.

![Banner, der vises for dokument med behandlingsfejl.](../media/SIERimage1.png)

Du kan også søge efter dokumenter, der har behandlingsfejl, ved hjælp af **statusbetingelsen Behandling** , når du [forespørger dokumenterne i et gennemsynssæt](review-set-search.md).

![Brug statusbetingelsen Behandling til at søge efter fejldokumenter.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Ignorer fejl

Du kan ignorere en behandlingsfejl ved at klikke på **Ignorer** i behandlingsfejlbanneret. Når du ignorerer en fejl, fjernes dokumentet fra arbejdsprocessen for [afhjælpning af massefejl](error-remediation-when-processing-data-in-advanced-ediscovery.md). Når en fejl ignoreres, skifter dokumentbanneret farve og angiver, at behandlingsfejlen blev ignoreret. Du kan når som helst gendanne beslutningen om at ignorere fejlen ved at klikke på **Genindlæs**.

![Klik på Ignorer for at ignorere behandlingsfejlen.](../media/SIERimage3.png)

Du kan også søge efter alle dokumenter, der havde en behandlingsfejl, som blev ignoreret, ved hjælp af betingelsen *Ignoreret behandlingsfejl* under forespørgsler om dokumenter i et korrektursæt.

![Brug betingelsen Ignoreret behandlingsfejl til at søge efter ignorerede fejldokumenter.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Afhjælp et dokument med fejl

Nogle gange kan du blive bedt om at afhjælpe en behandlingsfejl i dokumenter (ved at fjerne en adgangskode, dekryptere en krypteret fil eller genoprette et beskadiget dokument) og derefter føje det afhjælpede dokument til korrektursættet. Det giver dig mulighed for at gennemse og eksportere fejldokumentet sammen med de andre dokumenter i korrektursættet. 

Følg disse trin for at afhjælpe et enkelt dokument:

1. Klik på **Hent** > **original** for at hente en kopi af filen til en lokal computer.

   ![Download dokumentet med behandlingsfejlen.](../media/SIERimage5.png)

2. Afhjælp fejlen i filen offline. For krypterede filer, der kræver dekrypteringssoftware, for at fjerne adgangskodebeskyttelse, skal du enten angive adgangskoden og gemme filen eller bruge en adgangskode krakker. Når du har afhjælpet filen, skal du gå til næste trin.

3. I korrektursættet skal du vælge filen med den behandlingsfejl, du har løst, og derefter klikke på **Afhjælpning**.

   ![Klik på Afhjælpning i banneret for dokumentet med behandlingsfejl.](../media/SIERimage6.png)


4. Klik på **Gennemse**, gå til placeringen af den afhjælpede fil på din lokale computer, og vælg derefter filen.

   ![Klik på Gennemse, og vælg den afhjælpede fil på din lokale computer.](../media/SIERimage7.png)

    Når du har valgt den afhjælpede fil, uploades den automatisk til korrektursættet. Du kan spore filens behandlingsstatus.

    ![Status for afhjælpningsprocessen vises.](../media/SIERimage8.png)

   Når behandlingen er fuldført, kan du få vist det afhjælpede dokument.

    ![Du kan få vist den afhjælpede fil i det oprindelige format i korrektursættet.](../media/SIERimage9.png)

Du kan få flere oplysninger om, hvad der sker, når et dokument afhjælpes, under [Hvad sker der, når filer afhjælpes](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated).

## <a name="search-for-remediated-documents"></a>Søg efter afhjælpede dokumenter

Du kan søge efter alle dokumenter i et korrektursæt, der blev afhjælpet, ved hjælp af betingelsen **Nøgleord** og angive følgende egenskab:værdipar: **IsFromErrorRemediation:true**. Denne egenskab er også tilgængelig i eksportindlæsningsfilen, når du eksporterer dokumenter fra et gennemsynssæt.
