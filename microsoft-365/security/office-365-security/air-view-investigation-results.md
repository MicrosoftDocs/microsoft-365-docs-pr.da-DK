---
title: Få vist resultaterne af en automatisk undersøgelse i Microsoft 365
keywords: AIR, autoIR, Microsoft Defender til slutpunkt, automatiseret, undersøgelse, afhjælpning, handlinger
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
description: Under og efter en automatiseret undersøgelse af Microsoft 365, kan du se resultaterne og de vigtigste resultater.
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bf9fe34a88444d9d8ec6dccf4b22a507e55dfb00
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680792"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a>Detaljer og resultater af en automatisk undersøgelse i Microsoft 365

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Når en [automatisk undersøgelse](office-365-air.md) finder sted [i Microsoft Defender for Office 365](defender-for-office-365.md), er det muligt at få mere at vide om undersøgelsen under og efter den automatiske undersøgelsesproces. Hvis du har de nødvendige tilladelser, kan du få vist disse oplysninger i Microsoft 365 Defender portal. Undersøgelsesoplysninger giver dig opdateret status og mulighed for at godkende eventuelle afventende handlinger.

> [!TIP]
> Se den nye, samlede undersøgelsesside i Microsoft 365 Defender portal. Du kan få mere at vide under [(NY!) Siden Samlet undersøgelse](../defender/m365d-autoir-results.md#new-unified-investigation-page).

## <a name="investigation-status"></a>Undersøgelsesstatus

Status for undersøgelsen angiver status for analysen og handlingerne. I løbet af undersøgelsen ændres status for at angive, om der blev fundet trusler, og om handlingerne er blevet godkendt.

|Status|Beskrivelse|
|---|---|
|**Starter**|Undersøgelsen er blevet udløst og venter på at begynde at køre.|
|**Kører**|Undersøgelsesprocessen er startet og er i gang. Denne tilstand opstår også, når [afventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) godkendes.|
|**Der blev ikke fundet nogen trusler**|Undersøgelsen er afsluttet, og der blev ikke identificeret nogen trusler (brugerkonto, mail, URL-adresse eller fil). <p> **Tip**: Hvis du har mistanke om, at noget er gået glip af (f.eks. en falsk negativ), kan du gøre noget ved hjælp [af Threat Explorer](threat-explorer.md).|
|**Der blev fundet trusler**|Den automatiske undersøgelse fandt problemer, men der er ingen specifikke afhjælpningshandlinger til løsning af disse problemer. <p> **Statussen Trusler fundet** kan opstå, når en eller anden type brugeraktivitet blev identificeret, men der ikke er nogen oprydningshandlinger tilgængelige. Eksemplerne omfatter en af følgende brugeraktiviteter: <ul><li>En [hændelse til forebyggelse af datatab](../../compliance/dlp-learn-about-dlp.md)</li><li>En mail, der sender anomali</li><li>Sendt malware</li><li>Sendt phish</li></ul> <p> Undersøgelsen fandt ingen skadelige URL-adresser, filer eller mails at afhjælpe, og ingen postkasseaktivitet at løse, f.eks. deaktivering af regler for videresendelse eller uddelegering. <p> **Tip**: Hvis du har mistanke om, at noget er gået glip af (f.eks. en falsk negativ), kan du undersøge og gøre noget ved hjælp [af Threat Explorer](threat-explorer.md)|
|**Afsluttet efter system**|Undersøgelsen blev afbrudt. En undersøgelse kan stoppe af flere årsager: <ul><li>Undersøgelsens ventende handlinger er udløbet. Ventende handlinger får time out, efter du afventer godkendelse i en uge</li><li>Der er for mange handlinger. Hvis der f.eks. er for mange brugere, der klikker på skadelige URL-adresser, kan det overstige undersøgelsens mulighed for at køre alle analyseanalyserne, så undersøgelsen standses</li></ul> <p> **Tip**: Hvis en undersøgelse standses, før der blev foretaget handlinger, kan du prøve [at bruge Threat Explorer](threat-explorer.md) til at finde og håndtere trusler.|
|**Afventende handling**|Undersøgelsen har fundet en trussel, f.eks. en ondsindet mail, en ondsindet URL-adresse eller en risikabel postkasseindstilling, og en handling til at løse denne trussel [afventer godkendelse](air-review-approve-pending-completed-actions.md). <p> Tilstanden **Afventende** handling udløses, når der bliver fundet en trussel med en tilsvarende handling. Listen over afventende handlinger kan dog blive større, efterhånden som en undersøgelse kører. Få vist oplysninger om undersøgelsen for at se, om andre elementer stadig afventer fuldførelse.|
|**Afhjælpet**|Undersøgelsen blev afsluttet, og alle afhjælpningshandlinger blev godkendt (angivet som fuldt løst). <p> **BEMÆRK**: Godkendte afhjælpningshandlinger kan have fejl, der forhindrer, at handlingerne bliver foretaget. Uanset om afhjælpningshandlingerne er blevet gennemført, ændres undersøgelsesstatussen ikke. Få vist undersøgelsesoplysninger.|
|**Delvist afhjælpet**|Undersøgelsen har resulteret i afhjælpningshandlinger, og nogle er blevet godkendt og fuldført. Andre handlinger afventer [stadig](air-review-approve-pending-completed-actions.md).|
|**Mislykkedes**|Mindst én undersøgelsesanalyse stødte på et problem, hvor den ikke kunne fuldføres korrekt. <p> **BEMÆRK!** Hvis en undersøgelse mislykkes, efter afhjælpningshandlingerne er blevet godkendt, kan afhjælpningshandlingerne muligvis stadig være fuldført. Se undersøgelsesdetaljerne.|
|**I kø ved begrænsning**|En undersøgelse opbevares i en kø. Når andre undersøgelser er afsluttet, starter undersøgelser i kø. Begrænsning hjælper med at undgå dårlig tjenesteydeevne.  <p> **Tip**: Ventende handlinger kan begrænse, hvor mange nye undersøgelser, der kan køre. Sørg for at [godkende (eller afvise) afventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).|
|**Afsluttet ved begrænsning**|Hvis en undersøgelse opbevares i køen for længe, stopper den. <p> **Tip**: Du kan [starte en undersøgelse fra Threat Explorer](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).|

## <a name="view-details-of-an-investigation"></a>Få vist oplysninger om en undersøgelse

1. Gå til Microsoft 365 Defender -portalen (<https://security.microsoft.com>), og log på.
2. Vælg Handlingscenter i **navigationsruden**.
3. Vælg en handling **på fanerne** **Afventer** eller Historik. Pop op-ruden åbnes.
4. I pop op-ruden skal du **vælge Siden Åbn undersøgelse**. 
5. Brug de forskellige faner til at få mere at vide om undersøgelsen.

## <a name="view-details-about-an-alert-related-to-an-investigation"></a>Få vist oplysninger om en besked i forbindelse med en undersøgelse

Visse typer beskeder udløser automatiseret undersøgelse i Microsoft 365. Du kan få mere at vide under [Beskedpolitikker, der udløser automatiserede undersøgelser](office-365-air.md#which-alert-policies-trigger-automated-investigations).

1. Gå til Microsoft 365 Defender -portalen (<https://security.microsoft.com>), og log på.
2. Vælg Handlingscenter i **navigationsruden**.
3. Vælg en handling **på fanerne** **Afventer** eller Historik. Pop op-ruden åbnes.
4. I pop op-ruden skal du **vælge Siden Åbn undersøgelse**.
5. Vælg fanen **Vigtige beskeder** for at få vist en liste over alle de vigtige beskeder, der er knyttet til undersøgelsen.
6. Vælg et element på listen for at åbne pop op-ruden. Her kan du få vist flere oplysninger om beskeden.

## <a name="keep-the-following-points-in-mind"></a>Husk følgende punkter

- Mailantal beregnes på tidspunktet for undersøgelsen, og nogle optællinger genberegnes, når du åbner pop op-vinduer til undersøgelse (baseret på en underliggende forespørgsel).

- De optællinger af mails, der vises for mailklyngerne på fanen Mail og værdien for antal mails, der vises i pop op-gruppen, beregnes på tidspunktet for undersøgelsen og ændres ikke.

- Det antal mails, der vises nederst på fanen  Mail i pop op-vinduet med mailklyngen og antallet af mails, der vises i Stifinder, afspejler de mails, der er modtaget efter undersøgelsens indledende analyse.

  En mailklynge, der viser en oprindelig mængde af 10 mails, viser således en mailliste på i alt 15, når der modtages yderligere fem mails mellem undersøgelsesfasen, og hvornår administratoren gennemser undersøgelsen. På samme måde kan gamle undersøgelser begynde at vise højere antal, end Stifinder-forespørgsler viser, fordi data i Microsoft Defender til Office 365 Plan 2 udløber efter syv dage for prøveabonnementer og efter 30 dage for betalte licenser.

  Visning af både antal historiske og aktuelle optællinger i forskellige visninger udføres for at angive mailpåvirkningen på undersøgelses tidspunkt og de aktuelle konsekvenser frem til afhjælpningskørslen.

- I forbindelse med mail kan du som en del af undersøgelsen opleve en større trussel mod mængden. En volumenanomali angiver en samling af lignende mails omkring undersøgelsestiden i forhold til tidligere tidsrammer. En samling af mailtrafik sammen med visse karakteristika (f.eks. emne- og afsenderdomæne, brødtekst og afsender-IP) er typisk for starten af mailkampagner eller -angreb. Men massekampagner, spamkampagner og legitime mailkampagner deler ofte disse karakteristika.

- Volumenanomomier repræsenterer en potentiel trussel og kan derfor være mindre alvorlige sammenlignet med malware eller phish-trusler, der er identificeret ved hjælp af antivirusprogrammer, detonation eller skadeligt ry.

- Du behøver ikke at godkende alle handlinger. Hvis du ikke er enig med den anbefalede handling, eller din organisation ikke vælger bestemte typer handlinger, kan du vælge Afvis handlingerne eller blot ignorere dem og ikke gøre noget.

- Godkendelse og/eller afvisning af alle handlinger giver undersøgelsen mulighed for at lukke helt (status bliver løst), mens nogle handlinger vil være ufuldstændige, hvilket medfører, at undersøgelsens status ændres til en delvist afhjælpet tilstand.

## <a name="next-steps"></a>Næste trin

- [Gennemse og godkende afventende handlinger](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)
