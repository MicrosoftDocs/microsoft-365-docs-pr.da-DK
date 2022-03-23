---
title: Fejlfinding af integrationsproblemer med SIEM-værktøjet i Microsoft Defender til Slutpunkt
description: Foretag fejlfinding af problemer, der kan opstå, når du bruger SIEM-værktøjer med Microsoft Defender til slutpunkt.
keywords: troubleshoot, siem, client secret, secret
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: b6ed0342183734d9b4feb1c20a6c4059b77e64d6
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63592709"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>Fejlfinding af problemer med integration af SIEM-værktøjer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Du skal muligvis foretage fejlfinding af problemer, mens du trækker registreringer frem i dine SIEM-værktøjer.

Denne side indeholder detaljerede trin til fejlfinding af problemer, der kan opstå.

## <a name="learn-how-to-get-a-new-client-secret"></a>Få mere at vide om, hvordan du får en ny klienthemmelighed

Hvis din klienthemmelighed udløber, eller hvis du har forlagt kopien, da du aktiverede SIEM-værktøjsprogrammet, skal du have en ny hemmelig.

1. Log på [Azure-administrationsportalen](https://portal.azure.com).

2. Vælg **Azure Active Directory**.

3. Vælg din lejer.

4. Klik **på Appregistreringer**. Vælg derefter programmet på listen over programmer.

5. Vælg **Certifikater & Secrets** , Klik på Ny klienthemmelighed, angiv derefter en beskrivelse og angiv varigheden af gyldigheden.

6. Klik på **Gem**. Nøgleværdien vises.

7. Kopiér værdien, og gem den et sikkert sted.

## <a name="error-when-getting-a-refresh-access-token"></a>Fejl, når du får et adgangstoken til opdatering

Hvis du støder på en fejl, når du forsøger at få en opdateringstoken, når du bruger THREAT INTELLIGENCE API- eller SIEM-værktøjerne, skal du tilføje svar-URL for det relevante program i Azure Active Directory.

1. Log på [Azure-administrationsportalen](https://ms.portal.azure.com).

2. Vælg **Azure Active Directory**.

3. Vælg din lejer.

4. Klik **på Appregistreringer**. Vælg derefter programmet på listen over programmer.

5. Tilføj følgende URL-adresse:
   - For EU: `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - For Storbritannien: `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - For USA:  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback`.

6. Klik på **Gem**.

## <a name="error-while-enabling-the-siem-connector-application"></a>Fejl under aktivering af SIEM-forbindelsesprogrammet

Hvis du støder på en fejl, når du forsøger at aktivere SIEM-forbindelsesprogrammet, skal du kontrollere indstillinger for blokering af pop op-indstillinger i din browser. Det blokerer muligvis for, at det nye vindue bliver åbnet, når du aktiverer funktionen.

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshootsiem-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Træk registreringer til dine SIEM-værktøjer](configure-siem.md)

