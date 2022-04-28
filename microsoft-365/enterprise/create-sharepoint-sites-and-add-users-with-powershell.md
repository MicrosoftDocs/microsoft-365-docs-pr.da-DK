---
title: Opret SharePoint onlinewebsteder, og tilføj brugere med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Brug PowerShell til at oprette nye SharePoint Online-websteder, og føj derefter brugere og grupper til disse websteder.'
ms.openlocfilehash: 9d99f98825d88e2d2e63f106a7b5704c773c8be1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101331"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>Opret SharePoint onlinewebsteder, og tilføj brugere med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Når du bruger PowerShell til Microsoft 365 til at oprette SharePoint onlinewebsteder og tilføje brugere, kan du hurtigt og gentagne gange udføre opgaver meget hurtigere, end du kan i Microsoft 365 Administration. Du kan også udføre opgaver, der ikke er mulige at udføre i Microsoft 365 Administration.

## <a name="connect-to-sharepoint-online"></a>Forbind til SharePoint Online

Procedurerne i dette emne kræver, at du opretter forbindelse til SharePoint Online. Du kan finde instruktioner [under Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>Trin 1: Opret nye grupper af websteder ved hjælp af PowerShell

Opret flere websteder ved hjælp af PowerShell og en .csv fil, som du opretter ved hjælp af den angivne eksempelkode og Notesblok. I denne procedure erstatter du pladsholderoplysningerne, der vises i kantede parenteser, med dine egne websteds- og lejerspecifikke oplysninger. Med denne proces kan du oprette en enkelt fil og køre en enkelt PowerShell-kommando, der bruger den pågældende fil. Dette gør de handlinger, der udføres, både gentagelige og bærbare, og fjerner mange, hvis ikke alle, fejl, der kan komme fra at skrive lange kommandoer i SharePoint Online Management Shell. Der er to dele i denne procedure. Først skal du oprette en .csv fil, og derefter skal du referere til den .csv fil ved hjælp af PowerShell, som bruger indholdet til at oprette webstederne.

PowerShell-cmdlet'en importerer .csv-filen og piper den til en løkke i krøllede parenteser, der læser den første linje i filen som kolonneoverskrifter. PowerShell-cmdlet'en gentager derefter de resterende poster, opretter en ny gruppe af websteder for hver post og tildeler egenskaber for gruppen af websteder i henhold til kolonneoverskrifterne.

### <a name="create-a-csv-file"></a>Opret en .csv fil

> [!NOTE]
> Ressourcekvotaparameteren fungerer kun på klassiske websteder. Hvis du bruger denne parameter på et moderne websted, får du muligvis vist en advarsel om, at den er blevet frarådet.

1. Åbn Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Hvor *lejeren* er navnet på din lejer, og *ejeren* er brugernavnet på den bruger i din lejer, som du vil tildele rollen som primær administrator af gruppen af websteder.

   Du kan trykke på Ctrl+H, når du bruger Notesblok til at masse erstatte hurtigere.

2. Gem filen på skrivebordet som **SiteCollections.csv**.

> [!TIP]
> Før du bruger denne eller andre .csv- eller Windows PowerShell scriptfil, er det en god idé at sikre, at der ikke er overflødige tegn eller tegn, der ikke udskrives. Åbn filen i Word, og klik på afsnitsikonet på båndet for at få vist tegn, der ikke udskrives. Der må ikke være nogen tegn, der ikke udskrives. Der må f.eks. ikke være nogen afsnitsmærker ud over det sidste i slutningen af filen.

### <a name="run-the-windows-powershell-command"></a>Kør kommandoen Windows PowerShell

1. I prompten Windows PowerShell skal du skrive eller kopiere og indsætte følgende kommando og trykke på Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Hvor *MyAlias* er lig med dit brugeralias.

2. Vent på, at Windows PowerShell bliver bedt om at blive vist igen. Det kan tage et minut eller to.

3. I prompten Windows PowerShell skal du skrive eller kopiere og indsætte følgende cmdlet og trykke på Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Bemærk de nye grupper af websteder på listen. Ved hjælp af vores eksempel på en CSV-fil kan du se følgende grupper af websteder: **TeamSite01**, **Blog01**, **Project01** og **Community01**

Det var det hele. Du har oprettet flere grupper af websteder ved hjælp af den .csv fil, du har oprettet, og en enkelt Windows PowerShell kommando. Du er nu klar til at oprette og tildele brugere til disse websteder.

## <a name="step-2-add-users-and-groups"></a>Trin 2: Tilføj brugere og grupper

Nu skal du oprette brugere og føje dem til en gruppe af websteder. Du skal derefter bruge en .csv fil til masseupload af nye grupper og brugere.

Følgende procedurer fortsætter med at bruge eksempelwebstederne TeamSite01, Blog01, Project01 og Community01.

### <a name="create-csv-and-ps1-files"></a>Opret .csv- og .ps1-filer

1. Åbn Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Site,Group,PermissionLevels
   https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
   https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
   https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
   https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
   ```

   Hvor *lejeren* er lig med dit lejernavn.

2. Gem filen på skrivebordet som **GroupsAndPermissions.csv**.

3. Åbn en ny forekomst af Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Group,LoginName,Site
   Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
   ```

   Hvor *lejeren* er lig med dit lejernavn, og *brugernavn* er lig med brugernavnet for en eksisterende bruger.

4. Gem filen på skrivebordet som **Users.csv**.

5. Åbn en ny forekomst af Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Hvor MyAlias er lig med brugernavnet på den bruger, der i øjeblikket er logget på.

6. Gem filen på skrivebordet som **UsersAndGroups.ps1**. Dette er et simpelt Windows PowerShell script.

Du er nu klar til at køre UsersAndGroup.ps1 scriptet for at føje brugere og grupper til flere grupper af websteder.

### <a name="run-usersandgroupsps1-script"></a>Kør UsersAndGroups.ps1 script

1. Vend tilbage til SharePoint Online Management Shell.

2. I prompten Windows PowerShell skal du skrive eller kopiere og indsætte følgende linje og trykke på Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. Tryk på **Y** i bekræftelsesprompten.

4. I prompten Windows PowerShell skal du skrive eller kopiere og indsætte følgende og trykke på Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Hvor *MyAlias* er lig med dit brugernavn.

5. Vent på, at prompten vender tilbage, før du går videre. Du får først vist grupperne, når de oprettes. Derefter kan du se gruppelisten gentaget, efterhånden som brugerne tilføjes.

## <a name="see-also"></a>Se også

[Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Administrer SharePoint onlinewebstedsgrupper med PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
