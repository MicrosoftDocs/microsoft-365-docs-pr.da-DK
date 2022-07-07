---
title: forbrugsrapporter for Microsoft 365 Administration mailapps
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
- MET150
- MOE150
- GEA150
ms.assetid: c2ce12a2-934f-4dd4-ba65-49b02be4703d
description: Få mere at vide om, hvordan du får en forbrugsrapport for mailapps for at finde ud af, hvor mange mailapps der opretter forbindelse til Exchange Online, og hvilken version af Outlook-brugere der bruger.
ms.openlocfilehash: c4918b818cad5479b787528fece2c74412a5cfa4
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662080"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365-rapporter i Administration – Brug af mailapps

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md). I rapporten over brug af mailapps kan du se, hvor mange mailapps der opretter forbindelse til Exchange Online. Du kan også se versionsoplysningerne for De Outlook-apps, som brugerne bruger, hvilket giver dig mulighed for at følge op på dem, der bruger ikke-understøttede versioner til at installere understøttede versioner af Outlook.
  
## <a name="how-to-get-to-the-email-apps-report"></a>Sådan kommer du til mailappsrapporten

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På rullelisten **Mailaktivitet** skal du vælge **Brug af Exchange-mailapps**\>.
  
## <a name="interpret-the-email-apps-report"></a>Fortolkning af mailapps-rapporten

Du kan få vist aktivitet i mailapps ved at se på diagrammerne **Brugere** og **klienter** . 
  
![Mailklienter bruges.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)

Rapporten **over brug af mailapps** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret). Dataene i hver rapport dækker normalt op til de sidste 24 til 48 timer.

Visningen **Brugere** viser antallet af entydige brugere, der har oprettet forbindelse til Exchange Online ved hjælp af en hvilken som helst mailapp. 

Visningen **Apps** viser antallet af entydige brugere efter app i den valgte tidsperiode. 

I visningen **Versioner** kan du se antallet af entydige brugere for hver version af Outlook i Windows. 

I diagrammet Brugere er Y-aksen det samlede antal entydige brugere, der har oprettet forbindelse til en app på en hvilken som helst dag i rapporteringsperioden. Og X-aksen er antallet af entydige brugere, der har brugt appen i den pågældende rapporteringsperiode. 

I diagrammet Apps er Y-aksen det samlede antal entydige brugere, der brugte en bestemt app i rapporteringsperioden. Og X-aksen er listen over apps i din organisation. 

I diagrammet Versioner er Y-aksen det samlede antal entydige brugere, der bruger en bestemt version af Outlook Desktop. Hvis rapporten ikke kan fortolke versionsnummeret for Outlook, vises antallet som **Ikke defineret**. Og X-aksen er listen over apps i din organisation.

Du kan filtrere de serier, du kan se i diagrammet, ved at vælge et element i forklaringen. Du kan muligvis ikke se alle elementerne på listen nedenfor i kolonnerne, før du tilføjer dem.
 
|Element|Beskrivelse|
|:-----|:-----|
|Brugernavn | Navnet på ejeren af mailappen. |
|Seneste aktivitetsdato | Den seneste dato, hvor brugeren læste eller sendte en mail. |
|Mac mail, Mac Outlook, Outlook, Outlook Mobile og Outlook på internettet | Eksempler på mailapps, du kan have i din organisation. |
   
Hvis organisationens politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Tjek afsnittet **Hvordan gør jeg skjule detaljer på brugerniveau?** i [aktivitetsrapporterne i Microsoft 365 Administration](activity-reports.md). 

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  

![Rapport over brug af mailapps – vælg kolonner.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. 