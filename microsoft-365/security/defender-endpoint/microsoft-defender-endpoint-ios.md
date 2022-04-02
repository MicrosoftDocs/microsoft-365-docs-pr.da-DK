---
title: Microsoft Defender til Slutpunkt på iOS
ms.reviewer: ''
description: Beskrivelse af, hvordan du installerer og bruger Microsoft Defender til Slutpunkt på iOS
keywords: microsoft, defender, Microsoft Defender til Endpoint, ios, overview, installation, deploy, uninstallation, intune
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
ms.openlocfilehash: c144eb3cd0cec2d96f20294475618e7e9c49c816
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63603146"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender til Slutpunkt på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Microsoft Defender til Slutpunkt på iOS tilbyder** beskyttelse mod phishing og usikre netværksforbindelser fra websteder, mails og apps. Alle beskeder vil være tilgængelige via en enkelt rude med glas i Microsoft 365 Defender portal. Portalen giver sikkerhedsteams et centralt overblik over trusler på iOS-enheder sammen med andre platforme.

> [!CAUTION]
> Hvis du kører andre slutpunktsbeskyttelsesprodukter fra tredjepart sammen med Defender for Endpoint på iOS, kan det sandsynligvis medføre problemer med ydeevnen og uforudsete systemfejl.

## <a name="pre-requisites"></a>Forudsætninger

**For slutbrugere**

- Microsoft Defender for Endpoint-licens tildelt slutbrugeren/slutbrugerne af appen. Se [Licenskrav til Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **For tilmeldte enheder**:
    - Enheder er tilmeldt via [appen Intune-firmaportal](/mem/intune/user-help/enroll-your-device-in-intune-ios) at gennemtvinge politikker for overholdelse af enhed i Intune. Dette kræver, at slutbrugeren er tildelt en Microsoft Intune licens.
    - Intune-firmaportal-appen kan downloades fra [Apple App-Store](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Apple tillader ikke, at brugere omdirigeres for at downloade andre apps fra App Store, så dette trin skal udføres af brugeren, før onboarding til Microsoft Defender for Endpoint-appen.
    
    - Enheder er registreret hos Azure Active Directory. Dette kræver, at slutbrugeren er logget på [Microsoft Authenticator-appen](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **For enheder, der ikke er tilmeldt**: Enheder er registreret med Azure Active Directory. Dette kræver, at slutbrugeren er logget på [Microsoft Authenticator-appen](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Du kan finde flere oplysninger om, hvordan du tildeler licenser, [under Tildel licenser til brugere](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**For administratorer**

- Adgang til Microsoft 365 Defender portalen.

- Adgang [Microsoft Endpoint Manager Administration til](https://go.microsoft.com/fwlink/?linkid=2109431) at:
   - Installér appen til tilmeldte brugergrupper i organisationen.
   - Konfigurer risikosignaler for Microsoft Defender til slutpunkt i appbeskyttelsespolitik (MAM)


    > [!NOTE]
    > - Microsoft Defender til slutpunkt udvider nu beskyttelsen til en organisations data i et administreret program for dem, der ikke bruger administration af mobilenheder (MDM), men bruger Intune til at administrere mobilprogrammer. Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til [administration af mobilapps (MAM).](/mem/intune/apps/mam-faq)
    > - Desuden understøtter Microsoft Defender til slutpunkt allerede enheder, der er tilmeldt ved hjælp af Administration af mobilenheder i Intune (MDM).  

**Systemkrav**

- iOS-enhed, der kører iOS 12.0 og derover. iPads understøttes også. *Bemærk, at fra 31-marts 2022 vil det mindste understøttede iOS-version af Microsoft Defender til Slutpunkt være iOS 13.0.*

- Enheden er enten tilmeldt appen Intune-firmaportal [eller](https://apps.apple.com/us/app/intune-company-portal/id719171358) er registreret hos Azure Active Directory via [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) med den samme konto.

## <a name="installation-instructions"></a>Installationsvejledning

Installation af Microsoft Defender til slutpunkt på iOS kan udføres via Microsoft Endpoint Manager (MEM), og både overvågede og ikke-overvågede enheder understøttes. Slutbrugere kan også installere appen direkte fra [Apple App Store](https://aka.ms/mdatpiosappstore).

- Du kan finde oplysninger om installation på tilmeldte enheder via Microsoft Endpoint Manager eller Intune under [Deploy Microsoft Defender for Endpoint på iOS](ios-install.md).
- Du kan finde oplysninger om brug af Defender til slutpunkt i appbeskyttelsespolitik (MAM) i Konfigurer beskyttelsespolitik for apps til at medtage [Defender til slutpunkt-risikosignaler (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>Ressourcer

- Få besked om kommende udgivelser [ved at gå til Nyheder i Microsoft Defender til endpoint på iOS](ios-whatsnew.md) eller vores [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Giv feedback via feedbacksystemet i appen eller via den [samlede sikkerhedskonsol](https://security.microsoft.com)

## <a name="next-steps"></a>Næste trin

- [Installér Microsoft Defender til Slutpunkt på iOS via Intune til tilmeldte enheder](ios-install.md)
- [Konfigurer politik for appbeskyttelse til at medtage Defender til slutpunkt-risikosignaler (MAM)](ios-install-unmanaged.md)
- [Konfigurer Microsoft Defender til slutpunkt på iOS-funktioner](ios-configure-features.md)
- [Konfigurer betinget Access-politik baseret på risikoscore for enheder fra Microsoft Defender til Slutpunkt](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Grundlæggende funktioner til administration af mobilapps (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
