---
title: DeviceTvmSecureConfigurationAssessmentKB-tabel i det avancerede jagtskema
description: Få mere at vide om de forskellige sikre konfigurationer, der vurderes af Threat & Vulnerability Management i deviceTvmSecureConfigurationAssessmentKB-tabellen i det avancerede jagtskema.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, & håndtering af sikkerhedsrisici , TVM, enhedshåndtering, sikkerhedskonfiguration, MITRE ATT&CK framework, knowledge base, KB, DeviceTvmSecureConfigurationAssessmentKB
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
ms.openlocfilehash: 81f03a665a0c825388335c925cb908f3b931a918
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63592851"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt


Tabellen `DeviceTvmSecureConfigurationAssessmentKB` i det avancerede skema indeholder oplysninger om de forskellige sikre konfigurationer, der kontrolleres af [Threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Den indeholder også risikooplysninger, relaterede branchemålepunkter og gældende MITRE ATT-&CK-teknikker og -taktikker.

Denne tabel returnerer ikke hændelser eller poster. Vi anbefaler, at du slutter denne tabel til [tabellen DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) `ConfigurationId` ved hjælp af visning af tekstoplysninger om sikkerhedskonfigurationer i de returnerede bedømmelser.

Når du for eksempel forespørger `DeviceTvmSecureConfigurationAssessment` `ConfigurationDescription` i tabellen, kan det være en ide at få vist for de sikkerhedskonfigurationer, der vises i bedømmelsesresultaterne. Du kan se disse oplysninger ved at tilmelde denne tabel til brug `DeviceTvmSecureConfigurationAssessment` og `ConfigurationId` projicer `ConfigurationDescription`.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `ConfigurationId` | `string` | Entydigt id for en bestemt konfiguration |
| `ConfigurationImpact` | `string` | Klassificeret effekt af konfigurationen på det overordnede konfigurationsresultat (1-10) |
| `ConfigurationName` | `string` | Visningsnavn for konfigurationen |
| `ConfigurationDescription` | `string` | Beskrivelse af konfigurationen |
| `RiskDescription` | `string` | Beskrivelse af den tilknyttede risiko |
| `ConfigurationCategory` | `string` | Kategori eller gruppering, som konfigurationen tilhører: Program, OPERATIVSYSTEM, Netværk, Konti, Sikkerhedskontrolelementer|
| `ConfigurationSubcategory` | `string` |Underkategori eller undergruppering, som konfigurationen tilhører. I mange tilfælde beskrives specifikke funktioner. |
| `ConfigurationBenchmarks` | `string` | Liste over branchemålepunkter, der anbefaler den samme eller lignende konfiguration |
| `Tags` | `string` | Etiketter, der repræsenterer forskellige attributter, der bruges til at identificere eller kategorisere en sikkerhedskonfiguration |
| `RemediationOptions` | `string` | Anbefalede handlinger til at reducere eller håndtere eventuelle tilknyttede risici |

Du kan prøve denne eksempelforespørgsel for at returnere relevante konfigurationsmetadata sammen med oplysninger på enheder med ikke-kompatible antiviruskonfigurationer fra `DeviceTvmSecureConfigurationAssessment` tabellen:

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

## <a name="related-topics"></a>Relaterede emner

- [Proaktivt lede efter trusler](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af & af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)