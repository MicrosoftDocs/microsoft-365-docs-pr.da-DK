---
title: Avanceret api til jagt
ms.reviewer: ''
description: Lær at bruge den avancerede api til at køre avancerede forespørgsler på Microsoft Defender til slutpunkt. Få mere at vide om begrænsninger, og se et eksempel.
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
ms.openlocfilehash: 2e5898c0227128c099c7f0fe1ca99a6d9c8001ef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63606473"
---
# <a name="advanced-hunting-api"></a>Avanceret jagt-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="limitations"></a>Begrænsninger

1. Du kan kun køre en forespørgsel på data fra de seneste 30 dage.

2. Resultaterne medtager maksimalt 100.000 rækker.

3. Antallet af eksekveringer er begrænset pr. lejer:
   - API-opkald: Op til 45 opkald i minuttet, op til 1500 opkald pr. time.
   - Eksekveringstid: 10 minutters kørselstid hver time og 3 timers kørsel om dagen.

4. Den maksimale eksekveringstid for en enkelt anmodning er 10 minutter.

5. 429 svar repræsenterer at nå kvotegrænsen enten efter antal anmodninger eller efter CPU. Læs svarteksten for at forstå, hvilken grænse der er nået.

6. Den maksimale forespørgselsresultatstørrelse for en enkelt anmodning må ikke overstige 124 MB. Hvis overskredet, viser HTTP 400 Bad Request meddelelsen "Udførelse af forespørgsel har overskredet den tilladte resultatstørrelse. Optimer din forespørgsel ved at begrænse antallet af resultater, og prøv igen", vises.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|AdvancedQuery.Read.All|"Kør avancerede forespørgsler"
Delegeret (arbejds- eller skolekonto)|AdvancedQuery.Read|"Kør avancerede forespørgsler"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have AD-rolle "Vis data"
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>Anmod om brevhoveder

Sidehoved|Værdi
:---|:---
Godkendelse|Bearer {token}. **Påkrævet**.
Indholdstype|application/json

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
:---|:---|:---
Forespørgsel|Tekst|Den forespørgsel, der skal køres. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og _objektet QueryResponse_ i brødteksten.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

```json
{
    "Query":"DeviceProcessEvents
|where InitiatingProcessFileName =~ 'powershell.exe'
|where ProcessCommandLine contains 'appdata'
|project Timestamp, FileName, InitiatingProcessFileName, DeviceId
|limit 2"
}
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

> [!NOTE]
> Det svarobjekt, der er vist her, kan afkortes som korthed. Alle egenskaberne returneres fra et faktisk opkald.

```json
{
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Introduktion til Microsoft Defender til slutpunkts-API'er](apis-intro.md)
- [Avanceret jagt fra portal](advanced-hunting-query-language.md)
- [Avanceret jagt ved hjælp af PowerShell](run-advanced-query-sample-powershell.md)
