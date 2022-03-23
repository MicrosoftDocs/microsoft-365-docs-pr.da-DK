---
title: Søg i postkassens & OneDrive for Business efter en liste over brugere med indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/3/2017
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
ms.assetid: 5f4f8206-2d6a-4cb2-bbc6-7a0698703cc0
description: Brug indholdssøgning og scriptet i denne artikel til at søge i postkasser og OneDrive for Business efter en gruppe af brugere.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2fdf749511cc859c0aec2ea947c3a53cb800cf8c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63587920"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Brug indholdssøgning til at søge i postkassen og OneDrive for Business efter en liste over brugere

Security & Compliance Center PowerShell indeholder en række cmdlet'er, som gør det muligt at automatisere tidskrævende eDiscovery-relaterede opgaver. I øjeblikket tager det tid og forberedelse at oprette Microsoft 365 Overholdelsescenter indholdssøgning i programmet for at søge efter et stort antal indholdsplaceringer, hvor der er hjælp at finde. Før du opretter en søgning, skal du indsamle URL-adressen for hver OneDrive for Business-websted og derefter tilføje hver postkasse OneDrive for Business websted til søgningen. I fremtidige versioner vil det være nemmere at gøre i Microsoft 365 Overholdelsescenter. Indtil da kan du bruge scriptet i denne artikel til at automatisere denne proces. Dette script beder dig om navnet på organisationens domæne for Mit websted (f.eks. **contoso** i URL-adressen `https://contoso-my.sharepoint.com`), en liste over brugermailadresser, navnet på den nye indholdssøgning og den søgeforespørgsel, der skal bruges. Scriptet henter url-adressen til OneDrive for Business for hver bruger på listen, og derefter oprettes og startes en indholdssøgning, der søger i postkassen og OneDrive for Business-webstedet for hver bruger på listen ved hjælp af den søgeforespørgsel, du angiver.
  
## <a name="permissions-and-script-information"></a>Tilladelser og scriptoplysninger

- Du skal være medlem af eDiscovery Manager-rollegruppen i Microsoft 365 Overholdelsescenter og en global SharePoint Online-administrator for at køre scriptet i trin 3.

- Sørg for at gemme listen over brugere, du opretter i trin 2, og scriptet i trin 3 til den samme mappe. Det gør det nemmere at køre scriptet.

- Scriptet indeholder minimal fejlhåndtering. Dens primære formål er hurtigt og nemt at søge i postkassen OneDrive for Business websted for hver enkelt bruger.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptene leveres som de er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscripts og dokumentation forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Trin 1: Installér SharePoint Online Management Shell

Det første trin er at installere SharePoint Online Management Shell. Du behøver ikke at bruge shell i denne procedure, men du skal installere den, fordi den indeholder forudsætninger, der kræves af det script, du kører i trin 3. Disse forudsætninger gør det muligt for scriptet at kommunikere med SharePoint Online for at få URL-adresserne til OneDrive for Business websteder.
  
Gå til [Konfigurer SharePoint Online Management Shell Windows PowerShell-miljøet](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online), og udfør trin 1 og trin 2 for at installere SharePoint Online Management Shell.
  
## <a name="step-2-generate-a-list-of-users"></a>Trin 2: Opret en liste over brugere

Scriptet i trin 3 opretter en indholdssøgning for at søge i postkasser og OneDrive efter en liste over brugere. Du kan blot skrive mailadresserne i en tekstfil, eller du kan køre en kommando i Windows PowerShell for at få en liste over mailadresser og gemme dem i en fil (placeret i samme mappe, som du gemmer scriptet i trin 3).
  
