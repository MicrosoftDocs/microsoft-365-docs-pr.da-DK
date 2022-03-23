---
title: Annuller computerhandlings-API
description: Få mere at vide om, hvordan du annullerer en allerede startet computerhandling
keywords: apis, graph api,
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fc4191043e19df7fea4f350d85acd78d2eca1551
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592242"
---
# <a name="cancel-machine-action-api"></a>Annuller computerhandlings-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Annuller en allerede startet computerhandling, der endnu ikke er i den endelige tilstand (fuldført, annulleret, mislykkedes).

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md).

|Tilladelsestype|Tilladelse|Visningsnavn for tilladelse|
|---|---|---|
|Program|Machine.CollectForensics <br> Machine.Isoler <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Indsaml forskellige eksempler <br>Isoler maskine<br>Begræns udførelse af kode<br>  Scanningsmaskine<br>  Offboard machine<br> Stop og karantæne<br> Kør live svar på en bestemt computer|
|Delegeret (arbejds- eller skolekonto)|Machine.CollectForensics<br> Machine.Isoler  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Indsaml forskellige eksempler<br> Isoler maskine<br>  Begræns udførelse af kode<br> Scanningsmaskine<br>Offboard machine<br> Stop og karantæne<br> Kør live svar på en bestemt computer|

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Navn|Type|Beskrivelse|
|---|---|---|
|Godkendelse|String|Bearer {token}. Påkrævet.|
|Indholdstype|streng|application/json. Påkrævet.|

## <a name="request-body"></a>Anmodningstekst

|Parameter|Type|Beskrivelse|
|---|---|---|
|Kommenter|String|Kommentar, der skal knyttes til annulleringshandlingen.|

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med en computerhandlingsenhed. Hvis maskinhandlingsenhed med det angivne id ikke blev fundet – 404 Blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```HTTP
POST
https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/cancel
```

```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```

## <a name="related-topic"></a>Relateret emne

- [Hent computerhandlings-API](get-machineaction-object.md)
