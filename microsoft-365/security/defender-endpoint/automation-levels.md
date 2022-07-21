---
title: Automatiseringsniveauer i automatiseret undersøgelse og afhjælpning
description: Få et overblik over automatiseringsniveauer, og hvordan de fungerer i Microsoft Defender for Endpoint
keywords: automatiseret, undersøgelse, niveau, Microsoft Defender for Endpoint
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
ms.date: 07/20/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: fb7c4ee03c5391b12beb3d716b7817a880878af5
ms.sourcegitcommit: 979343980f05ceb546ca0df23562504aaca34b88
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66912570"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Automatiseringsniveauer i automatiserede undersøgelses- og afhjælpningsfunktioner

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

Air-funktioner (automatiseret undersøgelse og afhjælpning) i Microsoft Defender til virksomheder er forudkonfigureret og kan ikke konfigureres. I Microsoft Defender for Endpoint kan du konfigurere AIR til et af flere automatiseringsniveauer. Dit automatiseringsniveau påvirker, om afhjælpningshandlinger efter AIR-undersøgelser udføres automatisk eller kun efter godkendelse.

- *Fuld automatisering* (anbefales) betyder, at afhjælpningshandlinger automatisk udføres på artefakter, der er fastslået til at være skadelige. Fuld *automatisering er som standard angivet i Defender for Business*.
- *Semiautomatisering* betyder, at nogle afhjælpningshandlinger udføres automatisk, men andre afhjælpningshandlinger venter på godkendelse, før de udføres. Se tabellen i [Niveauer af automatisering](#levels-of-automation).
- Alle afhjælpningshandlinger, uanset om de afventer eller er fuldført, spores i Løsningscenter ([https://security.microsoft.com](https://security.microsoft.com)).

> [!TIP]
> For at opnå de bedste resultater anbefaler vi, at du bruger fuld automatisering, når du [konfigurerer AIR](configure-automated-investigations-remediation.md). Data, der er indsamlet og analyseret i løbet af det seneste år, viser, at kunder, der bruger fuld automatisering, havde fjernet 40 % flere malwareeksempler med høj tillid end kunder, der bruger lavere automatiseringsniveauer. Fuld automatisering kan hjælpe med at frigøre dine sikkerhedshandlinger, så du kan fokusere mere på dine strategiske initiativer.

## <a name="levels-of-automation"></a>Automatiseringsniveauer

|Automatiseringsniveau|Beskrivelse|
|---|---|
|**Fuld – afhjælp trusler automatisk** <br> (også kaldet *fuld automatisering*)|Med fuld automatisering udføres afhjælpningshandlinger automatisk på enheder, der anses for at være skadelige. Alle afhjælpningshandlinger, der udføres, kan ses i [Løsningscenter](auto-investigation-action-center.md) under fanen **Oversigt** . Hvis det er nødvendigt, kan en afhjælpningshandling fortrydes. <p> **_Fuld automatisering anbefales_* og vælges som standard for lejere med Defender for Endpoint, der blev oprettet den 16. august 2020 eller senere, uden at der er defineret nogen enhedsgrupper endnu.*<p>*Fuld automatisering er som standard angivet i Defender for Business.*|
|**Semi – kræver godkendelse til enhver afhjælpning** <br> (også kaldet *semiautomatisering*)|Med dette niveau af halvautomatisering kræves der godkendelse til *enhver* afhjælpningshandling. Disse ventende handlinger kan ses og godkendes i [Løsningscenter](auto-investigation-action-center.md) under fanen **Ventende** . <p> *Dette niveau for semiautomatisering er valgt som standard for lejere, der blev oprettet før den 16. august 2020 med Microsoft Defender for Endpoint, uden at der er defineret enhedsgrupper.*|
|**Semi – kræver godkendelse til afhjælpning af kernemapper** <br> (også en type *semiautomatisering*)|Med dette niveau af semiautomatisering kræves der godkendelse til alle afhjælpningshandlinger, der kræves på filer eller eksekverbare filer, der findes i kernemapper. Kernemapper omfatter operativsystemmapper, f.eks **. Windows** (`\windows\*`). <p> Afhjælpningshandlinger kan udføres automatisk på filer eller eksekverbare filer, der findes i andre (ikke-kerne) mapper. <p> Ventende handlinger for filer eller eksekverbare filer i kernemapper kan vises og godkendes i [Løsningscenter](auto-investigation-action-center.md) under fanen **Ventende** . <p> Handlinger, der er udført på filer eller eksekverbare filer i andre mapper, kan ses i [Løsningscenter](auto-investigation-action-center.md) under fanen **Oversigt** .|
|**Semi – kræver godkendelse til afhjælpning af mapper, der ikke er midlertidige** <br> (også en type *semiautomatisering*)|Med dette niveau af semiautomatisering kræves der godkendelse til eventuelle afhjælpningshandlinger, der er nødvendige for filer eller eksekverbare filer, der *ikke* findes i midlertidige mapper. <p> Midlertidige mapper kan indeholde følgende eksempler: <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Afhjælpningshandlinger kan udføres automatisk på filer eller eksekverbare filer, der er i midlertidige mapper. <p> Ventende handlinger for filer eller eksekverbare filer, der ikke findes i midlertidige mapper, kan vises og godkendes i [Løsningscenter](auto-investigation-action-center.md) under fanen **Ventende** . <p> Handlinger, der er udført på filer eller eksekverbare filer i midlertidige mapper, kan vises og godkendes i [Løsningscenter](auto-investigation-action-center.md) under fanen **Oversigt** .|
|**Intet automatiseret svar** <br> (også kaldet *ingen automatisering*)|Uden automatisering kører automatiseret undersøgelse ikke på organisationens enheder. Derfor udføres eller afventer ingen afhjælpningshandlinger som følge af en automatiseret undersøgelse. Andre funktioner til trusselsbeskyttelse, f.eks [. beskyttelse mod potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus), kan dog være i kraft, afhængigt af hvordan dine antivirus- og næste generations beskyttelsesfunktioner er konfigureret. <p> ***Det anbefales  ikke at bruge automatiseringsindstillingen**, da det reducerer sikkerhedsholdning på organisationens enheder. [Overvej at konfigurere dit automatiseringsniveau til fuld automatisering (eller i det mindste semiautomatisering).](/microsoft-365/security/defender-endpoint/machine-groups)|

## <a name="important-points-about-automation-levels"></a>Vigtige punkter om automatiseringsniveauer

- Fuld automatisering har vist sig at være pålidelig, effektiv og sikker og anbefales til alle kunder. Fuld automatisering frigør dine kritiske sikkerhedsressourcer, så de kan fokusere mere på dine strategiske initiativer.

- Nye lejere (som omfatter lejere, der blev oprettet den 16. august 2020 eller senere) med Defender for Endpoint er som standard angivet til fuld automatisering.

- [Defender for Business](../defender-business/compare-mdb-m365-plans.md) bruger som standard fuld automatisering. Defender for Business bruger ikke enhedsgrupper på samme måde som Defender for Business. Fuld automatisering er derfor slået til og anvendt på alle enheder i Defender for Business.

- Hvis dit sikkerhedsteam har defineret enhedsgrupper med et automatiseringsniveau, ændres disse indstillinger ikke af de nye standardindstillinger, der udrulles.

- Du kan beholde dine standardindstillinger for automatisering eller ændre dem i henhold til dine organisatoriske behov. Hvis du vil ændre dine indstillinger, [skal du angive automatiseringsniveauet](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Næste trin

- [Konfigurer automatiserede undersøgelses- og afhjælpningsfunktioner i Defender for Endpoint](configure-automated-investigations-remediation.md)
- [Besøg Løsningscenter](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
