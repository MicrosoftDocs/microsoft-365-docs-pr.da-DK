---
title: Oversigt over Microsoft 365 Defender API'er
description: Få mere at vide om de tilgængelige API'er i Microsoft 365 Defender
keywords: API, API'er, oversigt, hændelse, hændelser, trusselssøgning, Microsoft 365 Defender
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
ms.openlocfilehash: ec4a497fd0ee428fbc664ae064ec95f74fcdce85
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63591975"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Oversigt over Microsoft 365 Defender API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Microsoft 365 Defender er bygget oven på en integrationsklar platform.

Brug den Microsoft 365 Defender API'er til at automatisere arbejdsprocesser baseret på den delte hændelse og avancerede søgetabeller.

- **[Samlet kø til hændelser](api-incident.md)** – Fokuser på det, der er vigtigt, ved at gruppere det fulde angrebsomfang og alle på hinanden følgende aktiver under hændelses-API'en.

- På tværs af **[produkttrusler](api-advanced-hunting.md)** – Udnyt dit sikkerhedsteams organisatoriske viden til at lede efter tegn på kompromis ved at oprette dine egne brugerdefinerede forespørgsler for at udnytte rå data, der er indsamlet på tværs af flere beskyttelsesprodukter.

- **[Hændelsesstreaming-API](streaming-api.md)** – Send begivenheder og beskeder i realtid i en enkelt datastrøm, mens de opstår.

Sammen med disse Microsoft 365 Defender-specifikke API'er fremviser hver af vores andre sikkerhedsprodukter yderligere API'er, der kan hjælpe dig med at udnytte deres unikke egenskaber.[](api-articles.md)

> [!NOTE]
> Overgangen til den samlede portal bør ikke påvirke PowerBi-dashboards, der er baseret på Microsoft Defender til slutpunkt-API'er. Du kan fortsætte med at arbejde med de eksisterende API'er uanset den interaktive portalovergang.

## <a name="learn-more"></a>Lær mere

| **Forstå, hvordan du får adgang til API'er** |
|-|
| [Få mere at vide om API-kvoter og licenser](api-terms.md) |
| [Få adgang til Microsoft 365 Defender API'er](api-access.md) |
| **Byg apps** |
| [Opret en "Hej verden"-app](api-hello-world.md) |
| [Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md) |
| [Opret en app for at få adgang Microsoft 365 Defender uden en bruger](api-create-app-web.md) |
| [Opret en app med partneradgang til flere lejere til Microsoft 365 Defender API'er](api-partner-access.md) |
| **Fejlfinding og vedligeholdelse af dine apps** |
| [Forstå API-fejlkoder](api-error-codes.md) |
| [Administrer hemmeligheder i dine apps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implementer OAuth 2.0-godkendelse til bruger logon](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
