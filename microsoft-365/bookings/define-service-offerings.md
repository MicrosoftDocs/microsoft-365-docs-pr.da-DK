---
title: Definer dine servicetilbud i Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Vejledning til angivelse af oplysninger om tilbuddet, herunder tjenestenavn, beskrivelse, placering, varighed og pris. Du kan også mærke de medarbejdere, der er kvalificeret til at levere tjenesten.
ms.openlocfilehash: 6b276d9ec2d943527f1a6d8ab310fc91406f216c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591431"
---
# <a name="define-your-service-offerings-in-bookings"></a>Definer dine servicetilbud i Bookings

Når du definerer dine servicetilbud i Microsoft Bookings, angiver du et tjenestenavn, en beskrivelse, en placering (vælg, om du vil holde et personligt møde eller holde et onlinemøde), varighed, standardpåmindelser for kunder og personale, interne noter om tjenesten og priser. Du kan også mærke de medarbejdere, der er kvalificeret til at levere tjenesten. Når kunderne derefter kommer til virksomhedens websted for at lave en aftale, kan de se, præcist hvilke typer aftaler er tilgængelige, vælge den person, de vil levere tjenesten til, og hvor meget deres tjeneste koster.

Du kan også føje tilpassede oplysninger og URL-adresser til mailbekræftelsen og påmindelser, som du sender, når nogen reserverer en tjeneste via din bookingside.

## <a name="create-the-service-details"></a>Opret oplysninger om tjenesten

1. I Microsoft 365 skal du vælge Appstarteren og derefter vælge **Bookinger**.

