---
title: Eksportér vurdering af softwarelager pr. enhed
description: Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.
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
ms.openlocfilehash: 296b977452802d8e1ed8949cf6a8871cac171f3a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839988"
---
# <a name="export-software-inventory-assessment-per-device"></a>Eksportér vurdering af softwarelager pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Forskellige API-kald henter forskellige typer data. Da mængden af data kan være stor, er der to måder, den kan hentes på:

- [**JSON-svar til** evaluering af softwarelager](#1-export-software-inventory-assessment-json-response) API'en henter alle data i din organisation som Json-svar. Denne metode er bedst til _små organisationer med mindre end 100.000 enheder_. Svaret er sideinddelt, så du kan bruge feltet \@odata.nextLink fra svaret til at hente de næste resultater.

- [Eksportér **softwareoversigtsvurdering via filer**](#2-export-software-inventory-assessment-via-files)  Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade alle dine data fra Azure Storage på følgende måde:
  - Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.
  - Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.

Data, der indsamles (ved hjælp af enten _Json-svar_ eller _via filer_), er det aktuelle snapshot af den aktuelle tilstand. Den indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagre.

> [!NOTE]
> Medmindre andet er angivet, er alle angivne eksportvurderingsmetoder **_fuld eksport_** og **_efter enhed_** (også kaldet **_pr. enhed_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. Eksportér vurdering af softwarelager (JSON-svar)

### <a name="11-api-method-description"></a>Beskrivelse af API-metoden 1.1

Dette API-svar indeholder alle data fra installeret software pr. enhed. Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="limitations"></a>Begrænsninger

- Den maksimale sidestørrelse er 200.000.
- Hastighedsbegrænsninger for denne API er 30 kald pr. minut og 1.000 opkald pr. time.

### <a name="12-permissions"></a>1.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Software.Read.All|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'
Uddelegeret (arbejds- eller skolekonto)|Software.Read|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'

### <a name="13-url"></a>1.3 URL-adresse

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 Parametre

- pageSize (standard = 50.000): Antal resultater i svar.
- $top: Antallet af resultater, der skal returneres (returnerer ikke @odata.nextLink og trækker derfor ikke alle dataene)

### <a name="15-properties"></a>1.5 Egenskaber

> [!NOTE]
>
> - Hver post er ca. 0,5 KB data. Du skal tage højde for dette, når du vælger den korrekte pageSize-parameter for dig.
> - De egenskaber, der er defineret i følgende tabel, vises alfabetisk efter egenskabs-id. Når du kører denne API, returneres det resulterende output ikke nødvendigvis i den samme rækkefølge, som er angivet i denne tabel.
> - Nogle yderligere kolonner kan blive returneret i svaret. Disse kolonner er midlertidige og kan blive fjernet. Brug kun de dokumenterede kolonner.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Deviceid|Streng|Entydigt id for enheden i tjenesten.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|Streng|Fuldt domænenavn (FQDN) for enheden.|johnlaptop.europe.contoso.com
DiskPaths|Matrix[streng]|Disk, der beviser, at produktet er installeret på enheden.|[ "C:\\ Programfiler (x86)\\Microsoft\\Silverlight-program\\\\silverlight.exe" ]
Slutdato for support|Streng|Den dato, hvor support til denne software er eller ophører.|2020-12-30
EndOfSupportStatus|Streng|Ophør af supportstatus. Kan indeholde disse mulige værdier: None, EOS Version, Upcoming EOS Version, EOS Software, Upcoming EOS Software.|Kommende EOS
Id|Streng|Entydigt id for posten.|123ABG55_573AG&mnp!
NumberOfWeaknesses|Int|Antal svagheder ved denne software på denne enhed|3
OSPlatform|Streng|Platform for det operativsystem, der kører på enheden. Disse er specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.|Windows10 og Windows 11
RbacGroupName|Streng|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".|Servere
RegistryPaths|Matrix[streng]|Registreringsdatabase beviser, at produktet er installeret på enheden.|[ "HKEY_LOCAL_MACHINE\\ SOFTWARE\\WOW6432Node\\Microsoft\\ Windows\\ CurrentVersion\\Uninstall\\Microsoft Silverlight" ]
SoftwareFirstSeenTimestamp|Streng|Første gang denne software blev set på enheden.|2019-04-07 02:06:47
SoftwareName|Streng|Navnet på softwareproduktet.|Silverlight
SoftwareVendor|Streng|Navnet på softwareleverandøren.|Microsoft
SoftwareVersion|Streng|Softwareproduktets versionsnummer.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 Eksempler

#### <a name="161-request-example"></a>1.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>1.6.2 Svareksempel

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

### <a name="21-api-method-description"></a>2.1 Beskrivelse af API-metode

Dette API-svar indeholder alle data fra installeret software pr. enhed. Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion.

#### <a name="211-limitations"></a>2.1.1 Begrænsninger

Hastighedsbegrænsninger for denne API er 5 kald pr. minut og 20 opkald pr. time.

### <a name="22-permissions"></a>2.2 Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender for Endpoint API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Vist navn for tilladelse
---|---|---
Program|Software.Read.All|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'
Uddelegeret (arbejds- eller skolekonto)|Software.Read|\'Læs oplysninger om sårbarheder i forbindelse med trussels- og sårbarhedsstyring\'

### <a name="23-url"></a>2.3 URL-adresse

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>Parametre

- sasValidHours: Det antal timer, som URL-adresserne til download er gyldige i (højst 24 timer)

### <a name="25-properties"></a>2.5 Egenskaber

> [!NOTE]
>
> - Filerne er gzip-komprimerede & i JSON-format med flere streger.
> - URL-adresserne til download er kun gyldige i tre timer. Ellers kan du bruge parameteren .
> - Hvis du vil have maksimal downloadhastighed for dine data, kan du sikre dig, at du downloader fra det samme Azure-område, som dine data er placeret i.

<br>

****

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|Streng|Det tidspunkt, hvor eksporten blev genereret.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 Eksempler

#### <a name="261-request-example"></a>2.6.1 Eksempel på anmodning

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>2.6.2 Svareksempel

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

- [Eksportér vurderingsmetoder og -egenskaber pr. enhed](get-assessment-methods-properties.md)
- [Eksportér vurdering af sikker konfiguration pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwaresårbarheder pr. enhed](get-assessment-software-vulnerabilities.md)

Andre relaterede

- [Risikobaseret trussel & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsrisici i din organisation](tvm-weaknesses.md)
