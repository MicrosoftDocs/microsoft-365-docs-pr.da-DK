---
title: Tilmeld Microsoft Defender for Endpoint macOS-enheder til Jamf Pro
description: Tilmeld Microsoft Defender for Endpoint macOS-enheder til Jamf Pro
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune,propfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6189b61826cd56e2a8652032998c3b2df8f980ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468671"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>Tilmeld Microsoft Defender for Endpoint macOS-enheder til Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

   :::image type="content" source="images/a347307458d6a9bbfa88df7dbe15398f.png" alt-text="Konfigurationsindstillinger1" lightbox="images/a347307458d6a9bbfa88df7dbe15398f.png":::

2. Vælg **+ Ny**.

   :::image type="content" source="images/b6c7ad56d50f497c38fc14c1e315456c.png" alt-text="Nær op til en logobeskrivelse genereres automatisk" lightbox="images/b6c7ad56d50f497c38fc14c1e315456c.png":::

3. I **Angiv modtagere for >** under **Mailadresser** skal du angive mailadresserne på modtagerne.

    :::image type="content" source="images/718b9d609f9f77c8b13ba88c4c0abe5d.png" alt-text="Konfigurationsindstillingerne2" lightbox="images/718b9d609f9f77c8b13ba88c4c0abe5d.png":::

    :::image type="content" source="images/ae3597247b6bc7c5347cf56ab1e820c0.png" alt-text="Konfigurationsindstillingerne3" lightbox="images/ae3597247b6bc7c5347cf56ab1e820c0.png":::

    For eksempel: janedoe@contoso.com

    :::image type="content" source="images/4922c0fcdde4c7f73242b13bf5e35c19.png" alt-text="Konfigurationsindstillingerne4" lightbox="images/4922c0fcdde4c7f73242b13bf5e35c19.png":::

4. Konfigurer meddelelsen for invitationen.

   :::image type="content" source="images/ce580aec080512d44a37ff8e82e5c2ac.png" alt-text="Konfigurationsindstillingerne5" lightbox="images/ce580aec080512d44a37ff8e82e5c2ac.png":::

   :::image type="content" source="images/5856b765a6ce677caacb130ca36b1a62.png" alt-text="Konfigurationsindstillingerne6" lightbox="images/5856b765a6ce677caacb130ca36b1a62.png":::

   :::image type="content" source="images/3ced5383a6be788486d89d407d042f28.png" alt-text="Konfigurationsindstillingerne7" lightbox="images/3ced5383a6be788486d89d407d042f28.png":::

   :::image type="content" source="images/54be9c6ed5b24cebe628dc3cd9ca4089.png" alt-text="Konfigurationsindstillingerne8" lightbox="images/54be9c6ed5b24cebe628dc3cd9ca4089.png":::

## <a name="enrollment-method-2-prestage-enrollments"></a>Registreringsmetode 2: Prestage-registreringer

1. Gå til **Prestage-Pro i sylteboardet**.

   :::image type="content" source="images/6fd0cb2bbb0e60a623829c91fd0826ab.png" alt-text="Konfigurationsindstillingerne9" lightbox="images/6fd0cb2bbb0e60a623829c91fd0826ab.png":::

2. Følg vejledningen i [Computer PreStage-tilmeldinger](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>Tilmeld macOS-enhed

1. Vælg **Fortsæt,** og installér nøglecentercertifikatet fra **vinduet Systemindstillinger** .

   :::image type="content" source="images/jamfpro-ca-certificate.png" alt-text="The Jamf Pro registrering1" lightbox="images/jamfpro-ca-certificate.png":::

2. Når nøglecentercertifikatet er installeret, skal du vende tilbage til browservinduet **og vælge Fortsæt** og installere MDM-profilen.

   :::image type="content" source="images/jamfpro-install-mdm-profile.png" alt-text="The Jamf Pro registrering2" lightbox="images/jamfpro-install-mdm-profile.png":::

3. Vælg **Tillad** at downloade fra SYLF.

   :::image type="content" source="images/jamfpro-download.png" alt-text="The Jamf Pro registrering3" lightbox="images/jamfpro-download.png":::

4. Vælg **Fortsæt** for at fortsætte med installationen af MDM-profilen.

   :::image type="content" source="images/jamfpro-install-mdm.png" alt-text="The Jamf Pro rollment4" lightbox="images/jamfpro-install-mdm.png":::

5. Vælg **Fortsæt** for at installere MDM-profilen.

   :::image type="content" source="images/jamfpro-mdm-unverified.png" alt-text="The Jamf Pro registrering5" lightbox="images/jamfpro-mdm-unverified.png":::

6. Vælg **Fortsæt**  for at fuldføre konfigurationen.

   :::image type="content" source="images/jamfpro-mdm-profile.png" alt-text="The Jamf Pro registrering6" lightbox="images/jamfpro-mdm-profile.png":::
