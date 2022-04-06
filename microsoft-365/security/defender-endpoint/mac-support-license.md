---
title: Fejlfinding af licensproblemer for Microsoft Defender for Endpoint på Mac
description: Fejlfinding af licensproblemer i Microsoft Defender for Endpoint på Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, ydeevne
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 35b77183ee9ceb00569c956d30debb0dd61e63f7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471709"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af licensproblemer for Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
 [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Mens du gennemgår en [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md) og Manuel udrulning eller en Koncepttest (PoC), får du muligvis vist følgende fejlmeddelelse:[](mac-install-manually.md)

:::image type="content" source="images/no-license-found.png" alt-text="Licensfejl" lightbox="images/no-license-found.png":::

**Meddelelse:** 

Der blev ikke fundet nogen licens

Det ser ud til, at din organisation ikke har licens til Microsoft 365 Enterprise abonnement.

Kontakt administratoren for at få hjælp.

**Årsag:** 

Du har installeret og/eller installeret Microsoft Defender for Endpoint på macOS-pakken ("Download installationspakke"), men du har muligvis ikke kørt konfigurationsscriptet ("Download onboardingpakke"), eller du har ikke tildelt en licens til brugeren.

Du kan også støde på denne fejl, når Microsoft Defender for Endpoint på macOS-agent ikke er opdateret. 


**Løsning:**

Følg de MicrosoftDefenderATPOnboardingMacOs.py, der er dokumenteret her: [Klientkonfiguration](mac-install-manually.md#client-configuration)

For scenarier, Microsoft Defender for Endpoint på macOS ikke er opdateret, skal du opdatere agenten. 
