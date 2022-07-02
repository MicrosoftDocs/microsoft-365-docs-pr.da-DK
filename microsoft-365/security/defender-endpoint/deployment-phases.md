---
title: oversigt over Microsoft Defender for Endpoint udrulning
description: Få mere at vide om, hvordan du udruller Microsoft Defender for Endpoint ved at forberede, konfigurere og onboarde slutpunkter til den pågældende tjeneste
keywords: udrulle, forberede, konfigurere, onboarde, fase, udrulning, udrulning, implementering, konfiguration
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-overview
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3520d249e7241eb1b890c3939fe6e6165d5c6011
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607603"
---
# <a name="microsoft-defender-for-endpoint-deployment-overview"></a>oversigt over Microsoft Defender for Endpoint udrulning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Få mere at vide om, hvordan du udruller Microsoft Defender for Endpoint, så din virksomhed kan drage fordel af forebyggende beskyttelse, registrering efter sikkerhedsbrud, automatiseret undersøgelse og svar.

Denne vejledning hjælper dig med at arbejde på tværs af interessenter for at forberede dit miljø og derefter onboarde enheder på en metodisk måde, der går fra evaluering til en meningsfuld pilot til fuld udrulning.

Hvert afsnit svarer til en separat artikel i denne løsning.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Udrulningsfaserne med oplysninger fra tabellen" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Oversigt over udrulningsfaser: forbered, konfigurer, onboard" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Fase|Beskrivelse|
|---|---|
|[Fase 1: Forbered](prepare-deployment.md)|Få mere at vide om, hvad du skal overveje, når du udruller Defender for Endpoint, f.eks. godkendelser af interessenter, miljøovervejelser, adgangstilladelser og rækkefølgen af funktioner.|
|[Fase 2: Installation](production-deployment.md)|Få vejledning i de indledende trin, du skal udføre, så du kan få adgang til portalen, f.eks. validering af licenser, fuldførelse af konfigurationsguiden og netværkskonfiguration.|
|[Fase 3: Onboard](onboarding.md)|Få mere at vide om, hvordan du bruger udrulningsringe, understøttede onboardingværktøjer baseret på typen af slutpunkt og konfiguration af tilgængelige funktioner.|
|

Når du har fuldført denne vejledning, bliver du konfigureret med de rette adgangstilladelser, dine slutpunkter onboardes, og der rapporteres sensordata til tjenesten, og funktioner som beskyttelse i næste generation og reduktion af angrebsoverfladen vil være på plads.

Uanset hvilken miljøarkitektur og udrulningsmetode du vælger, der er beskrevet i [vejledningen til udrulning af planen](deployment-strategy.md) , understøtter denne vejledning dig i onboarding-slutpunkter.

## <a name="key-capabilities"></a>Nøglefunktioner

Selvom Microsoft Defender for Endpoint indeholder mange funktioner, er det primære formål med denne installationsvejledning at få dig i gang ved at onboarde enheder. Ud over onboarding får du denne vejledning i gang med følgende funktioner.

<br>

****

|Kapacitet|Beskrivelse|
|---|---|
|Slutpunktsregistrering og -svar|Der er indført funktioner til registrering af slutpunkter og svar for at registrere, undersøge og reagere på forsøg på indtrængen og aktive brud.|
|Næste generations beskyttelse|For yderligere at styrke sikkerhedsperimeteren på dit netværk bruger Microsoft Defender for Endpoint næste generations beskyttelse, der er designet til at fange alle typer nye trusler.|
|Reduktion af angrebsoverfladen|Angiv den første forsvarslinje i stakken. Ved at sikre, at konfigurationsindstillingerne angives korrekt, og at teknikkerne til afhjælpning af udnyttelse anvendes, modstår disse funktioner angreb og udnyttelse.|
|

Alle disse funktioner er tilgængelige for Microsoft Defender for Endpoint licensindehavere. Du kan få flere oplysninger under [Licenskrav](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Omfanget

### <a name="in-scope"></a>Inden for området

- Brug af Microsoft Endpoint Manager og Microsoft Endpoint Configuration Manager til at integrere slutpunkter i tjenesten og konfigurere funktioner
- Aktivering af Defender for EDR-funktioner (Endpoint Endpoint Detection and Response)
- Aktivering af Defender for EPP-funktioner (Endpoint Endpoint Protection Platform)
  - Næste generations beskyttelse
  - Reduktion af angrebsoverfladen

### <a name="out-of-scope"></a>Uden for området

Følgende er ikke omfattet af denne installationsvejledning:

- Konfiguration af tredjepartsløsninger, der kan integreres med Defender for Endpoint
- Indtrængningstest i produktionsmiljø

## <a name="see-also"></a>Se også

- [Fase 1: Forbered](prepare-deployment.md)
- [Fase 2: Konfigurer](production-deployment.md)
- [Fase 3: Onboard](onboarding.md)
- [Plan for udrulning](deployment-strategy.md)
