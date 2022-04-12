---
title: Planlæg regelmæssige hurtige og komplette scanninger med Microsoft Defender Antivirus
description: Konfigurer tilbagevendende (planlagte) scanninger, herunder hvornår de skal køre, og om de kører som komplette eller hurtige scanninger
keywords: hurtig scanning, fuld scanning, hurtig vs. fuld, planlæg scanning, dagligt, ugentligt, klokkeslæt, planlagt, tilbagevendende, regelmæssigt
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
ms.openlocfilehash: e7b854b2a4c9f4202296ed404d067182de8627bd
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790257"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Konfigurer planlagte hurtig- eller komplette Microsoft Defender Antivirus scanninger

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Ud over altid at være tændt, beskyttelse i realtid og [on-demand-antivirusscanninger](run-scan-microsoft-defender-antivirus.md) kan du konfigurere regelmæssige, planlagte antivirusscanninger. Du kan konfigurere scanningstypen, hvornår scanningen skal finde sted, og om scanningen skal finde sted efter en [opdatering af beskyttelse](manage-protection-updates-microsoft-defender-antivirus.md) , eller når der ikke bruges et slutpunkt. Du kan også konfigurere særlige scanninger for at fuldføre afhjælpningshandlinger, hvis det er nødvendigt.

## <a name="what-do-you-want-to-do"></a>Hvad vil du foretage dig?

- [Få mere at vide om hurtige scanninger, komplette scanninger og brugerdefinerede scanninger](#quick-scan-full-scan-and-custom-scan)
- [Brug Gruppepolitik til at planlægge antivirusscanninger](schedule-antivirus-scans-group-policy.md)
- [Brug Windows PowerShell til at planlægge antivirusscanninger](schedule-antivirus-scans-powershell.md)
- [Brug Windows Management Instrumentation til at planlægge antivirusscanninger](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Vær opmærksom på følgende punkter

- Som standard søger Microsoft Defender Antivirus efter en opdatering 15 minutter før tidspunktet for planlagte scanninger. Du kan [administrere tidsplanen for, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md) til at tilsidesætte denne standard.

- Hvis en enhed er frakoblet og kører på batteri under en planlagt fuld scanning, stopper den planlagte scanning med hændelsen 1002, hvor det angives, at scanningen stoppede før fuldførelsen. Microsoft Defender Antivirus kører en fuld scanning på det næste planlagte tidspunkt.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Hurtig scanning, fuld scanning og brugerdefineret scanning

Når du konfigurerer planlagte scanninger, kan du angive, om scanningen skal være en fuld eller hurtig scanning. I de fleste tilfælde anbefales en hurtig scanning.

<br/><br/>

|Hurtig scanning|Fuld scanning|Brugerdefineret scanning|
|---|---|---|
|(Anbefalet) En hurtig scanning ser på alle de steder, hvor der kan være malware registreret til at starte med systemet, såsom registreringsdatabasenøgler og kendte Windows startmapper. <br/><br/>Kombineret med altid aktiveret beskyttelse i realtid, som gennemgår filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe, hjælper en hurtig scanning med at yde stærk beskyttelse mod malware, der starter med systemet og malware på kerneniveau.<br/><br/>I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede mulighed for planlagte scanninger.|En fuld scanning starter ved at køre en hurtig scanning og fortsætter derefter med en sekventiel filscanning af alle tilsluttede faste diske og flytbare/netværksdrev (hvis den fulde scanning er konfigureret til at gøre det).<br/><br/>Det kan tage et par timer eller dage at udføre en fuld scanning, afhængigt af mængden og typen af data, der skal scannes.<br/><br/>Når den fulde scanning er fuldført, er der ny sikkerhedsintelligens tilgængelig, og der kræves derefter en ny scanning for at sikre, at der ikke registreres andre trusler med den nye sikkerhedsintelligens.<br/><br/>På grund af den tid og de ressourcer, der er involveret i en fuld scanning, anbefaler Microsoft generelt ikke, at der planlægges komplette scanninger.|En brugerdefineret scanning kører på filer og mapper, du angiver. Du kan f.eks. vælge at scanne et USB-drev eller en bestemt mappe på enhedens lokale drev.|

> [!NOTE]
> Hurtigsøgninger kører som standard på tilsluttede flytbare enheder, f.eks. USB-drev.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Hvordan gør jeg vide, hvilken scanningstype der skal vælges?

Brug følgende tabel til at vælge en scanningstype.
<br/><br/>

|Scenario|Anbefalet scanningstype|
|---|---|
|Du vil konfigurere almindelige, planlagte scanninger|Hurtig scanning <p> En hurtig scanning kontrollerer processerne, hukommelsen, profilerne og visse placeringer på enheden. Kombineret med [konstant beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) hjælper en hurtig scanning med at levere stærk dækning både for malware, der starter med systemet og malware på kerneniveau. Beskyttelse i realtid gennemser filer, når de åbnes og lukkes, og når en bruger navigerer til en mappe.|
|Trusler, f.eks. malware, registreres på en individuel enhed|Hurtig scanning <p> I de fleste tilfælde vil en hurtig scanning indhente og rydde op i registreret malware.|
|Du vil køre en [on-demand-scanning](run-scan-microsoft-defender-antivirus.md)|Hurtig scanning|
|Du vil sikre dig, at en bærbar enhed, f.eks. et USB-drev, ikke indeholder malware|Brugerdefineret scanning <p> Med en brugerdefineret scanning kan du vælge bestemte placeringer, mapper eller filer og køre en hurtig scanning.|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Hvad har jeg ellers brug for at vide om hurtige og komplette scanninger?

- Skadelige filer kan gemmes på placeringer, der ikke er inkluderet i en hurtig scanning. Men altid aktiveret beskyttelse i realtid gennemgår alle filer, der åbnes og lukkes, og alle filer, der findes i mapper, som en bruger har adgang til. Kombinationen af beskyttelse i realtid og en hurtig scanning hjælper med at yde stærk beskyttelse mod malware.

- Beskyttelse med on-access med [skybaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md) hjælper med at sikre, at alle de filer, der er adgang til på systemet, scannes med de nyeste modeller til sikkerhedsintelligens og maskinel indlæring i cloudmiljøet.

- Når realtidsbeskyttelse registrerer malware, og omfanget af de berørte filer ikke bestemmes i første omgang, starter Microsoft Defender Antivirus en fuld scanning som en del af afhjælpningsprocessen.

- En fuld scanning kan registrere skadelige filer, der ikke blev registreret af andre scanninger, f.eks. en hurtig scanning. En fuld scanning kan dog tage et stykke tid og bruge værdifulde systemressourcer til at fuldføre.

- Hvis en enhed er offline i en længere periode, kan det tage længere tid at fuldføre en fuld scanning.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)