---
title: 'Microsoft 365 Administration projektaktivitet '
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
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
description: Få mere at vide om, hvordan du henter projektaktivitetsrapporten og får indsigt i projektaktiviteten i din organisation.
ms.openlocfilehash: 202f9e0655f2d96e6897f2803a43264741343381
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858779"
---
# <a name="microsoft-365-reports-in-the-admin-center---project-activity"></a>Microsoft 365-rapporter i Administration – Projektaktivitet

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).

I **projektaktivitetsrapporten** kan du forstå aktiviteten for alle brugere, der har licens til at bruge Microsoft Project, ved at se på deres interaktion med Project. Det hjælper dig også med at forstå det samarbejdsniveau, der foregår, ved at se på antallet af besøgte projekter og opgaver, der er oprettet eller redigeret.

## <a name="how-to-get-to-the-project-activity-report"></a>Sådan kommer du til projektaktivitetsrapporten

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet Project.

## <a name="interpret-the-project-activity-report"></a>Fortolkning af projektaktivitetsrapporten

Du kan bruge denne rapport til at se aktiviteten og brugen af Project i dit miljø. Du får vist fire oversigtsdiagrammer i denne rapport:  <br/>![Microsoft 365-rapporter – Projektaktivitet.](../../media/project-activity.png)

- **Aktive brugere** – viser dig de daglige aktive brugere på hver dag over tid. Dette omfatter i øjeblikket kun Project for the Web og Project Online desktopklient.
- **Aktive brugere (efter klient)** – Viser dig de daglige aktive brugere på hver dag over tid, opdelt efter klient (Project for the Web vs. Project Online desktopklient).
- **Projektaktivitet** – Viser antallet af daglige sessioner af Project over tid for hver klient (Project for the Web og Project Online desktopklient).
- **Opgaveaktivitet** – Viser det daglige antal opgaver, der oprettes eller redigeres over tid i Project til internettet

Rapporten har også en tabel, der viser aktivitet for hver projektbruger i dit miljø.

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra tabellen.

![Projektaktivitetsrapport – vælg kolonner.](../../media/project-activity-columns.png)

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse.

**Projektaktivitetsrapporten** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Hvis du vælger en bestemt dag i rapporten, opdateres datatabellen pr. bruger i overensstemmelse hermed for at vise brugernes forbrug den pågældende dag. Denne funktion fungerer dog kun i de seneste 28 dage.

### <a name="privacy-settings-impact-on-the-dashboard"></a>Indstillinger for beskyttelse af personlige oplysninger påvirker dashboardet

Hvis brugere eller administratorer har angivet deres indstillinger for beskyttelse af personlige oplysninger til **Ingen af delene**, har vi ikke nøjagtige målepunkter for **projektaktivitetsdiagrammet** for Project Online desktopklient. De viste tal vil være undertal. Du kan få flere oplysninger om indstillinger for beskyttelse af personlige oplysninger under [Brug politikindstillinger til at administrere kontrolelementer til beskyttelse af personlige oplysninger for Microsoft 365 Apps for enterprise](/deployoffice/privacy/manage-privacy-controls.md).

## <a name="user-activity-table"></a>Brugeraktivitetstabel

Følgende er definitioner for hver metrikværdi i brugeraktivitetstabellen.

|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn|Brugerens hovednavn.|
|Vist navn|Brugerens fulde navn.|
|Seneste aktivitetsdato|Den seneste dato, hvor brugeren i rækken havde aktivitet i Project, herunder aktiviteter i oversigtsrapporterne.|
|Besøgte projekter (Desktop)|Det antal projekter, der er åbnet af brugeren i Project Online desktopklient i løbet af det tidsinterval, der er valgt øverst til højre på siden.|
|Besøgte projekter (web)| Det antal opgaver, der er oprettet af brugeren i Project på internettet i løbet af det tidsinterval, der er valgt øverst til højre på siden.|
|Oprettede opgaver (web)|Det antal opgaver, der er oprettet af brugeren i Project på internettet i løbet af det tidsinterval, der er valgt øverst til højre på siden.|
|Redigerede opgaver (web)|Det antal opgaver, der er redigeret af brugeren i Project på internettet i det tidsinterval, der er valgt øverst til højre på siden.|
|Andet|Denne værdi er sand, hvis brugeren har udført en aktivitet i Project Online desktopklient eller i Project for the Web (som ikke er dækket af de andre kolonner) i det tidsinterval, der er valgt øverst til højre på siden. Hvis brugeren ikke har gjort det, er denne værdi falsk.|
