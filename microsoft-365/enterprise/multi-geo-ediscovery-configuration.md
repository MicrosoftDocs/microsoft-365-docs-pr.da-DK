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
description: Få mere at vide om, hvordan du bruger områdeparameteren til at konfigurere eDiscovery til brug i satellitplaceringer Microsoft 365 Multi-Geo.
ms.openlocfilehash: b0366470984abbdc0ed0b3e407ca8ef6b5a5743f
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590331"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 fler geo eDiscovery-konfiguration

[Advanced eDiscovery funktioner giver](../compliance/overview-ediscovery-20.md) en multi-geo eDiscovery-administrator mulighed for at søge i alle geos uden at bruge et "Område"-sikkerhedsfilter. Data eksporteres til Azure-forekomsten af den centrale placering af multi-geo-lejeren. Det samme sker, når der anvendes venteposition på en vagt, men opbevaringsstatistikken i venteposition vises ikke uden sikkerhedsfilteret "Område". Ventepositionsstatistik, der viser 0, betyder ikke, at ventepositionen mislykkedes, så længe ventepositionsstatussen viser Til (vellykket).

Uden avancerede eDiscovery-egenskaber vil en eDiscovery-leder eller administrator for en multi-geo-lejer kun kunne gennemføre eDiscovery på den pågældende lejers centrale placering. For at understøtte muligheden for at udføre eDiscovery til satellitplaceringer er en ny parameter for overholdelsessikkerhedsfilter med navnet "Region" tilgængelig via PowerShell. Dette parameter kan bruges af lejere, hvis centrale placering er i Nordamerika, Europa eller Asien/Stillehavsområdet. Advanced eDiscovery til lejere, hvis centrale placering ikke er i Nordamerika, Europa eller Asien/Stillehavsområdet, og som skal udføre eDiscovery på tværs af satellit geoplaceringer. 

Den globale Microsoft 365-administrator skal tildele eDiscovery Manager-tilladelser for at give andre tilladelse til at udføre eDiscovery og tildele et "Område"-parameter i deres gældende Overholdelsessikkerhedsfilter for at angive det område, hvor eDiscovery skal udføres som satellitplacering, ellers vil der ikke blive udført eDiscovery til satellitplaceringen. Der understøttes kun ét "Område"-sikkerhedsfilter pr. bruger, så alle områder skal være inden for det samme sikkerhedsfilter.

Når eDiscovery-chefen eller administratorrollen er indstillet til en bestemt satellitplacering, vil eDiscovery-lederen eller administratoren kun kunne udføre eDiscovery-søgehandlinger mod SharePoint-websteder og OneDrive-websteder, der er placeret i den pågældende satellitplacering. Hvis en eDiscovery-leder eller administrator forsøger at SharePoint eller OneDrive websteder uden for den angivne satellitplacering, returneres ingen resultater. Når eDiscovery-chefen eller administratoren for en satellitplacering udløser en eksport, eksporteres data til Azure-forekomsten i det pågældende område. Dette hjælper organisationer med at overholde reglerne ved ikke at tillade eksport af indhold på tværs af kontrollerede kanter.

> [!NOTE]
> Hvis det er nødvendigt, at en eDiscovery Manager søger på tværs af flere SharePoint-satellitplaceringer, skal der oprettes en anden brugerkonto til eDiscovery Manager, som angiver den alternative satellitplacering, hvor OneDrive- eller SharePoint-webstederne er placeret.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Sådan angives filteret til overholdelse af regler og standarder for et område:

1. [Forbind Microsoft 365 Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Brug følgende syntaks:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Eksempel:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Se artiklen [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) for yderligere parametre og syntaks.
