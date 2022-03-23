---
title: Luk din konto
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
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: Når du lukker din konto med Microsoft, slettes alle oplysninger, der er relateret til din konto, herunder licenser, brugere og brugerdata.
ms.date: 04/02/2021
ms.openlocfilehash: b1ac828d047d2c2b9f39185a66ccc77976b8324b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587957"
---
# <a name="close-your-account"></a>Luk din konto

Når du lukker din konto hos Microsoft, slettes all oplysninger, der er relateret til din konto. Disse oplysninger omfatter abonnementer, licenser, betalingsmetoder, brugere og brugerdata.

## <a name="before-you-begin"></a>Før du begynder

Før du starter denne proces, skal du sørge for at sikkerhedskopiere alle data, du ønsker at bevare.

Du skal være global administrator eller faktureringsadministrator for at udføre opgaverne i denne artikel. Du kan få mere at vide [under Om administratorroller](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Trin 1: Slet brugere

Slet alle brugere med undtagelse af én global administrator. Den globale administrator fuldfører trinnene for at lukke kontoen. Før du kan slette mappen i slutningen af denne proces, skal du slette alle andre brugere.

Hvis brugere synkroniseres fra det lokale miljø, skal du først deaktivere synkronisering og derefter slette brugerne i mappen i skyen ved hjælp af Azure-portalen eller Azure PowerShell-cmdlet'er.

Hvis du vil slette brugere, [skal du se Administrator for brugerstyring: Slet en eller flere brugere](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Du kan også bruge [PowerShell-cmdlet'en Remove-MsolUser](/powershell/module/msonline/remove-msoluser) til at slette flere brugere en masse.

Hvis din organisation bruger Active Directory, der synkroniseres med Microsoft Azure Active Directory (Azure AD), skal du i stedet slette brugerkontoen fra Active Directory. Du kan finde en vejledning [under Masseslet brugere Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>Trin 2: Annuller alle aktive abonnementer

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. Find **et aktivt** abonnement på fanen Produkter. Vælg de tre d'er (flere handlinger), og vælg derefter **Annuller abonnement**.
3. I **ruden Annuller** abonnement skal du vælge en årsag til, hvorfor du annullerer. Du kan også give feedback.
4. Vælg **Gem**.
5. Gentag trin 1 til 4 for at annullere alle aktive abonnementer.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Trin 3: Slet alle deaktiverede abonnementer

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">BillingYour</a> >  products.
2. Vælg et **deaktiveret** abonnement på fanen Produkter.
3. På siden med abonnementsoplysninger skal du **i sektionen Abonnements- og betalingsindstillinger** vælge **Slet abonnement**.
4. I **ruden Slet abonnement** skal du vælge **Slet abonnement**.
5. I dialogboksen **Slet abonnement** skal du vælge **Ja**.
6. Gentag trin 3 til 5 for hvert deaktiveret abonnement, indtil alle abonnementer er slettet.

> [!NOTE]
> Hvis du ikke kan slette et deaktiveret abonnement med det samme, skal du [kontakte support](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>Trin 4: Deaktiver Multi-Factor Authentication

1. Log på Administration med en Global administratorkonto. Se Kontrollér administratorroller i organisationen for at [bekræfte, hvilke roller du har](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. Gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">BrugereAktivér</a> >  brugere.
3. Vælg **Multi-Factor Authentication**.
4. På siden multifaktorgodkendelse skal du deaktivere alle konti med undtagelse af den globale administratorkonto, du bruger i øjeblikket.

Du kan også [bruge PowerShell til at deaktivere multifaktorgodkendelse for flere brugere](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Trin 5: Slet mappen i Azure Active Directory

1. Log på <a href="https://aad.portal.azure.com/" target="_blank">Azure AD Administration med</a> en global administratorkonto.
2. Vælg **Azure Active Directory**.
3. Skift til den organisation, du vil slette.
4. Vælg **Slet lejer**.
5. Hvis din organisation mislykkes med en eller flere kontroller, får du vist et link til flere oplysninger om, hvordan du passerer kontrollerne. Når du har bestået alle kontroller, skal **du vælge** Slet for at fuldføre processen.

Når du har fuldført dette sidste trin, lukkes og slettes din konto med Microsoft.

## <a name="related-content"></a>Relateret indhold 

[Forstå din regning eller faktura for Microsoft 365 for business](./billing-and-payments/understand-your-invoice2.md) (artikel)\
[Annuller dit abonnement](./subscriptions/cancel-your-subscription.md) (artikel)

