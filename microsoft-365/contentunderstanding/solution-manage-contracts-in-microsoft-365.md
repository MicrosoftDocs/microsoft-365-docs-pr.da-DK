---
title: Administrer kontrakter ved hjælp af en Microsoft 365 løsning
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
ms.collection:
- m365solution-managecontracts
- m365solution-overview
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Få mere at vide om, hvordan du administrerer kontrakter Microsoft 365 en SharePoint Syntex, SharePoint lister, Microsoft Teams og Power Automate.
ms.openlocfilehash: 86ccbeef283b165e178b12debd3ae99f982afc04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63595926"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a>Administrer kontrakter ved hjælp af en Microsoft 365 løsning

I denne artikel beskrives det, hvordan du opretter en løsning til administration af kontrakter for din organisation ved hjælp SharePoint Syntex og komponenter Microsoft 365. Det giver dig en ramme, der kan hjælpe dig med at planlægge og oprette en løsning, der passer til dine unikke forretningsmæssige behov. Selvom denne løsning handler om kontraktstyring, kan du tilpasse den til at oprette andre dokumentstyringsløsninger, f.eks. til arbejdsopgørelser eller fakturaer.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWJUR0]

</br>

## <a name="identify-the-business-problem"></a>Identificer forretningsproblemet

Det første trin i planlægningen af dit kontraktstyringssystem er at forstå det problem, du forsøger at løse. For denne løsning skal der løses fire vigtige problemer:

- **Identificer kontrakter**. Din organisation arbejder med mange dokumenter, f.eks. fakturaer, kontrakter, arbejdsopgørelser osv.  Nogle er digitale aktiver, der sendes via mail, og nogle er papiraktiver, der sendes via traditionel mail. Du har brug for en metode til at identificere alle kundekontrakter fra alle andre dokumenter og derefter klassificere dem som sådanne.

- **Spor historikken for kontraktgodkendelser**. Din organisation har brug for en pålidelig metode til at finde ud af, om kontrakter er blevet godkendt eller afvist, og om betalingen er blevet behandlet. 

- **Websted til administration af godkendelse af kontrakt**. Din organisation skal oprette et samarbejdswebsted, hvor alle nødvendige interessenter nemt kan gennemse kontrakter. Interessenter bør kunne gennemgå hele kontrakten, hvis det er nødvendigt, men som oftest er interesserede i at se flere nøglefelter fra hver kontrakt (f.eks. kundenavn, IP-nummer og samlede omkostninger). Interessenter bør nemt kunne godkende eller afvise indgående kontrakter.

- **Distribuere reviderede kontrakter**. Godkendte og afviste kontrakter skal distribueres gennem en bestemt arbejdsproces. Godkendte kontrakter skal distribueres til en tredjepartsanmodning om betalingsbehandling. Afviste kontrakter skal distribueres til yderligere gennemgang.

## <a name="overview-of-the-solution"></a>Oversigt over løsningen

  ![Diagram over løsningen ved hjælp SharePoint Syntex, SharePoint lister, Teams og Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

Denne vejledning til kontraktadministrationsløsninger indeholder fire komponenter Microsoft 365:

- **Microsoft SharePoint Syntex**: Opret modeller til at identificere og klassificere dine kontraktfiler, og udtræk derefter de relevante data fra dem.

- **Microsoft SharePoint lister**: Brug den formatering, der er tilgængelig i moderne SharePoint til at præsentere kontrakter i et virksomhedsvenligt format.

- **Microsoft Teams**: Brug funktionaliteten i en Teams-kanal og tilknyttede faner for at give dine interessenter mulighed for at gennemse og administrere kontrakter.

- **Power Automate**: Brug flows til at føre kontrakter gennem godkendelsesprocessen og derefter til en tredjepartsbetalingsprogram.

### <a name="how-it-all-works"></a>Sådan fungerer det hele

  ![Diagram over løsningen, der viser arbejdsprocessen til overførsel af dokumenter, udtrække data, underrette interessenter samt godkende eller afvise kontrakten.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. Dokumenter overføres til et SharePoint dokumentbibliotek. En SharePoint Syntex dokumentforståelsesmodel er blevet anvendt i dokumentbiblioteket. Den kontrollerer hver fil for at se, om der findes en hvilken som helst type indholdstype, som den er trænet til at søge efter. Hvis der findes et match, klassificeres filen som en "kontrakt", og indholdstypen for dokumentet opdateres.

2. Modellen trækker også specifikke data ud fra hver kontraktfil, som interessenter er interesseret i at se, f.eks. beløb til *Klient, Leverandør* *og Gebyr*.

    Følgende side er et eksempel på en kontrakt, som modellen er trænet til at identificere.

      ![Eksempel på en kontrakt.](../media/content-understanding/contract.png)

3. I Microsoft Teams er alle interessenter medlemmer af en sikker Teams kanal, hvor alle kontrakter i dokumentbiblioteket kan ses til godkendelse eller afvisning. Ved at Teams-funktionaliteten får alle interessenter besked, når nye kontrakter skal gennemgås.

4. Ved hjælp Power Automate, flyttes kontrakter gennem godkendelsesprocessen i den Teams kanal. Når et medlem godkender en kontrakt, ændres kontraktstatus til godkendt, alle medlemmer får besked via et Teams-indlæg, og der oprettes et linjeelement for at vise, at kontrakten er klar til betaling. Denne proces kan udvides til at skrive direkte til en tredjeparts finansiel ansøgning om betaling.

5. Når et medlem afviser en kontrakt, ændres status til afvist, og alle medlemmer underrettes via et Teams indlæg.

6. Det endelige resultat af denne løsning er en automatiseret forretningsproces for din organisation. Medarbejdere kan nemt bruge den brugerdefinerede feltvisning i Teams til at starte og overvåge arbejdsprocessen for godkendelse af dine dokumenter. 

     ![Fanen Kontrakter.](../media/content-understanding/tile-view.png)

### <a name="licensing-requirements"></a>Licenskrav

Denne løsning afhænger af følgende funktionalitet, der alle er tilgængelig som en del af en Microsoft 365 Enterprise-licens (E1, E3, E5, F3) eller Business (Basic, Standard eller Premium):

- Microsoft SharePoint Syntex
- Microsoft Teams
- Power Automate

### <a name="learn-how-to-use-sharepoint-syntex"></a>Lær at bruge SharePoint Syntex

Er du ny SharePoint Syntex? Få mere at vide om, SharePoint Syntex du administrerer indhold ved hjælp af AI.

Med [Introduktion til](/learn/paths/syntex-get-started) SharePoint Syntex-læringssti lærer du, hvordan du kan bruge dokumentforståelse og modeller til formbehandling til at klassificere dokumenter, udtrække tekst og navndele dine dokumenter for at få hurtig og nem vidensstyring.

## <a name="create-the-solution"></a>Opret løsningen

De næste afsnit gennemgår, hvordan du konfigurerer din løsning til administration af kontrakter. Den er opdelt i tre trin:

- [Trin 1. Brug SharePoint Syntex til at identificere kontraktfiler og udtrække data](solution-manage-contracts-step1.md)
- [Trin 2. Brug Microsoft Teams til at oprette din kontraktadministrationskanal](solution-manage-contracts-step2.md)
- [Trin 3. Brug Power Automate til at oprette flowet til at behandle dine kontrakter](solution-manage-contracts-step3.md)
