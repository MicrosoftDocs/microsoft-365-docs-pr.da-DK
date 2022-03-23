---
title: Microsoft 365 Administration Yammer rapporter over brug af enheder
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
description: Få oplysninger Yammer om, hvilke enheder dine brugere bruger og Yammer på.
ms.openlocfilehash: fc59060cc4ec0ad3d34aae2b165bcb36ee1aee89
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590682"
---
# <a name="microsoft-365-reports-in-the-admin-center---yammer-device-usage-report"></a>Microsoft 365 Rapporter i Administration – rapport over Yammer brug af enhed

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).
  
Rapporterne Yammer brug af enheder giver dig oplysninger om, hvilke enheder dine brugere bruger Yammer på. Du kan få vist antallet af daglige brugere efter enhedstype og antallet af brugere efter enhedstype. Du kan få vist begge over en udvalgt tidsperiode. Du kan også få vist detaljer pr. bruger.
 
## <a name="how-do-i-get-to-the-yammer-device-usage-report"></a>Hvordan finder jeg rapporten over Yammer brug af enhed?

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på Yammer visitkort.
  
## <a name="interpret-the-yammer-device-usage-report"></a>Fortolk Yammer rapport over brug af enhed

Du kan få vist brugen i OneDrive rapport ved at vælge **fanen Enhedsforbrug**.<br/>![Microsoft 365 rapporter – Microsoft Yammer rapport over brug af enheder.](../../media/e21af4c0-0ad2-4485-8ab1-2f82d7dfa90e.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Yammer rapport over brug af enhed – vælg kolonner.](../../media/fc1fc8db-e197-4878-85c7-7ba0d67b9379.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **Yammer om** brug af enheder kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|Brugernavn  <br/> |Brugerens mailadresse. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt. Dette gitter viser brugere, som Yammer loggede på med Microsoft 365, eller som loggede på netværket med enkeltlog på. <br/> |
|Vist navn  <br/> |Brugerens fulde navn. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt.  <br/> |
|Brugertilstand  <br/> |En af tre værdier: Aktiv, Slettet eller Afbrudt. Disse rapporter viser data for aktive, afbrudte og slettede brugere. De afspejler ikke afventende brugere, fordi afventende brugere ikke kan sende, læse eller synes godt om en meddelelse.   <br/> |
|Dato for ændring af tilstand (UTC)  <br/> |Den dato, hvor brugerens tilstand blev ændret i Yammer.  <br/> |
|Dato for seneste aktivitet (UTC)  <br/> |Den sidste dato (UTC), som brugeren har deltaget i en Yammer aktivitet.  <br/> |
|Web  <br/> |Angiver, om brugeren har Yammer på internettet.  <br/> |
|Windows telefon  <br/> | Angiver, om brugeren har brugt Yammer på en Windows telefon.  <br/> |
|Android-telefon  <br/> |Angiver, om brugeren har brugt Yammer på en Android-telefon. <br/>|
|iphone <br/> | Angiver, om brugeren har brugt Yammer på en iPhone.  <br/> |
|ipad  <br/> |Angiver, om brugeren har brugt Yammer på en iPad. <br/>|
|andet  <br/> |Angiver, om brugeren har brugt en Yammer en anden enhed, der ikke er angivet tidligere. <br/>|
|||