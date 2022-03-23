---
title: Brug et script til at føje brugere til en venteposition i en Core eDiscovery-sag
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
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: bad352ff-d5d2-45d8-ac2a-6cb832f10e73
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Få mere at vide om, hvordan du kører et script for at føje postkasser & OneDrive for Business websteder til en ny venteposition, der er knyttet til en eDiscovery-sag i Microsoft 365 Overholdelsescenter.
ms.openlocfilehash: fd11ccb6c262cd0e31a65d2a1f95d5dbcd92869c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589148"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Brug et script til at føje brugere til en venteposition i en Core eDiscovery-sag

Security & Compliance Center PowerShell indeholder cmdlet'er, der gør det muligt at automatisere tidskrævende opgaver i forbindelse med oprettelse og administration af eDiscovery-sager. I øjeblikket tager det tid og forberedelse at bruge Core eDiscovery-Microsoft 365 Overholdelsescenter til at placere et stort antal afiansk indholdsplaceringer i venteposition. Før du opretter en venteposition, skal du f.eks. indsamle URL-adressen for hvert OneDrive for Business, du vil placere i venteposition. Derefter skal du for hver bruger, du vil placere i venteposition, føje deres postkasse og deres OneDrive for Business til venteposition. Du kan bruge scriptet i denne artikel til at automatisere denne proces.
  
