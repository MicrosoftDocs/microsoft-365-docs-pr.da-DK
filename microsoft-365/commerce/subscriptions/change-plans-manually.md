---
title: Skift Microsoft 365 til virksomheder-planer manuelt
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: nalinkla, jmueller
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
description: Skift abonnementer manuelt ved at købe et nyt abonnement og sikre, at både abonnementerne er angivet og aktive.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: 5e2d9e3da47c8d9c86e3e0b6d3d0b648c6016509
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493547"
---
# <a name="manually-change-microsoft-plans"></a>Skift Microsoft-planer manuelt

## <a name="step-1-decide-how-to-change-plans"></a>Trin 1: Beslut, hvordan du vil ændre planer

Den bedste måde at ændre alle dine brugere fra én plan til en anden på er ved at [bruge fanen Opgrader](upgrade-to-different-plan.md). Nogle gange er dette ikke muligt. Skift planer manuelt i stedet:

- Hvis fanen **Opgradering** angiver, at du ikke kan opgradere den aktuelle plan.

- Hvis den ønskede plan ikke vises, når du vælger fanen **Opgrader** .

- Hvis du ikke vil opgradere alle dine brugere på samme måde. Nogle virksomheder har brug for forskellige brugere, der abonnerer på forskellige planer. Brug en manuel ændring til dette.

Hvis du vil fortsætte med en manuel ændring, skal du læse [Trin 2: Køb et nyt abonnement](#step-2-buy-a-new-subscription) i dette emne.

> [!IMPORTANT]
> Hvis du skifter til en plan med færre datarelaterede tjenester end din aktuelle plan (nedgradering), skal du manuelt sikkerhedskopiere de data, du vil beholde. Du kan få flere oplysninger under [Sikkerhedskopiér data, før du ændrer planer](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Trin 2: Køb et nyt abonnement

**Har du allerede købt?** Hvis du allerede har et abonnement, du vil flytte brugere til, skal du springe dette trin over og gå til [Trin 3: Kontrollér dit nye abonnement og dine licenser](#step-3-check-your-new-subscription-and-licenses) i dette emne.

ELLER

**Køb et nyt abonnement og nye licenser:** Følg trinnene i [Køb et andet Abonnement på Microsoft 365 til virksomheder for](../try-or-buy-microsoft-365.md) at købe et nyt abonnement.

Sørg for at købe et abonnement til den samme organisation, som brugerne er i nu. Kontrollér f.eks. mailadresserne for de brugere, du vil flytte. Hvis deres mailadresser indeholder \@contoso.com, skal du købe et nyt abonnement til contoso.com.
Medtag en licens for hver bruger, du vil flytte.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Trin 3: Kontrollér dit nye abonnement og dine nye licenser

1. I Administration skal du gå til siden **Fakturering**\><a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.

2. **Kontrollér, at begge abonnementer er angivet og aktive** Det abonnement, du flytter brugere fra, og det abonnement, du flytter brugere til, skal angives sammen. Hvis det nye abonnement ikke er der, første gang du kontrollerer det, kan du prøve igen senere. Kontrollér, at begge abonnementer er aktive. [Det nye abonnement er ikke angivet eller er ikke aktivt](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Kontrollér, at du har tilstrækkelige licenser til hver bruger** Hver bruger skal have en licens, der svarer til deres abonnement. Så hvis du vil flytte ti brugere til Microsoft 365 Business Premium, skal du sikre dig, at der er ti licenser tilgængelige.

4. **Har du brug for flere licenser til det nye abonnement?**
   Gå til siden **Dine produkter** , og [køb flere licenser](../licenses/buy-licenses.md).

> [Hvad med de gamle licenser?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Det nye abonnement er ikke angivet eller er ikke aktivt

- **Hvis du har købt to abonnementer, og de ikke begge er angivet her**, kan de være blevet købt til forskellige organisationer (til forskellige domæner). Abonnementer kan ikke krydse organisationsgrænser.

- **Hvis du ved, at du har et ekstra abonnement**, og det ikke er angivet her eller ikke er aktivt, [kan du ringe til Microsoft Support](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Hvad med de gamle licenser?

Licenserne for det aktuelle abonnement fjernes senere. du betaler kun for de nye brugerlicenser fra da af.

## <a name="step-4-reassign-licenses"></a>Trin 4: Tildel licenser igen

Når du opgraderer fra en Office 365 plan til en Microsoft 365-plan, skal du ændre licenstildelingerne for alle brugere. Licenser tildeles ikke automatisk, når du ændrer planer manuelt.

### <a name="reassign-a-license-for-one-user"></a>Tildel en licens til én bruger igen

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

2. På siden **Aktive brugere** skal du vælge den bruger, du vil tildele en licens til.

3. Under fanen **Licenser og apps** skal du udvide **Licenser**, markere felterne for de licenser, du vil tildele, og derefter vælge **Gem ændringer**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Tildel licenser til flere brugere på én gang

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

2. Vælg cirklerne ud for navnene på de brugere, du vil erstatte eksisterende licenser for.

3. Øverst skal du vælge de tre prikker (flere handlinger) og derefter vælge **Administrer produktlicenser**.

4. Vælg **Erstat eksisterende produktlicenstildelinger** \> **Næste**.

5. Skift til/fra-knappen til positionen **Til** for de produkter, du vil tildele disse brugere.

    > [!TIP]
    > - Hvis du vil begrænse, hvilke tjenester der er tilgængelige for brugeren, skal du skifte til  til/fra-positionen for de tjenester, du vil fjerne for den pågældende bruger. Hvis du f.eks. ønsker, at brugeren skal have adgang til alle tilgængelige tjenester undtagen Skype for Business Online, kan du skifte til/fra-knappen for Skype for Business Online-tjenesten til positionen **Fra**.
    > - Alle tidligere licenstildelinger for de valgte brugere fjernes.

6. Nederst i ruden **Erstat eksisterende produkter** skal du vælge **Erstat** \> **luk**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Trin 5: Annuller abonnementer, eller fjern licenser, du ikke længere har brug for (valgfrit)

Hvis du har flyttet alle brugere fra ét abonnement til et andet, og du ikke længere har brug for det oprindelige abonnement, kan du [annullere abonnementet](cancel-your-subscription.md).

Hvis du kun har flyttet nogle brugere til et andet abonnement, skal du [fjerne licenser](../licenses/buy-licenses.md) , du ikke længere har brug for.

## <a name="call-support-to-help-you-change-plans"></a>Kontakt support for at hjælpe dig med at ændre planer

[Kontakt Microsoft Support](../../admin/get-help-support.md).
