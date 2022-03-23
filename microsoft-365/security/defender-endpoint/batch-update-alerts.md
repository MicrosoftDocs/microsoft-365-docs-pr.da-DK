---
title: Api'en til batchopdateringsbeskeder
description: Få mere at vide om, hvordan du opdaterer Microsoft Defender for Endpoint-beskeder i en batch ved hjælp af denne API. Du kan opdatere egenskaberne for status, bestemmelse, klassificering og tildeltTil.
keywords: apis, graph api, understøttede API'er, hent, besked, oplysninger, id
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a2d695a2b406d4850f0e9896af3ec3b2aede8870
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592087"
---
# <a name="batch-update-alerts"></a>Beskeder om batchopdatering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API-beskrivelse

Opdaterer egenskaberne for en batch af [eksisterende beskeder](alerts.md).

Indsendelse af **kommentar er** tilgængelig med eller uden opdateringsegenskaber.

Egenskaber, der kan opdateres, er`determination`: `status`, `classification` og `assignedTo`.

## <a name="limitations"></a>Begrænsninger

1. Du kan opdatere beskeder, der er tilgængelige i API'en. Se [Listebeskeder for at](get-alerts.md) få flere oplysninger.
2. Begrænsningerne for denne API er 10 opkald i minuttet og 500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype | Tilladelse | Visningsnavn for tilladelse
:---|:---|:---
Program | Alert.ReadWrite.All | "Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto) | Alert.ReadWrite | "Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Undersøgelse af beskeder" (Se [Opret](user-roles.md) og administrer roller for at få flere oplysninger)
> - Brugeren skal have adgang til den enhed, der er knyttet til beskeden, baseret på enhedsgrupperingsindstillinger (Se Opret og [administrer enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.
Indholdstype | String | application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive værdierne for de vigtige beskeder, der skal opdateres, samt værdierne for de relevante felter, du vil opdatere for disse beskeder.

Eksisterende egenskaber, der ikke er inkluderet i brødteksten i anmodningen, bevarer deres tidligere værdier eller genberegnes baseret på ændringer i andre egenskabsværdier.

Du opnår den bedste ydeevne ved ikke at medtage eksisterende værdier, der ikke er blevet ændret.

Egenskab | Type | Beskrivelse
:---|:---|:---
alertIds | ListString&lt;&gt;| En liste over de beskeder, der skal opdateres. **Påkrævet**
status | String | Angiver den opdaterede status for de angivne beskeder. Egenskabsværdierne er: "Ny", "InProgress" og "Løst".
assignedTo | String | Ejer af de angivne beskeder
klassificering | String | Angiver specifikationen af de angivne beskeder. Egenskabsværdierne er: 'Unknown', 'FalsePositive', 'TruePositive'. 
determination | String | Angiver bestemmelse af de angivne beskeder. Egenskabsværdierne er: "NotAvailable", "Apt", "Malware", "SecurityPersonnel", "SecurityTesting", "UnwantedSoftware", "Other"
kommentar | String | Kommentar, der skal føjes til de angivne beskeder.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK med en tom svartekst.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
