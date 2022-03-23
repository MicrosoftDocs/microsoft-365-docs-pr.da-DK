---
title: Opgrader til en anden forretningsplan
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- SaRA
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Den nemmeste måde at opgradere planer på er at bruge fanen Opgrader i Administration. Fanen Opgrader understøttes dog ikke altid.
ms.date: 04/21/2021
ms.openlocfilehash: 17e1a35d096762e1645fd4e7143935578cfc1a79
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590206"
---
# <a name="upgrade-to-a-different-plan"></a>Opgrader til en anden plan

Når din virksomhed ændres, eller du har brug for flere funktioner, kan du opgradere planer. Den nemmeste måde at gøre dette på er at **bruge fanen** Opgrader i Administration. Brug af fanen **Opgrader** understøttes dog ikke i alle situationer. I nogle tilfælde kan du muligvis ændre planer manuelt.

## <a name="use-the-upgrade-tab"></a>Brug fanen Opgrader

Når du bruger **fanen Opgrader** , bliver du ført gennem processen med at købe en ny plan. Alle brugere tildeles automatisk licenser i den nye plan, og din gamle plan annulleres for dig.

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.
2. Vælg det abonnement, du vil opgradere.
3. På siden med abonnementsoplysninger skal du vælge **Opgrader**.
4. Find den plan, du vil opgradere til, og vælg derefter **knappen Opgrader** .
5. Angiv antallet af licenser, du skal bruge, vælg, om du vil betale hver måned eller for hele året, og vælg derefter **Gå til kassen**.
    > [!NOTE]
    > Sørg for, at du køber nok licenser til at dække alle dine brugere.
6. På næste side skal du bekræfte **Solgt til-adressen** , **Oplysningerne Faktureret** til og **Varer i denne ordre**. Du kan ændre standardbetalingsmetoden på dette trin. Hvis du har brug for at foretage ændringer, skal du **vælge Skift** ud for den relevante sektion.
7. Når du er færdig, skal du vælge **Afstil ordre**.

Når du har fuldført betalingen, kan det tage et par minutter at gennemføre opgraderingen. Du kan begynde at bruge dit nye abonnement med det samme. Vælg **Kontrollér opgraderingsstatus** for at kontrollere status for opgraderingen. Du får besked, når opgraderingen er fuldført. Meddelelsen vises på siden Dine **produkter** ud for dit nye abonnement.

## <a name="the-upgrade-tab-is-empty"></a>Fanen Opgrader er tom

