---
title: Send eller opdater indikator-API
description: Få mere at vide om, hvordan du bruger Send eller opdater indikator-API'en til at indsende eller opdatere en ny Indikator-enhed i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, indsend, ti, indikator, opdatering
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
ms.openlocfilehash: a3fc1a0ce2f7d02ad8ed6804b99621f78fb859d3
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63592009"
---
# <a name="submit-or-update-indicator-api"></a>Send eller opdater indikator-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Sender eller opdaterer den nye [enhed](ti-indicator.md) Indikator.

CIDR-notation for IP'er understøttes ikke.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.
2. Der er en grænse på 15.000 aktive indikatorer pr. lejer.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Ti.ReadWrite|"Læs og skriv Indikatorer"
Program|Ti.ReadWrite.All|"Læs og skriv alle indikatorer"
Delegeret (arbejds- eller skolekonto)|Ti.ReadWrite|"Læs og skriv Indikatorer"

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|streng|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
:---|:---|:---
indicatorValue|String|Identiteten på [indikatorobjektet](ti-indicator.md) . **Påkrævet**
indicatorType|Enum|Type af indikatoren. De mulige værdier er: "FileSha1", "FileMd5", "CertificateThumbprint", "FileSha256", "IpAddress", "DomainName" og "URL". **Påkrævet**
handling|Enum|Den handling, der skal anvendes, hvis indikatoren findes i organisationen. Mulige værdier er: "Påmindelse", "Advar", "Bloker", "Overvågning, "BlokAndRemediate", "AlertAndBlock" og "Tilladt". **Påkrævet**. Parameteren "GenerateAlert" skal være angivet til "SAND", når du opretter en handling med "Overvågning".
program|String|Det program, der er knyttet til indikatoren. Dette felt fungerer kun for nye indikatorer. Den opdaterer ikke værdien på en eksisterende indikator. **Valgfrit**
titel|String|Titel på indikatormeddelelse. **Påkrævet**
beskrivelse|String|Beskrivelse af indikatoren. **Påkrævet**
expirationTime|DateTimeOffset|Indikatorens udløbstidspunkt. **Valgfrit**
alvorsgrad|Enum|Alvorsgrad for indikatoren. De mulige værdier er: "Informational", "Lav", "Mellem" og "Høj". **Valgfrit**
recommendedActions|String|Anbefalede handlinger for TI-indikatorbeskeder. **Valgfrit**
rbacGroupNames|String|Kommasepareret liste over RBAC-gruppenavne, som indikatoren ville blive anvendt på. **Valgfrit**
generateAlert|Enum|**Sand** , hvis generering af beskeder er **påkrævet, Falsk** , hvis denne indikator ikke bør generere en besked.
## <a name="response"></a>Svar

- Hvis det lykkes, returnerer denne metode 200 - OK-svarkode og den oprettede [/opdaterede](ti-indicator.md) indikatorenhed i svarteksten.
- Hvis det ikke lykkes: Denne metode returnerer 400 – dårlig anmodning. Dårlig anmodning angiver normalt forkert brødtekst.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

```json
{
    "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
    "indicatorType": "FileSha1",
    "title": "test",
    "application": "demo-test",
    "expirationTime": "2020-12-12T00:00:00Z",
    "action": "AlertAndBlock",
    "severity": "Informational",
    "description": "test",
    "recommendedActions": "nothing",
    "rbacGroupNames": ["group1", "group2"]
}
```

## <a name="related-topic"></a>Relateret emne

- [Administrer indikatorer](manage-indicators.md)
