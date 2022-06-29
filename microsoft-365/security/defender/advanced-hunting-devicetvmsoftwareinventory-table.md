---
title: DeviceTvmSoftwareInventory-tabel i det avancerede jagtskema
description: Få mere at vide om softwareoversigten på dine enheder i tabellen DeviceTvmSoftwareInventory i det avancerede jagtskema.
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & sårbarhedsstyring, TVM, enhedshåndtering, software, lager, sårbarheder, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: cecbf2078bff0143a5c14b8b0cffb636d4fa3454
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490791"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

>[!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.


Tabellen `DeviceTvmSoftwareInventory` i det avancerede jagtskema indeholder [oversigten over Administration af trussel & sårbarheder](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) over software, der i øjeblikket er installeret på enheder i dit netværk, herunder oplysninger om ophør af support. Du kan f.eks. jage efter hændelser, der involverer enheder, der er installeret med en aktuelt sårbar softwareversion. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

>[!NOTE]
> Tabellerne `DeviceTvmSoftwareInventory` og `DeviceTvmSoftwareVulnerabilities` har erstattet tabellen `DeviceTvmSoftwareInventoryVulnerabilities` . Tilsammen indeholder de første to tabeller flere kolonner, som du kan bruge til at informere dine vulnerablity-administrationsaktiviteter eller jage efter sårbare enheder.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn (FQDN) på computeren |
| `OSPlatform` | `string` | Platform for det operativsystem, der kører på computeren. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `OSVersion` | `string` | Version af operativsystemet, der kører på computeren |
| `OSArchitecture` | `string` | Arkitekturen i operativsystemet, der kører på computeren |
| `SoftwareVendor` | `string` | Navn på softwareleverandøren |
| `SoftwareName` | `string` | Navnet på softwareproduktet |
| `SoftwareVersion` | `string` | Softwareproduktets versionsnummer |
| `EndOfSupportStatus` | `string` | Angiver softwareproduktets livscyklusfase i forhold til den angivne slutdato for support (EOS) eller EOL (end-of-life) |
| `EndOfSupportDate` | `string` | Slutdato for support (EOS) eller ophør af levetid (EOL) for softwareproduktet |
| `ProductCodeCpe` | `string` | CPE af softwareproduktet eller 'ikke tilgængelig', hvis der ikke er nogen CPE |
| `CveTags` | `string` | En matrix af de mærker, der er relevante for CVE. De mærker, der understøttes i øjeblikket, er "ZeroDay" og "NoSecurityUpdate".

## <a name="related-topics"></a>Relaterede emner

- [Proaktiv jagt på trusler](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af trussel & sårbarheder](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)