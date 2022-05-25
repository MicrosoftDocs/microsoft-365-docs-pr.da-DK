---
title: Administrer køb via selvbetjening (administratorer)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: prlachhw, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
description: Administratorer kan få mere at vide om, hvordan de administrerer selvbetjeningskøb, der foretages af brugere i deres organisation.
ms.date: 05/24/2022
ms.openlocfilehash: 50d782052839c099f3c64e45cc82a6f2ae5ba853
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663508"
---
# <a name="manage-self-service-purchases-admin"></a>Administrer køb via selvbetjening (Administration)

Som administrator kan du se køb via selvbetjening foretaget af personer i din organisation. Du kan se produktnavn, købernavn, købte abonnementer, udløbsdato, købspris og tildelte brugere for hvert køb via selvbetjening. Hvis det kræves af din organisation, kan du slå køb via selvbetjening fra pr. produkt via PowerShell. Du har de samme politikker for dataadministration og adgang til produkter, der er købt via køb via selvbetjening eller centralt.

Du kan også styre, om brugere i din organisation kan foretage køb via selvbetjening. Du kan få flere oplysninger under [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Få vist selvbetjeningsabonnementer

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Fakturering**><a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Fakturering**\><a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Dine produkter</a>.
::: moniker-end

2. Under fanen **Produkter** skal du vælge filterikonet og derefter vælge **Selvbetjening**.
3. Hvis du vil have vist flere oplysninger om et abonnement, skal du vælge et på listen.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Få vist, hvem der har licenser til et selvbetjeningskøbsabonnement

> [!NOTE]
> Som administrator kan du ikke tildele eller fjerne tildeling af licenser til et selvbetjeningskøbsabonnement, der er købt af en bruger i din organisation. Du kan [overtage et selvbetjeningskøbsabonnement](#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildeling af licenser.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Faktureringslicenser</a>  >.

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

2. Vælg filterikonet, og vælg derefter **Selvbetjening**.
3. Vælg et produkt for at få vist licenser, der er tildelt personer.
    > [!NOTE]
    > Hvis der er flere køb for et produkt, vises det pågældende produkt kun én gang, og kolonnen **Tilgængelig mængde** viser det samlede antal abonnementer, der er købt for det pågældende produkt.
4. Listen **Brugere** er grupperet efter navnene på de personer, der foretog køb via selvbetjening.
5. Hvis du vil eksportere en liste over brugere med licenser til disse abonnementer, skal du vælge de abonnementer, du vil eksportere, og derefter vælge **Eksportér brugere**.

## <a name="disable-or-enable-self-service-purchases"></a>Deaktiver eller aktivér køb via selvbetjening

Du kan deaktivere eller aktivere køb via selvbetjening for brugere i din organisation. **MSCommerce** PowerShell-modulet indeholder en **PolicyID-parameterværdi** for **AllowSelfServicePurchase**, der giver dig mulighed for at styre, om brugerne i din organisation kan foretage køb via selvbetjening, og for hvilke produkter.

Du kan bruge **MSCommerce PowerShell-modulet** til at:

- Få vist standardtilstanden for parameterværdien **AllowSelfServicePurchase** – uanset om den er aktiveret eller deaktiveret af produktet
- Få vist en liste over relevante produkter, og om køb via selvbetjening er aktiveret eller deaktiveret
- Få vist eller rediger den aktuelle indstilling for et bestemt produkt for enten at aktivere eller deaktivere det

> [!IMPORTANT]
> Når du bruger politikken **AllowSelfServicePurchase** , aktiverer eller deaktiverer den både selvbetjeningskøb og selvbetjeningstest. Du kan se en liste over de produkter, der kan købes via selvbetjening, under [Få vist en liste over produkter til køb via selvbetjening og deres status](allowselfservicepurchase-powershell.md#view-a-list-of-self-service-purchase-products-and-their-status). Det er kun Project og Visio, der er tilgængelige for prøveabonnementer.

Du kan få flere oplysninger under [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Centraliser licenser under et enkelt abonnement

Du kan tildele eksisterende licenser eller købe yderligere abonnementer via eksisterende aftaler for brugere, der er tildelt til køb via selvbetjening. Når du har tildelt disse centralt købte licenser, kan du anmode køberne om at annullere deres eksisterende abonnementer.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Faktureringskøbstjenester</a>  >.

::: moniker-end

::: moniker range="o365-21vianet"

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a> skal du gå til siden **Fakturering** > **Køb tjenester** .

::: moniker-end

2. Find og vælg det produkt, du vil købe, og vælg derefter **Køb**.
3. Fuldfør de resterende trin for at fuldføre dit køb.
4. Følg trinnene i [Få vist, hvem der har licenser til et abonnement, der er købt via selvbetjening](#view-who-has-licenses-for-a-self-service-purchase-subscription) , for at eksportere en liste over brugere, der skal refereres til i næste trin.
5. Tildel licenser til alle, der har en licens i det andet abonnement. Du kan finde komplette trin under [Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md).
6. Kontakt den person, der har købt abonnementet på køb via selvbetjening, og bed vedkommende om at [annullere det](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Overtag et selvbetjeningskøbsabonnement

Du kan overtage et selvbetjeningskøbsabonnement, der er oprettet af en bruger i din organisation. Når du overtager et købsabonnement via selvbetjening, har du to muligheder:

1. Flyt brugerne til et andet abonnement, og annuller det oprindelige abonnement.
2. Annuller abonnementet på køb via selvbetjening, og fjern licenser fra tildelte brugere.

### <a name="move-users-to-a-different-subscription"></a>Flyt brugere til et andet abonnement

Når du flytter brugere til et andet abonnement, annulleres det gamle abonnement automatisk. Den bruger, der oprindeligt købte abonnementet på køb via selvbetjening, modtager en mail, hvor der står, at abonnementet er blevet annulleret.

> [!NOTE]
> Du skal have en tilgængelig licens for hver bruger, du flytter i det abonnement, du flytter brugere til.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Fakturering**><a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a> skal du gå til siden **Fakturering** > **af dine produkter** .

::: moniker-end

2. Under fanen **Produkter** skal du vælge filterikonet og derefter vælge **Selvbetjening**.
3. Vælg det abonnement, du vil overtage.
4. På siden med abonnementsoplysninger skal du i afsnittet **Abonnementer og indstillinger** vælge **Tag kontrol over dette abonnement**.
5. Vælg **Flyt brugere** i ruden til højre.
6. Vælg det produkt, du vil flytte brugerne til, og vælg derefter **Flyt brugere**.
7. I feltet **Flyt brugere til** skal du vælge **Flyt brugere**. Flytteprocessen kan tage flere minutter. Luk ikke browseren, mens processen kører.
8. Når flytteprocessen er færdig, skal du lukke **ruden Flyt fuldført**.
9. På siden med abonnementsoplysninger vises **abonnementsstatussen** for det købte abonnement via selvbetjening som **Slettet**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Annuller et selvbetjeningskøbsabonnement

Når du vælger at annullere et selvbetjeningskøbsabonnement, mister brugere med licenser adgang til produktet. Den bruger, der oprindeligt købte abonnementet på køb via selvbetjening, modtager en mail, hvor der står, at abonnementet er blevet annulleret.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Fakturering**><a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a> skal du gå til siden **Fakturering** > **af dine produkter** .

::: moniker-end

2. Under fanen **Produkter** skal du vælge filterikonet og derefter vælge **Selvbetjening**.
3. Vælg det abonnement, du ønsker at annullere.
4. På siden med abonnementsoplysninger skal du i afsnittet **Abonnementer og indstillinger** vælge **Tag kontrol over dette abonnement**.
5. Vælg **Annuller abonnement** i ruden til højre.
6. Vælg en årsag til din annullering på rullelisten, og vælg derefter **Annuller abonnement**.
7. I feltet **Er du sikker på, at du vil annullere? skal du** vælge **Annuller abonnement**.
8. Luk ruden til højre.
9. På siden med abonnementsoplysninger vises **abonnementsstatus** som **Slettet**.

## <a name="need-help-contact-us"></a>Har du brug for hjælp? Kontakt os.

Du kan få almindelige spørgsmål om køb via selvbetjening under [Ofte stillede spørgsmål om køb via selvbetjening](self-service-purchase-faq.yml).

Hvis du har spørgsmål eller har brug for hjælp til køb via selvbetjening, [skal du kontakte support](../../admin/get-help-support.md).
