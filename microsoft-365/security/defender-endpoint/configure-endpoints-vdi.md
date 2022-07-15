---
title: Onboard ikke-vedvarende VDI-enheder (Virtual Desktop Infrastructure)
description: Udrul konfigurationspakken på VDI-enheden (Virtual Desktop Infrastructure), så de er onboardet til Microsoft Defender for Endpoint-tjenesten.
keywords: konfigurer VDI-enhed (Virtual Desktop Infrastructure), vdi, enhedshåndtering, konfigurer Microsoft Defender for Endpoint, slutpunkter
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
ms.openlocfilehash: 7ef410beaacbc899c6f52e688ee38b3b545b8997
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823081"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Onboarde VDI-enheder (Virtual Desktop Infrastructure) i Microsoft 365 Defender

VDI (Virtual Desktop Infrastructure) er et koncept for it-infrastruktur, der gør det muligt for slutbrugere at få adgang til virtuelle virksomhedsskriveborde fra næsten alle enheder (f.eks. din personlige computer, smartphone eller tablet), hvilket fjerner behovet for, at organisationen giver brugerne fysiske maskiner. Brug af VDI-enheder reducerer omkostningerne, da it-afdelinger ikke længere er ansvarlige for at administrere, reparere og erstatte fysiske slutpunkter. Godkendte brugere kan få adgang til de samme virksomhedsservere, filer, apps og tjenester fra alle godkendte enheder via en sikker desktopklient eller -browser.

