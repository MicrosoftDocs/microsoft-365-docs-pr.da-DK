---
title: Gå på jagt efter blotlagte enheder
description: Lær, Håndtering af trusler og sikkerhedsrisici kan bruges til at hjælpe sikkerhedsadministratorer, it-administratorer og SecOps med at samarbejde.
keywords: Microsoft Defender til Endpoint-tvm-scenarier, Microsoft Defender til slutpunkt, tvm, tvm-scenarier, reducer eksponering af trusler & sikkerhedsrisikoen, reducer trussel og sikkerhedsrisiko, gør sikkerhedskonfigurationen bedre, gør Microsoft Secure Score til enheder større, forøg trussel & ssikkerhedsrisikoen Microsoft Secure Score til enheder, Microsoft Secure Score til enheder, eksponeringsscore, sikkerhedskontroller
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 40544ab3879acd026d7f327e63d02bdb79d00d83
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593417"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>Lede efter blotlagte enheder – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>Brug avanceret jagt til at finde enheder med sårbarheder

Avanceret jagt er et forespørgselsbaseret værktøj til trusselssøgning, som giver dig mulighed for at udforske op til 30 dages rå data. Du kan proaktivt undersøge hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Fleksibel adgang til data gør det muligt at gå på jagt efter både kendte og potentielle trusler. [Få mere at vide om avanceret jagt](advanced-hunting-overview.md)

### <a name="schema-tables"></a>Skematabeller

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) – lager af software, der er installeret på enheder, herunder versionsoplysninger og status for ophør af support.

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) - Softwarerisici fundet på enheder og listen over tilgængelige sikkerhedsopdateringer, der adresserer hver sikkerhedsrisiko.

- [DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) – vidensbase om offentligt offentliggjorte sårbarheder, herunder om udnyttelse af kode er offentligt tilgængelig.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) - Threat and håndtering af sikkerhedsrisici assessment events, der angiver status for forskellige sikkerhedskonfigurationer på enheder.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) – Vidensbase for forskellige sikkerhedskonfigurationer, der bruges af Threat & Vulnerability Management til at vurdere enheder; omfatter tilknytning til forskellige standarder og benchmarks

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>Kontrollér, hvilke enheder der er involveret i beskeder om høj alvorsgrad

1. Gå til **På jagt** \> **efter avanceret** jagt fra den venstre navigationsrude på Microsoft 365 Defender-portalen.

2. Rul ned til tvm'ets avancerede søgeskemaer for at blive fortrolig med kolonnenavnene.

3. Angiv følgende forespørgsler:

    ```kusto
    // Search for devices with High active alerts or Critical CVE public exploit
    let DeviceWithHighAlerts = AlertInfo
    | where Severity == "High"
    | project Timestamp, AlertId, Title, ServiceSource, Severity
    | join kind=inner (AlertEvidence | where EntityType == "Machine" | project AlertId, DeviceId, DeviceName) on AlertId
    | summarize HighSevAlerts = dcount(AlertId) by DeviceId;
    let DeviceWithCriticalCve = DeviceTvmSoftwareVulnerabilities
    | join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
    | where IsExploitAvailable == 1 and CvssScore >= 7
    | summarize NumOfVulnerabilities=dcount(CveId),
    DeviceName=any(DeviceName) by DeviceId;
    DeviceWithCriticalCve
    | join kind=inner DeviceWithHighAlerts on DeviceId
    | project DeviceId, DeviceName, NumOfVulnerabilities, HighSevAlerts
    ```

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [API'er](next-gen-threat-and-vuln-mgt.md#apis)
- [Konfigurere dataadgang for Håndtering af trusler og sikkerhedsrisici roller](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [Avanceret jagtoversigt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Alle avancerede jagttabeller](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
