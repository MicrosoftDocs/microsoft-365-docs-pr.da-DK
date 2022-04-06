---
title: Eksempel på et phishingmailangreb
description: Gennemgå en eksempelanalyse af et phishingangreb.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
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
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 413c4fadcc6de3527643be712713d37a1e2c346c
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501129"
---
# <a name="example-of-a-phishing-email-attack"></a>Eksempel på et phishingmailangreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender kan hjælpe med at registrere skadelige vedhæftede filer leveret via mail. Da [Office 365 Security and Compliance Center](https://protection.office.com/) integreres med Microsoft 365 Defender, kan sikkerhedsanalytikere få indsigt i trusler, der kommer fra Office 365, f.eks. via vedhæftede filer i mails.

En analytiker fik f.eks. tildelt en hændelse i flere faser.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="En hændelse i flere trin" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

På fanen **Beskeder** for hændelsen vises beskeder Defender for Office 365 og Microsoft Defender for Cloud Apps beskeder. Analytikeren kan analysere ned i Defender for Office 365 ved at vælge beskeder om mails. Oplysningerne om beskeden vises i sideruden.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="En mailbesked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
Ved at rulle længere ned vises der flere oplysninger, der viser de skadelige filer og brugere, der blev påvirket.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Bruger og filpåvirkning af en mailbesked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
Når du **vælger siden Åbn besked** , kommer du til den bestemte besked, hvor forskellige oplysninger kan vises mere detaljeret ved at vælge linket. Den faktiske mail kan vises ved at vælge **Vis meddelelser i Stifinder** nederst i panelet.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Oplysninger om en besked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

Dette fører analytikeren til siden Threat Management, hvor mailen Emne, Modtager, Afsender og andre oplysninger vises. **ZAP** under **Specialhandlinger fortæller** analytikeren, at funktionen automatisk tømning uden time blev implementeret. ZAP registrerer og fjerner automatisk skadelige meddelelser og spammeddelelser fra postkasser i hele organisationen. Du kan finde flere oplysninger [under Automatisk tømning uden time (ZAP) i Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Du kan udføre andre handlinger på bestemte meddelelser ved at vælge **Handlinger**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="De andre handlinger, der kan udføre på mails" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>Næste trin

Se den [identitetsbaserede angrebsundersøgelsessti](first-incident-path-identity.md) .

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
