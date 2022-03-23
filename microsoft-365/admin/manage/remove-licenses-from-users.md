---
title: Fjern tildeling af licenser fra brugere
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
description: Den metode, du bruger til at fjerne tildeling af produktlicenser, afhænger af, om du har fjernet tildelingen af licenser fra bestemte brugere eller fra et bestemt produkt.
ms.date: 09/16/2021
ms.openlocfilehash: 7308888c54a30cdd11618cb07a233f8bd55f27c2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588526"
---
# <a name="unassign-licenses-from-users"></a>Fjern tildeling af licenser fra brugere

Du kan fjerne tildeling af licenser fra brugere på **enten siden** Aktive brugere eller på **siden** Licenser. Den metode, du bruger, afhænger af, om du vil fjerne tildelingen af produktlicenser fra bestemte brugere eller fjerne tildeling af brugerlicenser fra et bestemt produkt.

> [!NOTE]
> 
> - Som administrator kan du ikke tildele eller fjerne tildeling af licenser for et selvbetjeningskøbsabonnement, der er købt af en bruger i organisationen. Du kan [overtage et abonnement på et selvbetjeningskøb](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) og derefter tildele eller fjerne tildelingen af licenser.
> 
> - For nogle abonnementer kan du kun opsige i en begrænset periode, efter du har købt eller fornyet dit abonnement. Hvis annulleringsvinduet er udløbet, skal du slå tilbagevendende fakturering fra for at annullere abonnementet i slutningen af abonnementsperioden.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global, licens, brugeradministrator for at fjerne tildeling af licenser. Få mere at vide under [Om Microsoft 365 administratorroller](../add-users/about-admin-roles.md).
- Du kan [fjerne licenser fra brugerkonti med Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Du kan også [slette brugerkonti,](../add-users/delete-a-user.md) der er blevet tildelt en licens, for at gøre deres licenser tilgængelige for andre brugere. Når du sletter en brugerkonto, kan brugerens licens straks tildeles en anden.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Brug siden Licenser til at fjerne tildeling af licenser

Når du bruger siden **Licenser** til at fjerne tildeling af licenser, skal du fjerne tildelingen af licenser til et bestemt produkt for op til 20 brugere.

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Faktureringslicenser**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Vælg det produkt, du vil fjerne tildelingen af licenser for.

3. Vælg de brugere, du vil fjerne tildelingen af licenser for.

4. Vælg **Fjern tildeling af licenser**.

5. I feltet **Fjern tildeling af licenser** skal du vælge **Fjern.**

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Brug siden Aktive brugere til at fjerne tildeling af licenser

Når du bruger siden **Aktive brugere** til at fjerne tildeling af licenser, skal du fjerne tildelingen af produktlicenser fra brugerne.

### <a name="unassign-licenses-from-one-user"></a>Fjern tildeling af licenser fra én bruger

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Markér rækken for den bruger, du vil fjerne tildelingen af en licens for.

3. I højre rude skal du vælge **Licenser og apps**.

4. Udvid **sektionen** Licenser, fjern markeringen i afkrydsningsfelterne for de licenser, du vil fjerne, og vælg derefter **Gem ændringer**.

### <a name="unassign-licenses-from-multiple-users"></a>Fjern tildeling af licenser fra flere brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Markér cirklerne ud for navnene på de brugere, du vil fjerne tildeling af licenser for.

3. Øverst skal du vælge **Administrer produktlicenser**.

4. I **ruden Administrer produktlicenser** skal du **vælge Fjern alle Lagringsændringer** > .

5. Vælg Udført nederst i **ruden**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Hvad sker der med en brugers data, når du fjerner brugerens licens?

- Når en licens fjernes fra en bruger, Exchange data, der er knyttet til den pågældende konto, i 30 dage. Efter de 30 dage slettes dataene og kan ikke gendannes.
- Filer, der OneDrive for Business filer, slettes ikke, medmindre brugeren slettes fra mappen Microsoft 365 Administration eller fjernes via Active Directory-synkronisering. Du kan finde flere oplysninger [OneDrive opbevaring og sletning](/onedrive/retention-and-deletion).
- Når licensen fjernes, er brugerens postkasse ikke længere søgbar ved hjælp af et eDiscovery-værktøj, f.eks. indholdssøgning eller Advanced eDiscovery. Du kan finde flere oplysninger under "Søgning i frakoblede eller ikke-licenserede postkasser" i [Indholdssøgning i Microsoft 365](../../compliance/content-search.md).
- Hvis du har et Enterprise-abonnement, f.eks. Office 365 Enterprise E3, kan Exchange Online bevare postkassedata fra en slettet brugerkonto ved hjælp af [inaktive postkasser](../../compliance/inactive-mailboxes-in-office-365.md). Få mere at vide under [Opret og administrer inaktive postkasser i Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Du kan få mere at vide om, hvordan du blokerer en brugers adgang til Microsoft 365-data, når licensen er fjernet, og hvordan du efterfølgende får adgang til dataene, under Fjern [en tidligere medarbejder](../add-users/remove-former-employee.md).
- Hvis du fjerner en brugers licens, og denne stadig har Office-apps installeret, får de vist Fejlmeddelelser om produkt uden licens og aktivering [i Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380), når de bruger Office apps.

## <a name="next-steps"></a>Næste trin

Hvis du ikke vil tildele ubrugte licenser til andre [brugere, bør](../../managed-desktop/get-started/assign-licenses.md) du overveje at fjerne licenserne fra dit abonnement, så du ikke betaler for flere licenser, end du har brug for.[](../../commerce/licenses/buy-licenses.md)

## <a name="related-content"></a>Relateret indhold

[Fjern licenser fra dit abonnement](../../commerce/licenses/buy-licenses.md) (artikel)\
[Tildel licenser til brugere](assign-licenses-to-users.md) (artikel)\
[Forstå abonnementer og licenser i Microsoft 365 for business](../../commerce/licenses/subscriptions-and-licenses.md) (artikel)
