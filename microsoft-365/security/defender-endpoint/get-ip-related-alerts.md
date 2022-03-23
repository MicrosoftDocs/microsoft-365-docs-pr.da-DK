---
title: Få IP-relaterede påmindelses-API'er
description: Hent en samling af beskeder, der er relateret til en given IP-adresse ved hjælp af Microsoft Defender til slutpunkt
keywords: apis, graph api, understøttede API'er, hent, ip, relaterede, beskeder
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
ms.openlocfilehash: b46e67a6fe2d30a4b6480b88ea3a40f842227669
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63593544"
---
# <a name="get-ip-related-alerts-api"></a>Få IP-relaterede påmindelses-API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse
Henter en samling af beskeder, der er relateret til en given IP-adresse.


## <a name="limitations"></a>Begrænsninger
1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.


## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Use Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alert.Read.All|"Læs alle beskeder"
Program|Alert.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto) | Alert.Read | "Læsebeskeder"
Delegeret (arbejds- eller skolekonto) | Alert.ReadWrite | "Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data' (Se Oprette og administrere [roller for at](user-roles.md) få flere oplysninger)
> - Svaret omfatter kun beskeder, der er knyttet til enheder, som brugeren har adgang til, baseret på enhedsgrupperingsindstillinger (se Opret og administrer enhedsgrupper [for at](machine-groups.md) få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/ips/{ip}/alerts
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og IP findes – 200 OK [med liste over](alerts.md) enheder til påmindelsesbeskeder i brødteksten. Hvis IP-adressen er ukendt, men gyldig, returneres et tomt sæt.
Hvis IP-adressen er ugyldig, returneres HTTP 400.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/alerts
```
