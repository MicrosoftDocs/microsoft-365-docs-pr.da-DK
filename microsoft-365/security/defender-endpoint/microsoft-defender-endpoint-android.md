---
title: Microsoft Defender til slutpunkt på Android
ms.reviewer: ''
description: Beskrivelse af, hvordan du installerer og bruger Microsoft Defender til Slutpunkt på Android
keywords: microsoft, defender, Microsoft Defender til Endpoint, android, installation, deploy, uninstallation, intune
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7d4e553e89f83f9b641367bb4037b4eb7da21f8b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63593190"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender til slutpunkt på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Defender til Slutpunkt på Android.

> [!CAUTION]
> Hvis du kører andre slutpunktsbeskyttelsesprodukter fra tredjepart sammen med Defender til Slutpunkt på Android, kan det sandsynligvis medføre problemer med ydeevnen og uforudsete systemfejl.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Sådan installerer du Microsoft Defender til Slutpunkt på Android

### <a name="prerequisites"></a>Forudsætninger

- **Til slutbrugere**:
  - Microsoft Defender for Endpoint-licens tildelt slutbrugeren/slutbrugerne af appen. Se [Licenskrav til Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Intune-firmaportal-appen kan downloades [fra Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) og er tilgængelig på Android-enheden.
  - Desuden kan enheder tilmeldes via appen [til](/mem/intune/user-help/enroll-device-android-company-portal) Intune-firmaportal at gennemtvinge politikker for overholdelse af enhed i Intune. Dette kræver, at slutbrugeren er tildelt en Microsoft Intune licens.
  - Du kan finde flere oplysninger om, hvordan du tildeler licenser, [under Tildel licenser til brugere](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **For administratorer**
   - Adgang til Microsoft 365 Defender portalen.
   - Adgang [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) til
       - Installér appen til tilmeldte brugergrupper i organisationen.
       - Konfigurer risikosignaler for Microsoft Defender til slutpunkt i beskyttelsespolitikken for apps.
  
    > [!NOTE]
    > - Microsoft Defender til Slutpunkt udvider nu beskyttelsen til en organisations data i et administreret program (MAM) for enheder, der ikke er tilmeldt administration af mobilenheder (MDM), men bruger Intune til at administrere mobilprogrammer. Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til [administration af mobilapps (MAM).](/mem/intune/apps/mam-faq)
    > - Desuden understøtter Microsoft Defender til slutpunkt allerede enheder, der er tilmeldt ved hjælp af Administration af mobilenheder i Intune (MDM).


### <a name="network-requirements"></a>Netværkskrav

- For at Microsoft Defender til Slutpunkt på Android kan fungere, når du har forbindelse til et netværk, skal firewallen/proxyen konfigureres til at aktivere adgangen til [URL-adresser for Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Systemkrav

- Mobiltelefoner, der kører Android 6.0 og derover. **Mobiltelefoner, der kører Android, tablets og andre mobilenheder, der kører Android, understøttes ikke i øjeblikket.**
- Intune-firmaportal-appen downloades fra [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) og installeres. Tilmelding af enheder er påkrævet, for at Politikker for overholdelse af enhed i Intune håndhæves.

### <a name="installation-instructions"></a>Installationsvejledning

Microsoft Defender til slutpunkt på Android understøtter installation på begge tilstande for enheder, der er tilmeldt – den ældre enhedsadministrator og Android Enterprise-tilstand. **Personligt ejet enheder med arbejdsprofil og virksomhedsejede fuldt administrerede tilmeldinger til brugerenheder understøttes i Android Enterprise. Understøttelse af andre Android Enterprise-tilstande annonceres, når den er klar.**

- Installation af Microsoft Defender til slutpunkt på Android er via Microsoft Intune (MDM). Få mere at vide under [Installér Microsoft Defender til Slutpunkt på Android med Microsoft Intune](android-intune.md).
- Installation af Microsoft Defender til slutpunkt på enheder, der ikke er tilmeldt ved hjælp af Administration af Intune-mobilenheder (MDM), skal du se Konfigurer [Microsoft Defender til slutpunkts risikosignaler i appbeskyttelsespolitik (MAM)](android-configure-mam.md).

> [!NOTE]
> **Microsoft Defender til slutpunkt på Android er tilgængelig på [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) nu.**
>
> Du kan oprette forbindelse til Google Play fra Intune for at installere Microsoft Defender til slutpunktsappen på tværs af tilstandene Enhedsadministrator og Android Enterprise-registrering.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Sådan konfigureres Microsoft Defender til slutpunkt på Android

Vejledning til, hvordan du konfigurerer Microsoft Defender til Slutpunkt på Android-funktioner er tilgængelig i [Konfigurer Microsoft Defender til Endpoint på Android-funktioner](android-configure.md).

## <a name="related-topics"></a>Relaterede emner

- [Installér Microsoft Defender til slutpunkt på Android med Microsoft Intune](android-intune.md)
- [Konfigurer Microsoft Defender til slutpunkt på Android-funktioner](android-configure.md)
- [Grundlæggende funktioner til administration af mobilapps (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
