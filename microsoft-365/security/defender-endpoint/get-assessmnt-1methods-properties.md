---
title: Eksportere vurderingsmetoder og egenskaber pr. enhed
description: Indeholder oplysninger om de API'er, der trækker "Håndtering af trusler og sikkerhedsrisici"-data. Der er forskellige API-opkald for at få forskellige typer data. Generelt indeholder hvert API-opkald de nødvendige data til enheder i organisationen. Da mængden af data kan være stor, er der to måder, hvorpå den kan hentes
keywords: API, API'er, eksportvurdering, pr. enhedsvurdering, pr. maskinvurdering, rapport over sikkerhedsrisiko, vurdering af sikkerhedsrisiko, rapport over sikkerhedsrisiko, sikker konfigurationsvurdering, sikker konfigurationsrapport, vurdering af softwarerisici, rapport om sikkerhedsrisiko, rapport over sikkerhedsrisiko efter maskine,
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
ms.openlocfilehash: e820875a3350761824c3e4e67311e55507a9cb6f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/05/2021
ms.locfileid: "63592225"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Eksportere vurderingsmetoder og egenskaber pr. enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>API-beskrivelse

Indeholder metoder og egenskabsoplysninger om de API'er, Håndtering af trusler og sikkerhedsrisici trækker data pr. enhed. Der er forskellige API-opkald for at få forskellige typer data. Generelt indeholder hvert API-opkald de nødvendige data til enheder i organisationen.

> [!Note]
>
> Medmindre andet er angivet, er alle de angivne **_eksportmetoder fuld eksport_** **_og efter_** enhed (også kaldet **_pr. enhed_**).

Der er tre API-metoder, du kan bruge til at hente (eksportere) forskellige typer oplysninger:

1. Eksportér vurdering af sikre konfigurationer

2. Vurdering af eksport af softwarelager

3. Vurdering af softwarerisici i forbindelse med eksport af software

For hver metode er der forskellige API-opkald for at få forskellige typer data. Da mængden af data kan være stor, er der to måder, det kan hentes på:

- **OData**  API'en trækker alle data i organisationen som Json-svar efter OData-protokollen. Denne metode er bedst til _små organisationer med mindre end 100 K-enheder_. Svaret er pagineret, så du kan bruge \@feltet odata.nextLink fra svaret til at hente de næste resultater.

- **via filer** Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data fra Azure Storage som følger:

  - Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data.

  - Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

Data, der indsamles (ved hjælp af _enten OData_ _eller via_ filer), er det aktuelle øjebliksbillede af den aktuelle tilstand og indeholder ikke historiske data. For at indsamle historiske data skal kunderne gemme dataene i deres egne datalagringer.

## <a name="1-export-secure-configurations-assessment"></a>1. Eksportér vurdering af sikre konfigurationer

Returnerer alle konfigurationer og deres status pr. enhed.

### <a name="11-methods"></a>1.1 Metoder

