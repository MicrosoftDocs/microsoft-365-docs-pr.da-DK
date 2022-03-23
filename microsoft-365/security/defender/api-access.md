---
title: Få adgang til Microsoft 365 Defender API'er
description: Få mere at vide om, hvordan du får adgang til Microsoft 365 Defender API'er
keywords: access, apis, programkontekst, brugerkontekst, aad-program, adgangstoken
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
ms.openlocfilehash: a8406c0ec27c238615b25f60b988efbb50a8d7d7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592706"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Få adgang til Microsoft 365 Defender API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Microsoft 365 Defender blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre fuld brug af Microsoft 365 Defender s funktioner.

Generelt skal du følge disse trin for at bruge API'er:

- Opret et Azure Active Directory program
- Få et adgangstoken ved hjælp af dette program
- Brug tokenet til at få adgang til Microsoft 365 Defender API

> [!NOTE]
> API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Når du har udført disse trin, er du klar til at få adgang til den nye Microsoft 365 Defender-API ved hjælp af en bestemt kontekst.

## <a name="application-context-recommended"></a>Programkontekst (anbefalet)

Brug denne kontekst til apps, der kører uden en bruger, der er logget på, f.eks. baggrundstjenester eller daemoner.

1. Opret et Azure Active Directory webprogram.
2. Tildele programmet de ønskede tilladelser.
3. Opret en nøgle til programmet.
4. Få et sikkerhedstoken ved hjælp af programmet og dets nøgle.
5. Brug tokenet til at få adgang til Microsoft 365 Defender API.

Få mere at vide under **[Opret en app for at få adgang Microsoft 365 Defender uden en bruger](api-create-app-web.md)**.

## <a name="user-context"></a>Brugerkontekst

Brug denne kontekst til at udføre handlinger på vegne af en enkelt bruger.

1. Opret et Azure Active Directory indbygget program.
2. Tildel den ønskede tilladelse til programmet.
3. Få et sikkerhedstoken ved hjælp af brugerlegitimationsoplysninger for programmet.
4. Brug tokenet til at få adgang til Microsoft 365 Defender API.

Få mere at vide under **[Opret en app for at få adgang Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md)**.

## <a name="partner-context"></a>Partnerkontekst

Brug denne kontekst, når du har brug for at give en app til mange brugere på tværs [af flere lejere](/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Opret et Azure Active Directory program med flere lejere.
2. Tildel den ønskede tilladelse til programmet.
3. Få [administratorsamtykke](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) til appen fra hver lejer.
4. Få et sikkerhedstoken ved hjælp af brugerlegitimationsoplysninger, der er baseret på en kundes lejer-id.
5. Brug tokenet til at få adgang til Microsoft 365 Defender API.

Få mere at vide under **[Opret en app med partneradgang til Microsoft 365 Defender API'er](api-partner-access.md)**.

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [OAuth 2.0-godkendelse til brugeradgang og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Opret et "Hej verden"-program, der har adgang til Microsoft 365 API'er](api-hello-world.md)
