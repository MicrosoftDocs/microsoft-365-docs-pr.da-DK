---
title: Gennemse administrative rettigheder for partnere
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
description: Få mere at vide om, hvordan du gennemgår listen over Microsoft-certificerede løsningsudbydere (partnere) for at bestemme, hvilke administratorrettigheder de har, og hvordan du fjerner disse rettigheder.
ms.date: 12/03/2021
ms.openlocfilehash: 067716689bd82e67dda357d675383ef2541b1dc3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593037"
---
# <a name="review-partner-administrative-privileges"></a>Gennemse administrative rettigheder for partnere

Hvis du har en Microsoft-certificeret udbyder af skyløsninger (forhandlerpartner), anbefaler vi, at du gennemfører en kvartalsvis gennemgang af de delegerede administrative rettigheder (DAP), der er tildelt dem. Sørg for, at din organisation ønsker, at denne partner skal have adgang til din organisations data og foretage køb på dine vegne.

> [!IMPORTANT]
> At give DAP, som omfatter globale administratortilladelser, til enhver partner, kan udgør en sikkerhedsrisiko. Det er også en sikkerhedsrisiko at have for mange globale administratorer. [Få mere at vide om den seneste aktivitet, der målretter delegerede rettigheder](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Når du har accepteret en DAP-aftale fra en forhandlerpartner, kan de tildele organisationens globale administratorrolle til deres medarbejdere. Den globale administratorrolle giver partnerens medarbejdere adgang til dine medarbejderes personlige data og andre følsomme oplysninger. Det giver dem også tilladelse til at udføre handlinger for hele lejeren, f.eks. følgende handlinger:

- Ændring af brugeradgangskoder
- Tilføje brugere med mailkonti
- Tilføje og administrere webdomæner, der er knyttet til organisationen

Når DAP er aktiveret, har du ingen kontrol over antallet af globale administratorer, som din partner kan tilføje. Du kan kun tildele eller afvise partneren DAP (global administrator) adgang til din konto.

## <a name="review-and-remove-roles-from-partners"></a>Gennemse og fjern roller fra partnere

1. I Microsoft 365 Administration skal du gå til **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner-relationer</a>. Partnere med DAP **har angivet Global administrator** i **kolonnen** Roller.
2. Hvis du vil fjerne rollen Global administrator fra en partner, skal du finde navnet på den partner, du vil fjerne.
3. Markér den række, **der indeholder** Forhandler **som Relationstype**.
4. På siden partneroplysninger skal du vælge **Fjern roller** og derefter vælge **Ja**.

> [!NOTE]
>
> - Hvis du fjerner DAP (global administratorrolle) fra en partner, anbefaler vi, at du kontakter denne for at diskutere fremtidig levering af tjenester. Du kan f.eks. oprette en brugerkonto med lavere rettigheder og dele disse kontooplysninger med din partner. Få mere at vide [om at tilføje](../admin/add-users/add-users.md) brugere [og tildele administratorroller](../admin/add-users/assign-admin-roles.md).
> - Selv når rollen Global administrator er fjernet, kan partneren stadig foretage køb på dine vegne. Vi anbefaler, at du kontakter partneren for at bede vedkommende om at fjerne denne mulighed i Partnercenter.

## <a name="related-content"></a>Relateret indhold

[Administrer partnerrelationer](manage-partners.md) (artikel)\
[Om administratorroller](../admin/add-users/about-admin-roles.md) (artikel)\
[Delegerede administratorrettigheder i Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (artikel)
