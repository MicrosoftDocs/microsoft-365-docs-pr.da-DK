---
title: DeviceTvmSoftwareVulnerabilitiesKB-tabel i det avancerede jagtskema
description: Få mere at vide om de softwaresårbarheder, der registreres af Threat & Vulnerability Management i tabellen DeviceTvmSoftwareVulnerabilitiesKB i det avancerede skema.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skema, reference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & håndtering af sikkerhedsrisici, TVM, enhedshåndtering, software, lager, sårbarheder, CVE-id, CVSS, DeviceTvmSoftwareVulnerabilitiesKB
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
ms.openlocfilehash: 545e2a3ba12924d364facda14a7a564ead212f30
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591158"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt



Tabellen `DeviceTvmSoftwareVulnerabilitiesKB` i det avancerede skema indeholder listen over sårbarheder [Threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) vurderer enheder for. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `CveId` | `string` | Entydigt id tildelt sikkerhedssikkerhedsrisikoen i CVE-systemet (Common Vulnerabilities and Exposures) |
| `CvssScore` | `string` | Alvorlighedsscore tildelt sikkerhedssikkerhedsrisikoen under det almindelige scoresystem for sikkerhedsrisiko (CVSS) |
| `IsExploitAvailable` | `boolean` | Angiver, om udnyttelseskoden for sikkerhedsrisikoen er offentligt tilgængelig |
| `VulnerabilitySeverityLevel` | `string` | Alvorsniveau tildelt sikkerhedsrisikoen baseret på CVSS-scoren og dynamiske faktorer, der påvirkes af trusselsbilledet |
| `LastModifiedTime` | `datetime` | Dato og klokkeslæt for, hvor elementet eller relaterede metadata sidst blev ændret |
| `PublishedDate` | `datetime` | Dato for sikkerhedsrisikoen blev offentliggjort |
| `VulnerabilityDescription` | `string` | Beskrivelse af sikkerhedsrisiko og tilknyttede risici |
| `AffectedSoftware` | `string` | Liste over alle softwareprodukter, der er berørt af sikkerhedsrisikoen |

## <a name="related-topics"></a>Relaterede emner

- [Proaktivt lede efter trusler](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af & af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)