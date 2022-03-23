---
title: Anbefalingsmetoder og -egenskaber
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
ms.openlocfilehash: f6e8295d83d5ab6fb86726903800d2779f394836
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592861"
---
# <a name="recommendation-resource-type"></a>Ressourcetypen Anbefaling

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>Metoder

<br>

****

|Metode|Returtype|Beskrivelse|
|---|---|---|
|[Vis alle anbefalinger](get-all-recommendations.md)|Samling af anbefaling|Henter en liste over alle sikkerhedsanbefalinger, der påvirker organisationen|
|[Få anbefaling efter id](get-recommendation-by-id.md)|Anbefaling|Henter en sikkerhedsanbefaling ud fra dens id|
|[Hent anbefalingssoftware](list-recommendation-software.md)|[Software](software.md)|Henter en sikkerhedsanbefaling, der er relateret til en bestemt software|
|[Få anbefalingsenheder](get-recommendation-machines.md)|MachineRef-samling|Henter en liste over enheder, der er knyttet til sikkerhedsanbefalingen|
|[Få sårbarheder, der er anbefaling om](get-recommendation-vulnerabilities.md)|[Samling af sikkerhedsrisikoe](vulnerability.md)|Henter en liste over sårbarheder, der er knyttet til sikkerhedsanbefalingen|
|

## <a name="properties"></a>Egenskaber

<br>

****

|Egenskab|Type|Beskrivelse|
|---|---|---|
|id|String|Anbefalings-id|
|productName|String|Relateret softwarenavn|
|anbefalingNavn|String|Navn på anbefaling|
|Fliser|Lang|Antal opdagede sårbarheder|
|Leverandør|String|Relateret leverandørnavn|
|recommendedVersion|String|Anbefalet version|
|recommendedProgram|String|Anbefalet program|
|anbefaletVenlighed|String|Anbefalet leverandør|
|anbefalingCategory|String|Kategorien Anbefaling. Mulige værdier er: "Konti", "Application", "Network", "OS", "SecurityControls"|
|underkategori|String|Underordnet kategori på anbefaling|
|alvorlighedScore|Dobbelt|Potentiel indvirkning af konfigurationen på organisationens Microsoft Secure Score for enheder (1-10)|
|publicExploit|Boolesk |Offentlig udnyttelse er tilgængelig|
|activeAlert|Boolesk |Aktiv besked er knyttet til denne anbefaling|
|associatedThreats|Strengsamling|Rapporten Trusselsanalyse er knyttet til denne anbefaling|
|remediationType|String|Afhjælpningstype. De mulige værdier er: "ConfigurationChange","Update","Upgrade","Uninstall"|
|Status|Enum|Status for anbefalingsundtagelse. De mulige værdier er: "Aktiv" og "Undtagelse"|
|configScoreImpact|Dobbelt|Microsoft Secure Score for devices impact|
|exposureImpact|Dobbelt|Eksponeringsscore|
|totalMachineCount|Lang|Antal installerede enheder|
|exposedMachinesCount|Lang|Antal installerede enheder, der er eksponeret for sårbarheder|
|nonProductivityImpactedAssets|Lang|Antal enheder, der ikke er påvirket|
|relatedComponent|String|Relateret softwarekomponent|
|
