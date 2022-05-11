---
title: Installation med et andet MDM-system (Mobile Enhedshåndtering) til Microsoft Defender for Endpoint på Mac
description: Installér Microsoft Defender for Endpoint på Mac på andre administrationsløsninger.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2fa64ee9822fe1f784788e2d1ead79e66eb200ef
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349741"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Installation med et andet MDM-system (Mobile Enhedshåndtering) til Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, kan du se [de primære Microsoft Defender for Endpoint på macOS side](microsoft-defender-endpoint-mac.md) for at få en beskrivelse af forudsætninger og systemkrav til den aktuelle softwareversion.


## <a name="approach"></a>Tilgang

> [!CAUTION]

> I øjeblikket understøtter Microsoft officielt kun Intune og JAMF til installation og administration af Microsoft Defender for Endpoint på macOS. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet nedenfor.

Hvis din organisation bruger en MDM-løsning (Mobile Enhedshåndtering), der ikke understøttes officielt, betyder det ikke, at du ikke kan installere eller køre Microsoft Defender for Endpoint på macOS.

Microsoft Defender for Endpoint på macOS afhænger ikke af nogen leverandørspecifikke funktioner. Den kan bruges sammen med en hvilken som helst MDM-løsning, der understøtter følgende funktioner:

- Installer en macOS .pkg på administrerede enheder.
- Udrul macOS systemkonfigurationsprofiler på administrerede enheder.
- Kør et vilkårligt administratorkonfigureret værktøj/script på administrerede enheder.

De fleste moderne MDM-løsninger omfatter disse funktioner, men de kan kalde dem anderledes.

Du kan dog installere Defender for Endpoint uden det sidste krav fra den foregående liste:

- Du kan ikke indsamle status på en centraliseret måde.
- Hvis du beslutter at fjerne Defender for Endpoint, skal du logge på klientenheden lokalt som administrator.

## <a name="deployment"></a>Installation

De fleste MDM-løsninger bruger den samme model til administration af macOS enheder med lignende terminologi. Brug [JAMF-baseret installation](mac-install-with-jamf.md) som en skabelon.

### <a name="package"></a>Pakke

Konfigurer installationen af en [påkrævet programpakke](mac-install-with-jamf.md), hvor installationspakken (wdav.pkg) er hentet fra [Microsoft 365 Defender portal.](mac-install-with-jamf.md)

Hvis du vil installere pakken i din virksomhed, skal du bruge de instruktioner, der er knyttet til din MDM-løsning.

### <a name="license-settings"></a>Licensindstillinger

Konfigurer [en systemkonfigurationsprofil](mac-install-with-jamf.md). 

MDM-løsningen kan kalde den f.eks. "Custom Indstillinger Profile", da Microsoft Defender for Endpoint på macOS ikke er en del af macOS.

Brug egenskabslisten jamf/WindowsDefenderATPOnboarding.plist, som kan udtrækkes fra en onboardingpakke, der downloades fra [Microsoft 365 Defender portal](mac-install-with-jamf.md).
Dit system understøtter muligvis en vilkårlig egenskabsliste i XML-format. Du kan uploade jamf/WindowsDefenderATPOnboarding.plist-filen, som den er i dette tilfælde.
Det kan også kræve, at du konverterer egenskabslisten til et andet format først.

Din brugerdefinerede profil har typisk et id, et navn eller en domæneattribut. Du skal bruge nøjagtigt "com.microsoft.wdav.atp" til denne værdi.
MDM bruger den til at installere indstillingsfilen på **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** på en klientenhed, og Defender for Endpoint bruger denne fil til indlæsning af onboardingoplysningerne.

### <a name="kernel-extension-policy"></a>Politik for kerneudvidelse

Konfigurer en KEXT- eller kerneudvidelsespolitik. Brug teamidentifikatoren **UBF8T346G9** til at tillade kerneudvidelser fra Microsoft.

> [!CAUTION]
> Hvis dit miljø består af Apple Silicon (M1)-enheder, bør disse maskiner ikke modtage konfigurationsprofiler med KEXT-politikker.
> Apple understøtter ikke KEXT på disse maskiner. Installationen af denne profil vil mislykkes på M1-maskiner.

### <a name="system-extension-policy"></a>Politik for systemudvidelse

Konfigurer en politik for systemudvidelse. Brug **team-id'et UBF8T346G9** , og godkend følgende bundt-id'er:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Politik for fuld diskadgang

Tildel fuld diskadgang til følgende komponenter:

- Microsoft Defender for Endpoint
    - Id: `com.microsoft.wdav`
    - Id-type: Bundt-id
    - Kodekrav: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- sikkerhedsudvidelsen Microsoft Defender for Endpoint
    - Id: `com.microsoft.wdav.epsext`
    - Id-type: Bundt-id
    - Kodekrav: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Politik for netværksudvidelse

Som en del af slutpunktsregistrerings- og svarfunktionerne Microsoft Defender for Endpoint på macOS undersøger sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

- Filtertype: Plug-in
- Plug-in-bundt-id: `com.microsoft.wdav`
- Filterdataproviderens bundt-id: `com.microsoft.wdav.netext`
- Udpeget krav til filterdataprovider: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filterstik: `true`

## <a name="check-installation-status"></a>Kontrollér installationsstatus

Kør [Microsoft Defender for Endpoint](mac-install-with-jamf.md) på en klientenhed for at kontrollere onboardingstatussen.
