---
title: Secure Messaging til organisationer i sundhedssektoren, der bruger Microsoft Teams
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
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: Få mere at vide om, hvordan du tilpasser en Secure Messaging-politik for Microsoft Teams, der kan indeholde kvitteringer for læsning og prioritetsmeddelelser.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 2116434f4149a8fdb7985ecaa7b5cf67eb686a81
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824101"
---
# <a name="secure-messaging-for-healthcare-organizations"></a>Sikre beskeder til organisationer i sundhedssektoren

Meddelelsespolitikker bruges til at styre, hvilke chat- og kanalmeddelelsesfunktioner der er tilgængelige for brugere i Microsoft Teams, og er en del af den overordnede udrulning af Secure Messaging til sundhedssektoren, f.eks. hospitaler, klinikker eller lægekontorer, hvor det er afgørende at få en besked samlet og handlet rettidigt, og det er også vigtigt at vide, når vigtige meddelelser læses.

Du kan bruge den globale politik (standardpolitik for hele organisationen) eller oprette en eller flere brugerdefinerede meddelelsespolitikker for personer i din organisation. Brugere i din organisation får automatisk den globale politik, medmindre du opretter og tildeler en brugerdefineret politik. Når du har oprettet en brugerdefineret politik, kan du tildele den en bruger eller grupper af brugere i din organisation. Du kan f.eks. vælge kun at tillade, at visse jobroller bruger disse funktioner (måske kun læger og sygeplejersker) og andre arbejdstagere (f.eks. pedellen eller køkkenpersonalet) for at få et mere begrænset sæt funktioner. Beslut dig selv for, hvilke behov din organisation har. Vejledningen her er højst et forslag.

