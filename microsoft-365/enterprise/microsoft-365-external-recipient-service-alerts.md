---
title: Beskeder om tjenesten eksterne modtagere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
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
description: Brug beskeder fra tjenesten eksterne modtagere til at overvåge postkasser i venteposition, der når deres postkassekvote.
ms.openlocfilehash: 8db8e090ec5430f13153bc3edf5b3315c041d9cf
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568000"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>Tjenestebeskeder om meddelelser, der afventer levering til eksterne modtagere Exchange Online overvågning

Tjenesten informerer administratorer om kø til eksterne modtagere uden for Exchange Online. Disse beskeder kræver muligvis afhjælpningshandlinger, der er uden for Microsoft, men de kan give dig de oplysninger, der er nødvendige for at afhjælpe dem.

Disse serviceadvarsler vises i Microsoft 365 Administration. Hvis du vil have vist disse tjenesteadvarsler > , <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**skal Tjenestetilstand**</a> >  **Exchange Online** og derefter klikke **på fanen Aktive** problemer. Navnet på disse serviceadvarsler er "Meddelelse i kø til eksterne modtagere over tærskelværdier".

![Tjenestebesked for meddelelser, der venter på levering til eksterne modtagere, der vises i Exchange Online dashboardet for overvågning.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

Når du dobbeltklikker på tjenestebeskeden, vises en pop op-side, der ligner følgende.

![Indhold i tjenestebeskeden for meddelelser, der venter på levering til eksterne modtagere.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>Hvad angiver disse serviceadvarsler?

Tjenestens beskeder om meddelelser, der venter på levering til eksterne modtagere, informerer dig om, at meddelelser, der er bestemt til modtagere uden for Exchange Online, kan blive forsinket. Køen af meddelelser kan skyldes dit lokale miljø eller en besked- eller journalløsning fra en tredjepart.

Her er nogle almindelige årsager til at sætte meddelelser i kø til eksterne modtagere. Men de problemer, der forårsager disse serviceadvarsler, er muligvis ikke begrænset til disse årsager.

- DNS-ændringer

- Unødvendige afsendelsestakster

- Lokale MTA-løsninger (Message Transfer Agents) eller journaliseringsløsninger med lav til ingen ledig diskplads

- MTAs i backpressure

- Netværksproblemer, herunder belastningsbalancer

- Certifikatproblemer

Hver tjenesteadvarsel indeholder anbefalinger på højt niveau til afhjælpning af problemet. Tjenesteadvarslen angiver også antallet af meddelelser, der er sat i kø på tidspunktet for beskeden, det domæne, hvor meddelelserne er i kø, og SMTP-fejlkoden, der er knyttet til de fleste af meddelelserne i kø.

Du kan finde flere oplysninger om den egentlige årsag til disse tjenestebeskeder i [Mailflow intelligence Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). Denne artikel indeholder også forslag til handlinger, der kan løse den egentlige årsag.

> [!NOTE]
> Microsoft kan ikke tage højde for hver SMTP-fejlkode, der leveres af tredjepartsleverandører. Derfor kan administratorer være nødvendige for at undersøge fejlkoder, der er specifikke for deres MTA- eller journaliseringsløsninger, der bruges af deres organisation.

## <a name="more-information"></a>Flere oplysninger

Hvis din organisation for nylig har oprettet eller ændret mailflow-forbindelser i din lokale eller lokale Exchange Online, kan du finde flere oplysninger i følgende artikler.

- [Konfigurer mailflow ved hjælp af forbindelser i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [Konfigurer forbindelser til at distribuere mail](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [Bedste fremgangsmåder for mailflow](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [Indsigt i mailflow i Security & Compliance Center](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [Indsigt i køen i dashboardet for mailflow](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [Spore en mail i Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
