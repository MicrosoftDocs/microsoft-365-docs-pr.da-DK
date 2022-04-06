---
title: Onboard din organisations enheder til at Microsoft Defender til virksomheder
description: Onboard din organisations enheder til at Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e9810b453136025e094ef8a0e88bff526f2c5a51
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634773"
---
# <a name="onboard-managed-devices-to-microsoft-defender-for-business"></a>Onboard administrerede enheder for at Microsoft Defender til virksomheder

Onboard-enheder til Microsoft Defender til virksomheder at beskytte dem med næste generations beskyttelse (antivirus, antimalware og cloud-leveret beskyttelse), firewallbeskyttelse, filtrering af webindhold og meget mere. 

Hvis du vil onboarde enheder, kan du vælge mellem flere forskellige muligheder:

- [Brug automatisk onboarding til Windows enheder, der allerede er tilmeldt Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Brug et lokalt script til at Windows og macOS-enheder](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Brug Endpoint Manager til at](#use-microsoft-endpoint-manager-to-enroll-devices) tilmelde enheder (Windows, macOS, iOS og Android), og anvend derefter Defender for Business-politikker på disse enheder

Denne artikel indeholder også:

- [Sådan køres en registreringstest på en Windows enhed](#run-a-detection-test-on-a-windows-device)

- [Sådan onboarder du enheder gradvist](#onboard-devices-gradually)

- [Sådan deaktiveres en enhed, hvis](#offboard-a-device) en enhed erstattes, eller en person forlader organisationen

> [!IMPORTANT]
> Hvis noget går galt, og din onboardingproces mislykkes, skal [du Microsoft Defender til virksomheder fejlfinding](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Brug automatisk onboarding til Windows enheder, der allerede er tilmeldt Microsoft Endpoint Manager

Indstillingen automatisk onboarding gælder kun for Windows enheder. Automatisk onboarding er tilgængelig, hvis din organisation allerede brugte Microsoft Endpoint Manager, Microsoft Intune eller MdM (Mobile Enhedshåndtering) i Microsoft Intune, før du fik Defender for Business, og du allerede har Windows  enheder, der er tilmeldt Endpoint Manager. 

Hvis Windows-enheder allerede er tilmeldt Endpoint Manager, registrerer Defender for Business disse enheder, mens du er i gang med at konfigurere Defender for Business. Du bliver spurgt, om du vil bruge automatisk onboarding til alle eller nogle af dine Windows enheder. Du kan onboarde Windows-enheder på én gang, eller du kan vælge specifikke enheder, du vil starte med, og derefter tilføje flere enheder senere.

Du kan få mere at vide om automatisk onboarding under Trin 2 [i Brug guiden til at konfigurere Microsoft Defender til virksomheder](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Brug et lokalt script til at Windows og macOS-enheder

Du kan bruge et lokalt script til at Windows- og macOS-enheder. Når du kører onboarding-scriptet på en enhed, opretter det en tillid til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmelder enheden i Microsoft Endpoint Manager (hvis den ikke allerede er tilmeldt) og onboarder derefter enheden til Defender for Business. 

Du kan onboarde op til 10 enheder ad gangen med denne metode.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. I navigationsruden skal du **vælge Indstillinger** >  **Endpoints**, og derefter skal du under **Enhedshåndtering** vælge **Onboarding**.

3. Vælg et operativsystem, f.eks **. Windows 10 og 11**, **og vælg derefter** Lokalt script i sektionen Installationsmetode under Onboard **en enhed**. 

4. Vælg **Download onboarding pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev.

5. Følg vejledningen i følgende artikler:

   - Windows-enheder: [Onboard Windows-enheder ved hjælp af et lokalt script](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - macOS-enheder: [Manuel udrulning Microsoft Defender for Endpoint på macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Brug Microsoft Endpoint Manager til at tilmelde enheder

Hvis du allerede brugte Endpoint Manager (som omfatter Microsoft Intune og Mobile Enhedshåndtering), kan du, før du fik Defender for Business, fortsætte med at bruge Endpoint Manager til at onboarde din organisations enheder. Med Endpoint Manager kan du onboarde computere, tablets og telefoner, herunder iOS- og Android-enheder.

Hvis din organisation bruger Android-enheder, skal du bruge denne metode.

Se [Tilmelding til enhed Microsoft Intune](/mem/intune/enrollment/device-enrollment).


## <a name="run-a-detection-test-on-a-windows-device"></a>Kør en registreringstest på en Windows enhed

Når du har onboardet Windows-enheder til Defender for Business, kan du køre en registreringstest på en Windows-enhed for at sikre, at alt fungerer korrekt.

1. På Windows skal du oprette en mappe: `C:\test-MDATP-test`.

2. Åbn Kommandoprompt som administrator.

3. I vinduet Kommandoprompt skal du køre følgende PowerShell-kommando:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes vinduet Kommandoprompt automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed på ca. 10 minutter.

## <a name="onboard-devices-gradually"></a>Onboard-enheder gradvist

Hvis du foretrækker at onboarde enheder i faser, som vi kalder gradvis *onboarding af enheder*, skal du følge disse trin: 

1. Identificer et sæt af enheder, der skal onboarde.

2. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

3. I navigationsruden skal du **vælge Indstillinger** >  **Endpoints**, og derefter skal du under **Enhedshåndtering** vælge **Onboarding**.

4. Vælg et operativsystem (f.eks. **Windows 10 og 11),** og vælg derefter en onboardingmetode (f.eks. **Lokalt script**). Følg vejledningen for den metode, du har valgt.

5. Gentag denne proces for hvert sæt af enheder, du vil onboarde. 

> [!TIP]
> Du behøver ikke at bruge den samme onboardingpakke, hver gang du onboarder enheder. Du kan f.eks. bruge et lokalt script til at onboarde visse enheder, og senere kan du vælge en anden metode til at onboarde flere enheder.

## <a name="offboard-a-device"></a>Offboard a device

Hvis du vil deaktivere en enhed, skal du følge disse trin:

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. I navigationsruden skal **du Indstillinger** slutpunkter og derefter **vælge Slutpunkter**.

3. Under **Enhedshåndtering** skal du **vælge Offboarding**.

4. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter Lokalt script i sektionen Installationsmetode under **Fraboard** **en enhed**. 

5. Gennemse oplysningerne i bekræftelsesskærmbilledet, og vælg derefter **Download for at** fortsætte.

6. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.

7. Kør scriptet på hver enhed, du vil offboarde. Har du brug for hjælp til denne opgave? Se følgende ressourcer:   

   - Windows enheder: [Offboard Windows enheder, der bruger et lokalt script](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - macOS-enheder: [Fjern på macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Offboarding af en enhed får enhederne til at holde op med at sende data til Defender for Business. Men data, der modtages før offboarding, bevares i op til seks (6) måneder.

## <a name="next-steps"></a>Næste trin

[Gennemse afhjælpningshandlinger i Microsoft 365 Business Premium](m365bp-review-remediation-actions-devices.md)