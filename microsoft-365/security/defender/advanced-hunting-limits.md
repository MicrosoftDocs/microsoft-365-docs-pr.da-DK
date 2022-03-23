---
title: Avancerede kvotaer og brugsparametre i Microsoft 365 Defender
description: Forstå forskellige kvoter og brugsparametre (tjenestebegrænsninger), der holder den avancerede jagttjeneste hurtig
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skema, kusto, CPU-grænse, forespørgselsgrænse, ressourcer, maksimale resultater, kvote, parametre, tildeling
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fe0ad42ac0ebfc7f6816e412ab6ffb0ac9291b44
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63592707"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>Avancerede kvote- og forbrugsparametre

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

For at holde tjenesten effektiv indstiller avanceret jagt forskellige kvoter og brugsparametre (også kaldet "servicebegrænsninger"). Disse kvoter og parametre gælder separat for forespørgsler, der køres manuelt, og for forespørgsler, der køres ved hjælp af [brugerdefinerede registreringsregler](custom-detection-rules.md). Kunder, der kører flere forespørgsler regelmæssigt, skal være opmærksom på disse begrænsninger og anvende bedste fremgangsmåder [til optimering](advanced-hunting-best-practices.md) for at minimere afbrydelser.

Se følgende tabel for at forstå eksisterende kvoter og forbrugsparametre.

| Kvote eller parameter | Størrelse | Opdateringscyklus | Beskrivelse |
|--|--|--|--|
| Dataområde | 30 dage | Hver forespørgsel | Hver forespørgsel kan søge efter data fra op til de seneste 30 dage. |
| Resultatsæt | 10.000 rækker | Hver forespørgsel | Hver forespørgsel kan returnere op til 10.000 poster. |
| Timeout | 10 minutter | Hver forespørgsel | Hver forespørgsel kan køre i op til 10 minutter. Hvis den ikke fuldføres inden for 10 minutter, viser tjenesten en fejl.
| CPU-ressourcer | Baseret på lejerstørrelse | Hvert 15. minut | Portalen [viser en fejl,](advanced-hunting-errors.md) når en forespørgsel køres, og lejeren har brugt mere end 10 % af allokerede ressourcer. Forespørgsler blokeres, hvis lejeren har nået 100 % indtil efter den næste 15-minutters cyklus. |

>[!NOTE] 
>Et separat sæt kvoter og parametre gælder for avancerede forespørgselsforespørgsler, der udføres via API'en. [Læs om avancerede API'er til jagt](./api-advanced-hunting.md)

## <a name="related-topics"></a>Relaterede emner

- [Avancerede bedste fremgangsmåder på jagt](advanced-hunting-best-practices.md)
- [Håndter avancerede jagtfejl](advanced-hunting-errors.md)
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)