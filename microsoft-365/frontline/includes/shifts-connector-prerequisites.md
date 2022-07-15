---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: ab375a876eb62e5f41e5dd7cda3743d4010b95ff
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823878"
---
Før du kommer i gang, skal du sørge for, at du har følgende forudsætninger:

- Blue Yonder WFM version 2020.3, 2021.1 eller 2021.2.

    > [!NOTE]
    > Hvis du har Blue Yonder WFM 2020.3 eller 2021.1, skal du anvende programrettelsen 2020.3.0.4 eller 2021.1.0.3. Denne programrettelse løser et problem, hvor brugerne får en vedvarende fejlmeddelelse i Skift. Det løser også et problem, der forhindrer brugerne i at opdatere deres tilgængelighed i skift.

- Dit Blue Yonder WFM tjenestekontonavn og url-adresser til adgangskode og tjeneste:

    - URL-adresse til godkendelse i organisationsnetværk
    - URL-adresse til cookiegodkendelse
    - URL-adresse til medarbejderselvbetjening
    - URL-adresse til detailweb-API
    - URL-adresse til WEBSTEDsstyring
    - URL-adresse til administrations-API

    Hvis du ikke har disse oplysninger, skal du kontakte Blue Yonder-support. Kontoen oprettes på rodvirksomhedsniveau af en blå Yonder-virksomhedsadministrator. Den skal have adgang til API, klient Administration og Store Manager. Kontoen og adgangskoden kræves for at oprette en forbindelse.
- SSO-godkendelse i organisationsnetværket er aktiveret i dit Blue Yonder WFM-miljø. Kontakt Blue Yonder-understøttelse for at sikre, at SSO i organisationsnetværket er aktiveret. De skal bruge følgende oplysninger:

    - federatedSSOValidationService: `https://wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` hvor {tenantId} er dit lejer-id
     - proxyHeader: X-MS-AuthToken

- Der er konfigureret mindst ét team i Teams.
- Du har føjet din Microsoft 365-systemkonto som teamejer til alle de teams, du vil tilknytte.</br> [Opret denne konto i Microsoft 365,](/microsoft-365/admin/add-users/add-users) og tildel den en Microsoft 365-licens. Føj derefter kontoen som teamejer til alle de teams, du vil tilknytte. Shifts-connectoren bruger denne konto, når Skift-ændringer synkroniseres fra Blue Yonder WFM.

    Vi anbefaler, at du opretter en konto specifikt til dette formål og ikke bruger din brugerkonto.