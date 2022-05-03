---
title: Få adgang til Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Få mere at vide om, hvordan du kan bruge API'er til at automatisere arbejdsprocesser og skabe innovation baseret på Microsoft Defender for Endpoint funktioner
keywords: apis, api, wdatp, open api, microsoft defender for endpoint api, Microsoft defender atp, public api, understøttede API'er, beskeder, enhed, bruger, domæne, ip, fil, avanceret jagt, forespørgsel
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3638357d2c1440604858fabfa42e5df32569aed3
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172264"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Få adgang til Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> Avancerede jagtegenskaber er ikke inkluderet i Defender for Business. Se [Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender for Endpoint fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er gør det muligt for dig at automatisere arbejdsprocesser og skabe innovation baseret på Funktionerne i Defender for Endpoint. API-adgangen kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Se denne video for at få et hurtigt overblik over Defender for Endpoints API'er.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Generelt skal du gøre følgende for at bruge API'erne:

- Opret et [AAD program](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Hent et adgangstoken ved hjælp af dette program
- Brug tokenet til at få adgang til Defender for Endpoint API

Du kan få adgang til Defender for Endpoint API med **programkontekst** eller **brugerkontekst**.

- **Programkontekst: (anbefales)**

  Bruges af apps, der kører uden en bruger, der er logget på. f.eks. apps, der kører som baggrundstjenester eller daemoner.

  Trin, der skal udføres for at få adgang til Defender for Endpoint API med programkontekst:

  1. Opret et AAD webprogram.
  2. Tildel den ønskede tilladelse til programmet, f.eks. 'Læs beskeder', 'Isoler maskiner'.
  3. Opret en nøgle til dette program.
  4. Hent token ved hjælp af programmet med nøglen.
  5. Brug tokenet til at få adgang til Microsoft Defender for Endpoint API'en

     Du kan få flere oplysninger under [Få adgang med programkontekst](exposed-apis-create-app-webapp.md).

- **Brugerkontekst:**

  Bruges til at udføre handlinger i API'en på vegne af en bruger.

  Trin, der skal udføres for at få adgang til Defender for Endpoint API med brugerkontekst:

  1. Opret AAD oprindeligt program.
  2. Tildel den ønskede tilladelse til programmet, f.eks. 'Læs beskeder', 'Isoler maskiner' osv.
  3. Hent token ved hjælp af programmet med brugerlegitimationsoplysninger.
  4. Brug tokenet til at få adgang til Microsoft Defender for Endpoint API'en

     Du kan få flere oplysninger under [Få adgang med brugerkontekst](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- [Adgang Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md)
- [Adgang Microsoft Defender for Endpoint med brugerkontekst](exposed-apis-create-app-nativeapp.md)
