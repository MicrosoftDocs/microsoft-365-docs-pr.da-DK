---
title: Eksportér vurderingsmetoder og -egenskaber pr. enhed
description: Indeholder oplysninger om de API'er, der henter "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.
keywords: api, apis, eksportvurdering, vurdering pr. enhed, vurdering af maskine, vurderingsrapport for sårbarheder, vurdering af enhedssårbarhed, rapport over enhedssårbarhed, vurdering af sikker konfiguration, vurdering af softwaresårbarheder, rapport over softwaresårbarheder, sårbarhedsrapport efter maskine,
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
ms.openlocfilehash: fc2686b9ef6a30c9c81d7633ce8a59a0454d622d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838932"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportér vurderingsmetoder og -egenskaber pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>API-beskrivelse

Indeholder metoder og egenskabsoplysninger om de API'er, der henter Håndtering af trusler og sikkerhedsrisici data pr. enhed. Der er forskellige API-kald til at hente forskellige typer data. Generelt indeholder hvert API-kald de nødvendige data for enheder i din organisation.

> [!NOTE]
> Medmindre andet er angivet, er alle angivne eksportvurderingsmetoder **_fuld eksport_** og **_efter enhed_** (også kaldet **_pr. enhed_**).

Du kan bruge API'erne til eksportvurdering til at hente (eksportere) forskellige typer oplysninger:

