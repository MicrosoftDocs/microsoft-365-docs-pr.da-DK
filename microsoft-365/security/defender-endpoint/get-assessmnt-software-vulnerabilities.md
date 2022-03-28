---
title: Eksportér vurdering af softwarerisici pr. enhed
description: API-svaret er pr. enhed og indeholder sårbar software, der er installeret på dine blotlagte enheder, samt kendte sårbarheder i disse softwareprodukter. Denne tabel indeholder også oplysninger om operativsystem, CVE-id'er og alvorlighedsoplysninger om sikkerhedsrisikoen.
keywords: api, apis, eksportvurdering, pr. enhedsvurdering, rapport over sikkerhedsrisiko, vurdering af sikkerhedsrisiko, rapport over sikkerhedsrisiko på enheder, sikker konfigurationsvurdering, sikker konfigurationsrapport, vurdering af softwarerisici, rapport over sikkerhedsrisiko, rapport over sikkerhedsrisiko på computer,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 951f78ba361a12e404a5cce2071f931eab30c43f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/05/2021
ms.locfileid: "63597950"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>Eksportér vurdering af softwarerisici pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
Returnerer alle kendte softwarerisici og deres oplysninger for alle enheder på én gang.

Der er forskellige API-opkald for at få forskellige typer data. Da mængden af data kan være meget stor, er der to måder, de kan hentes på:

- [Vurdering af softwarerisici i forbindelse med eksport af software](#1-export-software-vulnerabilities-assessment-odata)  API'en trækker alle data i organisationen som Json-svar efter OData-protokollen. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

- [Eksportér vurdering af softwarerisici via filer](#2-export-software-vulnerabilities-assessment-via-files) Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:

  - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.

  - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

Data, der indsamles (ved hjælp af _enten OData_ _eller via_ filer), er det aktuelle øjebliksbillede af den aktuelle tilstand og indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

> [!Note]
>
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

## <a name="1-export-software-vulnerabilities-assessment-odata"></a>1. Eksportér vurdering af softwarerisici (OData)

### <a name="11-api-method-description"></a>Beskrivelse af 1.1 API-metode

Dette API-svar indeholder alle data for installeret software pr. enhed. Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CVEID.

#### <a name="limitations"></a>Begrænsninger

>- Den maksimale sidestørrelse er 200.000.
>
>- Satsbegrænsninger for denne API er 30 opkald i minuttet og 1000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype | Tilladelse | Visningsnavn for tilladelse
---|---|---
Program | Vulnerability.Read.All | \'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto) | Vulnerability.Read | \'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000) – antal resultater i svar
- $top – antal resultater, der skal returneres (returnerer ikke @odata.nextLink og trækker derfor ikke alle data)

### <a name="15-properties"></a>1.5 Egenskaber
>
>[!Note]
>
>- Hver post er ca. 1KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
>
>- Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.
>
>- De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id.  Når du kører denne API, returneres outputtet ikke nødvendigvis i samme rækkefølge, som er angivet i denne tabel.
>

Egenskab (id) | Datatype | Beskrivelse | Eksempel på en returneret værdi
:---|:---|:---|:---
CveId | streng | Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures). | CVE-2020-15992
CvssScore | streng | CVSS-scoren for CVE'en. | 6.2
DeviceId | streng | Entydigt id for enheden i tjenesten. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | streng | Enhedens fulde domænenavn. | johnlaptop.europe.contoso.com
DiskPaths  | Matrixstreng\[\] | Disk bevis for, at produktet er installeret på enheden. | [ "C:\Programmer (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
ExploitabilityLevel | streng | Udnyttelsesniveauet for denne risiko (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit) | ExploitIsInKit
FirstSeenTimestamp | streng | Første gang CVE'en for dette produkt blev set på enheden. | 2020-11-03 10:13:34.8476880
Id | streng | Entydigt id for posten. | 123ABG55_573AG&mnp!
LastSeenTimestamp | streng | Sidste gang CVE blev set på enheden. | 2020-11-03 10:13:34.8476880
OSPlatform | streng | Platform for operativsystemet, der kører på enheden. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 7. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger. | Windows10
RbacGroupName  | streng | Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen". | Servere
AnbefalingReference | streng | En reference til det anbefalings-id, der er relateret til denne software. | va-_-microsoft-_-silverlight
RecommendedSecurityUpdate (valgfrit) | streng | Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen. | Sikkerhedsopdateringer for april 2020
RecommendedSecurityUpdateId (valgfrit) | streng | Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB) | 4550961
Registreringsdatabasestier  | Matrixstreng\[\] | Registreringsdatabasen beviser, at produktet er installeret på enheden. | [ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName | streng | Navnet på softwareproduktet. | chrome
SoftwareVendor | streng | Navnet på softwareleverandøren. | google
SoftwareVersion | streng | Softwareproduktets versionsnummer. | 81.0.4044.138
VulnerabilitySeverityLevel  | streng | Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet. | Mellem

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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
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
            "recommendationReference": "va-_-microsoft-_-windows_10"
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

Tilladelsestype | Tilladelse | Visningsnavn for tilladelse
---|---|---
Program | Vulnerability.Read.All | \'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto) | Vulnerability.Read | \'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 Parametre

- sasValidHours – Det antal timer, de hentede URL-adresser er gyldige i (maksimalt 24 timer)

### <a name="25-properties"></a>2.5 Egenskaber

>[!Note]
>
>- Filerne er gzip komprimerede filer & multiline Json-format.
>
>- URL-adresserne til download er kun gyldige i tre timer. Ellers kan du bruge parameteren.
>
>- Du kan sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i, for at få den maksimale downloadhastighed.
>

>[!Note]
>
>- Hver post er ca. 1KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
>
>- Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.
>

Egenskab (id) | Datatype | Beskrivelse | Eksempel på en returneret værdi
:---|:---|:---|:---
Eksportér filer | matrixstreng\[\]  | En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen. | [  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]
GeneratedTime | streng | Det tidspunkt, hvor eksporten blev oprettet. | 2021-05-20T08:00:00Z

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

## <a name="see-also"></a>Se også

- [Eksportere vurderingsmetoder og egenskaber pr. enhed](get-assessmnt-1methods-properties.md)

- [Eksportér sikker konfigurationsvurdering pr. enhed](get-assessmnt-secure-cfg.md)

- [Eksportér vurdering af softwarelager pr. enhed](get-assessmnt-software-inventory.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)

- [Sårbarheder i din organisation](tvm-weaknesses.md)
