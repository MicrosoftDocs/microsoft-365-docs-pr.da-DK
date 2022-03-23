---
title: ASR-regler for installationsfase 4 – drift
description: Giver vejledning i at drifte dine regler for reduktion af angrebsoverfladen.
keywords: Implementering af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, beskyttelsessystem til forebyggelse af indtrængen, beskyttelsesregler, anti exploit, udnyttelsesregler, regler for forebyggelse af indtrængen, Microsoft Defender til slutpunkt, konfigurer ASR-regler
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
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: b668519b84037000610fa3fe76ec5462b9657b3d
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63593653"
---
# <a name="asr-rules-deployment-phase-4-operationalize"></a>ASR-regler for installationsfase 4: drift

Når du har installeret ASR-regler fuldt ud, er det vigtigt, at du har processer på plads til at overvåge og reagere på ASR-relaterede aktiviteter.

## <a name="manage-false-positives"></a>Administrer falske positive

Falske positive/negativer kan forekomme med enhver trusselsbeskyttelsesløsning. Falske positive er tilfælde, hvor en enhed (f.eks. en fil eller proces) registreres og identificeres som skadelig, selvom enheden faktisk ikke er en trussel. I modsætning hertil er en falsk negativ en enhed, der ikke blev registreret som en trussel, men er skadelig. Du kan finde flere oplysninger om falske positive og falske negativer i: [Adresserer falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Holde styr på rapporter

Konsekvent, regelmæssig gennemgang af rapporter er et vigtigt aspekt i forbindelse med at opretholde dine AR-regler for installation og holde dig orienteret om nye trusler. Din organisation bør have planlagte anmeldelser af ASR-regelhændelser på en kadence, der holder sig opdateret med ASR-regelrapporterede hændelser. Afhængigt af størrelsen på din organisation kan anmeldelser være dagligt, hver time eller fortløbende overvågning.

## <a name="hunting"></a>På jagt

En af de mest effektive funktioner [i Microsoft 365 Defender er](https://security.microsoft.com) avanceret på jagt. Hvis du ikke kender til avanceret jagt, kan du se: [Proaktivt på jagt efter trusler med avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender Avanceret på jagt](images/asr-defender365-advanced-hunting2.png)

Avanceret jagt er et forespørgselsbaseret (Kusto-forespørgselssprog) værktøj til trusselssøgning, som giver dig mulighed for at udforske op til 30 dage af de registrerede (rå) data, som Microsoft Defender ATP-slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) indsamler fra alle dine computere. Ved hjælp af avanceret jagt kan du proaktivt undersøge begivenheder for at finde interessante indikatorer og enheder. Fleksibel adgang til data letter uoverensholdet jagt på både kendte og potentielle trusler.

Ved hjælp af avanceret jagt er det muligt at udtrække oplysninger om ASR-regler, oprette rapporter og få uddybende oplysninger om konteksten for en given asr-regelrevision eller blokere hændelse.

 Du kan oprette forespørgsler om ASR-regelhændelser fra tabellen DeviceEvents i afsnittet avanceret Microsoft 365 Defender portalen. Eksempelvis kan en simpel forespørgsel som den nedenfor rapportere alle hændelser, der har ASR-regler som datakilde for de seneste 30 dage, og opsummere dem med ActionType-antallet, som i dette tilfælde vil være det faktiske kodenavn for ASR-reglen.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender Avanceret forespørgsel på forespørgsel](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender avancerede forespørgselsresultater](images/asr-defender365-advanced-hunting4.png)

Ovenstående viser, at der blev registreret 187 hændelser for AsrLsassCredentialTheft:

- 102 for Blokeret
- 85 for Overvåget
- 2 hændelser for AsrOfficeProcess (1 for Overvåget og 1 for Blok)
- 8 hændelser for AsrPsexecWmiProcessAudited

Hvis du vil fokusere på reglen AsrOffice Direkteprocess og få mere at vide om de faktiske filer og processer, skal du ændre filteret for ActionType og erstatte opsummeringslinjen med en projektion af de ønskede felter (i dette tilfælde er det DeviceName, FileName, FolderPath osv.).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender Avanceret forespørgsel fokuseret](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender Avancerede forespørgsel fokuserede resultater](images/asr-defender365-advanced-hunting5b.png)

Den store fordel ved avanceret jagt er, at du kan forme forespørgslerne efter din smag. Ved at forme din forespørgsel kan du se den nøjagtige historie om, hvad der skete, uanset om du vil finde noget på en enkelt maskine, eller du vil udtrække viden fra hele miljøet.

Du kan finde flere oplysninger om muligheder for at lede i: [Afmystificere regler for reduktion af angrebsoverfladen – Del 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Emner i denne installationssamling

[Oversigt over ASR-regler for installation](attack-surface-reduction-rules-deployment.md)

[Fase 1: Plan](attack-surface-reduction-rules-deployment-phase-1.md)

[Fase 2: Test](attack-surface-reduction-rules-deployment-phase-2.md)

[Fase 4: Drift](attack-surface-reduction-rules-deployment-phase-4.md)
