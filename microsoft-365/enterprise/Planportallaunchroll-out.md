---
title: Planlægning af udrulning af portalstartplan i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: Denne artikel beskriver, hvordan du kan planlægge lanceringen af portalen i SharePoint Online, og hvilke trin du skal tage for en vellykket lancering
ms.openlocfilehash: c31a77f516aad7a58d908f47ee09dac353872283
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569490"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planlægning af udrulning af portalstartplan i SharePoint Online

En portal er et SharePoint på intranettet med mange webstedsbrugere, der forbruger indhold på webstedet. Store organisationer kan have flere portaler. Eksempelvis en firmaportal og en HR-portal. Portaler har typisk relativt få personer, der opretter og opretter webstedet og dets indhold. De fleste besøgende på portalen læser og bruger kun indholdet.

Denne artikel beskriver, hvordan du planlægger din udrulning og udrulningsplan til SharePoint Online. Den indeholder også fremgangsmåder, du kan følge, da traditionel belastningstest ikke er tilladt på SharePoint Online. SharePoint Online er en skybaseret tjeneste, og indlæsningsfunktionerne, tilstand og den overordnede balance mellem belastningen i tjenesten administreres af Microsoft.

For at hjælpe med at oprette en vellykket portal skal du følge de grundlæggende principper, fremgangsmåder og anbefalinger, der er beskrevet i Oprettelse [, lancering og vedligeholdelse af en sund portal](/sharepoint/portal-health)

Udrulnings-tilgangen er fremhævet nedenfor.

## <a name="portal-launch-scheduler"></a>Planlægning for portalstart

Brug planlæggeren til portalstart til at frigive din portal til brugere i organisationen i planlagte faser. Få mere at vide:

![Kalenderikon.](../media/calendar.png) [Planlægning for portalstart](/microsoft-365/enterprise/portallaunchscheduler)

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Oversigt over kapacitetsplanlægning i SharePoint Online

For effektivt at bruge kapacitet og håndtere uventet vækst i en hvilken som helst farm har vi automatisering, der registrerer visse brugsscenarier. Den nøjagtige vækst er uforudsigelig for hver enkelt lejer i en hvilken som helst farm, men den aggregerede sum af anmodninger er forudsigelig over tid. Ved at identificere væksttendenserne i SharePoint Online kan vi planlægge fremtidig udvidelse. Du kan finde flere [oplysninger om Kapacitetsplanlægning og belastningstest SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md).

En vigtig del af en vellykket lancering er "bølge" eller "faseopdelt udrulning"-tilgang, som er beskrevet nedenfor.

## <a name="can-i-load-test-sharepoint-online"></a>Kan jeg indlæse test SharePoint Online?

SharePoint Online er et delt miljø med flere lejere, der balanceres på tværs af farme, og skalaen tilpasses løbende. Belastningstest af et miljø som f.eks. SharePoint Online, hvis skaleringsændringer løbende ikke blot giver dig uventede resultater, men det er ikke tilladt.

