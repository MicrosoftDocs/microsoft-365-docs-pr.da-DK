---
title: Gennemse og administrer afhjælpningshandlinger i Microsoft Defender for Office 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automatiseret, undersøgelse, reaktion, afhjælpning, trusler, avanceret, trussel, beskyttelse
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
description: Få mere at vide om afhjælpningshandlinger i automatiserede undersøgelses- og svarfunktioner i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: aaa444a2bada254aeed83540aee361ed806ab0a0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649115"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>Gennemse og administrer afhjælpningshandlinger i Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Efterhånden som automatiserede undersøgelser af & samarbejdsindhold resulterer i domme, f.eks *. ondsindet* eller *mistænkeligt*, oprettes der visse afhjælpningshandlinger. I Microsoft Defender for Office 365 kan afhjælpningshandlinger omfatte:

- Blød sletning af mails eller klynger
- Deaktivering af ekstern videresendelse af mail

Disse afhjælpningshandlinger udføres ikke, medmindre og før sikkerhedsteamet godkender dem. Vi anbefaler, at du gennemgår og godkender eventuelle ventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser fuldføres rettidigt. I nogle tilfælde kan du overveje indsendte handlinger.  Du skal være en del af rollen Søg & fjerne, før du kan udføre nogen handlinger.

## <a name="approve-or-reject-pending-actions"></a>Godkend (eller afvis) ventende handlinger

Der er fire forskellige måder at finde og udføre automatiske undersøgelseshandlinger på:

- [Hændelseskø](https://security.microsoft.com/incidents)
- Selve undersøgelsen (tilgås via hændelse eller fra en besked)
- [Handlingscenter](https://security.microsoft.com/action-center/pending)
- [Kø for undersøgelses- og afhjælpningsundersøgelser](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>Hændelseskø

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til siden **Hændelser** under **Hændelser & beskeder** \> **Hændelser**. Hvis du vil gå direkte til siden **Hændelser** , skal du bruge <https://security.microsoft.com/incidents>.
2. Vælg et **hændelsesnavn** på siden Hændelser for at åbne oversigtssiden.
3. Vælg fanen **Beviser og Svar** .
4. Vælg et element på listen. Sideruden åbnes.
5. I sideruden skal du godkende eller afvise handlinger.

## <a name="action-center"></a>Handlingscenter

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til siden **Løsningscenter** ved at vælge **Løsningscenter**. Hvis du vil gå direkte til siden **Løsningscenter** , skal du bruge <https://security.microsoft.com/action-center/pending>.
2. Kontrollér, at fanen **Ventende** er valgt på siden **Løsningscenter**, og gennemse derefter listen over handlinger, der afventer godkendelse.
   - Vælg **siden Åbn undersøgelse** for at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en ventende handling.
   - Vælg **Afvis** for at forhindre, at der udføres en ventende handling.

## <a name="investigation-and-remediation-investigations-queue"></a>Kø for undersøgelses- og afhjælpningsundersøgelser

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til siden **Trusselsundersøgelse** på **Mail & samarbejdsundersøgelser**\>. Hvis du vil gå direkte til siden **Trusselsundersøgelse** , skal du bruge <https://security.microsoft.com/airinvestigation>.
2. På siden **Trusselsundersøgelse** skal du finde og et element på listen, hvis status er **Ventende handling**.
3. Klik på ![Åbn i nyt vinduesikon.](../../media/m365-cc-sc-open-icon.png) **Åbn i et nyt vindue** på listetidspunktet (mellem **id** og **status**).
4. På den side, der åbnes, skal du godkende eller afvise handlinger.

## <a name="change-or-undo-one-remediation-action"></a>Rediger eller fortryd én afhjælpningshandling

Der er to forskellige måder at overveje indsendte handlinger på:

- Gennem det [samlede handlingscenter](https://security.microsoft.com/action-center).
- Selvom [Office Handlingscenter](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Rediger eller fortryd via Unified Action Center

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til Unified Action Center ved at vælge **Løsningscenter**. Hvis du vil gå direkte til Unified Action Center, skal du bruge <https://security.microsoft.com/action-center/>.
2. På siden **Løsningscenter** skal du vælge fanen **Oversigt** og derefter vælge den handling, du vil ændre eller fortryde.
3. I ruden til højre på skærmen skal du vælge den relevante handling (**flyt til indbakke**, **flyt til uønsket** post, **flyt til slettede elementer**, **blød sletning** eller **hård sletning**).

## <a name="change-or-undo-through-the-office-action-center"></a>Rediger eller fortryd via Office Løsningscenter

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til Office løsningscenter i **Mail & samarbejdsområde** \> **Review** \> **Action Center**. Hvis du vil gå direkte til Office løsningscenter, skal du bruge <https://security.microsoft.com/threatincidents>.
2. Vælg den relevante afhjælpning på siden **Handlingscenter** .
3. Klik på posten med indsendelser af mails i sidepanelet, og vent på, at listen indlæses.
4. Vent på, at knappen Handling øverst for at aktivere, og vælg knappen Handling for at ændre handlingstypen.
5. Dette vil oprette de relevante handlinger.

## <a name="next-steps"></a>Næste trin

- [Brug Threat Explorer](threat-explorer.md)
- [Administration/manuelle handlinger](remediate-malicious-email-delivered-office-365.md)
- [Sådan rapporterer du falske positiver/negativer i automatiserede undersøgelses- og svarfunktioner](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Se også

- [Få vist detaljer og resultater af en automatisk undersøgelse i Office 365](air-view-investigation-results.md)
