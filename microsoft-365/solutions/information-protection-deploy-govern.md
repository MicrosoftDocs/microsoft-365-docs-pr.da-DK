---
title: Regulerer oplysninger, der er underlagt databeskyttelsesreglerne
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
ms.custom: ''
description: Brug Microsoft 365 og politikker til at administrere personlige data i dit Microsoft 365 miljø.
ms.openlocfilehash: b131c90e83a2ce211d51af444dd570f71f3b8263
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590074"
---
# <a name="govern-information-subject-to-data-privacy-regulation"></a>Regulerer oplysninger, der er underlagt databeskyttelsesreglerne

Kontrol af informationsstyring kan anvendes i dit miljø som en hjælp til at opfylde krav i forbindelse med beskyttelse af personlige oplysninger, herunder et tal, der er specifikke for General Data Protection Regulation (GDPR), HIPAA-HITECH (UNITED States health care privacy act), California Consumer Protection Act (CCPA) og Brazil Data Protection Act (LGPD). 

Disse kontrolelementer falder primært ind i følgende løsningsområder:

- Opbevaringspolitikker
- Opbevaringsnavne
- Datastyring

## <a name="data-privacy-regulations-impacting-information-governance-controls"></a>Regler for beskyttelse af personlige oplysninger, der påvirker kontrolelementer til styring af oplysninger

Her er et eksempel på en liste over bestemmelser om beskyttelse af personlige oplysninger, der kan være relateret til styring af oplysninger:

- GDPR-artikel (13)(2)(a)
- GDPR-artikel (5)(1)(f)
- HIPAA-HITECH (45 CFR 164.312(c)(2))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(i))
- HIPAA-HITECH (45 CFR 164.316(b)(1)(ii))
- LGPD artikel 46

Du kan finde flere oplysninger om disse bestemmelser i artiklen vurdere [risici i forbindelse med beskyttelse af personlige oplysninger og identificere følsomme oplysninger](information-protection-deploy-assess.md).

For informationsstyring kræver regler for beskyttelse af data typisk følgende:

- Du bør anvende et teknisk skema til opbevaring og sletning af personlige data, der er gemt i Microsoft 365.
- Hvis du vil gemme personlige data, skal du informere emnet om, hvor længe dataene bliver gemt, hvilket er standardpraksis nu på front end-websystemer.
- Personlige data skal beskyttes mod utilsigtet behandling, tab eller ændring ved hjælp af kontrollerbare metoder.
- Alle handlinger, der udføres mod personlige data, skal dokumenteres, og denne dokumentation skal opbevares i en bestemt periode.

Da reglerne om beskyttelse af personlige oplysninger ikke er meget specifikke for opbevaring og sletning af data, skal der tages højde for andre faktorer, der kan diktere retningslinjer for styring af personlige oplysninger, der er gemt i dit Microsoft 365-abonnement. Her er et par eksempler:

- Forældelse af forbrugerkonti efter 5 års inaktivitet og kræver sletning eller anonymisering af kontodata efter dette tidspunkt, hvilket kræver tilpasning mellem systemet til lagring af data og arbejdsprocesser, der er relateret til meddelelser og anden automatisering.
- Konfiguration af regler for at holde politikker og procedurer relateret til GDPR gældende i tre år efter de er blevet fjernet, hvilket passer med organisationens opbevaringstidsplan for politikker og procedurer.
- Vedligeholdelse af et separat abonnement til kommunikation med forbrugere via supportorganisationen. Al mailkommunikation bevares og slettes efter to uger for at reducere enhver opsnindtning af privatlivsgæld i systemet.

Et vigtigt spørgsmål at besvare er: 

- Hvor lang tid skal oplysninger, der indeholder personlige data, bevares af gyldige forretningsmæssige årsager for at undgå at bruge denne fremgangsmåde permanent? Dette skal afbalanceres med opbevaringsbehovet for forretningskontinuitet.

Uanset de juridiske og forretningsmæssige grunde til at opbevare personlige oplysninger omkring eller slette dem, leverer Microsoft en række funktioner til implementering af din datastyringsplan i Microsoft 365.

## <a name="managing-information-governance-in-microsoft-365"></a>Administration af informationsstyring i Microsoft 365

Til at begynde med skal [du læse Administrer informationsstyring](../compliance/manage-information-governance.md) [og Dataopbevaring, Sletning og Microsoft 365](/office365/Enterprise/office-365-data-retention-deletion-and-destruction-overview).

### <a name="develop-data-retention-schedules-for-containers-email-and-content"></a>Udvikle tidsplaner for dataopbevaring til beholdere, mail og indhold

Vær opmærksom på følgende:

- Oprettelse af en dataopbevaringstidsplan for definerede oplysningstyper bør betragtes som en forudsætning for implementering af et opbevarings- eller sletningsskema.

- Med det antal oplysningstyper, som de fleste organisationer anser som vigtige og de tilsvarende store dataopbevaringsplaner, der sammen med dem, kræver implementering af en strategi for dataopbevaring og datastyring planlægning. 

- Nøglen til at etablere en effektiv datastyringsstrategi af denne type er at fokusere på de forretningsfunktioner og informationstyper, der har højeste prioritet, som kræver mere formel administration. Eksempler er juridiske kontrakter, regnskaber og lovgivningsdokumentation om overholdelse af regler og standarder. Prøv at undgå at have en separat opbevaringstidsplan for hver enkelt oplysningstype. Prøv at bruge generelle kategorier så meget som muligt, f.eks. med opbevaringsplaner på 7 år for generelt virksomhedsindhold.

- Når typerne af personlige oplysninger i dit miljø er bedre kendt, kan du fastlægge tidsplaner for opbevaring og sletning for denne type indhold og justere din informationsarkitektur for at gøre styringen af denne type oplysninger nemmere. Isoler f.eks. personlige oplysninger i separate websteder, biblioteker eller mapper med kontrolleret adgang.

### <a name="retention-policies-and-retention-labels"></a>Opbevaringspolitikker og opbevaringsnavne

Brug [opbevaringspolitikker og opbevaringsmærkater](../compliance/retention.md) til at bevare eller slette indhold i Microsoft 365, der indeholder eller forventes at indeholde personlige data.

### <a name="records-management"></a>Datastyring

Brug opbevaringsetiketter, der erklærer indhold som en post[, for at implementere en](../compliance/records-management.md) løsning til datastyring i Microsoft 365.

For beskyttelse af datas personlige oplysninger erklæres anmodninger fra den juridiske afdeling om datasikkerhed, og de kan gemmes på ubestemt tid eller bortkastes med dokumentation for at overholde de lovmæssige specifikationer for opbevaring af aktiviteter.