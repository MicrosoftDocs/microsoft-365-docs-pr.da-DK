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
description: Få rapporten OneDrive om brug af filer for organisationen, og få mere at vide om aktiviteten for hver OneDrive-bruger, antallet af delte filer og anvendelsen af lagerplads.
ms.openlocfilehash: 52e925774ba2315f582f1b5ba50a4a75fe221c10
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590449"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-activity"></a>Microsoft 365 Rapporter i Administration – OneDrive for Business aktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det giver dig mulighed for at analysere individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).
  
Du kan f.eks. forstå aktiviteten for hver enkelt bruger, der har licens til at OneDrive, ved at se på deres interaktion med filer på OneDrive. Det kan også hjælpe dig med at forstå niveauet af samarbejde, der finder sted, ved at se på antallet af delte filer.

## <a name="how-do-i-get-to-the-onedrive-activity-report"></a>Hvordan finder jeg rapporten OneDrive Aktivitet?

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på OneDrive visitkort.
  
## <a name="interpret-the-onedrive-for-business-activity-report"></a>Fortolk OneDrive for Business aktivitetsrapport

Du kan få vist aktiviteterne i OneDrive ved at vælge **fanen** Aktivitet.<br/>![Microsoft 365 - Microsoft OneDrive aktivitetsrapport.](../../media/c89df0b0-2611-4acf-9ef7-17cedf7977be.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![OneDrive aktivitetsrapport – vælg kolonner.](../../media/252f311f-ffde-4e5a-9158-2b822bf86964.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere.

I **OneDrive for Business kan** du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|Brugernavn  <br/> |Brugernavnet på ejeren af den OneDrive konto.  <br/> |
|Dato for seneste aktivitet (UTC)  <br/> |Den seneste dato, hvor der blev udført en filaktivitet på OneDrive for det valgte datointerval. . Vælg datoen direkte i diagrammet for at se aktivitet, der fandt sted på en bestemt dato.  <br/> |
|Filer, der er vist eller redigeret  <br/> |Antallet af filer, som brugeren har uploadet, downloadet, ændret eller set.   <br/> |
|Filer, der er synkroniseret  <br/> |Antallet af filer, der er blevet synkroniseret fra en brugers lokale enhed til den OneDrive konto. <br/> |
|Filer, der er delt internt  <br/> | Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere inden for grupper (det kan omfatte eksterne brugere).  <br/> |
|Filer, der er delt eksternt  <br/> |Antallet af filer, der er delt med brugere uden for organisationen. <br/>|
|Slettet  <br/> | Dette angiver, at brugerens licens er blevet fjernet.  <br/> BEMÆRK! Aktivitet for en slettet bruger vises stadig i en rapport, så længe han eller hun var licenseret på et tidspunkt i den valgte tidsperiode. I **kolonnen Slettet** kan du se, at brugeren muligvis ikke længere er aktiv, men har bidraget til dataene i rapporten.  <br/> |
|Slettet dato  <br/> |Den dato, hvor brugerens licens blev fjernet. <br/>|
|Tildelt produkt  <br/> |De Microsoft 365 produkter, der er givet i licens til brugeren.|
|||