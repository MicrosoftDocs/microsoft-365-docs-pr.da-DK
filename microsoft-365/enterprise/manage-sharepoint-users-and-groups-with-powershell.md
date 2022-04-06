---
title: Administrer SharePoint onlinebrugere og -grupper med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel kan du lære at bruge PowerShell til Microsoft 365 at administrere SharePoint Online-brugere, -grupper og -websteder.
ms.openlocfilehash: e2166753b1be56c19011a1fc7e20d1584a5d3004
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681188"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Administrer SharePoint onlinebrugere og -grupper med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du er en SharePoint Online-administrator, der arbejder med store lister over brugerkonti eller grupper og ønsker en nemmere måde at administrere dem på, kan du bruge PowerShell til Microsoft 365.

Inden du begynder, kræver fremgangsmåderne i denne artikel, at du opretter forbindelse til SharePoint Online. Du kan finde en [vejledning Forbind at SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Få en liste over websteder, grupper og brugere

Før vi begynder at administrere brugere og grupper, skal du have lister over dine websteder, grupper og brugere. Du kan derefter bruge disse oplysninger til at gennemgå eksemplet i denne artikel.

Få en liste over webstederne i din lejer med denne kommando:

```powershell
Get-SPOSite
```

Få en liste over grupperne i din lejer med denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Få en liste over brugerne i din lejer med denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Føje en bruger til gruppen af administratorer af grupper af websteder

Du kan bruge `Set-SPOUser` cmdlet'en til at føje en bruger til listen over administratorer af grupper af websteder i en gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Hvis du vil bruge disse kommandoer, skal du erstatte alt i anførselstegnene, herunder < og >, med de korrekte navne.

Eksempelvis føjer dette sæt kommandoer Opal Castiro (brugernavn opalc) til listen over administratorer af grupper af websteder i contosoTest-gruppen af websteder i Contoso-lejen:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Du kan kopiere og indsætte disse kommandoer i Notesblok, ændre de variable værdier for $tenant, $site og $user til faktiske værdier fra dit miljø og derefter indsætte dette i dit SharePoint Online Management Shell-vindue for at køre dem.

## <a name="add-a-user-to-other-site-collection-groups"></a>Føje en bruger til andre grupper af websteder

I denne opgave bruger vi cmdlet'en `Add-SPOUser` til at føje en bruger til en SharePoint gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Lad os f.eks. føje Glen Rife (brugernavn glenr) til gruppen Revisorer i gruppen af ContosoTest-websteder i contoso-lejen:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Oprette en gruppe af websteder

Du kan bruge `New-SPOSiteGroup` cmdlet'en til at oprette en ny SharePoint og føje den til en gruppe af websteder.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

Gruppeegenskaber, f.eks. tilladelsesniveauer, kan opdateres senere ved hjælp af `Set-SPOSiteGroup` cmdlet'en.

Lad os f.eks. tilføje gruppen Revisorer med kun visningstilladelser til gruppen af contosotest-websteder i contoso-lejen:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Fjern brugere fra en gruppe

Nogle gange skal du fjerne en bruger fra et websted eller endda alle websteder. Måske flytter medarbejderen fra én division til en anden eller forlader virksomheden. Du kan nemt gøre dette for én medarbejder i brugergrænsefladen, men det er ikke nemt, når du skal flytte en komplet division fra ét websted til et andet.

Men ved at bruge SharePoint Online Management Shell- og CSV-filer er dette hurtigt og nemt. I denne opgave skal du bruge en Windows PowerShell at fjerne en bruger fra en sikkerhedsgruppe af websteder. Derefter skal du bruge en CSV-fil og fjerne mange brugere fra forskellige websteder.

Vi bruger cmdlet'en "Remove-SPOUser" til at fjerne en enkelt Microsoft 365-bruger fra en gruppe af websteder, så vi kan se kommandosyntaksen. Sådan ser syntaksen ud:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Lad os f.eks. fjerne Bobby Overby fra gruppen Revisorer for gruppe af websteder i gruppen af contosotest-websteder i contoso-lejen:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Antag, at vi vil fjerne Bobby fra alle de grupper, han aktuelt er i. Sådan ville vi gøre det:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Dette er blot et eksempel. Du bør ikke køre denne kommando, medmindre du er nødt til at fjerne en bruger fra hver gruppe, f.eks. hvis brugeren forlader virksomheden.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatiser administrationen af store lister over brugere og grupper

Hvis du vil føje et stort antal konti til SharePoint-websteder og give dem tilladelser, kan du bruge Microsoft 365 Administration, individuelle PowerShell-kommandoer eller PowerShell- og en CSV-fil. Csv-filen er den hurtigste måde at automatisere denne opgave på.

Den grundlæggende proces er at oprette en CSV-fil med overskrifter (kolonner), der svarer til de parametre, som Windows PowerShell behov for. Du kan nemt oprette en sådan liste i Excel og derefter eksportere den som en CSV-fil. Derefter skal du bruge et Windows PowerShell-script til at iterere gennem poster (rækker) i CSV-filen og føje brugerne til grupper og grupper til websteder.

Lad os f.eks. oprette en CSV-fil til at definere en gruppe af grupper af websteder, grupper og tilladelser. Derefter opretter vi en CSV-fil til at udfylde grupper med brugere. Til sidst opretter og kører vi et Windows PowerShell script, der opretter og udfylder grupperne.

Den første CSV-fil føjer en eller flere grupper til en eller flere grupper af websteder og får denne struktur:

Sidehoved:

```powershell
Site,Group,PermissionLevels
```

Vare:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Her er en eksempelfil:

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

Den anden CSV-fil føjer en eller flere brugere til en eller flere grupper og får denne struktur:

Sidehoved:

```powershell
Group,LoginName,Site
```

Vare:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Her er en eksempelfil:

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

I næste trin skal du have de to CSV-filer gemt på dit drev. Her er eksempelkommandoer, der bruger både CSV-filer og til at tilføje tilladelser og gruppemedlemskab:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Scriptet importerer indholdet af CSV-filen og bruger værdierne i kolonnerne til at udfylde parametrene for **New-SPOSiteGroup** - og **Add-SPOUser-kommandoerne** . I vores eksempel gemmer vi denne fil i O365Admin-mappen på drev C, men du kan gemme den, hvor du vil.

Lad os nu fjerne en gruppe personer for flere grupper på forskellige websteder ved hjælp af den samme CSV-fil. Her er en eksempelkommando:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Generere brugerrapporter

Det kan være en god ide at hente en rapport for nogle få websteder og vise brugerne for disse websteder, deres tilladelsesniveau og andre egenskaber. Sådan ser syntaksen ud:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Dette fanger dataene for disse tre websteder og skriver dem til en tekstfil på dit lokale drev. Parameteren –Tilføjelse føjer nyt indhold til en eksisterende fil.

Lad os f.eks. køre en rapport på ContosoTest-, TeamSite01- og Project01-webstederne for Contoso1-lejeren:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Vi var nødt til kun at **ændre $site** variablen. **Variablen $tenant** sin værdi gennem alle tre løb af kommandoen.

Men hvad nu, hvis du gerne vil gøre dette for alle websteder? Du kan gøre dette uden at skulle skrive alle webstederne ved hjælp af denne kommando:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Denne rapport er forholdsvis enkel, og du kan tilføje mere kode for at oprette mere specifikke rapporter eller rapporter, der indeholder mere detaljerede oplysninger. Men dette bør give dig en ide om, hvordan du bruger SharePoint Online Management Shell til at administrere brugere i SharePoint Online-miljøet.

## <a name="see-also"></a>Se også

[Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Administrer SharePoint Online med PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
