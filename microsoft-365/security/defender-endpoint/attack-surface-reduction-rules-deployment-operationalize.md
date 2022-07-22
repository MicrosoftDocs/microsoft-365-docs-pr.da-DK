---
title: Operationaliser regler for reduktion af angrebsoverflade
description: Indeholder en vejledning i, hvordan du kan udføre udrulningen af regler for reduktion af angrebsoverfladen.
keywords: Installation af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, forebyggelsessystem for værtsindtrængen, beskyttelsesregler, regler for bekæmpelse af udnyttelse, anti-exploit, udnyttelsesregler, regler til forebyggelse af infektion, Microsoft Defender for Endpoint, konfigurer ASR-regler
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- M365-security-compliance
- m365solution-asr-rules
ms.date: 1/18/2022
ms.openlocfilehash: b3a978f5bda7de3e606b4521eb55ab471465b7b2
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969326"
---
# <a name="operationalize-attack-surface-reduction-asr-rules"></a>Operationaliser regler for reduktion af angrebsoverflade

Når du har udrullet asr-regler (attack surface reduction), er det vigtigt, at du har processer på plads til at overvåge og reagere på ASR-relaterede aktiviteter.

## <a name="managing-false-positives"></a>Administration af falske positiver

Falske positiver/negativer kan forekomme med enhver trusselsbeskyttelsesløsning. Falske positiver er tilfælde, hvor en enhed (f.eks. en fil eller proces) registreres og identificeres som skadelig, selvom enheden faktisk ikke er en trussel. I modsætning hertil er et falsk negativt objekt et objekt, der ikke blev registreret som en trussel, men som er skadeligt. Du kan finde flere oplysninger om falske positiver og falske negativer [i: Adresse falske positive/negative i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Hold styr på rapporter

Konsekvent og regelmæssig gennemgang af rapporter er et vigtigt aspekt ved at opretholde udrulningen af dine ASR-regler og holde dig ajour med nye trusler. Din organisation skal have planlagte anmeldelser af ASR-regelhændelser i en kadence, der vil holde sig opdateret med rapporterede ASR-regler. Afhængigt af størrelsen på din organisation kan anmeldelser være dagligt, hver time eller løbende overvågning.

## <a name="hunting"></a>Jagt

Et af de mest magtfulde træk [ved Microsoft 365 Defender](https://security.microsoft.com) er avanceret jagt. Hvis du ikke er bekendt med avanceret jagt, kan du se: [Proaktivt jagt efter trusler med avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting2.png" alt-text="Siden Avanceret jagt på portalen Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting2.png":::

Avanceret jagt er et forespørgselsbaseret værktøj (Kusto Query Language), som du kan bruge til at udforske op til 30 dage af de hentede (rå) data, som EDR (Microsoft Defender ATP Endpoint Detection and Response) indsamler fra alle dine maskiner. Gennem avanceret jagt kan du proaktivt inspicere hændelser for at finde interessante indikatorer og enheder. Den fleksible adgang til data gør det muligt at jagte både kendte og potentielle trusler uden begrænsninger.

Gennem avanceret jagt er det muligt at udtrække oplysninger om ASR-regler, oprette rapporter og få detaljerede oplysninger om konteksten af en given ASR-regelrevision eller -blokhændelse.

 Du kan forespørge om ASR-regler fra tabellen DeviceEvents i afsnittet avanceret jagt på Microsoft 365 Defender portalen. En simpel forespørgsel som den nedenfor kan f.eks. rapportere alle de hændelser, der har ASR-regler som datakilde, i de sidste 30 dage og opsummere dem med antallet af ActionType, der i dette tilfælde vil være det faktiske kodenavn for ASR-reglen.

ASR-hændelser, der vises i den fremskredne jagtportal, begrænses til unikke processer, der ses hver time. Tidspunktet for ASR-hændelsen er første gang, hændelsen ses inden for den pågældende time.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting3.png" alt-text="Kommandolinjen avanceret jagtforespørgsel på Microsoft 365 Defender-portalen" lightbox="images/asr-defender365-advanced-hunting3.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4.png" alt-text="Forespørgslen Avanceret jagt resulterer i Microsoft 365 Defender-portalen" lightbox="images/asr-defender365-advanced-hunting4.png":::

Ovenstående viser, at 187 hændelser blev registreret for AsrLsassCredentialTheft:

- 102 for Blokeret
- 85 for overvåget
- 2 hændelser for AsrOfficeChildProcess (1 for Audited og 1 for Block)
- 8 hændelser for AsrPsexecWmiChildProcessAudited

Hvis du vil fokusere på reglen AsrOfficeChildProcess og få oplysninger om de faktiske filer og processer, skal du ændre filteret for ActionType og erstatte opsummeringslinjen med en projektion af de ønskede felter (i dette tilfælde er de DeviceName, FileName, FolderPath osv.).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4b.png" alt-text="Det fokuserede eksempel på avanceret jagtforespørgsel på Microsoft 365 Defender-portalen" lightbox="images/asr-defender365-advanced-hunting4b.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting5b.png" alt-text="Den avancerede jagtforespørgsel fokuserer på resultater på Microsoft 365 Defender-portalen" lightbox="images/asr-defender365-advanced-hunting5b.png":::

Den sande fordel ved avanceret jagt er, at du kan forme forespørgslerne efter din smag. Ved at forme din forespørgsel kan du se den nøjagtige historie om, hvad der skete, uanset om du vil fastgøre noget på en individuel maskine, eller du vil udtrække indsigt fra hele dit miljø.

Du kan finde flere oplysninger om jagtmuligheder under: [Afmystificerende regler for reduktion af angrebsoverfladen – del 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Emner i denne installationssamling

[Udrulningsoversigt til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md)

[Planlæg udrulning af reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Regler for testreduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-test.md)

[Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md)

[Henvisning til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)
