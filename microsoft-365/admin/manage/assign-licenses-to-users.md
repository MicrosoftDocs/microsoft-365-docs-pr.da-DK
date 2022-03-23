---
title: Tildel licenser til brugere
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- TopSMBIssues
- SaRA
- business_assist
- okr_SMB
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Tildel licenser afhængigt af, om du vil tildele produktlicenser til bestemte brugere eller tildele brugerlicenser til et bestemt produkt.
ms.date: 09/16/2021
ms.openlocfilehash: dd0469288ce53ac59663e119022a204130bad3ef
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589959"
---
# <a name="assign-licenses-to-users"></a>Tildel licenser til brugere

Du kan tildele licenser til brugere på **enten siden** Aktive brugere eller på **siden** Licenser. Den metode, du bruger, afhænger af, om du vil tildele produktlicenser til bestemte brugere eller tildele brugerlicenser til et bestemt produkt.

> [!NOTE]
> 
> - Som administrator kan du ikke tildele eller fjerne tildeling af licenser for et selvbetjeningskøbsabonnement, der er købt af en bruger i organisationen. Du kan [overtage et abonnement på et selvbetjeningskøb](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildelingen af licenser.
> - For nogle abonnementer kan du kun opsige i en begrænset periode, efter du har købt eller fornyet dit abonnement. Hvis annulleringsvinduet er udløbet, skal du slå tilbagevendende fakturering fra for at annullere abonnementet i slutningen af abonnementsperioden.

[Lær, hvordan du tilføjer en bruger og tildeler en licens på samme tid](../add-users/add-users.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global, licens- eller brugeradministrator for at tildele licenser. Få mere at vide under [Om Microsoft 365 administratorroller](../add-users/about-admin-roles.md).
- Du kan [tildele Microsoft 365 til brugerkonti med PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Hvis du vil bruge gruppebaseret licensering, skal [du se Tildel licenser til brugere efter gruppemedlemskab Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Nogle tjenester, f.eks. Sway, tildeles automatisk til brugere og behøver ikke tildeles individuelt.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Brug siden Licenser til at tildele licenser til brugere

Når du bruger siden **Licenser** til at tildele licenser, tildeler du licenser til et bestemt produkt til op til 20 brugere. På siden **Licenser** kan du se en liste over alle de produkter, du har abonnementer til. Du kan også se det samlede antal licenser for hvert produkt, hvor mange licenser der er tildelt, og hvor mange der er tilgængelige.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Vælg et produkt.

3. På siden med produktoplysninger skal du vælge **Tildel licenser**.

4. Begynd at **skrive et navn i** ruden Tildel licenser til brugere, og vælg det derefter blandt resultaterne for at føje det til listen. Du kan tilføje op til 20 brugere ad gangen.

4. Vælg **Slå apps og tjenester til eller fra for** at tildele eller fjerne adgang til bestemte elementer.

6. Når du er færdig, skal du vælge **Tildel** og derefter vælge **Luk**.

Hvis der er en konflikt, vises en meddelelse, der fortæller dig, hvad problemet er, og fortæller dig, hvordan du løser det. Hvis du f.eks. har valgt licenser, der indeholder modstridende tjenester, står der i fejlmeddelelsen, at du skal gennemgå de tjenester, der følger med hver licens, og prøve igen.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Ændre de apps og tjenester, som en bruger har adgang til

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. På siden **Licenser** skal du vælge rækken for en bestemt bruger.

3. I højre rude skal du markere eller fjerne markeringen af de apps og tjenester, du vil give adgang til eller fjerne adgang fra.

4. Når du er færdig, skal du **vælge Gem** og derefter vælge **Luk**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Brug siden Aktive brugere til at tildele licenser

Når du bruger siden **Aktive brugere til** at tildele licenser, tildeler du brugerlicenser til produkter.

### <a name="assign-licenses-to-multiple-users"></a>Tildel licenser til flere brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Markér cirklerne ud for navnene på de brugere, du vil tildele licenser til.

3. Øverst skal du vælge **Administrer produktlicenser**.

4. I **ruden Administrer produktlicenser** skal du vælge **Tildel flere: Behold de eksisterende licenser, og tildel flere** \> **Næste**.

5. Under **Licenser** skal du markere feltet for de licenser, som de valgte brugere skal have.\
    Som standard tildeles alle de tjenester, der er knyttet til disse licenser, automatisk til brugerne. Du kan begrænse, hvilke tjenester der er tilgængelige for brugerne. Fravælg felterne for de tjenester, brugerne ikke skal have.

6. Vælg Gem ændringer nederst i **ruden**.  
    Du skal muligvis købe flere licenser, hvis du ikke har nok licenser til alle.

> [!NOTE]
> Hvis du vil tildele licenser til et stort antal brugere, skal du bruge [Tildel licenser til brugere efter gruppemedlemskab Azure Active Directory](/azure/active-directory/enterprise-users/licensing-groups-assign)

### <a name="assign-licenses-to-one-user"></a>Tildele licenser til én bruger

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Markér rækken for den bruger, du vil tildele en licens til.

3. I højre rude skal du vælge **Licenser og apps**.

4. Udvid **sektionen** Licenser, markér felterne for de licenser, du vil tildele, og vælg derefter **Gem ændringer**.

## <a name="assign-a-license-to-a-guest-user"></a>Tildele en licens til en gæstebruger

Du kan invitere gæstebrugere til at samarbejde med din organisation Azure Active Directory Administration. Hvis du vil vide mere om gæstebrugere, [skal du se Hvad er gæstebrugeradgang Azure Active Directory B2B?](/azure/active-directory/external-identities/what-is-b2b). Hvis du ikke har nogen gæstebrugere, skal du se [Hurtig start: Tilføj gæstebrugere til dit katalog i Azure-portalen](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Du skal være global administrator for at udføre disse trin.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Azure Active Directory Administration</a>.

2. Vælg Brugere i **navigationsruden**.

3. På **siden | Siden Alle brugere (forhåndsvisning** ) skal du **vælge Tilføj filtre**.

4. I menuen **Vælg et felt** skal du vælge **Brugertype** og derefter vælge **Anvend**.

5. I den næste menu skal du vælge **Gæst**.

6. Vælg den bruger, der skal bruge en licens, på listen over resultater.

7. Under **Administrer skal** du vælge **Licenser**.

8. Vælg **Opgaver**.

9. På siden **Opdater licenstildelinger** skal du vælge det produkt, du vil tildele en licens til.

10. I højre side skal du fjerne markeringen i afkrydsningsfelterne for de tjenester, som gæstebrugeren ikke skal have adgang til.

11. Vælg **Gem**.

## <a name="next-steps"></a>Næste trin

Hvis dine brugere endnu ikke har Office-appsene installeret, kan du dele Startvejledningen for [](../setup/employee-quick-setup.md) medarbejdere med dine brugere for at konfigurere ting, f.eks. hvordan du downloader og installerer [Microsoft 365 eller Office 2019](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) på en pc eller Mac, og hvordan du konfigurerer [Office-apps](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f) og mail på en mobilenhed.

## <a name="related-content"></a>Relateret indhold

[Forstå abonnementer og licenser](../../commerce/licenses/subscriptions-and-licenses.md) (artikel)\
[Fjern tildeling af licenser fra brugere](remove-licenses-from-users.md) (artikel)\
[Køb eller fjern licenser til dit abonnement](../../commerce/licenses/buy-licenses.md) (artikel)
