---
title: Onboard ikke-vedvarende VDI-enheder (Virtual Desktop Infrastructure)
description: Installér konfigurationspakken på en VDI-enhed (Virtual Desktop Infrastructure), så de er onboardet til Microsoft Defender for Endpoint tjeneste.
keywords: konfigurere VDI-enhed (Virtual Desktop Infrastructure), vdi, enhedshåndtering, konfigurere Microsoft Defender for Endpoint, slutpunkter
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: e292c2f1e0d01e51e3962b71a940927078ab95ad
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634707"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure) i Microsoft 365 Defender

VDI (Virtual desktop infrastructure) er et IT-infrastrukturkoncept, der giver slutbrugere adgang til forekomster af virtuelle skriveborde i virksomheder fra næsten alle enheder (f.eks. din personlige computer, smartphone eller tablet), så organisationen eliminerer behovet for at give brugere fysiske maskiner. Brugen af VDI-enheder reducerer omkostningerne, da it-afdelinger ikke længere er ansvarlige for administration, reparation og udskiftning af fysiske slutpunkter. Autoriserede brugere kan få adgang til de samme virksomhedsservere, filer, apps og tjenester fra enhver godkendt enhed via en sikker computerklient eller browser.

Som alle andre systemer i it-miljøer bør disse også have en løsning til registrering og svar på slutpunkter (Slutpunktsregistrering og -svar) og antivirus-løsninger for at beskytte dig mod avancerede trusler og angreb.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- VDI-enheder (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Faste VDI'er** -  [Onboarding af en permanent VDI-maskine](configure-endpoints.md) i Microsoft Defender for Endpoint håndteres på samme måde, som du ville onboarde en fysisk maskine, f.eks. en stationær eller bærbar computer. Gruppepolitik, Microsoft Endpoint Manager og andre metoder kan bruges til at onboarde en fast maskine. Vælg din Microsoft 365 Defender onboardingmetodehttps://security.microsoft.com) under onboarding i portalen, og følg vejledningen for den pågældende type. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Onboarding ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)

Defender til Slutpunkt understøtter ikke-permanent VDI-session onboarding.

Der kan være udfordringer i forbindelse med onboarding af VDI-forekomster. Følgende er typiske udfordringer i dette scenarie:

- Øjeblikkelig tidlig onboarding af en kortvarig session, som skal være onboardet til Defender til Slutpunkt før den faktiske klargøring.
- Enhedsnavnet genbruges typisk til nye sessioner.

I et VDI-miljø kan VDI-forekomster have korte levetider. VDI-enheder kan vises i Defender til Endpoint-portalen som enten:


- Enkelt portalpost for hver VDI-forekomst. Hvis VDI-forekomsten allerede var onboardet til Microsoft Defender for Endpoint og på et tidspunkt slettet og derefter genoprettet med det samme værtsnavn, oprettes DER IKKE et nyt objekt, der repræsenterer denne VDI-forekomst, i portalen. 


  > [!NOTE]
  > I dette tilfælde skal det *samme* enhedsnavn konfigureres, når sessionen oprettes, f.eks. ved hjælp af en uovervåget svarfil.

- Flere poster for hver enhed – én for hver VDI-forekomst.

Følgende trin fører dig gennem onboarding VDI-enheder og fremhæver trin til enkelt og flere poster.

> [!WARNING]
> I miljøer, hvor der er lav ressourcekonfigurationer, kan VDI-startprocedure sænke onboarding af Defender til slutpunkt-sensoren.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>For Windows 10, Windows 11 eller Windows Server 2012 R2 og nyere

> [!NOTE]
> Windows Server 2016 og Windows Server 2012 R2 skal forberedes ved først at anvende installationspakken ved hjælp af instruktionerne i [Onboard Windows-servere](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere.

1.  Åbn VDI-konfigurationspakken .zip fil (*WindowsDefenderATPOnboardingPackage.zip*), du hentede fra guiden til start af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>:

    1. I **navigationsruden** skal du **vælge Indstillinger** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Vælg operativsystemet.

    1.  I feltet **Installationsmetode** skal du vælge **VDI-onboardingscripts for ikke-permanente slutpunkter**.

    1. Klik **på Download** pakke, og gem .zip fil.

2. Kopiér filerne fra mappen WindowsDefenderATPOnboardingPackage, der er hentet fra .zip-filen, til det gyldne/masterbillede under stien `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Hvis du implementerer flere poster for hver enhed – én for hver session, skal du kopiere WindowsDefenderATPOnboardingScript.cmd.
    2. Hvis du implementerer en enkelt post for hver enhed, skal du kopiere både Onboard-NonPersistentMachine.ps1 og WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Hvis du ikke kan se mappen `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , kan den være skjult. Du skal vælge indstillingen Vis **skjulte filer og mapper fra** Stifinder.

3. Åbn et lokalt Gruppepolitik Editor-vindue, og gå til **Computerkonfiguration, Windows Indstillinger** \>  \> **Start af scripts**\>.

   > [!NOTE]
   > Domæneadministratorer Gruppepolitik også bruges til onboarding af ikke-permanente VDI-enheder.

4. Afhængigt af den metode, du gerne vil implementere, skal du følge de relevante trin:
    - For enkelt indtastning for hver enhed:

         Vælg fanen **PowerShell-scripts**, og klik derefter på **Tilføj (Windows** Stifinder åbnes direkte i den sti, hvor du kopierede onboarding-scriptet tidligere). Naviger til onboarding PowerShell-script `Onboard-NonPersistentMachine.ps1`. Der er ingen grund til at angive den anden fil, da den udløses automatisk.

    - For flere poster for hver enhed:

         Vælg fanen **Scripts**, og klik **derefter på Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboarding-scriptet tidligere). Gå til onboarding bash-scriptet `WindowsDefenderATPOnboardingScript.cmd`.

5. Test din løsning:
   1. Opret en gruppe med én enhed.
   2. Log på enheden.
   3. Log af enheden.
   4. Log på enheden med en anden bruger.
   5. Afhængigt af den metode, du gerne vil implementere, skal du følge de relevante trin:
      - For enkelt indtastning for hver enhed: Kontrollér kun én post Microsoft 365 Defender portalen.
      - For flere poster for hver enhed: Kontrollér flere poster i Microsoft 365 Defender portal.

6. Klik **på listen Enheder** i ruden Navigation.

7. Brug søgefunktionen ved at skrive enhedens navn, og **vælg Enhed** som søgetype.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>For SKU'er på underniveau (Windows Server 2008 R2)

> [!NOTE]
> Denne vejledning til andre Windows-serverversioner gælder også, hvis du kører den forrige Microsoft Defender for Endpoint til Windows Server 2016 og Windows Server 2012 R2, der kræver OVERENSSTEMMELSE. Vejledning til at overføre til den nye samlede løsning findes i [Scenarier for serveroverførsel Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Følgende registreringsdatabase er kun relevant, når formålet er at opnå en "enkelt post for hver enhed".

1. Angiv registreringsdatabaseværdien til:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    eller ved hjælp af kommandolinjen:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Følg [server-onboardingprocessen](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Opdatering af ikke-permanente VDI-billeder (Virtual Desktop Infrastructure)

Som bedste fremgangsmåde anbefaler vi, at du bruger offline-serviceværktøjer til at rette golden-/masterbilleder.

Du kan f.eks. bruge nedenstående kommandoer til at installere en opdatering, mens billedet forbliver offline:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

For more information on DISM commands and offline servicing, refer to the articles below:

- [Modify a Windows image using DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [DISM Image Management Command-Line Options](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Reducer størrelsen på Store i et offline Windows billede](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Hvis offline-servicering ikke er en realistisk mulighed for dit ikke-permanente VDI-miljø, skal du følge disse trin for at sikre ensartethed og sensortilstand:

1. Når du har startet masterbilledet til online service eller programrettelse, skal du køre et offboarding-script for at deaktivere Defender for Endpoint-sensoren. Få mere at vide under [Offboard-enheder, der bruger et lokalt script](configure-endpoints-script.md#offboard-devices-using-a-local-script).

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
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Gør det gyldne billede/masterbilledet igen, som du normalt ville gøre det.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md)
