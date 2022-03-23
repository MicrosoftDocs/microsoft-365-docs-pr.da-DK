---
title: Opret en Microsoft 365 gruppe med en bestemt foretrukken dataplacering
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du Microsoft 365 en gruppe med en bestemt foretrukken dataplacering i et multi-geo-miljø.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 7de00ad0d94cda0a47f4981d78ebc07cedab6ada
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590574"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Opret en Microsoft 365 gruppe med en bestemt foretrukken dataplacering

Når brugere i et multigealt miljø opretter en Microsoft 365-gruppe, angives gruppens foretrukne dataplacering automatisk til brugerens. Globale, SharePoint og Exchange administratorer kan oprette grupper i et hvilket som helst område, de vælger. 

Hvis du har brug for at oprette en gruppe med en bestemt PDL, kan du gøre det ved hjælp af <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a> eller via Exchange Online New-UnifiedGroup Microsoft PowerShell-cmdlet'en. Når du gør dette, klargøres både gruppepostkassen og SharePoint websted, der er knyttet til gruppen, i den angivne PDL.

Hvis du vil oprette Microsoft 365-gruppe med den PDL, du angiver, skal du gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint</a> Administration i den geoplacering, hvor du vil oprette gruppewebstedet.

Eksempel:

Hvis du vil oprette et gruppewebsted i din placering i Australien, kan du gå til https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Vælg **+ Opret**.
2. Følg processen for at oprette et gruppewebsted.

Dit gruppewebsted bliver klargjort på den geoplacering, der svarer til SharePoint Administration, hvorfra du startede anmodningen om oprettelse af webstedet. 

Brug Exchange PowerShell 

Forbind til Exchange Online PowerShell og videregive parameteren *-MailBoxRegion* med geoplaceringskoden.

Eksempel: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Skærmbillede af New-UnifiedGroup PowerShell-cmdlet med syntaks.](../media/multi-geo-new-group-with-pdl-powershell.png)

Bemærk, SharePoint til klargøring af gruppewebsteder efter behov. Webstedet klargøres, første gang en gruppeejer eller et medlem forsøger at få adgang til det.

## <a name="geo-location-codes"></a>Geoplaceringskoder

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Relaterede emner

[Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Opret grupper med en bestemt foretrukken dataplacering ved hjælp Graph API](/graph/api/group-post-groups)
