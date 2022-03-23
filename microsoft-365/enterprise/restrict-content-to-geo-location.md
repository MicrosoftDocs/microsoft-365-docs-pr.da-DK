---
title: Begrænse SharePoint webstedsindhold til en geoplacering
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: I denne artikel kan du lære, hvordan du begrænser SharePoint til en bestemt geoplacering i et multi-geo-miljø.
ms.openlocfilehash: 06401658afe9f6a26b1280f5931ba6b3ba761742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590542"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a>Begrænse SharePoint webstedsindhold til en geoplacering

Under visse omstændigheder kan du vælge at gennemtvinge, at et websted og dets filindhold forbliver på den geoplacering, hvor webstedet blev oprettet, enten ved at forhindre webstedet i at blive flyttet eller ved at forhindre cachelagring af webstedets filindhold på en anden geoplacering.

Det kan du gøre ved hjælp af [Set-SPOSite-cmdlet'en](/powershell/module/sharepoint-online/set-sposite) med **parameteren RestrictedToGeo** . Denne parameter har en standardværdi for NULL, men du kan ændre den til en af følgende:

|Begrænsning|Beskrivelse|
|:----------|:----------|
|NoRestriction|Webstedet kan flyttes til en anden geoplacering.|
|BlockMoveOnly|Webstedet kan ikke flyttes til en anden geoplacering, men webstedsindhold kan cachelagres på andre geoplaceringer.|
|BlockFull|Webstedet kan ikke flyttes til en anden geoplacering, og fuldt filindhold cachelagres ikke på andre geoplaceringer. Filernes titel (lagret fra indholdet), filnavnet og andre egenskaber for filen kan stadig cachelagres i andre geoplaceringer.<br>Indhold, der er gemt på webstedet, før det blev konfigureret til BlockFull, kan fortsat være cachelagret på andre geoplaceringer.|

Brug følgende syntaks:

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

Eksempel:

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`