---
title: Onboard Windows 10 og Windows 11 enheder ved hjælp af Konfigurationsstyring
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
description: Brug Konfigurationsstyring til at installere konfigurationspakken på enheder, så de er onboardet til tjenesten.
ms.openlocfilehash: 9f9edc9543a446f98622ff80d8cceec406a2658a
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/12/2021
ms.locfileid: "63601040"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Onboard Windows 10 og Windows 11 enheder ved hjælp af Konfigurationsstyring

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>Onboard-enheder med System Center Configuration Manager

1. Hent konfigurationspakken .zip (*DeviceComplianceOnboardingPackage.zip*) fra [Microsoft Compliance Center](https://compliance.microsoft.com/).

2. I navigationsruden skal du <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**vælge Indstillinger**</a> >  **Enhed OnboardingOnboarding** > .

3. I feltet **Installationsmetode** skal du vælge **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

4. Vælg **Download pakke**, og gem .zip fil.

5. Udtræk indholdet af filen .zip en delt, skrivebeskyttet placering, der kan åbnes af de netværksadministratorer, der skal installere pakken. Du skal have en fil med *navnet DeviceComplianceOnboardingScript.cmd*.

6. Installer pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) artikel.

7. Vælg en foruddefineret samling af enheder, som pakken skal installeres på.

> [!NOTE]
> Microsoft 365 beskyttelse af oplysninger understøtter ikke onboarding i [OOBE-fasen (Out of box Experience](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87)). Sørg for, at brugerne fuldfører OOBE efter at have Windows installation eller opgradering.

