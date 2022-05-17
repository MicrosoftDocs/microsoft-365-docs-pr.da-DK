---
title: Opret, rediger eller slet en brugerdefineret brugervisning
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 4fe7f6ac-be8e-4b57-9e13-24ff889a4b28
description: Hvis du er global administrator eller brugeradministrationsadministrator af et Microsoft 365 til virksomhedsabonnement, kan du bruge filtre til at oprette, redigere eller slette brugerdefineret brugervisning.
ms.openlocfilehash: d90d324690d153fa708dbe7c36a9f41d349f8588
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436729"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Opret, rediger eller slet en brugerdefineret brugervisning

Hvis du er global administrator eller brugeradministrationsadministrator af et Microsoft 365 til virksomhedsabonnement, kan du oprette brugerdefinerede brugervisninger for at få vist et bestemt undersæt af brugere. Disse visninger er ud over standardsættet af visninger. Du kan oprette, redigere eller slette brugerdefinerede brugervisninger, og de brugerdefinerede visninger, du opretter, er tilgængelige for alle administratorer.
  
## <a name="custom-user-views-in-the-admin-center"></a>Brugerdefinerede brugervisninger i Administration

Når du opretter, redigerer eller sletter en brugerdefineret brugervisning, vises ændringerne på listen **Filter** , som alle administratorer i din virksomhed kan se, når de går til siden **Brugere** . Du kan oprette op til 50 brugerdefinerede visninger. 

> [!TIP]
>  Standardbrugervisninger vises som standard på rullelisten **Filtre** . Standardfiltrene omfatter **Alle brugere**, **Licenserede brugere**, **Gæstebrugere**,  **Tilladt logon**, **Blokeret logon**, Brugere uden **licens**, **Brugere med fejl**, **Faktureringsadministratorer**, **Globale administratorer**, **Helpdesk-administratorer**, **Tjenesteadministratorer** og **Administratorer af brugeradministration**. Du kan ikke redigere eller slette standardvisninger. 

Der er et par ting, du skal være opmærksom på i forbindelse med standardvisninger: 

- Nogle standardvisninger viser en usorteret liste, hvis der er mere end 2.000 brugere på listen. Hvis du vil finde bestemte brugere på denne liste, skal du bruge søgefeltet. 
- Hvis du ikke har købt Microsoft 365 fra Microsoft, vises **faktureringsadministratorer** ikke på listen over standardvisninger. Du kan få flere oplysninger under [Tildeling af administratorroller](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Vælg filtrene til din brugerdefinerede brugervisning

Du kan oprette og redigere dine brugerdefinerede visninger i ruden **Brugerdefineret filter** . Hvis du vælger flere filterindstillinger, får du resultater, der indeholder brugere, der opfylder alle de valgte kriterier. I følgende eksempel kan du se, hvordan du opretter en brugerdefineret visning med navnet "Canadiske brugere", der viser alle brugere på et bestemt domæne, som befinder sig i Canada. 

  
 **A - Domæne** Hvis du har flere domæner til din organisation, kan du vælge på en rulleliste over domæner, der er tilgængelige. 
  
 **B – Logonstatus** Vælg brugere, der er tilladt eller blokeret. 
  
 **C - Placering** Vælg en placering på en rulleliste over lande. 
  
 **D – Tildelt produktlicens** Vælg på en rulleliste over licenser, der er tilgængelige i din organisation. Brug dette filter til at vise brugere, der har den valgte licens tildelt dem. Brugerne kan også have yderligere licenser. 
  
Du kan også filtrere efter yderligere brugerprofiloplysninger, der bruges i din organisation, f.eks. afdeling, by, stat eller provins, land eller område eller stillingsbetegnelse.
  
 **Andre betingelser:**
  
- **Kun synkroniserede brugere** Markér dette afkrydsningsfelt for at få vist alle brugere, der er blevet synkroniseret med det lokale Active Directory, uanset om brugerne er blevet aktiveret eller ej. 
    
- **Brugere med fejl** Markér dette afkrydsningsfelt for at få vist brugere, der kan have klargøringsfejl. 
    
- **Brugere uden licens** Markér dette afkrydsningsfelt for at finde alle de brugere, der ikke har fået tildelt en licens. Resultaterne for denne visning kan også omfatte brugere, der har en Exchange postkasse, men som ikke har en licens. Hvis du vil spore disse brugere specifikt, skal du bruge filteret **Brugere uden licens med Exchange postkasser eller arkiver**. Resultaterne for denne visning kan også omfatte brugere, der har et Exchange arkiv, men som ikke har en licens.
    
- **Brugere uden licens med Exchange postkasser eller arkiver** Markér dette felt for at få vist brugerkonti, der er oprettet i Exchange Online og har en Exchange postkasse, men som ikke er tildelt en Microsoft 365 licens. Resultaterne af dette filter omfatter brugere, der har eller har fået tildelt et Exchange arkiv. 

> [!NOTE]
> Filteret **Brugere uden licens med Exchange postkasser** fungerer, når:
1. Postkassen er for nylig blevet konverteret fra **delt** til **bruger** , og den har ingen licens.
2. Postkassen er for nylig blevet overført til Microsoft 365 men der er ikke tildelt en licens.
3. Postkassen er oprettet ved hjælp af PowerShell, og der er ikke tildelt en licens.
4. En ny postkasse, der er oprettet lokalt med en New-RemoteMailbox-cmdlet, klargøres for brugeren.
    
> [!TIP]
> Hvis du opretter en brugerdefineret visning, der returnerer mere end 2.000 brugere, sorteres den resulterende brugerliste ikke. I dette tilfælde skal du bruge søgefeltet til at finde brugere eller redigere din brugerdefinerede visning for at tilpasse søgningen. 
  
## <a name="create-a-custom-user-view"></a>Opret en brugerdefineret brugervisning

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a>.  

::: moniker-end
    
2. På siden **Aktive brugere** skal du vælge **Filtre** og vælge **Nyt filter**.
  
3. På siden **Brugerdefineret filter** skal du angive navnet på dit filter, vælge betingelserne for dit brugerdefinerede filter og derefter vælge **Tilføj**. Din brugerdefinerede visning er nu inkluderet på rullelisten over filtre.

## <a name="edit-or-delete-a-custom-user-view"></a>Rediger eller slet en brugerdefineret brugervisning

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a>. 

::: moniker-end 
    
2. På siden **Aktive brugere** skal du vælge **Filter**, vælge det filter, du vil ændre, og derefter vælge **Rediger filter**. 
    
    > [!TIP]
    > Du kan kun redigere brugerdefinerede visninger. 
  
3. Rediger oplysningerne efter behov på siden **Brugerdefineret filter** , og vælg derefter **Gem**. Du kan også slette filteret ved at vælge **Slet** nederst på siden. 

## <a name="related-content"></a>Relateret indhold

[Oversigt over Microsoft 365 Administration](../admin-overview/admin-center-overview.md) (video)\
[Om administratorroller](../add-users/about-admin-roles.md) (video)\
[Tilpas temaet Microsoft 365 for din organisation](../setup/customize-your-organization-theme.md) (artikel)


     
