---
title: Tilføje dit Google Workspace-domæne
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan du flytter dit domæne fra Google Workspace Microsoft 365 til virksomheder.
ms.openlocfilehash: b41fdf304d0f0b9680f87f40a4564573593d6e75
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63593081"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Føj dit Google Workspace-domæne til Microsoft 365

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Føj dit Google Workspace-domæne Microsoft 365 til virksomheder, så du kan fortsætte med at bruge din virksomhedsmailadresse.

## <a name="try-it"></a>Prøv det!

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. I feltet Microsoft 365 Administration venstre navigation skal du vælge **Vis alle** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
1. Vælg **Tilføj domæne**, angiv dit domænenavn, og vælg **derefter Brug dette domæne**. 
1. Vælg, **Føj en TXT-post til domænerne DNS-poster**, **vælg Fortsæt**, og kopiér TXT-værdien. 
1. Gå tilbage til [Google Admin Console](https://admin.google.com), vælg **Domains**, **Manage domains**, **View Details**, **Manage domain**, **DNS**, og rul derefter ned til **Custom resource records**. 
1. Åbn rullemenuen Posttype, vælg TXT, **indsæt den TXT-værdi**, du kopierede, og vælg derefter **Tilføj**. 

    Opdateringen tager normalt et faktum inden for et par minutter, men det kan tage op til 48 timer. 
1. Gå tilbage til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Administration</a>, vælg **Bekræft**, og klik derefter **på Luk**. 
1. Hvis du vil angive dit domæne som den primære mail for dine brugere, skal du vælge **UsersActive** >  [**users i venstre navigationslinje**](https://go.microsoft.com/fwlink/p/?linkid=834822). 
1. Vælg en bruger, vælg **Administrer brugernavn og mail**, **Rediger**, vælg dit domæne på rullelisten, og vælg derefter **Udført** og **Gem ændringer**. 
1. Gentag denne proces for hver bruger. 

    Når du er færdig, er du klar til at installere Office-apps og overføre dine mails og kalenderelementer for at Microsoft 365. 