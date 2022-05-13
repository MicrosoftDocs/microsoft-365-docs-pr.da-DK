---
title: Metoder og egenskaber til vurdering af sikkerhedsgrundlinje pr. enhed
description: Indeholder oplysninger om API'er til grundlinjer for sikkerhed, der henter "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.
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
ms.openlocfilehash: 730eb90202acff9efad1cc2f01fd60431366e997
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393432"
---
# <a name="export-security-baselines-assessment-per-device"></a>Eksportér vurdering af grundlæggende sikkerhedsdata pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender – Opdater](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender? [Tilmeld dig en gratis prøveversion.- Opdater](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.

- **JSON-svar**  API'en henter alle data i din organisation som JSON-svar. Denne metode er bedst til _små organisationer med mindre end 100.000 enheder_. Svaret er sideinddelt, så du kan bruge feltet \@odata.nextLink fra svaret til at hente de næste resultater.

- **via filer** Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Du kan downloade data fra Azure Storage på følgende måde:
  - Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.
  - Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.

Data, der indsamles ved hjælp af enten '_JSON-svar_ eller _via filer_', er det aktuelle snapshot af den aktuelle tilstand. Den indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagre.

> [!NOTE]
> Medmindre andet er angivet, er alle angivne metoder til vurdering af eksportsikkerhedsgrundlinje **_fuld eksport_** og **_efter enhed_** (også kaldet **_pr. enhed_**)

## <a name="1-export-security-baselines-assessment-json-response"></a>1. Eksportér vurdering af grundlinjer for sikkerhed (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af API-metoden 1.1

Returnerer alle vurderinger af grundlæggende sikkerhedsdata for alle enheder på enhedsbasis. Den returnerer en tabel med en separat post for hver entydige kombination af DeviceId, ProfileId og ConfigurationId.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Hvis du vil vide mere, herunder hvordan du vælger tilladelser, skal du se [Brug Microsoft Defender for Endpoint API'er](apis-intro.md) for at få flere oplysninger.

Tilladelsestype|Tilladelse|Vist navn for tilladelse
:---|:---|:---
Program|SecurityBaselinesAssessment.Read.All |"Læs alle oplysninger om vurderinger af grundlæggende sikkerhedsgrundlinjer"
Uddelegeret (arbejds- eller skolekonto)|SecurityBaselinesAssessment.Read|'Læs oplysninger om vurderinger af grundlæggende sikkerhedsgrundlinjer'

### <a name="13-limitations"></a>1.3 Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Hastighedsbegrænsninger for denne API er 30 kald pr. minut og 1.000 opkald pr. time.

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000): Antal resultater i svar.
- $top: Antallet af resultater, der skal returneres (returnerer ikke @odata.nextLink og trækker derfor ikke alle dataene).

### <a name="15-http-request"></a>1.5 HTTP-anmodning

```http
GET /api/machines/baselineComplianceAssessmentByMachine
```

### <a name="16-properties-json-response"></a>1.6 Egenskaber (JSON-svar)

> [!NOTE]
> Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter.
>
> Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.
>
> De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres det resulterende output ikke nødvendigvis i den samme rækkefølge, som er angivet i denne tabel.

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
|configurationId|String|Entydigt id for en bestemt konfiguration i den oprindelige benchmark.
|profileId|String|Entydigt id for den vurderede profil.
|Deviceid|String|Entydigt id for enheden i tjenesten.
|deviceName|String|Fuldt domænenavn (FQDN) for enheden.
|isApplicable|Boolesk |Angiver, om konfigurationen gælder for denne enhed.
|er i overensstemmelse|Boolesk |Angiver, om enheden er kompatibel med konfigurationen.
|Id|String|Entydigt id for posten, som er en kombination af DeviceId, ProfileId og ConfigurationId.
|osVersion|String|Specifik version af operativsystemet, der kører på enheden.
|osPlatform|String|Operativsystemplatform, der kører på enheden. Specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se [TVM-understøttede operativsystemer og platforme](tvm-supported-os.md) for at få flere oplysninger.
|rbacGroupId|Int|Det rollebaserede adgangskontrolgruppe-id (RBAC). Hvis enheden ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
|rbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis enheden ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
|DataCollectionTimeOffset|Datetime|Det tidspunkt, hvor dataene blev indsamlet fra enheden. Dette felt vises muligvis ikke, hvis der ikke er indsamlet nogen data.
|ComplianceCalculationTimeOffset|Datetime|Det tidspunkt, hvor beregningsberegningen blev foretaget.
|Anbefalet værdi|String|Sæt af forventede værdier for den aktuelle enhedsindstilling, der skal klages over.
|CurrentValue|String|Sæt af registrerede værdier, der blev fundet på enheden.
|Kilde|String|Stien til registreringsdatabasen eller en anden placering, der bruges til at bestemme den aktuelle enhedsindstilling.

