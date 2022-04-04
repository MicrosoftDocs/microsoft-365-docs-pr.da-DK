---
title: Onboard Windows-servere til Microsoft Defender for Endpoint-tjenesten
description: Onboard Windows-servere, så de kan sende sensordata til Microsoft Defender for Endpoint sensoren.
keywords: onboard server, server, 2012r2, 2016, 2019, server onboarding, enhedshåndtering, konfigurer Microsoft Defender for Endpoint-servere, onboard Microsoft Defender for Endpoint-servere, onboard Microsoft Defender for Endpoint-servere
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 14c759cd243b8da9f338b777e430d4de9f735fc1
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498907"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Onboard Windows-servere til Microsoft Defender for Endpoint-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- Windows Server 2012 R2
- Windows Server 2016
- Windows server Semi-Annual virksomhedskanal
- Windows Server 2019 og nyere
- Windows Server 2019 core edition
- Windows Server 2022
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Defender til Slutpunkt udvider understøttelsen til også at omfatte Windows Server-operativsystemet. Denne support giver problemfrit avanceret registrering af angreb og undersøgelsesfunktioner via Microsoft 365 Defender-konsollen. Understøttelse af Windows server giver mere indsigt i serveraktiviteter, dækning af kerne- og hukommelsesangreb og aktiverer svarhandlinger.

I dette emne beskrives det, hvordan du kan onboarde bestemte Windows til Microsoft Defender for Endpoint.

