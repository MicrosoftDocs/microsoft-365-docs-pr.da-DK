---
title: Konfigurationer af vurdering af sikkerhedsgrundlinjer
description: Indeholder oplysninger om konfigurationer af vurdering af sikkerhedsgrundlinjer, der henter "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.
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
ms.openlocfilehash: 4a9b75698227c86c58255bad4e3336157c179c4a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419047"
---
# <a name="list-security-baselines-assessment-configurations"></a>Angiv vurderingskonfigurationer for sikkerhedsbaselines

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender – Opdater](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender? [Tilmeld dig en gratis prøveversion.- Opdater](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-all-security-baselines-assessment-configurations"></a>1. Hent alle konfigurationer af vurdering af grundlæggende sikkerhedsgrundlinjer

Denne API henter en liste over alle de mulige konfigurationer og indstillinger for vurdering af sikkerhedsgrundlinjer for alle tilgængelige benchmarks.

### <a name="11-parameters"></a>1.1 Parametre

- Understøtter OData V4-forespørgsler
- OData-understøttede operatorer:
  - `$filter` den: `id`, `category`, `name`, `CCE`
  - `$top` med en maksimumværdi på 10.000
  - `$skip`

### <a name="12-http-request"></a>1.2 HTTP-anmodning

```http
GET /api/baselineConfigurations 
```

### <a name="13-request-headers"></a>1.3 Anmodningsheadere

Navn|Type|Beskrivelse
:---|:---|:---
Tilladelse|String|Ihændehaver {token}. **Påkrævet**.

### <a name="14-response"></a>1.4 Svar

Hvis det lykkes, returnerer denne metode 200 OK med listen over grundlæggende konfigurationer i brødteksten.

### <a name="15-properties"></a>1.5 Egenskaber

|Ejendom | Type | Beskrivelse |
|:---|:---|:---|
|Id | String | Entydigt id for den specifikke konfiguration i den oprindelige benchmark.
|Navn | String | Konfigurationsnavnet på den vises i benchmarket.
|Beskrivelse | String | Konfigurationsbeskrivelsen, som den vises i benchmarket.
|Kategori | String | Konfigurationskategorien, som den vises i benchmarket.
|complianceLevel|String|Overholdelsesniveauet for det benchmark, hvor denne konfiguration vises.
|`cce`|Int|CCE for denne konfiguration, som den vises i benchmarket.
|Begrundelse |String|Begrundelsen for denne konfiguration, som det fremgår af benchmarket. For STIG-benchmark leveres dette ikke til denne konfiguration.

## <a name="16-example"></a>1.6 Eksempel

### <a name="151-request-example"></a>1.5.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/baselineConfigurations
```

### <a name="162-response-example"></a>1.6.2 Svareksempel

```json
{
    "@odata.context": " https://api-df.securitycenter.microsoft.com/api/$metadata#BaselineConfigurations ", 
    "value": [
        {
            "id": "1.1.8", 
            "name": "(L1) Ensure 'Allow importing of payment info' is set to 'Disabled'",
            "description": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">This policy setting controls whether users are able to import payment information from another browser into Microsoft Edge as well as whether payment information is imported on first use.</p>",
            "category": "Microsoft Edge",
            "complianceLevels": [
                "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
                "Level 2 (L2) - High Security/Sensitive Data Environment (limited functionality)"
            ],
            "cce": "",
            "rationale": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">Having payment information automatically imported or allowing users to import payment data from another browser into Microsoft Edge could allow for sensitive data to be imported into Edge.</p>",
            "remediation": "<div xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">\r\n  <p>\r\n    <p>\r\nTo establish the recommended configuration via GP, set the following UI path to                 <span class=\"inline_block\">Disabled</span></p>\r\n    <code class=\"code_block\">Computer Configuration\\Policies\\Administrative Templates\\Microsoft Edge\\Allow importing of payment info\r\n</code>\r\n    <p>\r\n      <strong>Note:</strong>\r\n This Group Policy path may not exist by default. It is provided by the Group Policy template                 <span class=\"inline_block\">MSEdge.admx/adml</span>\r\n that can be downloaded from Microsoft                 <a href=\"https://www.microsoft.com/en-us/edge/business/download\">here</a>\r\n.              </p>\r\n    <p class=\"bold\">Impact:</p>\r\n    <p>\r\n      <p>Users will be unable to perform a payment information import from other browsers into Microsoft Edge.</p>\r\n    </p>\r\n  </p>\r\n</div>",
            "benchmarkName": "CIS"
"recommendedValue": [ 
                "Equals '0'" 
            ], 
            "source": [ 
                "hkey_local_machine\\software\\policies\\microsoft\\windows\\eventlog\\security\\retention" 
            ]
        }, 
    ] 
} 
```

## <a name="see-also"></a>Se også

- [Eksportér vurdering af sikkerhedsbaselines](export-security-baseline-assessment.md)
- [Hent vurderingsprofiler for sikkerhedsgrundlinjer](get-security-baselines-assessment-profiles.md)
