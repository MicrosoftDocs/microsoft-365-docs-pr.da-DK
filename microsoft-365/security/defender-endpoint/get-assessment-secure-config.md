---
title: Eksportér sikker konfigurationsvurdering pr. enhed
description: Returnerer en post for hver entydige kombination af DeviceId, ConfigurationId.
keywords: api, apis, eksportvurdering, pr. enhedsvurdering, rapport over sikkerhedsrisiko, vurdering af sikkerhedsrisiko, rapport over sikkerhedsrisiko på enheder, sikker konfigurationsvurdering, sikker konfigurationsrapport, vurdering af softwarerisici, rapport over sikkerhedsrisiko, rapport over sikkerhedsrisiko på computer,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 2fc9870871641bb7239a6dcdcdf9f54334726384
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63599428"
---
# <a name="export-secure-configuration-assessment-per-device"></a>Eksportér sikker konfigurationsvurdering pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Returnerer alle konfigurationer og deres status pr. enhed.

Der er forskellige API-opkald for at få forskellige typer data. Da mængden af data kan være stor, er der to måder, det kan hentes på:

- [Eksportér **JSON-svar til sikker konfigurationsvurdering**](#1-export-secure-configuration-assessment-json-response): API'en trækker alle data i organisationen som Json-svar. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

- [Eksportér sikker **konfigurationsvurdering via filer**](#2-export-secure-configuration-assessment-via-files): Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:

  - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.

  - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

Data, der indsamles (ved hjælp af _enten JSON-svar_ eller _via_ filer), er det aktuelle øjebliksbillede af den aktuelle tilstand og indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

> [!NOTE]
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. Eksportér vurdering af sikker konfiguration (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af 1.1 API-metode

Dette API-svar indeholder Secure Configuration Assessment på dine eksponerede enheder og returnerer en post for hver unik kombination af DeviceId, ConfigurationId.

#### <a name="111-limitations"></a>Begrænsninger 1.1.1

- Den maksimale sidestørrelse er 200.000.

- Satsbegrænsninger for denne API er 30 opkald i minuttet og 1000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere](apis-intro.md) oplysninger.

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize \(default = 50.000\): Antal resultater i svar.
- \$top: Det antal resultater, der returneres \(, returnerer ikke \@odata.nextLink og trækker derfor ikke alle dataene\).

### <a name="15-properties"></a>1.5 Egenskaber

> [!NOTE]
>
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres outputtet ikke nødvendigvis i samme rækkefølge, som er angivet i denne tabel.
> - Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
---|---|---|---
ConfigurationCategory|streng|Kategori eller gruppering, som konfigurationen tilhører: Program, OPERATIVSYSTEM, Netværk, Konti, Sikkerhedskontrolelementer|Sikkerhedskontrolelementer
ConfigurationId|streng|Entydigt id for en bestemt konfiguration|scid-10000
ConfigurationImpact|streng|Klassificeret effekt af konfigurationen på det overordnede konfigurationsresultat (1-10)|9
ConfigurationName|streng|Visningsnavn for konfigurationen|Onboard-enheder til Microsoft Defender til Slutpunkt
ConfigurationSubcategory|streng|Underkategori eller undergruppering, som konfigurationen tilhører. I mange tilfælde beskrives specifikke funktioner.|Onboard-enheder
DeviceId|streng|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|streng|Enhedens fulde domænenavn.|johnlaptop.europe.contoso.com
IsApplicable|bool|Angiver, om konfigurationen eller politikken er gældende|sand
IsCompliant|bool|Angiver, om konfigurationen eller politikken er konfigureret korrekt|falsk
IsExpectedUserImpact|bool|Angiver, om der vil være brugerpåvirkning, hvis konfigurationen anvendes|sand
OSPlatform|streng|Platform for operativsystemet, der kører på enheden. Dette angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11
RbacGroupName|streng|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere
AnbefalingReference|streng|En reference til det anbefalings-id, der er relateret til denne software.|sca-_-scid-20000
Tidsstempel|streng|Sidste gang konfigurationen blev set på enheden|2020-11-03 10:13:34.8476880
|

### <a name="16-examples"></a>1.6 Eksempler

#### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Eksempel på svar

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-20000",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Onboard Devices",
            "configurationImpact": 9,
            "isCompliant": false,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Onboard devices to Microsoft Defender for Endpoint",
            "recommendationReference": "sca-_-scid-20000"
        },
        {
            "deviceId": "0002a1de123456a8c06de736785395d4ce7610",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-39",
            "configurationCategory": "OS",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Enable 'Domain member: Digitally sign secure channel data (when possible)'",
            "recommendationReference": "sca-_-scid-39"
        },
        {
            "deviceId": "00044f912345daf759462bde6bd733d6a9c56ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45612eeb224d2de2f5ea3142726e63f16a.DomainPII_21eed80d086e76dbfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-6093",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Antivirus",
            "configurationImpact": 5,
            "isCompliant": false,
            "isApplicable": false,
            "isExpectedUserImpact": false,
            "configurationName": "Enable Microsoft Defender Antivirus real-time behavior monitoring for Linux",
            "recommendationReference": "sca-_-scid-6093"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. Eksportér vurdering af sikker konfiguration (via filer)

### <a name="21-api-method-description"></a>Beskrivelse af 2.1 API-metoden

Dette API-svar indeholder Secure Configuration Assessment på dine eksponerede enheder og returnerer en post for hver unik kombination af DeviceId, ConfigurationId.

#### <a name="212-limitations"></a>Begrænsninger 2.1.2

Begrænsningerne for denne API er 5 opkald i minuttet og 20 opkald pr. time.

### <a name="22-permissions"></a>2.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs "Håndtering af trusler og sikkerhedsrisici" oplysninger om sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs "Håndtering af trusler og sikkerhedsrisici" oplysninger om sikkerhedsrisiko\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>Parametre

- sasValidHours: Det antal timer, de hentede URL-adresser er gyldige i (maksimalt 24 timer).

### <a name="25-properties"></a>2.5 Egenskaber

> [!NOTE]
>
> - Filerne er gzip komprimerede filer & multiline Json-format.
> - URL-adresserne til download er kun gyldige i tre timer. Ellers kan du bruge parameteren.
> - Du kan sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i, for at få den maksimale downloadhastighed.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
---|---|---|---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til download af filer, der indeholder det aktuelle øjebliksbillede af organisationen|["Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|streng|Det tidspunkt, hvor eksporten blev oprettet.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Eksempler

#### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>2.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#contoso.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Se også

- [Eksportere vurderingsmetoder og egenskaber pr. enhed](get-assessment-methods-properties.md)
- [Eksportér vurdering af softwarelager pr. enhed](get-assessment-software-inventory.md)
- [Eksportér vurdering af softwarerisici pr. enhed](get-assessment-software-vulnerabilities.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
