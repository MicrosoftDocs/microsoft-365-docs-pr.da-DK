---
title: Brug følsomhedsmærkater som betingelser i DLP-politikker
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om de tjenester og elementtyper, du kan bruge følsomhedsmærkater som betingelser i DLP-politikker
ms.openlocfilehash: 55803a2c354890264f99753af2aa6337cf49182a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632393"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>Brug følsomhedsmærkater som betingelser i DLP-politikker

Du kan bruge [følsomhedsmærkater](sensitivity-labels.md) som en betingelse i DLP-politikker for disse placeringer:

- Exchange Online mails
- SharePoint Online
- OneDrive for Business websteder
- Windows 10 enheder

Følsomhedsmærkater vises som en indstilling på listen **Indhold indeholder** .

> [!div class="mx-imgBorder"]
> ![følsomhedsmærkat som en betingelse.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **Følsomhedsmærkater** som en betingelse vil ikke være tilgængelige, hvis du har valgt **Teams-chat og kanalmeddelelser** som en placering til at anvende DLP-politikken.


## <a name="supported-items-scenarios-and-policy-tips"></a>Understøttede elementer, scenarier og politiktip

Du kan bruge følsomhedsmærkater som betingelser for disse elementer og i disse scenarier.

### <a name="supported-items"></a>Understøttede elementer

|Tjeneste  |Elementtype  |Tilgængelig for politiktip  |Eksigibel  |
|---------|---------|---------|---------|
|Exchange    |mailmeddelelse         |Ja         |Ja         |
|Exchange    |vedhæftet fil         |Nej         |Ja *         |
|SharePoint Online     |elementer i SharePoint Online         |Ja         |Ja         |
|OneDrive for Business     |Elementer         |Ja         |Ja         |
|Teams     |Teams- og kanalmeddelelser         |ikke tilgængelig         |ikke tilgængelig         |
|Teams     |Vedhæftede filer         |ja **         |ja **         |
|Windows 10 enheder     |Elementer         |Ja         |Ja         |
|MCAS (prøveversion) |Elementer         |Ja         |Ja         |

\* DLP-registrering af følsomhedsmærkater for vedhæftede filer i mails understøttes kun for Open XML-baserede Office-filtyper.

\** Vedhæftede filer, der sendes i Teams over 1:1 chat eller kanaler, uploades automatisk til OneDrive for Business og SharePoint. Så hvis SharePoint Online eller OneDrive for Business er inkluderet som placeringer i din DLP-politik, medtages navngivne vedhæftede filer, der sendes i Teams, automatisk i omfanget af denne betingelse. Teams som en placering behøver ikke at blive valgt i DLP-politikken.

> [!NOTE]
> DLP's mulighed for at registrere følsomhedsmærkater i SharePoint og OneDrive for business er begrænset. Du kan finde flere oplysninger under [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Understøttede scenarier

- DLP-Administration kan se en liste over alle følsomhedsmærkater i lejeren, når de vælger at inkludere en eller flere følsomhedsmærkater som en betingelse.

- Brug af følsomhedsmærkater som en betingelse understøttes på tværs af alle arbejdsbelastninger som angivet i supportmatrixen ovenfor.

- Tip til DLP-politikker vises fortsat på tværs af arbejdsbelastninger (undtagen Outlook Win32) for DLP-politikker, der indeholder følsomhedsmærkat som en betingelse.

- Følsomhedsmærkater vises også som en del af mailen med hændelsesrapporten, hvis der matches en DLP-politik med følsomhedsmærkat som en betingelse.

- Detaljer om følsomhedsmærkaten vises også i overvågningsloggen for DLP-reglens match for et DLP-politikmatch, der indeholder følsomhedsmærkat som en betingelse.


### <a name="support-policy-tips"></a>Tip til supportpolitik


|Arbejdsbyrde  |Politiktip understøttes/understøttes ikke  |
|---------|---------|
|OWA |    Understøttes     |
|Outlook Win 32    |  understøttes ikke       |
|SharePoint   |   Understøttes      |
|OneDrive for Business    |    Understøttes     |
|slutpunktsenheder   |  understøttes ikke       |
