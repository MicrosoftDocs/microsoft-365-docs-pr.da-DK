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
description: Angiv buffertid før eller efter en aftale i Microsoft Bookings for at tillade tid til oprydning eller nulstilling af udstyr.
ms.openlocfilehash: a33159b0b5f168bbb61c88bc9b4181e05c8abbb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590634"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>Angiv buffertid i Microsoft Bookings

Nogle af dine aftaler kan kræve tid før eller efter, at du mødes med din kunde for at konfigurere, rydde op eller nulstille dit lokale og udstyr. Eller hvis du er på farten mellem kundeaftaler, skal du muligvis bruge tid til at sikre, at du og dit team kan rejse mellem aftaler uden at vente med kunden.

Du kan angive buffertid, før aftaler starter, når dine aftaler er slut, eller begge dele for at give medarbejderne den ekstra tid, de skal bruge til at forberede sig på den næste aftale.

## <a name="set-buffer-time-defaults"></a>Angive standardindstillinger for buffertid

Standardindstillingerne for buffertid er angivet på **siden Tjenesteoplysninger** i Bookings. Som alle tjenestestandardindstillinger på denne side kan disse standarder redigeres af dig, så en bestemt booking kan opfylde specifikke kundebehov.

Indstillingen for buffertid kan findes lige under **vælgerne for Standardvarighed** på siden **Oplysninger om** tjeneste. Før den kan indstilles for en given tjeneste, skal du aktivere indstillingen for buffertid ved at vælge til/fra-knappen for buffertid. Dette medfører,  at rullelisten Før og Efter vises, som bruges til at vælge den standardtid, der skal ventes før og efter hver booking, som vist her:

   ![Billede af Bookings med buffertid aktiveret.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>Buffertid og tilgængelighed

Dine kunder kan ikke se og kan ikke ændre de buffertider, du angiver. Men da buffertid bruges til at beregne den samlede tjenestevarighed, vil kunder se dig og dine relevante medarbejdere som reserveret på både buffer- og almindelige aftaletider. Kunder kan også kun se tilgængeligheden for dig og dine medarbejdere, hvis der er tilstrækkelig tid til både aftalen og dens buffertid.

Som et eksempel kræver en en-timers aftale med en 15-minutters buffertid før aftalen en tilgængelig tidsblok på mindst 1 time og 15 minutter. En aftale for denne tjeneste udfylder derfor en 75-minutters periode i din kalender og skal bruge 75 minutters tilgængelighed for at reservere uden konflikt.
