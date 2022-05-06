---
title: Microsoft Defender for Endpoint på Android
ms.reviewer: ''
description: Beskriver, hvordan du installerer og bruger Microsoft Defender for Endpoint på Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, android, installation, installere, afinstallation, intune
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
ms.openlocfilehash: 51f4915da08920018526ac7eb17372247e28de6d
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243090"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender for Endpoint på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Defender for Endpoint på Android.

> [!CAUTION]
> Kørsel af andre tredjepartsbeskyttelsesprodukter til slutpunkter sammen med Defender for Endpoint på Android vil sandsynligvis medføre problemer med ydeevnen og uforudsigelige systemfejl.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Sådan installerer du Microsoft Defender for Endpoint på Android

### <a name="prerequisites"></a>Forudsætninger

- **For slutbrugere**:
  - Microsoft Defender for Endpoint licens, der er tildelt slutbrugerne af appen. Se [Microsoft Defender for Endpoint licenskrav](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).
  - Intune licens er nødvendig, før du onboarder Android-enheder.
  - Intune-firmaportal app kan downloades fra [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) og er tilgængelig på Android-enheden.
  - Derudover kan enheder [tilmeldes](/mem/intune/user-help/enroll-device-android-company-portal) via Intune-firmaportal-appen for at gennemtvinge Intune politikker for enhedsoverholdelse. Dette kræver, at slutbrugeren tildeles en Microsoft Intune licens.
  - Du kan få flere oplysninger om, hvordan du tildeler licenser, under [Tildel licenser til brugere](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **Til administratorer**
   - Adgang til Microsoft 365 Defender-portalen.
   - Få [adgang Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) til
       - Udrul appen til tilmeldte brugergrupper i din organisation.
       - Konfigurer Microsoft Defender for Endpoint risikosignaler i beskyttelsespolitikken for apps.
  
    > [!NOTE]
    > - Microsoft Defender for Endpoint nu udvider beskyttelsen til en organisations data i et administreret program (MAM) for enheder, der ikke er tilmeldt ved hjælp af MDM (Mobile Device Management), men bruger Intune til at administrere mobilapps. Denne support udvides også til kunder, der bruger andre løsninger til administration af virksomhedsmobilitet, mens de stadig bruger Intune til [administration af mobilapps (MAM).](/mem/intune/apps/mam-faq)
    > - Derudover understøtter Microsoft Defender for Endpoint allerede enheder, der er tilmeldt ved hjælp af Intune administration af mobilenheder (MDM).


### <a name="network-requirements"></a>Netværkskrav

- Hvis Microsoft Defender for Endpoint på Android skal fungere, når der er oprettet forbindelse til et netværk, skal firewallen/proxyen konfigureres for at [give adgang til Microsoft Defender for Endpoint tjeneste-URL-adresser](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Systemkrav

- Mobiltelefoner, der kører Android 6.0 og nyere. **Mobiltelefoner, der kører Android Go, tablets og andre mobilenheder, der kører Android, understøttes ikke i øjeblikket.**
- Intune-firmaportal app downloades fra [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) og installeres. Tilmelding af en enhed er påkrævet, for at Intune politikker for enhedsoverholdelse gennemtvinges.

### <a name="installation-instructions"></a>Installationsvejledning

Microsoft Defender for Endpoint på Android understøtter installation på begge tilstande for tilmeldte enheder – den ældre enhedsadministrator- og Android Enterprise-tilstand. **I øjeblikket understøttes personligt ejede enheder med arbejdsprofil og virksomhedsejede fuldt administrerede brugerenhedsregistreringer i Android Enterprise. Understøttelse af andre Android Enterprise-tilstande vil blive annonceret, når du er klar.**

- Installation af Microsoft Defender for Endpoint på Android sker via Microsoft Intune (MDM). Du kan få flere oplysninger under [Installér Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md).
- Installation af Microsoft Defender for Endpoint på enheder, der ikke er tilmeldt ved hjælp af Intune MDM (Mobile Device Management), skal du se [Konfigurer Microsoft Defender for Endpoint risikosignaler i MAM (App Protection Policy).](android-configure-mam.md)

> [!NOTE]
> **Microsoft Defender for Endpoint på Android er tilgængelig på [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) nu.**
>
> Du kan oprette forbindelse til Google Play fra Intune for at installere Microsoft Defender for Endpoint app på tværs af enhedsadministrator- og Android Enterprise-tilmeldingstilstande.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Sådan konfigurerer du Microsoft Defender for Endpoint på Android

Vejledning til, hvordan du konfigurerer Microsoft Defender for Endpoint på Android-funktioner, er tilgængelig i [Konfigurer Microsoft Defender for Endpoint på Android-funktioner](android-configure.md).

## <a name="related-topics"></a>Relaterede emner

- [Installér Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md)
- [Konfigurer Microsoft Defender for Endpoint på Android-funktioner](android-configure.md)
- [Grundlæggende om administration af mobilapps (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
