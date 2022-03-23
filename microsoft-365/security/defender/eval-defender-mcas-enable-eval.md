---
title: Aktivér evalueringsmiljøet for Microsoft Defender til skyapps
description: Få mere at vide om arkitekturen i Defender til skyapps i Microsoft Defender Office 365 og forstå interaktioner mellem Microsoft 365 Defender-produkter.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4c8f0ff2ca13d7f1c0e8adfcf4e0bdf09aa1c2ac
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592283"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Aktivér evalueringsmiljøet for Microsoft Defender til skyapps

**Gælder for:**

- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-mcas-overview.md) i oprettelsen af evalueringsmiljøet til Microsoft Defender til skyapps. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-mcas-overview.md).

I denne artikel bliver du vejet gennem processen med at få adgang til portalen for Defender til skyapps og konfigurere den nødvendige integration til at indsamle trafikdata for skyapps.

For at finde skyapps, der bruges i dit miljø, kan du gøre en eller begge af følgende:

- Kom hurtigt i gang med Cloud Discovery ved at integrere med Microsoft Defender til slutpunkt. Denne oprindelige integration giver dig mulighed for straks at begynde at indsamle data på skytrafik på tværs af Windows 10 og Windows 11-enheder på og fra dit netværk.
- Hvis du vil finde alle skyapps, der tilgås af alle enheder, der har forbindelse til dit netværk, skal du installere Logindsamler til Defender for Cloud Apps på dine firewalls og andre proxyer. Dette indsamler data fra dine slutpunkter og sender dem til Defender til skyapps til analyse. Defender til skyapps integreres oprindeligt med nogle tredjeparts-proxyer for at få endnu flere egenskaber.

Denne artikel indeholder vejledning til begge metoder.

Brug følgende trin til at konfigurere Microsoft Defender til skyapps.

![Trin til at aktivere Microsoft Microsoft Defender til skyapps i Microsoft Defender-evalueringsmiljøet.](../../media/defender/m365-defender-mcas-eval-enable-steps.png)

- [Trin 1. Forbind til Defender for Cloud Apps-portalen](#step-1)
- [Trin 2. Integrer med Microsoft Defender til slutpunkt](#step-2)
- [Trin 3. Installér logindsamleren Defender for Cloud Apps på dine firewalls og andre proxyer](#step-3)
- [Trin 4. Få vist dashboardet Cloud Discovery for at se, hvilke apps der bruges i din organisation](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Trin 1. Forbind til Defender for Cloud Apps-portalen

Hvis du vil bekræfte licenser og oprette forbindelse til Defender for Cloud Apps-portalen, skal du se [Hurtig start: Introduktion til Microsoft Defender til skyapps](/cloud-app-security/getting-started-with-cloud-app-security).

Hvis du ikke kan oprette forbindelse til portalen med det samme, skal du muligvis føje IP-adressen til listen over tilladte for din firewall. Se [Grundlæggende konfiguration for Defender til skyapps](/cloud-app-security/general-setup).

Hvis du stadig har problemer, skal du gennemse [Netværkskrav](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Trin 2. Integrer med Microsoft Defender til slutpunkt

Microsoft Defender til skyapps integreres oprindeligt med Microsoft Defender for Endpoint. Integrationen forenkler udrulningen af Cloud Discovery, udvider cloud Discovery-funktioner uden for virksomhedens netværk og muliggør enhedsbaseret undersøgelse. Denne integration viser skyapps og -tjenester, der tilgås fra it-administrerede Windows 10 og Windows 11 enheder.

Hvis du allerede har konfigureret Microsoft Defender til Slutpunkt, kan du konfigurere integration med Defender til skyapps i Microsoft 365 Defender. Når integration er slået til, kan du vende tilbage til portalen for Defender for Cloud Apps og få vist omfattende data i Cloud Discovery Dashboard.

Hvis du vil udføre disse opgaver, skal [du se Integration af Microsoft Defender for Endpoint med Microsoft Defender til skyapps](/cloud-app-security/mde-integration).

<a name="step-3"></a>

## <a name="step-3-deploy-the-defender-for-cloud-apps-log-collector-on-your-firewalls-and-other-proxies"></a>Trin 3. Installér logindsamleren Defender for Cloud Apps på dine firewalls og andre proxyer

For dækning på alle enheder, der har forbindelse til dit netværk, skal du installere Defender for Cloud Apps Log Collector på dine firewalls og andre proxyer for at indsamle data fra dine slutpunkter og sende dem til Defender for Cloud Apps til analyse.

Hvis du bruger en af følgende Secure Web Gateways (SWG), giver Defender til skyapps problemfri udrulning og integration:

- Zscaler
- iboss
- Corrata
- Menlo Security

Du kan finde flere oplysninger om integration med disse netværksenheder under [Konfigurer skyregistrering](/cloud-app-security/set-up-cloud-discovery).

<a name="step-4"></a>

## <a name="step-4-view-the-cloud-discovery-dashboard-to-see-what-apps-are-being-used-in-your-organization"></a>Trin 4. Få vist dashboardet Cloud Discovery for at se, hvilke apps der bruges i din organisation

Cloud Discovery-dashboardet er designet til at give dig mere indsigt i, hvordan skyapps bruges i din organisation. Den giver et hurtigt overblik over, hvilke typer apps der bruges, dine åbne beskeder og risikoniveauer for apps i din organisation.

For at komme i gang med at bruge cloud Discovery-dashboardet skal du [se Arbejde med fundne apps](/cloud-app-security/discovered-apps).

## <a name="next-steps"></a>Næste trin

Trin 3 af 3: [Pilot microsoft Defender til skyapps](eval-defender-mcas-pilot.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender til skyapps](eval-defender-mcas-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
