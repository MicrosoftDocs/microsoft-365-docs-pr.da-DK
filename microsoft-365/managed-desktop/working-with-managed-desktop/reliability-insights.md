---
title: Pålidelighedsindsigt
description: ''
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 06e1446ca290439c9e6689f4461c825438cf6aaf
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2021
ms.locfileid: "63588757"
---
# <a name="reliability-insights"></a>Pålidelighedsindsigt

Denne visning giver dig en tilstandsoversigt over dine administrerede enheder. Hvis du vil have vist pålidelighedsdata, skal du **vælge fanen** Pålidelighed.


![Ruden Pålidelighed: Pålidelighed på tværs af enheder øverst til venstre, graf over pålidelighed over tid øverst til højre, vigtigste problemtabel på tværs af bunden. Knapperne Hjælp og feedback nederst til højre.](../../media/insights_reliability.png)

Afsnittet **Pålidelighed** på tværs af enheder indeholder en hurtig tilstandsoversigt over din installation i løbet af de seneste 14 dage ved at rapportere procentdelen af enheder, der betragtes som "sunde", og den gennemsnitlige tid, der er observeret siden den seneste rapporterede fejl. 

 
**Grafen Pålidelighed over** tid til højre rapporterer antallet af enheder med kritiske fejl og det samlede antal observerede kritiske fejl over tid.

Afsnittet **Vigtigste problemer** beskriver specifikke registrerede problemer, der påvirker mindst 5 % af dine administrerede enheder. Rapporterede detaljer omfatter:

- Typen af problem
    - Programmet går ned, hvor en app stopper med at fungere eller uventet stopper
    - Programmet hænger, hvor et program holder op med at svare på input
    - Kritiske fejl, der opstår, når Windows har oplevet et problem, som det ikke kan gendanne fra
- Antallet af enheder, der er påvirket af det samme problem
- Procentdelen af administrerede enheder, der repræsenterer
- Det samlede antal forekomster af det specifikke problem
- Den softwarekomponent, der ser ud til at være kilden til problemet
- Kategorien for det registrerede problem:
    - Browser (Edge, Chrome, IE)
    - Ukendt (ikke-Microsoft-komponenter)
    - Driver (lyd, grafik eller andre drivere)
    - Produktivitet (Slæk, G-pakker, Microsoft Office og dets tilføjelses- eller udvidelser Teams)
    - Medier (billed-, musik- eller videoapps
    - Sikkerhed (Windows sikkerhedskomponenter)
- Den aktuelle status, når Microsoft-administrerede skrivebordshandlinger undersøger og afhjælper problemet

