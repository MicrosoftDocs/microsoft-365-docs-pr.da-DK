---
title: Eksportér vurdering af softwarelager pr. enhed
description: Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.
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
ms.openlocfilehash: 4c3464a3aec242bd098503ac5bca997943ac2a4a
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63606574"
---
# <a name="export-software-inventory-assessment-per-device"></a>Eksportér vurdering af softwarelager pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Forskellige API-opkald får forskellige typer data. Da mængden af data kan være stor, er der to måder, det kan hentes på:

- [JSON-svar til vurdering af **eksport af softwarelager**](#1-export-software-inventory-assessment-json-response) API'en trækker alle data i organisationen som Json-svar. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

- [Eksportér vurdering af softwarelager **via filer**](#2-export-software-inventory-assessment-via-files)  Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:
  - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.
  - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

Data, der indsamles (ved hjælp _af enten Json-svar_ _eller via filer_), er det aktuelle øjebliksbillede af den aktuelle tilstand. Det indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

> [!NOTE]
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Vurdering af eksport af softwarelager (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af 1.1 API-metode

Dette API-svar indeholder alle data for installeret software pr. enhed. Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="limitations"></a>Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Satsbegrænsninger for denne API er 30 opkald i minuttet og 1000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Software.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Software.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000): Antal resultater som svar.
- $top: Det antal resultater, der skal returneres (returnerer ikke @odata.nextLink, og trækker derfor ikke alle dataene)

### <a name="15-properties"></a>1.5 Egenskaber

> [!NOTE]
>
> - Hver post er ca. 0,5 TB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres outputtet ikke nødvendigvis i samme rækkefølge, som er angivet i denne tabel.
> - Nogle ekstra kolonner kan returneres i svaret. Disse kolonner er midlertidige og kan fjernes. Brug kun de dokumenterede kolonner.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
DeviceId|streng|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|streng|Enhedens fulde domænenavn.|johnlaptop.europe.contoso.com
DiskPaths|Matrix[streng]|Disk bevis for, at produktet er installeret på enheden.|[ "C:\\ Programfiler (x86)\\MicrosoftSilverlightApplication\\\\\\silverlight.exe" ]
EndOfSupportDate|streng|Den dato, hvor understøttelsen af denne software er eller slutter.|2020-12-30
EndOfSupportStatus|streng|Ophør af supportstatus. Kan indeholde disse mulige værdier: Ingen, EOS-version, Kommende EOS-version, EOS-software, kommende EOS-software.|Kommende EOS
Id|streng|Entydigt id for posten.|123ABG55_573AG&mnp!
AntalOfWeaknesses|int|Antal af personer, der bruger denne software på denne enhed|3
OSPlatform|streng|Platform for operativsystemet, der kører på enheden. Dette er specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11
RbacGroupName|streng|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere
Registreringsdatabasestier|Matrix[streng]|Registreringsdatabasen beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\\ SOFTWAREWOW6432NodeMicrosoft\\\\\\ Windows\\ CurrentVersionUninstallMicrosoft\\\\ Silverlight" ]
SoftwareFirstSeenTimestamp|streng|Første gang denne software blev set på enheden.|2019-04-07 02:06:47
SoftwareName|streng|Navnet på softwareproduktet.|Silverlight
SoftwareVendor|streng|Navnet på softwareleverandøren.|microsoft
SoftwareVersion|streng|Softwareproduktets versionsnummer.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 Eksempler

#### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>1.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "numberOfWeaknesses": 58,
            "diskPaths": [],
            "registryPaths": [],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "Upcoming EOS Version",
            "endOfSupportDate": "2021-05-11T00:00:00+00:00"
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eed80d086e79bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.7.214.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765ddaf71234bde6bd733d6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178aedfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "configuration_manager",
            "softwareVersion": "5.0.8634.1000",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{B7D3A842-E826-4542-B39B-1D883264B279}"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f38765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-inventory-assessment-via-files"></a>2. Eksportér vurdering af softwarelager (via filer)

### <a name="21-api-method-description"></a>Beskrivelse af 2.1 API-metoden

Dette API-svar indeholder alle data for installeret software pr. enhed. Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="211-limitations"></a>Begrænsninger 2.1.1

Begrænsningerne for denne API er 5 opkald i minuttet og 20 opkald pr. time.

### <a name="22-permissions"></a>2.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Software.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|Software.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametre

- sasValidHours: Det antal timer, de hentede URL-adresser er gyldige i (maksimalt 24 timer)

### <a name="25-properties"></a>2.5 Egenskaber

> [!NOTE]
>
> - Filerne er gzip-komprimerede & I JSON-format med flere streger.
> - URL-adresserne til download er kun gyldige i tre timer. Ellers kan du bruge parameteren.
> - Du kan sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i, for at få den maksimale downloadhastighed.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til download af filer, der indeholder det aktuelle øjebliksbillede af organisationen|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|streng|Det tidspunkt, hvor eksporten blev oprettet.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Eksempler

#### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>2.6.2 Eksempel på svar

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>Se også

- [Eksportere vurderingsmetoder og egenskaber pr. enhed](get-assessment-methods-properties.md)
- [Eksportér sikker konfigurationsvurdering pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwarerisici pr. enhed](get-assessment-software-vulnerabilities.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
