---
title: Exchange Online overvågning af Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Brug Exchange Online overvågning for oplysninger om mailhændelser eller rådgivning i Microsoft 365.
ms.openlocfilehash: 07d43a6f61ffe3e38f927d47e09d0a9685925f73
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520690"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online overvågning af Microsoft 365

Exchange Online understøtter følgende scenarier på organisationsniveau:

- **Mailklienter**: Du kan få vist tilstand for følgende mailklienter baseret på læseaktivitet for mail:

  - Outlook skrivebord
  - Outlook på internettet
  - Indbyggede mailklienter til iOS og Android
  - Outlook mobilapp i iOS og Android
  - Outlook Mac-klient

   For disse klienter kan du se antallet af aktive brugere i de sidste 30 minutter baseret på brugere, der læser en mail, samt antallet af hændelser og rådgivning i dashboardet. Disse data sammenlignes med det samme interval for den forrige uge for at se, om der er et problem.

   >[!Note]
   > Antallet af aktive brugere måles efter en enkelt aktivitet, f.eks. når en bruger læser en mail. Den tager kun hensyn til de seneste 30 minutters aktivitet.

- **Appforbindelse**: Anslået forbindelse er baseret på procentdelen af vellykkede, forbedrede forbindelser mellem din organisations enheder og Exchange Online og kan omfatte problemer uden for Microsofts kontrol. Du kan få mere at vide [Microsoft 365 Connectivity Optics](microsoft-365-connectivity-optics.md).

- **Grundlæggende godkendelse og moderne godkendelse**: Antallet af brugere er blevet valideret i Exchange Online tjeneste.

- **Mailflow**: Antallet af meddelelser, der blev leveret til en postkasse uden forsinkelse, efter meddelelsen blev nået Microsoft 365 netværket.

- **Åbn Outlook til internettet**: Antallet af brugere er logget på og Outlook på internettet.
  
Her er et eksempel på scenarier på organisationsniveau for Exchange Online på hoveddashboardet.

![Scenarier på organisationsniveau for Exchange Online overvågnings.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

For disse scenarier er de vigtigste tal for de sidste 30 minutter på hoveddashboardet. Detaljerede visninger for hvert af disse scenarier viser næsten realtidstendensen for syv dage med 30-minutters aggregatet sammenlignet med den forrige uge.

![Et eksempel på overvågning af Exchange for levering af mail.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

Du vil bemærke hændelser eller rådgivning, der er oprettet for din organisation med "Problemoprindelse" i meddelelsen, der er mærket som "Din organisation". Disse er meddelelser, der hver især er målrettet din organisation med problemer, der kræver din opmærksomhed for at afhjælpe og løse problemer. Du kan finde flere oplysninger om forskellige typer af problemer, der oprettes og kommunikeres i tjenestestilstand for at informere din organisation om den potentielle virkning, i følgende artikler:

- [Tjenestebeskeder om anvendelsen af postkasse](microsoft-365-mailbox-utilization-service-alerts.md)

- [Tjenestebeskeder om MRS-kildeforsinkelse](microsoft-365-mrs-source-delays-service-alerts.md)

- [Tjenestebeskeder om meddelelser, der afventer levering til eksterne modtagere](microsoft-365-external-recipient-service-alerts.md)

## <a name="priority-accounts-monitoring-scenarios"></a>Overvågningsscenarier for prioritetskonti

Når Exchange Online prioritetskontoovervågning, kan du få vist tilstand for følgende scenarier efter konfiguration af [prioritetskonti](/microsoft-365/admin/setup/priority-accounts):

- Exchange licensering

- Postkasselager

- Meddelelsesgrænse

- Undermapper pr. mappe

- Mappehierarki

- Genoprettelige elementer

Scenariet Exchange licensering kontrollerer, om prioritetskontoen ikke kan logge på på grund af ugyldige licensproblemer, som kan løses af lejeradministratoren.

De resterende fem scenarier ovenfor kontrollerer, om din prioritetskontos postkasse er tæt på at nå eller har nået de grænser, der er [beskrevet i Exchange Online grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

For disse scenarier kan du se aktive og løste rådgivere og hændelser, der påvirker dine prioritetskonti. Identificerbare oplysninger om prioritetskonti vises i oplysningerne om rådgivning eller hændelser sammen med anbefalinger. Her er et eksempel fra siden på **> Tjenestetilstand > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Eksempel på aktive og løste gode råd og hændelser, der påvirker dine prioritetskonti":::

I ruden med den berørte **konto har kolonnen Status** disse værdier:

- Rettet: Problemet, der forårsager, at rådgivningen eller hændelsen er blevet løst for prioritetskontoen. Der er ikke længere et problem. 

- Aktiv: Problemet, der forårsager rådgivningen eller hændelsen, er fortsat for prioritetskontoen. Problemet er der stadig. 

- Forsinket: Problemet, der forårsager, at rådgivningen eller hændelsen ikke er blevet behandlet for prioritetskontoen inden for 96 timer, så det stoppes midlertidigt. Problemet er der stadig. 

Her er et eksempel.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Eksempel på statuskolonnen i den berørte kontorude":::

En vejledning eller hændelse vil blive løst, når ingen konti forbliver i **den aktive** tilstand.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="1-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>1. Antallet af aktive brugere i dashboardet for hver klient ser ud til at være lavt. Vi har mange aktive licenser tildelt til brugere. Hvad betyder det?

Det aktive brugerantal, der vises under overvågning, er baseret på et 30-minutters vindue, hvor brugerne har udført den aktivitet, der er vist i funktionen. Dette må ikke forveksles med brugsnumre. Hvis du vil have vist forbrugsnumre, skal du bruge aktivitetsrapporter Microsoft 365 Administration (<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**ReportsUsage**</a> > ).

### <a name="2-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>2. Hvor er dataene, der anvendes til de scenarier, der viser aktivitetstendenser?

Dataene anvendes i Exchange Online tjeneste. Hvis der sker en fejl, før anmodningen når Exchange Online, eller der er en fejl i Exchange Online, kan du se en fald i aktivitetssignalet.
