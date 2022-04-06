---
title: Skift til Microsoft Defender for Endpoint – Forbered
description: Gør dig klar til at skifte til Microsoft Defender for Endpoint. Opdater dine enheder, og konfigurer dine netværksforbindelser.
keywords: overførsel, Microsoft Defender for Endpoint, bedste fremgangsmåde
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
ms.date: 11/30/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: aa0bd45c1765e2aa794e00e437bf08a63d1d742f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476725"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>Skift til Microsoft Defender for Endpoint – Fase 1: Forbered

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![Fase 1: Forbered.](images/phase-diagrams/prepare.png#lightbox)<br/>Fase 1: Forbered | [![Fase 2: Konfigurer](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[Fase 2: Konfigurer](switch-to-mde-phase-2.md) | [![Fase 3: Onboard](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[Fase 3: Onboard](switch-to-mde-phase-3.md) |
|--|--|--|
|*Du er her!*| | |

**Velkommen til Forbered fasen for [skift til Defender til slutpunkt](switch-to-mde-overview.md#the-migration-process)**.

Denne overførselsfase omfatter følgende trin:

1. [Hent og installer opdateringer på tværs af organisationens enheder](#get-and-deploy-updates-across-your-organizations-devices)
2. [Få Defender til slutpunkt](#get-microsoft-defender-for-endpoint).
3. [Giv adgang til Microsoft 365 Defender portalen](#grant-access-to-the-microsoft-365-defender-portal).
4. [Konfigurer indstillinger for enhedsproxy og internetforbindelse](#configure-device-proxy-and-internet-connectivity-settings).

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>Hent og installer opdateringer på tværs af organisationens enheder

Som en bedste fremgangsmåde skal du holde din organisations enheder og slutpunkter opdateret. Sørg for, at din eksisterende slutpunktsbeskyttelse og antivirusløsning er opdateret, og at de operativsystemer og apps, din organisation har, også har de seneste opdateringer. Hvis du gør dette nu, kan det forhindre problemer senere, når du overfører til Defender for Endpoint Microsoft Defender Antivirus.

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>Sørg for, at din eksisterende løsning er opdateret

Hold din eksisterende løsning til slutpunktsbeskyttelse opdateret, og sørg for, at organisationens enheder har de nyeste sikkerhedsopdateringer.

Har du brug for hjælp? Se løsningsudbyderens dokumentation.

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>Sørg for, at din organisations enheder er opdateret

Har du brug for hjælp til at opdatere din organisations enheder? Se følgende ressourcer:

<br/><br/>

|OPERATIVSYSTEM|Ressource|
|---|---|
|Windows|[Microsoft Update](https://www.update.microsoft.com)|
|macOS|[Sådan opdaterer du softwaren på din Mac](https://support.apple.com/HT201541)|
|iOS|[Opdater din iPhone, iPad eller iPod touch](https://support.apple.com/HT204204)|
|Android|[Kontrollér, & din Android-version er opdateret](https://support.google.com/android/answer/7680439)|
|Linux|[Linux 101: Opdatering af dit system](https://www.linux.com/training-tutorials/linux-101-updating-your-system)|

## <a name="get-microsoft-defender-for-endpoint"></a>Få Microsoft Defender for Endpoint

Nu hvor du har opdateret din organisations enheder, er næste trin at få Defender til Slutpunkt, tildele licenser og sikre, at tjenesten er klargjort.

1. Køb eller prøv Defender til Slutpunkt i dag. [Start en gratis prøveversion, eller anmod om et tilbud](https://aka.ms/mdatp).

2. Kontrollér, at dine licenser er korrekt klargjort. [Kontrollér din licenstilstand](production-deployment.md#check-license-state).

3. Konfigurer din dedikerede skyforekomst af Defender til Slutpunkt. Se [Konfiguration af Defender til slutpunkt: Lejerkonfiguration](production-deployment.md#tenant-configuration).

4. Hvis slutpunkter (f.eks. enheder) i organisationen bruger en proxy til at få adgang til internettet, skal du se [Konfiguration af Defender til slutpunkt: Netværkskonfiguration](production-deployment.md#network-configuration).

På nuværende tidspunkt er du klar til at give adgang til dine sikkerhedsadministratorer og sikkerhedsoperatorer, der skal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">bruge Microsoft 365 Defender-portalen</a>.

> [!NOTE]
> Den Microsoft 365 Defender portal kaldes sommetider for Defender for Endpoint-portalen og kan tilgås på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>. Den tidligere Microsoft Defender Security Center (https://securitycenter.windows.com)omdirigeres snart til Microsoft 365 Defender portalen. Du kan få mere at vide [Microsoft 365 Defender oversigt over portal.](portal-overview.md)

## <a name="grant-access-to-the-microsoft-365-defender-portal"></a>Give adgang til Microsoft 365 Defender-portalen

Portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender er</a> stedet, hvor du kan få adgang til og konfigurere funktioner og egenskaber for Defender til Slutpunkt. Du kan få mere at [vide under Oversigt over Microsoft 365 Defender portal](use.md).

Tilladelser til portalen Microsoft 365 Defender kan tildeles ved hjælp af grundlæggende tilladelser eller rollebaseret adgangskontrol (RBAC). Vi anbefaler, at du bruger RBAC, så du har mere detaljeret kontrol over tilladelser.

1. Planlæg roller og tilladelser til sikkerhedsadministratorer og sikkerhedsoperatorer. Se [Rollebaseret adgangskontrol](prepare-deployment.md#role-based-access-control).

2. Konfigurere RBAC. Vi anbefaler at [Intune](/mem/intune/fundamentals/what-is-intune) til at konfigurere RBAC, især hvis din organisation bruger en kombination af Windows 10-, macOS-, iOS- og Android-enheder. Se [konfiguration af RBAC ved hjælp Intune](/mem/intune/fundamentals/role-based-access-control).

    Hvis din organisation kræver en anden metode end Intune, skal du vælge en af følgende indstillinger:

    - [Konfigurationsstyring](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [Avanceret Gruppepolitik administration](/microsoft-desktop-optimization-pack/agpm)
    - [Windows Administration](/windows-server/manage/windows-admin-center/overview)

3. Giv adgang til Microsoft 365 Defender portalen. (Har du brug for hjælp? Se [Administrer portaladgang ved hjælp af RBAC](rbac.md).

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfigurere indstillinger for enhedsproxy og internetforbindelse

For at aktivere kommunikation mellem dine enheder og Defender til Slutpunkt skal du konfigurere proxy- og internetindstillinger. Følgende tabel indeholder links til ressourcer, du kan bruge til at konfigurere din proxy og dine internetindstillinger for forskellige operativsystemer og funktioner:

<br/><br/>

|Funktioner|Operativsystem|Ressourcer|
|---|---|---|
|[Registrering af slutpunkt og svar](overview-endpoint-detection-response.md) (Slutpunktsregistrering og -svar)|[Windows 10](/windows/release-health/release-information) eller nyere<br/><br/>Windows Server 2022 <br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/>[Windows Server 1803 eller nyere](/windows-server/get-started/whats-new-in-windows-server-1803)|[Konfigurere indstillinger for computerproxy og internetforbindelse](configure-proxy-internet.md)|
|Slutpunktsregistrering og -svar|[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)|[Konfigurere indstillinger for proxy og forbindelse til internettet](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings)|
|Slutpunktsregistrering og -svar|macOS (se [Systemkrav)](microsoft-defender-endpoint-mac.md)|[Defender til Slutpunkt på macOS: Netværksforbindelser](microsoft-defender-endpoint-mac.md#network-connections)|
|[Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md)|[Windows 10](/windows/release-health/release-information) <br/><br/> [Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<br/><br/> Windows Server 2022 <br/><br/> [Windows Server 1803 eller nyere](/windows-server/get-started/whats-new-in-windows-server-1803) <br/><br/> [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)|[Konfigurere og validere Microsoft Defender Antivirus netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md)|
|Antivirus|macOS (se [Systemkrav)](microsoft-defender-endpoint-mac.md)|[Defender til Slutpunkt på macOS: Netværksforbindelser](microsoft-defender-endpoint-mac.md#network-connections)|
|Antivirus|Linux (se [Systemkrav](microsoft-defender-endpoint-linux.md#system-requirements))|[Defender til slutpunkt på Linux: Netværksforbindelser](microsoft-defender-endpoint-linux.md#network-connections)|


## <a name="next-step"></a>Næste trin

**Tillykke**! Du har færdiggjort **fasen Forbered** skiftet [til Defender til Slutpunkt](switch-to-mde-overview.md#the-migration-process)!

- [Fortsæt med at konfigurere Defender til slutpunkt.](switch-to-mde-phase-2.md)
