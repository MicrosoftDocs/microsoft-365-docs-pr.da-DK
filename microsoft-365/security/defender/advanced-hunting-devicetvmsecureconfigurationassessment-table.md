---
title: DeviceTvmSecureConfigurationAssessment-tabellen i det avancerede jagtskema
description: Få mere at vide om hændelser til sikkerhedsvurdering i tabellen DeviceTvmSecureConfigurationAssessment i det avancerede jagtskema. Disse hændelser indeholder enhedsoplysninger, oplysninger om sikkerhedskonfiguration, virkning og overholdelse af regler og standarder.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & håndtering af sikkerhedsrisici, TVM, enhedshåndtering, sikkerhedskonfiguration, DeviceTvmSecureConfigurationAssesment
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
ms.openlocfilehash: 43f44458cde7d466d1097034e7bcc9d0e3072745
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591184"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt


Hver række i tabellen `DeviceTvmSecureConfigurationAssessment` indeholder en vurderingshændelse for en bestemt sikkerhedskonfiguration fra [Threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Brug denne reference til at kontrollere de nyeste vurderingsresultater og afgøre, om enhederne er kompatible.

Du kan joinforme denne tabel med tabellen [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) `ConfigurationId` ved hjælp af, `ConfigurationDescription` `DeviceTvmSecureConfigurationAssessmentKB` så du f.eks. kan se tekstbeskrivelsen af konfigurationen fra kolonnen i tabellen i resultaterne for konfigurationsvurderingen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn for enheden |
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på enheden. Angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7.|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår posten blev oprettet |
| `ConfigurationId` | `string` | Entydigt id for en bestemt konfiguration |
| `ConfigurationCategory` | `string` | Kategori eller gruppering, som konfigurationen tilhører: Program, OPERATIVSYSTEM, Netværk, Konti, Sikkerhedskontrolelementer |
| `ConfigurationSubcategory` | `string` | Underkategori eller undergruppering, som konfigurationen tilhører. I mange tilfælde beskriver streng bestemte funktioner eller funktioner. |
| `ConfigurationImpact` | `string` | Klassificeret effekt af konfigurationen på det overordnede konfigurationsresultat (1-10) |
| `IsCompliant` | `boolean` | Angiver, om konfigurationen eller politikken er konfigureret korrekt |
| `IsApplicable` | `boolean` | Angiver, om konfigurationen eller politikken gælder for enheden |
| `Context` | `string` | Yderligere kontekstafhængige oplysninger om konfigurationen eller politikken |
| `IsExpectedUserImpact` | `boolean` | Angiver, om der vil være brugerpåvirkning, hvis konfigurationen eller politikken anvendes |

Du kan prøve denne eksempelforespørgsel for at returnere oplysninger på enheder med ikke-kompatible antiviruskonfigurationer sammen med de relevante konfigurationsmetadata fra `DeviceTvmSecureConfigurationAssessmentKB` tabellen:

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