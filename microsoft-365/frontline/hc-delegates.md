---
title: Meddelelsesdelegering
author: samanro
ms.author: samanro
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: acolonna
description: Få mere at vide om, hvordan en bruger med statussen Ikke til stede eller Vil ikke forstyrres eksplicit kan angive en anden bruger som stedfortræder i sin statusmeddelelse.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 190b1f8bfdcf06c124163d97ecf77465f66ad67c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823974"
---
# <a name="message-delegation"></a>Meddelelsesdelegering

En bruger kan allerede eksplicit angive sin status til Ikke til stede eller Vil ikke forstyrres og angive brugerdefineret tekst. Funktionen meddelelsesdelegering fungerer på følgende måde:

1. En bruger @username nævner en anden bruger i en del af en tekststatusmeddelelse, hvilket antyder, at selvom de ikke er tilgængelige, skal du i stedet kontakte den @username nævnte bruger.
2. Den person, der er blevet tildelt som stedfortræder, får besked om, at vedkommende er blevet udnævnt til stedfortræder.
3. En person, der forsøger at kontakte den første bruger, kan derefter holde markøren over den indstillede stedfortræder og nemt sende en meddelelse til stedfortræderen i stedet.  

Dette er en proces, der er startet af brugeren, i klienten, og der kræves ingen Administration involvering for at aktivere funktionen. 

## <a name="delegation-use-scenario-in-healthcare"></a>Scenarie for delegeringsanvendelse i sundhedssektoren

*Eksempel på brug uden angivelse af stedfortrædere:*  Dr. Franco Piccio er på telefon hos afdelingen for radiologi. Han modtager en presserende personlig opfordring og er nødt til at træde væk i de næste par timer. Han beder en af hans ligemænd i radiologi afdelingen, Dr. Lena Ehrle, om at dække for ham, mens han er væk. Han uformelt afleverer sin personsøger til Dr. Ehrle, der lytter for presserende beskeder og pings på personsøgeren og reagerer på dem på vegne af Dr. Piccio i tillæg til hendes nuværende ansvar. Andre på holdet kan ikke indse den uformelle delegering skete, og forvirring opstår med en patient pleje.

*Eksempel på brug med indstillingsdelegerede:* Dr. Franco Piccio er på telefon hos afdelingen for radiologi. Han modtager en presserende personlig opfordring og er nødt til at træde væk i de næste par timer. Han beder en af hans ligemænd i radiologi afdelingen, Dr. Lena Ehrle til at dække for ham, mens han er væk. Han ændrer sin brugerdefinerede statusmeddelelse for at sige noget, der ligner "Jeg er ikke tilgængelig i de næste par timer. Kontakt @DrEhrle ved nødsituationer."  Andre på holdet indse, at delegationen skete, da de forsøger at kontakte Dr. Piccio, så de nu ved at kontakte Dr. Ehrle i mellemtiden. Kun lidt eller ingen forvirring giver en patient pleje.

## <a name="impact-of-co-existence-modes-on-user-status-in-the-teams-client"></a>Indvirkningen af tilstande for sam eksistens på brugerstatus i Teams-klienten

Administratorer skal være opmærksomme på, at funktionsmåden for omtale af statusnoter og delegering delvist afhænger af en brugers sam eksistenstilstand. Denne matrix viser mulighederne:

|Co-Existence-tilstand | Forventet funktionsmåde|
|---|---|
|Kun teams |Brugerne kan kun angive en note fra Teams. <br> Brugerens Teams-note er synlig i Teams & SfB. |
|Øer | Brugerens notesæt i Teams er kun synligt i Teams. <br> Brugerens notesæt i SfB er kun synligt i SfB |
|SfB*-tilstande | Brugerne kan kun angive en note fra SfB. <br> Brugerens SfB-note er synlig i SfB & Teams.  |
|||

En bruger kan kun angive en note i Teams, hvis vedkommendes tilstand er TeamsOnly eller Islands.  

### <a name="displaying-notes-set-in-skype-for-business"></a>Visning af noter, der er angivet i Skype for Business
  
Der er ingen visuel indikation for, at der er angivet en note fra Skype for Business.

Skype for Business gennemtvinger ikke en tegngrænse for statusnoter. Microsoft Teams viser kun de første 280 tegn i et notesæt fra Skype for Business. En ellipse (...) i slutningen af en note angiver afkortelse.
  
Skype for Business understøtter ikke udløbstider for noter.

Overførsel af noter fra Skype for Business til Teams understøttes ikke, når en bruger opgraderes til TeamsOnly-tilstand.

## <a name="related-topics"></a>Relaterede emner

[Sameksistens med Skype for Business](/microsoftteams/coexistence-chat-calls-presence)
