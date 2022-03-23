---
title: Indikatorressourcetype
description: Angiv enhedsoplysningerne, og definer udløb af indikatoren ved hjælp af Microsoft Defender til slutpunkt.
keywords: apis, understøttede api'er, hent, TiIndicator, Indikator, seneste
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
ms.openlocfilehash: 8e8660574f65d614bacfe705d7fad19e39d501a6
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591228"
---
# <a name="indicator-resource-type"></a>Indikatorressourcetype

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- Se den tilsvarende [side](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) Symboler i portalen.

Metode|Returtype|Beskrivelse
:---|:---|:---
[Listeindikatorer](get-ti-indicators-collection.md)|[Indikator](ti-indicator.md) Samling|Enheder [for](ti-indicator.md) listeindikator.
[Indsend-indikator](post-ti-indicator.md)|[Indikator](ti-indicator.md)|Submit or update [Indicator](ti-indicator.md) entity.
[Importér indikatorer](import-ti-indicators.md)|[Indikator](ti-indicator.md) Samling|Send eller [opdater enheder](ti-indicator.md) for indikatorer.
[Indikator for sletning](delete-ti-indicator-by-id.md)|Intet indhold|Deletes [Indicator-enhed](ti-indicator.md) .

## <a name="properties"></a>Egenskaber

Egenskab|Type|Beskrivelse
:---|:---|:---
id|String|Identiteten på [indikatorobjektet](ti-indicator.md) .
indicatorValue|String|Værdien af [indikatoren](ti-indicator.md).
indicatorType|Enum|Type af indikatoren. De mulige værdier er: "FileSha1", "FileSha256", "FileMd5", "CertificateThumbprint", "IpAddress", "DomainName" og "URL".
program|String|Det program, der er knyttet til indikatoren.
handling|Enum|Den handling, der skal anvendes, hvis indikatoren findes i organisationen. Mulige værdier er: "Advar", "Bloker", "Overvågning", "Påmindelse", "AlertAndBlock", "BlockAndRemediate" og "Allowed".
|externalID|String|Id, som kunden kan sende i anmodningen om brugerdefineret korrelation.|
sourceType|Enum|"Bruger" i tilfælde af at indikatoren blev oprettet af en bruger (f.eks. fra portalen), "AadApp", hvis den blev sendt via automatiseret program via API'en.
createdBySource|streng|Navnet på den bruger/det program, der sendte indikatoren.
createdBy|String|Entydig identitet for den bruger/det program, der sendte indikatoren.
lastUpdatedBy|String|Identiteten på den bruger/det program, der senest har opdateret indikatoren.
creationTimeDateTimeUtc|DateTimeOffset|Dato og klokkeslæt for oprettelse af indikatoren.
expirationTime|DateTimeOffset|Indikatorens udløbstidspunkt.
lastUpdateTime|DateTimeOffset|Sidste gang indikatoren blev opdateret.
alvorsgrad|Enum|Alvorsgrad for indikatoren. mulige værdier er: "Informational", "Lav", "Mellem" og "Høj".
titel|String|Indikatortitel.
beskrivelse|String|Beskrivelse af indikatoren.
recommendedActions|String|Anbefalede handlinger for indikatoren.
rbacGroupNames|Liste over strenge|RBAC-enhedsgruppenavne, hvor indikatoren vises og er aktiv. Tom liste i tilfælde af, at den vises på alle enheder.
rbacGroupIds|Liste over strenge|RBAC-enhedsgruppe-id'et er der, hvor indikatoren vises og er aktiv. Tom liste i tilfælde af, at den vises på alle enheder.
generateAlert|Enum|**Sand** , hvis generering af beskeder er **påkrævet, Falsk** , hvis denne indikator ikke bør generere en besked.

## <a name="indicator-types"></a>Indikatortyper

De indikatorhandlingstyper, der understøttes af API'en, er:

- Tilladt
- Overvågning
- Bloker
- BlokerOgRemediate
- Advar (kun Defender til skyapps)

Du kan finde flere oplysninger om beskrivelsen af svarhandlingstyper i [Opret indikatorer](manage-indicators.md).

> [!Note]
>
> Tidligere svarhandlinger (AlertAndBlock og Alert) understøttes indtil januar 2022. Efter denne dato skal alle kunder bruge en af de handlingstyper, der er angivet ovenfor.

## <a name="json-representation"></a>Json-repræsentation

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
