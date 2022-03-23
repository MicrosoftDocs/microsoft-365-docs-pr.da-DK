---
title: Produktbemærkninger til Microsoft Defender til Endpoint API
description: Produktbemærkninger for opdateringer af Microsoft Defender til slutpunktssæt af API'er.
keywords: Produktbemærkninger til Microsoft Defender til Endpoint API, mde, API'er, Microsoft Defender til Endpoint API, opdateringer, noter, udgivelse
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
ms.openlocfilehash: 2c34add5968021d6a31bffc80ec16e0ebed9baf0
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591776"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>Produktbemærkninger til Microsoft Defender til Endpoint API

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Følgende oplysninger viser de opdateringer, der er foretaget af Microsoft Defender for Endpoint API'er, og de datoer, de blev foretaget.

> [!TIP]
> RSS-feed: Få besked, når denne side opdateres, ved at kopiere og indsætte følgende URL-adresse i din feedlæser:
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>Produktbemærkninger – nyeste til ældste (dd.mm.yyyy)

### <a name="06102021"></a>06.10.2021

- Vi har tilføjet en ny API-metode til vurdering af eksport – _Vurdering af deltaeksport af softwarerisici (JSON-svar)_ [Eksportér vurderingsmetoder og egenskaber pr. enhed](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- Nye metoder og egenskaber [for vurdering af API-eksporter er blevet tilføjet pr. enhed](get-assessment-methods-properties.md).

### <a name="03052021"></a>03.05.2021

- Ny API tilføjet: [Afhjælpning af aktivitetsmetoder og egenskaber](get-remediation-methods-properties.md).

### <a name="10022021"></a>10.02.2021

- Tilføjet ny API: [Batchopdateringsbeskeder](batch-update-alerts.md).

### <a name="25012021"></a>25.01.2021

- Opdaterede satsbegrænsninger for [Avanceret jagt-API](run-advanced-query-api.md) fra 15 til 45 anmodninger pr. minut.

### <a name="21012021"></a>21.01.2021

- Tilføjet ny API: [Find enheder efter mærke](machine-tags.md).
- Tilføjet ny API: [Importindikatorer](import-ti-indicators.md).

### <a name="03012021"></a>03.01.2021

- Opdaterede beviser for besked: tilføjede ***detectionStatus** _, _*_parentProcessFilePath-_*_ og _ *_parentProcessFileName_**-egenskaber.
- Opdateret [Alert-enhed](alerts.md): tilføjet ***egenskaben id'et*** .

### <a name="15122020"></a>15.12.2020

- Opdateret [enhed](machine.md) enhed: Tilføjede ***IpInterfaces-liste*** . Se [Liste over enheder](get-machines.md).

### <a name="04112020"></a>04.11.2020

- Tilføjet ny API: [Angiv enhedsværdi](set-device-value.md).
- Opdateret [enhed enhed](machine.md) : tilføjet ***enhedsværdi-egenskab*** .

### <a name="01092020"></a>01.09.2020

- Tilføjet mulighed for at udvide objektet Alert med dets relaterede beviser. Se [Listebeskeder](get-alerts.md).
