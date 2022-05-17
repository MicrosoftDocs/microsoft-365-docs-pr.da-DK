---
title: Tildel Microsoft 365 Administration administratorroller
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
description: Få mere at vide om, hvordan du tildeler administratorroller til en bruger eller flere brugere i din virksomhed, så de kan udføre bestemte opgaver i Administration.
ms.openlocfilehash: 663a5fb60fa815eab079f4ab96e53e8b168105b7
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437014"
---
# <a name="assign-admin-roles-in-the-microsoft-365-admin-center"></a>Tildel administratorroller i Microsoft 365 Administration

Hvis du er den person, der har købt dit Microsoft-virksomhedsabonnement, er du global administrator. Det betyder, at du har ubegrænset kontrol over produkterne i dine abonnementer, og at du har adgang til de fleste data.

Du kan få mere at vide under [Om administratorroller](about-admin-roles.md).

Når du tilføjer nye brugere, og du ikke tildeler dem en administratorrolle, har de *brugerrollen* og har ikke administratorrettigheder til nogen af Microsoft-administratorcentrene. Men hvis du har brug for hjælp til at få tingene fra hånden, kan du tildele en administratorrolle til en bruger. Hvis du f.eks. har brug for en person til at nulstille adgangskoder, skal du ikke tildele vedkommende rollen global administrator, du skal tildele vedkommende rollen som adgangskodeadministrator. Det er en sikkerhedsrisiko at have for mange globale administratorer med ubegrænset adgang til dine data og onlineforretning.

## <a name="watch-add-an-admin"></a>Se: Tilføj en administrator

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Når du tilmelder dig Microsoft 365 Business, bliver du automatisk global administrator. Som en hjælp til at administrere virksomheden kan du også gøre andre personer til administratorer. 
1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktive**</a> >  brugere i Microsoft 365 Administration.
1. Vælg den bruger, du vil gøre til administrator, og vælg derefter **Administrer roller**.

Hvis du har fundet denne video nyttig, kan du se hele [træningsserien for små virksomheder og dem, der ikke er Microsoft 365](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Tildel administratorroller 

Du kan tildele brugere til en rolle på to forskellige måder:

- Du kan gå til brugerens oplysninger og **Administrer roller** for at tildele en rolle til brugeren.
- Du kan også gå til **Roller** og vælge rollen og derefter føje flere brugere til den.

### <a name="assign-admin-roles-to-users-using-roles"></a>Tildel administratorroller til brugere ved hjælp af roller

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Rolletildelinger**</a>. Vælg fanerne **Azure AD** eller **Intune** for at få vist de administratorroller, der er tilgængelige for din organisation.
2. Vælg den administratorrolle, du vil tildele brugeren til.
3. Vælg **Tildelt** **administratorerTilføj** > .
4. Skriv brugerens **viste navn** eller **brugernavn**, og vælg derefter brugeren på listen over forslag.
5. Tilføj flere brugere, indtil du er færdig.
6. Vælg **Gem**, hvorefter brugeren føjes til listen over tildelte administratorer.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Tildel en bruger til en administratorrolle fra Aktive brugere

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** > [Aktive brugere](https://go.microsoft.com/fwlink/p/?linkid=834822) .

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. På siden **Aktive brugere** skal du vælge den bruger, hvis administratorrolle du vil ændre. Vælg **Administrer roller** under **Roller** i pop op-ruden.

3. Vælg den administratorrolle, du vil tildele brugeren. Hvis du ikke kan se den rolle, du leder efter, skal du vælge **Vis alle** nederst på listen.

## <a name="assign-admin-roles-to-multiple-users"></a>Tildel administratorroller til flere brugere

Hvis du kender PowerShell, skal du se [Tildel roller til brugerkonti med PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). Det er ideelt til at tildele roller til hundredvis af brugere.
  
Brug følgende instruktioner til at tildele roller til mange brugere.

## <a name="check-admin-roles-in-your-organization"></a>Kontrollér administratorroller i din organisation

Du har muligvis ikke de korrekte tilladelser til at tildele administratorroller til andre brugere. Kontrollér, at du har de korrekte tilladelser, eller bed en anden administrator om at tildele roller til dig.

Du kan kontrollere administratorrolletilladelser på to forskellige måder:

- Du kan gå til brugerens oplysninger og se **under Roller** på siden **Konto** .
- Du kan også gå til **Roller** og vælge administratorrollen og vælge Tildelte administratorer for at se, hvilke brugere der er tildelt.

## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365 administratorroller](about-admin-roles.md) (artikel)\
[Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference) (artikel)\
[Tildel roller til brugerkonti med PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (artikel)\
[Godkend eller fjern partnerrelationer](../misc/add-partner.md) (artikel)