---
title: Konfigurer administrerede enheder
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
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Sådan konfigurerer du administrerede enheder
ms.openlocfilehash: a5498fc89a135a90d192b2b7ddb7165527e13123
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66858998"
---
# <a name="set-up-managed-devices"></a>Konfigurer administrerede enheder

En "administreret" enhed er en enhed, der er under kontrol og overvåges af organisationen, og den opdateres derfor regelmæssigt og er sikker. Det er en kritisk målsætning at have enheder under administreret kontrol. Hvis du vil have disse enheder under kontrol, skal du tilmelde dem i en enhedsadministrator med Microsoft Intune og Azure Active Directory, som begge er inkluderet i Microsoft Business Premium.

1. Konfigurer politikker for enheds- og databeskyttelse i [installationsguiden](../business/set-up.md).

2. Tilsluttet computeren til [Azure Active Directory](../business/set-up-windows-devices.md) med deres brugernavn og adgangskode til Microsoft 365. 

## <a name="enroll-devices-in-intune"></a>Tilmeld enheder i Intune

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Enheder** > **Tilmeld enheder**. 

   :::image type="content" source="media/m365bp-endpoint-manager-enroll-devices.png" alt-text="Brug Microsoft Endpoint Manager til at tilmelde enheder."::: 

3. Følg den specifikke vejledning til tilmelding af enheder nedenfor.

### <a name="for-windows-enrollment"></a>Til Windows-tilmelding:

1. Vælg **Windows-tilmelding** > . 

2. Vælg **Automatisk tilmelding** på listen over tilmeldingsmetoder.

### <a name="for-ios-enrollment"></a>Til iOS-tilmelding:

1. Vælg **iOS-tilmelding** > **til iOS**.

2. Vælg en politik på listen over politikker for at få vist dens detaljer.

3. Vælg **Egenskaber** for at administrere politikken.

4. Vælg **Indstillinger** > **Systemsikkerhed**, og konfigurer sikkerhedsoplysninger i Intune.

5. Se konfigurationsprofiler. 

6. Opret en profil, og send den til enhederne i din organisation efter behov.

### <a name="for-android-enrollment"></a>Til Android-tilmelding:

1. Vælg **Android-tilmelding** til **Android** > .

2. Vælg **Administreret Google Play** , og giv Microsoft tilladelse til at sende oplysninger til Google.

## <a name="next-objective"></a>Næste mål

Brug følgende vejledning til at [onboarde enheder til Defender for Business-funktioner](m365bp-onboard-devices-mdb.md).