> [!TIP]
> Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Bemærk, at det er muligt at oprette en registreringsregel på et Konfigurationsstyring program for hele tiden at kontrollere, om en enhed er blevet onboardet. Et program er en anden type objekt end en pakke og et program.
> Hvis en enhed endnu ikke er onboardet (på grund af afventende OOBE-fuldførelse eller en anden årsag), forsøger Konfigurationsstyring at onboarde enheden, indtil reglen registrerer statusændringen.
>
> Denne funktionsmåde kan udføres ved at oprette en registreringsregel, der kontrollerer, om registreringsdatabaseværdien "OnboardingState" (af typen REG_DWORD) = 1.
> Denne registreringsdatabaseværdi er placeret under "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status".
Få mere at vide under [Konfigurer registreringsmetoder i System Center 2012 R2 Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Konfigurere indstillinger for eksempelsamling

For hver enhed kan du angive en konfigurationsværdi for at angive, om der kan indsamles eksempler fra enheden, når der foretages en anmodning via Microsoft Defender Security Center om at sende en fil til dybdegående analyse.

> [!NOTE]
> Disse konfigurationsindstillinger udføres typisk via Konfigurationsstyring.

Du kan angive en regel for overholdelse af angivne standarder for konfigurationselement Konfigurationsstyring at ændre indstillingen for eksempelshare på en enhed.

Denne regel bør løse problemer *med konfigurationen* af overholdelsesreglen, der angiver værdien af en registreringsdatabasenøgle på målrettede enheder for at sikre, at de klages.

Konfigurationen angives via følgende registreringsdatabasenøglepost:

```
Path: “HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection”
Name: "AllowSampleCollection"
Value: 0 or 1
```
Hvor:<br>
Nøgletype er et D-WORD. <br>
De mulige værdier er:
- 0 – tillader ikke eksempeldeling fra denne enhed
- 1 – tillader deling af alle filtyper fra denne enhed

Standardværdien i tilfælde af, at registreringsdatabasenøglen ikke findes, er 1.

Du kan finde flere System Center Configuration Manager om overholdelse af regler og standarder i Introduktion til indstillinger for overholdelse af regler og standarder i [System Center 2012 R2 Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger
Efter onboardingenheder til tjenesten er det vigtigt at drage fordel af de medfølgende egenskaber til trusselsbeskyttelse ved at give dem følgende anbefalede konfigurationsindstillinger.

### <a name="device-collection-configuration"></a>Konfiguration af enhedssamling
Hvis du bruger Slutpunkt Konfigurationsstyring, version 2002 eller nyere, kan du vælge at udvide installationen og medtage servere eller klienter på down-level.


### <a name="next-generation-protection-configuration"></a>Næste generations beskyttelseskonfiguration

Følgende konfigurationsindstillinger anbefales:

**Scan**

- Scan flytbare lagringsenheder, f.eks. USB-drev: Ja

**Beskyttelse i realtid**

- Aktivér funktionsmådeovervågning: Ja
- Aktivér beskyttelse mod potentielt uønskede programmer ved download og før installation: Ja

**Cloud Protection Service**

- Medlemskabstype for Cloud Protection Service: Avanceret medlemskab

**Reduktion af angrebsoverfladen** Konfigurer alle tilgængelige regler til Overvågning.

> [!NOTE]
> Blokering af disse aktiviteter kan afbryde legitime forretningsprocesser. Den bedste fremgangsmåde er at indstille alt til overvågning, identificere, hvilke der er sikre at slå til, og derefter aktivere disse indstillinger på slutpunkter, der ikke har falske positive registreringer.

**Netværksbeskyttelse**

Før du aktiverer netværksbeskyttelse i overvågningstilstand eller blokeringstilstand, skal du sikre dig, at du har installeret opdateringen af antimalwareplatformen, som kan fås fra [supportsiden](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).


**Styret mappeadgang**

Aktivér funktionen i overvågningstilstand i mindst 30 dage. Efter dette tidsrum skal du gennemse registreringer og oprette en liste over programmer, der har tilladelse til at skrive i beskyttede mapper.

Få mere at vide under [Evaluer styret mappeadgang](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).


## <a name="offboard-devices-using-configuration-manager"></a>Offboard-enheder, der bruger Konfigurationsstyring

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Offboard-enheder, der Microsoft Endpoint Configuration Manager aktuelle forgrening

Hvis du bruger en Microsoft Endpoint Configuration Manager forgrening, skal du [se Opret en offboarding-konfigurationsfil](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>Offboard-enheder, der bruger System Center 2012 R2 Konfigurationsstyring

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>:

2. I navigationsruden skal du <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**vælge Indstillinger**</a> >   **Device onboardingOffboarding**> .

3. Vælg Windows 10 som operativsystem.

4. I feltet **Installationsmetode** skal du vælge **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602**.

5. Vælg **Download pakke**, og gem .zip fil.

6. Udtræk indholdet af filen .zip en delt, skrivebeskyttet placering, der kan åbnes af de netværksadministratorer, der skal installere pakken. Du skal have en fil med *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd*.

7. Installer pakken ved at følge trinnene i artiklen [Pakker og programmer i System Center 2012 R2 Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) artikel.

8. Vælg en foruddefineret samling af enheder, som pakken skal installeres på.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.


## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Hvis du bruger en Microsoft Endpoint Configuration Manager forgrening, skal du bruge det indbyggede Microsoft Defender for Endpoint-dashboard Konfigurationsstyring konsollen. Du kan finde flere oplysninger [i Microsoft Defender Advanced Threat Protection – Monitor](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

Hvis du bruger System Center 2012 R2 Konfigurationsstyring, består overvågning af to dele:

1. Bekræftelse af konfigurationspakken er blevet installeret korrekt og kører (eller er kørt) på enhederne i netværket.

2. Kontrollerer, at enhederne er kompatible med Microsoft 365-onboardingtjenesten (dette sikrer, at enheden kan fuldføre onboardingprocessen og kan fortsætte med at rapportere data til tjenesten).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Bekræft, at konfigurationspakken er installeret korrekt

1. I Konfigurationsstyring skal du klikke **på** Overvågning nederst i navigationsruden.

2. Vælg **Oversigt** og derefter **Installationer**.

3. Vælg på installationen med pakkenavnet.

4. Gennemgå statusindikatorerne under **Statistik for fuldførelse** og **Status for indhold**.

    Hvis der er mislykkede installationer (enheder med **fejl,** **krav**, der ikke er opfyldt eller statusserne Mislykkedes **), skal** du muligvis foretage fejlfinding af enhederne. Hvis du vil have mere at vide, skal [du se Fejlfinding i forbindelse med Microsoft Defender Advanced Threat Protection-onboarding](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Konfigurationsstyring vellykket installation uden fejl.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Kontrollér, at enhederne er kompatible med Microsoft 365 slutpunktstjenesten til forebyggelse af datatab

Du kan angive en overholdelsesregel for konfigurationselementet i System Center 2012 R2 Konfigurationsstyring at overvåge din installation.

> [!NOTE]
> Denne procedure og post i registreringsdatabasen gælder for Slutpunkt DLP samt Defender for Slutpunkt.

Denne regel skal være et *ikke-afhjælpende regelkonfigurationselement* , der overvåger værdien af en registreringsdatabasenøgle på målrettede enheder.

Overvåg følgende post i registreringsdatabasens nøgle:
```
Path: “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status”
Name: “OnboardingState”
Value: “1”
```
Få mere at vide under [Introduktion til indstillinger for overholdelse af regler og standarder i System Center 2012 R2 Konfigurationsstyring](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](device-onboarding-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)