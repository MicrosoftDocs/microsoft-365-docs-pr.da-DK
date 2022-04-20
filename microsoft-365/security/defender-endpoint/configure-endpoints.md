---
title: Onboardingværktøjer og -metoder til Windows enheder
description: Onboarde Windows enheder, så de kan sende sensordata til den Microsoft Defender for Endpoint sensor
keywords: Onboarde Windows enheder, gruppepolitik, administration af slutpunktkonfiguration, administration af mobilenheder, lokalt script, gp, sccm, mdm, intune
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fbc5a0981a6318d767252e968e45874d889aee85
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949095"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Onboardingværktøjer og -metoder til Windows enheder i Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Forebyggelse af datatab for slutpunkt (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Styring af insider-risiko](/microsoft-365/compliance/insider-risk-management)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Enheder i din organisation skal være konfigureret, så Defender for Endpoint-tjenesten kan hente sensordata fra dem. Der er forskellige metoder og installationsværktøjer, som du kan bruge til at konfigurere enhederne i din organisation.

Generelt skal du identificere den Windows enhed, du onboarder, og derefter følge det tilsvarende værktøj, der passer til enheden eller dit miljø.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="Onboardingværktøjer og -metoder" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>Onboardingværktøjer til slutpunkter

Afhængigt af det Windows slutpunkt, du vil onboarde, skal du bruge det tilsvarende værktøj eller den tilsvarende metode, der er beskrevet i følgende tabel.

Windows enhed | Onboardingværktøj eller -metode
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 og 2019 og 2022</li> <li>Windows Server 2012 R2 og 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Lokalt script (op til 10 enheder)](configure-endpoints-script.md)<br>   [Gruppepolitik](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/mobil Enhedshåndtering (Intune)](configure-endpoints-mdm.md)<br>    [VDI-scripts](configure-endpoints-vdi.md) <br><br> **BEMÆRK**! Et lokalt script er velegnet til blåstempling, men bør ikke bruges til produktionsinstallation. I forbindelse med en produktionsinstallation anbefaler vi, at du bruger Gruppepolitik, Microsoft Endpoint Configuration Manager eller Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft-overvågningsagent (MMA)](onboard-downlevel.md) <br>[Onboarde tidligere versioner af Windows](onboard-downlevel.md) eller [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **BEMÆRK**! Microsoft Monitoring Agent er nu Azure Log Analytics-agent. Du kan få mere at vide under [Oversigt over Log Analytics-agent](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft-overvågningsagent (MMA)](onboard-downlevel.md) <br><br> **BEMÆRK**! Microsoft Monitoring Agent er nu Azure Log Analytics-agent. Du kan få mere at vide under [Oversigt over Log Analytics-agent](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Onboard Windows servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>For at være berettiget til at købe Microsoft Defender for Endpoint Server SKU skal du allerede have købt et kombineret minimum af følgende, Windows E5/A5, Microsoft 365 E5/A5 eller Microsoft 365 E5 Sikkerhed abonnementslicenser.  Du kan få flere oplysninger om licenser under [Produktvilkår](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Emne|Beskrivelse
:---|:---
[Onboarde enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)|Brug Gruppepolitik til at installere konfigurationspakken på enheder.
[Onboarde enheder ved hjælp af Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Du kan bruge enten Microsoft Endpoint Manager (aktuel forgrening) version 1606 eller Microsoft Endpoint Manager (aktuel forgrening) version 1602 eller tidligere til at installere konfigurationspakken på enheder.
[Onboarde enheder ved hjælp af værktøjer til Enhedshåndtering mobilenheder](configure-endpoints-mdm.md)|Brug værktøjer til Enhedshåndtering mobilenheder eller Microsoft Intune til at installere konfigurationspakken på enheden.
[Onboarde enheder ved hjælp af et lokalt script](configure-endpoints-script.md)|Få mere at vide om, hvordan du bruger det lokale script til at installere konfigurationspakken på slutpunkter.
[Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)|Få mere at vide om, hvordan du bruger konfigurationspakken til at konfigurere VDI-enheder.

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at en enhed er onboardet korrekt til tjenesten. Du kan finde flere oplysninger under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).
