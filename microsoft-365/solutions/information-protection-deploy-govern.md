---
title: Styr de oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Brug Microsoft 365-opbevaringsmærkater og -politikker til at administrere personlige data i dit Microsoft 365-miljø.
ms.openlocfilehash: 2643e183b9121e7e82a3237bde4d977315667008
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748775"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Styr de oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger

Kontrolelementer til styring af oplysninger kan anvendes i dit miljø for at hjælpe med at håndtere overholdelse af angivne standarder for beskyttelse af personlige oplysninger, herunder et tal, der er specifikt for den generelle forordning om databeskyttelse (GDPR), HIPAA-HITECH (loven om beskyttelse af personlige oplysninger for USA sundhedspleje), California Consumer Protection Act (CCPA) og LGPD (Brazil Data Protection Act). 

Disse kontrolelementer falder primært inden for følgende løsningsområder:

- Opbevaringspolitikker
- Opbevaringsmærkater
- Datastyring

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Bestemmelser om beskyttelse af personlige oplysninger, der påvirker styringskontroller for oplysninger

Her er et eksempel på en liste over bestemmelser om beskyttelse af personlige oplysninger, der kan relatere til kontrolelementer for styring af oplysninger:

- GDPR-artikel (13)(2)(a)
- GDPR-artikel (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD-artikel 46

Du kan finde flere oplysninger om disse regler i [artiklen vurder risici for beskyttelse af personlige oplysninger og identificer følsomme oplysninger](information-protection-deploy-assess.md).

I forbindelse med styring af oplysninger kræver bestemmelser om beskyttelse af personlige oplysninger typisk følgende:

- Du skal anvende en teknisk ordning til opbevaring og sletning af personlige data, der er gemt i Microsoft 365.
- Hvis du vil gemme personlige data, skal du informere den registrerede om, hvor længe dataene gemmes, hvilket er en standardpraksis nu på frontendwebsystemer.
- Personlige data bør beskyttes mod utilsigtet behandling, tab eller ændring ved hjælp af verificerbare metoder.
- Enhver handling, der udføres mod personlige data, skal dokumenteres, og denne dokumentation skal opbevares i en bestemt periode.

Da reglerne for beskyttelse af personlige oplysninger ikke er særlig specifikke, når det gælder opbevaring og sletning af data, skal der tages hensyn til andre faktorer, der kan diktere retningslinjer for styring af oplysninger for personlige oplysninger, der er gemt i dit Microsoft 365-abonnement. Her er nogle få eksempler:

- Sletning af forbrugerkonti efter 5 års inaktivitet og kræver sletning eller anonymisering af kontodata efter dette tidspunkt, hvilket kræver orkestrering mellem systemet, der lagrer data og arbejdsprocesser relateret til meddelelser og anden automatisering.
- Konfiguration af regler for at holde politikker og procedurer relateret til GDPR omkring i tre år, efter at de er blevet tilsidesat, hvilket er i overensstemmelse med organisationens opbevaringsplan for politikker og procedurer.
- Vedligeholdelse af et separat abonnement til kommunikation med forbrugere via dens supportorganisation. Al e-mail-kommunikation blev opbevaret og slettet efter to uger for at reducere eventuelle oprustning af privatlivets fred i systemet.

Et vigtigt spørgsmål at besvare er: 

- Hvor længe skal oplysninger, der indeholder personlige data, opbevares af gyldige forretningsmæssige årsager for at undgå at "beholde dem for evigt"? Dette skal afbalanceres med opbevaringsbehov for forretningskontinuitet.

Uanset de juridiske og forretningsmæssige årsager til at bevare personlige oplysninger omkring eller slette dem, tilbyder Microsoft en række funktioner til at implementere din ordning for datastyring i Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Administration af styring af oplysninger i Microsoft 365

For at begynde [med skal du se Styr dine data med Microsoft Purview](../compliance/manage-data-governance.md) og [Data retention, Deletion and Destruction i Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Udvikl planer for dataopbevaring for objektbeholdere, mail og indhold

Vær opmærksom på følgende:

- Oprettelse af en tidsplan for dataopbevaring for definerede oplysningstyper bør betragtes som en forudsætning for at implementere enhver ordning for opbevaring eller sletning.

- På grund af det antal informationstyper, som de fleste organisationer anser for vigtige, og de tilsvarende store opbevaringsplaner for poster, der følger med dem, kræver implementering af en strategi for dataopbevaring og datastyring planlægning. 

- Nøglen til at etablere en effektiv strategi for datastyring af denne type er at fokusere på de højeste prioriterede forretningsfunktioner og informationstyper, der kræver mere formel administration. Eksempler er juridiske kontrakter, årsregnskaber og dokumentation til lovmæssig overholdelse af angivne standarder. Prøv at undgå at have en separat opbevaringsplan for hver enkelt oplysningstype. Prøv at bruge generelle kategorier så meget som muligt, f.eks. med opbevaringsplaner på 7 år for generelt forretningsindhold.

- Når de personlige oplysningstyper i dit miljø er bedre kendt, kan du oprette opbevarings- og sletningsplaner for denne type indhold og justere din informationsarkitektur for at gøre styringen af denne type oplysninger nemmere. Du kan f.eks. isolere personlige oplysninger på separate websteder, biblioteker eller mapper med kontrolleret adgang.

### <a name="retention-policies-and-retention-labels"></a>Opbevaringspolitikker og opbevaringsmærkater

Brug [opbevaringspolitikker og opbevaringsmærkater](../compliance/retention.md) til at bevare eller slette indhold i Microsoft 365, der indeholder eller forventes at indeholde personlige data.

### <a name="records-management"></a>Datastyring

Brug opbevaringsmærkater, der deklarerer indhold for en post, til at implementere en [løsning til dataadministration](../compliance/records-management.md) for data i Microsoft 365.

I forbindelse med databeskyttelse erklæres DSR-anmodninger (data subject requests), der modtages af den juridiske afdeling, som en post og kan gemmes på ubestemt tid eller bortskaffes med bevis for at overholde lovmæssige specifikationer for aktivitetsopbevaring.