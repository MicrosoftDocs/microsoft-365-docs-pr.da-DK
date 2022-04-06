---
title: Administrer, hvordan og hvor Microsoft Defender Antivirus modtager opdateringer
description: Administrer fallback-ordren for, hvordan Microsoft Defender Antivirus modtager beskyttelsesopdateringer.
keywords: opdateringer, grundlinjer for sikkerhed, beskyttelse, fallback-rækkefølge, ADL, MMPC, UNC, filsti, del, wsus
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
ms.openlocfilehash: 69c211e02b5bea12431e17bf2256405f96977b53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467395"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Administrere kilderne til Microsoft Defender Antivirus opdateringer til beskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Det er meget vigtigt at holde din antivirusbeskyttelse opdateret. Der er to komponenter i administrationen af sikkerhedsopdateringer til Microsoft Defender Antivirus:

- *Hvor* opdateringerne downloades fra; og
- *Når* opdateringer hentes og anvendes.

Denne artikel beskriver, hvordan du angiver, hvorfra opdateringer skal downloades (dette kaldes også for fallback-rækkefølgen). Se [emnet Microsoft Defender Antivirus administrer](manage-updates-baselines-microsoft-defender-antivirus.md) opdateringer og anvend oprindelige planer for at få en oversigt over, hvordan opdateringer fungerer, og hvordan du konfigurerer andre aspekter af opdateringer (f.eks. planlægning af opdateringer).

