---
title: Fastgør apps til dine brugeres appstarter
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
- Adm_TOC
ms.service: o365-administration
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
description: Som global administrator kan du fastgøre op til tre apps til dine brugeres appstarter.
ms.openlocfilehash: 7ff85e379198312666f03c2d7d6c8bb42b9e08d0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590627"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Fastgør apps til dine brugeres appstarter

Du kan bruge kontrolelementer i Azure Active Directory-portalen til at fastgøre op til tre apps til Office.com og appstarteren for alle brugerne i organisationen. Du kan også organisere grupper af programmer. En hvilken som helst app, du tilføjer senere, kan når som helst frigøres af brugeren. Hvis du vil fastgøre en app til dine brugere, skal du være administrator for skyprogrammet eller programadministratoren i Azure Active Directory eller global administrator i Office 365. Du kan finde flere oplysninger om [administratorroller i indbyggede roller og administratorroller i Azure AD](/azure/active-directory/roles/permissions-reference) [Microsoft 365](../add-users/about-admin-roles.md). 

Du kan finde flere oplysninger om appstarteren og Office.com i artiklen [om appstarteren](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) og opdateringer til [office.com og blogartikel Office 365-appstarteren](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503).

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Brug Azure Active Directory til at fastgøre apps

1. Gå til Microsoft 365 Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.
2. I venstre navigationslinje skal **du vælge Vis** alle, og under **Administrationer** skal **du Azure Active Directory**.
3. I **Azure Active Directory** du vælge **Enterprise-programmerBrugerindstillinger** > .
4. I sektionen **Office 365 Indstillinger** skal du vælge **Tilføj program**.
5. Vælg de programmer, du vil fastgøre til brugernes appstarter, og vælg derefter **Tilføj**.

:::image type="content" source="../../media/add-apps.png" alt-text="Microsoft 365 til at fastgøre apps.":::

### <a name="pin-a-custom-app"></a>Fastgør en brugerdefineret app

> [!NOTE]
> Brugergrænsefladen angiver, om du skal købe flere Azure AD-licenser for at bruge denne funktion. Du kan finde flere oplysninger [Azure Active Directory priser](https://azure.microsoft.com/pricing/details/active-directory/).

1. I **Azure Active Directory** du **vælge** **Enterprise-programmerNew** >  program øverst på **siden Alle** programmer.
2. På siden **Tilføj et program skal** du vælge programmet **Ikke-galleri** eller **Opret** dit eget program, hvis du er i eksempelversionen af Azure Active Directory. 
3. Skriv et navn til programmet, og tildel derefter brugeren **under fanen Brugere og** grupper.
4. Brug fanen **Egenskaber** til at overføre et ikon for appen.
5. Hvis du vil tildele en URL-adresse til appen, skal du **vælge Sammenkædet** under fanen Enkelt **logon og derefter** angive en URL-adresse.
6. Vælg **Gem**.

## <a name="create-application-collections"></a>Opret programsamlinger

Du kan også oprette programsamlinger for brugerne i organisationen. Du kan finde en [vejledning under Oprette samlinger på portalen Mine apps i Azure-portalen](/azure/active-directory/manage-apps/access-panel-collections).