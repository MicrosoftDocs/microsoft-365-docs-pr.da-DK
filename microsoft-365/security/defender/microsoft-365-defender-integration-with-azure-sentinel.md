---
title: Microsoft 365 Defender integration med Microsoft Sentinel
description: Brug Microsoft Sentinel som SIEM for Microsoft 365 Defender hændelser og hændelser.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, computere, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 75aea706cdcb65752b673d32ccff968209ba74b7
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499442"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>Microsoft 365 Defender integration med Microsoft Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Forbindelsen Microsoft 365 Defender Microsoft Sentinel (prøveversion) sender alle Microsoft 365 Defender hændelser og påmindelser til Microsoft Sentinel og holder hændelserne synkroniserede. 

Når du har tilføjet forbindelsen, Microsoft 365 Defender alle tilknyttede beskeder, enheder og relevante oplysninger, der modtages&mdash; fra Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Office 365 og Microsoft Defender for Cloud Apps&mdash; streames til Microsoft Sentinel som sikkerhedsoplysninger og oplysninger om begivenhedsstyring (SIEM), så du får kontekst til at udføre triage- og hændelsesrespons med Microsoft Sentinel. 

Når hændelser er blevet sendt til Microsoft Sentinel, synkroniseres hændelser tovejs med Microsoft 365 Defender, så du kan drage fordel af både Microsoft 365 Defender-portalen og Microsoft Sentinel i Azure Portal til undersøgelse af hændelser og svar.

Se denne korte oversigt over Integration af Microsoft Sentinel med Microsoft 365 Defender (4 minutter).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


Sådan fungerer det.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="Flowet og delingen af hændelsesdata for Microsoft 365 Defender og Microsoft Sentinel-portaler" lightbox="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png":::

## <a name="next-steps"></a>Næste trin

1. Få en dybere forståelse af [Microsoft 365 Defender integration med Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [Forbind data fra Microsoft 365 Defender til Microsoft Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser i Microsoft 365 Defender](incidents-overview.md)
- [Undersøg hændelser med Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases)
