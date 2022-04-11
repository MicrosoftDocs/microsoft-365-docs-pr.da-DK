---
title: Få mere at vide om og konfigurer browser til styring af insiderrisiko ved signalregistrering
description: Få mere at vide om browser til styring af insiderrisiko i Microsoft 365
keywords: Microsoft 365, insiderrisikostyring, risikostyring, overholdelse af angivne standarder
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
ms.openlocfilehash: e904c4576081cd459ca905a56e3dd6cec5b1af31
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758723"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Få mere at vide om og konfigurer browser til styring af insiderrisiko ved signalregistrering

Webbrowsere bruges ofte af brugere til at få adgang til både følsomme og ikke-følsomme filer i en organisation. Styring af insiderrisiko giver din organisation mulighed for at registrere og reagere på browserudfiltreringssignaler for alle ikke-eksekverbare filer, der vises i [Microsoft Edge](https://www.microsoft.com/edge)- og [Google Chrome-browsere](https://www.google.com/chrome). Med disse signaler kan analytikere og efterforskere hurtigt reagere, når en af følgende aktiviteter udføres af brugere af politikker i området, når de bruger disse browsere:

- Filer, der er kopieret til et personligt cloudlager
- Filer, der udskrives på lokale enheder eller netværksenheder
- Filer, der er overført eller kopieret til et netværksshare
- Filer, der er kopieret til USB-enheder

Signaler til disse hændelser registreres i Microsoft Edge ved hjælp af indbyggede browserfunktioner og ved hjælp af tilføjelsesprogrammet *Microsoft Compliance Extension*. I Google Chrome bruger kunderne *Microsoft Compliance Extension* til signalregistrering.

I følgende tabel opsummeres registrerede aktiviteter og udvidelsesunderstøttelse for hver browser:

| **Registrerede aktiviteter**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Filer, der er kopieret til et personligt cloudlager         | Indfødte             | Udvidelse         |
| Filer, der udskrives på lokale enheder eller netværksenheder      | Indfødte             | Udvidelse         |
| Filer, der er overført eller kopieret til et netværksshare | Udvidelse          | Udvidelse         |
| Filer, der er kopieret til USB-enheder                    | Udvidelse          | Udvidelse         |

## <a name="common-requirements"></a>Almindelige krav

Før du installerer Microsoft Edge-tilføjelsesprogrammet eller Google Chrome-udvidelsen, skal kunderne sikre, at enheder til brugere med en politik i omfang opfylder følgende krav:

- Seneste Windows 10 x64-build anbefales, minimum Windows 10 x64 build 1809 for understøttelse af signalregistrering. Browsersignalregistrering understøttes ikke i øjeblikket på enheder, der ikke er Windows.
- Nuværende [Microsoft 365 abonnement](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) med understøttelse af styring af insiderrisiko.
- Enheder skal [onboardes](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) til portalen for Microsoft 365 overholdelse.

Du kan se specifikke krav til konfiguration af browsere i afsnittene Microsoft Edge og Google Chrome senere i denne artikel.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Konfigurer browsersignalregistrering for Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>krav til Microsoft Edge browser

- Opfylder de almindelige krav
- Microsoft Edge x64, 91.0.864.41 eller nyere
- *Tilføjelsesprogrammet Microsoft Compliance Extension* version 1.0.0.44 eller nyere
- Edge.exe er ikke konfigureret som en webbrowser, der ikke er tilladt

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Mulighed 1: Grundlæggende konfiguration (anbefales til test med Edge)

Brug denne indstilling til at konfigurere selfhost for en enkelt maskine for hver enhed i din organisation, når du tester signalregistrering i browseren.

Fuldfør følgende trin for den grundlæggende konfiguration:

1. Gå til [Microsoft Compliance Extension](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Installér udvidelsen.

### <a name="option-2-intune-setup-for-edge"></a>Mulighed 2: Intune opsætning for Edge

Brug denne indstilling til at konfigurere udvidelsen og kravene for din organisation ved hjælp af Intune.

Du kan finde indstillingen Intune konfiguration ved at udføre følgende trin:

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com) ved hjælp af administratortilladelser.
2. Gå til **Konfigurationsprofiler**.
3. Vælg **Opret profil**.
4. Vælg **Windows 10** som platform.
5. Vælg **Administrative skabeloner** som *profiltype* , og vælg **Opret.**
6. Vælg fanen **Indstillinger**.
7. Vælg **Edge Version 77 og nyere.**
8. Søg efter **Udvidelser** , som giver dig et overblik over alle udvidelsesrelaterede indstillinger.
9. Vælg indstillingen **Kontrolelement for, hvilke udvidelser der installeres uovervåget.**
10. Vælg **Aktiveret.**
11. Tilføj udvidelses-id'et, når du bliver bedt om det: *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. Vælg **OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Mulighed 3: Gruppepolitik installation for Edge

Brug denne indstilling til at konfigurere udvidelsen og kravene til hele organisationen ved hjælp af Gruppepolitik.

For indstillingen Gruppepolitik konfiguration skal du udføre følgende trin:

**Trin 1: Importér den nyeste Microsoft Edge administrative skabelonfil (.admx).**

Enheder skal kunne administreres ved hjælp af gruppepolitikker, og alle [Microsoft Edge Administrative skabeloner](https://www.microsoft.com/edge/business/download) skal importeres til Gruppepolitik Central Store. Du kan få flere oplysninger under [Sådan opretter og administrerer du det centrale Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Trin 2: Føj *tilføjelsesprogrammet Microsoft Compliance Extension* til listen *Gennemtving installation* .**

Udfør følgende trin for at tilføje udvidelsen:

1. I **editoren til Gruppepolitik administration** skal du navigere til organisationsenheden.
2. Udvid følgende sti **Konfigurationspolitikker** \> for \> **computer/bruger** **Administrative skabeloner** \> **Klassiske administrative skabeloner** \> **Microsoft Edge** \> **Udvidelser**. Denne sti kan variere afhængigt af konfigurationen for din organisation.
3. Vælg **Konfigurer, hvilke udvidelser der installeres uovervåget.**
4. Højreklik, og vælg **Rediger**.
5. Kontrollér alternativknappen **Aktiveret** .
6. Vælg **Vis**.
7. For **Value** skal du tilføje følgende post: *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Vælg **OK** , og vælg **Anvend**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Konfigurer browsersignalregistrering for Google Chrome

Understøttelse af signalregistrering i browseren til styring af insiderrisiko for Google Chrome aktiveres via *Microsoft Compliance Extension*. Denne udvidelse understøtter også Endpoint DLP på Chrome. Du kan finde flere oplysninger om understøttelse af DLP-slutpunkt i [Kom i gang med Microsoft Compliance Extension (prøveversion).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>Krav til Google Chrome-browser

- Opfylder almindelige krav
- Seneste version af Google Chrome x64
- *Microsoft Compliance Extension* version 2.0.0.183 eller nyere
- Chrome.exe er ikke konfigureret som en webbrowser, der ikke er tilladt

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Mulighed 1: Grundlæggende konfiguration (anbefales til test med Chrome)

Brug denne indstilling til at konfigurere selfhost for en enkelt maskine for hver enhed i din organisation, når du tester signalregistrering i browseren.

Fuldfør følgende trin for den grundlæggende konfiguration:

**Trin 1: Aktivér påkrævede registreringsdatabasenøgler med PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Disse registreringsdatabasenøgler er påkrævet for at sikre korrekt funktionalitet af udvidelsen. Du skal aktivere disse registreringsdatabasenøgler, før du tester signaler.*

**Trin 2: Installér *Microsoft Compliance-udvidelsen***

1. Gå til [Microsoft Compliance Extension](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Installér udvidelsen.

### <a name="option-2-intune-setup-for-chrome"></a>Mulighed 2: Intune konfiguration til Chrome

Brug denne indstilling til at konfigurere udvidelsen og kravene for din organisation ved hjælp af Intune.

Du kan finde indstillingen Intune konfiguration ved at udføre følgende trin:

**Trin 1: Aktivér den påkrævede registreringsdatabasenøgle med Intune**

1. Kør følgende PowerShell-script:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).
3. Gå til **Scripts** for **enheder,** \> og vælg **Tilføj.**
4. Gå til placeringen af det script, der blev oprettet, da du blev bedt om det.
5. Vælg følgende indstillinger:

    - Kør dette script ved hjælp af legitimationsoplysningerne, der er logget på: *Ja*
    - Gennemtving kontrol af scriptsignatur: *Nej*
    - Kør script i 64-bit PowerShell-vært: *Ja*

6. Vælg de relevante enhedsgrupper, og anvend politikken.

**Trin 2: Konfigurer Intune Gennemtving installation**

Før du føjer Udvidelsen Microsoft DLP Chrome til listen over tv-installerede udvidelser, skal du installere Chrome-filen med den administrative skabelon (.admx) til Intune administration. Du kan finde en trinvis vejledning under [Administrer Chrome-browser med Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Når du har installeret filen med den administrative skabelon, skal du udføre følgende trin:

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).
2. Gå til **Konfigurationsprofiler**.
3. Vælg **Opret profil**.
4. Vælg **Windows 10** som *platform*.
5. Vælg **Brugerdefineret** som *profiltype* .
6. Vælg fanen **Indstillinger**.
7. Vælg **Tilføj.**
8. Angiv følgende politikoplysninger:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Datatype: *Streng*
    - Værdi: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. Vælg **Opret**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Mulighed 3: Gruppepolitik opsætning til Chrome

Brug denne indstilling til at konfigurere udvidelsen og kravene til hele organisationen ved hjælp af Gruppepolitik.

For indstillingen Gruppepolitik konfiguration skal du udføre følgende trin:

**Trin 1: Importér filen med den administrative Chrome-skabelon**

Dine enheder skal kunne administreres ved hjælp af Gruppepolitik, og alle [administrative Chrome-skabeloner](https://chromeenterprise.google/browser/download/) skal importeres til Gruppepolitik Central Store. Du kan få flere oplysninger under [Sådan opretter og administrerer du det centrale Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Trin 2: Aktivér den påkrævede registreringsdatabasenøgle med PowerShell**

1. Opret et PowerShell-script med følgende indhold:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Åbn **administrationskonsollen for Gruppepolitik**, og naviger til organisationsenheden.
3. Højreklik, og vælg **Opret et gruppepolitikobjekt i dette domæne, og opret et link til det her**. Når du bliver bedt om det, skal du tildele dette Gruppepolitik objekt et beskrivende navn. F.eks. *DLP Chrome Immediate PowerShell-script*.
4. Når du har oprettet gruppepolitikobjektet, skal du højreklikke og vælge **Rediger**. Dette valg fører dig til det Gruppepolitik objekt.
5. Gå til Indstillinger **for** \> **computerkonfiguration** \> **Kontrolpanel indstillinger** \> **Planlagte opgaver**.
6. Højreklik på det tomme område under **Planlagte opgaver,** og vælg **Ny** \> **øjeblikkelig opgave (mindst Windows 7).**
7. Angiv et *opgavenavn* og en *beskrivelse*.
8. Vælg den tilsvarende konto for at køre den øjeblikkelige opgave. Det kan f.eks. *være NT Authority*.
9. Vælg **Kør med de højeste rettigheder**.
10. Konfigurer politikken for Windows 10.
11. Vælg **Start et program** under fanen **Handlinger**.
12. Angiv stien til det program/script, der blev oprettet i **trin 1**.
13. Vælg **Anvend**.

**Trin 3: Føj Chrome-udvidelsen til listen Gennemtving installation**

1. I **Gruppepolitik Management Editor** skal du navigere til organisationsenheden.
2. Udvid følgende sti **Konfigurationspolitikker** \> for \> **computer/bruger** **Administrative skabeloner** \> **Klassiske administrative skabeloner** \> **Google** \> **Chrome-udvidelser**\>. Denne sti kan variere afhængigt af konfigurationen for din organisation.
3. Vælg **Konfigurer listen over tving installerede udvidelser**.
4. Højreklik, og vælg **Rediger**.
5. Vælg alternativknappen **Aktiveret** .
6. Vælg **Vis**.
7. For **Value** skal du tilføje følgende post: *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Vælg **OK** , og vælg **Anvend**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Test og bekræft signalregistreringer i browseren til styring af insiderrisiko

1. Opret en politik for styring af insiderrisiko med enhedsindikatorer aktiveret.
2. Hvis du vil teste signalregistrering for filer, der er kopieret til et personligt cloudlager, skal du udføre følgende trin fra en understøttet Windows enhed:

    - Åbn et websted til fildeling (Microsoft OneDrive, Google Drev osv.) med den browsertype, du har konfigureret til signalregistrering.
    - Med browseren kan du overføre en ikke-eksekverbar fil til webstedet.
3. Hvis du vil teste signalregistrering for filer, der udskrives på lokale enheder eller netværksenheder, filer, der er overført eller kopieret til et netværksshare, og filer, der er kopieret til USB-enheder, skal du udføre følgende trin fra en understøttet Windows enhed:

    - Åbn en ikke-eksekverbar fil direkte i browseren. Filen skal åbnes direkte via Stifinder eller åbnes i en ny browserfane til visning i stedet for en webside.
    - Udskriv filen.
    - Gem filen på en USB-enhed.
    - Gem filen på et netværksdrev.
  
4. Når din første politik for styring af insiderrisiko blev oprettet, begynder du at modtage beskeder fra aktivitetsindikatorer efter ca. 24 timer. Kontrollér [dashboardet Beskeder](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) for insiderrisikostyringsbeskeder for de testede aktiviteter.
