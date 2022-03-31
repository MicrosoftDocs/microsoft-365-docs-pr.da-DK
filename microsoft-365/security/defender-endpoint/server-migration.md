---
title: Scenarier for serveroverførsel for den nye version af Microsoft Defender til slutpunkt
description: Læs denne artikel for at få et overblik over, hvordan du overfører dine servere fra den forrige  ÆLDRE-baserede løsning til den aktuelle samlede Defender til endpoint-samlede løsningspakke.
keywords: overfør server, server, 2012r2, 2016, serveroverførsel, enhedshåndtering, konfigurer Microsoft Defender til slutpunktsservere, onboard Microsoft Defender til Endpoint-servere
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
ms.openlocfilehash: 7fd4ca4931c060c0eb7092f74ed708c0b8d69738
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63600992"
---
# <a name="server-migration-scenarios-from-the-previous-mma-based-microsoft-defender-for-endpoint-solution"></a>Scenarier for serveroverførsel fra den forrige, RRE-baserede Microsoft Defender for Endpoint-løsning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> [!NOTE]
> Sørg altid for Microsoft Defender Antivirus opdateret fuldt ud Windows Server 2016, før du fortsætter med installation eller opgradering. For at modtage regelmæssige produktforbedringer og løsninger til Slutpunktsregistrering og -svar sensorkomponenten skal du sikre dig, Windows [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) bliver anvendt eller godkendt. Desuden skal du, for at holde beskyttelseskomponenter opdaterede, se [Administrer Microsoft Defender Antivirus opdateringer og anvend oprindelige planer](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Disse instruktioner gælder for den nye samlede løsning og installationspakken til Microsoft Defender til slutpunkt Windows Server 2012 R2 og Windows Server 2016. Denne artikel indeholder instruktioner på højt niveau for forskellige mulige overførselsscenarier fra den forrige til den aktuelle løsning. Disse overordnede trin er tiltænkt som retningslinjer, der skal tilpasses til de installations- og konfigurationsværktøjer, der er tilgængelige i dit miljø.

> [!NOTE]
> Opgradering af operativsystem med Microsoft Defender til slutpunkt installeret understøttes ikke. Fjern derefter offboardet, før du fortsætter med en opgradering.

> [!NOTE]
> Under forhåndsvisningen bliver Microsoft Endpoint Configuration Manager fuld automatisering og integration til at udføre en automatisk opgradering i en senere version af MECM. Fra 2107-versionen med den nyeste hotfix-opdateringspakke kan du bruge Endpoint Protection-noden til konfiguration samt Gruppepolitik, PowerShell, Microsoft Endpoint Manager-lejeren vedhæfter eller lokal konfiguration. Desuden kan du udnytte eksisterende funktionalitet i Microsoft Endpoint Configuration Manager til at automatisere manuelle opgraderingstrin og metoder, som er beskrevet nedenfor.


## <a name="installer-script"></a>Installer script

For at muliggøre opgraderinger, når Microsoft Endpoint Configuration Manager eller Microsoft Defender for Cloud ikke er i brug eller endnu ikke er tilgængelige for at udføre opgraderingen, kan du bruge dette [opgraderingsscript](https://github.com/microsoft/mdefordownlevelserver). Det kan hjælpe med at automatisere følgende påkrævede trin:

1. Fjern OMS-arbejdsområdet for Microsoft Defender til slutpunkt (VALGFRIT).
2. Fjern System Center Endpoint Protection, hvis den er installeret.
3. Hvis det er nødvendigt, kan du downloade og installere (Windows Server 2012 R2). [](configure-server-endpoints.md#prerequisites)
4. Installer Microsoft Defender til slutpunkt.
5. Anvend onboarding-scriptet **til brug sammen med Gruppepolitik** downloadet [fra Microsoft 365 Defender](https://security.microsoft.com).

For at bruge scriptet skal du hente det til en installationsmappe, hvor du også har placeret installations- og onboardingpakkerne (se [Konfigurer serverslutpunkter](configure-server-endpoints.md)).

EKSEMPEL: .\install.ps1 -RemoveÆDER <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd"

## <a name="microsoft-endpoint-configuration-manager-migration-scenarios"></a>Microsoft Endpoint Configuration Manager overflytningsscenarier 

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-including-system-center-endpoint-protection-scep-and-are-running-the-microsoft-monitoring-agent-mma-based-sensor-you-want-to-upgrade-to-the-microsoft-defender-for-endpoint-unified-solution-preview"></a>Du bruger i øjeblikket Microsoft Endpoint Configuration Manager til at administrere dine servere, herunder System Center Endpoint Protection (SCEP), og kører den Microsoft Monitoring Agent (AGENT)-baserede sensor. Du vil opgradere til forhåndsvisningen af en samlet Microsoft Defender for **Endpoint-løsning**.

>[!NOTE]
>Du skal bruge Microsoft Endpoint Configuration Manager version 2107.


Overførselstrin: 

1. Opdater computeren fuldt ud, Microsoft Defender Antivirus (Windows Server 2016).
2. Opret en ny samling med medlemskabsregler for at inkludere maskiner, der skal overføres.
3. [Opret et program](/mem/configmgr/apps/deploy-use/create-applications) for at udføre følgende opgaver: 
   1. Fjern RUDEN-arbejdsområdekonfigurationen for Microsoft Defender til slutpunkt. Se [Fjern et arbejdsområde ved hjælp af PowerShell](/azure/azure-monitor/agents/agent-manage). Dette trin er valgfrit. den Slutpunktsregistrering og -svar sensor holder op med at køre, efter den nye er blevet aktiv (bemærk, at det kan tage flere timer).
   2. Fjern SCEP.
   3. Installer [forudsætningerne, hvor det](configure-server-endpoints.md#prerequisites) er relevant.
   4. Installer Microsoft Defender til slutpunkt (se [Konfigurer serverslutpunkter](configure-server-endpoints.md).
   5. Anvend onboarding-scriptet **til brug sammen med Gruppepolitik** downloadet [fra Microsoft 365 Defender](https://security.microsoft.com). 

   > [!TIP]
   > Du kan bruge [installationsscriptet](server-migration.md#installer-script) som en del af dit program til at automatisere ovenstående trin.
4. Installér programmet til den nye samling.
5. Opret og/eller tildel (eksisterende) Endpoint Protection politikker til samlingen.
6. Anvend opdateringer.

### <a name="you-are-currently-using-microsoft-endpoint-configuration-manager-to-manage-your-servers-are-running-a-non-microsoft-antivirus-solution-and-the-mma-based-sensor-you-want-to-upgrade-to-the-new-microsoft-defender-for-endpoint"></a>Du bruger i øjeblikket Microsoft Endpoint Configuration Manager til at administrere dine servere, kører en antivirusløsning, der ikke er Microsoft, og den OLE-baserede sensor. Du vil opgradere til det nye Microsoft Defender til slutpunkt.

Overførselstrin:

1. Opdater computeren fuldt ud, Microsoft Defender Antivirus (Windows Server 2016).
2. Opret en ny samling med medlemskabsregler for at inkludere maskiner, der skal overføres. 
3. Sørg for, at administration af antivirus fra tredjepart ikke længere skubber antivirus på disse computere.*
4. Author your policies in the Endpoint Protection node of MECM and target to the newly created collection.*
5. Opret et program for at udføre følgende opgaver:
   1. Fjern RUDEN-arbejdsområdekonfigurationen for Microsoft Defender til slutpunkt. Se [Fjern et arbejdsområde ved hjælp af PowerShell](/azure/azure-monitor/agents/agent-manage). Dette trin er valgfrit. den Slutpunktsregistrering og -svar sensor holder op med at køre, efter den nye er blevet aktiv (bemærk, at det kan tage flere timer).
   2. Installer [forudsætningerne, hvor det](configure-server-endpoints.md#prerequisites) er relevant.
   3. Installer pakken Microsoft Defender til slutpunkt til Windows Server 2012 R2 og 2016, og **aktivér passiv tilstand**. Se [Installér Microsoft Defender Antivirus ved hjælp af kommandolinjen](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
   4. Anvend onboarding-scriptet **til brug sammen med Gruppepolitik** downloadet [fra Microsoft 365 Defender](https://security.microsoft.com).
6. Anvend opdateringer.
7. Fjern din antivirussoftware, der ikke er Microsoft, ved enten at bruge den ikke-Microsoft-antiviruskonsol eller ved Microsoft Endpoint Configuration Manager efter behov. Sørg for at fjerne passive tilstandskonfiguration.*

> [!TIP]
> Du kan bruge [installer-scriptet](server-migration.md#installer script) som en del af dit program til at automatisere ovenstående trin. Hvis du vil aktivere passiv tilstand, skal du anvende det passive flag. F.eks. .\install.ps1 -RemoveÆDER <YOUR_WORKSPACE_ID> -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive

*Disse trin gælder kun, hvis du regner med at erstatte din antivirusløsning, som ikke er Microsoft. Se [bedre sammen: Microsoft Defender Antivirus og Microsoft Defender til slutpunkt](why-use-microsoft-defender-antivirus.md).

Hvis du vil flytte en maskine ud af passiv tilstand, skal du angive følgende nøgle til 0:

Sti: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Value: 0


## <a name="other-migration-scenarios"></a>Andre overførselsscenarier

### <a name="you-have-a-server-that-has-been-onboarded-using-the-mma-based-microsoft-defender-for-endpoint-it-has-scep-installed-windows-server-2012-r2-or-microsoft-defender-antivirus-windows-server-2016-this-machine-is-not-managed-through-microsoft-defender-for-cloud-microsoft-endpoint-manager-or-microsoft-endpoint-configuration-manager"></a>Du har en server, der er blevet onboardet ved hjælp af den  ÆLDRE-baserede Microsoft Defender til slutpunkt. Det har SCEP installeret (Windows Server 2012 R2) eller Microsoft Defender Antivirus (Windows Server 2016). Denne computer **administreres** ikke via Microsoft Defender til cloud, Microsoft Endpoint Manager eller Microsoft Endpoint Configuration Manager.

1. Opdater computeren fuldt ud, Microsoft Defender Antivirus (Windows Server 2016).
2. Fjern RUDEN-arbejdsområdekonfigurationen for Microsoft Defender til slutpunkt. Se [Fjern et arbejdsområde ved hjælp af PowerShell](/azure/azure-monitor/agents/agent-manage).
3. Fjern System Center Endpoint Protection (Windows Server 2012 R2).
4. Installer [forudsætningerne, hvor det](configure-server-endpoints.md#prerequisites) er relevant. 
5. Installer Microsoft Defender til slutpunkt (se [Konfigurer serverslutpunkter](configure-server-endpoints.md)).
6. Anvend onboarding-scriptet **til brug sammen med Gruppepolitik** downloadet [fra Microsoft 365 Defender](https://security.microsoft.com). 
7. Anvend opdateringer.
8. Opret og anvend politikker ved Gruppepolitik, PowerShell eller en tredjepartsadministrationsløsning.

> [!TIP]
> Du kan bruge installationsscriptet til at automatisere ovenstående trin.

### <a name="you-have-a-server-on-which-you-want-to-install-microsoft-defender-for-endpoint-it-has-a-non-microsoft-endpoint-protection-or-endpoint-detection-and-response-solution-installed-you-do-not-intend-to-use-microsoft-endpoint-configuration-manager-or-microsoft-defender-for-cloud-you-use-your-own-deployment-mechanism"></a>Du har en server, hvor du vil installere Microsoft Defender til slutpunkt. Den har en ikke-Microsoft-slutpunktsbeskyttelse eller slutpunktsregistrering og -svar-løsning installeret. Du har ikke til hensigt at bruge Microsoft Endpoint Configuration Manager eller Microsoft Defender til clouden. Du kan bruge din egen installationsmekanisme. 

1. Opdater computeren fuldt ud, Microsoft Defender Antivirus (Windows Server 2016).
2. Installér pakken Microsoft Defender for Endpoint Windows Server 2012 R2 & 2016, og **aktivér passiv tilstand**. Se [Installér Microsoft Defender Antivirus ved hjælp af kommandolinjen](configure-server-endpoints.md#install-microsoft-defender-for-endpoint-using-the-command-line).
3. Anvend onboardingscriptet, der er relevant for dit miljø, downloadet [Microsoft 365 Defender](https://security.microsoft.com). 
4. Fjern ikke-Microsoft-slutpunktsbeskyttelse eller -slutpunktsregistrering og -svar, og fjern passiv tilstand.*
5. Anvend opdateringer.
6. Opret og anvend politikker ved Gruppepolitik, PowerShell eller en tredjepartsadministrationsløsning.

> [!TIP]
> Du kan bruge [installationsprogrammets script](server-migration.md#installer-script) til at automatisere trin 1 til 4. Hvis du vil aktivere passiv tilstand, skal du anvende det passive flag, som sikrer, at Defender Antivirus går i passiv tilstand før onboarding og ikke forstyrrer en ikke-Microsoft-antimalwareløsning. For at sikre, at Defender Antivirus forbliver i passiv tilstand efter onboarding til at understøtte Slutpunktsregistrering og -svar-funktioner som f.eks. Slutpunktsregistrering og -svar Block, skal du sørge for at indstille registreringsdatabasenøglen "ForceDefenderPassiveMode". EKSEMPEL: `.\install.ps1 -OnboardingScript ".\WindowsDefenderATPOnboardingScript.cmd" -Passive`


*Dette trin gælder kun, hvis du regner med at erstatte din antivirusløsning, som ikke er Microsoft. Vi anbefaler, at Microsoft Defender Antivirus, der følger med Microsoft Defender til Slutpunkt, for at give adgang til alle funktioner. Se [bedre sammen: Microsoft Defender Antivirus og Microsoft Defender til slutpunkt](why-use-microsoft-defender-antivirus.md).

Hvis du vil flytte en maskine ud af passiv tilstand, skal du angive følgende nøgle til 0:

Sti: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection Name: ForceDefenderPassiveMode Type: REG_DWORD Value: 0


## <a name="microsoft-defender-for-cloud-scenarios"></a>Microsoft Defender til skyscenarier

### <a name="youre-using-microsoft-defender-for-cloud-the-microsoft-monitoring-agent-mma-andor-microsoft-antimalware-for-azure-scep-are-installed-and-you-want-to-upgrade"></a>Du bruger Microsoft Defender til skyen. Microsofts overvågningsagent (TERM) og/eller Microsoft Antimalware til Azure (SCEP) er installeret, og du vil opgradere.
Hvis du bruger Microsoft Defender til skyen, kan du udnytte den automatiske opgraderingsproces. Se [Beskyt dine slutpunkter med Defender for Clouds integrerede Slutpunktsregistrering og -svar: Microsoft Defender til slutpunkt](/azure/security-center/security-center-wdatp#enable-the-microsoft-defender-for-endpoint-integration).

## <a name="group-policy-configuration"></a>Gruppepolitik konfiguration
Hvis du vil konfigurere Gruppepolitik, skal du sikre dig, at du bruger de nyeste ADMX-filer i din central butik for at få adgang til de korrekte politikindstillinger for Defender til Endpoint. Se Sådan opretter og administrerer du [Central Store til Gruppepolitik](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) administrative skabeloner i Windows og download de nyeste filer til brug med **Windows 10**.
