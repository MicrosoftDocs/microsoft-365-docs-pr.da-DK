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
description: Brug Microsoft 365 Administration eller Windows PowerShell til at slette Bookings kalendere.
ms.openlocfilehash: 5b91a6b2c3d3d0637a017b0250ec45394958e147
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714367"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Slet en bookingkalender i Bookings

> [!NOTE]
> Denne artikel hjælper dig med at interagere med den nyeste version af Microsoft Bookings. Tidligere versioner udgår i de kommende måneder.

I denne artikel forklares det, hvordan du kan slette en uønsket bookingkalender. Du kan slette bookingkalenderen i Microsoft 365 Administration, eller du kan bruge PowerShell. Den Bookings kalender er en postkasse i Exchange Online så du sletter den tilsvarende brugerkonto for at slette bookingkalenderen.

> [!IMPORTANT]
> Alle bookingkalendere, du oprettede i 2017 eller før, skal slettes ved hjælp af PowerShell-vejledningen i dette emne. Alle bookingkalendere oprettet i 2018 eller senere kan slettes i Microsoft 365 Administration.

Bookingkalenderen er der, hvor alle relevante oplysninger om denne bookingkalender og de pågældende data gemmes, herunder:

- Firmaoplysninger, logo og arbejdstimer, der blev tilføjet, da bookingkalenderen blev oprettet
- Relevante medarbejdere og tjenester blev tilføjet, da bookingkalenderen blev oprettet
- Alle bookinger og aftaler om fridage føjes til bookingkalenderen, når den blev oprettet.

> [!WARNING]
> Når en bookingkalender er slettet, slettes disse yderligere oplysninger også permanent og kan ikke gendannes.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Slet en bookingkalender i Microsoft 365 Administration

1. Gå til Microsoft 365 Administration.

1. Vælg **Brugere** i Administration.

   ![Billede af brugergrænsefladen for brugere i Microsoft 365 Administration.](../media/bookings-admin-center-users.png)

1. På siden **Aktive brugere** skal du vælge navnene på de brugere, du vil slette, og derefter vælge **Slet bruger**.

   ![Billede af Slet brugerbrugergrænsefladen i Microsoft 365 Administration.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Slet en bookingkalender ved hjælp af Exchange Online PowerShell

Se [Forbind til at Exchange Online PowerShell for at](/powershell/exchange/exchange-online-powershell-v2) få forudsætninger og vejledning til at oprette forbindelse til Exchange Online PowerShell.

Hvis du vil udføre disse trin, skal du bruge et aktivt Microsoft PowerShell-kommandovindue, som du kørte, ved at vælge indstillingen "Kør som administrator".

1. I et PowerShell-vindue skal du indlæse EXO V2-modulet ved at køre følgende kommando:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > Hvis du allerede har [installeret EXO V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module), fungerer den forrige kommando som skrevet.
   
2. Den kommando, du skal køre, bruger følgende syntaks:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ er din konto i brugerens hovednavnsformat (f.eks. `john@contoso.com`).

3. Når du bliver bedt om det, skal du logge på med lejeradministratorens legitimationsoplysninger til den Microsoft 365 lejer, der er vært for den bookingkalender, du vil slette permanent.

4. Når denne kommando er blevet behandlet, skal du angive følgende kommando for at få vist en liste over bookingpostkasserne i din lejer:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. Skriv følgende kommando:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Vær forsigtig med at skrive det nøjagtige navn på det alias for bookingpostkassen, som du vil slette permanent.

6. Du kan kontrollere, at kalenderen er blevet slettet, ved at angive følgende kommando:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Den slettede kalender vises ikke i outputtet.
