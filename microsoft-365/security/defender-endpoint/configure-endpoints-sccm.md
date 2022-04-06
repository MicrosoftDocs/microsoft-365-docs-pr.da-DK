---
title: Onboard Windows-enheder ved hjælp af Configuration Manager
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
ms.openlocfilehash: d67a4ca067f16d74b15a1d7ece5c47d563f1a941
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471892"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Onboard Windows-enheder ved hjælp af Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager aktuel forgrening
- System Center 2012 R2 Configuration Manager

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Du kan bruge Configuration Manager til at onboarde slutpunkter til Microsoft Defender for Endpoint tjeneste. 

Der er flere muligheder, du kan bruge til onboard-enheder ved hjælp Configuration Manager:
- [Onboard-enheder med System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Lejer vedhæftet](/mem/configmgr/tenant-attach/)



For Windows Server 2012 R2 og Windows Server 2016 skal du konfigurere og opdatere System Center Endpoint Protection klienter, når du har fuldført [onboardingtrinnene](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Defender til Slutpunkt understøtter ikke onboarding under [OOBE-fasen (Out of Box Experience](https://answers.microsoft.com/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) ). Sørg for, at brugerne fuldfører OOBE efter at have Windows installation eller opgradering.
>
> Bemærk, at det er muligt at oprette en registreringsregel på et Configuration Manager program for hele tiden at kontrollere, om en enhed er blevet onboardet. Et program er en anden type objekt end en pakke og et program.
> Hvis en enhed endnu ikke er onboardet (på grund af afventende OOBE-fuldførelse eller en anden årsag), forsøger Configuration Manager at onboarde enheden igen, indtil reglen registrerer statusændringen.
>
> Denne funktionsmåde kan udføres ved at oprette en registreringsregel, der kontrollerer, om registreringsdatabaseværdien "OnboardingState" (af typen REG_DWORD) = 1.
> Denne registreringsdatabaseværdi er placeret under "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Du kan finde flere oplysninger [i Konfigurere registreringsmetoder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurere indstillinger for eksempelsamling

For hver enhed kan du angive en konfigurationsværdi, der angiver, om der kan indsamles eksempler fra enheden, når der foretages en anmodning via Microsoft 365 Defender om at sende en fil til dybdegående analyse.

> [!NOTE]
> Disse konfigurationsindstillinger udføres typisk via Configuration Manager.

Du kan angive en overholdelsesregel for konfigurationselementet Configuration Manager at ændre indstillingen for eksempelshare på en enhed.

Denne regel bør løse problemer *med konfigurationen* af overholdelsesreglen, der angiver værdien af en registreringsdatabasenøgle på målrettede enheder for at sikre, at de klages.

Konfigurationen angives via følgende registreringsdatabasenøglepost:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Hvor Tastetype er et D-WORD. De mulige værdier er:

- 0: Tillader ikke eksempeldeling fra denne enhed
- 1: Tillader deling af alle filtyper fra denne enhed

Standardværdien i tilfælde af, at registreringsdatabasenøglen ikke findes, er 1.

Du kan finde flere System Center Configuration Manager om overholdelse af regler og standarder i Introduktion til indstillinger for overholdelse af regler og standarder i [System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Efter onboardingenheder til tjenesten er det vigtigt at drage fordel af de medfølgende egenskaber til trusselsbeskyttelse ved at give dem følgende anbefalede konfigurationsindstillinger.

### <a name="device-collection-configuration"></a>Konfiguration af enhedssamling

Hvis du bruger Endpoint Configuration Manager, version 2002 eller nyere, kan du vælge at udvide installationen og medtage servere eller klienter på down-level.

### <a name="next-generation-protection-configuration"></a>Næste generations beskyttelseskonfiguration

Følgende konfigurationsindstillinger anbefales:

#### <a name="scan"></a>Scan

- Scan flytbare lagringsenheder, f.eks. USB-drev: Ja

#### <a name="real-time-protection"></a>Beskyttelse i realtid

- Aktivér funktionsmådeovervågning: Ja
- Aktivér beskyttelse mod potentielt uønskede programmer ved download og før installation: Ja

#### <a name="cloud-protection-service"></a>Cloud Protection Service

- Medlemskabstype for Cloud Protection Service: Avanceret medlemskab

#### <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Konfigurer alle tilgængelige regler til Overvågning.

> [!NOTE]
> Blokering af disse aktiviteter kan afbryde legitime forretningsprocesser. Den bedste fremgangsmåde er at indstille alt til overvågning, identificere, hvilke der er sikre at slå til, og derefter aktivere disse indstillinger på slutpunkter, der ikke har falske positive registreringer.

#### <a name="network-protection"></a>Netværksbeskyttelse

Før du aktiverer netværksbeskyttelse i overvågningstilstand eller blokeringstilstand, skal du sikre dig, at du har installeret opdateringen af antimalwareplatformen, som kan fås fra [supportsiden](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Styret mappeadgang

Aktivér funktionen i overvågningstilstand i mindst 30 dage. Efter dette tidsrum skal du gennemse registreringer og oprette en liste over programmer, der har tilladelse til at skrive i beskyttede mapper.

Få mere at vide under [Evaluer styret mappeadgang](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Offboard-enheder, der bruger Configuration Manager

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Offboard-enheder, der Microsoft Endpoint Manager aktuelle forgrening

Hvis du bruger Microsoft Endpoint Manager forgrening, skal du [se Opret en offboarding-konfigurationsfil](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Offboard-enheder, der bruger System Center 2012 R2 Configuration Manager

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>:
    1. I navigationsruden skal du **vælge Indstillinger** \> **Endpoints** \> **Device management** \>**Offboarding**.  
    1. Vælg Windows 10 eller Windows 11 som operativsystem.
    1. I feltet **Installationsmetode** skal du vælge **System Center Configuration Manager 2012/2012 R2/1511/1602**.
    1. Vælg **Download pakke**, og gem .zip fil.

2. Udtræk indholdet af filen .zip en delt, skrivebeskyttet placering, der kan åbnes af de netværksadministratorer, der skal installere pakken. Du skal have en fil med *WindowsDefenderATPOffboardingScript_valid_until_YYYY-DD.cmd-mm*.

3. Installer pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) artikel.

   Vælg en foruddefineret samling af enheder, som pakken skal installeres på.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Hvis du bruger en Microsoft Endpoint Manager forgrening, skal du bruge det indbyggede Defender for Endpoint-dashboard Configuration Manager konsollen. Du kan finde flere oplysninger [i Defender for Endpoint – Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Hvis du bruger System Center 2012 R2 Configuration Manager, består overvågning af to dele:

1. Bekræftelse af konfigurationspakken er blevet installeret korrekt og kører (eller er kørt) på enhederne i netværket.

2. Kontrollerer, at enhederne er kompatible med Defender for Endpoint-tjenesten (dette sikrer, at enheden kan fuldføre onboardingprocessen og kan fortsætte med at rapportere data til tjenesten).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Bekræft, at konfigurationspakken er installeret korrekt

1. I Configuration Manager skal du klikke **på** Overvågning nederst i navigationsruden.

2. Vælg **Oversigt** og derefter **Installationer**.

3. Vælg på installationen med pakkenavnet.

4. Gennemgå statusindikatorerne under **Statistik for fuldførelse** og **Status for indhold**.

    Hvis der er mislykkede installationer (enheder med **fejl,** **krav**, der ikke er opfyldt eller statusserne Mislykkedes **), skal** du muligvis foretage fejlfinding af enhederne. Du kan få mere at vide [under Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Den Configuration Manager, der viser en vellykket installation uden fejl" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Kontrollér, at enhederne er kompatible med Microsoft Defender for Endpoint tjeneste

Du kan angive en regel for overholdelse af regler og standarder for konfigurationselementet i System Center 2012 R2 Configuration Manager at overvåge din installation.

Denne regel skal være et *ikke-afhjælpende regelkonfigurationselement* , der overvåger værdien af en registreringsdatabasenøgle på målrettede enheder.

Overvåg følgende post i registreringsdatabasens nøgle:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Få mere at vide under [Introduktion til indstillinger for overholdelse af regler og standarder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af mobile Enhedshåndtering værktøjer](configure-endpoints-mdm.md)
- [Onboarde Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md)
