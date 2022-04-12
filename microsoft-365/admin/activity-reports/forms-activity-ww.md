---
title: Microsoft 365 Administration formularaktivitetsrapporter
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
description: Få mere at vide om, hvordan du får en Microsoft Forms aktivitetsrapport ved hjælp af dashboardet Microsoft 365 Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: c00c9e91d4b8e37021a30798088f46b786b3b4fc
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781923"
---
# <a name="microsoft-365-reports-in-the-admin-center---forms-activity"></a>Microsoft 365 rapporter i Administration – Formularaktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at zoome ind på individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for alle brugere, der har licens til at bruge Microsoft Forms, ved at se på deres interaktion med formularer. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af formularer, der er oprettet, og formularer, som brugeren besvarede.
  
## <a name="how-to-get-to-the-forms-activity-report"></a>Sådan får du vist aktivitetsrapporten Formularer

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. Klik på knappen **Vis mere** på kortet Formularer på startsiden for dashboardet.
  
## <a name="interpret-the-forms-activity-report"></a>Fortolkning af aktivitetsrapporten Formularer

Du kan få vist aktiviteterne i rapporten Formularer ved at vælge fanen **Aktivitet** .<br/>![Microsoft 365 rapporter – Microsoft Forms aktivitetsrapport.](../../media/275fb0a1-b9d9-4233-8aaf-e7df73cc705f.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Rapport over formularaktivitet – vælg kolonner.](../../media/0c9b0b69-5dc7-43ea-8e2c-54407b6ce2ab.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

Aktivitetsrapporten **Formularer** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Mailadressen på den bruger, der udførte aktiviteten på Microsoft Forms.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den seneste dato, hvor en formularaktivitet blev udført af brugeren for det valgte datointerval. Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.<br/><br/>Dette filtrerer tabellen, så der kun vises filaktivitetsdata for de brugere, der udførte aktiviteten på den pågældende dag.  <br/> |
|Antal formularer, der er oprettet  <br/> |Antallet af formularer, som brugeren har oprettet.   <br/> |
|Antal formularer, der er besvaret  <br/> |Det antal formularer, som brugeren har sendt svar til.|
|||
