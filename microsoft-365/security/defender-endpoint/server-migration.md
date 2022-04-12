---
title: Scenarier for serveroverførsel for den nye version af Microsoft Defender for Endpoint
description: Læs denne artikel for at få et overblik over, hvordan du overfører dine servere fra den tidligere MMA-baserede løsning til den aktuelle Unified-løsningspakke i Defender for Endpoint.
keywords: overfør server, server, 2012r2, 2016, serveroverførsel, enhedshåndtering, konfigurer Microsoft Defender for Endpoint servere, onboarde Microsoft Defender for Endpoint servere
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ed31a629f6cde18af03c3c6102b821cb6a04dd96
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782656"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Serveroverførselsscenarier fra den forrige MMA-baserede Microsoft Defender for Endpoint løsning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Sørg altid for, at operativsystemet og Microsoft Defender Antivirus på Windows Server 2016 opdateres fuldt ud, før du fortsætter med installationen eller opgraderingen. Hvis du vil modtage regelmæssige produktforbedringer og rettelser til komponenten Slutpunktsregistrering og -svar sensor, skal du sikre, at Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) anvendes eller godkendes efter installationen. Hvis du vil holde beskyttelseskomponenter opdateret, skal du desuden se [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Disse instruktioner gælder for den nye MSI-pakke (Unified Solution and Installer) med Microsoft Defender for Endpoint til Windows Server 2012 R2 og Windows Server 2016. Denne artikel indeholder instruktioner på højt niveau til forskellige mulige overførselsscenarier fra den forrige til den aktuelle løsning. Disse trin på højt niveau er beregnet som retningslinjer, der skal justeres til de udrulnings- og konfigurationsværktøjer, der er tilgængelige i dit miljø.

> [!NOTE]
> Opgraderinger af operativsystemet med Microsoft Defender for Endpoint installeret understøttes ikke. Fjern derefter offboard, før du fortsætter med en opgradering.

> [!NOTE]
> Fuld Microsoft Endpoint Configuration Manager automatisering og integration til at udføre en automatiseret opgradering vil være tilgængelig i en senere version af MECM. Fra 2107-versionen med den seneste hotfix-akkumulering kan du bruge noden Endpoint Protection til konfiguration samt Gruppepolitik, PowerShell Microsoft Endpoint Manager lejertilknyttelse eller lokal konfiguration. Derudover kan du udnytte eksisterende funktionalitet i Microsoft Endpoint Configuration Manager til at automatisere manuelle opgraderingstrin. Metoder, som er beskrevet nedenfor.


## <a name="installer-script"></a>Installationsscript

