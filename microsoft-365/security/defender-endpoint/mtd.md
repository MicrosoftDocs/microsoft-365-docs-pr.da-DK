---
title: Microsoft Defender for Endpoint – Mobile Threat Defense
ms.reviewer: ''
description: Oversigt over Mobile Threat Defense i Microsoft Defender for Endpoint
keywords: mobil, defender, Microsoft Defender for Endpoint, ios, mtd, android, sikkerhed
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
ms.openlocfilehash: 36b7703aeaf0fdf4ff30c9bd0dd1486ebe27f618
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923126"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Microsoft Defender for Endpoint – Mobile Threat Defense

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender for Endpoint på Android og iOS er vores **MTD (Mobile Threat Defense Solution).** Virksomheder er typisk proaktive i forhold til at beskytte pc'er mod sårbarheder og angreb, mens mobilenheder ofte ikke overvåges og beskyttes. Hvor mobilplatforme har indbygget beskyttelse, f.eks. appisolation og overvågede forbrugerappbutikker, forbliver disse platforme sårbare over for webbaserede eller andre avancerede angreb. Efterhånden som flere medarbejdere bruger enheder til arbejde og til at få adgang til følsomme oplysninger, er det altafgørende, at virksomheder udruller en MTD-løsning for at beskytte enheder og dine ressourcer mod stadig mere avancerede angreb på mobilenheder.

## <a name="key-capabilities"></a>Nøglefunktioner

