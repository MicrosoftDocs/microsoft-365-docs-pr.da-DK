---
title: Eksportér vurdering af softwarerisici pr. enhed
description: API-svaret er pr. enhed og indeholder sårbar software, der er installeret på dine eksponerede enheder og kendte sårbarheder i disse softwareprodukter. Denne tabel indeholder også oplysninger om operativsystem, CVE-id'er og alvorlighedsoplysninger om sikkerhedsrisikoen.
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
ms.openlocfilehash: 5d10b96e1d5abfe1c9e9a87b9800dafba081c961
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63599426"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Eksportér vurdering af softwarerisici pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Returnerer alle kendte softwarerisici og deres oplysninger for alle enheder på én gang.

Forskellige API-opkald får forskellige typer data. Da mængden af data kan være stor, er der to måder, det kan hentes på:

1. [JSON-svar til vurdering af **eksport af softwarerisici**](#1-export-software-vulnerabilities-assessment-json-response)  API'en trækker alle data i organisationen som Json-svar. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

2. [Eksportér vurdering af softwarerisici **via filer**](#2-export-software-vulnerabilities-assessment-via-files) Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Via-filer anbefales til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:
   - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.
   - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

3. [JSON-svar til vurdering af sårbarheder **ved eksport af deltasoftware**](#3-delta-export-software-vulnerabilities-assessment-json-response)  Returnerer en tabel med et element for hver entydige kombination af: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId og EventTimestamp.
API'en trækker data i organisationen som Json-svar. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.

   Den fulde "vurdering af softwarerisici (JSON-svar)" bruges til at få et helt øjebliksbillede af din organisations softwarerisici efter enhed. Men deltaeksport-API-opkaldet bruges til kun at hente de ændringer, der er sket mellem en valgt dato og den aktuelle dato ("delta"-API-opkaldet). I stedet for at eksportere en stor mængde data hver gang, får du kun specifikke oplysninger om nye, rettede og opdaterede sårbarheder. DELTA-eksport-JSON-svar-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sårbarheder blev rettet?" eller "hvor mange nye sårbarheder blev føjet til min organisation?"

   Da DELTA-eksport-JSON-svar-API-opkald til softwarerisici kun returnerer data for et målrettet datointerval, betragtes det ikke som _en fuld eksport_.

Data, der indsamles (ved hjælp _af enten Json-svar_ _eller via filer_), er det aktuelle øjebliksbillede af den aktuelle tilstand. Det indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

> [!NOTE]
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Eksportér vurdering af softwarerisici (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af 1.1 API-metode

Dette API-svar indeholder alle data for installeret software pr. enhed. Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="111-limitations"></a>Begrænsninger 1.1.1

- Den maksimale sidestørrelse er 200.000.
- Satsbegrænsninger for denne API er 30 opkald i minuttet og 1000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000): Antal resultater som svar.
- $top: Det antal resultater, der skal returneres (returnerer ikke @odata.nextLink, og træk derfor ikke alle dataene).

### <a name="15-properties"></a>1.5 Egenskaber

> [!NOTE]
>
> - Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres outputtet ikke nødvendigvis i samme rækkefølge, som er angivet i denne tabel.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
CveId|String|Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures).|CVE-2020-15992
CvssScore|String|CVSS-scoren for CVE'en.|6.2
DeviceId|String|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|String|Enhedens fulde domænenavn.|johnlaptop.europe.contoso.com
DiskPaths|Matrixstreng\[\]|Disk bevis for, at produktet er installeret på enheden.|[ "C:\Programmer (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel|String|Udnyttelsesniveauet for denne risiko (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|String|Første gang CVE'en for dette produkt blev set på enheden.|2020-11-03 10:13:34.8476880
Id|String|Entydigt id for posten.|123ABG55_573AG&mnp!
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.|2020-11-03 10:13:34.8476880
OSPlatform|String|Platform for operativsystemet, der kører på enheden. Denne egenskab angiver bestemte operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere
AnbefalingReference|String|En reference til det anbefalings-id, der er relateret til denne software.|va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (valgfrit)|String|Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen.|Sikkerhedsopdateringer for april 2020
RecommendedSecurityUpdateId (valgfrit)|String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB)|4550961
Registreringsdatabasestier|Matrixstreng\[\]|Registreringsdatabasen beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName|String|Navnet på softwareproduktet.|Chrome
SoftwareVendor|String|Navnet på softwareleverandøren.|Google
SoftwareVersion|String|Softwareproduktets versionsnummer.|81.0.4044.138
VulnerabilitySeverityLevel|String|Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet.|Mellem
|

### <a name="16-examples"></a>1.6 Eksempler

#### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Eksportér vurdering af softwarerisici (via filer)

### <a name="21-api-method-description"></a>Beskrivelse af 2.1 API-metoden

Dette API-svar indeholder alle data for installeret software pr. enhed. Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>Begrænsninger 2.1.2

Begrænsningerne for denne API er 5 opkald i minuttet og 20 opkald pr. time.

### <a name="22-permissions"></a>2.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger](apis-intro.md).

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametre

- sasValidHours: Det antal timer, de hentede URL-adresser er gyldige i (maksimalt 24 timer).

### <a name="25-properties"></a>2.5 Egenskaber

> [!NOTE]
>
> - Filerne er gzip komprimerede filer & multiline Json-format.
> - URL-adresserne til download er kun gyldige i tre timer. Ellers kan du bruge parameteren.
> - Du kan sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i, for at få den maksimale downloadhastighed.
>
> - Hver post er ca. 1KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|String|Det tidspunkt, hvor eksporten blev oprettet.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Eksempler

#### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>2.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Vurdering af sårbarheder ved eksport af deltasoftware (JSON-svar)

### <a name="31-api-method-description"></a>Beskrivelse af 3.1 API-metoden

Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. API'en trækker data i organisationen som Json-svar. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. I modsætning til den fulde vurdering af softwarerisici (JSON-svar) (der bruges til at få et helt øjebliksbillede af din organisations vurdering af softwarerisici efter enhed), bruges DELTA-svar-API-opkaldet fra deltaeksporten til kun at hente de ændringer, der er sket mellem en valgt dato og den aktuelle dato ("delta"API-opkaldet). I stedet for at eksportere en stor mængde data hver gang, får du kun specifikke oplysninger om nye, rettede og opdaterede sårbarheder. DELTA-eksport-JSON-svar-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sårbarheder blev rettet?" eller "hvor mange nye sårbarheder blev føjet til min organisation?"

> [!NOTE]
> Det anbefales kraftigt, at du bruger enheds-API-opkaldsvurderingen for fulde vurdering af softwarerisici i forbindelse med eksport af software mindst én gang om ugen, og disse ekstra sårbarheder i forbindelse med eksportsoftware ændres efter enhed (delta) API-opkald alle de andre ugedage. Til forskel fra de andre JSON-svar-API'er til Bedømmelser er "deltaeksporten" ikke en fuld eksport. Deltaeksporten indeholder kun de ændringer, der er sket mellem en valgt dato og dags dato ("delta"-API-opkaldet).

#### <a name="311-limitations"></a>Begrænsninger 3.1.1

- Den maksimale sidestørrelse er 200.000.
- Parameteren sinceTime har maksimalt 14 dage.
- Satsbegrænsninger for denne API er 30 opkald i minuttet og 1000 opkald pr. time.

### <a name="32-permissions"></a>3.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Vulnerability.Read.All|"Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko"
Delegeret (arbejds- eller skolekonto)|Vulnerability.Read|"Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko"

### <a name="33-url"></a>3.3 URL

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametre

- sinceTime (påkrævet): Dataene mellem et valgt tidspunkt og i dag.
- pageSize (standard = 50.000): antal resultater som svar.
- $top: antal resultater, der skal returneres (returnerer ikke @odata.nextLink, og træk derfor ikke alle dataene).

### <a name="35-properties"></a>3.5 Egenskaber

Hver returnerede post indeholder alle data fra enheds-API'ens fulde vurdering af softwarerisici samt yderligere to felter:  _**EventTimestamp**_ og _**Status**_.

> [!NOTE]
>
> - Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes, så du skal kun bruge de dokumenterede kolonner.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres outputtet ikke nødvendigvis i samme rækkefølge, som er angivet i denne tabel.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på returneret værdi
:---|:---|:---|:---
CveId |String|Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures).|CVE-2020-15992  
CvssScore|String|CVSS-scoren for CVE'en.|6.2  
DeviceId|String|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|String|Enhedens fulde domænenavn.|johnlaptop.europe.contoso.com  
DiskPaths|Matrix[streng]|Disk bevis for, at produktet er installeret på enheden.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|String|Det tidspunkt, hvor denne deltabegivenhed blev fundet.|2021-01-11T11:06:08.291Z
ExploitabilityLevel|String|Udnyttelsesniveauet for denne risiko (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|String|Første gang CVE'en for dette produkt blev set på enheden.|2020-11-03 10:13:34.8476880  
Id|String|Entydigt id for posten.|123ABG55_573AG&mnp!  
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.|2020-11-03 10:13:34.8476880  
OSPlatform|String|Platform for det operativsystem, der kører på enheden. specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11 
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere  
AnbefalingReference|streng|En reference til det anbefalings-id, der er relateret til denne software.|va--microsoft--silverlight  
RecommendedSecurityUpdate |String|Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen.|Sikkerhedsopdateringer for april 2020  
RecommendedSecurityUpdateId |String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB)|4550961  
Registreringsdatabasestier |Matrix[streng]|Registreringsdatabasen beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
SoftwareName|String|Navnet på softwareproduktet.|Chrome  
SoftwareVendor|String|Navnet på softwareleverandøren.|Google  
SoftwareVersion|String|Softwareproduktets versionsnummer.|81.0.4044.138  
Status|String|**Ny** (for en ny sikkerhedsrisiko, der introduceres på en **enhed) (** 1) Rettet (hvis denne sikkerhedsrisiko ikke findes længere på enheden, hvilket betyder, at den er løst). (2) **Opdateret** (hvis en sikkerhedsrisiko på en enhed er ændret. De mulige ændringer er: CVSS-score, udnyttelsesniveau, alvorsniveau, DiskPaths, Registreringsdatabasestier, RecommendedSecurityUpdate). |Rettet
VulnerabilitySeverityLevel|String|Alvorsniveau, der er tildelt sikkerhedsrisikoen. Det er baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet.|Mellem
|

#### <a name="clarifications"></a>Afklaring

- Hvis softwaren blev opdateret fra version 1.0 til version 2.0, og begge versioner er tilgængelige for CVE-A, modtager du to separate begivenheder:
   1. Rettet: CVE-A på version 1.0 blev rettet.
   1. Ny: CVE-A på version 2.0 blev tilføjet.

- Hvis en bestemt sikkerhedsrisiko (f.eks. CVE-A) først blev set på et bestemt tidspunkt (f.eks. 10. januar) på software med version 1.0, og et par dage senere denne software blev opdateret til version 2.0, som også eksponeres for den samme CVE-A, modtager du disse to adskilte begivenheder:
   1. Rettet: CVE-X, FirstSeenTimestamp 10. januar, version 1,0.
   1. Nyt: CVE-X, FirstSeenTimestamp 10. januar, version 2.0.

### <a name="36-examples"></a>3.6 Eksempler

#### <a name="361-request-example"></a>3.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>3.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.DeltaAssetVulnerability)",
    "value": [
        {
            "id": "008198251234544f7dfa715e278d4cec0c16c171_chrome_87.0.4280.88__",
            "deviceId": "008198251234544f7dfa715e278b4cec0c19c171",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_1c8fee370690ca24b6a0d3f34d193b0424943a8b8.DomainPII_0dc1aee0fa366d175e514bd91a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "87.0.4280.88",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Google Chrome"
            ],
            "lastSeenTimestamp": "2021-01-04 00:29:42",
            "firstSeenTimestamp": "2020-11-06 03:12:44",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "00e59c61234533860738ecf488eec8abf296e41e_onedrive_20.64.329.3__",
            "deviceId": "00e56c91234533860738ecf488eec8abf296e41e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_82c13a8ad8cf3dbaf7bf34fada9fa3aebc124116.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.64.329.3",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2127521184-1604012920-1887927527-24918864\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-11 19:49:48",
            "firstSeenTimestamp": "2020-12-07 18:25:47",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "01aa8c73095bb12345918663f3f94ce322107d24_firefox_83.0.0.0_CVE-2020-26971_",
            "deviceId": "01aa8c73065bb12345918693f3f94ce322107d24",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_42684eb981bea2d670027e7ad2caafd3f2b381a3.DomainPII_21eed80b086e76dbfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "mozilla",
            "softwareName": "firefox",
            "softwareVersion": "83.0.0.0",
            "cveId": "CVE-2020-26971",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "193220",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Mozilla Firefox 83.0 (x86 en-US)"
            ],
            "lastSeenTimestamp": "2021-01-05 17:04:30",
            "firstSeenTimestamp": "2020-05-06 12:42:19",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-mozilla-_-firefox",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "026f0fcb12345fbd2decd1a339702131422d362e_project_16.0.13701.20000__",
            "deviceId": "029f0fcb13245fbd2decd1a336702131422d392e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_a5706750acba75f15d69cd17f4a7fcd268d6422c.DomainPII_f290e982685f7e8eee168b4332e0ae5d2a069cd6.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "project",
            "softwareVersion": "16.0.13701.20000",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\ProjectProRetail - en-us"
            ],
            "lastSeenTimestamp": "2021-01-03 23:38:03",
            "firstSeenTimestamp": "2019-08-01 22:56:12",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-project",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "038df381234510b357ac19d0113ef622e4e212b3_chrome_81.0.4044.138_CVE-2020-16011_",
            "deviceId": "038df381234510d357ac19b0113ef922e4e212b3",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596a43a2ef2bbfa00f6a16c0cb1d108bc63e32.DomainPII_3c5fefd2e6fda2f36257359404f6c1092aa6d4b8.net",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "81.0.4044.138",
            "cveId": "CVE-2020-16011",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "ADV 200002",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{C4EBFDFD-0C55-3E5F-A919-E3C54949024A}"
            ],
            "lastSeenTimestamp": "2020-12-10 22:45:41",
            "firstSeenTimestamp": "2020-07-26 02:13:43",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        }
    ],
    "@odata.nextLink": "https://wpatdadi-eus-stg.cloudapp.net/api/machines/SoftwareVulnerabilitiesTimeline?sincetime=2021-01-11&pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="see-also"></a>Se også

- [Eksportere vurderingsmetoder og egenskaber pr. enhed](get-assessment-methods-properties.md)
- [Eksportér sikker konfigurationsvurdering pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwarelager pr. enhed](get-assessment-software-inventory.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
