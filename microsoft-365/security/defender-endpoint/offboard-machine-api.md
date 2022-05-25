---
title: Api til offlinecomputer
description: Få mere at vide om, hvordan du bruger en API til at tage en enhed fra Microsoft Defender for Endpoint.
keywords: apis, graph api, understøttede API'er, indsaml undersøgelsespakke
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
ms.openlocfilehash: a9e46b428500b41b143585434f7a16c13227db1c
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669754"
---
# <a name="offboard-machine-api"></a>Api til offlinecomputer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Offboard-enhed fra Defender for Endpoint.

## <a name="limitations"></a>Begrænsninger

- Hastighedsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> Denne API understøttes på Windows 11, Windows 10, version 1703 og nyere eller Windows Server 2019 og nyere.
>
> Denne API understøttes ikke på MacOS- eller Linux-enheder.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Brug Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Machine.Offboard|'Offboard-maskine'
Uddelegeret (arbejds- eller skolekonto)|Machine.Offboard|'Offboard-maskine'

> [!NOTE]
> Når du henter et token ved hjælp af brugerlegitimationsoplysninger:
>
> - Brugeren skal have AD-rollen 'Global Administration'
> - Brugeren skal have adgang til enheden baseret på indstillinger for enhedsgrupper (se [Opret og administrer enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

Computer-id'et findes i URL-adressen, når du vælger enheden. Generelt er det et 40-cifret alfanumerisk tal, der kan findes i URL-adressen.

## <a name="request-headers"></a>Anmodningsheadere

Navn|Type|Beskrivelse
---|---|---
Tilladelse|String|Ihændehaver {token}. **Påkrævet**.
Indholdstype|Streng|application/json. **Påkrævet**.

## <a name="request-body"></a>Brødtekst i anmodning

Angiv følgende parametre for et JSON-objekt i anmodningens brødtekst:

Parameter|Type|Beskrivelse
---|---|---
Kommenter|String|Kommentar, der skal knyttes til handlingen. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 – Oprettet svarkode og [Computerhandling](machineaction.md) i svarbrødteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmodning

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
