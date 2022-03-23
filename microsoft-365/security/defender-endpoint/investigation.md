---
title: Undersøgelsesressourcetype
description: Microsoft Defender for endpoint Investigation entity.
keywords: API'er, graph api, understøttede API'er, hent, vigtige beskeder, undersøgelser
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1749404942b42778ecde99417a8e3501c7c4f4cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592020"
---
# <a name="investigation-resource-type"></a>Undersøgelsesressourcetype

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

Repræsenterer en automatiseret undersøgelsesenhed i Defender for Slutpunkt.

Få mere at vide under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

## <a name="methods"></a>Metoder

Metode|Returtype|Beskrivelse
:---|:---|:---
[Listeundersøgelse](get-investigation-collection.md)|Undersøgelsessamling|Få en undersøgelsessamling
[Få en enkelt undersøgelse](get-investigation-object.md)|Undersøgelsesenhed|Får én undersøgelsesenhed.
[Start undersøgelse](initiate-autoir-investigation.md)|Undersøgelsesenhed|Starter undersøgelsen på en enhed.

## <a name="properties"></a>Egenskaber

Egenskab|Type|Beskrivelse
:---|:---|:---
Id|String|Identiteten af den undersøgende enhed. 
startTime|DateTime Nullable|Dato og klokkeslæt for oprettelse af undersøgelsen.
endTime|DateTime Nullable|Dato og klokkeslæt for, hvornår undersøgelsen blev afsluttet.
annulleretAf|String|Id'et for den bruger/det program, der annullerede undersøgelsen.
Stat|Enum|Undersøgelsens aktuelle status. Mulige værdier er: 'Ukendt', 'Afsluttet', 'Behæftet', 'Benign', 'Failed', 'PartiallyRemedated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyInvestigated', 'TerminatedByUser', 'TerminatedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'suppressedAlert'.
statusDetails|String|Yderligere oplysninger om tilstanden i undersøgelsen.
machineId|String|Id'et for den enhed, som undersøgelsen udføres på.
computerDnsName|String|Navnet på den enhed, som undersøgelsen udføres på.
triggeringAlertId|String|Id'et for den besked, der udløste undersøgelsen.

## <a name="json-representation"></a>Json-repræsentation

```json
{
    "id": "63004",
    "startTime": "2020-01-06T13:05:15Z",
    "endTime": null,
    "state": "Running",
    "cancelledBy": null,
    "statusDetails": null,
    "machineId": "e828a0624ed33f919db541065190d2f75e50a071",
    "computerDnsName": "desktop-test123",
    "triggeringAlertId": "da637139127150012465_1011995739"
}
```
