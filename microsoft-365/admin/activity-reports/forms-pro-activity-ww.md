---
title: Microsoft Dynamics 365 customer voice activity reports
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
description: Få mere at vide om, hvordan du får en Microsoft Dynamics 365 Customer Voice-aktivitetsrapport ved hjælp af dashboardet Rapporter og finder ud af, hvordan licenserede brugere samarbejder.
ms.openlocfilehash: 8f936f2b3232d8086928751c9846a8d762ff8219
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636564"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Microsoft 365 rapporter i Administration – Dynamics 365 Customer Voice-aktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at zoome ind på individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for alle brugere, der har licens til at bruge Microsoft Dynamics 365 Customer Voice, ved at se på deres interaktioner med Dynamics 365 Customer Voice. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af Pro undersøgelser, der er oprettet, og Pro undersøgelser, som brugerne har svaret på. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>Sådan kommer du til aktivitetsrapporten for Dynamics 365 Customer Voice

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på Dynamics 365 Customer Voice-kortet.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Fortolkning af aktivitetsrapporten for Dynamics 365 Customer Voice

Du kan få vist aktiviteterne i Dynamics 365 Customer Voice-rapporten ved at vælge fanen **Aktivitet** .<br/>![Microsoft 365 rapporter – Aktivitetsrapport for Microsoft Dynamics 365 Customer Voice.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Aktivitetsrapport for Dynamics 365 Customer Voice – vælg kolonner.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

**Aktivitetsrapporten for Dynamics 365 Customer Voice** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Mailadressen på den bruger, der udførte aktiviteten på Microsoft Forms.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den seneste dato, hvor en formularaktivitet blev udført af brugeren for det valgte datointerval. Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.<br/>Dette filtrerer tabellen, så der kun vises filaktivitetsdata for de brugere, der udførte aktiviteten på den pågældende dag.  <br/> |
|Antal oprettede undersøgelser  <br/> |Antallet af undersøgelser, som brugeren har oprettet.   <br/> |
|Antal undersøgelsessvar  <br/> |Antallet af svar fra besvarere, som undersøgelsen blev distribueret til.|
|||