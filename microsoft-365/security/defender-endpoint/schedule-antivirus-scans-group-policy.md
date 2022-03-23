---
title: Planlæg antivirusscanninger med Gruppepolitik
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
ms.openlocfilehash: 0e5e22b1c3f73f39ad65df39fd25e9b7b6e8a913
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592241"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planlæg antivirusscanninger med Gruppepolitik

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Denne artikel beskriver, hvordan du konfigurerer planlagte scanninger ved hjælp Gruppepolitik. Hvis du vil have mere at vide om planlægning af scanninger og om scanningstyper, skal du se Konfigurer Microsoft Defender Antivirus [scanninger](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Konfigurere antivirusscanninger ved hjælp af Gruppepolitik

1. På din Gruppepolitik administrationsmaskine skal du i Gruppepolitik Editor gå til **Administrative** \>  \> skabeloner til **computerkonfiguration Windows Komponenter** \> **Microsoft Defender Antivirus** \> **Scanning**.

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. Angiv indstillinger for Gruppepolitik objekt, og vælg derefter **OK**. 

4. Gentag trin 1-4 for hver indstilling, du vil konfigurere.

5. Installér dit Gruppepolitik-objekt, som du normalt gør det. Hvis du har brug for hjælp Gruppepolitik objekter, skal du [se Oprette Gruppepolitik objekt](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Når du konfigurerer planlagte scanninger, kan indstillingen Start kun den planlagte scanning, når **computeren** er tændt, men ikke er i brug, som er aktiveret som standard, påvirke den forventede planlagte tid ved at kræve, at computeren er inaktiv først.
>
> Ved ugentlige scanninger er standardfunktionsmåden på serveren Windows at scanne uden for automatisk vedligeholdelse, når maskinen er inaktiv. Standardindstillingen på Windows 10 og nyere er at scanne under automatisk vedligeholdelse, når maskinen er inaktiv. Hvis du vil ændre denne funktionsmåde, skal du ændre indstillingerne ved at **deaktivere ScanOnlyIfIdle** og derefter definere en tidsplan.

Du kan finde flere oplysninger i [Administrer, hvornår](manage-protection-update-schedule-microsoft-defender-antivirus.md) sikkerhedsopdateringer skal downloades og anvendes og Forebyd eller tillad brugere [at ændre emner for politikindstillinger](configure-local-policy-overrides-microsoft-defender-antivirus.md) lokalt.

## <a name="group-policy-settings-for-scheduling-scans"></a>Gruppepolitik indstillinger for planlægning af scanninger

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Scan | Angiv den scanningstype, der skal bruges til en planlagt scanning | Hurtig scanning |
| Scan | Angiv ugedagen for at køre en planlagt scanning | Angiv dagen (eller aldrig) for at køre en scanning. | Aldrig |
| Scan | Angiv det klokkeslæt på dagen, der skal køres en planlagt scanning | Angiv antallet af minutter efter midnat (skriv f.eks. **60** for 1:00). | 02:00 |
| Rod | Randomisere planlagte opgavetider |In Microsoft Defender Antivirus, randomize the start time of the scan to any interval from 0 to 23 hours. <p>I [SCEP](/mem/intune/protect/certificates-scep-configure) skal du randomisere scanninger til et interval plus eller minus 30 minutter. Dette kan være nyttigt i virtuelle maskiner eller VDI-installationer. | Aktiveret |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>Gruppepolitik til planlægning af scanninger til, når et slutpunkt ikke er i brug

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Scan | Starte den planlagte scanning, når computeren er tændt, men ikke i brug | Planlagte scanninger kan ikke køres, medmindre computeren er tændt, men ikke i brug | Aktiveret |

> [!NOTE]
> Når du planlægger scanninger for tidspunkter, hvor slutpunkter ikke er i brug, imødekommer scanninger ikke CPU-begrænsningskonfigurationen og udnytter de tilgængelige ressourcer til at fuldføre scanningen så hurtigt som muligt.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>Gruppepolitik indstillinger for scanninger, der er påkrævet til planlægning af afhjælpning

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|---|---|---|---|
| Afhjælpning | Angiv ugedagen for at køre en planlagt fuld scanning for at fuldføre afhjælpningen | Angiv dagen (eller aldrig) for at køre en scanning. | Aldrig |
| Afhjælpning | Angiv tidspunktet på dagen, der skal køres en planlagt fuld scanning for at fuldføre afhjælpningen | Angiv antallet af minutter efter midnat (skriv f.eks. **60** for 1:00). | 02:00 |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>Gruppepolitik indstillinger for planlægning af daglige scanninger

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret) |
|:---|:---|:---|:---|
| Scan | Angiv det interval, der skal køre hurtige scanninger pr. dag | Angiv, hvor mange timer der skal gå, før den næste hurtige scanning. Hvis du f.eks. vil køre hver to timer, skal du **angive 2**, angive **24** for én gang om dagen. Enter **0** for aldrig at køre en daglig hurtig scanning. | Aldrig |
| Scan | Angiv tidspunktet for en daglig hurtig scanning | Angiv antallet af minutter efter midnat (skriv f.eks. **60** for 1:00). | 02:00 |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>Gruppepolitik til planlægning af scanninger efter opdateringer til beskyttelse

| Placering | Indstilling | Beskrivelse | Standardindstilling (hvis den ikke er konfigureret)|
|:---|:---|:---|:---|
| Signaturopdateringer | Aktiver scanning efter Sikkerhedsintelligens-opdatering | En scanning udføres umiddelbart efter, at der er downloadet en ny sikkerhedsopdatering | Aktiveret |

