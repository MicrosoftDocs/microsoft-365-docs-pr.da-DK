---
title: Skifter forbindelse
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om Shifts-connectors, og hvordan du bruger dem til at forbinde Shifts med dit system til styring af arbejdsstyrken.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: c211e066a1b5c6ad610c2f3be703d50be3ecf6af
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824010"
---
# <a name="shifts-connectors"></a>Skifter forbindelse

## <a name="overview"></a>Oversigt

Med Shifts-connectors kan du integrere Shifts, som er værktøjet til styring af tidsplaner i Microsoft Teams, med dit system til styring af arbejdsstyrken (WFM). Når du har konfigureret en forbindelse, kan frontlinjemedarbejderne uden problemer få vist og administrere deres tidsplaner i dit WFM system inde fra Skift.

Når du forbinder dit WFM system til Teams, bliver din frontlinearbejdsstyrke i stand til at administrere tidsplaner mere effektivt og strømliner daglige processer for større engagement og produktivitet. Dine frontlinjemedarbejdere har ét sted, hvor de kan planlægge, kommunikere og samarbejde, så de kan få arbejdet fra hånden, uanset hvor de er, på alle enheder.

I denne artikel får du et overblik over Skifts-connectors, og hvordan de fungerer.

## <a name="how-shifts-connectors-work"></a>Sådan fungerer Shifts-connectors

Forbindelseselementer synkroniserer tidsplandata mellem dit WFM system og Skift, hvilket bringer organisationens tidsplaner ind i Teams. Vagter er stedet, hvor dine frontlinjemedarbejdere engagerer sig i deres planlægningsbehov. Dit WFM system er postsystemet for forretningsregler, overholdelse af angivne standarder og intelligens.

Dataflows via connectoren på begge måder for at sikre, at tidsplaner altid er opdaterede. Tidsplaner i dit WFM system synkroniseres til Skift. Og ændringer af tidsplaner i Skift synkroniseres tilbage til dit WFM system i realtid. Som postsystem gennemtvinges alle forretningsregler af dit WFM system, før data gemmes på Skift.

## <a name="managed-shifts-connectors"></a>Administrerede Shifts-forbindelser

Administrerede Shifts-connectors er forbindelser, der er udviklet i samarbejde med vores partnere. Administrerede connectors hostes og administreres enten af os eller vores partnere. Med administrerede connectors kræves der kun minimal konfiguration.

### <a name="microsoft-teams-shifts-connector-for-blue-yonder"></a>Microsoft Teams Shifts-connector til Blue Yonder
<a name="blue_yonder"> </a>

Teams Shifts-connectoren til Blue Yonder er et førstepartstilbud, der hostes og administreres af Microsoft. Med denne connector kan du integrere Skift med Blue Yonder Workforce Management (Blue Yonder WFM) version 2020.3, 2021.1 eller 2021.2 for at administrere dine tidsplaner og holde dem opdateret.  

> [!NOTE]
> Hvis du har Blue Yonder WFM version 2020.3 eller 2021.1, skal du anvende programrettelsen 2020.3.0.4 eller 2021.1.0.3. Denne programrettelse løser et problem, hvor brugerne får en vedvarende fejlmeddelelse i Skift. Det løser også et problem, der forhindrer brugerne i at opdatere deres tilgængelighed i skift.

:::image type="content" source="media/shifts-connector-blue-yonder.png" alt-text="Skærmbillede, der viser en swapanmodning i Skift på en mobilenhed, anmod om godkendelse i Teams på skrivebordet og en tidsplan i Blue Yonder WFM." lightbox="media/shifts-connector-blue-yonder.png":::

Frontlineadministratorer kan:

- Publicer vagter og tidsplaner i Blue Yonder WFM og få dem vist i Skift.
- Opret, administrer og tildel åbne vagter i Blue Yonder WFM og få dem vist i Skift.
- Tildel åbne skiftehold, der blev oprettet i Blue Yonder WFM i skift.
- Opret, rediger og slet fridag i Blue Yonder WFM og få vist i Skift.
- Få vist og godkend tidsplananmodninger fra arbejdere i både Blue Yonder WFM og Skift.
- Angiv og opdater arbejdertilgængelighed i Blue Yonder WFM og få vist i skift.

Frontlinjearbejdere kan:

- Se deres egne og deres teams vagter og tidsplaner i skiftehold.
- Anmod om fridag, åbne vagter og skift i skiftehold.
- Angiv deres tilgængelighed i Skift.

Følgende handlinger understøttes ikke i øjeblikket:

