---
title: Opret et Microsoft 365 Defender for større cybersikkerhed og XDR
description: Få mere at vide om, hvad der er inkluderet i den Microsoft 365 Defender XDR, du vil evaluere, og se dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø ved at aktivere prøvelicenser. Start din XDR-cybersikkerhedsrejse her, og lær, hvordan du tager testen for at producere.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/19/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 5b684a1ead5638a787413d7470cb103cbe55e7df
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775516"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Trin 1. Skab et Microsoft 365 Defender evalueringsmiljø for større cybersikkerhed

Du kan få mere at vide om og opbygge denne Microsoft Defender XDR løsning i trin, der er fordelt gennem resten af serien:

- [Sådan oprettes miljøet](eval-create-eval-environment.md)
- Konfigurer eller få mere at vide om hver teknologi i denne Microsoft XDR
    - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
    - [Microsoft Defender til Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender til Slutpunkt](eval-defender-endpoint-overview.md)
    - [Microsoft Defender til skyapps](eval-defender-mcas-overview.md)
- [Sådan undersøger og reagerer du ved hjælp af denne XDR](eval-defender-investigate-respond.md)
- [Yd prøveversionsmiljøet til produktion](eval-defender-promote-to-production.md)
- [Tilbage til oversigten](eval-overview.md)

Trinnene i denne serie kører fra ende til anden, fra at lære begreberne bag Microsoft 365 Defender XDR at bygge det og til at tage evalueringsmiljøet live til produktion.

Der er to almindelige måder at udføre dette næste trin i evalueringen på. Serien antager, at du allerede har en produktionslejer Microsoft 365 og aktiverer E5-prøvelicenser for at evaluere Microsoft 365 Defender i *det aktuelle miljø*. Med en direkte evaluering kan du beholde alle sikkerhedsmetoder ved køb af licenser efter evalueringsperioden.

Den anden er [at konfigurere dit Microsoft 365 Defender-prøvemiljø](setup-m365deval.md) med henblik på evaluering. Bemærk, at der muligvis ikke er mange reelle signaler fra virksomheden under test.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Du skal aktivere E5-prøvelicenser for at evaluere Microsoft 365 Defender

1. Log på din eksisterende Microsoft 365 lejeradministrationsportal.
2. Vælg **Køb tjenester** i navigationsmenuen.
3. Rul ned til sektionen Office 365, og **vælg knappen** Detaljer under Office 365 E5 licens.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Knappen Detaljer i Microsoft 365 Defender portal" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. Vælg **Start gratis prøveversionslink** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Knappen Start gratis prøveversion i Microsoft 365 Defender portal" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. Bekræft din anmodning, og klik **på knappen Prøv** nu.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Knappen Prøv nu i Microsoft 365 Defender portal" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>Gå til næste trin

[Få mere at vide om, hvordan du aktiverer Microsoft 365 til identitet](eval-defender-identity-overview.md)

Eller gå tilbage til Oversigt for [Evaluer og Microsoft 365 Defender](eval-overview.md)
