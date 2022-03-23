---
title: Opgrader fra et Office 365 E4-abonnement
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
- customer-email
- admindeeplinkMAC
search.appverid: MET150
description: Få mere at vide om, hvordan du opgraderer fra Office 365 E4-abonnement.
ms.date: 08/14/2020
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 60e7cb7c97255f3588c99a0eb66bc7c8379de8b9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590359"
---
# <a name="upgrade-from-an-office-365-e4-subscription"></a>Opgrader fra et Office 365 E4-abonnement

I denne artikel bliver du vej vejet gennem processen med at opgradere fra Office 365 E4 til et nyt abonnement. Du kan finde oplysninger om de muligheder, der er tilgængelige, når du opgraderer fra Office 365 E4, [under Vigtige oplysninger for Office 365 E4-kunder](important-information-e4.md).

> [!IMPORTANT]
> Denne artikel gælder kun Office 365 E4-abonnementer, der er købt direkte fra Microsoft via kreditkort eller faktura. Hvis dit abonnement blev købt på en anden måde, f.eks. via en partner eller via Volume Licensing Service Center, skal du kontakte din Microsoft-kunderepræsentant eller -partner for at få hjælp til at opgradere planer.

## <a name="what-are-my-options-for-how-to-upgrade"></a>Hvilke muligheder har jeg for at opgradere?

Den nemmeste måde at opgradere din plan på er ved **at bruge** fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Opgrader i Microsoft 365 Administration</a>. Brug af fanen **Opgrader** understøttes dog ikke i alle situationer. Hvis dit scenarie ikke understøttes, kan du muligvis opgradere planer manuelt.

## <a name="what-is-the-upgrade-tab"></a>Hvad er fanen Opgrader?

Fanen **Opgrader** udfører følgende opgaver for dig:

- Fører dig gennem processen med at købe en ny plan.
- Omfordeler alle brugerlicenser fra din gamle plan til den nye plan.
- Annullerer din gamle plan.

## <a name="what-does-it-mean-to-upgrade-plans-manually"></a>Hvad vil det sige at opgradere planer manuelt?

Opgradering af planer manuelt betyder, at du skal udføre følgende separate procedurer i stedet for at bruge **fanen** Opgrader.

- Køb et nyt abonnement med det rigtige antal licenser.
- Kontrollér, at det nye abonnement er klar til brug.
- Tildel licenser til brugerne.
- Annullere det oprindelige Office 365 E4-abonnement.

## <a name="find-out-if-you-can-use-the-upgrade-tab-to-upgrade-to-a-new-plan"></a>Find ud af, om du kan bruge fanen Opgrader til at opgradere til en ny plan

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. Vælg dit Office 365 E4-abonnement.
3. Vælg fanen **Opgrader** . Hvis du kan se andre planer på listen, betyder det, at du kan opgradere planer automatisk.
4. Hvis du ikke kan opgradere automatisk, får du vist en meddelelse, der beskriver årsagen til, at du ikke kan opgradere.

