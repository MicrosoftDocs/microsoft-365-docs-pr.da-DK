---
title: Installation med et andet MDM-system (Mobile Device Management) til Microsoft Defender til slutpunkt på Mac
description: Installer Microsoft Defender til Slutpunkt på Mac på andre administrationsløsninger.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: c8ffab850302967b9e36e841bf035cef07ad2775
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63597610"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Installation med et andet MDM-system (Mobile Device Management) til Microsoft Defender til slutpunkt på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du se microsoft [Defender for Endpoint på macOS-hovedsiden](microsoft-defender-endpoint-mac.md) for en beskrivelse af forudsætningerne og systemkravene for den aktuelle softwareversion.


## <a name="approach"></a>Fremgangsmåde

> [!CAUTION]

> I øjeblikket understøtter Microsoft officielt kun Intune og SYLF til installation og administration af Microsoft Defender til Endpoint på macOS. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til oplysningerne nedenfor.

Hvis din organisation bruger en løsning til administration af mobilenheder (MDM), der ikke understøttes officielt, betyder det ikke, at du ikke kan installere eller køre Microsoft Defender for Endpoint på macOS.

Microsoft Defender til Slutpunkt på macOS afhænger ikke af leverandørspecifikke funktioner. Den kan bruges sammen med en hvilken som helst MDM-løsning, der understøtter følgende funktioner:

- Installér en macOS .pkg på administrerede enheder.
- Installér macOS-systemkonfigurationsprofiler på administrerede enheder.
- Kør et vilkårligt administratorkonfigureret værktøj/script på administrerede enheder.

De fleste moderne MDM-løsninger omfatter disse funktioner, men de kan kalde dem anderledes.

Du kan dog installere Defender til slutpunkt uden det sidste krav fra den foregående liste:

- Du vil ikke kunne indsamle status på en central måde.
- Hvis du beslutter dig for at fjerne Defender til Slutpunkt, skal du logge på klientenheden lokalt som administrator.

## <a name="deployment"></a>Udrulning

De fleste MDM-løsninger bruger den samme model til administration af macOS-enheder med lignende terminologi. Brug [JAMF-baseret installation](mac-install-with-jamf.md) som en skabelon.

### <a name="package"></a>Pakke

Konfigurer [udrulning af en påkrævet](mac-install-with-jamf.md) programpakke med installationspakken (wdav.pkg) downloadet [fra Microsoft 365 Defender portal](mac-install-with-jamf.md).

For at installere pakken til din virksomhed skal du bruge den vejledning, der er knyttet til din MDM-løsning.

### <a name="license-settings"></a>Licensindstillinger

Konfigurer en [systemkonfigurationsprofil](mac-install-with-jamf.md). 

Din MDM-løsning kalder den muligvis noget i stedet for "Custom Indstillinger Profile", da Microsoft Defender til Slutpunkt på macOS ikke er en del af macOS.

Brug egenskabslisten,propf/WindowsDefenderATPOnboarding.plist, som kan udtrækkes fra en onboardingpakke, der er downloadet [Microsoft 365 Defender-portalen](mac-install-with-jamf.md).
Systemet understøtter muligvis en tilfældig egenskabsliste i XML-format. Du kan uploade syltefilen/WindowsDefenderATPOnboarding.plist-filen, som den er i det tilfælde.
Alternativt kan det kræve, at du konverterer egenskabslisten til et andet format først.

Typisk har din brugerdefinerede profil et id, navn eller en domæneattribut. Du skal bruge exactly "com.microsoft.wdav.atp" til denne værdi.
MDM bruger den til at installere indstillingsfilen til **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** på en klientenhed, og Defender til Slutpunkt bruger denne fil til at indlæse onboardingoplysningerne.

### <a name="kernel-extension-policy"></a>Udvidelsespolitik for kerne

Konfigurer en KEXT- eller kerneudvidelsespolitik. Brug team-id **UBF8T346G9 til** at tillade kerneudvidelser leveret af Microsoft.

> [!CAUTION]
> Hvis dit miljø består af Apple Silicon-enheder (M1), bør disse maskiner ikke modtage konfigurationsprofiler med KEXT-politikker.
> Apple understøtter ikke KEXT på disse computere, da udrulning af en sådan profil vil mislykkes på M1-computere.

### <a name="system-extension-policy"></a>Politik for systemudvidelse

Konfigurer en politik for systemudvidelser. Brug **team-id UBF8T346G9** , og godkend følgende bundle-id'er:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Politik for fuld diskadgang

Giv fuld diskadgang til følgende komponenter:

- Microsoft Defender til Slutpunkt
    - Identifikator: `com.microsoft.wdav`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- Microsoft Defender for Endpoint Security Extension
    - Identifikator: `com.microsoft.wdav.epsext`
    - Id-type: Bundle-id
    - Kodekrav: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Politik for netværksudvidelse

Som en del af egenskaberne Slutpunktsregistrering og Svar undersøger Microsoft Defender til slutpunkt på macOS sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender-portalen. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

- Filtertype: Plug-in
- Plug-in-id: `com.microsoft.wdav`
- Filtrer dataudbyderens bundle-id: `com.microsoft.wdav.netext`
- Filtrere dataudbyderens angivne krav: `identifier "com.microsoft.wdav.tunnelext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filter sockets: `true`

## <a name="check-installation-status"></a>Kontrollér installationsstatus

Kør [Microsoft Defender til slutpunkt på en](mac-install-with-jamf.md) klientenhed for at kontrollere onboardingstatus.
