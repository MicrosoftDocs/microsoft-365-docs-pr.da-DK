---
title: Vejledning til avanceret jagt med Python-API
ms.reviewer: ''
description: Få mere at vide om, hvordan du forespørger ved hjælp af api'en Microsoft Defender for Endpoint ved hjælp af Python med eksempler.
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
ms.openlocfilehash: 99fc848088725f7b28d91eebc78327c688059de8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174764"
---
# <a name="advanced-hunting-using-python"></a>Avanceret jagt ved hjælp af Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Kør avancerede forespørgsler ved hjælp af Python, se [API til avanceret jagt](run-advanced-query-api.md).

I dette afsnit deler vi Python-eksempler for at hente et token og bruge det til at køre en forespørgsel.

> **Forudsætning**: Du skal først [oprette en app](apis-intro.md).

## <a name="get-token"></a>Hent token

- Kør følgende kommandoer:

```python
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

Hvor

- tenantId: Id'et for den lejer, som du vil køre forespørgslen på (dvs. forespørgslen køres på dataene i denne lejer)
- appId: Id'et for din Azure AD app (appen skal have tilladelsen 'Kør avancerede forespørgsler' for at Microsoft Defender for Endpoint)
- appSecret: Hemmeligheden ved din Azure AD-app

## <a name="run-query"></a>Kør forespørgsel

 Kør følgende forespørgsel:

```python
query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]
```

- skemaet indeholder skemaet over resultaterne af din forespørgsel
- resultaterne indeholder resultaterne af din forespørgsel

### <a name="complex-queries"></a>Komplekse forespørgsler

Hvis du vil køre komplekse forespørgsler (eller forespørgsler med flere linjer), skal du gemme forespørgslen i en fil og i stedet for den første linje i ovenstående eksempel køre kommandoen nedenfor:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Arbejd med forespørgselsresultater

Du kan nu bruge forespørgselsresultaterne.

Hvis du vil gentage resultaterne, skal du gøre følgende:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Hvis du vil sende resultaterne af forespørgslen i CSV-format i en fil file1.csv skal du gøre følgende:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Hvis du vil sende resultaterne af forespørgslen i JSON-format i filen file1.json, skal du gøre følgende:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>Relateret emne

- [Microsoft Defender for Endpoint API'er](apis-intro.md)
- [Avanceret jagt-API](run-advanced-query-api.md)
- [Avanceret jagt ved hjælp af PowerShell](run-advanced-query-sample-powershell.md)
