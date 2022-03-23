---
title: Softwarelager i Håndtering af trusler og sikkerhedsrisici
description: Siden til softwarelager for Microsoft Defender til Endpoints Håndtering af trusler og sikkerhedsrisici viser, hvor mange sårbarheder der er registreret i software.
keywords: Håndtering af trusler og sikkerhedsrisici, Microsoft Defender for Endpoint, Microsoft Defender for Endpoint software inventory, Microsoft Defender for Endpoint threat & håndtering af sikkerhedsrisici, Microsoft Defender for Endpoint threat & håndtering af sikkerhedsrisici softwarelager, Microsoft Defender til Endpoint tvm software inventory, tvm software inventory
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e6bf614730caa9060a334c0a01c2dfe64b24df78
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591247"
---
# <a name="software-inventory---threat-and-vulnerability-management"></a>Softwarelager – Håndtering af trusler og sikkerhedsrisici


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Softwarelageret i Håndtering af trusler og sikkerhedsrisici en liste over kendt software i organisationen. Standardfilteret på softwarelagersiden viser al software med officielle [Common Platform Enumerations (CPE)](https://nvd.nist.gov/products/cpe). Visningen indeholder oplysninger som f.eks. navnet på leverandøren, antallet af personer, der ser ud, trusler og antallet af enheder, der vises.

Du kan fjerne **filteret CPE Tilgængelig** for at få større synlighed og øge søgeområdet på tværs af al installeret software i organisationen. Det betyder, at al software, herunder software uden CPE, nu vises på listen over softwarelager.

> [!NOTE]
> Da CPR'er bruges af håndtering af sikkerhedsrisici til at identificere softwaren og eventuelle sårbarheder, vil de ikke være understøttet af Håndtering af trusler og sikkerhedsrisici  og oplysninger som f.eks., udnyttelse, antal af enheder, der er eksponeret, og det er ikke muligt for dem.

## <a name="how-it-works"></a>Sådan fungerer det

Inden for discovery-området udnytter vi det samme sæt signaler, som er ansvarlig for registrering og vurdering af [sikkerhedsrisiko i Microsoft Defender](overview-endpoint-detection-response.md) med henblik på registrering og svar på slutpunkter.

Da det er i realtid, vil du på få minutter få vist oplysninger om sikkerhedsrisikoen, når de opdages. Programmet henter automatisk oplysninger fra flere sikkerhedsfeeds. Faktisk kan du se, om en bestemt software er forbundet til en direkte trusselskampagne. Den indeholder også et link til en Threat Analytics-rapport, så snart den er tilgængelig.

## <a name="navigate-to-the-software-inventory-page"></a>Gå til siden Softwarelager

Få adgang til siden til softwarelager **ved at** vælge Håndtering af trusler og sikkerhedsrisici i navigationsmenuen i [Microsoft 365 Defender portal](portal-overview.md).

Få vist software på bestemte enheder på de enkelte enheder på [listen over enheder](machines-view-overview.md).

> [!NOTE]
> Hvis du søger efter software ved hjælp af global søgning i Microsoft Defender til Slutpunkt, skal du sørge for at placere et understregningstegn i stedet for et mellemrum. Du får f.eks. de bedste søgeresultater ved at skrive "windows_10" eller "windows_11" i stedet for "Windows 10" eller "Windows 11".

## <a name="software-inventory-overview"></a>Oversigt over softwarelager

Siden **Softwarelager** åbnes med en liste over software, der er installeret i dit netværk, herunder leverandørens navn, fundne trusler, trusler, der er knyttet til dem, blotlagte enheder, påvirkning af eksponeringsscore og mærker.

Som standard filtreres visningen efter **produktkode (CPE): Tilgængelig**. Du kan også filtrere listevisningen baseret på værdier, der findes i softwaren, trusler knyttet til dem, og mærker som f.eks. om softwaren har nået ophør af understøttelsen.

:::image type="content" alt-text="Eksempel på landingssiden for softwarelager." source="images/software-inventory-page.png" lightbox="images/tvm-software-inventory.png":::

Vælg den software, du vil undersøge. Et pop op-panel åbnes med en mere kompakt visning af oplysningerne på siden. Du kan enten dykke dybere ned i undersøgelsen og vælge siden **Åbn software**, eller du kan markere eventuelle tekniske uoverensstemmelser ved at vælge **Rapportoplysninger**.

### <a name="software-that-isnt-supported"></a>Software, der ikke understøttes

Software, der i øjeblikket ikke understøttes af & håndtering af sikkerhedsrisici, kan være til stede på softwarelagersiden. Da det ikke understøttes, vil kun begrænsede data være tilgængelige. Filtrer efter ikke-understøttet software med indstillingen "Ikke tilgængelig" i afsnittet "Tilsnit".

:::image type="content" alt-text="Ikke-understøttet softwarefilter." source="images/tvm-unsupported-software-filter.png" lightbox="images/tvm-unsupported-software-filter.png":::

Følgende angiver, at software ikke understøttes:

- Feltet "Ikke tilgængeligt" vises
- Feltet Eksponerede enheder viser en bindestreg
- Informationstekst tilføjet i sidepanel og softwareside
- Softwaresiden får ikke sikkerhedsanbefalinger, opdagede sårbarheder eller afsnit med begivenhedstidslinje

## <a name="software-inventory-on-devices"></a>Lager af software på enheder

Fra navigationspanelet Microsoft 365 Defender på portalen skal du gå til lager **[for enhed](machines-view-overview.md)**. Vælg navnet på en enhed for at åbne enhedssiden (f.eks. Computer1), og vælg derefter fanen **Softwarelager** for at få vist en liste over al den kendte software, der findes på enheden. Vælg en bestemt softwarepost for at åbne pop op-uddelingskopien med flere oplysninger.

Software kan være synlig på enhedsniveau, selvom den i øjeblikket ikke understøttes af Håndtering af trusler og sikkerhedsrisici. Dog vil kun begrænsede data være tilgængelige. Du kan se, om softwaren ikke understøttes, da der står "Ikke tilgængeligt" i kolonnen "På den anden computer".

Software uden CPE kan også vises under dette enhedsspecifikke softwarelager.

### <a name="software-evidence"></a>Software beviser

Se bevis på, hvor vi har registreret en bestemt software på en enhed fra registreringsdatabasen, disken eller begge dele. Du kan finde den på enhver enhed i lagerlisten for enhedssoftware.

Vælg et softwarenavn for at åbne pop op-uddelingskopien, og se efter afsnittet "Software bevis".

:::image type="content" alt-text="Eksempel på softwareeksem Windows 10 på listen over enheder, der viser stien til registreringsdatabasen for software beviser." source="images/tvm-software-evidence.png" lightbox="images/tvm-software-evidence.png":::

## <a name="software-pages"></a>Softwaresider

Du kan få vist softwaresider på forskellige måder:

- Side for softwarelager > vælg et softwarenavn > Vælg **siden Åbn software** i pop op-pop op-dialogboksen
- [Siden med](tvm-security-recommendation.md) sikkerhedsanbefalinger > Vælg en anbefaling > Vælg **siden Åbn software** i pop op-pop-op-dialogboksen
- [Siden Tidslinje](threat-and-vuln-mgt-event-timeline.md) for begivenhed > Vælg en begivenhed > Vælg softwarenavnet med linket (f.eks. Visual Studio 2017) i sektionen med navnet "Relateret komponent" i pop op-pop-op-pop-meddelelse

 Der vises en hel side med alle oplysningerne om en bestemt software og følgende oplysninger:

- Sidepanel med leverandøroplysninger, softwaren, der anvendes inden for organisationen (herunder antal enheder, den er installeret på, og enheder, der er eksponeret, der ikke er patcher), om og udnyttelse er tilgængelig samt påvirkning af eksponeringsscore.
- Datavisualiseringer, der viser antallet af og alvorsgraderne af sårbarheder og forkert konfigurationer. Desuden grafer med antallet af enheder, der vises.
- Faner, der viser oplysninger som f.eks.:
  - Tilsvarende sikkerhedsanbefalinger for de identificerede sårbarheder og sårbarheder.
  - Navngivne CV'er for opdagede sårbarheder.
  - Enheder, der har softwaren installeret (sammen med enhedsnavn, domæne, operativsystem og meget mere).
  - Liste over softwareversioner (herunder antal enheder, versionen er installeret på, antallet af opdagede sårbarheder og navnene på de installerede enheder).

    :::image type="content" alt-text="Eksempelside for software til Visual Studio 2017 med softwaredetaljer, enheder, der er eksponeret, og meget mere." source="images/tvm-software-page-example.png" lightbox="images/tvm-software-page-example.png":::

## <a name="report-inaccuracy"></a>Rapportér unøjagtighed

Rapportér en unøjagtighed, når du ser oplysninger om sikkerhedsrisikoen og vurderingsresultater, der er forkerte.

1. Åbn pop op-programmet til software på softwarelagersiden.
2. Vælg **Rapport unøjagtighed**.
3. I pop op-ruden skal du vælge et problem at rapportere fra:

    - En softwaredetalje er forkert
    - softwaren ikke er installeret på nogen enhed i min organisation
    - antallet af installerede eller eksponerede enheder er forkert

4. Udfyld de ønskede oplysninger om unøjagtigheden. Dette varierer afhængigt af det problem, du rapporterer.

![Rapportér unøjagtighed](images/report-inaccuracy-software.png)

5. Vælg **Send**. Din feedback sendes straks til Håndtering af trusler og sikkerhedsrisici eksperter.

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Begivenhedstidslinje](threat-and-vuln-mgt-event-timeline.md)
- [Få vist og organiser listen over Microsoft Defender til slutpunktsenheder](machines-view-overview.md)
