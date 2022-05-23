---
title: Definer dine Bookings servicetilbud
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 4a1c391e-524f-48e0-bef8-185df3a9634b
description: Instruktioner til angivelse af oplysninger om servicetilbud, herunder tjenestenavn, beskrivelse, placering, varighed og priser. Du kan også mærke de medarbejdere, der er kvalificerede til at levere tjenesten.
ms.openlocfilehash: 0c302e8d84274fa2df8eea27362407ded4a468e3
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637775"
---
# <a name="define-your-service-offerings-in-bookings"></a>Definer dine servicetilbud i Bookings

Når du definerer dine servicetilbud i Microsoft Bookings, angiver du et tjenestenavn, en beskrivelse, en placering (vælg, om du vil mødes personligt eller have et onlinemøde), varighed, standardpåmindelser til kunder og medarbejdere, interne noter om tjenesten og priser. Du kan også mærke de medarbejdere, der er kvalificerede til at levere tjenesten. Derefter, når kunderne kommer til din virksomheds hjemmeside for at bestille en aftale, kan de se præcis, hvilke typer af aftaler er tilgængelige, vælge den person, de ønsker at levere tjenesten, og hvor meget deres service vil koste.

Du kan også føje tilpassede oplysninger og URL-adresser til mailbekræftelsen og påmindelser, som du sender, når nogen booker en tjeneste via din bookingside.

## <a name="create-the-service-details"></a>Opret oplysninger om tjenesten

1. I Microsoft 365 skal du vælge appstarteren og derefter vælge **Bookings**.

2. Gå til **Din kalenderTjenester** > **,** og vælg **Tilføj ny tjeneste**.

3. Tilføj dine valg på siden **Grundlæggende oplysninger** .

   **Tjenestenavn**: Angiv navnet på tjenesten. Dette er det navn, der vises i rullemenuen på siden Kalender. Dette navn vises også, når alle manuelt tilføjer en aftale på kalendersiden, og det vises som et felt på siden Selvbetjening.

   **Beskrivelse**: Den beskrivelse, du angiver, er den beskrivelse, der vises, når en bruger klikker på oplysningsikonet på siden Selvbetjening.

   **Standardplacering**: Denne placering er den placering, der vises ved bekræftelses- og påmindelsesmails for både personale og kunder, og den vises i den kalenderbegivenhed, der er oprettet for reservationen.

   **Tilføj onlinemøde**: Denne indstilling aktiverer eller deaktiverer onlinemøder for hver aftale, enten via Teams eller Skype, afhængigt af hvilken du konfigurerer som standardklient for medarbejderen.

   - Aktiveret:
     - Et link til et Teams eller Skype møde, der er unikt for bookingen, føjes til kalenderbegivenheden i både medarbejdernes og kundernes kalendere sammen med opkaldsoplysninger.
     - Linket til at deltage i mødet føjes til alle mails med bekræftelse og påmindelse som vist i følgende eksempel:

       :::image type="content" source="media/bookings-teams-meeting-link.jpg" alt-text="Eksempel på link til at deltage i Teams møde i Bookings.":::

       > [!NOTE]
       > Teams møder kan deltage via Teams mobilapp, Teams desktopapp, i en webbrowser eller via opkaldstelefonen. Vi anbefaler på det kraftigste, at du aktiverer Teams som standardtjenesten til onlinemøder for din lejer for at få den bedste oplevelse med at booke virtuelle aftaler.

   - Deaktiveret:
     - Aftaler indeholder ikke en mødeindstilling, og alle møderelaterede felter, der vises, når **Tilføj onlinemøde** er aktiveret, vises ikke.

   **Varighed**: Dette er, hvor længe alle møder reserveres. Tidspunktet er blokeret fra starttidspunktet, som vælges under reservationen. Den fulde aftaletid blokeres i medarbejdernes kalendere.

   **Buffertid**: Hvis du aktiverer denne indstilling, kan der tilføjes ekstra tid i personalets kalender, hver gang der bestilles en aftale.

   Tidspunktet blokeres for medarbejdernes kalender og påvirker oplysninger om ledig/optaget tid. Det betyder, at hvis en aftale slutter kl. 15.00, og der er føjet 10 minutters buffertid til mødets afslutning, vises medarbejdernes kalender som optaget og ikke-reserverbar indtil kl. 15.10. Dette kan være nyttigt, hvis dine medarbejdere har brug for tid før et møde til at forberede sig, f.eks. en læge, der gennemgår en patients diagram, eller en økonomisk rådgiver, der forbereder relevante kontooplysninger. Det kan også være nyttigt efter et møde, f.eks. når nogen har brug for tid til at rejse til et andet sted.

   **Prisen er ikke angivet**: Vælg de prisindstillinger, der skal vises på siden Self-Service. Hvis **Price ikke er angivet** , vises der ingen pris eller reference til omkostninger eller priser.

   **Bemærk**! Dette felt vises i bookingbegivenheden for det reserverede personale samt den begivenhed, der vises under fanen Kalender i Bookings webapp.

   **Maksimalt antal deltagere pr. begivenhed**: Denne indstilling giver dig mulighed for at oprette tjenester, der kræver mulighed for, at flere personer kan booke den samme aftaletid og det samme personale (f.eks. en fitnessklasse). Aftaletidsslotet for den valgte tjeneste, personale og tid vil være tilgængeligt for at booke, indtil det maksimale antal deltagere, der er angivet af dig, er nået. Den aktuelle aftalekapacitet og de aktuelle deltagere kan ses under fanen Kalender i Bookings webapp.

   :::image type="content" source="media/bookings-maximum-attendees.jpg" alt-text="Eksempel på angivelse af det maksimale antal deltagere i Bookings":::

   **Lad kunden administrere sin booking**: Denne indstilling bestemmer, om kunden kan ændre eller annullere sin booking, forudsat at den er booket via fanen Kalender på Bookings webapp.

   - Aktiveret:

     Knappen **Administrer booking** vises i kundens bekræftelsesmail. Når denne knap vælges af kunden, vises der tre indstillinger:

     - **Omplanlægge** Hvis du vælger denne indstilling, kommer brugeren til en tjenestespecifik Self-Service side, hvor vedkommende kan vælge et nyt tidspunkt og/eller en ny dato for den samme tjeneste og samme medarbejder fra den oprindelige reservation. Bemærk, at selvom den oprindelige medarbejder er knyttet til den omlagte reservation som standard, har brugeren også mulighed for at ændre medarbejderen.
     - **Annuller booking** Dette annullerer reservationen og fjerner den fra personalets kalender.
     - **Ny booking** Denne indstilling fører brugeren til Self-Service side med alle tjenester og personale angivet for at planlægge en ny booking.

        :::image type="content" source="media/bookings-manage-booking-button.jpg" alt-text="Knappen Administrer Bookings i Bookings.":::

      Vi anbefaler kun, at du lader denne indstilling være aktiveret, hvis du er fortrolig med de kunder, der har adgang til siden Self-Service.

   - Deaktiveret:

     Brugeren har ikke mulighed for at omlægge eller annullere sin reservation, når vedkommende booker via fanen Kalender i Bookings webapp. Når du booker via Self-Service side, vil kunderne dog stadig have knappen **Administrer booking** og alle dens muligheder, selvom denne indstilling er deaktiveret.

     Vi anbefaler, at du deaktiverer denne indstilling, hvis du vil begrænse adgangen til Self-Service side. Derudover foreslår vi, at du føjer tekst til din bekræftelse og påmindelsesmails, der fortæller dine kunder, hvordan de kan foretage ændringer af deres booking på andre måder, f.eks. ved at ringe til kontoret eller sende en mail til helpdesk.

