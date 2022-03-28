---
title: Softwaremetoder og -egenskaber
description: Henter de seneste vigtige beskeder.
keywords: apis, graph api, understøttede API'er, hent, beskeder, seneste
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6b08b7c4ebb0a818dec5bdf799c3114d91764259
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597608"
---
# <a name="software-resource-type"></a>Ressourcetype for software

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

<br>

****

|Metode|Returtype|Beskrivelse|
|---|---|---|
|[Listesoftware](get-software.md)|Samling af software|Opliste organisationens softwarelager|
|[Hent software efter id](get-software-by-id.md)|Software|Hent en bestemt software ved hjælp af dens software-id|
|[Liste over softwareversionsdistribution](get-software-ver-distribution.md)|Distributionssamling|Liste over softwareversionsdistribution efter software-id|
|[Liste over maskiner efter software](get-machines-by-software.md)|MachineRef-samling|Hente en liste over enheder, der er knyttet til software-id'et|
|[Opliste sårbarheder efter software](get-vuln-by-software.md)|[Samling af sikkerhedsrisikoe](vulnerability.md)|Hent en liste over sårbarheder, der er knyttet til software-id'et|
|[Bliv væk fra KBs](get-missing-kbs-software.md)|KB-samling|Få en liste over manglende KBs, der er knyttet til software-id'et|
|

## <a name="properties"></a>Egenskaber

<br>

****

|Egenskab|Type|Beskrivelse|
|---|---|---|
|id|String|Software-id|
|Navn|String|Softwarenavn|
|Leverandør|String|Navn på softwareudgiver|
|Fliser|Lang|Antal opdagede sårbarheder|
|publicExploit|Boolesk |Offentlig udnyttelse findes til nogle af sårbarhederne|
|activeAlert|Boolesk |Aktiv besked er knyttet til denne software|
|exposedMachines|Lang|Antal blotlagte enheder|
|impactScore|Dobbelt|Effekten af eksponeringsscore fra denne software|
|
