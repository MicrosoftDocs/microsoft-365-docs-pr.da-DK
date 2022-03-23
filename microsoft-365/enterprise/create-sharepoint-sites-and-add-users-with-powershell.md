---
title: Opret SharePoint Online-websteder, og tilføj brugere med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Brug PowerShell til at oprette nye SharePoint Online-websteder og derefter føje brugere og grupper til disse websteder.'
ms.openlocfilehash: 76411621c0c313a31e4c92417b4472d6fd34ddac
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591359"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>Opret SharePoint Online-websteder, og tilføj brugere med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Når du bruger PowerShell til Microsoft 365 til at oprette SharePoint Online-websteder og tilføje brugere, kan du hurtigt og gentagne gange udføre opgaver meget hurtigere end i Microsoft 365 Administration. Du kan også udføre opgaver, der ikke er mulige at udføre i Microsoft 365 Administration.

## <a name="connect-to-sharepoint-online"></a>Forbind til SharePoint Online

Fremgangsmåderne i dette emne kræver, at du opretter forbindelse til SharePoint Online. Du kan finde en [vejledning Forbind at SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>Trin 1: Opret nye grupper af websteder ved hjælp af PowerShell

Opret flere websteder ved hjælp af PowerShell, .csv en fil, du opretter, ved hjælp af den angivne eksempelkode og Notesblok. I denne fremgangsmåde skal du erstatte de pladsholderoplysninger, der vises i kantede parenteser, med dine egne websteds- og lejerspecifikke oplysninger. Med denne proces kan du oprette en enkelt fil og køre en enkelt PowerShell-kommando, der bruger den pågældende fil. Dette gør de handlinger, der er taget både gentages og bærbare, og eliminerer mange, hvis ikke alle, fejl, der kan komme fra at skrive lange kommandoer i SharePoint Online Management Shell. Denne procedure har to dele. Først skal du oprette en .csv-fil, og derefter skal du referere til den .csv-fil ved hjælp af PowerShell, som skal bruge indholdet til at oprette webstederne.

PowerShell-cmdletten importerer .csv-filen og rør den til en løkke i de krøllede parenteser, der læser den første linje i filen som kolonneoverskrifter. PowerShell-cmdletten gennemgår derefter de resterende poster, opretter en ny gruppe af websteder for hver post og tildeler egenskaber for gruppen af websteder i henhold til kolonneoverskrifterne.

### <a name="create-a-csv-file"></a>Oprette en .csv fil

> [!NOTE]
> Ressourcekvoteparameteren fungerer kun på klassiske websteder. Hvis du bruger denne parameter på et moderne websted, får du muligvis en advarsel om, at den er blevet udskrevet.

1. Åbn Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Hvor *lejer* er navnet på din lejer, og ejeren  er brugernavnet på den bruger i din lejer, som du vil tildele rollen som primær administrator for gruppen af websteder.

   (Du kan trykke på Ctrl+H, når du bruger Notesblok til at erstatte flere filer hurtigere).

2. Gem filen på skrivebordet som **SiteCollections.csv**.

> [!TIP]
> Før du bruger denne eller andre .csv eller Windows PowerShell scriptfil, er det en god ide at sikre, at der ikke er overflødige tegn eller tegn, der ikke udskrives. Åbn filen i Word, og klik på afsnitsikonet på båndet for at få vist tegn, som ikke udskrives. Der må ikke være overflødige tegn, der ikke udskrives. Eksempelvis bør der ikke være nogen afsnitstegn ud over det sidste i slutningen af filen.

### <a name="run-the-windows-powershell-command"></a>Kør Windows PowerShell kommando

1. Når du Windows PowerShell, skal du skrive eller kopiere og indsætte følgende kommando og trykke på Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Hvor *MyAlias er* lig med dit brugeralias.

2. Vent på, Windows PowerShell bliver bedt om at komme igen. Det kan tage et par minutter.

3. Når du Windows PowerShell, skal du skrive eller kopiere og indsætte følgende cmdlet og trykke på Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Bemærk de nye grupper af websteder på listen. Ved hjælp af vores eksempel-CSV-fil får du vist følgende grupper af websteder: **TeamWebsted01**, **Blog01**, **Project01** og **Community01**

Det var det. Du har oprettet flere grupper af websteder ved hjælp af den .csv fil, du har oprettet, og en enkelt Windows PowerShell kommando. Du er nu klar til at oprette og tildele brugere til disse websteder.

## <a name="step-2-add-users-and-groups"></a>Trin 2: Tilføj brugere og grupper

Nu skal du oprette brugere og føje dem til en gruppe af websteder. Du skal derefter bruge en .csv til at masseuploade nye grupper og brugere.

Følgende procedurer fortsætter med at bruge eksempelwebstederne TeamWebsted01, Blog01, Project01 og Community01.

### <a name="create-csv-and-ps1-files"></a>Oprette .csv og .ps1 filer

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

   Hvor *lejer er* lig med navnet på din lejer.

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

   Hvor *lejeren* er lig med dit lejernavn, *og* brugernavnet er lig med brugernavnet for en eksisterende bruger.

4. Gem filen på skrivebordet som **Users.csv**.

5. Åbn en ny forekomst af Notesblok, og indsæt følgende tekstblok i den:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Hvor MyAlias er lig med brugernavnet for den bruger, der aktuelt er logget på.

6. Gem filen på skrivebordet som **UsersAndGroups.ps1**. Dette er et simpelt Windows PowerShell script.

Du er nu klar til at køre scriptet UsersAndGroup.ps1 at føje brugere og grupper til flere grupper af websteder.

### <a name="run-usersandgroupsps1-script"></a>Kør UsersAndGroups.ps1 script

1. Gå tilbage til SharePoint Online Management Shell.

2. Når du Windows PowerShell, skal du skrive eller kopiere og indsætte følgende linje og trykke på Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. Tryk på Y, når du bliver **bedt om at bekræfte.**

4. Når du Windows PowerShell, skal du skrive eller kopiere og indsætte følgende og trykke på Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Hvor *MyAlias* er lig med dit brugernavn.

5. Vent på, at du bliver bedt om at vende tilbage, før du går videre. Du får først vist grupperne, efterhånden som de oprettes. Derefter vises gruppelisten gentaget, efterhånden som brugere tilføjes.

## <a name="see-also"></a>Se også

[Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Administrer SharePoint onlinewebstedsgrupper med PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
