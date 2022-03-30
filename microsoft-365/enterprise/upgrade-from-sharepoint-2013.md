---
title: Opgradering fra SharePoint 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: sharepoint-server-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Find oplysninger og ressourcer, der skal opgraderes SharePoint Server 2013 SharePoint Foundation 2013. Support for begge ender 11. april 2023.
ms.openlocfilehash: 05f545b67d60d6bcc45587049e49a5f5c1f6d654
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2021
ms.locfileid: "63598544"
---
# <a name="upgrading-from-sharepoint-2013"></a>Opgradering fra SharePoint 2013

Både Microsoft SharePoint Server 2013 og SharePoint Foundation 2013 slutter supporten d. **11. april 2023**. Denne artikel indeholder ressourcer, der kan hjælpe dig med at overføre dine eksisterende SharePoint Server-data til SharePoint Online i Microsoft 365 eller opgradere dit lokale SharePoint 2013-miljø. I resten af denne artikel bruger vi SharePoint 2013 til at henvise til både SharePoint Server 2013 og SharePoint Foundation 2013.

## <a name="what-is-end-of-support"></a>Hvad er *ophør af support*?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Efter datoen for ophør af support holder produktet ikke op med at fungere, men Microsoft yder ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.

- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.

- Tidszoneopdateringer.

Det betyder, at der ikke kommer nogen yderligere opdateringer, rettelser eller rettelser til produktet (herunder sikkerhedsrettelser/-rettelser). Microsoft Support vil have ændret sine supportindsatser til nyere versioner.

> [!NOTE]
> En softwarelivscyklus varer typisk fem år med generel support fra den første udgivelse og potentielt op til yderligere fem år med udvidet support. [Microsoft-løsningsudbydere](https://go.microsoft.com/fwlink/?linkid=841249) kan hjælpe dig med at opgradere til den næste version af softwaren eller overføre Microsoft 365 (eller begge). Sørg for, at du også er opmærksom på datoer for ophør af support for kritiske underliggende teknologier, især for den version af Microsoft SQL Server, du bruger sammen med SharePoint. Du kan få mere at vide under [Fast politik for livscyklus](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planlæg fremad

Kontrollér de datoer, der understøtter slutdatoer, på webstedet for produktlivscyklus for [SharePoint Server 2013](/lifecycle/products/sharepoint-server-2013) [SharePoint Foundation 2013](/lifecycle/products/sharepoint-foundation-2013). Planlæg dine opgraderinger eller migreringerne med disse datoer for øje. Husk, at produktet *ikke holder op med at fungere på* den angivne dato. Men da din installation ikke længere bliver patched efter denne dato, skal du planlægge en problemfri overgang til den næste version af produktet. Tabellen nedenfor viser en oversigt over de indstillinger, der er tilgængelige for dig.

|Ophør af supportprodukt|God|Bedre|Bedst|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|Opgrader SharePoint Server 2016 eller 2019|Opgrader til SharePoint Server Subscription Edition|Overfør til SharePoint i Microsoft 365

## <a name="whats-next"></a>Hvad sker der derefter?

Vi anbefaler overførsel til SharePoint i Microsoft 365 at drage fordel af de nyeste samarbejds-, intelligens- og sikkerhedsløsninger i Microsoft 365. De moderne oplevelsesfunktioner i Microsoft 365 designet til at være overbevisende, fleksibel og performant.

Hvis du har brug for at bevare en lokal SharePoint-installation, anbefaler vi en hybridinstallation, der gør det muligt at overføre så meget af SharePoint-funktionalitet som muligt til SharePoint i Microsoft 365. Se [SharePoint hybrid for at](/sharepoint/hybrid/hybrid) få mere at vide om og planlægge en hybrid implementering.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>Overfør til SharePoint i Microsoft 365

Du kan bruge SharePoint (SPMT) til at overføre dine websteder og indhold SharePoint i Microsoft 365. Vi har et omfattende bibliotek med indhold, der kan hjælpe dig med at planlægge fremad, udføre din overførsel og foretage fejlfinding af eventuelle problemer, du kan komme igennem. [Oversigt over SharePoint er et](/sharepointmigration/introducing-the-sharepoint-migration-tool) godt sted at starte.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>Opgrader til SharePoint Server Subscription Edition

Selvom der ikke er en direkte sti, som kan opgraderes fra SharePoint 2013 til Subscription Edition, er dette stadig den næstbedste mulighed. Den primære årsag er, at SharePoint Server Subscription Edition introducerer en fortløbende opdateringsmodel, der eliminerer behovet for at udgive nye større versioner af SharePoint Server fremover.

Hvis du vil opgradere til Subscription Edition, skal du køre SharePoint Server 2016 eller 2019. Da der heller ikke er en direkte sti fra SharePoint 2013 til 2019, er den bedste løsning at opgradere til 2016 først og derefter opgradere til Subscription Edition. Se nedenstående links for at få mere at vide om og planlægge din opgradering til Subscription Edition:

- [Opgrader til SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Opgrader til SharePoint Server Subscription Edition](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

Selvom du har brug for at bevare en lokal SharePoint-installation, anbefaler vi, at du overfører dele af dine websteder eller indhold til Microsoft 365 med [SharePoint-hybridinstallation](/sharepoint/hybrid/hybrid) for at begynde at udnytte de moderne samarbejdsoplevelser, sikkerhed og overholdelsesfunktioner i Microsoft 365.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>Opgrader SharePoint Server 2016 eller 2019

Både SharePoint Server 2016 og 2019 understøttes platforme, hvis du planlægger at vedligeholde din lokale SharePoint-installation ud over slutningen af supporten for 2013. Begge **versioner slutter dog understøttelsen d. 14. juli 2026**. Det betyder, at du skal planlægge en anden opgradering inden for 3 år efter slutdatoen for support for 2013. Her er siderne for supportlivscyklus for begge produkter:

- [SharePoint dato for supportlivscyklus for Server 2016](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 med datoer for supportlivscyklus](/lifecycle/products/sharepoint-server-2019)

Hvis du vil have mere at vide og planlægge din opgradering, skal du se følgende artikler:

- [Opgrader til SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Opgrader til SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

Selvom du har brug for at bevare en lokal SharePoint-installation, anbefaler vi, at du overfører dele af dine websteder eller indhold til Microsoft 365 med [SharePoint-hybridinstallation](/sharepoint/hybrid/hybrid) for at begynde at udnytte de moderne samarbejdsoplevelser, sikkerhed og overholdelsesfunktioner i Microsoft 365.  
