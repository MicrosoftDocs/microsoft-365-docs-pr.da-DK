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
ms.date: 07/19/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 0578aa2e672a0d485057ac983ed85d10828c952d
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893969"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>Onboarde tilmeldte enheder til Microsoft Defender til virksomheder

Microsoft 365 Business Premium omfatter [Microsoft Defender til virksomheder](../security/defender-business/mdb-overview.md), som er en sikkerhedsløsning til små og mellemstore virksomheder. Defender for Business sikrer næste generations beskyttelse (antivirus, antimalware og skybaseret beskyttelse), firewallbeskyttelse, filtrering af webindhold og meget mere til din virksomheds enheder. Beskyttelse anvendes, når du onboarder enheder og anvender sikkerhedspolitikker på disse enheder.

Hvis du vil onboarde enheder til Defender for Business, kan du vælge mellem flere muligheder:

- [Automatisk onboarding til Windows-enheder, der allerede er tilmeldt Microsoft Intune](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune)
- [Et lokalt script til onboarding af Windows- og Mac-enheder til Defender for Business](#use-a-local-script-to-onboard-windows-and-mac-devices-to-defender-for-business) (for enheder, der ikke allerede er tilmeldt Intune)
- [Intune til tilmelding af nye enheder, herunder mobilenheder](#use-intune-to-enroll-devices) (Windows, Mac, iOS og Android), og anvend derefter Defender for Business-politikker på disse enheder

Denne artikel indeholder også:

- [Hvad med servere?](#what-about-servers) (NY!)
- [Sådan kører du en registreringstest på en Windows-enhed](#run-a-detection-test-on-a-windows-device)
- [Sådan onboarder du enheder gradvist](#onboard-devices-gradually)
- [Sådan offboardes en enhed](#offboard-a-device) , hvis en enhed erstattes, eller nogen forlader organisationen

> [!IMPORTANT]
> Hvis noget går galt, og din onboardingproces mislykkes, [kan du se Microsoft Defender til virksomheder fejlfinding](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune"></a>Brug automatisk onboarding til Windows-enheder, der allerede er tilmeldt Intune

Du kan automatisk onboarde Windows-klientenheder til Defender for Business, hvis disse enheder allerede er tilmeldt Intune. Defender for Business registrerer Windows-klientenheder, der allerede er tilmeldt Intune, og beder dig om at vælge, om du vil onboarde disse enheder automatisk. Sikkerhedspolitikker og -indstillinger i Defender for Business anvendes derefter på disse enheder. Vi kalder denne proces *for automatisk onboarding*. 

Automatisk onboarding hjælper med at beskytte dine enheder næsten med det samme. Bemærk, at den automatiske onboarding-indstilling kun gælder for Windows-klientenheder, hvis følgende betingelser er opfyldt:

- Organisationen brugte allerede Intune eller MDM (Mobile Enhedshåndtering) i Intune, før du fik Defender for Business (Microsoft 365 Business Premium kunder allerede har Microsoft Intune og MDM).
- Du har allerede windows-klientenheder tilmeldt Intune.

> [!TIP]
> Hvis du bliver bedt om at bruge automatisk onboarding, anbefaler vi, at du vælger indstillingen "alle tilmeldte enheder". På den måde bliver Windows-enheder automatisk onboardet til Defender for Business, når de er tilmeldt Intune senere.

Hvis du vil vide mere om automatisk onboarding, skal du se [Brug guiden til at konfigurere Microsoft Defender til virksomheder](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-mac-devices-to-defender-for-business"></a>Brug et lokalt script til at onboarde Windows- og Mac-enheder til Defender for Business

Du kan bruge et lokalt script til at onboarde Windows- og Mac-enheder. Når du kører onboardingscriptet på en enhed, oprettes der et tillidsforhold til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmeldes enheden i Intune (hvis den ikke allerede er tilmeldt), og onboarder derefter enheden til Defender for Business. Du kan onboarde op til 10 enheder ad gangen ved hjælp af det lokale script.

Se [Onboard-enheder til Microsoft Defender til virksomheder for at](../security/defender-business/mdb-onboard-devices.md) få detaljerede instruktioner.

## <a name="use-intune-to-enroll-devices"></a>Brug Intune til at tilmelde enheder

Hvis du vil tilmelde en enhed, kan du selv tilmelde den, eller du kan få brugerne til at logge på firmaportalappen, tilmelde deres enheder og derefter installere de apps, der er nødvendige. 

Hvis du allerede brugte Intune eller mobil Enhedshåndtering, før du fik Defender for Business, kan du fortsætte med at bruge Intune til at onboarde din organisations enheder. Med Intune kan du onboarde computere, tablets og telefoner, herunder iOS- og Android-enheder.

Se [Tilmelding af enhed i Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="what-about-servers"></a>Hvad med servere?

Servere understøttes som standard ikke i Microsoft 365 Business Premium og den separate version af Defender for Business. Muligheden **for at onboarde en server, f.eks. et slutpunkt, der kører Windows Server eller Linux Server, fås nu som prøveversion**! 

Se [Sådan får du Microsoft Defender til virksomheder servere (prøveversion)](../security/defender-business/get-defender-business-servers.md).

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

2. Under **Enhedshåndtering** skal du vælge **Offboarding**.

3. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter **Lokalt script** under **Offboard en enhed** i afsnittet **Installationsmetode**. 

4. Gennemse oplysningerne på bekræftelsesskærmen, og vælg derefter **Download** for at fortsætte.

5. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.

6. Kør scriptet på hver enhed, du vil offboarde. Har du brug for hjælp til denne opgave? Se følgende ressourcer:   

   - Windows-enheder: [Offboard Windows-enheder ved hjælp af et lokalt script](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) 
   - Mac: [Fjernelse på Mac](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Hvis du om bord på en enhed holder op med at sende data til Defender for Business. Data, der modtages før offboarding, opbevares dog i op til seks (6) måneder.

## <a name="next-objective"></a>Næste mål

[Konfigurer beskyttelse af dine Windows-enheder](m365bp-protection-settings-for-windows-10-devices.md).
