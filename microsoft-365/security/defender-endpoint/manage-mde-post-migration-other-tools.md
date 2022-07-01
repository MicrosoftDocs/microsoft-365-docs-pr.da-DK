---
title: Administrer Microsoft Defender for Endpoint ved hjælp af PowerShell, WMI og MPCmdRun.exe
description: Få mere at vide om, hvordan du administrerer Microsoft Defender for Endpoint med PowerShell, WMI og MPCmdRun.exe
keywords: efter migrering, administration, drift, vedligeholdelse, udnyttelse, PowerShell, WMI, MPCmdRun.exe, Microsoft Defender for Endpoint, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 51ead270b8e8223b2fd67cfd5fb1cf4e9f8a05d4
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603291"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Administrer Microsoft Defender for Endpoint med PowerShell, WMI og MPCmdRun.exe

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem) til at administrere organisationens trusselsbeskyttelsesfunktioner for enheder (også kaldet slutpunkter). Endpoint Manager omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Microsoft Endpoint-Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [Få mere at vide om Endpoint Manager](/mem/endpoint-manager-overview)
> - [Samtidig administration af Microsoft Defender for Endpoint på Windows 10 og Windows 11 enheder med Configuration Manager og Intune](manage-mde-post-migration-intune.md)
> - [Administrer Microsoft Defender for Endpoint med Intune](manage-mde-post-migration-intune.md)

Du kan administrere nogle Microsoft Defender Antivirus-indstillinger på enheder med [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell), WMI (  [Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) ) og [Kommandolinjeværktøjet Microsoft Malware Protection](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Du kan f.eks. administrere nogle indstillinger for Microsoft Defender Antivirus. Og i nogle tilfælde kan du tilpasse dine regler for reduktion af angrebsoverfladen og udnytte beskyttelsesindstillinger.

> [!IMPORTANT]
> Trusselsbeskyttelsesfunktioner, som du konfigurerer ved hjælp af PowerShell, WMI eller MCPmdRun.exe, kan overskrives af konfigurationsindstillinger, der er installeret sammen med Intune eller Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Konfigurer Microsoft Defender for Endpoint med PowerShell

Du kan bruge PowerShell til at administrere Microsoft Defender Antivirus, udnytte beskyttelse og dine regler for reduktion af angrebsoverfladen.

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrer Microsoft Defender Antivirus** <br/><br/> Få vist status for beskyttelse mod antimalware, konfigurer indstillinger for antivirusscanninger & opdateringer, og foretag andre ændringer af antivirusbeskyttelsen.*|[Brug PowerShell-cmdlet'er til at konfigurere og administrere Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Brug PowerShell-cmdlet'er til at aktivere skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Konfigurer beskyttelse mod udnyttelse** for at afhjælpe trusler på din organisations enheder <br/><br/> *Vi anbefaler, at du bruger beskyttelse mod udnyttelse i [overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) i starten. På den måde kan du se, hvordan udnyttelsesbeskyttelse påvirker de apps, din organisation bruger.*|[Tilpas Exploit Protection](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [PowerShell-cmdlet'er til beskyttelse mod udnyttelse](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Konfigurer regler for reduktion af angrebsoverfladen** med PowerShell <br/><br/> *Du kan bruge PowerShell til at udelukke filer og mapper fra regler for reduktion af angrebsoverfladen.*|[Tilpas regler for reduktion af angrebsoverflade: Brug PowerShell til at udelade filer & mapper](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction) <br/><br/> Se også [António Vasconcelo's grafiske brugergrænsefladeværktøj til angivelse af regler for reduktion af angrebsoverflader med PowerShell](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI).|
|**Aktivér netværksbeskyttelse** med PowerShell <br/><br/> *Du kan bruge PowerShell til at aktivere Netværksbeskyttelse.*|[Slå Netværksbeskyttelse til med PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Konfigurer kontrolleret mappeadgang** for at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomware-beskyttelse.*|[Aktivér kontrolleret mappeadgang med PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Konfigurer Microsoft Defender Firewall** til at blokere uautoriseret netværkstrafik, der strømmer ind eller ud af organisationens enheder|[Microsoft Defender Firewall med Avanceret sikkerhedsadministration ved hjælp af Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Konfigurer kryptering og BitLocker** for at beskytte oplysninger på din organisations enheder, der kører Windows|[Referencevejledning til BitLocker PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Konfigurer Microsoft Defender for Endpoint med WMI (Windows Management Instrumentation)

WMI er en scriptgrænseflade, der giver dig mulighed for at hente, redigere og opdatere indstillinger. Du kan få mere at vide under [Brug af WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Aktivér skybaseret beskyttelse** på en enhed|[Brug WMI (Windows Management Instruction) til at aktivere skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Hent, rediger og opdater indstillinger** for Microsoft Defender Antivirus|[Brug WMI til at konfigurere og administrere Microsoft Defender Antivirus] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Gennemse listen over tilgængelige WMI-klasser og eksempelscripts](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Se også de arkiverede [referenceoplysninger for Windows Defender WMIv2-udbyder](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Konfigurer Microsoft Defender for Endpoint med Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe)

På en individuel enhed kan du køre en scanning, starte diagnosticeringssporing, søge efter sikkerhedsopdateringer og meget mere ved hjælp af kommandolinjeværktøjet mpcmdrun.exe. Du kan finde værktøjet i `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Kør den fra en kommandoprompt.

Du kan få mere at vide under [Konfigurer og administrer Microsoft Defender Antivirus med mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurer Microsoft 365 Defender-portalen

Hvis du ikke allerede har gjort det, kan du konfigurere <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">din Microsoft 365 Defender-portal</a> til at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om din organisations overordnede sikkerhedsholdning.

Du kan også konfigurere, om og hvilke funktioner slutbrugerne kan se i Microsoft Defender Security Center.

- [Oversigt over Microsoft Defender Security Center](/microsoft-365/security/defender-endpoint/use)
- [Slutpunktsbeskyttelse: Microsoft Defender Security Center](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Besøg dashboardet Microsoft Defender Security Center sikkerhedshandlinger](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [Administrer Microsoft Defender for Endpoint med Intune](manage-mde-post-migration-intune.md)
