---
title: Onboard Windows enheder med flere sessioner i Azure Virtual Desktop
description: Læs mere i denne artikel om onboarding Windows flersessionsenheder i Azure Virtual Desktop
keywords: Azure Virtual Desktop, WVD, microsoft defender, slutpunkt, onboard
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
ms.openlocfilehash: d97326987af49b9bac44b3578884c72d756d5595
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596895"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>Onboard Windows enheder med flere sessioner i Azure Virtual Desktop

6 minutter at læse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows flersessioner, der kører på Azure Virtual Desktop (AVD)

Microsoft Defender til Slutpunkt understøtter overvågning af både VDI- og Azure Virtual Desktop-sessioner. Afhængigt af din organisations behov kan det være nødvendigt at implementere VDI- eller Azure Virtual Desktop-sessioner for at hjælpe dine medarbejdere med at få adgang til virksomhedens data og apps fra en ikke-administreret enhed, fjernplacering eller lignende scenarie. Med Microsoft Defender til slutpunkt kan du overvåge disse virtuelle maskiner for unormal aktivitet.

## <a name="before-you-begin"></a>Før du begynder

Gør dig bekendt med [overvejelserne i forbindelse med en ikke-permanent VDI](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). Azure [Virtual Desktop](/azure/virtual-desktop/overview) giver ikke mulighed for vedholdende brug, men der er måder at bruge et gyldent Windows-billede, der kan bruges til at klargøre nye værter og geninstallere maskiner. Dette øger synligheden i miljøet og påvirker dermed, hvad opslag oprettes og vedligeholdes i Microsoft Defender til Endpoint-portalen, hvilket potentielt reducerer synligheden for dine sikkerhedsanalytikere.

> [!NOTE]
> Afhængigt af dit valg af onboardingmetode kan enheder vises i Microsoft Defender til Endpoint-portalen som enten:
>
> - Enkelt post for hver virtuel computer
> - Flere poster for hver virtuelle skrivebord

Microsoft anbefaler onboarding Azure Virtual Desktop som en enkelt post pr. virtuel skrivebord. Dette sikrer, at undersøgelsesoplevelsen i Microsoft Defender for Endpoint-portalen er i forbindelse med én enhed, der er baseret på computernavnet. Organisationer, der ofte sletter og geninstallerer WVD-værter, bør på det kraftigste overveje at bruge denne metode, da det forhindrer, at flere objekter til den samme computer oprettes på Microsoft Defender for Endpoint-portalen. Dette kan føre til forvirring, når der undersøges hændelser. I forbindelse med testmiljøer eller ikke-flygtige miljøer kan du vælge en anden.

Microsoft anbefaler, at du føjer onboardingscriptet Microsoft Defender for Endpoint til det gyldne billede af WVD. På denne måde kan du være sikker på, at dette onboardingscript kører straks ved første start. Det udføres som et startscript ved første start på alle WVD-maskiner, der er klargjort fra det gyldne billede i WVD. Men hvis du bruger et af galleribillederne uden ændring, skal du placere scriptet på en delt placering og ringe til det fra enten en lokal gruppepolitik eller en domænegruppepolitik.

> [!NOTE]
> Placeringen og konfigurationen af VDI-onboardingstartscriptet på det gyldne WVD-billede konfigurerer det som et startscript, der kører, når WVD'en starter. Det anbefales ikke **at** anvende det faktiske gyldne WVD-billede. En anden overvejelse er den metode, der bruges til at køre scriptet. Den bør køre så tidligt i opstarts-/klargøringsprocessen som muligt for at reducere tiden mellem den maskine, der bliver tilgængelig til at modtage sessioner og onboarding af enheden til tjenesten. Under scenarierne 1 og 2 skal du tage højde for dette.

### <a name="scenarios"></a>Scenarier

Der er flere måder at onboarde en WVD-værtscomputer på:

