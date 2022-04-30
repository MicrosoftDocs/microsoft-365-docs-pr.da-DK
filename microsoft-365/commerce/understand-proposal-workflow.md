---
title: Forstå arbejdsprocessen for forslaget
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: presharm, jmueller
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_purchase
- AdminSurgePortfolio
search.appverid: MET150
description: Få mere at vide om forslag, der kan hjælpe dig med at købe Microsoft-produkter og -tjenester.
ROBOTS: NOINDEX
ms.date: 04/28/2022
ms.openlocfilehash: 8dc80bfaadcbee236f282796dcdb37f59360ebe4
ms.sourcegitcommit: 58ec09f1fd66af9717dc2743585d06d358ec7360
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/30/2022
ms.locfileid: "65144855"
---
# <a name="understand-the-proposal-workflow"></a>Forstå arbejdsprocessen for forslaget

Et forslag er et formelt tilbud fra Microsoft om, at din organisation kan købe Microsoft-produkter og -tjenester. Du arbejder direkte sammen med en Microsoft-repræsentant om at fastlægge de specifikke produkter, tjenester og vilkår for dit forslag.

En Microsoft-repræsentant udarbejder et forslag, der indeholder de elementer, som du og din repræsentant har diskuteret. Repræsentanten sender dig en mail, der har et link til Azure Marketplace-portalen. Webstedet indeholder det forslag, der er udarbejdet specielt til dig og din organisation.

Når du har modtaget meddelelsesmailen, skal du følge linket til forslagswebstedet. Når du logger på webstedet, kan du starte processen til gennemsyn af forslag.

## <a name="prerequisites-for-buying-items-with-a-proposal"></a>Forudsætninger for køb af varer med et forslag

Før du kan købe varer til et forslag, skal du have en faktureringskonto og en aftale med Microsoft.

### <a name="billing-account"></a>Faktureringskonto

Du kan bruge en faktureringskonto til at administrere dine kontoindstillinger, fakturaer, faktureringsprofiler og produkter og tjenester. Hvis du ikke allerede har en faktureringskonto, opretter din Microsoft-repræsentant en for dig. Ellers bruger de en eksisterende faktureringskonto til din organisation, så længe du har tilladelse til at bruge denne faktureringskonto.

Tilladelser til faktureringskontoen administreres af ejeren af faktureringskontoen. Globale administratorer kan tildele sig selv rollen faktureringskontoejer og derefter gøre andre personer til ejere af faktureringskontoen.

Du kan få flere oplysninger om faktureringskonti under [Administrer faktureringskonti](manage-billing-accounts.md).

### <a name="microsoft-customer-agreement"></a>Microsoft-kundeaftale

