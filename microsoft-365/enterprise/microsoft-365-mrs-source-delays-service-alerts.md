---
title: Beskeder fra MRS-tjenesten
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Brug beskeder om postkasseoverførselstjenesten til at overvåge forsinkelser i postkasseoverførselsanmodninger i organisationen.
ms.openlocfilehash: 25c569030bd5da914dc6eb7ec0e58ebadfe4d766
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63596985"
---
# <a name="service-alerts-for-mrs-source-delays-in-exchange-online-monitoring"></a>Tjenestebeskeder om mrs-kildeforsinkelse i Exchange Online overvågning

MRS-kildeforsinkelsestjenesten (Mailbox Replication Service) informerer dig om lagerbegrænsninger eller problemer med høj processorforbrug på lejersiden (overførselskilde), som kan forsinke postkasseoverflytninger i din Microsoft 365 organisation. Disse serviceadvarsler indeholder også links til Microsoft-ressourcer, der kan hjælpe dig med at løse disse problemer.

Disse serviceadvarsler vises i Microsoft 365 Administration. For at få vist disse serviceadvarsler skal du **gå til HealthService** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**health**</a> >  **Exchange Online** og derefter klikke på **fanen Aktive** problemer.

## <a name="what-do-these-service-alerts-indicate"></a>Hvad angiver disse serviceadvarsler?

Denne tjenestebesked informerer dig om potentielle forsinkelser i postkasseoverflytninger i organisationen. Dette omfatter migrering på tværs af skove, onboarding-migrering og offboarding-migrering. Tjenestebeskeden indeholder en tabel med oplysninger om de aktuelle migreringerne i organisationen. Her er et eksempel på tabellen med oplysninger om forsinkelser i overførslen.

| BatchNavn | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|MRS Migration|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|OVERVÅGNING AF MRS-lejer|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

Følgende liste beskriver hver kolonne i det forrige eksempel.

- **Batchnavn**: Entydigt navn på overførselsjobbet.

- **ExchangeGuid**: GUID (Globally Unique Identifier) (GUID) for den brugerpostkasse, der overføres.

- **RequestGuid**: GUID for overførselsanmodningen.

- **DelayReason**: Årsagen til den forsinkede overførsel.

- **QueueHours**: Den varighed, overførslen er sat i kø og venter.

- **DelayInHours**: Den varighed, overførslen er blevet forsinket.

- **SourceServer**: Den lokale server, som overførslen stammer fra.

- **RemoteDatabaseName**: Det databasenavn, som overførslen stammer fra.

## <a name="more-information"></a>Flere oplysninger

Du kan finde flere oplysninger om MRS- og postkasseoverførsel i følgende artikler:

- [Postkassen flyttes i Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 og Office 365 bedste fremgangsmåder for overførsel](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Analyse af ydeevnen for postkasseoverførsel](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Fejlfinding i forbindelse med langsomme migrering](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Måder at overføre flere mailkonti til Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
