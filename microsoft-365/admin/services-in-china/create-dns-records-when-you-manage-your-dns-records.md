---
title: Oprette DNS-poster for Office 365, når du administrerer dine DNS-poster
f1.keywords:
- CSH
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
- MET150
- GEA150
ms.assetid: 0669bf14-414d-4f51-8231-6b710ce7980b
ROBOTS: NOINDEX
description: 'Lær at oprette DNS-poster for Office 365 drevet af 21Vianet, når du administrerer dine DNS-poster. '
monikerRange: o365-21vianet
ms.openlocfilehash: b1254ed341fb73f17f457798f14d01d89063f920
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589379"
---
# <a name="create-dns-records-for-office-365-when-you-manage-your-dns-records"></a>Oprette DNS-poster for Office 365, når du administrerer dine DNS-poster

Du kan finde detaljerede oplysninger om, hvordan du opretter DNS-poster for Office 365 drevet af 21Vianet, herunder den MX-post, der kræves til mailrouting, under Oprette [DNS-poster](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) for Office 365. 
  
  
Flere indstillinger og nogle ting, du skal være opmærksom på:
      
-  Hvis du ikke kender DNS-udbyderen eller domæneregistratoren for dit domæne, kan du se [Finde din domæneregistrator eller DNS-udbyder](../get-help-with-domains/find-your-domain-registrar.md). Du kan finde beskrivelser af, hvad DNS-posterne gør, under [Grundlæggende om DNS](../get-help-with-domains/dns-basics.md).
    
-  Nogle DNS-udbydere tillader ikke, at du opretter alle de nødvendige posttyper, hvilket medfører Tjenestebegrænsninger, når din udbyder ikke [understøtter SRV, CNAME, TXT eller omdirigering](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). Hvis din udbyder ikke understøtter SRV-, TXT- eller CNAME-poster, anbefaler vi, [](../get-help-with-domains/buy-a-domain-name.md) at du overfører dit domæne til en udbyder, der understøtter alle [de nødvendige posttyper](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). 
    
- Hvis du vil se, hvilke DNS-poster der er nødvendige, og finde de værdier, der skal bruges for hver post, herunder MX-posten til mail, skal du se Indsamle de oplysninger, du skal bruge for [at oprette Office 365 DNS-poster](../get-help-with-domains/information-for-dns-records.md). Du kan finde beskrivelser af, hvad DNS-posterne gør, under [Grundlæggende om DNS](../get-help-with-domains/dns-basics.md).
