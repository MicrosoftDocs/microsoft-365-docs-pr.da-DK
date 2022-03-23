---
title: Offboard machine API
description: Få mere at vide om, hvordan du bruger en API til at offboarde en enhed fra Microsoft Defender til Slutpunkt.
keywords: API'er, graph api, understøttede API'er, indsamling af undersøgelsespakke
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
ms.openlocfilehash: 1279f7271abbd4086c946492e95daa52962dbae5
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63591137"
---
# <a name="offboard-machine-api"></a>Offboard machine API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Offboard-enhed fra Defender for Endpoint.

## <a name="limitations"></a>Begrænsninger

- Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Denne API understøttes Windows 11, Windows 10, version 1703 og nyere eller Windows Server 2019 og nyere.
>
> Denne API understøttes ikke på MacOS- eller Linux-enheder.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Use Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Machine.Offboard|'Offboard machine'
Delegeret (arbejds- eller skolekonto)|Machine.Offboard|'Offboard machine'

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have AD-rolle som "global administrator"
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

Computer-id'et kan findes i URL-adressen, når du vælger enheden. Generelt er det et alfanumerisk tal på 40 cifre, der kan findes i URL-adressen.

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
---|---|---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|streng|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
---|---|---
Kommenter|String|Kommentar, der skal knyttes til handlingen. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201 – Oprettet svarkode og [Computerhandling](machineaction.md) i svarteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
