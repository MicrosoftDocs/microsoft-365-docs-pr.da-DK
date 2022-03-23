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
description: Finde oplysninger og ressourcer, der skal opgraderes fra Lync Server 2013. Support slutter 11. april 2023.
ms.openlocfilehash: 6d6d3baed383e85a1e97d37726ff7f1eb355e98c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63593018"
---
# <a name="upgrading-from-lync-server-2013"></a>Opgradering fra Lync Server 2013

Supporten til Microsoft Lync Server 2013 slutter den **11. april 2023**. Denne artikel indeholder ressourcer, der kan hjælpe dig med at opgradere din eksisterende Lync Server-installation Microsoft Teams eller Skype for Business lokalt miljø.

## <a name="what-is-end-of-support"></a>Hvad er *ophør af support*?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Efter datoen for ophør af support holder produktet ikke op med at fungere, men Microsoft yder ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.

- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.

- Tidszoneopdateringer.

Det betyder, at der ikke kommer nogen yderligere opdateringer, rettelser eller rettelser til produktet (herunder sikkerhedsrettelser/-rettelser). Microsoft Support vil have ændret sine supportindsatser til nyere versioner.

## <a name="plan-ahead"></a>Planlæg fremad

Kontrollér de datoer, der understøtter slutdatoer, på [webstedet produktlivscyklus](/lifecycle/products/lync-server-2013). Planlæg dine opgraderinger eller migreringerne med disse datoer for øje. Husk, at produktet *ikke holder op med at fungere på* den angivne dato. Men da din installation ikke længere bliver patched efter denne dato, skal du planlægge en problemfri overgang til den næste version af produktet. Tabellen nedenfor viser en oversigt over de indstillinger, der er tilgængelige for dig.

|Ophør af supportprodukt|Understøttet|Anbefalet|
|---|---|---|
|Lync Server 2013|Opgrader til Skype for Business Server 2015 eller 2019|Opgrader til Microsoft Teams

## <a name="whats-next"></a>Hvad sker der derefter?

Vi anbefaler, at du opgraderer Microsoft Teams. Microsoft Teams udvider funktionerne i Lync Server og samler chat, møder, opkald, samarbejde, appintegration og fillagring til en enkelt grænseflade. Teams hjælper med at strømline den måde, brugerne får tingene gjort på, hvilket forbedrer brugertilfredsheden og accelererer forretningsresultater. Vi udvider kontinuerligt Teams-funktionaliteter, så du kan kommunikere og samarbejde på nye måder, nedbryde organisatoriske og geografiske hindringer og fremme effektiviteten i processen og beslutningstagningen.

Hvis du ikke kan opgradere til en Microsoft Teams, kan du opgradere til Skype for Business Server 2015 eller 2019. En vigtig overvejelse i forbindelse med planlægning er, at begge disse produkter når slutdato for support d. 14. oktober 2025. Du kan finde flere oplysninger på følgende sider med supportlivscyklus:

- [Skype for Business Server 2015-oplysninger om supportlivscyklus](/lifecycle/products/skype-for-business-server-2015)
- [Skype for Business Server oplysninger om supportlivscyklus for 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Opgrader til Microsoft Teams

Vi har detaljeret vejledning til at opgradere Microsoft Teams fra din lokale installation. Lad os først dække nogle vigtige tekniske krav. Du skal etablere hybridforbindelse, som gør det muligt at flytte dine brugere til Teams. [Planlæg hybridforbindelse](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) giver et overblik over konfigurationen af et hybridmiljø. Selvom artiklen fokuserer på Skype for Business, gælder alle begreberne også for Lync Server 2013. Se afsnittet [med krav til serverversionen](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) af Lync Server 2013.

Du skal også sikre dig, at din Lync Server 2013-installation er helt opdateret. Vi udgiver en liste over alle de seneste opdateringer til [Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) Men følgende opdatering er en forudsætning for, at du kan opgradere Microsoft Teams:

- Samlet [opdatering 5.0.8308.1149 til Lync Server 2013, hovedkomponenter i september 2021](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043): Denne opdatering erstatter Live ID-godkendelse med OAuth-godkendelsesprotokol til `Move-CSUser` cmdlet'en, som bruges til at flytte lokale brugere til Microsoft Teams.

Selvom brugeroplevelsen i Microsoft Teams langt mere omfattende og overordnet i forhold til Lync, er det også markant anderledes. Derfor skal du også forberede din organisation og dine brugere for at sikre en hurtig indføring af Microsoft Teams. Vi har et væld af oplysninger om, hvordan du forbereder din organisation, planlægger din opgradering til Teams og sikrer en vellykket implementering.

**Vi anbefaler, at du starter på [vores Teams-opgraderingsportal](/MicrosoftTeams/upgrade-skype-teams)**, hvor du kan finde tekniske oplysninger, uddannelsesressourcer, links til Ignite-sessioner, tilgængelige hjælperessourcer, casestudier og meget mere.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Skærmbillede af Teams opgraderingsportal":::

### <a name="upgrade-to-skype-for-business-server"></a>Opgrader til Skype for Business Server

Stien til Skype for Business Server vil være forskellig afhængigt af den version, du vælger at opgradere til. Skype for Business Server 2015 understøtter en direkte opgradering fra Lync Server 2013. For at opgradere til Skype for Business Server 2019 skal du derimod introducere Skype for Business Server 2019 til din Lync Server 2013-installation ved at tilføje en eller flere nye servere og derefter overføre handlinger til de nye 2019-servere, du har tilføjet.

Et vigtigt punkt at overveje er, at den aktuelle supportfase for hvert produkt: Skype for Business 2019 ydes til generel support, og Skype for Business 2015 er i øjeblikket udvidet support.  Vi anbefaler derfor at opgradere til Skype for Business Server 2019. Du kan få mere at vide om forskellen mellem generel og udvidet support under [Fast politik for livscyklus](/lifecycle/policies/fixed).

Se følgende ressourcer for at få detaljerede oplysninger om hvert opgraderingsscenarie.

- [Opgrader til Skype for Business Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Opgrader til Skype for Business Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
