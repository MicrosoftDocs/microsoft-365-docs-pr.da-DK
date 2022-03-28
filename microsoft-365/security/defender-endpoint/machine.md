---
title: Maskinressourcetype
description: Få mere at vide om metoderne og egenskaberne for computerressourcetypen i Microsoft Defender til slutpunkt.
keywords: API'er, understøttede API'er, hent, maskiner
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
ms.openlocfilehash: 80ac3e9ed43de98d32fd14063261452cfd5b1372
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597646"
---
# <a name="machine-resource-type"></a>Maskinressourcetype

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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
|[Liste over maskiner](get-machines.md)|[maskine samling](machine.md)|Listesæt [af maskinenheder](machine.md) i organisationen.|
|[Hent computer](get-machine-by-id.md)|[maskine](machine.md)|Få fat [i en computer](machine.md) ved sin identitet.|
|[Få logget på brugere](get-machine-log-on-users.md)|[brugersamling](user.md)|Få sættet af [Brugere,](user.md) der er logget på [computeren](machine.md).|
|[Få relaterede beskeder](get-machine-related-alerts.md)|[samling af](alerts.md) beskeder|Få sættet af [beskedenheder](alerts.md) , der blev hævet på [computeren](machine.md).|
|[Hent installeret software](get-installed-software.md)|[softwaresamling](software.md)|Henter en samling af installeret software, der er relateret til et bestemt maskin-id.|
|[Få opdagede sårbarheder](get-discovered-vulnerabilities.md)|[indsamling af](vulnerability.md) sikkerhedsrisiko|Henter en samling af opdagede sårbarheder, der er relateret til et givet maskin-id.|
|[Få sikkerhedsanbefalinger](get-security-recommendations.md)|[samling af](recommendation.md) anbefaling|Henter en samling af sikkerhedsanbefalinger, der er relateret til et bestemt maskin-id.|
|[Tilføje eller fjerne computermærker](add-or-remove-machine-tags.md)|[maskine](machine.md)|Tilføje eller fjerne mærket på en bestemt computer.|
|[Find maskiner efter IP](find-machines-by-ip.md)|[maskine samling](machine.md)|Find maskiner, der er set med IP.|
|[Find maskiner efter mærke](find-machines-by-tag.md)|[maskine samling](machine.md)|Find maskiner efter [mærke](machine-tags.md).|
|[Bliv væk fra KBs](get-missing-kbs-machine.md)|KB-samling|Få en liste over manglende KBs, der er knyttet til maskin-id'et|
|[Angiv enhedsværdi](set-device-value.md)|[maskine samling](machine.md)|Angiv [værdien af en enhed](tvm-assign-device-value.md).|
|[Opdater computer](update-machine-method.md)|[maskine samling](machine.md)|Få opdateringsstatus for en computer.|
|

## <a name="properties"></a>Egenskaber

<br>

****

|Egenskab|Type|Beskrivelse|
|---|---|---|
|id|String|[computeridentitet](machine.md) .|
|computerDnsName|String|[fuldt](machine.md) kvalificeret navn.|
|firstSeen|DateTimeOffset|Den første dato og det første klokkeslæt [, hvor](machine.md) maskinen blev observeret af Microsoft Defender for Slutpunkt.|
|lastSeen|DateTimeOffset|Klokkeslæt og dato for hele enhedsrapporten, der er modtaget sidst. En enhed sender typisk en hel rapport én gang i døgnet.|
|osPlatform|String|Operativsystemplatform.|
|onboardingstatus|String|Status for onboarding af maskine. Mulige værdier er: "onboarded" og "offboarded".|
|osProcessor|String|Operativsystemprocessor. Brug i stedet egenskaben osArchitecture.|
|version|String|Version af operativsystem.|
|osBuild|Null-værdi lang|Buildnummer for operativsystem.|
|lastIpAddress|String|Sidste IP på lokal NIC på [computeren](machine.md).|
|lastExternalIpAddress|String|Sidste IP, hvorfra [computeren fik](machine.md) adgang til internettet.|
|healthStatus|Enum|[tilstandsstatus](machine.md) for en computer. Mulige værdier er: "Active", "Inaktiv", "ImpairedCommunication", "NoSensorData", "NoSensorDataImpairedCommunication" og "Unknown".|
|rbacGroupName|String|Computergruppenavn.|
|rbacGroupId|String|Maskingruppe-id.|
|riskScore|Null-værdi Enum|Risikoscore, som evalueres af Microsoft Defender for slutpunkt. De mulige værdier er: 'Ingen', 'Informational', 'Lav', 'Mellem' og 'Høj'.|
|aadDeviceId|Null-gengivelse af Guid|AAD enheds-id (når [computeren er AAD](machine.md) tilsluttet).|
|maskintags|Strengsamling|Sæt af [maskinmærker](machine.md) .|
|eksponeringNiveau|Null-værdi Enum|Eksponeringsniveau, som evalueres af Microsoft Defender for slutpunkt. De mulige værdier er: 'Ingen', 'Lav', 'Mellem' og 'Høj'.|
|deviceValue|Null-værdi Enum|[Enhedens værdi](tvm-assign-device-value.md). De mulige værdier er: 'Normal', 'Lav' og 'Høj'.|
|ipAddresses|IpAddress-samling|Sæt af ***IpAddress-objekter*** . Se [Hent maskiners API](get-machines.md).|
|osArchitecture|String|Operativsystemarkitektur. De mulige værdier er: "32-bit", "64-bit". Brug denne egenskab i stedet for osProcessor.|
|