Med Microsoft-kundeaftale (MCA) kan en organisation købe Microsoft-produkter og -tjenester. Du kan få flere oplysninger under [Microsoft-kundeaftale](https://www.microsoft.com/Licensing/how-to-buy/microsoft-customer-agreement).

## <a name="permissions-needed-to-sign-an-agreement-or-pay-for-items"></a>Tilladelser, der er nødvendige for at signere en aftale eller betale for elementer

Du skal være ejer af faktureringskontoen eller bidragyder til faktureringskontoen for at kunne underskrive en aftale eller købe produkter og tjenester. Hvis du er global administrator, men ikke har en af disse roller, kan du tildele rollerne til dig selv. Hvis du ikke er global administrator, skal du bede ejeren af din globale administrator eller faktureringskonto om at tildele dig en af rollerne.

Rollerne ejer af faktureringskontoen og bidragydere til faktureringskontoen tildeles ved hjælp af en af følgende metoder.

### <a name="assign-roles-in-the-microsoft-365-admin-center"></a>Tildel roller i Microsoft 365 Administration

1. I Microsoft 365 Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Faktureringsbilling-konti</a> > .
2. Vælg **Tildel roller** i sektionen **Faktureringskontoroller** på siden **Faktureringskonti**.
3. Søg efter navnet på den person, du vil tildele en rolle, i ruden **Tildel roller** .
4. Markér afkrydsningsfeltet for det rollenavn, personen skal have, og vælg derefter **Tildel**.

### <a name="assign-roles-in-the-azure-portal"></a>Tildel roller i Azure Portal

1. I Azure Portal skal du gå til siden <a href="https://portal.azure.com/#blade/Microsoft_Azure_GTM/ModernBillingMenuBlade/Overview" target="_blank">Adgangskontrol (IAM).</a>
2. På siden **Adgangskontrol (IAM)** skal du vælge **Tilføj**.
3. I ruden **Tilføj tilladelse** skal du vælge den **rolle** , der skal tildeles til brugeren.
4. Vælg brugeren, og vælg derefter **Gem**.

Du kan få flere oplysninger om faktureringskontoroller under [Forstå adgang til faktureringskonti](manage-billing-accounts.md#understand-access-to-billing-accounts).

Hvis dette er en ny faktureringskonto, og ingen har accepteret en aftale, bliver du automatisk ejeren af faktureringskontoen, forudsat at du:

- Er den person, der er nævnt i forslaget **, eller**
- Er allerede [en Azure Active Directory global administrator](/azure/active-directory/roles/permissions-reference#global-administrator) for din organisation

## <a name="what-is-the-overall-workflow"></a>Hvad er den overordnede arbejdsproces?

Arbejdsprocessen for det overordnede forslag ser sådan ud:

- Din Microsoft-repræsentant opretter et forslag og sender et link til dig i en mail.
- Du bruger linket til at gå til logonsiden for forslaget.
- Du gennemser din organisations oplysninger.
- Du gennemser forslaget, accepterer MCA'en, hvis det er nødvendigt, og afslutter udtjekningsprocessen.
  > [!IMPORTANT]
  > Du skal have tilladelse til at signere en MCA på vegne af din organisation. Hvis du ikke har denne autoritet, så en person, der gør, skal gøre dette trin.
- Når udtjekningen er fuldført, får du yderligere links til at konfigurere dine produkter og tjenester.

## <a name="proposal-terms"></a>Vilkår for forslag

Følgende tabel indeholder ord og definitioner, der vises i dit forslag og på forslagswebstedet.

| Udtrykket | Definition |
|---|---|
| Faktureringskonto | En konto, der bruges til at administrere dine kontoindstillinger, fakturaer, betalingsmetoder og produkter. |
| Faktureringsprofil | Oplysninger om din organisation, der giver dig mulighed for at tilpasse, hvilke elementer der er inkluderet på din faktura, og hvordan du betaler for dine fakturaer. Faktureringsprofilen indeholder navnet på faktureringskontoen, de betalingsmetoder, der bruges til den specifikke faktureringsprofil, kontaktoplysninger, fakturaindstillinger og tilladelser, der giver dig mulighed for at ændre faktureringsprofilen, betale regninger og købe produkter og tjenester. |
| Eksisterende aftaler | Alle aftaler, som din organisation allerede har indgået med Microsoft. Dette kan omfatte, men er ikke begrænset til, en Enterprise Agreement, Microsoft-produkt &-serviceaftale eller Microsoft-kundeaftale. |
| Microsoft-kundeaftale (MCA) | En aftale, der beskriver vilkårene og betingelserne for den konto, som din organisation har, med Microsoft. |
| Microsoft-repræsentant | En autoriseret Microsoft-repræsentant, der forbereder et forslag til dig og din organisation. |
| Organisation | En juridisk enhed, der bruger Microsoft-produkter, -teknologier eller -tjenester. |
| Udarbejdet af | Mailadressen på den Microsoft-repræsentant, der forberedte forslaget. |
| Supplerende vilkår | Ændringer af MCA, der indeholder vilkår, der er specifikke for din organisation. Hvis du vil acceptere supplerende vilkår, skal du bruge DocuSign til at registrere en elektronisk signatur. |

## <a name="step-1-review-organization-information"></a>Trin 1: Gennemse organisationsoplysninger

Når du har logget på, skal du først gennemse din organisations oplysninger.

### <a name="your-organization"></a>Din organisation

I afsnittet **Din organisation** vises den faktureringskonto, der er knyttet til den. Oplysningerne om faktureringskontoen hentes enten fra en eksisterende faktureringskonto eller oprettes for dig af Microsoft-repræsentanten. Hvis din organisation er partner i en anden organisation, kan du også se afsnittet **Kundeemneorganisation** med navnet og adressen på den pågældende organisation.

Hvis det er første gang, din organisation etablerer en kommerciel relation med Microsoft, og du endnu ikke har signeret en MCA, skal du kontakte repræsentanten for at foretage ændringer for dig, hvis oplysningerne under **Din organisation** eller **Kundeemneorganisation** er forkerte. Når du har accepteret en MCA, kan du gennemse og ændre din organisations adresse og kontaktoplysninger på siden [Faktureringskonti](https://go.microsoft.com/fwlink/p/?linkid=2084771) i Microsoft 365 Administration. Hvis organisationens navn ændres, skal du åbne en serviceanmodning for at få den opdateret. [Få mere at vide om, hvordan du åbner en serviceanmodning](../admin/get-help-support.md).

### <a name="your-information"></a>Dine oplysninger

Hvis du er ny kunde, skal du angive dit navn, din mailadresse og dit telefonnummer under **Dine oplysninger** og derefter vælge **Gem**. Hvis du er en eksisterende kunde, skal du kontrollere, at dine oplysninger er korrekte. Hvis du vil foretage rettelser, skal du vælge **Rediger**, foretage de nødvendige ændringer og derefter vælge **Gem**.

Når du er klar, skal du vælge **Fortsæt** for at gå til næste trin.

## <a name="step-2-review-proposal"></a>Trin 2: Gennemse forslag

Forslaget indeholder oplysninger om de elementer, du har diskuteret med din Microsoft-repræsentant. Du kan videresende mailen med linket til forslaget for at dele den med andre interessenter i din organisation. Alle andre, der bruger linket, har en skrivebeskyttet visning af forslaget.

Hvis du vil foretage ændringer af forslaget efter gennemgang, skal du kontakte din Microsoft-repræsentant.

### <a name="proposal-contents"></a>Forslagsindhold

Forslaget indeholder følgende oplysninger:

| Afsnit | Beskrivelse |
|---|---|
| Organisationsnavn | Navnet på den organisation, som forslaget blev forberedt for. |
| Gyldig indtil dato | Den dato, hvor tilbudet på forslaget udløber. Hvis du går glip af denne udløbsdato, skal du kontakte din Microsoft-repræsentant for at fortælle dem, at du stadig er interesseret i forslaget. |
| Valuta | Den valuta, der bruges til at beregne omkostningerne for varer i forslaget. |
| Forberedt til | Faktureringskontoens navn, adresse, mailadresse på kontakt og telefonnummer for den person, der har anmodet om forslaget. |
| Udarbejdet af | Mailadressen på den Microsoft-repræsentant, der forberedte forslaget. |
| Oversigt | Viser den subtotal, der er knyttet til forslaget. Hvis det er nødvendigt, vises også den valutakurs (FX), der bruges til at beregne omkostningerne. |
| Linjeelementer for forslag | Dette afsnit indeholder antallet, enhedsprisen og subtotalen for alle varer, der er inkluderet i forslaget. |
| Næste trin | Dette afsnit angiver den nødvendige handling, du skal udføre. |

Hvis du vil signere en MCA, skal du vælge knappen under **Næste trin**. Hvis du skal signere supplerende vilkår, fører et link dig til DocuSign-webstedet, hvor du følger trinnene til at signere dokumentet.

Når du har underskrevet de nødvendige aftaler eller supplerende vilkår, skal du vælge **Gå til kassen**.

## <a name="step-3-checkout"></a>Trin 3: Tjek ud

Udtjekningssiden indeholder følgende afsnit:

### <a name="sold-to"></a>Solgt til

I dette afsnit vises den faktureringskonto, der bruges til forslaget. Hvis du har brug for at ændre oplysninger, skal du vælge linket **Rediger** . Du kan også bruge linket **Rediger** til at tilføje din organisations skatte-id. Skatte-id'et skal være relateret til det land, der er angivet i afsnittet **Solgt til** . Hvis du har en skattefritagelse, skal du åbne en supportanmodning for at anmode om momsfritagelsesstatus.

Hvis du vil vide mere om skatte-id'er, og hvordan du ansøger om momsfritagelsesstatus, skal du se [Skatteoplysninger](billing-and-payments/tax-information.md).

### <a name="billed-to"></a>Faktureres til

I dette afsnit vises den faktureringsprofil, der bruges til at bestemme, hvilke elementer der er inkluderet på din faktura, og hvordan du betaler dine fakturaer. Hver faktureringscyklus modtager du en separat faktura for hver faktureringsprofil. Du betaler for fakturaer ved hjælp af enten check- eller wire transfer eller Azure-forudbetaling. Hvis du ikke allerede har en faktureringsprofil, opretter din Microsoft-repræsentant en for dig. Under udtjekningen kan du vælge en anden faktureringsprofil, hvis du har en, ændre navnet på faktureringsprofilen eller tilføje en P.O. Antallet. Du kan også oprette en ny faktureringsprofil.

Du kan få oplysninger om faktureringsprofiler under [Administrer faktureringsprofiler](billing-and-payments/manage-billing-profiles.md).

### <a name="proposal-items-in-this-order"></a>Forslagselementer i denne rækkefølge

I dette afsnit vises en liste over alle elementer, der er inkluderet i forslaget. Listen kan indeholde en eller flere af følgende kategorier:

- **Supplerende vilkår** En liste over eventuelle ændringer af MCA, der indeholder vilkår for din organisation. Denne liste kan f.eks. indeholde HIPAA- eller GDPR-vilkår.
- **Køb nu** En liste over elementer, du betaler for under udtjekning i slutningen af arbejdsprocessen for accept af forslag.
- **Rabatter (anvendes på fremtidige gebyrer)** En liste over rabatter, som du modtager som en del af forslaget.
- **Inkluderet** En liste over elementer, der er inkluderet som en del af forslagspakken uden ekstra omkostninger. Nogle af disse elementer kan have en omkostning knyttet til dem i fremtiden.

> [!NOTE]
> Dit forslag kan omfatte abonnementer med en fremtidig startdato. Du kan få flere oplysninger under [Forstå fakturering for fremtidige startdatoer](billing-and-payments/future-start-date.md).

### <a name="summary"></a>Oversigt

I dette afsnit vises antallet af varer, der betales for, subtotalen, anslået moms og det samlede beløb for ordren.

Hvis du vil afgive ordren, skal du vælge **Afgiv ordre** eller **Acceptér aftalestedsordre&amp;**.

Når du har angivet ordren, modtager du en bekræftelse med de næste trin. Hvis du har købt en Azure-plan, er dit næste trin at konfigurere din faktureringskonto i Azure Portal.

## <a name="step-4-set-up-your-new-billing-account-azure-customers-only"></a>Trin 4: Konfigurer din nye faktureringskonto (kun Azure-kunder)

Hvis du er ny kunde og har købt Azure-produkter som en del af forslaget, er dit næste trin at konfigurere din nye faktureringskonto. Du kan få mere at vide under [Konfigurer din faktureringskonto for en Microsoft-kundeaftale](/azure/cost-management-billing/manage/mca-setup-account).

Hvis du er eksisterende Azure-kunde med en Enterprise Agreement, og du signerer en MCA for første gang, er dit næste trin at få mere at vide om ændringerne mellem aftalerne, og hvordan du udfører opgaver med din nye faktureringskonto. Du kan få mere at vide under [Fuldføre Enterprise Agreement opgaver på din faktureringskonto for en Microsoft-kundeaftale](/azure/cost-management-billing/manage/mca-enterprise-operations).

## <a name="understand-invoicing"></a>Forstå fakturering

Når du har tjekket ud og gennemført din ordre, sendes en indledende faktura inden for 24-48 timer. Derefter modtager du fakturaer omkring den 5. i hver måned. Den månedlige faktura indeholder gebyrer fra den forrige måned. Hvis du har kreditter til din konto, trækkes de fra din faktureringsprofils pengekreditter og anvendes på din fakturasaldo. Den resterende saldo, efter at kreditterne er anvendt, er den skyldige saldo. Du har 30 dage fra faktureringsdatoen til at betale fakturaen.

Betalingsanvisninger for, hvor check eller bankoverførsler skal sendes hen, er inkluderet i PDF-kopien af din faktura. Hvis du vil have vist eller downloade din faktura, skal du se [Få vist din faktura eller faktura](billing-and-payments/view-your-bill-or-invoice.md).
