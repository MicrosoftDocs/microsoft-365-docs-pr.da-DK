---
title: Administrer Microsoft 365 med Windows PowerShell for DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Sådan kan Syndication- Cloud Solution Provider -partnere (CSP) bruge Windows PowerShell til at administrere Microsoft 365 lejere.
ms.openlocfilehash: 2678489d1e281a60d230c65e29b358dff5f1a8ad
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594259"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Sådan administreres Microsoft 365 med Windows PowerShell for partnere med tilladelse til delegeret adgang

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Delegerede adgangstilladelsespartnere (DAP) er Syndication- og Skyløsningsudbydere (CSP-partnere). Mange er netværksudbydere eller telekommunikationsudbydere. They bundle Microsoft 365 subscriptions into their service offerings. Når de sælger et Microsoft 365-abonnement, tildeles de automatisk Administrer på vegne af (AOBO)-tilladelser til kundens leje, så de kan administrere og rapportere om disse uoverensstemmelser. Disse opgaver er svære at udføre i Microsoft 365 Administration. Det er meget nemmere at bruge PowerShell til Microsoft 365 udføre administrative opgaver som f.eks.:
- Vis alle kundens **TenantIds** og deres domæner 
- Identificer alle brugere i en kundes leje og deres tildelte licenser
> [!NOTE]
> Nogle administrative opgaver kan kun udføres i PowerShell.

Følgende artikler viser, hvordan Syndication- og CSP-partnere bruger PowerShell til at administrere deres kundeancititeter:
  
- [Administrere Microsoft 365 lejere med Windows PowerShell for DAP-partnere (Delegated Access Permissions)](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Føj et domæne til en klients leje med Windows PowerShell for DAP-partnere (Delegated Access Permission)](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [Hent rapporteringsdata om kundelejer med Windows PowerShell for DAP-partnere (Delegated Access Permissions)](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
