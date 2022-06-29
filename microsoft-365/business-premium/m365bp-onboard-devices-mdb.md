---
title: Onboarde din organisations enheder for at Microsoft Defender til virksomheder
description: Onboarde din organisations enheder for at Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 7d86b04b1c3883bc5b3da0e429dbbddd8275622f
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489508"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Onboarde tilmeldte enheder til Microsoft Defender til virksomheder

Nu, hvor du har tilmeldt enhederne, skal du onboarde dem til Microsoft Defender til virksomheder til at implementere næste generations beskyttelse (antivirus, antimalware og skybaseret beskyttelse), firewallbeskyttelse, filtrering af webindhold og meget mere. 

Hvis du vil onboarde enheder, kan du vælge mellem flere muligheder:

- [Brug automatisk onboarding til Windows-enheder, der allerede er tilmeldt Microsoft Endpoint Manager](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [Brug et lokalt script til at onboarde Windows- og macOS-enheder](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [Brug Endpoint Manager til at tilmelde enheder](#use-microsoft-endpoint-manager-to-enroll-devices) (Windows, macOS, iOS og Android) og derefter anvende Defender for Business-politikker på disse enheder

Denne artikel indeholder også:

- [Sådan kører du en registreringstest på en Windows-enhed](#run-a-detection-test-on-a-windows-device)

- [Sådan onboarder du enheder gradvist](#onboard-devices-gradually)

- [Sådan offboardes en enhed](#offboard-a-device) , hvis en enhed erstattes, eller nogen forlader organisationen

> [!IMPORTANT]
> Hvis noget går galt, og din onboardingproces mislykkes, [kan du se Microsoft Defender til virksomheder fejlfinding](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>Brug automatisk onboarding til Windows-enheder, der allerede er tilmeldt Microsoft Endpoint Manager

Indstillingen for automatisk onboarding gælder kun for Windows-enheder. Automatisk onboarding er tilgængelig, hvis følgende betingelser er opfyldt:

- Din organisation brugte allerede Microsoft Endpoint Manager, Microsoft Intune eller Mobile Enhedshåndtering (MDM) i Microsoft Intune, før du fik Defender for Business (Microsoft 365 Business Premium  kunder allerede har Microsoft Intune).

- Du har allerede Windows-enheder tilmeldt Endpoint Manager.

Hvis Windows-enheder allerede er tilmeldt Endpoint Manager, registrerer Defender for Business disse enheder, mens du er i gang med at konfigurere Defender for Business. Du bliver spurgt, om du vil bruge automatisk onboarding til alle eller nogle af dine Windows-enheder. Du kan onboarde alle Windows-enheder på én gang, eller du kan vælge bestemte enheder, du vil starte med, og derefter tilføje flere enheder senere.

> [!TIP]
> Vi anbefaler, at du vælger indstillingen "alle de enheder, der er tilmeldt". På den måde bliver Windows-enheder automatisk onboardet til Defender for Business, når de er tilmeldt Endpoint Manager senere.
Hvis du vil vide mere om automatisk onboarding, skal du se Trin 2 i [Brug guiden til at konfigurere Microsoft Defender til virksomheder](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>Brug et lokalt script til at onboarde Windows- og macOS-enheder

Du kan bruge et lokalt script til at onboarde Windows- og Mac-enheder. Når du kører onboardingscriptet på en enhed, oprettes der et tillidsforhold til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmeldes enheden i Microsoft Endpoint Manager (hvis den ikke allerede er tilmeldt) og onboarder derefter enheden til Defender for Business. Denne metode er nyttig til onboarding af enheder i Defender for Business. Du kan onboarde op til 10 enheder ad gangen.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** > **Slutpunkter** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg et operativsystem, f.eks **. Windows 10 og 11** eller **macOS**, og vælg derefter **Lokalt script** i afsnittet **Installationsmetode**. 

4. Vælg **Download onboarding-pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev. Hvis du har valgt **macOS**, skal du også vælge **Download installationspakke** og gemme den på din flytbare enhed.

5. Brug følgende vejledning:

   - [Windows-enheder: Onboard Windows-enheder ved hjælp af et lokalt script](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - macOS-enheder: [Manuel installation af Microsoft Defender for Endpoint på macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>Brug Microsoft Endpoint Manager til at tilmelde enheder

Hvis du vil tilmelde en enhed, skal du selv tilmelde den eller få dine brugere til at logge på firmaportalen og tilmelde og installere de apps, der er nødvendige. 

Hvis du allerede har brugt Endpoint Manager (herunder Microsoft Intune og mobil Enhedshåndtering), kan du fortsætte med at bruge Endpoint Manager til at onboarde din organisations enheder, før du fik Defender for Business. Med Endpoint Manager kan du onboarde computere, tablets og telefoner, herunder iOS- og Android-enheder.

Se [Tilmelding af enhed i Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>Kør en registreringstest på en Windows-enhed

Når du har onboardet Windows-enheder til Defender for Business, kan du køre en registreringstest på en Windows-enhed for at sikre, at alt fungerer korrekt.

1. Opret en mappe på Windows-enheden: `C:\test-MDATP-test`.

2. Åbn kommandoprompten som administrator.

3. Kør følgende PowerShell-kommando i vinduet Kommandoprompt:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes kommandopromptvinduet automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed om ca. 10 minutter.

## <a name="onboard-devices-gradually"></a>Om bord på enheder gradvist

Hvis du foretrækker at onboarde enheder i faser, som vi kalder *gradvis onboarding af enheder*, skal du følge disse trin: 

1. Identificer et sæt enheder, der skal onboarde.

2. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

3. Vælg **Indstillinger** > **Slutpunkter** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

4. Vælg et operativsystem (f.eks **. Windows 10 og 11),** og vælg derefter en onboardingmetode (f.eks **. Lokalt script**). Følg vejledningen for den valgte metode.

5. Gentag denne proces for hvert sæt enheder, du vil onboarde. 

> [!TIP]
> Du behøver ikke at bruge den samme onboardingpakke, hver gang du onboarder enheder. Du kan f.eks. bruge et lokalt script til at onboarde nogle enheder, og senere kan du vælge en anden metode til at onboarde flere enheder.

## <a name="offboard-a-device"></a>Uden for en enhed

Hvis du vil være ombord på en enhed, skal du bruge en af følgende procedurer:

1. Vælg **Indstillinger** i navigationsruden, og vælg derefter **Slutpunkter**.

1. Under **Enhedshåndtering** skal du vælge **Offboarding**.

1. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter **Lokalt script** under **Offboard en enhed** i afsnittet **Installationsmetode**. 

1. Gennemse oplysningerne på bekræftelsesskærmen, og vælg derefter **Download** for at fortsætte.

1. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.

1. Kør scriptet på hver enhed, du vil offboarde. Har du brug for hjælp til denne opgave? Se følgende ressourcer:   

   - Windows-enheder: [Offboard Windows-enheder ved hjælp af et lokalt script](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - macOS-enheder: [Fjernelse på macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Hvis du om bord på en enhed holder op med at sende data til Defender for Business. Data, der modtages før offboarding, opbevares dog i op til seks (6) måneder.

## <a name="next-objective"></a>Næste mål

[Konfigurer beskyttelse af dine Windows-enheder](m365bp-protection-settings-for-windows-10-devices.md).
