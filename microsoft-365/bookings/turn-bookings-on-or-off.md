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
description: Få mere at vide om, hvordan du får adgang til Microsoft Bookings i Microsoft 365.
ms.openlocfilehash: 28398faba7c21b6d3cce84063934268dad11fd64
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823074"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Slå Microsoft Bookings til eller fra

> [!NOTE]
> Denne artikel hjælper dig med at interagere med den nyeste version af Microsoft Bookings. Tidligere versioner udgår i de kommende måneder.

Denne artikel er til administratorer. 

Bookings kan slås til eller fra for hele organisationen eller for bestemte brugere. Når du slår Bookings til for brugerne, kan de oprette en Bookings side, oprette en kalender og give andre mulighed for at booke tid hos dem.

> [!NOTE]
> De administratorkontrolelementer, der er beskrevet i disse afsnit, er ikke tilgængelige for Office 365 drevet af 21Vianet -kunder (Kina).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Slå Bookings til eller fra for din organisation ved hjælp af Microsoft 365 Administration

1. Log på Microsoft 365 Administration som global administrator.

2. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Organisationsindstillinger**</a>.

3. Markér afkrydsningsfeltet **for Tillad, at din organisation bruger Bookings** til at aktivere eller deaktivere Bookings for din organisation.

   > [!NOTE]
   > Hvis du deaktiverer Bookings, deaktiveres al adgang til tjenesten, herunder oprettelse og administration af Bookings sider.

4. Vælg **Gem ændringer**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Slå Bookings til eller fra for din organisation ved hjælp af PowerShell

Hvis du vil slå Bookings til eller fra for din organisation ved hjælp af [PowerShell-cmdlet'en Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [skal du Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) og køre følgende kommando:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="granular-controls"></a>Detaljerede kontrolelementer

Brug indstillingerne nedenfor til at styre, hvem der kan bruge Bookings, beslutte, hvilke Bookings oplysninger der deles, og om medarbejderne skal godkendes, før de kan føjes til en bookingkalender.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Skærmbillede: Indstillinger, der giver dig mulighed for at styre, hvem der kan bruge Bookings, beslutte, hvilke Bookings oplysninger der deles, og medarbejdergodkendelse":::

### <a name="block-bookings-from-outside-your-organization"></a>Bloker bookinger uden for din organisation

Du kan konfigurere Bookings, så det kun er personer i organisationen, der kan booke aftaler. Det er kun brugere i din organisation, der har logget på og er godkendt, der kan booke aftaler.

### <a name="block-social-sharing-options"></a>Bloker indstillinger for social deling

Du kan styre, hvordan bookingsider deles på sociale netværk. Denne indstilling er tilgængelig i Microsoft 365 Administration under **Indstillinger** ->  **Ellerg-indstillinger** ->  **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Bloker deling af medarbejderoplysninger med kunder

Personaleoplysninger, f.eks. kontaktoplysninger, sendes aldrig til kunder via e-mail eller anden kommunikation.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Kræv personalegodkendelser, før du deler oplysninger om ledig/optaget tid

Du kan kræve, at medarbejderne i din organisation tilmelder sig, før deres tilgængelighedsoplysninger deles via Bookings, og før de kan bookes via en bookingside.

Når denne indstilling er aktiveret, modtager personer, der tilføjes som medarbejdere i bookingkalendere, en mail med et link til **godkend/afvis** anmodningen.

## <a name="restrict-collection-of-customer-data"></a>Begræns indsamling af kundedata

Af hensyn til overholdelse af angivne standarder ønsker du muligvis ikke at indsamle nogle kundeoplysninger. Hvis du markerer et afkrydsningsfelt for en af disse indstillinger, medtages disse felter ikke i formularer, der vises for dine kunder eller kunder.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Skærmbillede: Markér afkrydsningsfelterne for at forhindre kunderne i at dele følsomme data med dig":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Slå Bookings til eller fra for individuelle brugere

Du kan deaktivere Bookings for individuelle brugere.

1. Gå til Microsoft 365 Administration, og vælg derefter **Aktive** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**brugere**</a>.

1. Vælg den ønskede bruger, og vælg derefter **Licenser og apps**.

1. Udvid **Apps**, og fjern markeringen i afkrydsningsfeltet for Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Tillad kun valgte brugere at oprette Bookings kalendere

Ved hjælp af politikbegrænsninger kan du begrænse brugere med licens, så de ikke kan oprette Bookings kalendere. Du skal først aktivere Bookings for hele organisationen. Alle brugere i organisationen har Bookings licenser, men kun dem, der er inkluderet i politikken, kan oprette Bookings kalendere og have fuld kontrol over, hvem der har adgang til de kalendere, de opretter.

Brugere, der er inkluderet i denne politik, kan oprette nye Bookings kalendere og kan føjes som personale i en hvilken som helst kapacitet (herunder administratorrollen) til eksisterende Bookings kalendere. Brugere, der ikke er inkluderet i denne politik, kan ikke oprette nye Bookings kalendere og modtager en fejlmeddelelse, hvis de forsøger at gøre det.

Du skal køre følgende kommandoer ved hjælp af Exchange Online PowerShell. Du kan få flere oplysninger om kørsel af Exchange Online cmdlet'er under [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Nedenstående trin forudsætter, at der ikke er oprettet andre politikker for Outlook Web App (OWA) i din organisation.

1. Opret en ny postkassepolitik for brugere, der skal have tilladelse til at oprette Bookings kalendere. (Bookings oprettelse af kalender er som standard tilladt af politikker for nye postkasser.

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Du kan få flere oplysninger under [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Tildel denne politik til de relevante brugere ved at køre denne kommando for hver bruger, du vil give tilladelse til at oprette Bookings kalendere.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Du kan få flere oplysninger under [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Valgfrit: Kør denne kommando, hvis du vil deaktivere Bookings for alle andre brugere i din organisation.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Du kan få flere oplysninger under [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Du kan få flere oplysninger om politikker for OWA-postkasser i følgende emner:

- [Opret en Outlook på internettet postkassepolitik i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Anvend eller fjern en Outlook på internettet postkassepolitik på en postkasse i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
