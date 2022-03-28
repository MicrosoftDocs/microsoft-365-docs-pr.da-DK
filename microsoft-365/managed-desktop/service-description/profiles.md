---
title: Forstå enhedsprofiler
description: De forskellige profiler, som administratorer kan tildele enheder
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d12a197db8dbcb6356882082c212754fef726d4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597888"
---
# <a name="device-profiles"></a>Enhedsprofiler

Du kan tænke på, at enhedsprofiler er en del af et hierarki af indstillinger for enhedskonfiguration.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Enhedskonfigurationer vist som en pyramide. Beskrivelse følger.":::

| Konfigurationsindstillinger for enhed | Beskrivelse
| ----- | ----- |
| Dine konfigurationer | Øverst finder du dine egne konfigurationer, f.eks. netværksoplysninger eller programmer. En enhed kan have et hvilket som helst antal af disse konfigurationer, som ikke administreres eller blokeres af Microsoft Managed Desktop. |
| Tilpasninger | Det næste højere niveau er [yderligere tilpasninger](customizing.md). Hver enhed kan have en eller flere (eller ingen) tilpasninger. Tilpasningerne kan enten ændre et lag på lavere niveau (Enhedsprofiler eller basiskonfigurationen), eller de kan være en helt ny anmodning, der er lagdelt oven på standardkonfigurationen. |
| Enhedsprofiler | Der skal være tildelt én og kun én profil på alle Microsoft-administrerede stationære computere. Administratorer kan vælge, hvilken profil en enhed er tildelt.<br><br>Du kan tildele forskellige forudindstillede profiler til enheder. Hver profil er optimeret til behovene hos bestemte typer af brugere. Der findes tre enhedsprofiler:<ul><li>Standard</li><li>Følsomme data</li><li>Superbruger</li> |
| Foundation | Grundlæggende har alle Microsoft-administrerede stationære computere et fundament, der indeholder:<br><ul><li>Standardsikkerheds oprindelig plan</li><li>Politikker for overholdelse af regler og standarder</li><li>Windows opdateringsindstillinger</li><li>Grupper</li></ul><br>Hvis du vil arbejde med Microsoft-administreret skrivebord, skal alle enheder indeholde alle disse elementer. Disse elementer kan ikke ændres af administratorer. Du skal sende en anmodning til Microsoft Managed Desktop. |

## <a name="device-profile-details"></a>Detaljer om enhedsprofil

Den følgende tabel opsummerer indstillingerne og deres standardværdier for hver indstilling, der er konfigureret af enhedsprofiler. I baggrunden er disse indstillinger konfigureret med OMA-URIs ved hjælp af Brugerdefinerede konfigurationsprofiler i Microsoft Endpoint Manager.

<br>

****

| Funktion | Følsomme data | Superbruger | Standard |
| ----- | :-----: | :-----: | :-----: |
|**Blokere eksterne Storage**| Ja | Ja | Nej |
|**[Bloker i skyen](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**| Høj | Høj | Høj |
|**Deaktiver Microsoft-konti**| Ja | Ja | Nej |
|**Deaktiver personlige OneDrive**| Ja | Ja | Nej |
|**[Skift til sikker desktopversion for udvidelse](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**| Nej | Ja | Nej |
|**Microsoft Defender for Endpoint Device Tag**| M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
|**Er du administrator på enheden?**| Nej | Ja | Nej |
|**AutoPilot-profil**| MMD Standard | Mmd-superbruger | MMD Standard |
|**AppLocker**| Ja | Nej | Nej |
|**Bloker offentlige Store**| Ja | Ja | Nej |
|

Hver enhedsprofil omfatter også disse elementer:

- Et dynamisk medlemskab Azure Active Directory en enhedsgruppe.
- Et statisk medlemskab Azure Active Directory enhedsgruppe.
- En Microsoft Endpoint Manager Konfigurationsprofil.

> [!IMPORTANT]
> Rediger ikke medlemskabet af disse grupper direkte. Brug brugergrænsefladen som beskrevet i [Tildel profiler igen](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Begrænsninger

Du kan anmode om undtagelser til enhedsprofiler og deres oplysninger på samme måde som med enhver anden politik.

Husk, at du kun kan have én af hver enhedsprofil i din Azure Active Directory organisation ("lejer"). Du kan f.eks. ikke anmode om, at profilen Følsom dataenhed kun deaktiverer AppLocker for nogle af dine brugere. Alle enheder med profilen for følsomme dataenheder skal have den samme konfiguration.

Hver enhed kan kun have én profil. Hvis en given enhed bruges af mere end én bruger, vil alle brugere på enheden have den samme konfiguration.
