---
title: Grundlæggende oplysninger om avanceret jagt med PowerShell API
ms.reviewer: ''
description: Få grundlæggende oplysninger om, hvordan du forespørger Microsoft Defender for Endpoint-API'en ved hjælp af PowerShell.
keywords: apis, understøttede API'er, avanceret jagt, forespørgsel
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc0cae0ff8c45f4c32213130773e3c118d779ed6
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243134"
---
# <a name="advanced-hunting-using-powershell"></a>Avanceret jagt ved hjælp af PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Kør avancerede forespørgsler ved hjælp af PowerShell under [API til avanceret jagt](run-advanced-query-api.md).

I dette afsnit deler vi PowerShell-eksempler for at hente et token og bruge det til at køre en forespørgsel.

## <a name="before-you-begin"></a>Før du begynder
Du skal først [oprette en app](apis-intro.md).

## <a name="preparation-instructions"></a>Forberedelsesinstruktioner

- Åbn et PowerShell-vindue.

- Hvis politikken ikke tillader, at du kører PowerShell-kommandoerne, kan du køre følgende kommando:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

Du kan få flere oplysninger i [PowerShell-dokumentationen](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>Hent token

- Kør følgende:

```powershell
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$body = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$response = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $body -ErrorAction Stop
$aadToken = $response.access_token
```

Hvor
- $tenantId: Id'et for den lejer, som du vil køre forespørgslen på (dvs. forespørgslen køres på dataene i denne lejer)
- $appId: Id'et for din Azure AD app (appen skal have tilladelsen 'Kør avancerede forespørgsler' til Defender for Endpoint)
- $appSecret: Hemmeligheden bag din Azure AD app

## <a name="run-query"></a>Kør forespørgsel

Kør følgende forespørgsel:

```powershell
$query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

$url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$body = ConvertTo-Json -InputObject @{ 'Query' = $query }
$webResponse = Invoke-WebRequest -Method Post -Uri $url -Headers $headers -Body $body -ErrorAction Stop
$response =  $webResponse | ConvertFrom-Json
$results = $response.Results
$schema = $response.Schema
```

- $results indeholder resultaterne af forespørgslen
- $schema indeholder skemaet over resultaterne af forespørgslen

### <a name="complex-queries"></a>Komplekse forespørgsler

Hvis du vil køre komplekse forespørgsler (eller forespørgsler med flere linjer), skal du gemme forespørgslen i en fil og i stedet for den første linje i ovenstående eksempel køre følgende kommando:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>Arbejd med forespørgselsresultater

Du kan nu bruge forespørgselsresultaterne.

Kør følgende kommando for at sende resultaterne af forespørgslen i CSV-format i file1.csv:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

Kør følgende kommando for at sende resultaterne af forespørgslen i JSON-format i filen file1.json:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>Relateret emne
- [Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Avanceret jagt-API](run-advanced-query-api.md)
- [Avanceret jagt ved hjælp af Python](run-advanced-query-sample-python.md)
