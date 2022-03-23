---
title: Brug indholdssøgning til målrettede samlinger
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Brug Indholdssøgning i Microsoft 365 Overholdelsescenter til at udføre en målrettet samling, som søger efter elementer i en bestemt postkasse eller webstedsmappe.
ms.openlocfilehash: a72984e3d4363dfd5d89e6167621dd65c9d57653
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63587720"
---
# <a name="use-content-search-for-targeted-collections"></a>Brug indholdssøgning til målrettede samlinger

Værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter er ikke en direkte måde i brugergrænsefladen til at søge i bestemte mapper i Exchange-postkasser eller SharePoint og OneDrive for Business websteder. Det er dog muligt at søge i bestemte mapper (kaldet en målrettet *samling) ved* at angive egenskaben mappe-id for mail eller sti (DocumentLink) for websteder i den faktiske søgeforespørgselssyntaksen. Det er nyttigt at bruge Indholdssøgning til at udføre en målrettet samling, når du er sikker på, at elementer, der reagerer på en sag eller privilegerede elementer, er placeret i en bestemt postkasse eller webstedsmappe. Du kan bruge scriptet i denne artikel til at hente mappe-id'et til postkassemapper eller stien (DocumentLink) til mapper på et SharePoint og OneDrive for Business websted. Derefter kan du bruge mappe-id'et eller stien i en søgeforespørgsel til at returnere elementer, der er placeret i mappen.

> [!NOTE]
> Hvis du vil returnere indhold, der er placeret i en mappe på et SharePoint- eller OneDrive for Business-websted, bruger scriptet i dette emne egenskaben DocumentLink administreret i stedet for egenskaben Sti. Egenskaben DocumentLink er mere robust end egenskaben Sti, da den returnerer alt indhold i en mappe, hvorimod egenskaben Sti ikke returnerer visse mediefiler.

## <a name="before-you-run-a-targeted-collection"></a>Før du kører en målrettet samling

- Du skal være medlem af rollegruppen eDiscovery Manager i gruppen Microsoft 365 Overholdelsescenter at køre scriptet i trin 1. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Du skal også have tildelt rollen Postmodtagere i Exchange Online organisation. Dette er påkrævet for at **køre cmdlet'en Get-MailboxFolderStatistics** , som er inkluderet i scriptet. Som standard tildeles rollen Postmodtagere rollegrupperne Organisationsadministration og Modtageradministration i Exchange Online. Du kan finde flere oplysninger om at tildele tilladelser Exchange Online i [Administrer medlemmer af rollegrupper](/exchange/manage-role-group-members-exchange-2013-help). Du kan også oprette en brugerdefineret rollegruppe, tildele rollen Postmodtagere til den og derefter tilføje de medlemmer, der skal køre scriptet i trin 1. Få mere at vide under [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

