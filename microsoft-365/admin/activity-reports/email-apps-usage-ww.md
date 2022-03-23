---
title: Microsoft 365 Administration brugsrapporter over mailapps
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
description: Få mere at vide om, hvordan du får rapporten om brug af mailapps for at få oplysninger om mailapps, der opretter forbindelse Exchange Online og den Outlook version, som brugerne bruger.
ms.openlocfilehash: c2d68c5b151b236ee51d0a06b4e51f6e6b16ede5
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590495"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-apps-usage"></a>Microsoft 365 Rapporter i Administration – brug af mailapps

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md). I rapporten brug af mailapps kan du se, hvor mange mailapps der opretter forbindelse til Exchange Online. Du kan også se versionsoplysningerne om Outlook-apps, som brugerne bruger, så du kan følge op på dem, der bruger ikke-understøttede versioner, for at installere understøttede versioner af Outlook.
  
## <a name="how-to-get-to-the-email-apps-report"></a>Sådan får du rapporten over mailapps

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug.
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På **rullelisten Mailaktivitet** skal du vælge Indstillinger Exchange **brug** \> **af mailapps**.
  
## <a name="interpret-the-email-apps-report"></a>Fortolk rapporten over mailapps

Du kan få et indblik i mailappaktiviteten ved at se på **diagrammerne Brugere** **og** Klienter. 
  
![Anvendte mailklienter.](../../media/d78af7db-2b41-4d37-8b6e-bc7e47edd1dd.png)
  
|Element|Beskrivelse|
|:-----|:-----|
|1.  <br/> |I **rapporten Brug af mailapps** kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).  <br/> |
|2.  <br/> |Dataene i hver rapport dækker normalt op til de seneste 24 til 48 timer.  <br/> |
|3.  <br/> |Visningen **Brugere** viser antallet af unikke brugere, der har forbindelse til en Exchange Online bruger en mailapp.  <br/> |
|4.  <br/> |Visningen **Apps** viser antallet af unikke brugere efter app i den valgte tidsperiode.  <br/> |
|5.  <br/> |Visningen **Versioner** viser antallet af unikke brugere for hver version af Outlook i Windows.  <br/> |
|6.  <br/> | I diagrammet **Brugere** er Y-aksen det samlede antal unikke brugere, der havde forbindelse til en app på en hvilken som helst dag i rapporteringsperioden.  <br/>  I diagrammet **Brugere** er X-aksen antallet af unikke brugere, der brugte appen til den pågældende rapporteringsperiode.  <br/>  I diagrammet **Apps** er Y-aksen det samlede antal unikke brugere, der brugte en bestemt app i løbet af rapporteringsperioden.  <br/>  I diagrammet **Apps** er X-aksen listen over apps i organisationen.  <br/>  I diagrammet **Versioner** er Y-aksen det samlede antal unikke brugere, der bruger en bestemt version Outlook skrivebord. Hvis rapporten ikke kan løse versionsnummeret på Outlook, vises antallet **som Ubestemt**.  <br/>  I diagrammet **Versioner** er X-aksen listen over apps i organisationen.  <br/> |
|7.  <br/> |Du kan filtrere de serier, du får vist i diagrammet, ved at vælge et element i forklaringen.  <br/> |
|8.  <br/> | Du kan muligvis ikke se alle elementerne på nedenstående liste i kolonnerne, før du tilføjer dem.<br/> **Brugernavn** er navnet på ejeren af mailappen.  <br/> **Dato for seneste** aktivitet er den seneste dato, hvor brugeren læser eller sender en mail.  <br/> **Mac Mail**, **Mac Outlook** **og Outlook**, **Outlook mobile** **og Outlook på internettet er** eksempler på mailapps, som du kan have i din organisation.  <br/>  Hvis din organisations politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Se sektionen **Hvordan skjuler jeg oplysninger på brugerniveau?** i [aktivitetsrapporter i Microsoft 365 Administration](activity-reports.md).  <br/> |
|9.  <br/> |Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Rapport over brug af mailapps – vælg kolonner.](../../media/041bd6ff-27e8-409d-9608-282edcfa2316.png)|
|10.  <br/> |Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere.  <br/> |
|||
   