- Tilføj, rediger, slet, gem eller publicer skift i skift.
- Tilføj, rediger, slet, gem eller udgiv fri i Skift.
- Tilføj, rediger, slet, gem eller publicer åbne skift i Skift.

Når en frontlinjeadministrator eller arbejder forsøger at udføre nogen af disse handlinger i Skift, modtager vedkommende en meddelelse om, at handlingen ikke understøttes.

#### <a name="example-scenario"></a>Eksempelscenarie

Eden, leder, publicerer en tidsplan i Blue Yonder WFM, som synkroniseres med Skift i Teams via connectoren. Alex, som er medarbejder, får besked i Teams på sin mobilenhed og ser sin tidsplan og tildelte vagter.

Alex skal tage fri og anmode om en fridag ved hjælp af Skift. Anmodningen sendes til Blue Yonder WFM via connectoren i realtid. Blue Yonder WFM sikrer, at anmodningen overholder forretningsregler, og at anmodningen oprettes. Eden ser og godkender anmodningen i Blue Yonder WFM, og godkendelsen synkroniseres til Teams. (Eden kan også se og godkende anmodningen i Skift). Alex får besked i Teams om, at hans anmodning er godkendt og ser hans opdaterede tidsplan.

Alex vil gerne skifte skiftehold med en kollega. I Skift får Alex vist en liste over alle skiftehold, der er berettiget til en swap baseret på forretningsregler i Blue Yonder WFM. Alex vælger et skiftehold, der i øjeblikket er tildelt Gena. Gena får besked i Teams på deres mobilenhed og accepterer swapanmodningen. Eden ser og godkender anmodningen i Skift, og godkendelsen synkroniseres med Blue Yonder WFM. (Eden kan også se og godkende anmodningen i Blue Yonder WFM). Alex og Gena får besked i Teams og får vist deres opdaterede tidsplaner.

#### <a name="set-up-a-connection"></a>Konfigurer en forbindelse

Integration af Shifts med Blue Yonder WFM ved hjælp af connectoren kræver blot nogle få trin. Du kan bruge guiden Skifts-connector i Microsoft 365 Administration til hurtigt at oprette en forbindelse. Guiden konfigurerer connectoren på baggrund af de indstillinger, du vælger, og opretter forbindelsen. Hvis du foretrækker at bruge PowerShell, leverer vi også PowerShell-scripts, som du kan bruge til at oprette forbindelse.

Du kan finde en trinvis vejledning i:

- [Brug guiden Skifts-connector til at forbinde Shifts med blåt Workforce Management](shifts-connector-wizard.md)
- [Brug PowerShell til at forbinde Skift til Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)

Når en forbindelse er konfigureret, kan du bruge PowerShell til at opdatere og ændre forbindelsesindstillingerne når som helst efter behov. Hvad angår selve connectoren, behøver du ikke at bekymre dig om opgraderinger eller vedligeholdelse. Det tager vi os af.

### <a name="reflexis-shifts-connector-for-microsoft-teams"></a>Reflexis Shifts-connector til Microsoft Teams

Reflexis Shifts-connectoren til Microsoft Teams hostes og administreres af Zebra. Med denne connector kan du integrere Skift med Reflexis WFM-systemet for at administrere dine tidsplaner og holde dem opdateret.

Frontlinjemedarbejdere har adgang til deres tidsplan i Skift i Teams, og deres anmodninger synkroniseres fra Shifts til Reflexis Workforce Scheduler (RWS). Status for anmodninger og skift, der er oprettet i RWS, synkroniseres til Skift i Teams.

:::image type="content" source="media/shifts-connector-reflexis.png" alt-text="Skærmbillede, der viser en liste over vagter på en mobilenhed og en tidsplan i Reflexis." lightbox="media/shifts-connector-reflexis.png":::

Frontlineadministratorer kan:

- Publicer vagter og tidsplaner i Reflexis, og få dem vist i Skift.
- Rediger skift i både Reflexis og Shifts.
- Opret, administrer og tildel åbne skift i både Reflexis og Shifts.
- Få vist og godkend tidsplananmodninger fra arbejdere i både Reflexis og Shifts.

Frontlinjearbejdere kan:

- Se deres egne og deres teams vagter og tidsplaner i skiftehold.
- Anmod om fri, åbne vagter, og byt om på og tilbyt skiftehold i skiftehold.

Du kan få mere at vide ved at gå til https://connect.zebra.com/microsoft-connectors.

## <a name="related-articles"></a>Relaterede artikler

- [Administrer appen Skift](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
