---
title: Annuller API til maskinel handling
description: Få mere at vide om, hvordan du annullerer en allerede startet computerhandling
keywords: apis, graf api,
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
ms.openlocfilehash: 08f302a541e60cb2844dc6ef2b91509556f03330
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873732"
---
# <a name="cancel-machine-action-api"></a>Annuller API til maskinel handling

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/defender-endpoint)
- [Microsoft Defender for Endpoint Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Annuller en allerede startet computerhandling, der endnu ikke er i endelig tilstand (fuldført, annulleret, mislykket).

## <a name="limitations"></a>Begrænsninger

1. Hastighedsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Kom i gang](apis-intro.md).

|Tilladelsestype|Tilladelse|Vist navn for tilladelse|
|---|---|---|
|Program|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|Indsaml tekniske oplysninger <br>Isoler maskine<br>Begræns kørsel af kode<br>  Scanningsmaskine<br>  offboard-maskine<br> Stop og sæt karantæne<br> Kør direkte svar på en bestemt maskine|
|Uddelegeret (arbejds- eller skolekonto)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|Indsaml tekniske oplysninger<br> Isoler maskine<br>  Begræns kørsel af kode<br> Scanningsmaskine<br>offboard-maskine<br> Stop og sæt karantæne<br> Kør direkte svar på en bestemt maskine|

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>Anmodningsheadere

|Navn|Type|Beskrivelse|
|---|---|---|
|Tilladelse|String|Ihændehaver {token}. Kræves.|
|Indholdstype|Streng|application/json. Kræves.|

## <a name="request-body"></a>Brødtekst i anmodning

|Parameter|Type|Beskrivelse|
|---|---|---|
|Kommenter|String|Kommentar, der skal knyttes til annulleringshandlingen.|

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med en computerhandlingsenhed. Hvis computerhandlingsenheden med det angivne id ikke blev fundet - 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmodning

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

- [Hent API til maskinel handling](get-machineaction-object.md)
