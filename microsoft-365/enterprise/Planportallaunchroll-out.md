---
title: Planlægning af udrulningsplanen for portalen i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel beskrives det, hvordan du kan planlægge din portalstart i SharePoint Online, og hvilke trin du skal udføre for at få en vellykket start
ms.openlocfilehash: 088416537317a6728e1c5533767badf309de7634
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097464"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planlægning af udrulningsplanen for portalen i SharePoint Online

En portal er et SharePoint websted på intranettet, hvor mange brugere af webstedet bruger indhold på webstedet. Store organisationer kan have flere portaler. Det kan f.eks. være en firmaportal og en HR-portal. Portaler har typisk relativt få personer, der opretter og opretter webstedet og dets indhold. De fleste besøgende på portalen læser og bruger kun indholdet.

I denne artikel beskrives det, hvordan du planlægger udrulningen og udrulningsplanen for SharePoint Online. Den indeholder også metoder, der skal følges, da traditionel belastningstest ikke er tilladt på SharePoint Online. SharePoint Online er en cloudtjeneste, og belastningsfunktionerne, tilstanden og den overordnede balance for belastningen i tjenesten administreres af Microsoft.

For at hjælpe med at oprette en vellykket portal skal du følge de grundlæggende principper, fremgangsmåder og anbefalinger, der er beskrevet i [Oprettelse, start og vedligeholdelse af en sund portal](/sharepoint/portal-health)

Udrulningstilgangen er fremhævet nedenfor.

## <a name="portal-launch-scheduler"></a>Portalstartstyring

Brug portalstartstyringen til at frigive din portal til brugere i din organisation i planlagte faser. Få mere at vide:

![Kalenderikon.](../media/calendar.png) [Portalstartstyring](/microsoft-365/enterprise/portallaunchscheduler)

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Oversigt over kapacitetsplanlægning i SharePoint Online

For effektivt at kunne bruge kapacitet og håndtere uventet vækst på alle farme har vi automatisering, der sporer visse forbrugsscenarier. Den nøjagtige vækst er uforudsigelig for en hvilken som helst lejer i en hvilken som helst farm, men den samlede sum af anmodninger er forudsigelig over tid. Ved at identificere væksttendenserne i SharePoint Online kan vi planlægge en fremtidig udvidelse. Du kan få flere oplysninger om [kapacitetsplanlægning og belastningstest SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md).

En vigtig del af en vellykket lancering er tilgangen "bølge" eller "faseinddelt udrulning", der er beskrevet nedenfor.

## <a name="can-i-load-test-sharepoint-online"></a>Kan jeg indlæse test SharePoint Online?

SharePoint Online er et delt miljø med flere lejere, der balanceres på tværs af farme, og skalering justeres løbende. Belastningstest af et miljø, f.eks. SharePoint Online, hvis skaleringsændringer løbende ikke kun giver dig uventede resultater, men det er ikke tilladt.