- [1. Eksportér vurdering af sikre konfigurationer](#1-export-secure-configurations-assessment)
- [2. Eksportér vurdering af softwarelager](#2-export-software-inventory-assessment)
- [3. Eksportér vurdering af softwaresårbarheder](#3-export-software-vulnerabilities-assessment)

De API'er, der svarer til typerne af eksportoplysninger, er beskrevet i afsnit 1, 2 og 3.

Hver metode har forskellige API-kald for at hente forskellige typer data. Da mængden af data kan være stor, er der to måder, den kan hentes på:

- **JSON-svar**  API'en henter alle data i din organisation som JSON-svar. Denne metode er bedst til _små organisationer med mindre end 100.000 enheder_. Svaret er sideinddelt, så du kan bruge feltet \@odata.nextLink fra svaret til at hente de næste resultater.

- **via filer** Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade alle dine data fra Azure Storage på følgende måde:
  - Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.
  - Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.

Data, der indsamles ved hjælp af enten '_JSON-svar_ eller _via filer_', er det aktuelle snapshot af den aktuelle tilstand. Den indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagre.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportér vurdering af sikre konfigurationer

Returnerer alle konfigurationer og deres status pr. enhed.

### <a name="11-methods"></a>1.1 Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
Eksportér vurdering af sikker konfiguration **(JSON-svar)**|Sikker konfiguration efter enhedsgruppe. Se: [1.2 Egenskaber (JSON-svar)](#12-properties-json-response)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, ConfigurationId. API'en henter alle data i din organisation som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100.000 enheder. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Eksportér vurdering af sikker konfiguration **(via filer)**|Sikker konfiguration efter enhedsgruppe. Se: [1.3 Egenskaber (via filer)](#13-properties-via-files)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, ConfigurationId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade alle dine data fra Azure Storage på følgende måde: <ol><li>Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.</li><li>Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
configurationCategory|String|Kategori eller gruppering, som konfigurationen tilhører: Application, OS, Network, Accounts, Security controls.
configurationId|String|Entydigt id for en bestemt konfiguration.
configurationImpact|String|Den vurderede effekt af konfigurationen til den overordnede konfigurationsscore (1-10).
configurationName|String|Vist navn på konfigurationen.
configurationSubcategory|String|Den underkategori eller undergruppe, som konfigurationen tilhører. I mange tilfælde specifikke egenskaber eller funktioner.
Deviceid|String|Entydigt id for enheden i tjenesten.
deviceName|String|Fuldt domænenavn (FQDN) for enheden.
isApplicable|Bool|Angiver, om konfigurationen eller politikken er relevant.
er i overensstemmelse|Bool|Angiver, om konfigurationen eller politikken er konfigureret korrekt.
isExpectedUserImpact|Bool|Angiver, om brugeren bliver påvirket, hvis konfigurationen anvendes.
osPlatform|String|Platform for det operativsystem, der kører på enheden. Specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se TVM-understøttede operativsystemer og platforme for at få flere oplysninger.
osVersion|String|Specifik version af operativsystemet, der kører på enheden.
rbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis enheden ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Det rollebaserede RBAC-gruppe-id (Access Control).
recommendationReference|String|En reference til det anbefalings-id, der er relateret til softwaren.
Tidsstempel|String|Sidste gang konfigurationen blev set på enheden.

### <a name="13-properties-via-files"></a>1.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev genereret.

## <a name="2-export-software-inventory-assessment"></a>2. Eksportér vurdering af softwarelager

Returnerer al den installerede software og deres oplysninger på hver enhed.

### <a name="21-methods"></a>2.1 Metoder

|Metode|Datatype|Beskrivelse|
|:---|:---|:---|
|Vurdering af softwarelager **(JSON-svar)**|Softwareoversigt efter enhedsindsamling. Se: [2.2 Egenskaber (JSON-svar)](#22-properties-json-response)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. API'en henter alle data i din organisation som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100.000 enheder. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. |
| Eksportér vurdering af softwarelager **(via filer)**|Softwareoversigt efter enhedsfiler. Se: [2.3 Egenskaber (via filer)](#23-properties-via-files)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade data fra Azure Storage på følgende måde: <ol><li>Kald API'en for at få en liste over URL-adresser til download med dine organisationsdata</li><li>Download filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Deviceid|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Fuldt domænenavn (FQDN) for enheden.
DiskPaths|Matrix[streng]|Disk, der beviser, at produktet er installeret på enheden.
Slutdato for support|String|Den dato, hvor support til denne software er eller ophører.
EndOfSupportStatus|String|Ophør af supportstatus. Kan indeholde disse mulige værdier: None, EOS Version, Upcoming EOS Version, EOS Software, Upcoming EOS Software.
NumberOfWeaknesses|Int|Antal svagheder ved denne software på denne enhed.
OSPlatform|String|Platform for det operativsystem, der kører på enheden; specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Det rollebaserede RBAC-gruppe-id (Access Control).
RegistryPaths|Matrix[streng]|Registreringsdatabase beviser, at produktet er installeret på enheden.
SoftwareFirstSeenTimestamp|String|Første gang denne software blev set på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.

### <a name="23-properties-via-files"></a>2.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev genereret.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Eksportér vurdering af softwaresårbarheder

Returnerer alle kendte sikkerhedsrisici på en enhed og deres oplysninger for alle enheder.

### <a name="31-methods"></a>3.1 Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
Eksportér vurdering af softwaresårbarheder **(JSON-svar)**|Undersøgelsessamling Se: [3.2 Egenskaber (JSON-svar)](#32-properties-json-response)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. API'en henter alle data i din organisation som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100.000 enheder. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Eksportér vurdering af softwaresårbarheder **(via filer)**|Undersøgelsesobjekt Se: [3.3 Egenskaber (via filer)](#33-properties-via-files)|Returnerer en tabel med en post for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100.000 enheder. Denne API henter alle data i din organisation som downloadfiler. Svaret indeholder URL-adresser til download af alle data fra Azure Storage. Denne API giver dig mulighed for at downloade alle dine data fra Azure Storage på følgende måde: <ol><li>Kald API'en for at få en liste over URL-adresser til download med alle dine organisationsdata.</li><li>Download alle filerne ved hjælp af URL-adresserne til download, og behandl dataene, som du vil.</li></ol>
**Vurdering af sårbarheder i forbindelse med deltaeksportsoftware** **(JSON-svar)**|Undersøgelsessamling Se: [3.4 Egenskaber Deltaeksport (JSON-svar)](#34-properties-delta-export-json-response)|Returnerer en tabel med en post for hver entydige kombination af: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId og EventTimestamp. <p> API'en henter data i din organisation som JSON-svar. Svaret er sideinddelt, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. JSON-svaret (full software vulnerabilities assessment) bruges til at få et helt snapshot af vurderingen af softwaresårbarheder for din organisation efter enhed. Api-kaldet til deltaeksport bruges dog kun til at hente de ændringer, der er foretaget mellem en valgt dato og dags dato (API-kaldet "delta"). I stedet for at få en fuld eksport med en stor mængde data hver gang får du kun specifikke oplysninger om nye, faste og opdaterede sikkerhedsrisici. Delta-eksport-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sikkerhedsrisici der blev rettet?" eller "hvor mange nye sikkerhedsrisici blev føjet til min organisation?" <p> Da delta-eksport-API-kaldet for softwaresårbarheder kun returnerer data for et bestemt datointerval, betragtes det ikke som en _fuld eksport_.

### <a name="32-properties-json-response"></a>3.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
CveId|String|Entydigt id, der er tildelt sikkerhedssårbarheden under CVE-systemet (Common Vulnerabilities and Exposures).
CvssScore|String|CVSS-scoren for CVE.
Deviceid|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Fuldt domænenavn (FQDN) for enheden.
DiskPaths|Matrixstreng\[\]|Disk, der beviser, at produktet er installeret på enheden.
Udnyttelsesniveau|String|Udnyttelsesniveauet for denne sårbarhed (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|String|Første gang CVE for dette produkt blev set på enheden.
Id|String|Entydigt id for posten.
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.
OSPlatform|String|Platform for det operativsystem, der kører på enheden; specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Det rollebaserede RBAC-gruppe-id (Access Control).
Reference til anbefaling|String|En reference til det anbefalings-id, der er relateret til denne software.
RecommendedSecurityUpdate|String|Navn på eller beskrivelse af den sikkerhedsopdatering, der leveres af softwareleverandøren til at løse problemet med sårbarheden.
RecommendedSecurityUpdateId|String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator for den tilsvarende vejledning eller videnbase (KB) artikler.
Matrixstreng\[for registreringsdatabasestier\]|Registreringsdatabase beviser, at produktet er installeret på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.
VulnerabilitySeverityLevel|String|Alvorsgradsniveau, der er tildelt til sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselslandskabet.

### <a name="33-properties-via-files"></a>3.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over URL-adresser til hentning af filer, der indeholder det aktuelle snapshot af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev genereret.

### <a name="34-properties-delta-export-json-response"></a>3.4 Egenskaber (delta export JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
CveId |String|Entydigt id, der er tildelt sikkerhedssårbarheden under CVE-systemet (Common Vulnerabilities and Exposures).
CvssScore|String|CVSS-scoren for CVE.
Deviceid|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Fuldt domænenavn (FQDN) for enheden.
DiskPaths|Matrix[streng]|Disk, der beviser, at produktet er installeret på enheden.
EventTimestamp|String|Det tidspunkt, hvor delta-hændelsen blev fundet.
Udnyttelsesniveau|String|Sårbarhedens udnyttelsesniveau (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|String|Første gang, produktets CVE blev set på enheden.
Id|String|Entydigt id for posten.  
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.
OSPlatform|String|Platform for det operativsystem, der kører på enheden; specifikke operativsystemer med variationer inden for samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, vil værdien være "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
Reference til anbefaling|String|En reference til det anbefalings-id, der er relateret til denne software.
RecommendedSecurityUpdate |String|Navn på eller beskrivelse af den sikkerhedsopdatering, der leveres af softwareleverandøren til at løse problemet med sårbarheden.
RecommendedSecurityUpdateId |String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator for de tilsvarende artikler om vejledning eller videnbase (KB)
RegistryPaths |Matrix[streng]|Registreringsdatabase beviser, at produktet er installeret på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.
Status|String|**Ny** (for en ny sårbarhed, der introduceres på en enhed). **Løst** (for en sårbarhed, der ikke længere findes på enheden, hvilket betyder, at den blev afhjælpet). **Opdateret** (for en sårbarhed på en enhed, der er blevet ændret. De mulige ændringer er: CVSS-score, udnyttelsesniveau, alvorsgradsniveau, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|String|Alvorsgradsniveau, der er tildelt sikkerhedssårbarheden baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselslandskabet.

## <a name="see-also"></a>Se også

- [Eksportér vurdering af sikker konfiguration pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwarelager pr. enhed](get-assessment-software-inventory.md)
- [Eksportér vurdering af softwaresårbarheder pr. enhed](get-assessment-software-vulnerabilities.md)

Andre relaterede

- [Risikobaseret trussel & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsrisici i din organisation](tvm-weaknesses.md)
