---
title: Administrer tilmeldingsabonnementer via selvbetjening
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
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
description: Få mere at vide om, hvordan du administrerer gratis tilmeldingsabonnementer via selvbetjening for din organisation.
ms.date: 03/17/2021
ms.openlocfilehash: 58c58c849b72c170e0ccf10de54389bd1245bced
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102344"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Administrer tilmeldingsabonnementer via selvbetjening

## <a name="what-are-self-service-sign-up-subscriptions"></a>Hvad er abonnementer på tilmelding via selvbetjening?

Der er et begrænset antal gratis tilmeldingsabonnementer til selvbetjening, som brugerne i din organisation kan tilmelde sig. En bruger kan kun tilmelde sig og selv bruge et tilmeldingsabonnement via selvbetjening. Du administrerer tilmeldingsabonnementer via selvbetjening ved at blokere brugere fra at tilmelde sig og ved at slette gratis abonnementer, som brugerne har tilmeldt sig. Du kan få flere oplysninger om tilmelding via selvbetjening og de tilgængelige abonnementer under [Brug af tilmelding via selvbetjening i din organisation](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Få vist en liste over tilmeldingsabonnementer via selvbetjening

1. I Administration skal du gå til siden **Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.
2. På fanen **Produkter** skal du vælge filterikonet og derefter vælge **Gratis**. Der vises en liste over alle tilmeldingsabonnementer via selvbetjening.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Hvordan adskiller disse abonnementer sig fra abonnementer på køb via selvbetjening?

Tilmeldingsabonnementer via selvbetjening er gratis og er tilgængelige for en større liste over produkter end abonnementer på køb via selvbetjening. Når en bruger tilmelder sig et selvbetjeningskøbsabonnement, er vedkommende ansvarlig for at betale for det. Abonnementer på køb via selvbetjening er kun tilgængelige for Power Platform-produkter (Power BI, Power Apps og Power Automate), Project og Visio. Du kan få flere oplysninger under [Ofte stillede spørgsmål om køb via selvbetjening](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Bloker brugere, så de ikke kan tilmelde sig

Du kan bruge [**Cmdlet'en Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) med parameteren **AllowAdHocSubscriptions** til at styre, om brugerne kan tilmelde sig selvbetjeningstilmeldingsabonnementer. Du kan få flere oplysninger under [Hvordan gør jeg styre indstillinger for selvbetjening?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Slet et tilmeldingsabonnement via selvbetjening

> [!IMPORTANT]
> Når du sletter et tilmeldingsabonnement via selvbetjening, blokerer du alle brugere fra at få adgang til deres data og mail og sletter alle data og mails.

1. I Administration skal du gå til siden **Fakturering** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Dine produkter</a>.
2. På fanen **Produkter** skal du vælge filterikonet og derefter vælge **Gratis**.
3. Vælg det tilmeldingsabonnement på selvbetjening, du vil slette. 
4. På siden med abonnementsoplysninger skal du i afsnittet **Abonnementer og betalingsindstillinger** vælge **Slet abonnement**.
5. I ruden **Slet abonnement** skal du markere afkrydsningsfeltet og derefter vælge **Slet abonnement**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Jeg har et tilmeldingsabonnement via selvbetjening, der blokerer for sletning af mapper

De selvbetjente tilmeldingsprodukter, som individuelle brugere kan tilmelde sig, opretter også en gæstebruger til godkendelse i din Azure AD mappe. For at undgå tab af data blokerer disse selvbetjente produkter katalogsletninger, indtil de slettes fuldstændigt fra mappen. De kan kun slettes af Azure AD-administratoren. Du kan få flere oplysninger under [Slet en mappe i Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
