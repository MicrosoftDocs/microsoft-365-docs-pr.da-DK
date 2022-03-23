---
title: Kunders stemmeaktivitetsrapporter for Microsoft Dynamics 365
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
description: Få mere at vide om, hvordan du får en Microsoft Dynamics 365 Customer Voice-aktivitetsrapport ved hjælp Microsoft 365 dashboardet Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: fb3f631db84dbd974123863956d5505f02c382d6
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590696"
---
# <a name="microsoft-365-reports-in-the-admin-center---dynamics-365-customer-voice-activity"></a>Microsoft 365 Rapporter i Administration – Dynamics 365 Customer Voice-aktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det giver dig mulighed for at analysere individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for hver bruger, der har licens til at bruge Microsoft Dynamics 365 Customer Voice, ved at se på deres interaktion med Dynamics 365 Customer Voice. Det kan også hjælpe dig med at forstå niveauet af samarbejde, der finder sted, ved at se på antallet af Pro-undersøgelser, der er oprettet og Pro Undersøgelser, som brugerne har reageret på. 
  
## <a name="how-to-get-to-the-dynamics-365-customer-voice-activity-report"></a>Sådan kommer du til Dynamics 365 Customer Voice-aktivitetsrapporten

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboard-startsiden skal du klikke på **knappen Vis** mere på Dynamics 365 Customer Voice-kortet.
  
## <a name="interpret-the-dynamics-365-customer-voice-activity-report"></a>Fortolk Dynamics 365 Customer Voice-aktivitetsrapporten

Du kan få vist aktiviteterne i Dynamics 365 Customer Voice-rapporten ved at vælge **fanen** Aktivitet.<br/>![Microsoft 365 -Microsoft Dynamics 365 Customer Voice-aktivitetsrapport.](../../media/a7e57d18-1ac8-4d4b-bd70-83361505dc3e.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Dynamics 365 Customer Voice-aktivitetsrapport – vælg kolonner.](../../media/5ab66f4b-32eb-4c9b-9683-1157ae9e2c0a.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **rapporten Dynamics 365 Customer Voice-aktivitet** kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|Brugernavn  <br/> |Mailadressen på den bruger, der udførte aktiviteten på Microsoft Forms.  <br/> |
|Dato for seneste aktivitet (UTC)  <br/> |Den seneste dato, hvor en formularaktivitet blev udført af brugeren for det valgte datointerval. Vælg datoen direkte i diagrammet for at se aktivitet, der fandt sted på en bestemt dato.<br/>Dette filtrerer tabellen for kun at vise filaktivitetsdata for brugere, der udførte aktiviteten på den pågældende dag.  <br/> |
|Antal oprettede undersøgelser  <br/> |Antallet af undersøgelser, som brugeren har oprettet.   <br/> |
|Antal undersøgelsessvar  <br/> |Antallet af svar fra svarere, som undersøgelsen blev distribueret til.|
|||