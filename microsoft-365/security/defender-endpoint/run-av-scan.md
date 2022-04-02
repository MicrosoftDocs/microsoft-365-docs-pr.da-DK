---
title: Kør antivirus-scannings-API
description: Brug denne API til at oprette opkald, der er relateret til at køre en antivirus-scanning på en enhed.
keywords: apis, graph api, understøttede API'er, fjern enheden fra isolation
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
ms.openlocfilehash: 3208ff32c2adda051b79fea684af915a909dd062
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63603144"
---
# <a name="run-antivirus-scan-api"></a>Kør antivirus-scannings-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Initier Microsoft Defender Antivirus scanning på en enhed.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Denne handling er tilgængelig for enheder på Windows 10, version 1709 eller nyere, og Windows 11.
> - En Microsoft Defender Antivirus (Microsoft Defender AV) kan køre sammen med andre antivirusløsninger, uanset om Microsoft Defender Antivirus er den aktive antivirusløsning eller ej. Microsoft Defender Antivirus kan være i passiv tilstand. Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility)

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.Scan|'Scanningsmaskine'
Delegeret (arbejds- eller skolekonto)|Machine.Scan|'Scanningsmaskine'

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Aktive afhjælpningshandlinger" (Se [Opret og administrer](user-roles.md) roller for at få flere oplysninger)
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/runAntiVirusScan
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|streng|application/json

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
:---|:---|:---
Kommenter|String|Kommentar, der skal knyttes til handlingen. **Påkrævet**.
ScanType|String|Definerer typen af scanningen. **Påkrævet**.

**ScanType** styrer typen af scanning, der skal udføres, og kan være et af følgende:

- **Hurtig**: Udfør en hurtig scanning på enheden
- **Fuld**: Udfør en fuld scanning på enheden

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201, Oprettet svarkode og _MachineAction-objektet_ i svarteksten.

Hvis du sender flere API-opkald for at køre en antivirusscanning for den samme enhed, returneres "afventende computerhandling" eller HTTP 400 med meddelelsen "Handlingen er allerede i gang".

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runAntiVirusScan 
```

```json
{
  "Comment": "Check machine for viruses due to alert 3212",
  "ScanType": "Full"
}
```
