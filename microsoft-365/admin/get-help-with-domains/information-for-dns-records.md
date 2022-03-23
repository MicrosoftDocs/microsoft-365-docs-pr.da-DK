---
title: Indsamle de oplysninger, du skal bruge til at oprette DNS-poster
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
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Indsamd de værdier/oplysninger, du skal bruge til at oprette DNS-poster for at forbinde dit domæne med dit Microsoft 365 abonnement.
ms.openlocfilehash: 672d57babb1b26e42b3fd24da8c9dc841223e41f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590156"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Indsamle de oplysninger, du skal bruge til at oprette DNS-poster

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Trin 1: Find værdien for TXT-posten, og bekræft

::: moniker range="o365-worldwide"

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Indstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domæner</a>.

::: moniker-end
    
2. På siden **Domæner skal** du vælge dit domæne og derefter vælge **Start installationen**. Du skal gå tilbage til konfigurationsguiden for domæner for at se den specifikke værdi, du skal tilføje.
    
3. På siden **Domænebekræftelse** skal du vælge **Tilføj en TXT-post til domænets DNS-poster** og derefter vælge **Fortsæt**.
    
4. Kopiér den **viste TXT-værdi** . Den ser sådan ud: **MS=msXXXXXXXX**. 
    
5. Gå til [Tilføj DNS-poster for at oprette forbindelse til](create-dns-records-at-any-dns-hosting-provider.md) dit domæne, og følg trinnene for at tilføje poster på DNS-værtens websted.
    
6. Følg trinnene for at oprette TXT-posten (eller MX-posten) hos din DNS-vært, og bekræft derefter domænet igen Microsoft 365.

7. Fjern TXT-posten (eller MX-posten) fra din DNS-vært, når domænet er blevet bekræftet i Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Trin 2: Find MX-postværdien til mail og meget mere

::: moniker range="o365-worldwide"

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **Indstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domæner</a>.

::: moniker-end
    
2. På siden **Domæner skal** du vælge dit domæne.
    
3. Vælg **Manage DNS**, vælg **More OptionsAdd** >  **your own DNS**, og vælg **Continue for at** få vist de DNS-poster, der skal tilføjes.
    
    Du skal sørge for, at disse oplysninger er tilgængelige, mens du foretager ændringer hos din DNS-vært, så du kan kopiere og indsætte værdierne.
    
    De grupper af DNS-poster, der er angivet på siden, afhænger af dine valg, der er angivet under **Domæneformål**.
    
4. Gå til [Tilføj DNS-poster for at oprette forbindelse til](create-dns-records-at-any-dns-hosting-provider.md) dit domæne, og følg trinnene for at tilføje poster på DNS-værtens websted.

5. Følg trinnene for at oprette posterne hos din DNS-vært.

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)\
[Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster](find-and-fix-issues.md) (artikel)\
[Administrer domæner](/admin) (linkside)