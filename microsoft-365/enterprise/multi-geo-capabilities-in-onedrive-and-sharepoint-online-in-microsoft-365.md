---
title: Multi-Geo-funktioner i OneDrive og SharePoint Online
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Udvid din Microsoft 365 tilstedeværelse til flere geografiske områder med multi-geo-funktioner i OneDrive Online.
ms.openlocfilehash: e49df6054e30e9e288e893da8d914ebb567eb8e5
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622235"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Multi-Geo-funktioner i OneDrive og SharePoint Online

Multi-Geo-funktioner i OneDrive og SharePoint Online gør det muligt at styre delte ressourcer, f.eks. SharePoint teamwebsteder og Microsoft 365 gruppepostkasser, der er gemt inaktivt på en angivet geografisk placering.

Hver bruger, gruppepostkasse og SharePoint websted har en foretrukken dataplacering (PDL), som angiver den geografiske placering, hvor relaterede data skal gemmes. Brugernes personlige data (Exchange postkasse og OneDrive) sammen med alle Microsoft 365-grupper eller SharePoint websteder, som de opretter, kan gemmes på den angivne geografiske placering for at opfylde kravene til dataopbevaring. Du kan [angive forskellige administratorer for hver geografisk placering](add-a-sharepoint-geo-admin.md).

Brugerne får en problemfri oplevelse, når de bruger Microsoft 365 tjenester, herunder Office programmer, OneDrive og søgning. Se [Brugeroplevelsen i et multi-geo-miljø](multi-geo-user-experience.md) for at få flere oplysninger.

## <a name="onedrive"></a>OneDrive

Hver brugers OneDrive kan klargøres i eller [flyttes af en administrator](move-onedrive-between-geo-locations.md) til en satellitplacering i overensstemmelse med brugerens PDL. Personlige filer opbevares derefter på den pågældende geografiske placering, selvom de kan deles med brugere på andre geografiske placeringer.

## <a name="sharepoint-sites-and-groups"></a>SharePoint websteder og grupper

Administration af Multi-Geo-funktionen er tilgængelig via <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. Du kan finde detaljerede oplysninger i det [tilsvarende blogindlæg](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Når en bruger opretter et SharePoint gruppeforbundet websted i et multi-geo-miljø, bruges deres PDL til at bestemme den geografiske placering, hvor webstedet og dets tilknyttede gruppepostkasse oprettes. Hvis brugerens PDL-værdi ikke er angivet eller er indstillet til geografisk placering, der ikke er konfigureret som en satellitplacering, oprettes webstedet og postkassen på den centrale placering.

Microsoft 365 andre tjenester end Exchange, OneDrive, SharePoint og Teams er ikke Multi-Geo. Men Microsoft 365-grupper, der oprettes af disse tjenester, konfigureres med forfatterens PDL og deres Exchange gruppepostkasse, SharePoint websted klargøres i det tilsvarende geografiske område. 

## <a name="managing-the-multi-geo-environment"></a>Administration af multi-geo-miljøet

Konfiguration og administration af dit multi-geo-miljø sker via <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. 

![Skærmbillede af siden med geografiske placeringer i SharePoint Administration.](../media/sharepoint-multi-geo-admin-center.png)

Nogle handlinger, f.eks. flytning af et SharePoint websted eller et OneDrive websted, kræver Microsoft PowerShell.

## <a name="see-also"></a>Se også

[Multi-Geo i SharePoint og Microsoft 365-grupper](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administration af et multigeografisk miljø](administering-a-multi-geo-environment.md)

[SharePoint lagerkvoter i multi-geo-miljøer](sharepoint-multi-geo-storage-quota.md)

[Administration af Exchange Online postkasser i et multi-geo-miljø](administering-exchange-online-multi-geo.md)
