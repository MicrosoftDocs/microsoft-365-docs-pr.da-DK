---
title: Trin 1. Planlæg Microsoft 365 Defender handlingsparathed
description: Det grundlæggende om planlægning af Microsoft 365 Defender operationsparathed, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb, secops, sikkerhedshandlinger, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8c69e92390e6ed6515be6f399703124ece99cc39
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664012"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Trin 1. Planlæg Microsoft 365 Defender handlingsparathed

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Uanset hvilken modenhed dine sikkerhedshandlinger er i øjeblikket, er det vigtigt for dig at tilpasse dig dit SOC (Security Operations Center). Selvom der ikke er en enkelt model, der passer til hver organisation, er der visse aspekter, der er mere almindelige end andre.

I følgende afsnit beskrives kernefunktionerne i SOC.

## <a name="provide-situational-awareness-of-modern-threats"></a>Giv en situationsbestemt bevidsthed om moderne trusler

Et SOC-team forbereder sig på og jagter nye og indgående trusler, så de kan arbejde sammen med organisationen om at etablere modforanstaltninger og svar. Dit SOC-team skal have personale, der er højt uddannet i moderne angrebsmetoder og -teknikker og forstår trusselsaktører. Delt trusselsintelligens og strukturer som [f.eks. Cyber Kill Chain](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) eller [MITRE ATT&CK-strukturen](https://attack.mitre.org/) kan styrke dine medarbejdere med trusselsanalytikere og trusselsjægere.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Angiv svar på første, andet og potentielt tredje niveau for cyberhændelser og -hændelser

SOC er frontlinjen i forsvaret til sikkerhedshændelser og hændelser. Når en hændelse, trussel, angreb, politikovertrædelse eller søgning efter overvågning udløser en besked eller et kald til handling, foretager SOC-teamet en vurdering for at evaluere og indeholde den eller eskalere den til undersøgelse. Soc-førstelinjereagere skal derfor have et bredt teknisk kendskab til sikkerhedshændelser og -indikatorer.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Centraliser overvågning og logføring af organisationens sikkerhedskilder

SOC-teamets kernefunktion er normalt at sikre, at alle sikkerhedsenheder som firewalls, systemer til forebyggelse af datatab, Håndtering af trusler og sikkerhedsrisici systemer og identitetssystemer fungerer korrekt og overvåges. SOC-holdene arbejder med de bredere netværkshandlinger, f.eks. identitet, DevOps, cloud, program, datavidenskab og andre forretningsteams for at sikre, at analysen af sikkerhedsoplysninger centraliseres og sikres. Derudover er SOC-teamet ansvarlig for at vedligeholde logge over dataene i brugbare og læsbare formater, hvilket kan omfatte fortolkning og normalisering af forskellige formater.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Etabler operationelt parathed for red-, blue- og purple-teamet

Hvert SOC-team bør teste sit beredskab som svar på en cyberhændelse. Test kan udføres via træningsøvelser, f.eks. table-tops og øvelseskørsler med forskellige personer inden for it, sikkerhed og på virksomhedsniveau. Individuelle træningstræningsteams oprettes på baggrund af repræsentative roller og spiller enten rollen som en forsvarer (Blue Team), en hacker (Red Team) eller som observatører, der søger at forbedre metoder og teknikker for både de blå og røde teams gennem styrker og svagheder, der afdækkes under øvelsen (Purple Team).

## <a name="next-step"></a>Næste trin

[Trin 2. Udfør en SOC-integrationsparathedsvurdering ved hjælp af Nul tillid Framework](integrate-microsoft-365-defender-secops-readiness.md)