4. På siden **Tilgængelighedsindstillinger** kan du se de indstillinger, du har valgt, **på siden Booking** for din planlægningspolitik og tilgængelighed for dine medarbejdere. Du kan få flere oplysninger under [Angiv dine planlægningspolitikker](set-scheduling-policies.md).

5. **Standardpris**  Dette er den pris, der vises på siden Self-Service. Hvis **Price ikke er angivet** , vises der ingen pris eller reference til omkostninger eller priser.

6. **Noter** Dette felt vises i bookingbegivenheden for det reserverede personale samt i den begivenhed, der vises under fanen Kalender i Bookings webapp.

7. **Brugerdefinerede felter** kan være nyttige, når du indsamler oplysninger, der er nødvendige, hver gang den specifikke aftale bestilles. Eksempler omfatter forsikringsudbyder forud for et klinikbesøg, lånetype for lånekonsultationer, større undersøgelse for akademisk rådgivning eller ansøger-id for kandidatinterview. Disse felter vises på siden Booking, når dine kunder bestiller aftaler med dig og dine medarbejdere.

   Kundemail, telefonnummer, adresse og noter er ikke-flytbare felter, men du kan gøre dem valgfrie ved at fravælge **Obligatorisk** ud for hvert felt.

8. På siden **Påmindelser og bekræftelser** kan du konfigurere påmindelser og meddelelser, du sender. Påmindelser og meddelelser sendes til kunder, medarbejdere eller begge dele på et angivet tidspunkt før aftalen. Der kan oprettes flere meddelelser for hver aftale, afhængigt af dine præferencer.

   :::image type="content" source="media/bookings-remind-confirm-2.png" alt-text="En bekræftelsesmail fra Bookings.":::

   Du kan medtage eventuel yderligere tekst, du vil have her, f.eks. oplysninger om omplanlægning, eller hvad kunderne skal medbringe til aftalen. Følgende er et eksempel på brugerdefineret tekst, der er føjet til den oprindelige bekræftelsesmail, i feltet **Yderligere oplysninger om mailbekræftelse** :

   :::image type="content" source="media/bookings-additional-info.jpg" alt-text="Yderligere oplysninger i en Bookings mail.":::

9. **Aktivér sms-beskeder for din kunde** Hvis indstillingen er valgt, sendes SMS meddelelser til kunden, men kun, hvis de tilmelder sig.

   - Tilvalgsfelt for manuel booking og Self-Service side:

     :::image type="content" source="media/bookings-opt-In-boc.jpg" alt-text="Feltet tilvalg i Bookings.":::

   - Sms-meddelelser ser ud på følgende måde (bemærk, at SMS meddelelser i øjeblikket kun er tilgængelige i Nordamerika):

     :::image type="content" source="media/bookings-text-notifications.jpg" alt-text="En tekstmeddelelse fra Bookings.":::

10. **Indstillingerne for standardplanlægning** er som standard slået til. Slå til/fra-knappen fra, hvis du vil tilpasse, hvordan kunder booker en bestemt medarbejder.

11. **Indstillinger for udgivelse** Vælg, om tjenesten skal vises som reserverbar på siden Self-Service, eller om tjenesten kun skal kunne reserveres under fanen Kalender i Bookings Webapp.
