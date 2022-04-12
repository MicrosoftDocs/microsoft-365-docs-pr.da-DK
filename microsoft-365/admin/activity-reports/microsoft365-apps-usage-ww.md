---
title: forbrugsrapporter for Microsoft 365 Administration apps
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
description: Få mere at vide om, hvordan du får en Microsoft 365 Apps til forbrugsrapport ved hjælp af dashboardet Microsoft 365 Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: 229797921de2e24754203efc466f63661eb26bc8
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781605"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Microsoft 365 rapporter i Administration – Microsoft 365 Apps brug

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).

Du kan f.eks. forstå aktiviteten for hver bruger med licens til at bruge Microsoft 365 Apps apps ved at se på deres aktivitet på tværs af appsene, og hvordan de anvendes på tværs af platforme.

> [!NOTE]
> Delte computeraktiveringer er ikke inkluderet i denne rapport.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Sådan kommer du til rapporten over Microsoft 365 Apps forbrug

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. Klik på knappen **Vis mere** på kortet Aktive brugere – Microsoft 365 Apps på startsiden for dashboardet.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Fortolkning af Microsoft 365 Apps forbrugsrapport

Du kan få vist din brugers Microsoft 365 Apps aktivitet ved at se på diagrammerne **Brugere** og **Platform**.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Apps forbrugsrapport.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

|Element|Beskrivelse|
|---|---|
|1.|Den **Microsoft 365 Apps forbrugsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).|
|2.|Dataene i hver rapport dækker normalt op til de sidste to dage. Hver sjette dag opdaterer vi rapporten med mindre opdateringer for at sikre datakvaliteten.|
|3.|Visningen **Brugere** viser tendensen i antallet af aktive brugere for hver app – Outlook, Word, Excel, PowerPoint, OneNote og Teams. "Aktive brugere" er alle, der udfører bevidst handling i disse apps.|
|4.|Visningen **Platforme** viser tendensen for aktive brugere på tværs af alle apps for hver platform – Windows, Mac, Web og Mobile.|
|5.|I diagrammet **Brugere** er Y-aksen antallet af entydige aktive brugere for den pågældende app. På **platformsdiagrammet** er Y-aksen antallet af entydige brugere for den pågældende platform. X-aksen i begge diagrammer er den dato, hvor en app blev brugt på en given platform.|
 6.|Du kan filtrere de serier, du kan se i diagrammet, ved at vælge et element i forklaringen. I diagrammet **Brugere** skal du f.eks. vælge Outlook, Word, Excel, PowerPoint, OneDrive eller Teams for kun at få vist de oplysninger, der er relateret til hver enkelt. Hvis du ændrer markeringen, ændres oplysningerne i gittertabellen under den ikke.|
|7.|I tabellen kan du se en opdeling af data på niveauet pr. bruger. Du kan tilføje eller fjerne kolonner fra tabellen. <br/><br/>**Brugernavn** er mailadressen på den bruger, der udførte aktiviteten på Microsoft Apps.<br><br/>**Seneste aktiveringsdato (UTC)** er den seneste dato, hvor brugeren aktiverede sit Microsoft 365 Apps-abonnement på en computer eller logger på en delt computer og starter appen med sin konto. <br/><br/>**Seneste aktivitetsdato (UTC)** er den seneste dato, hvor en bevidst aktivitet blev udført af brugeren. Hvis du vil se en aktivitet, der fandt sted på en bestemt dato, skal du vælge datoen direkte i diagrammet.<br/><br/>De andre kolonner identificerer, om brugeren var aktiv på denne platform for den pågældende app (inden for Microsoft 365 Apps) i den valgte periode.|
|8.|Vælg ikonet **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.|
|9.|Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel aggregering, sortering og filtrering for yderligere analyse. Hvis du har mindre end 100 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 100 brugere, skal du eksportere dataene for at filtrere og sortere.|
