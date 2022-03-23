---
title: Fejlfinding af forbindelsesproblemer i skyen til Microsoft Defender til Slutpunkt på macOS
description: I dette emne beskrives det, hvordan du foretager fejlfinding af forbindelsesproblemer i skyen for Microsoft Defender til Endpoint på macOS
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, deploy, uninstallation, intune,propf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 677737f530e35ed52a2a1f3fe7a8d6f18c26e7b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592145"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af forbindelsesproblemer i skyen til Microsoft Defender til Slutpunkt på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Platform** macOS

I dette emne beskrives det, hvordan du foretager fejlfinding af forbindelsesproblemer i skyen for Microsoft Defender til Endpoint på macOS.

## <a name="run-the-connectivity-test"></a>Kør forbindelsestesten
Hvis du vil teste, om Defender til Slutpunkt på Mac kan kommunikere til skyen med de aktuelle netværksindstillinger, skal du køre en forbindelsestest fra kommandolinjen:

```Bash
mdatp connectivity test
```

forventet output:
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

Hvis [forbindelsestesten mislykkes](microsoft-defender-endpoint-mac.md#network-connections) , skal du kontrollere, om enheden har internetadgang, og om nogle af de slutpunkter, der kræves af produktet, er blokeret af en proxy eller firewall.

Fejl med krøllefejl 35 eller 60 angiver afvisning af certifikatpinning, hvilket indikerer et potentielt problem med SSL- eller HTTPS-inspektion. Se instruktionerne nedenfor vedrørende SSL-inspektionskonfiguration.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>Fejlfindingstrin for miljøer uden proxy eller med PAC (Proxy Autoconfig) eller med WPAD (Web Proxy Autodiscovery Protocol)
Brug følgende procedure til at teste, at en forbindelse ikke er blokeret i et miljø uden en proxy eller med PAC (Proxy Autoconfig) eller med WPAD (Web Proxy Autodiscovery Protocol).

Hvis en proxy eller firewall blokerer anonym trafik, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

> [!WARNING]
> Godkendte proxyer understøttes ikke. Sørg for, at der kun bruges PAC, WPAD eller en statisk proxy. SSL-inspektion og skærings-proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at overføre data fra Microsoft Defender til Slutpunkt på macOS direkte til de relevante URL-adresser uden skæring. Tilføjelse af dit skæringscertifikat til det globale lager tillader ikke skæring.
Sådan tester du, om en forbindelse ikke er blokeret: I en browser som f.eks. Microsoft Edge til Mac eller Safari åben https://x.cp.wd.microsoft.com/api/report og https://cdn.x.cp.wd.microsoft.com/ping.

Du kan også køre følgende kommando i Terminal:

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

Outputtet fra denne kommando skal ligne dette:
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
