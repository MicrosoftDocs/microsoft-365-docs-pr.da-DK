---
title: Få adgang til Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Få mere at vide om, hvordan du kan bruge API'er til at automatisere arbejdsprocesser og udvikle baseret på Microsoft Defender til slutpunktsfunktioner
keywords: apis, api, wdatp, open api, microsoft defender for endpoint api, microsoft defender atp, public api, understøttede API'er, beskeder, enhed, bruger, domæne, ip, fil, avanceret jagt, forespørgsel
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
ms.openlocfilehash: a73df39c6d26bdfd44a7f4f629e148e7f0afabb2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591854"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Få adgang til Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender til Slutpunkt fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er gør det muligt at automatisere arbejdsprocesser og udvikle baseret på Defender for Endpoint-funktioner. API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Watch this video for a quick overview of Defender for Endpoint's API'er.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Generelt skal du følge disse trin for at bruge API'er:

- Opret et [AAD program](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Få et adgangstoken ved hjælp af dette program
- Brug tokenet til at få adgang til Defender for Endpoint API

Du kan få adgang til Defender for Endpoint API **med Programkontekst** eller **Brugerkontekst**.

- **Programkontekst: (Anbefalet)**

  Bruges af apps, der kører uden en bruger, der er logget på, til stede. f.eks. apps, der kører som baggrundstjenester eller daemoner.

  Trin, der skal tages for at få adgang til Defender for Endpoint API med programkontekst:

  1. Opret AAD webprogram.
  2. Tildel den ønskede tilladelse til programmet, f.eks. "Læsebeskeder", "Isoler maskiner".
  3. Opret en nøgle til dette program.
  4. Få token ved hjælp af programmet med dets nøgle.
  5. Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

     Du kan få mere at vide [under Få adgang til med programkontekst](exposed-apis-create-app-webapp.md).

- **Brugerkontekst:**

  Bruges til at udføre handlinger i API'en på vegne af en bruger.

  Trin for at få adgang til Defender for Endpoint API med brugerkontekst:

  1. Opret AAD indbygget program.
  2. Tildele programmet den ønskede tilladelse, f.eks. "Læsebeskeder", "Isoler maskiner" osv.
  3. Få token ved hjælp af programmet med brugerlegitimationsoplysninger.
  4. Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

     Du kan finde flere oplysninger [i Få adgang med brugerkontekst](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>Relaterede emner

- [Microsoft Defender til endpoint-API'er](exposed-apis-list.md)
- [Få adgang til Microsoft Defender til slutpunkt med programkontekst](exposed-apis-create-app-webapp.md)
- [Få adgang til Microsoft Defender til slutpunkt med brugerkontekst](exposed-apis-create-app-nativeapp.md)
