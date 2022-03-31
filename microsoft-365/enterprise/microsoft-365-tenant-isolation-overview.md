---
title: Lejerisolation i Microsoft 365
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
description: Denne artikel indeholder en oversigt over, hvordan Microsoft gennemtvinger lejerisolation i skytjenester som f.Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b52d936bb00ac0adef0baf428cbc5f9a8f8aba49
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63601601"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Lejerisolation i Microsoft 365

En af de primære fordele ved cloud computing er en delt, fælles infrastruktur på tværs af mange kunder samtidigt, hvilket medfører stor skala. Dette koncept kaldes *for flere lejemål*. Microsoft arbejder løbende på at sikre, at arkitekturer med flere lejere i vores skytjenester understøtter standarder for sikkerhed, fortrolighed, beskyttelse af personlige oplysninger, integritet og tilgængelighed på virksomhedsniveau.

Baseret på væsentlige investeringer og erfaringer fra [Trustworthy Computing](https://www.microsoft.com/trust-center) og [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/) blev Microsofts skytjenester udformet under den forudsætning, at alle lejere potentielt har alle andre lejere, og vi har implementeret sikkerhedsforanstaltninger for at forhindre, at en lejers handlinger påvirker sikkerheden eller tjenesten for en anden lejer.  eller få adgang til indholdet fra en anden lejer.

De to primære mål for at bevare lejerisolering i et miljø med flere lejere er:

1.    Undgå lækage af eller uautoriseret adgang til kundeindhold på tværs af lejere; og
2.    Undgå, at en lejers handlinger påvirker tjenesten i negativ ende for en anden lejer

Der er blevet implementeret flere former for beskyttelse i hele Microsoft 365 for at forhindre kunder i at gå på kompromis med Microsoft 365-tjenester eller -programmer eller for at få uautoriseret adgang til oplysningerne om andre lejere eller selve Microsoft 365-systemet, herunder:

- Logisk isolation af kundeindhold inden for hver lejer for Microsoft 365-tjenester opnås Azure Active Directory godkendelse og rollebaseret adgangskontrol.
- SharePoint Online indeholder dataisolationsmekanismer på lagerniveau.
- Microsoft bruger fysisk sikkerhed og baggrundskage og en krypteringsstrategi i flere lag til at beskytte fortroligheden og integriteten af kundeindhold. Alle Microsoft 365 har biometriske adgangskontrolelementer, hvor det mest er nødvendigt med håndfladeudskrifter for at få fysisk adgang. Desuden skal alle amerikansk baserede Microsoft-medarbejdere gennemføre en standard baggrundskontrol som en del af ansættelsesprocessen. Du kan finde flere oplysninger om de kontrolelementer, der bruges til administrativ adgang Microsoft 365, [under Microsoft 365 Administrative adgangskontroller](/compliance/assurance/assurance-administrative-access-controls-overview).
- Microsoft 365 bruger tjenesteteknologier, der krypterer kundens indhold under transport og under overførsel, herunder BitLocker, kryptering pr. fil, TLS (Transport Layer Security) og IPsec (Internet Protocol Security). Du kan finde specifikke oplysninger om Microsoft 365 i [Datakrypteringsteknologier i Microsoft 365](../compliance/office-365-encryption-in-the-microsoft-cloud-overview.md).

Tilsammen giver de ovennævnte beskyttelser robuste logiske isolationskontrolelementer, der giver trusselsbeskyttelse og afhjælpning svarende til dem, der leveres af fysisk isolation alene.

## <a name="related-links"></a>Relaterede links

- [Isolation og adgangskontrol i Azure Active Directory](microsoft-365-isolation-in-azure-active-directory.md)
- [Lejerisolation i Office Graph og Delve](microsoft-365-isolation-in-graph-and-delve.md)
- [Lejerisolation i Microsoft 365 søgning](microsoft-365-isolation-in-microsoft-365-search.md)
- [Ressourcebegrænsninger](/compliance/assurance/assurance-resource-limits)
- [Overvågning og test af lejergrænser](/compliance/assurance/assurance-monitoring-and-testing)
- [Isolation og adgangskontrol i Microsoft 365](microsoft-365-isolation-in-microsoft-365.md)