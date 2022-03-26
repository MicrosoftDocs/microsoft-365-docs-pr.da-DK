---
title: Microsoft Defender til slutpunkt på Android – oplysninger om beskyttelse af personlige oplysninger
description: Kontrolelementer til beskyttelse af personlige oplysninger, hvordan du konfigurerer politikindstillinger, der påvirker beskyttelse af personlige oplysninger og oplysninger om de diagnostiske data, der indsamles i Microsoft Defender til Slutpunkt på Android.
keywords: microsoft, defender, Microsoft Defender til Endpoint, android, privacy, diagnostic
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6772539f4ca4ea819a0f8cd2a92a817fcea650f3
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/01/2022
ms.locfileid: "63595822"
---
# <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Microsoft Defender til slutpunkt på Android – oplysninger om beskyttelse af personlige oplysninger

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender til Slutpunkt på Android indsamler oplysninger fra dine konfigurerede Android-enheder og gemmer dem i den samme lejer, hvor du har Defender til Slutpunkt. Oplysningerne indsamles for at holde Defender til Endpoint til Android sikker, opdateret, fungerer som forventet og for at understøtte tjenesten.

Du kan finde flere oplysninger om datalagring under [Microsoft Defender til lagring af data i slutpunktet og beskyttelse af personlige oplysninger](data-storage-privacy.md).

Der indsamles oplysninger for at sikre, at Defender til Endpoint til Android er sikkert, opdateret, fungerer som forventet og understøtter tjenesten.

Du kan finde flere oplysninger om de mest almindelige spørgsmål om beskyttelse af personlige oplysninger om Microsoft Defender til Endpoint på Android- og iOS-mobilenheder under [Microsoft Defender til Endpoint og dine personlige oplysninger på Android- og iOS-mobilenheder](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Påkrævede data

Påkrævede data består af data, der er nødvendige for at Defender til Endpoint til Android fungerer som forventet. Disse data er vigtige for tjenestens drift og kan omfatte data, der er relateret til slutbrugeren, organisationen, enheden og apps. Her er en liste over de typer data, der indsamles:

### <a name="app-information"></a>Appoplysninger

Oplysninger om **skadelige** Android-programpakker (APKs) på enheden, herunder

- Installer kilde
- Storage placering (filsti) for APK'en
- Tid på installation, størrelse af APK og tilladelser

Til Android Enterprise-enheder, der er fuldt administreret – oplysninger om Android-programpakker (APKs), der er installeret på enheden, herunder

- Navn og pakkenavn på appen
- Appens versionsnummer
- Leverandørnavn

Til Android Enterprise med en arbejdsprofil – Oplysninger om Android-programpakker (APKs), der er installeret på enhedens arbejdsprofil, herunder

- Navn og pakkenavn på appen
- Appens versionsnummer
- Leverandørnavn

*Din organisation kan også vælge at konfigurere Defender til Slutpunkt til at sende oplysninger om alle apps, der er installeret på enheden. Disse oplysninger sendes som standard ikke til din organisation.*


### <a name="web-page--network-information"></a>Webside/netværksoplysninger

- Kun den fulde URL-adresse til webstedet, når en ondsindet forbindelse eller webside registreres og blokeres.
- Forbindelsesoplysninger
- Protokoltype (f.eks. HTTP, HTTPS osv.)

### <a name="device-and-account-information"></a>Enheds- og kontooplysninger

- Enhedsoplysninger som f.eks & klokkeslæt, Android-version, OEM-model, CPU-oplysninger og Enheds-id.
- Enheds-id er et af nedenstående:
  - Wi-Fi-adapterens MAC-adresse
  - [Android-id](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (som genereret af Android på tidspunktet for enhedens første start).
  - Tilfældigt genereret GUID (Globally Unique Identifier) (GUID).

- Lejer-, enheds- og brugeroplysninger
  - Azure Active Directory (AD) Enheds-id og Azure-bruger-id: Identificerer entydigt enheden, brugeren på henholdsvis Azure Active Directory.
  - Azure-lejer-id: GUID, der identificerer din organisation Azure Active Directory.
  - Microsoft Defender for Endpoint-organisations-id: Entydigt id, der er knyttet til den virksomhed, enheden tilhører. Gør det muligt for Microsoft at identificere, om problemer påvirker et udvalgt sæt virksomheder, og hvor mange virksomheder der påvirkes.
  - Brugerens hovednavn: brugerens mail-id

### <a name="product-and-service-usage-data"></a>Brugsdata for produkter og tjenester

Følgende oplysninger indsamles kun for Microsoft Defender for Endpoint-appen, der er installeret på enheden. 

- App-pakkeoplysninger, herunder navn, version og appopgraderingsstatus.
- Handlinger, der udføres i appen.
- Oplysninger om trusselsregistrering, f.eks. trusselsnavn, kategori osv.
- Rapportlogfiler, der er oprettet af Android, går ned.

## <a name="optional-data"></a>Valgfri data

Valgfri data omfatter diagnostiske data og feedbackdata. Valgfrie diagnosticeringsdata er yderligere data, der kan hjælpe os med at udvikle produktforbedringer, og som giver avancerede oplysninger, der hjælper os til at registrere, diagnosticere og løse problemer. Valgfrie diagnostiske data omfatter:

- Brug af app, CPU og netværk.
- Enhedens tilstand fra app-perspektivet, herunder scanningsstatus, tidsindstillinger for scanning, tildelte apptilladelser og opgraderingsstatus.
- Funktioner, der er konfigureret af administratoren.
- Grundlæggende oplysninger om browsere på enheden.

**Feedbackdata** indsamles via feedback i appen, som leveres af brugeren

- Brugerens mailadresse, hvis brugeren vælger at angive den.
- Feedbacktype (smil, glad, ide) og eventuelle feedbackkommentarer, der sendes af brugeren.
