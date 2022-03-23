---
title: Administrer Microsoft Defender for Endpoint Plan 1
description: Vedligeholde og opdatere Defender for Endpoint Plan 1. Administrer indstillinger, få opdateringer, og håndter falske positive/negativer.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 69e4df29817675918873e4d13b81bfe5b00b1219
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63594011"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Administrer Microsoft Defender for Endpoint Plan 1

**Gælder for**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når du bruger Defender til Endpoint Plan 1 i din organisation, kan dit sikkerhedsteam tage visse trin for at opretholde din sikkerhedsløsning. Da dit sikkerhedsteam sammensætter din vedligeholdelses- og driftsplan, skal du sørge for som minimum at medtage følgende aktiviteter:

- [Administrer sikkerhedsintelligens og produktopdateringer](#manage-security-intelligence-and-product-updates)
- [Finjuster og juster Defender til Slutpunkt](#fine-tune-and-adjust-defender-for-endpoint)
- [Adressere falske positive/negativer](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Administrer sikkerhedsintelligens og produktopdateringer

Det er Microsoft Defender Antivirus at beskytte mod nye malware- og angrebsteknikker for at holde dig opdateret. Microsoft udgiver regelmæssige opdateringer til sikkerhedsintelligens, antivirus og antimalwarebeskyttelse. Opdateringer er organiseret i to kategorier: 

- Sikkerhedsintelligensopdateringer
- Produktopdateringer 

Hvis du vil administrere din sikkerheds- og produktopdateringer, [skal du se Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Finjuster og juster Defender til Slutpunkt

Defender til Slutpunkt giver dig stor fleksibilitet og konfigurationsindstillinger. Du kan justere og finjustere dine indstillinger, så de passer til din organisations behov. Du kan f.eks. bruge Microsoft Endpoint Manager, Gruppepolitik og andre metoder til at administrere sikkerhedsindstillingerne for slutpunkter. 

Du kan få mere at vide [under Administrer Defender til slutpunkt](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Adressere falske positive/negativer

En falsk positiv er en artefakt, f.eks. en fil eller en proces, der blev registreret som skadelig, selvom det rent faktisk ikke er en trussel. En falsk negativ er en enhed, der ikke blev registreret som en trussel, selvom det rent faktisk er. Falske positive/negativer kan forekomme med alle løsninger til slutpunktsbeskyttelse, herunder Defender til slutpunkt. Der er dog trin, du kan tage for at løse disse typer problemer og finjustere din løsning, som vist på følgende billede:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Oversigt over processen for falske positive og negativer":::

Hvis du ser falske positive/negativer i Defender til slutpunkt, skal du se [Adresserer falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Næste trin

- [Se nyheder i Microsoft Defender til slutpunkt](whats-new-in-microsoft-defender-endpoint.md)