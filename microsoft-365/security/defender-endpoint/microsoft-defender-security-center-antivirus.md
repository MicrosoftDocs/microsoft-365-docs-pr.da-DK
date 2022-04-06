---
title: Microsoft Defender Antivirus i Windows Sikkerhed appen
description: Nu Microsoft Defender Antivirus inkluderet i Windows Sikkerhed, kan du gennemse, sammenligne og udføre almindelige opgaver.
keywords: wdav, antivirus, firewall, sikkerhed, vinduer
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1c5177946ff3d54ab64c78e9013a8e0c07b0fd11
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468121"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Microsoft Defender Antivirus i Windows Sikkerhed appen

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I Windows 10 version 1703 og nyere er Windows Defender en del af Windows Sikkerhed.

Indstillinger, der tidligere var en del af Windows Defender-klienten og hoved Windows Indstillinger, er blevet kombineret og flyttet til den nye app, der er installeret som standard som en del af Windows 10, version 1703.

> [!IMPORTANT]
> Deaktivering af Windows Sikkerhed-apptjenesten deaktiverer ikke Microsoft Defender Antivirus eller [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Disse deaktiveres automatisk, når et antivirus- eller firewallprodukt fra en tredjepart installeres og holdes opdateret.
>
> Hvis du deaktiverer Windows Sikkerhed-apptjenesten eller konfigurerer dens tilknyttede Gruppepolitik-indstillinger for at forhindre den i at starte eller køre, kan Windows Sikkerhed-appen vise forældede eller unøjagtige oplysninger om eventuelle antivirus- eller firewallprodukter, du har installeret på enheden.
> Det kan også forhindre Microsoft Defender Antivirus i at aktivere sig selv, hvis du har et gammelt eller forældet antivirusprogram fra tredjepart, eller hvis du fjerner et antivirusprogram fra en tredjepart, du tidligere har installeret.
> Dette vil sænke beskyttelsen af din enhed betydeligt og kan føre til malware inficeret.

Se artiklen [Windows Sikkerhed, hvis](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) du vil have mere at vide Windows andre sikkerhedsfunktioner, der kan overvåges i appen.

Appen Windows Sikkerhed er en klientgrænseflade på Windows 10, version 1703 og nyere. Det er ikke den Microsoft 365 Defender, der bruges til at gennemse og administrere [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Gennemse indstillingerne for virus- og trusselsbeskyttelse i Windows Sikkerhed appen

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Indstillinger for virus- og trusselsbeskyttelse Windows Sikkerhed appen" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Åbn Windows Sikkerhed-appen ved at klikke på skjoldet på proceslinjen eller søge i menuen Start efter **Windows Sikkerhed**.

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

I de følgende afsnit beskrives det, hvordan du udfører nogle af de mest almindelige opgaver, når du gennemser eller interagerer med den trusselsbeskyttelse, der leveres Microsoft Defender Antivirus i Windows Sikkerhed-appen.

> [!NOTE]
> Hvis disse indstillinger er konfigureret og installeret ved hjælp af Gruppepolitik, bliver de indstillinger, der er beskrevet i dette afsnit, nedtonet og utilgængelige til brug på individuelle slutpunkter. Ændringer, der er foretaget via Gruppepolitik-objekt, skal først installeres til individuelle slutpunkter, før indstillingen opdateres Windows Indstillinger. I [emnet Konfigurer slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md) beskrives det, hvordan indstillinger for tilsidesættelse af lokal politik kan konfigureres.

## <a name="run-a-scan-with-the-windows-security-app"></a>Kør en scanning med Windows Sikkerhed appen

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen **Start, og** **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Hurtig scanning**. Hvis du vil køre en fuld scanning, skal du **vælge Scanningsindstillinger** og derefter vælge en indstilling, f.eks **. Fuld scanning**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Gennemse sikkerheds intelligence-opdateringsversionen, og download de seneste opdateringer i Windows Sikkerhed appen

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Sikkerhedsintelligens versionsnummer" lightbox="../../media/wdav-wdsc-defs.png":::

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen *Start, og* **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Opdateringer & virusbeskyttelse**. Den installerede version vises sammen med nogle oplysninger om, hvornår den blev downloadet. Du kan kontrollere din aktuelle version i forhold til den nyeste version, der kan hentes manuelt, eller du kan gennemse ændringsloggen for den pågældende version. Se [Sikkerhedsintelligens-opdateringer til Microsoft Defender Antivirus og anden Microsoft-antimalware](https://www.microsoft.com/wdsi/defenderupdates).

4. Vælg **Søg efter opdateringer for** at downloade nye sikkerhedsopdateringer (hvis der er nogen).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Kontrollér Microsoft Defender Antivirus er aktiveret i Windows Sikkerhed appen

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen *Start, og* **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Indstillinger & mod virusbeskyttelse**.

4. Slå beskyttelse **i realtid til** **Til**.

    > [!NOTE]
    > Hvis du slår **beskyttelse i realtid** fra, bliver den automatisk slået til igen efter kort tid. Dette sikrer, at du er beskyttet mod malware og trusler.
    > Hvis du installerer et andet antivirusprodukt, deaktiverer Microsoft Defender Antivirus automatisk sig selv og angives som sådan i Windows Sikkerhed-appen. Der vises en indstilling, der gør det muligt at aktivere [begrænset periodisk scanner](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Tilføj udeladelse for Microsoft Defender Antivirus i Windows Sikkerhed appen

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen *Start, og* **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Administrer & under Indstillinger** for **trusselsbeskyttelse under Virusbeskyttelse**.

4. Under **Udeladelse skal** du **vælge Tilføj eller fjern udeladelse.**

5. Vælg plusikonet (**+**) for at vælge typen og angive indstillingerne for hver udeladelse.

Følgende tabel opsummerer udeladelsestyper, og hvad der sker:

<br>

****
|Udeladelsestype|Defineret af|Hvad sker der?|
|---|---|---|
|**Filer**|Placering <br/>Eksempel: `c:\sample\sample.test`|Den specifikke fil ignoreres af Microsoft Defender Antivirus.|
|**Mappe**|Placering <br/>Eksempel: `c:\test\sample`|Alle elementer i den angivne mappe ignoreres med Microsoft Defender Antivirus.|
|**Filtype**|Filtypenavn <br/>Eksempel: `.test`|Alle filer med udvidelsen `.test` et vilkårligt sted på din enhed springes over af Microsoft Defender Antivirus.|
|**Proces**|Eksekverbar filsti <br>Eksempel: `c:\test\process.exe`|Den specifikke proces og eventuelle filer, der åbnes af denne proces, ignoreres af Microsoft Defender Antivirus.|
|

Du kan få mere at vide i følgende ressourcer:

- [Konfigurere og validere udeladelse baseret på filtypenavn og mappeplacering](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurere udeladelse af filer, der er åbnet af processer](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Gennemse historikken for trusselsregistrering i Windows Defender for Cloud-app

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen *Start, og* **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Historik for beskyttelse**. Alle de seneste elementer vises.

## <a name="set-ransomware-protection-and-recovery-options"></a>Angiv indstillinger for beskyttelse mod ransomware og gendannelse

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen *Start, og* **vælg Windows Sikkerhed.**

2. Vælg **flisen & for trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Under **Ransomware-beskyttelse** skal du **vælge Administrer beskyttelse mod ransomware**.

4. Hvis du vil **ændre indstillinger for styret mappeadgang** , [skal du se Beskyt vigtige mapper med styret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Hvis du vil konfigurere indstillinger for gendannelse af ransomware, skal du vælge **Konfigurer under** **Gendannelse af ransomware-data** og følge vejledningen til at sammenkæde eller konfigurere din OneDrive-konto, så du nemt kan gendanne efter en ransomware-angreb.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md)
