---
title: Hent domænerelaterede maskiner API
description: Få mere at vide om, hvordan du bruger Get domain-related machines API til at få maskiner, der kommunikeres til eller fra et domæne i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, domæne, relaterede, enheder
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
ms.openlocfilehash: 179b3bf9ecd1ff7f7045f386d740eff4e83a12c9
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63591840"
---
# <a name="get-domain-related-machines-api"></a>Hent domænerelaterede maskiner API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter en samling af maskiner [, der](machine.md) har kommunikeret til eller fra en given domæneadresse.

## <a name="limitations"></a>Begrænsninger

1. Du kan forespørge på enheder, der senest er opdateret i henhold til din konfigurerede opbevaringsperiode.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.Read.All|"Læs alle maskinprofiler"
Program|Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.Read|"Læs maskinoplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.ReadWrite|"Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Få mere at vide under [Opret og administrer roller](user-roles.md)
> - Svaret inkluderer kun enheder, som brugeren har adgang til, baseret på enhedsgruppeindstillinger (Få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md)

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/domains/{domain}/machines
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og domænet findes – 200 OK med liste [over enheder](machine.md) på computeren. Hvis domænet ikke findes – 200 OK med et tomt sæt.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/domains/api.securitycenter.microsoft.com/machines
```
