---
title: Fjern appbegrænsnings-API
description: Brug denne API til at oprette opkald, der er relateret til at fjerne en begrænsning fra programmer, der udføres.
keywords: apis, graph api, understøttede API'er, fjern enheden fra isolation
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: c2fe35d73cd9abf3483c32067bf59334c6ad016b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592124"
---
# <a name="remove-app-restriction-api"></a>Fjern appbegrænsnings-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Aktivér udførelse af et hvilket som helst program på enheden.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Fuld isolation er tilgængelig for enheder på Windows 10 version 1703.
> - Selektiv isolation er tilgængelig for enheder på Windows 10, version 1709 eller nyere.
> - Når du isolerer en enhed, er det kun visse processer og destinationer, der er tilladt. Derfor kan enheder, der er bag en fuld VPN-slutpunkt, ikke nå Microsoft Defender til slutpunktsskytjenesten, når enheden er isoleret. Vi anbefaler, at du bruger et opdelt VPN til Microsoft Defender til slutpunkt og Microsoft Defender Antivirus skybaseret beskyttelsesrelateret trafik.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.RestrictExecution|'Begræns udførelse af kode'
Delegeret (arbejds- eller skolekonto)|Machine.RestrictExecution|'Begræns udførelse af kode'

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Aktive afhjælpningshandlinger" (Se [Opret og administrer](user-roles.md) roller for at få flere oplysninger)
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
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
Kommenter|String|Kommentar, der skal knyttes til handlingen. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201 – Oprettet svarkode og [Computerhandling](machineaction.md) i svarteksten.

Hvis du sender flere API-opkald for at fjerne appbegrænsninger for den samme enhed, returneres "afventende maskinhandling" eller HTTP 400 med meddelelsen "Handlingen er allerede i gang".

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

Hvis du vil begrænse udførelse af kode på en enhed, skal du [se Begræns udførelse af apps](restrict-code-execution.md).
