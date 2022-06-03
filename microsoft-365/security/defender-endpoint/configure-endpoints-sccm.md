---
title: Onboarde Windows enheder ved hjælp af Configuration Manager
description: Brug Configuration Manager til at installere konfigurationspakken på enheder, så de er onboardet til Defender for Endpoint-tjenesten.
keywords: onboard-enheder ved hjælp af sccm, enhedshåndtering, konfigurer Microsoft Defender for Endpoint enheder
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 09/22/2021
ms.technology: mde
ms.openlocfilehash: d60d01bd2a77d992110f85967196390f3dceae3d
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873704"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Onboarde Windows enheder ved hjælp af Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager aktuelle forgrening
- System Center 2012 R2 Configuration Manager

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Du kan bruge Configuration Manager til at føje slutpunkter til Microsoft Defender for Endpoint-tjenesten. 

Der er flere muligheder, du kan bruge til at onboarde enheder ved hjælp af Configuration Manager:
- [Onboarde enheder ved hjælp af System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Lejer vedhæft](/mem/configmgr/tenant-attach/)



For Windows Server 2012 R2 og Windows Server 2016 – når du har fuldført onboardingtrinnene, skal du [konfigurere og opdatere System Center Endpoint Protection klienter](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Defender for Endpoint understøtter ikke onboarding i [OOBE-fasen (Out-Of-Box Experience).](/windows-hardware/test/assessments/out-of-box-experience) Sørg for, at brugerne fuldfører OOBE, når de har kørt Windows installation eller opgradering.
>
> Bemærk, at det er muligt at oprette en registreringsregel for et Configuration Manager program for løbende at kontrollere, om en enhed er blevet onboardet. Et program er en anden objekttype end en pakke og et program.
> Hvis en enhed endnu ikke er onboardet (på grund af ventende OOBE-fuldførelse eller andre årsager), vil Configuration Manager prøve at onboarde enheden igen, indtil reglen registrerer statusændringen.
>
> Denne funktionsmåde kan opnås ved at oprette en registreringsregel, der kontrollerer, om registreringsdatabaseværdien "OnboardingState" (af typen REG_DWORD) = 1.
> Denne registreringsdatabaseværdi er placeret under "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Du kan få flere oplysninger under [Konfigurer registreringsmetoder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurer indstillinger for eksempelsamling

For hver enhed kan du angive en konfigurationsværdi for at angive, om der kan indsamles eksempler fra enheden, når der foretages en anmodning via Microsoft 365 Defender til at sende en fil til detaljeret analyse.

> [!NOTE]
> Disse konfigurationsindstillinger udføres typisk via Configuration Manager.

Du kan angive en regel for overholdelse af regler og standarder for konfigurationselementet i Configuration Manager for at ændre indstillingen for eksempeldeling på en enhed.

Denne regel skal være en *afhjælpning af* konfigurationselementet for overholdelsesreglen, der angiver værdien af en registreringsnøgle på målrettede enheder for at sikre, at de klager.

Konfigurationen angives via følgende post i registreringsdatabasenøglen:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Hvor Nøgletype er et D-WORD. De mulige værdier er:

- 0: Tillader ikke eksempeldeling fra denne enhed
- 1: Tillader deling af alle filtyper fra denne enhed

Standardværdien, hvis registreringsdatabasenøglen ikke findes, er 1.

Du kan få flere oplysninger om System Center Configuration Manager overholdelse i [Introduktion til indstillinger for overholdelse af angivne standarder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Når du har onboardet enheder til tjenesten, er det vigtigt at drage fordel af de inkluderede trusselsbeskyttelsesfunktioner ved at aktivere dem med følgende anbefalede konfigurationsindstillinger.

### <a name="device-collection-configuration"></a>Konfiguration af enhedssamling

Hvis du bruger Endpoint Configuration Manager version 2002 eller nyere, kan du vælge at udvide installationen til at omfatte servere eller klienter på et tidligere niveau.

### <a name="next-generation-protection-configuration"></a>Næste generation af konfiguration af beskyttelse

Følgende konfigurationsindstillinger anbefales:

#### <a name="scan"></a>Skan

- Scan flytbare lagerenheder, f.eks. USB-drev: Ja

#### <a name="real-time-protection"></a>Beskyttelse i realtid

- Aktivér adfærdsovervågning: Ja
- Aktivér beskyttelse mod potentielt uønskede programmer ved download og før installation: Ja

#### <a name="cloud-protection-service"></a>Cloud Protection Service

- Medlemskabstype for Cloud Protection Service: Avanceret medlemskab

#### <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Konfigurer alle tilgængelige regler til Overvågning.

> [!NOTE]
> Blokering af disse aktiviteter kan afbryde legitime forretningsprocesser. Den bedste fremgangsmåde er at indstille alt til overvågning, identificere, hvilke der er sikre at aktivere, og derefter aktivere disse indstillinger på slutpunkter, der ikke har falske positive registreringer.

#### <a name="network-protection"></a>Netværksbeskyttelse

Før du aktiverer netværksbeskyttelse i overvågnings- eller bloktilstand, skal du sørge for, at du har installeret opdateringen af antimalwareplatformen, som kan hentes fra [supportsiden](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Styret mappeadgang

Aktivér funktionen i overvågningstilstand i mindst 30 dage. Efter denne periode skal du gennemse registreringer og oprette en liste over programmer, der har tilladelse til at skrive til beskyttede mapper.

Du kan finde flere oplysninger under [Evaluer kontrolleret mappeadgang](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at en enhed er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Offboard-enheder, der bruger Configuration Manager

Af sikkerhedsmæssige årsager udløber den pakke, der bruges til Offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Enheder uden for om bord, der bruger Microsoft Endpoint Manager aktuelle forgrening

Hvis du bruger Microsoft Endpoint Manager aktuelle forgrening, skal du se [Opret en konfigurationsfil til offboarding](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Offboard-enheder, der bruger System Center 2012 R2 Configuration Manager

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal:</a>
    1. I navigationsruden skal du vælge **Indstillinger** \> **Slutpunkter** \> **Administration af** \> enhed **offboarding**.  
    1. Vælg Windows 10 eller Windows 11 som operativsystem.
    1. I feltet **Installationsmetode** skal du vælge **System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. Vælg **Download pakke**, og gem filen .zip.

2. Udpak indholdet af .zip-filen på en delt, skrivebeskyttet placering, som netværksadministratorerne kan få adgang til, og som skal installere pakken. Du skal have en fil med navnet *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

3. Installér pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)).

   Vælg en foruddefineret enhedsgruppe, som pakken skal installeres på.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Hvis du bruger Microsoft Endpoint Manager aktuelle forgrening, skal du bruge det indbyggede Defender for Endpoint-dashboard i Configuration Manager-konsollen. Du kan finde flere oplysninger under [Defender for Endpoint – Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Hvis du bruger System Center 2012 R2 Configuration Manager, består overvågningen af to dele:

1. Bekræftelse af konfigurationspakken er installeret korrekt og kører (eller kører) på enhederne i netværket.

2. Kontrollerer, at enhederne overholder Defender for Endpoint-tjenesten (dette sikrer, at enheden kan fuldføre onboardingprocessen og kan fortsætte med at rapportere data til tjenesten).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Bekræft, at konfigurationspakken er installeret korrekt

1. Klik på **Overvågning** nederst i navigationsruden i Configuration Manager konsol.

2. Vælg **Oversigt** og derefter **Udrulninger**.

3. Vælg udrulningen med pakkenavnet.

4. Gennemse statusindikatorerne under **Statistik for fuldførelse** og **indholdsstatus**.

    Hvis der er mislykkede installationer (enheder med **statuserne Error**, **Requirements Not Met** eller **Failed**), skal du muligvis foretage fejlfinding af enhederne. Du kan finde flere oplysninger under [Fejlfinding af Microsoft Defender for Endpoint problemer med onboarding](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Den Configuration Manager, der viser en vellykket installation uden fejl" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Kontrollér, at enhederne overholder Microsoft Defender for Endpoint-tjenesten

Du kan angive en regel for overholdelse af regler og standarder for konfigurationselementet i System Center 2012 R2-Configuration Manager for at overvåge udrulningen.

Denne regel skal være et konfigurationselement til en *ikke-afhjælpningsregel* , der overvåger værdien af en registreringsdatabasenøgle på målrettede enheder.

Overvåg følgende post i registreringsdatabasenøglen:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Du kan få flere oplysninger under [Introduktion til indstillinger for overholdelse af angivne standarder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md)
- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
