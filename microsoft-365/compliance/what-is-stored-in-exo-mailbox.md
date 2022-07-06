---
title: Indhold, der er gemt i Exchange Online postkasser
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Indhold, der er produceret af cloudbaserede apps i Microsoft 365, gemmes eller knyttes til en brugers Exchange Online postkasse. Der kan søges i dette indhold ved hjælp af Microsoft eDiscovery-værktøjer.
ms.openlocfilehash: a5006721166a2f56d8abae9b79442f4ad93276a4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641048"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Indhold, der er gemt i Exchange Online postkasser til eDiscovery

En postkasse i Exchange Online bruges primært til at gemme mailrelaterede elementer, f.eks. meddelelser, kalenderelementer, opgaver og noter. Men det ændrer sig, efterhånden som flere cloudbaserede apps også gemmer deres data i en brugers postkasse. En fordel ved at gemme data i en postkasse er, at du kan bruge søgeværktøjerne i indholdssøgning, Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium) til at finde, få vist og eksportere dataene fra disse cloudbaserede apps. Dataene fra nogle af disse apps gemmes i skjulte mapper, der er placeret i et undertræ for en ikke-interpersonel meddelelse (ikke-IPM) i postkassen. Data fra andre cloudbaserede apps gemmes muligvis ikke _i_ postkassen, men de er _knyttet til_ postkassen og returneres i søgninger (hvis disse data stemmer overens med søgeforespørgslen). Uanset om skybaserede data er gemt i eller tilknyttet en brugerpostkasse, er dataene normalt ikke synlige i en mailklient, når en bruger åbner sin postkasse.

I følgende tabel vises de apps, der enten gemmer eller knytter data til en cloudbaseret postkasse. I tabellen beskrives også den type indhold, som hver app producerer.

<br>

****

|Microsoft 365-app|Beskrivelse|
|---|---|
|Former<sup>*</sup>|Formularer og svar på en formular gemmes i filer, der er knyttet til mails, og gemmes i en skjult mappe i postkassen for den bruger, der oprettede formularen. Formularer, der er oprettet før april 2020, gemmes som en PDF-fil. Formularer, der oprettes efter 2020, gemmes som en JSON-fil. Svar på en formular gemmes i en CSV-fil. Når du eksporterer indhold fra formularer i en PST-fil, er disse data placeret i mappen **ApplicationDataRoot** i en undermappe med navnet med følgende globalt entydige identificerede (GUID): **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Microsoft 365-grupper|Mails, kalenderelementer, kontakter (Personer), noter og opgaver gemmes i den postkasse, der er knyttet til en Microsoft 365-gruppe.|
|Outlook/Exchange Online|Mails, kalenderelementer, kontakter (Personer), noter og opgaver gemmes i en brugers postkasse.|
|Mennesker|Kontakter i appen Personer (som er de samme kontakter som dem, der er tilgængelige i Outlook) gemmes i en brugers postkasse.|
|Klasseplan|Planer, der er oprettet i klasseplanen, gemmes i postkassen for den tilsvarende Microsoft 365-gruppe, der klargøres, når der oprettes en ny plan. Aliasset for gruppepostkassen er navnet på planen.|
|Skype for Business|Samtaler i Skype for Business gemmes i mappen Samtaleoversigt i en brugers postkasse. Hvis postkassen for en deltager i et Skype-møde er sat i venteposition for procesførelse eller tildelt en opbevaringspolitik, bevares filer, der er knyttet til et møde, i deltagerpostkassen.|
|Sway<sup>*</sup>|Sways gemmes som en HTML-fil, der er knyttet til en mail, og gemmes i en skjult mappe i postkassen for den bruger, der oprettede swayen. Når du eksporterer indhold fra Sway i en PST-fil, er disse data placeret i mappen **ApplicationDataRoot** i en undermappe med navnet med følgende GUID: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Opgaver|Opgaver i appen Opgaver (som er de samme opgaver som dem, der er tilgængelige i Outlook) gemmes i en brugers postkasse.|
|Teams|Samtaler, der er en del af en Teams-kanal, er knyttet til Teams-postkassen. Samtaler, der er en del af chatlisten i Teams (også kaldet *1 x N-chats*), er knyttet til postkassen for de brugere, der deltager i chatten. Oversigtsoplysninger for møder og opkald i en Teams-kanal er også knyttet til postkasser for brugere, der ringede til mødet eller opkaldet. Så når du søger efter Teams-indhold, skal du søge i Teams-postkassen efter indhold i kanalsamtaler og søge i brugerpostkasser efter indhold i 1 x N-chats.|
|To-Do|Opgaver (kaldet *opgaver*, der gemmes på opgavelister) i To-Do-appen gemmes i en brugers postkasse.|
|Yammer|Samtaler og kommentarer i et Yammer-community er knyttet til Microsoft 365-gruppepostkassen samt brugerens postkasse for forfatteren og eventuelle navngivne modtagere (@ nævnte eller Cc'ed-brugere). Private meddelelser, der sendes uden for et Yammer-community, gemmes i postkassen for de brugere, der deltager i den private meddelelse.|
|

> [!NOTE]
> <sup>*</sup> Hvis en venteposition på nuværende tidspunkt er placeret i en postkasse (ved hjælp af ventepositioner i sager med eDiscovery (Standard) eller eDiscovery (Premium), bevares indhold fra denne app ikke af ventepositionen.
