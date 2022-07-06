---
title: Onboard ikke-vedvarende VDI-enheder (Virtual Desktop Infrastructure)
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
description: Udrul konfigurationspakken på VDI-enheden (Virtual Desktop Infrastructure), så de er onboardet til tjenesten til forebyggelse af datatab for Slutpunkt.
ms.openlocfilehash: 8a54d4ce3cfb4b3ba6571f2aee63cd60c2a6d71f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636133"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Onboarde enheder til ikke-vedvarende virtuelle skrivebordsinfrastrukturer

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

- VDI-enheder (Virtual Desktop Infrastructure)

> [!WARNING]
> Understøttelse af forebyggelse af datatab for Slutpunkt for Windows Virtual Desktop understøtter scenarier med en enkelt session. Scenarier med flere sessioner på Windows Virtual Desktop understøttes ikke i øjeblikket.

## <a name="onboard-vdi-devices"></a>Indbyggede VDI-enheder

Microsoft 365 understøtter onboarding af virtuelle skrivebordsinfrastrukturer (VDI).

> [!NOTE]
> Hvis du vil onboarde ikke-vedvarende VDI-sessioner, skal VDI-enheder være på Windows 10 1809 eller nyere.

Der kan være tilknyttede udfordringer, når du onboarder VM'er. Følgende er typiske udfordringer i dette scenarie:

- Øjeblikkelig tidlig onboarding af kortvarige sessioner, som skal onboardes til Microsoft 365 før den faktiske klargøring.
- Enhedsnavnet genbruges typisk til nye sessioner.

VDI-enheder kan vises i Microsoft Purview-compliance-portal som enten:

- Enkelt post for hver enhed.
Bemærk, at i dette tilfælde skal det *samme* enhedsnavn konfigureres, når sessionen oprettes, f.eks. ved hjælp af en automatisk svarfil.
- Flere poster for hver enhed – én for hver session.

Følgende trin fører dig gennem onboarding af VDI-enheder og fremhæver trin for enkelte og flere poster.

> [!WARNING]
> I miljøer, hvor der er konfigurationer med få ressourcer, kan VDI-startproceduren gøre onboardingprocessen for enheden langsommere.

1. Hent VDI-konfigurationspakken .zip-filen (*DeviceCompliancePackage.zip*) fra [Microsoft Purview-compliance-portal](https://compliance.microsoft.com).

2. I navigationsruden skal du vælge **Indstillinger For** > **onboarding af** >  enhed **.**

3. I feltet **Installationsmetode** skal du vælge **VDI-onboardingscripts for ikke-faste slutpunkter**.

4. Klik på **Download pakke** , og gem filen .zip.

5. Kopiér filerne fra mappen DeviceCompliancePackage, der er udpakket fra den .zip fil, til `golden` billedet under stien `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Hvis du ikke implementerer en enkelt post for hver enhed, skal du kopiere DeviceComplianceOnboardingScript.cmd.

7. Hvis du implementerer en enkelt post for hver enhed, skal du kopiere både Onboard-NonPersistentMachine.ps1 og DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Hvis du ikke kan se mappen `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , kan den være skjult. Du skal vælge indstillingen **Vis skjulte filer og mapper** fra Stifinder.

8. Åbn vinduet Lokal Gruppepolitik Editor, og naviger til **Computerkonfiguration** > **Windows-indstillinger Scripts** >  > **Start**.

   > [!NOTE]
   > Domæne Gruppepolitik kan også bruges til onboarding af ikke-faste VDI-enheder.

9. Afhængigt af den metode, du vil implementere, skal du følge de relevante trin:

   **Til en enkelt post for hver enhed**

   Vælg fanen **PowerShell-scripts** , og klik derefter på **Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding af PowerShell-script `Onboard-NonPersistentMachine.ps1`.

   **For flere poster for hver enhed**:

   Vælg fanen **Scripts** , og klik derefter på **Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding-bash-scriptet `DeviceComplianceOnboardingScript.cmd`.

10. Test din løsning:
    1. Opret en pulje med én enhed.
    1. Log på enheden.
    1. Log af enheden.
    1. Log på enheden med en anden bruger.
    1. **For en enkelt post for hver enhed**: Kontrollér kun én post i Microsoft Defender Security Center.
       **For flere poster for hver enhed**: Kontrollér flere poster i Microsoft Defender Security Center.

11. Klik på **Listen Enheder** i navigationsruden.

12. Brug søgefunktionen ved at angive enhedsnavnet, og vælg **Enhed** som søgetype.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Opdaterer VDI-billeder (Virtual Desktop Infrastructure), der ikke er faste

Som bedste praksis anbefaler vi, at du bruger offlineserviceværktøjer til at lappe gyldne billeder.

Du kan f.eks. bruge nedenstående kommandoer til at installere en opdatering, mens billedet forbliver offline:

```DOS
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Du kan finde flere oplysninger om DISM-kommandoer og offlineservicering i nedenstående artikler:

- [Rediger en Windows-afbildning ved hjælp af DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Indstillinger for DISM-Command-Line til administration af afbildninger](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Reducer størrelsen på komponentlageret i en offline Windows-afbildning](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Hvis offlineservicering ikke er en levedygtig mulighed for dit ikke-vedvarende VDI-miljø, skal du gøre følgende for at sikre konsistens og sensortilstand:

1. Når du har startet det gyldne billede til onlineservicering eller programrettelse, skal du køre et offboarding-script for at slå Microsoft 365-enhedens overvågningssensor fra. Du kan få flere oplysninger under [Offboard-enheder, der bruger et lokalt script](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. Sørg for, at sensoren stoppes ved at køre kommandoen nedenfor i et CMD-vindue:

   ```DOS
   sc query sense
   ```

3. Servicer billedet efter behov.

4. Kør nedenstående kommandoer ved hjælp af PsExec.exe (som kan downloades fra https://download.sysinternals.com/files/PSTools.zip) for at rydde op i indholdet i cybermappen, som sensoren kan have akkumuleret siden opstart:

    ```DOS
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Re-seal det gyldne billede som du normalt ville.

## <a name="related-topics"></a>Relaterede emner

- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Gruppepolitik](device-onboarding-gp.md)
- [Onboarde Windows 10 og Windows 11 enheder ved hjælp af Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af værktøjer til administration af mobilenheder](device-onboarding-mdm.md)
- [Onboard Windows 10- og Windows 11-enheder ved hjælp af et lokalt script](device-onboarding-script.md)
- [Fejlfinding af onboardingproblemer i Forbindelse med Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
