---
title: Microsoft Defender til slutpunkt – Mobile Threat Defense
ms.reviewer: ''
description: Oversigt over Mobile Threat Defense i Microsoft Defender til slutpunkt
keywords: mobil, defender, Microsoft Defender til Slutpunkt, ios, mtd, android, sikkerhed
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 07cd42d1ab1c6b945525b1e9ed4b463ee76376e1
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/14/2022
ms.locfileid: "63594638"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender til slutpunkt – Mobile Threat Defense

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender til slutpunkt på Android og iOS er vores **mobile trusselsforbehold (MTD)**. Typisk beskytter virksomheder proaktivt pc'er mod sårbarheder og angreb, mens mobilenheder ofte bliver overvåget og ubeskyttet. Hvis mobilplatforme har indbygget beskyttelse, f.eks. appisolation og har undersøgt forbrugerapplagre, forbliver disse platforme sårbar over for webbaserede eller andre avancerede angreb. Efterhånden som flere medarbejdere bruger enheder til arbejde og til at få adgang til følsomme oplysninger, er det af afgørende betydning, at virksomheder udruller en MTD-løsning for at beskytte enheder og dine ressourcer mod endnu mere avancerede angreb på mobil.

## <a name="key-capabilities"></a>Vigtige funktioner

Microsoft Defender til Slutpunkt på Android og iOS indeholder nedenstående vigtige funktioner. Du kan finde oplysninger om de nyeste funktioner og fordele ved at læse [vores meddelelser](https://aka.ms/mdeblog).

<br>

|Funktion|Beskrivelse|
|---|---|
|Webbeskyttelse|Antiphishing, blokering af usikre netværksforbindelser og understøttelse af brugerdefinerede indikatorer.|
|Malwarebeskyttelse (kun Android)|Scanning efter skadelige apps.|
|Jailbreak-registrering (kun iOS)|Registrering af jailbroken-enheder.|
|Administration af trusler og sikkerhedsrisiko (TVM) |Vurdering af sikkerhedsrisiko for onboardede mobilenheder. Besøg denne [side](next-gen-threat-and-vuln-mgt.md) for at få mere at vide Håndtering af trusler og sikkerhedsrisici i Microsoft Defender til slutpunkt. *Bemærk, at på iOS er det kun sikkerhedsrisici i operativsystemet, der understøttes i dette eksempel.*|
|Samlet advarsel|Beskeder fra alle platforme i den samlede M365-sikkerhedskonsol|
|Betinget adgang, Betinget start|Blokering af risikabelt udstyr fra at få adgang til virksomhedens ressourcer. Defender til Slutpunkt-risikosignaler kan også føjes til politikker for appbeskyttelse (MAM)|
|Kontrolelementer til beskyttelse af personlige oplysninger. I forhåndsvisning (se noten nedenfor)|Konfigurer beskyttelse af personlige oplysninger i trusselsrapporterne ved at kontrollere de data, der er sendt af Microsoft Defender til Slutpunkt. *Bemærk, at kontrolelementer til beskyttelse af personlige oplysninger i øjeblikket kun er tilgængelige for enheder, der er tilmeldt. Kontrolelementer til enheder, der ikke er tilmeldt, tilføjes senere*|
|Integration med Microsoft Tunnel|Kan integreres med Microsoft Tunnel, en VPN-gatewayløsning for at aktivere sikkerhed og forbindelse i en enkelt app. Kun tilgængelig på Android i øjeblikket|

Alle disse funktioner er tilgængelige for Microsoft Defender for slutbrugere af slutpunkter. Få mere at vide under [Licenskrav](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Oversigt og installation

Installation af Microsoft Defender til slutpunkt på mobil kan udføres via Microsoft Endpoint Manager (MEM). Se denne video for at få en hurtig oversigt over MTD-funktioner og -installation:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Installér

Følgende tabel opsummerer, hvordan du installerer Microsoft Defender til Slutpunkt på Android og iOS. Hvis du vil have detaljeret dokumentation, skal du se 
- [Oversigt over Microsoft Defender til slutpunkt på Android](microsoft-defender-endpoint-android.md), og
- [Oversigt over Microsoft Defender til slutpunkt på iOS](microsoft-defender-endpoint-ios.md)

**Android**

|Registreringstype     |Detaljer      |
|--------------------|-------------|
|Android Enterprise med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Installér på Android Enterprise-enheder, der er tilmeldt](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Enhedsadministrator med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Installér på enheder, der er tilmeldt Enhedsadministrator](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Ikke-administrerede BYOD ELLER-enheder, der administreres af andre Unified Endpoint Managers/Setup app protection policy (MAM)|[Konfigurer Defender-risikosignaler i appbeskyttelsespolitik (MAM)](android-configure-mam.md)|

**iOS**

|Registreringstype     |Detaljer      |
|--------------------|-------------|
|Overvågede enheder med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|1. [Installér som iOS Store-app](ios-install.md)<br/>2. [Konfiguration af Webbeskyttelse uden VPN til overvågede iOS-enheder](ios-install.md#complete-deployment-for-supervised-devices)|
|Ikke-uperviserede (BYOD)-enheder, der er tilmeldt Intune UEM (Microsoft Endpoint Manager)|[Installér som iOS Store-app](ios-install.md)|
|Ikke-administrerede BYOD OR-enheder administreret af andre UEMs/Setup app protection policy (MAM)|[Konfigurer Defender-risikosignaler i appbeskyttelsespolitik (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Onboarding til slutbruger

- [Konfigurer onboarding uden touch til iOS-tilmeldte](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) enheder: Administratorer kan konfigurere installationen af nul-touch til automatisk at onboarde Microsoft Defender til slutpunkt på tilmeldte iOS-enheder, uden at brugeren er nødt til at åbne appen. 

- [Konfigurer Betinget adgang for at gennemtvinge bruger-onboarding](android-configure.md#conditional-access-with-defender-for-endpoint-on-android): Dette kan anvendes for at sikre onboarding af slutbrugere i Microsoft Defender for Endpoint-appen efter udrulning. Watch this video for a quick demo on configuring conditional access with Defender for Endpoint risk signals. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Gør onboarding nemmere

- [iOS – Zero-Touch onboard](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview)
- [Android Enterprise – Setup Always-on VPN](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS – Automatisk konfiguration af VPN-profil](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Pilotevaluering

Når du vurderer mobiltrusler mod forsvar med Microsoft Defender til slutpunkt, kan du kontrollere, at visse kriterier er opfyldt, før du fortsætter med at installere tjenesten på et større sæt enheder. Du kan definere udgangskriterierne og sikre, at de er opfyldt, før de implementeres i stor udstrækning.

Dette er med til at reducere potentielle problemer, der kan opstå under udrulningen af tjenesten. Her er nogle test og exit-kriterier, som måske kan hjælpe:

- Enheder vises på lagerlisten for enheder: Når onboarding af Defender til slutpunkt er udført på mobilenheden, skal du kontrollere, at enheden er angivet i Lagerenhed i [sikkerhedskonsollen](https://security.microsoft.com).

- Kør en test til registrering af malware på en Android-enhed: Installer en testvirusapp fra Google Play Butik, og bekræft, at den bliver registreret af Microsoft Defender til slutpunkt. Her er en eksempelapp, der kan bruges til denne test: [Testvirus](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). Bemærk, at på Android Enterprise med en arbejdsprofil understøttes kun arbejdsprofilen.

- Kør en phishingtest: Find og bekræft https://smartscreentestratings2.net , at det bliver blokeret af Microsoft Defender til slutpunkt. Bemærk, at på Android Enterprise med en arbejdsprofil understøttes kun arbejdsprofilen.

- Beskeder vises i dashboard: Kontrollér, at beskeder for ovenstående registreringstest vises på [sikkerhedskonsollen](https://security.microsoft.com).

## <a name="configure"></a>Konfigurer

- [Konfigurer Android-funktioner](android-configure.md)
- [Konfigurer iOS-funktioner](ios-configure-features.md)
- [Konfigurer Webbeskyttelse uden VPN til overvågede iOS-enheder](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Ressourcer

- [Microsoft Defender til slutpunkt på Android](microsoft-defender-endpoint-android.md)
- [Microsoft Defender til Slutpunkt på iOS](microsoft-defender-endpoint-ios.md)
- Hold dig informeret om kommende udgivelser ved at læse [vores meddelelser](https://aka.ms/mdeblog).

