---
title: DeviceTvmSoftwareEvidenceBeta-tabel i det avancerede jagtskema
description: Få mere at vide om, hvordan du bruger tabellen DeviceTvmSoftwareEvidenceBeta i det avancerede jagtskema.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & håndtering af sikkerhedsrisici, bevis, softwarelegitimation, TVM, enhedshåndtering, software, lager, sårbarheder, CVE-id, OS DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 7fd064b906e4afe5e337df85d9dc6f174edc99cf
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/30/2021
ms.locfileid: "63601068"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

> [!IMPORTANT]
> Tabellen `DeviceTvmSoftwareEvidenceBeta` er i øjeblikket i betaversionen. Når den efterlader betaversionen, ændres det endelige tabelnavn, og kolonnenavnene kan også ændres. Ændringerne vil derefter sandsynligvis bryde forespørgsler, der stadig bruger tidligere navne. Det anbefales, at brugerne gennemser og justerer deres forespørgsler, når denne tabel er færdig. 


Tabellen `DeviceTvmSoftwareEvidenceBeta` i det avancerede skema indeholder data fra [Threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) , som er relateret til [afsnittet om software beviser](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence). Denne tabel giver dig mulighed at få vist bevis for, hvor en bestemt software blev registreret på en enhed. Du kan f.eks. bruge denne tabel til at identificere filstierne til bestemt software. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |
| `SoftwareVendor` | `string` | Navnet på softwareudgiveren |
| `SoftwareName` | `string` | Navnet på softwareproduktet |
| `SoftwareVersion` | `string` | Versionsnummer på softwareproduktet |
| `RegistryPaths` | `dynamic` | Registreringsdatabasestier, hvor der blev registreret beviser for eksistensen af softwaren på en enhed |
| `DiskPaths` | `dynamic` | Diskstier, hvor der på filniveau er bevis for, at der findes software på en enhed |
| `LastSeenTime` | `string` | Dato og klokkeslæt for, hvornår enheden sidst ses af denne tjeneste |




## <a name="related-topics"></a>Relaterede emner

- [Oversigt over administration af & af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Proaktivt lede efter trusler](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
