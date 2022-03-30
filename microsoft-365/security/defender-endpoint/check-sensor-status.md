---
title: Kontrollér tilstanden for sensoren i Microsoft Defender til slutpunkt
description: Kontrollér sensorens tilstand på enheder for at identificere, hvilke enheder der er konfigureret forkert, inaktive eller ikke rapporterer sensordata.
keywords: sensor, sensor sundhed, forkert konfigureret, inaktiv, ingen sensordata, sensordata, forringet kommunikation, kommunikation
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
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 926e23da7e439aa6035574a13bab2752004dd189
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63599290"
---
# <a name="check-sensor-health-state-in-microsoft-defender-for-endpoint"></a>Kontrollér sensorens tilstand i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

Feltet **Enheder med sensorproblemer** findes på dashboardet Sikkerhedshandlinger. Dette felt indeholder oplysninger om den enkelte enheds mulighed for at levere sensordata og kommunikere med Defender for Endpoint-tjenesten. Den rapporterer, hvor mange enheder der kræver opmærksomhed, og hjælper dig med at identificere problematiske enheder og tage skridt til at rette kendte problemer.

Der er to statusindikatorer på feltet, der indeholder oplysninger om antallet af enheder, der ikke rapporterer korrekt til tjenesten:

- **Forkert konfigureret** – Disse enheder kan delvist rapportere sensordata til tjenesten Defender til slutpunkt og kan have konfigurationsfejl, der skal rettes.
- **Inaktive** – Enheder, der er holdt op med at rapportere til Defender for Endpoint-tjenesten i mere end syv dage i den sidste måned.

Når du klikker på en af grupperne, dirigeres du **til listen Enheder**, der er filtreret efter eget valg.

![Skærmbillede af feltet Enheder med sensorproblemer.](images/atp-devices-with-sensor-issues-tile.png)

På **listen Enheder** kan du filtrere listen over tilstandstilstande ud fra følgende status:

- **Aktiv** – Enheder, der aktivt rapporterer til Defender for Endpoint-tjenesten.
- **Forkert konfigureret –** Disse enheder rapporterer muligvis delvist sensordata til Defender til slutpunktstjenesten, men har konfigurationsfejl, der skal rettes. Forkert konfigurerede enheder kan have enten en eller en kombination af følgende problemer:
  - **Ingen sensordata –** Enheder er holdt op med at sende sensordata. Der kan udløses begrænsede beskeder fra enheden.
  - **Forringet kommunikation** – Muligheden for at kommunikere med enheden er forringet. Det fungerer muligvis ikke at sende filer til dybdegående analyse, blokere filer, isolere enheden fra netværket og andre handlinger, der kræver kommunikation med enheden.
- **Inaktive** – Enheder, der er holdt op med at rapportere til Defender for Endpoint-tjenesten.

Du kan også downloade hele listen i CSV-format ved hjælp af **funktionen** Eksportér. Du kan finde flere oplysninger om filtre [i Få vist og organiser listen Enheder](machines-view-overview.md).

> [!NOTE]
> Eksportér listen i CSV-format for at få vist de ufiltrerede data. CSV-filen indeholder alle enheder i organisationen, uanset hvilken filtrering der anvendes i selve visningen, og kan tage lang tid at downloade, afhængigt af hvor stor din organisation er.

![Skærmbillede af listesiden Enheder.](images/atp-devices-list-page.png)

Du kan få vist oplysninger om enheden, når du klikker på en forkert konfigureret eller inaktiv enhed.

## <a name="see-also"></a>Se også

- [Ret usunde sensorer i Defender til Slutpunkt](fix-unhealthy-sensors.md)
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalyse](download-client-analyzer.md)
- [Kør klientanalysen på Windows](run-analyzer-windows.md)
- [Kør klientanalyse på macOS eller Linux](run-analyzer-macos-linux.md)
- [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)
