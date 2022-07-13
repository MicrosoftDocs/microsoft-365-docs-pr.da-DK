---
title: Pilot Microsoft Defender for Identity
description: Pilot-Microsoft Defender for Identity, sæt benchmarks, tag selvstudier om rekognoscering, kompromitterede legitimationsoplysninger, lateral bevægelse, domænedominans og eksfiltrationsbeskeder blandt andre.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
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
ms.openlocfilehash: 4805c97d79d36879a7b5081c347bd81c655c58c4
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747895"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Pilot Microsoft Defender for Identity


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3](eval-defender-identity-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Identity. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-identity-overview.md).

Brug følgende trin til at konfigurere piloten for Microsoft Defender for identitet. Bemærk, at anbefalingerne ikke omfatter oprettelse af en pilotgruppe. Bedste praksis er at installere sensoren på alle dine servere, der kører Active Directory-domæneservices (AD DS) og AD FS (Active Directory Federated Services).

:::image type="content" source="../../media/defender/m365-defender-identity-pilot-steps.png" alt-text="Trinnene til Microsoft Defender for Identity i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-identity-pilot-steps.png":::

I følgende tabel beskrives trinnene i illustrationen.

- [Trin 1: Konfigurer benchmarkanbefalinger for dit identitetsmiljø](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [Trin 2: Prøv funktioner – Gennemgang af selvstudier til identifikation og afhjælpning af forskellige angrebstyper ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>Trin 1. Konfigurer benchmarkanbefalinger for dit identitetsmiljø

Microsoft leverer anbefalinger til sikkerhedsbenchmarkering for kunder, der bruger Microsoft Cloud-tjenester. [Azure Security Benchmark](/security/benchmark/azure/overview) (ASB) indeholder præskriptive bedste fremgangsmåder og anbefalinger, der hjælper med at forbedre sikkerheden for arbejdsbelastninger, data og tjenester på Azure.

Disse benchmarkanbefalinger omfatter [Azure Security Baseline for Microsoft Defender for Identity](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). Det kan tage noget tid at planlægge og implementere disse anbefalinger. Selvom disse i høj grad vil øge sikkerheden i dit identitetsmiljø, bør de ikke forhindre dig i at fortsætte med at evaluere og implementere Microsoft Defender for Identity. Disse er angivet her for din opmærksomhed.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>Trin 2. Afprøvelse af funktioner – Gennemgang af selvstudier til identificering og afhjælpning af forskellige angrebstyper

Dokumentationen til Microsoft Defender for Identity indeholder en række selvstudier, der gennemgår processen med at identificere og afhjælpe forskellige angrebstyper.

Prøv Defender for Identity-selvstudier:
- [Beskeder om rekognoscering](/defender-for-identity/reconnaissance-alerts)
- [Beskeder om kompromitterede legitimationsoplysninger](/defender-for-identity/compromised-credentials-alerts)
- [Beskeder om tværgående flytning](/defender-for-identity/lateral-movement-alerts)
- [Beskeder om domænedominans](/defender-for-identity/domain-dominance-alerts)
- [Exfiltrationsbeskeder](/defender-for-identity/exfiltration-alerts)
- [Undersøg en bruger](/defender-for-identity/investigate-a-user)
- [Undersøg en computer](/defender-for-identity/investigate-a-computer)
- [Undersøg tværgående bevægelsesstier](/defender-for-identity/investigate-lateral-movement-path)
- [Undersøg enheder](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>Næste trin

[Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)