## <a name="17-example"></a>1.7 Eksempel

### <a name="171-request-example"></a>1.7.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="172-response-example"></a>1.7.2 Svareksempel

```json
{ 
"@odata.context": " https://api.securitycenter.microsoft.com /api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetBaselineAssessment)", 
"value": [
{ 
    "id": "0000682575d5d473e82ed4d8680425d152411251_9e1b90be-e83e-485b-a5ec-4a429412e734_1.1.1", 
    "configurationId": "1.1.1", 
    "deviceId": "0000682575d5d473242222425d152411251", 
    "deviceName": " ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596 ", 
    "profileId": "9e1b90be-e83e-485b-a5ec-4a429412e734", 
    "osPlatform": "WindowsServer2019", 
    "osVersion": "10.0.17763.2330", 
    "rbacGroupId": 86, 
    "rbacGroupName": "UnassignedGroup", 
    "isApplicable": true, 
    "isCompliant": false, 
    "dataCollectionTimeOffset": "2021-12-22T00:08:02.478Z", 
    "recommendedValue": [ 
                    "Greater than or equal '24'" 
                ], 
                "currentValue": [ 
                    "24" 
                ], 
                "source": [ 
                    "password_hist_len"
                ], 
}
```

## <a name="2-export-security-baselines-assessment-via-files"></a>2. Eksportér vurdering af grundlinjer for sikkerhed (via filer)

### <a name="21-api-method-description"></a>2.1 Beskrivelse af API-metode

Returnerer alle vurderinger af grundlæggende sikkerhedsdata for alle enheder på enhedsbasis. Den returnerer en tabel med en separat post for hver entydige kombination af DeviceId, ProfileId og ConfigurationId.

### <a name="22-limitations"></a>2.2 Begrænsninger

- Hastighedsbegrænsninger for denne API er 5 kald pr. minut og 20 opkald pr. time.

### <a name="23-url"></a>2.3 URL-adresse

```http
GET /api/machines/BaselineComplianceAssessmentExport
```

### <a name="24-parameters"></a>2.4 Parametre

- sasValidHours: Det antal timer, som URL-adresserne til download er gyldige i (højst 24 timer). 

### <a name="25-properties-via-files"></a>2.5 Egenskaber (via filer)

> [!NOTE]
> Filerne er gzip-komprimerede & i Json-format med flere streger.
>
>URL-adresserne til download er kun gyldige i 3 timer. Ellers kan du bruge parameteren .
>
>Hvis du vil maksimere downloadhastighederne, skal du sørge for, at du downloader dataene fra det samme Azure-område, hvor dine data er placeret.
>
>Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den pageSize-parameter, der fungerer for dig.
>
>Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
|Eksportér filer|matrix[streng]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.
|GeneratedTime|String|Det tidspunkt, hvor eksporten blev genereret.

## <a name="26-example"></a>2.6 Eksempel

### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Svareksempel

```json
{ 
    "@odata.context": "https://api.securitycenter. contoso.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse", 
    "exportFiles": 
    [ 
    "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId= OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00000-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv=ABCD", 
   "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00001-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv= ABCD", 
    ], 
    "generatedTime": "2021-01-11T11:01:00Z" 
}
```

## <a name="see-also"></a>Se også

- [Hent vurderingsprofiler for sikkerhedsgrundlinjer](get-security-baselines-assessment-profiles.md)
- [Hent konfigurationer af vurdering af sikkerhedsgrundlinjer](get-security-baselines-assessment-configurations.md)
