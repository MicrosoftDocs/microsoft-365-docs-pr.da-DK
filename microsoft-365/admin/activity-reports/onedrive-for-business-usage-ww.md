---
title: Microsoft 365 OneDrive for Business brugsrapporter
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: 'Få oplysninger OneDrive for Business om det samlede antal filer og den lagerplads, der bruges i hele organisationen. '
ms.openlocfilehash: d3b884f374cf3dde572bd67ad905fc308a1701d1
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591705"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 Rapporter i Administration – OneDrive for Business brug

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).
  
Eksempelvis giver OneDrive-kortet på dashboardet dig en højniveauvisning af den værdi, du får fra OneDrive for Business med hensyn til det samlede antal filer og den lagerplads, der bruges i hele organisationen. Du kan derefter analysere den for at forstå tendenserne for aktive OneDrive-konti, hvor mange filer brugerne interagerer med, samt hvor meget lagerplads der er brugt. Den giver dig også oplysninger om hver enkelt brugers OneDrive.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Hvordan finder jeg rapporten OneDrive brug?

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på OneDrive visitkort.
  
## <a name="interpret-the-onedrive-usage-report"></a>Fortolk OneDrive rapporten over brug

Du kan få vist brugen i OneDrive rapport ved at vælge **fanen** Brug.<br/>![Microsoft 365 rapporter – Microsoft OneDrive rapport over brug.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![OneDrive anvendelsesrapport – vælg kolonner.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **OneDrive for Business kan** du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|URL-adresse  <br/> |Webadressen for brugerens OneDrive. <br/> |
|Slettet  <br/> |Sletningsstatus for OneDrive. Det tager mindst 7 dage, før konti markeres som slettet.  <br/> |
|Ejer  <br/> |Brugernavnet for den primære administrator af OneDrive.   <br/> |
|Ejers hovednavn  <br/> |Mailadressen på ejeren af OneDrive. <br/> |
|Dato for seneste aktivitet (UTC)  <br/> | Den seneste dato, hvor der blev udført en filaktivitet i OneDrive. Hvis OneDrive havde nogen filaktivitet, vil værdien være tom.  <br/> |
|Filer  <br/> |Antallet af filer i OneDrive. <br/>|
|Aktive filer  <br/> | Antallet af aktive filer inden for tidsperioden.<br/> BEMÆRK! Hvis filerne er blevet fjernet i løbet af den angivne periode for rapporten, kan antallet af aktive filer, der vises i rapporten, være større end det aktuelle antal filer i OneDrive. > Slettede brugere vil fortsat blive vist i rapporter i 180 dage.  <br/> |
|Storage anvendt (MB)  <br/> |Mængden af lagerplads, OneDrive bruger i MB. |
|||
   
> [!NOTE]
> Rapporten omfatter kun brugere, der har en gyldig OneDrive for Business licens.
