---
title: Føj data fra ét korrektursæt til et andet
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvordan du vælger dokumenter fra ét korrektursæt og arbejder med dem individuelt i et andet sæt i en Microsoft Purview eDiscovery (Premium)-sag.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 4fc1548903ebea3a42d1612c8e9c74be32bbe0ba
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640958"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Føj data til et korrektursæt fra et andet korrektursæt

I nogle tilfælde kan det være nødvendigt at vælge dokumenter fra ét korrektursæt og arbejde med dem individuelt i et andet korrektursæt. Dette er især nyttigt, hvis du har slettet indhold i et anmeldelsessæt og gerne vil køre analyser på undersættet af data.

Følg arbejdsprocessen i denne artikel for at føje indhold fra ét korrektursæt til et andet.

## <a name="create-a-review-set"></a>Opret et korrektursæt

Før du starter, skal du oprette et korrektursæt, som dataene skal føjes til.  Der kan tilføjes et nyt korrektursæt under fanen **Gennemse sæt** i sagen. Du kan få flere oplysninger under [Opret et korrektursæt](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Trin 1: Identificer indhold, der skal føjes til et andet korrektursæt

Du kan føje indhold fra ét korrektursæt til et andet ved at vælge bestemte dokumenter i kildegennemsynssættet eller ved at vælge alle elementer, der returneres af en forespørgsel i korrektursæt. Hvis du tilføjer valgte elementer, skal du vælge elementerne, vælge **Handling** og derefter vælge **Føj til et andet korrektursæt**.

![Føj til et andet korrektursæt i menuen Handling.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Trin 2: Angiv indstillinger for tilføjelse til et andet korrektursæt

På siden **Føj til en anden indstilling for korrektursæt** skal du vælge det korrektursæt, du vil føje elementerne til. Vælg, om du vil tilføje **alle søgeresultater** eller **Valgte elementer**.  **Yderligere oplysninger** indeholder indstillinger for at inkludere alle metadata fra elementerne, og om du vil medtage mærkerne (ved at markere afkrydsningsfeltet **Mærkater** ) fra kildegennemsynssættet, når dokumenterne føjes til det nye korrektursæt.  

![Indstillinger for tilføjelse af data til et andet korrektursæt.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Når du har **klikket på OK**, oprettes der et nyt job (med navnet **Føj data til et andet korrektursæt**) for at føje indholdet til et andet korrektursæt. Du kan gå til fanen **Job** og overvåge status for dette job. Du kan få flere oplysninger under [Administrer job](managing-jobs-ediscovery20.md).
