---
title: Finjustere ydeevnen Exchange Online finjustere ydeevnen
ms.author: krowley
author: tracyp
manager: laurawi
ms.date: 12/14/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.assetid: 026e83cb-a945-4543-97b0-a8af6e80ac61
description: Denne artikel indeholder generelle tip og links til andre ressourcer, der fortæller dig, hvordan du forbedrer ydeevnen for Exchange Online.
ms.openlocfilehash: 5feb704a1da83ef93ebc3bbe72fb12c7f0c54574
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601607"
---
# <a name="tune-exchange-online-performance"></a>Finjustere ydeevnen Exchange Online finjustere ydeevnen

Denne artikel indeholder generelle tip og links til andre ressourcer, der fortæller dig, hvordan du forbedrer ydeevnen for Exchange Online, især foran en overførsel. Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md) projekt.
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Ting, du skal overveje for at forbedre Exchange Online ydeevnen

For at forbedre hastigheden af overførslen og reducere organisationens båndbreddebegrænsninger for Exchange Online skal du overveje følgende:
  
- **Reducer postkassestørrelser.** Mindre postkassestørrelser forbedrer overførselshastigheden. 
    
- **Brug flyttefunktionerne for postkassen sammen Exchange en hybridinstallation.** Med en Exchange hybridinstallation, offlinemail (i form af . OST-filer) kræver ikke genoverførsel, når du overfører til Exchange Online. Dette reducerer kravene til båndbredden betydeligt. 
    
- **Planlæg postkassebevægelser til at foregå i perioder med lav internettrafik og lav lokal Exchange brug.** Når du planlægger overførslen, sendes overførselsanmodninger til postkassens replikeringsproxy og overførslen finder muligvis ikke sted med det samme. 
    
- **Brug lean popouts til Outlook på internettet.** Lean popouts giver en mindre version af bestemte meddelelser i Microsoft Edge eller Internet Explorer, der bruger mindre hukommelse, ved at gengive visse komponenter på serveren. Få mere at vide under [Brug lean popouts til at reducere hukommelsesbrug, når du læser mails](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Generelle råd

- Kontrollér, at DNS-opslag for outlook.office.com angiver MS-datacenteret på en logisk postplacering for din placering.

- Cachelagring af postkasse til undersøgelse, og vælg de relevante indstillinger (gen. cachelagringsperiode, cachelagring af delt postkasse osv.).

- Sørg for Outlook dine data ikke videregiver VPN-forbindelser (til et centralt kontor), før de går via internettet.

- Sørg for, at dine postkassedata overholder begrænsningerne for mappe, element, beløb.
    
Du kan finde flere oplysninger Exchange af [overførselsydeevnen Office 365 bedste fremgangsmåder for overførsel](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
