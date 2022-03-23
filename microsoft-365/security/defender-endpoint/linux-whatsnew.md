---
title: Nyheder i Microsoft Defender til slutpunkt på Linux
description: Liste over større ændringer for Microsoft Defender til slutpunkt på Linux.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, whatsnew, release
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 48b278d23cd724cade823d2a6b052b11d02a3a13
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591168"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Nyheder i Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="1016093-30122012160930"></a>101.60.93 (30.122012.16093.0)

- Denne version indeholder en sikkerhedsopdatering til [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1016005-30122012160050"></a>101.60.05 (30.122012.16005.0)

- Ekstra understøttelse af kernel version 2.6.32-754.43.1.el6.x86_64 til RHEL 6.10
- Fejlrettelser

## <a name="1015880-30122012158800"></a>101.58.80 (30.122012.15880.0)

- Kommandolinjeværktøjet understøtter nu gendannelse af filer, der er sat i karantæne, på en anden placering end den, hvor filen oprindeligt blev fundet. Det kan du gøre via `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Fejlrettelser

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- Rettede et produktnedbrud, der blev introduceret i 101.53.02, og som har påvirket flere kunder

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Vi har tilføjet en funktion til at registrere følsomme log4j-jars, der bruges af Java-programmer. Maskinen undersøges med jævne mellemrum for at køre Java-processer med indlæste log4j-jars. Oplysningerne rapporteres til backend'en Microsoft Defender for Endpoint og blotlægges i området til administration af sikkerhedsrisikoen på portalen.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- Der er blevet tilføjet en ny parameter til kommandolinjeværktøjet til at styre, om arkiver scannes under scanninger efter behov. Dette kan konfigureres via `mdatp config scan-archives --value [enabled/disabled]`. Som standard er denne indstillet til `enabled`.
- Fejlrettelser

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- Fra og med denne version giver vi microsoft Defender for Endpoint-understøttelse til følgende distributionspunkter: 
  - RHEL6.7-6.10- og CentOS6.7-6.10-versioner.
  - Amazon Linux 2
  - 33 eller nyere
- Fejlrettelser


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Nye parametre er føjet til kommandolinjeværktøjet:
  - Kontrollere graden af parallelitet for scanninger efter behov. Dette kan konfigureres via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Som standard anvendes der en grad af `2` parallelitet.
  - Kontroller, om scanninger efter sikkerhedsintelligensopdateringer aktiveres eller deaktiveres. Dette kan konfigureres via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Som standard er denne indstillet til `enabled`.
- Ændring af produktlogniveauet kræver nu udvidelse
- Fejlrettelser

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- Fra og med denne version afhjælpes de trusler, der registreres under antivirusscanninger efter behov, som udløses via kommandolinjeklienten, automatisk. Trusler, der registreres under scanninger, der udløses via brugergrænsefladen, kræver stadig manuel handling.
- `mdatp diagnostic real-time-protection-statistics` understøtter nu yderligere to parametre:
  - `--sort`: sorterer outputtet faldende efter det samlede antal scannede filer
  - `--top N`: viser de øverste N resultater (fungerer kun, hvis `--sort` det også er angivet)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Microsoft Defender til Slutpunkt på Linux er nu tilgængelig i prøveversion for kunder i det amerikanske offentlige. Du kan finde flere oplysninger [under Microsoft Defender til slutpunkt for kunder i det amerikanske offentlige.](gov.md)
- Rettede et problem, hvor brugen af Microsoft Defender til slutpunkt på Linux på systemer med OFREY-filsystemer fik OS til at hænge
- Forbedring af ydeevnen & andre fejlrettelser

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Forbedring af ydeevnen i den situation, hvor et helt inderpunkt føjes til listen over undtagelser til antivirus. Før denne version blev filaktivitet, der stammer fra mount pointet, stadig behandlet af produktet. Fra og med denne version er filaktivitet for ekskluderede bjergpunkter undertrykket, hvilket fører til bedre produktydeevne
- Der er blevet føjet en ny indstilling til kommandolinjeværktøjet for at få vist oplysninger om den seneste scanning efter behov. Hvis du vil have vist oplysninger om den seneste scanning efter behov, skal du køre `mdatp health --details antivirus`
- Andre forbedringer af ydeevnen & fejlrettelser

## <a name="1011853"></a>101.18.53

- Slutpunktsregistrering og -svar til Linux er nu [generelt tilgængelig](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Vi har tilføjet en ny kommandolinjekontakt (`--ignore-exclusions`) for at ignorere udeladelse af AV under brugerdefinerede scanninger (`mdatp scan custom`)
- Udvidet `mdatp diagnostic create` med en ny parameter (`--path [directory]`), der gør det muligt at gemme diagnosticeringslogfilerne i en anden mappe
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011299"></a>101.12.99

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010476"></a>101.04.76

- Fejlrettelser

## <a name="1010348"></a>101.03.48

- Fejlrettelser

## <a name="1010255"></a>101.02.55

- Vi har rettet et problem, hvor produktet nogle gange ikke begynder at følge en genstart/opgradering
- Vi har rettet et problem, hvor proxyindstillingerne ikke er permanente på tværs af produktopgraderingerne

## <a name="1010075"></a>101.00.75

- Understøttelse af følgende filtyper er blevet tilføjet: `ecryptfs`, `fuse`, `fuseblk`, `jfs`, `nfs`, `overlay`, `ramfs`, , `reiserfs`, og `udf``vfat`
- Ny syntaks [for kommandolinjeværktøjet](linux-resources.md#configure-from-the-command-line).
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Når du opgraderer den installerede pakke fra en produktversion, der er ældre end 100.90.70, mislykkes opdateringen muligvis på Red Hat-baserede og SLES-fordelinger. Dette skyldes en større ændring i en filsti. En midlertidig løsning er at fjerne den ældre pakke og derefter installere den nye. Dette problem findes ikke i nyere versioner.

- [Antivirusudetagelser understøtter nu jokertegn](linux-exclusions.md#supported-exclusion-types)
- Vi har tilføjet muligheden [for at foretage fejlfinding af](linux-support-perf.md) problemer `mdatp` med ydeevnen via kommandolinjeværktøjet
- Forbedringer, der gør pakkeinstallationen mere robust
- Forbedringer af ydeevnen & fejlrettelser
