---
title: Slet en bookingkalender
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Brug den Microsoft 365 Administration eller Windows PowerShell til at slette Bookings-kalendere.
ms.openlocfilehash: 48556951382b95316ffdb9e07c1c561758276ded
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590416"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Slet en bookingkalender i Bookinger

I denne artikel forklares det, hvordan du kan slette en uønsket bookingkalender. Du kan slette bookingkalenderen i Microsoft 365 Administration eller du kan bruge PowerShell. Bookings-kalenderen er en postkasse i Exchange Online så du sletter den tilsvarende brugerkonto for at slette bookingkalenderen.

> [!IMPORTANT]
> Alle bookingkalendere, du oprettede i 2017 eller tidligere, skal slettes ved hjælp af PowerShell-vejledningen til dette emne. Alle bookingkalendere, der er oprettet i 2018 eller efter, kan slettes Microsoft 365 Administration.

Bookingkalenderen er stedet, hvor alle relevante oplysninger om den pågældende bookingkalender og data gemmes, herunder:

- Firmaoplysninger, logo og arbejdstid tilføjet, da bookingkalenderen blev oprettet
- Relevant personale og relevante tjenester tilføjet, da bookingkalenderen blev oprettet
- Alle bookinger og aftaler om fridage føjet til bookingkalenderen, da den blev oprettet.

> [!WARNING]
> Når en bookingkalender slettes, slettes disse yderligere oplysninger også permanent og kan ikke gendannes.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Slet en bookingkalender i Microsoft 365 Administration

1. Gå til Microsoft 365 Administration.

1. Vælg Brugere i **Administration**.

   ![Billede af brugergrænseflade i Microsoft 365 Administration.](../media/bookings-admin-center-users.png)

1. På siden **Aktive brugere** skal du vælge navnene på de brugere, du vil slette, og derefter vælge **Slet bruger**.

   ![Billede af Slet brugergrænseflade i Microsoft 365 Administration.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Slet en bookingkalender ved hjælp Exchange Online PowerShell

Se [Forbind til Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell-v2) for forudsætninger og vejledning til at oprette forbindelse til Exchange Online PowerShell.

For at udføre disse trin skal du bruge et aktivt Microsoft PowerShell-kommandovindue, som du kørte, ved at vælge indstillingen "Kør som administrator".

1. I et PowerShell-vindue skal du indlæse EXO V2-modulet ved at køre følgende kommando:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > Hvis du allerede har installeret [EXO V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module), fungerer den forrige kommando som skrevet.
   
2. Den kommando, du skal køre, bruger følgende syntaks:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ er din konto i formatet brugerens hovednavn (f.eks. `john@contoso.com`).

3. Når du bliver bedt om det, skal du logge på med lejeradministratorens legitimationsoplysninger til den Microsoft 365 lejer, der hoster den bookingkalender, du vil slette permanent.

4. Når denne kommando er færdig med at behandle, skal du angive følgende kommando for at få en liste over bookingpostkasser i din lejer:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. Skriv følgende kommando:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Sørg for at skrive det nøjagtige navn på det bookingpostkassealias, du vil slette permanent.

6. Du bekræfter, at kalenderen er blevet slettet, ved at angive følgende kommando:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Den slettede kalender vises ikke i outputtet.
