---
title: Onboarde enheder uden internetadgang til Microsoft Defender for Endpoint
ms.reviewer: ''
description: Onboarde enheder uden internetadgang, så de kan sende sensordata til den Microsoft Defender for Endpoint sensor
keywords: onboard, servers, vm, on-premises, oms gateway, log analytics, azure log analytics, mma
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 33b539018f479c1b023a656ab056ca892d27e526
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822175"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Onboarde enheder uden internetadgang til Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

For enheder uden direkte internetforbindelse er brugen af en proxyløsning den anbefalede fremgangsmåde. For ældre Windows-enheder, der er onboardet ved hjælp af den tidligere MMA-baserede løsning, giver brugen af OMS-gatewayløsningen en alternativ tilgang. Du kan få flere oplysninger om onboardingmetoder i følgende artikler:
- [Onboard tidligere versioner af Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Onboarder servere til Microsoft Defender for Endpoint-tjenesten](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)

> [!IMPORTANT]
> - Windows eller Windows Server i afbrudte miljøer skal kunne opdatere lister over tillidscertifikater offline via en intern fil eller webserver.
> - Du kan få flere oplysninger om, hvordan du opdaterer CTLs offline, under [Konfigurer en fil eller webserver til at hente CTL-filerne](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

## <a name="devices-running-windows-10-or-later-windows-server-2012-r2-or-later-linux-and-macos"></a>Enheder, der kører Windows 10 eller nyere, Windows Server 2012 R2 eller nyere, Linux og macOS

Afhængigt af operativsystemet kan den proxy, der skal bruges til Microsoft Defender for Endpoint konfigureres automatisk, typisk ved hjælp af autodiscovery eller en fil til automatisk konfiguration eller statisk specifik for Defender for Endpoint-tjenester, der kører på enheden.

- For Windows-enheder skal du se [Konfigurer indstillingerne for enhedsproxy og internetforbindelse](/microsoft-365/security/defender-endpoint/configure-proxy-internet)
- For Linux-enheder skal du se [Konfigurer Microsoft Defender for Endpoint på Linux til registrering af statisk proxy](/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration)
- For macOS-enheder henvises [der til Microsoft Defender for Endpoint på Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac#network-connections)

## <a name="windows-devices-running-the-previous-mma-based-solution"></a>Windows-enheder, der kører den tidligere MMA-baserede løsning

> [!NOTE]
> - En OMS-gatewayserver kan ikke bruges som proxy for frakoblede Windows- eller Windows Server-enheder, når den er konfigureret via registreringsdatabasen 'TelemetryProxyServer' eller GPO.
> - Til Windows eller Windows Server – selvom du kan bruge TelemetryProxyServer, skal den pege på en standardproxyenhed eller -apparat.

- Konfigurer Azure Log Analytics (tidligere kaldet OMS Gateway), så den fungerer som proxy eller hub:
  - [Azure Log Analytics Agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Installér og konfigurer Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) peg på Defender for Endpoint Workspace-nøglen & id

[Onboard tidligere versioner af Windows](onboard-downlevel.md)

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender for Cloud

- Gennemse afsnittet forudsætninger i [Beskyt dine slutpunkter med Defender for Clouds integrerede EDR-løsning: Microsoft Defender for Endpoint](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows#prerequisites)