Få mere at vide: [Kapacitetsplanlægning og belastningstests SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimer sider ved at følge anbefalede retningslinjer

Sider fra en lokal installation bør ikke blot flyttes, når de flyttes til SharePoint Online uden at gennemgå dem mod anbefalede retningslinjer for SharePoint Online. Den bedste fremgangsmåde er altid at optimere en hvilken som helst startside for et websted eller en portal i SharePoint, da det er her, de fleste brugere i organisationen vil få adgang til som udgangspunkt for dine websteder.

Der bør tages hensyn til nogle grundlæggende faktorer:

- Lokale installationer kan bruge traditionelle cacher på serversiden, f.eks. objektcache, outputcache og blobcache. Med forskellene i topologien i skyen er disse indstillinger ikke nødvendigvis tilgængelige, da de direkte skalaforskelle gør dem mindre realistiske metoder.
- Alle sider/funktioner/tilpasninger, der bruges til skyforbrug, skal optimeres til højere ventetid og de distribuerede placeringer af brugere, så brugere i forskellige områder eller områder får en mere ensartet oplevelse. Skyen tilbyder optimeringer som f.eks. Content Delivery Networks (CDN) til at optimere for en distribueret brugerbase, og for moderne SharePoint anvendes den senest kendte gode (LKG) af vores OOTB-webdele (out of the box).

**Hvad kan du gøre**?

- For alle webstedssider i SharePoint Online skal du bruge værktøjet [Sidediagnosticering](./page-diagnostics-for-spo.md), som er en Chromium-udvidelse, der hjælper med at analysere og give vejledning. Dette kan bruges af webstedsejere, redaktører, administratorer og udviklere, da det er designet til at være et udgangspunkt for analyse og optimering.
- Udviklere bør også bruge udviklingsværktøjer som f.eks. F12-browserudviklerværktøjet og CTRL-F12 i browseren på moderne sider. [Fiddler](https://www.telerik.com/download/fiddler) kan også bruges til at gennemgå størrelsens vægt (hvor stor siden er i megabyte) på siden og antallet af opkald og elementer, der påvirker den samlede indlæsning af siden.

Dette afsnit var en kort oversigt over optimering af sider.  Du kan få mere at vide under:  [Oprette, starte og vedligeholde en sund portal](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Følg en trinvis/faseopfaset udrulning-tilgang

Den traditionelle big bang-tilgang for webstedsstartere vil ikke tillade godkendelse af, at tilpasninger, eksterne kilder, tjenester eller processer er blevet testet på den rigtige skala. Denne fremgangsmåde betyder ikke, at det vil tage måneder at starte, men det anbefales over mindst flere dage afhængigt af organisationens størrelse. Efter en udrulningsplan for bølge giver du derfor mulighed for at afbryde og løse problemer, før du fortsætter med næste fase, og det reducerer derfor det potentielle antal brugere, der påvirkes af problemer. SharePoint som en tjeneste skalerer din kapacitet baseret på forbrug og forudsagt brug og forventet brug og har brug for, at du ikke har brug for at give os besked om lanceringen, skal du følge retningslinjerne for at sikre en vellykket gennemførelse.

Som vist på følgende billede er antallet af brugere, der inviteres, ofte væsentligt højere end det antal brugere, der faktisk bruger webstedet. Dette billede viser en strategi for, hvordan du udruller en udgivelse. Denne metode hjælper med at identificere metoder til at forbedre SharePoint, før de fleste brugere kan se det.

![Graph, der viser inviterede og aktive brugere.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)

I forsøgsfasen er det godt at få feedback fra brugere, organisationen har tillid til og ved vil være engagerede. På denne måde er det muligt at vurdere, hvordan systemet bruges, og hvordan det fungerer.

Under hver af rundene skal du indsamle brugerfeedback omkring funktionerne og ydeevnen i hver runde af installationen. Indsamling af feedback har den fordel, at du introducerer systemet langsomt og foretager forbedringer, efterhånden som systemet bruges mere. Dette giver også os mulighed for at reagere på den øgede belastning, efterhånden som webstedet rulles ud til flere brugere og kombineres med retningslinjerne for sideoptimering, hvilket sikrer en positiv oplevelse for dine brugere.

**Hvad kan du gøre**?

- Beslut dig for tidspunktet for hver fase, og sørg for, at du har en uforudset/midlertidig mulighed, hvis du er nødt til at foretage justeringer, før du fortsætter
- Planlæg din første gruppe af brugere, du vil aktivere, for at sikre, at du modtager den feedback, du skal bruge for at komme videre.  Hvis det er muligt, kan du vælge en aktiv gruppe af brugere, som giver feedback i tide
- Når du planlægger hver bølge, skal du prøve at starte med en lille brugerbase (mindre end 5000 brugere). Øg gruppestørrelserne, mens du fortsætter med hver bølge. Ved at oprette en forskudt tilgang giver den mulighed for nemmere pausemuligheder efter behov.
