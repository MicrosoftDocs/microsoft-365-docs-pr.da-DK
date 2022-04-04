---
title: Microsoft Defender Antivirus til installation af Virtual Desktop-infrastruktur
description: Lær, hvordan du installerer Microsoft Defender Antivirus et virtuelt skrivebordsmiljø for at få den bedste balance mellem beskyttelse og ydeevne.
keywords: vdi, hyper-v, VM, virtual machine, windows defender, antivirus, av, virtual desktop, rds, remote desktop
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
ms.openlocfilehash: d21fab14788a0402ddc314e2598dfcdf10830924
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679450"
---
# <a name="deployment-guide-for-microsoft-defender-antivirus-in-a-virtual-desktop-infrastructure-vdi-environment"></a>Installationsvejledning til Microsoft Defender Antivirus et VDI-miljø (Virtual Desktop Infrastructure)

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ud over almindelige lokale konfigurationer eller hardwarekonfigurationer kan du også bruge Microsoft Defender Antivirus i et fjernskrivebord eller et ikke-permanent VDI-miljø (Virtual Desktop Infrastructure).

Du kan finde flere oplysninger Microsoft Fjernskrivebord om understøttelse af VDI i [Dokumentation til Azure Virtual Desktop](/azure/virtual-desktop).

Hvis du bruger Azure-baserede virtuelle computere, [skal du se Endpoint Protection i Microsoft Defender til skyen](/azure/security-center/security-center-install-endpoint-protection).

Vi har gjort det nemt at installere opdateringer til VMs, der kører i VDIs, og derfor har vi forkortet denne vejledning, så du hurtigt og nemt kan fokusere på, hvordan du kan få opdateringer på dine computere. Du behøver ikke længere periodisk at oprette og lukke gyldne billeder, da opdateringer udvides til deres komponentbit på værtsserveren og derefter downloades direkte til VM, når den er slået til.

Denne vejledning beskriver, hvordan du konfigurerer dine VM'er for optimal beskyttelse og ydeevne, herunder hvordan du:

