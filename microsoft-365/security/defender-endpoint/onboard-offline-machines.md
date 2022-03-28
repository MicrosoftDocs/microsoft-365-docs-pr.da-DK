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
ms.openlocfilehash: db219fe7ce39ae59668cedff10f03e931ddba416
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597480"
---
# <a name="onboard-devices-without-internet-access-to-microsoft-defender-for-endpoint"></a>Onboard-enheder uden internetadgang til Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Hvis du vil onboarde enheder uden adgang til internettet, skal du gøre følgende generelle trin:

> [!IMPORTANT] 
> Nedenstående trin gælder kun for enheder, der kører tidligere versioner Windows f.eks.: Windows Server 2016 og tidligere eller Windows 8.1 og tidligere.

> [!NOTE]
> - En OMS-gatewayserver kan ikke bruges som proxy for afbrudte Windows- eller Windows-serverenheder, når den er konfigureret via registreringsdatabasen 'TelemetryProxyServer' eller gruppepolitikobjekt.
> - For Windows eller Windows server – mens du kan bruge TelemetryProxyServer, skal den pege på en standardproxyenhed eller -maskine.
> - Desuden skal Windows eller Windows Server i afbrudte miljøer kunne opdatere lister over certifikattillide offline via en intern fil eller webserver.
> - Du kan finde flere oplysninger om opdatering af [CTL-filer offline under Konfigurere en fil eller webserver til at hente CTL-filerne](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265983(v=ws.11)#configure-a-file-or-web-server-to-download-the-ctl-files).

Du kan finde flere oplysninger om onboardingmetoder i følgende artikler:
- [Onboard tidligere versioner af Windows](/microsoft-365/security/defender-endpoint/onboard-downlevel)
- [Onboard-servere til Microsoft Defender for Endpoint-tjenesten](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2008-r2-sp1--windows-server-2012-r2-and-windows-server-2016)
- [Konfigurere indstillinger for enhedsproxy og internetforbindelse](/microsoft-365/security/defender-endpoint/configure-proxy-internet#configure-the-proxy-server-manually-using-a-registry-based-static-proxy)

## <a name="on-premises-devices"></a>Lokale enheder

- Konfigurer Azure Log Analytics (tidligere kaldet OMS Gateway) til at fungere som proxy eller hub:
  - [Azure Log Analytics-agent](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
  - [Installér og konfigurer Microsoft Overvågningsagent (MANUELT)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) peger på Defender for Endpoint Workspace-&-id

[Onboard tidligere versioner af Windows](onboard-downlevel.md)

- Offlineenheder i det samme netværk af Azure Log Analytics
  - Konfigurer  ÆLDRE til at pege på:
    - Azure Log Analytics IP som proxy
    - Defender til endpoint-arbejdsområdets nøgle & id

## <a name="azure-virtual-machines"></a>Virtuelle Azure-maskiner

- Konfigurer Azure Log Analytics Gateway (tidligere kaldet OMS Gateway) til at fungere som proxy eller hub:
    - [Azure Log Analytics Gateway](/azure/azure-monitor/platform/gateway#download-the-log-analytics-gateway)
    - [Installér og konfigurer Microsoft Overvågningsagent (MANUELT)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) peger på Defender for Endpoint Workspace-&-id
- Offline Azure-VM'er i det samme netværk af OMS-gateway
    - Konfigurere Azure Log Analytics IP som en proxy
    - Azure Log Analytics-arbejdsområdenøgle til &-id
- Microsoft Defender til skyen
    - [Arbejdsområde til logfiler \> for sikkerhedspolitik](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)
    - [Trusselsregistrering \> Gør det muligt for Defender til slutpunkt at få adgang til mine data](/azure/security-center/security-center-wdatp#enable-windows-defender-atp-integration)

    Få mere at vide under [Arbejde med sikkerhedspolitikker](/azure/security-center/tutorial-security-policy).
