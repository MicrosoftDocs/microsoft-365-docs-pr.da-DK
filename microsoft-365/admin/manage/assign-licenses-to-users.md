---
title: Tildel licenser til brugere i Microsoft 365 Administration
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
description: Tildel licenser, afhængigt af om du vil tildele produktlicenser til bestemte brugere eller tildele brugerlicenser til et bestemt produkt.
ms.date: 07/12/2022
ms.openlocfilehash: bf315b0a13bdf0eebb2e38afa3eafb35d4a0361c
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748401"
---
# <a name="assign-microsoft-365-licenses-to-users"></a>Tildel Microsoft 365-licenser til brugere

Du kan tildele licenser til brugere på siden **Aktive brugere** eller på siden **Licenser** . Den metode, du bruger, afhænger af, om du vil tildele produktlicenser til bestemte brugere eller tildele brugerlicenser til et bestemt produkt.

> [!NOTE]
> 
> - Som administrator kan du ikke tildele eller fjerne tildeling af licenser til et selvbetjeningskøbsabonnement, der er købt af en bruger i din organisation. Du kan [overtage et selvbetjeningskøbsabonnement](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildeling af licenser.
> - For nogle abonnementer kan du kun annullere i løbet af et begrænset tidsrum, når du har købt eller fornyet dit abonnement. Hvis annulleringsvinduet er gået, skal du deaktivere tilbagevendende fakturering for at annullere abonnementet i slutningen af dets løbetid.

[Få mere at vide om, hvordan du tilføjer en bruger og tildeler en licens på samme tid](../add-users/add-users.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global administrator, licensadministrator eller brugeradministrator for at tildele licenser. Du kan få flere oplysninger under [Om administratorroller i Microsoft 365](../add-users/about-admin-roles.md).
- Du kan [tildele Microsoft 365-licenser til brugerkonti med PowerShell](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Hvis du vil bruge gruppebaserede licenser, skal du se [Tildel licenser til brugere efter gruppemedlemskab i Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Nogle tjenester, f.eks. Sway, tildeles automatisk til brugere og behøver ikke at blive tildelt individuelt.

## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Brug siden Licenser til at tildele licenser til brugere

På siden **Licenser** kan du tildele eller fjerne tildeling af licenser for op til 20 brugere ad gangen. På siden vises de produkter, du ejer, antallet af tilgængelige licenser for hvert produkt og antallet af tildelte licenser ud af det samlede antal tilgængelige licenser.

På siden **Licenser** vises et samlet antal licenser for alle abonnementer for det samme produktnavn. Du kan f.eks. have ét abonnement på Microsoft 365 Business Premium, der har fem licenser, og et andet abonnement, der har 8 licenser til det samme produkt. På siden **Licenser** kan du se, at du har i alt 13 licenser til Microsoft 365 Business Premium på tværs af alle dine abonnementer. Dette adskiller sig fra det, du ser på siden **Dine produkter** , som viser en række for hvert abonnement, du ejer, selvom de er for det samme produkt.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

2. Vælg et produkt.

3. På siden med produktoplysninger skal du vælge **Tildel licenser**.

4. I ruden **Tildel licenser til brugere** skal du begynde at skrive et navn og derefter vælge det fra resultaterne for at føje det til listen. Du kan tilføje op til 20 brugere ad gangen.

5. Vælg **Slå apps og tjenester til eller fra** for at tildele eller fjerne adgang til bestemte elementer.

6. Når du er færdig, skal du vælge **Tildel** og derefter lukke ruden til højre.

Hvis der er en konflikt, får du vist en meddelelse, der fortæller dig, hvad problemet er, og hvordan du løser det. Hvis du f.eks. har valgt licenser, der indeholder modstridende tjenester, vises der i fejlmeddelelsen, at du skal gennemse de tjenester, der er inkluderet i hver licens, og prøve igen.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Skift de apps og tjenester, som en bruger har adgang til

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

2. På siden **Licenser** skal du vælge rækken for en bestemt bruger.

3. I ruden til højre skal du vælge eller fravælge de apps og tjenester, du vil give adgang til eller fjerne adgang fra.

4. Når du er færdig, skal du vælge **Gem** og derefter vælge **Luk**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Brug siden Aktive brugere til at tildele licenser

Når du bruger siden **Aktive brugere** til at tildele licenser, tildeler du brugerlicenser til produkter.

### <a name="assign-licenses-to-multiple-users"></a>Tildel licenser til flere brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg cirklerne ud for navnene på de brugere, du vil tildele licenser til.

3. Øverst skal du vælge **Administrer produktlicenser**.

4. I ruden **Administrer produktlicenser** skal du vælge **Tildel mere: Bevar de eksisterende licenser, og tildel mere** \> **Næste**.

5. Under **Licenser** skal du markere afkrydsningsfeltet for den eller de licenser, som de valgte brugere skal have.\
    Alle tjenester, der er knyttet til disse licenser, tildeles som standard automatisk til brugerne. Du kan begrænse, hvilke tjenester der er tilgængelige for brugerne. Fjern markeringen af felterne for de tjenester, som du ikke ønsker, at brugerne skal have.

6. Vælg **Gem ændringer** nederst i ruden.  
    Du skal muligvis købe yderligere licenser, hvis du ikke har nok licenser til alle.

> [!NOTE]
> Hvis du vil tildele licenser til et stort antal brugere, skal du bruge [Tildel licenser til brugere efter gruppemedlemskab i Azure Active Directory](/azure/active-directory/enterprise-users/licensing-groups-assign)

### <a name="assign-licenses-to-one-user"></a>Tildel licenser til én bruger

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg den række for den bruger, du vil tildele en licens til.

3. Vælg **Licenser og apps** i ruden til højre.

4. Udvid afsnittet **Licenser** , markér felterne for de licenser, du vil tildele, og vælg derefter **Gem ændringer**.

## <a name="assign-a-license-to-a-guest-user"></a>Tildel en licens til en gæstebruger

Du kan invitere gæstebrugere til at samarbejde med din organisation i Azure Active Directory Administration. Hvis du vil vide mere om gæstebrugere, skal du se [Hvad er gæstebrugeradgang i Azure Active Directory B2B?](/azure/active-directory/external-identities/what-is-b2b). Hvis du ikke har nogen gæstebrugere, kan du se [Hurtig start: Føj gæstebrugere til din mappe i Azure Portal](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Du skal være global administrator for at kunne udføre disse trin.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Azure Active Directory Administration</a>.

2. Vælg **Brugere** i navigationsruden.

3. På **| Brugere På siden Alle brugere (prøveversion)** skal du vælge **Tilføj filtre**.

4. Vælg **Brugertype** i menuen **Vælg et felt**, og vælg derefter **Anvend**.

5. Vælg **Gæst** i den næste menu.

6. Vælg den bruger, der skal bruge en licens, på listen over resultater.

7. Under **Administrer** skal du vælge **Licenser**.

8. Vælg **Tildelinger**.

9. På siden **Opdater licenstildelinger** skal du vælge det produkt, du vil tildele en licens til.

10. Til højre skal du fjerne markeringen i afkrydsningsfelterne for de tjenester, som gæstebrugeren ikke skal have adgang til.

11. Vælg **Gem**.

## <a name="next-steps"></a>Næste trin

Hvis dine brugere endnu ikke har installeret Office-apps, kan du dele [vejledning til hurtig start af medarbejdere](../setup/employee-quick-setup.md) med dine brugere for at konfigurere ting, f.eks. [hvordan du downloader og installerer Microsoft 365 eller Office 2019 på en pc eller Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658)[, og hvordan du konfigurerer Office-apps og mail på en mobilenhed](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Relateret indhold

[Forstå abonnementer og licenser](../../commerce/licenses/subscriptions-and-licenses.md) (artikel)\
[Fjern tildeling af licenser fra brugere](remove-licenses-from-users.md) (artikel)\
[Køb eller fjern licenser til dit abonnement](../../commerce/licenses/buy-licenses.md) (artikel)
