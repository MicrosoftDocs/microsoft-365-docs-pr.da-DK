---
title: Administrer Microsoft Defender for Endpoint Plan 1
description: Vedligehold og opdater Defender for Endpoint Plan 1. Administrer indstillinger, hent opdateringer, og løs falske positive/negativer.
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
ms.openlocfilehash: 417dd33eed846e45453464e63ff403374ce224dc
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667400"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Administrer Microsoft Defender for Endpoint Plan 1

**Gælder for**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når du bruger Defender for Endpoint Plan 1 i din organisation, kan dit sikkerhedsteam udføre visse trin for at vedligeholde din sikkerhedsløsning. Når sikkerhedsteamet sammensætter din vedligeholdelses- og driftsplan, skal du sørge for at inkludere mindst følgende aktiviteter:

- [Administrer sikkerhedsintelligens og produktopdateringer](#manage-security-intelligence-and-product-updates)
- [Finjuster og juster Defender for Slutpunkt](#fine-tune-and-adjust-defender-for-endpoint)
- [Adresse falske positiver/negativer](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Administrer sikkerhedsintelligens og produktopdateringer

Det er vigtigt at holde Microsoft Defender Antivirus opdateret for at beskytte mod ny malware og angrebsteknikker. Microsoft udgiver regelmæssige opdateringer til sikkerhedsintelligens, antivirus- og antimalwarebeskyttelse. Opdateringer er organiseret i to kategorier: 

- Opdateringer til sikkerhedsintelligens
- Produktopdateringer 

Hvis du vil administrere dine sikkerhedsintelligens- og produktopdateringer, skal du se [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Finjuster og juster Defender for Slutpunkt

Defender for Endpoint giver dig stor fleksibilitet og konfigurationsmuligheder. Du kan justere og finjustere dine indstillinger, så de passer til organisationens behov. Du kan f.eks. bruge Microsoft Endpoint Manager, Gruppepolitik og andre metoder til at administrere dine sikkerhedsindstillinger for slutpunkter. 

Du kan få mere at vide under [Administrer Defender for Endpoint](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Adresse falske positiver/negativer

Et falsk positivt element er en artefakt, f.eks. en fil eller en proces, der blev registreret som skadelig, selvom det faktisk ikke er en trussel. Et falsk negativt er et objekt, der ikke blev registreret som en trussel, selvom det faktisk er. Der kan forekomme falske positiver/negativer for enhver løsning til beskyttelse af slutpunkter, herunder Defender for Endpoint. Der er dog trin, du kan udføre for at løse disse typer problemer og finjustere din løsning, som vist på følgende billede:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Oversigt over proces for falske positiver og negativer" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Hvis du får vist falske positiver/negativer i Defender for Endpoint, skal du se [Adresse falske positive/negative i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Næste trin

- [Se nyheder i Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md)