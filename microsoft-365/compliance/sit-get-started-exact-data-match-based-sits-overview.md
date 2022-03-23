---
title: Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger
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
description: Kom i gang med at oprette nøjagtige datamatchingbaserede følsomme oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75650484368b6ccbaf6f6d39aeead133403f5b8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594081"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger

Oprettelse og oprettelse af et nøjagtigt data match (EDM) baseret på følsomme oplysningstype (SIT) er en proces i flere faser. De kan bruges i politikker til forebyggelse af datatab, eDiscovery og visse indholdsstyringsopgaver Denne artikel beskriver arbejdsprocessen og links til procedurerne for hver af faserne

## <a name="before-you-begin"></a>Før du begynder

Gør dig bekendt med begreber og terminologi i følgende artikler:

- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Du skal være global administrator, overholdelsesadministrator eller Exchange Online for at udføre de opgaver, der er beskrevet i denne artikel. Du kan få mere at vide om DLP-tilladelser [under Tilladelser](data-loss-prevention-policies.md#permissions).

Se [tjenestebeskrivelsen til forebyggelse af datatab](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) for at få komplette licensoplysninger

## <a name="portal-links-for-your-subscription"></a>Portallinks til dit abonnement

|Portal|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender-portal|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft 365 over overholdelsescenter|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Hurtigt overblik over arbejdsflowet

![nøjagtige datamatchingfaser i arbejdsproces](..\media\swimlane_edm_process.png)


|Fase|Det, der er nødvendigt|
|---|---|
|[Fase 1: Eksportér kildedata for nøjagtig dataoverensstemmelsesbaseret følsom oplysningstype](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- Læse adgang til de følsomme data|
|[Fase 2: Opret skemaet for nøjagtige datamatchingbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- Adgang til guiden til følsomme oplysninger i Microsoft 365 Administration </br>- adgang til [Microsoft 365 Administration via Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) |
|[Fase 3: Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- Brugerdefineret sikkerhedsgruppe og brugerkonto </br>- **Hash og upload fra én computer**: Lokal administratoradgang til en computer med direkte internetadgang og som vært for EDM-Upload agent </br>- **Hash og upload fra separate** computere: Lokal administratoradgang til en computer med direkte internetadgang og vært for EDM Upload-agenten for overførslen og lokal administratoradgang til en sikker computer, der er vært for EDM Upload-agenten, der skal håndtere den følsomme kildetabel med oplysninger </br>- Læse adgang til kildetabelfilen med følsomme oplysninger </br> skemafilen |
|[Fase 4: Opret en nøjagtig data matchning af følsomme oplysningstype/regelpakke](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Adgang til Microsoft 365 Compliance Center |
|[Teste en nøjagtig datatype, der matcher følsomme oplysninger](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Adgang til Microsoft 365 Compliance Center

## <a name="see-also"></a>Se også

- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Eksportér kildedata for en nøjagtig dataoverensstemmelsesbaseret type af følsomme oplysninger](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
