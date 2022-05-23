---
title: Føj brugerdefinerede og obligatoriske spørgsmål til bookingsiden
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: fd6b7587-5055-4bcd-83a4-13bd4929bfff
description: Hvis du har brug for at stille spørgsmål til kunderne, når de bestiller en aftale hos dig online, kan du tilføje brugerdefinerede spørgsmål og påkrævede spørgsmål på bookingsiden.
ms.openlocfilehash: d42f883f3d58882ec5a2e8e8e2bbe7baf7ed3232
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637687"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Føj brugerdefinerede og obligatoriske spørgsmål til bookingsiden

Bookings kan du oprette spørgsmål, som dine kunder kan stille, når de bestiller aftaler. Du kan også vælge, hvilke spørgsmål der kræves.

Du knytter spørgsmålene til en tjeneste, så hver tjeneste kan have forskellige spørgsmål. For eksempel kan en hår stylist spørge kunder, der bestiller en hår farve aftale, hvis de har nogen kendte allergier over for blegemidler eller tonfarver. Dette giver dig og dine kunder mulighed for at spare tid, når de ankommer til deres aftale.

Kunderne får vist de brugerdefinerede spørgsmål, når de opretter deres aftale på bookingsiden. Personalet får vist de brugerdefinerede spørgsmål, når de opretter en ny booking fra Bookings kalender eller når de får vist en eksisterende aftale. Bookings gemmer alle dine spørgsmål på en masterliste, så du ikke behøver at oprette de samme spørgsmål igen for hver tjeneste. Du kan også vælge, om spørgsmål er påkrævede eller valgfrie.

> [!NOTE]
> Kundens svar på spørgsmålene kan ses, når du kigger på kundens aftale i bookingkalenderen.

Du kan få mere at vide om, hvordan du tilpasser og tilpasser din bookingside, på [siden Tilpas din booking](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Føj brugerdefinerede spørgsmål til dine tjenester

1. Log på Microsoft 365, og gå til **Bookings**.

1. Vælg din kalender.

1. Gå til **Tjenester,** og rediger enten en eksisterende tjeneste eller **Tilføj en tjeneste**.

1. Vælg afsnittet **Brugerdefinerede felter** .

   Vi har allerede tilføjet nogle grundlæggende spørgsmål om kundeoplysninger: Kundemail, telefonnummer, kundeadresse og kundenoter. Første gang du gør dette, fremhæves spørgsmålene om kundeoplysninger gråt. Det betyder, at brugeren får vist dette spørgsmål. Hvis du vælger spørgsmålet, forsvinder fremhævningsfeltet omkring det, og din kunde bliver ikke stillet dette spørgsmål.

   I dette eksempel er telefonnummer og kundenoter slået fra, og vi har oprettet to nye brugerdefinerede spørgsmål, der skal stilles.

   ![Billede af skærmen brugerdefinerede spørgsmål.](../media/bookings-questions-custom-fields.png)

1. Hvis du vil gøre spørgsmålet obligatorisk, skal du markere afkrydsningsfeltet **Påkrævet** . Din kunde kan ikke fuldføre reservationen, før vedkommende har besvaret de påkrævede spørgsmål.

1. Hvis du vil oprette et brugerdefineret spørgsmål, skal du vælge **Tilføj et spørgsmål** øverst i panelet. Skriv dit spørgsmål, og vælg derefter **Gem**.

1. Klik på spørgsmålet for at aktivere det. Der vises et fremhævet felt omkring det, og spørgsmålet er aktiveret.

1. Klik på **OK** øverst på siden, og klik derefter **på Gem tjenesten**.

Bookings gemmer alle dine brugerdefinerede spørgsmål på en masterliste, så du nemt kan føje spørgsmål til hver tjeneste uden at skulle skrive de samme spørgsmål gentagne gange. Hvis du f.eks. åbner en anden tjeneste, vises det spørgsmål, du oprettede for den første tjeneste, i afsnittet Brugerdefinerede felter, men det vil blive deaktiveret. Klik på spørgsmålet, så der vises et fremhævet rektangel, og spørgsmålet aktiveres.

I dette eksempel kan du se, at de spørgsmål, der blev tilføjet for den første tjeneste, er tilgængelige for denne tjeneste. Alle spørgsmål, du opretter for denne tjeneste, er tilgængelige for alle tjenester.

   ![Billede af spørgsmål, der vises for flere tjenester.](../media/bookings-questions-services.png)

Hvis din bookingside allerede er publiceret, behøver du ikke at foretage dig andet. Kunderne vil se spørgsmålene, næste gang de booker hos dig. Hvis din bookingside endnu ikke er publiceret, skal du gå til **bookingsiden** fra Outlook på internettet og derefter vælge **Gem og publicer**.

> [!WARNING]
> Du kan også slette spørgsmål fra hovedlisten. Men hvis du sletter et spørgsmål, slettes det fra alle tjenester. Vi anbefaler, at du deaktiverer spørgsmålet ved at vælge det for at sikre, at du ikke påvirker andre tjenester. Du kan se, at et spørgsmål er deaktiveret, hvis det ikke er omgivet af et fremhævet rektangel.

## <a name="customer-experience"></a>Kundeoplevelse

Når dine kunder bestiller en aftale med dig, vises de grundlæggende spørgsmål om kundeoplysninger i afsnittet **Tilføj dine oplysninger** . Alle brugerdefinerede spørgsmål, du tilføjer, findes i afsnittet **Angiv yderligere oplysninger** .

![Billede af, hvad kunder ser, når spørgsmål er aktiveret.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Personaleoplevelse

Når dine kunder bestiller en aftale hos dig, kan dine medarbejdere se spørgsmålene og kundens svar i bookingkalenderen. Hvis du vil se den, **skal du** gå til Bookings \> **kalender** og derefter åbne en aftale.

![Billede af, hvad medarbejderne ser, når spørgsmål er aktiveret.](../media/bookings-questions-staff.png)
