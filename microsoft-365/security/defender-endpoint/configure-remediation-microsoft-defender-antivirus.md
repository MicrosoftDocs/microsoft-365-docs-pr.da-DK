---
title: Konfigurer afhjælpning af Microsoft Defender Antivirus registreringer
description: Konfigurer, hvad Microsoft Defender Antivirus skal gøre, når der registreres en trussel, og hvor længe karantænefiler skal opbevares i karantænemappen
keywords: afhjælpning, rettelse, fjernelse, trusler, karantæne, scanning, gendannelse
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f07e62edd43098a493c80ca7f3155c148793578e
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419170"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Konfigurer afhjælpning af Microsoft Defender Antivirus registreringer


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Når Microsoft Defender Antivirus kører en scanning, forsøger den at afhjælpe eller fjerne de trusler, der registreres. Du kan konfigurere, hvordan Microsoft Defender Antivirus skal håndtere visse trusler, om der skal oprettes et gendannelsespunkt, før du afhjælper, og hvornår trusler skal fjernes.

I denne artikel beskrives det, hvordan du konfigurerer disse indstillinger ved hjælp af Gruppepolitik, men du kan også bruge [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) og [Microsoft Intune](/intune/device-restrictions-configure).

Du kan også bruge [PowerShell-cmdlet'en`Set-MpPreference`](/powershell/module/defender/set-mppreference) eller [`MSFT_MpPreference` WMI-klassen](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) til at konfigurere disse indstillinger.

## <a name="configure-remediation-options"></a>Konfigurer afhjælpningsindstillinger

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklik på det Gruppepolitik objekt, du vil konfigurere, og klik på **Rediger**.

2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus**.

4. Vælg en placering i tabellen nedenfor, og rediger derefter politikken efter behov.

5. Vælg **OK**.

<br/><br/>

|Placering|Indstilling|Beskrivelse|Standardindstilling (hvis den ikke er konfigureret)|
|---|---|---|---|
|Skan|Opret et systemgendannelsespunkt|Der oprettes et systemgendannelsespunkt hver dag, før der gøres forsøg på at rense eller scanne|Deaktiveret|
|Skan|Slå fjernelse af elementer til fra mappen med scanningsoversigten|Angiv, hvor mange dage elementer skal gemmes i scanningsoversigten|30 dage|
|Rod|Deaktiver rutinemæssig afhjælpning|Du kan angive, om Microsoft Defender Antivirus automatisk afhjælper trusler, eller om brugeren af slutpunktet skal spørge, hvad der skal gøres.|Deaktiveret (trusler afhjælpes automatisk)|
|Karantæne|Konfigurer fjernelse af elementer fra karantænemappen|Angiv, hvor mange dage elementer skal holdes i karantæne, før de fjernes|90 dage|
|Trusler|Angiv niveauer for trusselsbeskeder, hvor standardhandlingen ikke skal udføres, når den registreres|Alle trusler, der opdages af Microsoft Defender Antivirus, tildeles et trusselsniveau (lavt, mellem, højt eller alvorligt). Du kan bruge denne indstilling til at definere, hvordan alle trusler for hvert trusselsniveau skal afhjælpes (sættes i karantæne, fjernes eller ignoreres)|Ikke relevant|
|Trusler|Angiv trusler, som standardhandlingen ikke skal udføres på, når den registreres|Angiv, hvordan specifikke trusler (ved hjælp af deres trussels-id) skal afhjælpes. Du kan angive, om den specifikke trussel skal sættes i karantæne, fjernes eller ignoreres|Ikke relevant|

> [!IMPORTANT]
> Microsoft Defender Antivirus registrerer og afhjælper filer baseret på mange faktorer. Nogle gange kræver fuldførelse af en afhjælpning en genstart. Selvom registreringen senere bestemmes til at være en falsk positiv, skal genstarten fuldføres for at sikre, at alle yderligere afhjælpningstrin er fuldført.
>
> Hvis du er sikker på, Microsoft Defender Antivirus sat en fil i karantæne baseret på et falsk positivt element, kan du gendanne filen fra karantæne, når enheden genstarter. Se [Gendan filer, der er sat i karantæne i Microsoft Defender Antivirus](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> Hvis du vil undgå dette problem i fremtiden, kan du udelade filer fra scanningerne. Se [Konfigurer og valider udeladelser for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md).

Se også [Konfigurer de nødvendige planlagte komplette Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) for at få flere afhjælpningsrelaterede indstillinger.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Konfigurer scanningsindstillinger for Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Konfigurer planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Konfigurer og kør scanninger efter behov Microsoft Defender Antivirus](run-scan-microsoft-defender-antivirus.md)
- [Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurer slutbrugerens Microsoft Defender Antivirus interaktion](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Tilpas, start og gennemse resultaterne af Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
