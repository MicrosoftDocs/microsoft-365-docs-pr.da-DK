---
title: Sammenlign Microsoft Defender for Endpoint planer
description: Sammenlign Defender for Endpoint Plan 1 med Plan 2. Få mere at vide om forskellene mellem planerne, og vælg den plan, der passer til din organisations behov.
keywords: Defender for Endpoint, advanced threat protection, endpoint protection
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 06/17/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 34a5bd740b50eba561e2e138366ac05e732b016f
ms.sourcegitcommit: ad30b6bfccb402a338a198cb13e250b6ea21d545
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66612769"
---
# <a name="compare-microsoft-defender-for-endpoint-plans"></a>Sammenlign Microsoft Defender for Endpoint planer

Microsoft Defender for Endpoint er en sikkerhedsplatform til virksomhedsslutpunkter, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. Defender for Endpoint giver avanceret trusselsbeskyttelse, der omfatter antivirus, antimalware, afhjælpning af ransomware og meget mere samt central administration og rapportering. Du kan vælge mellem følgende indstillinger for Microsoft Defender for Endpoint:

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Du kan bruge denne artikel til at tydeliggøre, hvilken beskyttelse der leveres af de forskellige funktioner, der er tilgængelige i Defender for Endpoint Plan 1, Defender for Endpoint Plan 2, det nye tilføjelsesprogram til administration af sårbarheder i defender og Microsoft 365 Defender.

## <a name="compare-defender-for-endpoint-plans"></a>Sammenlign Defender for Endpoint-planer

I følgende tabel opsummeres det, der er inkluderet i hver Defender for Endpoint-plan.

| Plan | Hvad er inkluderet |
|:---|:---|
| [Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) | <ul><li>[Næste generations beskyttelse](defender-endpoint-plan-1.md#next-generation-protection) (omfatter antimalware og antivirus)</li><li>[Reduktion af angrebsoverfladen](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [Handlinger for manuelt svar](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Centraliseret administration](defender-endpoint-plan-1.md#centralized-management)</li><li>[Sikkerhedsrapporter](defender-endpoint-plan-1.md#reporting)</li><li>[Api'er](defender-endpoint-plan-1.md#apis)</li><li>[Understøttelse af Windows 10-, iOS-, Android OS- og macOS-enheder](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender for Endpoint Plan 2](microsoft-defender-endpoint.md) | Alle funktionerne i Defender for Endpoint Plan 1 plus:<ul><li>[Enhedssøgning](device-discovery.md)</li><li>[Enhedslager](machines-view-overview.md)</li><li>[Grundlæggende funktioner til administration af sårbarheder i Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Threat Analytics](threat-analytics.md)</li><li>[Automatiseret undersøgelse og svar](automated-investigations.md)</li><li>[Avanceret jagt](advanced-hunting-overview.md)</li><li>[Slutpunktsregistrering og -svar](overview-endpoint-detection-response.md)</li><li>[Microsoft Threat Experts](microsoft-threat-experts.md)</li><li>Understøttelse af [Windows-platforme](configure-endpoints.md) (klient og server) og [ikke-Windows-platforme](configure-endpoints-non-windows.md) (macOS, iOS, Android og Linux)</li></ul> |
| [Tilføjelsesprogram til administration af sårbarheder i Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Yderligere funktioner til administration af sårbarheder i Defender for Endpoint Plan 2:<ul><li>[Vurdering af sikkerhedsgrundlinjer](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Bloker sårbare programmer](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Browserudvidelser](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Vurdering af digitalt certifikat](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Analyse af netværksshare](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>Understøttelse af [Windows-platforme](configure-endpoints.md) (klient og server) og [ikke-Windows-platforme](configure-endpoints-non-windows.md) (macOS, iOS, Android og Linux)</li></ul> |
| [Microsoft 365 Defender](../defender/microsoft-365-defender.md) | Tjenesterne omfatter: <ul><li>[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)</li><li>[Microsoft Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management.md)</li><li>[Microsoft Defender for Office 365](../office-365-security/overview.md)</li><li>[Microsoft Defender for Identity](/defender-for-identity/)</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/)</li></ul>|

> [!IMPORTANT]
> De separate versioner af Defender for Endpoint Plan 1 og Plan 2 indeholder ikke serverlicenser. Hvis du vil onboarde servere, f.eks. slutpunkter, der kører Windows Server eller Linux, skal du bruge Defender for Servers Plan 1 eller Plan 2 som en del af [Defender for Cloud-tilbuddet](/azure/defender-for-cloud/defender-for-cloud-introduction) . For at få mere at vide. se [Oversigt over Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction).

## <a name="mixed-licensing-scenarios"></a>Blandede licensscenarier

Lad os antage, at din organisation bruger en blanding af Sikkerhedsabonnementer på Microsoft-slutpunkter, f.eks. Defender for Endpoint Plan 1 og Defender for Endpoint Plan 2. **I øjeblikket angiver det højeste funktionelle Sikkerhedsabonnement på Microsoft-slutpunkt oplevelsen for din lejer**. I dette eksempel vil din lejeroplevelse være Defender for Endpoint Plan 2 for alle brugere.

Du **kan dog kontakte support og anmode om en tilsidesættelse af din lejeroplevelse**. Du kan f.eks. anmode om en tilsidesættelse for at bevare Defender for Endpoint Plan 1-oplevelsen for alle brugere. 

- Du kan finde oplysninger om licenser og produktvilkår under [Licenser og produktvilkår for Microsoft 365-abonnementer](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).
- Du kan få oplysninger om, hvordan du kontakter support, under [Kontakt Microsoft Defender for Endpoint support](contact-support.md).

> [!TIP]
> Hvis din organisation er en lille eller mellemstor virksomhed, kan du se følgende artikler:
> - [Hvad er Microsoft Defender for Business?](../defender-business/mdb-overview.md)
> - [Sammenlign sikkerhedsfunktioner i Microsoft 365-planer for små og mellemstore virksomheder](../defender-business/compare-mdb-m365-plans.md).

## <a name="start-a-trial"></a>Start en prøveversion

- Hvis du vil prøve Defender for Endpoint, skal du gå til [siden med tilmelding til prøveversionen af Defender for Endpoint](https://go.microsoft.com/fwlink/p/?LinkID=2168109).
- Hvis du vil prøve tilføjelsesprogrammet Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender for Defender for Endpoint Plan 2, skal du besøge [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>Se også

- [Kom i gang med Microsoft Security (prøveversionstilbud)](https://www.microsoft.com/security/business/get-started/start-free-trial)

- [Microsoft Defender til virksomheder](../defender-business/mdb-overview.md) (beskyttelse af slutpunkter for små og mellemstore virksomheder)