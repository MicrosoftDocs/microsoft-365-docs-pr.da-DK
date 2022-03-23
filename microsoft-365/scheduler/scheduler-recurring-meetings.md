---
title: Planlægning af dynamiske tilbagevendende møder
ms.author: sarichardson
author: sallyri
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.reviewer: strettin
ms.localizationpriority: medium
description: Brugerne kan få mere at vide om planlægning af dynamiske tilbagevendende møder.
ms.openlocfilehash: d4f99b336088e7c565c741a8f631e4fefbada68f
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63593620"
---
# <a name="scheduling-dynamic-recurring-meetings"></a>Planlægning af dynamiske tilbagevendende møder

Schedulers dynamiske møder fungerer omkring brugerens travle tidsplan. Tilbagevendende møder, der administreres af Scheduler, fungerer anderledes end traditionelle tilbagevendende møder i Outlook. Hvis du vil holde din fremtidige kalender åben og minimere konflikter med deltagerne, planlægger Scheduler én forekomst af et tilbagevendende møde ad gangen.

Som et eksempel, der beder Cortana om at "Planlægge 30 minutters fokustid hver dag", oprettes der i første omgang en aftale om 30 minutter til den næste tilgængelige dato i kalenderen.  Når aftaletidspunktet er overskredet, fortsætter Scheduler med at reservere en anden forekomst på følgende dato. Hvis det oprindelige tidsrum ikke er tilgængeligt i øjeblikket, justerer Scheduler tiden ud fra din tilgængelighed.

Den samme heuristiske metode kan anvendes på møder med inviterede. Du kan medtage deltagere i din anmodning og bede Cortana om at "planlægge et møde hver anden uge". Det første og hvert efterfølgende møde planlægges dynamisk baseret på den aktuelle tilgængelighed for alle deltagere i organisationen. Hvis du eller en deltager ikke er til stede på den næste dato, justeres mødetidspunktet automatisk til, hvornår alle er tilgængelige, og den ønskede kadence bevares for følgemødeforekomster baseret på den nyligt planlagte dato.

## <a name="booking-with-attendees-outside-your-organization"></a>Booking med deltagere uden for din organisation

Når du planlægger med deltagere uden for organisationen, sender din virtuelle assistent de eksterne deltagere tidsindstillinger for det første møde. Alle fremtidige møder planlægges automatisk ud fra arrangørens og de interne deltageres tilgængelighed.

Scheduler understøtter daglige, ugentlige og månedlige intervaller.

## <a name="examples-of-how-to-request-recurring-meetings"></a>Eksempler på, hvordan du anmoder om tilbagevendende møder

Her er nogle eksempler på, hvordan du kan sende en mail til Cortana for at planlægge tilbagevendende møder:

- "Cortana, planlæg et møde hver 2. uge."
- "Bog 30 minutter månedligt for en anmeldelse."
- "Cortana finder 30 minutter, så vi kan mødes hver tirsdag."
- "Cortana, planlæg 30 minutter hver fredag kl. 15:30"

## <a name="changing-recurring-frequency"></a>Ændring af tilbagevendende hyppighed

Du kan ændre hyppigheden for et tilbagevendende møde eller et ikke-tilbagevendende møde, der administreres af Scheduler. Svar til Cortana fra den sidste bekræftelsesmail i mødetråden, og fortæl Cortana:

- "Skift dette til én gang hver måned."
- "Cortana, make this meeting biweekly."

## <a name="cancelling-recurring-meetings"></a>Annullere tilbagevendende møder

Du kan svare på Cortanas seneste bekræftelsesmeddelelse og bede om at "annullere dette møde" for at annullere den planlagte forekomst. Men Scheduler fortsætter med at planlægge fremtidige møder med samme hyppighed. Du kan også bare bede Scheduler om at ændre planlægningen af den næste forekomst til den ønskede dato eller det ønskede klokkeslæt. Hvis du vil annullere hele den tilbagevendende serie, skal du svare med "annuller denne serie", og der planlægges ikke fremtidige forekomster.

## <a name="recurring-meeting-limitations"></a>Begrænsninger for tilbagevendende møde

Bemærk, at der er nogle tekniske begrænsninger for, hvilke typer gentagelser Scheduler kan forstå og understøtte:

- Flere forekomster inden for samme interval understøttes ikke (f.eks.: "to gange om ugen").
- Slutdatoer for gentagelse understøttes ikke (f.eks.: "hver dag indtil 20. december"). Da hvert møde er planlagt efter afslutning af det forrige møde, skal du blot svare på den seneste meddelelse fra Cortana med "Annuller denne mødeserie".
- Scheduler understøtter i øjeblikket ikke gentagelsesfrekvenser, der er længere end 90 dage.
