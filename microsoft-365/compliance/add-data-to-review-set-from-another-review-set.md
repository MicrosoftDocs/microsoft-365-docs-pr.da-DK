---
title: Tilføje data fra ét korrektursæt til et andet korrektursæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvordan du vælger dokumenter fra ét korrektursæt og arbejder med dem enkeltvis i et andet sæt Advanced eDiscovery en sag.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 4f230c5a9a4a202fc417ad4e16ca5bee5f7e433b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587702"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Føje data til et korrektursæt fra et andet korrektursæt

I nogle tilfælde kan det være nødvendigt at vælge dokumenter fra ét korrektursæt og arbejde med dem enkeltvis i et andet korrektursæt. Dette er især nyttigt, hvis du har taget indhold fra et korrektursæt og vil køre analyser på undersættet af data.

Følg arbejdsprocessen i denne artikel for at tilføje indhold fra ét gennemsynssæt til et andet.

## <a name="create-a-review-set"></a>Opret et korrektursæt

Før du starter, skal du oprette et korrektursæt, som dataene skal føjes til.  Et nyt korrektursæt kan tilføjes **på fanen Gennemse** sæt for sagen. Få mere at vide under [Opret et korrektursæt](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Trin 1: Identificer indhold, der skal føjes til et andet korrektursæt

Du kan tilføje indhold fra én korrektursæt til en anden ved at vælge bestemte dokumenter i kildegennemsynssættet eller ved at vælge alle elementer, der returneres af gennemsynssætforespørgslen. Hvis du tilføjer markerede elementer, skal du markere elementerne, vælge **Handling** og derefter vælge Føj til **et andet korrektursæt**.

![Føj til et andet korrektursæt i menuen Handling.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Trin 2: Angiv indstillinger for tilføjelse til et andet korrektursæt

På pop **op-siden Føj til en anden** indstilling for korrekturindstillinger skal du vælge det korrektursæt, du vil føje elementerne til. Vælg, om du **vil tilføje Alle søgeresultater** eller **Markerede elementer**.  **Yderligere oplysninger** giver mulighed for at medtage alle metadata fra elementerne, og om mærkerne skal medtages (ved at markere  afkrydsningsfeltet Etiketter) fra kildegennemsynssættet, når dokumenter føjes til det nye korrektursæt.  

![Indstillinger for tilføjelse af data til et andet korrektursæt.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Når du har **klikket på OK**, oprettes der et nyt job (med navnet Føje **data** til et andet korrektursæt) for at føje indholdet til et andet korrektursæt. Du kan gå til **fanen Job** og overvåge status for dette job. Få mere at vide under [Administrer job](managing-jobs-ediscovery20.md).
