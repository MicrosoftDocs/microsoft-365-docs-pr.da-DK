---
title: Opret det Microsoft 365 Defender evalueringsmiljø for at opnå større cybersikkerhed og XDR
description: Få mere at vide om, hvad der er inkluderet i den Microsoft 365 Defender XDR, du evaluerer, og se dit Microsoft 365 Defender prøvelaboratorium eller pilotmiljø ved at aktivere prøvelicenser. Start din XDR-cybersikkerhedsrejse her, og få mere at vide om, hvordan du tager denne test til produktion.
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
- zerotrust-solution
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: fb097532fe809fa1b1ec4c29a9a489bcb4ea2871
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747961"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Trin 1. Opret det Microsoft 365 Defender evalueringsmiljø for at opnå større cybersikkerhed

Du kan få mere at vide om og udarbejde denne Microsoft Defender XDR løsning i trin, der distribueres via resten af denne serie:

- [Sådan opretter du miljøet](eval-create-eval-environment.md)
- Konfigurer eller få mere at vide om hver teknologi i denne Microsoft XDR
    - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
    - [Microsoft Defender til Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Sådan undersøges og reageres der ved hjælp af denne XDR](eval-defender-investigate-respond.md)
- [Hæv prøvemiljøet til produktion](eval-defender-promote-to-production.md)
- [Tilbage til Oversigt](eval-overview.md)

Trinnene i denne serie kører fra ende til anden, fra at lære de koncepter, der er bag Microsoft 365 Defender XDR, til at bygge det og til at sende evalueringsmiljøet direkte til produktion.

Der er to almindelige måder at gøre dette næste trin i evalueringen på. Denne serie forudsætter, at du allerede har en Microsoft 365-produktionslejer og aktiverer E5-prøvelicenser for at evaluere Microsoft 365 Defender i *det aktuelle miljø*. En lokal evaluering giver dig mulighed for at bevare alle sikkerhedsmetoder med køb af licenser efter evalueringsperioden.

Den anden er at [konfigurere dit Microsoft 365 Defender prøveversionslaboratorium](setup-m365deval.md) med henblik på evaluering. Bemærk, at den muligvis ikke har mange rigtige signaler fra virksomheden under test.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Du skal aktivere E5-prøvelicenser for at evaluere Microsoft 365 Defender

1. Log på din eksisterende Microsoft 365-lejeradministrationsportal.
2. Vælg **Køb tjenester** i navigationsmenuen.
3. Rul ned til sektionen Office 365, og vælg knappen **Detaljer** under Office 365 E5 licens.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Knappen Detaljer på Microsoft 365 Defender-portalen" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. Vælg **Linket Start gratis prøveversion** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Knappen Start gratis prøveversion på Microsoft 365 Defender-portalen" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. Bekræft din anmodning, og klik på Knappen **Prøv nu** .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Knappen Prøv nu på Microsoft 365 Defender-portalen" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>Gå til næste trin

[Få mere at vide om, hvordan du aktiverer Microsoft 365 for Identity](eval-defender-identity-overview.md)

Eller gå tilbage til Oversigt for [Evaluate- og pilot-Microsoft 365 Defender](eval-overview.md)
