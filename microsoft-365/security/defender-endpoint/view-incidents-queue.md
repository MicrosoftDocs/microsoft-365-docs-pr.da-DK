---
title: Få vist og organiser hændelseskøer
ms.reviewer: ''
description: Se listen over hændelser, og få mere at vide om, hvordan du anvender filtre for at begrænse listen og få en mere fokuseret visning.
keywords: få vist, organisere, hændelser, aggregere, undersøgelser, kø, ttp
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
ms.openlocfilehash: a2d75b935c19a20c37ecdbdb77feff73bbed4a79
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/11/2022
ms.locfileid: "66714635"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>Få vist og organiser køen Microsoft Defender for Endpoint hændelser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

**Køen Hændelser** viser en samling af hændelser, der er markeret fra enheder i netværket. Det hjælper dig med at sortere gennem hændelser for at prioritere og oprette en informeret beslutning om cybersikkerhedssvar.

Som standard viser køen hændelser, der er set inden for de seneste 30 dage, hvor den seneste hændelse vises øverst på listen, hvilket hjælper dig med at se de seneste hændelser først.

Der er flere indstillinger, du kan vælge imellem for at tilpasse køvisningen Hændelser. 

På den øverste navigationslinje kan du:
- Tilpas kolonner for at tilføje eller fjerne kolonner 
- Rediger det antal elementer, der skal vises pr. side
- Vælg de elementer, der skal vises pr. side
- Vælg batch for de hændelser, der skal tildeles 
- Naviger mellem sider
- Anvend filtre
- Tilpas og anvend datointervaller

:::image type="content" source="images/atp-incident-queue.png" alt-text="Hændelseskøen" lightbox="images/atp-incident-queue.png":::

## <a name="sort-and-filter-the-incidents-queue"></a>Sortér og filtrer hændelseskøen
Du kan anvende følgende filtre for at begrænse listen over hændelser og få en mere fokuseret visning.

### <a name="severity"></a>Sværhedsgraden

Alvorsgrad af hændelse | Beskrivelse
:---|:---
Høj </br>( Rød) | Trusler, der ofte er forbundet med avancerede vedvarende trusler (APT). Disse hændelser indikerer en høj risiko på grund af alvorligheden af skader, de kan påføre enheder.
Medium </br>( Orange) | Trusler, der sjældent observeres i organisationen, f.eks. unormal ændring af registreringsdatabasen, udførelse af mistænkelige filer og observeret adfærd, der er typisk for angrebsfaser.
Lav </br>(Gul) | Trusler forbundet med udbredt malware og hackværktøjer, der ikke nødvendigvis indikerer en avanceret trussel, der er målrettet til organisationen.
Informative </br>(Grå) | Informationshændelser betragtes muligvis ikke som skadelige for netværket, men kan være gode at holde styr på.

## <a name="assigned-to"></a>Tildelt til
Du kan vælge at filtrere listen ved at vælge Tildelt til alle eller dem, der er tildelt til dig.

### <a name="category"></a>Kategori
Hændelser er kategoriseret på baggrund af beskrivelsen af den fase, som cybersikkerhed kill chain er i. Denne visning hjælper trusselsanalytikeren med at bestemme prioritet, uopsættelighed og tilsvarende svarstrategi, der skal udrulles på baggrund af kontekst.

### <a name="status"></a>Status
Du kan vælge at begrænse listen over viste hændelser baseret på deres status for at se, hvilke der er aktive eller løst.

### <a name="data-sensitivity"></a>Datafølsomhed
Brug dette filter til at vise hændelser, der indeholder følsomhedsmærkater.

## <a name="incident-naming"></a>Navngivning af hændelse

For hurtigt at forstå hændelsens omfang genereres hændelsesnavne automatisk på baggrund af beskedattributter, f.eks. antallet af berørte slutpunkter, berørte brugere, registreringskilder eller kategorier.

Eksempel: *Hændelse med flere faser på flere slutpunkter rapporteret af flere kilder.*

> [!NOTE]
> Hændelser, der fandtes før udrulningen af automatisk navngivning af hændelser, bevarer deres navn.


## <a name="see-also"></a>Se også
- [Kø over hændelser](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)

