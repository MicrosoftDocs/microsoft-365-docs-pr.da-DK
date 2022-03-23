---
title: Slå Microsoft Bookings til eller fra
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Få mere at vide om, hvordan du får adgang til Microsoft Bookings Microsoft 365.
ms.openlocfilehash: 3feacd756c141dd51edd7e987c1c4a2033524ae3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591427"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Slå Microsoft Bookings til eller fra

Bookings kan slås til eller fra for hele organisationen eller for bestemte brugere. Når du slår Bookings til for brugere, kan de oprette en Bookings-side, oprette en kalender og give andre personer mulighed for at reservere tid med dem.

> [!NOTE]
> De administratorkontrolelementer, der er beskrevet i disse afsnit, er ikke tilgængelige for Office 365 drevet af 21Vianet -kunder (Kina).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Slå Bookings til eller fra for din organisation ved hjælp af Microsoft 365 Administration

1. Log på Microsoft 365 Administration global administrator.

2. I Administration skal du gå til  **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Indstillinger for organisation**</a>.

3. Markér afkrydsningsfeltet for **Tillad din organisation at bruge Bookings** til at aktivere eller deaktivere Bookings for organisationen.

   > [!NOTE]
   > Deaktivering af Bookings deaktiverer al adgang til tjenesten, herunder oprettelse og administration af Bookings-sider.

4. Vælg **Gem ændringer**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Slå Bookings til eller fra for din organisation ved hjælp af PowerShell

Hvis du vil slå Bookings til eller fra for din organisation ved hjælp af PowerShell-cmdlet'en [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [skal du Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) og køre følgende kommando:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

Brug indstillingerne nedenfor til at styre, hvem der kan bruge Bookings, bestemme, hvilke Bookings-oplysninger der deles, og om medarbejderne skal godkendes, før de kan føjes til en Booking-kalender.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Skærmbillede: Indstillinger, der giver dig mulighed for at styre, hvem der kan bruge Bookings, beslutte, hvilke Bookings-oplysninger der deles, og personalegodkendelse":::

### <a name="block-bookings-from-outside-your-organization"></a>Bloker bookinger uden for din organisation

Du kan konfigurere Bookinger, så kun personer i organisationen kan booke aftaler. Kun brugere i organisationen, som har signeret og er godkendt, kan booke aftaler.

### <a name="block-social-sharing-options"></a>Bloker indstillinger for social deling

Du kan styre, hvordan bookingsider deles på sociale netværk. Denne indstilling er tilgængelig på Microsoft 365 Administration under **Indstillinger** ->  **Org-indstillingerBøger** -> .

### <a name="block-sharing-staff-details-with-customers"></a>Bloker deling af personaleoplysninger med kunder

Personaleoplysninger, f.eks. kontaktoplysninger, vil aldrig blive sendt til kunder via mail eller anden kommunikation.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Kræv personalegodkendelser, før du deler oplysninger om ledig/optaget tid

Du kan kræve, at medarbejdere i din organisation skal tilmelde sig, før deres oplysninger om tilgængelighed deles via Bookings, og før de kan bookes via en bookingside.

Når denne indstilling er aktiveret, vil personer, der er tilføjet som personale i bookingkalendere, få en mail med et link til **Godkend/Afvis** anmodningen.

## <a name="restrict-collection-of-customer-data"></a>Begræns indsamling af kundedata

Af hensyn til overholdelse af regler og standarder ønsker du muligvis ikke at indsamle nogle kundeoplysninger. Hvis du markerer et afkrydsningsfelt for en af disse indstillinger, medtages disse felter ikke i formularer, der vises til kunder eller kunder.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Skærmbillede: Markér afkrydsningsfelterne for at forhindre kunder i at dele følsomme data med dig":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Slå Bookings til eller fra for individuelle brugere

Du kan deaktivere Bookings for individuelle brugere.

1. Gå til fanen Microsoft 365 Administration, og vælg **derefter Aktive** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**brugere.**</a>

1. Vælg den ønskede bruger, og vælg **derefter Licenser og apps**.

1. **Udvid Apps**, og fjern markeringen i afkrydsningsfeltet for Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Tillad kun udvalgte brugere at oprette Bookings-kalendere

Ved hjælp af politikbegrænsninger kan du begrænse brugere med licens i at kunne oprette Bookings-kalendere. Du skal først aktivere Bookings for hele organisationen. Alle brugere i organisationen har Bookings-licenser, men kun dem, der er inkluderet i politikken, kan oprette Bookings-kalendere og have fuld kontrol over, hvem der kan få adgang til de kalendere, de opretter.

Brugere, der er inkluderet i denne politik, kan oprette nye Bookings-kalendere og kan tilføjes som personale i enhver kapacitet (herunder administratorrollen) til eksisterende Bookings-kalendere. Brugere, der ikke er inkluderet i denne politik, kan ikke oprette nye Bookings-kalendere, og der vises en fejlmeddelelse, hvis de forsøger at gøre dette.

Du skal køre følgende kommandoer ved hjælp af Exchange Online PowerShell. Du kan finde flere oplysninger Exchange Online kørende [cmdlet'er i Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> I nedenstående trin antages det, at Outlook Web App (OWA) postkassepolitikker er blevet oprettet i organisationen.

1. Opret en ny postkassepolitik for brugere, der skal have tilladelse til at oprette Bookings-kalendere. (Oprettelse af Bookings-kalender er tilladt som standard af nye postkassepolitikker.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Du kan finde flere oplysninger [under New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Tildel denne politik til de relevante brugere ved at køre denne kommando for hver bruger, du vil give tilladelse til at oprette Bookings-kalendere.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Få mere at vide under [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Valgfrit: Kør denne kommando, hvis du vil deaktivere Bookings for alle andre brugere i organisationen.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Du kan finde flere oplysninger [under Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Du kan finde flere oplysninger om politikker for OWA-postkasser i følgende emner:

- [Opret en Outlook på internettet postkassepolitik i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Anvend eller fjern Outlook på internettet en postkassepolitik for en postkasse i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
