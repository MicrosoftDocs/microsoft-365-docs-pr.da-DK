---
title: Brugerressourcetype
description: Hent de seneste Microsoft Defender for Endpoint-beskeder, der er relateret til brugere.
keywords: apis, graph api, understøttede API'er, hent, beskeder, seneste
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 01b7eb32415e431dce37935abb4a1a69776db0f9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591917"
---
# <a name="user-resource-type"></a>Brugerressourcetype

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Metode|Returtype|Beskrivelse
---|---|---
[Vis brugerrelaterede beskeder](get-user-related-alerts.md)|[samling af](alerts.md) beskeder|Vis alle de beskeder, der er knyttet til en [bruger](user.md).
[Liste over brugerrelaterede enheder](get-user-related-machines.md)|[maskine samling](machine.md)|Vis alle de enheder, der blev logget på af en [bruger](user.md).
