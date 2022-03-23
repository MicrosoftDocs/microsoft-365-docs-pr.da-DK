---
title: Fejlfinding af licensproblemer for Microsoft Defender til Endpoint på Mac
description: Fejlfinding af licensproblemer i Microsoft Defender til Slutpunkt på Mac.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, ydeevne
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
ms.openlocfilehash: b0a328ffeee6ee5796cb92f00b8491b257e88a65
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592747"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af licensproblemer for Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md)
 [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Mens du gennemgår [Microsoft Defender til Endpoint på macOS](microsoft-defender-endpoint-mac.md) og Manuel [](mac-install-manually.md) udrulning eller en Koncepttest (PoC), får du muligvis vist følgende fejlmeddelelse:

![Billede af licensfejl.](images/no-license-found.png)

**Meddelelse:** 

Der blev ikke fundet nogen licens

Det ser ud til, at din organisation ikke har licens til Microsoft 365 Enterprise abonnement.

Kontakt administratoren for at få hjælp.

**Årsag:** 

Du har installeret og/eller installeret Microsoft Defender for Endpoint på macOS-pakken ("Download installationspakke"), men du har muligvis ikke kørt konfigurationsscriptet ("Download onboardingpakke"), eller du har ikke tildelt en licens til brugeren.

Du kan også støde på denne fejl, når Microsoft Defender til Endpoint på macOS-agent ikke er opdateret. 


**Løsning:**

Følg de MicrosoftDefenderATPOnboardingMacOs.py, der er dokumenteret her: [Klientkonfiguration](mac-install-manually.md#client-configuration)

For scenarier, hvor Microsoft Defender til slutpunkt på macOS ikke er opdateret, skal du opdatere agenten. 
