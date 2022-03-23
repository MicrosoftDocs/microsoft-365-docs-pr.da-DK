---
title: SharePoint lagerkvoter i multi-geo miljøer
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Få mere SharePoint om lagerkvoter i multi-geomiljøer, og hvordan kvoter kan administreres af SharePoint Online-administratoren.
ms.openlocfilehash: d1e47c206f1353093ba8bebf9db03ab7142d6da9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594276"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>SharePoint lagerkvoter i multi-geo miljøer

Som standard deler alle geoplaceringer i et multi-geo-miljø den tilgængelige lejers lagerkvote.

Med SharePoint geografisk lagerkvote kan du administrere lagerkvoten for hver geoplacering. Når du tildeler en lagerkvote for en geoplacering, bliver den den maksimale mængde lagerplads, der er tilgængelig for den pågældende geoplacering, og den trækkes fra den tilgængelige lejers lagerkvote. Den resterende tilgængelige lagerkvote for lejeren deles derefter på tværs af de konfigurerede geoplaceringer, som en bestemt lagerkvote ikke er blevet tildelt for.

Den SharePoint lagerkvote for en hvilken som helst geoplacering kan allokeres af SharePoint Online-administratoren ved at oprette forbindelse til den centrale placering. Geoadministratorer for satellitplaceringer kan få vist lagerkvoten, men kan ikke tildele den.

## <a name="configure-a-storage-quota-for-a-geo-location"></a>Konfigurere en lagerkvote for en geoplacering

Brug [Microsoft Office SharePoint Online-modulet](https://www.microsoft.com/download/details.aspx?id=35588), og opret forbindelse til den centrale placering for at allokere lagerkvoten til en geoplacering.

For at tildele Storage kvote for en placering skal du køre cmdlet'en:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

Hvis du vil Storage lagerkvote for den aktuelle geoplacering, skal du køre:

```powershell
Get-SPOGeoStorageQuota
```

![Skærmbillede af PowerShell-vinduet, der Get-SPOGeoStorageQuota en cmdlet.](../media/multi-geo-storage-quota.png)

Hvis du vil Storage lagerkvote for alle geoplaceringer, skal du køre:

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

Hvis du vil fjerne den tildelte lagerkvote for en geoplacering, skal du angive `StorageQuota value = 0`:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```
