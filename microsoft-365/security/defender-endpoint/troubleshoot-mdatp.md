---
title: Fejlfinding af problemer med Microsoft Defender til slutpunktstjenesten
description: Find løsninger og løsninger på kendte problemer, f.eks. serverfejl, når du forsøger at få adgang til tjenesten.
keywords: fejlfinding af Microsoft Defender til Slutpunkt, serverfejl, adgang nægtet, ugyldige legitimationsoplysninger, ingen data, dashboardportal, tillad, hændelsesvisning
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: e9a0fdb1bd10d734da95ba88c459ec665635f40e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592897"
---
# <a name="troubleshoot-service-issues"></a>Fejlfinding af tjenesteproblemer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Dette afsnit omhandler de problemer, der kan opstå, når du bruger Microsoft Defender for Endpoint-tjenesten.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Serverfejl – Adgang nægtet på grund af ugyldige legitimationsoplysninger

Hvis der opstår en serverfejl, når du forsøger at få adgang til tjenesten, skal du ændre dine indstillinger for browser cookie.
Konfigurer din browser til at tillade cookies.

## <a name="elements-or-data-missing-on-the-portal"></a>Elementer eller data, der mangler på portalen

Hvis nogle elementer eller data mangler på Microsoft 365 Defender er det muligt, at proxyindstillingerne blokerer dem.

Sørg for, at `*.security.microsoft.com` proxy-tilladelseslisten er inkluderet.

> [!NOTE]
> Du skal bruge HTTPS-protokollen, når du tilføjer følgende slutpunkter.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Microsoft Defender for Endpoint-tjenesten viser hændelses- eller fejllogfiler i Logbog

Se [Gennemse hændelser og fejl ved hjælp af Hændelsesvisning](event-error-codes.md) for at få vist en liste over hændelses-jegder, der rapporteres af Microsoft Defender for Endpoint-tjenesten. Artiklen indeholder også fejlfindingstrin til hændelsesfejl.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Tjenesten Microsoft Defender for Endpoint kan ikke startes efter en genstart og viser fejl 577

Hvis onboardingenhederne fuldføres, men Microsoft Defender til Slutpunkt ikke starter efter en genstart og viser fejl 577, skal du kontrollere, Windows Defender er deaktiveret af en politik.

Du kan finde flere oplysninger [under Sørg for, Microsoft Defender Antivirus ikke er deaktiveret af politikken](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>Kendte problemer med regionale formater

### <a name="date-and-time-formats"></a>Dato- og klokkeslætsformater

Der er nogle kendte problemer med formaterne for dato og klokkeslæt.

Følgende datoformater understøttes:

- MM/dd/år-til-år
- dd/MM/år-til-år

Følgende dato- og klokkeslætsformater understøttes ikke i øjeblikket:

- Datoformat yyyy/MM/dd
- Datoformat dd/MM/år
- Datoformat med yy. Viser kun yyyy.
- Klokkeslætsformatet HH:mm:ss understøttes ikke (formatet 12-timers format understøttes ikke). Kun 24-timers formatet understøttes.

### <a name="use-of-comma-to-indicate-thousand"></a>Brug af komma til at angive tusind

Understøttelse af brug af komma som en separator i tal understøttes ikke. Områder, hvor et tal er adskilt med et komma for at angive tusind, vil kun se brugen af en prik som en separator. Eksempelvis vises 15.5K som 15,5K.

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Microsoft Defender for Endpoint-lejeren blev automatisk oprettet i Europa

Når du bruger Microsoft Defender for Cloud til at overvåge servere, oprettes automatisk en Microsoft Defender for Endpoint-lejer. Microsoft Defender for Endpoint-data gemmes som standard i Europa.

## <a name="related-topics"></a>Relaterede emner

- [Fejlfinding af onboardingproblemer i Microsoft Defender til Slutpunkt](troubleshoot-onboarding.md)
- [Gennemse hændelser og fejl ved hjælp af Logvisning](event-error-codes.md)
