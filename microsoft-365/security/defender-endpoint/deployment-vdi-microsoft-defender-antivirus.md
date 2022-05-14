---
title: installationsvejledning til Microsoft Defender Antivirus virtuel desktopinfrastruktur
description: Få mere at vide om, hvordan du udruller Microsoft Defender Antivirus i et virtuelt skrivebordsmiljø for at få den bedste balance mellem beskyttelse og ydeevne.
keywords: vdi, hyper-v, vm, virtuel maskine, Windows Defender, antivirus, av, virtuelt skrivebord, rds, fjernskrivebord
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 03/18/2022
ms.reviewer: jesquive
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 690ec028b3013bf00e28547ff440c7804b4d0f64
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416414"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Udrulningsvejledning til Microsoft Defender Antivirus i et VDI-miljø (Virtual Desktop Infrastructure)

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Ud over standardkonfigurationer i det lokale miljø eller hardwarekonfigurationer kan du også bruge Microsoft Defender Antivirus i et RDS-miljø (Fjernskrivebord) eller et VDI-miljø (Non-Persistent Virtual Desktop Infrastructure).

Du kan få flere oplysninger om Microsoft Fjernskrivebord-tjenester og VDI-support under [Dokumentation til Azure Virtual Desktop](/azure/virtual-desktop).

For Azure-baserede virtuelle maskiner skal du se [Installér Endpoint Protection i Microsoft Defender for Cloud](/azure/security-center/security-center-install-endpoint-protection).

Med muligheden for nemt at udrulle opdateringer til VM'er, der kører i VM'er, har vi forkortet denne vejledning for at fokusere på, hvordan du hurtigt og nemt kan få opdateringer på dine maskiner. Du behøver ikke længere at oprette og forsegle gyldne billeder regelmæssigt, da opdateringer udvides til deres komponentbits på værtsserveren og derefter downloades direkte til vm'en, når den er slået til.

I denne vejledning beskrives det, hvordan du konfigurerer dine VM'er for at opnå optimal beskyttelse og ydeevne, herunder hvordan du:

