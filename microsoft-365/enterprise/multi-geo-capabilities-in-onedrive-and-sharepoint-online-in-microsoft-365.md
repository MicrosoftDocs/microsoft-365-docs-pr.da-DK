---
title: Multi-Geo Capabilities in OneDrive and SharePoint Online
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
description: Udvid din Microsoft 365 til flere geografiske områder med multi-geo-funktioner i OneDrive Online.
ms.openlocfilehash: 778efca6035dad05ec9bc77298b888e50f381ca1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590332"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a>Multi-Geo Capabilities in OneDrive and SharePoint Online

Multi-Geo-funktioner i OneDrive og SharePoint Online muliggør kontrol over delte ressourcer som f.eks. SharePoint-teamwebsteder og Microsoft 365-gruppepostkasser, der er gemt i hvile på en bestemt geoplacering.

Hver bruger, gruppepostkasse og SharePoint-websted har en FORETRUKken dataplacering (PDL), som angiver den geoplacering, hvor relaterede data skal gemmes. Brugernes personlige data (Exchange-postkasse og OneDrive) sammen med eventuelle Microsoft 365 Grupper eller SharePoint-websteder, som de opretter, kan gemmes på det angivne geoplacering for at opfylde krav til dataopbevaring. Du kan [angive forskellige administratorer for hver geoplacering](add-a-sharepoint-geo-admin.md).

Brugerne får en problemfri oplevelse, når de bruger Microsoft 365, herunder Office, OneDrive og Søg. Se [Brugeroplevelse i et multi-geo-miljø for at](multi-geo-user-experience.md) få flere oplysninger.

## <a name="onedrive"></a>OneDrive

Hver brugers OneDrive kan klargøres eller flyttes af en [administrator](move-onedrive-between-geo-locations.md) til en satellitplacering i overensstemmelse med brugerens PDL. Personlige filer opbevares derefter på den pågældende geoplacering, selvom de kan deles med brugere på andre geoplaceringer.

## <a name="sharepoint-sites-and-groups"></a>SharePoint websteder og grupper

Administration af funktionen Multi-Geo er tilgængelig via <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. Detaljerede oplysninger kan findes i det tilsvarende [blogindlæg](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).

Når en bruger opretter et SharePoint-gruppeforbundet websted i et multi-geo-miljø, bruges deres PDL til at bestemme den geoplacering, hvor webstedet og den tilknyttede gruppepostkasse oprettes. Hvis brugerens PDL-værdi ikke er blevet angivet eller er indstillet til en geoplacering, der ikke er konfigureret som en satellitplacering, oprettes webstedet og postkassen på den centrale placering.

Microsoft 365 andre tjenester end Exchange, OneDrive, SharePoint og Teams ikke multi-geo. Men Microsoft 365 grupper, der er oprettet af disse tjenester, vil blive konfigureret med PDL hos den, der har oprettet filen, og dennes Exchange-gruppepostkasse, klargøres SharePoint-webstedet i det tilsvarende geo. 

## <a name="managing-the-multi-geo-environment"></a>Administration af multi-geo-miljøet

Konfiguration og administration af dit multi-geo-miljø udføres <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">via SharePoint Administration</a>. 

![Skærmbillede af siden med geoplaceringer i SharePoint Administration.](../media/sharepoint-multi-geo-admin-center.png)

(Nogle handlinger, f.eks. flytning af SharePoint websted eller et OneDrive websted kræver Microsoft PowerShell).

## <a name="see-also"></a>Se også

[Multi-Geo i SharePoint og Microsoft 365 Grupper](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[Administration af et multi-geo-miljø](administering-a-multi-geo-environment.md)

[SharePoint lagerkvoter i multi-geo miljøer](sharepoint-multi-geo-storage-quota.md)

[Administration Exchange Online postkasser i et multi-geo-miljø](administering-exchange-online-multi-geo.md)
