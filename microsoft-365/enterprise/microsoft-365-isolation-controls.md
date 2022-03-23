---
title: Microsoft 365 af isolationskontrolelementer
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Få mere at vide om, hvordan isolationskontrolelementer fungerer inden Microsoft 365, så tjenester kan fungere sammen med andre eller bevares efter behov.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 514b12e44d9e81a18b691ebf3196a3d21157e71b
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63590576"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 af isolationskontrolelementer 

Microsoft arbejder løbende på at sikre, at arkitekturen med flere lejere i Microsoft 365 understøtter standarder for sikkerhed, fortrolighed, beskyttelse af personlige oplysninger, integritet, lokale, internationale og [tilgængelighedsstandarder på virksomhedsniveau](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons). Omfanget og omfanget af tjenester, der leveres af Microsoft, gør det svært og ikke-økonomisk at administrere Microsoft 365 med en betydelig menneskelig interaktion. Microsoft 365-tjenester leveres via flere globalt distribuerede datacentre, hver meget automatiseret med få handlinger, der kræver menneskelig berøring eller nogen form for adgang til kundeindhold. Vores medarbejdere understøtter disse tjenester og datacentre ved hjælp af automatiserede værktøjer og meget sikker fjernadgang. 

Microsoft 365 består af flere tjenester, der giver vigtig forretningsfunktionalitet og bidrager til hele Microsoft 365 oplevelse. Hver af disse tjenester er selvstændige og udviklet til at integrere med hinanden.

Microsoft 365 er designet med følgende principper:

 - **[Tjenesteorienteret arkitektur](/previous-versions/aa480021(v=msdn.10)):** design og udvikling af software i form af interoperaoperatbaserede tjenester, der giver veldefineret forretningsfunktionalitet.
 - **[Driftssikkerhedssikring](https://www.microsoft.com/download/details.aspx?id=40872):** en ramme, der inkorporerer den viden, der er opnået via forskellige funktioner, der er unikke for Microsoft, herunder Livscyklus for [Microsofts Sikkerhedsudvikling](https://www.microsoft.com/sdl/default.aspx), [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx) og en dybtgående indsigt i cybersikkerhedstruslerbilledet.

Microsoft 365 tjenester, der arbejder sammen med hinanden, men er designet og implementeret, så de kan installeres og drives som tjenester, der er uafhængige af hinanden. Microsoft fratager ansvarsområder og ansvarsområder Microsoft 365 at reducere risikoen for uautoriseret eller utilsigtet ændring eller misbrug af organisationens aktiver. Microsoft 365 teams har defineret roller som en del af en omfattende rollebaseret adgangskontrolmekanismen.

## <a name="customer-content-isolation"></a>Kundeindholdsisolation

Alt kundeindhold i en lejer isoleres fra andre lejere og fra handlinger og systemer, der bruges i administrationen af Microsoft 365. Der er implementeret flere former for beskyttelse i Microsoft 365 for at minimere risikoen for at gå på kompromis med Microsoft 365 tjeneste eller program. Flere former for beskyttelse forhindrer også uautoriseret adgang til oplysningerne om lejere eller selve Microsoft 365 selve systemet.

Du kan finde oplysninger om, hvordan Microsoft implementerer logisk isolation af Microsoft 365 i Microsoft 365, under [Lejerisolation Microsoft 365](microsoft-365-tenant-isolation-overview.md).