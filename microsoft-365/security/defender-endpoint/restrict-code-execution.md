---
title: Begræns appudførelses-API
description: Brug denne API til at oprette opkald, der er relateret til at begrænse et program i at blive udført.
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
ms.openlocfilehash: dee5ad9466793892d09af2f85faa9f3fd2348ca6
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63595861"
---
# <a name="restrict-app-execution-api"></a>Begræns appudførelses-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Begræns udførelsen af alle programmer på enheden undtagen et foruddefineret sæt.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

[!include[Device actions note](../../includes/machineactionsnote.md)]


> [!IMPORTANT]
>
> - Denne handling er tilgængelig for enheder på Windows 10, version 1709 eller nyere, og Windows 11.
> - Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus.
> - Denne handling skal opfylde politikformaterne Windows Defender af kodeintegritet i programkontrolprogrammet og krav til signering. Du kan finde flere oplysninger under [Formater for politik for kodeintegritet og signering](/windows/device-security/device-guard/requirements-and-deployment-planning-guidelines-for-device-guard#code-integrity-policy-formats-and-signing).

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
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
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

Hvis du sender flere API-opkald for at begrænse udførelse af apps for den samme enhed, returneres "afventende maskinhandling" eller HTTP 400 med meddelelsen "Handlingen er allerede i gang".

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}
```

- Hvis du vil fjerne begrænsningen for udførelse af kode fra en enhed, skal du [se Fjern appbegrænsning](unrestrict-code-execution.md).
