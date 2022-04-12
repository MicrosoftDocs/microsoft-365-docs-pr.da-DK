---
title: Microsoft 365 OneDrive for Business aktivitetsrapporter
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
description: Hent OneDrive forbrugsrapport for din organisation, og kend aktiviteten for hver OneDrive bruger, antallet af delte filer og lagerudnyttelsen.
ms.openlocfilehash: 48edb30eae60f6e7dcac5bc63dc9676dc27e0a90
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781577"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 rapporter i Administration – OneDrive for Business aktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at zoome ind på individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for alle brugere med licens til at bruge OneDrive ved at se på deres interaktion med filer på OneDrive. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af filer, der deles.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Hvordan gør jeg du gå til OneDrive aktivitetsrapporten?

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet OneDrive.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Fortolkning af OneDrive for Business aktivitetsrapport

Du kan få vist aktiviteterne i OneDrive rapport ved at vælge fanen **Aktivitet**.<br/>![Microsoft 365 rapporter – Microsoft OneDrive aktivitetsrapport.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![OneDrive aktivitetsrapport – vælg kolonner.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem.

Den **OneDrive for Business aktivitetsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Brugernavnet på ejeren af den OneDrive konto.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den seneste dato, hvor en filaktivitet blev udført på den OneDrive konto for det valgte datointerval. . Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.  <br/> |
|Viste eller redigerede filer  <br/> |Antallet af filer, som brugeren har uploadet, downloadet, ændret eller fået vist.   <br/> |
|Synkroniserede filer  <br/> |Det antal filer, der er blevet synkroniseret fra en brugers lokale enhed til den OneDrive konto. <br/> |
|Filer, der deles internt  <br/> | Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|Filer, der deles eksternt  <br/> |Antallet af filer, der er blevet delt med brugere uden for organisationen. <br/>|
|Slettet  <br/> | Dette angiver, at brugerens licens blev fjernet.  <br/> BEMÆRK! Aktivitet for en slettet bruger vises stadig i en rapport, så længe vedkommende har fået licens på et tidspunkt i den valgte tidsperiode. Kolonnen **Slettet** hjælper dig med at bemærke, at brugeren muligvis ikke længere er aktiv, men har bidraget til dataene i rapporten.  <br/> |
|Slettet dato  <br/> |Den dato, hvor brugerens licens blev fjernet. <br/>|
|Tildelt produkt  <br/> |De Microsoft 365 produkter, der er givet i licens til brugeren.|
|||