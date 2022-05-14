---
title: Profiler til vurdering af sikkerhedsgrundlinjer
description: Indeholder oplysninger om API'er til vurderingsprofiler for sikkerhedsgrundlinjer, der henter "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.
keywords: api, apis, eksportvurdering, vurdering pr. enhed, vurdering af maskine, vurderingsrapport for sårbarheder, vurdering af enhedssårbarhed, rapport over enhedssårbarhed, vurdering af sikker konfiguration, vurdering af softwaresårbarheder, rapport over softwaresårbarheder, sårbarhedsrapport efter maskine,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 301b586249268148ba005b193438937a1c55e46f
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417625"
---
# <a name="list-all-security-baselines-assessment-profiles"></a>Vis alle vurderingsprofiler for sikkerhedsgrundlinjer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender – Opdater](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender? [Tilmeld dig en gratis prøveversion.- Opdater](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-security-baselines-assessment-profiles"></a>1. Hent vurderingsprofiler for grundlinjer for sikkerhed

Denne API henter en liste over alle vurderingsprofiler for sikkerhedsgrundlinjer, der er oprettet af organisationen.

### <a name="11-parameters"></a>1.1 Parametre

- Understøtter OData V4-forespørgsler.
- OData-understøttede operatorer:
  - $filter på : id,navn, operatingSystem, operatingSystemVersion, status, settingsNumber, passedDevices, totalDevices
  - $top med en maksimumværdi på 10.000.
  - $skip.

### <a name="12-http-request"></a>1.2 HTTP-anmodning

```http
GET:/api/baselineProfiles
```

### <a name="13-request-headers"></a>1.3 Anmodningsheadere

Navn|Type|Beskrivelse
:---|:---|:---
Tilladelse|String|Ihændehaver {token}. **Påkrævet**.

### <a name="14-properties"></a>1.4 Egenskaber

|Ejendom | Type | Beskrivelse |
|:---|:---|:---|
|Id | String | Entydigt id for den specifikke grundlinjeprofil.
|Navn | String | Profilnavnet.
|Beskrivelse | String | Profilbeskrivelsen.
|Benchmark | String | Profilbenchmark.
|Version | String | Profilversionen.
|operatingSystem|String|Den profil, der gælder for operativsystemet.
|operatingSystemVersion|String|Den profil, der gælder for operativsystemets version.
|Status|Boolesk |Angiver, om profilen er aktiv eller ej
|complianceLevel|String|Det overholdelsesniveau, der er valgt for profilen.
|settingsNumber|Int|Antal valgte konfigurationer i profilen.
|createdBy|String|Den bruger, der oprettede denne profil.
|lastUpdatedBy|Datetime|Den sidste bruger, der redigerer denne profil.
|createdOnTimeOffset|Datetime|Den dato og det klokkeslæt, hvor profilen blev oprettet.
|lastUpdateTimeOffset|Datetime|Den dato og det klokkeslæt, hvor profilen sidst blev opdateret.
|passedDevices|Int|Antallet af enheder, der gælder for denne profil, som er kompatible med alle profilkonfigurationerne.
|totalDevices|Int|Antal enheder, der gælder for denne profil.

## <a name="15-example"></a>1.5 Eksempel

### <a name="151-request-example"></a>1.5.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/baselineProfiles
```

### <a name="162-response-example"></a>1.6.2 Svareksempel

```json
{
    "@odata.context": "https:// api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicBaselineProfileDto)",
    "value":
    [
        {
            "id": "02bcbb9d-d197-479e-811e-1cd5a6f9f8fa",
            "name": "Windows 10 build 1909 CIS profile",
            "description": "important",
            "benchmark": "CIS",
            "version": "1.0.0",
            "operatingSystem": "Windows 10",
            "operatingSystemVersion": "1909",
            "status": true,
            "complianceLevel": "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
            "settingsNumber": 51,
            "createdBy": "user@org.net",
            "lastUpdatedBy": null,
            "createdOnTimestampUTC": "0001-01-01T00:00:00Z",
            "lastUpdateTimestampUTC": "0001-01-01T00:00:00Z",
            "passedDevices": 0,
            "totalDevices": 10
        }
     ]
}
```

## <a name="see-also"></a>Se også

- [Eksportér vurdering af sikkerhedsbaselines](export-security-baseline-assessment.md)
- [Hent konfigurationer af vurdering af sikkerhedsgrundlinjer](get-security-baselines-assessment-configurations.md)