- Kør scriptet i det gyldne billede (eller fra en delt placering) under opstart.
- Brug et administrationsværktøj til at køre scriptet.
- Integration [med Microsoft Defender til skyen](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*Scenarie 1: Brug af lokal gruppepolitik*

Dette scenarie kræver, at scriptet anbringes i et gyldent billede og anvender lokal gruppepolitik til at køre tidligt i startprocessen.

Brug vejledningen i [Onboarding af de ikke-permanente VDI-enheder (Virtual Desktop Infrastructure](configure-endpoints-vdi.md)).

Følg vejledningen for en enkelt post for hver enhed.

#### <a name="scenario-2-using-domain-group-policy"></a>*Scenarie 2: Brug af domænegruppepolitik*

Dette scenarie anvender et centralt placeret script og kører det ved hjælp af en domænebaseret gruppepolitik. Du kan også placere manuskriptet i det gyldne billede og køre det på samme måde.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>Download den WindowsDefenderATPOnboardingPackage.zip fil fra Windows 365 Defender-portalen

1. Åbn VDI-konfigurationspakken .zip filen (WindowsDefenderATPOnboardingPackage.zip)

    1. I **navigationsruden** Microsoft 365 Defender på portalen skal **du Indstillinger** \> slutpunkter \> **onboarding** (under **Enhedshåndtering**).
    1. Vælg Windows 10 eller Windows 11 som operativsystem.
    1. I feltet **Installationsmetode** skal du vælge VDI-onboardingscripts for ikke-permanente slutpunkter.
    1. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enheden. Du skal have en mappe med **navnet OptionalParamsPolicy** og filerne **WindowsDefenderATPOnboardingScript.cmd** **ogOnboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>Brug Gruppepolitik administrationskonsollen til at køre scriptet, når den virtuelle maskine starter

1. Åbn Gruppepolitik Administrationskonsol (GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

2. I administrationseditoren Gruppepolitik skal du gå til **Indstillinger for computerkonfiguration** \> **i** \> **Kontrolpanelindstillinger**.

3. Højreklik på Planlagte **opgaver**, klik på **Ny**, og klik derefter på **Øjeblikkelig** opgave (mindst Windows 7).

4. I vinduet Opgave, der åbnes, skal du gå **til fanen** Generelt. Under **Sikkerhedsindstillinger skal** du **klikke på Skift bruger eller Gruppe** og skrive SYSTEM. Klik **på Kontrollér navne,** og klik derefter på OK. NT AUTHORITY\SYSTEM vises som den brugerkonto, opgaven kører som.

5. Vælg **Kør, om brugeren er logget på eller** ej, **og markér afkrydsningsfeltet Kør med højeste** rettigheder.

6. Gå til fanen **Handlinger,** og klik på **Ny**. Sørg for **, at Start et** program er markeret i feltet Handling. Angiv følgende:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   Vælg derefter **OK,** og luk alle åbne GPMC-vinduer.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*Scenarie 3: Onboarding ved hjælp af administrationsværktøjer*

Hvis du planlægger at administrere dine maskiner ved hjælp af et administrationsværktøj, kan du onboarde enheder med Microsoft Endpoint Configuration Manager.

Få mere at vide under [Onboard Windows enheder, der bruger Konfigurationsstyring](configure-endpoints-sccm.md).

> [!WARNING]
> Hvis du planlægger at bruge reference til reduktionsregler for angrebsoverfladen[, skal](attack-surface-reduction-rules-reference.md) du bemærke, at reglen "Bloker procesoprettelser, der stammer fra [PSExec- og WMI-kommandoer](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)", ikke skal bruges, fordi denne regel ikke er kompatibel med administration via Microsoft Endpoint Configuration Manager. Reglen blokerer WMI-kommandoer, som Konfigurationsstyring klient bruger til at fungere korrekt.

> [!TIP]
> Efter onboarding af enheden kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>Mærkning af dine maskiner, når du opbygger dit gyldne billede

Som en del af din onboarding kan du overveje at angive et maskinmærke for nemmere at kunne skelne mellem WVD-computere i Microsoft Security Center. Få mere at vide under Tilføj [enhedsmærker ved at angive en nøgleværdi i registreringsdatabasen](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Når du opbygger dit gyldne billede, kan det også være en god ide at konfigurere de indledende beskyttelsesindstillinger. Du kan finde flere oplysninger [under Andre anbefalede konfigurationsindstillinger](configure-endpoints-gp.md#other-recommended-configuration-settings).

Hvis du bruger FSlogix-brugerprofiler, anbefaler vi desuden, at du udelader følgende filer fra altid-on-beskyttelse:

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

**Ekskluder processer:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>Licenskrav

Bemærk om licenser: Når du bruger Windows Enterprise-multisession, kan du, afhængigt af dine krav, vælge enten at have alle brugere licenseret via Microsoft Defender til slutpunkt (pr. bruger), Windows Enterprise E5, Microsoft 365 Security eller Microsoft 365 E5 eller få VM licenseret via Microsoft Defender for Cloud.
Licenskrav for Microsoft Defender til slutpunkt kan findes på: [Licenskrav](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

Kun Microsoft Edge understøttes til webfiltrering i Windows 10 eller flere sessioner.

#### <a name="related-links"></a>Relaterede links

[Tilføj udeladelse for Defender til slutpunkt via PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
