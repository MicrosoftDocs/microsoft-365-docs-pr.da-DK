---
title: Onboarde tidligere versioner af Windows på Microsoft Defender for Endpoint
description: Onboarde understøttede tidligere versioner af Windows-enheder, så de kan sende sensordata til den Microsoft Defender for Endpoint sensor
keywords: onboard, windows, 7, 81, oms, sp1, enterprise, pro, down level
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4d8665f379683ccc113a10e6308c6fa4026616c6
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717202"
---
# <a name="onboard-previous-versions-of-windows"></a>Onboard tidligere versioner af Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforme**

- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender for Endpoint udvider supporten til at omfatte operativsystemer på et tidligere niveau, hvilket giver avancerede funktioner til registrering af angreb og undersøgelsesfunktioner på understøttede Windows-versioner.

Hvis du vil føje Windows-klientslutpunkter på et niveau ned til Defender for Endpoint, skal du:

- [Konfigurer og opdater System Center Endpoint Protection klienter](#configure-and-update-system-center-endpoint-protection-clients)
- [Installér og konfigurer Microsoft Monitoring Agent (MMA) til at rapportere sensordata](#install-and-configure-microsoft-monitoring-agent-mma)

Til Windows Server 2008 R2 SP1 har du mulighed for [at onboarde via Microsoft Defender for Cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Der kræves en separat serverlicens til Defender for Endpoint pr. node for at kunne onboarde en Windows-server via Microsoft Monitoring Agent (mulighed 1). Alternativt kræves der en Licens til Microsoft Defender til servere pr. node for at onboarde en Windows-server via Microsoft Defender for Cloud (mulighed 2), se [Understøttede funktioner, der er tilgængelige i Microsoft Defender for Cloud](/azure/defender-for-cloud/supported-machines-endpoint-solutions-clouds-servers).

> [!TIP]
> Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at den er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på et nyligt onboardet Defender for Endpoint-slutpunkt](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Konfigurer og opdater System Center Endpoint Protection klienter

> [!IMPORTANT]
> Dette trin er kun påkrævet, hvis din organisation bruger System Center Endpoint Protection (SCEP).

Defender for Endpoint kan integreres med System Center Endpoint Protection for at give synlighed til malwareregistreringer og for at stoppe overførsel af et angreb i din organisation ved at forbyde potentielt skadelige filer eller mistanke om malware.

Følgende trin er påkrævet for at aktivere denne integration:

- Installér [opdateringen til antimalwareplatformen fra januar 2017 for Endpoint Protection-klienter](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Konfigurer medlemskabet af SCEP-klienten Cloud Protection Service til indstillingen **Avanceret**
- Konfigurer dit netværk for at tillade forbindelser til Microsoft Defender Antivirus-cloudmiljøet. Du kan få flere oplysninger under [Konfigurer og valider Netværksforbindelser til Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Installér og konfigurer Microsoft Monitoring Agent (MMA)

### <a name="before-you-begin"></a>Før du begynder

Gennemse følgende oplysninger for at bekræfte minimumsystemkrav:

- Installér den [månedlige opdateringspakke fra februar 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598) – Link til direkte download fra det Windows Update katalog er tilgængeligt [her](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)

- Installér [opdateringen af servicestakken fra 12. marts 2019 (eller nyere)](https://support.microsoft.com/topic/servicing-stack-update-for-windows-7-sp1-and-windows-server-2008-r2-sp1-march-12-2019-b4dc0cff-d4f2-a408-0cb1-cb8e918feeba) – link til direkte download fra Windows Update kataloget er tilgængeligt [her](https://www.catalog.update.microsoft.com/search.aspx?q=4490628)

- Installér [supportopdateringen til SHA-2-kodesignering](https://support.microsoft.com/topic/sha-2-code-signing-support-update-for-windows-server-2008-r2-windows-7-and-windows-server-2008-september-23-2019-84a8aad5-d8d9-2d5c-6d78-34f9aa5f8339) – Link til direkte download fra Windows Update kataloget er tilgængeligt [her](https://www.catalog.update.microsoft.com/search.aspx?q=kb4474419)

  > [!NOTE]
  > Gælder kun for Windows Server 2008 R2, Windows 7 SP1 Enterprise og Windows 7 SP1 Pro.

- Installér [opdateringen til kundeoplevelse og diagnosticeringstelemetri](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installér [Microsoft .Net Framework 4.5.2 eller nyere](https://www.microsoft.com/en-US/download/details.aspx?id=42642)

    > [!NOTE]
    > Installationen af .NET 4.5 kan kræve, at du genstarter computeren efter installationen.

- Opfylder minimumsystemkravene til Azure Log Analytics-agenten. Du kan finde flere oplysninger under [Indsaml data fra computere i dit miljø med Log Analytics](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Installationstrin

1. Download agentinstallationsfilen: [Windows 64-bit agent](https://go.microsoft.com/fwlink/?LinkId=828603) eller [Windows 32-bit agent](https://go.microsoft.com/fwlink/?LinkId=828604).

    >[!NOTE]
    >På grund [af udfasningen af SHA-1-support af MMA-agenten skal MMA-agenten](/azure/azure-monitor/agents/agent-windows#sha-2-code-signing-support-requirement) være version 10.20.18029 eller nyere.
    

2. Hent arbejdsområde-id'et:
   - I navigationsruden Defender for Endpoint skal du vælge **Indstillinger > Enhedshåndtering > Onboarding**
   - Vælg operativsystemet
   - Kopiér arbejdsområde-id'et og arbejdsområdenøglen

3. Brug arbejdsområde-id'et og nøglen Workspace til at vælge en af følgende installationsmetoder for at installere agenten:
    - [Installer agenten manuelt ved hjælp af konfigurationen](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      På siden **Indstillinger for agentopsætning** skal du vælge **Opret forbindelse mellem agenten og Azure Log Analytics (OMS)**

    - [Installér agenten ved hjælp af kommandolinjen](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Konfigurer agenten ved hjælp af et script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > Hvis du er [us government-kunde](gov.md), skal du under "Azure Cloud" vælge "Azure US Government", hvis du bruger installationsguiden, eller hvis du bruger en kommandolinje eller et script – angiv parameteren "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" til 1.

4. Hvis du bruger en proxy til at oprette forbindelse til internettet, skal du se afsnittet Konfigurer indstillinger for proxy- og internetforbindelse.

Når du er færdig, kan du se onboardede slutpunkter på portalen inden for en time.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Konfigurer indstillinger for proxy- og internetforbindelse
Hvis dine servere skal bruge en proxy til at kommunikere med Defender for Endpoint, skal du bruge en af følgende metoder til at konfigurere MMA til at bruge proxyserveren:

- [Konfigurer MMA til at bruge en proxyserver](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Konfigurer Windows til at bruge en proxyserver til alle forbindelser](configure-proxy-internet.md)

Hvis en proxy eller firewall er i brug, skal du sørge for, at serverne kan få adgang til alle URL-adresserne til Microsoft Defender for Endpoint-tjenesten direkte og uden SSL-opfangelse. Du kan finde flere oplysninger under [Aktivér adgang til URL-adresser til Defender for Endpoint-tjenesten](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Brug af SSL-opfangelse forhindrer systemet i at kommunikere med Defender for Endpoint-tjenesten.

Når du er færdig, kan du se onboardede Windows-servere på portalen inden for en time.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Onboarde Windows-servere via Microsoft Defender for Cloud

1. I Microsoft 365 Defender navigationsrude skal du vælge **Indstillinger** > **Onboarding af enhedshåndtering** > .

2. Vælg **Windows Server 2008 R2 SP1** som operativsystem.

3. Klik på **Onboard Servers i Microsoft Defender for Cloud**.

4. Følg onboardingvejledningen i [Microsoft Defender for Endpoint med Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp), og hvis du bruger Azure ARC, skal du følge onboardingvejledningen under [Aktivering af Microsoft Defender for Endpoint-integration](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Når du har fuldført onboardingtrinnene, skal du [konfigurere og opdatere System Center Endpoint Protection klienter](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - Hvis onboarding via Microsoft Defender for servere skal fungere som forventet, skal serveren have et passende arbejdsområde og en passende nøgle konfigureret i MMA-indstillingerne (Microsoft Monitoring Agent).
> - Når den er konfigureret, installeres den relevante cloudadministrationspakke på computeren, og sensorprocessen (MsSenseS.exe) installeres og startes.
> - Dette er også påkrævet, hvis serveren er konfigureret til at bruge en OMS Gateway-server som proxy.



## <a name="verify-onboarding"></a>Bekræft onboarding

Kontrollér, at Microsoft Defender AV og Microsoft Defender for Endpoint kører. 

> [!NOTE]
> Det er ikke nødvendigt at køre Microsoft Defender AV, men det anbefales. Hvis et andet antivirusprogram er den primære løsning til beskyttelse af slutpunkter, kan du køre Defender Antivirus i passiv tilstand. Du kan kun bekræfte, at passiv tilstand er slået til, når du har bekræftet, at Microsoft Defender for Endpoint sensor (SENSE) kører. 

1. Kør følgende kommando for at kontrollere, at Microsoft Defender AV er installeret:

   ```sc.exe query Windefend```

    Hvis resultatet er 'Den angivne tjeneste findes ikke som en installeret tjeneste', skal du installere Microsoft Defender AV. Du kan få flere oplysninger [under Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-windows.md).

    Du kan få oplysninger om, hvordan du bruger Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus på dine Windows-servere, under [Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md).


2. Kør følgende kommando for at kontrollere, at Microsoft Defender for Endpoint kører:

    ```sc.exe query sense```
    
    Resultatet bør vise, at det kører. Hvis du støder på problemer med onboarding, skal du se [Fejlfinding af onboarding](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Kør en registreringstest
Følg trinnene i [Kør en registreringstest på en nyligt onboardet enhed](run-detection-test.md) for at bekræfte, at serveren rapporterer til Defender for endpoint-tjenesten.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Onboarding-slutpunkter uden en administrationsløsning 

### <a name="using-group-policy"></a>Brug af Gruppepolitik

**Trin 1: Download den tilsvarende opdatering til dit slutpunkt.**

1. Naviger til c:\windows\sysvol\domain\scripts (ændringskontrol kan være nødvendig på en af domænecontrollerne).
1. Opret en mappe med navnet MMA.
1. Download følgende, og placer dem i MMA-mappen:
   
    - Opdatering til kundeoplevelse og diagnosticeringstelemetri:
      - [Til Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Der kræves også følgende opdateringer til Windows Server 2008 R2 SP1:

    Månedlig opdatering i februar 2018 – KB4074598 (Windows Server 2008 R2)

    [Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Download opdateringer til Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Til Windows Server 2008 R2 x64](/iis/install/installing-iis-7/install-windows-server-2008-and-windows-server-2008-r2)
    
    >[!NOTE]
    > I denne artikel antages det, at du bruger x64-baserede servere (MMA Agent .exe x64 Ny SHA-2-kompatibel version).


**Trin 2: Opret et filnavn DeployMMA.cmd (ved hjælp af notesblok)** Føj følgende linjer til cmd-filen. Bemærk, at du skal bruge dit arbejdsområde-id og din NØGLE.

Følgende kommando er et eksempel. Erstat følgende værdier:
- KB – Brug det relevante KB, der er relevant for det slutpunkt, du onboarder
- Arbejdsområde-id og NØGLE – Brug dit id og din nøgle


```dos
@echo off  
cd "C:" 
IF EXIST "C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe" (  
exit 
) ELSE ( 
 
wusa.exe C:\Windows\MMA\Windows6.1-KB3080149-x64.msu /quiet /norestart 
wusa.exe C:\Windows\MMA\Windows6.1-KB4074598-x64.msu /quiet /norestart 
wusa.exe C:\Windows\MMA\Windows6.1-KB3154518-x64.msu /quiet /norestart 
wusa.exe C:\Windows\MMA\Windows8.1-KB3080149-x64.msu /quiet /norestart 
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t:"C:\Windows\MMA"
c:\windows\MMA\setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1 OPINSIGHTS_WORKSPACE_ID="<your workspace ID>" OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1

) 
```





### <a name="group-policy-configuration"></a>konfiguration af Gruppepolitik

Opret en ny gruppepolitik specielt til onboarding af enheder, f.eks. "Microsoft Defender for Endpoint Onboarding".

- Opret en Gruppepolitik mappe med navnet "c:\windows\MMA"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="Mappeplaceringen" lightbox="images/grppolicyconfig1.png":::

    **Dette vil tilføje en ny mappe på alle servere, der anvender GPO'et, kaldet MMA, og gemmes i c:\windows. Dette vil indeholde installationsfilerne til MMA, forudsætninger og installationsscript.**

- Opret en indstilling for Gruppepolitik Filer for hver af de filer, der er gemt i Net logon.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="Gruppepolitikken – 1" lightbox="images/grppolicyconfig2.png":::

Filerne kopieres fra DOMAIN\NETLOGON\MMA\filename til C:\windows\MMA\filename – **så installationsfilerne er lokale på serveren**:

:::image type="content" source="images/deploymma.png" alt-text="Egenskaberne for installation af mma cmd" lightbox="images/deploymma.png":::

Gentag processen, men opret målretning på elementniveau under fanen COMMON, så filen kun kopieres til den relevante platform/operativsystemversion i omfang:

:::image type="content" source="images/targeteditor.png" alt-text="Destinationseditoren" lightbox="images/targeteditor.png":::

Til Windows Server 2008 R2 skal du bruge (og det kopierer kun ned) følgende:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Når dette er gjort, skal du oprette en politik for startscript:

:::image type="content" source="images/startupprops.png" alt-text="Startegenskaberne" lightbox="images/startupprops.png":::

Navnet på den fil, der skal køres her, er c:\windows\MMA\DeployMMA.cmd.
Når serveren genstartes som en del af opstartsprocessen, installeres opdateringen til kundeoplevelsen og diagnosticeringstelemetri KB, og MMA-agenten installeres, mens arbejdsområde-id'et og nøglen angives, og serveren onboardes.

Du kan også bruge en **øjeblikkelig opgave** til at køre deployMMA.cmd, hvis du ikke vil genstarte alle serverne.

Dette kan gøres i to faser. Opret først **filerne og mappen i** GPO – Giv systemet tid til at sikre, at gruppepolitikobjektet er anvendt, og at alle serverne har installationsfilerne. Tilføj derefter den øjeblikkelige opgave. Dette vil opnå det samme resultat uden at kræve en genstart.

Da scriptet har en afslutningsmetode og ikke kan køres igen, hvis MMA er installeret, kan du også bruge en daglig planlagt opgave til at opnå det samme resultat. På samme måde som med en Configuration Manager politik for overholdelse af angivne standarder kontrolleres det dagligt for at sikre, at MMA er til stede.

:::image type="content" source="images/schtask.png" alt-text="planlæg opgave" lightbox="images/schtask.png":::

:::image type="content" source="images/newtaskprops.png" alt-text="De nye opgaveegenskaber" lightbox="images/newtaskprops.png":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="Egenskaber for installation af mma-download" lightbox="images/deploymmadowmload.png":::

:::image type="content" source="images/tasksch.png" alt-text="Opgavestyringen" lightbox="images/tasksch.png":::

Som nævnt i onboardingdokumentationen til Server specifikt omkring Server 2008 R2, skal du se nedenfor: For Windows Server 2008 R2 SP1 skal du sikre, at du opfylder følgende krav:

- Installér den [månedlige opdateringspakke fra februar 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Installér enten [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (eller nyere) eller [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Kontrollér, at nøgletal er til stede, før du onboarder Windows Server 2008 R2. Denne proces giver dig mulighed for at onboarde alle serverne, hvis du ikke har Configuration Manager administration af servere.


## <a name="offboard-endpoints"></a>Slutpunkter uden for tavlen

Du har to muligheder for at komme uden for Windows-slutpunkter fra tjenesten:

- Fjern MMA-agenten
- Fjern konfigurationen af Defender for Slutpunktarbejdsområde

> [!NOTE]
> Offboarding medfører, at Windows-slutpunktet stopper med at sende sensordata til portalen, men data fra slutpunktet, herunder reference til eventuelle beskeder, det har haft, bevares i op til seks måneder.

### <a name="uninstall-the-mma-agent"></a>Fjern MMA-agenten

Hvis du vil væk fra Windows-slutpunktet, kan du fjerne MMA-agenten eller fjerne den fra rapportering til dit Defender for Endpoint-arbejdsområde. Når du har offboardet agenten, sender slutpunktet ikke længere sensordata til Defender for Endpoint.
Du kan få flere oplysninger under [Sådan deaktiverer du en agent](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Fjern konfigurationen af Defender for Slutpunktarbejdsområde

Du kan bruge en af følgende metoder:

- Fjern konfigurationen af Defender for Endpoint-arbejdsområdet fra MMA-agenten
- Kør en PowerShell-kommando for at fjerne konfigurationen

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Fjern konfigurationen af Defender for Endpoint-arbejdsområdet fra MMA-agenten

1. Under **Egenskaber for Microsoft-overvågningsagent** skal du vælge fanen **Azure Log Analytics (OMS).**

2. Vælg Arbejdsområdet Defender for Endpoint, og klik på **Fjern**.

    :::image type="content" source="images/atp-mma.png" alt-text="Ruden Arbejdsområder" lightbox="images/atp-mma.png":::

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Kør en PowerShell-kommando for at fjerne konfigurationen

1. Hent dit arbejdsområde-id:

   1. Vælg **Indstillinger** > **Onboarding** i navigationsruden.

   1. Vælg det relevante operativsystem, og hent dit arbejdsområde-id.

    
2. Åbn en PowerShell med administratorrettigheder, og kør følgende kommando. Brug det arbejdsområde-id, du har hentet og erstattet `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
