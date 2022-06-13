---
title: Opret, rapportér på, og slet indholdssøgninger
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du automatiserer opgaver til indholdssøgning, f.eks. oprettelse af søgninger og kørsel af rapporter ved hjælp af PowerShell til sikkerhed & overholdelse af angivne standarder.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 50d0a66957e4bdca1e39cb42c837aa0f992bad98
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018069"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>Opret, rapportér om og slet flere indholdssøgninger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

 Hurtig oprettelse og rapportering af registreringssøgninger er ofte et vigtigt skridt i eDiscovery og undersøgelser, når du forsøger at få mere at vide om de underliggende data og dine søgningers rigdom og kvalitet. For at hjælpe dig med at gøre dette tilbyder PowerShell & overholdelse af angivne standarder et sæt cmdlet'er, der kan automatisere tidskrævende opgaver i forbindelse med indholdssøgning. Disse scripts giver en hurtig og nem måde at oprette en række søgninger på og derefter køre rapporter over de anslåede søgeresultater, der kan hjælpe dig med at bestemme mængden af pågældende data. Du kan også bruge scripts til at oprette forskellige versioner af søgninger for at sammenligne de resultater, som hver enkelt producerer. Disse scripts kan hjælpe dig med hurtigt og effektivt at identificere og slagte dine data.

## <a name="before-you-create-a-content-search"></a>Før du opretter en indholdssøgning

- Du skal være medlem af rollegruppen eDiscovery Manager på Microsoft Purview-overholdelsesportalen for at køre de scripts, der er beskrevet i dette emne.

- Hvis du vil indsamle en liste over URL-adresserne for de OneDrive for Business websteder i din organisation, som du kan føje til CSV-filen i Trin 1, skal du se [Opret en liste over alle OneDrive placeringer i din organisation](/onedrive/list-onedrive-urls).

- Sørg for at gemme alle de filer, du opretter i dette emne, i den samme mappe. Det vil gøre det nemmere at køre scripts.

- Scripts omfatter minimal fejlhåndtering. Deres primære formål er hurtigt at oprette, rapportere om og slette flere indholdssøgninger.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i microsofts standardsupportprogram eller -tjeneste. Eksempelscripts leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscripts og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>Trin 1: Opret en CSV-fil, der indeholder oplysninger om de søgninger, du vil køre

Den fil med kommaseparerede værdier (CSV), som du opretter i dette trin, indeholder en række for hver bruger, der vil søge. Du kan søge i brugerens Exchange Online postkasse (herunder arkivpostkassen, hvis den er aktiveret) og vedkommendes OneDrive for Business websted. Du kan også søge i postkassen eller på OneDrive for Business websted. Du kan også søge på et hvilket som helst websted i din SharePoint Online-organisation. Det script, du kører i trin 3, opretter en separat søgning for hver række i CSV-filen.

1. Kopiér og indsæt følgende tekst i en .txt fil ved hjælp af Notesblok. Gem filen i en mappe på din lokale computer. Du skal også gemme de andre scripts i denne mappe.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   Den første række eller kolonneoverskrift i filen viser de parametre, der skal bruges af **New-ComplianceSearch-cmdlet** (i scriptet i trin 3) til at oprette en ny indholdssøgning. Hvert parameternavn er adskilt af et komma. Sørg for, at der ikke er mellemrum i kolonneoverskriften. Hver række under overskriftsrækken repræsenterer parameterværdierne for hver søgning. Sørg for at erstatte pladsholderdataene i CSV-filen med dine faktiske data.

2. Åbn .txt-filen i Excel, og brug derefter oplysningerne i følgende tabel til at redigere filen med oplysninger for hver søgning.

   ****

   |Parameter|Beskrivelse|
   |---|---|
   |`ExchangeLocation`|SMTP-adressen på brugerens postkasse.|
   |`SharePointLocation`|URL-adressen for brugerens OneDrive for Business websted eller URL-adressen for et hvilket som helst websted i din organisation. Til URL-adressen til OneDrive for Business websteder skal du bruge dette format: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. For eksempel  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|Søgeforespørgslen for søgningen. Du kan finde flere oplysninger om oprettelse af en søgeforespørgsel under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).|
   |`StartDate`|I forbindelse med mail er datoen på eller efter, at en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter på SharePoint eller OneDrive for Business websteder, datoen på eller efter, at et dokument sidst blev ændret.|
   |`EndDate`|I forbindelse med mail er datoen på eller før en meddelelse sendt af brugeren. For dokumenter på SharePoint eller OneDrive for Business websteder, datoen på eller før et dokument sidst blev ændret.|
   |

3. Gem Excel-filen som en CSV-fil i en mappe på din lokale computer. Det script, du opretter i trin 3, bruger oplysningerne i denne CSV-fil til at oprette søgninger.

## <a name="step-2-connect-to-security--compliance-powershell"></a>Trin 2: Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder

