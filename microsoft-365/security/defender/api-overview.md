---
title: Oversigt over Microsoft 365 Defender API'er
description: Få mere at vide om de tilgængelige API'er i Microsoft 365 Defender
keywords: api, apis, oversigt, hændelse, hændelser, trusselsjagt, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: c2a340c2ad147e32082a50e326a2e0c7e11718c2
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739599"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Oversigt over Microsoft 365 Defender API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Microsoft 365 Defender er bygget oven på en platform, der er klar til integration.

Brug Microsoft 365 Defender API'er til at automatisere arbejdsprocesser baseret på den delte hændelse og avancerede jagttabeller.

- **[Kø for kombinerede hændelser](api-incident.md)** – Fokuser på, hvad der er vigtigt, ved at gruppere det fulde angrebsomfang og alle påvirkede aktiver samlet under hændelses-API'en.

- **[Jagt på trusler på tværs af produkter](api-advanced-hunting.md)** – Udnyt dit sikkerhedsteams organisationsviden til at søge efter tegn på kompromis ved at oprette dine egne brugerdefinerede forespørgsler for at sidestille rådata, der indsamles på tværs af flere beskyttelsesprodukter.

- **[API til hændelsesstreaming](streaming-api.md)** – Send hændelser i realtid og beskeder i en enkelt datastream, efterhånden som de opstår.

Sammen med disse Microsoft 365 Defender-specifikke API'er fremviser hvert af vores andre sikkerhedsprodukter [yderligere API'er](api-articles.md) for at hjælpe dig med at drage fordel af deres unikke funktioner.

> [!NOTE]
> Overgangen til den samlede portal må ikke påvirke PowerBi-dashboards, der er baseret på Microsoft Defender for Endpoint API'er. Du kan fortsætte med at arbejde med de eksisterende API'er uanset den interaktive portalovergang.

Se denne korte video for at få mere at vide om, hvordan du kan bruge Microsoft 365 Defender til at automatisere arbejdsprocesser og integrere apps.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M?rel=0]

## <a name="learn-more"></a>Lær mere

| **Forstå, hvordan du får adgang til API'erne** |
|-|
| [Få mere at vide om API-kvoter og -licenser](api-terms.md) |
| [Få adgang til de Microsoft 365 Defender API'er](api-access.md) |
| **Byg apps** |
| [Opret en 'Hello world'-app](api-hello-world.md) |
| [Opret en app for at få adgang til Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md) |
| [Opret en app for at få adgang til Microsoft 365 Defender uden en bruger](api-create-app-web.md) |
| [Opret en app med partneradgang med flere lejere til Microsoft 365 Defender API'er](api-partner-access.md) |
| **Foretag fejlfinding af og vedligehold dine apps** |
| [Om API-fejlkoder](api-error-codes.md) |
| [Administrer hemmeligheder i dine apps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implementer OAuth 2.0-godkendelse for brugerlogon](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
