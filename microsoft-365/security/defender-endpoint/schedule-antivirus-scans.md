---
title: Planlæg almindelige hurtige og fulde scanninger med Microsoft Defender Antivirus
description: Konfigurer tilbagevendende (planlagte) scanninger, herunder hvornår de skal køre, og om de kører som fulde scanninger eller hurtige scanninger
keywords: hurtig scanning, fuld scanning, hurtig vs fuld, planlæg scanning, dagligt, ugentligt, klokkeslæt, planlagt, tilbagevendende, almindelig
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 02/22/2022
ms.reviewer: pauhijbr, ksarens, mkaminska
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 96827430b8d2fe1b45b9839ffe87eb5aa5571b93
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597967"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Konfigurere planlagte hurtige eller komplette Microsoft Defender Antivirus scanninger

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Ud over altid-on, beskyttelse i realtid og [on-demand antivirus](run-scan-microsoft-defender-antivirus.md) scanninger, kan du konfigurere regelmæssige, planlagte antivirusscanninger. Du kan konfigurere typen af scanning, hvornår scanningen skal udføres, og om scanningen skal udføres efter en sikkerhedsopdatering, eller når et slutpunkt ikke bruges.[](manage-protection-updates-microsoft-defender-antivirus.md) Du kan også konfigurere særlige scanninger for at fuldføre afhjælpningshandlinger, hvis det er nødvendigt.

## <a name="what-do-you-want-to-do"></a>Hvad vil du gøre?

- [Få mere at vide om hurtige scanninger, fulde scanninger og brugerdefinerede scanninger](#quick-scan-full-scan-and-custom-scan)
- [Brug Gruppepolitik til at planlægge antivirusscanninger](schedule-antivirus-scans-group-policy.md)
- [Brug Windows PowerShell til at planlægge antivirusscanninger](schedule-antivirus-scans-powershell.md)
- [Brug Windows Management Instrumentation til at planlægge antivirusscanninger](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Husk følgende punkter

- Som standard søger Microsoft Defender Antivirus, om der er en opdatering 15 minutter før tidspunktet for planlagte scanninger. Du kan [Administrere tidsplanen for, hvornår sikkerhedsopdateringer skal downloades og anvendes for](manage-protection-update-schedule-microsoft-defender-antivirus.md) at tilsidesætte denne standard.

- Hvis stikket til en enhed er frakoblet og kører på batteri under en planlagt fuld scanning, stopper den planlagte scanning med hændelse 1002, hvilket betyder, at scanningen stoppede før fuldførelsen. Microsoft Defender Antivirus kører en fuld scanning på det næste planlagte tidspunkt.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Hurtig scanning, fuld scanning og brugerdefineret scanning

Når du konfigurerer planlagte scanninger, kan du angive, om scanningen skal være en fuld eller hurtig scanning. I de fleste tilfælde anbefales en hurtig scanning.

<br/><br/>

|Hurtig scanning|Fuld scanning|Brugerdefineret scanning|
|---|---|---|
|(Anbefalet) En hurtig scanning kigger på alle de placeringer, hvor der kan være registreret malware for at starte med systemet, f.eks registreringsdatabasenøgler og kendte Windows startmapper. <br/><br/>Kombineret med altid tændt beskyttelse i realtid, som gennemser filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe, hjælper en hurtig scanning med at yde stærk beskyttelse mod malware, der starter med systemet og malware på kerneniveau.<br/><br/>I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede indstilling for planlagte scanninger.|En fuld scanning starter ved at køre en hurtig scanning og fortsætter derefter med en sekventiel filscanning af allemonterede faste diske og flytbare/netværksdrev (hvis den fulde scanning er konfigureret til at gøre dette).<br/><br/>Det kan tage et par timer eller dage at gennemføre en komplet scanning, afhængigt af mængden og typen af data, der skal scannes.<br/><br/>Når den fulde scanning er fuldført, er ny sikkerhedsintelligens tilgængelig, og der kræves en ny scanning for at sikre, at der ikke registreres andre trusler med den nye sikkerhedsintelligens.<br/><br/>På grund af den tid og de ressourcer, der er involveret i en komplet scanning, anbefaler Microsoft generelt ikke, at der planlægges fulde scanninger.|En brugerdefineret scanning kører på filer og mapper, som du angiver. Du kan f.eks. vælge at scanne et USB-drev eller en bestemt mappe på enhedens lokale drev.|

> [!NOTE]
> Som standard kører hurtige scanninger påmonterede flytbare enheder, f.eks. USB-drev.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Hvordan ved jeg, hvilken scanningstype jeg skal vælge?

Brug følgende tabel til at vælge en scanningstype.
<br/><br/>

|Scenarie|Anbefalet scanningstype|
|---|---|
|Du vil konfigurere almindelige, planlagte scanninger|Hurtig scanning <p> En hurtig scanning kontrollerer processer, hukommelse, profiler og visse placeringer på enheden. I kombination [med beskyttelse i](configure-real-time-protection-microsoft-defender-antivirus.md) realtid, hjælper en hurtig scanning med at sikre en stærk dækning af malware, der starter med systemet, og malware på kerneniveau. Beskyttelse i realtid gennemser filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe.|
|Der registreres trusler, f.eks. malware, på en enkelt enhed|Hurtig scanning <p> I de fleste tilfælde vil en hurtig scanning opfange og rydde op i registreret malware.|
|Du vil køre en [on-demand-scanning](run-scan-microsoft-defender-antivirus.md)|Hurtig scanning|
|Du vil sikre dig, at en bærbar enhed, f.eks. et USB-drev, ikke indeholder malware|Brugerdefineret scanning <p> En brugerdefineret scanning gør det muligt at vælge bestemte placeringer, mapper eller filer og køre en hurtig scanning.|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Hvad mere har jeg brug for at vide om hurtige og komplette scanninger?

- Ondsindede filer kan gemmes på placeringer, der ikke er inkluderet i en hurtig scanning. Beskyttelse af altid i realtid gennemser dog alle filer, der åbnes og lukkes, og alle filer, der findes i mapper, der tilgås af en bruger. Kombinationen af beskyttelse i realtid og en hurtig scanning hjælper med at yde stærk beskyttelse mod malware.

- Beskyttelse ved adgang med skybaseret beskyttelse hjælper med at sikre, at alle de filer, der åbnes på systemet, scannes med den nyeste sikkerhedsintelligens og modeller, der lærer at lære om skyen.[](cloud-protection-microsoft-defender-antivirus.md)

- Når beskyttelse i realtid registrerer malware, og omfanget af de påvirkede filer ikke bestemmes i første omgang, starter Microsoft Defender Antivirus en fuld scanning som en del af afhjælpningsprocessen.

- En komplet scanning kan registrere skadelige filer, der ikke blev registreret af andre scanninger, f.eks. en hurtig scanning. Men en komplet scanning kan tage et stykke tid og bruge værdifulde systemressourcer at fuldføre.

- Hvis en enhed er offline i en længere periode, kan det tage længere tid at udføre en fuld scanning.
