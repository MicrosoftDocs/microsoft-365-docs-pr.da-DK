---
title: Ret usunde sensorer i Microsoft Defender for Endpoint
description: Ret sensorer, der rapporterer som forkert konfigurerede eller inaktive, så tjenesten modtager data fra enheden.
keywords: konfigureret forkert, inaktiv, fixsensor, sensortilstand, ingen sensordata, sensordata, nedsat kommunikation, kommunikation
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
ms.openlocfilehash: cc88fa877c0c284555f1702a5fa3190a06e7e47e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490857"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Ret usunde sensorer i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Enheder kan kategoriseres som forkert konfigurerede eller inaktive af forskellige årsager. Dette afsnit indeholder nogle forklaringer af, hvad der kan have forårsaget, at en enhed er kategoriseret som inaktiv eller konfigureret forkert.

## <a name="inactive-devices"></a>Inaktive enheder

En inaktiv enhed er ikke nødvendigvis markeret på grund af et problem. Følgende handlinger, der udføres på en enhed, kan medføre, at en enhed kategoriseres som inaktiv:

- Enheden er ikke i brug
- Enheden blev geninstalleret eller omdøbt
- Enheden blev offboardet
- Enheden sender ikke signaler


### <a name="device-isnt-in-use"></a>Enheden er ikke i brug

Alle enheder, der ikke er i brug i mere end syv dage, bevarer statussen 'Inactive' på portalen.

### <a name="device-was-reinstalled-or-renamed"></a>Enheden blev geninstalleret eller omdøbt
Der genereres et nyt enhed i Microsoft 365 Defender til geninstallerede eller omdøbte enheder. Den forrige enhed forbliver med statussen 'Inactive' på portalen. Hvis du har geninstalleret en enhed og installeret Defender for Endpoint-pakken, skal du søge efter navnet på den nye enhed for at kontrollere, at enheden rapporterer normalt.

### <a name="device-was-offboarded"></a>Enheden blev offboardet
Hvis enheden blev offboardet, vises den stadig på listen over enheder. Efter syv dage skal enhedens tilstandstilstand ændres til inaktiv.

### <a name="device-isnt-sending-signals"></a>Enheden sender ikke signaler
Hvis enheden af en eller anden grund ikke sender nogen signaler til nogen Microsoft Defender for Endpoint kanaler i mere end syv dage, kan en enhed af en eller anden grund betragtes som inaktiv. Dette omfatter betingelser, der falder ind under forkert konfigureret enhedsklassificering.

Forventer du, at en enhed er i status 'Aktiv'? [Åbn en supportanmodning](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Forkert konfigurerede enheder
Forkert konfigurerede enheder kan klassificeres yderligere til:
- Nedsat kommunikation
- Ingen sensordata

### <a name="impaired-communications"></a>Nedsat kommunikation
Denne status angiver, at der er begrænset kommunikation mellem enheden og tjenesten.

Følgende foreslåede handlinger kan hjælpe med at løse problemer, der er relateret til en forkert konfigureret enhed med nedsat kommunikation:

- [Kontrollér, at enheden har internetforbindelse](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Den Microsoft Defender for Endpoint sensor kræver Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender for Endpoint-tjenesten.

- [Bekræft klientforbindelsen til URL-adresser til Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Kontrollér, at proxykonfigurationen er fuldført, at WinHTTP kan finde og kommunikere via proxyserveren i dit miljø, og at proxyserveren tillader trafik til URL-adresserne til Microsoft Defender for Endpoint-tjenesten.

Hvis du har gennemført korrigerende handlinger, og enhedsstatussen stadig er konfigureret forkert, [skal du åbne en supportanmodning](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Ingen sensordata
En forkert konfigureret enhed med statussen 'Ingen sensordata' har kommunikation med tjenesten, men kan kun rapportere delvise sensordata.

Følg disse handlinger for at rette kendte problemer, der er relateret til en forkert konfigureret enhed med statussen 'Ingen sensordata':

- [Kontrollér, at enheden har internetforbindelse](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Den Microsoft Defender for Endpoint sensor kræver Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender for Endpoint-tjenesten.

- [Bekræft klientforbindelsen til URL-adresser til Microsoft Defender for Endpoint-tjenesten](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Kontrollér, at proxykonfigurationen er fuldført, at WinHTTP kan finde og kommunikere via proxyserveren i dit miljø, og at proxyserveren tillader trafik til URL-adresserne til Microsoft Defender for Endpoint-tjenesten.

- [Sørg for, at diagnosticeringsdatatjenesten er aktiveret](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Hvis enhederne ikke rapporterer korrekt, skal du kontrollere, at Windows-diagnosticeringsdatatjenesten er indstillet til at starte automatisk. Kontrollér også, at Windows-diagnosticeringsdatatjenesten kører på slutpunktet.

- [Sørg for, at Microsoft Defender Antivirus ikke er deaktiveret af en politik](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Hvis dine enheder kører en antimalwareklient fra tredjepart, kræver Defender for Endpoint Agent, at MICROSOFT Defender Antivirus ELAM-driveren (Early Launch Antimalware) er aktiveret.

Hvis du har gennemført korrigerende handlinger, og enhedsstatussen stadig er konfigureret forkert, [skal du åbne en supportanmodning](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Se også
- [Kontrollér sensortilstand i Microsoft Defender for Endpoint](check-sensor-status.md)
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalysen](download-client-analyzer.md)
- [Kør klientanalysen på Windows](run-analyzer-windows.md)
- [Kør klientanalysen på macOS eller Linux](run-analyzer-macos-linux.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)