- [Konfigurer en dedikeret VDI-filshare til sikkerhedsintelligensopdateringer](#set-up-a-dedicated-vdi-file-share)
- [Randomisere planlagte scanninger](#randomize-scheduled-scans)
- [Brug hurtige scanninger](#use-quick-scans)
- [Forebyd meddelelser](#prevent-notifications)
- [Deaktiver scanninger efter hver opdatering](#disable-scans-after-an-update)
- [Scan forældede maskiner eller maskiner, der har været offline i et stykke tid](#scan-vms-that-have-been-offline)
- [Anvend udeladelse](#exclusions)

Du kan også downloade [whitepaper-Microsoft Defender Antivirus på Virtual Desktop-infrastruktur](https://demo.wd.microsoft.com/Content/wdav-testing-vdi-ssu.pdf), som ser på den nye funktion til opdatering af delt sikkerhedsintelligens sammen med ydeevnetest og vejledning til, hvordan du kan teste antivirusydeevnen på din egen VDI.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

> [!IMPORTANT]
> Selvom VDI kan hostes på Windows Server 2012 eller Windows Server 2016, bør de virtuelle computere som minimum køre Windows 10, 1607 på grund af øget beskyttelsesteknologier og funktioner, der ikke er tilgængelige i tidligere versioner af Windows.
>
> Der er forbedringer af ydeevnen og funktionen på den måde, som Microsoft Defender AV fungerer på virtuelle computere på i Windows 10 Insider Preview, build 18323 (og nyere). Vi identificerer i denne vejledning, hvis du skal bruge et Insider Preview-build; Hvis den ikke er angivet, er minimumskravet til version for den bedste beskyttelse og ydeevne Windows 10 1607.

## <a name="set-up-a-dedicated-vdi-file-share"></a>Konfigurer en dedikeret VDI-filshare

I Windows 10, version 1903, introducerede vi funktionen delt sikkerhedsintelligens, der aflæser udpakkede downloadede sikkerhedsintelligensopdateringer på en værtscomputer, hvilket sparer tidligere CPU-, disk- og hukommelsesressourcer på individuelle maskiner. Denne funktion er blevet backporteret og fungerer nu i Windows 10 version 1703 og nyere. Du kan indstille denne funktion med en Gruppepolitik eller PowerShell.

### <a name="use-group-policy-to-enable-the-shared-security-intelligence-feature"></a>Brug Gruppepolitik til at aktivere funktionen delt sikkerhedsintelligens:

1. På Gruppepolitik administrationscomputer skal du åbne administrationskonsollen Gruppepolitik, højreklikke på det Gruppepolitik-objekt, du vil konfigurere, og derefter klikke på **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Sikkerhedsvidens opdateringer**.

5. Dobbeltklik på **Definer sikkerhedsintelligensplacering for VDI-klienter**, og angiv derefter indstillingen til **Aktiveret**. Der vises automatisk et felt.

6. Enter `\\<sharedlocation\>\wdav-update` (for at få hjælp med denne værdi skal [du se Download og unpackage](#download-and-unpackage-the-latest-updates)).

7. Klik på **OK**.

8. Installér gruppepolitikobjekt til de VMs, du vil teste.

### <a name="use-powershell-to-enable-the-shared-security-intelligence-feature"></a>Brug PowerShell til at aktivere funktionen til delt sikkerhedsintelligens

Brug følgende cmdlet til at aktivere funktionen. Du skal derefter skubbe dette, som du normalt ville skubbe PowerShell-baserede konfigurationspolitikker til VM'erne:

```PowerShell
Set-MpPreference -SharedSignaturesPath \\<shared location>\wdav-update
```

Se afsnittet [Download og udpak](#download-and-unpackage-the-latest-updates) for at se, hvad der \<shared location\> bliver af disse.

## <a name="download-and-unpackage-the-latest-updates"></a>Download og udpak de seneste opdateringer

Nu kan du komme i gang med at hente og installere nye opdateringer. Nedenfor har vi oprettet et eksempel på et PowerShell-script. Dette script er den nemmeste måde at downloade nye opdateringer på og gøre dem klar til dine VM'er. Du bør derefter indstille scriptet til at køre på et bestemt tidspunkt på administrationsmaskine ved hjælp af en planlagt opgave (eller hvis du er bekendt med at bruge PowerShell-scripts i Azure, Intune eller SCCM, kan du også bruge disse scripts).

```PowerShell
$vdmpathbase = "$env:systemdrive\wdav-update\{00000000-0000-0000-0000-"
$vdmpathtime = Get-Date -format "yMMddHHmmss"
$vdmpath = $vdmpathbase + $vdmpathtime + '}'
$vdmpackage = $vdmpath + '\mpam-fe.exe'

New-Item -ItemType Directory -Force -Path $vdmpath | Out-Null

Invoke-WebRequest -Uri 'https://go.microsoft.com/fwlink/?LinkID=121721&arch=x64' -OutFile $vdmpackage

cmd /c "cd /d $vdmpath & mpam-fe.exe /x"
```

Du kan angive, at en planlagt opgave skal køre én gang om dagen, så VM'erne modtager den nye opdatering, når pakken hentes og udpakkes.
Vi anbefaler, at du starter med en gang om dagen, men du bør eksperimentere med at øge eller mindske hyppigheden for at forstå effekten.

Sikkerhedsintelligens-pakker publiceres typisk én gang i mellem tre til fire timer. Det frarådes at angive en hyppighed, der er kortere end fire timer, da det øger netværksomkostningerne på din administrationsmaskine uden nogen fordel.

Du kan også konfigurere din enkelt server eller computer til at hente opdateringerne på vegne af VM'erne med et interval og placere dem i filsharen til forbrug.
Dette er muligt, når enhederne har share- og NTFS-tilladelser til læseadgang til delingen, så de kan hente opdateringerne.

Sådan gør du:
 1. Opret et SMB/CIFS-filshare. 
 
 2. Brug følgende eksempel til at oprette et filshare med følgende tilladelser til deling.

    ```PowerShell
    PS c:\> Get-SmbShareAccess -Name mdatp$

    Name   ScopeName AccountName AccessControlType AccessRight
    ----   --------- ----------- ----------------- -----------
    mdatp$ *         Everyone    Allow             Read
    ```
   
    > [!NOTE]
    > Der tilføjes en NTFS-tilladelse **for godkendte brugere:Læs:**. 

    I dette eksempel er filsharen:

    \\\fileserver.fqdn\mdatp$\wdav-update

### <a name="set-a-scheduled-task-to-run-the-powershell-script"></a>Indstil en planlagt opgave til at køre PowerShell-scriptet

1. Åbn opgavestyringen på administrationsmaskine, menuen Start skriv **Opgavestyring**. Åbn den, og **vælg Opret opgave...** i sidepanelet.

2. Skriv navnet som Security **intelligence unpacker**. Gå til fanen **Udløser** . Vælg **Ny...** \> **Dagligt**, og vælg **OK**.

3. Gå til fanen **Handlinger** . Vælg **Ny...** Angiv **PowerShell** i **feltet Program/** script. Angiv `-ExecutionPolicy Bypass c:\wdav-update\vdmdlunpack.ps1` i **feltet Tilføj** argumenter. Vælg **OK**.

4. Du kan vælge at konfigurere flere indstillinger, hvis du ønsker det.

5. Vælg **OK** for at gemme den planlagte opgave.

Du kan starte opdateringen manuelt ved at højreklikke på opgaven og klikke på **Kør**.

### <a name="download-and-unpackage-manually"></a>Download og oppak manuelt

Hvis du foretrækker at gøre alt manuelt, skal du gøre følgende for at kopiere scriptet:

1. Opret en ny mappe på systemroden kaldet til `wdav_update` at gemme intelligence-opdateringer, f.eks. oprette mappen `c:\wdav_update`.

2. Opret en undermappe under wdav_update *med* et GUID-navn, f.eks. `{00000000-0000-0000-0000-000000000000}`

   Her er et eksempel: `c:\wdav_update\{00000000-0000-0000-0000-000000000000}`

   > [!NOTE]
   > I scriptet angiver vi det, så de sidste 12 cifre i GUID'et er det år, måned, dag og klokkeslæt, hvor filen blev hentet, så der oprettes en ny mappe hver gang. Du kan ændre dette, så filen hentes til den samme mappe hver gang.

3. Download en sikkerhedsintelligenspakke [https://www.microsoft.com/wdsi/definitions](https://www.microsoft.com/wdsi/definitions)  fra mappen GUID. Filen skal navngives `mpam-fe.exe`.

4. Åbn et cmd-promptvindue, og gå til den GUID-mappe, du har oprettet. Brug kommandoen **/X udtræk** til at udtrække filerne, f.eks `mpam-fe.exe /X`. .

   > [!NOTE]
   > VM'erne tager den opdaterede pakke, når der oprettes en ny GUID-mappe med en udpakket opdateringspakke, eller når en eksisterende mappe opdateres med en ny udpakket pakke.

## <a name="randomize-scheduled-scans"></a>Randomisere planlagte scanninger

Planlagte scanninger kører ud over [beskyttelse og scanning i realtid](configure-real-time-protection-microsoft-defender-antivirus.md).

Starttidspunktet for selve scanningen er stadig baseret på politikken for planlagt scanning (**ScheduleDay**, **ScheduleTime** og **ScheduleQuickScanTime**). Randomisering medfører, Microsoft Defender Antivirus starte en scanning på hver computer inden for en fire-timers periode fra det tidspunkt, der er angivet for den planlagte scanning.

Se [Planlæg scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) for andre tilgængelige konfigurationsindstillinger for planlagte scanninger.

## <a name="use-quick-scans"></a>Brug hurtige scanninger

Du kan angive den type scanning, der skal udføres under en planlagt scanning. Hurtige scanninger er den foretrukne fremgangsmåde, da de er designet til at se ud alle de steder, hvor malware skal være aktiv. Følgende procedure beskriver, hvordan du konfigurerer hurtige scanninger ved hjælp Gruppepolitik.

1. I din Gruppepolitik Editor skal du gå til **Administrative skabeloner Windows** \> **komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

2. Vælg **Angiv den scanningstype, der skal bruges til en planlagt scanning** , og rediger derefter politikindstillingen.

3. Angiv politikken til **Aktiveret**, og vælg **derefter** Hurtig scanning  **under Indstillinger**.

4. Vælg **OK**.

5. Installér dit Gruppepolitik objekt, som du normalt gør.

## <a name="prevent-notifications"></a>Forebyd meddelelser

Nogle gange Microsoft Defender Antivirus meddelelser sendes til eller bevares på tværs af flere sessioner. For at minimere dette problem kan du låse Microsoft Defender Antivirus brugergrænsefladen. Følgende procedure beskriver, hvordan du undertrykker meddelelser med Gruppepolitik.

1. I din Gruppepolitik Editor skal du gå **til Windows komponenter** \> **Microsoft Defender Antivirus Client** \> **Interface**.

2. Vælg **Suppress all notifications** and then edit the policy settings.

3. Angiv politikken til **Aktiveret**, og vælg derefter **OK**.

4. Installér dit Gruppepolitik objekt, som du normalt gør.

Hvis du undertrykker meddelelser, forhindres Microsoft Defender Antivirus meddelelser i at blive vist i Handlingscenter på computeren Windows 10 når scanningerne er udført, eller der foretages afhjælpningshandlinger. Dit sikkerhedsteam kan dog se resultaterne af scanningen i portalen Microsoft 365 Defender, mens det blev registreret og stoppet. Beskeder, f.eks. en "startadgangsbesked", blev udløst og vist på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Hvis du vil åbne Handlingscenter på Windows 10 eller Windows 11, skal du gøre et af følgende:
>
> - Vælg ikonet Handlingscenter i højre side af proceslinjen.
> - Tryk på Windows-tasten + A.
> - Stryg ind fra højre kant af skærmen på en enhed med touchskærm.

## <a name="disable-scans-after-an-update"></a>Deaktiver scanninger efter en opdatering

Hvis du deaktiverer en scanning efter en opdatering, forhindres en scanning efter modtagelse af en opdatering. Du kan anvende denne indstilling, når du opretter basisbilledet, hvis du også har kørt en hurtig scanning. På denne måde kan du forhindre den nyligt opdaterede VM i at udføre en scanning igen (som du allerede har scannet, da du oprettede basisbilledet).

> [!IMPORTANT]
> Hvis du kører scanninger efter en opdatering, er det med til at sikre, at dine VM'er er beskyttet med de nyeste Sikkerhedsintelligens-opdateringer. Hvis du deaktiverer denne indstilling, reduceres beskyttelsesniveauet af dine VM'er, og de bør kun bruges, når du først opretter eller udruller basisbilledet.

1. I din Gruppepolitik Editor skal du gå **til Windows komponenter** \> **Microsoft Defender Antivirus** \> **Security Intelligence-opdateringer**.

2. Vælg **Aktiver scanning efter sikkerhedsintelligensopdatering** , og rediger derefter politikindstillingen.

3. Angiv politikken til **Deaktiveret**.

4. Vælg **OK**.

5. Installér dit Gruppepolitik objekt, som du normalt gør.

Denne politik forhindrer en scanning i at køre umiddelbart efter en opdatering.

## <a name="scan-vms-that-have-been-offline"></a>Scan VMs, der har været offline

1. I din Gruppepolitik Editor skal du gå **til Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scan**.

2. Vælg **Slå hurtig scanning til, og** rediger derefter politikindstillingen.

3. Indstil politikken til **Aktiveret**.

4. Vælg **OK**.

5. Installér dit Gruppepolitik-objekt, som du normalt gør det.

Denne politik gennemtvinger en scanning, hvis VM har mistet to eller flere planlagte scanninger efter hinanden.

## <a name="enable-headless-ui-mode"></a>Aktivér brugergrænsefladen uden hoved

1. I din Gruppepolitik Editor skal du gå **til Windows komponenter** \> **Microsoft Defender Antivirus Client** \> **Interface**.

2. Vælg **Aktivér brugergrænseflade uden sidehoved** , og rediger politikken.

3. Indstil politikken til **Aktiveret**.

4. Klik på **OK**.

5. Installér dit Gruppepolitik-objekt, som du normalt gør det.

Denne politik skjuler hele Microsoft Defender Antivirus brugergrænseflade fra slutbrugere i organisationen.

## <a name="exclusions"></a>Udeladelser

Udeladelse kan tilføjes, fjernes eller tilpasses efter dine behov.

Få mere at vide under [Konfigurer Microsoft Defender Antivirus udeladelse på Windows Server](configure-exclusions-microsoft-defender-antivirus.md).

## <a name="additional-resources"></a>Yderligere ressourcer

- [Tech Community-blog: Konfiguration Microsoft Defender Antivirus for ikke-permanente VDI-computere](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/configuring-microsoft-defender-antivirus-for-non-persistent-vdi/ba-p/1489633)
- [TechNet-fora på Fjernskrivebord-tjenester og VDI](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)
- [SignatureDownloadCustomTask PowerShell-script](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)
