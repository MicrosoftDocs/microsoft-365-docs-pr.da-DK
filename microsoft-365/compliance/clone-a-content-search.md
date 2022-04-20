---
title: Klon en indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: Brug PowerShell-scriptet i denne artikel til hurtigt at klone en eksisterende indholdssøgning i overholdelsescenteret i Office 365 eller Microsoft 365.
ms.openlocfilehash: 782620d3693f4659c135d2a52aa7062a490a7cd0
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940483"
---
# <a name="clone-a-content-search"></a>Klon en indholdssøgning

Det kan tage et stykke tid at oprette en indholdssøgning i overholdelsescenteret i Office 365 eller Microsoft 365, der søger i mange postkasser eller SharePoint og OneDrive for Business websteder. Hvis du angiver de websteder, der skal søges efter, kan der også opstå fejl, hvis du angiver en URL-adresse forkert. Du kan undgå disse problemer ved at bruge scriptet Windows PowerShell i denne artikel til hurtigt at klone en eksisterende indholdssøgning. Når du kloner en søgning, oprettes der en ny søgning (med et andet navn), der indeholder de samme egenskaber (f.eks. indholdsplaceringer og søgeforespørgslen) som den oprindelige søgning. Derefter kan du redigere den nye søgning ved at ændre nøgleordsforespørgslen eller datointervallet og køre den.
  
Hvorfor klone indholdssøgninger?
  
- Hvis du vil sammenligne resultaterne af forskellige nøgleordssøgeforespørgsler, der kører på de samme indholdsplaceringer.
    
- For at spare dig for at skulle angive et stort antal indholdsplaceringer igen, når du opretter en ny søgning.
    
- Hvis du vil reducere størrelsen af søgeresultaterne. Hvis du f.eks. har en søgning, der returnerer for mange resultater til eksport, kan du klone søgningen og derefter tilføje en søgebetingelse baseret på et datointerval for at reducere antallet af søgeresultater.
  
## <a name="script-information"></a>Scriptoplysninger

- Du skal være medlem af rollegruppen eDiscovery Manager på Microsoft Purview-overholdelsesportalen for at køre scriptet, der er beskrevet i dette emne.
    
- Scriptet indeholder minimal fejlhåndtering. Det primære formål med scriptet er hurtigt at klone en indholdssøgning.
    
- Scriptet opretter en ny indholdssøgning, men starter den ikke.
    
- Dette script tager højde for, om den indholdssøgning, du kloner, er knyttet til en eDiscovery-sag. Hvis søgningen er knyttet til en sag, knyttes den nye søgning også til den samme sag. Hvis den eksisterende søgning ikke er knyttet til en sag, vises den nye søgning på siden **Indholdssøgning** i Overholdelsescenter. 
    
- Det eksempelscript, der er angivet i dette emne, understøttes ikke i et hvilket som helst Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.
  
## <a name="step-1-run-the-script-to-clone-a-search"></a>Trin 1: Kør scriptet for at klone en søgning

Scriptet i dette trin opretter en ny indholdssøgning ved at klone en eksisterende. Når du kører dette script, bliver du bedt om følgende oplysninger:
  
- **Dine brugerlegitimationsoplysninger** – Scriptet bruger dine legitimationsoplysninger til at oprette forbindelse til PowerShell & Security & Compliance Center. Som tidligere nævnt skal du være medlem af rollegruppen eDiscovery Manager i Security & compCompliance Center for at køre scriptet. 
    
- **Navnet på den eksisterende søgning** – dette er den indholdssøgning, du vil klone. 
    
- **Navnet på den nye søgning, der oprettes** – Hvis du lader denne værdi være tom, opretter scriptet et navn til den nye søgning, der er baseret på navnet på den søgning, du kloner. 
    
Sådan kloner du en søgning:
  
1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `CloneSearch.ps1`f.eks. .
    
  ```powershell
  # This PowerShell script clones an existing content search in the Security &amp; Compliance Center.
  # Get login credentials from the user
  if(!$UserCredential)
  {
      $UserCredential = Get-Credential
      $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
      if (!$Session)
      {
          Write-Error "Couldn't create a remote PowerShell session."
          return
      }
      Import-PSSession $Session -AllowClobber -DisableNameChecking
      $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Security & Compliance Center)"
  }
  # Ask for the name of the search you want to clone
  $searchName = Read-Host 'Enter the name of the search that you want to clone'
  # Ask for the name of the new search
  $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
  $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
  # Make sure we have a valid search before continuing
  if(!$originalSearch)
  {
      Write-Error "Couldn't find search: $searchName"
      return
  }
  $searchNameCounter = 1
  # Find a suitable name for the new search
  while(!$newSearchName)
  {
      $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
      $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
      if ($tempSearch)
      {
          $newSearchName = $null
          $searchNameCounter++
      }
  }
  $caseName
  # Determine if the search is part of a case; if so get the case name
  if ($originalSearch.CaseId)
  {
      $searchCase = Get-ComplianceCase $originalSearch.CaseId
      $caseName = $searchCase.Name
  }
  # Need to cast this value as a Boolean the old fashion way
  $allowNotFoundExchangeLocationsEnabled = $false
  if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
  {
      $allowNotFoundExchangeLocationsEnabled = $true
  }
  $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
  if ($newSearch)
  {
      Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
  }
  ```

2. Åbn Windows PowerShell, og gå til den mappe, hvor du gemte scriptet.
    
3. Kør scriptet. f.eks.:
    
    ```powershell
    .\CloneSearch.ps1
    ```

4. Når du bliver bedt om dine legitimationsoplysninger, skal du angive din mailadresse og adgangskode og derefter klikke på **OK**.
    
5. Angiv følgende oplysninger, når scriptet beder om det. Skriv hver oplysning, og tryk derefter på **Enter**.
    
    - Navnet på den eksisterende søgning.
    
    - Navnet på den nye søgning.
    
    Scriptet opretter den nye indholdssøgning, men starter den ikke. Det giver dig mulighed for at redigere og køre søgningen i næste trin. Du kan få vist egenskaberne for den nye søgning ved at køre **Get-ComplianceSearch-cmdlet'en** eller ved at gå til **indholdssøgnings-** eller **eDiscovery-siden** i overholdelsescenteret, afhængigt af om den nye søgning er knyttet til en sag. 
  
## <a name="step-2-edit-and-run-the-cloned-search-in-the-compliance-center"></a>Trin 2: Rediger og kør den klonede søgning i Overholdelsescenter

Når du har kørt scriptet for at klone en eksisterende indholdssøgning, er næste trin at gå til Overholdelsescenter for at redigere og køre den nye søgning. Som tidligere angivet kan du redigere en søgning ved at ændre søgeforespørgslen med nøgleordet og tilføje eller fjerne søgebetingelser. Du kan finde flere oplysninger under:
  
- [Indholdssøgning i Office 365](content-search.md)
    
- [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)
    
- [eDiscovery-sager](./get-started-core-ediscovery.md)