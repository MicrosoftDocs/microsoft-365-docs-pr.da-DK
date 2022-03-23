---
title: Administrer SharePoint onlinewebstedsgrupper med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
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
description: I denne artikel kan du finde procedurer for brug af PowerShell til Microsoft 365 at administrere SharePoint Online-webstedsgrupper.
ms.openlocfilehash: deef41118789a9df4353fa188c88d827909dc863
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590592"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Administrer SharePoint onlinewebstedsgrupper med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Selvom du kan bruge Microsoft 365 Administration, kan du også bruge PowerShell til Microsoft 365 at administrere dine SharePoint Online-webstedsgrupper.

## <a name="before-you-begin"></a>Før du begynder

Fremgangsmåderne i denne artikel kræver, at du opretter forbindelse til SharePoint Online. Du kan finde en [vejledning Forbind at SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Vis SharePoint Online med PowerShell til Microsoft 365

Onlineadministration SharePoint har nogle brugervenlige metoder til administration af webstedsgrupper. Antag f.eks., at du vil se på grupperne og gruppemedlemmerne for `https://litwareinc.sharepoint.com/sites/finance` webstedet. Du skal gøre følgende:

1. Vælg aktive SharePoint i <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Administration, og**</a> vælg derefter URL-adressen til webstedet.
2. På webstedssiden skal <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**du Indstillinger**</a> (findes i øverste højre hjørne på siden) og derefter vælge **Webstedstilladelser**.

Gentag derefter processen for det næste websted, du vil se nærmere på.

Hvis du vil have en liste over grupperne med PowerShell Microsoft 365, kan du bruge følgende kommandoer:

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

Der er to måder at køre dette kommandosæt på i SharePoint Online Management Shell-kommandoprompt:

- Kopiér kommandoerne til Notesblok (eller et andet tekstredigeringsprogram), rediger værdien af **$siteURL-variablen**, markér kommandoerne, og indsæt dem derefter i SharePoint Online Management Shell-kommandoprompten. Når du gør det, stopper PowerShell ved en **>>** meddelelse. Tryk på Enter for at udføre `foreach` kommandoen.<br/>
- Kopiér kommandoerne til Notesblok (eller et andet tekstredigeringsprogram), rediger værdien af **$siteURL-variablen**, og gem derefter denne tekstfil med et navn og filtypenavnet .ps1 i en passende mappe. Kør derefter scriptet fra SharePoint Online Management Shell ved at angive dens sti og filnavn. Her er en eksempelkommando:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

I begge tilfælde bør du se noget, der ligner dette:

![SharePoint Online-webstedsgrupper.](../media/SPO-site-groups.png)

Dette er alle de grupper, der er oprettet for webstedet `https://litwareinc.sharepoint.com/sites/finance`, og alle de brugere, der er tildelt disse grupper. Gruppenavnene vises med gult for at hjælpe dig med at adskille gruppenavnene fra deres medlemmer.

Som et andet eksempel er her et kommandosæt, der viser grupperne og alle gruppemedlemskaberne for alle dine SharePoint Online-websteder.

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

[Opret SharePoint Online-websteder, og tilføj brugere med PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrer SharePoint onlinebrugere og -grupper med PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
