---
title: Skift til Microsoft Defender for Endpoint - Forbered
description: Gør dig klar til at skifte til Microsoft Defender for Endpoint. Opdater dine enheder, og konfigurer dine netværksforbindelser.
keywords: migrering, Microsoft Defender for Endpoint, bedste praksis
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
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: c08ab1c96adc2b9d83cc6869573f2f0dbe75ac78
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782913"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Skift til Microsoft Defender for Endpoint - fase 1: Forbered

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Fase 1: Forbered.](images/phase-diagrams/prepare.png#lightbox)<br/>Fase 1: Forbered | [![Fase 2: Konfigurer](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Fase 2: Konfigurer](switch-to-mde-phase-2.md) | [![Fase 3: Onboard](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Fase 3: Onboard](switch-to-mde-phase-3.md) |
|--|--|--|
|*Du er her!*| | |

**Velkommen til forberedelsesfasen for [skift til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)**.

Denne overførselsfase omfatter følgende trin:

1. [Hent og udrul opdateringer på tværs af organisationens enheder](#get-and-deploy-updates-across-your-organizations-devices)
2. [Hent Defender for Endpoint](#get-microsoft-defender-for-endpoint).
3. [Tildel adgang til Microsoft 365 Defender-portalen](#grant-access-to-the-microsoft-365-defender-portal).
4. [Konfigurer indstillingerne for enhedsproxy og internetforbindelse](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Hent og udrul opdateringer på tværs af organisationens enheder

Som bedste praksis skal du holde organisationens enheder og slutpunkter opdateret. Sørg for, at din eksisterende løsning til beskyttelse af slutpunkter og antivirus er opdateret, og at de operativsystemer og apps, din organisation har, også har de nyeste opdateringer. Hvis du gør dette nu, kan det hjælpe med at forhindre problemer senere, når du overfører til Defender for Endpoint og Microsoft Defender Antivirus.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Sørg for, at din eksisterende løsning er opdateret

Hold din eksisterende løsning til beskyttelse af slutpunkter opdateret, og sørg for, at organisationens enheder har de nyeste sikkerhedsopdateringer.

Har du brug for hjælp? Se din løsningsudbyders dokumentation.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Sørg for, at organisationens enheder er opdaterede

Har du brug for hjælp til at opdatere organisationens enheder? Se følgende ressourcer:

|Operativsystem|Ressource|
|---|---|
|Windows|[Microsoft Update](https://www.update.microsoft.com)|
|Macos|[Sådan opdaterer du softwaren på din Mac](https://support.apple.com/HT201541)|
|Ios|[Opdater dine iPhone, iPad eller iPod touch](https://support.apple.com/HT204204)|
|Android|[Kontrollér& opdatere din Android-version](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: Opdaterer dit system](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Hent Microsoft Defender for Endpoint

Nu, hvor du har opdateret organisationens enheder, er næste trin at hente Defender for Endpoint, tildele licenser og sikre, at tjenesten er klargjort.

1. Køb eller prøv Defender for Endpoint i dag. [Start en gratis prøveversion, eller anmod om et tilbud](https://aka.ms/mdatp).

2. Kontrollér, at dine licenser er klargjort korrekt. [Kontrollér din licenstilstand](production-deployment.md#check-license-state).

3. Konfigurer din dedikerede cloudforekomst af Defender for Endpoint. Se [Konfiguration af slutpunkt i Defender for: Lejerkonfiguration](production-deployment.md#tenant-configuration).

4. Hvis slutpunkter (f.eks. enheder) i din organisation bruger en proxy til at få adgang til internettet, skal du se [Konfiguration af Defender for Endpoint: Netværkskonfiguration](production-deployment.md#network-configuration).

På dette tidspunkt er du klar til at give adgang til dine sikkerhedsadministratorer og sikkerhedsoperatører, der skal bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

> [!NOTE]
> Microsoft 365 Defender-portalen kaldes nogle gange Defender for Endpoint-portalen og kan tilgås på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. Den tidligere Microsoft Defender Security Center (https://securitycenter.windows.com) omdirigerer snart til Microsoft 365 Defender-portalen. Du kan få mere at vide [under oversigt over Microsoft 365 Defender portal](portal-overview.md).

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Giv adgang til Microsoft 365 Defender-portalen

I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> kan du få adgang til og konfigurere funktioner og funktioner i Defender for Endpoint. Du kan få mere at vide under [Oversigt over Microsoft 365 Defender-portalen](use.md).

Tilladelser til Microsoft 365 Defender portalen kan tildeles ved hjælp af enten grundlæggende tilladelser eller rollebaseret adgangskontrol. Vi anbefaler, at du bruger RBAC, så du har mere detaljeret kontrol over tilladelser.

1. Planlæg rollerne og tilladelserne for dine sikkerhedsadministratorer og sikkerhedsoperatører. Se [Rollebaseret adgangskontrol](prepare-deployment.md#role-based-access-control).

2. Konfigurer og konfigurer RBAC. Vi anbefaler, at du bruger [Intune](/mem/intune/fundamentals/what-is-intune) til at konfigurere RBAC, især hvis din organisation bruger en kombination af Windows 10, macOS-, iOS- og Android-enheder. Se [Konfiguration af RBAC ved hjælp af Intune](/mem/intune/fundamentals/role-based-access-control).

    Hvis din organisation kræver en anden metode end Intune, skal du vælge en af følgende indstillinger:

    - [Konfigurationsstyring](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)

    - [Administration af avancerede Gruppepolitik](/microsoft-desktop-optimization-pack/agpm)
    
    - [Windows Administration](/windows-server/manage/windows-admin-center/overview)

3. Tildel adgang til Microsoft 365 Defender-portalen. (Har du brug for hjælp? Se [Administrer portaladgang ved hjælp af RBAC](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfigurer indstillinger for enhedsproxy og internetforbindelse

Hvis du vil aktivere kommunikation mellem dine enheder og Defender for Endpoint, skal du konfigurere proxy- og internetindstillinger. Følgende tabel indeholder links til ressourcer, du kan bruge til at konfigurere proxy- og internetindstillingerne for forskellige operativsystemer og funktioner:

|Kapaciteter|Operativsystem|Ressourcer|
|---|---|---|
|[Registrering af slutpunkt og svar](overview-endpoint-detection-response.md) (Slutpunktsregistrering og -svar)|[Windows 10](/windows/release-health/release-information) eller nyere<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 eller nyere](/windows-server/get-started/whats-new-in-windows-server-1803)<br/><br/>[Windows Server 2016*](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Konfigurer indstillinger for computerproxy og internetforbindelse](configure-proxy-internet.md)|
|Slutpunktsregistrering og -svar [Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Konfigurer indstillinger for proxy- og internetforbindelse](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|Slutpunktsregistrering og -svar|macOS (se [Systemkrav](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint på macOS: Netværksforbindelser](microsoft-defender-endpoint-mac.md#network-connections)|
|[Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 eller nyere](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)<br/><br/>[Windows Server 2012 R2*](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)|[Konfigurer og valider Microsoft Defender Antivirus netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md)|
|Antivirus|macOS (se [Systemkrav](microsoft-defender-endpoint-mac.md)|[Defender for Endpoint på macOS: Netværksforbindelser](microsoft-defender-endpoint-mac.md#network-connections)|
|Antivirus|Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender for Endpoint på Linux: Netværksforbindelser](microsoft-defender-endpoint-linux.md#network-connections)|

*Kræver installation af den moderne, samlede løsning til Windows Server 2012 R2 og 2016. Du kan få flere oplysninger under [Onboard Windows-servere til tjenesten Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført **klargøringsfasen** for [at skifte til Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [Fortsæt med at konfigurere Defender for Endpoint](switch-to-mde-phase-2.md).
