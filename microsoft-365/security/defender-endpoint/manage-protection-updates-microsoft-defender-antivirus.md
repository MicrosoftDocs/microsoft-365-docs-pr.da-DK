---
title: Administrer, hvordan og hvor Microsoft Defender Antivirus modtager opdateringer
description: Administrer reserveordren for, hvordan Microsoft Defender Antivirus modtager beskyttelsesopdateringer.
keywords: opdateringer, grundlæggende sikkerhedsindstillinger, beskyttelse, reserveordre, ADL, MMPC, UNC, filsti, share, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 4f6c43da4940ddee099c515a5dc8889cb5aca62b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101397"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Administrer kilderne til Microsoft Defender Antivirus beskyttelsesopdateringer

> [!IMPORTANT]
> Kunder, der anvendte opdateringen til Microsoft Defender-programmet fra marts 2022 (**1.1.19100.5**), kan have oplevet høj ressourceudnyttelse (CPU og/eller hukommelse). Microsoft har udgivet en opdatering (**1.1.19200.5**), der løser de fejl, der blev introduceret i den tidligere version. Kunder anbefales at opdatere til denne nye motor build af Antivirus Engine (**1.1.19200.5**). Hvis du vil sikre, at eventuelle problemer med ydeevnen er fuldt løst, anbefales det at genstarte maskiner efter anvendelse af opdatering. Du kan få flere oplysninger under [Månedlige platform- og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Det er vigtigt at holde antivirusbeskyttelsen opdateret. Der er to komponenter til administration af beskyttelsesopdateringer til Microsoft Defender Antivirus:

- *Hvor* opdateringerne downloades fra Og
- *Når* opdateringer downloades og anvendes.

I denne artikel beskrives det, hvordan du angiver, hvor opdateringer skal downloades fra (dette kaldes også reserveordren). Se emnet [Administrer Microsoft Defender Antivirus opdateringer og anvendelse af grundlinjer](manage-updates-baselines-microsoft-defender-antivirus.md) for at få en oversigt over, hvordan opdateringer fungerer, og hvordan du konfigurerer andre aspekter af opdateringer (f.eks. planlægning af opdateringer).

> [!IMPORTANT]
> Microsoft Defender Antivirus Opdateringer til sikkerhedsintelligens og platformopdateringer leveres gennem Windows Update og fra og med mandag den 21. oktober 2019 signeres alle sikkerhedsintelligensopdateringer udelukkende. Dine enheder skal opdateres for at understøtte SHA-2 for at kunne opdatere din sikkerhedsintelligens. Du kan få mere at vide under [Supportkrav til sha-2-signering af kode i 2019 for Windows og WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Reserveordre

Du konfigurerer typisk slutpunkter til individuelt at downloade opdateringer fra en primær kilde efterfulgt af andre kilder i prioriteret rækkefølge baseret på din netværkskonfiguration. Opdateringer hentes fra kilder i den rækkefølge, du angiver. Hvis opdateringer fra den aktuelle kilde er forældede, bruges den næste kilde på listen med det samme.

Når der publiceres opdateringer, anvendes der noget logik for at minimere opdateringens størrelse. I de fleste tilfælde er det kun forskellene mellem den seneste opdatering og den opdatering, der er installeret i øjeblikket (kaldes delta) på enheden, der downloades og anvendes. Deltaets størrelse afhænger imidlertid af to hovedfaktorer:

- Alderen på den seneste opdatering på enheden; Og
- Den kilde, der bruges til at downloade og anvende opdateringer.

Jo ældre opdateringerne på et slutpunkt er, jo større bliver downloaden. Du skal dog også overveje downloadfrekvensen. En tidsplan for hyppigere opdateringer kan resultere i mere netværksbrug, hvorimod en mindre hyppig tidsplan kan resultere i større filstørrelser pr. download.

Der er fem steder, hvor du kan angive, hvor et slutpunkt skal hente opdateringer:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Server Update Service](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Netværksfilshare](#unc-share)
- [Sikkerhedsintelligensopdateringer til Microsoft Defender Antivirus og anden antimalware](https://www.microsoft.com/wdsi/defenderupdates) <sup>fra Microsoft [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune intern definitionsopdateringsserver – Hvis du bruger SCCM/SUP til at hente definitionsopdateringer til Microsoft Defender Antivirus og har brug for at få adgang til Windows Update på blokerede klientenheder, kan du skifte til medadministration og aflaste arbejdsbelastningen for beskyttelse af slutpunkter for at Intune. I den antimalwarepolitik, der er konfigureret i Intune er der en mulighed for 'intern definitionsopdateringsserver', som kan konfigureres til at bruge WSUS i det lokale miljø som opdateringskilde. Dette hjælper dig med at styre, hvilke opdateringer fra den officielle WU-server der godkendes til virksomheden, og hjælper også med at proxy- og gemme netværkstrafik til det officielle Windows UPdates-netværk.

(<a id="fn1">2</a>) Din politik og registreringsdatabase kan have dette angivet som Microsoft Malware Protection Center (MMPC) security intelligence, dens tidligere navn.

For at sikre det bedste beskyttelsesniveau giver Microsoft Update mulighed for hurtige udgivelser, hvilket betyder, at mindre downloads hyppigt. Kilderne Windows Server Update Service, Microsoft Endpoint Configuration Manager, Microsoft Security Intelligence og platformopdateringer leverer mindre hyppige opdateringer. Således kan delta være større, hvilket resulterer i større downloads.

> [!NOTE]
> Sikkerhedsintelligensopdateringer indeholder programopdateringer og udgives månedligt.
Sikkerhedsintelligensopdateringer leveres også flere gange om dagen, men denne pakke indeholder ikke et program.


> [!IMPORTANT]
> Hvis du har angivet [opdateringer af Microsoft Security Intelligence-siden](https://www.microsoft.com/security/portal/definitions/adl.aspx) som reservekilde efter Windows Server Update Service eller Microsoft Update, downloades opdateringer kun fra opdateringer til sikkerhedsintelligens og platform, når den aktuelle opdatering anses for at være forældet. (Som standard er det syv dage i træk, hvor opdateringer fra Windows Server Update Service eller Microsoft Update-tjenester ikke kan anvendes).
> Du kan dog [angive antallet af dage, før beskyttelse rapporteres som forældet](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> Fra mandag den 21. oktober 2019 underskrives sikkerhedsintelligensopdateringer og platformopdateringer udelukkende af SHA-2. Enheder skal opdateres for at understøtte SHA-2 for at få de nyeste opdateringer til sikkerhedsintelligens og platformopdateringer. Du kan få mere at vide under [Supportkrav til sha-2-signering af kode i 2019 for Windows og WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Hver kilde har typiske scenarier, der afhænger af, hvordan dit netværk er konfigureret, ud over hvor ofte de publicerer opdateringer, som beskrevet i følgende tabel:

<br/><br/>

|Placering|Eksempelscenarie|
|---|---|
|Windows Server Update Service|Du bruger Windows Server Update Service til at administrere opdateringer til dit netværk.|
|Microsoft Update|Dine slutpunkter skal oprette direkte forbindelse til Microsoft Update. Dette kan være nyttigt for slutpunkter, der uregelmæssigt opretter forbindelse til virksomhedsnetværket, eller hvis du ikke bruger Windows Server Update Service til at administrere dine opdateringer.|
|Filshare|Du har enheder, der ikke har forbindelse til internettet (f.eks. VM'er). Du kan bruge din vm-vært med internetforbindelse til at downloade opdateringerne til et netværksshare, hvorfra VM'erne kan hente opdateringerne. I [VDI-installationsvejledningen](deployment-vdi-microsoft-defender-antivirus.md) kan du se, hvordan filshares kan bruges i VDI-miljøer (Virtual Desktop Infrastructure).|
|Microsoft Endpoint Manager|Du bruger Microsoft Endpoint Manager til at opdatere dine slutpunkter.|
|Opdateringer til sikkerhedsintelligens og platformopdateringer til Microsoft Defender Antivirus og anden Microsoft antimalware (tidligere kaldet MMPC)|[Sørg for, at dine enheder opdateres, så de understøtter SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Microsoft Defender Antivirus Sikkerhedsintelligens og platformopdateringer leveres gennem Windows Update, og fra og med mandag den 21. oktober 2019 underskrives sikkerhedsintelligensopdateringer og platformopdateringer udelukkende af SHA-2. <br/>Download de seneste beskyttelsesopdateringer på grund af en nylig infektion eller for at hjælpe med at klargøre en stærk, grundlæggende afbildning til [VDI-udrulning](deployment-vdi-microsoft-defender-antivirus.md). Denne indstilling bør generelt kun bruges som en endelig reservekilde og ikke som den primære kilde. Den bruges kun, hvis opdateringer ikke kan downloades fra Windows Server Update Service eller Microsoft Update i [et angivet antal dage](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Du kan administrere den rækkefølge, som opdateringskilder bruges i med Gruppepolitik, Microsoft Endpoint Configuration Manager, PowerShell-cmdlet'er og WMI.

> [!IMPORTANT]
> Hvis du angiver Windows Server Update Service som en downloadplacering, skal du godkende opdateringerne, uanset hvilken administrationsværktøj du bruger til at angive placeringen. Du kan konfigurere en regel for automatisk godkendelse med Windows Server Update Service, hvilket kan være nyttigt, når opdateringer modtages mindst én gang om dagen. Du kan få mere at vide [under Synkroniser opdateringer til beskyttelse af slutpunkter i separate Windows Server Update Service](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Procedurerne i denne artikel beskriver først, hvordan du angiver rækkefølgen, og derefter hvordan du konfigurerer indstillingen **Filshare** , hvis du har aktiveret den.

## <a name="use-group-policy-to-manage-the-update-location"></a>Brug Gruppepolitik til at administrere opdateringsplaceringen

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Politikker** og derefter **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Windows Defender** \> **Signaturopdateringer**, og konfigurer følgende indstillinger:

   1. Dobbeltklik på indstillingen **Definer rækkefølgen af kilder til download af sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**.

   2. Angiv rækkefølgen af kilder adskilt af en enkelt pipe, f.eks.: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`, som vist på følgende skærmbillede.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Gruppepolitikindstilling, der viser kilderækkefølgen" lightbox="../../media/wdav-order-update-sources.png":::

   3. Vælg **OK**. Dette angiver rækkefølgen af kilder til beskyttelsesopdatering.

   4. Dobbeltklik på indstillingen **Definer filshares til download af sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**.

   5. Angiv kilden til filsharet. Hvis du har flere kilder, skal du angive hver kilde i den rækkefølge, de skal bruges, adskilt af en enkelt pipe. Brug [UNC-standardnotation](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) til at angive stien, f.eks.: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Hvis du ikke angiver nogen stier, springes denne kilde over, når VM'en downloader opdateringer.

   6. Klik på **OK**. Dette angiver rækkefølgen af filshares, når der refereres til denne kilde i gruppepolitikindstillingen **Definer rækkefølgen af kilder...**

> [!NOTE]
> For Windows 10, version 1703 til og med 1809 er politikstien **Windows Komponenter > Microsoft Defender Antivirus > Signaturopdateringer** til Windows 10, version 1903, er politikstien **Windows Komponenter > Microsoft Defender Antivirus > sikkerhedsintelligensopdateringer**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Brug Configuration Manager til at administrere opdateringsplaceringen

Se [Konfigurer opdateringer til sikkerhedsintelligens for at få Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates) for at få oplysninger om konfiguration af Microsoft Endpoint Manager (aktuel forgrening).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Brug PowerShell-cmdlet'er til at administrere opdateringsplaceringen

Brug følgende PowerShell-cmdlet'er til at angive opdateringsrækkefølgen.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Du kan få flere oplysninger i følgende artikler:

- [Set-MpPreference –SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference –SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender Antivirus-cmdlet'er](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Brug WMI (Windows Management Instruction) til at administrere opdateringsplaceringen

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Du kan få flere oplysninger i følgende artikler:

- [Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Brug Mobile Enhedshåndtering (MDM) til at administrere opdateringsplaceringen

Se [Politik-CSP – Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) for at få oplysninger om konfiguration af MDM.

## <a name="what-if-were-using-a-third-party-vendor"></a>Hvad nu, hvis vi bruger en tredjepartsleverandør?

I denne artikel beskrives det, hvordan du konfigurerer og administrerer opdateringer for Microsoft Defender Antivirus. Tredjepartsleverandører kan dog bruges til at udføre disse opgaver.

Antag f.eks., at Contoso har hyret Fabrikam til at administrere deres sikkerhedsløsning, hvilket omfatter Microsoft Defender Antivirus. Fabrikam bruger typisk [Windows Management Instrumentation](./use-wmi-microsoft-defender-antivirus.md), [PowerShell-cmdlet'er](./use-powershell-cmdlets-microsoft-defender-antivirus.md) eller [Windows kommandolinje](./command-line-arguments-microsoft-defender-antivirus.md) til at installere programrettelser og opdateringer.

> [!NOTE]
> Microsoft tester ikke tredjepartsløsninger til administration af Microsoft Defender Antivirus.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-and-platform-updates"></a>Opret et UNC-share til sikkerhedsintelligens og platformopdateringer

Konfigurer et netværksfilshare (UNC/tilknyttet drev) for at downloade sikkerhedsintelligens- og platformopdateringer fra MMPC-webstedet ved hjælp af en planlagt opgave.

1. Opret en mappe, hvor du vil gemme scriptet, i det system, hvor du vil klargøre delingen og downloade opdateringerne.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Opret den mappe, som signaturopdateringerne skal gemmes i.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Download PowerShell-scriptet fra [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Klik på **Manuel download**.

5. Klik på **Download den rå nupkg-fil**.

6. Udpak filen.

7. Kopiér filen SignatureDownloadCustomTask.ps1 til den mappe, du tidligere har oprettet. `C:\Tool\PS-Scripts\`

8. Brug kommandolinjen til at konfigurere den planlagte opgave.

   > [!NOTE]
   > Der er to typer opdateringer: fuld og delta.

   - For x64 delta:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - For x64 fuld:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - For x86 delta:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - For x86 fuld:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > Når de planlagte opgaver oprettes, kan du finde disse i Opgavestyring under `Microsoft\Windows\Windows Defender`.

9. Kør hver opgave manuelt, og kontrollér, at du har data (`mpam-d.exe`, `mpam-fe.exe`og `nis_full.exe`) i følgende mapper (du har muligvis valgt forskellige placeringer):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   Hvis den planlagte opgave mislykkes, skal du køre følgende kommandoer:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > Problemer kan også skyldes udførelsespolitik.

10. Opret et share, `\\server\updates`der peger på `C:\Temp\TempSigs` (f.eks. ).

    > [!NOTE]
    > Godkendte brugere skal som minimum have adgang til "Læs". Dette krav gælder også for domænecomputere, sharet og NTFS (sikkerhed).

11. Angiv delingsplaceringen i politikken til sharet.

    > [!NOTE]
    > Tilføj ikke mappen x64 (eller x86) i stien. Den mpcmdrun.exe proces tilføjer den automatisk.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Installer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrer opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og VM'er](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
