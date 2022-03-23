---
title: Beskyttelse af personlige oplysninger – Microsoft Defender til Slutpunkt på iOS
ms.reviewer: ''
description: Beskriver beskyttelse af personlige oplysninger for Microsoft Defender til Endpoint på iOS
keywords: microsoft, defender, Microsoft Defender til Endpoint, ios, politik, oversigt
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4fc5d4fb51170a70edc8664d5ccba0943b93353d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63592695"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>Beskyttelse af personlige oplysninger – Microsoft Defender til Slutpunkt på iOS

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> Defender til Slutpunkt på iOS bruger et VPN til at levere webbeskyttelsesfunktionen. Dette er ikke et almindeligt VPN og er et lokalt eller selvløkkende VPN, der ikke tager trafik uden for enheden. **Microsoft eller din organisation, kan ikke se dine browseraktiviteter.**

Defender til Slutpunkt på iOS indsamler oplysninger fra dine konfigurerede iOS-enheder og gemmer dem i den samme lejer, hvor du har Defender til slutpunkt. Oplysningerne indsamles for at holde Defender for Endpoint på iOS sikker, opdateret, fungerer som forventet og for at understøtte tjenesten.

Du kan finde flere oplysninger om datalagring under [Microsoft Defender til lagring af data i slutpunktet og beskyttelse af personlige oplysninger](data-storage-privacy.md).

Du kan finde flere oplysninger om de mest almindelige spørgsmål om beskyttelse af personlige oplysninger om Microsoft Defender til Endpoint på Android- og iOS-mobilenheder under [Microsoft Defender til Endpoint og dine personlige oplysninger på Android- og iOS-mobilenheder](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Påkrævede data

Påkrævede data består af data, der er nødvendige for at Defender til Slutpunkt på iOS fungerer som forventet. Disse data er vigtige for tjenestens drift og kan omfatte data, der er relateret til slutbrugeren, organisationen, enheden og apps.

Her er en liste over de typer data, der indsamles:

### <a name="web-page-or-network-information"></a>Webside eller netværksoplysninger

- Det er kun webstedets domænenavn og IP-adresse, der oprettes, når der registreres en skadelig forbindelse eller webside.

### <a name="device-and-account-information"></a>Enheds- og kontooplysninger

- Enhedsoplysninger som f.eks & klokkeslæt, iOS-version, CPU-oplysninger og Enheds-id, hvor Enheds-id er et af følgende:
  - Wi-Fi-adapterens MAC-adresse
  - Tilfældigt genereret GUID (Globally Unique Identifier) (GUID)
- Lejer-, enheds- og brugeroplysninger
  - Azure Active Directory (AD) Enheds-id og Azure-bruger-id – identificerer entydigt enheden, brugeren på henholdsvis Azure Active Directory.
  - Azure-lejer-id – GUID, der identificerer din organisation Azure Active Directory.
  - Microsoft Defender for Endpoint-organisations-id – Entydigt id, der er knyttet til den virksomhed, enheden tilhører. Gør det muligt for Microsoft at identificere, om der er problemer, der påvirker et udvalgt sæt virksomheder og antallet af virksomheder, der påvirkes.
  - Brugerens hovednavn – brugerens mail-id.

### <a name="product-and-service-usage-data"></a>Brugsdata for produkter og tjenester

Følgende oplysninger indsamles kun for Microsoft Defender for Endpoint-appen, der er installeret på enheden.

- App-pakkeoplysninger, herunder navn, version og appopgraderingsstatus.
- Handlinger, der er udført i appen.
- Rapportlogfiler, der er oprettet af iOS, går ned.
- Hukommelsesforbrugsdata.

## <a name="optional-data"></a>Valgfri data

Valgfri data omfatter diagnostiske data og feedbackdata fra klienten. Valgfrie diagnosticeringsdata er yderligere data, der kan hjælpe os med at udvikle produktforbedringer, og som giver avancerede oplysninger, der hjælper os til at registrere, diagnosticere og løse problemer. Disse data er kun til diagnosticeringsformål og er ikke nødvendige for selve tjenesten.

Valgfrie diagnostiske data omfatter:

- App-, CPU- og netværksbrug for Defender til slutpunkt.
- Funktioner, der er konfigureret af administratoren for Defender til Slutpunkt.

Feedbackdata indsamles via feedback i appen, som leveres af brugeren.

- Brugerens mailadresse, hvis brugeren vælger at angive den.
- Feedbacktype (smil, glad, ide) og eventuelle feedbackkommentarer, der sendes af brugeren.

Du kan få mere at vide under [Mere om beskyttelse af personlige oplysninger](https://aka.ms/mdatpiosprivacystatement).
