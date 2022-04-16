---
title: Onboard ikke-vedvarende VDI-enheder (Virtual Desktop Infrastructure)
description: Udrul konfigurationspakken på VDI-enheden (Virtual Desktop Infrastructure), så de er onboardet til Pertahanan Microsoft untuk Titik Akhir-tjenesten.
keywords: konfigurer VDI-enhed (Virtual Desktop Infrastructure), vdi, enhedshåndtering, konfigurer Pertahanan Microsoft untuk Titik Akhir, slutpunkter
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
ms.date: 04/15/2022
ms.technology: mde
ms.openlocfilehash: 78d22772ccc9713b968347de5dee4c3a9699fe26
ms.sourcegitcommit: dba1a846ae78ea14240d28efa8d4934fe303f308
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/16/2022
ms.locfileid: "64891860"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Onboarde VDI-enheder (Virtual Desktop Infrastructure) i Microsoft 365 Defender

VDI (Virtual Desktop Infrastructure) er et koncept for it-infrastruktur, der gør det muligt for slutbrugere at få adgang til virtuelle virksomhedsskriveborde fra næsten alle enheder (f.eks. din personlige computer, smartphone eller tablet), hvilket fjerner behovet for, at organisationen giver brugerne fysiske maskiner. Brug af VDI-enheder reducerer omkostningerne, da it-afdelinger ikke længere er ansvarlige for at administrere, reparere og erstatte fysiske slutpunkter. Godkendte brugere kan få adgang til de samme virksomhedsservere, filer, apps og tjenester fra alle godkendte enheder via en sikker desktopklient eller -browser.

