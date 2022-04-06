---
title: Microsoft Defender for Endpoint med flag til tidslinje på enheden
description: Brug Microsoft Defender for Endpoint tidslinje til at
keywords: Defender for endpoint-enhedstidslinje, begivenhedsflag
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
ms.openlocfilehash: 44292893249872c1c4b8dc3b4f66d10085fb0a2b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471181"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Microsoft Defender for Endpoint med flag til tidslinje på enheden

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Begivenhedsflag på tidslinjen for Defender for Endpoint-enheden hjælper dig med at filtrere og organisere bestemte hændelser, når du undersøger potentielle angreb.

Tidslinjen for Defender for slutpunkt-enheden giver en kronologisk visning af de hændelser og tilknyttede beskeder, der er observeret på en enhed. Denne liste over hændelser giver fuld indsigt i hændelser, filer og IP-adresser, der er observeret på enheden. Listen kan nogle gange være længere. Hændelsesflag for enhedens tidslinje hjælper dig med at spore hændelser, der kunne være relaterede.

Når du har gennemgået en tidslinje på en enhed, kan du sortere, filtrere og eksportere de specifikke hændelser, du har markeret med flag.

Mens du navigerer på enhedens tidslinje, kan du søge efter og filtrere efter bestemte hændelser. Du kan angive begivenhedsflag ved at:

- Fremhæve de vigtigste begivenheder
- Markering af hændelser, der kræver dybt dyk
- Opbygning af en tidslinje med rene brud

## <a name="flag-an-event"></a>Markér en begivenhed med flag

1. Find den begivenhed, du vil markere med flag

2. Klik på flagikonet i kolonnen Flag. 

:::image type="content" source="images/device-flags.png" alt-text="Enhedens tidslinjeflag" lightbox="images/device-flags.png":::

## <a name="view-flagged-events"></a>Få vist begivenheder, der er markeret med flag

1. I sektionen **Tidslinjefiltre** skal du aktivere **hændelser markeret med flag**.
2. Klik på **Anvend**. Kun begivenheder, der er markeret med flag, vises.

Du kan anvende yderligere filtre ved at klikke på tidslinjen. Dette viser kun begivenheder før den markerede begivenhed.  

:::image type="content" source="images/device-flag-filter.png" alt-text="Enhedens tidslinjeflag med filteret slået til" lightbox="images/device-flag-filter.png":::