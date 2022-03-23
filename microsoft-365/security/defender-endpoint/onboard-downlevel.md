---
title: Onboard tidligere versioner af Windows på Microsoft Defender til Slutpunkt
description: Onboard understøttede tidligere versioner af Windows enheder, så de kan sende sensordata til Microsoft Defender for Endpoint-sensoren
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
ms.openlocfilehash: 60fd10024be0b214aed4cbc7ae89d7129df99e79
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591983"
---
# <a name="onboard-previous-versions-of-windows"></a>Onboard tidligere versioner af Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforme**

- Windows 7 SP1 Enterprise
- Windows 7 SP1-Pro
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows Server 2008 R2 SP1

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-downlevel-abovefoldlink)

Defender til Slutpunkt udvider understøttelsen til at omfatte operativsystemer på down-niveau, hvilket giver avanceret registrering af angreb og undersøgelsesfunktioner på understøttede Windows versioner.

Hvis du vil onboarde Windows klientslutpunkter til Defender til slutpunkt, skal du:

- [Konfigurere og opdatere System Center Endpoint Protection klienter](#configure-and-update-system-center-endpoint-protection-clients)
- [Installér og konfigurer Microsoft Monitoring Agent (OVERSIGT) for at rapportere sensordata](#install-and-configure-microsoft-monitoring-agent-mma)

Med Windows Server 2008 R2 SP1 har du mulighed for [at onboarde via Microsoft Defender for Cloud](#onboard-windows-servers-through-microsoft-defender-for-cloud).

> [!NOTE]
> Defender til separat slutpunkt-serverlicens er påkrævet pr. node for at kunne onboarde en Windows-server via Microsoft Monitoring Agent (mulighed 1). Alternativt kræves der en licens til Microsoft Defender til servere pr. node for at kunne onboarde en Windows-server via Microsoft Defender for Cloud (valgmulighed 2) under Understøttede funktioner, der er tilgængelige i [Microsoft Defender for Cloud](/azure/security-center/security-center-services).

> [!TIP]
> Efter onboarding af enheden kan du vælge at køre en registreringstest for at bekræfte, at den er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på et nyligt onboardet Defender til slutpunktsslutpunkt](run-detection-test.md).

## <a name="configure-and-update-system-center-endpoint-protection-clients"></a>Konfigurere og opdatere System Center Endpoint Protection klienter

> [!IMPORTANT]
> Dette trin er kun påkrævet, hvis din organisation System Center Endpoint Protection (SCEP).

Defender for Endpoint integreres med System Center Endpoint Protection for at give synlighed til malwareregistreringer og stoppe overførslen af et angreb i organisationen ved at udelukke potentielt skadelige filer eller potentielt malware.

Følgende trin er nødvendige for at aktivere denne integration:

- Installér opdateringen [til antimalwareplatformen for januar 2017 for Endpoint Protection klienter](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie)
- Konfigurer medlemskab af SCEP-klientens Skybeskyttelsestjeneste til **indstillingen Avanceret**
- Konfigurer dit netværk for at tillade forbindelser til Microsoft Defender Antivirus skyen. Du kan finde flere oplysninger [i Konfigurere og Microsoft Defender Antivirus netværksforbindelser](/microsoft-365/security/defender-endpoint/configure-network-connections-microsoft-defender-antivirus)

## <a name="install-and-configure-microsoft-monitoring-agent-mma"></a>Installér og konfigurer Microsoft Overvågningsagent (MANUELT)

### <a name="before-you-begin"></a>Før du begynder

Gennemgå følgende oplysninger for at bekræfte minimumsystemkrav:

- Installér [den månedlige opdateringspakke for februar 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)

  > [!NOTE]
  > Gælder kun for Windows Server 2008 R2, Windows 7 SP1 Enterprise og Windows 7 SP1 Pro.

- Installere opdatering [til kundeoplevelse og diagnosticeringstelemetri](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

- Installér [enten .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (eller nyere) eller [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

    > [!NOTE]
    > Gælder kun for Windows Server 2008 R2, Windows 7 SP1 Enterprise og Windows 7 SP1 Pro.
    >
    > Installér ikke .NET Framework 4.0.x, da det vil negere ovenstående installation.
    >
    > Installation af .NET 4.5 kræver muligvis, at du genstarter computeren efter installationen.

- Mød minimumskravene til Azure Log Analytics-agenten. Få mere at vide under [Indsaml data fra computere i dit miljø med Loganalyse](/azure/log-analytics/log-analytics-concept-hybrid#prerequisites)

### <a name="installation-steps"></a>Installationstrin

1. Hent installationsfilen til agent: [Windows 64-bit agent](https://go.microsoft.com/fwlink/?LinkId=828603) [eller Windows 32-bit agent](https://go.microsoft.com/fwlink/?LinkId=828604).

2. Hent arbejdsområde-id'et:
   - I navigationsruden Defender til slutpunkt skal du vælge **Indstillinger > administration af > onboarding**
   - Vælg operativsystemet
   - Kopiér arbejdsområde-id'et og arbejdsområdenøglen

3. Vælg en af følgende installationsmetoder for at installere agenten ved hjælp af arbejdsområde-id'et og arbejdsområdet:
    - [Installer agenten manuelt ved hjælp af konfigurationen](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard).

      På siden **Indstillinger for agentopsætning** skal **Forbind agenten til Azure Log Analytics (OMS)**

    - [Installér agenten ved hjælp af kommandolinjen](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line).
    - [Konfigurer agenten ved hjælp af et script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation).

   > [!NOTE]
   > Hvis du er kunde [](gov.md)hos det amerikanske offentlige myndigheder, skal du under "Azure Cloud" vælge "Azure US Government", hvis du bruger konfigurationsguiden, eller hvis du bruger en kommandolinje eller et script – skal du angive parameteren "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" til 1.

4. Hvis du bruger en proxy til at oprette forbindelse til internettet, skal du se afsnittet Konfigurer indstillinger for proxy og internetforbindelse.

Når du er færdig, bør du kunne se onboardede slutpunkter i portalen inden for en time.

## <a name="configure-proxy-and-internet-connectivity-settings"></a>Konfigurere indstillinger for proxy og internetforbindelse
Hvis dine servere skal bruge en proxy til at kommunikere med Defender for Endpoint, skal du bruge en af følgende metoder til at konfigurere OVERENSSTEMMELSE til at bruge proxyserveren:

- [Konfigurere  MANUELt til at bruge en proxyserver](/azure/azure-monitor/platform/agent-windows#install-agent-using-setup-wizard)

- [Konfigurere Windows at bruge en proxyserver for alle forbindelser](configure-proxy-internet.md)

Hvis en proxy eller firewall er i brug, skal du sikre dig, at serverne kan få adgang til alle URL-adresserne for Microsoft Defender for Endpoint-tjenesten direkte og uden SSL-skæring. Få mere at vide under [Aktivér adgang til URL-adresser for Defender for Endpoint-tjenesten](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Brug af SSL-skæringspunkt forhindrer systemet i at kommunikere med Defender for Endpoint-tjenesten.

Når det er fuldført, bør du kunne se Windows serverne i portalen inden for en time.

## <a name="onboard-windows-servers-through-microsoft-defender-for-cloud"></a>Onboard Windows-servere via Microsoft Defender til Cloud

1. I navigationsruden Microsoft 365 Defender du vælge **Indstillinger** >  **AdministrationOnboarding** > .

2. Vælg **Windows Server 2008 R2 SP1** som operativsystem.

3. Klik **på Onboard Servers i Microsoft Defender til skyen**.

4. Følg onboardinginstruktionerne i [Microsoft Defender til slutpunkt med Microsoft Defender til skyen](/azure/security-center/security-center-wdatp) , og hvis du bruger Azure ARC, skal du følge onboardinginstruktionerne i Aktivering af [Microsoft Defender til slutpunktsintegration](/azure/security-center/security-center-wdatp#enabling-the-microsoft-defender-for-endpoint-integration).

Når du har fuldført onboardingtrinnene, skal du [konfigurere og opdatere System Center Endpoint Protection klienter](#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
>
> - For at onboarding via Microsoft Defender kan fungere som forventet, skal serveren have et relevant arbejdsområde og en nøgle konfigureret i indstillingerne for Microsoft Monitoring Agent (AGENT).
> - Når den er konfigureret, installeres den relevante skyadministrationspakke på computeren, og sensorprocessen (MsSenseS.exe) installeres og startes.
> - Dette er også påkrævet, hvis serveren er konfigureret til at bruge en OMS-gatewayserver som proxy.



## <a name="verify-onboarding"></a>Bekræfte onboarding

Kontrollér, at Microsoft Defender AV og Microsoft Defender til Slutpunkt kører. 

> [!NOTE]
> Det er ikke påkrævet at køre Microsoft Defender AV, men det anbefales. Hvis et andet antivirusleverandørprodukt er den primære løsning til slutpunktsbeskyttelse, kan du køre Defender Antivirus i passiv tilstand. Du kan kun bekræfte, at passiv tilstand er aktiveret, når du har bekræftet, at Microsoft Defender til slutpunkts sensor (SENSE) kører. 

1. Kør følgende kommando for at bekræfte, at Microsoft Defender AV er installeret:

   ```sc.exe query Windefend```

    Hvis resultatet er "Den angivne tjeneste findes ikke som en installeret tjeneste", skal du installere Microsoft Defender AV. Du kan finde flere oplysninger [under Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-windows.md).

    Du kan finde oplysninger om, hvordan du bruger Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus på dine Windows-servere, under Brug [Gruppepolitik-indstillinger](use-group-policy-microsoft-defender-antivirus.md) til at konfigurere og administrere Microsoft Defender Antivirus.


2. Kør følgende kommando for at bekræfte, at Microsoft Defender til slutpunkt kører:

    ```sc.exe query sense```
    
    Resultatet skal vise, at det kører. Hvis du støder på problemer med onboarding, skal du [se Fejlfinding af onboarding](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Kør en registreringstest
Følg trinnene i Kør [en registreringstest på en nyligt onboardet](run-detection-test.md) enhed for at bekræfte, at serveren rapporterer til Defender for Endpoint-tjenesten.





## <a name="onboarding-endpoints-with-no-management-solution"></a>Onboarding-slutpunkter uden administrationsløsning 

### <a name="using-group-policy"></a>Brug af Gruppepolitik

**Trin 1: Hent den tilsvarende udpate for dit slutpunkt.**

1. Naviger til c:\windows\sysvol\domain\scripts (Ændringskontrol kan være nødvendig på en af domænecontrollerne).
1. Opret en mappe med navnet MAPPE.
1. Download følgende, og placer dem i mappen MAPPE:
   
    - Opdatering til kundeoplevelse og diagnosticeringstelemetri:
      - [Til Windows Server 2008 R2 x64](https://www.microsoft.com/download/details.aspx?familyid=1bd1d18d-4631-4d8e-a897-327925765f71)
     
    Til Windows Server 2008 R2 SP1 kræves der også følgende opdateringer:

    Månedlig opdatering for februar 2018 – KB4074598 (Windows Server 2008 R2)

    [Microsoft Update-katalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4074598)<br>
    Download opdateringer til Windows Server 2008 R2 x64
    
    .NET Framework 3.5.1 (KB315418)<br>
    [Til Windows Server 2008 R2 x64](https://download.microsoft.com/download/6/8/0/680ee424-358c-4fdf-a0de-b45dee07b711/windows6.1-kb3154518-x64.msu)
    
    >[!NOTE]
    > I denne artikel antages det, at du bruger x64-baserede servere (AGENT .exe x64 Ny SHA-2-kompatibel version).


**Trin 2: Opret et filnavn DeployTRAPPE.cmd (ved hjælp af notesblok)** Føj følgende linjer til cmd-filen. Bemærk, at du skal bruge dit WORKSPACE-id og din NØGLE.

Følgende kommando er et eksempel. Erstat følgende værdier:
- KB – Brug den relevante KB, som er relevant for det slutpunkt, du onboarder
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
"c:\windows\MMA\MMASetup-AMD64.exe" /c /t: "C:\Windows\MMA"c:\windows\MMA\ setup.exe /qn NOAPM=1 ADD_OPINSIGHTS_WORKSPACE=1
OPINSIGHTS_WORKSPACE_ID="<your workspace ID>"
OPINSIGHTS_WORKSPACE_KEY="<your workspace key>" AcceptEndUserLicenseAgreement=1
)

)
```





### <a name="group-policy-configuration"></a>Gruppepolitik konfiguration

Opret en ny gruppepolitik specifikt for onboardingenheder som f.eks. "Microsoft Defender til onboarding af slutpunkt".

- Create a Gruppepolitik folder named "c:\windows\CHET"

     :::image type="content" source="images/grppolicyconfig1.png" alt-text="mapper":::

    **Dette tilføjer en ny mappe på hver server, der får det anvendte gruppepolitikobjekt anvendt, kaldet OKA, og gemmes i c:\windows. Dette vil indeholde installationsfilerne til FORFATTER, forudsætninger og installér script.**

- Opret en Gruppepolitik filer for hver af de filer, der er gemt i Net-logon.

     :::image type="content" source="images/grppolicyconfig2.png" alt-text="billede af gruppepolitik1":::

Den kopierer filerne fra DOMAIN\NETLOGON\CHET\filnavn til C:\windows\MAPPE\filnavn – så installationsfilerne er lokale **for serveren**:

:::image type="content" source="images/deploymma.png" alt-text="Installér cmd":::

Gentag processen, men opret målretning på elementniveau under fanen FÆLLES, så filen kun kopieres til den relevante platform/operativsystemversion i omfang:

:::image type="content" source="images/targeteditor.png" alt-text="destinationseditor":::

For Windows Server 2008 R2 skal du (og der kopieres kun ned) følgende:
- Windows6.1-KB3080149-x64.msu
- Windows6.1-KB3154518-x64.msu
- Windows6.1-KB4075598-x64.msu


Når dette er gjort, skal du oprette en start-up script-politik:

:::image type="content" source="images/startupprops.png" alt-text="startegenskaber":::

Navnet på den fil, der skal køre her, er c:\windows\MAPPE\Deploy INSTALLER.cmd.
Når serveren genstartes som en del af startprocessen, installeres Opdateringen til kundeoplevelse og diagnostisk telemetri KB, og derefter installeres RUDEN-agenten, mens arbejdsområde-id og nøgle angives, og serveren vil blive onboardet.

Du kan også bruge **en øjeblikkelig opgave** til at køre deployRUDEN.cmd, hvis du ikke vil genstarte alle serverne.

Det kan gøres i to faser. Opret først **filerne og mappen** i gruppepolitikobjekt – Giv systemet tid til at sikre, at gruppepolitikobjektet er blevet anvendt, og alle serverne har installationsfilerne. Tilføj derefter den øjeblikkelige opgave. Dette vil opnå det samme resultat uden at kræve en genstart.

Da scriptet har en afslutningsmetode og ikke kan køre igen, hvis  RUNDT ER installeret, kan du også bruge en dagligt planlagt opgave for at opnå det samme resultat. Ligesom en Konfigurationsstyring politik for overholdelse af regler og standarder, kontrollerer den dagligt for at sikre, at OVERENSSTEMMELSE er til stede.

:::image type="content" source="images/schtask.png" alt-text="planlæg opgave":::

:::image type="content" source="images/newtaskprops.png" alt-text="nye opgaveegenskaber":::

:::image type="content" source="images/deploymmadowmload.png" alt-text="installér download props":::

:::image type="content" source="images/tasksch.png" alt-text="opgavestyring":::

Som nævnt i onboardingdokumentationen for Server specifikt vedrørende Server 2008 R2 skal du se nedenfor: For Windows Server 2008 R2 SP1 skal du sikre dig, at du opfylder følgende krav:

- Installér [den månedlige opdateringspakke for februar 2018](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
- Installér [enten .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (eller nyere) eller [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

Kontrollér, at KBs er til stede, før Windows Server 2008 R2. Denne proces giver dig mulighed for at onboarde alle serverne, hvis du ikke har Konfigurationsstyring administrere servere.


## <a name="offboard-endpoints"></a>Offboard-slutpunkter

Du har to muligheder for at Windows slutpunkter fra tjenesten:

- Fjern  ÆLDRE-agenten
- Fjern arbejdsområdekonfigurationen for Defender til Slutpunkt

> [!NOTE]
> Offboarding får Windows-slutpunktet til at holde op med at sende sensordata til portalen, men data fra slutpunktet, herunder reference til eventuelle beskeder, det har haft, bevares i op til seks måneder.

### <a name="uninstall-the-mma-agent"></a>Fjern  ÆLDRE-agenten

For at offboarde Windows slutpunktet kan du afinstallere ÆDER-agenten eller fjerne den fra rapporteringen til dit Defender til Slutpunkt-arbejdsområdet. Når du har deaktiveret agenten, sender slutpunktet ikke længere sensordata til Defender til slutpunktet.
Du kan finde flere oplysninger [i Sådan deaktiverer du en agent](/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### <a name="remove-the-defender-for-endpoint-workspace-configuration"></a>Fjern arbejdsområdekonfigurationen for Defender til Slutpunkt

Du kan bruge en af følgende metoder:

- Fjern konfigurationen af Arbejdsområdet Defender til Slutpunkt fra RUDEN AGENT
- Kør en PowerShell-kommando for at fjerne konfigurationen

#### <a name="remove-the-defender-for-endpoint-workspace-configuration-from-the-mma-agent"></a>Fjern konfigurationen af Arbejdsområdet Defender til Slutpunkt fra RUDEN AGENT

1. I **egenskaberne for Microsofts overvågningsagent** skal du **vælge fanen Azure Log Analytics (OMS** ).

2. Vælg arbejdsområdet Defender for Endpoint, og klik på **Fjern**.

    ![Billede af egenskaber for Microsoft Overvågningsagent](images/atp-mma.png)

#### <a name="run-a-powershell-command-to-remove-the-configuration"></a>Kør en PowerShell-kommando for at fjerne konfigurationen

1. Få dit Arbejdsområde-id:

   1. I navigationsruden skal du vælge **Indstillinger** >  **Onboarding**.

   1. Vælg det relevante operativsystem, og få dit Workspace-id.

    
2. Åbn en eleveret PowerShell, og kør følgende kommando. Brug det Arbejdsområde-id, du har fået, og som erstatter `WorkspaceID`:

    ```   
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace("WorkspaceID")
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()

    ```
