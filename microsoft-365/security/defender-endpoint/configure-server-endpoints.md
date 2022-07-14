---
title: Onboarde Windows-servere til Microsoft Defender for Endpoint-tjenesten
description: Onboarde Windows-servere, så de kan sende sensordata til den Microsoft Defender for Endpoint sensor.
keywords: onboard server, server, 2012r2, 2016, 2019, server onboarding, enhedshåndtering, konfigurer Microsoft Defender for Endpoint servere, onboarde Microsoft Defender for Endpoint servere, onboarde Microsoft Defender for Endpoint servere
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
ms.openlocfilehash: ac40dcc986dfb4c66b9030cdf8c22ebabe1bd3d2
ms.sourcegitcommit: 5463d4518c269d9c125bb66836a780df292b4854
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66795416"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Onboarde Windows-servere til Microsoft Defender for Endpoint-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- Windows Server 2012 R2
- Windows Server 2016
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 og nyere
- Windows Server 2019 Core Edition
- Windows Server 2022
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Defender for Endpoint udvider understøttelsen til også at omfatte Windows Server-operativsystemet. Denne understøttelse leverer problemfrit avancerede funktioner til registrering og undersøgelse af angreb via Microsoft 365 Defender-konsollen. Understøttelse af Windows Server giver bedre indsigt i serveraktiviteter, dækning af registrering af kerne- og hukommelsesangreb og aktiverer svarhandlinger.

I dette emne beskrives det, hvordan du onboarder specifikke Windows-servere for at Microsoft Defender for Endpoint.

