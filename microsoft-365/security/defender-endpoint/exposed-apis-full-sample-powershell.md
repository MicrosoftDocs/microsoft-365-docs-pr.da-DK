---
title: Avanceret jagt med PowerShell API-vejledning
ms.reviewer: ''
description: Brug disse kodeeksempler, og forespørger på flere Microsoft Defender for Endpoint-API'er.
keywords: API'er, understøttede api'er, avanceret jagt, forespørgsel
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 09/24/2018
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6b1f501b942512500c11c7f9fe1e9308d67706e9
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593179"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>Microsoft Defender til slutpunkt-API'er ved hjælp af PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Fuldt scenarie ved brug af flere API'er fra Microsoft Defender til slutpunkt.

I dette afsnit deler vi PowerShell-eksempler til 
- Hent et token 
- Brug token til at hente de seneste beskeder i Microsoft Defender til Slutpunkt
- Hvis beskeden har mellem eller høj prioritet og stadig er i gang, skal du kontrollere, hvor mange gange enheden har oprettet forbindelse til mistænkelig URL-adresse for hver besked.

**Forudsætninger**: Du skal først [oprette en app](apis-intro.md).

## <a name="preparation-instructions"></a>Vejledning til forberedelse

- Åbn et PowerShell-vindue.
- Hvis din politik ikke tillader, at du kører PowerShell-kommandoerne, kan du køre nedenstående kommando:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Du kan finde flere oplysninger i [dokumentationen til PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Hent token

Kør nedenstående:

- $tenantId: Id for lejeren på vegne af hvilken du vil køre forespørgslen (dvs. forespørgslen køres på dataene for denne lejer)
- $appId: Id for din AAD-app (appen skal have tilladelsen "Kør avancerede forespørgsler" til Defender til slutpunkt)
- $appSecret: Hemmelig for din Azure AD-app

- $suspiciousUrl: URL-adressen


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>Se også
- [Microsoft Defender til endpoint-API'er](apis-intro.md)
- [Avanceret api til jagt](run-advanced-query-api.md)
- [Avanceret jagt ved hjælp af Python](run-advanced-query-sample-python.md)
