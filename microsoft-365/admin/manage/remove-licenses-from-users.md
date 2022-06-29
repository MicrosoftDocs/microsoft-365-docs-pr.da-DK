---
title: Fjern licenser fra brugere
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_smb
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Den metode, du bruger til at fjerne tildelingen af produktlicenser, afhænger af, om du fjerner tildelingen af licenser fra bestemte brugere eller fra et bestemt produkt.
ms.date: 06/23/2022
ms.openlocfilehash: 87e62b8c39e5ba0a8f61caeea3560438a716881d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486170"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>Fjern tildeling af Microsoft 365-licenser fra brugere

Du kan fjerne tildelingen af licenser fra brugere på siden **Aktive brugere** eller på siden **Licenser** . Den metode, du bruger, afhænger af, om du vil fjerne tildelingen af produktlicenser fra bestemte brugere eller fjerne tildelingen af brugerlicenser fra et bestemt produkt.

> [!NOTE]
> 
> - Som administrator kan du ikke tildele eller fjerne tildeling af licenser til et selvbetjeningskøbsabonnement, der er købt af en bruger i din organisation. Du kan [overtage et selvbetjeningskøbsabonnement](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildeling af licenser.
> 
> - For nogle abonnementer kan du kun annullere i løbet af et begrænset tidsrum, når du har købt eller fornyet dit abonnement. Hvis annulleringsvinduet er gået, skal du deaktivere tilbagevendende fakturering for at annullere abonnementet i slutningen af dets løbetid.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global administrator, licensadministrator og brugeradministrator for at fjerne tildelingen af licenser. Du kan få flere oplysninger under [Om administratorroller i Microsoft 365](../add-users/about-admin-roles.md).
- Du kan [fjerne licenser fra brugerkonti med Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Du kan også [slette brugerkonti](../add-users/delete-a-user.md) , der er tildelt en licens, for at gøre deres licens tilgængelig for andre brugere. Når du sletter en brugerkonto, er vedkommendes licens straks tilgængelig til at tildele til en anden.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Brug siden Licenser til at fjerne tildelingen af licenser

På siden **Licenser** kan du tildele eller fjerne tildeling af licenser for op til 20 brugere ad gangen. På siden vises de produkter, du ejer, antallet af tilgængelige licenser for hvert produkt og antallet af tildelte licenser ud af det samlede antal tilgængelige licenser. Antallet af licenser er et samlet antal licenser for alle abonnementer for det samme produktnavn.

Du kan f.eks. have ét abonnement på Microsoft 365 Business Premium, der har fem licenser, og et andet abonnement, der har 8 licenser til det samme produkt. På siden **Licenser** kan du se, at du har i alt 13 licenser til Microsoft 365 Business Premium på tværs af alle dine abonnementer. Dette adskiller sig fra det, du ser på siden **Dine produkter** , som viser en række for hvert abonnement, du ejer, selvom de er for det samme produkt.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Faktureringslicenser</a>  \>.

::: moniker-end

1. Vælg et produkt.

2. Markér afkrydsningsfelterne for de brugere, du vil fjerne tildelingen af licenser til.

3. Vælg **Fjern tildeling af licenser**.

4. I feltet **Fjern tildeling af licenser** skal du vælge **Fjern tildeling**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Brug siden Aktive brugere til at fjerne tildelingen af licenser

Når du bruger siden **Aktive brugere** til at fjerne tildelingen af licenser, fjerner du tildelingen af produktlicenser fra brugere.

### <a name="unassign-licenses-from-one-user"></a>Fjern tildeling af licenser fra én bruger

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg den række for den bruger, du vil fjerne tildelingen af en licens for.

3. Vælg **Licenser og apps** i ruden til højre.

4. Udvid afsnittet **Licenser** , fjern markeringen i felterne for de licenser, du vil fjerne tildelingen af, og vælg derefter **Gem ændringer**.

### <a name="unassign-licenses-from-multiple-users"></a>Fjern tildeling af licenser fra flere brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Vælg cirklerne ud for navnene på de brugere, du vil fjerne tildelingen af licenser for.

3. Øverst skal du vælge **Administrer produktlicenser**.

4. I ruden **Administrer produktlicenser** skal du vælge **Fjern tildeling af alle** > **gem ændringer**.

5. Vælg **Udført** nederst i ruden.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Hvad sker der med en brugers data, når du fjerner brugerens licens?

- Når en licens fjernes fra en bruger, opbevares Exchange Online data, der er knyttet til den pågældende konto, i 30 dage. Efter den 30-dages respitperiode slettes dataene og kan ikke gendannes. Den er dog knyttet til opbevaringspolitikken, og det indhold, der svarer til opbevaringsmærkater, bevares til registrering.
- Filer, der er gemt i OneDrive for Business, slettes ikke, medmindre brugeren slettes fra Microsoft 365 Administration eller fjernes via Active Directory-synkronisering. Du kan få flere oplysninger under [Opbevaring og sletning af OneDrive](/onedrive/retention-and-deletion).
- Når licensen fjernes, kan der ikke længere søges i brugerens postkasse ved hjælp af et eDiscovery-værktøj, f.eks. indholdssøgning eller eDiscovery (Premium). Du kan finde flere oplysninger under "Søgning i fjernede postkasser eller postkasser med ikke-licenseret" i [Indholdssøgning i Microsoft 365](../../compliance/content-search.md).
- Hvis du har et Enterprise-abonnement, f.eks. Office 365 Enterprise E3, kan du Exchange Online bevare postkassedataene for en slettet brugerkonto ved hjælp af [inaktive postkasser](../../compliance/inactive-mailboxes-in-office-365.md). Du kan få flere oplysninger under [Opret og administrer inaktive postkasser i Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Hvis du vil vide mere om, hvordan du blokerer en brugers adgang til Microsoft 365-data, når vedkommendes licens er fjernet, og hvordan du får adgang til dataene bagefter, skal du se [Fjern en tidligere medarbejder](../add-users/remove-former-employee.md).
- Hvis du fjerner en brugers licens, og brugeren stadig har Office-apps installeret, får vedkommende vist [fejl i Produkt uden licens og aktivering i Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) , når brugeren bruger Office-apps.

## <a name="next-steps"></a>Næste trin

Hvis du ikke vil [overdrage ubrugte licenser til andre brugere](../../managed-desktop/get-started/assign-licenses.md), kan du overveje at [fjerne licenserne fra dit abonnement](../../commerce/licenses/buy-licenses.md) , så du ikke betaler for flere licenser, end du har brug for.

## <a name="related-content"></a>Relateret indhold

[Fjern licenser fra dit abonnement](../../commerce/licenses/buy-licenses.md) (artikel)\
[Tildel licenser til brugere](assign-licenses-to-users.md) (artikel)\
[Forstå abonnementer og licenser i Microsoft 365 til virksomheder](../../commerce/licenses/subscriptions-and-licenses.md) (artikel)
