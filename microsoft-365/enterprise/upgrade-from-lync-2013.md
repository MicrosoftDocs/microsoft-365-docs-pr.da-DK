---
title: Opgradering fra Lync Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Find oplysninger og ressourcer, der skal opgraderes fra Lync Server 2013. Support ophører den 11. april 2023.
ms.openlocfilehash: 925b53d751cd559ce3ccdf28d823531021611551
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129135"
---
# <a name="upgrading-from-lync-server-2013"></a>Opgradering fra Lync Server 2013

Support til Microsoft Lync Server 2013 ophører **den 11. april 2023**. Denne artikel indeholder ressourcer, der kan hjælpe dig med at opgradere din eksisterende Lync Server-installation til Microsoft Teams eller Skype for Business i det lokale miljø.

## <a name="what-is-end-of-support"></a>Hvad er *ophør af support*?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Efter slutdatoen for support holder produktet ikke op med at fungere, men Microsoft leverer ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.

- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.

- Tidszoneopdateringer.

Det betyder, at der ikke vil være flere opdateringer, programrettelser eller rettelser til produktet (herunder sikkerhedsrettelser/rettelser). Microsoft Support har helt ændret sin supportindsats til nyere versioner.

## <a name="plan-ahead"></a>Planlægge

Kontrollér de datoer, der understøttes, slutter på [webstedet Produktlivscyklus](/lifecycle/products/microsoft-lync-server-2013). Planlæg dine opgraderinger eller migreringer med disse datoer i tankerne. Husk, at dit produkt *ikke holder op med at fungere* på den angivne dato. Men da installationen ikke længere repareres efter denne dato, skal du planlægge en problemfri overgang til den næste version af produktet. I nedenstående tabel vises de indstillinger, der er tilgængelige for dig.

|Ophør af supportprodukt|Understøttes|Anbefalede|
|---|---|---|
|Lync Server 2013|Opgrader til Skype for Business Server 2015 eller 2019|Opgrader til Microsoft Teams

## <a name="whats-next"></a>Hvad sker der derefter?

Vi anbefaler, at du opgraderer til Microsoft Teams. Microsoft Teams udvider funktionerne i Lync Server, så chat, møder, opkald, samarbejde, appintegration og fillagring samles i en enkelt grænseflade. Teams hjælper med at strømline den måde, brugerne får tingene gjort på, forbedre brugertilfredsheden og fremskynde forretningsmæssige resultater. Vi udvider hele tiden Teams' funktioner, så du kan kommunikere og samarbejde på nye måder, nedbryde organisatoriske og geografiske barrierer og skabe effektivitet i processen og beslutningstagningen.

Hvis du ikke kan opgradere til Microsoft Teams, kan du opgradere til Skype for Business Server 2015 eller 2019. En vigtig planlægningsovervejelse at vide er, at begge disse produkter når ophør af support den 14. oktober 2025. Du kan få flere oplysninger på følgende sider for supportlivscyklus:

- [Skype for Business Server 2015 oplysninger om supportlivscyklus](/lifecycle/products/skype-for-business-server-2015)
- [Skype for Business Server 2019 supportlivscyklusoplysninger](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Opgrader til Microsoft Teams

Vi har en detaljeret vejledning i opgradering til Microsoft Teams fra udrulningen i det lokale miljø. Lad os først dække nogle af de vigtigste tekniske krav. Du skal etablere hybridforbindelse, hvilket gør det muligt for dig at flytte dine brugere til Teams. [Plan hybridforbindelse](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) giver et overblik over, hvordan du konfigurerer et hybridmiljø. Selvom artiklen fokuserer på Skype for Business, gælder alle begreber også for Lync Server 2013. Se afsnittet [krav til serverversion](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) for at få oplysninger om Lync Server 2013.

Du skal også sikre dig, at installationen af Lync Server 2013 er helt opdateret. Vi publicerer en [liste over alle de nyeste opdateringer til Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164), men følgende opdatering er en forudsætning for en opgradering til Microsoft Teams:

- [Kumulativ opdatering fra september 2021 5.0.8308.1149 til Lync Server 2013, Kernekomponenter](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043): Denne opdatering erstatter Live ID-godkendelsen med OAuth-godkendelsesprotokollen for `Move-CSUser` cmdlet'en, som bruges til at flytte brugere i det lokale miljø for at Microsoft Teams.

Selvom brugeroplevelsen i Microsoft Teams er langt rigere og bedre end Lync, er den også dramatisk anderledes. Derfor skal du også forberede din organisation og dine brugere for at sikre en hurtig implementering af Microsoft Teams. Vi har et væld af oplysninger om, hvordan du forbereder din organisation, planlægger din opgradering til Teams og sikrer en vellykket udrulning.

**Vi anbefaler, at du starter på vores [Teams opgraderingsportal](/MicrosoftTeams/upgrade-skype-teams)**, hvor du kan finde tekniske oplysninger, træningsressourcer, links til Ignite-sessioner, tilgængelige hjælpressourcer, casestudier og meget mere.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Skærmbillede af Teams-opgraderingsportalen":::

### <a name="upgrade-to-skype-for-business-server"></a>Opgrader til Skype for Business Server

Stien til Skype for Business Server vil være anderledes, afhængigt af den version du vælger at opgradere til. Skype for Business Server 2015 understøtter en lokal opgradering fra Lync Server 2013. På den anden side skal du for at opgradere til Skype for Business Server 2019 først introducere Skype for Business Server 2019 til din Lync Server 2013-installation ved at tilføje en eller flere nye servere og derefter overføre handlinger til de nye 2019-servere, du har tilføjet.

Et vigtigt punkt at overveje er, at den aktuelle supportfase for hvert produkt: Skype for Business 2019 er i generel support, og Skype for Business 2015 er i øjeblikket i udvidet support.  Derfor anbefaler vi, at du opgraderer til Skype for Business Server 2019. Hvis du vil vide mere om forskellen mellem generel og udvidet support, skal du se [Fast livscykluspolitik](/lifecycle/policies/fixed).

Se følgende ressourcer for at få detaljerede oplysninger om hvert opgraderingsscenarie.

- [Opgrader til Skype for Business Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Opgrader til Skype for Business Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
