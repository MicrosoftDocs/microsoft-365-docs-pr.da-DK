---
title: Få vist resultaterne af en automatisk undersøgelse i Microsoft 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automatiseret, undersøgelse, afhjælpning, handlinger
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Under og efter en automatiseret undersøgelse i Microsoft 365 kan du få vist resultaterne og de vigtigste resultater.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6e3234168383a0dad6d8a9de3fb680b27b7ce6cb
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139689"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Detaljer og resultater af en automatisk undersøgelse i Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Når der forekommer en [automatiseret undersøgelse](office-365-air.md) i [Microsoft Defender for Office 365](defender-for-office-365.md), er oplysninger om undersøgelsen tilgængelige under og efter den automatiserede undersøgelsesproces. Hvis du har de nødvendige tilladelser, kan du få vist disse oplysninger på Microsoft 365 Defender-portalen. Undersøgelsesdetaljer giver dig opdateret status og mulighed for at godkende eventuelle ventende handlinger.

> [!TIP]
> Se den nye, samlede undersøgelsesside på portalen Microsoft 365 Defender. Du kan få mere at vide under [(NY!) Unified Investigation-side](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>Undersøgelsesstatus

Undersøgelsesstatussen angiver status for analysen og handlingerne. I takt med at undersøgelsen kører, ændres status for at angive, om der blev fundet trusler, og om handlinger er blevet godkendt.

|Status|Beskrivelse|
|---|---|
|**Start**|Undersøgelsen er blevet udløst og venter på at begynde at køre.|
|**Kører**|Undersøgelsesprocessen er startet og er i gang. Denne tilstand forekommer også, når [ventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) godkendes.|
|**Der blev ikke fundet nogen trusler**|Undersøgelsen er afsluttet, og der blev ikke identificeret nogen trusler (brugerkonto, mail, URL-adresse eller fil). <p> **TIP**! Hvis du har mistanke om, at noget blev overset (f.eks. et falsk negativt), kan du udføre handlinger ved hjælp af [Threat Explorer](threat-explorer.md).|
|**Delvist undersøgt**|Den automatiserede undersøgelse fandt problemer, men der er ingen specifikke afhjælpningshandlinger til at løse disse problemer. <p> Status **for Delvist undersøgt** kan forekomme, når en eller anden type brugeraktivitet blev identificeret, men ingen oprydningshandlinger er tilgængelige. Eksempler omfatter en af følgende brugeraktiviteter: <ul><li>En [hændelse til forebyggelse af datatab](../../compliance/dlp-learn-about-dlp.md)</li><li>En mail, der sender uregelmæssigheder</li><li>Sendt malware</li><li>Sendt phish</li></ul> <p> **Bemærk**! Denne **delvist undersøgte** status, der bruges til at blive mærket som **Fundne trusler**. <p> Undersøgelsen fandt ingen skadelige URL-adresser, filer eller mailmeddelelser, der skal afhjælpes, og ingen postkasseaktivitet at løse, f.eks. deaktivering af regler for videresendelse eller delegering. <p> **Tip**: Hvis du har mistanke om, at noget blev overset (f.eks. et falsk negativt), kan du undersøge og udføre handlinger ved hjælp af [Threat Explorer](threat-explorer.md)|
|**Afbrudt af systemet**|Undersøgelsen stoppede. En undersøgelse kan stoppe af flere årsager: <ul><li>Undersøgelsens ventende handlinger er udløbet. Ventende handlinger får timeout, efter at der er ventet på godkendelse i en uge</li><li>Der er for mange handlinger. Hvis der f.eks. er for mange brugere, der klikker på skadelige URL-adresser, kan det overskride undersøgelsens mulighed for at køre alle analyserne, så undersøgelsen stopper</li></ul> <p> **TIP**! Hvis en undersøgelse stopper, før der blev udført handlinger, kan du prøve at bruge [Threat Explorer](threat-explorer.md) til at finde og håndtere trusler.|
|**Ventende handling**|Undersøgelsen har fundet en trussel, f.eks. en skadelig mail, en skadelig URL-adresse eller en risikofuld postkasseindstilling og en handling til at afhjælpe denne trussel, der [afventer godkendelse](air-review-approve-pending-completed-actions.md). <p> Tilstanden **Ventende handling** udløses, når der findes en trussel med en tilsvarende handling. Listen over ventende handlinger kan dog øges, når en undersøgelse køres. Vis undersøgelsesdetaljer for at se, om andre elementer stadig afventer fuldførelse.|
|**Afhjælpet**|Undersøgelsen blev afsluttet, og alle afhjælpningsforanstaltninger blev godkendt (noterede sig, at de var fuldt afhjælpede). <p> **BEMÆRK**! Godkendte afhjælpningshandlinger kan have fejl, der forhindrer, at handlingerne udføres. Uanset om afhjælpningshandlinger er fuldført, ændres undersøgelsesstatussen ikke. Vis undersøgelsesdetaljer.|
|**Delvist afhjælpet**|Undersøgelsen resulterede i afhjælpende foranstaltninger, og nogle blev godkendt og afsluttet. Andre handlinger [afventer](air-review-approve-pending-completed-actions.md) stadig.|
|**Mislykkedes**|Mindst én undersøgelsesanalyse stødte på et problem, hvor det ikke kunne fuldføres korrekt. <p> **BEMÆRK** Hvis en undersøgelse mislykkes, efter at afhjælpningshandlinger blev godkendt, kan afhjælpningshandlingerne stadig være lykkedes. Få vist oplysninger om undersøgelsen.|
|**Sat i kø af begrænsning**|En undersøgelse tilbageholdes i en kø. Når andre undersøgelser er fuldført, startes efterforskninger i kø. Begrænsning hjælper med at undgå dårlig tjenesteydeevne.  <p> **TIP**! Ventende handlinger kan begrænse, hvor mange nye undersøgelser der kan køre. Sørg for at [godkende (eller afvise) ventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Afbrudt af begrænsning**|Hvis en undersøgelse opbevares i køen for længe, stopper den. <p> **Tip**: Du kan [starte en undersøgelse fra Threat Explorer](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|

## <a name="view-details-of-an-investigation"></a>Få vist detaljer om en undersøgelse

1. Gå til Microsoft 365 Defender-portalen (<https://security.microsoft.com>), og log på.
2. Vælg **Løsningscenter** i navigationsruden.
3. Vælg en handling under fanerne **Ventende** eller **Oversigt** . Dens pop op-rude åbnes.
4. Vælg **Åbn undersøgelsesside** i pop op-ruden. 
5. Brug de forskellige faner til at få mere at vide om undersøgelsen.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Få vist oplysninger om en besked, der er relateret til en undersøgelse

Visse typer beskeder udløser en automatisk undersøgelse i Microsoft 365. Du kan få mere at vide under [Vigtige politikker, der udløser automatiserede undersøgelser](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Gå til Microsoft 365 Defender-portalen (<https://security.microsoft.com>), og log på.
2. Vælg **Løsningscenter** i navigationsruden.
3. Vælg en handling under fanerne **Ventende** eller **Oversigt** . Dens pop op-rude åbnes.
4. Vælg **Åbn undersøgelsesside** i pop op-ruden.
5. Vælg fanen **Beskeder** for at få vist en liste over alle de beskeder, der er knyttet til undersøgelsen.
6. Vælg et element på listen for at åbne dets pop op-rude. Der kan du få vist flere oplysninger om beskeden.

## <a name="keep-the-following-points-in-mind"></a>Vær opmærksom på følgende punkter

- Antallet af mails beregnes på tidspunktet for undersøgelsen, og nogle optællinger genberegnes, når du åbner undersøgelses-pop op-vinduet (baseret på en underliggende forespørgsel).

- De mailantal, der vises for mailklynger under fanen **Mail** og den værdi for mailantal, der vises på klyngens pop op-vindue, beregnes på undersøgelsestidspunktet og ændres ikke.

- Antallet af mails, der vises nederst på fanen **Mail** i pop op-vinduet Mailklynge, og antallet af mails, der vises i Stifinder, afspejler de mails, der er modtaget efter undersøgelsens indledende analyse.

  En mailklynge, der viser en oprindelig mængde på 10 mails, viser således en mailliste på i alt 15, når der modtages yderligere fem mails mellem undersøgelsesanalysefasen, og når administratoren gennemgår undersøgelsen. På samme måde kan gamle undersøgelser begynde at vise højere antal, end Explorer-forespørgsler viser, fordi data i Microsoft Defender for Office 365 Plan 2 udløber efter syv dage for prøveversioner og efter 30 dage for betalte licenser.

  Der vises både antal historiske og aktuelle optællinger i forskellige visninger for at angive mailpåvirkningen på undersøgelsestidspunktet og den aktuelle indvirkning indtil det tidspunkt, hvor afhjælpningen køres.

- I forbindelse med mail kan du få vist en trusselsoverflade for uregelmæssigheder i volumen som en del af undersøgelsen. En uregelmæssighed i mængden angiver en stigning i lignende mails omkring undersøgelseshændelsens tid sammenlignet med tidligere tidsrammer. En stigning i mailtrafik sammen med visse egenskaber (f.eks. emne- og afsenderdomæne, kropslighed og afsender-IP) er typisk for starten af mailkampagner eller angreb. Massekampagner, spam og legitime mailkampagner deler dog ofte disse egenskaber.

- Volumenuregelmæssigheder repræsenterer en potentiel trussel og kan derfor være mindre alvorlige sammenlignet med malware- eller phishtrusler, der identificeres ved hjælp af antivirusprogrammer, detonation eller ondsindet omdømme.

- Du behøver ikke at godkende alle handlinger. Hvis du ikke er enig i den anbefalede handling, eller din organisation ikke vælger visse typer handlinger, kan du vælge at **afvise** handlingerne eller blot ignorere dem og ikke foretage dig noget.

- Godkendelse og/eller afvisning af alle handlinger gør det muligt at lukke undersøgelsen fuldt ud (status bliver afhjælpet), mens visse handlinger er ufuldstændige, hvilket medfører, at undersøgelsesstatussen ændres til en delvist afhjælpet tilstand.

## <a name="next-steps"></a>Næste trin

- [Gennemse og godkend ventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