Microsoft Defender for Endpoint på Android og iOS indeholder nedenstående vigtige funktioner. Du kan finde oplysninger om de nyeste funktioner og fordele ved at læse vores [meddelelser](https://aka.ms/mdeblog).

<br>

|Kapacitet|Beskrivelse|
|---|---|
|Webbeskyttelse|Anti-phishing, blokering af usikre netværksforbindelser og understøttelse af brugerdefinerede indikatorer.|
|Beskyttelse mod skadelig software (kun Android)|Søger efter skadelige apps.|
|Jailbreak Detection (kun iOS)|Registrering af jailbrokenenheder.|
|Trussels- og sårbarhedsstyring (TVM) |Vurdering af sårbarheder for onboardede mobilenheder. Besøg denne [side](next-gen-threat-and-vuln-mgt.md) for at få mere at vide om administration af trusler og sårbarheder i Microsoft Defender for Endpoint. *Bemærk, at i iOS understøttes kun sikkerhedsrisici i operativsystemet i denne prøveversion.*|
|Netværksbeskyttelse *(offentlig prøveversion)*| Beskyttelse mod rogue Wi-Fi relaterede trusler og rogue certifikater; mulighed for at tillade liste over rodnøglecenter- og private rodnøglecentercertifikater i Intune; etablere tillid med slutpunkter.|
|Unified Alerting|Beskeder fra alle platforme i den samlede M365-sikkerhedskonsol|
|Betinget adgang, betinget start|Blokering af risikable enheder i at få adgang til virksomhedens ressourcer. Defender for Endpoint-risikosignaler kan også føjes til politikker for appbeskyttelse (MAM)|
|Kontrolelementer til beskyttelse af personlige oplysninger. I eksempelvisning (se note nedenfor)|Konfigurer beskyttelse af personlige oplysninger i trusselsrapporterne ved at styre de data, der sendes af Microsoft Defender for Endpoint. *Bemærk, at kontrolelementer til beskyttelse af personlige oplysninger i øjeblikket kun er tilgængelige for tilmeldte enheder. Kontrolelementer for ikke-tilmeldte enheder tilføjes senere*|
|Integration med Microsoft Tunnel|Kan integrere med Microsoft Tunnel, en VPN-gatewayløsning for at aktivere sikkerhed og forbindelse i en enkelt app. Tilgængelig på Android og er nu også offentlig tilgængelig på iOS.|

Alle disse funktioner er tilgængelige for licensindehavere af Microsoft Defender for Endpoint. Du kan få flere oplysninger under [Licenskrav](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Oversigt og udrul

Installation af Microsoft Defender for Endpoint på mobil kan udføres via Microsoft Endpoint Manager (MEM). Se denne video for at få et hurtigt overblik over MTD-funktioner og -udrulning:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Rul ud

I følgende tabel opsummeres det, hvordan du installerer Microsoft Defender for Endpoint på Android og iOS. Du kan finde en detaljeret dokumentation under 
- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md) og
- [Oversigt over Microsoft Defender for Endpoint på iOS](microsoft-defender-endpoint-ios.md)

**Android**

|Tilmeldingstype     |Detaljer      |
|--------------------|-------------|
|Android Enterprise med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Installér på tilmeldte Android Enterprise-enheder](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Enhedsadministrator med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Installér på de enheder, der er tilmeldt af enhedsadministratoren](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Ikke-administrerede BYOD ELLER-enheder, der administreres af andre Unified Endpoint Managers/Setup App Protection Policy (MAM)|[Konfigurer Defender-risikosignaler i appbeskyttelsespolitikken (MAM)](android-configure-mam.md)|

**Ios**

|Tilmeldingstype     |Detaljer      |
|--------------------|-------------|
|Overvågede enheder med Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|1. [Udrul som iOS Store-app](ios-install.md)<br/>2. [Konfigurer webbeskyttelse uden VPN til overvågede iOS-enheder](ios-install.md#complete-deployment-for-supervised-devices)|
|BYOD-enheder (Unsupervised) tilmeldt med Intune UEM (Microsoft Endpoint Manager)|[Udrul som iOS Store-app](ios-install.md)|
|Ikke-administrerede BYOD ELLER-enheder, der administreres af andre VM'er/konfiguration af appbeskyttelsespolitik (MAM)|[Konfigurer Defender-risikosignaler i appbeskyttelsespolitikken (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Onboarding af slutbrugere

- [Konfigurer Zero-touch onboard for iOS-tilmeldte enheder](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint): Administratorer kan konfigurere zero-touch-installation til uovervåget onboarding af Microsoft Defender for Endpoint på tilmeldte iOS-enheder, uden at brugeren skal åbne appen. 

- [Konfigurer betinget adgang for at gennemtvinge bruger onboarding](android-configure.md#conditional-access-with-defender-for-endpoint-on-android): Dette kan anvendes for at sikre, at slutbrugere onboardes til Microsoft Defender for Endpoint-appen efter installation. Se denne video for at få en hurtig demo om konfiguration af betinget adgang med Defender for Endpoint-risikosignaler. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Gør onboarding mere enkel

- [iOS – Zero-Touch onboardet](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint)
- [Android Enterprise – Konfigurer Vpn, der altid er aktiveret](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS – Automatisk konfiguration af VPN-profil](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Pilotevaluering

Når du evaluerer forsvar af mobiltrusler med Microsoft Defender for Endpoint, kan du kontrollere, at visse kriterier er opfyldt, før du fortsætter med at udrulle tjenesten på et større sæt enheder. Du kan definere afslutningskriterierne og sikre, at de er opfyldt, før du udruller bredt.

Dette hjælper med at reducere potentielle problemer, der kan opstå, når tjenesten udrulles. Her er nogle test og afslutningskriterier, der kan hjælpe:

- Enheder vises på listen over enheders lager: Når onboarding af Defender for Endpoint på mobilenheden er fuldført, skal du kontrollere, at enheden er angivet i enhedsoversigten i [sikkerhedskonsollen](https://security.microsoft.com).

- Kør en test til registrering af malware på en Android-enhed: Installer en hvilken som helst testvirusapp fra Google Play Store, og kontrollér, at den registreres af Microsoft Defender for Endpoint. Her er et eksempel på en app, der kan bruges til denne test: [Test virus](https://play.google.com/store/apps/details?id=com.antivirus&hl=en_US&gl=US). Bemærk, at det kun er arbejdsprofilen, der understøttes på Android Enterprise med en arbejdsprofil.

- Kør en phishing-test: Gå til , https://smartscreentestratings2.net og bekræft, at den bliver blokeret af Microsoft Defender for Endpoint. Bemærk, at det kun er arbejdsprofilen, der understøttes på Android Enterprise med en arbejdsprofil.

- Beskeder vises i dashboardet: Kontrollér, at beskeder om ovenstående registreringstest vises på [sikkerhedskonsollen](https://security.microsoft.com).

## <a name="configure"></a>Konfigurer

- [Konfigurer Android-funktioner](android-configure.md)
- [Konfigurer iOS-funktioner](ios-configure-features.md)
- [Konfigurer webbeskyttelse uden VPN for overvågede iOS-enheder](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Ressourcer

- [Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Microsoft Defender for Endpoint på iOS](microsoft-defender-endpoint-ios.md)
- Hold dig orienteret om kommende udgivelser ved at læse vores [meddelelser](https://aka.ms/mdeblog).

