---
title: Få domænerelaterede påmindelses-API'er
description: Få mere at vide om, hvordan du bruger Hent domænerelaterede påmindelses-API'er til at hente beskeder, der er relateret til en given domæneadresse i Microsoft Defender til slutpunkt.
keywords: API'er, graph api, understøttede API'er, hent, domæne, relaterede, beskeder
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
ms.openlocfilehash: b67b97ac115057b0e17bfd492e6330a13ee9e213
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592073"
---
# <a name="get-domain-related-alerts-api"></a>Få domænerelaterede påmindelses-API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling af beskeder [, der er](alerts.md) relateret til en bestemt domæneadresse.

## <a name="limitations"></a>Begrænsninger

- Du kan oprette en forespørgsel på beskeder, der senest er opdateret i henhold til din konfigurerede opbevaringsperiode.
- Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alert.Read.All|"Læs alle beskeder"
Program|Alert.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto)|Alert.Read|"Læsebeskeder"
Delegeret (arbejds- eller skolekonto)|Alert.ReadWrite|"Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)
> - Svaret omfatter kun beskeder, der er knyttet til enheder, som brugeren har adgang til, baseret på enhedsgrupperingsindstillinger (se Opret og administrer enhedsgrupper [for at](machine-groups.md) få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/domains/{domain}/alerts
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Sidehoved|Værdi|
|---|---|
|Godkendelse|String|

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og domænet findes – 200 OK med liste [over](alerts.md) enheder med påmindelser. Hvis domæne ikke findes – 200 OK med et tomt sæt.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/domains/client.wns.windows.com/alerts
```
