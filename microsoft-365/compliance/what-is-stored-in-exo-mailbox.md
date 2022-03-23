---
title: Indhold, der er gemt Exchange Online postkasser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ''
description: Indhold, der er produceret af skybaserede apps i Microsoft 365, gemmes eller er knyttet til en Exchange Online postkasse. Der kan søges i dette indhold ved hjælp af Microsoft eDiscovery-værktøjer.
ms.openlocfilehash: f7db327d21928df925bfd6451226ab96782d715b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589155"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Indhold gemt i Exchange Online til eDiscovery

En postkasse i Exchange Online primært bruges til at gemme mailrelaterede elementer som meddelelser, kalenderelementer, opgaver og noter. Men det ændrer sig i og med, at flere skybaserede apps også gemmer deres data i en brugers postkasse. En af fordelene ved at gemme data i en postkasse er, at du kan bruge søgeværktøjerne i indholdssøgning, Grundlæggende eDiscovery og Advanced eDiscovery til at finde, få vist og eksportere data fra disse skybaserede apps. Dataene fra nogle af disse apps er gemt i skjulte mapper, der er placeret i et undertræ i postkassen, som ikke er mellempersonlige meddelelser (ikke IPM). Data fra andre skybaserede apps gemmes muligvis ikke i postkassen, men er knyttet til postkassen  og returneres i søgninger (hvis disse data svarer til søgeforespørgslen). Uanset om skybaserede data er gemt i eller knyttet til en brugerpostkasse, er dataene typisk ikke synlige i en mailklient, når en bruger åbner sin postkasse.

I følgende tabel vises de apps, der enten gemmer eller knytter data til en skybaseret postkasse. Tabellen beskriver også den type indhold, der frembringes af hver app.

<br>

****

|Microsoft 365 app|Beskrivelse|
|---|---|
|Formularer<sup>*</sup>|Formularer og svar på en formular gemmes i filer, der er vedhæftet mails, og som gemmes i en skjult mappe i postkassen for den bruger, der har oprettet formularen. Formularer, der er oprettet før april 2020, gemmes som en PDF-fil. Formularer, der er oprettet efter 2020, gemmes som en JSON-fil. Svar på en formular gemmes i en CSV-fil. Når du eksporterer indhold fra Forms i en PST-fil, er disse data placeret i mappen **ApplicationDataRoot** i en undermappe navngivet med følgende globalt entydige identificerede (GUID): **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Microsoft 365 grupper|Mails, kalenderelementer, kontakter (Personer), noter og opgaver gemmes i den postkasse, der er knyttet til en Microsoft 365 gruppe.|
|Outlook/Exchange Online|Mails, kalenderelementer, kontakter (Personer), noter og opgaver gemmes i en brugers postkasse.|
|Personer|Kontakter i appen Personer (som er de samme kontakter som dem, der er tilgængelige i Outlook) gemmes i en brugers postkasse.|
|Klasseplan|Planer, der er oprettet i klassetidsplan, gemmes i postkassen for de tilsvarende Microsoft 365 grupper, der er klargjort, når der oprettes en ny plan. Aliasset for gruppepostkassen er navnet på planen.|
|Skype for Business|Samtaler i Skype for Business gemmes i mappen Samtaleoversigt i en brugers postkasse. Hvis en deltagers postkasse i et Skype-møde er sat i retslig tilbageholdelse eller tildelt en opbevaringspolitik, bevares de filer, der er vedhæftet et møde, i deltagerpostkassen.|
|Sway<sup>*</sup>|Swayer gemmes som en HTML-fil, der er vedhæftet en mail og gemmes i en skjult mappe i postkassen for den bruger, der har oprettet swayen. Når du eksporterer indhold fra Sway i en PST-fil, er disse data placeret i mappen **ApplicationDataRoot** i en undermappe, der er navngivet med følgende GUID: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Opgaver|Opgaver i appen Opgaver (som er de samme opgaver som dem, der er tilgængelige i Outlook) gemmes i en brugers postkasse.|
|Teams|Samtaler, der er en del af en Teams kanal, er knyttet til Teams postkasse. Samtaler, der er en del af chatlisten i Teams (også kaldet *1 x N-chatsamtaler*), er knyttet til postkassen for de brugere, der deltager i chatten. Desuden er oversigtsoplysninger om møder og opkald i en Teams-kanal knyttet til postkasser for brugere, der ringede til mødet eller opkaldet. Så når du søger Teams indhold, skal du søge i Teams-postkassen efter indhold i kanalsamtaler og søge i brugerpostkasser efter indhold i 1 x N-chats.|
|To-Do|Opgaver (kaldet opgaver, som er gemt på opgavelister) i To-Do gemmes i en *brugers* postkasse.|
|Yammer|Samtaler og kommentarer i et Yammer-community er knyttet til Microsoft 365-gruppepostkassen samt brugerpostkassen for forfatteren og eventuelle navngivne modtagere (@omtaler eller Cc'er brugere). Private meddelelser, der sendes uden for Yammer et community, gemmes i postkassen for de brugere, der deltager i den private meddelelse.|
|

> [!NOTE]
> <sup>*</sup>Hvis en venteposition er sat i venteposition i en postkasse (ved hjælp af venteposition i Core eDiscovery- eller Advanced eDiscovery-sager), bevares indhold fra denne app ikke af ventepositionen.
