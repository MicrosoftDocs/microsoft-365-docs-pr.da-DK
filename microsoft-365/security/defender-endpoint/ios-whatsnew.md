---
title: Nyheder i Microsoft Defender for Endpoint på iOS
description: Få mere at vide om de overordnede ændringer af tidligere versioner af Microsoft Defender for Endpoint på iOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 7f3a687eb365813192948e48514bf7384cc584d0
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188175"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Nyheder i Microsoft Defender for Endpoint på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


## <a name="integration-with-tunnel"></a>Integration med Tunnel
Microsoft Defender for Endpoint på iOS kan nu integreres med Microsoft Tunnel, en VPN-gatewayløsning, der muliggør sikkerhed og forbindelse i en enkelt app.  Integration med Tunnel giver en enklere og sikker VPN-oplevelse på iOS med kun én app. Denne funktion var tidligere kun tilgængelig på Android. Du kan finde flere oplysninger [i techcommunity-indlægget her](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Forbedret oplevelse på overvågede iOS-enheder

Microsoft Defender for Endpoint på iOS har nu specialiseret sig i overvågede iOS-/iPadOS-enheder på grund af de øgede administrationsfunktioner, der leveres af platformen på disse typer enheder. Den kan også levere webbeskyttelse **uden at konfigurere en lokal VPN-forbindelse på enheden**. Dette giver slutbrugerne en problemfri oplevelse, mens de stadig er beskyttet mod phishing og andre webbaserede angreb. Du kan finde flere oplysninger i [denne dokumentation](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender for Endpoint er nu Microsoft Defender i App Store

Microsoft Defender for Endpoint er nu tilgængelig som **Microsoft Defender** i appbutikken. Med denne opdatering er appen tilgængelig som prøveversion for **forbrugere i området USA**. Afhængigt af hvordan du logger på appen med din arbejdskonto eller personlige konto, har du adgang til funktioner til Microsoft Defender for Endpoint eller funktioner til Microsoft Defender for enkeltpersoner. Du kan få flere oplysninger på [denne blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Trussels- og sårbarhedsstyring

Den 25. januar 2022 annoncerede vi den generelle tilgængelighed af trussels- og sårbarhedsstyring på Android og iOS. Du kan finde flere oplysninger [i techcommunity-indlægget her](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).


## <a name="1128250101"></a>1.1.28250101
- **Integration med Tunnel** – Microsoft Defender for Endpoint på iOS kan nu integreres med Microsoft Tunnel, en VPN-gatewayløsning, der muliggør sikkerhed og forbindelse i en enkelt app. Du kan få flere oplysninger under [Oversigt over Microsft Tunnel](/mem/intune/protect/microsoft-tunnel-overview).
- **Onboard zero-touch for tilmeldte iOS-enheder**, der er tilmeldt via Microsoft Endpoint Manager (Intune), er offentligt tilgængelig. Du kan få flere oplysninger under [Onboarding af Microsoft Defender for Endpoint uden berøring](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint).
- Fejlrettelser.


## <a name="1124210103"></a>1.1.24210103

- Løste problemer med internetforbindelsen på overvågede enheder. Du kan finde flere oplysninger under [Installér Defender for Endpoint på tilmeldte iOS-enheder](ios-install.md).
- Fejlrettelser.

## <a name="1123250104"></a>1.1.23250104

- Optimering af ydeevnen – Test batteriydeevnen med denne version, og fortæl os din feedback.
- **Zero-touch onboard for tilmeldte iOS-enheder** – Med denne version er prøveversionen af Zero-touch onboard for enheder, der er tilmeldt via Microsoft Endpoint Manager (Intune) blevet tilføjet. Du kan finde flere oplysninger i denne [dokumentation](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) for at få flere oplysninger om konfiguration.
- **Kontrolelementer til beskyttelse af personlige oplysninger** – Konfigurer kontrolelementer til beskyttelse af personlige oplysninger for rapporten over phishbeskeder. Du kan få flere oplysninger under [Konfigurer iOS-funktioner](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Forbedringer af fejlrettelser og ydeevne 
  - Der blev foretaget optimeringer af ydeevnen i denne version. Test batteriydeevnen med denne version, og giv os din feedback.

## <a name="1120240103"></a>1.1.20240103
- Kortet Device Health – Enhedens tilstandskort giver slutbrugerne besked om eventuelle ventende softwareopdateringer.
- Forbedringer af anvendelighed – Slutbrugere kan nu deaktivere Defender for Endpoint VPN fra selve MSDefender-appen. Før denne opdatering skulle slutbrugerne kun deaktivere VPN fra Indstillinger-appen.
- Fejlrettelser.

## <a name="1120020101"></a>1.1.20020101
- Forbedringer af UX – Microsoft Defender for Endpoint har fået et nyt udseende.
- Fejlrettelser.

## <a name="1117240101"></a>1.1.17240101
- Understøttelse af MAM (Mobile Application Management) via Intune er offentlig tilgængelig med denne version. Du kan få flere oplysninger under [Microsoft Defender for Endpoint risikosignaler, der er tilgængelige for dine Appbeskyttelse politikker](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Jailbreak Detection** er generelt tilgængelig. Du kan få flere oplysninger under [Konfiguration af politik for betinget adgang baseret på enhedsrisikosignaler](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatisk konfiguration af VPN-profilen** for tilmeldte enheder via Microsoft Endpoint Manager (Intune) er offentlig tilgængelig. Du kan få flere oplysninger under [Automatisk konfiguration af VPN-profil for tilmeldte iOS-enheder](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Fejlrettelser.

## <a name="1115140101"></a>1.1.15140101

- **Jailbreak Detection** fås som prøveversion. Du kan få flere oplysninger under [Konfiguration af politik for betinget adgang baseret på enhedsrisikosignaler](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatisk konfiguration af VPN-profil** er en prøveversion for tilmeldte enheder via Microsoft Endpoint Manager (Intune). Du kan få flere oplysninger under [Automatisk konfiguration af VPN-profil for tilmeldte iOS-enheder](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Microsoft Defender ATP-produktnavnet er nu blevet opdateret til Microsoft Defender for Endpoint i appbutikken.
- Forbedret logonoplevelse.
- Fejlrettelser.

## <a name="1115010101"></a>1.1.15010101

- Med denne version annoncerer vi understøttelse af iPadOS/iPad enheder.
- Fejlrettelser.
