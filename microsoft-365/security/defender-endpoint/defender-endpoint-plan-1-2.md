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
ms.date: 07/14/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: d41c228ceeae0dcd373f98c6dcd89bf88b0feacd
ms.sourcegitcommit: 5463d4518c269d9c125bb66836a780df292b4854
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66795394"
---
# <a name="compare-microsoft-endpoint-security-plans"></a>Sammenlign Sikkerhedsplaner for Microsoft-slutpunkter

Microsofts sikkerhedsplaner for slutpunkter, f.eks. Microsoft Defender for Endpoint og Microsoft 365 Defender, er udviklet til at hjælpe virksomhedsorganisationer med at forhindre, registrere, undersøge og reagere på avancerede trusler. Microsoft Defender til virksomheder og Microsoft 365 Business Premium leverer lignende funktioner, der er optimeret til små og mellemstore virksomheder. Disse planer giver avanceret trusselsbeskyttelse med antivirus- og antimalwarebeskyttelse, ransomware-afhjælpning og meget mere sammen med centraliseret administration og rapportering. 

Denne artikel hjælper med at tydeliggøre, hvad der er inkluderet i følgende planer: 

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Vulnerability Management](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)
- [Microsoft 365 Business Premium](../../business-premium/index.md)

> [!IMPORTANT]
> Denne artikel indeholder en oversigt over funktioner til trusselsbeskyttelse i Microsofts sikkerhedsplaner for slutpunkter. Det er dog ikke meningen, at det skal være en tjenestebeskrivelse eller et licenskontraktdokument. Du kan finde flere detaljerede oplysninger i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="compare-microsoft-endpoint-security-plans"></a>Sammenlign Sikkerhedsplaner for Microsoft-slutpunkter

I følgende tabel opsummeres det, hvad der er inkluderet i Microsoft-slutpunktssikkerhedsplaner.

| Plan | Hvad er inkluderet |
|:---|:---|
| [Microsoft 365 Defender](../defender/microsoft-365-defender.md) | Tjenesterne omfatter: <ul><li>[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)</li><li>[Microsoft Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management.md)</li><li>[Microsoft Defender for Office 365](../office-365-security/overview.md)</li><li>[Microsoft Defender for Identity](/defender-for-identity/)</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/)</li></ul>|
| [Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) <sup>[[1](#fn1)]</sup> | <ul><li>[Næste generations beskyttelse](defender-endpoint-plan-1.md#next-generation-protection) (omfatter antimalware og antivirus)</li><li>[Reduktion af angrebsoverfladen](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [Handlinger for manuelt svar](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Centraliseret administration](defender-endpoint-plan-1.md#centralized-management)</li><li>[Sikkerhedsrapporter](defender-endpoint-plan-1.md#reporting)</li><li>[Api'er](defender-endpoint-plan-1.md#apis)</li><li>[Understøttelse af Windows 10-, iOS-, Android OS- og macOS-enheder](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender for Endpoint Plan 2](microsoft-defender-endpoint.md) <sup>[[2](#fn2)]</sup> | Alle funktionerne i Defender for Endpoint Plan 1 plus:<ul><li>[Enhedssøgning](device-discovery.md)</li><li>[Enhedslager](machines-view-overview.md)</li><li>[Grundlæggende funktioner til administration af sårbarheder i Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Threat Analytics](threat-analytics.md)</li><li>[Automatiseret undersøgelse og svar](automated-investigations.md)</li><li>[Avanceret jagt](advanced-hunting-overview.md)</li><li>[Slutpunktsregistrering og -svar](overview-endpoint-detection-response.md)</li><li>[Microsoft Threat Experts](microsoft-threat-experts.md)</li><li>Understøttelse af [Windows-platforme](configure-endpoints.md) (klient og server) og [ikke-Windows-platforme](configure-endpoints-non-windows.md) (macOS, iOS, Android og Linux)</li></ul> |
| [Tilføjelsesprogram til administration af sårbarheder i Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Yderligere funktioner til administration af sårbarheder i Defender for Endpoint Plan 2:<ul><li>[Vurdering af sikkerhedsgrundlinjer](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Bloker sårbare programmer](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Browserudvidelser](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Vurdering af digitalt certifikat](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Analyse af netværksshare](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>Understøttelse af [Windows-platforme](configure-endpoints.md) (klient og server) og [ikke-Windows-platforme](configure-endpoints-non-windows.md) (macOS, iOS, Android og Linux)</li></ul> |
| [Defender for Business](../defender-business/mdb-overview.md) <sup>[[3](#fn3)]</sup> <br/>Og<br/>[Microsoft 365 Business Premium](../../business-premium/index.md) | [Tjenester, der er optimeret til små og mellemstore virksomheder](../defender-business/compare-mdb-m365-plans.md) , omfatter: <ul><li>Mailbeskyttelse</li><li>Antispambeskyttelse</li><li>Beskyttelse modmalware</li><li>Næste generations beskyttelse</li><li>Reduktion af angrebsoverfladen</li><li>Slutpunktsregistrering og -svar</li><li>Automatiseret undersøgelse og svar </li><li>Håndtering af trusler og sikkerhedsrisici</li><li>Centraliseret rapportering</li><li>API'er (til integration med brugerdefinerede apps eller rapporteringsløsninger)</li><li>[Integration med Microsoft 365 Lighthouse](../defender-business/mdb-lighthouse-integration.md)</li></ul> |

(<a id="fn1">1</a>) Microsoft Defender for Endpoint Plan 1 er tilgængeligt som et separat abonnement for erhvervs- og uddannelseskunder. Den er også inkluderet som en del af Microsoft 365 E3/A3.

(<a id="fn2">2</a>) Microsoft Defender for Endpoint Plan 2, der tidligere blev kaldt Microsoft Defender for Endpoint, er tilgængelig som et separat abonnement. Det er også inkluderet som en del af følgende planer:

- Windows 11 Enterprise E5/A5
- Windows 10 Enterprise E5/A5
- Microsoft 365 E5/A5/G5 (herunder Windows 10 eller Windows 11 Enterprise E5)
- Microsoft 365 E5/A5/G5/F5 Security
- Microsoft 365 F5 Security & Compliance

(<a id="fn3">3</a>) Microsoft Defender til virksomheder er tilgængeligt som et selvstændigt abonnement for små og mellemstore virksomheder. Den er også inkluderet som en del af Microsoft 365 Business Premium. Disse planer indeholder avancerede sikkerhedsfunktioner med en forenklet konfigurationsoplevelse.

## <a name="options-for-onboarding-servers"></a>Indstillinger for onboarding af servere

De separate versioner af Defender for Business, Defender for Endpoint Plan 1 og 2 og Microsoft 365 Business Premium omfatter ikke serverlicenser. Hvis du vil onboarde servere, skal du vælge mellem følgende indstillinger:

- **Defender for Servers Plan 1 eller Plan 2** som en del af [Defender for Cloud-tilbuddet](/azure/defender-for-cloud/defender-for-cloud-introduction) . For at få mere at vide. se [Oversigt over Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction).

- **Microsoft Defender til virksomheder servere (prøveversion)** til små og mellemstore virksomheder. Se [Sådan får du Microsoft Defender til virksomheder servere (prøveversion)](../defender-business/get-defender-business-servers.md).

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