Det næste trin er at oprette forbindelse til Security & Compliance PowerShell for din organisation. Du kan finde en trinvis vejledning under [Forbind til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>Trin 3: Kør scriptet for at oprette og starte søgninger

Scriptet i dette trin opretter en separat indholdssøgning for hver række i den CSV-fil, du oprettede i trin 1. Når du kører dette script, bliver du bedt om at angive to værdier:

- **Søgegruppe-id** – Dette navn er en nem måde at organisere de søgninger, der oprettes ud fra CSV-filen. Hver søgning, der oprettes, navngives med søgegruppe-id'et, og derefter føjes der et tal til søgenavnet. Hvis du f.eks. angiver **ContosoCase** for søgegruppe-id'et, navngives søgninger **ContosoCase_1**, **ContosoCase_2**, **ContosoCase_3** osv. Bemærk, at der skelnes mellem store og små bogstaver i det navn, du skriver. Når du bruger søgegruppe-id'et i trin 4 og trin 5, skal du bruge den samme sag, som du gjorde, da du oprettede den.

- **CSV-fil** – Navnet på den CSV-fil, du oprettede i trin 1. Sørg for at inkludere brugen af det fulde filnavn, medtag filtypenavnet .csv. f.eks.  `ContosoCase.csv`.

Sådan kører du scriptet:

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `CreateSearches.ps1`f.eks. . Gem filen i den samme mappe, hvor du gemte de andre filer.

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

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i det forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. Skriv navnet på en søgegruppe i prompten **Søgegruppe-id** , og tryk derefter på **Enter**. f.eks.  `ContosoCase`. Husk, at der skelnes mellem store og små bogstaver i dette navn, så du skal skrive det på samme måde i de efterfølgende trin.

4. Skriv navnet på **CSV-filen** ved prompten Kilde CSV, herunder filtypenavnet .csv. f.eks.  `ContosoCase.csv`.

5. Tryk på **Enter** for at fortsætte med at køre scriptet.

   Scriptet viser status for oprettelse og kørsel af søgninger. Når scriptet er fuldført, vender det tilbage til prompten.

   ![Eksempeloutput fra kørsel af scriptet for at oprette flere søgninger i overholdelse af angivne standarder.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>Trin 4: Kør scriptet for at rapportere søgeestimaterne

Når du har oprettet søgninger, er det næste trin at køre et script, der viser en enkel rapport over antallet af søgeresultat for hver søgning, der blev oprettet i trin 3. Rapporten indeholder også størrelsen af resultaterne for hver søgning og det samlede antal forekomster og den samlede størrelse af alle søgninger. Når du kører rapporteringsscriptet, bliver du bedt om at angive søgegruppe-id'et og et CSV-filnavn, hvis du vil gemme rapporten i en CSV-fil.

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `SearchReport.ps1`f.eks. . Gem filen i den samme mappe, hvor du gemte de andre filer.

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

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i det forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\SearchReport.ps1
   ```

3. Skriv navnet på en søgegruppe i prompten **Søgegruppe-id** , og tryk derefter på **Enter**. for eksempel  `ContosoCase`. Husk, at der skelnes mellem store og små bogstaver i dette navn, så du skal skrive det på samme måde, som du gjorde, da du kørte scriptet i trin 3.

4. I prompten **Filsti for at gemme rapporten i en CSV-fil (lad argumentet være tomt for kun at vise rapporten)** skal du skrive et filnavn med den fulde sti til filnavnet (herunder .csv filtypenavn), hvis du vil gemme rapporten i en CSV-fil. navnet på CSV-filen, herunder filtypenavnet .csv. Du kan f.eks. skrive  `ContosoCaseReport.csv` for at gemme den i den aktuelle mappe, eller du kan skrive  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` for at gemme den i en anden mappe. Du kan også lade prompten være tom for at få vist rapporten, men ikke gemme den i en fil.

5. Tryk på **Enter**.

   Scriptet viser status for oprettelse og kørsel af søgninger. Når scriptet er fuldført, vises rapporten.

   ![Kør søgerapporten for at få vist estimaterne for søgegruppen.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> Hvis den samme postkasse eller det samme websted er angivet som en indholdsplacering i mere end én søgning i en søgegruppe, kan det samlede estimat af resultater i rapporten (for både antallet af elementer og den samlede størrelse) indeholde resultater for de samme elementer. Det skyldes, at den samme mail eller det samme dokument tælles mere end én gang, hvis det svarer til forespørgslen for forskellige søgninger i søgegruppen.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>Trin 5: Kør scriptet for at slette søgninger

Da du muligvis opretter mange søgninger, gør dette sidste script det nemt hurtigt at slette de søgninger, du oprettede i trin 3. På samme måde som med de andre scripts bliver du også bedt om at angive søgegruppe-id'et. Alle søgninger med søgegruppe-id'et i søgenavnet slettes, når du kører dette script.

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `DeleteSearches.ps1`f.eks. . Gem filen i den samme mappe, hvor du gemte de andre filer.

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

2. I Windows PowerShell skal du gå til den mappe, hvor du gemte scriptet i det forrige trin, og derefter køre scriptet, f.eks.:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. Skriv navnet på en søgegruppe for de søgninger, du vil slette, i prompten **søgegruppe-id** , og tryk derefter på **Enter**. f.eks.  `ContosoCase`. Husk, at der skelnes mellem store og små bogstaver i dette navn, så du skal skrive det på samme måde, som du gjorde, da du kørte scriptet i trin 3.

   Scriptet viser navnet på hver søgning, der slettes.

   ![Kør scriptet for at slette søgninger i søgegruppen.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
