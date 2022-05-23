---
title: Microsoft 365 Administration SharePoint aktivitetsrapporter
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
description: Få rapporten over SharePoint aktivitetsforbrug for at få mere at vide om SharePoint brugerfilinteraktioner med licens, antallet af delte filer og lagerudnyttelse.
ms.openlocfilehash: 52aaaf3d9eef59c582977ee7b7c04ded44233c59
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636498"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-activity"></a>Microsoft 365 rapporter i Administration – SharePoint aktivitet

Som Microsoft 365 administrator viser dashboardet Rapporter aktivitetsoversigten på tværs af forskellige produkter i din organisation. Det giver dig mulighed for at foretage detailudledning for at få mere detaljeret indsigt i de aktiviteter, der er specifikke for hvert produkt. Se [aktivitetsrapporterne i Microsoft 365 Administration](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for alle brugere, der er licenseret til at bruge SharePoint ved at se på deres interaktion med filer. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af filer, der deles.
  
## <a name="how-do-i-get-to-the-sharepoint-activity-report"></a>Hvordan gør jeg du gå til aktivitetsrapporten for SharePoint?

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet SharePoint.
  
## <a name="interpret-the-sharepoint-activity-report"></a>Fortolkning af SharePoint aktivitetsrapport

Du kan få vist aktiviteterne i SharePoint rapport ved at vælge fanen **Aktivitet**.<br/>![Microsoft 365 rapporter – Microsoft SharePoint aktivitetsrapport.](../../media/5a0a96f-0e4f-4fb9-8baa-3262275b3d1f.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![SharePoint aktivitetsrapport – vælg kolonner.](../../media/3c396cd1-9701-4712-8eaa-eb7bba702aa8.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

Den **SharePoint aktivitetsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Mailadressen på den bruger, der udførte aktiviteten på SharePoint-webstedet.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den seneste dato, hvor en filaktivitet blev udført, eller en side blev besøgt for det valgte datointerval. Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.  <br/> |
|Viste eller redigerede filer  <br/> |Antallet af filer, som brugeren har uploadet, downloadet, ændret eller fået vist.   <br/> |
|Synkroniserede filer  <br/> |Antallet af filer, der er blevet synkroniseret fra en brugers lokale enhed til det SharePoint websted. <br/> |
|Filer, der deles internt  <br/> | Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|Filer, der deles eksternt  <br/> |Antallet af filer, der er blevet delt med brugere uden for organisationen. <br/>|
|Besøgte sider  <br/> |Brugerens besøg på entydige sider. <br/>|
|Slettet  <br/> | Dette angiver, at brugerens licens blev fjernet.  <br/>  **BEMÆRK:** Aktivitet for en slettet bruger vises stadig i rapporten, så længe vedkommende har fået licens på et tidspunkt i den valgte tidsperiode. Kolonnen Slettet hjælper dig med at bemærke, at brugeren muligvis ikke længere er aktiv, men har bidraget til dataene i rapporten.  <br/> |
|Slettet dato  <br/> |Den dato, hvor brugerens licens blev fjernet. <br/>|
|Tildelt produkt  <br/> |De Microsoft 365 produkter, der er givet i licens til brugeren.|
|||