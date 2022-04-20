---
title: Brug indholdssøgning til en liste over brugere i postkassen & OneDrive for Business webstedet
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
description: Brug Indholdssøgning og scriptet i denne artikel til at søge i postkasserne og OneDrive for Business websteder efter en gruppe af brugere.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 14c518c4450b01e387f84b4211da8d0eb346fe7a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949261"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Brug indholdssøgning til at søge i postkassen og OneDrive for Business websted efter en liste over brugere

Security & Compliance Center PowerShell indeholder en række cmdlet'er, der giver dig mulighed for at automatisere tidskrævende eDiscovery-relaterede opgaver. I øjeblikket tager det tid og forberedelse at oprette en indholdssøgning på Microsoft Purview-overholdelsesportalen for at søge i et stort antal placeringer med tilsynsførende indhold. Før du opretter en søgning, skal du indsamle URL-adressen for hvert OneDrive for Business websted og derefter føje hver postkasse og OneDrive for Business websted til søgningen. I fremtidige versioner bliver det nemmere at gøre det på overholdelsesportalen. Indtil da kan du bruge scriptet i denne artikel til at automatisere denne proces. I dette script bliver du bedt om at angive navnet på din organisations MySite-domæne (f.eks. **contoso** i URL-adressen `https://contoso-my.sharepoint.com`), en liste over brugermailadresser, navnet på den nye indholdssøgning og den søgeforespørgsel, der skal bruges. Scriptet henter OneDrive for Business URL-adresse for hver bruger på listen og opretter og starter derefter en indholdssøgning, der søger i postkassen og OneDrive for Business websted for hver bruger på listen ved hjælp af den søgeforespørgsel, du angiver.
  
## <a name="permissions-and-script-information"></a>Tilladelser og scriptoplysninger

- Du skal være medlem af rollegruppen eDiscovery Manager på overholdelsesportalen og en SharePoint Global Online-administrator for at køre scriptet i trin 3.

- Sørg for at gemme listen over brugere, du opretter i trin 2, og scriptet i trin 3 i den samme mappe. Det vil gøre det nemmere at køre scriptet.

- Scriptet indeholder minimal fejlhåndtering. Dens primære formål er hurtigt og nemt at søge i postkassen og OneDrive for Business websted for hver bruger.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i microsofts standardsupportprogram eller -tjeneste. Eksempelscripts leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscripts og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Trin 1: Installér SharePoint Online Management Shell

Det første trin er at installere SharePoint Online Management Shell. Du behøver ikke at bruge shell'en i denne procedure, men du skal installere den, fordi den indeholder forudsætninger, der kræves af det script, du kører i trin 3. Disse forudsætninger gør det muligt for scriptet at kommunikere med SharePoint Online for at hente URL-adresserne til de OneDrive for Business websteder.
  
Gå til [Konfigurer SharePoint Shell til onlineadministration Windows PowerShell miljø](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online), og udfør trin 1 og trin 2 for at installere SharePoint Online Management Shell.
  
## <a name="step-2-generate-a-list-of-users"></a>Trin 2: Opret en liste over brugere

Scriptet i trin 3 opretter en indholdssøgning for at søge i postkasserne og OneDrive konti for en liste over brugere. Du kan blot skrive mailadresserne i en tekstfil, eller du kan køre en kommando i Windows PowerShell for at få vist en liste over mailadresser og gemme dem i en fil (placeret i samme mappe, som du gemmer scriptet i i trin 3).
  
Her er en [Exchange Online PowerShell-kommando](/powershell/exchange/connect-to-exchange-online-powershell), som du kan køre for at få en liste over mailadresser for alle brugere i din organisation og gemme den i en tekstfil med navnet `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Når du har kørt denne kommando, skal du åbne filen og fjerne den header, der indeholder egenskabsnavnet . `PrimarySmtpAddress` Tekstfilen skal blot indeholde en liste over mailadresser og intet andet. Sørg for, at der ikke er tomme rækker før eller efter listen over mailadresser.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>Trin 3: Kør scriptet for at oprette og starte søgningen

Når du kører scriptet i dette trin, bliver du bedt om følgende oplysninger. Sørg for at have disse oplysninger klar, før du kører scriptet.
  
- **Dine brugerlegitimationsoplysninger** – Scriptet bruger dine legitimationsoplysninger til at få adgang til SharePoint Online for at hente OneDrive for Business URL-adresser og oprette forbindelse til Security & Compliance Center PowerShell. 
    
- **Navnet på dit MySite-domæne** – MySite-domænet er det domæne, der indeholder alle de OneDrive for Business websteder i din organisation. Hvis URL-adressen for dit MySite-domæne f.eks. er **https://contoso-my.sharepoint.com**, skal du angive  `contoso` , når scriptet beder dig om navnet på dit MySite-domæne. 
    
- **Stinavn på tekstfilen fra Trin 2** – Stinavnet på den tekstfil, du oprettede i trin 2. Hvis tekstfilen og scriptet er placeret i den samme mappe, skal du angive navnet på tekstfilen. Ellers skal du angive det fulde stinavn for tekstfilen. 
    
- **Navnet på indholdssøgningen** – Navnet på den indholdssøgning, der oprettes af scriptet. 
    
- **Søgeforespørgsel** – Den søgeforespørgsel, der skal bruges sammen med indholdssøgningen, oprettes og køres. Du kan finde flere oplysninger om søgeforespørgsler under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).


**Sådan kører du scriptet:**
    
1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af .ps1, `SearchEXOOD4B.ps1`f.eks. . Gem filen i den samme mappe, hvor du gemte listen over brugere i trin 2.
    
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

2. Åbn Windows PowerShell, og gå til den mappe, hvor du gemte scriptet, og listen over brugere fra trin 2.
    
3. Start scriptet. f.eks.:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Når du bliver bedt om dine legitimationsoplysninger, skal du angive din mailadresse og adgangskode og derefter klikke på **OK**. 
    
5. Angiv følgende oplysninger, når scriptet beder om det. Skriv hver oplysning, og tryk derefter på **Enter**.
    
    - Navnet på dit MySite-domæne. 
    
    - Stinavnet på den tekstfil, der indeholder listen over brugere.
    
    - Et navn til indholdssøgningen.
    
    - Søgeforespørgslen (lad dette være tomt for at returnere alle elementer på indholdsplaceringerne).
    
    Scriptet henter URL-adresserne for hvert OneDrive for Business websted og opretter og starter derefter søgningen. Du kan enten køre **Get-ComplianceSearch-cmdlet'en** i Security & Compliance Center PowerShell for at få vist søgestatistikken og -resultaterne, eller du kan gå til siden **Indholdssøgning** på overholdelsesportalen for at få vist oplysninger om søgningen.
