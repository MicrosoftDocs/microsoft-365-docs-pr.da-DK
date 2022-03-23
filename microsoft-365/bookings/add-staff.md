---
title: Føj personale til Bookinger
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Brug denne side til at oprette en personaleliste og administrere medarbejderoplysninger som f.eks. navn, telefonnummer og mailadresse.
ms.openlocfilehash: 03ebf5c21e40d53e87067866e05fc37c2c255331
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63589799"
---
# <a name="add-staff-to-bookings"></a>Føj personale til Bookinger

På siden Personale i Bookings kan du oprette din personaleliste og administrere medarbejderoplysninger som f.eks. navn, telefonnummer og mailadresse. Du kan også angive arbejdstider for hver medarbejder herfra.

## <a name="before-you-begin"></a>Før du begynder

Selvom Bookings er en funktion i Microsoft 365, er det ikke alle dine medarbejdere, der skal have en Microsoft 365 konto. Alle medarbejdere skal have en gyldig mailadresse, så de kan modtage bookinger og planlægge ændringer.

## <a name="watch-add-your-staff-to-bookings"></a>Se: Føj dine medarbejdere til Bookings

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Trin

> [!NOTE]
> Disse trin er endnu ikke tilgængelige i den nye Bookings-oplevelse.

1. Gå til siden [Administrer personale,](https://outlook.office.com/bookings/staff) og vælg **Tilføj personale**

2. Vælg **knappen Tilføj** personale.

3. Når du tilføjer medarbejdere fra din organisation, skal du skrive deres navn  i feltet Tilføj personer og vælge dem, når de vises i rullemenuen. De andre felter udfyldes automatisk.

    Når en medarbejder er tilføjet, kan du redigere det navn, der vises på alle Bookings-kommunikationer, ved at vælge **x** ud for deres navn og redigere **feltet Tilføj** personer. Dette kan være nyttigt, hvis medarbejdere skal have en bestemt titel eller et bestemt navn vist for kunder, f.eks. som "Dr. Vance, MD".

4. Hvis du vil tilføje medarbejdere uden for organisationen, skal du manuelt udfylde deres mail og andre oplysninger.

    > [!NOTE]
    > Medarbejdere uden for din lejer vil ikke kunne dele oplysninger om ledig/optaget tid med Bookings.

5. Vælg en rolle for hver medarbejder: Administrator, Fremviser eller Gæst.
    - **Administratorer** kan redigere alle indstillinger, tilføje og fjerne medarbejdere samt oprette, redigere eller slette bookinger.
    - **Brugere kan** se alle bookinger i kalenderen, men de kan ikke ændre eller slette dem. De har skrivebeskyttet adgang til indstillinger.
    - **Gæster** kan tildeles bookinger, men de kan ikke åbne bookingpostkassen.

6. Vælg **Underret alle medarbejdere via mail, når en booking tildelt til dem oprettes eller ændres for** at aktivere medarbejdermails. Følgende er et eksempel på en mail:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="En mail fra Bookings.":::

7. Vælg **Begivenheder på Office 365 påvirker** tilgængelighed, hvis du vil have oplysninger om ledig/optaget tid fra medarbejdernes kalendere til at påvirke tilgængelighed for bookingtjenester via Bookings.

    Hvis en medarbejder f.eks. har et teammøde eller en personlig aftale, der er planlagt til kl. 17 om onsdagen, viser Bookings, at medarbejderen ikke kan reserveres i det tidsrum. Denne tid vises som optaget eller foreløbig i Bookings-kalendervisningen, som vist i nedenstående eksempel.

    :::image type="content" source="media/bookings-busy-tentative-view.jpg" alt-text="En visning af en Bookings-kalender.":::

> [!IMPORTANT]
> Vi anbefaler kraftigt, at du lader denne indstilling være slået til (den er slået til som standard) for at undgå dobbeltbooking og for at optimere dine medarbejderes tilgængelighed.

8. Vælg **Brug åbningstider for** at angive, at alle de tidspunkter, der kan reserveres, kun skal være inden for den arbejdstid, du  har angivet i sektionen Åbningstider på siden Firmaoplysninger.

    Ved at fjerne markeringen af dette felt kan medarbejdere få brugerdefinerede timer, som yderligere begrænser, hvornår de kan reserveres. Dette er nyttigt i scenarier, hvor en medarbejder kun kan være på webstedet tirsdage og onsdage, eller de dedikerer deres morgener til én type aftaler og deres aftener til andre typer.

    > [!NOTE]
    > Bookings understøtter op til 100 medarbejdere i en Bookings-kalender.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Gør en Bookings-bruger til superbruger uden at tilføje vedkommende som personale i Bookings

Det kan være en god ide at føje en person til din personaleliste i Bookings uden at gøre dem tilgængelige for kunder eller kunder. Når du gør brugeren til superbruger, bliver vedkommende administrator for bookingpostkassen. At være administrator for en bookingpostkasse er defineret som at have fuld adgang og send-som-tilladelser til bookingpostkassen.

> [!NOTE]
> Disse trin fungerer kun, hvis den bruger, der tilføjes, ikke allerede er tildelt **en seerrolle** i Bookings.

1. [Forbind til Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Brug PowerShell til at tildele fuld adgang med følgende kommandoer:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Og kør derefter denne kommando for at tildele Send-som-tilladelser.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Her er et eksempel på en PowerShell-kommando til at føje Allie Bellew til Contoso dayposition-bookingpostkassen.

1. Kør først denne kommando:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Kør derefter denne kommando:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** har nu administratoradgang, men vises ikke som personale, der kan reserveres, i Bookings.
