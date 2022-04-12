---
title: Microsoft 365 OneDrive for Business anvendelsesrapporter
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
description: 'Få OneDrive for Business anvendelsesrapport for at få mere at vide om det samlede antal filer og lagerplads, der bruges på tværs af organisationen. '
ms.openlocfilehash: f212a29a5fb41aae9ecb0daeae0638d7af1e5dd1
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781545"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Microsoft 365 rapporter i Administration – OneDrive for Business brug

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Kortet OneDrive på dashboardet giver dig f.eks. en overordnet visning af den værdi, du får fra OneDrive for Business i forhold til det samlede antal filer og lagerplads, der bruges på tværs af din organisation. Du kan derefter analysere det for at forstå tendenserne for aktive OneDrive konti, hvor mange filer brugerne interagerer med, samt det anvendte lager. Du får også oplysninger om hver brugers OneDrive.

## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Hvordan gør jeg du gå til OneDrive forbrugsrapport?

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet OneDrive.
  
## <a name="interpret-the-onedrive-usage-report"></a>Fortolkning af forbrugsrapporten for OneDrive

Du kan få vist forbruget i OneDrive rapport ved at vælge fanen **Forbrug**.<br/>![Microsoft 365 rapporter – Microsoft OneDrive forbrugsrapport.](../../media/3cdaf2fb-1817-479b-a0e1-2afa228690cf.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![OneDrive forbrugsrapport – vælg kolonner.](../../media/9ee80f25-cfe3-411d-8e31-08f1507d18c1.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

Den **OneDrive for Business forbrugsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|URL  <br/> |Webadressen på brugerens OneDrive. <br/> |
|Slettet  <br/> |Status for sletning for OneDrive. Det tager mindst 7 dage, før konti markeres som slettede.  <br/> |
|Ejer  <br/> |Brugernavnet for den primære administrator af OneDrive.   <br/> |
|Ejerens hovednavn  <br/> |Mailadressen på ejeren af OneDrive. <br/> |
|Seneste aktivitetsdato (UTC)  <br/> | Den seneste dato, hvor en filaktivitet blev udført i OneDrive. Hvis OneDrive ikke har nogen filaktivitet, er værdien tom.  <br/> |
|Filer  <br/> |Antallet af filer i OneDrive. <br/>|
|Aktive filer  <br/> | Antallet af aktive filer inden for tidsperioden.<br/> BEMÆRK! Hvis filer blev fjernet i den angivne tidsperiode for rapporten, kan antallet af aktive filer, der vises i rapporten, være større end det aktuelle antal filer i OneDrive. > Slettede brugere vises fortsat i rapporter i 180 dage.  <br/> |
|Storage brugt (MB)  <br/> |Den lagermængde, som OneDrive bruger i MB. |
|||
   
> [!NOTE]
> Rapporten indeholder kun brugere, der har en gyldig OneDrive for Business licens.
