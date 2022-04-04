---
title: Oprette, redigere eller slette en brugerdefineret brugervisning
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
description: Lær at bruge filtre til at oprette, redigere eller slette brugerdefineret brugervisning i Microsoft 365.
ms.openlocfilehash: cf3e286a7d8f0e9b5f9741541974b2125df505ad
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499589"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Oprette, redigere eller slette en brugerdefineret brugervisning

Hvis du er global administrator eller brugeradministrator for et Microsoft 365 for business-abonnement, kan du oprette brugerdefinerede brugervisninger for at få vist et bestemt undersæt af brugere. Disse visninger er i tillæg til standardsættet af visninger. Du kan oprette, redigere eller slette brugerdefinerede brugervisninger, og de brugerdefinerede visninger, du opretter, er tilgængelige for alle administratorer.
  
## <a name="custom-user-views-in-the-admin-center"></a>Brugerdefinerede brugervisninger i Administration

Når du opretter, redigerer eller sletter en brugerdefineret brugervisning, vises ændringerne på listen **Filter** , som alle administratorer i virksomheden kan se, når de går til **siden** Brugere. Du kan oprette op til 50 brugerdefinerede visninger. 

> [!TIP]
>  Standardbrugervisninger vises som standard **på rullelisten** Filtre. Standardfiltrene omfatter Alle **brugere,** **licenserede** **brugere,** gæstebrugere **, logon** tilladt, blokeret **logon, brugere** uden licens, brugere med fejl, **faktureringsadministratorer**, **globale** administratorer, **Helpdesk-administratorer**, **tjenesteadministratorer** og administratorer for **brugeradministration**.  Du kan ikke redigere eller slette standardvisninger. 

Et par ting, du skal være opmærksom på vedrørende standardvisninger: 

- Nogle standardvisninger viser en usorteret liste, hvis der er mere end 2.000 brugere på listen. Hvis du vil finde bestemte brugere på denne liste, skal du bruge søgefeltet. 
- Hvis du ikke har købt Microsoft 365 fra Microsoft, vises **faktureringsadministratorer** ikke på listen over almindelige visninger. Få mere at vide under [Tildel administratorroller](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Vælg filtrene for din brugerdefinerede brugervisning

Du kan oprette og redigere dine brugerdefinerede visninger i **ruden Brugerdefineret** filter. Hvis du vælger flere filterindstillinger, får du resultater, der indeholder brugere, der opfylder alle de valgte kriterier. I følgende eksempel vises det, hvordan du opretter en brugerdefineret visning med navnet "Canadiske brugere", der viser alle brugere på et bestemt domæne, der er i Canada. 

  
 **A - Domæne** Hvis du har flere domæner for organisationen, kan du vælge på en rulleliste med domæner, der er tilgængelige. 
  
 **B – Logonstatus** Vælg brugere, der er tilladte eller blokerede. 
  
 **C – Placering** Vælg en placering på en rulleliste over lande. 
  
 **D – Tildelt produktlicens** Vælg fra en rulleliste over licenser, der er tilgængelige i din organisation. Brug dette filter til at vise brugere, der har den licens, du har tildelt til dem. Brugere kan også have flere licenser. 
  
Du kan også filtrere efter yderligere brugerprofiloplysninger, der bruges i organisationen, f.eks. afdeling, by, stat eller provins, land eller område eller stilling.
  
 **Andre betingelser:**
  
- **Kun synkroniserede brugere** Markér dette felt for at få vist alle brugere, der er blevet synkroniseret med det lokale Active Directory, uanset om brugerne er blevet aktiveret eller ej. 
    
- **Brugere med fejl** Markér dette felt for at få vist brugere, der kan have klargøringsfejl. 
    
- **Brugere uden licens** Markér dette felt for at finde alle de brugere, der ikke har fået tildelt en licens. Resultaterne for denne visning kan også omfatte brugere, der har en Exchange postkasse, men ikke har en licens. For at spore disse brugere specifikt skal du bruge **filteret Brugere uden licens Exchange postkasser eller arkiver**. Resultaterne for denne visning kan også omfatte brugere, der har Exchange, men ikke har en licens.
    
- **Brugere uden licens** til Exchange-postkasser eller arkiver Markér dette felt for at få vist brugerkonti, der er oprettet i Exchange Online og har en Exchange-postkasse, men ikke blev tildelt en Microsoft 365-licens. Resultaterne af dette filter omfatter brugere, der har, eller som blev tildelt Exchange arkiv. 

> [!NOTE]
> **Filteret Brugere uden licens Exchange postkasser** fungerer, når:
1. Postkassen er for nylig blevet konverteret fra **delt** til **bruger,** og den har ingen licens.
2. Postkassen er for nylig blevet overført til Microsoft 365 men der er ikke tildelt en licens.
3. Postkassen er oprettet ved hjælp af PowerShell, og der er ikke tildelt en licens.
4. En ny postkasse, der er oprettet lokalt med en New-RemoteMailbox cmdlet, klargøres for brugeren.
    
> [!TIP]
> Hvis du opretter en brugerdefineret visning, der returnerer mere end 2.000 brugere, sorteres listen over resulterende brugere ikke. I dette tilfælde skal du bruge søgefeltet til at finde brugere eller redigere din brugerdefinerede visning for at afgrænse søgningen. 
  
## <a name="create-a-custom-user-view"></a>Oprette en brugerdefineret brugervisning

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **Aktive brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for brugere</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Aktive brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for brugere</a>.  

::: moniker-end
    
2. På siden **Aktive brugere skal** du vælge **Filtre** og vælge **Nyt filter**.
  
3. På siden **Brugerdefineret filter** skal du skrive navnet på dit filter, vælge betingelserne for dit brugerdefinerede filter og derefter vælge **Tilføj**. Din brugerdefinerede visning er nu inkluderet i rullelisten over filtre.

## <a name="edit-or-delete-a-custom-user-view"></a>Redigere eller slette en brugerdefineret brugervisning

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **Aktive brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for brugere</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Aktive brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for brugere</a>. 

::: moniker-end 
    
2. På siden **Aktive brugere skal** du vælge **Filter**, vælge det filter, du vil ændre, og derefter vælge **Rediger filter**. 
    
    > [!TIP]
    > Du kan kun redigere brugerdefinerede visninger. 
  
3. Rediger oplysningerne **efter behov** på siden Brugerdefineret filter, og vælg derefter **Gem**. Hvis du vil slette filteret, skal du vælge Slet nederst på **siden**. 

## <a name="related-content"></a>Relateret indhold

[Oversigt over Microsoft 365 Administration](../admin-overview/admin-center-overview.md) (video)\
[Om administratorroller](../add-users/about-admin-roles.md) (video)\
[Tilpasse Microsoft 365 til din organisation](../setup/customize-your-organization-theme.md) (artikel)


     