Som ethvert andet system i et it-miljø skal disse også have en EDR- (Endpoint Detection and Response) og Antivirus-løsning for at beskytte mod avancerede trusler og angreb.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- VDI-enheder (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Faste VDI'er** – Onboarding af en vedvarende VDI-maskine i Microsoft Defender for Endpoint håndteres på samme måde, som du ville onboarde en fysisk maskine, f.eks. en stationær eller bærbar computer. Gruppepolitik, Microsoft Endpoint Manager og andre metoder kan bruges til at onboarde en vedvarende maskine. På Microsoft 365 Defender-portalen (https://security.microsoft.com) under onboarding skal du vælge din foretrukne onboardingmetode og følge instruktionerne for den pågældende type. Du kan få flere oplysninger under [Onboarding Windows-klient](onboard-windows-client.md).

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Onboarding af VDI-enheder (Virtual Desktop Infrastructure), der ikke er vedvarende

Defender for Endpoint understøtter onboarding af en VDI-session, der ikke er vedvarende.

Der kan være tilknyttede udfordringer, når du onboarder VDI-instanser. Følgende er typiske udfordringer i dette scenarie:

- Øjeblikkelig tidlig onboarding af en kortlivet session, som skal onboardes til Defender for Endpoint før den faktiske klargøring.
- Enhedsnavnet genbruges typisk til nye sessioner.

I et VDI-miljø kan VDI-forekomster have korte levetider. VDI-enheder kan vises i Defender for Endpoint Portal som enten:


- Enkelt portalpost for hver VDI-forekomst. Hvis VDI-forekomsten allerede er onboardet til Microsoft Defender for Endpoint og på et tidspunkt er slettet og derefter gendannet med det samme værtsnavn, oprettes der IKKE et nyt objekt, der repræsenterer denne VDI-forekomst, på portalen. 


  > [!NOTE]
  > I dette tilfælde skal det *samme* enhedsnavn konfigureres, når sessionen oprettes, f.eks. ved hjælp af en automatisk svarfil.

- Flere poster for hver enhed – én for hver VDI-forekomst.

Følgende trin fører dig gennem onboarding af VDI-enheder og fremhæver trin for enkelte og flere poster.

> [!WARNING]
> I miljøer, hvor der er konfigurationer med få ressourcer, kan VDI-startproceduren nedsætte onboarding af Defender for Endpoint-sensoren.

### <a name="onboarding-steps"></a>Onboardingtrin

> [!NOTE]
> Windows Server 2016 og Windows Server 2012 R2 skal forberedes ved først at anvende installationspakken ved hjælp af vejledningen i [Onboard Windows-servere](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) , for at denne funktion fungerer.

1.  Åbn VDI-konfigurationspakken .zip fil (*WindowsDefenderATPOnboardingPackage.zip*), som du har downloadet fra guiden til onboarding af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>:

    1. I navigationsruden skal du vælge **Indstillinger** > **Endpoints** > **Onboarding til enhedshåndtering** > .

    1. Vælg operativsystemet.

    1.  I feltet **Installationsmetode** skal du vælge **VDI-onboardingscripts for ikke-faste slutpunkter**.

    1. Klik på **Download pakke** , og gem filen .zip.

2. Kopiér filerne fra mappen WindowsDefenderATPOnboardingPackage, der er udtrukket fra den .zip fil, til det gyldne/overordnede billede under stien `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Hvis du implementerer flere poster for hver enhed – én for hver session, skal du kopiere WindowsDefenderATPOnboardingScript.cmd.
    2. Hvis du implementerer en enkelt post for hver enhed, skal du kopiere både Onboard-NonPersistentMachine.ps1 og WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Hvis du ikke kan se mappen `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , kan den være skjult. Du skal vælge indstillingen **Vis skjulte filer og mapper** fra Stifinder.

3. Åbn vinduet Lokal Gruppepolitik editor, og naviger til **Computerkonfiguration** \> **Windows-indstillinger Scripts** \>  \> **Start**.

   > [!NOTE]
   > Domæne Gruppepolitik kan også bruges til onboarding af ikke-faste VDI-enheder.

4. Afhængigt af den metode, du vil implementere, skal du følge de relevante trin:
    - For en enkelt post for hver enhed:

         Vælg fanen **PowerShell-scripts** , og klik derefter på **Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding af PowerShell-script `Onboard-NonPersistentMachine.ps1`. Det er ikke nødvendigt at angive den anden fil, da den udløses automatisk.

    - For flere poster for hver enhed:

         Vælg fanen **Scripts** , og klik derefter på **Tilføj** (Windows Stifinder åbnes direkte i den sti, hvor du kopierede onboardingscriptet tidligere). Naviger til onboarding-bash-scriptet `WindowsDefenderATPOnboardingScript.cmd`.

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
> Disse instruktioner til andre Windows-serverversioner gælder også, hvis du kører den tidligere Microsoft Defender for Endpoint til Windows Server 2016 og Windows Server 2012 R2, der kræver MMA. Instruktioner til migrering til den nye samlede løsning finder du [i Server migrationsscenarier i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

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

   > [!NOTE]
   > Hvis du har onboardet masterbilledet af dit ikke-vedvarende VDI-miljø (SENSE-tjenesten kører), skal du offboard og rydde nogle data, før du sætter billedet i produktion igen.
   > 1. Sørg for, at sensoren stoppes ved at køre kommandoen nedenfor i et CMD-vindue:
   >  ```console
   >  sc query sense
   >  ```
   > 2. Kør nedenstående kommandoer ved hjælp af PsExec.exe (som kan downloades fra https://download.sysinternals.com/files/PSTools.zip)
   >
   >  ```console
   >  PsExec.exe -s cmd.exe
   >  cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
   >  del *.* /f /s /q
   >  REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
   >  exit
   >  ```


## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

Når du har onboardet enheder til tjenesten, er det vigtigt at drage fordel af de inkluderede trusselsbeskyttelsesfunktioner ved at aktivere dem med følgende anbefalede konfigurationsindstillinger.


### <a name="next-generation-protection-configuration"></a>Næste generation af konfiguration af beskyttelse

Følgende konfigurationsindstillinger anbefales:

#### <a name="cloud-protection-service"></a>Cloud Protection Service

- Slå skybaseret beskyttelse til: Ja
- Skybaseret beskyttelsesniveau: Ikke konfigureret
- Udvidet timeout for Defender Cloud i sekunder: 20


#### <a name="exclusions"></a>Udeladelser
- Deaktiver lokal administratorfletning: Ikke konfigureret
- Defender-processer, der skal udelades:
  - `%Programfiles%\FSLogix\Apps\frxccd.exe`
  - `%Programfiles%\FSLogix\Apps\frxccds.exe`
  - `%Programfiles%\FSLogix\Apps\frxsvc.exe`


- Filtypenavne, der skal udelades fra scanninger og beskyttelse i realtid:
  -  `%Programfiles%\FSLogix\Apps\frxccd.sys`
  - `%Programfiles%\FSLogix\Apps\frxdrv.sys`
  - `%Programfiles%\FSLogix\Apps\frxdrvvt.sys`
  - `%TEMP%*.VHD`
  - `%TEMP%*.VHDX`
  - `%Windir%\TEMP*.VHD`
  - `%Windir%\TEMP*.VHDX`
  - `\\stroageaccount.file.core.windows.net\share**.VHD`
  -  `\\stroageaccount.file.core.windows.net\share**.VHDX`


#### <a name="real-time-protection"></a>Beskyttelse i realtid

- Slå alle indstillinger til, og angiv til at overvåge alle filer

#### <a name="remediation"></a>Oprydning
- Antal dage, malware skal bevares i karantæne: 30
- Indsend samtykke til eksempler: Send alle eksempler automatisk
- Handling, der skal udføres på potentielt uønskede apps: Aktivér
- Handlinger for registrerede trusler:
  - Lav trussel: Ren
  - Moderat trussel, høj trussel, alvorlig trussel: Karantæne



#### <a name="scan"></a>Skan

- Scan arkiverede filer: Ja
- Brug lav CPU-prioritet til planlagte scanninger: Ikke konfigureret
- Deaktiver komplet søgning efter indfangning: Ikke konfigureret
- Deaktiver hurtig scanning af opfangning: Ikke konfigureret
- Grænse for CPU-forbrug pr. scanning: 50
- Scan tilknyttede netoword-drev under fuld scanning: Ikke konfigureret
- Kør daglig hurtig scanning kl. 12
- Scanningstype: Ikke konfigureret
- Ugedag til kørsel af planlagt scanning: Ikke konfigureret
- Tidspunkt på dagen til kørsel af en planlagt scanning: Ikke konfigureret
- Kontrollér, om der er signaturopdateringer, før du kører scanningen: Ja

#### <a name="updates"></a>Opdateringer
- Angiv, hvor ofte der skal søges efter opdateringer til sikkerhedsintelligens: 8
- Lad andre indstillinger være i standardtilstand

#### <a name="user-experience"></a>Brugeroplevelse
- Tillad brugeradgang til Microsoft Defender-appen: Ikke konfigureret


#### <a name="enable-tamper-protection"></a>Aktivér beskyttelse mod manipulation
- Aktivér beskyttelse mod ændring for at forhindre, at Microsoft Defender deaktiveres: Aktivér

#### <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

- Aktivér netværksbeskyttelse: Overvågningstilstand
- Kræv SmartScreen til Microsoft Edge: Ja
- Bloker maclious webstedsadgang: Ja
- Bloker ikke-bekræftet fildownload: Ja

#### <a name="attack-surface-reduction-rules"></a>Regler for reduktion af angrebsoverflade
- Konfigurer alle tilgængelige regler til Overvågning.


> [!NOTE]
> Blokering af disse aktiviteter kan afbryde legitime forretningsprocesser. Den bedste fremgangsmåde er at indstille alt til overvågning, identificere, hvilke der er sikre at aktivere, og derefter aktivere disse indstillinger på slutpunkter, der ikke har falske positive registreringer.






## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
- [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
