---
title: Nyheder i Microsoft Defender for Endpoint på Android
description: Få mere at vide om de overordnede ændringer af tidligere versioner af Microsoft Defender for Endpoint på Android.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
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
ms.openlocfilehash: 48d6ef27e71f89f6a81ac3c77ea17cf60dc90ee1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664562"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Nyheder i Microsoft Defender for Endpoint på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Microsoft Defender for Endpoint er nu Microsoft Defender i Play-butikken

Microsoft Defender for Endpoint er nu tilgængelig som **Microsoft Defender** i afspilningslageret. Med denne opdatering vil appen være tilgængelig som prøveversion for **forbrugere i området USA** – afhængigt af hvordan du logger på appen med din arbejdskonto eller personlige konto, har du adgang til funktioner til Microsoft Defender for Endpoint eller funktioner til Microsoft Defender for enkeltpersoner. Se [denne blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) for at få flere oplysninger.

## <a name="threat-and-vulnerability-management"></a>Trussels- og sårbarhedsstyring

Den 25. januar 2022 annoncerede vi den generelle tilgængelighed af trussels- og sårbarhedsstyring på Android og iOS. Du kan finde flere oplysninger [i techcommunity-indlægget her](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Kommende ændringer af tilladelser for Microsoft Defender for Endpoint, der kører Android 11 eller nyere (november 2021)

Udgivelsesbuild: 1.0.3501.0301 Udgivelsesmåned: November 2021 Microsoft Defender for Endpoint har udgivet denne opdatering, der kræves af [Google](https://developer.android.com/distribute/play-policies#APILevel30) for at opgradere til Android API 30. Denne ændring beder brugerne om adgang til [ny lagertilladelse](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) for enheder, der kører Android 11 eller nyere. Brugerne skal acceptere denne nye lagertilladelse, når de opdaterer Defender-appen med version build 1.0.3501.0301 eller nyere. Dette sikrer, at defender for Endpoints appsikkerhedsfunktion fungerer uden afbrydelser. Du kan få flere oplysninger i følgende afsnit.

**Hvordan påvirker det din organisation:** Disse ændringer træder i kraft, hvis du bruger Microsoft Defender for Endpoint på enheder, der kører Android 11 eller nyere, og opdaterede Defender for Endpoint til version build 1.0.3501.0301 eller nyere.

> [!NOTE]
> Administratoren kan ikke konfigurere de nye lagertilladelser til "Autogodkend" via Microsoft Endpoint Manager. Brugeren skal udføre handlinger for at give adgang til denne tilladelse.

- **Brugeroplevelse:** Brugerne modtager en meddelelse, der angiver, at der mangler en tilladelse til appsikkerhed. Hvis brugeren afviser denne tilladelse, slås funktionen 'App security' fra på enheden. Hvis brugeren ikke accepterer eller afviser tilladelse, modtager brugeren fortsat prompten, når vedkommende låser sin enhed op eller åbner appen, indtil den er blevet godkendt.

> [!NOTE]
> Hvis din organisation får vist funktionen "Tamper Protection", og hvis de nye lagertilladelser ikke er tildelt af brugeren inden for 7 dage efter opdatering til den nyeste version, kan brugeren miste adgangen til virksomhedens ressourcer.

**Det skal du gøre for at forberede:**

Giv dine brugere og helpdesk (efter behov) besked om, at brugerne skal acceptere de nye tilladelser, når de bliver bedt om det, når de har opdateret Defender for Endpoint til build 1.0.3501.0301 eller nyere version. Brugerne skal gøre følgende for at acceptere tilladelserne:

1. Tryk på meddelelsen Defender for Endpoint i appen, eller åbn appen Defender for Endpoint. Brugerne får vist en skærm, der viser de nødvendige tilladelser. Der mangler et grønt flueben ud for tilladelsen Storage.

2. Tryk på **Start**.

3. Tryk på til/fra-knappen for **Tillad adgang til at administrere alle filer.**

4. Enheden er nu beskyttet.

  > [!NOTE]
  > Denne tilladelse giver Microsoft Defender for Endpoint adgang til lagerplads på brugerens enhed, hvilket hjælper med at registrere og fjerne skadelige og uønskede apps. Microsoft Defender for Endpoint kun adgang til/scanner Android-apppakkefil (.apk). På enheder med en arbejdsprofil scanner Defender for Endpoint kun arbejdsrelaterede filer.
