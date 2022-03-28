---
title: Avanceret jagt med Python API-vejledning
ms.reviewer: ''
description: Få mere at vide om, hvordan du forespørger ved hjælp af Microsoft Defender for Endpoint API ved hjælp af Python, med eksempler.
keywords: API'er, understøttede api'er, avanceret jagt, forespørgsel
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
ms.openlocfilehash: 73be2b3c2aa40bb88ac6ccff60eec5cb7f55338c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597476"
---
# <a name="advanced-hunting-using-python"></a>Avanceret jagt ved hjælp af Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Kør avancerede forespørgsler ved hjælp af Python, se [Avanceret jagt-API](run-advanced-query-api.md).

I dette afsnit deler vi Python-eksempler for at hente et token og bruge det til at køre en forespørgsel.

> **Forudsætninger**: Du skal først [oprette en app](apis-intro.md).

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

hvor

- tenantId: Id for lejeren på vegne af hvilken du vil køre forespørgslen (det vil sige, at forespørgslen køres på dataene for denne lejer)
- appId: Id for din Azure AD-app (appen skal have tilladelsen "Kør avancerede forespørgsler" til Microsoft Defender til slutpunkt)
- appSekret: Hemmeligheden bag din Azure AD-app

## <a name="run-query"></a>Kør forespørgsel

 Kør følgende forespørgsel:

```python
query = 'RegistryEvents | limit 10' # Paste your own query here

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

- skema indeholder skemaet for resultaterne af forespørgslen
- resultater indeholder resultaterne af din forespørgsel

### <a name="complex-queries"></a>Komplekse forespørgsler

Hvis du vil køre komplekse forespørgsler (eller forespørgsler med flere linjer), skal du gemme forespørgslen i en fil og, i stedet for den første linje i eksemplet ovenfor, køre nedenstående kommando:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>Arbejd med forespørgselsresultater

Du kan nu bruge forespørgselsresultaterne.

Hvis du vil genaktivere resultaterne, skal du gøre følgende:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

Hvis du vil have vist resultaterne af forespørgslen i CSV-format i file1.csv skal du gøre følgende:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

Gør følgende for at få vist resultaterne af forespørgslen i JSON-format i file file1.json:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>Relateret emne

- [Microsoft Defender til endpoint-API'er](apis-intro.md)
- [Avanceret api til jagt](run-advanced-query-api.md)
- [Avanceret jagt ved hjælp af PowerShell](run-advanced-query-sample-powershell.md)
