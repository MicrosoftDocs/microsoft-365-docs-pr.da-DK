---
title: Microsoft Defender for Endpoint på iOS
ms.reviewer: ''
description: Beskriver, hvordan du installerer og bruger Microsoft Defender for Endpoint på iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, overview, installation, deploy, uninstallation, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ac2c34359686da45998fab1076b7501357651318
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695856"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender for Endpoint på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Microsoft Defender for Endpoint på iOS** giver beskyttelse mod phishing og usikre netværksforbindelser fra websteder, mails og apps. Alle beskeder vil være tilgængelige via en enkelt rude i Microsoft 365 Defender-portalen. Portalen giver sikkerhedsteams en central visning af trusler på iOS-enheder sammen med andre platforme.

> [!CAUTION]
> Kørsel af andre tredjepartsbeskyttelsesprodukter til slutpunkter sammen med Defender for Endpoint på iOS vil sandsynligvis medføre problemer med ydeevnen og uforudsigelige systemfejl.

## <a name="prerequisites"></a>Forudsætninger

**Til slutbrugere**

- Microsoft Defender for Endpoint licens, der er tildelt slutbrugerne af appen. Se [Microsoft Defender for Endpoint licenskrav](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **For tilmeldte enheder**:
    - Enheder [tilmeldes](/mem/intune/user-help/enroll-your-device-in-intune-ios) via appen Intune-firmaportal for at gennemtvinge Intune politikker for enhedsoverholdelse. Dette kræver, at slutbrugeren tildeles en Microsoft Intune licens.
    - Intune-firmaportal app kan downloades fra [Apple App Store](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Apple tillader ikke, at omdirigering af brugere downloader andre apps fra appbutikken, så dette trin skal udføres af brugeren, før brugeren onboarder til Microsoft Defender for Endpoint app.)


    - Enheder er registreret i Azure Active Directory. Dette kræver, at slutbrugeren er logget på via [Microsoft Authenticator-appen](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **For ikke-tilmeldte enheder**: Enheder er registreret i Azure Active Directory. Dette kræver, at slutbrugeren er logget på via [Microsoft Authenticator-appen](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Du kan få flere oplysninger om, hvordan du tildeler licenser, under [Tildel licenser til brugere](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Til administratorer**

- Adgang til Microsoft 365 Defender-portalen.

- Adgang til [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) til:
   - Udrul appen til tilmeldte brugergrupper i din organisation.
   - Konfigurer Microsoft Defender for Endpoint risikosignaler i MAM (App Protection Policy)


    > [!NOTE]
    > - Microsoft Defender for Endpoint nu udvider beskyttelsen til en organisations data i et administreret program for dem, der ikke bruger MDM (Mobile Device Management), men bruger Intune til at administrere mobilapps. Denne support udvides også til kunder, der bruger andre løsninger til administration af virksomhedsmobilitet, mens de stadig bruger Intune til [administration af mobilapps (MAM).](/mem/intune/apps/mam-faq)
    > - Derudover understøtter Microsoft Defender for Endpoint allerede enheder, der er tilmeldt ved hjælp af Intune administration af mobilenheder (MDM).  

**Systemkrav**

- iOS-enhed, der kører iOS 12.0 og nyere. iPads understøttes også. *Bemærk, at fra den 31. marts 2022 er den mindste understøttede iOS-version fra Microsoft Defender for Endpoint iOS 13.0.*

- Enheden er enten tilmeldt [Intune-firmaportal-appen](https://apps.apple.com/us/app/intune-company-portal/id719171358) eller er registreret i Azure Active Directory via [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) med den samme konto.

 > [!NOTE]
 > Microsoft Defender for Endpoint på iOS understøttes ikke i øjeblikket, når du bruger iOS-brugertilmelding.

## <a name="installation-instructions"></a>Installationsvejledning

Installation af Microsoft Defender for Endpoint på iOS kan udføres via Microsoft Endpoint Manager (MEM), og både overvågede og ikke-overvågede enheder understøttes. Slutbrugere kan også installere appen direkte fra [Apple App Store](https://aka.ms/mdatpiosappstore).

- Du kan få oplysninger om installation på tilmeldte enheder via Microsoft Endpoint Manager eller Intune under [Udrul Microsoft Defender for Endpoint på iOS](ios-install.md).
- Du kan finde oplysninger om brug af Defender for Endpoint i MAM (App Protection Policy) under [Konfigurer beskyttelsespolitik for apps til at inkludere MAM (Defender for Endpoint Risk Signals)](ios-install-unmanaged.md)

## <a name="resources"></a>Ressourcer

- Hold dig orienteret om kommende udgivelser ved at gå til [Nyheder i Microsoft Defender for Endpoint på iOS](ios-whatsnew.md) eller på vores [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Giv feedback via et feedbacksystem i appen eller via [den samlede sikkerhedskonsol](https://security.microsoft.com)

## <a name="next-steps"></a>Næste trin

- [Udrul Microsoft Defender for Endpoint på iOS via Intune til tilmeldte enheder](ios-install.md)
- [Konfigurer beskyttelsespolitikken for apps, så den omfatter Defender for Endpoint-risikosignaler (MAM)](ios-install-unmanaged.md)
- [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
- [Konfigurer politik for betinget adgang baseret på enhedens risikoscore fra Microsoft Defender for Endpoint](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Grundlæggende om administration af mobilapps (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
