---
title: Fejlfinding af forbindelsesproblemer i skyen til Microsoft Defender til slutpunkt på Linux
ms.reviewer: ''
description: Få mere at vide om fejlfinding af forbindelsesproblemer i skyen for Microsoft Defender til Slutpunkt på Linux
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, cloud, connectivity, communication
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
ms.openlocfilehash: a4c279dff6fa5a5c85a2f65144a301dde75a1615
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591862"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Fejlfinding af forbindelsesproblemer i skyen til Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a>Kør forbindelsestesten

Hvis du vil teste, om Defender til slutpunkt på Linux kan kommunikere til skyen med de aktuelle netværksindstillinger, skal du køre en forbindelsestest fra kommandolinjen:

```bash
mdatp connectivity test
```

forventet output:

```output
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

Hvis [forbindelsestesten mislykkes](microsoft-defender-endpoint-linux.md#network-connections) , skal du kontrollere, om enheden har internetadgang, og om nogle af de slutpunkter, der kræves af produktet, er blokeret af en proxy eller firewall.

Fejl med krøllefejl 35 eller 60 angiver afvisning af certifikatpinning. Kontrollér, om forbindelsen er under SSL- eller HTTPS-inspektion. Hvis det er nødvendigt, skal du føje Microsoft Defender til slutpunktet til listen over tilladte.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a>Fejlfindingstrin for miljøer uden proxy eller med gennemsigtig proxy

Hvis du vil teste, om en forbindelse ikke er blokeret i et miljø uden en proxy eller med en gennemsigtig proxy, skal du køre følgende kommando i terminalen:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Outputtet fra denne kommando skal ligne dette:

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a>Fejlfindingstrin for miljøer med statisk proxy

> [!WARNING]
> PAC, WPAD og godkendte proxyer understøttes ikke. Sørg for, at der kun bruges en statisk proxy eller gennemsigtig proxy.
>
> SSL-inspektion og skærings-proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at gå direkte gennem data fra Defender til Slutpunkt på Linux til de relevante URL-adresser uden skæring. Tilføjelse af dit skæringscertifikat til det globale lager tillader ikke skæring.

Hvis en statisk proxy er påkrævet, skal du føje en proxyparameter til ovenstående kommando, hvor `proxy_address:port` svarer til proxyadressen og port:

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Sørg for at bruge den samme proxyadresse og port, som er konfigureret i `/lib/system/system/mdatp.service` filen. Kontrollér din proxykonfiguration, hvis der er fejl fra ovenstående kommandoer.

Hvis du vil angive proxyen for mdatp, skal du bruge følgende kommando:

```bash
mdatp config proxy set --value http://address:port 
```


Når det lykkes, skal du forsøge en anden forbindelsestest fra kommandolinjen:

```bash
mdatp connectivity test
```

Hvis problemet fortsætter, skal du kontakte kundesupport.

## <a name="resources"></a>Ressourcer

- Du kan finde flere oplysninger om, hvordan du konfigurerer produktet til at bruge en statisk proxy, under Konfigurer [Microsoft Defender til slutpunkt for statisk proxyregistrering](linux-static-proxy-configuration.md).
