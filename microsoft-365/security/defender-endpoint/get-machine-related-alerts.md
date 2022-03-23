---
title: Hent API'er, der er relateret til maskiner
description: Få mere at vide om, hvordan du bruger Api'en Hent maskinrelaterede beskeder. Denne API gør det muligt at hente alle beskeder, der er relateret til en bestemt enhed i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, enheder, relaterede, beskeder
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
ms.openlocfilehash: 49cc0fca3ae7617b86ab079daace92eb3790db94
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63593444"
---
# <a name="get-machine-related-alerts--api"></a>Hent API'er, der er relateret til maskiner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter alle beskeder [, der er](alerts.md) relateret til en bestemt enhed.

## <a name="limitations"></a>Begrænsninger

1. Du kan forespørge på enheder, der senest er opdateret i henhold til din konfigurerede opbevaringsperiode.
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alert.Read.All|"Læs alle beskeder"
Program|Alert.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto) | Alert.Read | "Læsebeskeder"
Delegeret (arbejds- eller skolekonto) | Alert.ReadWrite | "Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have mindst følgende rolletilladelse: 'Vis data'. Du kan finde flere oplysninger om tilladelser i [Oprette og administrere roller](user-roles.md).
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder. Du kan finde flere oplysninger om indstillinger for enhedsgrupper [i Opret og administrer enhedsgrupper](machine-groups.md).

## <a name="http-request"></a>HTTP-anmodning

```http
GET /api/machines/{id}/alerts
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, og enheden findes: 200 OK [med liste over](alerts.md) enheder med vigtige beskeder i brødteksten. Hvis enheden ikke blev fundet: 404 Blev ikke fundet.
