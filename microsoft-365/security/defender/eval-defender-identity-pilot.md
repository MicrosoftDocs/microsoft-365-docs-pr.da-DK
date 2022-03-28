---
title: Prøve på Microsoft Defender for Identity
description: Prøve microsoft Defender for Identity, angive benchmarks, tage selvstudier til rekognosering, kompromitterede legitimationsoplysninger, lateral bevægelse, domæneadvarsler og udfyldningsbeskeder blandt andre.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: bba910b46c4b4769e67ae00af0381e129139dfe5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754561"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Prøve på Microsoft Defender for Identity


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3](eval-defender-identity-overview.md) i oprettelsen af evalueringsmiljøet for Microsoft Defender for Identity. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-identity-overview.md).

Brug følgende trin til at konfigurere pilotprojektet for Microsoft Defender til identitet. Bemærk, at anbefalingerne ikke omfatter konfiguration af en pilotgruppe. Den bedste fremgangsmåde er at installere sensoren på alle dine servere, der kører Active Directory-domæneservices (AD DS) og Active Directory Federated Services (AD FS).

:::image type="content" source="../../media/defender/m365-defender-identity-pilot-steps.png" alt-text="Trinnene til pilotprojekter med Microsoft Defender for Identity i microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-identity-pilot-steps.png":::

I følgende tabel beskrives trinnene i illustrationen.

- [Trin 1: Konfigurer anbefalinger til retningspunkter for dit identitetsmiljø](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [Trin 2: Afprøve funktioner – Gennemgå selvstudier til at identificere og afhjælpe forskellige angrebstyper ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>Trin 1. Konfigurer benchmarkanbefalinger for dit identitetsmiljø

Microsoft leverer anbefalinger til sikkerheds-benchmark for kunder, der bruger Microsoft Cloud-tjenester. Azure [Security Benchmark](/security/benchmark/azure/overview) (ASB) indeholder præskrivive bedste fremgangsmåder og anbefalinger, der kan hjælpe med at forbedre sikkerheden for arbejdsbelastninger, data og tjenester på Azure.

Disse benchmarkanbefalinger [omfatter Azure-sikkerhedsplan for Microsoft Defender for Identity](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). Implementering af disse anbefalinger kan tage lidt tid at planlægge og implementere. Selvom disse kan øge sikkerheden i dit identitetsmiljø markant, bør de ikke forhindre dig i fortsat at evaluere og implementere Microsoft Defender for Identity. Disse findes her for din opmærksomhed.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>Trin 2. Prøv funktioner – Gennemgå selvstudier til at identificere og afhjælpe forskellige angrebstyper

Dokumentationen til Microsoft Defender for Identity omfatter en række selvstudier, der gennemgår processen med at identificere og afhjælpe forskellige angrebstyper.

Prøv selvstudier til Defender for Identity:
- [Rekognosering af beskeder](/defender-for-identity/reconnaissance-alerts)
- [Beskeder om kompromitterede legitimationsoplysninger](/defender-for-identity/compromised-credentials-alerts)
- [Beskeder om efterfølgende bevægelser](/defender-for-identity/lateral-movement-alerts)
- [Beskeder om domæneadvarsler](/defender-for-identity/domain-dominance-alerts)
- [Beskeder om udfyldning](/defender-for-identity/exfiltration-alerts)
- [Undersøg en bruger](/defender-for-identity/investigate-a-user)
- [Undersøg en computer](/defender-for-identity/investigate-a-computer)
- [Undersøg laterale bevægelsesstier](/defender-for-identity/investigate-lateral-movement-path)
- [Undersøg enheder](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>Næste trin

[Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)