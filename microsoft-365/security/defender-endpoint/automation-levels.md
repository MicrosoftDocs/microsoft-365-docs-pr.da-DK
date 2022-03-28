---
title: Automatiseringsniveauer i automatiseret undersøgelse og afhjælpning
description: Få et overblik over automatiseringsniveauer, og hvordan de fungerer i Microsoft Defender til Slutpunkt
keywords: automatiseret, undersøgelse, niveau, Microsoft Defender til Slutpunkt
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 10/22/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: e440675a46a4340e2f659b23a31b19dbab33d2c0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597503"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Automatiseringsniveauer i automatiseret undersøgelse og afhjælpningsfunktioner

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Automatiserede undersøgelses- og afhjælpningsfunktioner (AIR) i Microsoft Defender til Slutpunkt kan konfigureres til en af flere niveauer med automatisering. Dit automatiseringsniveau påvirker, om afhjælpningshandlinger, der følger efter AIR-undersøgelser, skal løses automatisk eller kun efter godkendelse.

- *Fuld automatisering* (anbefales) betyder, at afhjælpningshandlinger automatisk tages på artefakter, der vurderes at være skadelige.
- *Halv-automatisering betyder* , at nogle afhjælpningshandlinger bliver taget automatisk, men andre afhjælpningshandlinger afventer godkendelse, før de kan tages. (Se tabellen i [Niveauer af automatisering](#levels-of-automation)).
- Alle afhjælpningshandlinger, uanset om de er ventende eller fuldførte, registreres i Handlingscenter ([https://security.microsoft.com](https://security.microsoft.com)).

> [!TIP]
> For at opnå de bedste resultater anbefaler vi, at du bruger fuld automatisering, når [du konfigurerer AIR](configure-automated-investigations-remediation.md). Data, der er indsamlet og analyseret i løbet af det sidste år, viser, at kunder, der bruger fuld automatisering, har fjernet 40 % flere malwareeksempler med høj tillid end kunder, der bruger lavere automatiseringsniveauer. En fuld automatisering kan hjælpe dig med at frigøre dine sikkerhedsressourcer til at fokusere mere på dine strategiske initiativer.

## <a name="levels-of-automation"></a>Niveauer af automatisering

I følgende tabel beskrives hvert niveau af automatisering, og hvordan det fungerer.

<br>

****

|Automatiseringsniveau|Beskrivelse|
|---|---|
|**Fuld – afhjulpet trusler automatisk** <br> (også kaldet *fuld automatisering*)|Når du har fuld automatisering, udføres afhjælpningshandlinger automatisk. Alle afhjælpningshandlinger, der er taget, kan vises [i Handlingscenter](auto-investigation-action-center.md) på **fanen Oversigt** . Hvis det er nødvendigt, kan en afhjælpningshandling fortrydes. <p> **_Fuld automatisering anbefales_* og vælges som standard for lejere, der blev oprettet d. 16. august 2020 med Microsoft Defender til Slutpunkt, uden nogen enhedsgrupper er defineret endnu.*|
|**Semi – kræver godkendelse for enhver afhjælpning** <br> (også kaldet *semi-automatisering*)|Med dette niveau af semi-automatisering kræves godkendelse for *enhver* afhjælpningshandling. Disse afventende handlinger kan ses og godkendes i [Handlingscenter](auto-investigation-action-center.md) under **fanen Afventer** . <p> *Dette niveau af semi-automatisering vælges som standard for lejere, der blev oprettet før den 16. august 2020 med Microsoft Defender til slutpunkt uden definerede enhedsgrupper.*|
|**Semi – kræver godkendelse til afhjælpning af centrale mapper** <br> (også en type *semi-automatisering*)|Med dette niveau af semi-automatisering kræves godkendelse for enhver afhjælpningshandlinger, der er nødvendige for filer eller eksekverbare filer, der findes i kernemapper. Kernemapper inkluderer mapper i operativsystemet, f.eks **. Windows** (`\windows\*`). <p> Afhjælpningshandlinger kan udføres automatisk på filer eller eksekverbare filer, der findes i andre (ikke-kerne) mapper. <p> Ventende handlinger for filer eller eksekverbare filer i kernemapper kan vises og godkendes i [Handlingscenter](auto-investigation-action-center.md) på **fanen Afventer** . <p> Handlinger, der er udført på filer eller eksekverbare filer i andre mapper, kan vises i [Handlingscenter](auto-investigation-action-center.md) på **fanen Oversigt** .|
|**Semi – kræver godkendelse til ikke-midlertidige mapper afhjælpning** <br> (også en type *semi-automatisering*)|Med dette niveau af semi-automatisering er godkendelse påkrævet for eventuelle afhjælpningshandlinger, der er nødvendige for filer eller eksekverbare filer, *der ikke er* i midlertidige mapper. <p> Midlertidige mapper kan indeholde følgende eksempler: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Afhjælpningshandlinger kan udføres automatisk på filer eller eksekverbare filer, der findes i midlertidige mapper. <p> Ventende handlinger for filer eller eksekverbare filer, der ikke er i midlertidige [mapper, kan](auto-investigation-action-center.md) vises og godkendes i Handlingscenter på **fanen Afventer** . <p> Handlinger, der er udført på filer eller eksekverbare filer i midlertidige [mapper, kan](auto-investigation-action-center.md) vises og godkendes i Handlingscenter på **fanen Oversigt** .|
|**Intet automatiseret svar** <br> (også kaldet *ingen automatisering*)|Uden automatisering kører automatiseret undersøgelse ikke på din organisations enheder. Det betyder, at der ikke bliver taget eller afventer nogen afhjælpningshandlinger som et resultat af automatiseret undersøgelse. Andre funktioner til trusselsbeskyttelse, f.eks. beskyttelse fra potentielt uønskede [programmer, kan](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) dog være gældende, afhængigt af hvordan dit antivirusprogram og næste generations beskyttelsesfunktioner er konfigureret. <p> ***Det anbefales *ikke at* bruge nogen automatiseringsindstilling**, da det reducerer sikkerheden for din organisations enheder. [Overvej at indstille dit automatiseringsniveau til fuld automatisering (eller mindst halv-automatisering).](/microsoft-365/security/defender-endpoint/machine-groups)|
|

## <a name="important-points-about-automation-levels"></a>Vigtige punkter om automatiseringsniveauer

- Fuld automatisering har vist sig at være pålidelig, effektiv og sikker og anbefales til alle kunder. Fuld automatisering frigøres dine vigtige sikkerhedsressourcer, så de kan fokusere mere på dine strategiske initiativer.

- Nye lejere (som omfatter lejere, der blev oprettet d. 16. august 2020) med Microsoft Defender til Slutpunkt er indstillet til fuld automatisering som standard.

- Hvis sikkerhedsteamet har defineret enhedsgrupper med et automatiseringsniveau, ændres disse indstillinger ikke ved udrulning af de nye standardindstillinger.

- Du kan beholde standardindstillingerne for automatisering, eller du kan ændre dem i overensstemmelse med virksomhedens behov. Hvis du vil ændre dine indstillinger, [skal du angive dit automatiseringsniveau](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Næste trin

- [Konfigurer automatiseret undersøgelse og afhjælpningsfunktioner i Microsoft Defender til Slutpunkt](configure-automated-investigations-remediation.md)
- [Gå til handlingscenter](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
