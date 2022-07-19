---
title: DeviceTvmInfoGathering-tabel i det avancerede jagtskema
description: Få mere at vide om vurderingshændelserne, herunder status for forskellige konfigurationer og tilstande for angrebsoverfladen for enheder i tabellen DeviceTvmInfoGathering i det avancerede jagtskema.
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
ms.openlocfilehash: 738168153738f8bf4e12220829114efc0cc8beb2
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858874"
---
# <a name="devicetvminfogathering"></a>DeviceTvmInfoGathering

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

>[!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Tabellen `DeviceTvmInfoGathering` i det avancerede jagtskema indeholder [Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) vurderingshændelser, herunder status for forskellige konfigurationer og enheders tilstande for angrebsoverfladen. Du kan bruge denne tabel til at søge efter vurderingshændelser, der er relateret til afhjælpning i nuldage, vurdering af stillingsvurdering for nye trusler, der understøtter statusrapporter for trusselsanalysemitigering, aktiverede TLS-protokolversioner på servere og meget mere. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `LastSeenTime` | `datetime` | Dato og klokkeslæt for, hvornår tjenesten sidst så enheden |
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |
| `DeviceName` | `string` | Fuldt domænenavn (FQDN) for enheden |
| `OSPlatform` | `string` | Platform for det operativsystem, der kører på enheden. Dette angiver specifikke operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 10 og Windows 7. |
| `AdditionalFields` | `string` | Yderligere oplysninger om hændelsen  |

Hvis du f.eks. vil have vist de enheder, der er påvirket af [Log4Shell-sårbarheden](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) , hvor afhjælpningen af afhjælpningen endnu ikke er blevet anvendt eller er blevet anvendt og afventer genstart, kan du bruge følgende forespørgsel.

```kusto
DeviceTvmInfoGathering
| where AdditionalFields.Log4JEnvironmentVariableMitigation in ("RebootRequired", "false")
| join kind=inner (
    DeviceTvmSoftwareVulnerabilities
    | where CveId == "CVE-2021-44228"
) on DeviceId
| summarize any(DeviceName), any(AdditionalFields.Log4JEnvironmentVariableMitigation) by DeviceId
```

## <a name="related-topics"></a>Relaterede emner
- [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af sårbarheder i Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Få mere at vide om, hvordan du administrerer Log4Shell-sårbarheden i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/tvm-manage-log4shell-guidance)