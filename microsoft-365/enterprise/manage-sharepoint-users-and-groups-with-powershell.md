---
title: Administrer SharePoint Online-brugere og -grupper med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
description: I denne artikel kan du få mere at vide om, hvordan du bruger PowerShell til Microsoft 365 til at administrere SharePoint Online-brugere, -grupper og -websteder.
ms.openlocfilehash: 78c829e476c63e435d9543b3a4175cdbbccb76e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100671"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Administrer SharePoint Online-brugere og -grupper med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du er SharePoint Online-administrator, der arbejder med store lister over brugerkonti eller grupper og ønsker en nemmere måde at administrere dem på, kan du bruge PowerShell til Microsoft 365.

Før du begynder, kræver procedurerne i denne artikel, at du opretter forbindelse til SharePoint Online. Du kan finde instruktioner [under Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Hent en liste over websteder, grupper og brugere

Før vi begynder at administrere brugere og grupper, skal du hente lister over dine websteder, grupper og brugere. Du kan derefter bruge disse oplysninger til at gennemgå eksemplet i denne artikel.

Hent en liste over webstederne i din lejer med denne kommando:

```powershell
Get-SPOSite
```

Hent en liste over grupperne i din lejer med denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Hent en liste over brugerne i din lejer med denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Føj en bruger til gruppen af administratorer af gruppen af websteder

Du kan bruge cmdlet'en `Set-SPOUser` til at føje en bruger til listen over administratorer af grupper af websteder på en gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Hvis du vil bruge disse kommandoer, skal du erstatte alt i anførselstegnene, herunder < og > tegn, med de korrekte navne.

Dette sæt kommandoer føjer f.eks. Opal Castillo (brugernavn opalc) til listen over administratorer af grupper af websteder på gruppen af ContosoTest-websteder i Contoso-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Du kan kopiere og indsætte disse kommandoer i Notesblok, ændre variabelværdierne for $tenant, $site og $user til faktiske værdier fra dit miljø og derefter indsætte dem i vinduet SharePoint Online Management Shell for at køre dem.

## <a name="add-a-user-to-other-site-collection-groups"></a>Føj en bruger til andre grupper af websteder

I denne opgave skal vi bruge cmdlet'en `Add-SPOUser` til at føje en bruger til en SharePoint gruppe på en gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Lad os f.eks. føje Glen Rife (user name glenr) til gruppen Auditører på gruppen af ContosoTest-websteder i contoso-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Opret en gruppe af websteder

Du kan bruge cmdlet'en `New-SPOSiteGroup` til at oprette en ny SharePoint gruppe og føje den til en gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

Gruppeegenskaber, f.eks. tilladelsesniveauer, kan opdateres senere ved hjælp af cmdlet'en `Set-SPOSiteGroup` .

Lad os f.eks. føje gruppen Revisorer med tilladelsen Vis kun til gruppen af contosotest-websteder i contoso-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Fjern brugere fra en gruppe

Nogle gange er du nødt til at fjerne en bruger fra et websted eller endda alle websteder. Måske flytter medarbejderen fra én afdeling til en anden eller forlader virksomheden. Det kan du nemt gøre for én medarbejder i brugergrænsefladen, men det er ikke nemt, når du skal flytte en komplet division fra ét websted til et andet.

Men ved hjælp af SharePoint Online Management Shell- og CSV-filer er dette hurtigt og nemt. I denne opgave skal du bruge Windows PowerShell til at fjerne en bruger fra en sikkerhedsgruppe for en gruppe af websteder. Derefter skal du bruge en CSV-fil og fjerne mange brugere fra forskellige websteder.

Vi bruger cmdlet'en 'Remove-SPOUser' til at fjerne en enkelt Microsoft 365 bruger fra en gruppe af websteder, så vi kan se kommandosyntaksen. Sådan ser syntaksen ud:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Lad os f.eks. fjerne Bobby Overby fra gruppen af revisorer for gruppen af websteder i gruppen af contosotest-websteder i contoso-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Lad os antage, at vi vil fjerne Bobby fra alle de grupper, han er i i øjeblikket. Sådan gør vi:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Dette er blot et eksempel. Du bør ikke køre denne kommando, medmindre du virkelig skal fjerne en bruger fra hver gruppe, f.eks. hvis brugeren forlader virksomheden.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatiser administration af store lister over brugere og grupper

Hvis du vil føje et stort antal konti til SharePoint websteder og give dem tilladelser, kan du bruge Microsoft 365 Administration, individuelle PowerShell-kommandoer eller PowerShell og en CSV-fil. Af disse valg er CSV-filen den hurtigste måde at automatisere denne opgave på.

Den grundlæggende proces er at oprette en CSV-fil, der har overskrifter (kolonner), der svarer til de parametre, som Windows PowerShell script har brug for. Du kan nemt oprette en sådan liste i Excel og derefter eksportere den som en CSV-fil. Derefter kan du bruge et Windows PowerShell script til at gentage via poster (rækker) i CSV-filen og føje brugerne til grupper og grupperne til websteder.

Lad os f.eks. oprette en CSV-fil for at definere en gruppe af grupper af websteder, grupper og tilladelser. Derefter skal vi oprette en CSV-fil for at udfylde grupperne med brugere. Til sidst opretter og kører vi et Windows PowerShell script, der opretter og udfylder grupperne.

Den første CSV-fil føjer en eller flere grupper til en eller flere grupper af websteder og har denne struktur:

Header:

```powershell
Site,Group,PermissionLevels
```

Element:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Her er et eksempel på en fil:

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Den anden CSV-fil føjer en eller flere brugere til en eller flere grupper og har denne struktur:

Header:

```powershell
Group,LoginName,Site
```

Element:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Her er et eksempel på en fil:

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

Til næste trin skal du gemme de to CSV-filer på drevet. Her er eksempler på kommandoer, der bruger både CSV-filer og til at tilføje tilladelser og gruppemedlemskab:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Scriptet importerer indholdet af CSV-filen og bruger værdierne i kolonnerne til at udfylde parametrene for kommandoerne **New-SPOSiteGroup** og **Add-SPOUser** . I vores eksempel gemmer vi denne fil i mappen O365Admin på drev C, men du kan gemme den, hvor du vil.

Lad os nu fjerne en masse personer til flere grupper på forskellige websteder ved hjælp af den samme CSV-fil. Her er et eksempel på en kommando:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generér brugerrapporter

Det kan være en god idé at hente en rapport for et par websteder og få vist brugerne for disse websteder, deres tilladelsesniveau og andre egenskaber. Sådan ser syntaksen ud:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Dette henter dataene til disse tre websteder og skriver dem til en tekstfil på dit lokale drev. Parameteren – Tilføjelse føjer nyt indhold til en eksisterende fil.

Lad os f.eks. køre en rapport på webstederne ContosoTest, TeamSite01 og Project01 for Contoso1-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Vi var nødt til kun at ændre variablen **$site** . Variablen **$tenant** bevarer sin værdi gennem alle tre kørsler af kommandoen.

Men hvad nu hvis du ville gøre dette for hvert websted? Det kan du gøre uden at skulle skrive alle disse websteder ved hjælp af denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Denne rapport er forholdsvis enkel, og du kan tilføje mere kode for at oprette mere specifikke rapporter eller rapporter, der indeholder mere detaljerede oplysninger. Men det bør give dig en idé om, hvordan du kan bruge SharePoint Online Management Shell til at administrere brugere i SharePoint Online-miljøet.

## <a name="see-also"></a>Se også

[Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Administrer SharePoint Online med PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
