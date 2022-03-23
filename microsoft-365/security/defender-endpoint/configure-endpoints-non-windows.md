---
title: Onboard ikke-Windows enheder til Microsoft Defender for Endpoint-tjenesten
description: Konfigurer ikke-Windows enheder, så de kan sende sensordata til Tjenesten Microsoft Defender til Slutpunkt.
keywords: onboard non-Windows-enheder, macos, linux, enhedshåndtering, konfigurer Microsoft Defender til Endpoint-enheder
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
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4573e7002454e9e72648df42352104abaa4c22d6
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592816"
---
# <a name="onboard-non-windows-devices"></a>Onboard ikke-Windows enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platforme**
- macOS
- Linux

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

Defender til Slutpunkt giver en centraliseret sikkerhedsoplevelse til Windows og ikke-Windows platforme. Du vil kunne se beskeder fra forskellige understøttede operativsystemer (OS) i Microsoft 365 Defender og bedre beskytte din organisations netværk.

Du skal kende de nøjagtige Linux-distros og macOS-versioner, der er kompatible med Defender for Endpoint, for at integrationen kan fungere. Du kan finde flere oplysninger under:

- [Systemkrav til Microsoft Defender til Slutpunkt på Linux](microsoft-defender-endpoint-linux.md#system-requirements)
- [Systemkrav for Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Onboarding af ikke-Windows enheder

Du skal følge disse trin for at onboarde enheder, der ikke Windows enheder:

1. Vælg din foretrukne onboardingmetode:

   - For macOS-enheder kan du vælge at onboarde via Microsoft Defender til slutpunkt eller via en tredjepartsløsning. Du kan finde flere oplysninger [i Microsoft Defender til slutpunkt på Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac).

   - Ved andre enheder, Windows enheder, **der ikke er Windows, via tredjepartsintegration**.
    1. I navigationsruden skal du vælge **Partnere og API'er-partnerprogrammer** \> . Sørg for, at tredjepartsløsningen er angivet.
    2. På siden **Partnerprogrammer skal** du vælge den partner, der understøtter dine Windows enheder.
    3. Klik **på** Vis for at åbne partnerens side. Følg vejledningen på siden.
    4. Når du har oprettet en konto eller abonneret på partnerløsningen, bør du gå til et trin, hvor en global lejeradministrator i organisationen bliver bedt om at acceptere en anmodning om tilladelse fra partnerprogrammet. Læs anmodningen om tilladelse omhyggeligt for at sikre, at den er justeret med den tjeneste, du kræver.

2. Kør en registreringstest ved at følge vejledningen i tredjepartsløsningen.

## <a name="offboard-non-windows-devices"></a>Offboard ikke-Windows enheder

For macOS- og Linux-enheder kan du vælge at offboard via Microsoft Defender til slutpunkt. I navigationsruden skal du **vælge Indstillinger** \> **Offboard** \> **Vælg operativsystem for at starte offboarding-processen**.

Du kan også deaktivere ikke-Windows-enheder ved at deaktivere tredjepartsintegrationen. Aktivér dækning for enheder, der Windows-platforme[, ved at integrere tredjepartsløsninger](https://security.microsoft.com/interoperability/partners).

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder](configure-endpoints.md)
- [Onboard-servere](configure-server-endpoints.md)
- [Konfigurere indstillinger for proxy og internetforbindelse](configure-proxy-internet.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender til Slutpunkt](troubleshoot-onboarding.md)
