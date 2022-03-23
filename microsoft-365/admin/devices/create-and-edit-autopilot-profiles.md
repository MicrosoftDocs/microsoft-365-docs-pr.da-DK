---
title: Opret og rediger AutoPilot-profiler
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Lær at oprette en AutoPilot-profil og anvende den på en enhed, samt redigere eller slette en profil eller fjerne en profil fra en enhed.
ms.openlocfilehash: 91df801fb1833c9bfe5f1112e6a3cd5fc8efcf5d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594595"
---
# <a name="create-and-edit-autopilot-profiles"></a>Opret og rediger AutoPilot-profiler

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="create-a-profile"></a>Opret en profil

En profil gælder for en enhed eller en gruppe af enheder,
  
1. I menuen Microsoft 365 Administration du vælge **Devices** \> **AutoPilot**.
  
2. På siden **AutoPilot** skal du vælge **fanen Profiler** Opret \> **profil**.
    
3. På siden **Opret profil skal** du angive et navn til profilen, som hjælper dig med at identificere den, f.eks. Marketing. Slå den ønskede indstilling til, og vælg derefter **Gem**. Du kan finde flere oplysninger om AutoPilot-profilindstillinger [under Om AutoPilot-profilindstillinger](autopilot-profile-settings.md).
    
    ![Angiv navn, og aktiver indstillingerne i panelet Opret profil.](../../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Anvend en profil på en enhed

Når du har oprettet en profil, kan du anvende den på en enhed eller en gruppe af enheder. Du kan vælge en eksisterende profil i den [](add-autopilot-devices-and-profile.md) trinvise vejledning og anvende den på nye enheder, eller du kan erstatte en eksisterende profil for en enhed eller en gruppe af enheder. 
  
1. På siden **Forbered Windows** skal du vælge **fanen** Enheder. 
    
2. Markér afkrydsningsfeltet ud for navnet på en enhed, og vælg en  profil på rullelisten Tildelt profil i panelet  **Enhed**.\>
    
    ![I panelet Enhed skal du vælge en Tildelt profil for at anvende den.](../../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Rediger, slet eller fjern en profil

Når du har tildelt en profil til en enhed, kan du opdatere den, også selvom du allerede har givet enheden til en bruger. Når enheden opretter forbindelse til internettet, downloader den den nyeste version af din profil under konfigurationen. Hvis brugeren gendanner enhedens standardindstillinger, vil enheden igen hente de seneste opdateringer til din profil. 
  
### <a name="edit-a-profile"></a>Redigere en profil

1. På siden **Forbered Windows** skal du vælge **fanen** Profiler. 
    
2. Markér afkrydsningsfeltet ud for navnet på en enhed, og opdater **en af** de tilgængelige indstillinger i \> panelet **Profil**.
    
    Hvis du gør dette, før en bruger opretter forbindelse mellem enheden og internettet, så anvendes profilen i konfigurationsprocessen.
    
### <a name="delete-a-profile"></a>Slet en profil

1. På siden **Forbered Windows** skal du vælge **fanen** Profiler. 
    
2. Markér afkrydsningsfeltet ud for navnet på en enhed, og vælg **Slet** profil i **panelet** \> **Profil**.
    
    Når du sletter en profil, fjernes den fra en enhed eller en gruppe af enheder, den er tildelt til.
    
### <a name="remove-a-profile"></a>Fjern en profil

1. På siden **Forbered Windows** skal du vælge **fanen** Enheder. 
    
2. Markér afkrydsningsfeltet ud for navnet på en enhed,  \> og vælg Ingen  på rullelisten Tildelt profil i panelet **Enhed**.
    
## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)