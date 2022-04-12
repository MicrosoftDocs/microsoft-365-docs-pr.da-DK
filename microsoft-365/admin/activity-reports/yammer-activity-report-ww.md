---
title: Microsoft 365 Administration Yammer aktivitetsrapporter
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Hent rapporten over Yammer aktivitet, og få mere at vide om antallet af brugere, der bruger Yammer til at poste, f.eks. eller læse en meddelelse.
ms.openlocfilehash: 3ab1f13ec9b7b86bb1a7d858b849f22e687ae8aa
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781287"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-activity-report"></a>Microsoft 365 rapporter i Administration – aktivitetsrapport for Yammer

Som Microsoft 365 administrator viser dashboardet Rapporter data om brugen af produkterne i din organisation. Se [aktivitetsrapporter i Administration](activity-reports.md). Med **rapporten over Yammer aktivitet** kan du forstå niveauet af engagement i din organisation med Yammer ved at se på antallet af unikke brugere, der bruger Yammer til at sende, synes godt om eller læse en meddelelse og mængden af aktivitet, der genereres på tværs af organisationen. 
 
## <a name="how-do-i-get-to-the-yammer-activity-report"></a>Hvordan gør jeg gå til Yammer aktivitetsrapport?

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet Yammer.

  
## <a name="interpret-the-yammer-activity-report"></a>Fortolkning af Yammer aktivitetsrapport

Du kan få vist aktiviteterne i Yammer rapport ved at vælge fanen **Aktivitet**.<br/>![Microsoft 365 rapporter – Microsoft Yammer aktivitetsrapport.](../../media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Yammer aktivitetsrapport – vælg kolonner.](../../media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

Den **Yammer aktivitetsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Brugerens mailadresse. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt. I dette gitter vises de brugere, der er logget på Yammer ved hjælp af den Microsoft 365 konto, eller som er logget på netværket ved hjælp af enkeltlogon. <br/> |
|Vist navn  <br/> |Brugerens fulde navn. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt.  <br/> |
|Brugertilstand  <br/> |En af tre værdier: Aktiveret, Slettet eller Afbrudt. Disse rapporter viser data for aktive, midlertidigt afbrudte og slettede brugere. De afspejler ikke ventende brugere, fordi ventende brugere ikke kan sende, læse eller synes godt om en meddelelse.  <br/> |
|Dato for ændring af tilstand (UTC)  <br/> |Den dato, hvor brugerens tilstand blev ændret i Yammer.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> | Den sidste dato, hvor brugeren oprettede, læste eller syntes godt om en meddelelse.  <br/> |
|Bogført  <br/> |Det antal meddelelser, som brugeren har sendt i den angivne tidsperiode. <br/>|
|Læse  <br/> |Antallet af samtaler, som brugeren har læst i den angivne tidsperiode.  <br/> |
|Kunne lide  <br/> |Det antal meddelelser, som brugeren syntes godt om i den angivne tidsperiode.  <br/>|
|Tildelt produkt  <br/> |De produkter, der er tildelt denne bruger.|
|||