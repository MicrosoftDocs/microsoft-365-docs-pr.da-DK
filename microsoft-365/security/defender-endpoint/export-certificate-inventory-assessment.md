---
title: Metoder og egenskaber for certifikatvurdering pr. enhed
description: Indeholder oplysninger om de certifikat-API'er, der henter "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.
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
ms.openlocfilehash: c7718175789755a711a0dd43dce041f125d18972
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368826"
---
# <a name="export-certificate-inventory-per-device"></a>Eksportér certifikatlager pr. enhed

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

## <a name="1-export-certificate-assessment-json-response"></a>1. Eksportér certifikatvurdering (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af API-metoden 1.1

Returnerer alle certifikatvurderinger for alle enheder pr. enhed. Den returnerer en tabel med en separat post for hver entydige kombination af DeviceId, Aftryk og Sti.

#### <a name="12-limitations"></a>1.2 Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Hastighedsbegrænsninger for denne API er 30 kald pr. minut og 1.000 opkald pr. time.

### <a name="13-parameters"></a>1.3 Parametre

- pageSize (standard = 50.000): Antal resultater i svar.
- $top: Antallet af resultater, der skal returneres (returnerer ikke @odata.nextLink og trækker derfor ikke alle dataene).

### <a name="14-http-request"></a>1.4 HTTP-anmodning

```http
GET /api/machines/certificateAssessmentByMachine
```

### <a name="15-properties-json-response"></a>1.5 Egenskaber (JSON-svar)

> [!NOTE]
> Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter.
>
> Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.
>
> De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres det resulterende output ikke nødvendigvis i den samme rækkefølge, som er angivet i denne tabel.

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
|Deviceid|String|Entydigt id for enheden i tjenesten.
|DeviceName|String|Fuldt domænenavn (FQDN) for enheden.
|Aftryk|Boolesk |Entydigt id for certifikatet.
|Sti|String|Certifikatets placering.
|SignatureAlgorithm|String|Hashalgoritmen og krypteringsalgoritmen bruges.
|KeySize|String|Størrelsen på den nøgle, der bruges i signaturalgoritmen.
|Udløbsdato|String|Den dato og det klokkeslæt, hvor certifikatet ikke længere er gyldigt.
|IssueDate|String|Den tidligste dato og det tidligste klokkeslæt, hvor certifikatet blev gyldigt.
|Emnetype|String|Angiver, om certifikatindehaveren er et nøglecenter eller en slutenhed.
|SerialNumber|String|Entydigt id for certifikatet i et nøglecenters systemer.
|Udstedt til|Objekt|Enhed, som et certifikat tilhører. kan være en enhed, en person eller en organisation.
|Udstedt af|Objekt|Enhed, der bekræftede oplysningerne og signerede certifikatet.
|Nøgleusage|String|Den gyldige kryptografiske brug af certifikatets offentlige nøgle.
|ExtendedKeyUsage|String|Andre gyldige anvendelser af certifikatet.
|RbacGroupId|String|Det rollebaserede RBAC-gruppe-id (Access Control).
|RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-grupper, er værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".

## <a name="16-example"></a>1.6 Eksempel

### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>1.6.2 Svareksempel

```json

  {
     "@odata.context":"https://127.0.0.1/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetCertificateAssessment)",
      "value":[
        {
        "deviceId":"49126b9e4a5473b5229c73799e9e55c48668101b",
        "deviceName":"testmachine5",
        "thumbprint":"A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "path":"LocalMachine\\TestSignRoot\\A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "signatureAlgorithm":"sha384ECDSA",
        "keyLength":0,"notAfter":"0001-01-01T00:00:00Z",
        "notBefore":"0001-01-01T00:00:00Z",
        "subjectType":"CA",
        "serialNumber":"6086A185EAFA2B9943B4671603F40323",
        "subjectObject":null,
        "issuerObject":null,
        "keyUsageArray":null,
        "extendedKeyUsageArray":null,
        "isSelfSigned":false,
        "rbacGroupId":4226,
        "rbacGroupName":"testO6343398Gq31"}],
        "@odata.nextLink":"https://127.0.0.1/api/machines/CertificateAssessmentByMachine?pagesize=1&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wMy0yMS8wNTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjF9"
  }
```

## <a name="2-export-certificate-assessment-via-files"></a>2. Eksportér certifikatvurdering (via filer)

### <a name="21-api-method-description"></a>2.1 Beskrivelse af API-metode

Returnerer alle certifikatvurderinger for alle enheder pr. enhed. Den returnerer en tabel med en separat post for hver entydige kombination af DeviceId, Aftryk og Sti.

#### <a name="22-limitations"></a>2.2 Begrænsninger

- Hastighedsbegrænsninger for denne API er 5 kald pr. minut og 20 opkald pr. time. 

### <a name="23-parameters"></a>2.3 Parametre

- sasValidHours: Det antal timer, som URL-adresserne til download er gyldige i (højst 24 timer).

### <a name="24-http-request"></a>2.4 HTTP-anmodning

```http
GET /api/machines/certificateAssessmentExport
```

### <a name="25-properties-json-response"></a>2.5 Egenskaber (JSON-svar)

> [!NOTE]
> Filerne er gzip-komprimerede & i Json-format med flere streger.
>
> URL-adresserne til download er kun gyldige i 3 timer. Ellers kan du bruge parameteren .
>
> Hvis du vil maksimere downloadhastighederne, skal du sørge for, at du downloader dataene fra det samme Azure-område, hvor dine data er placeret.
>
> Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den pageSize-parameter, der fungerer for dig.
>
> Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
|Eksportér filer|Streng[matrix]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.
|GeneratedTime|Datetime|Det tidspunkt, hvor eksporten blev genereret.


## <a name="26-example"></a>2.6 Eksempel

### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.contoso.com/api/machines/certificateAssessmentExport
```

### <a name="262-response-example"></a>2.6.2 Svareksempel

```json
    {
        "@odata.context":"https://127.0.0.1/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
        "exportFiles":["https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4226/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=IMmwTOYmGvU0ei5AHLNAxnFCmZkE2jvBHzRmuAu9xaA%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4414/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=2r0y74WZsATa0DjQTwfBxNqL5vN2Wl0AZKHMNrxuJ30%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=75/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=uVdY4%2BBpMdPMwaD3G0RJTZkS4R9J8oN8I3tu%2FOcG35c%3D"],
        "generatedTime":"2022-03-20T13:18:00Z"
   }
```
