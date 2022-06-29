---
title: Gennemse partneradministrationsrettigheder
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
search.appverid: MET150
description: Få mere at vide om, hvordan du gennemser din liste over Microsoft-certificerede løsningsudbydere (partnere) for at bestemme, hvilke administratorrettigheder de har, og hvordan du fjerner disse rettigheder.
ms.date: 12/03/2021
ms.openlocfilehash: eefbe2c8b70afee9c1e24e4335a73488906bf844
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490691"
---
# <a name="review-microsoft-certified-cloud-solution-provider-partner-administrative-privileges"></a>Gennemse administratorrettigheder til Microsoft-certificeret cloudløsningsudbyder

Hvis du har en Microsoft-certificeret cloudløsningsudbyder (forhandlerpartner), anbefaler vi, at du foretager en kvartalsvis gennemgang af de delegerede administrative rettigheder (DAP), der er tildelt dem. Sørg for, at din organisation ønsker, at denne partner skal have adgang til organisationens data og foretage køb på dine vegne.

> [!IMPORTANT]
> Hvis du giver DAP, som omfatter globale administratortilladelser, til en hvilken som helst partner, kan det udgøre en sikkerhedsrisiko. Det er også en sikkerhedsrisiko at have for mange globale administratorer. [Få mere at vide om seneste aktivitet, der er målrettet til delegerede rettigheder](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Når du har accepteret en DAP-aftale fra en forhandlerpartner, kan de tildele rollen Global administrator for din organisation til deres medarbejdere. Rollen Global administrator giver partnerens medarbejdere adgang til dine medarbejderes personlige data og andre følsomme oplysninger. Den giver dem også tilladelse til at udføre handlinger for hele lejeren, f.eks. følgende handlinger:

- Ændring af brugeradgangskoder
- Tilføjelse af brugere med mailkonti
- Tilføjelse og administration af webdomæner, der er knyttet til din organisation

Når DAP er aktiveret, har du ingen kontrol over antallet af globale administratorer, som din partner kan tilføje. Du kan kun give eller nægte partneren DAP (Global administrator) adgang til din konto.

## <a name="review-and-remove-roles-from-partners"></a>Gennemse og fjern roller fra partnere

1. I Microsoft 365 Administration skal du gå til siden **Indstillinger partnerrelationer** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank"></a> Partnere med DAP har **global administrator** angivet i kolonnen **Roller** .
2. Hvis du vil fjerne rollen Global administrator fra en partner, skal du finde navnet på den partner, du vil fjerne.
3. Vælg den række, hvor **Reseller** er **relationstypen**.
4. På siden med partneroplysninger skal du vælge **Fjern roller** og derefter vælge **Ja**.

> [!NOTE]
>
> - Hvis du fjerner DAP (Global administratorrolle) fra en partner, anbefaler vi, at du kontakter dem for at diskutere fremtidig levering af tjenester. Du kan f.eks. oprette en brugerkonto med lavere rettigheder og dele disse kontooplysninger med din partner. Få mere at vide om [tilføjelse af brugere](../admin/add-users/add-users.md) og [tildeling af administratorroller](../admin/add-users/assign-admin-roles.md).
> - Selvom rollen Global administrator er fjernet, kan partneren stadig foretage køb på dine vegne. Vi anbefaler, at du kontakter partneren for at bede vedkommende om at fjerne denne mulighed i Partnercenter.

## <a name="related-content"></a>Relateret indhold

[Administrer partnerrelationer](manage-partners.md) (artikel)\
[Om administratorroller](../admin/add-users/about-admin-roles.md) (artikel)\
[Delegerede administratorrettigheder i Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (artikel)
