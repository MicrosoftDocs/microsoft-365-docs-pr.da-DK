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
ms.openlocfilehash: 1117471e38b430f1d7289c6aae76994ac5acd494
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63594331"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>Brug følsomhedsmærkater som betingelser i DLP-politikker

Du kan bruge [følsomhedsmærkater](sensitivity-labels.md) som en betingelse i DLP-politikker for disse placeringer:

- Exchange Online mails
- SharePoint Online
- OneDrive for Business websteder
- Windows 10 enheder

Følsomhedsmærkater vises som en indstilling på **listen Indhold** indeholder.

> [!div class="mx-imgBorder"]
> ![følsomhedsmærkat som en betingelse.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **FølsomhedSetiketter** som en betingelse er ikke tilgængelige, hvis du har **valgt at Teams chat og kanalmeddelelser** som en placering til at anvende DLP-politikken.


## <a name="supported-items-scenarios-and-policy-tips"></a>Understøttede elementer, scenarier og politiktip

Du kan bruge følsomhedsmærkater som betingelser for disse elementer og i disse scenarier.

### <a name="supported-items"></a>Understøttede elementer

|Tjeneste  |Elementtype  |Tilgængelig for politiktip  |Kan håndhæves  |
|---------|---------|---------|---------|
|Exchange    |mail         |Ja         |Ja         |
|Exchange    |vedhæftet fil i mail         |Nej         |ja *         |
|SharePoint Online     |elementer i SharePoint Online         |Ja         |Ja         |
|OneDrive for Business     |elementer         |Ja         |Ja         |
|Teams     |Teams og kanalmeddelelser         |ikke tilgængelig         |ikke tilgængelig         |
|Teams     |vedhæftede filer         |ja **         |ja **         |
|Windows 10 enheder     |elementer         |Ja         |Ja         |
|MCAS (preview) |elementer         |Ja         |Ja         |

\*DLP-registrering af følsomhedsmærkater for vedhæftede filer i mails understøttes Office alle filtyper.

\** Vedhæftede filer, der Teams via 1:1 chat eller kanaler, uploades automatisk til OneDrive for Business og SharePoint. Så hvis SharePoint Online eller OneDrive for Business er inkluderet som placeringer i din DLP-politik, medtages etiketterede vedhæftede filer, der er sendt i Teams, automatisk i omfanget af denne betingelse. Teams som en placering behøver ikke at være valgt i DLP-politikken.

> [!NOTE]
> DLP's mulighed for at registrere følsomhedsmærkater i SharePoint og OneDrive til virksomheder er begrænset. Få mere at vide under [Aktivér følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Understøttede scenarier

- DLP-administratoren vil kunne se en liste over alle følsomhedsmærkater i lejeren, når de vælger at medtage en eller flere følsomhedsmærkater som en betingelse.

- Brug af følsomhedsetiketter som en betingelse understøttes på tværs af alle arbejdsbelastninger som angivet i supportmatrixen ovenfor.

- Tips til DLP-politik vil fortsat blive vist på tværs af arbejdsbelastninger (undtagen Outlook Win32) for DLP-politikker, der indeholder følsomhedsmærkat som en betingelse.

- Følsomhedsmærkater vises også som en del af mailen med hændelsesrapporten, hvis en DLP-politik med følsomhedsmærkat som en betingelse er matchet.

- Oplysninger om følsomhedsmærkat vises også i DLP-reglens overvågningslog for match til DLP-politik, der indeholder følsomhedsmærkat som en betingelse.


### <a name="support-policy-tips"></a>Tip til supportpolitik


|Arbejdsbelastning  |Politiktip understøttes/understøttes ikke  |
|---------|---------|
|OWA |    understøttet     |
|Outlook Win 32    |  understøttes ikke       |
|SharePoint   |   understøttet      |
|OneDrive for Business    |    understøttet     |
|slutpunktsenheder   |  understøttes ikke       |
