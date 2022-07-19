---
title: Brug PowerShell til at forbinde Skift til Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du bruger PowerShell til at integrere Skift med Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 22b820bdbb372b5f07967836613a9d7348bd7b1c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859070"
---
# <a name="use-powershell-to-connect-shifts-to-blue-yonder-workforce-management"></a>Brug PowerShell til at forbinde Skift til Blue Yonder Workforce Management

## <a name="overview"></a>Oversigt

Brug [Microsoft Teams Shifts-connectoren til Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) til at integrere Appen Shifts i Microsoft Teams med Blue Yonder-Workforce Management (Blue Yonder WFM). Når en forbindelse er oprettet, kan dine frontlinjemedarbejdere uden problemer få vist og administrere deres tidsplaner i Blue Yonder WFM fra Skift.

I denne artikel gennemgår vi, hvordan du bruger PowerShell til at konfigurere connectoren til at integrere Shifts med Blue Yonder WFM.

Hvis du vil konfigurere forbindelsen, skal du køre et PowerShell-script. Scriptet konfigurerer connectoren, anvender synkroniseringsindstillinger, opretter forbindelsen og knytter Blue Yonder WFM forekomster til teams. Synkroniseringsindstillinger bestemmer de funktioner, der er aktiveret i Skift, og de tidsplanoplysninger, der synkroniseres mellem Blue Yonder WFM og Shifts. Tilknytninger definerer synkroniseringsrelationen mellem dine Blue Yonder-WFM instanser og teams i Teams. Du kan knytte til eksisterende teams og nye teams.

Vi leverer to scripts. Du kan bruge begge scripts, afhængigt af om du vil knytte til eksisterende teams eller oprette nye teams, der skal tilknyttes.

Du kan konfigurere flere forbindelser, der hver især har forskellige synkroniseringsindstillinger. Hvis din organisation f.eks. har flere placeringer med forskellige tidsplankrav, skal du oprette en forbindelse med entydige synkroniseringsindstillinger for hver placering. Vær opmærksom på, at en Blue Yonder-WFM instans kun kan knyttes til ét team på et givent tidspunkt. Hvis en forekomst allerede er knyttet til et team, kan den ikke knyttes til et andet team.

Med Blue Yonder-WFM som postsystem kan dine frontlinjearbejdere se og skifte skiftehold, administrere deres tilgængelighed og anmode om fridag i skiftehold på deres enheder. Frontlineledere kan fortsætte med at bruge Blue Yonder WFM til at oprette tidsplaner.

> [!NOTE]
> Du kan også bruge [guiden Skifts-connector](shifts-connector-wizard.md) i Microsoft 365 Administration til at forbinde Shifts med blåt WFM.

## <a name="before-you-begin"></a>Før du begynder

### <a name="prerequisites"></a>Forudsætninger

