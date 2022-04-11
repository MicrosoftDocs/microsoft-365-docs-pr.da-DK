---
title: Onboarde Windows 10- og Windows 11 enheder ved hjælp af Configuration Manager
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Brug Configuration Manager til at installere konfigurationspakken på enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: 2cca9cc073ca08c7fabb19511a4253e4a682057a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760707"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Onboarde Windows 10- og Windows 11 enheder ved hjælp af Configuration Manager

**Gælder for:**

- [Microsoft 365 Endpoint DLP (forebyggelse af datatab)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>Onboarde enheder ved hjælp af System Center Configuration Manager

1. Hent konfigurationspakken .zip-filen (*DeviceComplianceOnboardingPackage.zip*) fra [Microsoft Compliance Center](https://compliance.microsoft.com/).

2. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> >  **Device OnboardingOnboarding** >  i navigationsruden.

3. I feltet **Installationsmetode** skal du vælge **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

4. Vælg **Download pakke**, og gem filen .zip.

5. Udpak indholdet af .zip-filen på en delt, skrivebeskyttet placering, som netværksadministratorerne kan få adgang til, og som skal installere pakken. Du skal have en fil med navnet *DeviceComplianceOnboardingScript.cmd*.

6. Installér pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

7. Vælg en foruddefineret enhedsgruppe, som pakken skal installeres på.

> [!NOTE]
> Microsoft 365 information protection understøtter ikke onboarding under [OOBE-fasen (Out-Of-Box Experience).](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) Sørg for, at brugerne fuldfører OOBE, når de har kørt Windows installation eller opgradering.

> [!TIP]
> Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at en enhed er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Bemærk, at det er muligt at oprette en registreringsregel på et Configuration Manager program for løbende at kontrollere, om en enhed er blevet onboardet. Et program er en anden objekttype end en pakke og et program.
> Hvis en enhed endnu ikke er onboardet (på grund af ventende OOBE-fuldførelse eller andre årsager), vil Configuration Manager prøve at onboarde enheden igen, indtil reglen registrerer statusændringen.
>
> Denne funktionsmåde kan opnås ved at oprette en registreringsregel, der kontrollerer, om registreringsdatabaseværdien "OnboardingState" (af typen REG_DWORD) = 1.
> Denne registreringsdatabaseværdi er placeret under "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Du kan få flere oplysninger under [Konfigurer registreringsmetoder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurer indstillinger for eksempelsamling

For hver enhed kan du angive en konfigurationsværdi for at angive, om der kan indsamles eksempler fra enheden, når der foretages en anmodning via Microsoft Defender Security Center til at sende en fil til detaljeret analyse.

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

Hvor:

Nøgletypen er et D-WORD.

De mulige værdier er:

- 0 – tillader ikke eksempeldeling fra denne enhed
- 1 – tillader deling af alle filtyper fra denne enhed

Standardværdien, hvis registreringsdatabasenøglen ikke findes, er 1.

Du kan få flere oplysninger om System Center Configuration Manager overholdelse i [Introduktion til indstillinger for overholdelse af angivne standarder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Når du har onboardet enheder til tjenesten, er det vigtigt at drage fordel af de inkluderede trusselsbeskyttelsesfunktioner ved at aktivere dem med følgende anbefalede konfigurationsindstillinger.

### <a name="device-collection-configuration"></a>Konfiguration af enhedssamling

Hvis du bruger Endpoint Configuration Manager version 2002 eller nyere, kan du vælge at udvide installationen til at omfatte servere eller klienter på et tidligere niveau.

### <a name="next-generation-protection-configuration"></a>Næste generation af konfiguration af beskyttelse

Følgende konfigurationsindstillinger anbefales:

**Skan**

- Scan flytbare lagerenheder, f.eks. USB-drev: Ja

**Beskyttelse i realtid**

- Aktivér adfærdsovervågning: Ja
- Aktivér beskyttelse mod potentielt uønskede programmer ved download og før installation: Ja

**Cloud Protection Service**

- Medlemskabstype for Cloud Protection Service: Avanceret medlemskab

**Reduktion af angrebsoverflade** Konfigurer alle tilgængelige regler til Overvågning.

> [!NOTE]
> Blokering af disse aktiviteter kan afbryde legitime forretningsprocesser. Den bedste fremgangsmåde er at indstille alt til overvågning, identificere, hvilke der er sikre at aktivere, og derefter aktivere disse indstillinger på slutpunkter, der ikke har falske positive registreringer.

**Netværksbeskyttelse**

Før du aktiverer netværksbeskyttelse i overvågnings- eller bloktilstand, skal du sørge for, at du har installeret opdateringen af antimalwareplatformen, som kan hentes fra [supportsiden](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

**Styret mappeadgang**

Aktivér funktionen i overvågningstilstand i mindst 30 dage. Efter denne periode skal du gennemse registreringer og oprette en liste over programmer, der har tilladelse til at skrive til beskyttede mapper.

Du kan finde flere oplysninger under [Evaluer kontrolleret mappeadgang](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).

## <a name="offboard-devices-using-configuration-manager"></a>Offboard-enheder, der bruger Configuration Manager

Af sikkerhedsmæssige årsager udløber den pakke, der bruges til Offboard-enheder, 30 dage efter den dato, hvor den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du downloader en offboarding-pakke, får du besked om pakkernes udløbsdato, og den medtages også i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, ellers vil det medføre uforudsigelige kollisioner.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Enheder uden for om bord, der bruger Microsoft Endpoint Configuration Manager aktuelle forgrening

Hvis du bruger Microsoft Endpoint Configuration Manager aktuelle forgrening, skal du se [Opret en konfigurationsfil til offboarding](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Offboard-enheder, der bruger System Center 2012 R2 Configuration Manager

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>:

2. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> >   **Device onboardingOffboarding**>  i navigationsruden.

3. Vælg Windows 10 som operativsystem.

4. I feltet **Installationsmetode** skal du vælge **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

5. Vælg **Download pakke**, og gem filen .zip.

6. Udpak indholdet af .zip-filen på en delt, skrivebeskyttet placering, som netværksadministratorerne kan få adgang til, og som skal installere pakken. Du skal have en fil med navnet *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. Installér pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)).

8. Vælg en foruddefineret enhedsgruppe, som pakken skal installeres på.

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Hvis du bruger Microsoft Endpoint Configuration Manager aktuelle forgrening, skal du bruge det indbyggede Microsoft Defender for Endpoint dashboard i Configuration Manager-konsollen. Du kan få flere oplysninger under [Microsoft Defender Advanced Threat Protection – Skærm](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Hvis du bruger System Center 2012 R2 Configuration Manager, består overvågningen af to dele:

1. Bekræftelse af konfigurationspakken er installeret korrekt og kører (eller kører) på enhederne i netværket.

2. Kontrollerer, at enhederne overholder Microsoft 365 onboardingtjeneste (dette sikrer, at enheden kan fuldføre onboardingprocessen og kan fortsætte med at rapportere data til tjenesten).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Bekræft, at konfigurationspakken er installeret korrekt

1. Klik på **Overvågning** nederst i navigationsruden i Configuration Manager konsol.

2. Vælg **Oversigt** og derefter **Udrulninger**.

3. Vælg udrulningen med pakkenavnet.

4. Gennemse statusindikatorerne under **Statistik for fuldførelse** og **indholdsstatus**.

    Hvis der er mislykkede installationer (enheder med **statuserne Error**, **Requirements Not Met** eller **Failed**), skal du muligvis foretage fejlfinding af enhederne. Du kan finde flere oplysninger under [Fejlfinding af onboardingproblemer med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Configuration Manager viser en vellykket installation uden fejl.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Kontrollér, at enhederne overholder Microsoft 365 tjenesten til forebyggelse af datatab på slutpunktet

Du kan angive en regel for overholdelse af regler og standarder for konfigurationselementet i System Center 2012 R2-Configuration Manager for at overvåge udrulningen.

> [!NOTE]
> Denne procedure og registreringsdatabasepost gælder for Endpoint DLP samt Defender for Endpoint.

Denne regel skal være et konfigurationselement til en *ikke-afhjælpningsregel* , der overvåger værdien af en registreringsdatabasenøgle på målrettede enheder.

Overvåg følgende post i registreringsdatabasenøglen:

```text
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Du kan få flere oplysninger under [Introduktion til indstillinger for overholdelse af angivne standarder i System Center 2012 R2 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>Relaterede emner

- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Forbindelse med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
