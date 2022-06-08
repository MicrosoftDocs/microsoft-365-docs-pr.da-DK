---
title: Opret en Microsoft 365-gruppe med en bestemt foretrukket dataplacering
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
description: Få mere at vide om, hvordan du opretter en Microsoft 365-gruppe med en angivet foretrukken dataplacering i et multi-geo-miljø.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: ff9b6ae6949ab1e6af1ee102abfcf2cb132fed9f
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940706"
---
# <a name="create-a-microsoft-365-group-with-a-specific-preferred-data-location"></a>Opret en Microsoft 365-gruppe med en bestemt foretrukken dataplacering

Når brugere i et multi-geo-miljø opretter en Microsoft 365-gruppe, angives gruppens foretrukne dataplacering (PDL) automatisk til brugerens. Globale administratorer, SharePoint- og Exchange-administratorer kan oprette grupper i et hvilket som helst område, de vælger. 

Hvis du har brug for at oprette en gruppe med en bestemt PDL, kan du gøre det ved hjælp af <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Fra SharePoint Administration</a> eller via Exchange Online New-UnifiedGroup Microsoft PowerShell-cmdlet. Når du gør dette, klargøres både den gruppepostkasse og det SharePoint-websted, der er knyttet til gruppen, i den angivne PDL.

Hvis du vil oprette en Microsoft 365-gruppe med den PDL, du angiver, skal du gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a> på den geografiske placering, hvor du vil oprette gruppewebstedet.

Eksempel:

Hvis du vil oprette et gruppewebsted på din placering i Australien, kan du gå til `https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement`

1. Vælg **+ Opret**.
2. Følg processen for at oprette et gruppewebsted.

Dit gruppewebsted klargøres på den geografiske placering, der svarer til SharePoint Administration, hvorfra du startede anmodningen om oprettelse af webstedet. 

Brug af Exchange PowerShell 

Opret forbindelse til Exchange Online PowerShell, og overfør parameteren *-MailBoxRegion* med geoplaceringskoden.

Eksempel: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Skærmbillede af New-UnifiedGroup PowerShell-cmdlet med syntaks.](../media/multi-geo-new-group-with-pdl-powershell.png)

> [!Note]
> Klargøring af SharePoint-gruppewebsted er efter behov. Webstedet klargøres, første gang en gruppeejer eller et medlem forsøger at få adgang til det.

## <a name="geo-location-codes"></a>Geo-placeringskoder

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="related-topics"></a>Relaterede emner

[Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

[Opret grupper med en bestemt foretrukket dataplacering ved hjælp af Graph API](/graph/api/group-post-groups)
