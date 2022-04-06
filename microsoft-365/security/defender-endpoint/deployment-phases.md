---
title: Installationsfaser
description: Få mere at vide om, hvordan du installerer Microsoft Defender til slutpunkt ved at forberede, konfigurere og onboarde slutpunkter til den pågældende tjeneste
keywords: Installér, forbered, konfiguration, onboard, fase, installation, implementering, indføring, konfiguration
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
ms.openlocfilehash: 5715a796e0c7b78ae369f074b5edcb6ccfc8ae90
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606429"
---
# <a name="deployment-phases"></a>Installationsfaser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Få mere at vide om, hvordan du installerer Microsoft Defender til slutpunkt, så din virksomhed kan drage fordel af forebyggelse, registrering af brud, automatisk undersøgelse og svar.

Denne vejledning hjælper dig med at arbejde på tværs af interessenter for at forberede dit miljø og derefter implementere enheder på en metodisk måde, fra evaluering til et relevant pilotprojekt til en komplet installation.

Hver sektion svarer til en separat artikel i denne løsning.

![Billede af installationsfaser med oplysninger fra tabellen.](images/deployment-guide-phases.png)


![Oversigt over installationsfaser: klargør, konfiguration, onboard.](images/phase-diagrams/deployment-phases.png)

<br>

****

|Fase|Beskrivelse|
|---|---|
|[Fase 1: Forbered](prepare-deployment.md)|Få mere at vide om, hvad du skal overveje, når du udruller Defender til Slutpunkt, f.eks. interessenters godkendelser, overvejelser om miljøet, adgangstilladelser og rækkefølgen af funktioner for anvendelse.|
|[Fase 2: Konfiguration](production-deployment.md)|Få vejledning i de indledende trin, du skal udføre, så du kan få adgang til portalen, f.eks. validering af licenser, fuldføre konfigurationsguiden og netværkskonfiguration.|
|[Fase 3: Onboard](onboarding.md)|Få mere at vide om, hvordan du gør brug af installationsringene, understøttede onboardingværktøjer baseret på slutpunktstypen og konfiguration af tilgængelige funktioner.|
|

Når du har gennemført denne vejledning, konfigureres du med de rette adgangstilladelser, dine slutpunkter bliver onboardet og rapporterer sensordata til tjenesten, og egenskaber som f.eks. reduktion af næste generations beskyttelse og reduktion af angrebsoverfladen vil være på plads.

Uanset miljøarkitekturen og installationsmetoden, du vælger, beskrevet i Vejledningen [](deployment-strategy.md) til planlægning af installation, vil denne vejledning understøtte dig i onboardingslutpunkter.

## <a name="key-capabilities"></a>Vigtige funktioner

Selvom Microsoft Defender til Slutpunkt indeholder mange funktioner, er det primære formål med denne installationsvejledning at komme i gang med onboardingenheder. Ud over onboarding får denne vejledning dig i gang med følgende funktioner.

<br>

****

|Funktion|Beskrivelse|
|---|---|
|Registrering af slutpunkt og svar|Registrering af slutpunkter og svarfunktioner er blevet aktiveret for at registrere, undersøge og reagere på forsøg på indtrængen og aktive overtrædelser.|
|Næste generations beskyttelse|For yderligere at styrke dit netværks sikkerhedsperimeter bruger Microsoft Defender til Slutpunkt næste generations beskyttelse, der er udviklet til at fange alle typer af nye trusler.|
|Reduktion af angrebsoverfladen|Angiv den første forsvarslinje i stakken. Ved at sikre, at konfigurationsindstillingerne er korrekt indstillet, og de teknikker til afhjælpning af udnyttelse, der anvendes, kan disse egenskaber modstå angreb og udnyttelse.|
|

Alle disse funktioner er tilgængelige for Microsoft Defender for slutbrugere af slutpunkter. Få mere at vide under [Licenskrav](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Omfang

### <a name="in-scope"></a>Inden for området

- Brug af Microsoft Endpoint Manager og Microsoft Endpoint Configuration Manager til at onboarde slutpunkter i tjenesten og konfigurere funktioner
- Aktivering af Defender for slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar)
- Aktivering af Defender for endpoint-slutpunktsbeskyttelsesplatformen (EPP)
  - Næste generations beskyttelse
  - Reduktion af angrebsoverfladen

### <a name="out-of-scope"></a>Uden for området

Følgende er ikke omfattet af denne installationsvejledning:

- Konfiguration af tredjepartsløsninger, der kan integreres med Defender for Endpoint
- Test af test af test i produktionsmiljø

## <a name="see-also"></a>Se også

- [Fase 1: Forbered](prepare-deployment.md)
- [Fase 2: Konfigurer](production-deployment.md)
- [Fase 3: Onboard](onboarding.md)
- [Planlæg udrulning](deployment-strategy.md)
