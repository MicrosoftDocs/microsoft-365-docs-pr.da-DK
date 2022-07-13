---
title: Aktivér evalueringsmiljøet for Microsoft Defender for Cloud Apps
description: Få mere at vide om arkitekturen i Defender for Cloud Apps i Microsoft Defender for Office 365 og forstå interaktioner mellem de Microsoft 365 Defender produkter.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0c9f4687cf36d4db5f22cd6e1b95f55eebc84cf9
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749918"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Aktivér evalueringsmiljøet for Microsoft Defender for Cloud Apps

**Gælder for:**

- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-mcas-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Cloud Apps. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-mcas-overview.md).

I denne artikel gennemgår vi processen med at få adgang til Defender for Cloud Apps-portalen og konfigurere den nødvendige integration for at indsamle trafikdata for cloudapps.

Hvis du vil finde cloudapps, der bruges i dit miljø, kan du implementere en eller begge af følgende metoder:

- Kom hurtigt i gang med Cloud Discovery ved at integrere med Microsoft Defender for Endpoint. Med denne oprindelige integration kan du straks begynde at indsamle data om cloudtrafik på tværs af dine Windows 10 og Windows 11 enheder, på og uden for dit netværk.
- Hvis du vil finde alle cloudapps, der tilgås af alle enheder, der har forbindelse til dit netværk, skal du installere defender for Cloud Apps-logopsamleren på dine firewalls og andre proxyer. Denne udrulning hjælper med at indsamle data fra dine slutpunkter og sender dem til Defender for Cloud Apps til analyse. Defender for Cloud Apps integreres oprindeligt med nogle proxyer fra tredjepart for at få endnu flere funktioner.

Denne artikel indeholder en vejledning til begge metoder.

Brug følgende trin til at konfigurere Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="Trinnene til aktivering af Microsoft Microsoft Defender for Cloud Apps i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [Trin 1. Opret forbindelse til Defender for Cloud Apps-portalen](#step-1)
- [Trin 2. Integrer med Microsoft Defender for Endpoint](#step-2)
- [Trin 3. Udrul Defender for Cloud Apps-logopsamleren på dine firewalls og andre proxyer](#step-3)
- [Trin 4. Få vist dashboardet Cloud Discovery for at se, hvilke apps der bruges i din organisation](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Trin 1. Opret forbindelse til Defender for Cloud Apps-portalen

Hvis du vil bekræfte licenser og oprette forbindelse til Defender for Cloud [Apps-portalen, skal du se Hurtig start: Kom i gang med Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

Hvis du ikke kan oprette forbindelse til portalen med det samme, skal du muligvis føje IP-adressen til listen over tilladte i din firewall. Se [Grundlæggende konfiguration af Defender for Cloud Apps](/cloud-app-security/general-setup).

Hvis du stadig har problemer, skal du gennemse [Netværkskrav](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Trin 2. Integrer med Microsoft Defender for Endpoint

Microsoft Defender for Cloud Apps integreres med Microsoft Defender for Endpoint som standard. Integrationen forenkler udrulningen af Cloud Discovery, udvider Cloud Discovery-funktionerne ud over virksomhedens netværk og muliggør enhedsbaseret undersøgelse. Denne integration viser, at cloudapps og -tjenester tilgås fra it-administrerede Windows 10 og Windows 11 enheder.

Hvis du allerede har konfigureret Microsoft Defender for Endpoint, er konfiguration af integration med Defender for Cloud Apps en til/fra-knap i Microsoft 365 Defender. Når integration er slået til, kan du vende tilbage til Defender for Cloud Apps-portalen og få vist omfattende data i Dashboard til cloudregistrering.

Hvis du vil udføre disse opgaver, [skal du se Microsoft Defender for Endpoint integration med Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Trin 3. Udrul Defender for Cloud Apps-logopsamleren på dine firewalls og andre proxyer

Hvis du vil have dækning på alle de enheder, der er forbundet til dit netværk, skal du installere defender for Cloud Apps-logopsamleren på dine firewalls og andre proxyer for at indsamle data fra dine slutpunkter og sende dem til Defender for Cloud Apps til analyse.

Hvis du bruger en af følgende SWG (Secure Web Gateways), leverer Defender for Cloud Apps problemfri udrulning og integration:

- Zscaler
- iboss
- Korrugeret
- Menlo Security

Du kan finde flere oplysninger om integration med disse netværksenheder under [Konfigurer Cloudregistrering](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Trin 4. Få vist dashboardet Cloud Discovery for at se, hvilke apps der bruges i din organisation

Cloud Discovery-dashboardet er designet til at give dig mere indsigt i, hvordan cloudapps bruges i din organisation. Den giver et hurtigt overblik over, hvilke typer apps der bruges, dine åbne beskeder og risikoniveauerne for apps i din organisation.

Hvis du vil i gang med at bruge dashboardet Cloud Discovery, skal du se [Arbejde med fundne apps](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: [Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
