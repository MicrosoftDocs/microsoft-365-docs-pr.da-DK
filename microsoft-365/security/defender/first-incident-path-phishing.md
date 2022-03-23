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
ms.openlocfilehash: 112bfd63a5f3667b22378790b62f3e33fba784d6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592186"
---
# <a name="example-of-a-phishing-email-attack"></a>Eksempel på et phishingmailangreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender kan hjælpe med at registrere skadelige vedhæftede filer leveret via mail. Da [Office 365 Security and Compliance Center](https://protection.office.com/) integreres med Microsoft 365 Defender, kan sikkerhedsanalytikere få indsigt i trusler, der kommer fra Office 365, f.eks. via vedhæftede filer i mails.

En analytiker fik f.eks. tildelt en hændelse i flere faser.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Eksempel på en hændelse i flere trin."::: 

På fanen **Beskeder** for hændelsen vises beskeder fra Defender Office 365 og Microsoft Defender til skyapps. Analytikeren kan analysere ned i Defender for Office 365 vigtige beskeder ved at vælge beskeder om mails. Oplysningerne om beskeden vises i sideruden.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="Eksempel på en mailbesked.":::
 
Ved at rulle længere ned vises der flere oplysninger, der viser de skadelige filer og brugere, der blev påvirket.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Eksempel på bruger- og filpåvirkning af en mailbesked.":::
  
Når du **vælger siden Åbn besked** , kommer du til den bestemte besked, hvor forskellige oplysninger kan vises mere detaljeret ved at vælge linket. Den faktiske mail kan vises ved at vælge **Vis meddelelser i Stifinder** nederst i panelet.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Eksempel på oplysninger om en besked."::: 

Dette fører analytikeren til siden Threat Management, hvor mailen Emne, Modtager, Afsender og andre oplysninger vises. **ZAP** under **Specialhandlinger fortæller** analytikeren, at funktionen automatisk tømning uden time blev implementeret. ZAP registrerer og fjerner automatisk skadelige meddelelser og spammeddelelser fra postkasser i hele organisationen. Du kan finde flere oplysninger [under Automatisk tømning uden time (ZAP) i Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Du kan udføre andre handlinger på bestemte meddelelser ved at vælge **Handlinger**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="Eksempel på de andre handlinger, der kan udføre på mails."::: 

## <a name="next-step"></a>Næste trin

Se den [identitetsbaserede angrebsundersøgelsessti](first-incident-path-identity.md) .

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
