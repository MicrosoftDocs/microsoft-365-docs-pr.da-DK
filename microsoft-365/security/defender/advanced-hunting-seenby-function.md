---
title: Funktionen SeenBy() i avanceret jagt efter Microsoft 365 Defender
description: Få mere at vide om, hvordan du bruger funktionen SeenBy() til at søge efter, hvilke onboardede enheder der har fundet en bestemt enhed
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, SeenBy, enhedsregistrering, funktion, berigelse
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
ms.openlocfilehash: 4a17efeeaf62ddcf63988f055ca93b536e68c962
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174988"
---
# <a name="seenby"></a>SeenBy()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Funktionen `SeenBy()` aktiveres for at få vist en liste over onboardede enheder, der har set en bestemt enhed ved hjælp af funktionen til enhedsregistrering.

Denne funktion returnerer en tabel, der har følgende kolonne:

| Kolonne | Datatype | Beskrivelse |
|------------|---------------|-------------|
| `DeviceId` | `string` | Entydigt id for enheden i tjenesten |


## <a name="syntax"></a>Syntaks

```kusto
invoke SeenBy(x)
```

- hvor **x** er det enheds-id, der er interessant

>[!TIP]
> Berigelsesfunktioner viser kun supplerende oplysninger, når de er tilgængelige. Tilgængeligheden af oplysninger er forskellig og afhænger af mange faktorer. Sørg for at overveje dette, når du bruger SeenBy() i dine forespørgsler eller i forbindelse med oprettelse af brugerdefinerede registreringer. Vi anbefaler, at du bruger funktionen SeenBy() med tabellen DeviceInfo for at opnå de bedste resultater.

### <a name="example-obtain-list-of-onboarded-devices-that-have-seen-a-device"></a>Eksempel: Få en liste over onboardede enheder, der har set en enhed

```kusto
DeviceInfo 
| where OnboardingStatus <> "Onboarded" 
| limit 100 | invoke SeenBy()
```

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Få flere eksempler på forespørgsler](advanced-hunting-shared-queries.md)
