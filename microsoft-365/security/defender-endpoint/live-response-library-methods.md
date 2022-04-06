---
title: Metoder og egenskaber for Live Response-bibliotek
description: Få mere at vide om, hvordan du bruger metoder og egenskaber for live svarbiblioteket.
keywords: apis, graph api, understøttede API'er, hent, enheder
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
ms.technology: m365d
ms.openlocfilehash: c9eb1de08be8905a41b172a19a33db58dbdc19b9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705495"
---
#  <a name="live-response-library-methods-and-properties"></a>Metoder og egenskaber for Live Response-bibliotek

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** [Microsoft Defender til slutpunkt](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>Metoder

| **Metode**          | **Returtype**         | **Beskrivelse**                         |
|---------------------|-------------------------|-----------------------------------------|
| Listebiblioteksfiler  | Biblioteksfilsamling | Enheder for listebiblioteksfil              |
| Upload til bibliotek   | Biblioteksfilenhed     | Upload en fil til live svarbibliotek |
| Slet fra bibliotek | Intet indhold              | Slet biblioteksfilenhed              |

## <a name="properties"></a>Egenskaber

| **Egenskab** | **Type**                         | **Beskrivelse**                                        |
|--------------|----------------------------------|--------------------------------------------------------|
| Kommandoer     | Live Response-kommandosamling | Matrix med kommandoobjekter. Se [live svarkommandoer](live-response.md#live-response-commands). |

