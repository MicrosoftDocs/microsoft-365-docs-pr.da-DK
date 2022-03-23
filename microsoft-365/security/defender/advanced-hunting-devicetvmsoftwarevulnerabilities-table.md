---
title: DeviceTvmSoftwareVulnerabilities tabel i det avancerede jagtskema
description: Få mere at vide om de softwaresårbarheder, der findes på enheder, og listen over tilgængelige sikkerhedsopdateringer, der adresserer hver sikkerhedsrisiko i tabellen DeviceTvmSoftwareVulner i det avancerede søgeskema.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & håndtering af sikkerhedsrisici, TVM, enhedshåndtering, software, lager, sårbarheder, CVE-id, OS DeviceTvmSoftwareInventoryVulnerabilities
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a6588134ba2cdf166a465998cd0b1a4fd7134dbb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592732"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

>[!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan være væsentligt ændret, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Tabellen `DeviceTvmSoftwareVulnerabilities` i det avancerede jagtskema indeholder listen [over sikkerhedsrisici & Threat &](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) i installerede softwareprodukter. Denne tabel indeholder også oplysninger om operativsystem, CVE-id'er og alvorlighedsoplysninger om sikkerhedsrisikoen. Du kan f.eks. bruge denne tabel til at lede efter begivenheder, der involverer enheder med alvorlige sårbarheder i deres software. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

>[!NOTE]
> Tabellerne `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` og tabellerne har erstattet `DeviceTvmSoftwareInventoryVulnerabilities` tabellen. Sammen indeholder de to første tabeller flere kolonner, du kan bruge til at informere dine håndtering af sikkerhedsrisici aktiviteter eller lede efter følsomme enheder.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på computeren. Angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `OSVersion` | `string` | Version af operativsystemet, der kører på computeren |
| `OSArchitecture` | `string` | Arkitektur for det operativsystem, der kører på computeren |
| `SoftwareVendor` | `string` | Navnet på softwareudgiveren |
| `SoftwareName` | `string` | Navnet på softwareproduktet |
| `SoftwareVersion` | `string` | Versionsnummer på softwareproduktet |
| `CveId` | `string` | Entydigt id tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures) |
| `VulnerabilitySeverityLevel` | `string` | Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet |
| `RecommendedSecurityUpdate` | `string` | Navn eller beskrivelse af den sikkerhedsopdatering, softwareudgiveren har leveret for at afhjælpe sikkerhedsrisikoen |
| `RecommendedSecurityUpdateId` | `string` | Identifikator for de relevante sikkerhedsopdateringer eller identifikator til den tilsvarende vejledning eller videnbaseartikler (KB) |



## <a name="related-topics"></a>Relaterede emner

- [Proaktivt lede efter trusler](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af & af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)