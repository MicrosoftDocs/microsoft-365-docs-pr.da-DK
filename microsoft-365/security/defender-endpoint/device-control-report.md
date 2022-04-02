---
title: Beskyt din organisations data med enhedsstyring
description: Overvåg organisationens datasikkerhed via rapporter om enhedsstyring.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8a31ce05ed6986159d9f6e4c489e6f7707cfecc4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465283"
---
# <a name="device-control-report"></a>Rapport over enhedsstyring

**Gælder for:** 
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint beskytter mod datatab ved at overvåge og kontrollere mediebrug af enheder i organisationen, f.eks. brug af flytbare lagringsenheder og USB-drev.

Med enhedsstyringsrapporten kan du få vist hændelser, der er relateret til medieforbrug, f.eks.:

- **Overvågningshændelser:** Viser antallet af overvågningshændelser, der sker, når eksterne medier er tilsluttet.
- **Politikhændelser:** Viser antallet af politikhændelser, der sker, når en politik for enhedsstyring udløses.

> [!NOTE]
> Overvågningshændelsen til at spore medieforbrug er aktiveret som standard for enheder, der er onboardet Microsoft Defender for Endpoint.

## <a name="understanding-the-audit-events"></a>Forstå overvågningshændelser

Overvågningshændelser omfatter:

- **USB-drevholder og -unmount:** Overvågningshændelser, der genereres, når et USB-drev ermonteret eller ikke-tilsluttet.
- **PnP:** Plug and Play overvågningshændelser genereres, når flytbart lager, en printer eller Bluetooth medie er tilsluttet.
- **Kontrol af flytbare lageradgang:** Hændelser genereres, når der udløses en kontrolpolitik for flytbar lageradgang. Det kan være Overvågning, Bloker eller Tillad.

## <a name="monitor-device-control-security"></a>Overvåg sikkerhed for enhedsstyring

Enhedsstyring i Microsoft Defender for Endpoint giver sikkerhedsadministratorer værktøjer, der gør det muligt for dem at spore deres organisations enhedsstyringssikkerhed via rapporter. Du kan finde rapporten om enhedsstyring i Microsoft 365 Defender ved at gå til **Rapporter > Enhedsbeskyttelse**.

Kortet Enhedsbeskyttelse på dashboardet **Rapporter** viser antallet af overvågningshændelser, der er genereret af medietype i løbet af de seneste 180 dage.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](https://user-images.githubusercontent.com/81826151/138504137-e9a7673e-e988-48cd-820d-2625ec6df352.png)

Knappen **Vis detaljer** viser flere medieforbrugsdata på siden **til rapport om enhedsstyring** .

Siden indeholder et dashboard med samlet antal hændelser pr. type og en liste over begivenheder. Administratorer kan filtrere efter tidsinterval, medieklassenavn og enheds-id.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Siden med oplysninger om enhedsstyringsrapport i Microsoft 365 Defender portal" lightbox="images/Detaileddevicecontrolreport.png":::

Når du vælger en begivenhed, vises der et pop op-vindue, der viser dig flere oplysninger:

- **Generelle oplysninger:** Dato, Handlingstilstand, politikken og Access for denne hændelse.
- **Medieoplysninger:** Medieoplysninger omfatter Medienavn, Klassenavn, Klasse-GUID, Enheds-id, Leverandør-id, Serienummer og Bustype.
- **Oplysninger om placering:** Enhedsnavn, bruger- og MDATP-enheds-id.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Siden Filter på enhedskontrolrapport" lightbox="images/devicecontrolreportfilter.png":::

Hvis du vil se aktivitet i realtid for disse medier i hele organisationen, skal du vælge **knappen Åbn avanceret jagt** . Dette omfatter en integreret, foruddefineret forespørgsel.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Siden Forespørgsel på enhedskontrolrapport" lightbox="images/Devicecontrolreportquery.png":::

Hvis du vil se enhedens sikkerhed, skal du **vælge knappen Åbn enhed side** i pop op-pop-op-dialogboksen. Denne knap åbner enhedsenhedssiden.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Enhedsenhedssiden" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Rapportering af forsinkelser

Rapporten enhedsstyring kan have en 12-timers forsinkelse fra det tidspunkt, hvor en medieforbindelse oprettes, til det tidspunkt, hvor hændelsen afspejles på kortet eller på listen over domæner.
