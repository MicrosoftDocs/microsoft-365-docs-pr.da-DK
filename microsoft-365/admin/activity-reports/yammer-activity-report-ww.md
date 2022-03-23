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
description: Få rapporten Yammer Aktivitet, og få mere at vide om antallet af brugere, der bruger Yammer til at skrive, synes godt om eller læse en meddelelse.
ms.openlocfilehash: e5e865266d09d839777ed00feddf3682a24b6e7e
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591712"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-activity-report"></a>Microsoft 365 Rapporter i Administration – Yammer aktivitetsrapport

Som Microsoft 365 administrator viser dashboardet Rapporter data om brugen af produkterne i din organisation. Se [aktivitetsrapporter i Administration](activity-reports.md). Med **rapporten Yammer Activity** kan du forstå graden af engagement i din organisation med Yammer ved at se på antallet af unikke brugere, der bruger Yammer til at skrive, synes godt om eller læse en meddelelse og mængden af aktivitet, der genereres på tværs af organisationen. 
 
## <a name="how-do-i-get-to-the-yammer-activity-report"></a>Hvordan finder jeg rapporten Yammer aktivitet?

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på Yammer visitkort.

  
## <a name="interpret-the-yammer-activity-report"></a>Fortolk Yammer aktivitetsrapport

Du kan få vist aktiviteterne i Yammer rapporten ved at vælge **fanen** Aktivitet.<br/>![Microsoft 365 - Microsoft Yammer aktivitetsrapport.](../../media/9b251183-c2b3-430c-ab2d-58bf11e7e3ae.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Yammer aktivitetsrapport – vælg kolonner.](../../media/7ef6351d-f7e9-4504-913d-2c2df9062bf6.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **Yammer kan** du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|Brugernavn  <br/> |Brugerens mailadresse. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt. Dette gitter viser brugere, som Yammer loggede på med Microsoft 365, eller som loggede på netværket med enkeltlog på. <br/> |
|Vist navn  <br/> |Brugerens fulde navn. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt.  <br/> |
|Brugertilstand  <br/> |En af tre værdier: Aktiveret, slettet eller afbrudt. Disse rapporter viser data for aktive, afbrudte og slettede brugere. De afspejler ikke afventende brugere, fordi afventende brugere ikke kan sende, læse eller synes godt om en meddelelse.  <br/> |
|Dato for ændring af tilstand (UTC)  <br/> |Den dato, hvor brugerens tilstand blev ændret i Yammer.  <br/> |
|Dato for seneste aktivitet (UTC)  <br/> | Den seneste dato, hvor brugeren har opslået, læst eller syntes godt om en meddelelse.  <br/> |
|Opslået  <br/> |Antallet af meddelelser, brugeren har sendt i den periode, du angav. <br/>|
|Læs  <br/> |Antallet af samtaler, brugeren har læst i den periode, du har angivet.  <br/> |
|Synes godt om  <br/> |Antallet af meddelelser, brugeren har syntes godt om i den periode, du angav.  <br/>|
|Tildelt produkt  <br/> |De produkter, der er tildelt denne bruger.|
|||