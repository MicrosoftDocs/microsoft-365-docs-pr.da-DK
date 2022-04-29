---
title: Konfigurer Microsoft 365 Multi-Geo eDiscovery
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
ms.collection: Strat_SP_gtc
description: Få mere at vide om, hvordan du bruger parameteren Region til at konfigurere eDiscovery til brug på satellitplaceringer i Microsoft 365 Multi-Geo.
ms.openlocfilehash: a220e68e6dbe010f2eab6876dc2813dcd84d5d6d
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130927"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 Multi-Geo eDiscovery-konfiguration

[eDiscovery-funktioner (Premium)](../compliance/overview-ediscovery-20.md) gør det muligt for en multi-geo-eDiscovery-administrator at søge i alle geos uden at skulle bruge et sikkerhedsfilter af typen "Område". Data eksporteres til Azure-forekomsten af den centrale placering af multi-geo-lejeren.

Uden eDiscovery-funktioner (Premium) kan en eDiscovery-administrator eller administrator af en multi-geo-lejer kun udføre eDiscovery på den centrale placering af lejeren. For at understøtte muligheden for at udføre eDiscovery for satellitplaceringer er der en ny filterparameter for overholdelse af angivne standarder med navnet "Område" tilgængelig via PowerShell. Denne parameter kan bruges af lejere, hvis centrale placering er i Nordamerika, Europa eller Asien og Stillehavsområdet. eDiscovery (Premium) anbefales til lejere, hvis centrale placering ikke er i Nordamerika, Europa eller Asien og Stillehavsområdet, og som har brug for at udføre eDiscovery på tværs af geografiske satellitplaceringer.

Den Microsoft 365 globale administrator skal tildele eDiscovery Manager-tilladelser for at give andre tilladelse til at udføre eDiscovery og tildele en "Område"-parameter i deres relevante overholdelsessikkerhedsfilter for at angive området til udførelse af eDiscovery som satellitplacering, ellers udføres der ingen eDiscovery for satellitplaceringen. Der understøttes kun ét "Område"-sikkerhedsfilter pr. bruger, så alle områder skal være inden for det samme sikkerhedsfilter.

Når rollen eDiscovery Manager eller Administrator er angivet for en bestemt satellitplacering, kan eDiscovery Manager eller Administrator kun udføre eDiscovery-søgehandlinger på de SharePoint websteder og OneDrive websteder, der er placeret på denne satellitplacering. Hvis en eDiscovery-administrator forsøger at søge SharePoint eller OneDrive websteder uden for den angivne satellitplacering, returneres der ingen resultater. Når eDiscovery Manager eller Administrator for en satellitplacering udløser en eksport, eksporteres data også til Azure-forekomsten af det pågældende område. Dette hjælper organisationer med at overholde angivne standarder ved ikke at tillade, at indhold eksporteres på tværs af kontrollerede grænser.

> [!NOTE]
> Hvis det er nødvendigt for en eDiscovery Manager at søge på tværs af flere SharePoint satellitplaceringer, skal der oprettes en anden brugerkonto for eDiscovery Manager, som angiver den alternative satellitplacering, hvor de OneDrive eller SharePoint websteder er placeret.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Sådan angiver du sikkerhedsfilteret for overholdelse af angivne standarder for et område:

1. [Forbind til Microsoft 365 Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Brug følgende syntaks:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Eksempel:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Se artiklen [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) for at få flere parametre og syntaks.
