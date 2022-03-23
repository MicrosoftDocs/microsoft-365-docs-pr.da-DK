---
title: Tilføje eller fjerne en geoadministrator
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Har du brug for at konfigurere separate administratorer for hver geoplacering? Lær at tilføje eller fjerne en geoadministrator i Microsoft 365 Multi-Geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e661e42759fe0b035bfe97c33165f78316973403
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591002"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Tilføje eller fjerne en geoadministrator i Microsoft 365 Multi-Geo

Du kan konfigurere separate administratorer for hver geoplacering, du har i din lejer. Disse administratorer har adgang til de SharePoint Online og OneDrive, der er specifikke for deres geoplacering.

Nogle tjenester – f.eks. ordbanken – administreres fra den centrale placering og replikeres til satellitplaceringer. Geo-administratoren for den centrale placering har adgang til disse, mens geoadministratorer for satellitplaceringer ikke har adgang til dem.

Globale administratorer og SharePoint Online-administratorer har fortsat adgang til indstillinger på den centrale placering og alle satellitplaceringer.

## <a name="configuring-geo-administrators"></a>Konfiguration af geoadministratorer

Konfiguration af geoadministratorer kræver et SharePoint Online PowerShell-modul.

Brug [Forbind-SPOService](/powershell/module/sharepoint-online/Connect-SPOService) til at oprette forbindelse til Administration for den geoplacering, hvor du vil tilføje geoadministratoren. (F.eks. Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Hvis du vil have vist de eksisterende geoadministratorer for en placering, skal du køre `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Tilføje en bruger som geoadministrator

Hvis du vil tilføje en bruger som geoadministrator, skal du køre `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Hvis du vil fjerne en bruger som geoadministrator for en placering, skal du køre  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Tilføje en gruppe som geoadministrator

Du kan tilføje en sikkerhedsgruppe eller en mailaktiveret sikkerhedsgruppe som geoadministrator. Distributionsgrupper og Microsoft 365-grupper understøttes ikke.

Hvis du vil tilføje en gruppe som geoadministrator, skal du køre `Add-SPOGeoAdministrator -GroupAlias <alias>`

Hvis du vil fjerne en gruppe som geoadministrator, skal du køre `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Bemærk, at ikke alle sikkerhedsgrupper har et gruppealias. Hvis du vil tilføje en sikkerhedsgruppe, der ikke har et alias, skal du køre [Get-MsolGroup](/powershell/module/msonline/get-msolgroup) for at hente en liste over grupper, finde din sikkerhedsgruppes Objekt-id og derefter køre:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Hvis du vil fjerne en gruppe ved hjælp af objekt-id'et, skal du køre `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="related-topics"></a>Relaterede emner

[Add-SPOGeoAdministrator](/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Angiv et alias (MailNickName) for en sikkerhedsgruppe](/powershell/module/azuread/set-azureadgroup)