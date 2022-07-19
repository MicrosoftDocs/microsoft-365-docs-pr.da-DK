---
title: Om profilindstillinger for autopilot
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: Autopilotprofiler hjælper dig med at styre, hvordan Windows installeres på brugerenheder. Profilerne indeholder standardindstillinger og valgfrie indstillinger, f.eks. spring Cortana-installationen over.
ms.openlocfilehash: 387346c68ad9ff85c3f97e4d8ca8b0ccdb28dcbd
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858831"
---
# <a name="about-autopilot-profile-settings"></a>Om profilindstillinger for autopilot

## <a name="autopilot-profile-settings"></a>Profilindstillinger for Autopilot

Du kan bruge Autopilot-profiler til at styre, hvordan Windows installeres på brugerenheder. Profilerne indeholder følgende indstillinger.
  
## <a name="autopilot-default-features-required-that-are-set-automatically"></a>Standardfunktioner for autopilot (påkrævet), der angives automatisk
  
| Indstilling | Beskrivelse |
|:-----|:-----|
|Spring Cortana, OneDrive og OEM-registrering over  |Springer installationen af forbrugerapps som Cortana og personlige OneDrive over. Enhedsbrugeren kan installere disse senere, så længe brugeren er lokal administrator på enheden. Den oprindelige producentregistrering springes over, fordi enheden administreres af Microsoft 365 Business Premium.  |
|Log på erfaring med dit firmamærke  |Hvis din virksomhed har [siden Føj din firmabranding til Microsoft 365 Log på](../admin/setup/customize-sign-in-page.md), får enhedsbrugeren denne oplevelse, når der logges på.  |
|AUTOMATISK MDM-tilmelding med konfigurerede AAD-konti.  |Brugeridentiteten administreres af Azure Active Directory, og brugerne logger på Windows og Microsoft 365 med deres Microsoft 365 Business Premium legitimationsoplysninger.  |

## <a name="optional-settings"></a>Valgfrie indstillinger
  
| Indstilling | Beskrivelse |
|:-----|:-----|
|Spring indstillinger for beskyttelse af personlige oplysninger over (slået fra som standard)  |Hvis denne indstilling er angivet til **Til**, kan enhedsbrugeren ikke se licensaftalen for enheden og Windows, når han eller hun logger på første gang.  |
|Tillad ikke, at brugeren bliver lokal administrator  |Hvis denne indstilling er angivet til **Til**, kan enhedsbrugeren ikke installere nogen personlige apps, f.eks Cortana.|

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)