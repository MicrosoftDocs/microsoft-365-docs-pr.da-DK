---
title: Trin 1. Planlæg, Microsoft 365 Defender parathed for handlinger
description: Grundlæggende om planlægning af parathed Microsoft 365 Defender handlinger, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
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
ms.openlocfilehash: 45abe5dfa77e9ed224f2d55e15986eba732f2aff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598040"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Trin 1. Planlæg, Microsoft 365 Defender parathed for handlinger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Uanset den aktuelle udløbsdato for dine sikkerhedshandlinger er det vigtigt, at du justerer den efter din SOC (Security Operations Center). Der findes ikke nogen enkelt model, der passer til alle organisationer, men der er visse aspekter, der er mere almindelige end andre. 

De følgende afsnit beskriver soc-funktionernes kernefunktioner.

## <a name="provide-situational-awareness-of-modern-threats"></a>Gør opmærksom på situationen omkring moderne trusler

Et SOC-team forbereder sig på og opsporer nye og indgående trusler, så de kan samarbejde med organisationen om at opstille modforanstaltninger og svar. Dit SOC-team skal have medarbejdere, der er meget uddannet i moderne angrebsmetoder og -teknikker, og forstå trusselsbilledet. Delt trusselsintelligens og struktur som [Cyber Kill Chain](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) eller [MITRE ATT&CK-framework](https://attack.mitre.org/) kan give dine medarbejdere af trusselsanalytikere og trusselseksperter nye værktøjer.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Angiv først, andet og potentielt tredje niveau svar på cyberhændelser og begivenheder

SOC er frontlinjen i forsvar for sikkerhedshændelser og hændelser. Når en hændelse, trussel, angreb, overtrædelse af politik eller undersøgelse udløser en besked eller et opkald til handling, foretager SOC-teamet en vurdering for at undersøge og inddæmme og eskalere den til undersøgelse. Derfor skal svarere på første linje af SOC have et bredt teknisk kendskab til sikkerhedshændelser og indikatorer.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Centralisere overvågning og logføring af organisationens sikkerhedskilder 

SOC-teamets kernefunktion er som regel at sikre, at alle sikkerhedsenheder som f.eks firewalls, systemer til forebyggelse af indtrængen, systemer til forebyggelse af datatab, Håndtering af trusler og sikkerhedsrisici-systemer og identitetssystemer fungerer korrekt og overvåges. SOC-teams arbejder med de bredere netværkshandlinger som identitet, DevOps, sky, program, datavidenskab og andre forretningsteams for at sikre, at analysen af sikkerhedsoplysninger er centraliseret og sikret. SOC-teamet har desuden ansvaret for at vedligeholde logfiler over dataene i brugbare og læsbare formater, som kan omfatte fortolkning og normalisering af separate formater.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Opret driftsparathed for rødt, blåt og lilla team

Hvert SOC-team bør teste sin forberedelse til at reagere på en cyberhændelse. Test kan udføres via øvelser, f.eks. tabeltops og øvelsesløb med forskellige personer inden for it, sikkerhed og på virksomhedsniveau. Individuelle træningshold oprettes ud fra repræsentative roller og spiller enten rollen som en defender (Blåt Team), en hacker (rødt team) eller som angrebsmand, der søger efter at forbedre metoder og teknikker for både det Blå og Røde team gennem styrker og forbedringer, der er blevet afdækket under øvelsen (lilla hold).

## <a name="next-step"></a>Næste trin

[Trin 2. Udfør en vurdering af parathed for SOC-integration ved hjælp af Zero Trust Framework](integrate-microsoft-365-defender-secops-readiness.md)