Politikker kan nemt administreres i [Microsoft Teams Administration](https://admin.teams.microsoft.com) ved at logge på med administratorlegitimationsoplysninger og vælge **Meddelelsespolitikker** i venstre navigationsrude.

 :::image type="content" source="media/hc-messaging-policy-admin-center-new.png" alt-text="Skærmbillede af siden Meddelelsespolitikker." lightbox="media/hc-messaging-policy-admin-center-new.png":::
 
 Hvis du vil redigere den eksisterende standardmeddelelsespolitik for din organisation, skal du klikke på **Global (standard for hele organisationen)** og derefter foretage dine ændringer. Hvis du vil oprette en ny brugerdefineret meddelelsespolitik, skal du klikke på **Tilføj** og derefter vælge dine indstillinger. Vælg **Gem** , når du er færdig.

![Skærmbillede af indstillinger for meddelelsespolitik.](media/hc-messaging-policy.png)

Følgende indstillinger er af særlig interesse for sundhedssektoren og bør overvejes, når du designer en brugerdefineret politik, der bruges i sundhedssektoren:

## <a name="read-receipts"></a>Kvitteringer for læsning

Kvitteringer for læsning giver afsenderen af en chatbesked besked om, hvornår vedkommendes meddelelse blev læst af modtageren i 1:1 og gruppechats med 20 personer eller mindre. Brug denne indstilling til at angive, om kvitteringer for læsning styres af brugeren, til for alle eller fra for alle. Kvitteringer for læsning af meddelelser er vigtige i sundhedssektoren, fordi de fjerner usikkerhed om, hvorvidt en meddelelse blev læst.

I forbindelse med sundhedssektoren skal du vælge enten **Brugerkontrolleret** eller **Slået til for alle**. Vær opmærksom på, at når du bruger indstillingen **Slået til for alle** , er den eneste måde at angive kvitteringer for hele lejeren på enten kun at have én meddelelsespolitik for hele lejeren (standardpolitikken med navnet "Global (Standard for hele organisationen)") eller for at få alle meddelelsespolitikker i lejeren til at bruge de samme indstillinger for kvitteringer. Funktionen kvitteringer for læsning er mest effektiv, når funktionen er aktiveret til **Til for alle**.

*Eksempel på brug uden kvitteringer for læsning:* Højrisikopatient Jakob Roth indlægges på hospitalet.  Sofia Krause er en sygeplejerske, der arbejder som en del af det tværfaglige team (IDT) af læger, herunder forskellige specialister, er udpeget som den primære pleje koordinator med ansvar for denne patient.  Sofia sender mails og andre chatbeskeder til en gruppe sygeplejersker og læger, der bruger en række meddelelsesklienter og apps og ofte ikke får noget svar eller en indikation af, om en meddelelse blev læst af teammedlemmer. På grund af sammenfiltrede kommunikationsprocesser bliver Jakobs medicin anvendt forkert, og hans ophold på hospitalet forlænges.

*Eksempel på anvendelse med kvitteringer for læsning:* Højrisikopatient Jakob Roth indlægges på hospitalet.  Sofia Krause er en sygeplejerske, der arbejder som en del af det tværfaglige team (IDT) af læger, herunder forskellige specialister, er udpeget som den primære pleje koordinator med ansvar for denne patient.  Sofia starter en gruppe snak med et sæt læger og andre sygeplejersker, der vil arbejde med patienten til at koordinere pleje og starter en nødsituation triage.  Sygeplejersker og læger kommunikerer og samarbejder om patientens plejeplan i hele plejekoordineringsprocessen.  Vigtige og presserende meddelelser sendes via 1:1 og gruppechatsamtaler. Sofia bruger funktionaliteten til kvitteringer for læsning til at afgøre, om meddelelser, der sendes med anmodning om support, leveres og læses af de målrettede læger eller sygeplejersker. Jakobs patientresultater er næsten optimale, og han kommer tidligere hjem, fordi hans sundhedsteam kommunikerer problemfrit.

## <a name="send-urgent-messages-using-priority-notifications"></a>Send vigtige meddelelser ved hjælp af prioritetsmeddelelser

En bruger kan markere en meddelelse som *presserende* , når der sendes chatbeskeder til andre brugere. Denne funktion hjælper hospitalspersonalet med at advare hinanden, når en kritisk hændelse kræver deres opmærksomhed. I modsætning til almindelige *vigtige* meddelelser giver [prioritetsmeddelelser](https://support.microsoft.com/article/mark-a-message-as-important-or-urgent-in-teams-ea99d5b6-1317-4550-8d75-86ff14cd4462) brugerne besked hvert andet minut i op til 20 minutter, eller indtil meddelelsen er samlet op og læst af modtageren, hvilket maksimerer sandsynligheden for, at meddelelsen reageres rettidigt.

En administrator kan aktivere eller deaktivere muligheden for, at brugere, der har fået tildelt denne politik, kan sende prioritetsmeddelelser. Denne funktion er som standard slået til. Modtageren af prioritetsmeddelelsen har muligvis ikke den samme meddelelsespolitik og har ikke mulighed for at deaktivere modtagelse af prioritetsmeddelelser. I forbindelse med sundhedssektoren anbefaler vi, at du aktiverer funktionen for i det mindste nogle brugere, men du skal afgøre, hvilke der er.

*Eksempel på brug:* Sofia Krause er ved at eftertage en højrisikopatient, Jakob Roth. Manuela Carstens, en læge, er den primære sundhedsplejerske for denne patient.  Sofia sender et budskab til Manuela ved hjælp af en prioriteret meddelelse, der beder om øjeblikkelig hjælp med triage af Jakob.  Manuelas telefon modtager meddelelsen, men Manuela følte ikke telefonens vibration og svarer ikke. Teams giver Manuela besked igen og vil fortsat give besked igen, indtil hun læser meddelelsen. Hvis kvitteringer for læsning også er aktiveret, kan Sofia være opmærksom på, at meddelelsen blev læst af Manuela, selv før Manuela beslutter, hvordan hun vil svare.

## <a name="related-topics"></a>Relaterede emner

- [Administrer meddelelsespolitikker i Teams](/microsoftteams/messaging-policies-in-teams)
- [Kom i gang med Teams til sundhedssektoren](teams-in-hc.md)
