---
title: Registreringsmetoder for enhed i Microsoft Managed Desktop
description: Oplysninger om enhedens registreringsmetoder i Microsoft Managed Desktop
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 7d0cabc0a9d11d337e5adabde568bd2a56ceca86
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704665"
---
# <a name="device-registration-methods"></a>Registreringsmetoder for enhed

Før Microsoft kan administrere dine enheder i Microsoft Managed Desktop, skal du have enheder, der er registreret med tjenesten.

## <a name="registration-process"></a>Registreringsproces

Microsoft Managed Desktop drives af Windows Autopilot-tjenesten til enhedsregistreringsarbejdsprocessen. Vellykket enhedsregistrering kræver en totrinsproces:

1. Enhedens unikke hardwareidentitet, også kaldet hardwarehash, registreres og uploades til Autopilot-tjenesten.
1. Enheden er knyttet til et Azure Active Directory lejer-id.

Ideelt set udføres begge trin af OEM, forhandleren eller distributøren, hvor enhederne blev købt. En OEM eller en anden enhedsudbyder bruger registreringsgodkendelsesprocessen til at udføre enhedsregistrering på dine vegne.

## <a name="registration-methods"></a>Registreringsmetoder

Registrering kan også udføres inden for organisationen ved at indsamle hardwareidentiteten fra nye eller eksisterende enheder og uploade den manuelt. Nedenfor finder du de registreringsmetoder, som Microsoft Managed Desktop understøtter:

- OEM-registrering
    - [Brug af partnerportalen](partner-registration.md#register-devices-using-the-partner-center)
    - [Brug af OEM-API'er](partner-registration.md#register-devices-by-using-the-oem-api)
- [Manuel registrering](manual-registration.md)
- [Manuel registrering af eksisterende enheder](manual-registration-existing-devices.md)

## <a name="recommended-resources"></a>Anbefalede ressourcer

- [Oversigt over Windows Autopilot](/mem/autopilot/windows-autopilot)
- [Windows Autopilot-registrering](/mem/autopilot/registration-overview)

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).
