---
title: Eksportere vurderingsmetoder og egenskaber pr. enhed
description: Indeholder oplysninger om de API'er, der trækker "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-opkald for at få forskellige typer data. Generelt indeholder hvert API-opkald de nødvendige data til enheder i organisationen.
keywords: API, API'er, eksportvurdering, pr. enhedsvurdering, pr. maskinvurdering, rapport over sikkerhedsrisiko, vurdering af sikkerhedsrisiko, rapport over sikkerhedsrisiko, sikker konfigurationsvurdering, sikker konfigurationsrapport, vurdering af softwarerisici, rapport om sikkerhedsrisiko, rapport over sikkerhedsrisiko efter maskine,
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
ms.openlocfilehash: c10f454919afc725b37537aa354fed05b95cb571
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63599425"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportere vurderingsmetoder og egenskaber pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>API-beskrivelse

Indeholder metoder og egenskabsoplysninger om de API'er, Håndtering af trusler og sikkerhedsrisici trækker data pr. enhed. Der er forskellige API-opkald for at få forskellige typer data. Generelt indeholder hvert API-opkald de nødvendige data til enheder i organisationen.

> [!NOTE]
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

Du kan bruge eksportvurderings-API'er til at hente (eksportere) forskellige typer oplysninger:

- [1. Eksportér vurdering af sikre konfigurationer](#1-export-secure-configurations-assessment)
- [2. Vurdering af eksport af softwarelager](#2-export-software-inventory-assessment)
- [3. Vurdering af softwarerisici](#3-export-software-vulnerabilities-assessment)

De API'er, der svarer til typerne af eksportoplysninger, er beskrevet i afsnit 1, 2 og 3.

Hver metode har forskellige API-opkald for at få forskellige typer data. Da mængden af data kan være stor, er der to måder, det kan hentes på:

- **JSON-svar**  API'en trækker alle data i organisationen som JSON-svar. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

- **via filer** Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:
  - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.
  - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

Data, der indsamles ved hjælp af enten "_JSON-svar_ _eller via filer_", er det aktuelle øjebliksbillede af den aktuelle tilstand. Det indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportér vurdering af sikre konfigurationer

Returnerer alle konfigurationer og deres status pr. enhed.

### <a name="11-methods"></a>1.1 Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
Eksportér sikker konfigurationsvurdering **(JSON-svar)**|Sikre konfiguration efter samling af enheder. Se: [1.2 Egenskaber (JSON-svar)](#12-properties-json-response)|Returnerer en tabel med en post for hver entydig kombination af DeviceId, ConfigurationId. API'en trækker alle data i organisationen som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Eksportér sikker **konfigurationsvurdering (via filer)**|Sikre konfiguration efter samling af enheder. Se: [1.3 Egenskaber (via filer)](#13-properties-via-files)|Returnerer en tabel med en post for hver entydig kombination af DeviceId, ConfigurationId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger: <ol><li>Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.</li><li>Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
configurationCategory|String|Kategori eller gruppering, som konfigurationen tilhører: Program, OPERATIVSYSTEM, Netværk, Konti, Sikkerhedskontrolelementer.
configurationId|String|Entydigt id for en bestemt konfiguration.
configurationImpact|String|Klassificeret effekt af konfigurationen på det overordnede konfigurationsscore (1-10).
configurationName|String|Det viste navn på konfigurationen.
configurationSubcategory|String|Underkategori eller undergruppering, som konfigurationen tilhører. I mange tilfælde er det specifikke funktioner eller funktioner.
deviceId|String|Entydigt id for enheden i tjenesten.
deviceName|String|Enhedens fulde domænenavn.
isApplicable|Bool|Angiver, om konfigurationen eller politikken er gældende.
isCompliant|Bool|Angiver, om konfigurationen eller politikken er konfigureret korrekt.
isExpectedUserImpact|Bool|Angiver, om brugeren bliver påvirket, hvis konfigurationen anvendes.
osPlatform|String|Platform for operativsystemet, der kører på enheden. Specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se yderligere oplysninger på TVM-understøttede operativsystemer og -platforme.
osVersion|String|Specifik version af det operativsystem, der kører på enheden.
rbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis enheden ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Rollebaseret adgangskontrol (RBAC) -gruppe-id.
anbefalingReference|String|En reference til det anbefalings-id, der er relateret til softwaren.
tidsstempel|String|Sidste gang konfigurationen blev set på enheden.

### <a name="13-properties-via-files"></a>1.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev oprettet.

## <a name="2-export-software-inventory-assessment"></a>2. Vurdering af eksport af softwarelager

Returnerer al installeret software og deres oplysninger på hver enhed.

### <a name="21-methods"></a>2.1 Metoder

|Metode|Datatype|Beskrivelse|
|:---|:---|:---|
|Vurdering af eksport af **softwarelager (JSON-svar)**|Lager af software efter enhedssamling. Se: [2.2 Egenskaber (JSON-svar)](#22-properties-json-response)|Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. API'en trækker alle data i organisationen som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. |
| Eksportér vurdering af **softwarelager (via filer)**|Lager af software efter enhedsfiler. Se: [2.3 Egenskaber (via filer)](#23-properties-via-files)|Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at downloade data fra Azure Storage som følger: <ol><li>Ring til API'en for at få en liste over download-URL-adresser med organisationens data</li><li>Download filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
DeviceId|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Enhedens fulde domænenavn.
DiskPaths|Matrix[streng]|Disk bevis for, at produktet er installeret på enheden.
EndOfSupportDate|String|Den dato, hvor understøttelsen af denne software er eller slutter.
EndOfSupportStatus|String|Ophør af supportstatus. Kan indeholde disse mulige værdier: Ingen, EOS-version, Kommende EOS-version, EOS-software, kommende EOS-software.
AntalOfWeaknesses|Int|Antal af personer, der bruger denne software på denne enhed.
OSPlatform|String|Platform for det operativsystem, der kører på enheden. specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Rollebaseret adgangskontrol (RBAC) -gruppe-id.
Registreringsdatabasestier|Matrix[streng]|Registreringsdatabasen beviser, at produktet er installeret på enheden.
SoftwareFirstSeenTimestamp|String|Første gang denne software blev set på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.

### <a name="23-properties-via-files"></a>2.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev oprettet.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Vurdering af softwarerisici

Returnerer alle kendte sikkerhedsrisici på en enhed og deres oplysninger for alle enheder.

### <a name="31-methods"></a>3.1 Metoder

Metode|Datatype|Beskrivelse
:---|:---|:---
Vurdering af eksport af **softwarerisici (JSON-svar)**|Undersøgelsessamling Se: [3.2 Egenskaber (JSON-svar)](#32-properties-json-response)|Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. API'en trækker alle data i organisationen som JSON-svar. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Vurdering af softwarerisici **(via filer)**|Undersøgelsesenhed Se: [3.3 Egenskaber (via filer)](#33-properties-via-files)|Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Det anbefales derfor til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger: <ol><li>Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.</li><li>Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.</li></ol>
**Vurdering af sårbarheder** ved eksport af **deltasoftware (JSON-svar)**|Undersøgelsessamling Se: [3.4 Properties Delta-eksport (JSON-svar)](#34-properties-delta-export-json-response)|Returnerer en tabel med et element for hver entydige kombination af: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId og EventTimestamp. <p> API'en trækker data i organisationen som JSON-svar. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater. Den fulde vurdering af softwarerisici (JSON-svar) bruges til at få et helt øjebliksbillede af din organisations softwarerisici efter enhed. Men deltaeksport-API-opkaldet bruges til kun at hente de ændringer, der er sket mellem en valgt dato og den aktuelle dato ("delta"-API-opkaldet). I stedet for at eksportere en stor mængde data hver gang, får du kun specifikke oplysninger om nye, rettede og opdaterede sårbarheder. Deltaeksport-API-kald kan også bruges til at beregne forskellige KPI'er, f.eks. "hvor mange sårbarheder blev rettet?" eller "hvor mange nye sårbarheder blev føjet til min organisation?" <p> Da Delta-eksport-API-opkald til softwaresårbarheder kun returnerer data for et målrettet datointerval, betragtes det ikke som en _fuld eksport_.

### <a name="32-properties-json-response"></a>3.2 Egenskaber (JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
CveId|String|Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures).
CvssScore|String|CVSS-scoren for CVE'en.
DeviceId|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Enhedens fulde domænenavn.
DiskPaths|Matrixstreng\[\]|Disk bevis for, at produktet er installeret på enheden.
ExploitabilityLevel|String|Udnyttelsesniveauet for denne risiko (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|String|Første gang CVE'en for dette produkt blev set på enheden.
Id|String|Entydigt id for posten.
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.
OSPlatform|String|Platform for det operativsystem, der kører på enheden. specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
rbacGroupId|String|Rollebaseret adgangskontrol (RBAC) -gruppe-id.
AnbefalingReference|String|En reference til det anbefalings-id, der er relateret til denne software.
RecommendedSecurityUpdate|String|Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen.
RecommendedSecurityUpdateId|String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB).
Matrixstrenge i registreringsdatabasen\[\]|Registreringsdatabasen beviser, at produktet er installeret på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.
VulnerabilitySeverityLevel|String|Alvorsniveau, der er tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet.

### <a name="33-properties-via-files"></a>3.3 Egenskaber (via filer)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
Eksportér filer|matrixstreng\[\]|En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime|String|Det tidspunkt, hvor eksporten blev oprettet.

### <a name="34-properties-delta-export-json-response"></a>3.4 Egenskaber (deltaeksport JSON-svar)

Egenskab (id)|Datatype|Beskrivelse
:---|:---|:---
CveId |String|Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures).
CvssScore|String|CVSS-scoren for CVE'en.
DeviceId|String|Entydigt id for enheden i tjenesten.
DeviceName|String|Enhedens fulde domænenavn.
DiskPaths|Matrix[streng]|Disk bevis for, at produktet er installeret på enheden.
EventTimestamp|String|Det tidspunkt, hvor deltabegivenhed blev fundet.
ExploitabilityLevel|String|Sikkerhedsrisikoens udnyttelsesniveau (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|String|Første gang produktets CVE blev set på enheden.
Id|String|Entydigt id for posten.  
LastSeenTimestamp|String|Sidste gang CVE blev set på enheden.
OSPlatform|String|Platform for det operativsystem, der kører på enheden. specifikke operativsystemer med variationer inden for den samme familie, f.eks. Windows 10 og Windows 11. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName|String|Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
AnbefalingReference|String|En reference til det anbefalings-id, der er relateret til denne software.
RecommendedSecurityUpdate |String|Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen.
RecommendedSecurityUpdateId |String|Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB)
Registreringsdatabasestier |Matrix[streng]|Registreringsdatabasen beviser, at produktet er installeret på enheden.
SoftwareName|String|Navnet på softwareproduktet.
SoftwareVendor|String|Navnet på softwareleverandøren.
SoftwareVersion|String|Softwareproduktets versionsnummer.
Status|String|**Nyt** (ved en ny sikkerhedsrisiko, der introduceres på en enhed). **Rettet** (ved en sikkerhedsrisiko, der ikke længere findes på enheden, hvilket betyder, at det er løst). **Opdateret** (for en sikkerhedsrisiko på en enhed, der er blevet ændret. De mulige ændringer er: CVSS-score, udnyttelsesniveau, alvorsniveau, DiskPaths, Registreringsdatabasestier, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|String|Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet.

## <a name="see-also"></a>Se også

- [Eksportér sikker konfigurationsvurdering pr. enhed](get-assessment-secure-config.md)
- [Eksportér vurdering af softwarelager pr. enhed](get-assessment-software-inventory.md)
- [Eksportér vurdering af softwarerisici pr. enhed](get-assessment-software-vulnerabilities.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