Få mere at vide: [Kapacitetsplanlægning og belastningstest SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimer sider ved at følge anbefalede retningslinjer

Sider fra en lokal udrulning bør ikke blot flyttes, som de er, til SharePoint Online uden at gennemgå dem i forhold til anbefalede retningslinjer for SharePoint Online. Den bedste fremgangsmåde er altid at optimere en hvilken som helst startside for et websted eller en hvilken som helst portal i SharePoint, da det er her, de fleste brugere i organisationen får adgang som udgangspunkt for dit eller dine websteder.

Der skal tages højde for nogle få grundlæggende faktorer:

- Udrulninger i det lokale tilfælde kan bruge traditionelle cachelagre på serversiden, f.eks. objektcache, outputcache og blobcache. Med topologiforskellene i cloudmiljøet er disse indstillinger ikke nødvendigvis tilgængelige, da de store forskelle i skalering gør dem mindre levedygtige tilgange.
- Alle sider/funktioner/tilpasninger, der bruges til cloudforbrug, skal optimeres til højere ventetid og distribuerede placeringer for brugere, så brugere i forskellige områder eller områder får en mere ensartet oplevelse. Cloud tilbyder optimeringer som Content Delivery Networks (CDN) for at optimere til en distribueret brugerbase og til moderne SharePoint anvendes det sidst kendte gode (LKG) af vores OOTB-webdele (out of the box).

**Sådan gør du**:

- For alle webstedssider i SharePoint Online skal du bruge [værktøjet Sidediagnosticering](./page-diagnostics-for-spo.md), som er en Chromium udvidelse, der hjælper med at analysere og vejlede. Dette kan bruges af webstedsejere, redaktører, administratorer og udviklere, da det er designet til at være et udgangspunkt for analyse og optimering.
- Udviklere bør også bruge udviklingsværktøjer som f.eks. F12-browserudviklerværktøj og CTRL-F12 i browseren på moderne sider. [Fiddler](https://www.telerik.com/download/fiddler) kan også bruges til at gennemse sidens størrelse (hvor stor siden er i megabyte) og antallet af kald og elementer, der påvirker den samlede sidebelastning.

Dette afsnit var en kort oversigt over optimering af sider.  Du kan få mere at vide under:  [Oprettelse, start og vedligeholdelse af en sund portal](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Følg en bølge-/faseinddelt udrulningstilgang

Den traditionelle big bang-tilgang til webstedslanceringer tillader ikke bekræftelse af, at tilpasninger, eksterne kilder, tjenester eller processer er blevet testet i den rigtige skala. Denne fremgangsmåde betyder ikke, at det vil tage flere måneder at starte den, men den anbefales i mindst flere dage, afhængigt af organisationens størrelse. Når du følger en plan for udrulning af bølge, får du derfor mulighed for at sætte problemer på pause og løse dem, før du fortsætter med næste fase, og det reducerer derfor det potentielle antal brugere, der påvirkes af eventuelle problemer. SharePoint som en tjeneste skalerer din kapacitet baseret på forbrug og forudsagt forbrug, og selvom vi ikke har brug for, at du giver os besked om din lancering, skal du følge retningslinjerne for at sikre succes.

Som vist på følgende billede er antallet af brugere, der inviteres, ofte betydeligt højere end dem, der rent faktisk bruger webstedet. På dette billede vises en strategi for, hvordan du udruller en udgivelse. Denne metode hjælper med at identificere måder, hvorpå du kan forbedre SharePoint websted, før de fleste brugere ser det.

![Graph viser inviterede og aktive brugere.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)

I pilotfasen er det godt at få feedback fra brugere, som organisationen har tillid til og kender, vil være engageret. På denne måde er det muligt at måle, hvordan systemet bruges, og hvordan det fungerer.

Under hver af bølgerne skal du indsamle brugerfeedback omkring funktionerne og ydeevnen under hver bølge af udrulning. Indsamling af feedback har den fordel, at du langsomt introducerer systemet og foretager forbedringer, efterhånden som systemet bliver mere brugt. Dette giver os også mulighed for at reagere på den øgede belastning, da webstedet udrulles til flere brugere og kombineret med at følge retningslinjerne for sideoptimering sikrer en positiv oplevelse for dine brugere.

**Sådan gør du**:

- Beslut timingen af hver fase, og sørg for, at du har en uforudsete/pausemulighed, hvis du skal foretage justeringer, før du fortsætter
- Planlæg din første gruppe af brugere, som du vil aktivere, for at sikre, at du modtager den feedback, du skal bruge for at komme videre.  Hvor det er muligt, skal du vælge en aktiv gruppe af brugere, der vil give feedback rettidigt
- Når du planlægger hver bølge, kan du prøve at starte med en lille brugerbase (mindre end 5.000 brugere). Forøg gruppestørrelserne, efterhånden som du fortsætter med hver bølge. Når du opretter en forskudt tilgang, giver det nemmere pausemuligheder efter behov.
