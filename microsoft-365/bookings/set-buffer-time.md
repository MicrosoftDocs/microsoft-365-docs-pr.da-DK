---
title: Angiv buffertid i Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: Angiv buffertid før eller efter en aftale i Microsoft Bookings for at give tid til oprydning eller nulstilling af udstyr.
ms.openlocfilehash: 28d4c7feb76770cb40f5a780c2d406dc3bfeef8d
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714697"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Angiv buffertid i Microsoft Bookings

> [!NOTE]
> Denne artikel hjælper dig med at interagere med den nyeste version af Microsoft Bookings. Tidligere versioner udgår i de kommende måneder.

Nogle af dine aftaler kan kræve tid før eller efter, at du mødes med kunden for at konfigurere, rydde op eller nulstille dit værelse og udstyr. Eller hvis du er på vej mellem kundeaftaler, skal du muligvis bruge tid til at sikre, at du og dit team kan rejse mellem aftaler uden at få kunden til at vente.

Du kan angive buffertid, før aftaler starter, efter aftaler er afsluttet, eller begge dele for at give medarbejderne den ekstra tid, de skal bruge for at forberede sig på deres næste aftale.

## <a name="set-buffer-time-defaults"></a>Angiv standarder for buffertid

Buffertidsstandarden angives på siden **Tjenesteoplysninger** i Bookings. Som alle tjenestestandarder, der er angivet på denne side, kan disse standarder redigeres af dig for en bestemt booking, der opfylder specifikke kundebehov.

Du kan finde buffertidsindstillingen på siden **Tjenesteoplysninger** . Før den kan angives for en given tjeneste, skal du aktivere buffertidsindstillingen ved at vælge buffertidsindstillingen. Dette medfører, at rullemenuerne **Før** og **Efter** vises, som bruges til at vælge den standardmængde af tid, der skal bevares før og efter hver booking, som vist her:

   ![Billede af Bookings med buffertid aktiveret.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Buffertid og -tilgængelighed

Dine kunder kan ikke se og kan ikke ændre de buffertider, du har angivet. Men da buffertiden bruges til at beregne den samlede servicevarighed, ser kunderne dig og dine relevante medarbejdere som booket under både buffer- og almindelige aftaletider. Kunderne kan også kun se tilgængeligheden for dig og dine medarbejdere, hvis der er tid nok til både aftalen og dens buffertid.

En aftale på én time med buffertid på 15 minutter før aftalen kræver f.eks. en tilgængelig tidsblok på mindst 1 time og 15 minutter. En aftale for denne service vil derfor fylde 75 minutters tid i kalenderen og skal bruge 75 minutters tilgængelighed for at booke uden konflikt.
