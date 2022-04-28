---
title: Finjuster ydeevnen i Exchange Online
ms.author: krowley
author: tracyp
manager: scotv
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
description: Denne artikel indeholder generelle tip og links til andre ressourcer, der fortæller dig, hvordan du kan forbedre ydeevnen af Exchange Online.
ms.openlocfilehash: 3b048db5e3ea5090ce5ed2391269f8167c459538
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092023"
---
# <a name="tune-exchange-online-performance"></a>Finjuster ydeevnen i Exchange Online

Denne artikel indeholder generelle tip og links til andre ressourcer, der fortæller dig, hvordan du kan forbedre ydeevnen af Exchange Online, især foran en migrering. Denne artikel er en del af [projektet Netværksplanlægning og justering af ydeevne for Office 365](./network-planning-and-performance.md).
   
## <a name="things-to-consider-in-order-to-improve-exchange-online-performance"></a>Ting, du skal overveje for at forbedre ydeevnen Exchange Online

Hvis du vil forbedre migreringshastigheden og reducere din organisations båndbreddebegrænsninger for Exchange Online, skal du overveje følgende:
  
- **Reducer størrelsen på postkasser.** Størrelsen på mindre postkasser forbedrer overførselshastigheden. 
    
- **Brug flyttefunktionerne i postkassen med en Exchange hybridinstallation.** Med en Exchange hybridinstallation, offlinemails (i form af . OST-filer) kræver ikke download igen, når der migreres til Exchange Online. Dette reducerer kravene til downloadbåndbredde markant. 
    
- **Planlæg, at postkassen flyttes i perioder med lav internettrafik og lav lokal Exchange brug.** Når du planlægger flytninger, sendes overflytningsanmodninger til postkassereplikeringsproxyen og finder muligvis ikke sted med det samme. 
    
- **Brug lean popouts til Outlook på internettet.** Lean popouts leverer mindre, mindre hukommelseskrævende versioner af visse mails i Microsoft Edge eller Internet Explorer ved at gengive nogle komponenter på serveren. Du kan få flere oplysninger under [Brug lean-popouts til at reducere den hukommelse, der bruges ved læsning af mails](https://support.office.com/article/a6d6ba01-2562-4c3d-a8f1-78748dd506cf).


## <a name="general-advice"></a>Generelle råd

- Sørg for, at DNS-opslag for outlook.office.com indtaster MS-datacenteret på en logisk indtastningsplacering for din placering.

- Cachelagring af opslagspostkasser, og vælg de relevante indstillinger (re. cachelagringsperiode, cachelagring af delte postkasser et cetera).

- Sørg for, at dine Outlook data ikke overføres via VPN-forbindelser (til et centralt kontor), før de overføres via internettet.

- Sørg for, at postkassedataene overholder begrænsningerne for beløb for mapper og elementer.
    
Du kan få flere oplysninger om Exchange overførselsydeevne [under Office 365 overførselsydeevne og bedste fremgangsmåder](https://support.office.com/article/d9acb371-fd6c-4c14-aa8e-db5cbe39aa57).
