---
title: Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder-Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du bruger PowerShell til at administrere din Shifts-forbindelse til Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 1064401dee3a25a7d1749db6e4a36a110f21da0b
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823966"
---
# <a name="use-powershell-to-manage-your-shifts-connection-to-blue-yonder-workforce-management"></a>Brug PowerShell til at administrere din Skift-forbindelse til Blue Yonder-Workforce Management

## <a name="overview"></a>Oversigt

[Med Microsoft Teams Shifts-connectoren til Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) kan du integrere Appen Shifts i Microsoft Teams med Blue Yonder-Workforce Management (Blue Yonder WFM). Når du har konfigureret en forbindelse, kan dine frontlinjemedarbejdere uden problemer få vist og administrere deres tidsplaner i Blue Yonder WFM inde fra Skift.

Du kan bruge [guiden Skifts-connector](shifts-connector-wizard.md) i Microsoft 365 Administration eller [PowerShell](shifts-connector-blue-yonder-powershell-setup.md) til at konfigurere en forbindelse. Når en forbindelse er konfigureret, kan du administrere den ved hjælp af [PowerShell-cmdlet'er til Shifts-connectoren](#shifts-connector-cmdlets).

I denne artikel beskrives det, hvordan du bruger PowerShell til at gøre følgende:

- [Kontrollér status for konfiguration af forbindelse](#check-connection-setup-status)
- [Få vist en fejlrapport for en forbindelse](#view-an-error-report-for-a-connection)
- [Løs forbindelsesfejl](#resolve-connection-errors)
- [Skift forbindelsesindstillinger](#change-connection-settings)
- [Fjern tilknytningen af et team fra én forbindelse, og knyt den til en anden forbindelse](#unmap-a-team-from-one-connection-and-map-it-to-another-connection)
- [Deaktiver synkronisering for en forbindelse](#disable-sync-for-a-connection)

> [!NOTE]
> I denne artikel antages det, at du allerede har konfigureret en forbindelse til Blue Yonder WFM enten ved hjælp af guiden eller PowerShell.

## <a name="before-you-begin"></a>Før du begynder

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>Konfigurer dit miljø

> [!NOTE]
> Sørg for at følge disse trin for at konfigurere dit miljø, før du kører kommandoer eller scripts i denne artikel.

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

7. Opret forbindelse til Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    Når du bliver bedt om det, skal du logge på med dine administratorlegitimationsoplysninger. Du er nu konfigureret til at køre scripts i denne artikel og Shifts-connector-cmdlet'er.

## <a name="check-connection-setup-status"></a>Kontrollér status for konfiguration af forbindelse

<a name="setup_status"> </a>

Hvis du vil kontrollere status for den forbindelse, du har konfigureret, ved hjælp af det handlings-id, du har modtaget i mailen:

1. [Konfigurer dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det).
1. Kør følgende kommando. Denne kommando giver dig den overordnede status for teamtilknytningerne for forbindelsen.

    ``` powershell
    Get-CsTeamsShiftsConnectionOperation -OperationId <YourOperationId>
    ```

Du kan få mere at vide under [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation).

## <a name="view-an-error-report-for-a-connection"></a>Få vist en fejlrapport for en forbindelse

<a name="error_report"> </a>

Du kan køre en rapport, der viser fejloplysninger for en forbindelse. Rapporten viser team- og brugertilknytninger, der lykkedes og mislykkedes. Den indeholder også oplysninger om eventuelle problemer, der er relateret til de konti, der er knyttet til forbindelsen.

1. [Konfigurer dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det).
1. Hent en liste over fejlrapporter for en forbindelse.

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Kør følgende kommando for at få vist en bestemt fejlrapport:

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ErrorReportId <ErrorReportId>
    ```

Du kan få mere at vide under [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport).

## <a name="resolve-connection-errors"></a>Løs forbindelsesfejl

### <a name="user-mapping-errors"></a>Fejl i brugertilknytning

Der kan opstå fejl i brugertilknytningen, hvis en eller flere brugere i en Blue Yonder-WFM forekomst ikke er medlem af det tilknyttede team i Teams. Du kan løse dette problem ved at sikre, at brugerne i det tilknyttede team stemmer overens med brugerne i den blå yonder-forekomst WFM forekomst.

Hvis du vil have vist oplysninger om ikke-tilknyttede brugere, skal du [konfigurere dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det) og derefter køre følgende script.

```powershell
#View sync errors script
Write-Host "View sync errors"
Start-Sleep 1

#Ensure Teams module is of version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to retrieve user sync results from'
}
else {
    throw "Instance list is empty"
}

#Get a list of the mappings
Write-Host "Listing team mappings"
$mappings = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $mappings

#For each mapping, retrieve the failed mappings
ForEach ($mapping in $mappings){
    $teamsTeamId = $mapping.TeamId
    $wfmTeamId = $mapping.WfmTeamId
    Write-Host "Failed mapped users in the mapping of ${teamsTeamId} and ${wfmTeamId}:"
    $userSyncResult = Get-CsTeamsShiftsConnectionSyncResult -ConnectorInstanceId $InstanceId -TeamId $teamsTeamId
    Write-Host "Failed AAD users:"
    write $userSyncResult.FailedAadUser
    Write-Host "Failed WFM users:"
    write $userSyncResult.FailedWfmUser
}
```

### <a name="account-authorization-errors"></a>Kontogodkendelsesfejl

Der kan opstå fejl i forbindelse med godkendelse af kontoen, hvis blue yonder-WFM-tjenestekontoen eller legitimationsoplysningerne til Microsoft 365-systemkontoen er forkerte eller ikke har de nødvendige tilladelser.

Hvis du vil ændre din Blue Yonder WFM-tjenestekonto eller legitimationsoplysninger til Microsoft 365-systemkontoen for forbindelsen, kan du køre [Cmdlet'en Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) eller bruge PowerShell-scriptet i afsnittet [Skift forbindelsesindstillinger](#change-connection-settings) i denne artikel.

## <a name="change-connection-settings"></a>Skift forbindelsesindstillinger
<a name="change_settings"> </a>

Brug dette script til at ændre forbindelsesindstillingerne. Indstillinger, som du kan ændre, omfatter din Blue Yonder-WFM-tjenestekonto og -adgangskode, Microsoft 365-systemkonto, teamtilknytninger og synkroniseringsindstillinger.

Synkroniseringsindstillinger omfatter synkroniseringshyppigheden (i minutter) og de tidsplandata, der synkroniseres mellem Blue Yonder WFM og Skift. Planlægningsdata defineres i følgende parametre, som du kan få vist ved at køre [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

- Parameteren **enabledConnectorScenarios** definerer data, der synkroniseres fra Blue Yonder WFM til Skift. Indstillingerne er `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift``OpenShiftRequest`, , `TimeOff`, `TimeOffRequest`.
- Parameteren **enabledWfiScenarios** definerer data, der synkroniseres fra Skift til Blue Yonder WFM. Indstillingerne er `SwapRequest`, `OpenShiftRequest`, `TimeOffRequest`, `UserShiftPreferences`.

    > [!NOTE]
    > Hvis du vælger ikke at synkronisere åbne skiftehold, anmodninger om åbning af skiftehold, swapanmodninger eller anmodninger om fridag mellem Skift og Blue Yonder WFM, er der endnu et trin, du skal udføre for at skjule funktionen i Skift. Når du har kørt dette script, skal du sørge for at følge trinnene i afsnittet [Deaktiver åbne skiftehold, anmodninger om åbning af skiftehold, swapanmodninger og anmodninger om fridag](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) senere i denne artikel.

> [!IMPORTANT]
> I forbindelse med indstillinger, du ikke vil ændre, skal du angive de oprindelige indstillinger igen, når du bliver bedt om det af scriptet.

[Konfigurer dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det), og kør derefter følgende script.

```powershell
#Update connector instance and mapping script
Write-Host "Update connector instance and mapping"
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

#List connection instances available
Write-Host "Listing connection instances available"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Prompt for the WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Get the instance ID
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$InstanceId = Read-Host -Prompt 'Input the instance ID that you want to update'
$Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
$Etag = $Instance.etag

#Change sync setting
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$UpdatedInstanceName = Read-Host -Prompt 'Input new connection instance name'
$updatedConnectorScenarioString = Read-Host -Prompt 'Input new enabled connector scenarios'
$updatedWfiScenarioString = Read-Host -Prompt 'Input new enabled WFI scenarios'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$updatedConnectorScenario = $updatedConnectorScenarioString -Split {$Delimiters -contains $_}
$updatedConnectorScenario = $updatedConnectorScenario.Trim()
$updatedConnectorScenario = $updatedConnectorScenario.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
$updatedWfiScenario = $updatedWfiScenarioString -Split {$Delimiters -contains $_}
$updatedWfiScenario = $updatedWfiScenario.Trim()
$updatedWfiScenario = $updatedWfiScenario.Split('', [System.StringSplitOptions]::RemoveEmptyEntries)
$adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
$cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
$essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
$federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
$retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
$siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
$syncFreq = Read-Host -Prompt 'Input new sync frequency'

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
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $teamsUserId -EnabledConnectorScenario $updatedConnectorScenario -EnabledWfiScenario $updatedWfiScenario -Name $UpdatedInstanceName -SyncFrequencyInMin $syncFreq -IfMatch $Etag -ConnectorAdminEmail $AdminEmailList

#Get a list of the mappings
Write-Host "Listing mappings"
$TeamMaps = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $TeamMaps

#Modify a mapping
#Remove a mapping
Write-Host "Removing a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to unlink'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to unlink'
Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId
Write-Host "Success"

#Add a mapping
Write-Host "Adding a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to link'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to link'
New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"
```

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>Deaktiver åbne skiftehold, anmodninger om åbne skiftehold, byt om på anmodninger og anmodninger om fridag

> [!IMPORTANT]
> Følg kun disse trin, hvis du har valgt at deaktivere åbne skiftehold, anmodninger om åbning af skiftehold, ombytningsanmodninger eller anmodninger om fridag ved hjælp af scriptet i afsnittet [Skift forbindelsesindstillinger](#change-connection-settings) tidligere i denne artikel eller ved hjælp af [Set-CsTeamsShiftsConnectionInstance-cmdlet'en](/powershell/module/teams/set-csteamsshiftsconnectioninstance) . Når du fuldfører dette trin, skjules funktionen i Skift. Uden dette andet trin kan brugerne stadig se funktionen i Skift og får vist fejlmeddelelsen "ikke-understøttet handling", hvis de forsøger at bruge den.

Hvis du vil skjule åbne skiftehold, bytte om på anmodninger og anmodninger om fridag i Skift, skal du bruge Graph [API-planlægningsressourcetypen](/graph/api/resources/schedule) til at angive følgende parametre for ```false``` hvert team, du har knyttet til en Blue Yonder-WFM forekomst:

- Åbne skiftehold: ```openShiftsEnabled```
- Byt om på anmodninger:  ```swapShiftsRequestsEnabled```
- Anmodninger om fridag: ```timeOffRequestsEnabled```

Hvis du vil skjule anmodninger om åbne skiftehold i Skiftehold, skal du gå til **Indstillinger** i Skift og derefter slå indstillingen **Åbn skift** fra.

## <a name="unmap-a-team-from-one-connection-and-map-it-to-another-connection"></a>Fjern tilknytningen af et team fra én forbindelse, og knyt den til en anden forbindelse

> [!NOTE]
> Microsoft 365-systemkontoen skal være den samme for begge forbindelser. Hvis den ikke er det, får du vist fejlmeddelelsen "Denne udpegede agentprofil har ikke teamejerskabsrettigheder".

Hvis du vil fjerne tilknytningen af et team fra én forbindelse og knytte den til en anden forbindelse:

1. [Konfigurer dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det).
1. Få vist en liste over alle teamtilknytninger for en forbindelse.

    ```powershell
    Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Fjern en gruppetilknytning fra forbindelsen.

    ```powershell
    Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId>
    ```

1. Knyt teamet til en anden forbindelse.

    ```powershell
    New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId> -WfmTeamId <SiteId> -TimeZone <TimeZone>
    ```

Du kan få mere at vide under [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap), [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) og [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap).

## <a name="disable-sync-for-a-connection"></a>Deaktiver synkronisering for en forbindelse

Brug dette script til at deaktivere synkronisering for en forbindelse. Vær opmærksom på, at dette script ikke fjerner eller sletter en forbindelse. Det slår synkronisering fra, så ingen data synkroniseres mellem Skift og Blue Yonder WFM for den forbindelse, du angiver.

[Konfigurer dit miljø](#set-up-your-environment) (hvis du ikke allerede har gjort det), og kør derefter følgende script.

```powershell
#Disable sync script
Write-Host "Disable sync"
#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to disable sync'
    $Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
    $Etag = $Instance.etag
    $InstanceName = $Instance.Name
    $DesignatedActorId = $Instance.designatedActorId
    $adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
    $cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
    $essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
    $federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
    $retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
    $siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
    $ConnectorAdminEmail = $Instance.ConnectorAdminEmail
}
else {
    throw "Instance list is empty"
}

#Remove scenarios in the mapping
Write-Host "Disabling scenarios in the team mapping"
$UpdatedInstanceName = $InstanceName + " - Disabled"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $DesignatedActorId -EnabledConnectorScenario @() -EnabledWfiScenario @() -Name $UpdatedInstanceName -SyncFrequencyInMin 60 -IfMatch $Etag -ConnectorAdminEmail $ConnectorAdminEmail

if ($UpdatedInstance.Id -ne $null) {
    Write-Host "Success"
}
else {
    throw "Update instance failed"
}
```

## <a name="shifts-connector-cmdlets"></a>Skifter forbindelses-cmdlet'er

Hvis du vil have hjælp til Shifts-connector-cmdlet'er, skal du søge efter **CsTeamsShiftsConnection** i [Teams PowerShell-cmdlet-referencen](/powershell/teams/intro). Her er links til nogle almindeligt anvendte cmdlet'er.

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

- [Skifter forbindelse](shifts-connectors.md)
- [Brug guiden Skifts-connector til at forbinde Shifts med blåt Workforce Management](shifts-connector-wizard.md)
- [Brug PowerShell til at forbinde Skift til Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)
- [Administrer appen Skift](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Oversigt over Teams PowerShell](/microsoftteams/teams-powershell-overview)
