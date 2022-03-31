---
title: Administrer Microsoft Defender for Slutpunkt ved hjælp af PowerShell, WMI og MPCmdRun.exe
description: Få mere at vide om, hvordan du administrerer Microsoft Defender til slutpunkt med PowerShell, WMI og MPCmdRun.exe
keywords: efter overførslen, administrere, handlinger, vedligeholdelse, udnyttelse, PowerShell, WMI, MPCmdRun.exe, Microsoft Defender til slutpunkt, edr
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
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: b5794b978e35faa23df51528a077fe90444fdce1
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/30/2021
ms.locfileid: "63601050"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>Administrer Microsoft Defender til slutpunkt med PowerShell, WMI og MPCmdRun.exe

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Vi anbefaler at [Microsoft Endpoint Manager til](/mem) at administrere organisationens funktioner til trusselsbeskyttelse af enheder (også kaldet slutpunkter). Endpoint Manager omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Microsoft Endpoint Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [Få mere at vide Endpoint Manager](/mem/endpoint-manager-overview)
> - [Administrer Microsoft Defender for Slutpunkt på Windows 10 og Windows 11 enheder med Konfigurationsstyring og Intune](manage-mde-post-migration-intune.md)
> - [Administrer Microsoft Defender til slutpunkt med Intune](manage-mde-post-migration-intune.md)

Du kan administrere nogle Microsoft Defender Antivirus-indstillinger på enheder med [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell), [Windows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) og [Microsoft Malware Protection Command Line Utility](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). Du kan f.eks. administrere nogle Microsoft Defender Antivirus indstillinger. Og i nogle tilfælde kan du tilpasse dine reduktionsregler for angrebsoverfladen og udnytte beskyttelsesindstillingerne.

> [!IMPORTANT]
> Funktioner til trusselsbeskyttelse, som du konfigurerer ved hjælp af PowerShell, WMI eller MCPmdRun.exe, kan overskrives ved hjælp af konfigurationsindstillinger, der er installeret med Intune eller Konfigurationsstyring.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>Konfigurer Microsoft Defender til slutpunkt med PowerShell

Du kan bruge PowerShell til at administrere Microsoft Defender Antivirus, udnytte beskyttelsen og dine regler for reduktion af angrebsoverfladen.<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrer Microsoft Defender Antivirus** <br/><br/> Få vist status for beskyttelse mod antimalware, konfigurer indstillinger for antivirusscanninger & opdateringer, og foretag andre ændringer af din antivirusbeskyttelse.*|[Brug PowerShell-cmdlet'er til at konfigurere og administrere Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [Brug PowerShell-cmdlet'er til at aktivere skybaseret leveringsbeskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**Konfigurer udnyttelse af** beskyttelse for at afhjælpe trusler på organisationens enheder <br/><br/> *Vi anbefaler, at du bruger [udnyttelsesbeskyttelse i overvågningstilstand](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) i første omgang. På den måde kan du se, hvordan udnyttelse af beskyttelse påvirker apps, som din organisation bruger.*|[Tilpasse udnyttelsesbeskyttelse](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [PowerShell-cmdlet'er til udnyttelse af beskyttelse](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**Konfigurer regler for reduktion af angrebsoverfladen** med PowerShell <br/><br/> *Du kan bruge PowerShell til at udelukke filer og mapper fra regler for reduktion af angrebsoverfladen.*|[Tilpas regler for reduktion af angrebsoverfladen: Brug PowerShell til at udelukke filer & mapper](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders) <br/><br/> Se også [António Vasconcelo's](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI) grafiske brugergrænsefladeværktøj til indstilling af regler for reduktion af angrebsoverfladen med PowerShell.|
|**Aktivér netværksbeskyttelse** med PowerShell <br/><br/> *Du kan bruge PowerShell til at aktivere netværksbeskyttelse.*|[Aktivere netværksbeskyttelse med PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**Konfigurer styret mappeadgang for** at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomwarebeskyttelse.*|[Aktivér styret mappeadgang med PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**Konfigurer Microsoft Defender Firewall** til at blokere uautoriseret netværkstrafik, der flyder ind eller ud af organisationens enheder|[Microsoft Defender Firewall med Advanced Security Administration ved hjælp Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**Konfigurer kryptering og BitLocker** til at beskytte oplysninger på organisationens enheder, der kører Windows|[BitLocker PowerShell-referencevejledning](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>Konfigurer Microsoft Defender til slutpunkt med Windows Management Instrumentation (WMI)

WMI er en scripting-grænseflade, der gør det muligt at hente, redigere og opdatere indstillinger. Du kan få mere at vide [under Brug af WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Aktivér beskyttelse i skyen** på en enhed|[Brug Windows -administrationsvejledning (WMI) til at aktivere skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**Hent, rediger og opdater indstillinger** for Microsoft Defender Antivirus|[Brug WMI til at konfigurere og administrere Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [Gennemse listen over tilgængelige WMI-klasser og eksempelscripts](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> Se også de arkiverede [Windows Defender WMIv2-udbyderreferenceoplysninger](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>Konfigurer Microsoft Defender til slutpunkt med Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe)

På en enkelt enhed kan du køre en scanning, starte diagnosticeringssporing, søge efter sikkerhedsintelligensopdateringer og meget mere ved mpcmdrun.exe kommandolinjeværktøjet. Du kan finde værktøjet i `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. Kør den fra en kommandoprompt.

Du kan få mere at vide [under Konfigurer og administrer Microsoft Defender Antivirus med mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurere din Microsoft 365 Defender portal

Hvis du ikke allerede har gjort det, skal du konfigurere <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">din Microsoft 365 Defender-portal</a> for at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om organisationens overordnede sikkerhedsstilling.

Du kan også konfigurere, om og hvilke funktioner slutbrugere kan se i Microsoft Defender Security Center.

- [Oversigt over Microsoft Defender Security Center](/microsoft-365/security/defender-endpoint/use)

- [Slutpunktsbeskyttelse: Microsoft Defender Security Center](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [Gå til Microsoft Defender Security Center med dashboardet for sikkerhedshandlinger](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [Administrer Microsoft Defender til slutpunkt med Intune](manage-mde-post-migration-intune.md)
