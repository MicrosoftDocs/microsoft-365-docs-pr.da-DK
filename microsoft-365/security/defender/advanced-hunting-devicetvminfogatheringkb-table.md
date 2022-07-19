---
title: DeviceTvmInfoGatheringKB-tabel i det avancerede jagtskema
description: Få mere at vide om metadataene for vurderingshændelser i tabellen DeviceTvmInfoGathering i det avancerede jagtskema.
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
ms.openlocfilehash: c654ca395762426072bf8e5e20fd3f62e78a480c
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66858917"
---
# <a name="devicetvminfogatheringkb"></a>DeviceTvmInfoGatheringKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Tabellen `DeviceTvmInfoGatheringKB` i det avancerede jagtskema indeholder metadata for [Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) vurderingshændelsesdata, der indsamles i tabellen`DeviceTvmInfoGathering`. Tabellen `DeviceTvmInfoGatheringKB` indeholder en liste over forskellige vurderinger af konfigurations- og angrebsoverfladen, der bruges af Defender Vulnerability Management-oplysninger, som indsamles for at vurdere enheder. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `IgId` | `string` | Entydigt id for den oplysning, der indsamles |
| `FieldName` | `string` | Navnet på det felt, hvor disse oplysninger vises i kolonnen AdditionalFields i tabellen DeviceTvmInfoGathering |
| `Description` | `string` | Beskrivelse af de indsamlede oplysninger |
| `Categories` | `string` | Liste over kategorier, som oplysningerne tilhører, i matrixformatet JSON  |
| `DataStructure` | `string` | Datastrukturen for de indsamlede oplysninger  |

Du kan bruge denne tabel til at udforske de typer oplysninger, der er tilgængelige i `DeviceTvmInfoGathering` , så du senere kan finjustere din jagtforespørgsel.

Hvis du f.eks. vil se listen over de oplysninger, der indsamles, kan du prøve følgende forespørgsel:

```kusto
// Check out what is being collected 
DeviceTvmInfoGatheringKB  
```

Fra resultaterne kan du f.eks. sige, at du er interesseret i de tilgængelige kategorier, bruge følgende forespørgsel:

```kusto
// Return all available categories 
DeviceTvmInfoGatheringKB 
| mv-expand Categories to typeof(string) 
| distinct Categories 
```

Lad os derefter sige, at du vil se de vurderingskategorier, der involverer TLS-protokollen:

```kusto
// Return all findings for a specified category 
DeviceTvmInfoGatheringKB 
| where Categories contains "tls" 
```

Ved hjælp af de resulterende felter kan du derefter bruge tabellen `DeviceTvmInfoGathering` til at få vist en liste over enheder, der bruger TLS-klientversion 1.0.

```kusto
// Return all devices on which the TLS version 1.0 is enabled 
DeviceTvmInfoGathering 
| where AdditionalFields.TlsClient10 == "Enabled" or AdditionalFields.TlsServer10 == "Enabled" 
```

## <a name="related-topics"></a>Relaterede emner

- [DeviceTvmInfoGathering](advanced-hunting-devicetvminfogathering-table.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af sårbarheder i Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
