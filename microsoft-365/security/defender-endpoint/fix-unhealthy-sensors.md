---
title: Ret usunde sensorerne i Microsoft Defender til Slutpunkt
description: Ret enhedssensorer, der rapporterer som forkert konfigurerede eller inaktive, så tjenesten modtager data fra enheden.
keywords: forkert konfigureret, inaktiv, rettelse af sensor, sensor sundhed, ingen sensordata, sensordata, forringet kommunikation, kommunikation
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
ms.date: 11/23/2020
ms.technology: mde
ms.openlocfilehash: e801776001b79bf1ae3e6e8a220c5e4c395896db
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63592721"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Ret usunde sensorerne i Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Enheder kan kategoriseres som forkert konfigurerede eller inaktive er markeret med flag til forskellige årsager. I dette afsnit gives nogle forklaringer om, hvad der kunne have forårsaget, at en enhed blev kategoriseret som inaktiv eller forkert konfigureret.

## <a name="inactive-devices"></a>Inaktive enheder

En inaktiv enhed er ikke nødvendigvis markeret med flag på grund af et problem. Følgende handlinger, der er foretaget på en enhed, kan medføre, at en enhed kategoriseres som inaktiv:

### <a name="device-is-not-in-use"></a>Enheden er ikke i brug

Enheder, der ikke er i brug i mere end syv dage, bevarer statussen "Inaktiv" på portalen.

### <a name="device-was-reinstalled-or-renamed"></a>Enheden blev geninstalleret eller omdøbt
Der genereres en ny enhed i Microsoft 365 Defender for geninstallerede eller omdøbte enheder. Den tidligere enhed forbliver med statussen "Inaktiv" på portalen. Hvis du har geninstalleret en enhed og installeret Defender for Endpoint-pakken, skal du søge efter navnet på den nye enhed for at bekræfte, at enheden rapporterer normalt.

### <a name="device-was-offboarded"></a>Enheden blev slukket
Hvis enheden blev slået fra, vises den stadig på listen over enheder. Efter syv dage bør enhedens tilstand blive inaktiv.

### <a name="device-is-not-sending-signals"></a>Enheden sender ikke signaler
Hvis enheden af en eller anden grund ikke sender signaler til nogen Microsoft Defender til slutpunktskanaler i mere end syv dage, kan en enhed betragtes som inaktiv. dette omfatter betingelser, der falder under forkert konfigurerede enheders klassificering.

Forventer du, at en enhed er "Aktiv"-status? [Åbn en supportbillet](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Forkert konfigurerede enheder
Forkert konfigurerede enheder kan klassificeres yderligere til:
- Forringet kommunikation
- Ingen sensordata

### <a name="impaired-communications"></a>Forringet kommunikation
Denne status angiver, at der er begrænset kommunikation mellem enheden og tjenesten.

Følgende foreslåede handlinger kan hjælpe med at løse problemer i forbindelse med en forkert konfigureret enhed med forringet kommunikation:

- [Kontrollér, at enheden har forbindelse til internettet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Microsoft Defender for Endpoint-sensoren kræver Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender til slutpunktstjenesten.

- [Bekræft klientforbindelsen til URL-adresser for Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Kontrollér, at proxykonfigurationen blev gennemført, at WinHTTP kan finde og kommunikere via proxyserveren i dit miljø, og at proxyserveren tillader trafik til URL-adresserne for Microsoft Defender for Endpoint-tjenesten.

Hvis du har taget afhjælpende handlinger, og enhedens status stadig er konfigureret forkert, skal [du åbne en supportanmodning](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Ingen sensordata
En forkert konfigureret enhed med status "Ingen sensordata" har kommunikation med tjenesten, men kan kun rapportere delvise sensordata.

Følg disse handlinger for at rette kendte problemer i forbindelse med en forkert konfigureret enhed med statussen "Ingen sensordata":

- [Kontrollér, at enheden har forbindelse til internettet](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Microsoft Defender for Endpoint-sensoren kræver Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender til slutpunktstjenesten.

- [Bekræft klientforbindelsen til URL-adresser for Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Kontrollér, at proxykonfigurationen blev gennemført, at WinHTTP kan finde og kommunikere via proxyserveren i dit miljø, og at proxyserveren tillader trafik til URL-adresserne for Microsoft Defender for Endpoint-tjenesten.

- [Sørg for, at den diagnostiske datatjeneste er aktiveret](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Hvis enhederne ikke rapporterer korrekt, skal du kontrollere, at den Windows datatjeneste er indstillet til automatisk start. Kontrollér også, Windows diagnostiske datatjeneste kører på slutpunktet.

- [Kontrollér, Microsoft Defender Antivirus ikke er deaktiveret af politikken](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Hvis dine enheder kører en tredjeparts antimalwareklient, kræver Defender til slutpunkt-agent, at Microsoft Defender Antivirus-driveren til tidlig start-antimalware er aktiveret.

Hvis du har taget afhjælpende handlinger, og enhedens status stadig er konfigureret forkert, skal [du åbne en supportanmodning](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Se også
- [Kontrollér sensorens tilstand i Microsoft Defender til slutpunkt](check-sensor-status.md)
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalyse](download-client-analyzer.md)
- [Kør klientanalysen på Windows](run-analyzer-windows.md)
- [Kør klientanalyse på macOS eller Linux](run-analyzer-macos-linux.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)

