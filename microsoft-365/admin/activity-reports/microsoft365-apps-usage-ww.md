---
title: Microsoft 365 Administration brugsrapporter over apps
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
description: Få mere at vide om, hvordan du får Microsoft 365 Apps rapport over brug ved hjælp Microsoft 365 dashboardet Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: c7a8e5bbf2fec8450b52b3cbe52e110d97061ed3
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63593369"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Microsoft 365 Rapporter i Administration – Microsoft 365 Apps brug

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).

 Du kan f.eks. forstå aktiviteten for hver bruger, der har licens til at bruge Microsoft 365 Apps-apps, ved at se på deres aktivitet på tværs af appsene, og hvordan de bruges på tværs af platforme.
 
 > [!NOTE]
 > Aktiveringer af delte computere er ikke medtaget i denne rapport.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Sådan får du rapporten over Microsoft 365 Apps brug

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboard-startsiden skal du klikke **på knappen Vis** flere på listen Aktive brugere – Microsoft 365 Apps visitkort.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Fortolk Microsoft 365 Apps rapporten over brug

Du kan få et indblik i dine brugeres Microsoft 365 Apps ved at se på **diagrammerne Brugere** **og** Platform.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Apps rapport over brug.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

|Element|Beskrivelse|
 |:-----|:-----|
 |1. <br/> |I **Microsoft 365 Apps kan** du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet). <br/> |
 |2. <br/> |Dataene i hver rapport dækker normalt op til de seneste to dage. Hver sjette dag opdaterer vi rapporten med mindre opdateringer for at sikre datakvaliteten. <br/> |
 |3. <br/> |**Visningen Brugere** viser tendensen i antallet af aktive brugere for hver app – Outlook, Word, Excel, PowerPoint, OneNote og Teams. "Aktive brugere" er alle, der udfører bevidst handlinger inden for disse apps. <br/> |
 |4. <br/> |Visningen **Platforme** viser tendensen for aktive brugere på tværs af alle apps for hver platform – Windows, Mac, web og mobil. <br/> |
 |5.<br/>|I diagrammet **Brugere** er Y-aksen antallet af unikke aktive brugere for den pågældende app.  **PåPlatformschart**  er Y-aksen antallet af unikke brugere for den pågældende platform. X-aksen i begge diagrammer er den dato, hvor en app blev brugt på en given platform.<br/>|
 6.<br/>|Du kan filtrere de serier, du får vist i diagrammet, ved at vælge et element i forklaringen. I diagrammet Brugere skal du  f.eks. vælge Outlook, Word, Excel, PowerPoint, OneDrive eller Teams for kun at få vist de oplysninger, der er relateret til hver enkelt. Hvis du ændrer dette valg, ændres oplysningerne i gittertabellen under den ikke.|
 |7.<br/>|Tabellen viser dig en oversigt over dataene pr. bruger. Du kan tilføje eller fjerne kolonner fra tabellen. <br/><br/>**Brugernavn** er mailadressen på den bruger, der udførte aktiviteten på Microsoft Apps.<br><br/>**Dato for seneste aktivering (UTC)** er den seneste dato, hvor brugeren har aktiveret sit Microsoft 365 Apps-abonnement på en computer eller logger på en delt computer og starter appen med sin konto. <br/><br/>**Dato for seneste aktivitet (UTC)** er den seneste dato, hvor brugeren udførte en bevidst aktivitet. Vælg datoen direkte i diagrammet for at se aktivitet, der fandt sted på en bestemt dato.<br/><br/>De andre kolonner identificerer, om brugeren var aktiv på den pågældende platform for den pågældende app (inden for Microsoft 365 Apps) i den valgte periode. |
 |8.<br/>|Vælg ikonet **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.|
 |9.<br/>|Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel akkumulering, sortering og filtrering til yderligere analyse. Hvis der er mindre end 100 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 100 brugere, skal du eksportere dataene, før du kan filtrere og sortere.|
