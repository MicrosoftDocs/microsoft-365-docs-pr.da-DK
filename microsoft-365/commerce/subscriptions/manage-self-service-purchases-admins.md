---
title: Administrer selvbetjeningskøb (administratorer)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
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
description: Administratorer kan lære, hvordan de administrerer selvbetjeningskøb foretaget af brugere i organisationen.
ms.date: 03/26/2021
ms.openlocfilehash: 19f276107de7b1dd1053e500d249950a8700ac41
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587959"
---
# <a name="manage-self-service-purchases-admin"></a>Administrer selvbetjeningskøb (administrator)

Som administrator kan du se selvbetjeningskøb foretaget af personer i organisationen. Du kan se produktnavn, indkøbernavn, købte abonnementer, udløbsdato, købspris og tildelte brugere for hvert selvbetjeningskøb. Hvis din organisation kræver det, kan du deaktivere selvbetjeningskøb pr. produkt via PowerShell. Du har de samme dataadministrations- og adgangspolitikker for produkter, der er købt via selvbetjeningskøb eller centralt.

Du kan også styre, om brugerne i organisationen kan foretage selvbetjeningskøb. Få mere at vide under [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Få vist selvbetjeningsabonnementer

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">dine</a> produkter.
::: moniker-end

2. På fanen **Produkter** skal du vælge filterikonet og derefter **vælge Selvbetjening**.
3. Hvis du vil have vist flere oplysninger om et abonnement, skal du vælge et på listen.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Få vist, hvem der har licenser til et abonnement på et selvbetjeningskøb

> [!NOTE]
> Som administrator kan du ikke tildele eller fjerne tildeling af licenser for et selvbetjeningskøbsabonnement, der er købt af en bruger i organisationen. Du kan [overtage et abonnement på et selvbetjeningskøb](#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildelingen af licenser.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Faktureringslicenser**>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Vælg filterikonet, og vælg **derefter Selvbetjening**.
3. Vælg et produkt for at få vist de licenser, der er tildelt til personer.
    > [!NOTE]
    > Hvis der er flere køb for et produkt, er det pågældende produkt kun angivet én gang, og  kolonnen Tilgængeligt antal viser det samlede antal af alle abonnementer, der er købt for det pågældende produkt.
4. Listen **Brugere** er grupperet efter navnene på de personer, der har foretaget selvbetjeningskøb.
5. Hvis du vil eksportere en liste over brugere med licenser til disse abonnementer, skal du vælge de abonnementer, du vil eksportere, og derefter vælge **Eksportér brugere**.

## <a name="disable-or-enable-self-service-purchases"></a>Deaktiver eller aktivér selvbetjeningskøb

Du kan deaktivere eller aktivere selvbetjeningskøb for brugere i organisationen. Modulet **MSCommerce** PowerShell indeholder en **PolicyID-parameterværdi** for **AllowSelfServicePurchase** , som giver dig mulighed for at styre, om brugerne i organisationen kan foretage selvbetjeningskøb og for hvilke produkter.

Du kan bruge **MSCommerce** PowerShell-modulet til at:

- Få vist standardtilstanden for **parameterværdien AllowSelfServicePurchase** – uanset om den er aktiveret eller deaktiveret efter produkt
- Få vist en liste over relevante produkter, og om selvbetjeningskøb er aktiveret eller deaktiveret
- Få vist eller rediger den aktuelle indstilling for et bestemt produkt for enten at aktivere eller deaktivere det

Få mere at vide under [Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Centralisere licenser under et enkelt abonnement

Du kan tildele eksisterende licenser eller købe yderligere abonnementer via eksisterende aftaler for brugere, der er tildelt til selvbetjeningskøb. Når du tildeler disse centralt købte licenser, kan du anmode om, at indkøbere annullerer deres eksisterende abonnementer.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Faktureringskøbstjenester</a>>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">skal du</a> gå til siden **Faktureringskøb**  > af tjenester.

::: moniker-end

2. Find og vælg det produkt, du vil købe, og vælg derefter **Køb**.
3. Udfør de resterende trin for at fuldføre dit køb.
4. Følg trinnene i Se, [hvem der har licenser til](#view-who-has-licenses-for-a-self-service-purchase-subscription) et selvbetjeningskøbt abonnement for at eksportere en liste over brugere, der skal refereres til, i næste trin.
5. Tildel licenser til alle, der har en licens i det andet abonnement. Se de fulde trin under [Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md).
6. Kontakt den person, der har købt abonnementet på selvbetjening, og bed vedkommende om at [annullere det](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Overtage et selvbetjeningskøbsabonnement

Du kan overtage et selvbetjeningskøbsabonnement, som er foretaget af en bruger i organisationen. Når du overtager et abonnement på et selvbetjeningskøb, har du to muligheder:

1. Flyt brugerne til et andet abonnement, og annuller det oprindelige abonnement.
2. Annuller selvbetjeningskøbsabonnementet, og fjern licenser fra tildelte brugere.

### <a name="move-users-to-a-different-subscription"></a>Flytte brugere til et andet abonnement

Når du flytter brugere til et andet abonnement, annulleres det gamle abonnement automatisk. Den bruger, der oprindeligt købte selvbetjeningskøbsabonnementet, modtager en mail, hvor der står, at abonnementet blev annulleret.

> [!NOTE]
> Du skal have en tilgængelig licens for hver bruger, du flytter i det abonnement, du flytter brugere til.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">skal</a> du gå til **siden Fakturering** > **dine** produkter.

::: moniker-end

2. På fanen **Produkter** skal du vælge filterikonet og derefter **vælge Selvbetjening**.
3. Vælg det abonnement, du vil overtage.
4. På siden med abonnementsoplysninger i **sektionen Abonnementer og indstillinger skal** du vælge **Tag kontrol over dette abonnement**.
5. Vælg Flyt brugere i højre **rude**.
6. Vælg det produkt, du vil flytte brugerne til, og vælg derefter **Flyt brugere**.
7. I feltet **Flyt brugere til** skal du vælge **Flyt brugere**. Flytningsprocessen kan tage flere minutter. Luk ikke browseren, mens processen kører.
8. Når flytningen er færdig, skal du lukke **ruden Flyt fuldført**.
9. På siden med abonnementsoplysninger vises **Abonnementsstatus** for det selvkøbte abonnement som **Slettet**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Annuller et abonnement på selvbetjeningskøb

Når du vælger at annullere et abonnement på et selvbetjeningskøb, mister brugere med licenser adgang til produktet. Den bruger, der oprindeligt købte selvbetjeningskøbsabonnementet, modtager en mail, hvor der står, at abonnementet blev annulleret.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">skal</a> du gå til **siden Fakturering** > **dine** produkter.

::: moniker-end

2. På fanen **Produkter** skal du vælge filterikonet og derefter **vælge Selvbetjening**.
3. Vælg det abonnement, du ønsker at annullere.
4. På siden med abonnementsoplysninger i **sektionen Abonnementer og indstillinger skal** du vælge **Tag kontrol over dette abonnement**.
5. Vælg Annuller abonnement i højre **rude**.
6. Vælg en årsag til din annullering på rullelisten, og vælg derefter **Annuller abonnement**.
7. I feltet **Er du sikker på, at du vil annullere?** skal du vælge **Annuller abonnement**.
8. Luk højre rude.
9. På siden med abonnementsoplysninger **vises Abonnementsstatus** som **Slettet**.

## <a name="need-help-contact-us"></a>Har du brug for hjælp? Kontakt os.

Du kan finde almindelige spørgsmål om selvbetjeningskøb i [Ofte stillede spørgsmål om selvbetjeningskøb](self-service-purchase-faq.yml).

Hvis du har spørgsmål eller har brug for hjælp til selvbetjeningskøb, skal du [kontakte support](../../admin/get-help-support.md).