Scriptet beder dig om navnet på din organisations domæne Mit websted ( `contoso` f.eks. i URL-adressen https://contoso-my.sharepoint.com), navnet på en eksisterende eDiscovery-sag, navnet på den nye venteposition, der er knyttet til sagen, en liste over mailadresser på de brugere, du vil sætte i venteposition, og en søgeforespørgsel, der kan bruges, hvis du vil oprette en forespørgselsbaseret venteposition. Scriptet henter derefter URL-adressen til OneDrive for Business-webstedet for hver bruger på listen, opretter den nye venteposition og tilføjer derefter postkassen og OneDrive for Business-webstedet for hver bruger på listen i venteposition. Scriptet genererer også logfiler, der indeholder oplysninger om den nye venteposition.
  
Her er trinnene, der skal til for at gøre dette:
  
[Trin 1: Installér SharePoint Online Management Shell](#step-1-install-the-sharepoint-online-management-shell)
  
[Trin 2: Opret en liste over brugere](#step-2-generate-a-list-of-users)
  
[Trin 3: Kør scriptet for at oprette en venteposition og tilføje brugere](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Før du føjer brugere til en venteposition

- Du skal være medlem af eDiscovery Manager-rollegruppen i Microsoft 365 Overholdelsescenter og en SharePoint Online-administrator for at køre scriptet i trin 3. Få mere at vide under [Tildel eDiscovery-tilladelser i Office 365 Security & Compliance Center](assign-ediscovery-permissions.md).

- Maksimalt 1.000 postkasser og 100 websteder kan føjes til en venteposition, der er knyttet til en eDiscovery-sag i Microsoft 365 Overholdelsescenter. Hvis alle brugere, du vil placere i venteposition, har et OneDrive for Business-websted, kan du maksimalt føje 100 brugere til en venteposition ved hjælp af scriptet i denne artikel.

- Sørg for at gemme listen over brugere, du opretter i trin 2, og scriptet i trin 3 til den samme mappe. Det gør det nemmere at køre scriptet.

- Scriptet føjer listen over brugere til en ny venteposition, der er knyttet til en eksisterende sag. Sørg for, at den sag, du vil knytte ventepositionen til, er oprettet, før du kører scriptet.

- Scriptet i denne artikel understøtter moderne godkendelse, når du opretter forbindelse til Security & Compliance Center PowerShell SharePoint Online Management Shell. Du kan bruge scriptet, som det er, hvis du er Microsoft 365 eller Microsoft 365 GCC organisation. Hvis du er en Office 365 Germany-organisation, en Microsoft 365 GCC High-organisation eller en Microsoft 365 DoD-organisation, skal du redigere scriptet for at køre det korrekt. Du skal redigere `Connect-IPPSSession` linjen og bruge parametrene *ConnectionUri* og *AzureADAuthorizationEndpointUri* (og de relevante værdier for din organisationstype) til at oprette forbindelse til Security & Compliance Center PowerShell. Du kan finde flere oplysninger i eksemplerne [Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Scriptet afbryder automatisk forbindelsen til Security & Compliance Center PowerShell og SharePoint Online Management Shell.

- Scriptet indeholder minimal fejlhåndtering. Dens primære formål er hurtigt og nemt at placere postkassen og OneDrive for Business for hver bruger i venteposition.

- De eksempelscripts, der er angivet i dette emne, understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptene leveres som de er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscripts og dokumentation forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Trin 1: Installér SharePoint Online Management Shell

Det første trin er at installere SharePoint Online Management Shell, hvis den ikke allerede er installeret på din lokale computer. Du behøver ikke at bruge shell i denne procedure, men du skal installere den, fordi den indeholder forudsætninger, der kræves af det script, du kører i trin 3. Disse forudsætninger gør det muligt for scriptet at kommunikere med SharePoint Online for at få URL-adresserne til OneDrive for Business websteder.
  
Gå til [Konfigurer SharePoint Online Management Shell Windows PowerShell-miljøet](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online), og udfør trin 1 og trin 2 for at installere SharePoint Online Management Shell på din lokale computer.

## <a name="step-2-generate-a-list-of-users"></a>Trin 2: Opret en liste over brugere

Scriptet i trin 3 opretter en venteposition, der er knyttet til en eDiscovery-sag, og tilføjelsen af postkasser og OneDrive for Business-websteder med en liste over brugere i venteposition. Du kan blot skrive mailadresserne i en tekstfil, eller du kan køre en kommando i Windows PowerShell for at få en liste over mailadresser og gemme dem i en fil (placeret i samme mappe, som du gemmer scriptet i trin 3).
  
Her er en PowerShell-kommando (som du kører ved hjælp af Remote PowerShell forbundet med din Exchange Online-organisation) til at hente en liste over mailadresser for alle brugere i organisationen og gemme den i en tekstfil med navnet HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Når du har kørt denne kommando, skal du åbne tekstfilen og fjerne det sidehoved, der indeholder egenskabsnavnet. `PrimarySmtpAddress` Fjern derefter alle mailadresser undtagen dem for de brugere, du vil føje til ventepositionen, som du opretter i trin 3. Sørg for, at der ikke er nogen tomme rækker før eller efter listen over mailadresser.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>Trin 3: Kør scriptet for at oprette en venteposition og tilføje brugere

Når du kører scriptet i dette trin, bliver du bedt om følgende oplysninger. Sørg for, at disse oplysninger er klar, før du kører scriptet.
  
- **Dine brugerlegitimationsoplysninger:** Scriptet bruger dine legitimationsoplysninger til at oprette forbindelse til Security & Compliance Center med PowerShell. Den vil også bruge disse legitimationsoplysninger til at SharePoint Online til at hente OneDrive for Business URL-adresser for listen over brugere.

- **Navnet på dit SharePoint-domæne:** Scriptet beder dig om at angive dette navn, så <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">det kan oprette forbindelse SharePoint Administration</a>. Den anvender også domænenavnet til OneDrive i organisationen. Hvis URL-adressen `https://contoso-admin.sharepoint.com` til administration f.eks. er, og URL-adressen for OneDrive er `https://contoso-my.sharepoint.com`, `contoso` skal du angive, når scriptet beder dig om dit domænenavn.

- **Navnet på sagen:** Navnet på en eksisterende sag. Scriptet opretter en ny venteposition, der er knyttet til denne sag.

- **Navnet på ventepositionen:** Navnet på den venteposition, som scriptet opretter og knytter til den angivne sag.

- **Søgeforespørgsel til forespørgselsbaseret venteposition:** Du kan oprette en forespørgselsbaseret venteposition, så kun det indhold, der opfylder de angivne søgekriterier, er sat i venteposition. Hvis du vil placere alt indhold i venteposition, skal du blot trykke **på Enter** , når du bliver bedt om at angive en søgeforespørgsel.

- **Aktivering af ventepositionen eller ej:** Du kan få scriptet til at aktivere ventepositionen, når det er oprettet, eller du kan få scriptet til at oprette ventepositionen uden at aktivere det. Hvis du ikke har scriptet aktiveret i venteposition, kan du aktivere det senere i Microsoft 365 Overholdelsescenter eller ved at køre følgende PowerShell-kommandoer:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Navnet på tekstfilen med** listen over brugere – navnet på tekstfilen fra trin 2, der indeholder listen over brugere, der skal føjes til ventepositionen. Hvis denne fil er placeret i den samme mappe som scriptet, skal du blot skrive navnet på filen (f.eksHoldUsers.txt). Hvis tekstfilen er i en anden mappe, skal du skrive hele filens stinavn.

Når du har indsamlet de oplysninger, som scriptet vil bede dig om, er det sidste trin at køre scriptet for at oprette den nye venteposition og føje brugere til den.
  
1. Gem følgende tekst i en Windows PowerShell-scriptfil ved hjælp af et filnavnsuffiks af `.ps1`. F.eks. `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   Core eDiscovery cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
write-host "***********************************************"
" "
# Connect to SCC PowerShell using modern authentication
if (!$SccSession)
{
  Import-Module ExchangeOnlineManagement
  Connect-IPPSSession
}

# Get the organization's domain name. We use this to create the SharePoint admin URL and root URL for OneDrive for Business.
""
$mySiteDomain = Read-Host "Enter the domain name for your SharePoint organization. We use this name to connect to SharePoint admin center and for the OneDrive URLs in your organization. For example, 'contoso' in 'https://contoso-admin.sharepoint.com' and 'https://contoso-my.sharepoint.com'"
""

# Connect to PnP Online using modern authentication
Import-Module PnP.PowerShell
Connect-PnPOnline -Url https://$mySiteDomain-admin.sharepoint.com -UseWebLogin

# Load the SharePoint assemblies from the SharePoint Online Management Shell
# To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
{
    $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
    $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
    $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
    if (!$SharePointClient)
    {
        Write-Error "The SharePoint Online Management Shell isn't installed. Please install it from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then re-run this script."
        return;
    }
}

# Get other required information
do{
$casename = Read-Host "Enter the name of the case"
$caseexists = (get-compliancecase -identity "$casename" -erroraction SilentlyContinue).isvalid
if($caseexists -ne 'True')
{""
write-host "A case named '$casename' doesn't exist. Please specify the name of an existing case, or create a new case and then re-run the script." -foregroundColor Yellow
""}
}While($caseexists -ne 'True')
""
do{
$holdName = Read-Host "Enter the name of the new hold"
$holdexists=(get-caseholdpolicy -identity "$holdname" -case "$casename" -erroraction SilentlyContinue).isvalid
if($holdexists -eq 'True')
{""
write-host "A hold named '$holdname' already exists. Please specify a new hold name." -foregroundColor Yellow
""}
}While($holdexists -eq 'True')
""
$holdQuery = Read-Host "Enter a search query to create a query-based hold, or press Enter to hold all content"
""
$holdstatus = read-host "Do you want the hold enabled after it's created? (Yes/No)"
do{
""
$inputfile = read-host "Enter the name of the text file that contains the email addresses of the users to add to the hold"
""
$fileexists = test-path -path $inputfile
if($fileexists -ne 'True'){write-host "$inputfile doesn't exist. Please enter a valid file name." -foregroundcolor Yellow}
}while($fileexists -ne 'True')
#Import the list of addresses from the txt file.  Trim any excess spaces and make sure all addresses 
    #in the list are unique.
  [array]$emailAddresses = Get-Content $inputfile -ErrorAction SilentlyContinue | where {$_.trim() -ne ""}  | foreach{ $_.Trim() }
  [int]$dupl = $emailAddresses.count
  [array]$emailAddresses = $emailAddresses | select-object -unique
  $dupl -= $emailAddresses.count
#Validate email addresses so the hold creation does not run in to an error.
if($emailaddresses.count -gt 0){
write-host ($emailAddresses).count "addresses were found in the text file. There were $dupl duplicate entries in the file." -foregroundColor Yellow
""
Write-host "Validating the email addresses. Please wait..." -foregroundColor Yellow
""
$finallist =@()
foreach($emailAddress in $emailAddresses)
{
if((get-recipient $emailaddress -erroraction SilentlyContinue).isvalid -eq 'True')
{$finallist += $emailaddress}
else {"Unable to find the user $emailaddress"
[array]$excludedlist += $emailaddress}
}
""
#Find user's OneDrive account URL using email address
Write-Host "Getting the URL for each user's OneDrive for Business site." -foregroundColor Yellow 
""
$AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
$mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
$urls = @()
foreach($emailAddress in $finallist)
{
try
{
$url=Get-PnPUserProfileProperty -Account $emailAddress | Select PersonalUrl
$urls += $url.PersonalUrl
       Write-Host "- $emailAddress => $url"
       [array]$ODadded += $url.PersonalUrl
       }catch { 
 Write-Warning "Could not locate OneDrive for $emailAddress"
 [array]$ODExluded += $emailAddress
 Continue }
}
$urls | FL
if(($finallist.count -gt 0) -or ($urls.count -gt 0)){
""
Write-Host "Creating the hold named $holdname. Please wait..." -foregroundColor Yellow
if(($holdstatus -eq "Y") -or ($holdstatus -eq  "y") -or ($holdstatus -eq "yes") -or ($holdstatus -eq "YES")){
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $True | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery | out-null
}
else{
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $false | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery -disabled $false | out-null
}
""
}
else {"No valid locations were identified. Therefore, the hold wasn't created."}
#write log files (if needed)
$newhold=Get-CaseHoldPolicy -Identity "$holdname" -Case "$casename" -erroraction SilentlyContinue
$newholdrule=Get-CaseHoldRule -Identity "$holdName" -erroraction SilentlyContinue
if(($ODAdded.count -gt 0) -or ($ODExluded.count -gt 0) -or ($finallist.count -gt 0) -or ($excludedlist.count -gt 0) -or ($newhold.isvalid -eq 'True') -or ($newholdrule.isvalid -eq 'True'))
{
Write-Host "Generating output files..." -foregroundColor Yellow
if($ODAdded.count -gt 0){
"OneDrive Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.SharePointLocation.name | add-content .\LocationsOnHold.txt}
if($ODExluded.count -gt 0){ 
"Users without OneDrive locations" | add-content .\LocationsNotOnHold.txt
"================================" | add-content .\LocationsNotOnHold.txt
$ODExluded | add-content .\LocationsNotOnHold.txt}
if($finallist.count -gt 0){
" " | add-content .\LocationsOnHold.txt
"Exchange Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.ExchangeLocation.name | add-content .\LocationsOnHold.txt}
if($excludedlist.count -gt 0){
" "| add-content .\LocationsNotOnHold.txt
"Mailboxes not added to the hold" | add-content .\LocationsNotOnHold.txt
"===============================" | add-content .\LocationsNotOnHold.txt
$excludedlist | add-content .\LocationsNotOnHold.txt}
$FormatEnumerationLimit=-1
if($newhold.isvalid -eq 'True'){$newhold|fl >.\GetCaseHoldPolicy.txt}
if($newholdrule.isvalid -eq 'True'){$newholdrule|Fl >.\GetCaseHoldRule.txt}
}
}
else {"The hold wasn't created because no valid entries were found in the text file."}
""
#Disconnect from SCC PowerShell and PnPOnline

Write-host "Disconnecting from SCC PowerShell and PnP Online" -foregroundColor Yellow
Get-PSSession | Remove-PSSession
Disconnect-PnPOnline

Write-host "Script complete!" -foregroundColor Yellow
""
#script end
```

2. Åbn Scriptet på din lokale Windows PowerShell og gå til den mappe, hvor du gemte scriptet.

3. Kør scriptet. for eksempel:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Angiv de oplysninger, som scriptet beder dig om.

   Scriptet opretter forbindelse til Security & Compliance Center PowerShell og opretter derefter den nye venteposition i eDiscovery-sagen og tilføjer postkasser og OneDrive for Business til brugerne på listen. Du kan gå til sagen på **eDiscovery-siden** i Microsoft 365 Overholdelsescenter for at få vist den nye venteposition.

Når scriptet er færdigt med at køre, oprettes følgende logfiler, og de gemmes i den mappe, hvor scriptet er placeret.
  
- **LocationsOnHold.txt:** Indeholder en liste over postkasser og OneDrive for Business, som scriptet er sat i venteposition.

- **LocationsNotOnHold.txt:** Indeholder en liste over postkasser og OneDrive for Business websteder, som scriptet ikke placerede i venteposition. Hvis en bruger har en postkasse, men ikke et OneDrive for Business-websted, medtages brugeren på listen over OneDrive for Business-websteder, der ikke er sat i venteposition.

- **GetCaseHoldPolicy.txt:** Indeholder output fra **Get-CaseHoldPolicy-cmdlet'en** for den nye venteposition, som scriptet kørte efter oprettelse af den nye venteposition. De oplysninger, der returneres af denne cmdlet, omfatter en liste over brugere, hvis postkasser og OneDrive for Business er sat i venteposition, og om ventepositionen er aktiveret eller deaktiveret. 

- **GetCaseHoldRule.txt:** Indeholder output fra **Get-CaseHoldRule-cmdlet'en** for den nye venteposition, som scriptet kørte efter oprettelse af den nye venteposition. De oplysninger, der returneres af denne cmdlet, omfatter søgeforespørgslen, hvis du har brugt scriptet til at oprette en forespørgselsbaseret venteposition.