Her er en [Exchange Online PowerShell-kommando](/powershell/exchange/connect-to-exchange-online-powershell), som du kan køre for at få en liste over mailadresser for alle brugere i organisationen og gemme den i en tekstfil med navnet `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Når du har kørt denne kommando, skal du sørge for at åbne filen og fjerne det sidehoved, der indeholder egenskabsnavnet. `PrimarySmtpAddress` Tekstfilen skal blot indeholde en liste over mailadresser og intet andet. Sørg for, at der ikke er nogen tomme rækker før eller efter listen over mailadresser.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>Trin 3: Kør scriptet for at oprette og starte søgningen

Når du kører scriptet i dette trin, bliver du bedt om følgende oplysninger. Sørg for, at disse oplysninger er klar, før du kører scriptet.
  
- **Dine brugerlegitimationsoplysninger** – Scriptet bruger dine legitimationsoplysninger til at få adgang til SharePoint Online for at få URL-adresserne til OneDrive for Business og til at oprette forbindelse til Security & Compliance Center PowerShell. 
    
- **Navnet på dit domæne for Mit websted** – Domænet Mit websted er det domæne, der indeholder alle OneDrive for Business i organisationen. Hvis URL-adressen for domænet for Mit websted f.eks. er , `contoso` skal du angive, når scriptet beder dig om navnet på dit domæne for Mit **https://contoso-my.sharepoint.com** websted. 
    
- **Stinavn for tekstfilen fra trin 2** – stinavnet på tekstfilen, du oprettede i trin 2. Hvis tekstfilen og scriptet er placeret i den samme mappe, skal du skrive navnet på tekstfilen. Ellers skal du angive hele stinavnet for tekstfilen. 
    
- **Navnet på indholdssøgningen** – navnet på den indholdssøgning, der oprettes af scriptet. 
    
- **Søgeforespørgsel** – Den søgeforespørgsel, der skal bruges sammen med Indholdssøgning, oprettes og køres. Du kan finde flere oplysninger om søgeforespørgsler [under Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).


**Sådan kører du scriptet:**
    
1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. `SearchEXOOD4B.ps1`. Gem filen i den samme mappe, hvor du gemte listen over brugere i trin 2.
    
  ```powershell
  # This PowerShell script will prompt you for the following information:
  #    * Your user credentials 
  #    * The name of your organization's MySite domain                                              
  #    * The pathname for the text file that contains a list of user email addresses
  #    * The name of the Content Search that will be created
  #    * The search query string
  # The script will then:
  #    * Find the OneDrive for Business site for each user in the text file
  #    * Create and start a Content Search using the above information
  # Get user credentials
  if (!$credentials)
  {
      $credentials = Get-Credential
  }
  # Get the user's MySite domain name.  We use this to create the admin URL and root URL for OneDrive for Business
  $mySiteDomain = Read-Host "What is your organization's MySite domain?  For example,  'contoso' for 'https://contoso-my.sharepoint.com'"
  $AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
  $mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
  # Get other required information
  $inputfile = read-host "Enter the file name of the text file that contains the email addresses for the users you want to search"
  $searchName = Read-Host "Enter the name for the new search"
  $searchQuery = Read-Host "Enter the search query you want to use"
  $emailAddresses = Get-Content $inputfile | where {$_ -ne ""}  | foreach{ $_.Trim() }
  # Connect to Security & Compliance Center PowerShell
  if (!$s -or !$a)
  {
      Import-Module ExchangeOnlineManagement
      Connect-IPPSSession
  }
  
  # Load the SharePoint assemblies from the SharePoint Online Management Shell
  # To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
  if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
  {
      $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
      $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
      $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
      if (!$SharePointClient)
      {
          Write-Error "SharePoint Online Management Shell isn't installed, please install from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then run this script again"
          return;
      }
  }
  if (!$spCreds)
  {
      $spCreds = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($credentials.UserName, $credentials.Password)
  }
  # Add the path of the User Profile Service to the SPO admin URL, then create a new webservice proxy to access it
  $proxyaddr = "$AdminUrl/_vti_bin/UserProfileService.asmx?wsdl"
  $UserProfileService= New-WebServiceProxy -Uri $proxyaddr -UseDefaultCredential False
  $UserProfileService.Credentials = $credentials
  # Take care of auth cookies
  $strAuthCookie = $spCreds.GetAuthenticationCookie($AdminUrl)
  $uri = New-Object System.Uri($AdminUrl)
  $container = New-Object System.Net.CookieContainer
  $container.SetCookies($uri, $strAuthCookie)
  $UserProfileService.CookieContainer = $container
  Write-Host "Getting each user's OneDrive for Business URL"
  $urls = @()
  foreach($emailAddress in $emailAddresses)
  {
      try
      {
          $prop = $UserProfileService.GetUserProfileByName("i:0#.f|membership|$emailAddress") | Where-Object { $_.Name -eq "PersonalSpace" } 
          $url = $prop.values[0].value
          $furl = $mySiteUrlRoot + $url
          $urls += $furl
          Write-Host "-$emailAddress => $furl"
      }
      catch
      {
          Write-Warning "Could not locate OneDrive for $emailAddress"
      }
  }
  Write-Host "Creating and starting the search"
  $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $emailAddresses -SharePointLocation $urls -ContentMatchQuery $searchQuery
  # Finally, start the search and then display the status
  if($search)
  {
      Start-ComplianceSearch $search.Name
      Get-ComplianceSearch $search.Name
  }
  
  ```

2. Åbn Windows PowerShell, og gå til den mappe, hvor du gemte scriptet og listen over brugere fra trin 2.
    
3. Start scriptet. for eksempel:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Når du bliver bedt om dine legitimationsoplysninger, skal du angive din mailadresse og adgangskode og derefter klikke på **OK**. 
    
5. Angiv følgende oplysninger, når du bliver bedt om det af scriptet. Skriv hver enkelt oplysning, og tryk derefter på **Enter**.
    
    - Navnet på dit domæne for Mit websted. 
    
    - Stinavnet på den tekstfil, der indeholder listen over brugere.
    
    - Et navn til Indholdssøgning.
    
    - Søgeforespørgslen (lad denne være tom for at returnere alle elementer på indholdsplaceringerne).
    
    Scriptet henter URL-adresserne for hver OneDrive for Business og opretter og starter derefter søgningen. Du kan enten køre **Cmdlet'en Get-ComplianceSearch** i Security & Compliance Center PowerShell for at få vist søgestatistik og resultater, eller du kan gå til siden Indholdssøgning i Microsoft 365 Overholdelsescenter for at få vist oplysninger om søgningen.
