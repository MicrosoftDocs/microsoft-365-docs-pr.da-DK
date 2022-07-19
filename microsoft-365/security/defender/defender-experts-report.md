---
title: Forstå Defender Experts for Hunting-rapporten i Microsoft 365 Defender
ms.reviewer: ''
description: Defender Experts for Hunting service udgiver månedlige rapporter for at hjælpe dig med at forstå alle de trusler, som jagttjenesten dukker op i dit miljø
keywords: analytikerrapport, defender experts report, detections, defender expert notification, hunting, notifications, threat categories, hunting reports
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1cf768ce5dec194f2f1514a29e7cb98c6d753223
ms.sourcegitcommit: a0b78895d92cf3b8321b5282b5f4ff8984e95c06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66859114"
---
# <a name="understand-the-defender-experts-for-hunting-report-in-microsoft-365-defender"></a>Forstå Defender Experts for Hunting-rapporten i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender Experts for Hunting lag menneskelig intelligens og ekspertoplært teknologi for at hjælpe Microsoft 365 Defender kunder med at forstå de betydelige trusler, de står overfor. Den viser, hvordan Defender Experts trusselsjagtfærdigheder, en grundig forståelse af trusselslandskabet og viden om nye trusler kan hjælpe dig med at identificere, prioritere og håndtere disse trusler i dit miljø. 

Defender Experts for Hunting service udgiver månedlige rapporter for at hjælpe dig med at forstå alle de trusler, som jagttjenesten dukker op i dit miljø, sammen med de beskeder, der genereres af dine Microsoft 365 Defender produkter.

Hvis du vil have vist den seneste rapport på din Microsoft 365 Defender portal, skal du gå til **Rapporter** og vælge **Defender Experts** > **Defender Experts for Hunting report**.

## <a name="scan-the-defender-experts-for-hunting-report-to-know-what-to-prioritize"></a>Scan Defender Experts for Hunting-rapporten for at finde ud af, hvad du skal prioritere

Hvert afsnit i rapporten er designet til at give mere indsigt i de trusler, som vores Defender Experts fandt i dit miljø. Rapporterne indeholder de afsnit, der er beskrevet i følgende tabel:

| Rapportsektion | Beskrivelse |
|--|--|
| Jaget og triaged | Det samlede antal potentielle cybersikkerhedsproblemer, der findes i dit miljø. |
| Undersøgt | Antallet af cybersikkerhedsproblemer, der har brug for yderligere analyse for at bestemme deres karakter og omfang. |
| Meddelt (vis meddelelse) | Antallet af Defender Experts-meddelelser, som Defender Experts har sendt. Disse meddelelser er relateret til de undersøgte mulige trusselsaktiviteter i dit miljø, der skal prioriteres baseret på uopsættelighed og indvirkning. |
| MITRE ATT&CK taktik observeret | Antallet af angreb taktik og teknikker observeret i dit miljø og kortlagt i henhold til [MITRE ATT&CK rammer](https://attack.mitre.org/). Dette afsnit visualiserer, hvor mange angreb der er nået hver taktik, så du kan tage passende handlinger som at gennemgå dem, der skrider yderligere frem først. |
| Observerede trusselskategorier | Kategorierne viser de største trusler og risici, der er observeret i dit miljø. De mest kritiske kategorier er fremhævet for at hjælpe dig med yderligere at vurdere og evaluere din sikkerhedsholdning baseret på truslernes kendte egenskaber, adfærd og potentielle indvirkning. Det giver dig også mulighed for at fokusere på og prioritere presserende opgaver, der skal håndteres. |

Se følgende skærmbillede af en eksempelrapport:

![defender experts report](../../media/mte/defender-experts-report.png)

## <a name="view-defender-experts-notifications"></a>Vis meddelelser fra Defender Experts

En meddelelse fra Defender Experts beskriver den betydelige trusselsaktivitet Defender Experts for Hunting, der er observeret i dit miljø, og indeholder anbefalinger til at afhjælpe og forsvare din organisation.

Defender Experts for Hunting-rapporterne giver dig det samlede antal Defender Experts-meddelelser, som vores Defender-eksperter har sendt til dit valgte tidspunkt. Hvis du vil have vist disse meddelelser, skal du klikke på **Vis meddelelse** ud **for Meddelelse**.

Dette link omdirigerer dig til siden med Microsoft 365 Defender hændelser. Defender Expert for Hunting alerts eller Defender Experts Notifications er mærket med **Defender Experts**.

> [!NOTE]
> Linket **Vis meddelelse** vises kun, hvis den værdi, der vises i **Meddelelse,** er mindst 1.

## <a name="identify-potential-attack-entry-points-and-other-security-weak-spots"></a>Identificer potentielle indgangspunkter for angreb og andre svage sikkerhedspunkter

MITRE ATT-&CK-taktik repræsenterer modstanderens mål – det, de forsøger at opnå i hver angrebsfase. **MITRE ATT&CK taktik observeret** afsnit af rapporten sporer progressionen af angreb mod den fase, de nåede:

1.  Rekognoscering
2.  Ressourceudvikling
3.  Indledende adgang
4.  Udførelse   
3.  Persistens 
4.  Rettighedseskalering    
5.  Forsvarsunddragelse 
6.  Adgang til legitimationsoplysninger
7.  Opdagelse
8.  Tværgående bevægelse    
9.  Samling
10. Kommando og kontrolelement
11. Eksfiltration    
12. Indvirkning

Signaler fra Microsoft 365 Defender og undersøgelser foretaget af Defender Experts for Hunting hjælper med at identificere disse taktikker, der er repræsenteret i det liggende søjlediagram. Dette diagram hjælper dig med at visualisere, hvor overspændingen er, og giver dig de oplysninger, du skal bruge for at planlægge de tilsvarende opbevarings- og afhjælpningshandlinger.

## <a name="know-and-understand-the-prevalent-threats-in-your-environment"></a>Kend og forstå de udbredte trusler i dit miljø

Trusselskategorier hjælper med at identificere og organisere sikkerhedstrusler i klasser for at vurdere og evaluere deres indvirkning og udvikle strategier for at forhindre eller afhjælpe disse trusler mod dit miljø. Afsnittet **Trusselskategorier, der er observeret** i rapporten, viser et liggende søjlediagram med betydelige risici og trusler, der er registreret i dit miljø, hvilket hjælper dig med at forstå bredden og omfanget af din eksponering.

Blandt de forskellige trusselskategorier, der er tilgængelige, vælges følgende kategorier omhyggeligt, fordi de ikke er omfattet af MITRE ATT-&CK-strukturen:

- Ransomware
- Malware
- Våben
- Udnytte
- Levering

Du kan prioritere afhjælpning baseret på den mest påvirkede kategori, som vist i søjlediagrammet.
