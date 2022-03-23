---
title: Microsoft 365 netværksvurdering
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
description: Microsoft 365 netværksvurdering
ms.openlocfilehash: 5ff858ef652c7fc536310c9d27887863d156fb5d
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63591018"
---
# <a name="microsoft-365-network-assessment"></a>Microsoft 365 netværksvurdering

I Microsoft 365 Administration Center for netværksforbindelse samler netværksvurderinger et aggregat af mange målepunkter for netværksydeevnen i et **øjebliksbillede** af virksomhedens netværksperimeterstilstand. En netværksvurdering fortæller dig, hvor meget det kunde ansvarlige netværksdesign påvirker Office 365 brugeroplevelsen. Netværksvurderinger er relevante for både hele lejeren og hver geografisk placering, hvorfra brugerne opretter forbindelse til din lejer. Bedømmelsesvurderingerne giver Microsoft 365-administratorer en nem måde til øjeblikkeligt at få en fornemmelse af virksomhedens netværkstilstand og hurtigt analysere ned i en detaljeret rapport for enhver global kontorplacering.

Værdien for netværksvurderingspunkter er fra 0 til 100 og er et gennemsnit af TCP-ventetid, downloadhastighed og UDP-forbindelseskvalitetsmål. Disse målepunkter kompileres én gang om dagen. Målepunkter for ydeevnen for Microsoft-ejede netværk medtages ikke i disse målinger for at sikre, at vurderingsresultaterne er entydige og specifikke for virksomhedens netværk.

