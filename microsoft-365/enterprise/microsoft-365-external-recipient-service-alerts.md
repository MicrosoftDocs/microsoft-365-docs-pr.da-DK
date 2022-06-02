---
title: Tjenestebeskeder for eksterne modtagere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Brug tjenestebeskeder for eksterne modtagere til at overvåge postkasser i venteposition, der når kvoten for postkassen.
ROBOTS: NOINDEX
ms.openlocfilehash: 2eac85b5a4b6f0f1c7c8737041edc9de50b5a074
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840447"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Tjenestebeskeder for meddelelser, der afventer levering til eksterne modtagere i Exchange Online overvågning

Tjenestebeskederne informerer administratorer af mailkøer til eksterne modtagere uden for Exchange Online. Disse beskeder kan kræve afhjælpningshandlinger, der er uden for Microsoft, men de kan give dig de oplysninger, der er nødvendige for at afhjælpe problemet.

Disse tjenestebeskeder vises i Microsoft 365 Administration. Hvis du vil have vist disse tjenestebeskeder, skal <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**du**</a> >  gå til **Tilstand** >  Tjenestetilstand **Exchange Online** og derefter klikke på fanen **Aktive problemer**. Navnet på disse tjenestebeskeder er "Meddelelseskø til eksterne modtagere over tærskler".

![Tjenestebesked om meddelelser, der afventer levering til eksterne modtagere, som vises i Exchange Online overvågningsdashboard.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Når du dobbeltklikker på tjenestebeskeden, vises der en pop op-side, der ligner følgende.

![Indhold i tjenestebeskeden om meddelelser, der afventer levering til eksterne modtagere.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Hvad angiver disse tjenestebeskeder?

Tjenestebeskederne for meddelelser, der afventer levering til eksterne modtagere, informerer dig om, at meddelelser, der sendes til modtagere uden for Exchange Online, kan blive forsinket. Køen af meddelelser kan skyldes dit lokale miljø eller en tredjepartsmeddelelses- eller journalløsning.

Her er nogle almindelige årsager til at sætte meddelelser i kø til eksterne modtagere. De problemer, der forårsager disse tjenestebeskeder, er muligvis ikke begrænset til disse årsager.

- DNS-ændringer

- Høje afsendelsesrater

- MTA (Message Transfer Agents) i det lokale miljø eller journalløsninger med lav eller ingen ledig diskplads

- MTA'er i backpressure

- Netværksproblemer, herunder belastningsjusteringer

- Certifikatproblemer

Hver tjenestebesked indeholder anbefalinger på højt niveau til afhjælpning af problemet. Tjenestebeskeden angiver også antallet af meddelelser, der er sat i kø på beskedtidspunktet, det domæne, hvor meddelelserne er sat i kø, og den SMTP-fejlkode, der er knyttet til de fleste af de meddelelser, der er sat i kø.

Du kan finde flere oplysninger om årsagen til disse tjenestebeskeder [under Mailflow intelligence i Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Denne artikel indeholder også foreslåede handlinger til at løse den egentlige årsag.

> [!NOTE]
> Microsoft kan ikke tage højde for hver SMTP-fejlkode, der leveres af tredjepartsleverandører. Administratorer kan derfor blive bedt om at undersøge fejlkoder, der er specifikke for deres MTA- eller journalingløsninger, som bruges af deres organisation.

## <a name="more-information"></a>Flere oplysninger

Hvis din organisation for nylig har oprettet eller ændret forbindelser til mailflow i din lokale eller Exchange Online organisation, kan du få flere oplysninger i følgende artikler.

- [Konfigurer mailflow ved hjælp af connectors i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Konfigurer forbindelser til distribution af mail](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Bedste praksis for mailflow](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Indsigt i mailflow i Security & Compliance Center](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Sætter indsigt i kø i dashboardet Mailflow](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Spor en mail i Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
