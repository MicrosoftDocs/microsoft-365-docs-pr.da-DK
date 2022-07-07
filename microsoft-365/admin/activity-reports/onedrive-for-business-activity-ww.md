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
description: Hent OneDrive-forbrugsrapporten for din organisation, og find ud af alle OneDrive-brugeres aktivitet, antallet af delte filer og udnyttelsen af lagerplads.
ms.openlocfilehash: 02290333af41ee5e5773c0979fef1c282f2e0e21
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662618"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365-rapporter i Administration – OneDrive for Business aktivitet

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at zoome ind på individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for alle brugere, der har licens til at bruge OneDrive, ved at se på deres interaktion med filer på OneDrive. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af filer, der deles.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Hvordan gør jeg du gå til OneDrive-aktivitetsrapporten?

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. Klik på knappen **Vis mere** på kortet OneDrive på startsiden for dashboardet.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Fortolkning af OneDrive for Business aktivitetsrapport

Du kan få vist aktiviteterne i OneDrive-rapporten ved at vælge fanen **Aktivitet** .<br/>![Microsoft 365-rapporter – Microsoft OneDrive-aktivitetsrapport.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Aktivitetsrapport for OneDrive – vælg kolonner.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. 

Den **OneDrive for Business aktivitetsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Brugernavnet på ejeren af OneDrive-kontoen.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den seneste dags filaktivitet fandt sted på OneDrive-kontoen for det valgte datointerval. Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.  <br/> |
|Viste eller redigerede filer  <br/> |Antallet af filer, som brugeren har uploadet, downloadet, ændret eller fået vist.   <br/> |
|Synkroniserede filer  <br/> |Antallet af filer, der er blevet synkroniseret fra en brugers lokale enhed til OneDrive-kontoen. <br/> |
|Filer, der deles internt  <br/> | Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|Filer, der deles eksternt  <br/> |Antallet af filer, der er blevet delt med brugere uden for organisationen. <br/>|
|Slettet  <br/> | Dette angiver, at brugerens licens blev fjernet.  <br/> BEMÆRK! Aktivitet for en slettet bruger vises stadig i en rapport, så længe vedkommende har fået licens på et tidspunkt i den valgte tidsperiode. Kolonnen **Slettet** hjælper dig med at bemærke, at brugeren muligvis ikke længere er aktiv, men har bidraget til dataene i rapporten.  <br/> |
|Slettet dato  <br/> |Den dato, hvor brugerens licens blev fjernet. <br/>|
|Tildelt produkt  <br/> |De Microsoft 365-produkter, der er givet i licens til brugeren.|
|||