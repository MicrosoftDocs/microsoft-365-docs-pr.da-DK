---
title: Onboard-enheder uden internetadgang til Microsoft Defender til Slutpunkt
ms.reviewer: ''
description: Onboard-enheder uden internetadgang, så de kan sende sensordata til Microsoft Defender til slutpunkts sensoren
keywords: onboard, servers, VM, on-premises, oms gateway, log analytics, azure log analytics,  gateway
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
ms.openlocfilehash: 83f0f53e2d2376975f853d826531e749732416b7
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754315"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Onboard-enheder uden internetadgang til Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Hvis du vil onboarde enheder uden adgang til internettet, skal du gøre følgende generelle trin:

> [!IMPORTANT] 
> Følgende trin gælder kun for enheder, der kører tidligere versioner af Windows der bruger den  VERSIONS-baserede løsning. Få mere at vide under [Onboard Windows-servere til Microsoft Defender for Endpoint-tjenesten](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

> [!NOTE]
> - En OMS-gatewayserver kan ikke bruges som proxy for afbrudte Windows- eller Windows-serverenheder, når den er konfigureret via registreringsdatabasen 'TelemetryProxyServer' eller gruppepolitikobjekt.
> - For Windows eller Windows server – mens du kan bruge TelemetryProxyServer, skal den pege på en standardproxyenhed eller -maskine.
> - Desuden skal Windows eller Windows Server i afbrudte miljøer kunne opdatere lister over certifikattillide offline via en intern fil eller webserver.
> - Du kan finde flere oplysninger om opdatering af [CTL-filer offline under Konfigurere en fil eller webserver til at hente CTL-filerne](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

Du kan finde flere oplysninger om onboardingmetoder i følgende artikler:
- [Onboard tidligere versioner af Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Onboard-servere til Microsoft Defender for Endpoint-tjenesten](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [Konfigurere indstillinger for enhedsproxy og internetforbindelse](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="devices-running-the-previous-mma-based-solution"></a>Enheder, der kører den forrige  ÆLDRE-baserede løsning

- Konfigurer Azure Log Analytics (tidligere kaldet OMS Gateway) til at fungere som proxy eller hub:
  - [Azure Log Analytics-agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Installér og konfigurer Microsoft Overvågningsagent (MANUELT)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) peger på Defender for Endpoint Workspace-&-id

[Onboard tidligere versioner af Windows](onboard-downlevel.md)

- Offlineenheder i det samme netværk af Azure Log Analytics
  - Konfigurer  ÆLDRE til at pege på:
    - Azure Log Analytics IP som proxy
    - Defender til endpoint-arbejdsområdets nøgle & id

### <a name="azure-virtual-machines"></a>Virtuelle Azure-maskiner

- For enheder, der kører den forrige,  ÆLDRE-baserede løsning, skal du konfigurere Azure Log Analytics Gateway (tidligere kaldet OMS Gateway) til at fungere som proxy eller hub:
    - [Azure Log Analytics Gateway](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Installér og konfigurer Microsoft Overvågningsagent (MANUELT)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) peger på Defender for Endpoint Workspace-&-id
- Offline Azure-VM'er i det samme netværk af OMS-gateway
    - Konfigurere Azure Log Analytics IP som en proxy
    - Azure Log Analytics-arbejdsområdenøgle til &-id
- Microsoft Defender til skyen
    - [Arbejdsområde til logfiler \> for sikkerhedspolitik](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Trusselsregistrering \> Gør det muligt for Defender til slutpunkt at få adgang til mine data](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Få mere at vide under [Arbejde med sikkerhedspolitikker](/azure/security-center/tutorial-security-policy).
