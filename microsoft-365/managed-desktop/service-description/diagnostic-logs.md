---
title: Diagnostiske logfiler
description: Logfiler, der kan indsamles fra enheder under fejlfinding, og hvordan de gemmes
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 808ce2e426a0540c95195f26c9872f569e595715
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63592197"
---
# <a name="diagnostic-logs"></a>Diagnostiske logfiler

Uanset om du har rapporteret et problem, eller om et problem er blevet identificeret af vores tjeneste, kan det være nødvendigt at indsamle visse diagnostiske logfiler fra enheden uden handling fra brugeren.

Vi indsamler ikke brugergenereret indhold eller oplysninger fra brugermapper. Vi indsamler kun diagnostiske og logdata, der vedrører enhedens tilstand og status.

Vi gemmer alle indsamlede logfiler i 28 dage og sletter dem derefter. Vi behandler alle logfiler, der indsamles fra en enhed, efter vores [standarder for datahåndtering](privacy-personal-data.md).

## <a name="data-collected"></a>Data, der indsamles

Denne liste nedenfor indeholder alle de mapper, hændelseslogfiler, eksekverbare filer eller registreringsdatabaseplaceringer, som Microsoft Managed Desktop kan indsamle diagnostiske logfiler fra. De faktiske data, der indsamles, vil være et undersæt af denne liste og afhænger af det identificerede problem.

### <a name="registry-keys"></a>Registreringsdatabasenøgler

- HKLMSYSTEMCurrentControlSetServices\\\\\\
- HKLMSOFTWAREMicrosoftSurface\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows\\ WindowsUpdate
- HKLMSYSTEMCurrentControlSetControlMUIUILanguages\\\\\\\\\\
- HKLMSoftwarePoliciesMicrosoftWindowsStore\\\\\\\\
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionWindowsStoreWindowsUpdate\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppModel\\
- HKLMSYSTEMCurrentControlSetControlFirmwareResources\\\\\\\\
- HKLMSOFTWAREMicrosoftWindowsSelfhost\\\\\\
- HKLMSOFTWAREMicrosoftWindowsUpdate\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppx\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows NTCurrentVersionSuperfetch\\\\
- HKLMSYSTEMSetup\\\\
- HKLMSoftwareMicrosoftIntuneManagementExtension\\\\\\
- HKLMSOFTWAREMicrosoftSystemCertificatesAuthRoot\\\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows Advanced Threat Protection
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAuthenticationLogonUI\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionInternet\\ Indstillinger
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSoftwarePolicies\\\\
- HKLMSOFTWAREPoliciesMicrosoftCryptographyConfigurationSSL\\\\\\\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows Advanced Threat Protection
- HKLMSOFTWAREWOW6432NodeMicrosoft\\\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSYSTEMCurrentControlSetControlSecurityProvidersSCHANNEL\\\\\\\\\\

### <a name="commands"></a>Kommandoer

- %programfiles%\\windows defender\\mpcmdrun.exe -GetFiles
- %windir%\\system32\\certutil.exe -store
- %windir%\\system32\\certutil.exe -store -user my
- %windir%\\system32\\Dsregcmd.exe/status
- %windir%\\system32\\ipconfig.exe/all
- %windir%\\system32\\ipconfig.exe/displaydns
- %windir%\\system32\\mdmdiagnosticstool.exe
- %windir%\\system32\\msinfo32.exe /report %temp%\\MDMDiagnosticsmsinfo32.log\\
- %windir%\\system32\\netsh.exe advfirewall show allprofiles
- %windir%\\system32\\netsh.exe advfirewall show global
- %windir%\\system32\\netsh.exe lan show profiles
- %windir%\\system32\\netsh.exe winhttp show proxy
- %windir%\\system32\\netsh.exe wlan show profiles
- %windir%\\system32\\netsh.exe wlan show wlanreport
- %windir%\\system32\\ping.exe -n 50 localhost
- %windir%\\system32\\powercfg.exe/batteryreport /output %temp%\\MDMDiagnostics\\battery-report.html
- %windir%\\system32\\powercfg.exe /energy/output %temp%\\MDMDiagnostics\\energy-report.html
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -arne -get
- Windows PowerShell kommandoer:
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype bundle
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32product\_
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32PnPSignedDriver\_

### <a name="event-logs"></a>Hændelseslogfiler

- Program
- Microsoft-Windows-AppLocker/EXE og DLL
- Microsoft-Windows-AppLocker/MSI og Script
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Administration af Microsoft-Windows-BitLocker/BitLocker
- Microsoft-Windows-SENSE/Drift
- Microsoft-Windows-SenseIR/Drift
- Konfiguration
- System

### <a name="files"></a>Filer

- %ProgramData%\\MicrosoftDiagnosticLogCSPCollectors.etl\\\\\\\*
- %ProgramData%\\MicrosoftIntuneManagementExtensionLogs\\\\\\\*.\*
- %ProgramData%\\Microsoft\\ Windows Defender\\ Support\\MpSupportFiles.cab
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport\\wlan-report-latest.html
- %ProgramData%\\Microsoft\\ Windows\\ WlanReport -SourceFileName wlan-report-latest.html
- %windir%\\ccmlogs.log\\\*
- %windir%\\ccmsetuplogs.log\\\*
- %windir%\\logsCBScbs.log\\\\
- %windir%\\logsmeasuredboot\*\\.\*
- %windir%\\LogsWindowsUpdate.etl\\\*
- %windir%\\inf.log\\\*
- %windir%\\servicingsessions\\\\ActionList.xml
- %windir%\\servicingsessions\\\\Sessions.xml
- %windir%\\SoftwareDistributionDataStoreLogsedb.log\\\\\\
- %windir%\\SoftwareDistributionDataStoreDataStore.edb\\\\
- %windir%\\logsdismdism.log\\\\
- %SystemRoot%\\System32WinevtLogs\\\\\\
- %appdata%\\Microsoft\\ Teams\\ media-stack.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ skylib.blog\\\*
- %appdata%\\Microsoft\\ Teams\\ media-stack.etl\\\*
- %appdata%\\Microsoft\\ Teams\\logs.txt
- %windir%\\Windows System32winevt\\\\\*.\\\*