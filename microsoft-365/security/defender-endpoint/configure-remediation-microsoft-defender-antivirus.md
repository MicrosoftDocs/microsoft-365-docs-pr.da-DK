---
title: Konfigurere afhjælpning af Microsoft Defender Antivirus registreringer
description: Konfigurer, Microsoft Defender Antivirus skal gøre, når der registreres en trussel, og hvor længe filer, der er i karantæne, skal opbevares i karantænemappen
keywords: afhjælpning, løse, fjerne, trusler, sætte i karantæne, scanne, gendanne
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
ms.openlocfilehash: 182e0b39c1a9c7795fbdd716fc2e260d06d5c451
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63593204"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Konfigurere afhjælpning af Microsoft Defender Antivirus registreringer


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når Microsoft Defender Antivirus kører en scanning, forsøger den at afhjælpe eller fjerne de registrerede trusler. Du kan konfigurere, Microsoft Defender Antivirus skal håndtere bestemte trusler, om der skal oprettes et gendannelsespunkt, før afhjælpningen fjernes, og hvornår trusler skal fjernes.

Denne artikel beskriver, hvordan du konfigurerer disse indstillinger ved hjælp Gruppepolitik, men du kan også bruge [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) og [Microsoft Intune](/intune/device-restrictions-configure).

Du kan også bruge [`Set-MpPreference` PowerShell-cmdlet'en eller](/powershell/module/defender/set-mppreference) [`MSFT_MpPreference` WMI-klassen](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) til at konfigurere disse indstillinger.

## <a name="configure-remediation-options"></a>Konfigurere afhjælpningsindstillinger

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I **administrationseditoren Gruppepolitik skal** du **gå til Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows flere** \> **Microsoft Defender Antivirus**.

4. Brug tabellen nedenfor til at vælge en placering, og rediger derefter politikken efter behov.

5. Vælg **OK**.

<br/><br/>

|Placering|Indstilling|Beskrivelse|Standardindstilling (hvis den ikke er konfigureret)|
|---|---|---|---|
|Scan|Opret et systemgendannelsespunkt|Der oprettes et systemgendannelsespunkt hver dag, før der forsøges på at rydde op eller scanne systemet|Deaktiveret|
|Scan|Slå fjernelse af elementer fra mappen med scanningsoversigten til|Angiv, hvor mange dage elementer skal gemmes i scanningsoversigten|30 dage|
|Rod|Slå rutinemæssig afhjælpning fra|Du kan angive, Microsoft Defender Antivirus automatisk afhjælper trusler, eller om slutpunktsbrugeren skal spørge, hvad der skal gøres.|Deaktiveret (trusler afhjælpes automatisk)|
|Karantæne|Konfigurere fjernelse af elementer fra karantænemappen|Angiv, hvor mange dage elementer skal opbevares i karantæne, før de fjernes|90 dage|
|Trusler|Angive niveauer for besked om trusler, hvor standardhandlingen ikke skal tages, når den registreres|Enhver trussel, der registreres af Microsoft Defender Antivirus, tildeles et trusselsniveau (lav, mellem, høj eller alvorlig). Du kan bruge denne indstilling til at definere, hvordan alle trusler for hvert af trusselsniveauerne skal afhjælpes (sat i karantæne, fjernes eller ignoreres)|Ikke relevant|
|Trusler|Angive trusler, som standardhandlingen ikke skal anvendes på, når den registreres|Angiv, hvordan bestemte trusler (ved hjælp af deres trussels-id) skal afhjælpes. Du kan angive, om den specifikke trussel skal være i karantæne, fjernet eller ignoreret|Ikke relevant|

> [!IMPORTANT]
> Microsoft Defender Antivirus registrerer og afhjælper filer baseret på mange faktorer. Nogle gange kræver afhjælpning en genstart. Selvom registrering senere vurderes som en falsk positiv, skal genstart udføres for at sikre, at alle yderligere afhjælpningstrin er fuldført.
>
> Hvis du er sikker på Microsoft Defender Antivirus har sat en fil i karantæne baseret på en falsk positiv, kan du gendanne filen fra karantæne, når enheden genstarter. Se [Gendan filer, der er i karantæne, Microsoft Defender Antivirus](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> For at undgå dette problem i fremtiden kan du udelade filer fra scanningerne. Se [Konfigurere og validere udeladelse for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md).

Se også [Konfigurer planlagte fulde scanninger Microsoft Defender Antivirus afhjælpning for at få mere afhjælpningsrelaterede](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) indstillinger.

## <a name="see-also"></a>Se også

- [Konfigurere Microsoft Defender Antivirus indstillinger for scanning](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Konfigurere planlagte Microsoft Defender Antivirus scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Konfigurere og køre on-demand-Microsoft Defender Antivirus scanninger](run-scan-microsoft-defender-antivirus.md)
- [Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurere slutbrugerens Microsoft Defender Antivirus interaktion](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Tilpas, initier og gennemse resultaterne Microsoft Defender Antivirus scanninger og afhjælpning](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
