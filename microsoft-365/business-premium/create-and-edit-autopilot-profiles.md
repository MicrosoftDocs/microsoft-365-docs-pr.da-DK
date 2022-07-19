---
title: Opret og rediger Autopilot-profiler
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: Få mere at vide om, hvordan du opretter en Autopilot-profil og anvender den på en enhed og redigerer eller sletter en profil eller fjerner en profil fra en enhed.
ms.openlocfilehash: 6f019e494eb073f47921f4adef454c0e48541b49
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858818"
---
# <a name="create-and-edit-autopilot-profiles"></a>Opret og rediger Autopilot-profiler

Du kan anvende en [Windows Autopilot-installationsprofil](/mem/autopilot/profiles) på enheder, der er i en [enhedsgruppe](m365bp-device-groups-mdb.md). Installationsprofiler bestemmer den Windows-udrulnings- og tilmeldingsoplevelse, som brugerne vil have. 

## <a name="create-a-profile"></a>Opret en profil

En profil gælder for en enhed eller en gruppe enheder,
  
1. I Microsoft 365 Administration skal du vælge **Enheder** \> **Autopilot**.
  
2. På siden **Autopilot** skal du vælge fanen \> **Profiler** **Opret profil**.

3. På siden **Opret profil** skal du angive et navn på den profil, der hjælper dig med at identificere den, f.eks. Marketing. Slå den ønskede indstilling til, og vælg derefter **Gem**. Du kan få flere oplysninger om profilindstillinger for Autopilot under [Om profilindstillinger for autopilot](m365bp-Autopilot-profile-settings.md).

    ![Angiv navn, og aktivér indstillinger i panelet Opret profil.](./../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>Anvend profil på en enhed

Når du har oprettet en profil, kan du anvende den på en enhed eller en gruppe af enheder. Du kan vælge en eksisterende profil i den [trinvise vejledning](m365bp-add-Autopilot-devices-and-profile.md) og anvende den på nye enheder eller erstatte en eksisterende profil for en enhed eller gruppe af enheder.
  
1. Vælg fanen **Enheder** på siden **Forbered Windows**.

2. Markér afkrydsningsfeltet ud for et enhedsnavn, og vælg en profil på rullelisten \> **Tildelt profil** **Gem** i panelet **Enhed**.

    ![Vælg en Tildelt profil i panelet Enhed for at anvende den.](./../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>Rediger, slet eller fjern en profil

Når du har tildelt en profil til en enhed, kan du opdatere den, selvom du allerede har givet enheden til en bruger. Når enheden opretter forbindelse til internettet, downloades den nyeste version af din profil under konfigurationsprocessen. Hvis brugeren gendanner sin enhed til fabriksstandardindstillingerne, downloader enheden igen de seneste opdateringer til din profil.
  
### <a name="edit-a-profile"></a>Rediger en profil

1. På siden **Forbered Windows** skal du vælge fanen **Profiler** .

2. Markér afkrydsningsfeltet ud for et enhedsnavn, og opdater en af de tilgængelige indstillinger \> **Gem** i panelet **Profil**.

    Hvis du udfører denne opgave, før en bruger opretter forbindelse mellem enheden og internettet, anvendes profilen på konfigurationsprocessen.

### <a name="delete-a-profile"></a>Slet en profil

1. På siden **Forbered Windows** skal du vælge fanen **Profiler** .

2. Markér afkrydsningsfeltet ud for et enhedsnavn, og vælg **Slet profil** \> **gem** i panelet **Profil**.

    Når du sletter en profil, fjernes den fra en enhed eller en gruppe enheder, den er tildelt til.

### <a name="remove-a-profile"></a>Fjern en profil

1. Vælg fanen **Enheder** på siden **Forbered Windows**.

2. Markér afkrydsningsfeltet ud for et enhedsnavn, og vælg **Ingen** på rullelisten \> **Tildelt profil** **Gem** i panelet **Enhed**.

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)
