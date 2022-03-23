---
title: Tildel administratorroller Microsoft 365 Administration
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- okr_smb
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: eac4d046-1afd-4f1a-85fc-8219c79e1504
description: Lær, hvordan du tildeler administratorroller til en bruger eller flere brugere i din virksomhed, så de kan udføre bestemte opgaver i Administration.
ms.openlocfilehash: fd38bb9ed378e6b3ffc20a79ca71eb2943599dcc
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63590104"
---
# <a name="assign-admin-roles"></a>Tildel administratorroller

Hvis du er den person, der har købt dit Microsoft-virksomhedsabonnement, er du den globale administrator. Det betyder, at du har ubegrænset kontrol over produkterne i dine abonnementer, og du kan få adgang til de fleste data.

Du kan få mere at vide [under Om administratorroller](about-admin-roles.md).

Når du tilføjer nye brugere, og du ikke tildeler dem en administratorrolle, så er de i brugerrollen og har ikke administratorrettigheder til nogen af Microsofts administrationscentre. Men hvis du har brug for hjælp til at få tingene gjort, kan du tildele en administratorrolle til en bruger. Hvis du f.eks. har brug for nogen til at hjælpe med at nulstille adgangskoder, skal du ikke tildele dem den globale administratorrolle, bør du tildele dem rollen som adgangskodeadministrator. For mange globale administratorer med ubegrænset adgang til dine data og onlineforretning er en sikkerhedsrisiko.

## <a name="watch-add-an-admin"></a>Se: Tilføje en administrator

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Når du tilmelder dig Microsoft 365 Business, bliver du automatisk global administrator. Hvis du vil have hjælp til at administrere virksomheden, kan du også gøre andre til administratorer. 
1. Vælg Microsoft 365 Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Brugereaktive brugere**</a> >  i dialogboksen Indstillinger.
1. Vælg den bruger, du vil gøre til administrator, og vælg derefter **Administrer roller**.

Hvis du synes, denne video var nyttig, kan du [se den komplette kursusserie til små virksomheder og dem, der er nye Microsoft 365](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Tildel administratorroller 

Du kan tildele brugere en rolle på to forskellige måder:

- Du kan gå til brugerens oplysninger og Administrer roller **for** at tildele en rolle til brugeren.
- Eller du kan gå **til Roller** og vælge rollen og derefter føje flere brugere til den.

### <a name="assign-admin-roles-to-users-using-roles"></a>Tildel administratorroller til brugere ved hjælp af roller

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Rolletildelinger**</a>. Vælg **fanerne Azure AD** **eller Intune** for at få vist de administratorroller, der er tilgængelige for organisationen.
2. Vælg den administratorrolle, du vil tildele brugeren til.
3. Vælg **Tildelte** **administratorerAdministratorer** > .
4. Skriv brugerens viste navn **eller** **brugernavn,** og vælg derefter brugeren på listen over forslag.
5. Tilføj flere brugere, indtil du er færdig.
6. Vælg **Gem**, og brugeren føjes derefter til listen over tildelte administratorer.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Tildele en bruger en administratorrolle fra Aktive brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** > brugere [for](https://go.microsoft.com/fwlink/p/?linkid=834822) brugere.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Aktive** > brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Vælg den **bruger** , du vil ændre administratorrollen for, på siden Aktive brugere. Vælg Administrer roller under Roller **i** pop **op-ruden**.

3. Vælg den administratorrolle, du vil tildele brugeren. Hvis du ikke kan se den rolle, du leder efter, skal **du vælge Vis** alle nederst på listen.

## <a name="assign-admin-roles-to-multiple-users"></a>Tildel administratorroller til flere brugere

Hvis du kender PowerShell, kan du se [Tildel roller til brugerkonti med PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). Det er ideelt til at tildele roller til hundredvis af brugere.
  
Brug følgende fremgangsmåde til at tildele roller til ti brugere.

## <a name="check-admin-roles-in-your-organization"></a>Kontrollér administratorroller i din organisation

Du har muligvis ikke de rette tilladelser til at tildele administratorroller til andre brugere. Kontrollér, at du har de rette tilladelser, eller bed en anden administrator om at tildele roller til dig.

Du kan kontrollere administratorrolletilladelser på to forskellige måder:

- Du kan gå til brugerens oplysninger og se under **Roller** på **siden** Konto.
- Eller du kan gå til **Roller** og vælge administratorrollen og vælge tildelte administratorer for at se, hvilke brugere der er tildelt.

## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365 administratorroller](about-admin-roles.md) (artikel)\
[Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference) (artikel)\
[Tildel roller til brugerkonti med PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (artikel)\
[Godkend eller fjern partnerrelationer](../misc/add-partner.md) (artikel)