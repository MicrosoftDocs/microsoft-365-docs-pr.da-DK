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
description: Inden for 30 dage efter sletningen af en brugerkonto kan du gendanne kontoen og alle data, og brugeren kan logge på med den samme konto.
ms.openlocfilehash: fc011f9589d789a7eb2faa332a104ef670cf6590
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63589912"
---
# <a name="restore-a-user"></a>Gendan en bruger
   
Når du gendanner en brugerkonto inden for 30 dage efter sletningen, gendannes kontoen og alle de tilknyttede data. Brugeren kan logge på med den samme arbejds- eller skolekonto. Deres postkasse gendannes fuldstændigt. Hvis du vil vide, hvor lang tid der er tilbage, før en bestemt brugerkonto ikke længere kan gendannes, skal [du kontakte os](../../business-video/get-help-support.md).
  
Her er et par tip:
  
- Sørg for, at licenser er tilgængelige til at tildele til kontoen.
    
- Hvis din virksomhed bruger Active Directory, kan du finde en vejledning til gendannelse af en brugerkonto under Sådan foretager du fejlfinding af [slettede brugerkonti Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Gendan en eller flere brugerkonti

Du skal være global Microsoft 365 eller brugeradministrator for at udføre disse trin. 

1. I Administration skal du gå til **siden Slettede** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">for</a> Brugere.

2. På siden **Slettede brugere** skal du vælge navnene på de brugere, du vil gendanne, og derefter vælge **Gendan**.
    
3. Følg instruktionerne for at angive adgangskoden, og vælg derefter **Gendan**.
    
4. Hvis brugeren er gendannet, skal du vælge **Send mail og luk**. Hvis der opstår en navnekonflikt eller proxyadressekonflikt, skal du se vejledningen nedenfor for at gendanne disse konti.
    
Når du har gendannet en bruger, skal du sørge for at give brugeren besked om, at vedkommendes adgangskode er ændret, og du følger op med dem.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Gendanne en bruger med en brugernavnskonflikt

Der opstår en brugernavnskonflikt, når du sletter en brugerkonto, opretter en ny brugerkonto med det samme brugernavn (enten til den samme bruger eller en anden bruger med et lignende navn) og derefter forsøger at gendanne den slettede konto.
  
Det løser du ved at erstatte den aktive brugerkonto med den, du gendanner. Du kan også tildele et andet brugernavn til den konto, du gendanner, så der ikke er to konti med samme brugernavn. Sådan gør du.

1. I Administration skal du gå til **siden Slettede** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">for</a> Brugere.
  
2. På siden **Slettede brugere** skal du vælge navnene på de brugere, du vil gendanne, og derefter vælge **Gendan**.
    
    > [!NOTE]
    > Hvis to eller flere brugere ikke kan gendannes, får du i en fejlmeddelelse at vide, at gendannelsen af nogle brugere ikke lykkedes. I logfilen kan du se, hvilke brugere der ikke blev gendannet, og derefter gendanne disse konti én af gangen. 
  
3. Følg instruktionerne for at angive adgangskoden, og vælg **Gendan**.
    
4. Der vises en pop op-meddelelse, hvor der står, at der opstod et problem under gendannelsen af kontoen. Gør et af følgende:
    
     - Annuller gendannelsen, og omdøb den aktuelle aktive bruger. Forsøg derefter at gendanne igen.
    
     - ELLER skriv en ny primær mailadresse for brugeren, og vælg **Gendan**.
    
5. Gennemse resultaterne, og vælg derefter **Luk**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Gendan en bruger med en proxyadressekonflikt

Der opstår en proxyadressekonflikt, når du sletter en brugerkonto, der indeholder en proxyadresse, tildeler den samme proxyadresse til en anden konto og derefter forsøger at gendanne den slettede konto. Følg trinnene nedenfor for at løse problemet.
  
Du skal have [administratortilladelser i din](about-admin-roles.md) Microsoft 365 for at gøre dette. 

1. I Administration skal du gå til **siden Slettede** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">for</a> Brugere.

2. På siden **Slettede brugere** skal du vælge den bruger, du vil gendanne, og derefter vælge **Gendan**. 
    
3. På siden **Gendan** skal du følge vejledningen for at angive adgangskoden og vælge **Gendan**. Eventuelle problemer med uens proxyadresser fjernes automatisk fra den bruger, du gendanner.
    
4. Gennemse resultaterne, og vælg derefter **Luk**.

## <a name="related-content"></a>Relateret indhold

[Slet en bruger](delete-a-user.md) (artikel)\
[Tildel administratorroller](assign-admin-roles.md) (video)\
[Tildel licenser til brugere](../manage/assign-licenses-to-users.md) (artikel)
