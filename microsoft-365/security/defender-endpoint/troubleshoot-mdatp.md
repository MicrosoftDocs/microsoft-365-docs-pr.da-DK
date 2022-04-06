---
title: Fejlfinding af problemer med tjenesten Microsoft Defender for Endpoint
description: Find løsninger og løsninger på kendte problemer, f.eks. serverfejl, når du forsøger at få adgang til tjenesten.
keywords: foretag fejlfinding af Microsoft Defender for Endpoint, serverfejl, adgang nægtet, ugyldige legitimationsoplysninger, ingen data, dashboardportal, tillad, Logbog
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
ms.openlocfilehash: bcd0f5ba70d154c40972c0b8035d1617a9e71966
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665838"
---
# <a name="troubleshoot-service-issues"></a>Fejlfinding af tjenesteproblemer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Dette afsnit omhandler problemer, der kan opstå, når du bruger tjenesten Microsoft Defender for Endpoint.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Serverfejl – Adgang nægtet pga. ugyldige legitimationsoplysninger

Hvis der opstår en serverfejl, når du forsøger at få adgang til tjenesten, skal du ændre indstillingerne for browsercookie.
Konfigurer din browser til at tillade cookies.

## <a name="elements-or-data-missing-on-the-portal"></a>Elementer eller data, der mangler på portalen

Hvis nogle elementer eller data mangler på Microsoft 365 Defender er det muligt, at proxyindstillingerne blokerer det.

Sørg for, at `*.security.microsoft.com` er inkluderet proxy-listen over tilladte.

> [!NOTE]
> Du skal bruge HTTPS-protokollen, når du tilføjer følgende slutpunkter.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Microsoft Defender for Endpoint tjeneste viser hændelses- eller fejllogge i Logbog

Se [Gennemse hændelser og fejl ved hjælp af Logbog](event-error-codes.md) for at få vist en liste over hændelses-id'er, der rapporteres af Microsoft Defender for Endpoint-tjenesten. Artiklen indeholder også fejlfindingstrin for hændelsesfejl.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Microsoft Defender for Endpoint tjeneste kan ikke starte efter en genstart og viser fejl 577

Hvis onboardingenhederne fuldføres, men Microsoft Defender for Endpoint ikke starter efter en genstart og viser fejl 577, skal du kontrollere, at Windows Defender ikke er deaktiveret af en politik.

Du kan få flere oplysninger under [Kontrollér, at Microsoft Defender Antivirus ikke er deaktiveret af en politik](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>Kendte problemer med internationale formater

### <a name="date-and-time-formats"></a>Dato- og klokkeslætsformater

Der er nogle kendte problemer med klokkeslæts- og datoformater.

Følgende datoformater understøttes:

- MM/dd/åååå
- dd/MM/åååå

Følgende formater for dato og klokkeslæt understøttes ikke i øjeblikket:

- Datoformat åååå/MM/dd
- Datoformat dd/MM/ååå
- Datoformat med ååå. Vil kun vise yyyy.
- Klokkeslætsformatet HH:mm:ss understøttes ikke (formatet 12 timer AM/PM understøttes ikke). Kun 24-timers formatet understøttes.

### <a name="use-of-comma-to-indicate-thousand"></a>Brug af komma til at angive tusindtal

Understøttelse af brug af komma som separator i tal understøttes ikke. Områder, hvor et tal er adskilt med et komma for at angive tusindtal, kan kun se brugen af en prik som separator. For eksempel vises 15,5K som 15,5K.

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Microsoft Defender for Endpoint lejer blev automatisk oprettet i Europa

Når du bruger Microsoft Defender for Cloud til at overvåge servere, oprettes der automatisk en Microsoft Defender for Endpoint lejer. De Microsoft Defender for Endpoint data gemmes som standard i Europa.

## <a name="related-topics"></a>Relaterede emner

- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
- [Gennemse hændelser og fejl ved hjælp af Logbog](event-error-codes.md)
