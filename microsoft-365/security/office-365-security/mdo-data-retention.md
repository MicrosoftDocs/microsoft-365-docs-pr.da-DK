---
title: Microsoft Defender for Office 365 dataopbevaring
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Microsoft Defender for Office 365 oplysninger om dataopbevaringThreat Explorer/Real-Time registreringer
ms.openlocfilehash: 9cab47358890b47796a42e48b690818d65e20527
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772788"
---
# <a name="data-retention-information-for-microsoft-defender-for-office-365"></a>Oplysninger om dataopbevaring for Microsoft Defender for Office 365

Data på tværs af forskellige funktioner bevares som standard i højst 30 dage. Men for nogle af funktionerne kan du angive opbevaringsperioden baseret på politik. Se følgende tabel for at få vist de forskellige opbevaringsperioder for hver funktion.

> [!NOTE]
> Microsoft Defender for Office 365 findes i to forskellige plantyper. Du kan se, om du har **Plan 1** , hvis du har 'Realtidsregistreringer' og **Plan 2**, hvis du har Threat Explorer. Den Plan, du har, påvirker de værktøjer, du vil se, så vær sikker på, at du er opmærksom på din plan, efterhånden som du lærer.

## <a name="defender-for-office-365-plan-1"></a>Defender for Office 365 Plan 1

|Funktion|Opbevaringsperioden|
|---|---|
|Oplysninger om metadata for beskeder (Microsoft Defender for Office beskeder) | 90 dage |
|Oplysninger om objektmetadata (mails) | 30 dage |
|Oplysninger om aktivitetsbeskeder (overvågningslogge) | 7 dage |
|Mailobjektside | 30 dage |
|Karantæne | 30 dage (kan maksimalt konfigureres til 30 dage) |
|Rapporter | 90 dage (for alle aggregerede data) <br>30 dage (for alle detaljerede oplysninger undtagen nedenfor) <br> 10 dage (oplysninger om rapportoplysninger om trusselsbeskyttelsesstatus og spoof mailrapport) <br> 7 dage (oplysninger om URL-beskyttelsesrapport) <br>
|Indlæg | 30 dage |
|Trusselsoversigt/Real-Time registreringer | 30 dage |

## <a name="defender-for-office-365-plan-2"></a>Defender for Office 365 Plan 2

Defender for Office 365 Plan 1-funktioner plus:

|Funktion|Opbevaringsperioden|
|---|---|
|Løsningscenter | 180 dage, 30 dage (Office Løsningscenter)   |
|Avanceret jagt | 30 dage |
|AIR (automatiseret undersøgelse og svar) | 60 dage (for undersøgelser af metadata)<br> 30 dage (for metadata for mail)  |
|Simuleringsdata for angreb | 18 måneder |
|Kampagner | 30 dage |
|Hændelser | 30 dage|
|Oprydning | 30 dage |
|Threat Analytics | 30 dage |
|Trusselssporinger | 30 dage |
