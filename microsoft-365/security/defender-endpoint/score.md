---
title: Scoremetoder og -egenskaber
description: Henter din organisations eksponeringsscore, enhedens sikre score og eksponeringsscore efter enhedsgruppe
keywords: apis, graph api, understøttede API'er, score, eksponeringsscore, enhedsscore, eksponeringsscore efter enhedsgruppe
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe69b42c2d8bf80089b749cd41e59664cc2921e3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63603077"
---
# <a name="score-resource-type"></a>Ressourcetypen Score

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Metoder

Metode|Returtype|Beskrivelse
:---|:---|:---
[Få eksponeringsscore](get-exposure-score.md)|[Score](score.md)|Få den organisatoriske eksponeringsscore.
[Få sikker score på enhed](get-device-secure-score.md)|[Score](score.md)|Få et sikkert resultat for organisationens enhed.
[Vis eksponeringsscore efter enhedsgruppe](get-machine-group-exposure-score.md)|[Score](score.md)|Opliste karakterer efter enhedsgruppe.

## <a name="properties"></a>Egenskaber

Egenskab|Type|Beskrivelse
:---|:---|:---
Score|Dobbelt|Det aktuelle resultat.
Klokkeslæt|DateTime|Dato og klokkeslæt for, hvor opkaldet for denne API blev foretaget.
RbacGroupName|String|Enhedsgruppens navn.
RbacGroupId|String|Enhedsgruppe-id'et.
