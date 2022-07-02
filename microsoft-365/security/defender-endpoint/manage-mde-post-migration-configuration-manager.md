---
title: Administrer Microsoft Defender for Endpoint ved hjælp af Configuration Manager
description: Få mere at vide om, hvordan du administrerer Microsoft Defender for Endpoint med Configuration Manager
keywords: efter migrering, administration, drift, vedligeholdelse, udnyttelse, Configuration Manager, Microsoft Defender for Endpoint, kant
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: b253fe7dad271684f5c0e927ec162ea4e993df29
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607383"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Administrer Microsoft Defender for Endpoint med Configuration Manager

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem), som omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) og [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) (Configuration Manager ) til at administrere organisationens trusselsbeskyttelsesfunktioner for enheder (også kaldet slutpunkter).

- [Få mere at vide om Endpoint Manager](/mem/endpoint-manager-overview)
- [Samtidig administration af Microsoft Defender for Endpoint på Windows 10 og Windows 11 enheder med Configuration Manager og Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Konfigurer Microsoft Defender for Endpoint med Configuration Manager

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Installér Configuration Manager-konsollen**, hvis du ikke allerede har den <br/><br/> *Hvis du ikke allerede har konfigurationsstyringskonsollen, kan du bruge disse ressourcer til at hente bittene og installere den.*|[Hent installationsmediet](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Installér Configuration Manager-konsollen](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Brug Configuration Manager til at onboarde enheder** for at Microsoft Defender for Endpoint <br/><br/> *Hvis du har enheder (eller slutpunkter), der ikke allerede er onboardet til Microsoft Defender for Endpoint, kan du gøre det med Configuration Manager.*|[Onboard til Microsoft Defender for Endpoint med Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Administrer antimalwarepolitikker og Windows Firewall-sikkerhed** for klientcomputere (slutpunkter) <br/><br/> *Konfigurer beskyttelsesfunktioner for slutpunkter, herunder Microsoft Defender for Endpoint, udnyttelse af beskyttelse, programkontrol, antimalware, firewallindstillinger m.m.*|[Configuration Manager: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Vælg metoder til opdatering af antimalwareopdateringer** på organisationens enheder <br/><br/> *Med Endpoint Protection i Configuration Manager kan du vælge mellem flere metoder for at holde antimalwaredefinitioner opdateret på din organisations enheder.*|[Konfigurer definitionsopdateringer til Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Brug Configuration Manager til at levere definitionsopdateringer](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Aktivér Netværksbeskyttelse** for at forhindre medarbejdere i at bruge apps, der har skadeligt indhold på internettet <br/><br/> *Vi anbefaler, at du først bruger [overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-network-protection) til netværksbeskyttelse i et testmiljø for at se, hvilke apps der blokeres, før de udrulles.*|[Slå netværksbeskyttelse til med Configuration Manager](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Konfigurer kontrolleret mappeadgang** for at beskytte mod ransomware <br/><br/> *Kontrolleret mappeadgang kaldes også antiransomware-beskyttelse.*|[Endpoint Protection: Adgang til styrede mapper](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Aktivér kontrolleret mappeadgang i Microsoft Endpoint Configuration Manage](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurer Microsoft 365 Defender-portalen

Hvis du ikke allerede har gjort det, kan du konfigurere din Microsoft 365 Defender-portal til at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om din organisations overordnede sikkerhedsholdning. Se Mens angrebet blev registreret og stoppet, blev beskeder, f.eks. en "indledende adgangsbesked", udløst og vist på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugerne kan se på portalen Microsoft 365 Defender.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Beskyttelse af slutpunkter: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Besøg dashboardet til Microsoft 365 Defender-portalens sikkerhedshandlinger](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Administrer Microsoft Defender for Endpoint med Intune](manage-mde-post-migration-intune.md)