- Scriptet i denne artikel understøtter moderne godkendelse. Du kan bruge scriptet, som det er, hvis du er Microsoft 365 eller Microsoft 365 GCC organisation. Hvis du er en Office 365 Germany-organisation, en Microsoft 365 GCC High-organisation eller en Microsoft 365 DoD-organisation, skal du redigere scriptet for at køre det korrekt. Specifikt skal du redigere linjen `Connect-ExchangeOnline` og bruge *ExchangeEnvironmentName-parameteren* (og den relevante værdi for din organisationstype) til at oprette forbindelse til Exchange Online PowerShell.  Du skal også `Connect-IPPSSession` redigere linjen og bruge parametrene *ConnectionUri* og *AzureADAuthorizationEndpointUri* (og de relevante værdier for din organisationstype) til at oprette forbindelse til Security & Compliance Center PowerShell. Du kan finde flere oplysninger i eksemplerne [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) [og Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Hver gang du kører scriptet, oprettes der en ny PowerShell-fjernsession. Det betyder, at du kan bruge alle de eksterne PowerShell-sessioner, der er tilgængelige for dig. For at forhindre dette sker, skal du køre følgende kommando for at afbryde forbindelsen til dine aktive eksterne PowerShell-sessioner.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Du kan finde flere oplysninger [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Scriptet indeholder minimal fejlhåndtering. Det primære formål med scriptet er hurtigt at få vist en liste over postkassemappe-websteder eller webstedsstier, der kan bruges i syntaksen for søgeforespørgslen i en indholdssøgning til at udføre en målrettet samling.

- Eksempelscriptet, der er angivet i dette emne, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Trin 1: Kør scriptet for at få en liste over mapper til en postkasse eller et websted

Det script, du kører i dette første trin, returnerer en liste over postkassemapper eller SharePoint- og OneDrive for Business-mapper og det tilsvarende mappe-id eller sti for hver mappe. Når du kører dette script, bliver du bedt om følgende oplysninger.

- **Url-adresse eller websteds-URL-adresse**: Skriv en mailadresse på den, der skal håndtere postkassen, for at returnere Exchange af postkassemapper og mappe-websteder. Eller skriv URL-adressen til et SharePoint websted eller et OneDrive for Business for at returnere en liste over stier til det angivne websted. Her er nogle eksempler:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive for Business**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Dine brugerlegitimationsoplysninger**: Scriptet bruger dine legitimationsoplysninger til at oprette forbindelse til Exchange Online PowerShell eller Security & Compliance Center PowerShell ved hjælp af moderne godkendelse. Som beskrevet tidligere skal du have tildelt de relevante tilladelser for at kunne køre dette script.

Sådan får du vist en liste over postkassemapper eller navne på webstedsdokumentlink (sti):

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the Microsoft 365 compliance center.            #
   # The script will then:                                            #
   #    * If an email address is supplied: list the folders for the target mailbox.            #
   #    * If a SharePoint or OneDrive for Business site is supplied: list the documentlinks (folder paths) #
   #    * for the site.                                                                                    #
   #    * In both cases, the script supplies the correct search properties (folderid: or documentlink:)    #
   #      appended to the folder ID or documentlink to use in a Content Search.                #
   # Notes:                                                #
   #    * For SharePoint and OneDrive for Business, the paths are searched recursively; this means the     #
   #      the current folder and all sub-folders are searched.                        #
   #    * For Exchange, only the specified folder will be searched; this means sub-folders in the folder    #
   #      will not be searched.  To search sub-folders, you need to use the specify the folder ID for    #
   #      each sub-folder that you want to search.                                #
   #    * For Exchange, only folders in the user's primary mailbox will be returned by the script.        #
   #########################################################################################################
   # Collect the target email address or SharePoint Url
   $addressOrSite = Read-Host "Enter an email address or a URL for a SharePoint or OneDrive for Business site"
   # Authenticate with Exchange Online and the Microsoft 365 compliance center (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline -ShowBanner:$false -CommandName Get-MailboxFolderStatistics
      }
      $folderQueries = @()
      $folderStatistics = Get-MailboxFolderStatistics $emailAddress
      foreach ($folderStatistic in $folderStatistics)
      {
          $folderId = $folderStatistic.FolderId;
          $folderPath = $folderStatistic.FolderPath;
          $encoding= [System.Text.Encoding]::GetEncoding("us-ascii")
          $nibbler= $encoding.GetBytes("0123456789ABCDEF");
          $folderIdBytes = [Convert]::FromBase64String($folderId);
          $indexIdBytes = New-Object byte[] 48;
          $indexIdIdx=0;
          $folderIdBytes | select -skip 23 -First 24 | %{$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -shr 4];$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -band 0xF]}
          $folderQuery = "folderid:$($encoding.GetString($indexIdBytes))";
          $folderStat = New-Object PSObject
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderPath -Value $folderPath
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderQuery -Value $folderQuery
          $folderQueries += $folderStat
      }
      Write-Host "-----Exchange Folders-----"
      $folderQueries |ft
   }
   elseif ($addressOrSite.IndexOf("http") -ige 0)
   {
      $searchName = "SPFoldersSearch"
      $searchActionName = "SPFoldersSearch_Preview"
      # List the folders for the SharePoint or OneDrive for Business Site
      $siteUrl = $addressOrSite
      # Connect to Security & Compliance Center PowerShell
      if (!$SccSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-IPPSSession
      }
      # Clean-up, if the script was aborted, the search we created might not have been deleted.  Try to do so now.
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
      # Create a Content Search against the SharePoint Site or OneDrive for Business site and only search for folders; wait for the search to complete
      $complianceSearch = New-ComplianceSearch -Name $searchName -ContentMatchQuery "contenttype:folder" -SharePointLocation $siteUrl
      Start-ComplianceSearch $searchName
      do{
          Write-host "Waiting for search to complete..."
          Start-Sleep -s 5
          $complianceSearch = Get-ComplianceSearch $searchName
      }while ($complianceSearch.Status -ne 'Completed')
      if ($complianceSearch.Items -gt 0)
      {
          # Create a Compliance Search Action and wait for it to complete. The folders will be listed in the .Results parameter
          $complianceSearchAction = New-ComplianceSearchAction -SearchName $searchName -Preview
          do
          {
              Write-host "Waiting for search action to complete..."
              Start-Sleep -s 5
              $complianceSearchAction = Get-ComplianceSearchAction $searchActionName
          }while ($complianceSearchAction.Status -ne 'Completed')
          # Get the results and print out the folders
          $results = $complianceSearchAction.Results
          $matches = Select-String "Data Link:.+[,}]" -Input $results -AllMatches
          foreach ($match in $matches.Matches)
          {
              $rawUrl = $match.Value
              $rawUrl = $rawUrl -replace "Data Link: " -replace "," -replace "}"
              Write-Host "DocumentLink:""$rawUrl"""
          }
      }
      else
      {
          Write-Host "No folders were found for $siteUrl"
      }
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
   }
   else
   {
      Write-Error "Couldn't recognize $addressOrSite as an email address or a site URL"
   }
   ```

2. Åbn Scriptet på din lokale Windows PowerShell og gå til den mappe, hvor du gemte scriptet.

3. Kør scriptet. for eksempel:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Angiv de oplysninger, som scriptet beder dig om.

    Scriptet viser en liste over postkassemapper eller webstedsmapper for den angivne bruger. Lad dette vindue være åbent, så du kan kopiere et mappe-id eller et dokumentlinknavn og indsætte det i en søgeforespørgsel i trin 2.

    > [!TIP]
    > I stedet for at vise en liste over mapper på computerskærmen kan du dirigere outputtet fra scriptet til en tekstfil igen. Denne fil gemmes i den mappe, hvor scriptet er placeret. Hvis du f.eks. vil omdirigere scriptoutput til en tekstfil, skal du køre følgende kommando i trin 3:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Derefter kan du kopiere et mappe-id eller et dokumentlink fra filen til brug i en søgeforespørgsel.

### <a name="script-output-for-mailbox-folders"></a>Scriptoutput for postkassemapper

Hvis du får postkassemappe-id'er, opretter scriptet forbindelse til Exchange Online PowerShell, kører **Get-MailboxFolderStatisics-cmdlet'en** og viser derefter listen over mapperne fra den angivne postkasse. For hver mappe i postkassen viser scriptet navnet på mappen i kolonnen **FolderPath** og mappe-id'et i **kolonnen FolderQuery** . Desuden føjer scriptet præfikset **folderId** (som er navnet på postkasseegenskaben) til mappe-id'et. Da **egenskaben folderid** er en søgbar egenskab,  `folderid:<folderid>` skal du bruge den i en søgeforespørgsel i trin 2 til at søge i den pågældende mappe. 

> [!IMPORTANT]
> Scriptet i denne artikel indeholder kodningslogik, der konverterer id-værdierne for mappen 64-tegn, der returneres af **Get-MailboxFolderStatistics** , til det samme 48-tegns format, der er indekseret til søgning. Hvis du lige kører **cmdlet'en Get-MailboxFolderStatistics** i PowerShell for at få et mappe-id (i stedet for at køre scriptet i denne artikel), vil en søgeforespørgsel, der bruger denne mappe-id-værdi, mislykkes. Du skal køre scriptet for at få de korrekt formaterede mappe-id'er, der kan bruges i en indholdssøgning.

Her er et eksempel på det output, der returneres af scriptet for postkassemapper.

![Eksempel på listen over postkassemapper og mappe-i-filer, der returneres af scriptet.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

Eksemplet i trin 2 viser den forespørgsel, der bruges til at søge i undermappen Fjernet i brugerens mappe med genoprettelige elementer.

### <a name="script-output-for-site-folders"></a>Scriptoutput for webstedsmapper

Hvis du får stien til egenskaben **documentlink** fra SharePoint- eller OneDrive for Business-websteder, opretter scriptet forbindelse til Security & Compliance PowerShell, opretter en ny indholdssøgning, der søger efter mapper på webstedet, og viser derefter en liste over de mapper, der er placeret på det angivne websted. Scriptet viser navnet på hver mappe og tilføjer præfikset **dokumentlink** til mappens URL-adresse. Da **documentlink-egenskaben** er en søgbar egenskab, `documentlink:<path>` skal du bruge egenskab:værdi-par i en søgeforespørgsel i trin 2 til at søge i den pågældende mappe. Scriptet viser maksimalt 100 webstedsmapper. Hvis der er mere end 100 webstedsmapper, vises de nyeste.

Her er et eksempel på det output, der returneres af scriptet for webstedsmapper.

![Eksempel på listen over documentlink-navne for webstedsmapper, der returneres af scriptet.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Trin 2: Brug et mappe-id eller et dokumentlink til at udføre en målrettet samling

Når du har kørt scriptet for at indsamle en liste over mappe-id'er eller dokumentlinks for en bestemt bruger, skal du gå til Microsoft 365 Overholdelsescenter og oprette en ny indholdssøgning for at søge i en bestemt mappe. `folderid:<folderid>` `documentlink:<path>` Du skal bruge parret property:value i søgeforespørgslen, som du konfigurerer i feltet nøgleordet Indholdssøgning (eller som værdien for *ContentMatchQuery-parameteren*, hvis du bruger **New-ComplianceSearch-cmdlet'en**). Du kan kombinere egenskaben  `folderid` med  `documentlink` andre søgeparametre eller søgebetingelser. Hvis du kun medtager  `folderid` egenskaben eller  `documentlink` egenskaben i forespørgslen, returnerer søgningen alle elementer, der er placeret i den angivne mappe.

1. Gå til <https://compliance.microsoft.com> og log på med den konto og de legitimationsoplysninger, du brugte til at køre scriptet i trin 1.

2. I venstre rude i Overholdelsescenter skal du klikke på **Vis** **allContent-søgning** >  og derefter klikke på **Ny søgning**.

3. I feltet **Nøgleord skal** du indsætte den eller `folderid:<folderid>` den  `documentlink:<path>/*` værdi, der blev returneret af scriptet i trin 1.

    For eksempel søger forespørgslen i følgende skærmbillede efter et element i undermappen Fjernet i brugerens mappe genoprettelige elementer ( `folderid` værdien af egenskaben for undermappen Fjernet vises i skærmbilledet i trin 1):

    ![Indsæt mappe-id'et eller dokumentlinket i søgeforespørgslens nøgleordsfelt.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > søgninger i dokumentlinks kræver brug af en efterstillet  `asterisk '/*'`.  

4. Under **Placeringer skal** du vælge **Bestemte placeringer og** derefter klikke på **Rediger**.

5. Gør et af følgende, afhængigt af om du søger i en postkassemappe eller en webstedsmappe:

    - Ud for **Exchange skal** du klikke på Vælg brugere **,** grupper eller teams og derefter tilføje den samme postkasse, som du angav, da du kørte scriptet i trin 1.

      Eller

    - Ud for **SharePoint skal** du klikke på Vælg websteder  og derefter tilføje den samme URL-adresse til webstedet, som du angav, da du kørte scriptet i trin 1.

6. Når du har gemt den indholdsplacering, du vil søge efter, skal du klikke på **Gem &** kørsel, skrive et navn på indholdssøgningen og derefter klikke på Gem for at starte den målrettede søgning i samlingen.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Eksempler på søgeforespørgsler til målrettede samlinger

Her er nogle eksempler på brug af og egenskaber  `folderid` i  `documentlink` en søgeforespørgsel til at udføre en målrettet samling. Pladsholdere bruges til og for  `folderid:<folderid>`  `documentlink:<path>` at spare plads.

- I dette eksempel søges der i tre forskellige postkassemapper. Du kan bruge en lignende forespørgselssyntaksen til at søge i de skjulte mapper i en brugers mappe Genoprettelige elementer.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- I dette eksempel søges der i en postkassemappe efter elementer, der indeholder et bestemt udtryk.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- I dette eksempel søges der i en webstedsmappe (og eventuelle undermapper) efter dokumenter, der indeholder bogstaverne "NDA" i titlen.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- I dette eksempel søges der i en webstedsmappe (og en undermappe) efter dokumenter, der er blevet ændret inden for et datointerval.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Flere oplysninger

Husk følgende, når du bruger scriptet i denne artikel til at udføre målrettede samlinger.

- Scriptet fjerner ikke nogen mapper fra resultaterne. Derfor kan nogle mapper, der vises i resultaterne, være ikke søgbare (eller returnere nul elementer), fordi de indeholder systemgenereret indhold, eller fordi de kun indeholder undermapper og ikke postkasseelementer.

- Dette script returnerer kun mappeoplysninger for brugerens primære postkasse. Den returnerer ikke oplysninger om mapper i brugerens arkivpostkasse. Hvis du vil returnere oplysninger om mapper i brugerens arkivpostkasse, kan du redigere manuskriptet. Det gør du ved at ændre linjen `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` til `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` og derefter gemme og køre det redigerede script. Denne ændring returnerer mappe-id'erne til mapper og undermapper i brugerens arkivpostkasse. Hvis du vil søge i hele arkivpostkassen, kan du forbinde alle mappe-id-egenskab:værdipar med en `OR` operator i en søgeforespørgsel.

- Når du søger i postkassemapper, søges der kun i den angivne mappe ( `folderid` identificeres ved hjælp af dens egenskab). Der søges ikke i undermapper. Hvis du vil søge i undermapper, skal du bruge mappe-id'et for den undermappe, du vil søge i.

- Når du søger i webstedsmapper, søges der i mappen `documentlink` (identificeres ved hjælp af dens egenskab) og alle undermapper.

- Når du `folderid` eksporterer resultaterne af en søgning, hvor du kun har angivet egenskaben i søgeforespørgslen, kan du vælge den første eksportindstilling, "Alle elementer, undtagen dem, der har et ukendt format, krypteres eller blev ikke indekseret af andre årsager." Alle elementer i mappen eksporteres altid, uanset deres indekseringsstatus, da mappe-id'et altid er indekseret.
