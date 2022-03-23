---
title: Ændre Microsoft 365 planer for virksomheder manuelt
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
- AdminSurgePortfolio
search.appverid: MET150
description: Skift abonnementer manuelt ved at købe et nyt abonnement og sikre, at begge abonnementer er angivet og aktive.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: adc76ff3fbfa5fd81893f0b260e76018288350f1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588484"
---
# <a name="change-plans-manually"></a>Skift planer manuelt

## <a name="step-1-decide-how-to-change-plans"></a>Trin 1: Beslut, hvordan du ændrer plan

Den bedste måde at ændre alle dine brugere fra én plan til en anden er at [bruge fanen Opgrader](upgrade-to-different-plan.md). Nogle gange er dette ikke muligt. Skift planer manuelt i stedet:

- Hvis fanen **Opgrader** angiver, at du ikke kan opgradere den aktuelle plan.

- Hvis den ønskede plan ikke **vises** , når du vælger fanen Opgrader.

- Hvis du ikke vil opgradere alle dine brugere på samme måde. Nogle virksomheder har brug for, at forskellige brugere abonnerer på forskellige planer. Brug en manuel ændring til dette.

Hvis du vil fortsætte med en manuel ændring, skal [du læse Trin 2: Køb et nyt abonnement](#step-2-buy-a-new-subscription) i dette emne.

> [!IMPORTANT]
> Hvis du ændrer til en plan med færre datarelaterede tjenester end din aktuelle plan (nedgradering), skal du manuelt sikkerhedskopiere alle data, du vil beholde. Du kan finde flere oplysninger i [Sikkerhedskopier data, før du ændrer planer](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Trin 2: Køb et nyt abonnement

**Har du allerede købt?** Hvis du allerede har et abonnement, som du vil flytte brugere til, skal du springe dette trin over og gå til Trin 3: Kontrollér dit nye abonnement og [dine nye](#step-3-check-your-new-subscription-and-licenses) licenser i dette emne.

ELLER

**Køb et nyt abonnement og nye licenser:** Følg trinnene i Køb [et andet Microsoft 365 for business-abonnement](../try-or-buy-microsoft-365.md) for at købe et nyt abonnement.

Sørg for, at du køber et abonnement til den samme organisation, som brugerne er i nu. Kontrollér f.eks. mailadresserne på de brugere, du vil flytte. Hvis deres mailadresser contoso.com \@, skal du købe et nyt abonnement til contoso.com.
Medtag en licens for hver bruger, du vil flytte.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Trin 3: Kontrollér dit nye abonnement og dine nye licenser

1. I Administration skal du gå til **siden Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">dine</a> produkter.

2. **Kontrollér, at begge abonnementer er angivet og aktive** Det abonnement, som du flytter brugere fra, og det abonnement, du flytter brugere til, skal være angivet sammen. Hvis det nye abonnement ikke vises, når du tjekker første gang, kan du prøve igen senere. Kontrollér, at begge abonnementer er aktive. [Det nye abonnement er ikke angivet eller er ikke aktivt](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Kontrollér, at du har nok licenser til hver bruger** Hver bruger skal have en licens, der svarer til deres abonnement. Så hvis du vil flytte ti brugere til Microsoft 365 Business Premium, skal du sikre dig, at ti licenser er tilgængelige.

4. **Har du brug for flere licenser til det nye abonnement?**
   Gå til siden **Dine produkter** , og [køb flere licenser](../licenses/buy-licenses.md).

> [Hvad med de gamle licenser?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Det nye abonnement er ikke angivet eller er ikke aktivt

- **Hvis du har købt to abonnementer, og** de ikke begge er angivet her, kan de være blevet købt til forskellige organisationer (med forskellige domæner). Abonnementer kan ikke gå på tværs af organisationsgrænser.

- **Hvis du ved, at du har et ekstra abonnement**, og det ikke er angivet her, eller ikke er aktivt, skal du [ringe til Microsoft Support](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Hvad med de gamle licenser?

Licenserne for det aktuelle abonnement fjernes senere. skal du derefter kun betale for de nye brugerlicenser.

## <a name="step-4-reassign-licenses"></a>Trin 4: Tildel licenser igen

Når du opgraderer fra Office 365 til en Microsoft 365-plan, skal du ændre licenstildelingerne for alle brugere. Licenser tildeles ikke automatisk, når du ændrer plan manuelt.

### <a name="reassign-a-license-for-one-user"></a>Tildel en licens til én bruger igen

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

2. Vælg den **bruger** , du vil tildele en licens til, på siden Aktive brugere.

3. På fanen **Licenser og apps** skal du **udvide Licenser**, markere felterne for de licenser, du vil tildele, og derefter vælge **Gem ændringer**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Tildel licenser til flere brugere på én gang

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

2. Markér cirklerne ud for navnene på de brugere, som du vil erstatte eksisterende licenser for.

3. Øverst skal du vælge de tre prik (flere handlinger) og derefter vælge **Administrer produktlicenser**.

4. Vælg **Erstat eksisterende produktlicenstildelinger** \> **Næste**.

5. Skift til/fra-knappen **til positionen** Til for de produkter, du vil tildele disse brugere.

    > [!TIP]
    > - Hvis du vil begrænse, hvilke tjenester der er tilgængelige for brugeren, skal du skifte til **Fra** for de tjenester, du vil fjerne for den pågældende bruger. Hvis du f.eks. vil have, at brugeren skal have adgang til alle tilgængelige tjenester med undtagelse af Skype for Business Online, kan du skifte til/fra-knappen for Skype for Business Online-tjenesten til **positionen Fra.**
    > - Eventuelle tidligere licenstildelinger for de valgte brugere fjernes.

6. Nederst i ruden **Erstat eksisterende produkter skal** du vælge **Erstat** \> **Luk**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Trin 5: Annuller abonnementer, eller fjern licenser, du ikke længere skal bruge (valgfrit)

Hvis du har flyttet alle brugere fra ét abonnement til et andet, og du ikke længere har brug for det oprindelige abonnement, kan [du annullere abonnementet](cancel-your-subscription.md).

Hvis du kun har flyttet nogle brugere til et andet abonnement, skal du [fjerne licenser, du](../licenses/buy-licenses.md) ikke længere har brug for.

## <a name="call-support-to-help-you-change-plans"></a>Ring til support for at få hjælp til at ændre planer

[Ring til Microsoft Support](../../admin/get-help-support.md).
