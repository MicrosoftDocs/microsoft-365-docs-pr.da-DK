---
title: Nyheder i Microsoft Defender til slutpunkt på Android
description: Få mere at vide om de større ændringer for tidligere versioner af Microsoft Defender til Slutpunkt på Android.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d250fefbdcc2c268563b6321ee7d91eca4881063
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606756"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Nyheder i Microsoft Defender til slutpunkt på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Microsoft Defender til Slutpunkt er nu Microsoft Defender i Play Store

Microsoft Defender til Slutpunkt er nu tilgængelig som **Microsoft Defender** i Play Store. Med denne opdatering bliver appen tilgængelig som **prøveversion for forbrugere** i USA – afhængigt af hvordan du logger på appen med din arbejdskonto eller personlige konto, har du adgang til funktioner for Microsoft Defender til Slutpunkt eller til funktioner for Microsoft Defender for enkeltpersoner. Se denne [blog for at](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) få flere oplysninger.

## <a name="threat-and-vulnerability-management"></a>Administration af trusler og sikkerhedsrisiko

Den 25. januar 2022 offentliggjorde vi den generelle tilgængelighed af administration af trusler og sikkerhedsrisiko på Android og iOS. Du kan finde flere oplysninger [i techcommunity-indlægget her](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Kommende ændringer i tilladelser for Microsoft Defender til Slutpunkt, der kører Android 11 eller nyere (nov 2021)

Udgivelsesversion: 1.0.3501.0301 Udgivelsesmåned: Nov 2021 Microsoft Defender for Endpoint har udgivet denne opdatering, der kræves af [Google](https://developer.android.com/distribute/play-policies#APILevel30) for at opgradere til Android API 30. Denne ændring vil bede brugere, der søger adgang [til nye tilladelser til lagerplads](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play), for enheder, der kører Android 11 eller nyere. Brugerne skal acceptere denne nye lagertilladelse, når de opdaterer Defender-appen med udgivelsesversionen 1.0.3501.0301 eller nyere. Dette sikrer, at Defender for Endpoints appsikkerhedsfunktion fungerer uden afbrydelse. Du kan finde flere oplysninger i de følgende afsnit.

**Hvordan vil dette påvirke din organisation:** Disse ændringer træder i kraft, hvis du bruger Microsoft Defender til Slutpunkt på enheder, der kører Android 11 eller nyere og har opdateret Defender til Endpoint til at udgive build 1.0.3501.0301 eller nyere.

> [!NOTE]
> De nye lagertilladelser kan ikke konfigureres af administratoren til "Autogodkend" via Microsoft Endpoint Manager. Brugeren skal gøre noget for at give adgang til denne tilladelse.

- **Brugeroplevelse:** Brugerne modtager en meddelelse om manglende tilladelse til appsikkerhed. Hvis brugeren afviser denne tilladelse, deaktiveres funktionen "Appsikkerhed" på enheden. Hvis brugeren ikke accepterer eller afviser tilladelse, vil brugeren fortsat modtage prompten, når enheden låses op eller åbnes, indtil den er blevet godkendt.

> [!NOTE]
> Hvis din organisation får vist funktionen "Tamper Protection", og hvis de nye lagertilladelser ikke tildeles af brugeren inden for 7 dage efter opdatering til den nyeste version, kan brugeren miste adgang til virksomhedens ressourcer.

**Det skal du gøre for at forberede dig:**

Giv dine brugere og helpdesk (alt efter hvad der er relevant) besked om, at brugerne skal acceptere de nye tilladelser, når de bliver bedt om det, når de har opdateret Defender til Slutpunkt til build 1.0.3501.0301 eller nyere version. For at acceptere tilladelserne skal brugerne:

1. Tryk på meddelelsen Defender for Endpoint i appen, eller åbn appen Defender for Endpoint. Brugerne får vist et skærmbillede, der viser de nødvendige tilladelser. Der mangler en grøn markering ud for den Storage tilladelse.

2. Tryk **på Begynd**.

3. Tryk på til/ **fra-knappen for Tillad adgang til at administrere alle filer.**

4. Enheden er nu beskyttet.

  > [!NOTE]
  > Denne tilladelse giver Microsoft Defender for Endpoint adgang til lagerplads på brugerens enhed, hvilket hjælper med at registrere og fjerne skadelige og uønskede apps. Kun Microsoft Defender til Endpoint-adgange/scanninger i Android-apppakkefilen (.apk). På enheder med en arbejdsprofil scanner Defender for Endpoint kun arbejdsrelaterede filer.