[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

### <a name="admin-role-to-manage-the-connector-using-powershell"></a>Administration rolle til administration af connectoren ved hjælp af PowerShell

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>Konfigurer dit miljø

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

## <a name="connect-to-teams"></a>Opret forbindelse til Teams

Kør følgende for at oprette forbindelse til Teams.

```powershell
Connect-MicrosoftTeams
```

Når du bliver bedt om det, skal du logge på med dine administratorlegitimationsoplysninger. Du er nu konfigureret til at køre scripts i denne artikel og Shifts-connector-cmdlet'er.

## <a name="identify-the-teams-you-want-to-map"></a>Identificer de teams, du vil tilknytte

> [!NOTE]
> Fuldfør dette trin, hvis du knytter Blue Yonder WFM forekomster til eksisterende teams. Hvis du opretter nye teams, der skal tilknyttes, kan du springe dette trin over.

I Azure Portal skal du gå til siden [Alle grupper](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) for at få vist en liste over TeamId'er for teams i din organisation.

Notér TeamId'erne for de teams, du vil tilknytte. Scriptet beder dig om at angive disse oplysninger.

> [!NOTE]
> Hvis et eller flere teams har en eksisterende tidsplan, fjerner scriptet tidsplanerne fra disse teams. Ellers kan du se dublerede skift.

## <a name="run-the-script"></a>Kør scriptet

Kør scriptet:

- Hvis du vil oprette en forbindelse og oprette nye teams, der skal tilknyttes, [skal du køre dette script](#set-up-a-connection-and-create-new-teams-to-map).
- Hvis du vil konfigurere en forbindelse og knytte til eksisterende teams, [skal du køre dette script](#set-up-a-connection-and-map-to-existing-teams).

Scriptet udfører følgende handlinger. Du bliver bedt om at angive oplysninger om konfiguration og konfiguration.

1. Tester og kontrollerer forbindelsen til Blue Yonder WFM ved hjælp af legitimationsoplysningerne for den blå yonder-WFM tjenestekonto og tjeneste-URL-adresser, som du angiver.
1. Konfigurerer Shifts-connectoren.
1. Anvender synkroniseringsindstillinger. Disse indstillinger omfatter synkroniseringshyppigheden (i minutter) og de tidsplandata, der synkroniseres mellem Blue Yonder WFM og Skift. Planlægningsdata er defineret i følgende parametre:

    - Parameteren **enabledConnectorScenarios** definerer data, der synkroniseres fra Blue Yonder WFM til Skift. Indstillingerne er `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift``OpenShiftRequest`, , `TimeOff`, `TimeOffRequest`.
    - Parameteren **enabledWfiScenarios** definerer data, der synkroniseres fra Skift til Blue Yonder WFM. Indstillingerne er `SwapRequest`, `OpenShiftRequest`, `TimeOffRequest`, `UserShiftPreferences`.

    Du kan få mere at vide under [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance). Hvis du vil se en liste over understøttede synkroniseringsindstillinger for hver parameter, skal du køre [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

    > [!IMPORTANT]
    > Scriptet aktiverer synkronisering for alle disse indstillinger. Hvis du vil ændre synkroniseringsindstillingerne, kan du gøre det, når forbindelsen er oprettet. Du kan få mere at vide under [Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

1. Opretter forbindelsen.
1. Kort blue yonder WFM forekomster til teams. Tilknytninger er baseret på de blå yonder-id'er WFM instans-id'er og TeamIds, som du angiver, eller nye teams, du opretter, afhængigt af det script, du kører. Hvis et team har en eksisterende tidsplan, fjerner scriptet tidsplandata for det dato- og tidsinterval, du angiver.

En meddelelse om fuldførelse på skærmen angiver, at forbindelsen er konfigureret korrekt.

## <a name="if-you-need-to-make-changes-to-a-connection"></a>Hvis du har brug for at foretage ændringer af en forbindelse

Hvis du vil foretage ændringer af en forbindelse, når den er konfigureret, skal du se [Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder Workforce Management](shifts-connector-powershell-manage.md). Du kan f.eks. opdatere synkroniseringsindstillinger, teamtilknytninger og deaktivere synkronisering for en forbindelse.

## <a name="scripts"></a>Scripts

### <a name="set-up-a-connection-and-create-new-teams-to-map"></a>Konfigurer en forbindelse, og opret nye teams, der skal tilknyttes

```powershell
#Map WFM instances to teams script
Write-Host "Map WFM sites to teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM super user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create a connection instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Enter your Microsoft 365's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency"

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq -ConnectorAdminEmail $AdminEmailList
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of WFM instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

#Create a new Teams team with owner set to system account and name set to the site name
Write-Host "Creating a Teams team"
$teamsTeamName = Read-Host -Prompt "Input the Teams team name"
$Team = New-Team -DisplayName $teamsTeamName -Visibility "Public" -Owner $teamsUserId
Write-Host "Success"
$TeamsTeamId=$Team.GroupId

#Add users to the Team for Shifts
Write-Host "Adding users to Teams team"
$currentUser = Read-Host -Prompt "Input the current user's user name or ID"
Add-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
$failedWfmUsers=@()
foreach ($user in $WFMUsers) {
    try {
    $userEmail = $user.Name + "@" +$domain
    Add-TeamUser -GroupId $TeamsTeamId -User $userEmail
    } catch {
        $failedWfmUsers+=$user
    }
}
if($failedWfmUsers.Count -gt 0){
    Write-Host "There are WFM users not existed in Teams tenant:"
    write $failedWfmUsers
}

#Enable scheduling in the group
$RequestBody = @{
    Enabled = $true
    TimeZone = "America/Los_Angeles"
}
$teamUpdateUrl="https://graph.microsoft.com/v1.0/teams/"+$TeamsTeamId+"/schedule"
$Schedule = Invoke-MgGraphRequest -Uri $teamUpdateUrl -Method PUT -Body $RequestBody

#Create a mapping of the new team to the WFM instance
Write-Host "Create a mapping of the new team to the site"
$TimeZone = Read-Host -Prompt "Input the time zone of team mapping"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone $TimeZone -WfmTeamId $WfmTeamId
Write-Host "Success"

$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}

#The Teams admin was set as an owner directly when creating a new team, removing it from owners
Remove-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
Disconnect-MgGraph
```

### <a name="set-up-a-connection-and-map-to-existing-teams"></a>Konfigurer en forbindelse, og knyt til eksisterende teams

```powershell
#Map WFM sites to existing teams script
Write-Host "Map WFM sites to existing teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM super user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create a connection instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Enter your Microsoft 365 user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency in minutes. Value should be equal to or more than 10."

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq -ConnectorAdminEmail AdminEmailList

$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of WFM instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

$TeamsTeamId = Read-Host -Prompt "Input the ID of the Teams team to be mapped"
#Clear schedule of the Teams team
Write-Host "Clear schedule of the existing team"
$startTime = Read-Host -Prompt "Input the start time of clear schedule"
$endTime = Read-Host -Prompt "Input the end time of clear schedule"

$entityTypeString = Read-Host -Prompt 'Input the entity types of clear schedule'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$entityType = $entityTypeString -Split {$Delimiters -contains $_}
$entityType = $entityType.Trim()
$entityType = $entityType.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
Remove-CsTeamsShiftsScheduleRecord -TeamId $TeamsTeamId -DateRangeStartDate $startTime -DateRangeEndDate $endTime -ClearSchedulingGroup:$True -EntityType $entityType -DesignatedActorId $$teamsUserId

#Create a mapping of the new team to the WFM instance
Write-Host "Create a mapping of the existing team to the site"
$TimeZone = Read-Host -Prompt "Input the time zone of team mapping"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone $TimeZone -WfmTeamId $WfmTeamId
Write-Host "Success"


$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Disconnect-MgGraph
```

## <a name="shifts-connector-cmdlets"></a>Skifter forbindelses-cmdlet'er

Hvis du vil have hjælp til Shifts-connector-cmdlet'er, herunder de cmdlet'er, der bruges i scripts, skal du søge efter **CsTeamsShiftsConnection** i [Reference til Teams PowerShell-cmdlet'en](/powershell/teams/intro). Her er links til nogle almindeligt anvendte cmdlet'er.

- [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation)
- [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance)
- [Get-CsTeamsShiftsConnectionInstance](/powershell/module/teams/get-csteamsshiftsconnectioninstance)
- [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance)
- [Fjern-CsTeamsShiftsConnectionInstance](/powershell/module/teams/remove-csteamsshiftsconnectioninstance)
- [Test-CsTeamsShiftsConnectionValidate](/powershell/module/teams/test-csteamsshiftsconnectionvalidate)
- [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap)
- [Fjern-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector)
- [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult)
- [Get-CsTeamsShiftsConnectionWfmUser](/powershell/module/teams/get-csteamsshiftsconnectionwfmuser)
- [Get-CsTeamsShiftsConnectionWfmTeam](/powershell/module/teams/get-csteamsshiftsconnectionwfmteam)
- [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport)
- [Fjern-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord)

## <a name="related-articles"></a>Relaterede artikler

- [Vagtforbindelser](shifts-connectors.md)
- [Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder-Workforce Management](shifts-connector-powershell-manage.md)
- [Administrer appen Vagter](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Oversigt over Teams PowerShell](/microsoftteams/teams-powershell-overview)
- [Reference til Teams PowerShell-cmdlet](/powershell/teams/intro)
