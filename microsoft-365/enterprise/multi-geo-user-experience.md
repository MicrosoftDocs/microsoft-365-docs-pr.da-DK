---
title: Brugeroplevelse i et multi-geo-miljø
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Lær om SharePoint, OneDrive og Exchange i et multi-geo-miljø for Microsoft 365.
ms.openlocfilehash: 638aa7d65f9243bfd110eebac6473d641e1d0b61
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591568"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Brugeroplevelse i et multi-geo-miljø

Her er, hvad dine brugere ser i en OneDrive Multi-Geo konfiguration:

## <a name="exchange-mailbox"></a>Exchange postkasse

En brugers postkasse Exchange klargøres til deres foretrukne dataplacering og flyttes automatisk, hvis deres PDL ændres. Brugerne kan bruge Outlook og Outlook på internettet normalt uden nogen ændring i brugeroplevelsen i et multi-geo-miljø.

## <a name="hub-sites"></a>Hubwebsteder

SharePoint Hub-websteder forbedrer opdagelsen og engagementet i indhold for medarbejderne, mens du opretter en komplet og ensartet repræsentation af projekter, afdelinger eller områder. I et multi-geo-miljø kan websteder fra satellitplaceringer nemt knyttes til et hubwebsted uanset hubwebstedets geografiske placering. Brugere kan søge og få resultater på tværs af hubben gennem en enkelt søgeoplevelse, uanset webstederens geografiske placering.

## <a name="microsoft-365-app-launcher"></a>Microsoft 365 appstarteren

Appstarteren er multi-geo-orienteret og dirigerer hvert felt til den relevante geoplacering af arbejdsmængden. Felterne SharePoint og OneDrive peger brugeren mod den placering, der svarer til brugerens klargjorte geoplacering. Det betyder, at brugeren har en OneDrive på den centrale placering, vil deres SharePoint-felt pege dem på SP Home på den centrale placering, men deres gruppewebsted klargøres på den placering, der svarer til deres PDL. 

## <a name="office-applications"></a>Office programmer

Office programmer som Word, Excel og PowerPoint automatisk registrerer den korrekte OneDrive-geoplacering for hver bruger, når de logger på. Brugere behøver ikke at angive den geospecifikke URL-adresse til deres OneDrive eller SharePoint websteder.

## <a name="onedrive-sync-app"></a>OneDrive-synkronisering app

Appen OneDrive-synkronisering (version 17.3.6943.0625 og nyere) registrerer automatisk den korrekte OneDrive geografiske placering for brugeren. Understøttelse af synkroniseringsappen omfatter muligheden for at synkronisere gruppebaserede websteder, uanset deres geografiske placering. Synkroniseringsklienten Groove ikke for multi-geo. 

## <a name="onedrive-location"></a>OneDrive placering

Brugerne får deres OneDrive deres foretrukne dataplacering. Hvis en bruger navigerer til en URL-adresse til OneDrive, der indeholder en forkert geoplacering (f.eks. et bogmærke fra en tidligere geoplacering), omdirigeres de automatisk til OneDrive på den relevante geoplacering.

## <a name="onedrive-ios-and-android"></a>OneDrive iOS og Android 

I OneDrive iOS- og Android-mobilapps kan du se dine OneDrive filer og filer, der deles med dig, uanset deres geografiske placering. Søgning fra OneDrive-mobilapps viser relevante resultater fra alle geoplaceringer. Download den nyeste version af disse apps.

Få mere at vide under Brug [OneDrive på iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) og [Brug OneDrive til Android for at](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) få flere oplysninger.

## <a name="onedrive-mobile-client"></a>OneDrive-mobilklient 

Mobilklienten OneDrive multi-geo-bevidste og vil vise relevant indhold og resultater fra alle geoplaceringer.

## <a name="search"></a>Søg

Hver geoplacering har sit eget søgeindeks og søgecenter. Når en bruger søger, sendes forespørgslen til alle geoplaceringerne, og de returnerede resultater flettes og rangeres derefter, så brugeren får samlede resultater. Brugere får resultater fra alle geoplaceringer uanset deres egen geoplacering. Se [Konfigurer søgning efter OneDrive Multi-Geo](configure-search-for-multi-geo.md) oplysninger.

Følgende søgeklienter understøttes:

-   OneDrive

-   Delve

-   SharePoint startside

-   Søgecenter

-   Brugerdefinerede søgeprogrammer, der bruger SharePoint Search API

## <a name="sharepoint-home"></a>SharePoint startside 

I SharePoint Multi-Geo er din SharePoint vært på den placering, hvor brugeren er placeret, som bestemmes af brugerens OneDrive placering. Hvis brugeren f.eks. har sin OneDrive en satellitplacering i Europa, gengives deres SharePoint Home fra Europa. SharePoint omfatter alt indhold, der er relevant for brugeren, uanset brugerens geoplacering. 

**Fulgte websteder, Nyheder fra websteder, Seneste websteder, Hyppige websteder og Foreslåede websteder**

Alle disse komponenter vises for brugeren uanset den geoplacering, hvor indholdet er hostet, så længe brugeren har tilladelse til det pågældende indhold. 

**Funktionslinks**

Administratorer kan konfigurere Udvalgte links i SharePoint efter behov for hver geoplacering. Dette gør det muligt for administratoren at funktionen i SP Home for hvert område de links, der er relevante for brugere i området. 

## <a name="sharepoint-mobile-client"></a>SharePoint-mobilklient

Mobilklienten SharePoint multi-geo-bevidste og vil vise relevant indhold og resultater fra alle geoplaceringer.

## <a name="sharing"></a>Deling

I People Picker-oplevelsen vises alle brugere, uanset deres geografiske placering. Dette gør det muligt for en bruger at dele med en anden bruger i deres samme geo eller på andre af din lejers geoplaceringer. Indhold fra forskellige geoplaceringer vises i visningen Delt med  mig i brugerens OneDrive-, Word-, Excel-, PowerPoint- og Office.com-visning og kan benyttes med Single Sign-On-oplevelse, uanset hvilken geoplacering den er hostet i.

## <a name="teams-experience"></a>Teams oplevelse

Teams er en multi-geo-tjeneste. OneDrive filer og senest viste filer vises uanset brugerens geoplacering. @-omtaler fungerer sammen med brugere fra alle geografiske placeringer.

## <a name="user-profiles"></a>Brugerprofiler

Brugerprofiloplysningerne masteres i brugerens geografiske placering. Når du vælger en bruger, bliver du ført til den relevante geoplacering for brugeren, hvor du kan se deres fulde profiloplysninger.

Hvis Delve er slået fra, kan du se den klassiske profiloplevelse i SharePoint, som ikke er multi-geo-opmærksom.