Som ethvert andet system i et it-miljø skal disse også have en løsning til registrering og svar af slutpunkter (Slutpunktsregistrering og -svar) og antivirus for at beskytte mod avancerede trusler og angreb.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- VDI-enheder (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Faste VDI'er** -  [Onboarding af en vedvarende VDI-maskine](configure-endpoints.md) i Pertahanan Microsoft untuk Titik Akhir håndteres på samme måde, som du ville onboarde en fysisk maskine, f.eks. en stationær eller bærbar computer. Gruppepolitik, Microsoft Endpoint Manager og andre metoder kan bruges til at onboarde en vedvarende maskine. På Microsoft 365 Defender-portalen (https://security.microsoft.com) under onboarding skal du vælge din foretrukne onboardingmetode og følge instruktionerne for den pågældende type. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Onboarding af VDI-enheder (Virtual Desktop Infrastructure), der ikke er vedvarende

Defender for Endpoint understøtter onboarding af en VDI-session, der ikke er vedvarende.

Der kan være tilknyttede udfordringer, når du onboarder VDI-instanser. Følgende er typiske udfordringer i dette scenarie:

- Øjeblikkelig tidlig onboarding af en kortlivet session, som skal onboardes til Defender for Endpoint før den faktiske klargøring.
- Enhedsnavnet genbruges typisk til nye sessioner.

I et VDI-miljø kan VDI-forekomster have korte levetider. VDI-enheder kan vises i Defender for Endpoint Portal som enten:


- Enkelt portalpost for hver VDI-forekomst. Hvis VDI-forekomsten allerede er onboardet til Pertahanan Microsoft untuk Titik Akhir og på et tidspunkt er slettet og derefter gendannet med det samme værtsnavn, oprettes der IKKE et nyt objekt, der repræsenterer denne VDI-forekomst, på portalen. 


  > [!NOTE]
  > I dette tilfælde skal det *samme* enhedsnavn konfigureres, når sessionen oprettes, f.eks. ved hjælp af en automatisk svarfil.

- Flere poster for hver enhed – én for hver VDI-forekomst.

Følgende trin fører dig gennem onboarding af VDI-enheder og fremhæver trin for enkelte og flere poster.

> [!WARNING]
> I miljøer, hvor der er konfigurationer med få ressourcer, kan VDI-startproceduren nedsætte onboarding af Defender for Endpoint-sensoren.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>Til Windows 10 eller Windows 11 eller Windows Server 2012 R2 og nyere

> [!NOTE]
> Windows Server 2016 og Windows Server 2012 R2 skal forberedes ved først at anvende installationspakken ved hjælp af vejledningen i [Onboard Windows-servere](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016), før denne funktion fungerer.

1.  Åbn VDI-konfigurationspakken .zip fil (*WindowsDefenderATPOnboardingPackage.zip*), som du har downloadet fra guiden til onboarding af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>:

    1. I navigationsruden skal du vælge **Indstillinger** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Vælg operativsystemet.

    1.  I feltet **Installationsmetode** skal du vælge **VDI-onboardingscripts for ikke-faste slutpunkter**.

    1. Klik på **Download pakke** , og gem filen .zip.

2. Kopiér filerne fra mappen WindowsDefenderATPOnboardingPackage, der er udtrukket fra den .zip fil, til det gyldne/overordnede billede under stien `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Hvis du implementerer flere poster for hver enhed – én for hver session, skal du kopiere WindowsDefenderATPOnboardingScript.cmd.
    2. Hvis du implementerer en enkelt post for hver enhed, skal du kopiere både Onboard-NonPersistentMachine.ps1 og WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Hvis du ikke kan se mappen `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , kan den være skjult. Du skal vælge indstillingen **Vis skjulte filer og mapper** fra Stifinder.

3. Åbn vinduet Lokal Gruppepolitik Editor, og naviger til **Computerkonfiguration** \> **Windows Indstillinger** \> **Start** **scripts**\>.

   > [!NOTE]
   > Domæne Gruppepolitik kan også bruges til onboarding af ikke-faste VDI-enheder.

4. Afhængigt af den metode, du vil implementere, skal du følge de relevante trin:
    - For en enkelt post for hver enhed:

         Vælg fanen **PowerShell-scripts**, og klik derefter på **Tilføj** (Windows Explorer åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding af PowerShell-script `Onboard-NonPersistentMachine.ps1`. Det er ikke nødvendigt at angive den anden fil, da den udløses automatisk.

    - For flere poster for hver enhed:

         Vælg fanen **Scripts**, og klik derefter på **Tilføj** (Windows Explorer åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding-bash-scriptet `WindowsDefenderATPOnboardingScript.cmd`.

5. Test din løsning:
   1. Opret en pulje med én enhed.
   2. Log på enheden.
   3. Log af enheden.
   4. Log på enheden med en anden bruger.
   5. Afhængigt af den metode, du vil implementere, skal du følge de relevante trin:
      - For en enkelt post for hver enhed: Kontrollér kun én post i Microsoft 365 Defender portal.
      - For flere poster for hver enhed: Kontrollér flere poster på Microsoft 365 Defender portal.

6. Klik på **Listen Enheder** i navigationsruden.

7. Brug søgefunktionen ved at angive enhedsnavnet, og vælg **Enhed** som søgetype.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>For sku'er på et lavere niveau (Windows Server 2008 R2)

> [!NOTE]
> Disse instruktioner til andre Windows serverversioner gælder også, hvis du kører den tidligere Pertahanan Microsoft untuk Titik Akhir til Windows Server 2016 og Windows Server 2012 R2, der kræver MMA. Instruktioner til migrering til den nye samlede løsning finder du [i Server migrationsscenarier i Pertahanan Microsoft untuk Titik Akhir](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Følgende registreringsdatabase er kun relevant, når målet er at opnå en "enkelt post for hver enhed".

1. Angiv registreringsdatabaseværdien til:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    eller ved hjælp af kommandolinjen:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Følg [processen til onboarding af serveren](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Opdaterer VDI-billeder (Virtual Desktop Infrastructure), der ikke er faste

Med muligheden for nemt at udrulle opdateringer til VM'er, der kører i VM'er, har vi forkortet denne vejledning for at fokusere på, hvordan du hurtigt og nemt kan få opdateringer på dine maskiner. Du behøver ikke længere at oprette og forsegle gyldne billeder regelmæssigt, da opdateringer udvides til deres komponentbits på værtsserveren og derefter downloades direkte til vm'en, når den er slået til.

Du kan finde flere oplysninger ved at følge vejledningen i [Installationsvejledning til Microsoft Defender Antivirus i et VDI-miljø (Virtual Desktop Infrastructure).](/microsoft-365/security/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)


## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Fejlfinding af problemer med Pertahanan Microsoft untuk Titik Akhir onboarding](troubleshoot-onboarding.md)