- [Konfigurer et dedikeret VDI-filshare til sikkerhedsintelligensopdateringer](#set-up-a-dedicated-vdi-file-share)
- [Randomiser planlagte scanninger](#randomize-scheduled-scans)
- [Brug hurtig scanninger](#use-quick-scans)
- [Forbyd meddelelser](#prevent-notifications)
- [Deaktiver scanninger, der forekommer efter hver opdatering](#disable-scans-after-an-update)
- [Scan forældede maskiner eller maskiner, der har været offline i et stykke tid](#scan-vms-that-have-been-offline)
- [Anvend udeladelser](#exclusions)

Du kan også downloade [whitepaper-Microsoft Defender Antivirus på Virtual Desktop Infrastructure](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf), som ser på den nye funktion til opdatering af delte sikkerhedsintelligens, sammen med test af ydeevne og vejledning til, hvordan du kan teste ydeevnen for antivirus på din egen VDI.

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

> [!IMPORTANT]
> Selvom VDI'en kan hostes på Windows Server 2012 eller Windows Server 2016, skal de virtuelle maskiner (VM'er) som minimum køre Windows 10 1607 på grund af øgede beskyttelsesteknologier og funktioner, der ikke er tilgængelige i tidligere versioner af Windows.
>
> Der er forbedringer af ydeevne og funktioner til den måde, hvorpå Microsoft Defender AV fungerer på virtuelle maskiner i Windows 10 Insider Preview, build 18323 (og nyere). Vi identificerer i denne vejledning, om du skal bruge et Insider Preview-build. Hvis den ikke er angivet, er den version, der som minimum kræves for at opnå den bedste beskyttelse og ydeevne, Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Konfigurer et dedikeret VDI-filshare

I Windows 10 version 1903 introducerede vi funktionen til delt sikkerhedsintelligens, som fjerner udpakningen af downloadede sikkerhedsintelligensopdateringer på en værtscomputer, hvilket sparer tidligere CPU-, disk- og hukommelsesressourcer på individuelle maskiner. Denne funktion er blevet backporteret og fungerer nu i Windows 10 version 1703 og nyere. Du kan angive denne funktion med en Gruppepolitik eller PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Brug Gruppepolitik til at aktivere funktionen til delt sikkerhedsintelligens:

1. Åbn administrationskonsollen Gruppepolitik Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik derefter på **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **sikkerhedsintelligensopdateringer**.

5. Dobbeltklik på **Definer placering af sikkerhedsintelligens for VDI-klienter**, og angiv derefter indstillingen til **Aktiveret**. Der vises automatisk et felt.

6. Angiv `\\<sharedlocation\>\wdav-update` (hvis du vil have hjælp til denne værdi, skal du se [Download og pak ud](#download-and-unpackage-the-latest-updates)).

7. Klik på **OK**.

8. Installer gruppepolitikobjektet på de VM'er, du vil teste.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Brug PowerShell til at aktivere funktionen til delt sikkerhedsintelligens

Brug følgende cmdlet til at aktivere funktionen. Du skal derefter pushe dette, som du normalt ville pushe PowerShell-baserede konfigurationspolitikker til VM'erne:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Se afsnittet [Download og udpakning](#download-and-unpackage-the-latest-updates) for at se \<shared location\> , hvad der vil være.

## <a name="download-and-unpackage-the-latest-updates"></a>Download og pak de seneste opdateringer ud

Nu kan du komme i gang med at downloade og installere nye opdateringer. Vi har oprettet et eksempel på et PowerShell-script for dig nedenfor. Dette script er den nemmeste måde at downloade nye opdateringer på og gøre dem klar til dine VM'er. Du skal derefter indstille scriptet til at køre på et bestemt tidspunkt på administrationscomputeren ved hjælp af en planlagt opgave (eller, hvis du er fortrolig med at bruge PowerShell-scripts i Azure, Intune eller SCCM, kan du også bruge disse scripts).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd /d $vdmpath & mpam-fe.exe /x"
```

Du kan angive, at en planlagt opgave skal køre én gang om dagen, så VM'erne modtager den nye opdatering, når pakken downloades og pakkes ud.
Vi foreslår, at du starter med én gang om dagen, men du bør eksperimentere med at øge eller mindske hyppigheden for at forstå virkningen.

Sikkerhedsintelligenspakker udgives typisk hver tredje til fire timer. Det anbefales ikke at angive en frekvens, der er kortere end fire timer, da det vil øge netværksbelastningen på din administrationsmaskine uden fordel.

Du kan også konfigurere din enkeltserver eller computer til at hente opdateringerne på vegne af VM'erne med et interval og placere dem i filsharet til forbrug.
Dette er muligt, når enhederne har delings- og NTFS-tilladelserne til læseadgang til delingen, så de kan hente opdateringerne.

Sådan gør du:
 1. Opret et SMB/CIFS-filshare. 
 
 2. Brug følgende eksempel til at oprette et filshare med følgende delingstilladelser.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Der tilføjes en NTFS-tilladelse for **Godkendte brugere:Læs:**. 

    I dette eksempel er filsharet:

    \\\fileserver.fqdn\mdatp$\wdav-update

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Angiv en planlagt opgave for at køre PowerShell-scriptet

1. Åbn menuen Start på administrationscomputeren, og skriv **Opgavestyring**. Åbn den, og vælg **Opret opgave...** i sidepanelet.

2. Angiv navnet som **udpakning af Sikkerhedsintelligens**. Gå til fanen **Udløser** . Vælg **Ny...** \> **Dagligt**, og vælg **OK**.

3. Gå til fanen **Handlinger** . Vælg **Ny...** Angiv **PowerShell** i feltet **Program/Script** . Angiv `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` i feltet **Tilføj argumenter** . Vælg **OK**.

4. Du kan vælge at konfigurere yderligere indstillinger, hvis du vil.

5. Vælg **OK** for at gemme den planlagte opgave.

Du kan starte opdateringen manuelt ved at højreklikke på opgaven og klikke på **Kør**.

### <a name="download-and-unpackage-manually"></a>Download og pak ud manuelt

Hvis du foretrækker at gøre alt manuelt, skal du gøre følgende for at replikere scriptets funktionsmåde:

1. Opret en ny mappe på systemroden, der kaldes `wdav_update` til lagring af intelligensopdateringer, f.eks. opret mappen `c:\wdav_update`.

2. Opret en undermappe under *wdav_update* med et GUID-navn, f.eks. `{00000000-0000-0000-0000-000000000000}`

   Her er et eksempel: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > I scriptet angiver vi det, så de sidste 12 cifre i GUID'et er det år, den måned, den dag og det klokkeslæt, hvor filen blev downloadet, så der oprettes en ny mappe hver gang. Du kan ændre dette, så filen downloades til den samme mappe hver gang.

3. Download en security intelligence-pakke fra [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  til GUID-mappen. Filen skal navngives `mpam-fe.exe`.

4. Åbn et cmd-promptvindue, og naviger til den GUID-mappe, du har oprettet. Brug kommandoen **/X** extraction til at udtrække filerne, f.eks `mpam-fe.exe /X`. .

   > [!NOTE]
   > VM'erne henter den opdaterede pakke, når der oprettes en ny GUID-mappe med en udpakket opdateringspakke, eller når en eksisterende mappe opdateres med en ny pakke, der er udpakket.

## <a name="randomize-scheduled-scans"></a>Randomiser planlagte scanninger

Planlagte scanninger kører ud over [beskyttelse og scanning i realtid](configure-real-time-protection-microsoft-defender-antivirus.md).

Starttidspunktet for selve scanningen er stadig baseret på politikken for planlagt scanning (**ScheduleDay**, **ScheduleTime** og **ScheduleQuickScanTime**). Randomisering medfører, at Microsoft Defender Antivirus starter en scanning på hver computer inden for et firetimers vindue fra det tidspunkt, der er angivet for den planlagte scanning.

Se [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) for at se andre konfigurationsindstillinger, der er tilgængelige for planlagte scanninger.

## <a name="use-quick-scans"></a>Brug hurtig scanninger

Du kan angive, hvilken type scanning der skal udføres under en planlagt scanning. Hurtig scanninger er den foretrukne tilgang, da de er designet til at se ud alle steder, hvor malware skal være placeret for at være aktiv. I følgende procedure beskrives det, hvordan du konfigurerer hurtigsøgninger ved hjælp af Gruppepolitik.

1. I editoren til Gruppepolitik skal du gå til **Administrative skabeloner** \> **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

2. Vælg **Angiv den scanningstype, der skal bruges til en planlagt scanning** , og rediger derefter politikindstillingen.

3. Angiv politikken til **Aktiveret**, og vælg derefter **Hurtig scanning** under **Indstillinger**.

4. Vælg **OK**.

5. Udrul dit Gruppepolitik objekt, som du normalt gør.

## <a name="prevent-notifications"></a>Forbyd meddelelser

Nogle gange kan Microsoft Defender Antivirus meddelelser blive sendt til eller bevares på tværs af flere sessioner. Hvis du vil minimere dette problem, kan du låse den Microsoft Defender Antivirus brugergrænseflade. I følgende procedure beskrives det, hvordan du undertrykker meddelelser med Gruppepolitik.

1. Gå til **Windows komponenter** \> Microsoft Defender Antivirus **klientgrænsefladen** **i** \> Gruppepolitik Editor.

2. Vælg **Skjul alle meddelelser,** og rediger derefter politikindstillingerne.

3. Angiv politikken til **Aktiveret**, og vælg derefter **OK**.

4. Udrul dit Gruppepolitik objekt, som du normalt gør.

Undertrykkelse af meddelelser forhindrer, at meddelelser fra Microsoft Defender Antivirus vises i Løsningscenter på Windows 10 når der udføres scanninger, eller der udføres afhjælpningshandlinger. Sikkerhedsteamet kan dog se resultaterne af scanningen, mens angrebet blev opdaget og stoppet. beskeder, f.eks. en "indledende adgangsbesked", udløses og vises på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Benyt en af følgende fremgangsmåder for at åbne Løsningscenter på Windows 10 eller Windows 11:
>
> - Vælg ikonet Løsningscenter i højre ende af proceslinjen.
> - Tryk på Windows logotasten + A.
> - Stryg ind fra højre kant af skærmen på en touchskærmenhed.

## <a name="disable-scans-after-an-update"></a>Deaktiver scanninger efter en opdatering

Deaktivering af en scanning efter en opdatering vil forhindre, at der sker en scanning efter modtagelse af en opdatering. Du kan anvende denne indstilling, når du opretter basisbilledet, hvis du også har kørt en hurtig scanning. På denne måde kan du forhindre den nyligt opdaterede VM i at udføre en scanning igen (som du allerede har scannet den, da du oprettede basisbilledet).

> [!IMPORTANT]
> Kørsel af scanninger efter en opdatering hjælper med at sikre, at dine VM'er er beskyttet med de nyeste sikkerhedsintelligensopdateringer. Hvis du deaktiverer denne indstilling, reduceres beskyttelsesniveauet for dine VM'er, og den bør kun bruges, første gang du opretter eller installerer basisafbildningen.

1. I editoren til Gruppepolitik skal du gå til **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Sikkerhedsintelligensopdateringer**.

2. Vælg **Slå scanning til efter sikkerhedsintelligensopdatering** , og rediger derefter politikindstillingen.

3. Angiv politikken til **Deaktiveret**.

4. Vælg **OK**.

5. Udrul dit Gruppepolitik objekt, som du normalt gør.

Denne politik forhindrer, at en scanning kører umiddelbart efter en opdatering.

## <a name="scan-vms-that-have-been-offline"></a>Scan VM'er, der har været offline

1. I Gruppepolitik Editor skal du gå til **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

2. Vælg **Slå hurtigsøgning til** , og rediger derefter politikindstillingen.

3. Angiv politikken til **Aktiveret**.

4. Vælg **OK**.

5. Udrul dit Gruppepolitik-objekt, som du normalt gør.

Denne politik gennemtvinger en scanning, hvis den virtuelle maskine har overset to eller flere planlagte scanninger efter hinanden.

## <a name="enable-headless-ui-mode"></a>Aktivér hovedløs brugergrænsefladetilstand

1. Gå til **Windows komponenter** \> Microsoft Defender Antivirus **klientgrænsefladen** **i** \> Gruppepolitik Editor.

2. Vælg **Aktivér hovedløs brugergrænsefladetilstand,** og rediger politikken.

3. Angiv politikken til **Aktiveret**.

4. Klik på **OK**.

5. Udrul dit Gruppepolitik-objekt, som du normalt gør.

Denne politik skjuler hele Microsoft Defender Antivirus brugergrænseflade fra slutbrugere i din organisation.

## <a name="exclusions"></a>Udeladelser

Udeladelser kan tilføjes, fjernes eller tilpasses, så de passer til dine behov.

Du kan få flere oplysninger under [Konfigurer Microsoft Defender Antivirus udeladelser på Windows Server](configure-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="additional-resources"></a>Yderligere ressourcer

- [Tech Community-blog: Konfiguration af Microsoft Defender Antivirus til ikke-vedvarende VDI-maskiner](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [TechNet-forummer om Fjernskrivebord-tjenester og VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask PowerShell-script](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
