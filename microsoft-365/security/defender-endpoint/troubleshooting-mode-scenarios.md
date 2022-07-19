---
title: Fejlfindingstilstandsscenarier i Microsoft Defender for Endpoint
description: Brug Microsoft Defender for Endpoint fejlfindingstilstand til at løse forskellige antivirusproblemer.
keywords: antivirus, fejlfinding, fejlfindingstilstand, manipulationsbeskyttelse, kompatibilitet
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c4824c603fda14d95487abdbc4f3b4949fdf0e97
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66858755"
---
# <a name="troubleshooting-mode-scenarios-in-microsoft-defender-for-endpoint"></a>Fejlfindingstilstandsscenarier i Microsoft Defender for Endpoint 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Microsoft Defender for Endpoint fejlfindingstilstand giver dig mulighed for at foretage fejlfinding af forskellige Microsoft Defender Antivirus-funktioner ved at aktivere dem fra enheden og teste forskellige scenarier, også selvom de styres af organisationspolitikken. Fejlfindingstilstanden er deaktiveret som standard og kræver, at du aktiverer den for en enhed (og/eller gruppe af enheder) i en begrænset periode. Bemærk, at dette udelukkende er en funktion, der kun er til virksomheder, og som kræver Microsoft 365 Defender adgang.

## <a name="scenario-1-unable-to-install-application"></a>Scenarie 1: Programmet kan ikke installeres

Hvis du vil installere et program, men får vist en fejlmeddelelse om, at Microsoft Defender Antivirus og beskyttelse mod manipulation er slået til, skal du følge nedenstående trin for at foretage fejlfinding af problemet.

1. Bed sikkerhedsadministratoren om at aktivere fejlfindingstilstand. Du får en Windows Sikkerhed meddelelse, når fejlfindingstilstanden starter.  

2. Opret forbindelse til enheden (f.eks. ved hjælp af Terminal Services) med lokale administratortilladelser.  

3. Start procesovervågning (ProcMon). Se de trin, der er beskrevet i [Fejlfinding af problemer med ydeevnen, der er relateret til beskyttelse i realtid](troubleshoot-performance-issues.md).  

4. Gå til **Windows security** > **Threat & virusbeskyttelse** > **Administrer indstillinger** > **Ændringsbeskyttelse** > **Slået fra**.  

5. Start en PowerShell-kommandoprompt med administratorrettigheder, og slå RTP fra. 

    - Kør `Get-MpComputerStatus` for at kontrollere status for RealTimeProtection.
    - Kør `Set-mppreference -DisableRealtimeMonitoring $true` for at slå RTP fra.
    - Kør `Get-MpComputerStatus` igen for at bekræfte realtimeProtection-status.

6. Prøv at installere programmet.

## <a name="scenario-2-high-cpu-usage-due-to-windows-defender-msmpengexe"></a>Scenarie 2: Højt CPU-forbrug på grund af Windows Defender (MsMpEng.exe)

Nogle gange kan MsMpEng.exe bruge høj CPU under en planlagt scanning.

1. Gå til fanen **Detaljer** i **Jobliste** >  for at bekræfte, at MsMpEng.exe er årsagen til det høje CPU-forbrug. Kontrollér også, om en planlagt scanning er i gang i øjeblikket.

2. Kør ProcMon under CPU-spidsbelastning i ca. 5 minutter, og gennemse derefter ProcMon-loggen for spor. 

3. Når rodårsagen er bestemt, skal du slå fejlfindingstilstand til. 

4. Log på computeren, og start en PowerShell-kommandoprompt med administratorrettigheder. 

5. Tilføj process/file/folder/extension exclusions baseret på ProcMon-resultater ved hjælp af en af følgende kommandoer (stien, filtypenavnet og procesudeladelser, der er nævnt nedenfor, er kun eksempler): 

    - `Set-mppreference -ExclusionPath` (f.eks. C:\DB\DataFiles) 
    
    - `Set-mppreference –ExclusionExtension` (f.eks. .dbx) 
    
    - `Set-mppreference –ExclusionProcess` (f.eks. C:\DB\Bin\Convertdb.exe) 

6. Når du har tilføjet udeladelse, skal du kontrollere, om CPU-forbruget er faldet. 

Du kan få flere oplysninger om konfigurationsindstillinger for Set-MpPreference cmdlet for Windows Defender scanninger og opdateringer under [Angiv-MpPreference](/powershell/module/defender/set-mppreference). 

## <a name="scenario-3-application-taking-longer-to-perform-an-action"></a>Scenarie 3: Det tager længere tid for programmet at udføre en handling

Når Microsoft Defender Antivirus beskyttelse i realtid er slået til, tager programmet lang tid at udføre grundlæggende opgaver. Hvis du vil slå beskyttelse i realtid fra og foretage fejlfinding af problemet, skal du følge nedenstående trin. 

1. Anmod sikkerhedsadministratoren om at aktivere fejlfindingstilstand på enheden. 

2. Hvis du vil deaktivere RTP i dette scenarie, skal du først slå beskyttelse mod manipulation fra. Du kan få flere oplysninger under [Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md). 

3. Når manipulationsbeskyttelse er deaktiveret, skal du logge på enheden. 

4. Start en PowerShell-kommandoprompt med administratorrettigheder. 

    - `Set-mppreference -DisableRealtimeMonitoring $true` 

5. Når du har deaktiveret RTP, skal du kontrollere, om programmet er langsomt. 

## <a name="scenario-4-microsoft-office-plugin-blocked-by-attack-surface-reduction"></a>Scenarie 4: Microsoft Office-plug-in blokeret af Attack Surface Reduction

ASR (Attack Surface Reduction) tillader ikke, at Microsoft Office-plug-in fungerer korrekt, fordi **Bloker alle Office-programmer fra oprettelse af underordnede processer** er indstillet til bloktilstand. 

1. Slå fejlfindingstilstand til, og log på enheden. 

2. Start en PowerShell-kommandoprompt med administratorrettigheder. 

    - `Set-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EFC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions Disabled` 

3. Når du har deaktiveret ASR-reglen, skal du bekræfte, at Microsoft Office-plug-in'en nu fungerer.

Du kan få flere oplysninger under [Oversigt over reduktion af angrebsoverfladen](overview-attack-surface-reduction.md). 

## <a name="scenario-5-domain-blocked-by-network-protection"></a>Scenarie 5: Domæne blokeret af Network Protection

Network Protection blokerer Microsoft-domænet, hvilket forhindrer brugerne i at få adgang til det. 

1. Slå fejlfindingstilstand til, og log på enheden. 

2. Start en PowerShell-kommandoprompt med administratorrettigheder. 

    - `Set-MpPreference -EnableNetworkProtection Disabled` 

3. Når netværksbeskyttelse er deaktiveret, skal du kontrollere, om domænet nu er tilladt. 

Du kan finde flere oplysninger under [Brug netværksbeskyttelse til at forhindre forbindelser til forkerte websteder](network-protection.md). 

## <a name="related-topics"></a>Relaterede emner

- [Aktivér fejlfindingstilstand](enable-troubleshooting-mode.md)
- [Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md)
- [Set-MpPreference](/powershell/module/defender/set-mppreference)
- [Beskyt dit netværk](network-protection.md)
- [Oversigt over reduktion af angrebsoverflade](overview-attack-surface-reduction.md)
- [Find og bloker potentielt uønskede programmer](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Få et overblik over Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)
- [Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)
