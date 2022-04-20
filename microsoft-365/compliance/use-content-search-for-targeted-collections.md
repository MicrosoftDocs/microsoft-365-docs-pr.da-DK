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
description: Brug Indholdssøgning på Microsoft Purview-overholdelsesportalen til at udføre en målrettet samling, som søger efter elementer i en bestemt postkasse eller webstedsmappe.
ms.openlocfilehash: b01197ebc942b13f1b3806d2ad3b5a564b609098
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947049"
---
# <a name="use-content-search-for-targeted-collections"></a>Brug indholdssøgning til målrettede samlinger

Indholdssøgeværktøjet på Microsoft Purview-overholdelsesportalen giver ikke en direkte måde i brugergrænsefladen at søge i bestemte mapper i Exchange postkasser eller SharePoint og OneDrive for Business websteder. Det er dog muligt at søge i bestemte mapper (kaldet en *målrettet samling*) ved at angive egenskaben mappe-id for mail- eller stiegenskaben (DocumentLink) for websteder i den faktiske søgeforespørgselssyntaks. Brug af indholdssøgning til at udføre en målrettet samling er nyttigt, når du er sikker på, at elementer, der svarer til en sag eller privilegerede elementer, er placeret i en bestemt postkasse eller webstedsmappe. Du kan bruge scriptet i denne artikel til at hente mappe-id'et for postkassemapper eller stien (DocumentLink) til mapper på et SharePoint og OneDrive for Business websted. Derefter kan du bruge mappe-id'et eller stien i en søgeforespørgsel til at returnere elementer, der er placeret i mappen.

> [!NOTE]
> Hvis du vil returnere indhold, der er placeret i en mappe på et SharePoint eller OneDrive for Business websted, bruger scriptet i dette emne den administrerede egenskab DocumentLink i stedet for egenskaben Path. Egenskaben DocumentLink er mere robust end egenskaben Path, fordi den returnerer alt indhold i en mappe, mens egenskaben Path ikke returnerer nogle mediefiler.

## <a name="before-you-run-a-targeted-collection"></a>Før du kører en målrettet samling

- Du skal være medlem af rollegruppen eDiscovery Manager på overholdelsesportalen for at køre scriptet i trin 1. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

- Du skal også have tildelt rollen Mailmodtagere i din Exchange Online organisation. Dette er påkrævet for at køre cmdlet'en **Get-MailboxFolderStatistics** , som er inkluderet i scriptet. Rollen Mailmodtagere tildeles som standard til rollegrupperne Administration af organisation og Modtageradministration i Exchange Online. Du kan få flere oplysninger om tildeling af tilladelser i Exchange Online under [Administrer medlemmer af rollegruppen](/exchange/manage-role-group-members-exchange-2013-help). Du kan også oprette en brugerdefineret rollegruppe, tildele rollen Mailmodtagere til den og derefter tilføje de medlemmer, der skal køre scriptet i trin 1. Du kan få flere oplysninger under [Administrer rollegrupper](/Exchange/permissions-exo/role-groups).

