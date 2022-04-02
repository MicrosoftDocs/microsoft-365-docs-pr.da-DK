---
title: Aktivere evalueringsmiljøet for Microsoft Defender for Cloud Apps
description: Lær arkitekturen i Defender til skyapps i Microsoft Defender for Office 365 og forstå interaktioner mellem Microsoft 365 Defender-produkter.
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
ms.openlocfilehash: a66a3563d01e8e4239a0f4815fec9234fd46e1fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498973"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-cloud-apps"></a>Aktivere evalueringsmiljøet for Microsoft Defender for Cloud Apps

**Gælder for:**

- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-mcas-overview.md) i oprettelsen af evalueringsmiljøet til Microsoft Defender for Cloud Apps. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-mcas-overview.md).

I denne artikel bliver du vejet gennem processen med at få adgang til portalen for Defender til skyapps og konfigurere den nødvendige integration til at indsamle trafikdata for skyapps.

Hvis du vil finde skyapps, der bruges i dit miljø, kan du implementere en eller begge af følgende metoder:

- Kom hurtigt i gang med Cloud Discovery ved at integrere med Microsoft Defender for Endpoint. Denne oprindelige integration giver dig mulighed for straks at begynde at indsamle data på skytrafik på tværs af dine Windows 10- Windows 11-enheder på og uden for dit netværk.
- Hvis du vil finde alle skyapps, der tilgås af alle enheder, der har forbindelse til dit netværk, skal du installere Logindsamler til Defender for Cloud Apps på dine firewalls og andre proxyer. Denne installation hjælper med at indsamle data fra dine slutpunkter og sender dem til Defender til skyapps til analyse. Defender til skyapps integreres oprindeligt med nogle tredjeparts-proxyer for at få endnu flere egenskaber.

Denne artikel indeholder vejledning til begge metoder.

Brug følgende trin til at konfigurere Microsoft Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-eval-enable-steps.png" alt-text="Disse trin til at aktivere Microsoft Microsoft Defender for Cloud Apps i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-mcas-eval-enable-steps.png":::

- [Trin 1. Forbind til Defender for Cloud Apps-portalen](#step-1)
- [Trin 2. Integrer med Microsoft Defender for Endpoint](#step-2)
- [Trin 3. Installér logindsamleren Defender for Cloud Apps på dine firewalls og andre proxyer](#step-3)
- [Trin 4. Få vist dashboardet Cloud Discovery for at se, hvilke apps der bruges i din organisation](#step-4)

<a name="step-1"></a>

## <a name="step-1-connect-to-the-defender-for-cloud-apps-portal"></a>Trin 1. Forbind til Defender for Cloud Apps-portalen

Hvis du vil bekræfte licenser og oprette forbindelse til Defender for Cloud Apps-portalen, skal du se [Hurtig start: Introduktion til Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

Hvis du ikke kan oprette forbindelse til portalen med det samme, skal du muligvis føje IP-adressen til den tilladte liste over din firewall. Se [Grundlæggende konfiguration for Defender til skyapps](/cloud-app-security/general-setup).

Hvis du stadig har problemer, skal du gennemse [Netværkskrav](/cloud-app-security/network-requirements).

<a name="step-2"></a>

## <a name="step-2-integrate-with-microsoft-defender-for-endpoint"></a>Trin 2. Integrer med Microsoft Defender for Endpoint

Microsoft Defender for Cloud Apps integreret med Microsoft Defender for Endpoint oprindelige. Integrationen forenkler udrulningen af Cloud Discovery, udvider cloud Discovery-funktioner uden for virksomhedens netværk og muliggør enhedsbaseret undersøgelse. Denne integration viser skyapps og -tjenester, der tilgås via it-administrerede Windows 10 og Windows 11-enheder.

Hvis du allerede har konfigureret Microsoft Defender for Endpoint, kan du konfigurere integration med Defender til skyapps i Microsoft 365 Defender. Når integration er slået til, kan du vende tilbage til portalen for Defender for Cloud Apps og få vist omfattende data i Cloud Discovery Dashboard.

For at udføre disse opgaver skal [du Microsoft Defender for Endpoint integration med Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration).

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

Trin 3 af 3: [Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
