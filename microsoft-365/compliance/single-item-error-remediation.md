---
title: Afhjælpning af fejl i et enkelt element
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Du kan løse en behandlingsfejl i et dokument i et gennemsynssæt i Advanced eDiscovery uden at skulle følge massefejlrettelsesprocessen.
ms.openlocfilehash: c816ef1e3fd28299bb316e51aa434a8f08d544a0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588977"
---
# <a name="single-item-error-remediation-in-advanced-ediscovery"></a>Afhjælpning af fejl i et enkelt element i Advanced eDiscovery

Fejl afhjælpning giver Advanced eDiscovery mulighed for at udbedre dataproblemer, der Advanced eDiscovery i at behandle indholdet korrekt. Filer, der er beskyttet med adgangskode, kan f.eks. ikke behandles, fordi disse filer er låst eller krypteret. Tidligere kunne du kun løse fejl flere gange ved hjælp af [denne arbejdsproces](error-remediation-when-processing-data-in-advanced-ediscovery.md). Nogle gange giver det ikke mening at løse fejl i flere filer, når du ikke er sikker på, om nogen af disse filer reagerer på den sag, du undersøger. Det giver heller ikke mening at løse fejl, før du har haft mulighed for at gennemse filens metadata (f.eks. filplacering eller hvem der havde adgang) for at hjælpe dig med at træffe direkte beslutninger om svarighed. En ny funktion kaldet  afhjælpning af en enkelt fejl giver eDiscovery-ledere mulighed for at få vist metadataene for filer med en behandlingsfejl og om nødvendigt løse fejlen direkte i gennemsynssættet. Artiklen beskriver, hvordan du identificerer, ignorerer og afhjælper filer med behandlingsfejl i et gennemsynssæt.

## <a name="identify-documents-with-errors"></a>Identificer dokumenter med fejl

Dokumenter med behandlingsfejl i et gennemsynssæt identificeres nu (med et banner). Du kan løse eller ignorere fejlen. Følgende skærmbillede viser banneret til behandlingsfejl for et Word-dokument i et korrektursæt, der er beskyttet med en adgangskode. Bemærk også, at du kan få vist filens metadata for dokumenter med behandlingsfejl.

![Banner vist for dokument med behandlingsfejl.](../media/SIERimage1.png)

Du kan også søge efter dokumenter, der har behandlingsfejl, ved hjælp af tilstanden Behandler **status** , når der forespørges i [dokumenterne i et gennemsynssæt](review-set-search.md).

![Brug statusbetingelse for behandling til at søge efter fejldokumenter.](../media/SIERimage2.png)

### <a name="ignore-errors"></a>Ignorer fejl

Du kan ignorere en behandlingsfejl ved at klikke på **Ignorer** i banneret behandlingsfejl. Når du ignorerer en fejl, fjernes dokumentet fra [arbejdsprocessen til afhjælpning af massefejl](error-remediation-when-processing-data-in-advanced-ediscovery.md). Når en fejl ignoreres, skifter dokumentets bannerfarve og angiver, at behandlingsfejlen blev ignoreret. Du kan når som helst vende tilbage til beslutningen om at ignorere fejlen ved at klikke på **Gendan**.

![Klik på Ignorer for at ignorere behandlingsfejlen.](../media/SIERimage3.png)

Du kan også søge efter alle dokumenter, der havde en behandlingsfejl, der blev ignoreret  ved hjælp af betingelsen Ignoreret behandlingsfejl, når der forespørges om dokumenter i et gennemsynssæt.

![Brug betingelsen Ignoreret behandlingsfejl til at søge efter ignorerede fejldokumenter.](../media/SIERimage4.png)

## <a name="remediate-a-document-with-errors"></a>Løse et dokument med fejl

Nogle gange kan det være nødvendigt at løse en behandlingsfejl i dokumenter (ved at fjerne en adgangskode, dekryptere en krypteret fil eller gendanne et beskadiget dokument) og derefter føje det afhjælpede dokument til korrektursættet. Dette giver dig mulighed for at gennemse og eksportere fejldokumentet sammen med de andre dokumenter i korrektursættet. 

Du kan løse et enkelt dokument ved at følge disse trin:

1. Klik **på** **DownloadDownload** >  original for at downloade en kopi af filen til en lokal computer.

   ![Download dokumentet med behandlingsfejlen.](../media/SIERimage5.png)

2. Afhjulpet fejlen i filen offline. For krypterede filer, der kræver dekrypteringssoftware, for at fjerne adgangskodebeskyttelse, skal du enten angive adgangskoden og gemme filen eller bruge en adgangskode cracker. Når du har løst problemet med filen, skal du gå til næste trin.

3. I korrektursættet skal du vælge filen med den behandlingsfejl, du har løst, og derefter klikke **på Afhjælpning**.

   ![Klik på Afhjælpning i banneret for dokumentet med behandlingsfejl.](../media/SIERimage6.png)


4. Klik **på** Gennemse, gå til placeringen for den afhjælpede fil på din lokale computer, og vælg derefter filen.

   ![Klik på Gennemse, og vælg den afhjælpede fil på din lokale computer.](../media/SIERimage7.png)

    Når du har valgt den afhjælpede fil, uploades den automatisk til korrektursættet. Du kan spore filens behandlingsstatus.

    ![Status for afhjælpningsprocessen vises.](../media/SIERimage8.png)

   Når behandlingen er fuldført, kan du se det afhjulpete dokument.

    ![Du kan få vist den afhjælpede fil i det oprindelige format i korrektursættet.](../media/SIERimage9.png)

Du kan finde flere oplysninger om, hvad der sker, når et dokument afhjælpes, under [Hvad sker der, når filer afhjælpes](error-remediation-when-processing-data-in-advanced-ediscovery.md#what-happens-when-files-are-remediated).

## <a name="search-for-remediated-documents"></a>Søge efter afhjælpede dokumenter

Du kan søge efter alle dokumenter i et korrektursæt, der er blevet løst,  ved hjælp af betingelsen Nøgleord og ved at angive følgende egenskab:værdipar: **IsFromErrorRemediation:true**. Denne egenskab er også tilgængelig i eksportindlæsningsfilen, når du eksporterer dokumenter fra et gennemsynssæt.
