---
title: Skiftehold for frontlinjearbejdere
description: Få den administratorvejledning, du skal bruge til at konfigurere og administrere Skift, værktøjet til administration af tidsplan, i Microsoft Teams.
ms.topic: conceptual
author: LanaChin
ms.author: v-lanachin
audience: admin
manager: samanro
f1.keywords:
- NOCSH
ms.service: microsoft-365-frontline
ms.collection:
- M365-collaboration
- m365-frontline
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-frontline
- m365solution-scenario
search.appverid: MET150
ms.localizationpriority: high
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-jun2020
ms.openlocfilehash: 0d9a0104e601b31448b586e3958df0c8d17cad7e
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824104"
---
# <a name="shifts-for-frontline-workers"></a>Skiftehold for frontlinjearbejdere

Vagter, som er værktøjet til styring af tidsplaner i Teams, holder frontlinjearbejdsstyrken forbundet og synkroniseret. Den er bygget mobil først til hurtig og effektiv planlægnings- og kommunikationsstyring. Med Shifts kan frontlinjeledere og medarbejdere uden problemer administrere tidsplaner og holde kontakten.

Ledere kan oprette, opdatere og administrere vagtplaner for deres teams. De kan tildele vagter, tilføje åbne vagter og godkende anmodninger om tidsplaner fra medarbejdere. Medarbejdere kan få vist deres egne og deres teams tidsplaner, angive deres tilgængelighed, anmode om at skifte eller tilbyde et skiftehold, anmode om fridag og stemple ind og ud.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE42FjP]

Brug følgende ressourcer til at hjælpe dig med at konfigurere og administrere skift i din organisation.

## <a name="set-up-and-manage-shifts"></a>Konfigurer og administrer skiftehold

|&nbsp;  |&nbsp; |
|---------|---------|
|<img src="/office/media/icons/calendar-teams.png" alt="Calendar symbol.">   |**[Administrer skiftehold](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Få mere at vide om, hvordan du administrerer vagter for din organisation.         |
|<img src="/office/media/icons/users-people.png" alt="Users/people symbol.">   |**[Administrer tidsplanejere for skiftstyring](schedule-owner-for-shift-management.md)** Denne funktion giver dig mulighed for at hæve tilladelserne for et teammedlem til en tidsplanejer uden at gøre medarbejderen til teamejer.         |
|<img src="/office/media/icons/help.png" alt="Help symbol.">     | **[Skifter ofte stillede spørgsmål om data](/microsoftteams/expand-teams-across-your-org/shifts/shifts-data-faq?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Få mere at vide om, hvor Shifts-data gemmes, og andre emner, der er relateret til Shifts-data, herunder opbevaring, hentning og kryptering.        |

## <a name="shifts-connectors"></a>Skifter forbindelse

Hvis du bruger et tredjepartssystem til styring af arbejdsstyrken (WFM) til planlægning, kan du integrere direkte med Shifts via administrerede Shifts-forbindelser. Når du har konfigureret en forbindelse, kan frontlinjemedarbejderne uden problemer få vist og administrere deres tidsplaner i dit WFM system inde fra Skift.

|&nbsp;  |&nbsp;  |
|---------|---------|
|<img src="/office/media/icons/connector-teams.png" alt="Connector symbol.">     | **[Oversigt over forskydninger af forbindelser](shifts-connectors.md)** Få et overblik over Shifts-connectors, og hvordan de fungerer. Få mere at vide om de administrerede connectors, der er tilgængelige, og de understøttede WFM systemer.   |
|<img src="/office/media/icons/connector-teams.png" alt="Connector symbol.">     | **[Administrerede Shifts-forbindelser](shifts-connectors.md#managed-shifts-connectors)** Administrerede Shifts-connectors, der er udviklet i samarbejde med vores partnere, hostes og administreres enten af os eller vores partnere. Du kan få mere at vide under [Microsoft Teams Shifts-connector til Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) - og [Reflexis Shifts-connector til Microsoft Teams](shifts-connectors.md#reflexis-shifts-connector-for-microsoft-teams).    |
|   | **[Brug guiden Shifts-connector til at forbinde Shifts med blå yonder Workforce Management](shifts-connector-wizard.md)** Guiden Skifts-connector i Microsoft 365 Administration hjælper dig med hurtigt at oprette forbindelse til dit WFM system. I øjeblikket understøtter guiden Teams Shifts-connectoren for Blue Yonder til at integrere Shifts med blå yonder Workforce Management.
|  | **[Brug PowerShell til at forbinde Skift til Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)** Få mere at vide om, hvordan du bruger PowerShell til at konfigurere en forbindelse til Blue Yonder-Workforce Management via Teams Shifts-connectoren til Blue Yonder.         |
|   | **[Brug PowerShell til at administrere din Shifts-forbindelse til Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)** Få vejledning i, hvordan du bruger PowerShell til at administrere din Shifts-forbindelse til Blue Yonder-Workforce Management, når du har konfigureret den via guiden Skifts-connector eller PowerShell.

## <a name="shifts-extensions"></a>Skifter udvidelser

|&nbsp;|&nbsp;|
| ------------- | ------------- |
| <img src="/office/media/icons/api.png" alt="Three gears - API."> | **[Shift Graph-API'er](/graph/api/resources/shift)** Med Shifts Graph-API'er kan du integrere Shifts-data med eksterne WFM systemer. Du får fleksibiliteten til at skabe brugerdefinerede Skift-oplevelser i backend, samtidig med at du giver brugerne en omfattende frontendoplevelse i Teams.             |
|<img src="/office/media/icons/process-flow-teams.png" alt="Process/flow chart symbol."> | **[Skift + Power Automate](https://github.com/OfficeDev/Microsoft-Teams-Shifts-Power-Automate-Templates)** Med Shifts + Power Automate kan du hente oplysninger fra Skift og oprette brugerdefinerede arbejdsprocesser med andre apps og udføre handlinger i stor skala. Automatiser vigtige processer med lidt eller ingen kode. Udløserne og skabelonerne understøtter forskellige scenarier, f.eks. aktivering af automatiske godkendelser for skiftanmodninger, når en leders godkendelse ikke er nødvendig. |

## <a name="featured-training"></a>Udvalgt træning

|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| <img src="/office/media/icons/get-started-teams.png" alt="Get started symbol.">  |  [Video: Hvad er Skift?](https://support.office.com/article/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821) |<img src="/office/media/icons/clock-teams.png" alt="Clock symbol."> |  [Video: Opret en tidsplan for vagter](https://support.microsoft.com/office/create-a-shifts-schedule-2b94ca38-36db-4a1c-8fee-f8f0fec9a984) |<img src="/office/media/icons/blocks-teams.png" alt="Blocks symbol.">|  [Video: Administrer en tidsplan for skiftehold](https://support.microsoft.com/office/manage-and-view-a-shifts-schedule-63acda7b-ea39-441a-b1c6-c404a72e79f7) |
