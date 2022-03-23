---
title: Administrer Microsoft Defender for Slutpunkt ved hjælp af Konfigurationsstyring
description: Få mere at vide om, hvordan du administrerer Microsoft Defender til slutpunkt med Konfigurationsstyring
keywords: efter overførslen, administrere, handlinger, vedligeholdelse, Konfigurationsstyring, Microsoft Defender til slutpunkt, edr
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
- m365solution-scenario
- m365initiative-defender-endpoint
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 40bac47a4c22e3a8706ed4b38b479fff5d500410
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63593654"
---
# <a name="manage-microsoft-defender-for-endpoint-with-configuration-manager"></a>Administrer Microsoft Defender for Slutpunkt med Konfigurationsstyring

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Vi anbefaler at [bruge Microsoft Endpoint Manager](/mem), som omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (Intune) og [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction) (Konfigurationsstyring) til at administrere organisationens funktioner til trusselsbeskyttelse på enheder ( også kaldet slutpunkter).

- [Få mere at vide Endpoint Manager](/mem/endpoint-manager-overview)
- [Administrer Microsoft Defender for Slutpunkt på Windows 10 og Windows 11 enheder med Konfigurationsstyring og Intune](manage-mde-post-migration-intune.md)

## <a name="configure-microsoft-defender-for-endpoint-with-configuration-manager"></a>Konfigurer Microsoft Defender til slutpunkt med Konfigurationsstyring

<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Installér Konfigurationsstyring,** hvis du ikke allerede har den <br/><br/> *Hvis du ikke allerede har konsollen Configuration Manger, kan du bruge disse ressourcer til at hente bits og installere den.*|[Hent installationsmedierne](/mem/configmgr/core/servers/deploy/install/get-install-media) <br/><br/> [Installér Konfigurationsstyring konsol](/mem/configmgr/core/servers/deploy/install/install-consoles)|
|**Brug Konfigurationsstyring til at onboarde enheder** til Microsoft Defender til Slutpunkt <br/><br/> *Hvis du har enheder (eller slutpunkter), der ikke allerede er onboardet til Microsoft Defender til slutpunkt, kan du gøre det med Konfigurationsstyring.*|[Onboard to Microsoft Defender for Endpoint with Konfigurationsstyring](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection#about-onboarding-to-atp-with-configuration-manager)|
|**Administrer antimalwarepolitikker og Windows firewallsikkerhed** for klientcomputere (slutpunkter) <br/><br/> *Konfigurer slutpunktsbeskyttelsesfunktioner, herunder Microsoft Defender til slutpunkt, udnyttelsesbeskyttelse, programkontrol, antimalware, firewallindstillinger og meget mere.*|[Konfigurationsstyring: Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection)|
|**Vælg metoder til opdatering af antimalwareopdateringer** på din organisations enheder <br/><br/> *Med Endpoint Protection i Konfigurationsstyring kan du vælge mellem flere forskellige metoder til at holde antimalwaredefinitioner opdateret på organisationens enheder.*|[Konfigurere definitionsopdateringer til Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-definition-updates) <br/><br/> [Brug Konfigurationsstyring til at levere definitionsopdateringer](/mem/configmgr/protect/deploy-use/endpoint-definitions-configmgr)|
|**Aktivér netværksbeskyttelse** for at forhindre medarbejdere i at bruge apps med skadeligt indhold på internettet <br/><br/> *Vi anbefaler, at [du først bruger overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-network-protection) for netværksbeskyttelse i et testmiljø for at se, hvilke apps der blev blokeret før udrulning.*|[Slå netværksbeskyttelse til med Konfigurationsstyring](/microsoft-365/security/defender-endpoint/enable-network-protection#microsoft-endpoint-configuration-manager)|
|**Konfigurer styret mappeadgang for** at beskytte mod ransomware <br/><br/> *Kontrolleret mappeadgang kaldes også antiransomwarebeskyttelse.*|[Slutpunktsbeskyttelse: Styret mappeadgang](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Aktivér styret mappeadgang i Konfigurationsstyring for Microsoft Endpoint](/microsoft-365/security/defender-endpoint/enable-controlled-folders#microsoft-endpoint-configuration-manager)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurere din Microsoft 365 Defender portal

Hvis du ikke allerede har gjort det, skal du konfigurere din Microsoft 365 Defender-portal for at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om organisationens overordnede sikkerhedslag. Se Mens angrebene blev registreret og stoppet, blev beskeder, f.eks. en "startadgangsbesked", udløst og vist [i Microsoft 365 Defender portal](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugere kan se i Microsoft 365 Defender portal.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Slutpunktsbeskyttelse: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Gå til Microsoft 365 Defender portalsikkerhedsdashboard](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Administrer Microsoft Defender til slutpunkt med Intune](manage-mde-post-migration-intune.md)
