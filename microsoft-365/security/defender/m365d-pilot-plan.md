---
title: Planlægning af dit Microsoft 365 Defender projekt
description: Planlæg dit Microsoft 365 Defender med interessenter for at håndtere forventninger og sikre et vellykket resultat.
keywords: Microsoft 365 Defender pilotprojekt, planlæg Microsoft 365 Defender projekt, evaluer Microsoft 365 Defender i produktion, Microsoft 365 Defender  pilotprojekt, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6a52df8035ce6f84770a2d06c3b8c127e426622e
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63593484"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>Planlægning af dit Microsoft 365 Defender projekt 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

|![Planlægning](../../media/phase-diagrams/1-planning.png)<br/>Planlægning|[![Forbered](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[Forberedelse](prepare-m365d-eval.md) | [![Simulere angreb](../../media/phase-diagrams/3-simluate.png)](m365d-pilot-simulate.md)<br/>[Simulere angreb](m365d-pilot-simulate.md) | [![Luk og opsummer](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[Luk og opsummer](m365d-pilot-close.md)|
|--|--|--|--|
|*Du er her!*| | | |

Du er i øjeblikket i planlægningsfasen.

For at sikre at pilotprojektet lykkes, er det vigtigt at planlægge grundigt med og få godkendelser fra dine interessenter i begyndelsen. Elementer i planlægningen omfatter identificering af omfang, use cases, krav og succeskriterier.

I denne vejledning får du at vide, hvordan du planlægger dit pilotprojekt. 

>[!IMPORTANT]
>Følg pilotinstruktionerne så tæt som muligt for at opnå optimale resultater.


## <a name="scope"></a>Omfang

Pilotens omfang afgør, hvor bred testen skal være, baseret på dit miljø og acceptable testmetoder. Her er nogle eksempler på områder, du skal overveje:

- Udviklings- eller testmiljø, som omfatter slutpunkter, servere, domænecontrollere.
- Produktionsmiljø med Microsoft 365, Azure, Active Directory-tjenester, slutpunkter og servere

>[!NOTE]
>Hvis du endnu ikke har de fulde licenser, kan du få prøvelicenser for at evaluere [Microsoft 365 Defender](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) – planlægge, forberede, konfigurere, konfigurere og køre dit pilotprojekt. Dine interessenter kommer til at spille en stor rolle i at hjælpe med at lette processen fra start til slut.

De typer operativsystemer, der skal evalueres, bør også defineres baseret på organisatoriske forhold. Dette kan omfatte følgende: [Mac-slutpunkter](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements), [Linux-servere](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements), [Windows 10](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions) slutpunkter, [Windows Server 2016](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>Use cases

Use cases repræsenterer udsagn om, hvordan værktøjet, der testes, er beregnet til at blive brugt af dets tilsigtede brugere. Disse kan formuleres som brugerhistorier fra en bestemt persons perspektiv, f.eks. en SOC-analytiker. Eksempel:

- Som SOC-analytiker har jeg brug for at få vist, korrelere, vurdere og administrere vigtige beskeder og hændelser på tværs af enheder, brugere og postkasser i mit netværk. [Hændelsesstyring]
- Som SOC-analytiker skal jeg have værktøjet og processen til automatisk at undersøge og reagere på skadelige hændelser i mit netværk. [Automatisk IR]
- Som SOC-analytiker skal jeg søge i data fra mit miljø for at finde kendte og potentielle trusler og mistænkelige aktiviteter. [Avanceret jagt]

Husk, at disse use cases skal oprettes inden for parametrene for det definerede omfang. Hvis omfanget af test f.eks. ikke omfatter en evaluering af værktøjer som Microsoft Cloud App Security, bør der ikke oprettes use cases, der afhænger af dette som en datakilde.

## <a name="requirements"></a>Krav

På listen over use cases kan du begynde at oprette krav. Kravene omfatter funktioner, som et værktøj skal opfylde i use cases. Disse krav kan opdeles i kategorier, f.eks. konfiguration og vedligeholdelse, understøttelse af integrationer og funktionsspecifikke krav som f.eks. jagt på evner og muligheden for at opbygge brugerdefinerede beskeder.

## <a name="test-plan"></a>Testplan

Afhængigt af kravene kan forskellige testmetoder være passende. Hvis kravet f.eks. er at evaluere effekten af Automatiseret afhjælpning, skal testplanen indeholde trin til at generere den eller de funktionsmåder, der udløser en automatisk afhjælpningshandling inden for Microsoft 365 Defender. Hvis kravet er at registrere en bestemt adfærd eller angreb, kan testen omfatte flere trin. Pointen er at have en plan på plads, så den præcist tester i forhold til dine krav.

## <a name="success-criteria"></a>Succeskriterier

Succeskriterier er i sidste ende søjlen, der er indstillet til at måle i forhold til det, du tester. Uanset om du tester Microsoft 365 Defender (eller anden teknologi for den sags skyld) mod andre værktøjer eller af sig selv, skal der være nogle kvantificerbare kriterier for at bestemme den værdi, værktøjet leverer. Succeskriterierne er baseret på omfanget, kravene og testplanen og afgør, hvordan testen skal scores. Dette bør være mindre af en pass eller fail og mere af en vægtet pointdeling baseret på dine behov. Et værktøj kan f.eks. have behov for at score over 80 % på visse kritiske områder, som du identificerer.

## <a name="scorecard"></a>Scorecard

En måde at samle alle elementer i din plan på kan være at oprette et scorecard. Se et eksempelscorecard nedenfor:

| Use case | Krav | Konfigurationskrav | Testplan | Forventet resultat | Teststatus | Score | Bemærkninger |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|Hændelsesstyring|- Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender til slutpunkt </br></br>- Microsoft Cloud App Security (valgfrit)|Se [forudsætningerne](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) for forberedelse, konfiguration og konfiguration, hvis du vil have mere at vide |[Simulere angreb](m365d-pilot-simulate.md) <br></br>[Undersøg hændelsen](./m365d-pilot-simulate.md#investigate-an-incident) |Ligene kan forstå omfanget og effekten af hændelsen og administrere hændelsen||||
|AutoIR|- Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender til slutpunkt |Se [forudsætningerne](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) for forberedelse, konfiguration og konfiguration, hvis du vil have mere at vide <br>Aktivér AutoIR  |[Simulere angreb](m365d-pilot-simulate.md) <br></br>[Automatiseret undersøgelse](m365d-pilot-simulate.md#automated-investigation-and-remediation) |Beskeder og hændelser afhjælpes automatisk af Microsoft 365 Defender||||
|Avanceret jagt|- Microsoft 365 Defender </br></br>- Microsoft Defender til slutpunkt </br></br>-Microsoft Defender til Office 365 |Se [forudsætningerne](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) for forberedelse, konfiguration og konfiguration, hvis du vil have mere at vide|[Avanceret scenarie med jagt](./m365d-pilot-simulate.md#advanced-hunting-scenario) |Objekter kan finde data gennem avanceret jagt, dreje til påkrævne enheder og ved at oprette brugerdefinerede registreringer||||

## <a name="next-step"></a>Næste trin

|![Forberedelsesfase](../../media/mtp/prep.png) <br>[Forberedelsesfase](prepare-m365d-eval.md) | Forbered dit Microsoft 365 Defender pilotmiljø
|:-------|:-----|