For at lette opgraderinger, når Microsoft Endpoint Configuration Manager eller Microsoft Defender for Cloud ikke er i brug eller endnu ikke er tilgængelige til at udføre opgraderingen, kan du bruge dette [opgraderingsscript](https://github.com/microsoft/mdefordownlevelserver). Det kan hjælpe med at automatisere følgende påkrævede trin:

1. Fjern OMS-arbejdsområdet for Microsoft Defender for Endpoint (VALGFRIt).
2. Fjern SCEP-klienten (System Center Endpoint Protection), hvis den er installeret.
3. Download og installér (Windows Server 2012 R2) [forudsætninger](configure-server-endpoints.md#prerequisites), hvis det er nødvendigt.
4. Installer Microsoft Defender for Endpoint.
5. Anvend onboardingscriptet **til brug med Gruppepolitik, der** downloades fra [Microsoft 365 Defender](https://security.microsoft.com).

Hvis du vil bruge scriptet, skal du downloade det til en installationsmappe, hvor du også har placeret installations- og onboardingpakkerne (se [Konfigurer serverslutpunkter](configure-server-endpoints.md).

EKSEMPEL: .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager migreringsscenarier 

>[!NOTE]
>Du skal bruge Microsoft Endpoint Configuration Manager version 2107 eller nyere.

Overførselstrin: 

1. Opdater computeren fuldt ud, herunder Microsoft Defender Antivirus (Windows Server 2016).
2. Opret en ny samling med medlemskabsregler for at inkludere maskiner, der skal overføres.
3. [Opret et program](/mem/configmgr/apps/deploy-use/create-applications) for at udføre følgende opgaver: 
   1. Fjern SCEP.
   2. Installér [forudsætningerne,](configure-server-endpoints.md#prerequisites) hvor det er relevant.
   3. Installér Microsoft Defender for Endpoint (se [Konfigurer serverslutpunkter](configure-server-endpoints.md).
   4. Anvend onboardingscriptet **til brug med Gruppepolitik, der** downloades fra [Microsoft 365 Defender](https://security.microsoft.com). 
   > [!TIP]
   > Du kan bruge [installationsscriptet](server-migration.md#installer-script) som en del af dit program til at automatisere ovenstående trin.
4. Installer programmet i den nye samling.
5. Opret og/eller tildel (eksisterende) Endpoint Protection politikker til samlingen.
6. Anvend opdateringer.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Du bruger i øjeblikket Microsoft Endpoint Configuration Manager til at administrere dine servere, kører en antivirusløsning, der ikke er fra Microsoft, og den MMA-baserede sensor. Du vil opgradere til den nye Microsoft Defender for Endpoint.

Overførselstrin:

1. Opdater computeren fuldt ud, herunder Microsoft Defender Antivirus (Windows Server 2016).
2. Opret en ny samling med medlemskabsregler for at inkludere maskiner, der skal overføres. 
3. Sørg for, at administration af antivirus fra tredjepart ikke længere overfører antivirus til disse maskiner.*
4. Skriv dine politikker i noden Endpoint Protection i MECM, og målret til den nyoprettede samling.*
5. Opret et program for at udføre følgende opgaver:
   1. Fjern konfigurationen af MMA-arbejdsområdet for Microsoft Defender for Endpoint. Se [Fjern et arbejdsområde ved hjælp af PowerShell](/azure/azure-monitor/agents/agent-manage). Dette trin er valgfrit. den forrige Slutpunktsregistrering og -svar holder op med at køre, når den nyere sensor bliver aktiv.
   2. Installér [forudsætningerne,](configure-server-endpoints.md#prerequisites) hvor det er relevant.
   3. Installér Microsoft Defender for Endpoint til Windows Server 2012 R2- og 2016-pakken, og **aktivér passiv tilstand**. Se [Installér Microsoft Defender Antivirus ved hjælp af kommandolinjen](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Anvend onboardingscriptet **til brug med Gruppepolitik, der** downloades fra [Microsoft 365 Defender](https://security.microsoft.com).
6. Anvend opdateringer.
7. Fjern dit antivirusprogram, der ikke er Fra Microsoft, ved enten at bruge antiviruskonsollen, der ikke er Microsoft, eller ved at bruge Microsoft Endpoint Configuration Manager efter behov. Sørg for at fjerne konfigurationen af passiv tilstand.*

> [!TIP]
> Du kan bruge [installationsscriptet](server-migration.md#installer script) som en del af dit program til at automatisere ovenstående trin. Hvis du vil aktivere passiv tilstand, skal du anvende flaget -Passive. Eksempelvis .\install.ps1 -RemoveMMA <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*Disse trin gælder kun, hvis du vil erstatte din antivirusløsning, der ikke er Fra Microsoft. Se [Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md).

Hvis du vil flytte en computer ud af passiv tilstand, skal du angive følgende nøgle til 0:

Sti: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Værdi: 0


## <a name="other-migration-scenarios"></a>Andre overførselsscenarier

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Du har en server, der er blevet onboardet ved hjælp af den MMA-baserede Microsoft Defender for Endpoint. ScEP er installeret (Windows Server 2012 R2) eller Microsoft Defender Antivirus (Windows Server 2016). Denne computer administreres **ikke** via Microsoft Defender for Cloud, Microsoft Endpoint Manager eller Microsoft Endpoint Configuration Manager.

1. Opdater computeren fuldt ud, herunder Microsoft Defender Antivirus (Windows Server 2016).
2. Fjern konfigurationen af MMA-arbejdsområdet for Microsoft Defender for Endpoint. Se [Fjern et arbejdsområde ved hjælp af PowerShell](/azure/azure-monitor/agents/agent-manage).
3. Fjern System Center Endpoint Protection (Windows Server 2012 R2).
4. Installér [forudsætningerne,](configure-server-endpoints.md#prerequisites) hvor det er relevant. 
5. Installér Microsoft Defender for Endpoint (se [Konfigurer serverslutpunkter](configure-server-endpoints.md)).
6. Anvend onboardingscriptet **til brug med Gruppepolitik, der** downloades fra [Microsoft 365 Defender](https://security.microsoft.com). 
7. Anvend opdateringer.
8. Opret og anvend politikker ved hjælp af Gruppepolitik, PowerShell eller en administrationsløsning fra tredjepart.

> [!TIP]
> Du kan bruge installationsscriptet til at automatisere ovenstående trin.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Du har en server, hvor du vil installere Microsoft Defender for Endpoint. Der er installeret en ikke-Microsoft-slutpunktsbeskyttelse eller en slutpunktsregistrering og -svar-løsning. Du har ikke til hensigt at bruge Microsoft Endpoint Configuration Manager eller Microsoft Defender for Cloud. Du bruger din egen udrulningsmekanisme. 

1. Opdater computeren fuldt ud, herunder Microsoft Defender Antivirus (Windows Server 2016).
2. Installér Microsoft Defender for Endpoint til Windows Server 2012 R2 & 2016-pakken, og **aktivér passiv tilstand**. Se [Installér Microsoft Defender Antivirus ved hjælp af kommandolinjen](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Anvend onboardingscriptet, der passer til dit miljø, og som downloades fra [Microsoft 365 Defender](https://security.microsoft.com). 
4. Fjern den ikke-Microsoft-slutpunktsbeskyttelse eller -slutpunktsregistrering og -svar-løsning, og fjern passiv tilstand.*
5. Anvend opdateringer.
6. Opret og anvend politikker ved hjælp af Gruppepolitik, PowerShell eller en administrationsløsning fra tredjepart.

> [!TIP]
> Du kan bruge [installationsscriptet](server-migration.md#installer-script) til at automatisere trin 1 til 4. Hvis du vil aktivere passiv tilstand, skal du anvende flaget -Passive, som sikrer, at Defender Antivirus går i passiv tilstand før onboarding og ikke forstyrrer en ikke-Microsoft-antimalwareløsning. Hvis du derefter vil sikre, at Defender Antivirus forbliver i passiv tilstand efter onboarding for at understøtte Slutpunktsregistrering og -svar funktioner, f.eks. Slutpunktsregistrering og -svar Block, skal du sørge for at angive registreringsdatabasenøglen "ForceDefenderPassiveMode". EKSEMPEL: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Dette trin gælder kun, hvis du vil erstatte din antivirusløsning, der ikke er fra Microsoft. Vi anbefaler, at du bruger Microsoft Defender Antivirus, der er inkluderet i Microsoft Defender for Endpoint, til at levere det fulde sæt funktioner. Se [Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md).

Hvis du vil flytte en computer ud af passiv tilstand, skal du angive følgende nøgle til 0:

Sti: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Værdi: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Microsoft Defender for Cloud-scenarier

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Du bruger Microsoft Defender for Cloud. Microsoft Monitoring Agent (MMA) og/eller Microsoft Antimalware til Azure (SCEP) er installeret, og du vil opgradere.
Hvis du bruger Microsoft Defender for Cloud, kan du udnytte den automatiserede opgraderingsproces. Se [Beskyt dine slutpunkter med Defender for Clouds integrerede Slutpunktsregistrering og -svar løsning: Microsoft Defender for Endpoint](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>Gruppepolitik konfiguration
Hvis du vil konfigurere ved hjælp af Gruppepolitik, skal du sikre dig, at du bruger de nyeste ADMX-filer i dit centrale lager til at få adgang til de korrekte politikindstillinger for Defender for Endpoint. Se [Under Sådan opretter og administrerer du Det centrale Store for Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) og downloader de nyeste filer **til brug sammen med Windows 10**.
