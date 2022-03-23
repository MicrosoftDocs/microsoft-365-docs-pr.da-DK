---
title: Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Installér konfigurationspakken på en VDI-enhed (Virtual Desktop Infrastructure), så de er onboardet til Microsoft 365 endpoint-tjenesten til forebyggelse af datatab.
ms.openlocfilehash: 6ac13edde066319a5174234450dac67c29209b1b
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/12/2021
ms.locfileid: "63594679"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Onboard ikke-permanente virtuelle desktop-infrastrukturenheder

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- VDI-enheder (Virtual Desktop Infrastructure)

> [!WARNING]
> Microsoft 365 understøttelse af forebyggelse af datatab på slutpunktet i Windows Virtual Desktop understøtter scenarier med enkeltsessioner. Scenarier med flere sessioner på Windows virtuel skrivebord understøttes ikke i øjeblikket.

## <a name="onboard-vdi-devices"></a>Onboard VDI-enheder

Microsoft 365 understøtter ikke-permanent VDI-session (Virtual Desktop Infrastructure).

> [!NOTE]
> Hvis du vil onboarde ikke-permanente VDI-sessioner, skal VDI-enheder være på Windows 10 1809 eller nyere.

Der kan være udfordringer i forbindelse med onboarding af VDIs. Følgende er typiske udfordringer i dette scenarie:

- Øjeblikkelig tidlig onboarding af en kortvarig sessioner, som skal onboardes til en Microsoft 365 før den faktiske klargøring.
- Enhedsnavnet genbruges typisk til nye sessioner.

VDI-enheder kan vises i Microsoft 365 Compliance Center som enten:

- Enkelt indtastning for hver enhed.
Bemærk, at i dette tilfælde *skal det samme* enhedsnavn konfigureres, når sessionen oprettes, f.eks. ved hjælp af en uovervåget svarfil.
- Flere poster for hver enhed – én for hver session.

Følgende trin fører dig gennem onboarding VDI-enheder og fremhæver trin til enkelt og flere poster.

> [!WARNING]
> I miljøer, hvor der er lav ressourcekonfigurationer, kan VDI-startproceduren sænke onboardingprocessen for enheden.

1. Hent VDI-konfigurationspakken .zip (*DeviceCompliancePackage.zip*) fra [Microsoft Compliance Center](https://compliance.microsoft.com).

2. I navigationsruden skal du **vælge Indstillinger** >  **Enhed onboardingOnboarding** > .

3. I feltet **Installationsmetode** skal du vælge **VDI-onboardingscripts for ikke-permanente slutpunkter**.

4. Klik **på Download** pakke, og gem .zip fil.

5. Kopiér filerne fra mappen DeviceCompliancePackage, der er hentet fra .zip til billedet `golden/master` under stien `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Hvis du ikke implementerer en enkelt post for hver enhed, skal du kopiere DeviceComplianceOnboardingScript.cmd.

7. Hvis du implementerer en enkelt post for hver enhed, skal du kopiere Onboard-NonPersistentMachine.ps1 og DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Hvis du ikke kan se mappen `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , kan den være skjult. Du skal vælge indstillingen Vis **skjulte filer og mapper** i Stifinder.

8. Åbn et Lokalt Gruppepolitik Editor-vindue, og gå til **Computerkonfiguration** >  **Windows Indstillinger** >  **ScriptsStartup** > .

   > [!NOTE]
   > Domæneadministratorer Gruppepolitik også bruges til onboarding af ikke-permanente VDI-enheder.

9. Afhængigt af den metode, du gerne vil implementere, skal du følge de relevante trin:

   **For enkelt indtastning for hver enhed**

   Vælg fanen **PowerShell-scripts**, og klik derefter på **Tilføj (Windows** Stifinder åbnes direkte i den sti, hvor du kopierede onboarding-scriptet tidligere). Naviger til onboarding PowerShell-script `Onboard-NonPersistentMachine.ps1`.

   **For flere poster for hver enhed**:

   Vælg fanen **Scripts**, og klik **derefter på Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboarding-scriptet tidligere). Gå til onboarding bash-scriptet `DeviceComplianceOnboardingScript.cmd`.

10. Test din løsning:
    1. Opret en gruppe med én enhed.
    1. Logon på enhed.
    1. Logoff fra enhed.
    1. Log på enheden med en anden bruger.
    1. **Ved enkelt indtastning for hver enhed**: Kontrollér kun én post Microsoft Defender Security Center.
       **For flere poster for hver enhed**: Kontrollér flere poster i Microsoft Defender Security Center.

11. Klik **på listen Enheder** i ruden Navigation.

12. Brug søgefunktionen ved at skrive enhedens navn, og **vælg Enhed** som søgetype.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Opdatering af ikke-permanente VDI-billeder (Virtual Desktop Infrastructure)

Som bedste fremgangsmåde anbefaler vi, at du bruger offline-serviceværktøjer til at rette golden-/masterbilleder.

Du kan f.eks. bruge nedenstående kommandoer til at installere en opdatering, mens billedet forbliver offline:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

For more information on DISM commands and offline servicing, please to the articles below:

- [Modify a Windows image using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [DISM Image Management Command-Line Options](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Reducer størrelsen på Store i et offline Windows billede](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Hvis offline-servicering ikke er en realistisk mulighed for dit ikke-permanente VDI-miljø, skal du følge disse trin for at sikre ensartethed og sensortilstand:

1. Når du har startet masterbilledet med henblik på online-service eller programrettelser, skal du køre et offboarding-script for at Microsoft 365 enhedens overvågnings sensor fra. Få mere at vide under [Offboard-enheder, der bruger et lokalt script](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. Kontrollér, at sensoren er stoppet ved at køre kommandoen nedenfor i et CMD-vindue:

   ```console
   sc query sense
   ```

3. Tjeneste billedet efter behov.

4. Kør nedenstående kommandoer ved hjælp PsExec.exe ( https://download.sysinternals.com/files/PSTools.zip) som kan downloades fra for at rydde op i indholdet fra cybermappen, som sensoren kan have akkumuleret siden start:

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Luk det gyldne/masterbillede igen, som du normalt ville gøre det.

## <a name="related-topics"></a>Relaterede emner

- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10 og Windows 11 enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
