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
description: Få mere at vide om, hvordan du opretter en Microsoft 365 gruppe med en angivet foretrukken dataplacering i et multi-geo-miljø.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 162f499a783c23ec45ec75610833c61978beaafb
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623384"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Opret en Microsoft 365 gruppe med en bestemt foretrukken dataplacering

Når brugere i et multi-geo-miljø opretter en Microsoft 365 gruppe, angives PDL (group preferred data location) automatisk til brugerens. Globale, SharePoint og Exchange administratorer kan oprette grupper i et hvilket som helst område, de vælger. 

Hvis du har brug for at oprette en gruppe med en bestemt PDL, kan du gøre det ved hjælp af <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">fra SharePoint Administration</a> eller via Exchange Online New-UnifiedGroup Microsoft PowerShell-cmdlet'en. Når du gør dette, klargøres både gruppepostkassen og SharePoint websted, der er knyttet til gruppen, i den angivne PDL.

Hvis du vil oprette en Microsoft 365 gruppe med den PDL, du angiver, skal du gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a> på den geografiske placering, hvor du vil oprette gruppewebstedet.

Eksempel:

Hvis du vil oprette et gruppewebsted på din placering i Australien, kan du gå til https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement

1. Vælg **+ Opret**.
2. Følg processen for at oprette et gruppewebsted.

Dit gruppewebsted klargøres på den geografiske placering, der svarer til den SharePoint Administration, hvorfra du startede anmodningen om oprettelse af webstedet. 

Brug Exchange PowerShell 

Forbind til at Exchange Online PowerShell og overføre parameteren *-MailBoxRegion* med geoplaceringskoden.

Eksempel: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Skærmbillede af New-UnifiedGroup PowerShell-cmdlet med syntaks.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> SharePoint klargøring af gruppewebsted er efter behov. Webstedet klargøres, første gang en gruppeejer eller et medlem forsøger at få adgang til det.

## <a name="geo-location-codes"></a>Geo-placeringskoder

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Relaterede emner

[Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Opret grupper med en bestemt foretrukken dataplacering ved hjælp af Graph API](/graph/api/group-post-groups)