Hvis fanen **Opgrader** er tom, får du vist en forklaring på, hvorfor du ikke kan opgradere på nuværende tidspunkt. Du kan prøve at [ændre planer manuelt](change-plans-manually.md). Du kan finde flere oplysninger [under Hvorfor kan jeg ikke opgradere planer?](#why-cant-i-upgrade-plans).

## <a name="i-dont-see-the-plan-i-want"></a>Jeg kan ikke se den ønskede plan

Når du bruger fanen **Opgrader** , vises planerne, som du kan opgradere til, baseret på tjenesterne i din aktuelle plan. Du kan kun bruge fanen **Opgrader** til at flytte til en plan, der har de samme datarelaterede tjenester eller til en nyere version. Dette sikrer, at brugerne ikke mister data, der er relateret til disse tjenester under ændringen.

Hvis du vil flytte til en plan med færre tjenester, kan du ændre planer [manuelt](change-plans-manually.md) eller ringe til [support](../../admin/get-help-support.md) for at få hjælp.

## <a name="i-only-want-to-upgrade-some-of-my-users-how-do-i-do-that"></a>Jeg vil kun opgradere nogle af mine brugere. Hvordan gør jeg det?

Hvis du kun vil opgradere nogle brugere til en anden plan, men først skal købe det nye abonnement, skal du se [Skift planer manuelt](change-plans-manually.md). Hvis du allerede har det abonnement, du vil opgradere brugere til, skal du se [Flyt brugere til et andet abonnement](move-users-different-subscription.md).

## <a name="why-some-changes-take-longer"></a>Hvorfor nogle ændringer tager længere tid

**Antal tildelte brugere:** Hvis du har et stort antal tildelte brugere, tager det længere tid at udføre opgraderingen for at flytte dem til den nye plan.

**Kontrol af kreditværdighed ved ændring af planer:** Hvis du betaler via faktura eller når et bestemt omkostningsniveau, kan det være nødvendigt med kontrol af kreditværdig grad. En kreditkontrol kan tage op til to arbejdsdage. Brugere har fuld adgang til deres aktuelle plan, indtil du flytter dem til den nye. Du modtager en besked, hvis en kreditkontrol er påkrævet.

## <a name="why-cant-i-upgrade-plans"></a>Hvorfor kan jeg ikke opgradere planer?

Hvis du ikke kan se nogen planer under fanen **Opgrader** , betyder det, at din plan ikke kan opgraderes automatisk. I nogle tilfælde kan du muligvis løse problemet, så du kan få vist tilgængelige planer for opgraderingen, eller du kan muligvis opgradere eller ændre planer manuelt i stedet.

### <a name="why-are-there-no-plans-listed-to-upgrade"></a>Hvorfor er der ingen planer om at opgradere?

#### <a name="you-cant-upgrade-subscriptions-now-because-you-have-more-users-than-licenses"></a>Du kan ikke opgradere abonnementer nu, fordi du har flere brugere end licenser

Hvis du vil opgradere planer automatisk, skal alle dine brugere have tildelt gyldige licenser. Hvis du har tildelt flere licenser, end du har købt, får du vist en besked på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a> Licenser om, at du har en licenskonflikt, som skal løses. [Få mere at vide om, hvordan du løser licenskonflikter](../../commerce/licenses/buy-licenses.md). Når du har løst eventuelle licenskonflikter, bør du kunne se planerne på **fanen Opgrader** . Hvis ikke, kan du [ændre planer manuelt](change-plans-manually.md) eller [ringe til support](../../admin/get-help-support.md).

#### <a name="you-cant-upgrade-subscriptions-right-now-because-this-subscription-isnt-fully-set-up-or-the-service-isnt-available"></a>Du kan ikke opgradere abonnementer lige nu, fordi dette abonnement ikke er fuldt konfigureret, eller tjenesten ikke er tilgængelig

Hvis f.eks. en af tjenesterne har en hændelse, kan du ikke opgradere, før alle tjenester er sunde. Hvis du vil se, om der er klargørings- eller tjenesteproblemer, skal du gå til **siden Tilstandstilstand** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">i</a> Administration.

Hvis du finder ud af, at en tjeneste ikke er helt klargjort, eller hvis du har et problem med tjenestestilstanden, skal du vente et par timer for at gøre din tjeneste tilgængelig og prøve igen. Hvis du stadig har problemer, skal du [ringe til support](../../admin/get-help-support.md).

#### <a name="you-cant-upgrade-plans-because-another-plan-is-in-the-process-of-being-upgraded-or-is-pending-a-credit-check"></a>Du kan ikke opgradere planer, fordi en anden plan er ved at blive opgraderet eller afventer en kreditkontrol

Vent, indtil kreditkontrollen er gennemført, før du opgraderer planer. Kreditkontroller kan tage op til to arbejdsdage.

#### <a name="currently-this-subscription-is-not-eligible-to-upgrade"></a>Dette abonnement er i øjeblikket ikke berettiget til at opgradere

Du kan [ændre planer manuelt eller](change-plans-manually.md) [ringe til support](../../admin/get-help-support.md).

#### <a name="i-see-a-different-message-than-whats-listed-here"></a>Jeg får vist en anden meddelelse end den, der er angivet her

Du kan [ændre planer manuelt eller](change-plans-manually.md) [ringe til support](../../admin/get-help-support.md).

### <a name="additional-reasons-you-cant-upgrade"></a>Yderligere årsager til, at du ikke kan opgradere

#### <a name="you-have-two-or-more-plans-for-the-same-product"></a>Du har to eller flere planer for det samme produkt

Du kan kun bruge fanen **Opgrader** , hvis alle brugere abonnerer på den samme plan. Hvis du f.eks. har to Microsoft 365 Business Standard-planer, kan du ikke automatisk opgradere en af dem til en anden plan.

#### <a name="you-have-a-prepaid-plan"></a>Du har en forudbetalt plan

Hvis du har betalt for dit abonnement på forhånd, kan du muligvis [ændre planerne manuelt](change-plans-manually.md). Du får dog ikke krediteret ubrugt resterende tid i dit nuværende abonnement, hvis du opgraderer planer, før den aktuelle plan udløber.

Du kan også ringe [til support](../../admin/get-help-support.md) for at få hjælp.

#### <a name="you-have-a-government-or-non-profit-plan"></a>Du har en plan til offentlige myndigheder eller non-profit organisationer

Hvis du har en plan til offentlige myndigheder eller non-profit organisationer, kan du [ændre planer manuelt](change-plans-manually.md) eller ringe [til support](../../admin/get-help-support.md) for at få hjælp.

#### <a name="the-subscription-that-you-want-to-upgrade-from-has-a-temporary-issue"></a>Det abonnement, du vil opgradere fra, har et midlertidigt problem

Du kan muligvis ikke se nogen planer på **fanen** Opgrader, fordi tjenesten er i gang med at opgradere et stort antal planer. Prøv igen om en time efter det første forsøg.

#### <a name="the-plan-that-you-want-to-upgrade-to-isnt-a-supported-option"></a>Den plan, du vil opgradere til, understøttes ikke

Når du opgraderer planer, vises de planer, du kan opgradere til, baseret på tjenesterne i din aktuelle plan. Du kan kun opgradere til en plan, der har de samme datarelaterede tjenester, f.eks. Exchange Online eller SharePoint Online, eller til en nyere version af dem. Dette sikrer, at brugerne ikke\' mister data, der er relateret til disse tjenester under opgraderingen.

Hvis din plan ikke er berettiget til at opgradere planer automatisk, kan du muligvis ændre [planerne manuelt i](change-plans-manually.md) stedet. Du kan også ringe [til support](../../admin/get-help-support.md) for at få hjælp.

#### <a name="your-subscription-has-an-add-on"></a>Dit abonnement har et tilføjelsesprogrammet

Hvis du har et tilføjelsesprogrammet med dit abonnement, kan du muligvis [ændre plan manuelt](change-plans-manually.md).

#### <a name="your-subscription-has-an-unpaid-balance"></a>Der er en ubetalt saldo på dit abonnement

For at løse dette skal du finde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">abonnementet på siden</a> Dine produkter og vælge **linket** Betal nu i **afsnittet** Fakturering. Når betalingen er foretaget, skal du kontrollere **fanen Opgrader** igen.

## <a name="what-does-upgrading-a-plan-do-to-my-service-and-billing"></a>Hvordan opgraderer jeg et abonnement til min tjeneste og fakturering?

Når du opgraderer planer automatisk ved hjælp  af knappen Skift planer (eller  fanen Opgrader i den nye Administration), påvirkes dine tjenester og fakturering.

### <a name="access-to-services"></a>Adgang til tjenester

**Administratorer** kan ikke bruge Administration, mens planen opgraderes. Det kan tage op til en time.
  
**Brugerne** vil ikke opleve afbrydelser af tjenesten. De vil fortsat have den eksisterende tjeneste, indtil opgraderingen er fuldført.
  
### <a name="users-and-licenses"></a>Brugere og licenser

Brugere på det gamle abonnement flyttes automatisk til det nye abonnement.

Hvis dit gamle abonnement omfatter flere tjenester, og hvis du har ændret, hvilke af disse tjenester brugerne er tildelt til, kan det være en ide at notere dette, før du opgraderer planer, så du kan genskabe disse ændringer bagefter. Alle brugere får adgang til alle tjenester i det nye abonnement. Hvis du f.eks. tidligere har købt Microsoft 365 Business Premium til alle 100 af dine brugere, men ikke har tildelt SharePoint Online-tjenesten fra 50 af dem, bevares denne ændring ikke, efter du har opgraderet planerne.

Hvis du har mere end ét abonnement, før du opgraderer planer, og har brugere, der har fået tildelt licenser til mere end ét abonnement, bevares dette tildelingsmønster så meget som muligt i det nye abonnement.
Alle brugerdata bevares under opgraderingen, herunder Exchange postkasser og SharePoint Online-dokumenter, -lister og andre oplysninger.
  
### <a name="billing"></a>Fakturering

Den dag, hvor planopgraderingen er fuldført, bliver fakturering på dit gamle abonnement deaktiveret, og fakturering på dit nye abonnement bliver aktiveret. Du får en forholdsmæssig kredit for alle ubrugte tjenester på det gamle abonnement. Du modtager en ny faktura, der indeholder kreditten for dit gamle abonnement inden for 30 dage efter opgraderingen til det nye abonnement.
  
> [!NOTE]
> Hvor lang tid det faktisk tager at kreditere din betalingskonto, afhænger af den betalingsmetode, der blev brugt til abonnementet.
  
**Opgraderer du fra et forudbetalt abonnement, før det udløber?** Hvis den samlede pris for dit nye abonnement er større end eller lig med den resterende værdi af dit forudbetalte abonnement, mister du ikke nogen forudbetalt tid. På betalingssiden får du vist en kredit for din ubrugte tid. Men hvis den samlede pris for dit nye abonnement er mindre end den resterende værdi af dit nuværende forudbetalte abonnement, mister du noget af din ubrugte tid. Du får besked, før du skal betale, og du kan vente med at opgradere, indtil du er tættere på udløbsdatoen for dit forudbetalte abonnement.

## <a name="call-support-to-help-you-upgrade-plans"></a>Ring til support for at få hjælp til at opgradere planer

[Ring til Microsoft Support](../../admin/get-help-support.md).

## <a name="related-content"></a>Relateret indhold

[Skift planer manuelt](change-plans-manually.md) (artikel)\
[Sikkerhedskopier data, før du Microsoft 365 planer til for virksomheder](back-up-data-before-switching-plans.md) (artikel)
