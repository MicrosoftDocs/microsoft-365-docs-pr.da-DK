---
title: Oprette, rapportere om og slette flere indholdssøgninger
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
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: Få mere at vide om, hvordan du automatiserer opgaver med indholdssøgning, f.eks. oprettelse af søgninger og kørsel af rapporter ved & Security & Compliance Center PowerShell.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 602997114c46a68be13182a504d0b123e98d2be2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589108"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Oprette, rapportere om og slette flere indholdssøgninger

 Hurtig oprettelse og rapportering af discovery-søgninger er ofte et vigtigt trin i eDiscovery og undersøgelser, når du forsøger at lære om de underliggende data samt den omfattende og kvalitet af dine søgninger. Som en hjælp til at gøre dette tilbyder Security & Compliance Center PowerShell et sæt cmdlet'er til at automatisere tidskrævende opgaver med indholdssøgning. Disse scripts er en hurtig og nem måde at oprette et antal søgninger på og derefter køre rapporter over de anslåede søgeresultater, som kan hjælpe dig med at bestemme mængden af data, der er tale om. Du kan også bruge scripts til at oprette forskellige versioner af søgninger for at sammenligne de resultater, der er resultatet af hvert enkelt resultat. Disse scripts kan hjælpe dig med hurtigt og effektivt at identificere og annullere dine data.

## <a name="before-you-create-a-content-search"></a>Før du opretter en indholdssøgning

- Du skal være medlem af rollegruppen eDiscovery Manager i gruppen Microsoft 365 Overholdelsescenter at køre de scripts, der er beskrevet i dette emne.

- Hvis du vil indsamle en liste over URL-adresserne for OneDrive for Business-websteder i organisationen, som du kan føje til CSV-filen i trin 1, skal du se Opret en liste [over alle OneDrive-placeringer i organisationen](/onedrive/list-onedrive-urls).

- Sørg for at gemme alle de filer, du opretter i dette emne, i den samme mappe. Det gør det nemmere at køre scripterne.

- Scriptene omfatter minimal fejlhåndtering. Deres primære formål er hurtigt at oprette, rapportere om og slette flere indholdssøgninger.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptene leveres som de er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscripts og dokumentation forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>Trin 1: Opret en CSV-fil, der indeholder oplysninger om de søgninger, du vil køre

CSV-filen (kommaseparerede værdier), som du opretter i dette trin, indeholder en række for hver bruger, du vil søge efter. Du kan søge i brugerens Exchange Online (som omfatter arkivpostkassen, hvis den er aktiveret), og dennes OneDrive for Business websted. Eller du kan søge i postkassen eller OneDrive for Business websted. Du kan også søge på et hvilket som helst websted i SharePoint Online-organisation. Det script, du kører i trin 3, opretter en separat søgning for hver række i CSV-filen.

1. Kopiér og indsæt følgende tekst i en .txt fil ved hjælp af Notesblok. Gem denne fil i en mappe på din lokale computer. Du skal også gemme de andre scripts i denne mappe.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Den første række (eller kolonneoverskriften) i filen viser de parametre, der skal bruges af **cmdlet'en New-ComplianceSearch** (i scriptet i trin 3) til at oprette en ny indholdssøgning. Hvert parameternavn er adskilt af et komma. Sørg for, at der ikke er nogen mellemrum i kolonneoverskriften. Hver række under kolonneoverskriften repræsenterer parameterværdierne for hver søgning. Sørg for at erstatte pladsholderdataene i CSV-filen med dine faktiske data.

2. Åbn filen .txt i Excel, og brug derefter oplysningerne i følgende tabel til at redigere filen med oplysninger for hver søgning.

   ****

   |Parameter|Beskrivelse|
   |---|---|
   |`ExchangeLocation`|SMTP-adressen på brugerens postkasse.|
   |`SharePointLocation`|URL-adressen til brugerens websted OneDrive for Business URL-adressen for et websted i organisationen. For URL-adressen til OneDrive for Business skal du bruge dette format: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. F.eks.  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|Søgeforespørgslen til søgningen. Hvis du vil have mere at vide om at oprette en [søgeforespørgsel, skal du se Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).|
   |`StartDate`|For mails: Datoen på eller efter, at en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter på SharePoint eller OneDrive for Business websteder skal datoen på eller efter dokumentet sidst blev ændret.|
   |`EndDate`|For mails er datoen på eller før en meddelelse sendt af en sendt af brugeren. For dokumenter på SharePoint eller OneDrive for Business websteder skal datoen på eller før dokumentet sidst blev ændret.|
   |

3. Gem filen Excel en CSV-fil i en mappe på din lokale computer. Det script, du opretter i trin 3, bruger oplysningerne i denne CSV-fil til at oprette søgninger.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>Trin 2: Forbind til Security & Compliance Center PowerShell

