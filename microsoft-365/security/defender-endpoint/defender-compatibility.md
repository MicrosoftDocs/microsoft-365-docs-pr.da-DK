---
title: Kompatibilitet med antivirusløsning med Defender til Slutpunkt
description: Få mere at vide Windows Defender fungerer sammen med Microsoft Defender for Endpoint. Få også mere at vide om, hvordan Defender til Slutpunkt fungerer, når en tredjeparts antimalwareklient bruges.
keywords: windows defender compatibility, defender, Microsoft Defender for Endpoint, defender for endpoint, antivirus, mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 05/06/2021
ms.technology: mde
ms.openlocfilehash: a8384ed28e8c65871f61241dc522461390106be0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63599287"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>Kompatibilitet med antivirusløsning med Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

Agenten Microsoft Defender til slutpunkt afhænger af din Microsoft Defender Antivirus for nogle funktioner som f.eks. filscanning.

> [!IMPORTANT]
> Defender til Slutpunkt overholder ikke indstillingerne for Microsoft Defender Antivirus udeladelse.

Du skal konfigurere sikkerhedsintelligensopdateringer på Defender til slutpunktsenheder, Microsoft Defender Antivirus er den aktive antimalware eller ej. Få mere at vide under [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md).

Hvis en onboardet enhed er beskyttet af en tredjeparts antimalwareklient, Microsoft Defender Antivirus på dette slutpunkt i passiv tilstand.

Microsoft Defender Antivirus fortsat modtage opdateringer, og processen *mspeng.exe* angivet som en tjeneste, der kører. Men den udfører ikke scanninger og erstatter ikke den kørende tredjeparts antimalwareklient.

Den Microsoft Defender Antivirus grænseflade deaktiveres. Brugere på enheden kan ikke bruge funktioner til Microsoft Defender Antivirus foretage scanninger efter behov eller konfigurere de fleste indstillinger.

Du kan finde flere oplysninger [i emnet Microsoft Defender Antivirus og Defender for Endpoint-kompatibilitet](microsoft-defender-antivirus-compatibility.md).