Der er flere årsager til, at du ikke kan opgradere planer automatisk. De fleste af problemerne er midlertidige, f.eks. problemer med tjeneste sundhed, som du kan løse. Du kan få mere at [vide under Hvorfor kan jeg ikke opgradere planer?](upgrade-to-different-plan.md#why-cant-i-upgrade-plans) Hvis du har brug for hjælp til din opgradering, kan [du kontakte support](../../admin/get-help-support.md).

## <a name="will-a-credit-check-be-required"></a>Skal der kontrolleres kredit?

Hvis du betaler for den nye plan via faktura, eller hvis købet er over et bestemt gebyr, kan det være nødvendigt med kontrol af din kreditværdig mail. Hvis en kreditkontrol er nødvendig, kan opgraderingen tage op til to arbejdsdage. Administratorer har ikke adgang til kreditkontrollen Microsoft 365 Administration før kreditkontrollen er fuldført. Men brugerne har stadig fuld adgang til E4-planen, indtil opgraderingen er færdig.

## <a name="upgrade-your-plan-by-using-the-upgrade-tab"></a>Opgrader din plan ved hjælp af fanen Opgrader

### <a name="before-you-begin"></a>Før du begynder

Her er nogle ting, der er vigtige at vide, før du begynder.

- **Planlæg administrativ nedetid.** Administratorer kan ikke bruge administratorerne Microsoft 365 Administration mens planen opgraderes. Afhængigt af antallet af brugere, du har, kan opgraderingen tage fra minutter til timer. Vi anbefaler, at du planlægger at udføre opgraderingen, når du ikke har brug for at foretage opdateringer ved hjælp Microsoft 365 Administration.

    Brugerne oplever ikke afbrydelser af tjenesten, mens planen opgraderes – de har fortsat fuld adgang til E4-abonnementet under opgraderingsprocessen. Når opgraderingen er færdig, har brugerne adgang til den nye plan.
- **Brugere, licenser, fakturering og brugerdefinerede domæner.** For at forstå, hvordan brugere og licenser håndteres under opgraderingen, hvordan opgraderingsplaner påvirker din fakturering, og hvordan du skal håndtere brugerdefinerede domæner, skal du se Hvad gør en opgradering af en plan for min [tjeneste og fakturering?](upgrade-to-different-plan.md#what-does-upgrading-a-plan-do-to-my-service-and-billing)
- **Rediger antallet af brugerlicenser.** Du kan ikke fjerne licenser som en del af opgraderingsplaner. Du kan dog reducere [antallet af licenser, før](../licenses/buy-licenses.md) eller efter du opgraderer planer.

### <a name="start-the-upgrade-by-using-the-upgrade-tab"></a>Start opgraderingen ved hjælp af fanen Opgrader

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. Vælg dit Office 365 E4-abonnement.
3. På siden med abonnementsoplysninger skal du vælge **fanen Opgrader** .
4. Find det abonnement, du vil købe, og vælg derefter **Opgrader**.
5. På siden **Kurv** skal du kontrollere, at alt er korrekt. Vælg, om du vil betale månedligt eller årligt, og bekræft antallet af licenser under **Antal**.
    > [!NOTE]
    > Alle tilføjelsesabonnementer, der er knyttet til Office 365 E4-abonnement, f.eks. Ekstra fillager til Office 365, vises også. Men hvis du har nogen abonnementer på tilføjelser, som er inkluderet i det abonnement, du opgraderer til, fjerner vi dem.
6. Når du har gennemset din ordre, skal du vælge **Gå til kassen**.
7. På siden **Til kassen** skal du **gennemse Solgt til**, **Faktureret** til og **Varer i denne ordre**. Vælg **Rediger** ud for et af disse elementer for at redigere oplysningerne.
    > [!NOTE]
    > Muligheden for at bruge faktura som betalingsmetode er kun tilgængelig for ordrer, der er over et bestemt beløb. Hvis du vælger fakturabetaling, kan det forsinke opgraderingsprocessen med op til to hverdage, hvis der kræves kontrol af kreditværdiglsen.
8. Når du er færdig, skal du vælge **Afstil ordre**.

> [!NOTE]
> Opgradering af planer tager typisk mindre end ti minutter, hvis der ikke er nogen fejl eller problemer. Du kan kontrollere status for din opgradering ved enten at se på dit gamle eller nye abonnement.

## <a name="upgrade-your-plan-manually"></a>Opgrader din plan manuelt

Hvis du manuelt vil opgradere brugere til et andet abonnement, skal du udføre følgende trin i den viste rækkefølge.

- [Trin 1: Køb et nyt abonnement](#step-1-buy-a-new-subscription)
- [Trin 2: Kontrollér, at dit abonnement har det rigtige antal licenser](#step-2-verify-that-your-subscription-has-the-right-number-of-licenses)
- [Trin 3: Tildel licenser til brugerne igen](#step-3-reassign-licenses-to-users)
- [Trin 4: Annuller Office 365 E4-abonnement](#step-4-cancel-the-office-365-e4-subscription)

### <a name="step-1-buy-a-new-subscription"></a>Trin 1: Køb et nyt abonnement

Hvis du endnu ikke har et nyt abonnement, kan du købe endnu [et Microsoft 365 for Business-abonnement](../try-or-buy-microsoft-365.md).

Hvis du allerede har et abonnement, skal du fortsætte til næste trin.

### <a name="step-2-verify-that-your-subscription-has-the-right-number-of-licenses"></a>Trin 2: Kontrollér, at dit abonnement har det rigtige antal licenser

Før du går videre til næste trin, er det vigtigt at sikre, at alle tjenesterne i dit nye abonnement er blevet konfigureret. Hvis abonnementet ikke er klar, når du kontrollerer første gang, kan du prøve igen senere.

> [!NOTE]
> Hvis du vælger at betale for det nye abonnement via faktura, kan det være nødvendigt med kontrol af kreditværdig mail. Det kan tage op til to arbejdsdage, før abonnementet er tilgængeligt.

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. Vælg **Aktiv på** rullelisten **Abonnementsstatus**.
3. Sørg for, at dit nye abonnement vises, og at antallet af licenser er det samme som det, du havde til Office 365 E4.
4. Hvis du har brug for at købe flere licenser, skal du følge trinnene [i Køb eller fjern abonnementslicenser](../licenses/buy-licenses.md).

### <a name="step-3-reassign-licenses-to-users"></a>Trin 3: Tildel licenser til brugerne igen

Du kan bruge [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) til at tildele licenser igen for op til 20 brugere ad gangen. Se, hvordan du gør, [under Flyt brugere til et andet abonnement](move-users-different-subscription.md).

> [!TIP]
> Hvis du har mange brugere, kan du bruge [Office 365 PowerShell til at tildele brugerlicenser flere gange](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).

### <a name="step-4-cancel-the-office-365-e4-subscription"></a>Trin 4: Annuller Office 365 E4-abonnement

Når alle dine brugere er blevet tildelt dit nye abonnement, kan du [annullere abonnementet Office 365 E4](cancel-your-subscription.md).

## <a name="related-content"></a>Relateret indhold

[Opgrader til en anden plan](upgrade-to-different-plan.md) (artikel)\
[Køb eller fjern abonnementslicenser](../licenses/buy-licenses.md) (artikel)\
[Tildel licenser til brugere](../../admin/manage/assign-licenses-to-users.md) (artikel)
