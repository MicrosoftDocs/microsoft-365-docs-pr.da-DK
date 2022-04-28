---
title: Administrer SharePoint onlinewebstedsgrupper med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/17/2019
audience: Admin
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: I denne artikel kan du finde procedurer for brug af PowerShell til Microsoft 365 til at administrere SharePoint onlinewebstedsgrupper.
ms.openlocfilehash: 411ab477668b7956a63843d0b58b8d6d9bfc9059
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096430"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Administrer SharePoint onlinewebstedsgrupper med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Selvom du kan bruge Microsoft 365 Administration, kan du også bruge PowerShell til Microsoft 365 til at administrere dine SharePoint onlinewebstedsgrupper.

## <a name="before-you-begin"></a>Før du begynder

Procedurerne i denne artikel kræver, at du opretter forbindelse til SharePoint Online. Du kan finde instruktioner [under Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Vis SharePoint Online med PowerShell til Microsoft 365

SharePoint Online Administration har nogle brugervenlige metoder til administration af webstedsgrupper. Lad os f.eks. antage, at du vil se på grupperne og gruppemedlemmerne `https://litwareinc.sharepoint.com/sites/finance` for webstedet. Her er, hvad du skal gøre for at:

1. Vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> i SharePoint Administration, og vælg derefter URL-adressen til webstedet.
2. På webstedssiden skal du vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Indstillinger**</a> (placeret i øverste højre hjørne af siden) og derefter vælge **Webstedstilladelser**.

Gentag derefter processen for det næste websted, du vil se på.

Hvis du vil hente en liste over grupperne med PowerShell til Microsoft 365, kan du bruge følgende kommandoer:

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Der er to måder at køre dette kommandosæt på i kommandoprompten SharePoint Online Management Shell:

- Kopiér kommandoerne til Notesblok (eller en anden teksteditor), rediger værdien af variablen **$siteURL**, vælg kommandoerne, og indsæt dem derefter i kommandoprompten SharePoint Online Management Shell. Når du gør det, stopper PowerShell, **>>** når du bliver bedt om det. Tryk på Enter for at udføre kommandoen `foreach` .<br/>
- Kopiér kommandoerne til Notesblok (eller en anden teksteditor), rediger værdien af variablen **$siteURL**, og gem derefter denne tekstfil med et navn og filtypenavnet .ps1 i en passende mappe. Kør derefter scriptet fra kommandoprompten SharePoint Online Management Shell ved at angive stien og filnavnet. Her er et eksempel på en kommando:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

I begge tilfælde kan du se noget, der ligner dette:

![SharePoint onlinewebstedsgrupper.](../media/SPO-site-groups.png)

Dette er alle de grupper, der er oprettet for webstedet `https://litwareinc.sharepoint.com/sites/finance`, og alle de brugere, der er tildelt disse grupper. Gruppenavnene er gule for at hjælpe dig med at adskille gruppenavne fra deres medlemmer.

Som et andet eksempel er her et kommandosæt, der viser grupperne og alle gruppemedlemskaber for alle dine SharePoint Online-websteder.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```

## <a name="see-also"></a>Se også

[Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Opret SharePoint onlinewebsteder, og tilføj brugere med PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrer SharePoint Online-brugere og -grupper med PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
