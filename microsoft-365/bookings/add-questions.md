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
description: Hvis du har brug for at stille kunder spørgsmål, når de reserverer en aftale med dig online, kan du tilføje brugerdefinerede spørgsmål og obligatoriske spørgsmål til bookingsiden.
ms.openlocfilehash: d7d997ff02e2a6b8d849cb50014924733bac8e32
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589798"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Føj brugerdefinerede og obligatoriske spørgsmål til bookingsiden

Bookings gør det muligt at oprette spørgsmål, som dine kunder kan stille, når de reserverer aftaler. Du kan også vælge, hvilke spørgsmål der kræves.

Du knytter spørgsmålene til en tjeneste, så hver tjeneste kan have forskellige sæt spørgsmål. En hair stylist kan f.eks. spørge kunder, der reserverer en aftale om farvelægning af frisører, hvis de har kendte allergier til patienter eller tonfarver. Det giver dig og dine kunder mulighed for at spare tid, når de når frem til deres aftale.

Kunderne får vist de brugerdefinerede spørgsmål, når de opretter deres aftale på bookingsiden. Medarbejdere får vist de brugerdefinerede spørgsmål, når de opretter en ny booking fra Bookings-kalenderen, eller når de får vist en eksisterende aftale. Bookings gemmer alle dine spørgsmål til en hovedliste, så du ikke behøver at oprette de samme spørgsmål for hver tjeneste igen. Du kan også vælge, om spørgsmål er påkrævede eller valgfrie.

> [!NOTE]
> Kundens svar på spørgsmålene kan ses, når du kigger på deres aftale i bookingkalenderen.

Du kan finde flere oplysninger om, hvordan du tilpasser og tilpasser din bookingside, [under Tilpas din bookingside](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Føj brugerdefinerede spørgsmål til dine tjenester

1. Log på Microsoft 365 og gå til **Bookings**.

1. Gå til **Tjenester** , og rediger enten en eksisterende tjeneste eller **Tilføj en tjeneste**.

1. Rul ned til **sektionen Brugerdefinerede** felter, og vælg derefter **Rediger**.

   Vi har allerede tilføjet nogle grundlæggende spørgsmål om kundeoplysninger: kundemail, telefonnummer, kundeadresse og kundenoter. Første gang du gør dette, er spørgsmålene om kundeoplysninger fremhævet med gråt. Det betyder, at brugeren får vist dette spørgsmål. Hvis du vælger spørgsmålet, forsvinder det fremhævningsfelt omkring det, og din kunde vil ikke blive stillet dette spørgsmål.

   I dette eksempel er telefonnummer og kundenoter blevet slået fra, og vi har oprettet to nye brugerdefinerede spørgsmål, vi kan stille.

   ![Billede af skærmen brugerdefinerede spørgsmål.](../media/bookings-questions-custom-fields.png)

1. Hvis du vil gøre spørgsmålet obligatorisk, skal du markere **afkrydsningsfeltet** Påkrævet. Din kunde kan ikke gennemføre bookingen, før de har besvaret de nødvendige spørgsmål.

1. Hvis du vil oprette et brugerdefineret spørgsmål, **skal du vælge** Tilføj et spørgsmål øverst i panelet. Skriv dit spørgsmål, og vælg derefter **Gem**.

1. Klik på spørgsmålet for at aktivere det. Der vises et fremhævet felt omkring det, og spørgsmålet er aktiveret.

1. Klik **på OK** øverst på siden, og **gem derefter tjenesten**.

Bookings gemmer alle dine brugerdefinerede spørgsmål på en hovedliste, så du nemt kan tilføje spørgsmål til hver enkelt tjeneste uden at skulle skrive de samme spørgsmål gentagne gange. Hvis du f.eks. åbner en anden tjeneste, vises det spørgsmål, du oprettede for den første tjeneste, i sektionen Brugerdefinerede felter, men det vil være deaktiveret. Klik på spørgsmålet, så der vises et fremhævet rektangel, og spørgsmålet er aktiveret.

I dette eksempel kan du se, at de spørgsmål, der blev tilføjet for den første tjeneste, er tilgængelige for denne tjeneste. De spørgsmål, du opretter til denne tjeneste, vil være tilgængelige for alle tjenester.

   ![Billede af spørgsmål, der vises for flere tjenester.](../media/bookings-questions-services.png)

Hvis din bookingside allerede er publiceret, behøver du ikke at gøre mere. Kunder får vist spørgsmålene, næste gang de reserverer hos dig. Hvis din bookingside ikke er publiceret endnu, skal du gå til **bookingsiden** fra Outlook på internettet og derefter vælge **Gem og publicer**.

> [!WARNING]
> Du kan også slette spørgsmål fra hovedlisten. Men hvis du sletter et spørgsmål, bliver det slettet fra alle tjenester. Vi anbefaler, at du deaktiverer spørgsmålet ved at vælge det for at sikre, at du ikke påvirker andre tjenester. Du kan se, at et spørgsmål er deaktiveret, hvis det ikke er omgivet af et fremhævet rektangel.

## <a name="customer-experience"></a>Kundeoplevelse

Når dine kunder reserverer en aftale med dig, vises spørgsmålene om de grundlæggende kundeoplysninger i **sektionen Tilføj dine** oplysninger. Eventuelle tilpassede spørgsmål, du tilføjer, findes i **sektionen Angiv yderligere** oplysninger.

![Billede af, hvad kunderne ser, når spørgsmål er aktiveret.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Personaleoplevelse

Når dine kunder reserverer en aftale med dig, vil dine medarbejdere se spørgsmålene og kundens svar i bookingkalenderen. Du kan se den ved at gå **til Bookings-kalender** \> og derefter åbne en aftale.

![Billede af, hvad medarbejdere ser, når spørgsmål er aktiveret.](../media/bookings-questions-staff.png)
