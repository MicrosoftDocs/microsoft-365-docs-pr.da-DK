---
title: Microsoft 365 til Insights
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 til Insights
ms.openlocfilehash: 429b066a7132cb29f2a35d43857534695391d33c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591581"
---
# <a name="microsoft-365-network-insights"></a>Microsoft 365 til Insights

**Netværksindsigt** er målepunkter for ydeevnen, der indsamles fra din Microsoft 365 lejer, og som kun kan vises af administrative brugere i din lejer. Insights vises i Microsoft 365 Administration på <https://portal.microsoft.com/adminportal/home#/networkperformance>.

Insights har til formål at hjælpe med at designe netværksperimetere for dine kontorplaceringer. Hvert indsigt giver liveoplysninger om egenskaberne for ydeevnen for et bestemt almindeligt problem for hver geografisk placering, hvor brugerne tilgår din lejer.

Der er seks specifikke netværksindsigt, der kan vises for hver kontorplacering:

- [Backhauled network udgangspunktress](#backhauled-network-egress)
- [Netværk mellemliggende enhed](#network-intermediary-device)
- [Bedre ydeevne registreret for kunder i nærheden af dig](#better-performance-detected-for-customers-near-you)
- [Brug af en ikke-optimal Exchange Online en serviceforsideport](#use-of-a-non-optimal-exchange-online-service-front-door)
- [Brug af en ikke-optimal SharePoint en online service front dør](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Lav downloadhastighed SharePoint en forsideport](#low-download-speed-from-sharepoint-front-door)
- [Brugerens optimale netværks udgangspunkt i Kina](#china-user-optimal-network-egress)

Der er to netværksindsigt på lejerniveau, der kan vises for lejeren:

- [Exchange forbindelser, der er påvirket af forbindelsesproblemer](#exchange-sampled-connections-affected-by-connectivity-issues)
- [SharePoint forbindelser, der er påvirket af forbindelsesproblemer](#sharepoint-sampled-connections-affected-by-connectivity-issues)

Disse indsigter vises også på produktivitetsscoresiderne.

>[!IMPORTANT]
>Netværksindsigt, anbefalinger om ydeevne og evalueringer i Microsoft 365 Administration-center er i øjeblikket en forhåndsvisningsstatus og er kun tilgængelig for Microsoft 365-lejere, der er tilmeldt preview-programmet til funktioner.

## <a name="backhauled-network-egress"></a>Backhauled network udgangspunktress

Dette indsigt vises, hvis tjenesten Netværksindsigt registrerer, at afstanden fra en given brugerplacering til netværkets udgangspunkt er større end 500 kilometer (800 kilometer). Dette kan betyde, Microsoft 365 trafik tilbagehases til en fælles enhed eller proxy i Internet edge.

Dette indsigt er forkortet som "Egress" i nogle oversigtsvisninger.

> [!div class="mx-imgBorder"]
> ![Backhauled network udgangspunktress.](../media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>Hvad betyder det?

Dette identificerer, at afstanden mellem kontorplaceringen og netværkets udgangspunkt er mere end 500 kilometer (800 kilometer). Kontorplaceringen identificeres af en obskøn placering på klientcomputeren, og netværks udgangspunktet identificeres ved hjælp af omvendt IP-adresse til placering af databaser. Placeringen af kontoret kan være unøjagtig, hvis Windows placeringstjenester er deaktiveret på maskiner. Placeringen af netværks udgangspunktet kan være unøjagtig, hvis de omvendte oplysninger i IP-adressedatabasen er unøjagtige.

Detaljer for denne indsigt omfatter:

- Office placering
- Anslået procentdel af lejerbruger i alt på placeringen
- Aktuel udgangsplacering for netværket
- Relevansen af udgangspunktet
- Afstand mellem placeringen og det aktuelle udgangspunkt
- Den dato, hvor betingelsen først blev registreret
- Den dato, hvor betingelsen blev løst

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Vi anbefaler et netværks udgangspunkt så tæt på kontorplaceringen som muligt.  Microsoft 365 trafik skal dirigere optimalt til Microsofts globale netværk og til den nærmeste Microsoft 365 service front door. Hvis du har et tæt netværks udgangspunkt for brugeres kontorplaceringer, kan det også øge ydeevnen, efterhånden som Microsoft udvider både netværkspunkterne for tilstedeværelse og Microsoft 365 for døre i fremtiden.

Du kan finde flere oplysninger om, hvordan du løser [dette problem, Egress netværksforbindelser lokalt](microsoft-365-network-connectivity-principles.md#egress-network-connections-locally) [Microsoft 365 Network Connectivity Principles](microsoft-365-network-connectivity-principles.md).

## <a name="network-intermediary-device"></a>Netværk mellemliggende enhed

Dette indsigt vises, hvis vi har registreret enheder mellem dine brugere og Microsofts netværk. Vi anbefaler, at latenstidsfølsomme Microsoft 365 netværkstrafik tilsidesætter sådanne enheder. Denne anbefaling er yderligere beskrevet i Microsoft 365 [Network Connectivity Principles](microsoft-365-network-connectivity-principles.md).

Et netværks mellemled, som vi viser, er SSL-pause og -inspektion, når kritiske Microsoft 365-netværksslutpunkter for Exchange, SharePoint og Teams opsnappes og dekrypteres af mellemliggende netværksenheder.

### <a name="what-does-this-mean"></a>Hvad betyder det?

Netværksenheder som f.eks. proxyservere, VPN og enheder til forebyggelse af datatab kan påvirke ydeevnen og stabiliteten af Microsoft 365 klienter, hvor trafik er mellemliggende.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Konfigurer den netværk mellemliggende enhed, der blev registreret, for at tilsidesætte behandlingen Microsoft 365 netværkstrafik.

## <a name="better-performance-detected-for-customers-near-you"></a>Bedre ydeevne registreret for kunder i nærheden af dig

Dette indsigt vises, hvis tjenesten Netværksindsigt registrerer, at et betydeligt antal kunder i dit metroområde har bedre ydeevne end brugerne på denne kontorplacering.

Dette indsigt er forkortet som "Peers" i nogle oversigtsvisninger.

> [!div class="mx-imgBorder"]
> ![Relativ netværksydeevne.](../media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>Hvad betyder det?

Dette indsigt undersøger den aggregerede ydeevne for Microsoft 365 kunder i samme by som denne kontorplacering. Dette indsigt vises, hvis den gennemsnitlige ventetid for dine brugere er 10 % større end den gennemsnitlige ventetid for tilstødende lejere.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Der kan være mange grunde til denne betingelse, herunder ventetid i virksomhedens netværk eller internetudbyder, flaskehalse eller arkitekturdesignproblemer. Undersøg ventetiden mellem hvert hop på rute mellem dit kontornetværk og den aktuelle Microsoft 365 forsideport. Du kan finde flere oplysninger [Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md).

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Brug af en ikke-optimal Exchange Online en serviceforsideport

Dette indsigt vises, hvis tjenesten Netværksindsigt registrerer, at brugere på en bestemt placering ikke opretter forbindelse til en optimal Exchange Online service front dør.

Dette indsigt er forkortet som "Routing" i nogle oversigtsvisninger.

> [!div class="mx-imgBorder"]
> ![Ikke-optimal EXO-forsideport.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>Hvad betyder det?

Vi har Exchange Online døre, der er egnet til brug fra kontorets placeringsby. Hvis den aktuelle test viser brug af en Exchange Online service front door, der ikke er på denne liste, anbefaler vi denne anbefaling.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Brug af en ikke-optimal Exchange Online serviceforsideport kan skyldes backhaul for netværket, i hvilket tilfælde vi anbefaler et lokalt og direkte netværksud udgangspunkt. Hvis du har implementeret en ekstern DNS Recursive Resolver-server, anbefaler vi, at du justerer serverkonfigurationen med netværkets udgangspunkt.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>Brug af en ikke-optimal SharePoint en online service front dør

Dette indsigt vises, hvis tjenesten Netværksindsigt registrerer, at brugere på en bestemt placering ikke opretter forbindelse til den nærmeste SharePoint Online-service frontport.

Dette indsigt er forkortet som "Afd" i nogle oversigtsvisninger.

> [!div class="mx-imgBorder"]
> ![Ikke-optimal SPO-forsideport.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>Hvad betyder det?

Vi har identificeret SharePoint, som testklienten opretter forbindelse til. Så for den kontorplaceringsby, vi sammenligner med den forventede SharePoint online service front door for den pågældende by. Hvis den ikke stemmer overens, anbefaler vi denne.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Brug af en ikke-optimal SharePoint Online-tjenesteforsideport kan skyldes backhaul for netværket før virksomhedens udgangspunkt. Hvis det er tilfældet, anbefaler vi et lokalt og direkte netværksud udgangspunkt. Det kan også skyldes brug af en ekstern DNS Recursive Resolver-server, hvor vi anbefaler, at DNS Recursive Resolver-serveren justeres med netværkets udgangspunkt.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Lav downloadhastighed SharePoint en forsideport

Dette indsigt vises, hvis tjenesten Netværksindsigt registrerer, at båndbredden mellem den specifikke kontorplacering og SharePoint Online er mindre end 1 MBps.

Dette indsigt er forkortet som "Overførselshastighed" i nogle oversigtsvisninger.

### <a name="what-does-this-mean"></a>Hvad betyder det?

Den downloadhastighed, en bruger kan få fra SharePoint Online og OneDrive for Business forside døre måles i megabyte pr. sekund (MBps). Hvis denne værdi er mindre end 1 MBps, giver vi dig dette indsigt.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Hvis du vil forbedre downloadhastighederne, skal båndbredden muligvis øges. Alternativt kan der være overbelastning af netværket mellem computere på kontorplaceringen og SharePoint-tjenestens frontport. Denne betingelse begrænser den downloadhastighed, der er tilgængelig for brugere, selvom tilstrækkelig båndbredde er tilgængelig.

## <a name="china-user-optimal-network-egress"></a>Brugerens optimale netværks udgangspunkt i Kina

Dette indsigt vises, hvis din organisation har brugere i Kina, der opretter forbindelse til din Microsoft 365 lejer på andre geografiske placeringer.

### <a name="what-does-this-mean"></a>Hvad betyder det?

Hvis din organisation har en privat WAN-forbindelse, anbefaler vi, at du konfigurerer et netværks-WAN-kredsløb fra dine kontorplaceringer i Kina, der har netværks udgangspunkt til internettet på en af følgende placeringer:

- Hongkong
- Japan
- Taiwan
- Sydkorea
- Singapore
- Malaysia

Internet udfald længere væk fra brugere end disse placeringer vil reducere ydeevnen, og udgangspunktet i Kina kan forårsage problemer med høj latenstid og forbindelse på grund af overbelastning på tværs af grænser.

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Du kan finde flere oplysninger om, hvordan du kan afhjælpe problemer med ydeevnen i forbindelse med denne indsigt, Microsoft 365 global optimering af lejerens [ydeevne for Kina-brugere](microsoft-365-networking-china.md).

## <a name="exchange-sampled-connections-affected-by-connectivity-issues"></a>Exchange forbindelser, der er påvirket af forbindelsesproblemer

Dette indsigt viser, når 50 % eller flere af forbindelserne i stikprøven påvirkes. Virkningen defineres af, at Exchange er under 60 % for hver stikprøve.

### <a name="what-does-this-mean"></a>Hvad betyder det?

Dette angiver, at de fleste af dine brugere sandsynligvis oplever problemer med at Outlook til Exchange Online. Procentdelen af eksempler repræsenterer procentdelen af brugere, der viser under 60 point.  

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Aktivér synlighed af netværksforbindelsen for kontorplacering, hvis du ikke allerede har gjort det. Find ud af, hvilke kontorer der påvirkes af dårlig netværksforbindelse, og find måder at forbedre netværksperimeteren på hver, der forbinder brugerne til Microsofts netværk.

## <a name="sharepoint-sampled-connections-affected-by-connectivity-issues"></a>SharePoint forbindelser, der er påvirket af forbindelsesproblemer

Dette indsigt viser, når 50 % eller flere af forbindelserne i stikprøven påvirkes. Virkningen defineres af, at SharePoint er under 40 % for hver stikprøve.

### <a name="what-does-this-mean"></a>Hvad betyder det?

Dette angiver, at de fleste af dine brugere sandsynligvis oplever problemer med SharePoint og OneDrive. Procentdelen af eksempler repræsenterer procentdelen af brugere, der viser under 40 point.  

### <a name="what-should-i-do"></a>Hvad skal jeg gøre?

Aktivér synlighed af netværksforbindelsen for kontorplacering, hvis du ikke allerede har gjort det. Find ud af, hvilke kontorer der påvirkes af dårlig netværksforbindelse, og find måder at forbedre netværksperimeteren på hver, der forbinder brugerne til Microsofts netværk.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 testværktøj til netværksforbindelse](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 til placeringstjenester for netværksforbindelse](office-365-network-mac-location-services.md)
