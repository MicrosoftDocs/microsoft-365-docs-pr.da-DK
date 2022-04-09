---
title: Føj medarbejdere til Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Brug denne side til at oprette din personaleliste og til at administrere medarbejderoplysninger, f.eks. navn, telefonnummer og mailadresse.
ms.openlocfilehash: ca938acf4bfb567d366c7ffd684e8bce8c9eea74
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746788"
---
# <a name="add-staff-to-bookings"></a>Føj medarbejdere til Bookings

> [!NOTE]
> Denne artikel hjælper dig med at interagere med den nyeste version af Microsoft Bookings. Tidligere versioner udgår i de kommende måneder.

På siden Personale i Bookings kan du oprette din personaleliste og administrere medarbejderoplysninger, f.eks. navn, telefonnummer og mailadresse. Du kan også angive arbejdstimer for hver medarbejder herfra.

## <a name="before-you-begin"></a>Før du begynder

Selvom Bookings er en funktion i Microsoft 365, er det ikke alle dine medarbejdere, der skal have en Microsoft 365 konto. Alle medarbejdere skal have en gyldig mailadresse, så de kan modtage bookinger og planlægge ændringer.

## <a name="watch-add-your-staff-to-bookings"></a>Se: Føj dine medarbejdere til Bookings

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Trin

1. Vælg din kalender på startsiden. 

2. Gå til personaleindstillingen i venstre rude, og vælg **Tilføj nyt personale**.

3. Når du tilføjer personale fra din organisation, skal du skrive deres navn i feltet **Tilføj personer** og vælge dem, når de vises i rullemenuen. De andre felter udfyldes automatisk.

    Når en medarbejder er tilføjet, kan du redigere det navn, der vises på alle Bookings kommunikation, ved at vælge **x** ud for vedkommendes navn og redigere feltet **Tilføj personer**. Dette kan være nyttigt, hvis medarbejderne skal have en bestemt titel eller et navn, der vises for kunder, f.eks. angive Adele Vance som "Dr. Vance, MD".

4. Hvis du vil tilføje medarbejdere uden for din organisation, skal du manuelt udfylde deres mail og andre oplysninger.

    > [!NOTE]
    > Personale uden for din lejer kan ikke dele oplysninger om ledig/optaget tid med Bookings.

5. For hver medarbejder skal du vælge en rolle: Administrator, Seer eller Gæst.
    - **Administratorer** kan redigere alle indstillinger, tilføje og fjerne medarbejdere og oprette, redigere eller slette bookinger.
    - **Seerne** kan se alle bookinger i kalenderen, men de kan ikke ændre eller slette dem. De har skrivebeskyttet adgang til indstillinger.
    - **Gæster** kan tildeles til bookinger, men de kan ikke åbne bookingpostkassen.

6. Vælg **Giv alle medarbejdere besked via mail, når en reservation, der er tildelt dem, oprettes eller ændres** for at aktivere personalemails. Følgende er et eksempel på en mail:

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="En mail med en meddelelse fra Bookings.":::

7. Vælg **Begivenheder i Office 365 kalender påvirker tilgængeligheden**, hvis oplysninger om ledig/optaget tid fra medarbejdernes kalendere skal påvirke tilgængeligheden af bookingtjenester via Bookings.

    Hvis en medarbejder f.eks. har et teammøde eller en personlig aftale, der er planlagt til kl. 15 på en onsdag, viser Bookings, at medarbejderen ikke er tilgængelig til at blive booket inden for dette tidsrum. Dette klokkeslæt vises som optaget eller foreløbigt i Bookings kalendervisning, som vist i nedenstående eksempel.

    :::image type="content" source="media/bookings-busy-tentative-view-2.png" alt-text="En visning af en Bookings kalender.":::

> [!IMPORTANT]
> Vi anbefaler på det kraftigste, at du lader denne indstilling være slået til (den er slået til som standard) for at undgå dobbeltbookinger og for at optimere tilgængeligheden af dine medarbejdere.

8. Vælg **Brug åbningstider** for at angive, at alle de medarbejdere, der kan bookes, kun skal være inden for de åbningstider, du har angivet i afsnittet **Åbningstider** på siden Firmaoplysninger.

    Ved at fravælge denne boks kan medarbejderne få brugerdefinerede timer, der yderligere begrænser, hvornår de kan bookes. Dette er nyttigt i scenarier, hvor en medarbejder kun kan være på stedet tirsdage og onsdage, eller de dedikerer deres morgener til én type aftaler og deres eftermiddage til andre typer.

    > [!NOTE]
    > Bookings understøtter op til 100 medarbejdere i en Bookings kalender.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Gør en Bookings bruger til en superbruger uden at tilføje dem som personale i Bookings

Det kan være en god idé at føje en person til personalelisten i Bookings uden at gøre dem tilgængelige for kunder eller klienter. Når du gør dem til superbrugere, bliver de administrator af bookingpostkassen. At være administrator af en bookingpostkasse defineres som at have fuld adgang og send som tilladelser til bookingpostkassen.

> [!NOTE]
> Disse trin fungerer kun, hvis den bruger, der tilføjes, ikke allerede er tildelt en **seerrolle** i Bookings.

1. [Forbind til at Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. Ved hjælp af PowerShell kan du tildele fuld adgang med følgende kommandoer:

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Og kør derefter denne kommando for at tildele send som-tilladelser.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Her er et eksempel på en PowerShell-kommando til at føje Allie Bellew til Contoso-dagplejens bookingpostkasse.

1. Kør først denne kommando:

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Kør derefter denne kommando:

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** har nu administratoradgang, men vises ikke som reserverbart personale i Bookings.
