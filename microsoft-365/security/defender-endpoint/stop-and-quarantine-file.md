---
title: Stop og karantæne fil-API
description: Få mere at vide om, hvordan du stopper med at køre en fil på en enhed og sletter filen i Microsoft Defender til slutpunkt. Se et eksempel.
keywords: API'er, graph api, understøttede API'er, stop- og karantænefil
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
ms.openlocfilehash: 1f61e238030c5c8c31e514ef76cf90ffc4b5bd92
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591229"
---
# <a name="stop-and-quarantine-file-api"></a>Stop og karantæne fil-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Stop udførelse af en fil på en enhed, og slet den.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
> Du kan kun gøre følgende, hvis:
>
> - Den enhed, du tager handlingen på, kører Windows 10 version 1703 eller nyere eller Windows 11
> - Filen tilhører ikke udgivere, der er tillid til, eller som ikke er signeret af Microsoft
> - Microsoft Defender Antivirus skal som minimum køre i passiv tilstand. Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)


## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.StopAndQuarantine|"Stop og karantæne"
Program|Machine.Read.All|"Læs alle maskinprofiler"
Program|Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.StopAndQuarantine|"Stop og karantæne"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Aktive afhjælpningshandlinger" (Se [Opret og administrer](user-roles.md) roller for at få flere oplysninger)
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/StopAndQuarantineFile
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
Sha1|String|Sha1 af filen, der skal stoppes og sætte i karantæne på enheden. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201 – Oprettet svarkode og [Computerhandling](machineaction.md) i svarteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/StopAndQuarantineFile 
```

```json
{
  "Comment": "Stop and quarantine file on machine due to alert 441688558380765161_2136280442",
  "Sha1": "87662bc3d60e4200ceaf7aae249d1c343f4b83c9"
}
```