2. Gå til **Indstillinger** ->  [Manager tjenester,](https://outlook.office.com/bookings/settings/services) og vælg **Tilføj ny tjeneste**.

3. Tilføj **dine valg** på siden Grundlæggende detaljer.

   **Tjenestenavn**: Angiv navnet på din tjeneste. Dette er det navn, der vises i rullemenuen på siden Kalender. Dette navn vises også, når alle manuelt tilføjer en aftale på siden Kalender, og den vises som et felt på siden Selvbetjening.

   **Beskrivelse**: Den beskrivelse, du angiver, er, hvad der vises, når en bruger klikker på oplysningsikonet på siden Selvbetjening.

   **Standardplacering**: Denne placering vises i bekræftelses- og påmindelsesmails for både personale og kunder, og den vises i den kalenderbegivenhed, der er oprettet for bookingen.

   **Tilføj onlinemøde**: Denne indstilling aktiverer eller deaktiverer onlinemøder for hver aftale, enten via Teams eller Skype, afhængigt af hvilken du konfigurerer som standardklient for medarbejderen.

   - Aktiveret:
     - Et link til et Teams- eller Skype-møde, som er unikt for bookingen, føjes til kalenderbegivenhed i både medarbejderens og kundens kalendere sammen med opkaldsoplysninger.
     - Linket til at deltage i mødet føjes til alle bekræftelses- og påmindelsesmails, som vist i følgende eksempel:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Eksempel på link til at deltage Teams et møde i Bookings.":::

       > [!NOTE]
       > Teams-møder kan blive forbundet via Teams-mobilappen, Teams-skrivebordsappen, i en webbrowser eller via telefonmøder med manuelt opkald. Vi anbefaler, at du Teams standardtjenesten for onlinemøder for din lejer, så du får den bedste oplevelse med at reservere virtuelle aftaler.

   - Deaktiveret:
     - Aftaler indeholder ikke en mødeindstilling, og alle de møderelaterede felter, der vises, når **Tilføj onlinemøde** er aktiveret, vises ikke.

   **Varighed**: Dette er, hvor længe alle møder reserveres til. Tiden blokeres fra og med starttidspunktet, som er valgt under booking. Det fulde aftaletid blokeres i medarbejderens kalendere.

   **Buffertid**: Hvis du aktiverer denne indstilling, kan der tilføjes ekstra tid i medarbejderens kalender, hver gang en aftale reserveres.

   Tiden blokeres i medarbejderens kalender og påvirker oplysninger om ledig/optaget tid. Det betyder, at hvis en aftale slutter kl. 15:00, og buffertid er føjet til slutningen af mødet, vises medarbejderens kalender som optaget og kan ikke reserveres indtil kl. 15:10. Dette kan være nyttigt, hvis dine medarbejdere skal bruge tid før et møde for at forberede sig, f.eks. en læge, der gennemgår en patients diagram, eller en finansiel rådgiver, der forbereder relevante kontooplysninger. Det kan også være nyttigt efter et møde, f.eks. når en person har brug for tid til at rejse til en anden placering.

   **Prisen er ikke** angivet: Vælg de prisindstillinger, der vises på Self-Service side. Hvis **Ikke angivet pris** er valgt, vises der ingen pris eller reference til omkostninger eller priser.

   **Noter**: Dette felt vises i bookingbegivenhed for reserverede medarbejdere samt under den begivenhed, der vises under fanen Kalender i webappen Bookinger.

   **Maksimalt antal deltagere pr**. begivenhed: Denne indstilling giver dig mulighed for at oprette tjenester, der kræver, at flere personer kan reservere den samme aftale og det samme personale (f.eks. et motionskursus). Tidsrum for aftalen for den valgte tjeneste, det valgte personale og det valgte tidsrum vil være tilgængeligt, indtil det maksimale antal deltagere, som du har angivet, er nået. Den aktuelle aftalekapacitet og deltagere kan vises på fanen Kalender i webappen Bookings.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Eksempel på indstilling af det maksimale antal deltagere i Bookings":::

   **Lad kunden administrere sin booking**: Denne indstilling bestemmer, om kunden kan ændre eller annullere sin booking, forudsat at den er reserveret via fanen Kalender i Webappen Bookings.

   - Aktiveret:

     Knappen **Administrer Booking** vises i mailen med kundebekræftelsen. Når denne knap er valgt af kunden, vises der tre indstillinger:

     - **Omlæg** Hvis du vælger denne indstilling, kommer brugeren til en tjenestespecifik Self-Service-side, hvor brugeren kan vælge et nyt tidspunkt og/eller en ny dato for den samme tjeneste og den samme medarbejder fra den oprindelige booking. Bemærk, at selvom den oprindelige medarbejder som standard er knyttet til den ændrede reservation, har brugeren også mulighed for at ændre medarbejderen.
     - **Annuller booking** Dette annullerer bookingen og fjerner den fra medarbejderens kalender.
     - **Ny booking** Denne indstilling bringer brugeren til siden Self-Service med alle tjenester og personale angivet til planlægning af en ny booking.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Knappen Administrer bookinger i Bookinger.":::

      Vi anbefaler kun, at du lader denne indstilling være aktiveret, hvis du er tryg ved at have kunder, der Self-Service siden.

   - Deaktiveret:

     Brugeren har ingen mulighed for at ændre eller annullere sin booking, når brugeren reserverer via fanen Kalender i Webappen Bookinger. Når du reserverer via Self-Service side, vil kunder dog stadig have knappen **Administrer Booking** og alle dens muligheder, selv når denne indstilling er deaktiveret.

     Vi anbefaler, at du deaktiverer denne indstilling, hvis du vil begrænse adgangen til Self-Service side. Vi anbefaler desuden, at du føjer tekst til dine bekræftelses- og påmindelsesmails, der fortæller dine kunder, hvordan de kan foretage ændringer i deres booking via andre måder, f.eks. ved at ringe til kontoret eller sende en mail til helpdesk.

4. På siden **Tilgængelighedsindstillinger** kan du se de indstillinger, du har valgt fra bookingsiden **for din** planlægningspolitik og tilgængelighed for dine medarbejdere. Få mere at vide under [Angiv dine planlægningspolitikker](set-scheduling-policies.md).

    :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Eksempel på indstilling af det maksimale antal deltagere i Bookings.":::

5. **Standardpris**  Dette er den pris, der vises på Self-Service side. Hvis **Ikke angivet pris** er valgt, vises der ingen pris eller reference til omkostninger eller priser.

6. **Noter** Dette felt vises i bookingbegivenhed for reserveret personale samt i den begivenhed, der vises under fanen Kalender i webappen Bookinger.

7. **Brugerdefinerede felter** kan være nyttige ved indsamling af oplysninger, der er nødvendige, hver gang den bestemte aftale reserveres. Eksempler på dette er forsikringsselskabsudbydere før et besøg, låntype til konsultationer af lån, en omfattende undersøgelse til akademisk rådgivning eller id for kandidater til jobsamtaler. Disse felter vises på Booking-siden, når dine kunder booker aftaler med dig og dine medarbejdere.

   Kundens mail, telefonnummer, adresse og noter er ikke-flytbare felter, men du kan gøre dem valgfri ved at fjerne markeringen **Påkrævet** ud for hvert felt.

8. På siden **Påmindelser og bekræftelser** kan du konfigurere påmindelser og meddelelser, du sender. Påmindelser og meddelelser sendes ud til kunder, medarbejdere eller begge dele på et bestemt tidspunkt før aftalen. Der kan oprettes flere meddelelser for hver aftale efter din præference.

   :::image type="content" source="media/bookings-remind-confirm.jpg" alt-text="En bekræftelsesmail fra Bookings.":::

   Du kan medtage al yderligere tekst, du vil have her, f.eks. oplysninger om omplanlægning eller hvad kunderne skal hente til aftalen. Følgende er et eksempel på tilpasset tekst, der er føjet til den oprindelige bekræftelsesmail, som kan ses i **feltet Yderligere oplysninger om bekræftelse af** mail:

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Yderligere oplysninger i en Bookings-mail.":::

9. **Aktivér sms-beskeder for din kunde** Hvis dette vælges, sendes der sms-beskeder til kunden, men kun hvis kunden tilmelder sig.

   - Feltet Tilmelding på siden manuel reservation og Self-Service siden:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Tilmeldingsfeltet i Bookings.":::

   - Sms-beskeder ser således ud (bemærk, at sms-beskeder i øjeblikket kun er tilgængelige i Nordamerika):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="En sms fra Bookings.":::

10. **Standardplanlægningsindstillingerne** er som standard markeret. Slå til/fra-knappen fra, hvis du vil tilpasse, hvordan kunder reserverer en bestemt medarbejder.

11. **Publiceringsindstillinger** Vælg, om denne tjeneste skal kunne reserveres på siden Self-Service, eller om tjenesten kun skal kunne bookes under fanen Kalender i Webappen Bookings.
