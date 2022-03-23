---
title: Administrer selvbetjeningsabonnementer til tilmelding
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
description: Få mere at vide om, hvordan du administrerer gratis abonnementer på selvbetjening for tilmelding for organisationen.
ms.date: 03/17/2021
ms.openlocfilehash: be93a09ca63a4ee24945438be59b725e7d41911c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588198"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Administrer selvbetjeningsabonnementer til tilmelding

## <a name="what-are-self-service-sign-up-subscriptions"></a>Hvad er selvbetjeningsabonnementer til tilmelding?

Brugere i organisationen kan tilmelde sig et begrænset antal gratis abonnementer på selvbetjening. En bruger kan kun tilmelde sig og bruge et selvoptegnelsesabonnement til sig selv. Du administrerer selvbetjeningsabonnementer ved at blokere brugere fra at tilmelde sig og ved at slette gratis abonnementer, som brugerne har tilmeldt sig. Du kan finde flere oplysninger om tilmelding via selvbetjening og de tilgængelige abonnementer i Brug [af selvbetjeningsabonnement i din organisation](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Få vist en liste over selvbetjeningsabonnementer til tilmelding

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. På fanen **Produkter** skal du vælge filterikonet og derefter vælge **Gratis**. Der vises en liste over alle abonnementer på selvbetjeningsabonnementer.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>Hvordan er disse abonnementer forskellige fra selvbetjeningskøbsabonnementer?

Selvbetjeningsabonnementer til tilmelding er gratis og er tilgængelige for en større liste over produkter end abonnementer på selvbetjeningskøb. Når en bruger tilmelder sig et abonnement på et selvbetjeningskøb, er brugeren ansvarlig for at betale for det. Abonnementer på selvbetjeningskøb er kun tilgængelige for Power Platform-produkter (Power BI, Power Apps og Power Automate), Project og Visio. Få mere at vide under Ofte [stillede spørgsmål om selvbetjeningskøb](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Bloker brugere i at tilmelde sig

Du kan bruge cmdlet'en [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) med **parameteren AllowAdHocSubscriptions** til at styre, om brugerne kan tilmelde sig selvbetjeningsabonnementer til tilmelding. Du kan finde flere oplysninger [under Hvordan styrer jeg selvbetjeningsindstillinger?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Slette et selvbetjeningsabonnement til tilmelding

> [!IMPORTANT]
> Når du sletter et selvbetjeningsabonnement, blokerer du alle brugere fra at få adgang til deres data og mail og slette alle data og mail.

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. På fanen **Produkter** skal du vælge filterikonet og derefter vælge **Gratis**.
3. Vælg det selvbetjeningsabonnement, du vil slette. 
4. På siden med abonnementsoplysninger i sektionen **Abonnementer og betalingsindstillinger** skal du vælge **Slet abonnement**.
5. I **ruden Slet abonnement** skal du markere afkrydsningsfeltet og derefter vælge **Slet abonnement**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>Jeg har et selvbetjeningsabonnement, der blokerer katalogsletning

De tilmeldingsprodukter til selvbetjening, som individuelle brugere kan tilmelde sig, kan også oprette en gæstebruger til godkendelse i dit Azure AD-katalog. For at undgå datatab blokerer disse selvbetjeningsprodukter katalogsletninger, indtil de slettes fuldstændigt fra kataloget. De kan kun slettes af Azure AD-administratoren. Du kan få mere at vide [under Slet en mappe Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
