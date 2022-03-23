---
title: Opdatere DNS-poster for at beholde dit websted hos din nuværende hostingudbyder
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Få mere at vide om, hvordan du dirigerer trafik til et eksisterende offentligt websted, der er hostet uden for Microsoft, hvis du har indstillet Microsoft til at administrere DNS-poster for dit brugerdefinerede domæne.
ms.openlocfilehash: 9bb12d4f73e8d95717ddd90492fb9cb97c73eec9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588328"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Opdatere DNS-poster for at beholde dit websted hos din nuværende hostingudbyder

 **Hvis du administrerer dit domænes Microsoft-poster hos din DNS-udbyder**, behøver du ikke at bekymre dig om trinnene i dette emne. Dit websted bliver, hvor det er, og folk kan stadig få adgang til det. 
  
 **Hvis Microsoft administrerer dine DNS-poster**, skal du gøre følgende for at dirigere trafikken til et eksisterende offentligt websted, der er hostet uden for Microsoft, efter at du har tilføjet dit domæne til Microsoft: 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Opdater DNS-poster på Microsoft 365 Administration
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

1. På siden **Domains** skal du vælge domænet og derefter vælge **DNS Records**.

1. Vælg **+ Tilføj post** , og angiv følgende: 
    
   - Skriv **følgende** : **A (adresse)**
    
   - For **Værtsnavn eller alias** skal du skrive følgende: **@**
    
   - For **IP-adresse** skal du skrive den statiske IP-adresse til dit websted, hvor det aktuelt hostes (f.eks. 172.16.140.1). 
    
   Dette skal være en  *statisk*  IP-adresse til webstedet, ikke en  *dynamisk*  IP-adresse. Kontakt webstedet, hvor dit websted hostes, for at sikre, at du kan få en statisk IP-adresse til dit offentlige websted. 
    
1. Vælg **Gem**. 
    
Desuden kan du oprette en CNAME-post for at hjælpe kunderne med at finde dit websted.
  
1. Vælg **+ Tilføj post** , og angiv følgende: 
    
   - Skriv **følgende** for type: **CNAME (Alias)**
    
   - For **Værtsnavn eller alias** skal du skrive følgende: **www**
    
   - For **Peger på adresse** skal du skrive det fulde domænenavn for dit websted (f.eks. contoso.com). 
    
2. Vælg **Gem**. 
    
Til sidst skal du gøre følgende:
  
[Opdater dit domænes NS-poster,](../setup/add-domain.md) så de peger på Microsoft. 
  
Når NS-posterne er blevet opdateret til at pege på Microsoft, er dit domæne konfigureret. Mail dirigeres til Microsoft, og trafik til din webadresse fortsætter med at gå til din nuværende webstedsvært.