Metode | Datatype | Beskrivelse
:---|:---|:---
Eksportér vurdering af sikker konfiguration **(OData)** | Sikre konfiguration efter samling af enheder. Se: [1.2 Egenskaber (OData)](#12-properties-odata) | Returnerer en tabel med en post for hver entydig kombination af DeviceId, ConfigurationId. API'en trækker alle data i organisationen som Json-svar efter OData-protokollen. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Eksportér sikker **konfigurationsvurdering (via filer)** | Sikre konfiguration efter samling af enheder. Se: [1.2 Egenskaber (OData)](#12-properties-odata) | Returnerer en tabel med en post for hver entydig kombination af DeviceId, ConfigurationId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data Azure Storage følgende: 1.  Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data. 2.  Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

### <a name="12-properties-odata"></a>1.2 Egenskaber (OData)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
ConfigurationCategory | streng | Kategori eller gruppering, som konfigurationen tilhører: Program, OPERATIVSYSTEM, Netværk, Konti, Sikkerhedskontrolelementer
ConfigurationId | streng | Entydigt id for en bestemt konfiguration
ConfigurationImpact | streng | Klassificeret effekt af konfigurationen på det overordnede konfigurationsresultat (1-10)
ConfigurationName | streng | Visningsnavn for konfigurationen
ConfigurationSubcategory | streng | Underkategori eller undergruppering, som konfigurationen tilhører. I mange tilfælde beskrives specifikke funktioner.
DeviceId | streng | Entydigt id for enheden i tjenesten.
DeviceName | streng | Enhedens fulde domænenavn.
IsApplicable | bool | Angiver, om konfigurationen eller politikken er gældende
IsCompliant | bool | Angiver, om konfigurationen eller politikken er konfigureret korrekt
IsExpectedUserImpact | bool | Angiver, om der vil være brugerpåvirkning, hvis konfigurationen anvendes
OSPlatform | streng | Platform for operativsystemet, der kører på enheden. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 7. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName | streng | Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
AnbefalingReference | streng | En reference til det anbefalings-id, der er relateret til denne software.
Tidsstempel | streng | Sidste gang konfigurationen blev set på enheden

### <a name="13-properties-via-files"></a>1.3 Egenskaber (via filer)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
Eksportér filer | matrixstreng\[\] | En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime | streng | Det tidspunkt, hvor eksporten blev oprettet.

## <a name="2-export-software-inventory-assessment"></a>2. Vurdering af eksport af softwarelager

Returnerer al installeret software og deres oplysninger på hver enhed.

### <a name="21-methods"></a>2.1 Metoder

Metode | Datatype | Beskrivelse
:---|:---|:---
Vurdering af eksport af **softwarelager (OData)** | Lager af software efter enhedssamling. Se: [2.2 Egenskaber (OData)](#22-properties-odata) | Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. API'en trækker alle data i organisationen som Json-svar efter OData-protokollen. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Eksportér vurdering af **softwarelager (via filer)** | Lager af software efter enhedsfiler. Se: [2.3 Egenskaber (via filer)](#23-properties-via-files) | Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data Azure Storage følgende: 1.  Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data. 2.  Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

### <a name="22-properties-odata"></a>2.2 Egenskaber (OData)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
DeviceId | streng | Entydigt id for enheden i tjenesten.
DeviceName | streng | Enhedens fulde domænenavn.
DiskPaths | Matrix[streng]  | Disk bevis for, at produktet er installeret på enheden.
EndOfSupportDate | streng | Den dato, hvor understøttelsen af denne software er eller slutter.
EndOfSupportStatus | streng | Ophør af supportstatus. Kan indeholde disse mulige værdier: Ingen, EOS-version, Kommende EOS-version, EOS-software, kommende EOS-software.
Id | streng | Entydigt id for posten.
AntalOfWeaknesses | int|Antal af personer, der bruger denne software på denne enhed
OSPlatform | streng | Platform for operativsystemet, der kører på enheden. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 7. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName | streng | Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
Registreringsdatabasestier | Matrix[streng] | Registreringsdatabasen beviser, at produktet er installeret på enheden.
SoftwareFirstSeenTimestamp | streng | Første gang denne software blev set på enheden.
SoftwareName | streng | Navnet på softwareproduktet.
SoftwareVendor | streng | Navnet på softwareleverandøren.
SoftwareVersion | streng | Softwareproduktets versionsnummer.

### <a name="23-properties-via-files"></a>2.3 Egenskaber (via filer)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
Eksportér filer | matrixstreng\[\] | En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime | streng | Det tidspunkt, hvor eksporten blev oprettet.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Vurdering af softwarerisici

Returnerer alle kendte sikkerhedsrisici på en enhed og deres oplysninger for alle enheder.

### <a name="31-methods"></a>3.1 Metoder

Metode | Datatype | Beskrivelse
:---|:---|:---
Vurdering af eksport af softwarerisici **(OData)** | Undersøgelsessamling Se: [3.2 Egenskaber (OData)](#32-properties-odata) | Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. API'en trækker alle data i organisationen som Json-svar efter OData-protokollen. Denne metode er bedst til små organisationer med mindre end 100 K-enheder. Svaret er pagineret, så du kan bruge feltet @odata.nextLink fra svaret til at hente de næste resultater.
Vurdering af softwarerisici **(via filer)** | Undersøgelsesenhed Se: [3.3 Egenskaber (via filer)](#33-properties-via-files) | Returnerer en tabel med et element for hver entydige kombination af DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId. Denne API-løsning gør det muligt at trække større mængder data hurtigere og mere pålideligt. Derfor anbefales det til store organisationer med mere end 100 K-enheder. Denne API henter alle data i organisationen som downloadfiler. Svaret indeholder URL-adresser til at hente alle data fra Azure Storage. Denne API gør det muligt at hente alle dine data Azure Storage følgende: 1.  Ring til API'en for at få en liste over downloadede URL-adresser med alle organisationens data. 2.  Download alle filerne ved hjælp af URL-adresserne til overførslen, og bearbejde dataene, som du ønsker.

### <a name="32-properties-odata"></a>3.2 Egenskaber (OData)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
CveId | streng | Entydigt id, der er tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures).
CvssScore | streng | CVSS-scoren for CVE'en.
DeviceId | streng | Entydigt id for enheden i tjenesten.
DeviceName | streng | Enhedens fulde domænenavn.
DiskPaths | Matrixstreng\[\] | Disk bevis for, at produktet er installeret på enheden.
ExploitabilityLevel | streng | Udnyttelsesniveauet for denne risiko (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp | streng | Første gang CVE'en for dette produkt blev set på enheden.
Id | streng | Entydigt id for posten.
LastSeenTimestamp | streng | Sidste gang CVE blev set på enheden.
OSPlatform | streng | Platform for operativsystemet, der kører på enheden. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 7. Se tvm-understøttede operativsystemer og platforme for at få flere oplysninger.
RbacGroupName | streng | Den rollebaserede adgangskontrolgruppe (RBAC). Hvis denne enhed ikke er tildelt nogen RBAC-gruppe, bliver værdien "Ikke tildelt". Hvis organisationen ikke indeholder nogen RBAC-grupper, er værdien "Ingen".
AnbefalingReference | streng | En reference til det anbefalings-id, der er relateret til denne software.
RecommendedSecurityUpdate | streng | Navn eller beskrivelse af den sikkerhedsopdatering, softwareleverandøren har leveret for at løse sikkerhedsrisikoen.
RecommendedSecurityUpdateId | streng | Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB)
Matrixstrenge i registreringsdatabasen\[\] | Registreringsdatabasen beviser, at produktet er installeret på enheden.
SoftwareName | streng | Navnet på softwareproduktet.
SoftwareVendor | streng | Navnet på softwareleverandøren.
SoftwareVersion | streng | Softwareproduktets versionsnummer.
VulnerabilitySeverityLevel | streng | Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet.

### <a name="33-properties-via-files"></a>3.3 Egenskaber (via filer)

Egenskab (id) | Datatype | Beskrivelse
:---|:---|:---
Eksportér filer | matrixstreng\[\]  | En liste over DOWNLOAD URL-adresser til filer, der indeholder det aktuelle øjebliksbillede af organisationen.
GeneratedTime | streng | Det tidspunkt, hvor eksporten blev oprettet.

## <a name="see-also"></a>Se også

- [Eksportér sikker konfigurationsvurdering pr. enhed](get-assessmnt-secure-cfg.md)

- [Eksportér vurdering af softwarelager pr. enhed](get-assessmnt-software-inventory.md)

- [Eksportér vurdering af softwarerisici pr. enhed](get-assessmnt-software-vulnerabilities.md)

Andre relaterede

- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)

- [Sårbarheder i din organisation](tvm-weaknesses.md)
