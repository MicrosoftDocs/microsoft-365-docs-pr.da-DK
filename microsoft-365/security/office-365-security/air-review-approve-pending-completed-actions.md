---
title: Gennemse og administrer afhjælpningshandlinger i Microsoft Defender for Office 365
keywords: AIR, autoIR, Microsoft Defender til slutpunkt, automatiseret, undersøgelse, svar, afhjælpning, trusler, avanceret, trussel, beskyttelse
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Få mere at vide om afhjælpningshandlinger i forbindelse med automatiseret undersøgelse og svarfunktioner i Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: 35e9293fa83b86fb80c1c907fbf3a0769e323503
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588186"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Gennemse og administrer afhjælpningshandlinger i Office 365

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)

I forbindelse med automatiserede undersøgelser af & af samarbejdsindhold medfører konklusioner som f.eks.  Ondsindet eller *Mistænkelig,* oprettes der visse afhjælpningshandlinger. I Microsoft Defender til Office 365 kan afhjælpningshandlinger omfatte:

- Blød sletning af mails eller klynger
- Deaktivere ekstern videresendelse af mail

Disse afhjælpningshandlinger udføres ikke, medmindre og indtil sikkerhedsteamet godkender dem. Vi anbefaler, at du gennemgår og godkender eventuelle afventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fuldføres i tide. I nogle tilfælde kan du genoverveje indsendte handlinger.  Du skal være en del af søgefunktionen & fjerne rollen, før du kan udføre nogen handlinger.

## <a name="approve-or-reject-pending-actions"></a>Godkend (eller afvis) afventende handlinger

Der er fire forskellige måder at finde og udføre handlinger til automatisk undersøgelse:

- [Hændelseskøen](https://security.microsoft.com/incidents)
- Undersøgelse af sig selv (åbnet via hændelse eller fra en besked)
- [Handlingscenter](https://security.microsoft.com/action-center/pending)
- [Kø til undersøgelse og afhjælpningsundersøgelse](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>Hændelseskøen

1. I Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **siden** Hændelser på Hændelser & **beskeder om** \> **hændelser**. For at gå direkte til **siden Hændelser skal** du bruge <https://security.microsoft.com/incidents>.
2. På siden Hændelser skal du vælge navnet på en hændelse for at åbne **dens oversigtsside** .
3. Vælg **fanen Beviser og** Svar.
4. Vælg et element på listen. Sideruden åbnes.
5. I sideruden skal du godkende eller afvise handlinger.

## <a name="action-center"></a>Handlingscenter

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til siden **Handlingscenter** ved at vælge **Handlingscenter**. Hvis du vil gå direkte til siden **Handlingscenter** , skal du bruge <https://security.microsoft.com/action-center/pending>.
2. På siden **Handlingscenter** skal du bekræfte, **at fanen** Afventer er markeret, og derefter gennemse listen over handlinger, der afventer godkendelse.
   - Vælg **siden Åbn undersøgelse for** at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en afventende handling.
   - Vælg **Afvis** for at forhindre, at der tages en afventende handling.

## <a name="investigation-and-remediation-investigations-queue"></a>Kø til undersøgelse og afhjælpningsundersøgelse

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Trusselsundersøgelse** på **Mail & samarbejdsundersøgelse**\>. For at gå direkte til siden **Trusselsundersøgelse** skal du bruge <https://security.microsoft.com/airinvestigation>.
2. På siden **Trusselsundersøgelse** skal du finde og et element fra den liste, hvis status er **Afventende handling**.
3. Klik ![på ikonet Åbn i nyt vindue.](../../media/m365-cc-sc-open-icon.png) **Åbn i nyt vindue** på listetid (mellem **ID** og **Status**).
4. På den side, der åbnes, skal du godkende eller afvise handlinger.

## <a name="change-or-undo-one-remediation-action"></a>Ændre eller fortryde en afhjælpningshandling

Der er to forskellige måder, hvorpå du kan genoverveje indsendte handlinger:

- Via det [samlede handlingscenter](https://security.microsoft.com/action-center).
- Selvom Office [handlingscenter](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Ændre eller fortryde via det samlede handlingscenter

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til det samlede handlingscenter ved at vælge **Handlingscenter**. Hvis du vil gå direkte til det samlede handlingscenter, skal du bruge <https://security.microsoft.com/action-center/>.
2. På siden **Handlingscenter** skal du vælge fanen **Oversigt** og derefter vælge den handling, du vil ændre eller fortryde.
3. I ruden i højre side af skærmen skal du vælge den relevante **handling (flyt** til **indbakke, flyt** til uønsket **mail, flyt** til slettede **elementer, blød** sletning eller **hård sletning**).

## <a name="change-or-undo-through-the-office-action-center"></a>Ændre eller fortryde Office handlingscenter

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til handlingscenteret Office på **Mailsamarbejde &** \> **Handlingscenter** \> **Gennemse**. Hvis du vil gå direkte Office handlingscenter, skal du bruge <https://security.microsoft.com/threatincidents>.
2. Vælg **den relevante** afhjælpning på siden Handlingscenter.
3. Klik på posten for mailindsendelser i sidepanelet, og vent på, at listen indlæses.
4. Vent på, at knappen Handling øverst aktiverer, og vælg handlingsknappen for at ændre handlingstypen.
5. Dette vil oprette de relevante handlinger.

## <a name="next-steps"></a>Næste trin

- [Brug Trusselsoversigt](threat-explorer.md)
- [Administrator /Manuelle handlinger](remediate-malicious-email-delivered-office-365.md)
- [Sådan rapporterer du falske positive/negativer i automatiseret undersøgelse og svarmuligheder](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Se også

- [Få vist detaljer og resultater af en automatisk undersøgelse i Office 365](air-view-investigation-results.md)
