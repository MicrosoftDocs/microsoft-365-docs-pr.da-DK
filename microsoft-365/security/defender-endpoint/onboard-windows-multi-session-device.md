---
title: Onboarde Windows enheder med flere sessioner i Azure Virtual Desktop
description: Læs mere i denne artikel om Onboarding Windows enheder med flere sessioner i Azure Virtual Desktop
keywords: Azure Virtual Desktop, AVD, Microsoft Defender, slutpunkt, onboard
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 7a093a3b50d7153c71eecb9707ff8ab0dbef0d20
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013282"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Onboarde Windows enheder med flere sessioner i Azure Virtual Desktop

6 minutter til læsning

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows multisession, der kører på Azure Virtual Desktop (AVD)

Microsoft Defender for Endpoint understøtter overvågning af både VDI- og Azure Virtual Desktop-sessioner. Afhængigt af organisationens behov skal du muligvis implementere VDI- eller Azure Virtual Desktop-sessioner for at hjælpe dine medarbejdere med at få adgang til virksomhedens data og apps fra en ikke-administreret enhed, en ekstern placering eller et lignende scenarie. Med Microsoft Defender for Endpoint kan du overvåge disse virtuelle maskiner for uregelmæssig aktivitet.

## <a name="before-you-begin"></a>Før du begynder

Bliv fortrolig med [overvejelserne i forbindelse med VDI, der ikke er vedvarende](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). Selvom [Azure Virtual Desktop](/azure/virtual-desktop/overview) ikke giver mulighed for ikke-vedholdenhed, giver det mulighed for at bruge et gyldent Windows billede, der kan bruges til at klargøre nye værter og geninstallere maskiner. Dette øger volatiliteten i miljøet og påvirker således, hvilke poster der oprettes og vedligeholdes på Microsoft Defender for Endpoint portalen, hvilket kan reducere synligheden for dine sikkerhedsanalytikere.

> [!NOTE]
> Afhængigt af dit valg af onboardingmetode kan enheder vises på Microsoft Defender for Endpoint portal som enten:
>
> - Enkelt post for hvert virtuelt skrivebord
> - Flere poster for hvert virtuelle skrivebord

Microsoft anbefaler onboarding af Azure Virtual Desktop som en enkelt post pr. virtuelt skrivebord. Dette sikrer, at undersøgelsesoplevelsen på Microsoft Defender for Endpoint-portalen er i forbindelse med én enhed baseret på computernavnet. Organisationer, der ofte sletter og geninstallerer AVD-værter, bør på det kraftigste overveje at bruge denne metode, da det forhindrer, at der oprettes flere objekter for den samme computer på Microsoft Defender for Endpoint-portalen. Dette kan føre til forvirring, når hændelser undersøges. I forbindelse med testmiljøer eller ikke-flygtige miljøer kan du vælge at vælge anderledes.

Microsoft anbefaler, at du føjer Microsoft Defender for Endpoint onboardingscript til det gyldne AVD-billede. På denne måde kan du være sikker på, at dette onboardingscript kører med det samme ved første start. Det udføres som et startscript ved første start på alle AVD-maskiner, der klargøres fra det gyldne AVD-billede. Men hvis du bruger et af galleribillederne uden ændringer, skal du placere scriptet på en delt placering og kalde det fra enten lokal gruppepolitik eller domænegruppepolitik.

> [!NOTE]
> Placeringen og konfigurationen af VDI-onboarding-startscriptet på det gyldne AVD-billede konfigurerer det som et startscript, der kører, når AVD starter. Det anbefales **ikke** at onboarde det faktiske AVD gyldne billede. En anden overvejelse er den metode, der bruges til at køre scriptet. Det bør køre så tidligt i start-/klargøringsprocessen som muligt for at reducere tiden mellem, at maskinen er tilgængelig til at modtage sessioner, og enheden onboarder til tjenesten. Nedenstående scenarier 1 og 2 tager højde for dette.

### <a name="scenarios"></a>Scenarier

Der er flere måder at onboarde en AVD-værtsmaskine på:

