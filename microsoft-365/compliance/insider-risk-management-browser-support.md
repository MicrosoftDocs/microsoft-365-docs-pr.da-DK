---
title: Få mere at vide om og konfigurer registrering af insider-browsersignal i risikostyring
description: Få mere at vide om registrering af insider-browsersignal i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: c3cb9e432f3ea94f88c63cfad928ba577471b420
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63598042"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Få mere at vide om og konfigurer registrering af insider-browsersignal i risikostyring

Webbrowsere bruges ofte af brugerne til at få adgang til både følsomme og ikke-følsomme filer i en organisation. Insider-risikostyring gør det muligt for din organisation at registrere og reagere på browserudfyldningssignaler for alle ikke-eksekverbare filer, der vises [i Microsoft Edge](https://www.microsoft.com/edge) [og Google Chrome-browsere](https://www.google.com/chrome). Med disse signaler kan analytikere og analysebrugere hurtigt reagere, når en af følgende aktiviteter udføres af brugere af politikker inden for området, når de bruger disse browsere:

- Filer, der er kopieret til personligt skylager
- Filer, der udskrives på lokale enheder eller netværksenheder
- Filer, der er overført eller kopieret til et netværksshare
- Filer, der er kopieret til USB-enheder

Signaler for disse hændelser registreres i Microsoft Edge ved hjælp af indbyggede browserfunktioner og ved hjælp *af tilføjelsesprogrammet Microsoft Compliance Extension*. I Google Chrome bruger kunder *Microsoft-overholdelsesudvidelsen til* at registrere signaler.

Følgende tabel opsummerer registrerede aktiviteter og understøttelse af udvidelser for hver browser:

| **Registrerede aktiviteter**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Filer, der er kopieret til personligt skylager         | Native             | Udvidelse         |
| Filer, der udskrives på lokale enheder eller netværksenheder      | Native             | Udvidelse         |
| Filer, der er overført eller kopieret til et netværksshare | Udvidelse          | Udvidelse         |
| Filer, der er kopieret til USB-enheder                    | Udvidelse          | Udvidelse         |

## <a name="common-requirements"></a>Almindelige krav

Før du installerer tilføjelsesprogrammet Microsoft Edge Google Chrome- eller Google Chrome-udvidelsen, skal kunder sikre, at enheder for brugere af en omfangsbaseret politik opfylder følgende krav:

- Nyeste Windows 10 x64-build anbefales som minimum Windows 10 x64-build 1809 til understøttelse af signalregistrering. Registrering af browsersignal understøttes i øjeblikket ikke på ikke-Windows enheder.
- Aktuelt [Microsoft 365 med](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) insider-support til risikostyring.
- Enheder skal være [onboardet](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) til Microsoft 365 Compliance Portal.

Se specifikke krav til browserkonfiguration i Microsoft Edge og Google Chrome senere i denne artikel.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Konfigurer registrering af browsersignal for Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge browserkrav

- Opfylder de almindelige krav
- Microsoft Edge version x64, 91.0.864.41 eller nyere
- *Tilføjelsesprogrammet Microsoft Compliance Extension* version 1.0.0.44 eller nyere
- Edge.exe ikke er konfigureret som en ikke-tilladt browser

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Mulighed 1: Grundlæggende konfiguration (anbefales til test med Edge)

Brug denne indstilling til at konfigurere enkelt maskin-egenvært for hver enhed i organisationen, når du tester registrering af browsersignal.

Hvis du vil bruge den grundlæggende konfiguration, skal du udføre følgende trin:

1. Gå til [Microsoft Overholdelsesudvidelse](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Installer udvidelsen.

### <a name="option-2-intune-setup-for-edge"></a>Mulighed 2: Intune-konfiguration for Edge

Brug denne indstilling til at konfigurere udvidelsen og kravene for organisationen ved hjælp af Intune.

For intune-konfigurationsindstillingen skal du udføre følgende trin:

1. Log på Administration [ved Microsoft Endpoint Manager](https://endpoint.microsoft.com) hjælp af administratortilladelser.
2. Gå til **Konfigurationsprofiler**.
3. Vælg **Opret profil**.
4. Vælg **Windows 10** som platform.
5. Vælg **Administrative skabeloner som** *Profiltype,* og vælg **Opret.**
6. Vælg **Indstillinger** fane.
7. Vælg **Edge version 77 og nyere.**
8. Søg efter **Udvidelser,** som giver dig en oversigt over alle udvidelsesrelaterede indstillinger.
9. Vælg indstillingen Styr **, hvilke udvidelser der installeres automatisk.**
10. Vælg **Aktiveret.**
11. Tilføj udvidelses-id'et, når du *bliver bedt om det: lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. Vælg **OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Mulighed 3: Gruppepolitik til Edge

Brug denne indstilling til at konfigurere udvidelsen og kravene for hele organisationen ved hjælp Gruppepolitik.

For at Gruppepolitik konfigurationsindstillingen skal du udføre følgende trin:

**Trin 1: Importér den Microsoft Edge administrative skabelonfil (.admx).**

Enheder skal kunne administreres ved hjælp af gruppepolitikker[, Microsoft Edge](https://www.microsoft.com/edge/business/download) alle administrative skabeloner skal importeres Gruppepolitik Central Store. Få mere at vide under [Sådan opretter og administrerer du den centrale Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Trin 2: Føj *tilføjelsesprogrammet Microsoft Compliance Extension* til listen *Gennemtving* installation.**

Udfør følgende trin for at tilføje udvidelsen:

1. I Gruppepolitik **Administration skal** du gå til din Organisationsenhed (OU).
2. Udvid følgende sti **Politikker for konfiguration af computer/** \> **bruger** \> **Administrative skabeloner** \> **Klassiske administrative skabeloner** \> **Microsoft Edge** \> **Udvidelser**. Denne sti kan variere afhængigt af konfigurationen for din organisation.
3. Vælg **Konfigurer, hvilke udvidelser der installeres automatisk.**
4. Højreklik, og vælg **Rediger**.
5. Kontrollér **alternativknappen** Aktiveret.
6. Vælg **Vis**.
7. Tilføj **følgende** post for Værdi: *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Vælg **OK** , og vælg **Anvend**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Konfigurer registrering af browsersignal i Google Chrome

Insider-understøttelse af browsersignalregistrering for risikostyring i Google Chrome er aktiveret via *Microsoft-overholdelsesudvidelsen*. Denne udvidelse understøtter også Slutpunkt DLP i Chrome. Du kan finde flere oplysninger om DLP-understøttelse af slutpunkter [i Introduktion til Microsoft-overholdelsesudvidelsen (preview)](/microsoft-365/compliance/dlp-chrome-get-started).

### <a name="google-chrome-browser-requirements"></a>Browserkrav til Google Chrome

- Opfylder almindelige krav
- Nyeste version af Google Chrome x64
- *Microsoft Overholdelsesudvidelse* version 2.0.0.183 eller nyere
- Chrome.exe ikke er konfigureret som en ikke-tilladt browser

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Mulighed 1: Grundlæggende konfiguration (anbefales til test med Chrome)

Brug denne indstilling til at konfigurere enkelt maskin-egenvært for hver enhed i organisationen, når du tester registrering af browsersignal.

Hvis du vil bruge den grundlæggende konfiguration, skal du udføre følgende trin:

**Trin 1: Aktivér nødvendige registreringsdatabasenøgler med PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Disse registreringsdatabasenøgler er nødvendige for at sikre den korrekte funktionalitet for udvidelsen. Du skal aktivere disse registreringsdatabasenøgler, før du tester eventuelle signaler.*

**Trin 2: Installer *Microsoft Overholdelsesudvidelsen***

1. Gå til [Microsoft Overholdelsesudvidelse](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Installer udvidelsen.

### <a name="option-2-intune-setup-for-chrome"></a>Mulighed 2: Intune-konfiguration til Chrome

Brug denne indstilling til at konfigurere udvidelsen og kravene for organisationen ved hjælp af Intune.

For intune-konfigurationsindstillingen skal du udføre følgende trin:

**Trin 1: Aktivér påkrævet registreringsdatabasenøgle med Intune**

1. Kør følgende PowerShell-script:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).
3. Gå til **Enheders** \> **scripts,** og vælg **Tilføj.**
4. Gå til placeringen for det script, der blev oprettet, når du bliver bedt om det.
5. Vælg følgende indstillinger:

    - Kør dette script ved hjælp af legitimationsoplysningerne, der er logget på: *Ja*
    - Gennemtving kontrol af scriptsignatur: *Nej*
    - Kør script i 64-bit PowerShell-vært: *Ja*

6. Vælg de relevante enhedsgrupper, og anvend politikken.

**Trin 2: Konfigurer Intune Force Install**

Før du føjer Microsoft DLP Chrome-udvidelsen til listen over tv-installerede udvidelser, skal du installere den administrative Chrome-skabelonfil (.admx) til administration af Intune. Du kan finde en trinvis vejledning under [Administrer Chrome-browser med Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Når du har installeret den administrative skabelonfil, skal du udføre følgende trin:

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).
2. Gå til **Konfigurationsprofiler**.
3. Vælg **Opret profil**.
4. Vælg **Windows 10** som *platform*.
5. Vælg **Brugerdefineret** som *profiltype* .
6. Vælg **Indstillinger** fane.
7. Vælg **Tilføj.**
8. Angiv følgende politikoplysninger:

    - OMA-URI: *./device/vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Datatype: *Streng*
    - Værdi: *\<enabled/\>\<data id=”ExtensionInstallForcelistDesc” value=”1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx″/\>*

9. Vælg **Opret**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Mulighed 3: Gruppepolitik til Chrome

Brug denne indstilling til at konfigurere udvidelsen og kravene for hele organisationen ved hjælp Gruppepolitik.

For at Gruppepolitik konfigurationsindstillingen skal du udføre følgende trin:

**Trin 1: Importér den administrative Chrome-skabelonfil**

Dine enheder skal kunne administreres ved hjælp Gruppepolitik[, og alle administrative skabeloner i Chrome](https://chromeenterprise.google/browser/download/) skal importeres Gruppepolitik Central Store. Få mere at vide under [Sådan opretter og administrerer du den centrale Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Trin 2: Aktivér påkrævet registreringsdatabasenøgle med PowerShell**

1. Opret et PowerShell-script med følgende indhold:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Åbn Gruppepolitik **administrationskonsollen,** og gå til din organisationsenhed ( OU).
3. Højreklik, og vælg Opret **et gruppepolitikobjekt for dette domæne, og sammenkæd det her**. Når du bliver bedt om det, skal du tildele dette Gruppepolitik objekt (GPO). For eksempel bruger *DLP Chrome Immediate PowerShell Script*.
4. Når du har oprettet gruppepolitikobjektet, skal du højreklikke og vælge **Rediger**. Dette fører dig til Gruppepolitik objekt.
5. Gå til **Indstillinger for** **computerkonfiguration** \> \> **Kontrolpanelindstillinger for Planlagte** \> **opgaver**.
6. Højreklik på det tomme område under Planlagte opgaver **, og** vælg **Ny** \> **øjeblikkelig opgave (mindst Windows 7).**
7. Angiv en opgave *Navn* og *Beskrivelse*.
8. Vælg den tilsvarende konto for at køre den øjeblikkelige opgave. NT *Authority*.
9. Vælg **Kør med højeste rettigheder**.
10. Konfigurer politikken for Windows 10.
11. Vælg Start **et** program **på fanen Handlinger**.
12. Angiv stien til det program/script, der blev oprettet **i trin 1**.
13. Vælg **Anvend**.

**Trin 3: Føj Chrome-udvidelsen til listen Gennemtving installation**

1. I Gruppepolitik **Administration skal** du gå til din organisationsenhed (OU).
2. Udvid den følgende sti **Politikker for konfiguration af computer**\>/**bruger** \> **Administrative skabeloner** \> **Klassiske administrative skabeloner** \> **for Google** \> **Google Chrome-udvidelser**\>. Denne sti kan variere afhængigt af konfigurationen for din organisation.
3. Vælg **Konfigurer listen over tving til installerede udvidelser**.
4. Højreklik, og vælg **Rediger**.
5. Vælg **alternativknappen** Aktiveret.
6. Vælg **Vis**.
7. Tilføj **følgende** post for Værdi: *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Vælg **OK** , og vælg **Anvend**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Test og bekræft browsersignalregistreringer for Insider Risk Management

1. Opret en Insider-politik for risikostyring med enhedsindikatorer aktiveret.
2. Hvis du vil teste signalregistrering for filer, der er kopieret til personligt skylager, skal du udføre følgende trin fra en Windows enhed:

    - Åbn et websted til fildeling (Microsoft OneDrive, Google Drev osv.) med den browsertype, du har konfigureret til signalregistrering.
    - Med browseren kan du uploade en ikke-eksekverbar fil til webstedet.
3. Hvis du vil teste signalregistrering for filer, der er udskrevet til lokale enheder eller netværksenheder, filer, der er overført eller kopieret til et netværksshare, og filer, der er kopieret til USB-enheder, skal du udføre følgende trin fra en understøttet Windows enhed:

    - Åbn en ikke-eksekverbar fil direkte i browseren. Filen skal åbnes direkte via Stifinder eller åbnes i en ny fane i browseren til visning i stedet for en webside.
    - Udskriv filen.
    - Gem filen på en USB-enhed.
    - Gem filen på et netværksdrev.
  
4. Når din første Insider-politik for risikostyring blev oprettet, begynder du at modtage beskeder fra aktivitetsindikatorer efter ca. 24 timer. Se [dashboardet Beskeder](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) for insider-risikostyringsbeskeder for de testede aktiviteter.
