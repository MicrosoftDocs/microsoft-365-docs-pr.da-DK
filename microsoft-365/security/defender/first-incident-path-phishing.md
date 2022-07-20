---
title: Eksempel på et phishing-mailangreb
description: Gennemgå et eksempel på en analyse af et phishing-angreb.
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: dcf620cfaeb1d33665538d16d080e72745b96e42
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66892902"
---
# <a name="example-of-a-phishing-email-attack"></a>Eksempel på et phishing-mailangreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender kan hjælpe med at registrere skadelige vedhæftede filer, der leveres via mail. Da [Office 365 Security and Compliance Center](https://protection.office.com/) kan integreres med Microsoft 365 Defender, kan sikkerhedsanalytikere have synlighed over trusler, der kommer ind fra Office 365, f.eks. via vedhæftede filer i mails.

En analytiker blev f.eks. tildelt en hændelse med flere faser.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="En hændelse med flere faser" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

Under fanen **Beskeder** i hændelsen vises beskeder fra Defender for Office 365 og Microsoft Defender for Cloud Apps. Analytikeren kan foretage detailudledning i Defender for Office 365 beskeder ved at vælge beskederne i mailmeddelelserne. Oplysningerne om beskeden vises i sideruden.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="En mailbesked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
Når du ruller længere ned, vises der flere oplysninger, der viser de skadelige filer og den bruger, der blev påvirket.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Bruger- og filpåvirkning af en mailbesked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
Hvis du vælger **Åbn beskedside** , kommer du til den specifikke besked, hvor forskellige oplysninger kan vises mere detaljeret, ved at vælge linket. Du kan få vist den faktiske mail ved at vælge **Vis meddelelser i Stifinder** nederst i panelet.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Oplysningerne om en besked" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

Dette fører analytikeren til siden Threat Management, hvor mailemnet, modtageren, afsenderen og andre oplysninger vises. **ZAP** under **Særlige handlinger** fortæller analytikeren, at funktionen Automatisk sletning på nul timer blev implementeret. ZAP registrerer og fjerner automatisk skadelige meddelelser og spam-meddelelser fra postkasser på tværs af organisationen. Du kan få flere oplysninger [under Zap (automatisk tøm på nul timer) i Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Andre handlinger kan udføres på bestemte meddelelser ved at vælge **Handlinger**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="De andre handlinger, der kan udføres på mails" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>Næste trin

Se den [identitetsbaserede](first-incident-path-identity.md) angrebsundersøgelsessti.

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
