---
title: Trin 6. Overvåg enhedsrisici og overholdelse af grundlinjer for sikkerhed
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Få mere at vide om, Microsoft Intune forbindelse til Defender til Slutpunkt, og overvåg risikoen på enheden som en betingelse for adgang.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f58611f555b022b69211e39f149effef925dde17
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63594089"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>Trin 6. Overvåg enhedsrisici og overholdelse af grundlinjer for sikkerhed

Når din organisation har installeret Microsoft Defender til Slutpunkt, kan du få større indsigt og beskyttelse af dine enheder ved at integrere Microsoft Intune med Defender til slutpunkt. For mobilenheder omfatter dette muligheden for at overvåge enhedsrisici som en betingelse for adgang. For Windows enheder kan du overvåge, at disse enheder overholder de oprindelige planer for sikkerhed. 

![Illustration af integration af Defender Microsoft Intune endpoint og Microsoft Intune](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

I denne illustration:
- Microsoft Defender til Slutpunkt øger markant den sofistikerede trusselsbeskyttelse til enheder. 
- Mens Microsoft Intune giver dig mulighed for at angive politikker for appbeskyttelse og administrere enheder (herunder konfigurationsændringer), overvåger Defender til slutpunkt løbende dine enheder for trusler og kan udføre automatiserede handlinger for at løse angreb. 
- Du kan bruge Intune til at onboarde enheder til Defender for Endpoint. Når du gør dette, giver du også disse enheder mulighed for at arbejde med Microsoft 365 forebyggelse af datatab på slutpunkter (endpoint DLP).

Denne artikel indeholder disse trin:
- Forbind Microsoft Intune til Defender til Slutpunkt
- Overvåg enhedsrisici
- Overvåg overholdelse af sikkerheds oprindelige planer

Hvis Defender til Slutpunkt ikke allerede er konfigureret, kan du samarbejde med din administrator for trusselsbeskyttelse for [at konfigurere evaluerings- og pilotmiljøet](../security/defender/eval-defender-endpoint-overview.md). Du kan arbejde sammen med pilotgruppen for at afprøve funktionerne i denne artikel.

## <a name="connect-microsoft-intune-to-defender-for-endpoint"></a>Forbind Microsoft Intune til Defender til Slutpunkt

Det er nemt at konfigurere Microsoft Intune med Defender til slutpunkt. Brug denne artikel: [Konfigurer Microsoft Defender til slutpunkt i Intune](/mem/intune/protect/advanced-threat-protection-configure). 

![Forbind Intune til Microsoft Defender for Endpoint](../media/devices/connect-intune-to-microsoft-defender.png#lightbox)

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Overvåg enhedsrisici som en betingelse for adgang

Når Microsoft Defender til slutpunkt er installeret, kan du drage fordel af trusselsrisici. Dette giver dig mulighed at blokere adgangen til enheder baseret på deres risikoscore. Microsoft anbefaler at tillade adgang til enheder med et risikoscore på mellem eller under.

I Android og iOS/iPadOS kan trusselssignaler bruges i din appbeskyttelsespolitikker (APP). Du kan finde oplysninger om, hvordan du konfigurerer dette [, under Opret og tildel beskyttelsespolitik for apps for at angive risikoniveau for enheder](/mem/intune/protect/advanced-threat-protection-configure).

For alle platforme kan du angive risikoniveauet i de eksisterende politikker for enhedsoverholdelse. Se [Opret og tildel overholdelsespolitik for at angive risikoniveau for enheder](/mem/intune/protect/advanced-threat-protection-configure).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Installér grundlinjer for sikkerhed, og overvåg overholdelse af disse indstillinger

Gælder for: Windows 10, Windows 11

Artiklen, [Trin 5. Implementer konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md), anbefaler, at du kommer i gang med konfigurationsprofiler ved hjælp af de sikkerheds oprindelige planer, der er tilgængelige for Windows 10 og Windows 11. Microsoft Defender til slutpunkt omfatter også sikkerheds oprindelige planer, der giver indstillinger, der optimerer alle sikkerhedskontrolelementerne i stakken Defender til slutpunkt, herunder indstillinger for slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). Disse installeres også ved hjælp af Microsoft Intune.

Ideelt set installeres enheder, der er onboardet til Defender til Slutpunkt, begge grundlinjer: sikkerheds baseline for Windows Intune til indledningsvist at sikre Windows og derefter Defender for Endpoint-sikkerhedslinjen lagdelt oven på for optimalt at konfigurere sikkerhedskontrolelementerne for Defender til Endpoint.

For at drage fordel af de nyeste data om risici og trusler og minimere konflikter i forbindelse med udvikling af grundlinjer skal du altid anvende de nyeste versioner af de oprindelige planer på tværs af alle produkter, så snart de frigives. 

Hvis du bruger Defender til slutpunkt, kan du overvåge overholdelse af disse grundlinjer. 

![Kortet til overvågning af overholdelse af de oprindelige planer for sikkerhed](../media/devices/secconmgmt-baseline-card.png#lightbox)

Hvis du vil installere grundlinjer for sikkerhed og overvåge overholdelse af disse indstillinger, skal du følge trinnene i denne tabel.


|Trin  |Beskrivelse  |
|---------|---------|
|1     |Gennemgå nøglekoncepter, og sammenlign Microsoft Defender for Endpoint og Windows intune-sikkerheds baselines. <br><br>Se [Øg overholdelse af regler og standarder i sikkerhedslinjen Microsoft Defender til Endpoint for](../security/defender-endpoint/configure-machines-security-baseline.md) at få anbefalinger.<br><br>Se [Brug oprindelige sikkerhedsscenarier til at konfigurere Windows enheder i Intune ](/mem/intune/protect/security-baselines) for at gennemgå listen over tilgængelige grundlinjer for sikkerhed, og hvordan du undgår konflikter.         |
|2     |  Installér Windows sikkerhedsindstillinger for Intune. Du har muligvis allerede fuldført dette, hvis du fulgte vejledningen i [trin 5. Installér konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Deploy Defender for Endpoint baseline settings for Intune. Se [Administrer profiler for oprindelige planer for sikkerhed Microsoft Intune](/mem/intune/protect/security-baselines-configure) at oprette profilen og vælge den oprindelige version.<br><br>Du kan også følge vejledningen her: Gennemse [og tildele sikkerhedslinjen Microsoft Defender for Endpoint](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | I Defender til Slutpunkt skal du gennemse kortet [sikkerhed på administration af enhedskonfiguration](../security/defender-endpoint/configure-machines.md).          |
| | |

## <a name="next-steps"></a>Næste trin
Gå til [Trin 7. Implementer DLP med funktioner til beskyttelse af oplysninger på slutpunkter](manage-devices-with-intune-dlp-mip.md).