Du kan finde en vejledning til at downloade og bruge Windows Sikkerhed Baselines for Windows-servere [under Windows Sikkerhed Baselines](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Windows oversigt over onboarding af server

Du skal udføre følgende generelle trin for at kunne onboarde servere.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="En illustration af onboardingflow til Windows servere og Windows 10-enheder" lightbox="images/server-onboarding-tools-methods.png":::

**Windows Server 2012 R2 og Windows Server 2016 (Preview)**

>[!IMPORTANT]
> Du skal aktivere visningsfunktionerne i afsnittet Slutpunkter i Microsoft 365 Defender at bruge denne funktionalitet. Gå til [Microsoft 365 Defender > Indstillinger > slutpunkter > avancerede funktioner,](https://security.microsoft.com/preferences2/integration) og aktiver Funktioner til eksempelvisning.

- Download installations- og onboardingpakker
- Anvend installationspakken
- Følg onboardingtrinnene for det tilsvarende værktøj

**Windows Server Semi-Annual Enterprise-kanal og Windows Server 2019**

- Download onboardingpakken
- Følg onboardingtrinnene for det tilsvarende værktøj

>[!IMPORTANT]
>For at være berettiget til at købe Microsoft Defender for Endpoint Server SKU skal du allerede have købt et kombineret minimum af et af følgende, Windows E5/A5, Microsoft 365 E5/A5 eller Microsoft 365 E5 Sikkerhed-abonnementslicenser.  Du kan finde flere oplysninger om licenser i [produktvilkårene](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  



### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview"></a>Ny Windows server 2012 R2- og 2016-funktionalitet i den moderne samlede løsning (Preview)

Tidligere implementering af onboardingserveren Windows Server 2012 R2 og Windows Server 2016 krævede brug af Microsoft Monitoring Agent (AGENT).

Den nye samlede løsningspakke gør det nemmere at onboarde servere ved at fjerne afhængigheder og installationstrin. Desuden leveres denne samlede løsningspakke med følgende større forbedringer:

- [Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) med [næste generations beskyttelse](/microsoft-365/security/defender-endpoint/next-generation-protection) til Windows Server 2012 R2
- [Regler for reduktion af angrebsoverfladen (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection)
- [Styret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders)
- [Blokering af potentielt uønsket program (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Forbedrede registreringsfunktioner](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Udvidede svarfunktioner på](/microsoft-365/security/defender-endpoint/respond-machine-alerts) enheder og [filer](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [Slutpunktsregistrering og -svar i bloktilstand](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Live-svar](/microsoft-365/security/defender-endpoint/live-response)
- [Automatiseret undersøgelse og svar (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Beskyttelse mod tamper](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

Afhængigt af den server, du onboarder, installeres den samlede løsning Microsoft Defender Antivirus/eller Slutpunktsregistrering og -svar sensoren. Følgende tabel angiver, hvilken komponent der er installeret, og hvad der er indbygget som standard.

|Serverversion|AV|Slutpunktsregistrering og -svar|
|----|----|----|
|Windows Server 2012 R2 SP1|![Ja.](images/svg/check-yes.svg)|![Ja.](images/svg/check-yes.svg)|
|Windows Server 2016|Indbygget|![Ja.](images/svg/check-yes.svg)|
|Windows Server 2019 eller nyere|Indbygget|Indbygget|

Hvis du tidligere har onboardet dine servere ved hjælp af VEJLEDNINGEN, skal du følge vejledningen i [Serveroverførsel](server-migration.md) for at overføre til den nye løsning.

>[!NOTE]
>Mens denne metode til onboarding Windows Server 2012 R2 og Windows Server 2016 er i preview, kan du vælge at fortsætte med at bruge den tidligere onboardingmetode ved hjælp af Microsoft Monitoring Agent (RUDEN). Få mere at vide under [Installér og konfigurer slutpunkter ved hjælp af MANUELT](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

#### <a name="known-issues-and-limitations-on-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>Kendte problemer og begrænsninger for den nye, samlede løsningspakke til Windows Server 2012 R2 og 2016

Følgende oplysninger gælder for den nye samlede løsningspakke til Windows Server 2012 R2 og 2016:

- Sørg for, at kravene til forbindelsen som [angivet i Aktivér adgang Microsoft Defender for Endpoint url-adresser for tjenesten er](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) opfyldt. De svarer til dem for Windows Server 2019. 
- Vi undersøger et problem med Windows Server 2012 R2-forbindelse til skyen, når statisk TelemetryProxyServer bruges, og URL-adresser for tilbagekaldte certifikater ikke kan nås fra SYSTEM-kontokontekst. Den øjeblikkelige afhjælpning er enten at bruge en alternativ proxyindstilling, der giver en sådan forbindelse, eller at konfigurere den samme proxy via WinInet-indstillingen i SYSTEM-kontokontekst.
- Tidligere var det tilladt for OMS-/Log Analytics-gatewayen at levere forbindelse til Defender-skytjenester på Windows Server 2016 og nedenfor. Den nye løsning, f.eks. Microsoft Defender for Endpoint på Windows Server 2019, Windows Server 2022 og Windows 10, understøtter ikke denne gateway.

- På Windows Server 2016 skal du kontrollere, Microsoft Defender Antivirus er installeret, er aktiv og opdateret. Du kan downloade og installere den nyeste platformversion ved hjælp af Windows Update. Alternativt kan du downloade opdateringspakken manuelt fra [Microsoft Update-kataloget eller](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) fra [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).  
- På Windows Server 2012 R2 er der ingen brugergrænseflade til Microsoft Defender Antivirus. Desuden tillader brugergrænsefladen i Windows Server 2016 kun grundlæggende handlinger. Hvis du vil udføre handlinger på en enhed lokalt, skal [du se Microsoft Defender for Endpoint med PowerShell, WMI og MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). Derfor fungerer funktioner, der specifikt afhænger af brugerinteraktion, f.eks. hvor brugeren bliver bedt om at træffe en beslutning eller udføre en bestemt opgave, muligvis ikke som forventet. Det anbefales at deaktivere eller ikke aktivere brugergrænsefladen eller kræve brugerinteraktion på en administreret server, da det kan påvirke beskyttelse.
- Ikke alle regler for reduktion af angrebsoverfladen er tilgængelige på alle operativsystemer. Se [reglerne for reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules).
- Hvis du [vil aktivere netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection), kræves yderligere konfiguration:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  Desuden anbefales test af ydeevnen i dit miljø på maskiner med en stor mængde netværkstrafik, før du aktiverer denne funktion bredt. Du skal muligvis tage højde for yderligere ressourceforbrug.
- På Windows Server 2012 R2 udfyldes netværkshændelser muligvis ikke på tidslinjen. Dette problem kræver en Windows Update udgivet som en del af den månedlige opdatering [fra d. 12. oktober 2021 (KB5006714)](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e).
- Opgraderinger af operativsystemet understøttes ikke. Fjern derefter før opgradering.
- Automatisk udeladelse for *serverroller* understøttes ikke på Windows Server 2012 R2, men indbyggede udeladelsesforanstaltninger for operativsystemfiler er. Du kan finde flere oplysninger om at tilføje udeladelse i [Anbefalinger til virusscanning for virksomhedscomputere, der kører i øjeblikket understøttede versioner Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- Hvis du i øjeblikket vælger at offboarde og afinstallere den moderne, samlede løsning og tager den forrige OLE-baserede Slutpunktsregistrering og -svar-sensor i brug igen, `MsSenseS.exe` kan du støde på gentagne nedbrud. 

Du kan løse problemet ved at fjerne følgende registreringsdatabasenøgler, hvis de findes:
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\fdedb2b8-61e4-4a7e-8b15-abf214a08fcc`
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security\c60418cc-7e07-400f-ae3b-d521c5dbd96f`

Du kan bruge følgende kommandoer:

```cmd
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v fdedb2b8-61e4-4a7e-8b15-abf214a08fcc /f
reg delete HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Security /v c60418cc-7e07-400f-ae3b-d521c5dbd96f /f
```
Ingen genstart er påkrævet.


<a name="integration-with-azure-defender"></a>

## <a name="integration-with-microsoft-defender-for-cloud"></a>Integration med Microsoft Defender til skyen

Microsoft Defender for Endpoint integreres problemfrit med Microsoft Defender for Cloud. Du kan onboarde servere automatisk, få servere overvåget af Azure Defender til at blive vist i Defender til slutpunkt og udføre detaljerede undersøgelser som en Microsoft Defender for Cloud-kunde.

Du kan få mere at vide [under Integration med Microsoft Defender til cloud.](azure-server-integration.md)

> [!NOTE]
> For Windows Server 2012 R2 og 2016, der kører den moderne samlede prøveversion af løsningen, er integration med Microsoft Defender for Cloud/Microsoft Defender til servere til advarsel og automatiseret installation endnu ikke tilgængelig. Hvis du har mulighed for manuelt at installere den nye løsning på disse computere, vil der ikke blive vist nogen advarsler i Microsoft Defender for Cloud.

> [!NOTE]
> - Integrationen mellem Microsoft Defender for servere og Microsoft Defender for Endpoint er blevet udvidet til at understøtte Windows Server 2022, [Windows Server 2019 og Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).
> - Serverslutpunktovervågning, der udnytter denne integration, er deaktiveret for Office 365 GCC kunder.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 og Windows Server 2016

> [!NOTE]
> Mens denne metode til onboarding Windows Server 2012 R2 og Windows Server 2016 er i preview, kan du vælge at fortsætte med at bruge den tidligere onboardingmetode ved hjælp af Microsoft Monitoring Agent (RUDEN). Få mere at vide under [Installér og konfigurer slutpunkter ved hjælp af MANUELT](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma).

### <a name="prerequisites"></a>Forudsætninger

**Forudsætninger for Windows Server 2012 R2**

Hvis du har fuldt opdateret dine computere med den seneste [månedlige](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) opdateringspakke, er **der ingen** yderligere forudsætninger.

Installationsprogrammet kontrollerer, om følgende komponenter allerede er installeret via en opdatering:

- [Opdatering til kundeoplevelse og diagnosticeringstelemetri](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Opdatering til Universal C Runtime Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

**Forudsætninger for Windows Server 2016** 

Ud over at opdatere computeren fuldt ud med den seneste kumulative opdatering (LCU) skal du kontrollere, Microsoft Defender Antivirus er installeret, er aktiv og opdateret. Du kan downloade og installere den nyeste platformversion ved hjælp af Windows Update. Alternativt kan du downloade opdateringspakken manuelt fra [Microsoft Update-kataloget eller](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) fra [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64). 

> [!NOTE]
> For at kunne opdatere den indbyggede version af Windows Defender, som har et versionsnummer, der starter med 4.10, til den nyeste tilgængelige platform, skal der være anvendt en serviceringsstabling samt den seneste kumulative opdatering (LCU) lig med eller senere end d. 20. september 2018 – KB4457127 (OS Build 14393.2515).

**Forudsætninger for at køre med tredjepartssikkerhedsløsninger**

Hvis du har til hensigt at bruge en tredjeparts antimalwareløsning, skal du køre Microsoft Defender Antivirus i passiv tilstand. Du skal huske at indstille til passiv tilstand under installationen og onboardingprocessen.

**Ny opdateringspakke til Microsoft Defender for Endpoint på Windows Server 2012 R2 og 2016**

For at modtage regelmæssige produktforbedringer og løsninger til Slutpunktsregistrering og -svar sensorkomponenten skal du sikre dig, Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) bliver anvendt eller godkendt. Desuden kan du få mere at vide om at holde sikkerhedskomponenter opdateret [under Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

### <a name="onboarding-steps-summary"></a>Oversigt over onboardingtrin

- TRIN 1: [Download installations- og onboardingpakkerne](#step-1-download-installation-and-onboarding-packages)
- TRIN 2: [Anvend installations- og onboardingpakken](#step-2-apply-the-installation-and-onboarding-package)
- TRIN 3: [Fuldfør onboardingtrinnene](#step-3-complete-the-onboarding-steps) 


### <a name="step-1-download-installation-and-onboarding-packages"></a>TRIN 1: Download installations- og onboardingpakker

Du skal downloade både installations- **og** **onboardingpakkerne** fra portalen.

> [!div class="mx-imgBorder"]
> ![Billede af onboardingdashboard](images/install-agent-onboard.png)


   > [!NOTE]
   > På Windows Server 2012R2 installeres Microsoft Defender Antivirus af installationspakken og vil være aktiv, medmindre du indstiller den til passiv tilstand. På Windows Server 2016 skal Microsoft Defender Antivirus være installeret som en funktion (se Skift til [MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) først og være fuldt opdateret, før du fortsætter med installationen.
   > 
   > Hvis du kører en ikke-Microsoft-antimalwareløsning, skal du inden installationen føje udeladelse for Microsoft Defender Antivirus (fra denne liste over [Microsoft Defender Processes på fanen Defender Processes](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)) til den løsning, der ikke er Fra Microsoft.  Det anbefales også at føje sikkerhedsløsninger, der ikke er Microsoft, til listen til udelukkelse af Defender Antivirus.


**Installationspakken indeholder** en MSI-fil, der installerer Microsoft Defender for Endpoint agent.

**Onboardingpakken** indeholder følgende filer:

- `OptionalParamsPolicy` - indeholder den indstilling, der aktiverer indsamling af eksempler
- `WindowsDefenderATPOnboardingScript.cmd` - indeholder onboardingscriptet

Brug følgende trin til at downloade pakkerne: 

1. I Microsoft 365 Defender skal du gå **til Indstillinger > Enhedshåndtering > Onboarding**.

2. Vælg **Windows Server 2012 R2 og 2016**.

3. Vælg **Download installationspakke** , og gem .msi fil. 
 
4. Vælg **Download onboardingpakke** , og gem .zip fil.

5. Installer installationspakken ved hjælp af en af indstillingerne for at installere Microsoft Defender Antivirus. Installationen kræver administrative tilladelser.



### <a name="step-2-apply-the-installation-and-onboarding-package"></a>TRIN 2: Anvend installations- og onboardingpakken
I dette trin skal du installere de komponenter til forebyggelse og registrering, der kræves, før du tager enheden i Microsoft Defender for Endpoint-skymiljø for at forberede computeren til onboarding. Sørg for [, at alle](#prerequisites) forudsætninger er opfyldt. 

   > [!NOTE]
   > Microsoft Defender Antivirus installeres og vil være aktiv, medmindre du indstiller den til passiv tilstand. 

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Indstillinger for installation af Microsoft Defender for Endpoint pakker

I forrige afsnit hentede du en installationspakke. Installationspakken indeholder installationsprogrammet for alle Microsoft Defender for Endpoint komponenter. 

Du kan bruge en af følgende indstillinger til at installere agenten:
- [Installér ved hjælp af kommandolinjen](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Installér ved hjælp af et script](#install-microsoft-defender-for-endpoint-using-a-script)
- [Anvend installations- og onboardingpakker ved hjælp af Gruppepolitik](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Installér Microsoft Defender For Endpoint ved hjælp af kommandolinjen
Brug installationspakken fra det forrige trin for at installere Microsoft Defender for Endpoint. 


Kør følgende kommando for at installere Microsoft Defender for Endpoint:

```console
Msiexec /i md4ws.msi /quiet
```

Hvis du vil fjerne installationen, skal du først sikre dig, at computeren er slukket ved hjælp af det relevante offboarding-script. Brug derefter Kontrolpanel \> programmer \> og funktioner til at udføre fjernelsen.

Alternativt kan du køre følgende kommando for at fjerne Microsoft Defender for Endpoint:

```console
Msiexec /x md4ws.msi /quiet
```

Du skal bruge den samme pakke, du brugte til installation for at få ovenstående kommando til at lykkes.

Parameteren `/quiet` undertrykker alle meddelelser.

> [!NOTE]
> Microsoft Defender Antivirus går ikke automatisk i passiv tilstand. Du kan vælge at indstille Microsoft Defender Antivirus til at køre i passiv tilstand, hvis du kører en løsning, der ikke er Microsoft-antivirus/antimalware. For kommandolinjeinstallationer indstiller den valgfrie `FORCEPASSIVEMODE=1` straks Microsoft Defender Antivirus til Passiv tilstand for at undgå forstyrrelser. For at sikre at Defender Antivirus forbliver i passiv tilstand efter onboarding for at understøtte funktioner som f.eks. Slutpunktsregistrering og -svar Block, skal du indstille registreringsdatabasenøglen "ForceDefenderPassiveMode".

Understøttelse af Windows server giver mere indsigt i serveraktiviteter, dækning af kerne- og hukommelsesangreb og aktiverer svarhandlinger.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Installere Microsoft Defender for Endpoint ved hjælp af et script

Du kan bruge [installationsprogrammets script](server-migration.md#installer-script) til at automatisere installation, fjernelse af installation og onboarding. Du kan finde flere oplysninger i vejledningen i det følgende afsnit for at bruge scriptet Gruppepolitik.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Anvend installations- Microsoft Defender for Endpoint onboardingpakker ved hjælp af gruppepolitik

1. Opret en gruppepolitik: <br> Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)GPMC), højreklik på de **Gruppepolitik,** du vil konfigurere, og klik på **Ny**. Skriv navnet på det nye gruppepolitikobjekt i dialogboksen, der vises, og klik på **OK**.

2. Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

3. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration** **og derefter** Indstillinger og **derefter indstillinger for Kontrolpanel**.

4. Højreklik på Planlagte **opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave (mindst Windows 7)**.

5. I vinduet **Opgave** , der åbnes, skal du gå **til fanen** Generelt. Klik **på Skift bruger** **eller gruppe under Sikkerhedsindstillinger, og** skriv SYSTEM, og klik derefter **på Kontrollér navne** og **OK**. NT AUTHORITY\SYSTEM vises som den brugerkonto, opgaven kører som.

6. Vælg **Kør, om brugeren er logget på eller** ej, **og markér afkrydsningsfeltet Kør med højeste** rettigheder.

7. Skriv et velegnet navn til den planlagte opgave i feltet Navn (f.eks. Defender til slutpunktsinstallation).

8. Gå til fanen **Handlinger** , og vælg **Ny...** Sørg for **, at Start et** program er markeret i **feltet** Handling. [Installationsprogrammets script](server-migration.md#installer-script) håndterer installationen og udfører straks onboardingtrinnet, når installationen er fuldført. Vælg *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* angiv derefter argumenterne:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```  

     >[!NOTE]
    >Hvis du skal foretage fejlfinding af problemer med installation af agent, skal du føje "-etl-log" til install.ps1 scriptparametre.
    >
    >Den anbefalede indstilling for eksekveringspolitik er `Allsigned`. Dette kræver, at du importerer scriptens signeringscertifikat til publishere, der er tillid til, på den lokale computer, hvis scriptet kører som SYSTEM på slutpunktet.

    Erstat \\servername-or-dfs-space\share-name med UNC-stien ved hjælp af filserverens fulde domænenavn (FQDN) for den *delteinstall.ps1* fil. Installationspakken skal md4ws.msi placeres i den samme mappe.  Sørg også for, at tilladelserne for UNC-stien giver læseadgang til den computerkonto, der installerer platformen.

   

    For scenarier, hvor Microsoft Defender Antivirus skal findes sammen med ikke-Microsoft-antimalwareløsninger, skal du tilføje parameteren $Passive at angive passiv tilstand under installationen.

9. Vælg **OK,** og luk alle åbne GPMC-vinduer.

10. Hvis du vil knytte gruppepolitikobjektet til en organisationsenhed, skal du højreklikke og vælge **Sammenkæd et eksisterende gruppepolitikobjekt**. I dialogboksen, der vises, skal du vælge det Gruppepolitik objekt, du vil sammenkæde. Klik på **OK**.

Du kan finde flere konfigurationsindstillinger under [Konfigurer eksempel på samlingsindstillinger](configure-endpoints-gp.md#configure-sample-collection-settings) [og Andre anbefalede konfigurationsindstillinger](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>TRIN 3: Fuldfør onboardingtrinnene

Følgende trin er kun gældende, hvis du bruger en tredjeparts antimalwareløsning. Du skal anvende følgende Microsoft Defender Antivirus passive tilstand. Kontrollér, at det er konfigureret korrekt:

1. Angiv følgende post i registreringsdatabasen:
    - Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Navn: `ForceDefenderPassiveMode`
    - Skriv: `REG_DWORD`
    - Værdi: `1`

       :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="Bekræftelsesresultat for passiv tilstand" lightbox="images/atp-verify-passive-mode.png":::
> [!IMPORTANT]
>
> - Når du bruger Microsoft Defender for Cloud til at overvåge servere, oprettes automatisk en Defender for Endpoint-lejer (i USA for amerikanske brugere, i EU for europæiske brugere og i Storbritannien for brugere i Storbritannien).
Data, der indsamles af Defender til Slutpunkt, gemmes på lejerens geoplacering, som identificeret under klargøring.
> - Hvis du bruger Defender til slutpunkt, før du bruger Microsoft Defender til skyen, gemmes dine data på den placering, du angav, da du oprettede din lejer, også selvom du integrerer med Microsoft Defender for Cloud på et senere tidspunkt.
> - Når det er konfigureret, kan du ikke ændre den placering, hvor dine data er gemt. Hvis du vil flytte dine data til en anden placering, skal du kontakte Microsoft Support for at nulstille lejeren.
> - Onboarding-pakken til Windows Server 2019 og Windows Server 2022 til og Microsoft Endpoint Manager i øjeblikket et script. Du kan finde flere oplysninger om, hvordan du installerer scripts Configuration Manager i [Pakker og programmer Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).
> - Et lokalt script er egnet til en koncept proof of concept, men bør ikke bruges til produktionsinstallation. Til en produktionsinstallation anbefaler vi, at du bruger Gruppepolitik eller Microsoft Endpoint Configuration Manager.



## <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise-kanal Windows Server 2019 og Windows Server 2022

Onboarding-pakken til Windows Server 2019 og Windows Server 2022 til og Microsoft Endpoint Manager i øjeblikket med et script. Du kan finde flere oplysninger om, hvordan du installerer scripts Configuration Manager i [Pakker og programmer Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).

### <a name="download-package"></a>Download pakke

1. I Microsoft 365 Defender skal du gå **til Indstillinger > Enhedshåndtering > Onboarding**.

2. Vælg **Windows Server 1803 og 2019**.

3. Vælg **Download pakke**. Gem den som WindowsDefenderATPOnboardingPackage.zip.

4. Følg trinnene i sektionen [Fuldfør onboardingtrinnene](#step-3-complete-the-onboarding-steps) .


## <a name="verify-the-onboarding-and-installation"></a>Bekræfte onboarding og installation

Kontrollér, Microsoft Defender Antivirus og Microsoft Defender for Endpoint kører.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

> [!NOTE]
> Kørsel Microsoft Defender Antivirus er ikke påkrævet, men det anbefales. Hvis et andet antivirusleverandørprodukt er den primære løsning til slutpunktsbeskyttelse, kan du køre Defender Antivirus i passiv tilstand. Du kan kun bekræfte, at passiv tilstand er aktiveret, når du har bekræftet Microsoft Defender for Endpoint sensoren (SENSE) kører.

1. Kør følgende kommando for at bekræfte, at Microsoft Defender Antivirus er installeret:

    >[!NOTE]
    >Dette trin til verifcation er kun påkrævet, hvis du bruger Microsoft Defender Antivirus som din aktive antimalwareløsning.

    `sc.exe query Windefend`


    Hvis resultatet er "Den angivne tjeneste findes ikke som en installeret tjeneste", skal du installere Microsoft Defender Antivirus. 


    Du kan finde oplysninger om, hvordan du bruger Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus på dine Windows-servere, under Brug Gruppepolitik-indstillinger til at konfigurere og [administrere Microsoft Defender Antivirus ](use-group-policy-microsoft-defender-antivirus.md).

2. Kør følgende kommando for at bekræfte, at Microsoft Defender for Endpoint kører:

    `sc.exe query sense`

    Resultatet skal vise, at det kører. Hvis du støder på problemer med onboarding, skal du [se Fejlfinding af onboarding](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Kør en registreringstest

Følg trinnene i Kør [en registreringstest på en nyligt onboardet](run-detection-test.md) enhed for at bekræfte, at serveren rapporterer til Defender for Endpoint-tjenesten.

## <a name="next-steps"></a>Næste trin

Når onboardingenheder er blevet installeret på tjenesten, skal du konfigurere de enkelte komponenter i Microsoft Defender for Endpoint. Følg [indføringsrækkefølgen](prepare-deployment.md#adoption-order) for at blive vejledt om aktivering af de forskellige komponenter.

## <a name="offboard-windows-servers"></a>Offboard Windows-servere

Du kan offboard Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 og Windows Server 2019 Core-version på samme metode, der er tilgængelig for Windows 10-klientenheder.

- [Offboard-enheder, der bruger Gruppepolitik](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Offboard-enheder, der bruger Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Offboard og monitor enheder ved hjælp af Mobile Enhedshåndtering værktøjer](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Offboard-enheder, der bruger et lokalt script](configure-endpoints-script.md#offboard-devices-using-a-local-script)

For Windows serverversioner har du to muligheder for at offboarde Windows servere fra tjenesten:

- Fjern  ÆLDRE-agenten
- Fjern arbejdsområdekonfigurationen for Defender til Slutpunkt

> [!NOTE]
> Disse offboardinginstruktioner til andre Windows-serverversioner gælder også, hvis du kører den forrige Microsoft Defender for Endpoint til Windows Server 2016 og Windows Server 2012 R2, der kræver OVERENSSTEMMELSE. Vejledning til at overføre til den nye samlede løsning findes i [Scenarier for serveroverførsel Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Relaterede emner

- [Onboard tidligere versioner af Windows](onboard-downlevel.md)
- [Onboard Windows 10 enheder](configure-endpoints.md)
- [Onboard ikke-Windows enheder](configure-endpoints-non-windows.md)
- [Konfigurere indstillinger for proxy og internetforbindelse](configure-proxy-internet.md)
- [Kør en registreringstest på en nyligt onboardet Defender til slutpunktsenhed](run-detection-test.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md)
