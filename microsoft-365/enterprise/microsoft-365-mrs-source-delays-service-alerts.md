---
title: BESKEDER TIL FRU-tjenesten
ms.author: kvice
author: kelleyvice-msft
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
description: Brug beskeder om overførsel af postkasser til at overvåge forsinkelser i anmodninger om migrering af postkasser i din organisation.
ms.openlocfilehash: fe6f60b75fb7d27781d442faf82ff981ac54808a
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810731"
---
# <a name="service-advisories-for-mrs-source-delays-in-exchange-online-monitoring"></a>Tjenestevarsler for fru kildeforsinkelser i forbindelse med overvågning af Exchange Online

Besked om forsinkelsestjeneste for postkassereplikeringstjeneste (MRS) giver dig besked om lagerbegrænsninger eller problemer med høj processorudnyttelse på lejersiden (overførselskilde), der kan forsinke migrering af postkasser i din Microsoft 365 organisation. Disse tjenestemeddelelser indeholder også links til Microsoft-ressourcer, der kan hjælpe dig med at løse disse problemer.

Disse tjenestemeddelelser vises i Microsoft 365 Administration. Hvis du vil have vist disse tjenestemeddelelser, skal <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**du**</a> >  gå til **Tilstand** >  Tjenestetilstand **Exchange Online** og derefter klikke på fanen **Aktive problemer**.

## <a name="what-do-these-service-advisories-indicate"></a>Hvad indikerer disse servicemeddelelser?

Denne tjenestemeddelelse informerer dig om potentielle forsinkelser i migrering af postkasser i din organisation. Dette omfatter migreringer på tværs af områder, onboarding af migreringer og migrering uden for området. Servicemeddelelsen indeholder en tabel med oplysninger om de aktuelle migreringer i din organisation. Her er et eksempel på tabellen med oplysninger om migreringsforsinkelser.

| BatchGuid | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | Navn på ekstern database |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|12345678-1234-1234-1234-1234567891011|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|87654321-4321-4321-4321-1101987654321|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

På følgende liste beskrives hver kolonne i det forrige eksempel.

- **BatchGuid**: Entydigt GUID for overflytningsjobbet.

- **ExchangeGuid**: Det globalt entydige id (GUID) for den brugerpostkasse, der overføres.

- **RequestGuid**: GUID for overflytningsanmodningen.

- **DelayReason**: Årsagen til den forsinkede migrering.

- **QueueHours**: Varigheden af overførslen er sat i kø og venter.

- **DelayInHours**: Varigheden af migreringen er blevet forsinket.

- **SourceServer**: Den lokale server, som overflytningen stammer fra.

- **RemoteDatabaseName**: Det databasenavn, som overflytningen stammer fra.

## <a name="more-information"></a>Flere oplysninger

Du kan få flere oplysninger om migrering af FRU og postkasse i følgende artikler:

- [Postkasse flyttes i Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 og Office 365 overførselsydeevne og bedste praksis](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Ydeevneanalyse af overførsel af postkasse](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Fejlfinding af langsomme migreringer](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Måder at overføre flere mailkonti til Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
