---
title: Tilmeld Microsoft Defender til slutpunkt på macOS-enheder i Jamf Pro
description: Tilmeld Microsoft Defender til slutpunkt på macOS-enheder i Jamf Pro
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ab3db2e2b64261ae00008aef448a214cd235bda9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63606437"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Tilmeld Microsoft Defender til slutpunkt på macOS-enheder i Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>Tilmeld macOS-enheder

Der er flere metoder til at blive tilmeldt SylteF.

I denne artikel beskrives to metoder:

- [Metode 1: Tilmeldingsinvitationer](#enrollment-method-1-enrollment-invitations)
- [Metode 2: Prestage-tilmeldinger](#enrollment-method-2-prestage-enrollments)

Du kan se en komplet liste [under Om computerregistrering](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html).

## <a name="enrollment-method-1-enrollment-invitations"></a>Registreringsmetode 1: Tilmeldingsinvitationer

1. I Syltef-Pro dashboardet skal du **gå til Tilmeldingsinvitationer**.

    ![Billede af konfigurationsindstillinger1.](images/a347307458d6a9bbfa88df7dbe15398f.png)

2. Vælg **+ Ny**.

    ![Et nær nærheden af et logo Beskrivelse genereres automatisk.](images/b6c7ad56d50f497c38fc14c1e315456c.png)

3. I **Angiv modtagere for >** under **Mailadresser** skal du angive mailadresserne på modtagerne.

    ![Billede af konfigurationsindstillinger2.](images/718b9d609f9f77c8b13ba88c4c0abe5d.png)

    ![Billede af konfigurationsindstillinger3.](images/ae3597247b6bc7c5347cf56ab1e820c0.png)

    For eksempel: janedoe@contoso.com

    ![Billede af konfigurationsindstillinger4.](images/4922c0fcdde4c7f73242b13bf5e35c19.png)

4. Konfigurer meddelelsen for invitationen.

    ![Billede af konfigurationsindstillinger5.](images/ce580aec080512d44a37ff8e82e5c2ac.png)

    ![Billede af konfigurationsindstillinger6.](images/5856b765a6ce677caacb130ca36b1a62.png)

    ![Billede af konfigurationsindstillinger7.](images/3ced5383a6be788486d89d407d042f28.png)

    ![Billede af konfigurationsindstillinger8.](images/54be9c6ed5b24cebe628dc3cd9ca4089.png)

## <a name="enrollment-method-2-prestage-enrollments"></a>Registreringsmetode 2: Prestage-registreringer

1. Gå til **Prestage-Pro i sylteboardet**.

    ![Billede af konfigurationsindstillinger9.](images/6fd0cb2bbb0e60a623829c91fd0826ab.png)

2. Følg vejledningen i [Computer PreStage-tilmeldinger](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Tilmeld macOS-enhed

1. Vælg **Fortsæt,** og installér nøglecentercertifikatet fra **vinduet Systemindstillinger** .

    ![Billede af Sylte Pro tilmelding1.](images/jamfpro-ca-certificate.png)

2. Når nøglecentercertifikatet er installeret, skal du vende tilbage til browservinduet **og vælge Fortsæt** og installere MDM-profilen.

    ![Billede af Jamf Pro registrering2.](images/jamfpro-install-mdm-profile.png)

3. Vælg **Tillad** at downloade fra SYLF.

    ![Billede af Sylte Pro tilmelding3.](images/jamfpro-download.png)

4. Vælg **Fortsæt** for at fortsætte med installationen af MDM-profilen.

    ![Billede af Sylte Pro tilmelding4.](images/jamfpro-install-mdm.png)

5. Vælg **Fortsæt** for at installere MDM-profilen.

    ![Billede af Jamf Pro registrering5.](images/jamfpro-mdm-unverified.png)

6. Vælg **Fortsæt**  for at fuldføre konfigurationen.

    ![Billede af Sylte Pro registrering6.](images/jamfpro-mdm-profile.png)
