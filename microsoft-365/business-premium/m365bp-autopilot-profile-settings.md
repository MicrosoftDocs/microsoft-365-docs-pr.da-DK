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
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
description: Autopilotprofiler hjælper dig med at styre, hvordan Windows installeres på brugerenheder. Profilerne indeholder standardindstillinger og valgfrie indstillinger, f.eks. spring Cortana-installationen over.
ms.openlocfilehash: 9fcec0d34a23a56943a1a17d7e7f74435910055e
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894717"
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