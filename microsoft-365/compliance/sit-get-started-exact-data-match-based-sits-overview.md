---
title: Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Kom i gang med at oprette præcise datamatchbaserede følsomme oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0f221ba0521a50f484bfb9a8d5030e33b495c495
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759739"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger

Oprettelse og oprettelse af et nøjagtigt datamatch (EDM) baseret på sin følsomme informationstype (SIT) er en flerfaset proces. De kan bruges i politikker til forebyggelse af datatab, eDiscovery og visse indholdsstyringsopgaver Denne artikel beskriver arbejdsprocessen og links til procedurerne for hver af faserne

## <a name="before-you-begin"></a>Før du begynder

Bliv fortrolig med begreberne og terminologien i disse artikler:

- [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal være global administrator, overholdelsesadministrator eller Exchange Online administrator for at kunne udføre de opgaver, der er beskrevet i denne artikel. Du kan få mere at vide om DLP-tilladelser under [Tilladelser](data-loss-prevention-policies.md#permissions).

Se [beskrivelsen af tjenesten til forebyggelse af datatab](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) for at få komplette licensoplysninger

## <a name="portal-links-for-your-subscription"></a>Portallinks til dit abonnement

|Portal|Verdensomspændende/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender portal|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft 365 Compliance Center|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Et hurtigt overblik over arbejdsflowet

![nøjagtige data matcher arbejdsprocesfaser](..\media\swimlane_edm_process.png)


|Fase|Hvad er der brug for|
|---|---|
|[Fase 1: Eksportér kildedata for præcise datamatchbaserede følsomme oplysninger](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|– Læseadgang til følsomme data|
|[Fase 2: Opret skemaet for præcise datamatchbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Adgang til guiden til følsomme oplysninger i Microsoft 365 Administration </br>– adgang til [Microsoft 365 Administration via PowerShell til sikkerheds & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell) |
|[Fase 3: Hash og upload den følsomme informationskildetabel for præcise data matcher følsomme informationstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- Brugerdefineret sikkerhedsgruppe og brugerkonto </br>- **Hash og upload fra én computer**: lokal administratoradgang til en computer med direkte internetadgang og vært for EDM-Upload Agent </br>- **Hash og upload fra separate computere**: lokal administratoradgang til en computer med direkte internetadgang og vært for EDM-Upload Agent for upload og lokal administratoradgang til en sikker computer som vært for EDM-Upload Agent for at hashkode den følsomme informationskildetabel </br>- Læseadgang til den følsomme informationskildetabelfil </br> skemafilen |
|[Fase 4: Opret præcise data, der stemmer overens med følsomme oplysningers type/regelpakke](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |– adgang til Microsoft 365 Compliance Center |
|[Test et nøjagtigt datamatch for typen af følsomme oplysninger](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| – adgang til Microsoft 365 Compliance Center

## <a name="see-also"></a>Se også

- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Eksportér kildedata for at finde nøjagtigt datamatch baseret på følsom oplysningstype](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