- Kør scriptet i det gyldne billede (eller fra en delt placering) under opstart.
- Brug et administrationsværktøj til at køre scriptet.
- Gennem [integration med Microsoft Defender for Cloud](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scenarie 1: Brug af lokal gruppepolitik*

Dette scenarie kræver, at scriptet placeres i et gyldent billede og bruger lokal gruppepolitik til at køre tidligt i startprocessen.

Brug vejledningen i [Onboard de ikke-faste VDI-enheder (Virtual Desktop Infrastructure).](configure-endpoints-vdi.md)

Følg vejledningen for en enkelt post for hver enhed.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scenarie 2: Brug af domænegruppepolitikken*

Dette scenarie bruger et centralt placeret script og kører det ved hjælp af en domænebaseret gruppepolitik. Du kan også placere scriptet i det gyldne billede og køre det på samme måde.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Download WindowsDefenderATPOnboardingPackage.zip-filen fra Windows 365 Defender-portalen

1. Åbn VDI-konfigurationspakken .zip filen (WindowsDefenderATPOnboardingPackage.zip)

    1. Vælg **Indstillinger** **Onboarding-slutpunkter** \> (under **Enhedshåndtering**\>) i navigationsruden Microsoft 365 Defender portalen.
    1. Vælg Windows 10 eller Windows 11 som operativsystem.
    1. I feltet **Installationsmetode** skal du vælge VDI-onboardingscripts for ikke-faste slutpunkter.
    1. Klik på **Download pakke** , og gem filen .zip.

2. Udpak indholdet af den .zip fil til en delt, skrivebeskyttet placering, som enheden kan få adgang til. Du skal have en mappe med navnet **OptionalParamsPolicy** og filerne **WindowsDefenderATPOnboardingScript.cmd** og **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Brug Gruppepolitik administrationskonsol til at køre scriptet, når den virtuelle maskine starter

1. Åbn GPMC (Gruppepolitik Management Console), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. I Gruppepolitik Management Editor skal du gå til **Indstillinger for** \> **computerkonfiguration** \> **Kontrolpanelindstillinger**.

3. Højreklik på **Planlagte opgaver**, klik på **Ny**, og klik derefter på **Øjeblikkelig opgave** (mindst Windows 7).

4. I vinduet Opgave, der åbnes, skal du gå til fanen **Generelt** . Under **Sikkerhedsindstillinger** skal du klikke på **Skift bruger eller gruppe** og skrive SYSTEM. Klik på **Kontrollér navne,** og klik derefter på OK. NT AUTHORITY\SYSTEM vises som den brugerkonto, som opgaven kører som.

5. Vælg **Kør, om brugeren er logget på eller ej** , og markér afkrydsningsfeltet **Kør med de højeste rettigheder** .

6. Gå til fanen **Handlinger,** og klik på **Ny**. Kontrollér, at **Start et program** er markeret i feltet Handling. Angiv følgende:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Vælg derefter **OK** , og luk alle åbne GPMC-vinduer.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scenarie 3: Onboarding ved hjælp af administrationsværktøjer*

Hvis du planlægger at administrere dine maskiner ved hjælp af et administrationsværktøj, kan du onboarde enheder med Microsoft Endpoint Configuration Manager.

Du kan få flere oplysninger under [Onboard Windows enheder ved hjælp af Configuration Manager](configure-endpoints-sccm.md).

> [!WARNING]
> Hvis du planlægger at bruge [reference til regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md), skal du være opmærksom på, at reglen "[Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)", ikke bør bruges, fordi reglen ikke er kompatibel med administration via Microsoft Endpoint Configuration Manager. Reglen blokerer WMI-kommandoer, som Configuration Manager-klienten bruger til at fungere korrekt.

> [!TIP]
> Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Mærkning af dine maskiner, når du bygger dit gyldne billede

Som en del af onboarding kan du overveje at angive et computermærke for nemmere at differentiere AVD-maskiner i Microsoft Security Center. Du kan få flere oplysninger under [Tilføj enhedskoder ved at angive en værdi for registreringsdatabasenøglen](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Når du bygger dit gyldne billede, kan det også være en god idé at konfigurere de indledende beskyttelsesindstillinger. Du kan få flere oplysninger under [Andre anbefalede konfigurationsindstillinger](configure-endpoints-gp.md#other-recommended-configuration-settings).

Hvis du bruger FSlogix-brugerprofiler, anbefaler vi også, at du udelukker følgende filer fra always-on-beskyttelse:

**Udelad filer:**

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**Ekskluderingsprocesser:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Licenskrav

Bemærk om licensering: Når du bruger Windows enterprise-multisession, kan du, afhængigt af dine krav, vælge enten at have alle brugere licenseret via Microsoft Defender for Endpoint (pr. bruger), Windows Enterprise E5, Microsoft 365 Security eller Microsoft 365 E5 , eller få den virtuelle maskine licenseret via Microsoft Defender for Cloud.
Du kan finde licenskrav til Microsoft Defender for Endpoint på: [Licenskrav](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

Det er kun Microsoft Edge, der understøttes til webfiltrering i Windows 10 flere sessioner.

#### <a name="related-links"></a>Relaterede links

[Tilføj udeladelser for Defender for Endpoint via PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