> [!IMPORTANT]
> Microsoft Defender Antivirus sikkerhedsintelligensopdateringer leveres via Windows Update og fra den 21. oktober 2019 bliver alle sikkerhedsintelligensopdateringer udelukkende signeret af SHA-2. Dine enheder skal opdateres til at understøtte SHA-2 for at opdatere din sikkerhedsintelligens. Du kan få mere at vide [i 2019 SHA-2 Krav til understøttelse af signering af kode Windows og WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Fallback-ordre

Typisk konfigurerer du slutpunkter til individuelt at hente opdateringer fra en primær kilde efterfulgt af andre kilder i prioriteret rækkefølge baseret på netværkskonfigurationen. Opdateringer hentes fra kilder i den rækkefølge, du angiver. Hvis opdateringer fra den aktuelle kilde er forældede, bruges den næste kilde på listen straks.

Når opdateringerne er udgivet, anvendes der logik til at minimere størrelsen af opdateringen. I de fleste tilfælde hentes og anvendes kun forskellene mellem den seneste opdatering og den opdatering, der aktuelt er installeret (dette kaldes delta) på enheden. Deltastørrelsen afhænger dog af to hovedfaktorer:

- Alderen på den seneste opdatering på enheden; og
- Den kilde, der bruges til at hente og anvende opdateringer.

Jo ældre opdateringerne er på et slutpunkt, jo større bliver overførslen. Du skal dog også overveje downloadfrekvens. En hyppigere opdateringsplan kan resultere i mere netværksbrug, hvorimod en mindre hyppige tidsplan kan resultere i større filstørrelser pr. download.

Der er fem steder, hvor du kan angive, hvor et slutpunkt skal hente opdateringer:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows serveropdateringstjeneste](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Netværksfildeling](#unc-share)
- [Sikkerhedsintelligensopdateringer til Microsoft Defender Antivirus og anden Microsoft-antimalware](https://www.microsoft.com/wdsi/defenderupdates) <sup>[[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune Intern definition af opdateringsserver – Hvis du bruger SCCM/SUP til at få definitionsopdateringer til Microsoft Defender Antivirus og har brug for at få adgang til Windows Update på blokerede klientenheder, kan du overgå til samtidig administration og fjerne arbejdsbelastningen for slutpunktsbeskyttelse til Intune. I antimalwarepolitikken, der er konfigureret i Intune er der en indstilling for "intern opdateringsserver til definition", som kan konfigureres til at bruge lokale WSUS som opdateringskilde. Dette hjælper dig med at kontrollere, hvilke opdateringer fra den officielle WU-server, der er godkendt til virksomheden, og hjælper også proxy og gemmer netværkstrafik på det officielle Windows UPdates-netværk.

(<a id="fn1">2</a>) Din politik og registreringsdatabasen kan have denne angivet som den Microsoft Malware Protection Center (MMPC) sikkerhedsintelligens, dens tidligere navn.

For at sikre det bedste beskyttelsesniveau tillader Microsoft Update hurtige udgivelser, hvilket betyder, at der ofte hentes mindre filer. Server Windows opdateringstjenesten, serveropdateringstjenesten, Microsoft Endpoint Configuration Manager og Microsofts kilder til sikkerhedsopdateringer leverer mindre hyppige opdateringer. Deltaet kan således være større, hvilket resulterer i større downloads.

> [!IMPORTANT]
> Hvis du har angivet [Microsoft Security Intelligence-sideopdateringer](https://www.microsoft.com/security/portal/definitions/adl.aspx) som reservekilde efter Windows Serveropdateringstjeneste eller Microsoft Update, hentes opdateringer kun fra sikkerhedsintelligensopdateringer, når den aktuelle opdatering betragtes som forældet. (Dette er som standard syv fortløbende dage, efter at opdateringer fra tjenesten Windows Serveropdatering eller Microsoft Update ikke kan anvendes).
> Du kan dog angive [, hvor mange dage før beskyttelsen rapporteres som forældet](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> Fra og med mandag d. 21. oktober 2019 vil sikkerhedsintelligensopdateringer udelukkende være SHA-2 signeret. Enheder skal opdateres for at understøtte SHA-2 for at få de nyeste sikkerhedsintelligensopdateringer. Du kan få mere at vide [i 2019 SHA-2 Krav til understøttelse af signering af kode Windows og WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Hver kilde har typiske scenarier, der afhænger af, hvordan dit netværk er konfigureret, ud over hvor ofte de publicerer opdateringer, som beskrevet i følgende tabel:

<br/><br/>

|Placering|Eksempelscenarie|
|---|---|
|Windows serveropdateringstjeneste|Du bruger tjenesten Windows til at administrere opdateringer til dit netværk.|
|Microsoft Update|Du vil have dine slutpunkter til at oprette direkte forbindelse til Microsoft Update. Dette kan være nyttigt for slutpunkter, der uregelmæssigt opretter forbindelse til dit virksomhedsnetværk, eller hvis du ikke bruger Windows Server Update Service til at administrere dine opdateringer.|
|Filshare|Du har ikke-internetforbundne enheder (f.eks. VM'er). Du kan bruge din internetforbundne VM-vært til at hente opdateringerne til et netværksshare, hvorfra VM'erne kan hente opdateringerne. Se [VDI-installationsvejledningen](deployment-vdi-microsoft-defender-antivirus.md) for at finde ud af, hvordan filshares kan bruges i VDI-miljøer (Virtual Desktop Infrastructure).|
|Microsoft Endpoint Manager|Du bruger Microsoft Endpoint Manager til at opdatere dine slutpunkter.|
|Sikkerheds intelligenceopdateringer til Microsoft Defender Antivirus og anden Microsoft-antimalware (tidligere kaldet MMPC)|[Sørg for, at dine enheder er opdateret til at understøtte SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Microsoft Defender Antivirus sikkerhedsintelligensopdateringer leveres via Windows Update, og fra og med mandag d. 21. oktober 2019 signeres sikkerhedsintelligensopdateringer udelukkende af SHA-2. <br/>Download de nyeste opdateringer til beskyttelse på grund af en nylig har været indfarvet eller for at klargøre et stærkt, grundlæggende billede til [VDI-installation](deployment-vdi-microsoft-defender-antivirus.md). Denne indstilling bør generelt kun bruges som en endelig reservekilde og ikke som den primære kilde. Den bruges kun, hvis opdateringer ikke kan downloades fra Windows serveropdateringstjenesten eller Microsoft Update [i et angivet antal dage](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Du kan administrere den rækkefølge, som opdateringskilder bruges i med Gruppepolitik, Microsoft Endpoint Configuration Manager, PowerShell-cmdlet'er og WMI.

> [!IMPORTANT]
> Hvis du angiver Windows serveropdateringstjeneste som en downloadplacering, skal du godkende opdateringerne, uanset hvilket administrationsværktøj du bruger til at angive placeringen. Du kan konfigurere en regel for automatisk godkendelse med Windows serveropdateringstjeneste, hvilket kan være nyttigt, når opdateringer ankommer mindst en gang om dagen. Du kan få mere at [vide under Synkronisere opdateringer til slutpunktsbeskyttelse i den enkeltstående Windows Serveropdateringstjeneste](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Fremgangsmåderne i denne artikel beskriver først, hvordan du angiver rækkefølgen, og derefter hvordan du konfigurerer indstillingen **Filshare** , hvis du har aktiveret den.

## <a name="use-group-policy-to-manage-the-update-location"></a>Brug Gruppepolitik til at administrere opdateringsplaceringen

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I Gruppepolitik **skal du** gå til **Computerkonfiguration**.

3. Klik **på Politikker** og **derefter på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Windows Defender** \> **signaturopdateringer,** og konfigurer følgende indstillinger:

   1. Dobbeltklik på indstillingen **Definer rækkefølgen af kilder til hentning af sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**.

   2. Angiv rækkefølgen af kilder, adskilt af et enkelt rør, f.eks.: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`, som vist på følgende skærmbillede.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Gruppepolitikindstilling med en liste over kilders rækkefølge" lightbox="../../media/wdav-order-update-sources.png":::

   3. Vælg **OK**. Dette indstiller rækkefølgen af opdateringskilder til beskyttelse.

   4. Dobbeltklik på indstillingen **Definer filshares for at hente sikkerhedsintelligensopdateringer** , og angiv indstillingen til **Aktiveret**.

   5. Angiv filsharekilden. Hvis du har flere kilder, skal du angive hver kilde i den rækkefølge, de skal bruges, adskilt af et enkelt rør. Brug [standard-UNC-notation](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) til at tildele stien, f.eks.: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Hvis du ikke angiver nogen stier, springes denne kilde over, når VM'en henter opdateringer.

   6. Klik på **OK**. Dette angiver rækkefølgen af filshares, når der refereres til kilden i **gruppepolitikindstillingen Definer rækkefølgen** af kilder....

> [!NOTE]
> For Windows 10, version 1703 op til og med 1809, er politikstien **Windows Komponenter > Microsoft Defender Antivirus > Signaturopdateringer** til Windows 10, version 1903, politikstien er **Windows Components > Microsoft Defender Antivirus > Security Intelligence-opdateringer**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Brug Configuration Manager til at administrere opdateringsplaceringen

Se [Konfigurer sikkerhedsintelligensopdateringer til Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates) for at få mere at vide om konfiguration Microsoft Endpoint Manager (aktuel forgrening).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Brug PowerShell-cmdlet'er til at administrere opdateringsplaceringen

Brug følgende PowerShell-cmdlet'er til at angive opdateringsrækkefølgen.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Se følgende artikler for at få flere oplysninger:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender Antivirus-cmdlet'er](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Brug Windows (WMI) til at administrere opdateringsplaceringen

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) til følgende egenskaber:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Se følgende artikler for at få flere oplysninger:

- [Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Brug mobile Enhedshåndtering (MDM) til at administrere opdateringsplaceringen

Se [Politik-CSP – Defender/SignatureUpdateFallbackOrder, hvis](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) du vil have mere at vide om konfiguration af MDM.

## <a name="what-if-were-using-a-third-party-vendor"></a>Hvad nu, hvis vi bruger en tredjepartsleverandør?

Denne artikel beskriver, hvordan du konfigurerer og administrerer opdateringer til Microsoft Defender Antivirus. Tredjepartsleverandører kan dog bruges til at udføre disse opgaver.

Antag f.eks., at Contoso har ansat Fabrikam til at administrere deres sikkerhedsløsning, hvilket Microsoft Defender Antivirus. Fabrikam bruger [typisk Windows Management Instrumentation](./use-wmi-microsoft-defender-antivirus.md), [PowerShell-cmdlet'er](./use-powershell-cmdlets-microsoft-defender-antivirus.md) [eller Windows-kommandolinjen](./command-line-arguments-microsoft-defender-antivirus.md) til at installere rettelser og opdateringer.

> [!NOTE]
> Microsoft tester ikke tredjepartsløsninger til administration af Microsoft Defender Antivirus.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-updates"></a>Opret en UNC-deling til sikkerhedsintelligensopdateringer

Konfigurer et netværksfilshare (UNC/tilknyttet drev) til at hente sikkerhedsintelligensopdateringer fra MMPC-webstedet ved hjælp af en planlagt opgave.

1. På det system, hvor du vil klargøre delingen og hente opdateringerne, skal du oprette en mappe, som scriptet skal gemmes i.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Opret den mappe, som signaturopdateringerne skal gemmes i.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Download PowerShell-scriptet [fra www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Klik **på Manuel download**.

5. Klik **på Download den rå nupkg-fil**.

6. Udtræk filen.

7. Kopiér filen SignatureDownloadCustomTask.ps1 den mappe, du tidligere har oprettet. `C:\Tool\PS-Scripts\`

8. Brug kommandolinjen til at konfigurere den planlagte opgave.

   > [!NOTE]
   > Der findes to typer opdateringer: fuld og delta.

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
   > Når de planlagte opgaver er oprettet, kan du finde disse i Opgavestyring under `Microsoft\Windows\Windows Defender`.

9. Kør hver opgave manuelt, og bekræft, at du har data (`mpam-d.exe`, `mpam-fe.exe``nis_full.exe`og ) i følgende mapper (du har muligvis valgt forskellige placeringer):

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
    > Problemer kan også skyldes eksekveringspolitik.

10. Opret et share, der peger `C:\Temp\TempSigs` på (f.eks. `\\server\updates`).

    > [!NOTE]
    > Godkendte brugere skal som minimum have "Læse"-adgang. Dette krav gælder også for domænecomputere, deling og NTFS (sikkerhed).

11. Indstil delingsplaceringen i politikken til delingen.

    > [!NOTE]
    > Tilføj ikke mappen x64 (eller x86) i stien. Den mpcmdrun.exe proces tilføjer den automatisk.

## <a name="related-articles"></a>Relaterede artikler

- [Installér Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Administrere Microsoft Defender Antivirus opdateringer og anvende oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Administrere opdateringer for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Administrer opdateringer til mobilenheder og VM'er](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
