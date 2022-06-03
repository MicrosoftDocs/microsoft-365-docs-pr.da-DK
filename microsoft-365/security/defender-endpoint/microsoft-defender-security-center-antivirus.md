---
title: Microsoft Defender Antivirus i appen Windows Sikkerhed
description: Når Microsoft Defender Antivirus nu er inkluderet i Windows Sikkerhed-appen, kan du gennemse, sammenligne og udføre almindelige opgaver.
keywords: wdav, antivirus, firewall, sikkerhed, windows
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
ms.openlocfilehash: bd045ac36f1685c3bf12cedf04dd074ed6c7fc5e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873980"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Microsoft Defender Antivirus i appen Windows Sikkerhed

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I Windows 10 version 1703 og nyere er appen Windows Defender en del af Windows Sikkerhed.

Indstillinger, der tidligere var en del af Windows Defender-klienten og de primære Windows Indstillinger, er blevet kombineret og flyttet til den nye app, som som standard installeres som en del af Windows 10 version 1703.

> [!IMPORTANT]
> Deaktivering af Windows Sikkerhed apptjenesten deaktiverer ikke Microsoft Defender Antivirus eller [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Disse deaktiveres automatisk, når et antivirus- eller firewallprodukt fra tredjepart installeres og holdes opdateret.
> Hvis du deaktiverer Windows Sikkerhed-apptjenesten eller konfigurerer de tilknyttede indstillinger for Gruppepolitik for at forhindre den i at starte eller køre, kan den Windows Sikkerhed app vise forældede eller unøjagtige oplysninger om eventuelle antivirus- eller firewallprodukter, du har installeret på enheden.
> Det kan også forhindre Microsoft Defender Antivirus i at aktivere sig selv, hvis du har et gammelt eller forældet antivirusprogram fra tredjepart, eller hvis du fjerner et antivirusprogram fra tredjepart, som du tidligere har installeret.
> Dette vil reducere beskyttelsen af din enhed betydeligt og kan føre til malware-infektion.

Se artiklen [om Windows Sikkerhed](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) for at få flere oplysninger om andre Windows sikkerhedsfunktioner, der kan overvåges i appen.

Appen Windows Sikkerhed er en klientgrænseflade på Windows 10, version 1703 og nyere. Det er ikke den Microsoft 365 Defender webportal, der bruges til at gennemse og administrere [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Gennemse indstillinger for beskyttelse mod virus og trusler i Windows Sikkerhed-appen

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Indstillinger for beskyttelse mod virus og trusler i Windows Sikkerhed app" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Åbn appen Windows Sikkerhed ved at klikke på skjoldikonet på proceslinjen eller ved at søge i menuen Start efter **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

I følgende afsnit beskrives det, hvordan du udfører nogle af de mest almindelige opgaver, når du gennemser eller interagerer med den trusselsbeskyttelse, der leveres af Microsoft Defender Antivirus i appen Windows Sikkerhed.

> [!NOTE]
> Hvis disse indstillinger konfigureres og installeres ved hjælp af Gruppepolitik, er de indstillinger, der er beskrevet i dette afsnit, nedtonet og utilgængelige til brug på individuelle slutpunkter. Ændringer, der foretages via et Gruppepolitik objekt, skal først installeres på individuelle slutpunkter, før indstillingen opdateres i Windows Indstillinger. I emnet [Konfigurer slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md) beskrives det, hvordan indstillinger for tilsidesættelse af lokal politik kan konfigureres.

## <a name="run-a-scan-with-the-windows-security-app"></a>Kør en scanning med Windows Sikkerhed-appen

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter **Sikkerhed** og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Hurtig scanning**. Eller hvis du vil køre en fuld scanning, skal du vælge **Scanningsindstillinger** og derefter vælge en indstilling, f.eks **. Fuld scanning**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Gennemse versionen af sikkerhedsintelligensopdateringen, og download de nyeste opdateringer i Windows Sikkerhed-appen

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Versionsnummer for sikkerhedsintelligens" lightbox="../../media/wdav-wdsc-defs.png":::

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter *Sikkerhed* og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Opdateringer til virus & trusselsbeskyttelse**. Den installerede version vises sammen med nogle oplysninger om, hvornår den blev downloadet. Du kan kontrollere din aktuelle i forhold til den nyeste version, der kan downloades manuelt, eller gennemse ændringsloggen for den pågældende version. Se [Opdateringer til sikkerhedsintelligens for Microsoft Defender Antivirus og anden Microsoft antimalware](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

4. Vælg **Søg efter opdateringer for** at downloade nye beskyttelsesopdateringer (hvis der er nogen).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Sørg for, at Microsoft Defender Antivirus er aktiveret i appen Windows Sikkerhed

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter *Sikkerhed* og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Indstillinger for virus & trusselsbeskyttelse**.

4. Slå beskyttelse i **realtid** til **Til**.

    > [!NOTE]
    > Hvis du slår **beskyttelse i realtid** fra, tændes den automatisk igen efter en kort forsinkelse. Dette er for at sikre, at du er beskyttet mod malware og trusler.
    > Hvis du installerer et andet antivirusprogram, deaktiverer Microsoft Defender Antivirus automatisk sig selv og er angivet som sådan i Windows Sikkerhed-appen. Der vises en indstilling, der giver dig mulighed for at aktivere [begrænset periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Tilføj udeladelser for Microsoft Defender Antivirus i appen Windows Sikkerhed

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter *Sikkerhed* og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Under **Indstillinger for virus & trusselsbeskyttelse** skal du vælge **Administrer indstillinger**.

4. Under **Udeladelser** skal du vælge **Tilføj eller fjern udeladelser**.

5. Vælg plusikonet (**+**) for at vælge typen og angive indstillingerne for hver udeladelse.

I følgende tabel opsummeres udeladelsestyper, og hvad der sker:

|Udeladelsestype|Defineret af|Hvad sker der|
|---|---|---|
|**Filer**|Placering <br/>Eksempel: `c:\sample\sample.test`|Den specifikke fil springes over af Microsoft Defender Antivirus.|
|**Mappe**|Placering <br/>Eksempel: `c:\test\sample`|Alle elementer i den angivne mappe springes over af Microsoft Defender Antivirus.|
|**Filtype**|Filtypenavn <br/>Eksempel: `.test`|Alle filer med `.test` udvidelsen overalt på din enhed springes over af Microsoft Defender Antivirus.|
|**Proces**|Eksekverbar filsti <br>Eksempel: `c:\test\process.exe`|Den specifikke proces og eventuelle filer, der åbnes af den pågældende proces, springes over af Microsoft Defender Antivirus.|

Du kan få mere at vide i følgende ressourcer:

- [Konfigurer og valider udeladelser baseret på filtypenavn og mappeplacering](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Konfigurer udeladelser for filer, der er åbnet af processer](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Gennemse oversigten over trusselsregistrering i Windows Defender for Cloud-appen

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter *Sikkerhed* og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Vælg **Beskyttelsesoversigt**. Eventuelle seneste elementer vises.

## <a name="set-ransomware-protection-and-recovery-options"></a>Angiv indstillinger for beskyttelse og genoprettelse af ransomware

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter *Sikkerhed* og derefter vælge **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre).

3. Under **Ransomware-beskyttelse** skal du vælge **Administrer ransomware-beskyttelse**.

4. Hvis du vil ændre indstillinger for **adgang til styrede mapper** , skal du se [Beskyt vigtige mapper med adgang via kontrolleret mappe](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Hvis du vil konfigurere indstillinger for ransomware-gendannelse, skal du vælge **Konfigurer** under **Ransomware-datagendannelse** og følge instruktionerne for at linke eller konfigurere din OneDrive-konto, så du nemt kan komme dig efter et ransomware-angreb.

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus](microsoft-defender-antivirus-in-windows-10.md)
