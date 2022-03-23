---
title: Onboardingværktøjer og metoder til Windows-enheder
description: Onboard Windows-enheder, så de kan sende sensordata til Microsoft Defender for Endpoint-sensoren
keywords: Onboard Windows-enheder, gruppepolitik, slutpunktskonfigurationsstyring, administration af mobilenheder, lokalt script, gp, sccm, mdm, intune
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
ms.openlocfilehash: c4b70bfa9875d1e8c09d21e9435d8b4200555b5c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592950"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Onboardingværktøjer og metoder til Windows enheder i Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 Insider-risikostyring](/microsoft-365/compliance/insider-risk-management)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Enheder i din organisation skal konfigureres, så Defender for Endpoint-tjenesten kan hente sensordata fra dem. Der er forskellige metoder og installationsværktøjer, du kan bruge til at konfigurere enhederne i organisationen.

Generelt skal du identificere den enhed Windows onboardingenhed, og derefter følge det tilsvarende værktøj, der passer til enheden eller dit miljø.

![Billede af onboardingværktøjer og -metoder](images/onboarding-config-tools.png)

## <a name="endpoint-onboarding-tools"></a>Startværktøjer til slutpunkter

Afhængigt af Windows slutpunkt, du vil onboarde, skal du bruge det tilsvarende værktøj eller den tilsvarende metode, der er beskrevet i følgende tabel.

Windows enhed | Onboardingværktøj eller -metode
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 og 2019 og 2022</li> <li>Windows Server 2012 R2 og 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Lokalt script (op til 10 enheder)](configure-endpoints-script.md)<br>   [Gruppepolitik](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/administration af mobilenheder (Intune)](configure-endpoints-mdm.md)<br>    [VDI-scripts](configure-endpoints-vdi.md) <br><br> **BEMÆRK**: Et lokalt script er egnet til en koncept proof of concept, men bør ikke bruges til produktionsinstallation. Til en produktionsinstallation anbefaler vi, at du Gruppepolitik, Microsoft Endpoint Configuration Manager eller Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Overvågningsagent (ÆLDRE)](onboard-downlevel.md) <br>[Onboard tidligere versioner af Windows](onboard-downlevel.md) eller [Microsoft Defender til Cloud](/azure/security-center/security-center-wdatp) <br><br> **BEMÆRK**! Microsoft Overvågningsagent er nu agent for Azure Log Analytics. Du kan få mere at vide [under Oversigt over loganalyseagent.](/azure/azure-monitor/platform/log-analytics-agent)  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1-Pro </li> <li>  Windows 8.1 Pro </li> <li> Windows 8.1 Enterprise</li></ul>  | [Microsoft Overvågningsagent (ÆLDRE)](onboard-downlevel.md) <br><br> **BEMÆRK**! Microsoft Overvågningsagent er nu agent for Azure Log Analytics. Du kan få mere at vide [under Oversigt over loganalyseagent.](/azure/azure-monitor/platform/log-analytics-agent)

(<a id="fn1">1</a>) Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne [i Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>For at være berettiget til at købe Microsoft Defender til Endpoint Server SKU skal du allerede have købt et kombineret minimum af et af følgende, Windows E5/A5, Microsoft 365 E5/A5- eller Microsoft 365 E5 Sikkerhed-abonnementslicenser.  Du kan finde flere oplysninger om licenser i [produktvilkårene](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Emne|Beskrivelse
:---|:---
[Onboard-enheder med Gruppepolitik](configure-endpoints-gp.md)|Brug Gruppepolitik til at installere konfigurationspakken på enheder.
[Onboard-enheder, der bruger Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Du kan enten bruge Microsoft Endpoint Manager (aktuel forgrening) version 1606 eller Microsoft Endpoint Manager (aktuel forgrening) version 1602 eller tidligere til at installere konfigurationspakken på enheder.
[Onboard-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)|Brug værktøjer til administration af mobilenheder Microsoft Intune til at installere konfigurationspakken på enheden.
[Onboard-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)|Lær at bruge det lokale script til at installere konfigurationspakken på slutpunkter.
[Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)|Få mere at vide om, hvordan du bruger konfigurationspakken til at konfigurere VDI-enheder.

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](run-detection-test.md).
