---
title: Konfigurere lokale tilsidesættelser for Microsoft Defender Antivirus indstillinger
description: Aktivér eller deaktiver brugere, så de ikke kan ændre indstillingerne lokalt i Microsoft Defender AV.
keywords: lokal tilsidesættelse, lokal politik, gruppepolitik, gruppepolitik, lockdown,flet, lister
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
ms.openlocfilehash: ec916b008ddb3e0669111efe2bd493c709327296
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592151"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Forhindre eller tillade brugere at redigere politikindstillingerne Microsoft Defender Antivirus lokalt


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Som standard forhindrer Microsoft Defender Antivirus, der installeres via et Gruppepolitik-objekt til slutpunkterne i dit netværk, brugerne i at ændre indstillingerne lokalt. Du kan ændre dette i nogle tilfælde.

Det kan f.eks. være nødvendigt at tillade visse brugergrupper (f.eks sikkerhedseksperter og trusselseksperter) yderligere kontrol over de enkelte indstillinger på de slutpunkter, de bruger.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Konfigurere lokale tilsidesættelser for Microsoft Defender Antivirus indstillinger

Standardindstillingen for disse politikker er **Deaktiveret**.

Hvis de er indstillet til Aktiveret **, kan** brugere på slutpunkter foretage ændringer til den tilknyttede indstilling med [Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md), lokale Gruppepolitik-indstillinger og PowerShell-cmdlet'er (hvor det er relevant).

I følgende tabel vises hver af de tilsidesættende politikindstillinger og konfigurationsvejledningen for den tilknyttede funktion eller indstilling.

Sådan konfigurerer du disse indstillinger:

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I menuen **Gruppepolitik skal du** gå til **Computerkonfiguration og** klikke på **Administrative skabeloner**.

3. Udvid træet til **Windows komponenter** >  **Microsoft Defender Antivirus** og derefter den Placering, **der er angivet** i tabellen over indstillinger (i denne artikel).

4. Dobbeltklik på **politikindstillingen som** angivet i tabellen nedenfor, og angiv indstillingen til den ønskede konfiguration. Klik **på OK**, og gentag for eventuelle andre indstillinger.

5. Installér objektet Gruppepolitik som normalt.

## <a name="table-of-settings"></a>Tabel over indstillinger

<br/><br/>

| Placering | Indstilling | Artikel |
|---|---|---|---|
| KORT |Konfigurere tilsidesættelse af lokale indstillinger for rapportering til Microsoft MAPS|[Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Karantæne|Konfigurere tilsidesættelse af lokale indstillinger for fjernelse af elementer fra mappen Karantæne|[Konfigurer afhjælpning af scanninger](configure-remediation-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af fil- og programaktivitet på computeren|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for overvågning af indgående og udgående filaktivitet | [Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for scanning af alle downloadede filer og vedhæftede filer|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurere tilsidesættelse af lokale indstillinger for at aktivere overvågning af funktionsmåder|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Beskyttelse i realtid|Konfigurer tilsidesættelse af lokale indstillinger for at aktivere beskyttelse i realtid|[Aktivér og konfigurer Microsoft Defender Antivirus altid-on-beskyttelse og -overvågning](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Afhjælpning|Konfigurere tilsidesættelse af lokale indstillinger for tidspunktet på dagen til at køre en planlagt fuld scanning for at fuldføre afhjælpningen|[Konfigurer afhjælpning af scanninger](configure-remediation-microsoft-defender-antivirus.md) |
| Scan|Konfigurere tilsidesættelse af lokale indstillinger for den maksimale procentdel af CPU-anvendelsen|[Konfigurere og køre scanninger](run-scan-microsoft-defender-antivirus.md) |
| Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlægning af scanningdag|[Konfigurere planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlagt hurtig scanning|[Konfigurere planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Scan|Konfigurere tilsidesættelse af lokale indstillinger for planlagt scanningstid|[Konfigurere planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Scan|Konfigurere tilsidesættelse af lokale indstillinger for den scanningstype, der skal bruges til en planlagt scanning|[Konfigurere planlagte scanninger](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Konfigurere, hvordan lokalt og globalt definerede lister over afhjælpning af trusler og udeladelse flettes

Du kan også konfigurere, hvordan lokalt definerede lister kombineres eller flettes med globalt definerede lister. Denne indstilling gælder for [udeladelseslister](configure-exclusions-microsoft-defender-antivirus.md), [angivne afhjælpningslister](configure-remediation-microsoft-defender-antivirus.md) og reduktion [af angrebsoverfladen](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Som standard sammenflettes lister, der er konfigureret i den lokale gruppepolitik og Windows Sikkerhed-appen, med lister, der er defineret af det relevante Gruppepolitik-objekt, som du har installeret på dit netværk. Hvis der opstår konflikter, har den globalt definerede liste forrang.

Du kan deaktivere denne indstilling for at sikre, at kun globalt definerede lister (f.eks. dem fra eventuelle installerede GPOs) bruges.

### <a name="use-group-policy-to-disable-local-list-merging"></a>Brug Gruppepolitik til at deaktivere lokal listefletning

1. På Gruppepolitik administrationscomputer skal du åbne Gruppepolitik [Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. I menuen **Gruppepolitik skal du** gå til **Computerkonfiguration og** klikke på **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter > Microsoft Defender Antivirus**.

4. Dobbeltklik på Konfigurer **den lokale administratorfletningsfunktionsmåde for lister,** og angiv indstillingen til **Deaktiveret**. Klik på **OK**.

> [!NOTE]
> Hvis du deaktiverer lokal listefletning, tilsidesætter den kontrollerede indstillinger for mappeadgang. Den tilsidesætter også alle beskyttede mapper eller tilladte apps, der er angivet af den lokale administrator. Du kan finde flere oplysninger om indstillinger for styret mappeadgang [i Tillad en blokeret app Windows Sikkerhed](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Konfigurere slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md)