- Scriptet i denne artikel understøtter moderne godkendelse. Du kan bruge scriptet, som det er, hvis du er en Microsoft 365 eller en Microsoft 365 GCC organisation. Hvis du er en Office 365 Germany-organisation, en Microsoft 365 GCC High-organisation eller en Microsoft 365 DoD-organisation, skal du redigere scriptet for at kunne køre det. Du skal specifikt redigere linjen `Connect-ExchangeOnline` og bruge parameteren *ExchangeEnvironmentName* (og den relevante værdi for din organisationstype) til at oprette forbindelse til Exchange Online PowerShell.  Du skal også redigere linjen `Connect-IPPSSession` og bruge parametrene *ConnectionUri* og *AzureADAuthorizationEndpointUri* (og de relevante værdier for din organisationstype) til at oprette forbindelse til Security & Compliance Center PowerShell. Du kan få flere oplysninger i eksemplerne i [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) og [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Hver gang du kører scriptet, oprettes der en ny ekstern PowerShell-session. Det betyder, at du kan bruge alle de eksterne PowerShell-sessioner, der er tilgængelige for dig. Du kan forhindre, at dette sker, ved at køre følgende kommando for at afbryde forbindelsen til dine aktive PowerShell-fjernsessioner.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Du kan få flere oplysninger under [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Scriptet indeholder minimal fejlhåndtering. Det primære formål med scriptet er hurtigt at få vist en liste over mappe-id'er for postkasser eller webstedsstier, der kan bruges i søgeforespørgslens syntaks i en indholdssøgning til at udføre en målrettet samling.

- Det eksempelscript, der er angivet i dette emne, understøttes ikke i et hvilket som helst Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Trin 1: Kør scriptet for at få en liste over mapper for en postkasse eller et websted

Det script, du kører i dette første trin, returnerer en liste over postkassemapper eller SharePoint og OneDrive for Business mapper samt det tilsvarende mappe-id eller den tilsvarende mappe-sti for hver mappe. Når du kører dette script, bliver du bedt om følgende oplysninger.

- **Mailadresse eller URL-adresse til websted**: Skriv en mailadresse til vogteren for at returnere en liste over Exchange postkassemapper og mappe-id'er. Du kan også skrive URL-adressen til et SharePoint websted eller et OneDrive for Business websted for at returnere en liste over stier for det angivne websted. Her er nogle eksempler:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive for Business**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Dine brugerlegitimationsoplysninger**: Scriptet bruger dine legitimationsoplysninger til at oprette forbindelse til Exchange Online PowerShell eller Security & Compliance Center PowerShell ved hjælp af moderne godkendelse. Som tidligere forklaret, skal du have tildelt de nødvendige tilladelser for at kunne køre dette script.

Sådan får du vist en liste over postkassemapper eller webstedsdokumentlinknavne (sti):

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `GetFolderSearchParameters.ps1`f.eks. .

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the compliance portal.            #
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
   # Authenticate with Exchange Online and the compliance portal (Exchange Online Protection - EOP)
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

2. Åbn Windows PowerShell på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

3. Kør scriptet. f.eks.:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Angiv de oplysninger, som scriptet beder dig om.

    Scriptet viser en liste over postkassemapper eller webstedsmapper for den angivne bruger. Lad dette vindue være åbent, så du kan kopiere et mappe-id eller et dokumentlinknavn og indsætte det i en søgeforespørgsel i trin 2.

    > [!TIP]
    > I stedet for at vise en liste over mapper på computerskærmen kan du sende outputtet fra scriptet til en tekstfil igen. Denne fil gemmes i den mappe, hvor scriptet er placeret. Hvis du f.eks. vil omdirigere scriptoutputtet til en tekstfil, skal du køre følgende kommando i trin 3:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` Derefter kan du kopiere et mappe-id eller et dokumentlink fra filen, der skal bruges i en søgeforespørgsel.

### <a name="script-output-for-mailbox-folders"></a>Scriptoutput til postkassemapper

Hvis du henter mappe-id'er for postkasser, opretter scriptet forbindelse til Exchange Online PowerShell, kører cmdlet'en **Get-MailboxFolderStatisics** og viser derefter listen over mapperne fra den angivne postkasse. For hver mappe i postkassen viser scriptet navnet på mappen i kolonnen **FolderPath** og mappe-id'et i kolonnen **FolderQuery** . Scriptet føjer desuden præfikset **for folderId** (som er navnet på egenskaben for postkassen) til mappe-id'et. Da egenskaben **folderid** er en søgbar egenskab, skal du bruge  `folderid:<folderid>` i en søgeforespørgsel i trin 2 til at søge i den pågældende mappe. 

> [!IMPORTANT]
> Scriptet i denne artikel indeholder kodningslogik, der konverterer de mappe-id-værdier på 64 tegn, der **returneres af Get-MailboxFolderStatistics** , til det samme format på 48 tegn, som er indekseret til søgning. Hvis du bare kører **cmdlet'en Get-MailboxFolderStatistics** i PowerShell for at hente et mappe-id (i stedet for at køre scriptet i denne artikel), mislykkes en søgeforespørgsel, der bruger denne mappe-id-værdi. Du skal køre scriptet for at hente de korrekt formaterede mappe-id'er, der kan bruges i en indholdssøgning.

Her er et eksempel på det output, der returneres af scriptet for postkassemapper.

![Eksempel på listen over postkassemapper og mappe-id'er, der returneres af scriptet.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

I eksemplet i trin 2 vises den forespørgsel, der bruges til at søge i undermappen Renser i brugerens mappe Genoprettelige elementer.

### <a name="script-output-for-site-folders"></a>Scriptoutput til webstedsmapper

Hvis du henter stien til egenskaben **documentlink** fra SharePoint eller OneDrive for Business websteder, opretter scriptet forbindelse til Security & Compliance PowerShell, opretter en ny indholdssøgning, der søger på webstedet efter mapper og derefter viser en liste over de mapper, der er placeret på det angivne websted. Scriptet viser navnet på hver mappe og føjer præfikset for **documentlink** til mappens URL-adresse. Da egenskaben **documentlink** er en søgbar egenskab, skal du bruge `documentlink:<path>` property:value pair i en søgeforespørgsel i Trin 2 til at søge i den pågældende mappe. Scriptet viser maksimalt 100 webstedsmapper. Hvis der er mere end 100 webstedsmapper, vises de nyeste.

Her er et eksempel på det output, der returneres af scriptet for webstedsmapper.

![Eksempel på listen over dokumentlinknavne for webstedsmapper, der returneres af scriptet.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Trin 2: Brug et mappe-id eller et dokumentlink til at udføre en målrettet samling

Når du har kørt scriptet for at indsamle en liste over mappe-id'er eller dokumentlinks for en bestemt bruger, skal du næste trin gå til overholdelsesportalen og oprette en ny indholdssøgning for at søge i en bestemt mappe. Du skal bruge parret  `folderid:<folderid>` eller  `documentlink:<path>` property:value i den søgeforespørgsel, du konfigurerer i nøgleordsfeltet Indholdssøgning (eller som værdien for parameteren  *ContentMatchQuery*  , hvis du bruger cmdlet'en **New-ComplianceSearch** ). Du kan kombinere  `folderid` egenskaben eller  `documentlink` med andre søgeparametre eller søgebetingelser. Hvis du kun medtager  `folderid` egenskaben or  `documentlink` i forespørgslen, returnerer søgningen alle de elementer, der er placeret i den angivne mappe.

1. Gå til , <https://compliance.microsoft.com> og log på med den konto og de legitimationsoplysninger, du brugte til at køre scriptet i trin 1.

2. I venstre rude i overholdelsescenteret skal du klikke på **Vis** **alleIndholdssøgning** >  og derefter klikke på **Ny søgning**.

3. I feltet **Nøgleord** skal du indsætte den `folderid:<folderid>` værdi eller  `documentlink:<path>/*` , der blev returneret af scriptet, i trin 1.

    Forespørgslen på følgende skærmbillede søger f.eks. efter et hvilket som helst element i undermappen Fjern elementer i brugerens mappe Gendanbare elementer (værdien af `folderid` egenskaben for undermappen Renser vises på skærmbilledet i trin 1):

    ![Indsæt mappe-id'et eller dokumentlinket i søgeforespørgslens nøgleordsfelt.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > documentlink-søgninger kræver brug af en efterstillet  `asterisk '/*'`.  

4. Under **Placeringer** skal du vælge **Bestemte placeringer** og derefter klikke på **Rediger**.

5. Gør et af følgende, afhængigt af om du søger i en postkassemappe eller en webstedsmappe:

    - Ud for **Exchange mail** skal du klikke på **Vælg brugere, grupper eller teams** og derefter tilføje den samme postkasse, som du angav, da du kørte scriptet i trin 1.

      Eller

    - Ud for **SharePoint websteder** skal du klikke på **Vælg websteder** og derefter tilføje den samme URL-adresse til webstedet, som du angav, da du kørte scriptet i Trin 1.

6. Når du har gemt indholdsplaceringen til søgning, skal du klikke på **Gem & køre**, skrive et navn til indholdssøgningen og derefter klikke på **Gem** for at starte søgningen efter målrettede samlinger.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Eksempler på søgeforespørgsler for målrettede samlinger

Her er nogle eksempler på, hvordan du bruger  `folderid` egenskaberne og  `documentlink` i en søgeforespørgsel til at udføre en målrettet samling. Pladsholdere bruges til og `documentlink:<path>` til `folderid:<folderid>` at spare plads.

- I dette eksempel søges der i tre forskellige postkassemapper. Du kan bruge lignende forespørgselssyntaks til at søge i de skjulte mapper i en brugers mappe Med genoprettelige elementer.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- I dette eksempel søges der i en postkassemappe efter elementer, der indeholder et nøjagtigt udtryk.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- I dette eksempel søges der i en webstedsmappe (og eventuelle undermapper) efter dokumenter, der indeholder bogstaverne "NDA" i titlen.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- I dette eksempel søges der i en webstedsmappe (og en hvilken som helst undermappe) efter dokumenter, der er ændret inden for et datointerval.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Flere oplysninger

Vær opmærksom på følgende ting, når du bruger scriptet i denne artikel til at udføre målrettede samlinger.

- Scriptet fjerner ikke nogen mapper fra resultaterne. Nogle mapper, der er angivet i resultaterne, kan derfor være usøgelige (eller returnere nul elementer), fordi de indeholder systemoprettede indhold, eller fordi de kun indeholder undermapper og ikke postkasseelementer.

- Dette script returnerer kun mappeoplysninger for brugerens primære postkasse. Den returnerer ikke oplysninger om mapper i brugerens arkivpostkasse. Hvis du vil returnere oplysninger om mapper i brugerens arkivpostkasse, kan du redigere scriptet. Det gør du ved at ændre linjen `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` til `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` og derefter gemme og køre det redigerede script. Denne ændring returnerer mappe-id'erne for mapper og undermapper i brugerens arkivpostkasse. Hvis du vil søge i hele arkivpostkassen, kan du forbinde alle mappe-id-egenskaben:værdipar med en `OR` operator i en søgeforespørgsel.

- Når du søger i postkassemapper, er det kun den angivne mappe (identificeret af dens `folderid` egenskab), der søges i. Der søges ikke i undermapper. Hvis du vil søge i undermapper, skal du bruge mappe-id'et for den undermappe, du vil søge i.

- Når du søger i webstedsmapper, søges der i mappen (identificeret af dens `documentlink` egenskab) og alle undermapper.

- Når du eksporterer resultaterne af en søgning, hvor du kun har angivet `folderid` egenskaben i søgeforespørgslen, kan du vælge den første eksportindstilling: "Alle elementer, bortset fra elementer, der har et ukendt format, krypteres eller ikke er indekseret af andre årsager." Alle elementer i mappen eksporteres altid, uanset deres indekseringsstatus, fordi mappe-id'et altid er indekseret.
