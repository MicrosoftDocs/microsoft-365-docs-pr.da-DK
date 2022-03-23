---
title: Opdater enheds-API til påmindelse
description: Få mere at vide om, hvordan du opdaterer en microsoft Defender for Endpoint-besked ved hjælp af denne API. Du kan opdatere egenskaberne for status, bestemmelse, klassificering og tildeltTil.
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4efe1460374350d054bbe6d19543c75454d7b5ce
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63591305"
---
# <a name="update-alert"></a>Opdateringsbesked

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse
Opdaterer egenskaberne for eksisterende [besked](alerts.md).

Indsendelse af **kommentar er** tilgængelig med eller uden opdateringsegenskaber.

Egenskaber, der kan opdateres, er`determination`: `status`, `classification`, og `assignedTo`.

## <a name="limitations"></a>Begrænsninger

1. Du kan opdatere beskeder, der er tilgængelige i API'en. Du kan få mere at vide [under Listebeskeder](get-alerts.md).
2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alerts.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto)|Alert.ReadWrite|"Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Undersøgelse af beskeder" (Få mere at vide under [Opret og administrer roller](user-roles.md) )
> - Brugeren skal have adgang til den enhed, der er knyttet til beskeden, baseret på enhedsgrupperingsindstillinger (få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md)

## <a name="http-request"></a>HTTP-anmodning

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|String|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive værdierne for de relevante felter, der skal opdateres.

Eksisterende egenskaber, der ikke er inkluderet i brødteksten i anmodningen, bevarer deres tidligere værdier eller genberegnes baseret på ændringer i andre egenskabsværdier.

Du opnår den bedste ydeevne ved ikke at medtage eksisterende værdier, der ikke er blevet ændret.

Egenskab|Type|Beskrivelse
:---|:---|:---
Status|String|Angiver beskedens aktuelle status. Egenskabsværdierne er: "Ny", "InProgress" og "Løst".
assignedTo|String|Ejeren af beskeden
Klassificering|String|Angiver beskedens specifikation. Egenskabsværdierne er: 'Unknown', 'FalsePositive', 'TruePositive'.
Bestemmelse|String|Angiver bestemmelse af beskeden. Egenskabsværdierne er: "NotAvailable", "Apt", "Malware", "SecurityPersonnel", "SecurityTesting", "UnwantedSoftware", "Other"
Kommenter|String|Kommentar, der skal føjes til beskeden.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og [beskedenheden](alerts.md) i svarteksten med de opdaterede egenskaber. Hvis beskeden med det angivne id ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
PATCH https://api.securitycenter.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
