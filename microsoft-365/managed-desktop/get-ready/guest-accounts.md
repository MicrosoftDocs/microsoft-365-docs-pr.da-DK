---
title: Forudsætninger for gæstekonti
description: Konfigurationsretningslinjer for gæstekonti, og hvordan de tilpasses
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 80770c6c122cc4e2892c22a43f185ffbac40c637
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63590478"
---
# <a name="prerequisites-for-guest-accounts"></a>Forudsætninger for gæstekonti

## <a name="external-collaboration-settings"></a>Indstillinger for eksternt samarbejde

Microsoft Managed Desktop anbefaler følgende konfiguration i din Azure AD-organisation for gæstekontoadgang. Du kan justere disse indstillinger på [Azure-portalen](https://portal.azure.com) under **Indstillinger for eksterne identiteter/Eksternt samarbejde**:

| Indstilling | Indstil til |
| ------ | ------ |
| Gæsteadgang | Gæster har begrænset adgang til egenskaber og medlemskaber af katalogobjekter. |
| Indstillinger for gæste inviterer | Medlemsbrugere og brugere, der er tildelt bestemte administratorroller, kan invitere gæster, herunder gæster med medlemstilladelser |

Microsoft Managed Desktop kræver følgende konfiguration i din Azure AD-organisation for gæstekontoadgang. Du kan justere denne indstilling på [Azure-portalen](https://portal.azure.com) under **Indstillinger for eksterne identiteter/Eksternt samarbejde**:

| Indstilling | Indstilling |
| ------ | ------ |
| Begrænsninger for samarbejde | Vælg en af disse indstillinger: <ul><li>Hvis du vælger **Tillad, at invitationer sendes til et domæne (mest inklusive)** kræves ingen anden konfiguration.</li><li>Hvis du vælger **Afvisning af invitationer** til de angivne domæner, skal du sikre dig, Microsoft.com ikke er angivet i destinationsdomænerne.</li><li>Hvis du vælger **Tillad kun invitationer** til de angivne domæner (mest restriktive), skal du kontrollere, Microsoft.com *er* angivet i destinationsdomænerne.</li><ul>

Hvis du angiver begrænsninger, der interagerer med disse indstillinger, skal du sikre dig, at Azure Active Directory **konti til tjenesten Moderne arbejdsplads**. Hvis du f.eks. har en politik for betinget adgang, der forhindrer gæstekonti i at få adgang til Intune-portalen, skal du udelade gruppen Konti for moderne arbejdsplads-tjeneste fra denne politik.

Få mere at vide under [Aktivér eksternt B2B-samarbejde, og administrer, hvem der kan invitere gæster](/azure/active-directory/external-identities/delegate-invitations#to-configure-external-collaboration-settings).

## <a name="unlicensed-intune-admin"></a>Intune-administrator uden licens

Indstillingen **Tillad adgang til administratorer uden licens skal** være aktiveret. Uden denne indstilling er aktiveret, kan der opstå fejl, når vi forsøger at få adgang til din Azure AD-organisation til service. Du kan uden problemer aktivere denne indstilling uden at bekymre dig om, hvad det betyder for sikkerheden. Adgangsomfanget defineres af de roller, der er tildelt til brugere, herunder vores driftsmedarbejdere.

**Sådan aktiveres denne indstilling:**

1. Gå til Microsoft Endpoint Manager [Administration](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Gå til **Lejeradministration,** og vælg **Roller**. Vælg derefter **Administratorlicens**.
3. I sektionen **Tillad adgang til administratorer uden licens skal** du vælge **Ja**.

> [!IMPORTANT]
> Du kan ikke fortryde denne indstilling, efter at du har valgt **Ja**.

Du kan finde flere oplysninger [under Administratorer uden licens i Microsoft Intune](/mem/intune/fundamentals/unlicensed-admins).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå forudsætningerne for gæstekonti (denne artikel).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
