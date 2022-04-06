---
title: Nyheder i Microsoft Defender til Slutpunkt på iOS
description: Få mere at vide om de større ændringer for tidligere versioner af Microsoft Defender til Slutpunkt på iOS.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, macos, whatsnew
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
ms.openlocfilehash: 503ae29fd371948f68b0c25aafe34f02f7bb8f1d
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63606489"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Nyheder i Microsoft Defender til Slutpunkt på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="improved-experience-on-supervised-ios-devices"></a>Forbedret oplevelse på overvågede iOS-enheder

Microsoft Defender til slutpunkt på iOS har nu en særlig mulighed for at overvåge iOS/iPadOS-enheder under forudsætning af de øgede administrationsfunktioner, der leveres af platformen på disse typer enheder. Det kan også levere Web Protection **uden at konfigurere et lokalt VPN på enheden**. Dette giver slutbrugerne en problemfri oplevelse, mens de stadig er beskyttet mod phishing og andre webbaserede angreb. Du kan finde flere oplysninger i [denne dokumentation](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Microsoft Defender til Slutpunkt er nu Microsoft Defender i App Store

Microsoft Defender til Slutpunkt er nu tilgængelig som **Microsoft Defender** i appbutikken. Med denne opdatering bliver appen tilgængelig som prøveversion for **forbrugere i USA**. Afhængigt af hvordan du logger på appen med din arbejdskonto eller personlige konto, har du adgang til funktioner for Microsoft Defender til Endpoint eller til funktioner for Microsoft Defender for enkeltpersoner. Du kan finde flere oplysninger i [denne blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Administration af trusler og sikkerhedsrisiko

Den 25. januar 2022 offentliggjorde vi den generelle tilgængelighed af administration af trusler og sikkerhedsrisiko på Android og iOS. Du kan finde flere oplysninger [i techcommunity-indlægget her](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1124210103"></a>1.1.24210103

- Løste problemer med internetforbindelsen på enheder, der overvåges. Du kan få mere at [vide under Deploy Defender til Slutpunkt på tilmeldte iOS-enheder](ios-install.md).
- Fejlrettelser.

## <a name="1123250104"></a>1.1.23250104

- Optimering af ydeevne – Test batteriets ydeevne med denne version, og fortæl os din feedback.
- Onboard uden touch til tilmeldte **iOS-enheder** – Med denne version er prøveversionen af zero-touch onboard for enheder, der er tilmeldt via Microsoft Endpoint Manager (Intune), blevet tilføjet. Du kan finde flere oplysninger i denne [dokumentation](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) for at få mere at vide om konfiguration og konfiguration.
- **Kontrolelementer til beskyttelse** af personlige oplysninger – Konfigurer kontrolelementer til beskyttelse af personlige oplysninger for rapport om phish-besked. Få mere at vide under [Konfigurer iOS-funktioner](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Fejlrettelser og forbedringer af ydeevnen 
  - Der blev foretaget optimeringer af ydeevnen i denne version. Test batteriets ydeevne med denne version, og fortæl os din feedback.

## <a name="1120240103"></a>1.1.20240103
- Enhedstilstandskort – Kortet Enhedstilstand giver slutbrugerne besked om ventende softwareopdateringer.
- Forbedringer af brugervenlighed – Slutbrugere kan nu deaktivere Defender for Endpoint VPN fra selve MSDefender-appen. Før denne opdatering var slutbrugere nødt til kun at deaktivere VPN fra Indstillinger app.
- Fejlrettelser.

## <a name="1120020101"></a>1.1.20020101
- Forbedringer af UX – Microsoft Defender til slutpunkt har fået et nyt udseende.
- Fejlrettelser.

## <a name="1117240101"></a>1.1.17240101
- Understøttelse af administration af mobilapps (MAM) via Intune er generelt tilgængelig med denne version. Få mere at vide under [Risikosignaler fra Microsoft Defender til Slutpunkt, der er tilgængelige for dine politikker for appbeskyttelse](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Jailbreak Detection** er generelt tilgængelig. Få mere at vide under [Konfigurer politik for betinget adgang baseret på risikosignaler for enheder](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatisk konfiguration af VPN-profilen** for tilmeldte enheder via Microsoft Endpoint Manager (Intune) er generelt tilgængelig. Få mere at vide under [Automatisk konfiguration af VPN-profil for tilmeldte iOS-enheder](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Fejlrettelser.

## <a name="1115140101"></a>1.1.15140101

- **Jailbreak Detection** er i preview. Få mere at vide under [Konfigurer politik for betinget adgang baseret på risikosignaler for enheder](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatisk konfiguration af VPN-profil** er i forhåndsvisning for tilmeldte enheder via Microsoft Endpoint Manager (Intune). Få mere at vide under [Automatisk konfiguration af VPN-profil for tilmeldte iOS-enheder](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Produktnavnet på Microsoft Defender ATP er nu blevet opdateret til Microsoft Defender for endpoint i appbutikken.
- Forbedret logonoplevelse.
- Fejlrettelser.

## <a name="1115010101"></a>1.1.15010101

- Med denne version annoncerer vi understøttelse af iPadOS/iPad enheder.
- Fejlrettelser.