Næste trin er at oprette forbindelse til Security & Compliance Center For din organisation. Du kan finde en trinvis vejledning under [Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>Trin 3: Kør scriptet for at oprette og starte søgninger

Scriptet i dette trin opretter en separat indholdssøgning for hver række i CSV-filen, du oprettede i trin 1. Når du kører dette script, bliver du bedt om to værdier:

- **Søgegruppe-id** – Dette navn gør det nemt at organisere de søgninger, der oprettes ud fra CSV-filen. Hver søgning, der oprettes, navngives med id'et for søgegruppen, og derefter føjes et tal til søgenavnet. Hvis du f.eks. angiver **ContosoCase** for søgegruppens id, så kaldes søgninger for **ContosoCase_1**, **ContosoCase_2**, **ContosoCase_3** osv. Bemærk, at der er store og små bogstaver i det navn, du skriver. Når du bruger søgegruppe-id'et i trin 4 og trin 5, skal du bruge den samme sag, som du gjorde, da du oprettede den.

- **CSV-fil** – Navnet på den CSV-fil, du oprettede i trin 1. Sørg for at medtage brugen af det fulde filnavn, medtag .csv filtypenavnet; f.eks.  `ContosoCase.csv`.

Sådan kører du scriptet:

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `CreateSearches.ps1`. Gem filen i den samme mappe, hvor du gemte de andre filer.

   ```Powershell
   # Get the Search Group ID and the location of the CSV input file
   $searchGroup = Read-Host 'Search Group ID'
   $csvFile = Read-Host 'Source CSV file'

   # Do a quick check to make sure our group name will not collide with other searches
   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    $searchName = $searchGroup +'_' + $searchCounter
    $search = Get-ComplianceSearch $searchName -EA SilentlyContinue
    if ($search)
    {
       Write-Error "The Search Group ID conflicts with existing searches.  Please choose a search group name and restart the script."
       return
    }
    $searchCounter++
   }

   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    # Create the query
    $query = $_.ContentMatchQuery
    if(($_.StartDate -or $_.EndDate))
    {
          # Add the appropriate date restrictions.  NOTE: Using the Date condition property here because it works across Exchange, SharePoint, and OneDrive for Business.
          # For Exchange, the Date condition property maps to the Sent and Received dates; for SharePoint and OneDrive for Business, it maps to Created and Modified dates.
          if($query)
          {
              $query += " AND"
          }
          $query += " ("
          if($_.StartDate)
          {
              $query += "Date >= " + $_.StartDate
          }
          if($_.EndDate)
          {
              if($_.StartDate)
              {
                  $query += " AND "
              }
              $query += "Date <= " + $_.EndDate
          }
          $query += ")"
    }

     # -ExchangeLocation can't be set to an empty string, set to null if there's no location.
     $exchangeLocation = $null
     if ( $_.ExchangeLocation)
     {
           $exchangeLocation = $_.ExchangeLocation
     }

    # Create and run the search
    $searchName = $searchGroup +'_' + $searchCounter
    Write-Host "Creating and running search: " $searchName -NoNewline
    $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $exchangeLocation -SharePointLocation $_.SharePointLocation -ContentMatchQuery $query

    # Start and wait for each search to complete
    Start-ComplianceSearch $search.Name
    while ((Get-ComplianceSearch $search.Name).Status -ne "Completed")
    {
       Write-Host " ." -NoNewline
       Start-Sleep -s 3
    }
    Write-Host ""

    $searchCounter++
   }
   ```

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. Skriv navnet **på en søgegruppe** ved prompten Søgegruppe-id, og tryk derefter på **Enter**. f.eks.  `ContosoCase`. Husk, at der er tale om store og små bogstaver i dette navn, så du skal skrive det på samme måde i efterfølgende trin.

4. Ved **prompten Kilde-CSV-fil** skal du skrive navnet på CSV-filen, .csv filtypenavnet. f.eks.  `ContosoCase.csv`.

5. Tryk **på Enter** for at fortsætte med at køre scriptet.

   Scriptet viser status for oprettelse og kørsel af søgninger. Når scriptet er færdigt, vender det tilbage til prompten.

   ![Eksempel på output fra at køre scriptet til at oprette flere kompatibilitetssøgninger.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>Trin 4: Kør scriptet for at rapportere de anslåede søgninger

Når du har oprettet søgninger, er næste trin at køre et script, der viser en simpel rapport over antallet af søgehits for hver søgning, der blev oprettet i trin 3. Rapporten indeholder også størrelsen på resultaterne for hver søgning, det samlede antal besøg og den samlede størrelse af alle søgninger. Når du kører rapporteringsscriptet, bliver du bedt om at angive dit søgegruppe-id og et CSV-filnavn, hvis du vil gemme rapporten i en CSV-fil.

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `SearchReport.ps1`. Gem filen i den samme mappe, hvor du gemte de andre filer.

   ```Powershell
   $searchGroup = Read-Host 'Search Group ID'
   $outputFile = Read-Host 'Enter a file name or file path to save the report to a .csv file. Leave blank to only display the report'
   $searches = Get-ComplianceSearch | ?{$_.Name -clike $searchGroup + "_*"}
   $allSearchStats = @()
   foreach ($partialObj in $searches)
   {
      $search = Get-ComplianceSearch $partialObj.Name
      $sizeMB = [System.Math]::Round($search.Size / 1MB, 2)
      $searchStatus = $search.Status
      if($search.Errors)
      {
          $searchStatus = "Failed"
      }elseif($search.NumFailedSources -gt 0)
      {
          $searchStatus = "Failed Sources"
      }
      $searchStats = New-Object PSObject
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Name -Value $search.Name
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name ContentMatchQuery -Value $search.ContentMatchQuery
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Status -Value $searchStatus
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Items -Value $search.Items
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size" -Value $search.Size
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size(MB)" -Value $sizeMB
      $allSearchStats += $searchStats
   }
   # Calculate the totals
   $allItems = ($allSearchStats | Measure-Object Items -Sum).Sum
   # Convert the total size to MB and round to the nearst 100th
   $allSize = ($allSearchStats | Measure-Object 'Size' -Sum).Sum
   $allSizeMB = [System.Math]::Round($allSize  / 1MB, 2)
   # Get the total successful searches and total of all searches
   $allSuccessCount = ($allSearchStats |?{$_.Status -eq "Completed"}).Count
   $allCount = $allSearchStats.Count
   $allStatus = [string]$allSuccessCount + " of " + [string]$allCount
   # Totals Row
   $totalSearchStats = New-Object PSObject
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Name -Value "Total"
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Status -Value $allStatus
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Items -Value $allItems
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name "Size(MB)" -Value $allSizeMB
   $allSearchStats += $totalSearchStats
   # Just get the columns we're interested in showing
   $allSearchStatsPrime = $allSearchStats | Select-Object Name, Status, Items, "Size(MB)", ContentMatchQuery
   # Print the results to the screen
   $allSearchStatsPrime |ft -AutoSize -Wrap
   # Save the results to a CSV file
   if ($outputFile)
   {
      $allSearchStatsPrime | Export-Csv -Path $outputFile -NoTypeInformation
   }
   ```

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\SearchReport.ps1
   ```

3. Skriv navnet **på en søgegruppe** ved prompten Søgegruppe-id, og tryk derefter på **Enter**. for eksempel  `ContosoCase`. Husk, at der er tale om store og små bogstaver i dette navn, så du skal skrive det på samme måde, som du gjorde, da du kørte scriptet i trin 3.

4. På stien Filer for at gemme rapporten i en **CSV-fil (** lad være tom for kun at vise rapporten) skal du skrive et filnavn på hele stien til filnavnet (herunder filtypenavnet .csv), hvis du vil gemme rapporten i en CSV-fil. navnet på CSV-filen, herunder .csv filtypenavnet. Du kan f.eks. skrive  `ContosoCaseReport.csv` for at gemme den i den aktuelle mappe, eller du kan skrive  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` for at gemme den i en anden mappe. Du kan også lade prompten være tom for at få vist rapporten, men ikke gemme den i en fil.

5. Tryk **på Enter**.

   Scriptet viser status for oprettelse og kørsel af søgninger. Når scriptet er færdigt, vises rapporten.

   ![Kør søgerapporten for at få vist estimater for søgegruppen.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Hvis den samme postkasse eller det samme websted er angivet som en indholdsplacering i mere end én søgning i en søgegruppe, kan det samlede resultat i rapporten (for både antallet af elementer og den samlede størrelse) omfatte resultater for de samme elementer. Det skyldes, at den samme mail eller det samme dokument tælles mere end én gang, hvis det svarer til forespørgslen for forskellige søgninger i søgegruppen.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>Trin 5: Kør scriptet for at slette søgninger

Da du muligvis opretter mange søgninger, gør dette sidste script det bare nemt hurtigt at slette de søgninger, du oprettede i trin 3. Ligesom de andre scripts bliver du også bedt om at bruge søgegruppens id. Alle søgninger med søgegruppe-id'et i navnet på søgningen slettes, når du kører dette script.

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `DeleteSearches.ps1`. Gem filen i den samme mappe, hvor du gemte de andre filer.

   ```Powershell
   # Delete all searches in a search group
   $searchGroup = Read-Host 'Search Group ID'
   Get-ComplianceSearch |
      ForEach-Object{
      # If the name matches the search group name pattern (case sensitive), delete the search
      if ($_.Name -cmatch $searchGroup + "_\d+")
      {
          Write-Host "Deleting search: " $_.Name
          Remove-ComplianceSearch $_.Name -Confirm:$false
      }
   }
   ```

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. I **prompten Søgegruppe-id** skal du skrive navnet på en søgegruppe for de søgninger, du vil slette, og derefter trykke på **Enter**. f.eks.  `ContosoCase`. Husk, at der er tale om store og små bogstaver i dette navn, så du skal skrive det på samme måde, som du gjorde, da du kørte scriptet i trin 3.

   Scriptet viser navnet på hver søgning, der er blevet slettet.

   ![Kør scriptet for at slette søgninger i søgegruppen.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
