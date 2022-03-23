---
title: Anerkend en meddelelse om venteposition
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Lær at bruge Advanced eDiscovery til at sende og følge op på meddelelser om retslig venteposition via mail samt overvåge forpligtelsesstatus.
ms.openlocfilehash: 57cda6e88968fc90845965a8554f55d80bd3ded0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588704"
---
# <a name="acknowledge-a-hold-notification"></a>Anerkend en meddelelse om venteposition

Når du besvarer en lovgivningsmæssig anmodning eller undersøgelse, kan det være påkrævet, at du informerer personer, der er ansvarlige for deres forpligtelse til at opbevare elektronisk gemte oplysninger (ESI) og alt materiale, der kan være relevant for en aktiv eller umiddelbart for sen juridisk sag. Når de er sendt, skal juridiske teams vide, at hver vagtleder har modtaget, læst, forstået og accepteret at følge de angivne instruktioner.

For at reducere tid, omkostninger og anstrengelser for at følge op med dine Advanced eDiscovery giver Advanced eDiscovery dig mulighed for at sende og følge op på meddelelser om retsligt hold via mail. Ud over mailbeskeder har hver hjælper at få adgang til en individuel overholdelsesportal, så hjælpere, der kan hjælpe med at blive holdt orienteret om ændringer af deres status for forpligtelse.

## <a name="email-notifications"></a>Mailbeskeder

Når en meddelelse om retsligt hold er blevet udstedt, modtager hver enkelt meddelelse om retslig venteposition en unik og personlig mail, der indeholder din definerede meddelelse om retslig venteposition og tilføjede instruktioner. 

> [!TIP]
> Se, hvordan du kan bruge den indbyggede  [Kommunikationseditor](using-communications-editor.md) til at give dine brugere tilladelse til at anerkende deres meddelelse eller få adgang til deres overholdelsesportal direkte fra deres mail.

Baseret på konfigurationen af din meddelelse om retslig venteposition kan dine selvtere modtage følgende meddelelser: 

- **Meddelelse om udstedelse:** Den første meddelelse, der sendes til din vagtleder. Denne meddelelse indeholder dine udsendelsesinstruktioner og meddelelsen om venteposition, som er føjet til slutningen af meddelelsen.

- **Påmindelsesmeddelelse:** Hvis denne indstilling er aktiveret, sendes der en påmindelsesmeddelelse til dine ydvntere baseret på den angivne hyppighed og det angivne interval. Påmindelserne vil fortsat blive sendt, enten indtil vagten har bekræftet sin meddelelse, eller indtil antallet af påmindelser er opbrugt.

- **Eskaleringsmeddelelse:** Hvis denne indstilling er aktiveret, sendes en eskaleringsmeddelelse til din vagtchef og dennes leder, når påmindelsesmeddelelsen er opbrugt. Systemet vil automatisk sende eskaleringsbeskeder, indtil det angivne antal eskaleringer er gennemført, eller indtil den din besked om venteposition er bekræftet.

- **Meddelelse igen:** Hvis indholdet af den ventende meddelelse opdateres i løbet af en undersøgelse, sendes den opdaterede meddelelse automatisk til den, der er vagtleder.

- **Meddelelse om udgivelse:** Når en vagter frigives fra sagen, får de tilsendt en meddelelse om frigivelsen. 

## <a name="compliance-portal"></a>Overholdelsesportal

Ud over mailmeddelelser har hver enkelt hjælper adgang til en unik overholdelsesportal. Via portalen kan hver deltager se, få adgang til og anerkende deres aktive meddelelser om venteposition.

![Overholdelsesportal for en kontrollerende bruger.](../media/CustodianPortal.jpg)
