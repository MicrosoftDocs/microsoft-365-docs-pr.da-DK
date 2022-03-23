---
title: Hvad er formålet med den Office 365 CNAME-post for MSOID?
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: Få mere at vide om "MSOID" CNAME-posten i Office 365, der dirigerer dig til den bedste server til godkendelsesprocesser, så du får et hurtigere svar.
monikerRange: o365-21vianet
ms.openlocfilehash: 1b053ac0df7cd770b5627b688e90641688f94141
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589377"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>Hvad er formålet med den Office 365 CNAME-post for MSOID?

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
> [!NOTE]
> Følgende gælder kun for **Office 365 drevet af 21Vianet.
  
Du undrer dig måske over, hvorfor du skal tilføje "MSOID" CNAME-posten Office 365. Dette er en post, der skal tilføjes for alle brugerdefinerede domæner, uanset hvilket abonnement du bruger. Hvorfor har du brug for det? Det er lidt teknisk, men dybest set gør det, at du bliver omdirigeret til den bedste server for visse godkendelsesprocesser, så du får hurtigere svar.
  
Tekniske detaljer: Når du kører et klientprogram, der fungerer sammen med Office 365 f.eks. Skype for Business Online, Outlook, Windows PowerShell eller Microsoft Azure Active Directory-synkroniseringsværktøjet, skal dine legitimationsoplysninger være godkendt. Office 365 bruger en CNAME-post til at pege på det korrekte godkendelsesslutpunkt for din placering, hvilket sikrer hurtige svartider for godkendelse.
  
Hvis denne CNAME-post mangler for dit domæne, bruger disse programmer et standardslutpunkt for godkendelse i USA, hvilket betyder, at godkendelsen tager langsommere. Hvis denne CNAME-post ikke er konfigureret korrekt, f.eks. hvis der er en slåfejl i peger på **adressen, kan** disse programmer ikke godkende.
  
 **Hvis Office 365 administrerer dit domænes DNS-poster,** konfigurerer Office 365 denne CNAME-post for dig. 
  
 **Hvis du administrerer DNS-posterne for** dit domæne hos din DNS-vært, opretter du selv denne post ved at [følge vejledningen til din DNS-vært](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
  
Hvis du planlægger en Office 365-installation, og du vil vide mere om alle de DNS-poster, du muligvis skal tilføje eller opdatere, skal du læse om dem i [Reference: Eksterne DNS-poster for Office 365](../../enterprise/external-domain-name-system-records.md).