Du kan finde en vejledning i, hvordan du downloader og bruger Windows Sikkerhed Baselines til Windows-servere, [under Windows Sikkerhed Baselines](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Oversigt over onboarding af Windows Server

Du skal udføre følgende generelle trin for at kunne onboarde servere.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="En illustration af onboardingflow til Windows-servere og Windows 10 enheder" lightbox="images/server-onboarding-tools-methods.png":::

## <a name="integration-with-microsoft-defender-for-servers"></a>Integration med Microsoft Defender for Servers

Microsoft Defender for Endpoint integreres problemfrit med Microsoft Defender for Servers. Du kan onboarde servere automatisk, få servere overvåget af Microsoft Defender for Cloud vist i Defender for Endpoint og udføre detaljerede undersøgelser som Microsoft Defender for Cloud-kunde.

Du kan få flere oplysninger under [Integration med Microsoft Defender for Cloud](azure-server-integration.md).

> [!NOTE]
> Til Windows Server 2012 R2 og 2016, der kører den moderne unified løsning, kan du enten manuelt installere/opgradere den nye løsning på disse computere eller bruge integrationen til automatisk at installere eller opgradere servere, der er omfattet af din respektive Microsoft Defender for Server-plan. Du kan finde flere oplysninger om, hvordan du skifter i [Beskyt dine slutpunkter med Defender for Clouds integrerede EDR-løsning: Microsoft Defender for Endpoint](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows).
> - Når du bruger Microsoft Defender for Cloud til at overvåge servere, oprettes der automatisk en Defender for Endpoint-lejer (i USA for amerikanske brugere, i EU for europæiske brugere og i Storbritannien for brugere i Storbritannien).
Data, der indsamles af Defender for Endpoint, gemmes på lejerens geo-placering som identificeret under klargøring.
> - Hvis du bruger Defender for Endpoint, før du bruger Microsoft Defender for Cloud, gemmes dine data på den placering, du angav, da du oprettede din lejer, selvom du integrerer med Microsoft Defender for Cloud på et senere tidspunkt.
> - Når dataene er konfigureret, kan du ikke ændre den placering, hvor dine data er gemt. Hvis du har brug for at flytte dine data til en anden placering, skal du kontakte Microsoft Support for at nulstille lejeren.
> - Integrationen mellem Microsoft Defender til servere og Microsoft Defender for Endpoint er blevet udvidet til at understøtte Windows Server 2022, [Windows Server 2019 og Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - Overvågning af serverslutpunkt, der udnytter denne integration, er blevet deaktiveret for Office 365 GCC-kunder.

**Windows Server 2012 R2 og Windows Server 2016**:

- Download installations- og onboardingpakker
- Anvend installationspakken
- Følg onboardingtrinnene for det tilsvarende værktøj

**Windows Server Semi-Annual Enterprise Channel og Windows Server 2019**:

- Download onboardingpakken
- Følg onboardingtrinnene for det tilsvarende værktøj

>[!IMPORTANT]
>For at være berettiget til at købe Microsoft Defender for Endpoint Server SKU skal du allerede have købt et kombineret minimum af følgende, Windows E5/A5, Microsoft 365 E5/A5 eller Microsoft 365 E5 Sikkerhed abonnementslicenser.  Du kan få flere oplysninger om licenser under [Produktvilkår](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution"></a>Ny Windows Server 2012 R2- og 2016-funktionalitet i den moderne samlede løsning

Den tidligere implementering af onboarding af Windows Server 2012 R2 og Windows Server 2016 krævede brug af Microsoft Monitoring Agent (MMA).

Den nye samlede løsningspakke gør det nemmere at onboarde servere ved at fjerne afhængigheder og installationstrin. Desuden leveres denne samlede løsningspakke med følgende større forbedringer:

- [Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) med [næste generations beskyttelse](/microsoft-365/security/defender-endpoint/next-generation-protection) af Windows Server 2012 R2
- [ASR-regler (Attack Surface Reduction)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection)
- [Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders)
- [Potentielt uønsket programblokering (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Forbedrede registreringsfunktioner](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Udvidede svarfunktioner](/microsoft-365/security/defender-endpoint/respond-machine-alerts) på enheder og [filer](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR i bloktilstand](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Live-svar](/microsoft-365/security/defender-endpoint/live-response)
- [Automatiseret undersøgelse og svar (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Ændringsbeskyttelse](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

Afhængigt af den server, du onboarder, installerer den samlede løsning Microsoft Defender Antivirus og/eller EDR-sensoren. I følgende tabel kan du se, hvilken komponent der er installeret, og hvad der som standard er indbygget.

|Serverversion|AV|EDR|
|----|----|----|
|Windows Server 2012 R2 SP1|![Ja.](images/svg/check-yes.svg)|![Ja.](images/svg/check-yes.svg)|
|Windows Server 2016|Indbygget|![Ja.](images/svg/check-yes.svg)|
|Windows Server 2019 eller nyere|Indbygget|Indbygget|

Hvis du tidligere har onboardet dine servere ved hjælp af MMA, skal du følge vejledningen i [Serveroverførsel](server-migration.md) for at migrere til den nye løsning.

#### <a name="known-issues-and-limitations-in-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>Kendte problemer og begrænsninger i den nye, samlede løsningspakke til Windows Server 2012 R2 og 2016

Følgende specifikke oplysninger gælder for den nye samlede løsningspakke til Windows Server 2012 R2 og 2016:

- Sørg for, at forbindelseskravene som angivet i [Aktivér adgang til Microsoft Defender for Endpoint tjeneste-URL-adresser på proxyserveren](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) er opfyldt. De svarer til dem for Windows Server 2019.
- Vi har identificeret et problem med Windows Server 2012 R2-forbindelse til skyen, når der bruges statisk telemetryProxyServer, **og** URL-adresserne på listen over tilbagekaldte certifikater (CRL) kan ikke nås fra SYSTEM-kontokonteksten. Den øjeblikkelige afhjælpning er enten at bruge en alternativ proxyindstilling ("hele systemet"), der leverer en sådan forbindelse, eller konfigurere den samme proxy via indstillingen WinInet på SYSTEM-kontokonteksten.
Alternativt kan du bruge instruktionerne i [Løsning på et kendt problem med TelemetryProxyServer på frakoblede computere](#workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines) for at installere et certifikat som en midlertidig løsning.
- Tidligere var brugen af Microsoft Monitoring Agent (MMA) på Windows Server 2016 og nedenfor tilladt for OMS/Log Analytics-gatewayen til at levere forbindelse til Defender-cloudtjenester. Den nye løsning, f.eks. Microsoft Defender for Endpoint på Windows Server 2019, Windows Server 2022 og Windows 10, understøtter ikke denne gateway.
- På Windows Server 2016 skal du kontrollere, at Microsoft Defender Antivirus er installeret, er aktiv og opdateret. Du kan downloade og installere den nyeste platformversion ved hjælp af Windows Update. Du kan også hente opdateringspakken manuelt fra [Microsoft Update-kataloget](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) eller fra [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).
- På Windows Server 2012 R2 er der ingen brugergrænseflade til Microsoft Defender Antivirus. Derudover tillader brugergrænsefladen på Windows Server 2016 kun grundlæggende handlinger. Hvis du vil udføre handlinger på en enhed lokalt, skal du se [Administrer Microsoft Defender for Endpoint med PowerShell, WMI og MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). Derfor fungerer funktioner, der specifikt er afhængige af brugerinteraktion, f.eks. hvor brugeren bliver bedt om at træffe en beslutning eller udføre en bestemt opgave, muligvis ikke som forventet. Det anbefales at deaktivere eller ikke aktivere brugergrænsefladen eller kræve brugerinteraktion på en administreret server, da det kan påvirke beskyttelsesfunktionerne.
- Det er ikke alle regler for reduktion af angrebsoverfladen, der er tilgængelige på alle operativsystemer. Se [ASR-regler (Attack Surface Reduction).](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- Yderligere konfiguration er påkrævet for at aktivere [Netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection):
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  På maskiner med en stor mængde netværkstrafik anbefales det desuden på det kraftigste at teste ydeevnen i dit miljø, før du aktiverer denne funktion bredt. Du skal muligvis tage højde for yderligere ressourceforbrug.
- På Windows Server 2012 R2 udfyldes netværkshændelser muligvis ikke på tidslinjen. Dette problem kræver en Windows Update udgivet som en del af den [månedlige akkumulering fra 12. oktober 2021 (KB5006714)](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e).
- Opgraderinger af operativsystemet understøttes ikke. Fjern derefter Offboard, før du opgraderer.
- Automatiske udeladelser for **serverroller** understøttes ikke på Windows Server 2012 R2. Indbyggede undtagelser for operativsystemfiler er dog. Du kan få flere oplysninger om tilføjelse af udeladelser under [Anbefalinger til virusscanning for Enterprise-computere, der kører aktuelt understøttede versioner af Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- På maskiner, der er blevet opgraderet fra den forrige MMA-baserede løsning, og EDR-sensoren er en (prøveversion) version, der er ældre end 10.8047.22439.1056, kan fjernelse og gendannelse tilbage til den MMA-baserede løsning føre til nedbrud. Hvis du bruger sådan en prøveversion, skal du opdatere ved hjælp af KB5005292.
- Hvis du vil udrulle og onboarde den nye løsning ved hjælp af Microsoft Endpoint Manager, skal du i øjeblikket oprette en pakke. Du kan få flere oplysninger om, hvordan du installerer programmer og scripts i Configuration Manager, [under Pakker og programmer i Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs). MECM 2107 med hotfix-akkumulering eller nyere er påkrævet for at understøtte administration af politikkonfiguration ved hjælp af noden Endpoint Protection.

## <a name="workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines"></a>Løsning på et kendt problem med TelemetryProxyServer på frakoblede maskiner

Problembeskrivelse: Når du bruger indstillingen TelemetryProxyServer til at angive en proxy, der skal bruges af EDR-komponenten i Microsoft Defender for Endpoint, medfører et manglende mellemliggende certifikat, at EDR-sensoren ikke kan oprette forbindelse til cloudtjenesten, når du bruger indstillingen TelemetryProxyServer til at angive en proxy, der skal bruges af EDR-komponenten i Microsoft Defender for Endpoint.

Berørt scenarie: -Microsoft Defender for Endpoint med Sense-versionsnummer 10.8048.22439.1065 eller tidligere prøveversioner, der kører på Windows Server 2012 R2 -Bruger proxykonfigurationen TelemetryProxyServer. Andre metoder påvirkes ikke

Løsning:
1. Kontrollér, at computeren kører Sense version 10.8048.22439.1065 eller nyere ved enten at installere ved hjælp af den nyeste pakke, der er tilgængelig fra onboardingsiden, eller ved at anvende KB5005292.
2. Download og udpakke certifikatet fra https://github.com/microsoft/mdefordownlevelserver/blob/main/InterCA.zip
3. Importér certifikatet til lageret "Mellemliggende nøglecentre", der er tillid til, på den lokale computer.
Du kan bruge PowerShell-kommandoen: Import-Certificate -FilePath .\InterCA.cer -CertStoreLocation Cert:\LocalMachine\Ca

## <a name="integration-with-microsoft-defender-for-cloud"></a>Integration med Microsoft Defender for Cloud

Microsoft Defender for Endpoint integreres problemfrit med Microsoft Defender for Cloud. Du kan onboarde servere automatisk, få servere overvåget af Microsoft Defender for Cloud vist i Defender for Endpoint og udføre detaljerede undersøgelser som Microsoft Defender for Cloud-kunde. 

Du kan få flere oplysninger under [Integration med Microsoft Defender for Cloud](azure-server-integration.md). Servere, der er onboardet via Microsoft Defender for Cloud, får deres indledende konfiguration indstillet til at køre Defender Antivirus i [passiv tilstand](/defender-endpoint/microsoft-defender-antivirus-compatibility#microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions).

> [!NOTE]
> - Integrationen mellem Microsoft Defender til servere og Microsoft Defender for Endpoint er blevet udvidet til at understøtte Windows Server 2022, [Windows Server 2019 og Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - Overvågning af serverslutpunkt, der udnytter denne integration, er blevet deaktiveret for Office 365 GCC-kunder.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 og Windows Server 2016

### <a name="prerequisites"></a>Forudsætninger

#### <a name="prerequisites-for-windows-server-2012-r2"></a>Forudsætninger for Windows Server 2012 R2

Hvis du har opdateret dine maskiner fuldt ud med den seneste [månedlige akkumuleringspakke](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) , er der **ingen** yderligere forudsætninger.

Installationspakken kontrollerer, om følgende komponenter allerede er installeret via en opdatering:

- [Opdatering til kundeoplevelse og diagnosticeringstelemetri](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Opdatering til Universal C Runtime i Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

#### <a name="prerequisites-for-windows-server-2016"></a>Forudsætninger for Windows Server 2016

- Service stack-opdateringen (SSU) fra 14. september 2021 eller nyere skal installeres.
- Den seneste kumulative opdatering (LCU) fra 20. september 2018 eller nyere skal installeres.  Det anbefales at installere den nyeste tilgængelige SSU og LCU på serveren.  – Microsoft Defender Antivirus-funktionen skal være aktiveret/installeret og opdateret. Du kan downloade og installere den nyeste platformversion ved hjælp af Windows Update. Du kan også hente opdateringspakken manuelt fra [Microsoft Update-kataloget](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) eller fra [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).

#### <a name="prerequisites-for-running-with-third-party-security-solutions"></a>Forudsætninger for at køre med sikkerhedsløsninger fra tredjepart

Hvis du vil bruge en tredjepartsløsning til antimalware, skal du køre Microsoft Defender Antivirus i passiv tilstand. Du skal huske at indstille til passiv tilstand under installationen og onboardingprocessen.

> [!NOTE]
> Hvis du installerer Microsoft Defender for Endpoint på servere med McAfee Endpoint Security (ENS) eller VirusScan Enterprise (VSE), skal versionen af McAfee-platformen muligvis opdateres for at sikre, at Microsoft Defender Antivirus ikke fjernes eller deaktiveres. Du kan få flere oplysninger, herunder de specifikke versionsnummer, der kræves, i [artiklen McAfee Knowledge Center](https://kc.mcafee.com/corporate/index?page=content&id=KB88214).

#### <a name="update-package-for-microsoft-defender-for-endpoint-on-windows-server-2012-r2-and-2016"></a>Opdateringspakke til Microsoft Defender for Endpoint på Windows Server 2012 R2 og 2016

Hvis du vil modtage regelmæssige produktforbedringer og rettelser til EDR-sensorkomponenten, skal du sikre, at Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) anvendes eller godkendes. Hvis du vil holde beskyttelseskomponenterne opdateret, skal du desuden se [Administrer opdateringer til Microsoft Defender Antivirus og anvende grundlinjer](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Hvis du bruger Windows Server Update Services (WSUS) og/eller Microsoft Endpoint Configuration Manager, er denne nye "Microsoft Defender for Endpoint opdatering til EDR-sensor" tilgængelig under kategorien " Microsoft Defender for Endpoint".

### <a name="onboarding-steps-summary"></a>Oversigt over onboardingtrin

- TRIN 1: [Download installations- og onboardingpakkerne](#step-1-download-installation-and-onboarding-packages)
- TRIN 2: [Anvend installations- og onboardingpakken](#step-2-apply-the-installation-and-onboarding-package)
- TRIN 3: [Fuldfør onboardingtrinnene](#step-3-complete-the-onboarding-steps)

### <a name="step-1-download-installation-and-onboarding-packages"></a>TRIN 1: Download installations- og onboardingpakker

Du skal downloade både **installations** - og **onboardingpakker** fra portalen.

> [!NOTE]
> Installationspakken opdateres månedligt. Sørg for at downloade den nyeste pakke, før du bruger den.

> [!div class="mx-imgBorder"]
> ![Billede af onboardingdashboard](images/install-agent-onboard.png)

   > [!NOTE]
   > På Windows Server 2012R2 installeres Microsoft Defender Antivirus af installationspakken og vil være aktiv, medmindre du indstiller den til passiv tilstand. På Windows Server 2016 skal Microsoft Defender Antivirus installeres som en funktion (se [Skift til MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) først og opdateres fuldt ud, før du fortsætter med installationen.
   >
   > Hvis du kører en antimalwareløsning, der ikke er fra Microsoft, skal du sørge for at føje undtagelser for Microsoft Defender Antivirus ([fra denne liste over Microsoft Defender-processer under fanen Defender-processer](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)) til den løsning, der ikke er Microsoft, før installationen.  Det anbefales også at føje sikkerhedsløsninger, der ikke er fra Microsoft, til listen over undtagelser fra Defender Antivirus.

**Installationspakken** indeholder en MSI-fil, der installerer den Microsoft Defender for Endpoint agent.

**Onboardingpakken** indeholder følgende filer:

- `OptionalParamsPolicy` – indeholder den indstilling, der muliggør indsamling af eksempler
- `WindowsDefenderATPOnboardingScript.cmd` - indeholder onboardingscriptet

Brug følgende trin til at downloade pakkerne:

1. I Microsoft 365 Defender skal du gå til **Indstillinger > Enhedshåndtering > Onboarding**.

2. Vælg **Windows Server 2012 R2 og 2016**.

3. Vælg **Download installationspakken** , og gem .msi-filen.

4. Vælg **Download onboarding-pakke,** og gem filen .zip.

5. Installér installationspakken ved hjælp af en af mulighederne for at installere Microsoft Defender Antivirus. Installationen kræver administrative tilladelser.

### <a name="step-2-apply-the-installation-and-onboarding-package"></a>TRIN 2: Anvend installations- og onboardingpakken

I dette trin skal du installere de komponenter til forebyggelse og registrering, der kræves, før du onboarder din enhed til det Microsoft Defender for Endpoint cloudmiljø, for at forberede maskinen til onboarding. Sørg for, at alle [forudsætninger](#prerequisites) er opfyldt.

   > [!NOTE]
   > Microsoft Defender Antivirus installeres og vil være aktiv, medmindre du angiver det til passiv tilstand.

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Indstillinger for installation af Microsoft Defender for Endpoint-pakker

I det forrige afsnit har du downloadet en installationspakke. Installationspakken indeholder installationsprogrammet til alle Microsoft Defender for Endpoint komponenter.

Du kan bruge en af følgende indstillinger til at installere agenten:

- [Installér ved hjælp af kommandolinjen](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Installér ved hjælp af et script](#install-microsoft-defender-for-endpoint-using-a-script)
- [Anvend installations- og onboardingpakker ved hjælp af Gruppepolitik](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Installér Microsoft Defender for Endpoint ved hjælp af kommandolinjen

Brug installationspakken fra det forrige trin til at installere Microsoft Defender for Endpoint.

Kør følgende kommando for at installere Microsoft Defender for Endpoint:

```console
Msiexec /i md4ws.msi /quiet
```

Hvis du vil fjerne installationen, skal du sikre, at computeren er offboardet først ved hjælp af det relevante offboarding-script. Brug derefter Kontrolpanel \> Programmer \> og funktioner til at udføre fjernelsen.

Du kan også køre følgende fjernelseskommando for at fjerne Microsoft Defender for Endpoint:

```console
Msiexec /x md4ws.msi /quiet
```

Du skal bruge den samme pakke, som du brugte til installationen, for at ovenstående kommando kan fuldføres.

Kontakten `/quiet` undertrykker alle meddelelser.

> [!NOTE]
> Microsoft Defender Antivirus skifter ikke automatisk til passiv tilstand. Du kan vælge at indstille Microsoft Defender Antivirus til at køre i passiv tilstand, hvis du kører en ikke-Microsoft-antivirus-/antimalwareløsning. I forbindelse med kommandolinjeinstallationer angiver den valgfrie `FORCEPASSIVEMODE=1` straks Microsoft Defender Antivirus-komponenten til passiv tilstand for at undgå interferens. Hvis du derefter vil sikre, at Defender Antivirus forbliver i passiv tilstand efter onboarding for at understøtte funktioner som EDR Block, skal du angive registreringsdatabasenøglen "ForceDefenderPassiveMode".

Understøttelse af Windows Server giver bedre indsigt i serveraktiviteter, dækning af registrering af kerne- og hukommelsesangreb og aktiverer svarhandlinger.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Installér Microsoft Defender for Endpoint ved hjælp af et script

Du kan bruge [installationsscriptet](server-migration.md#installer-script) til at automatisere installation, fjernelse og onboarding. Du kan finde flere oplysninger i instruktionerne i følgende afsnit om at bruge scriptet sammen med Gruppepolitik.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Anvend Microsoft Defender for Endpoint-installations- og onboardingpakker ved hjælp af gruppepolitik

1. Opret en gruppepolitik: <br> Åbn [GPMC (Gruppepolitik Management Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)), højreklik **Gruppepolitik objekter**, du vil konfigurere, og klik på **Ny**. Angiv navnet på det nye gruppepolitikobjekt i dialogboksen, der vises, og klik på **OK**.

2. Åbn [GPMC (Gruppepolitik Management Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

3. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration**, derefter **Indstillinger** og derefter **Indstillinger for Kontrolpanel**.

4. Højreklik på **Planlagte opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave (mindst Windows 7).**

5. I vinduet **Opgave** , der åbnes, skal du gå til fanen **Generelt** . Under **Sikkerhedsindstillinger** skal du klikke på **Skift bruger eller gruppe** , skrive SYSTEM og derefter klikke på **Kontrollér navne** og derefter **PÅ OK**. NT AUTHORITY\SYSTEM vises som den brugerkonto, som opgaven kører som.

6. Vælg **Kør, om brugeren er logget på eller ej** , og markér afkrydsningsfeltet **Kør med de højeste rettigheder** .

7. I feltet Navn skal du skrive et passende navn til den planlagte opgave (f.eks. Defender for Endpoint Deployment).

8. Gå til fanen **Handlinger,** og vælg **Ny...** Kontrollér, at **Start et program** er markeret i feltet **Handling** . [Installationsscriptet](server-migration.md#installer-script) håndterer installationen og udfører straks onboardingtrinnet, når installationen er fuldført. Vælg *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* angiv derefter argumenterne:

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```

    > [!NOTE]

    > Den anbefalede politikindstilling for udførelse er `Allsigned`. Dette kræver, at scriptets signeringscertifikat importeres til det lokale udgiverlager, der er tillid til, hvis scriptet kører som SYSTEM på slutpunktet.

    Erstat \\servernavn-eller-dfs-space\share-name med UNC-stien ved hjælp af filserverens fulde domænenavn (FQDN) for den delte *install.ps1* fil. Installationspakken md4ws.msi skal placeres i den samme mappe.  Sørg for, at tilladelserne til UNC-stien tillader skriveadgang til den computerkonto, der installerer pakken, for at understøtte oprettelse af logfiler. Hvis du vil deaktivere oprettelsen af logfiler (anbefales ikke), kan du bruge parametrene -noETL -noETW.

    I scenarier, hvor Microsoft Defender Antivirus skal fungere sammen med ikke-Microsoft-antimalwareløsninger, skal du tilføje parameteren $Passive for at angive passiv tilstand under installationen.

9. Vælg **OK** , og luk alle åbne GPMC-vinduer.

10. Hvis du vil knytte gruppepolitikobjektet til en organisationsenhed, skal du højreklikke og vælge **Sammensæt et eksisterende gruppepolitikobjekt**. I den dialogboks, der vises, skal du vælge det Gruppepolitik objekt, du vil sammenkæde. Klik på **OK**.

Du kan finde flere konfigurationsindstillinger under [Konfigurer indstillinger for eksempelsamling](configure-endpoints-gp.md#configure-sample-collection-settings) og [Andre anbefalede konfigurationsindstillinger](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>TRIN 3: Fuldfør onboardingtrinnene

Følgende trin gælder kun, hvis du bruger en tredjepartsløsning til antimalware. Du skal anvende følgende indstilling for passiv tilstand for Microsoft Defender Antivirus. Kontrollér, at den er konfigureret korrekt:

1. Angiv følgende post i registreringsdatabasen:
    - Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Navn: `ForceDefenderPassiveMode`
    - Type: `REG_DWORD`
    - Værdi: `1`

   :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="Bekræftelsesresultatet for passiv tilstand" lightbox="images/atp-verify-passive-mode.png":::

> [!IMPORTANT]
>
> - Onboarding-pakken til Windows Server 2012 R2, 2016, 2019 og 2022 via Microsoft Endpoint Manager leveres i øjeblikket som script. Du kan få flere oplysninger om, hvordan du installerer programmer og scripts i Configuration Manager, [under Pakker og programmer i Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).
> - Et lokalt script er egnet til blåstempling, men bør ikke bruges til produktionsinstallation. I forbindelse med en produktionsinstallation anbefaler vi, at du bruger Gruppepolitik eller Microsoft Endpoint Configuration Manager.

## <a name="windows-server-semi-annual-enterprise-channel-sac-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel (SAC), Windows Server 2019 og Windows Server 2022

### <a name="download-package"></a>Download pakke

1. I Microsoft 365 Defender skal du gå til **Indstillinger > Enhedshåndtering > Onboarding**.

2. Vælg **Windows Server 1803 og 2019**.

3. Vælg **Download pakke**. Gem den som WindowsDefenderATPOnboardingPackage.zip.

4. Følg de trin, der er angivet i afsnittet [Fuldfør onboardingtrinnene](#step-3-complete-the-onboarding-steps) .

## <a name="verify-the-onboarding-and-installation"></a>Kontrollér onboarding og installation

Kontrollér, at Microsoft Defender Antivirus og Microsoft Defender for Endpoint kører.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at en enhed er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

> [!NOTE]
> Det er ikke nødvendigt at køre Microsoft Defender Antivirus, men det anbefales. Hvis et andet antivirusprogram er den primære løsning til beskyttelse af slutpunkter, kan du køre Defender Antivirus i passiv tilstand. Du kan kun bekræfte, at passiv tilstand er slået til, når du har bekræftet, at Microsoft Defender for Endpoint sensor (SENSE) kører.

1. Kør følgende kommando for at kontrollere, at Microsoft Defender Antivirus er installeret:

    > [!NOTE]
    > Dette bekræftelsestrin er kun påkrævet, hvis du bruger Microsoft Defender Antivirus som din aktive antimalwareløsning.

    ```DOS
    sc.exe query Windefend
    ```

    Hvis resultatet er 'Den angivne tjeneste findes ikke som en installeret tjeneste', skal du installere Microsoft Defender Antivirus.

    Du kan få oplysninger om, hvordan du bruger Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus på dine Windows-servere, under [Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md).

2. Kør følgende kommando for at kontrollere, at Microsoft Defender for Endpoint kører:

    ```DOS
    sc.exe query sense
    ```

    Resultatet bør vise, at det kører. Hvis du støder på problemer med onboarding, skal du se [Fejlfinding af onboarding](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Kør en registreringstest

Følg trinnene i [Kør en registreringstest på en nyligt onboardet enhed](run-detection-test.md) for at bekræfte, at serveren rapporterer til Defender for endpoint-tjenesten.

## <a name="next-steps"></a>Næste trin

Når du har onboardet enheder til tjenesten, skal du konfigurere de enkelte komponenter i Microsoft Defender for Endpoint. Følg [adoptionsordren](prepare-deployment.md#adoption-order) for at få vejledning i aktivering af de forskellige komponenter.

## <a name="offboard-windows-servers"></a>Windows-servere uden for bord

Du kan offboard Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 og Windows Server 2019 Core edition i den samme metode, der er tilgængelig for Windows 10 klientenheder.

- [Offboard-enheder, der bruger Gruppepolitik](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Offboard-enheder, der bruger Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Offboard-enheder, der bruger værktøjer til Enhedshåndtering mobilenheder](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)
- [Offboard-enheder, der bruger et lokalt script](configure-endpoints-script.md#offboard-devices-using-a-local-script)

Efter offboarding kan du fortsætte med at fjerne den samlede løsningspakke på Windows Server 2012 R2 og Windows Server 2016.

I forbindelse med andre Windows-serverversioner har du to muligheder for at komme uden for Windows-servere fra tjenesten:

- Fjern MMA-agenten
- Fjern konfigurationen af Defender for Slutpunktarbejdsområde

> [!NOTE]
> Disse instruktioner til offboarding til andre Windows-serverversioner gælder også, hvis du kører den tidligere Microsoft Defender for Endpoint til Windows Server 2016 og Windows Server 2012 R2, der kræver MMA. Instruktioner til migrering til den nye samlede løsning finder du [i Server migrationsscenarier i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Relaterede emner

- [Onboard tidligere versioner af Windows](onboard-downlevel.md)
- [Onboarde Windows 10 enheder](configure-endpoints.md)
- [Onboard ikke-Windows-enheder](configure-endpoints-non-windows.md)
- [Konfigurer indstillinger for proxy- og internetforbindelse](configure-proxy-internet.md)
- [Kør en registreringstest på en nyligt onboardet Defender for Endpoint-enhed](run-detection-test.md)
- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
