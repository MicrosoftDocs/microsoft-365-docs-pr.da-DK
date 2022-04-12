---
title: Planlæg antivirusscanninger ved hjælp af Gruppepolitik
description: Brug Gruppepolitik til at konfigurere antivirusscanninger
keywords: hurtig scanning, fuld scanning, tidsplan, gruppepolitik, antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/10/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: dbd3f2b4342757509a6440ff87a112b75b663f22
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788034"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planlæg antivirusscanninger ved hjælp af Gruppepolitik

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

I denne artikel beskrives det, hvordan du konfigurerer planlagte scanninger ved hjælp af Gruppepolitik. Hvis du vil vide mere om planlægning af scanninger og scanningstyper, skal du se [Konfigurer planlagte hurtig- eller komplette Microsoft Defender Antivirus scanninger](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Konfigurer antivirusscanninger ved hjælp af Gruppepolitik

1. Gå til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Komponenter** \>  \> Microsoft Defender Antivirus **Scanning** i Gruppepolitik Editor på din Gruppepolitik-administrationscomputer.

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. Angiv indstillinger for det Gruppepolitik objekt, og vælg derefter **OK**. 

4. Gentag trin 1-4 for hver indstilling, du vil konfigurere.

5. Udrul dit Gruppepolitik Objekt, som du normalt gør. Hvis du har brug for hjælp til Gruppepolitik Objekter, skal du se [Opret et Gruppepolitik objekt](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Når du konfigurerer planlagte scanninger, kan indstillingen **Start kun den planlagte scanning, når computeren er tændt, men ikke i brug**, som er aktiveret som standard, påvirke det forventede planlagte tidspunkt ved at kræve, at computeren er inaktiv først.
>
> Ved ugentlige scanninger er standardfunktionsmåden på Windows Server at scanne uden for automatisk vedligeholdelse, når computeren er inaktiv. Standarden på Windows 10 og nyere er at scanne under automatisk vedligeholdelse, når computeren er inaktiv. Hvis du vil ændre denne funktionsmåde, skal du ændre indstillingerne ved at deaktivere **ScanOnlyIfIdle** og derefter definere en tidsplan.

Du kan finde flere oplysninger i emnet [Administrer, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md) , og [Forbyd eller tillad brugere at ændre politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md) .

## <a name="group-policy-settings-for-scheduling-scans"></a>Gruppepolitik indstillinger for planlægning af scanninger

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Skan | Angiv den scanningstype, der skal bruges til en planlagt scanning | Hurtig scanning |
| Skan | Angiv den ugedag, hvor en planlagt scanning skal køres | Angiv den dag (eller aldrig), hvor en scanning skal køres. | Aldrig |
| Skan | Angiv det tidspunkt på dagen, hvor en planlagt scanning skal køres | Angiv antallet af minutter efter midnat (skriv f.eks. **60** for 1 om natten). | Kl. 02.00 |
| Rod | Randomiser planlagte opgavetider |I Microsoft Defender Antivirus skal du randomisere starttidspunktet for scanningen til et interval mellem 0 og 23 timer. <p>I [SCEP](/mem/intune/protect/certificates-scep-configure) skal du randomisere scanninger til et vilkårligt interval plus eller minus 30 minutter. Dette kan være nyttigt i virtuelle maskiner eller VDI-installationer. | Aktiveret |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>Gruppepolitik indstillinger for planlægning af scanninger, når et slutpunkt ikke er i brug

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Skan | Start kun den planlagte scanning, når computeren er tændt, men ikke i brug | Planlagte scanninger kan ikke køre, medmindre computeren er tændt, men ikke i brug | Aktiveret |

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, overholder scanningerne ikke CPU-begrænsningskonfigurationen og drager fuld fordel af de ressourcer, der er tilgængelige til at fuldføre scanningen så hurtigt som muligt.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>Gruppepolitik indstillinger for planlægning af de scanninger, der kræves til afhjælpning

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|---|---|---|---|
| Oprydning | Angiv den ugedag, hvor der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen | Angiv den dag (eller aldrig), hvor en scanning skal køres. | Aldrig |
| Oprydning | Angiv det tidspunkt på dagen, hvor der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen | Angiv antallet af minutter efter midnat (angiv f.eks. **60** for 1 om natten) | Kl. 02.00 |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>Gruppepolitik indstillinger for planlægning af daglige scanninger

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Skan | Angiv intervallet for hurtig scanning pr. dag | Angiv, hvor mange timer der skal gå, før den næste hurtige scanning. Hvis du f.eks. vil køre hver anden time, skal du angive **2**, for en gang om dagen **, angive 24**. Angiv **0** for aldrig at køre en daglig hurtigscanning. | Aldrig |
| Skan | Angiv tidspunktet for en daglig hurtigsøgning | Angiv antallet af minutter efter midnat (angiv f.eks. **60** for 1 om natten) | Kl. 02.00 |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>Gruppepolitik indstillinger for planlægning af scanninger efter beskyttelsesopdateringer

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret)|
|:---|:---|:---|:---|
| Signaturopdateringer | Slå scanning til efter sikkerhedsintelligensopdatering | Der foretages en scanning, umiddelbart efter at en ny beskyttelsesopdatering er downloadet | Aktiveret |

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)