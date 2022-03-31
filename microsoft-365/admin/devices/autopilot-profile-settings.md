---
title: Om profilindstillinger for AutoPilot
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: medium
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
description: AutoPilot-profiler hjælper dig med at kontrollere, Windows bliver installeret på brugerenheder. Profilerne indeholder standardindstillinger og valgfrie indstillinger som f.eks. Cortana installationen.
ms.openlocfilehash: d0b1a15ef8279234868b94ab5c16e449a54cf62f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63600954"
---
# <a name="about-autopilot-profile-settings"></a>Om profilindstillinger for AutoPilot

## <a name="autopilot-profile-settings"></a>Profilindstillinger for AutoPilot

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

Du kan bruge AutoPilot-profiler til at styre, hvordan Windows er installeret på brugerenheder. Profilerne indeholder følgende indstillinger.
  
 **AutoPilot-standardfunktioner (påkrævet), der indstilles automatisk:**
  
|**Indstilling**|**Beskrivelse**|
|:-----|:-----|
|Spring Cortana, OneDrive og OEM-registrering over  <br/> |Springer installation af apps til forbrugere over, f.eks. Cortana og personlige OneDrive. Brugeren af enheden kan installere disse senere, så længe brugeren er lokal administrator på enheden. Den oprindelige producentregistrering ignoreres, fordi enheden administreres af Microsoft 365 Business Premium.  <br/> |
|Log på-oplevelsen med dit firmas brand  <br/> |Hvis din virksomhed har en [Føj din firmabranding til Microsoft 365 logonside](../setup/customize-sign-in-page.md), får brugeren af enheden denne oplevelse, når de logger på.  <br/> |
|Automatisk registrering af MDM med konfigurerede AAD konti.  <br/> |Brugerens identitet administreres af Azure Active Directory, og brugerne logger på Windows og Microsoft 365 med deres Microsoft 365 Business Premium legitimationsoplysninger.  <br/> |
   
 **Valgfri indstillinger:**
  
|**Indstilling**|**Beskrivelse**|
|:-----|:-----|
|Spring indstillinger for beskyttelse af personlige oplysninger over (fra som standard)  <br/> |Hvis denne indstilling er **indstillet til** Til, får brugeren af enheden ikke vist licensaftalen for enheden og Windows når han eller hun logger på første gang.  <br/> |
|Tillad ikke, at brugeren bliver den lokale administrator  <br/> |Hvis denne indstilling er indstillet **til Til**, kan brugeren af enheden ikke installere personlige apps, f.eks. Cortana.<br/> |

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)