> [!div class="mx-imgBorder"]
> ![Værdi for netværksvurdering.](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

En meget lav værdi for netværksvurdering antyder, Microsoft 365 klienter har betydelige problemer med at oprette forbindelse til lejeren eller opretholde en effektiv brugeroplevelse. En høj værdi angiver et korrekt konfigureret netværk med få løbende problemer med ydeevnen. En værdi på 80 % repræsenterer en sund grundlinje, over hvilken du ikke bør forvente at modtage almindelige brugerklager om Microsoft 365-forbindelse eller reaktionighed på grund af netværkets ydeevne. Efterhånden som der foretages forbedringer af den iterative netværksforbindelse, øges denne værdi sammen med brugeroplevelsen.

| Netværksvurdering | Forventet brugeroplevelse |
| :----------------- | :----------------------- |
| 100                | Bedst                     |
| 80                 | Kommer med anbefalinger    |
| 60                 | Acceptabel               |
| 40                 | Brugere kan opleve problemer |
| 20                 | Brugere kan brokke sig       |
| 0                  | Netværksproblemer, som er et fælles diskussionsemne |

## <a name="network-assessment-panel"></a>Panel til netværksvurdering

Hver netværksvurdering, uanset om det er område for lejeren eller en bestemt kontorplacering, viser et panel med oplysninger om vurderingen. Dette panel viser et liggende søjlediagram over vurderingen både som en procentdel og som de samlede punkter for hver komponents arbejdsbyrde, herunder kun arbejdsbelastninger, hvor måledata blev modtaget. Ved en vurdering af et kontorplaceringsnetværk viser vi også en sammenligning med procentdelen af Microsoft 365-kunder i hver af de fem kunder, der har rapporteret data i den samme by som din kontorplacering.

> [!div class="mx-imgBorder"]
> ![Eksempel på værdi for netværksvurdering.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

**Opdelingen af** Bedømmelse i panelet viser vurderingen for hver af komponentens arbejdsbelastninger.

**Vurderingshistorikken** viser de seneste 30 dage af vurderingen og benchmarken. Du kan også rapportere om metrikoversigten for en hvilken som helst kontorplacering i op til to år ved hjælp af fanen Historik. Under fanen Historik kan du vælge de attributter, du vil rapportere på. Ved at vælge en tidsramme for rapporten kan du fremhæve virkningen af et projekt med netværksopdatering og se forbedringen af din netværksvurdering.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Bedømmelser af lejernetværk og netværksvurderinger for kontorplacering

En netværksvurdering måler designet af netværksperimeteren for en kontorplacering til Microsofts netværk. Forbedringer af netværksperimeteren udføres bedst på hver enkelt kontorplacering.

Vi viser en værdi for netværksvurdering for hele Microsoft 365 på siden med oversigt over netværksydeevne. Denne værdi er et vægtet gennemsnit af netværksvurderinger for alle kontorplaceringer. Der er også en bestemt netværksvurderingsværdi for hver registreret kontorplacering på oversigtssiden for den pågældende placering.

## <a name="exchange-online"></a>Exchange Online

For Exchange Online målees TCP-ventetiden fra klientcomputeren til Exchange-frontporten. Denne ventetid kan påvirkes af den afstand, netværket bevæger sig over kundernes LAN og WAN. Det kan også påvirkes af netværk mellemledsenheder eller -tjenester, hvilket forsinker forbindelsen eller medfører, at pakkerne bliver sendt igen. Og det er påvirket af, hvor langt væk den nærmeste Exchange og frontporten er. Medianen (også kaldet den 50. fraktil eller P50-målingen) anvendes til alle målinger i løbet af de foregående tre dage.

Den Exchange Online vurdering foretages ved hjælp af følgende tabel. Et hvilket som helst TCP-latenstidsnummer mellem tærskelværdierne tildeles punkter lineært inden for båndet.

| TCP-ventetid   | Point |
| :------------ | :----- |
| 10 ms eller mindre  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms eller mere | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

For SharePoint Online måles den downloadhastighed, der er tilgængelig for en bruger til at få adgang SharePoint et dokument OneDrive dokumentet. Dette kan påvirkes af den tilgængelige båndbredde på netværkskredsløb mellem klientcomputeren og Microsofts netværk. Den påvirkes ofte af overbelastning af netværket, der findes i flaskehalse i komplekse netværksenheder eller i dårlig dækning Wi-Fi områder. Downloadhastigheden måles i megabyte pr. sekund, hvilket er ca. en tiendedel af et kredsløb klassificeret megabit pr. sekund. MegaByte pr. sekund-enheden er nyttig, fordi du direkte kan se, hvilken filstørrelse der kan downloades i løbet af 1 sekund. Den 25. fraktil (også kaldet P25-målingen) anvendes for alle målinger i løbet af de foregående tre dage. Denne 25. fraktil hjælper med at reducere effekten af varierende overbelastning over tid.

Den SharePoint Online-vurdering foretages ved hjælp af følgende tabel. Et hvilket som helst tal for downloadhastighed mellem tærskelværdier tildeles punkter lineært inden for båndet.

| Downloadhastighed | Point |
| :------------- | :----- |
| 20MBps eller mere | 100    |
| 14MBps         | 80     |
| 8MBps          | 60     |
| 4MBps          | 40     |
| 2MBps          | 20     |
| 0MBps          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

For Microsoft Teams måles netværkskvaliteten som UDP-ventetid, UDP-jitter og UDP-pakketab. UDP bruges til lyd- og videomedieforbindelse til opkald og møder for at Microsoft Teams. Dette kan påvirkes af de samme faktorer som for ventetid og downloadhastighed ud over forbindelsesproblemer i et netværks UDP-understøttelse, da UDP konfigureres separat til den mere almindelige TCP-protokol. Medianen (også kaldet den 50. fraktil eller P50-målingen) anvendes til alle målinger i løbet af de foregående tre dage. 

Vi beregner et gennemsnitlig vurderingsresultat ud fra disse UDP-mål for en skala fra én til fem. Derefter tilknytter vi det til skalaen på 0-100 punkter for Microsoft Teams for netværksvurderingen.  Generelt set er god over 87,5 point, og overordnet set er dårlig under 50 point.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md)

[Microsoft 365 indsigt i netværksydeevne](office-365-network-mac-perf-insights.md)

[Microsoft 365 testværktøj til netværksforbindelse](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 til placeringstjenester for netværksforbindelse](office-365-network-mac-location-services.md)
