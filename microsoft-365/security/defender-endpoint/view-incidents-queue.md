---
title: Få vist og organiser køen hændelser
ms.reviewer: ''
description: Se listen over hændelser, og få mere at vide om, hvordan du anvender filtre for at begrænse listen og få en mere fokuseret visning.
keywords: få vist, organisere, hændelser, samle, undersøgelser, kø, ttp
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d57097d255b9f64782320dbd380f90b7a98573cb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591815"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>Få vist og organiser køen for Microsoft Defender til slutpunktshændelser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

**Køen Hændelser viser** en samling af hændelser, der er markeret med flag fra enheder i dit netværk. Det hjælper dig med at sortere efter hændelser for at prioritere og skabe en informeret beslutning om svar på cybersikkerhed.

Som standard viser køen hændelser i løbet af de seneste 30 dage, hvor den seneste hændelse vises øverst på listen, hvilket hjælper dig med at se de seneste hændelser først.

Der er flere muligheder, du kan vælge mellem for at tilpasse visningen af køen Hændelser. 

På den øverste navigationslinje kan du:
- Tilpasse kolonner for at tilføje eller fjerne kolonner 
- Rediger antallet af elementer, der skal vises pr. side
- Vælg de elementer, der skal vises pr. side
- Batch-vælg de hændelser, der skal tildeles 
- Naviger mellem sider
- Anvend filtre

![Billede af kø over hændelser.](images/atp-incident-queue.png)

## <a name="sort-and-filter-the-incidents-queue"></a>Sortér og filtrer køen over hændelser
Du kan anvende følgende filtre til at begrænse listen over hændelser og få en mere fokuseret visning.

### <a name="severity"></a>Alvorsgrad

Hændelsens alvorsgrad | Beskrivelse
:---|:---
Høj </br>(Rød) | Trusler, der ofte er knyttet til avancerede permanente trusler (APT). Disse hændelser angiver en høj risiko på grund af den alvorlige skade, de kan påtfalde på enheder.
Mellem </br>(Orange) | Trusler, der sjældent observeres i organisationen, f.eks. unormale registreringsdatabaseændringer, udførelse af mistænkelige filer og observerede funktionsmåder, der typisk forekommer i forbindelse med angrebsfaser.
Lav </br>(Gul) | Trusler, der er knyttet til meget almindeligt malware og hack-værktøjer, der ikke nødvendigvis indikerer en avanceret trusselsmålretning mod organisationen.
Information </br>(Grå) | Informationshændelser kan ikke betragtes som skadelige for netværket, men kan være gode at holde styr på.

## <a name="assigned-to"></a>Tildelt til
Du kan vælge at filtrere listen ved at vælge tildelt til en eller flere af dem, du har fået tildelt.

### <a name="category"></a>Kategori
Hændelser kategoriseres efter beskrivelsen af den fase, hvor cybersecurity-kill-kæden er i. Denne visning hjælper trusselsanalytikeren med at fastlægge prioritet, haster og tilsvarende svarstrategi til implementering baseret på kontekst.

### <a name="status"></a>Status
Du kan vælge at begrænse listen over hændelser, der vises, ud fra deres status for at se, hvilke hændelser der er aktive eller løst.

### <a name="data-sensitivity"></a>Datafølsomhed
Brug dette filter til at vise hændelser, der indeholder følsomhedsmærkater.

## <a name="incident-naming"></a>Navngivning af hændelse

For hurtigt at forstå hændelsens omfang genereres hændelsesnavne automatisk baseret på beskedattributter som f.eks. antallet af berørte slutpunkter, brugere, der er påvirket, registreringskilder eller kategorier.

For eksempel: *Hændelser i flere faser på flere slutpunkter rapporteret af flere kilder.*

> [!NOTE]
> Hændelser, der fandtes før rullen af automatisk navngivning af hændelser, bevarer deres navn.


## <a name="see-also"></a>Se også
- [Kø over hændelser](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)

