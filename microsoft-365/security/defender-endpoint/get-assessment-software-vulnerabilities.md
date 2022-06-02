---
title: Eksportér vurdering af softwaresårbarheder pr. enhed
description: API-svaret er pr. enhed og indeholder sårbar software, der er installeret på dine eksponerede enheder og eventuelle kendte sikkerhedsrisici i disse softwareprodukter. Denne tabel indeholder også oplysninger om operativsystem, CVE-id'er og oplysninger om sårbarhedens alvorsgrad.
keywords: api, apis, eksportvurdering, vurdering pr. enhed, vurderingsrapport for sårbarheder, vurdering af enhedens sårbarhed, rapport over enhedssårbarhed, vurdering af sikker konfiguration, sikkerhedskonfigurationsrapport, vurdering af softwaresårbarheder, rapport over softwaresårbarheder, rapport over sårbarheder efter maskine,
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
ms.openlocfilehash: 86d2b0b09748a83c9b73430c4c6e371ca2e37f31
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838969"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Eksportér vurdering af softwaresårbarheder pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Returnerer alle kendte softwaresårbarheder og deres oplysninger for alle enheder på enhedsbasis.

Forskellige API-kald henter forskellige typer data. Da mængden af data kan være stor, er der to måder, den kan hentes på:

1. [**JSON-svar** til vurdering af softwaresårbarheder](#1-export-software-vulnerabilities-assessment-json-response)  API'en henter alle data i din organisation som Json-svar. Denne metode er bedst til _små organisationer med mindre end 100.000 enheder_. Svaret er sideinddelt, så du kan bruge feltet \@odata.nextLink fra svaret til at hente de næste resultater.

2. [Eksportér vurdering af softwaresårbarheder **via filer**](#2-export-software-vulnerabilities-assessment-via-files) Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Via-filer anbefales til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade alle dine data fra Azure Storage på følgende måde:
   - Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.
   - Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.

3. [**JSON-svar på JSON-vurdering** af sårbarheder i forbindelse med deltaeksportsoftware](#3-delta-export-software-vulnerabilities-assessment-json-response)  Returnerer en tabel med en post for hver entydige kombination af: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId og EventTimestamp.
API'en henter data i din organisation som Json-svar. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.

   Den fulde "vurdering af softwaresårbarheder (JSON-svar)" bruges til at få et helt snapshot af vurderingen af softwaresårbarheder for din organisation efter enhed. Api-kaldet til deltaeksport bruges dog kun til at hente de ændringer, der er foretaget mellem en valgt dato og dags dato (API-kaldet "delta"). I stedet for at få en fuld eksport med en stor mængde data hver gang får du kun specifikke oplysninger om nye, faste og opdaterede sikkerhedsrisici. Delta export JSON-svar-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sikkerhedsrisici blev løst?" eller "hvor mange nye sikkerhedsrisici blev føjet til min organisation?"

   Da deltaeksport-JSON-svar-API-kaldet for softwaresårbarheder kun returnerer data for et bestemt datointerval, anses det ikke for at være en _fuld eksport_.

Data, der indsamles (ved hjælp af enten _Json-svar_ eller _via filer_), er det aktuelle snapshot af den aktuelle tilstand. Den indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagre.

> [!NOTE]
> Medmindre andet er angivet, er alle angivne eksportvurderingsmetoder **_fuld eksport_** og **_efter enhed_** (også kaldet **_pr. enhed_**).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. Eksportér vurdering af softwaresårbarheder (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af API-metoden 1.1

Dette API-svar indeholder alle data fra installeret software pr. enhed. Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="111-limitations"></a>1.1.1 Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Hastighedsbegrænsninger for denne API er 30 kald pr. minut og 1.000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'
Uddelegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'

### <a name="13-url"></a>1.3 URL-adresse

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000): Antal resultater i svar.
- $top: Antallet af resultater, der skal returneres (returnerer ikke @odata.nextLink og trækker derfor ikke alle dataene).

### <a name="15-properties"></a>1.5 Egenskaber

> [!NOTE]
>
> - Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres det resulterende output ikke nødvendigvis i den samme rækkefølge, som er angivet i denne tabel.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
CveId|String|Entydigt id, der er tildelt sikkerhedssårbarheden under CVE-systemet (Common Vulnerabilities and Exposures).|CVE-2020-15992
CvssScore|String|CVSS-scoren for CVE.|6.2
Deviceid|String|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|String|Fuldt domænenavn (FQDN) for enheden.|johnlaptop.europe.contoso.com
DiskPaths|Matrixstreng\[\]|Disk, der beviser, at produktet er installeret på enheden.|[ "C:\Programmer (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
Udnyttelsesniveau|String|Udnyttelsesniveauet for denne sårbarhed (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit
FirstSeenTimestamp|String|Første gang CVE for dette produkt blev set på enheden.|2020-11-03 10:13:34.8476880
Id|String|Entydigt id for posten.|123ABG55_573AG&mnp!
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.|2020-11-03 10:13:34.8476880
OSPlatform|String|Platform for det operativsystem, der kører på enheden. Denne egenskab angiver specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere
Reference til anbefaling|String|En reference til det anbefalings-id, der er relateret til denne software.|va _--microsoft-_-silverlight
RecommendedSecurityUpdate (valgfrit)|String|Navn på eller beskrivelse af den sikkerhedsopdatering, der leveres af softwareleverandøren til at løse problemet med sårbarheden.|Sikkerhedsopdateringer fra april 2020
RecommendedSecurityUpdateId (valgfrit)|String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator for de tilsvarende artikler om vejledning eller videnbase (KB)|4550961
RegistryPaths|Matrixstreng\[\]|Registreringsdatabase beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName|String|Navnet på softwareproduktet.|Chrome
SoftwareVendor|String|Navnet på softwareleverandøren.|Google
SoftwareVersion|String|Softwareproduktets versionsnummer.|81.0.4044.138
VulnerabilitySeverityLevel|String|Alvorsgradsniveau, der er tildelt sikkerhedssårbarheden baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselslandskabet.|Medium
|

### <a name="16-examples"></a>1.6 Eksempler

#### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>1.6.2 Svareksempel

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

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. Eksportér vurdering af softwaresårbarheder (via filer)

### <a name="21-api-method-description"></a>2.1 Beskrivelse af API-metode

Dette API-svar indeholder alle data fra installeret software pr. enhed. Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="212-limitations"></a>2.1.2 Begrænsninger

Hastighedsbegrænsninger for denne API er 5 kald pr. minut og 20 opkald pr. time.

### <a name="22-permissions"></a>2.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er for at få flere oplysninger](apis-intro.md).

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Vulnerability.Read.All|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'
Uddelegeret (arbejds- eller skolekonto)|Vulnerability.Read|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'

### <a name="23-url"></a>2.3 URL-adresse

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametre

- sasValidHours: Det antal timer, som URL-adresserne til download er gyldige i (højst 24 timer).

### <a name="25-properties"></a>2.5 Egenskaber

> [!NOTE]
>
> - Filerne er gzip-komprimerede & i Json-format med flere streger.
> - URL-adresserne til download er kun gyldige i 3 timer. Ellers kan du bruge parameteren .
> - Hvis du vil have maksimal downloadhastighed for dine data, kan du sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i.
>
> - Hver post er ca. 1 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|String|Det tidspunkt, hvor eksporten blev genereret.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Eksempler

#### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>2.6.2 Svareksempel

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

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. Vurdering af sårbarheder i forbindelse med deltaeksport af software (JSON-svar)

### <a name="31-api-method-description"></a>Beskrivelse af API-metoden 3.1

Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. API'en henter data i din organisation som Json-svar. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. I modsætning til vurderingen af sikkerhedsrisici i hele softwaren (JSON-svar) (som bruges til at få et helt snapshot af vurderingen af softwaresårbarheder for din organisation efter enhed) bruges deltaeksport-JSON-svar-API-kaldet til kun at hente de ændringer, der er sket mellem en valgt dato og den aktuelle dato (API-kaldet "delta"). I stedet for at få en fuld eksport med en stor mængde data hver gang får du kun specifikke oplysninger om nye, faste og opdaterede sikkerhedsrisici. Delta export JSON-svar-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sikkerhedsrisici blev løst?" eller "hvor mange nye sikkerhedsrisici blev føjet til min organisation?"

> [!NOTE]
> Det anbefales på det kraftigste, at du bruger vurderingen af sårbarheder i forbindelse med eksport af software ved hjælp af enheds-API-kald mindst én gang om ugen, og denne ekstra eksportsoftwares sårbarheder ændres efter enhedens (delta)API-kald til alle de andre dage i ugen. I modsætning til de andre JSON-svar-API'er til vurderinger er "deltaeksport" ikke en fuld eksport. Delta-eksporten omfatter kun de ændringer, der er sket mellem en valgt dato og dags dato (API-kaldet "delta").

#### <a name="311-limitations"></a>3.1.1 Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Parameteren sinceTime har maksimalt 14 dage.
- Hastighedsbegrænsninger for denne API er 30 kald pr. minut og 1.000 opkald pr. time.

### <a name="32-permissions"></a>3.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Vulnerability.Read.All|'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring'
Uddelegeret (arbejds- eller skolekonto)|Vulnerability.Read|'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring'

### <a name="33-url"></a>3.3 URL-adresse

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 Parametre

- sinceTime (påkrævet): Dataene mellem et valgt tidspunkt og i dag.
- pageSize (standard = 50.000): antal resultater i svar.
- $top: Antallet af resultater, der skal returneres (returnerer ikke @odata.nextLink, og trækker derfor ikke alle dataene).

### <a name="35-properties"></a>3.5 Egenskaber

Hver returnerede post indeholder alle data fra vurderingen af sårbarheder i forbindelse med fuld eksport af software efter enheds-API samt yderligere to felter:  _**EventTimestamp**_ og _**Status**_.

> [!NOTE]
>
> - Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet, så brug kun de dokumenterede kolonner.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres det resulterende output ikke nødvendigvis i den samme rækkefølge, som er angivet i denne tabel.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på returneret værdi
:---|:---|:---|:---
CveId |String|Entydigt id, der er tildelt sikkerhedssårbarheden under CVE-systemet (Common Vulnerabilities and Exposures).|CVE-2020-15992  
CvssScore|String|CVSS-scoren for CVE.|6.2  
Deviceid|String|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
DeviceName|String|Fuldt domænenavn (FQDN) for enheden.|johnlaptop.europe.contoso.com  
DiskPaths|Matrix[streng]|Disk, der beviser, at produktet er installeret på enheden.|["C:\Programmer (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
EventTimestamp|String|Det tidspunkt, hvor denne delta-hændelse blev fundet.|2021-01-11T11:06:08.291Z
Udnyttelsesniveau|String|Udnyttelsesniveauet for denne sårbarhed (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)|ExploitIsInKit  
FirstSeenTimestamp|String|Første gang CVE for dette produkt blev set på enheden.|2020-11-03 10:13:34.8476880  
Id|String|Entydigt id for posten.|123ABG55_573AG&mnp!  
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.|2020-11-03 10:13:34.8476880  
OSPlatform|String|Platform for det operativsystem, der kører på enheden; specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11 
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere  
Reference til anbefaling|Streng|En reference til det anbefalings-id, der er relateret til denne software.|va--microsoft--silverlight  
RecommendedSecurityUpdate |String|Navn på eller beskrivelse af den sikkerhedsopdatering, der leveres af softwareleverandøren til at løse problemet med sårbarheden.|Sikkerhedsopdateringer fra april 2020  
RecommendedSecurityUpdateId |String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator for de tilsvarende artikler om vejledning eller videnbase (KB)|4550961  
RegistryPaths |Matrix[streng]|Registreringsdatabase beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
SoftwareName|String|Navnet på softwareproduktet.|Chrome  
SoftwareVendor|String|Navnet på softwareleverandøren.|Google  
SoftwareVersion|String|Softwareproduktets versionsnummer.|81.0.4044.138  
Status|String|**Ny** (for en ny sårbarhed, der introduceres på en enhed) (1) **Fast** (hvis denne sårbarhed ikke længere findes på enheden, hvilket betyder, at den blev afhjælpet). (2) **Opdateret** (hvis en sikkerhedsrisiko på en enhed er blevet ændret. De mulige ændringer er: CVSS-score, udnyttelsesniveau, alvorsgradsniveau, DiskPaths, RegistryPaths, RecommendedSecurityUpdate). |Fast
VulnerabilitySeverityLevel|String|Alvorsgradsniveau, der er tildelt til sikkerhedsrisikoen. Den er baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselslandskabet.|Medium
|

#### <a name="clarifications"></a>Præciseringer

- Hvis softwaren blev opdateret fra version 1.0 til version 2.0, og begge versioner er eksponeret for CVE-A, modtager du to separate hændelser:
   1. Løst: CVE-A på version 1.0 blev rettet.
   1. Ny: CVE-A på version 2.0 blev tilføjet.

- Hvis en bestemt sårbarhed (f.eks. CVE-A) først blev set på et bestemt tidspunkt (f.eks. 10. januar) på software med version 1.0, og et par dage senere blev softwaren opdateret til version 2.0, som også blev eksponeret for samme CVE-A, modtager du disse to adskilte hændelser:
   1. Løst: CVE-X, FirstSeenTimestamp 10. januar, version 1,0.
   1. Ny: CVE-X, FirstSeenTimestamp 10. januar, version 2.0.

### <a name="36-examples"></a>3.6 Eksempler

#### <a name="361-request-example"></a>3.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>3.6.2 Svareksempel

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

- [Eksportér vurderingsmetoder og -egenskaber pr. enhed](get-assessment-methods-properties.md)
- [Eksportér vurdering af sikker konfiguration pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwarelager pr. enhed](get-assessment-software-inventory.md)

Andre relaterede

- [Risikobaseret trussel & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsrisici i din organisation](tvm-weaknesses.md)
