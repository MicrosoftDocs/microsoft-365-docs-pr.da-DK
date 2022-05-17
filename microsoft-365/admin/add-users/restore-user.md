---
title: Gendan en bruger
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
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: Inden for 30 dage efter sletning af en brugerkonto kan du gendanne kontoen og alle data, og brugeren kan logge på med den samme konto.
ms.openlocfilehash: 2f9a28e5000c1ba826b5458916f30c3e8a438253
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436201"
---
# <a name="restore-a-user-in-the-microsoft-365-admin-center"></a>Gendan en bruger i Microsoft 365 Administration
   
Når du gendanner en brugerkonto inden for 30 dage efter sletningen, gendannes kontoen og alle tilknyttede data. Brugeren kan logge på med den samme arbejds- eller skolekonto. Postkassen gendannes helt. [Kontakt os](../../business-video/get-help-support.md) for at finde ud af, hvor lang tid der er tilbage, før en bestemt brugerkonto ikke længere kan gendannes.
  
Her er et par tip:
  
- Sørg for, at der er tilgængelige licenser, som kontoen kan tildeles.
    
- Hvis din virksomhed bruger Active Directory, kan du finde oplysninger om, hvordan du gendanner en brugerkonto, [under Sådan foretager du fejlfinding af slettede brugerkonti i Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Gendan en eller flere brugerkonti

Du skal være Microsoft 365 global administrator eller administrator af brugeradministration for at kunne udføre disse trin. 

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">slettede brugere</a> .

2. På siden **Slettede brugere** skal du vælge navnene på de brugere, du vil gendanne, og derefter vælge **Gendan**.
    
3. Følg prompterne for at angive deres adgangskode, og vælg derefter **Gendan**.
    
4. Hvis brugeren er gendannet, skal du vælge **Send mail og lukke**. Hvis du støder på en navnekonflikt eller en proxyadressekonflikt, skal du se vejledningen nedenfor for at få oplysninger om, hvordan du gendanner disse konti.
    
Når du har gendannet en bruger, skal du sørge for at give vedkommende besked om, at adgangskoden er ændret, og du følger op på den.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Gendan en bruger, der har en konflikt med et brugernavn

Der opstår en brugernavnskonflikt, når du sletter en brugerkonto, opretter en ny brugerkonto med samme brugernavn (enten for den samme bruger eller en anden bruger med et lignende navn) og senere forsøger at gendanne den slettede konto.
  
Du kan løse problemet ved at erstatte den aktive brugerkonto med den, du gendanner. Eller tildel et andet brugernavn til den konto, du gendanner, så der ikke er to konti med samme brugernavn. Her er trinnene.

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">slettede brugere</a> .
  
2. På siden **Slettede brugere** skal du vælge navnene på de brugere, du vil gendanne, og derefter vælge **Gendan**.
    
    > [!NOTE]
    > Hvis to eller flere brugere ikke kan gendannes, får du en fejlmeddelelse om, at gendannelsen mislykkedes for nogle brugere. Vis logfilen for at se, hvilke brugere der ikke blev gendannet, og gendan derefter de mislykkede konti én ad gangen. 
  
3. Følg prompterne for at angive adgangskoden, og vælg **Gendan**.
    
4. En meddelelse dukker op, der siger, at der var et problem med at gendanne kontoen. Gør et af følgende:
    
     - Annuller gendannelsen, og omdøb den aktuelle aktive bruger. Prøv derefter at gendanne igen.
    
     - ELLER du kan skrive en ny primær mailadresse for brugeren og vælge **Gendan**.
    
5. Gennemse resultaterne, og vælg derefter **Luk**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Gendan en bruger, der har en proxyadressekonflikt

Der opstår en proxyadressekonflikt, når du sletter en brugerkonto, der indeholder en proxyadresse, tildeler den samme proxyadresse til en anden konto og derefter forsøger at gendanne den slettede konto. Følg nedenstående trin for at løse problemet.
  
Du skal have [administratortilladelser](about-admin-roles.md) i Microsoft 365 for at gøre dette. 

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">slettede brugere</a> .

2. På siden **Slettede brugere** skal du vælge den bruger, du vil gendanne, og derefter vælge **Gendan**. 
    
3. Følg instruktionerne på siden **Gendan** for at angive adgangskoden, og vælg **Gendan**. Alle modstridende proxyadresser fjernes automatisk fra den bruger, du gendanner.
    
4. Gennemse resultaterne, og vælg derefter **Luk**.

## <a name="related-content"></a>Relateret indhold

[Slet en bruger](delete-a-user.md) (artikel)\
[Tildel administratorroller](assign-admin-roles.md) (video)\
[Tildel licenser til brugere](../manage/assign-licenses-to-users.md) (artikel)
