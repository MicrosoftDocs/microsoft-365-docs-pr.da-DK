---
title: Beskyt din organisations data med enhedsstyring
description: Overvåg din organisations datasikkerhed via enhedskontrolrapporter.
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
ms.openlocfilehash: 6fe93be2ec244628f2bf2195eb453307235ea06f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129179"
---
# <a name="device-control-report"></a>Rapport over enhedskontrol

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint enhedskontrol beskytter mod tab af data ved at overvåge og styre medier, der bruges af enheder i din organisation, f.eks. brug af flytbare lagerenheder og USB-drev.

Med rapporten over enhedskontrol kan du få vist hændelser, der er relateret til medieforbrug. Sådanne hændelser omfatter:

- **Overvågningshændelser:** Viser antallet af overvågningshændelser, der opstår, når der er forbindelse til eksterne medier.
- **Politikhændelser:** Viser antallet af politikhændelser, der opstår, når en politik for enhedskontrol udløses.

> [!NOTE]
> Overvågningshændelsen til sporing af medieforbrug er som standard aktiveret for enheder, der er onboardet til Microsoft Defender for Endpoint.

## <a name="understanding-the-audit-events"></a>Om overvågningshændelserne

Overvågningshændelserne omfatter:

- **Tilslutning og afmontering af USB-drev:** Overvågningshændelser, der genereres, når et USB-drev er tilsluttet eller ikke er tilsluttet.
- **PnP:** Plug and Play overvågningshændelser genereres, når der er tilsluttet et flytbart lager, en printer eller Bluetooth medie.
- **Adgangskontrol til flytbart lager:** Hændelser genereres, når en politik for adgangskontrol til flytbare lagermedier udløses. Det kan være Overvågning, Bloker eller Tillad.

## <a name="monitor-device-control-security"></a>Overvåg sikkerhed for enhedskontrol

Enhedskontrol i Defender for Endpoint giver sikkerhedsadministratorer værktøjer, der gør det muligt for dem at spore deres organisations enhedskontrolsikkerhed via rapporter. Du kan finde rapporten over enhedskontrol på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Gå til Rapporten **Generel** > **sikkerhed** for **rapporter** > . Find **enhedens kontrolkort** , og vælg linket for at åbne rapporten. 

Kortet Enhedsbeskyttelse på dashboardet **Rapporter** viser antallet af overvågningshændelser, der er genereret af medietypen, i løbet af de sidste 180 dage.

Knappen **Vis detaljer** viser flere data om medieforbrug på **rapportsiden for enhedskontrol** .

Siden indeholder et dashboard med et samlet antal hændelser pr. type og en liste over hændelser og viser 500 hændelser pr. side, men administratorer kan rulle ned for at se flere hændelser og kan filtrere efter tidsinterval, medieklassenavn og enheds-id.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="Siden Detaljer om rapport for enhedskontrol på portalen Microsoft 365 Defender" lightbox="images/Detaileddevicecontrolreport.png":::

Når du vælger en hændelse, vises der et pop op-vindue, der viser flere oplysninger:

- **Generelle oplysninger:** Dato, Handlingstilstand, politikken og Adgang for denne hændelse.
- **Medieoplysninger:** Medieoplysninger omfatter Medienavn, Klassenavn, Klasse-GUID, Enheds-id, Leverandør-id, Serienummer og Bustype.
- **Oplysninger om placering:** Enhedsnavn, Bruger og MDATP-enheds-id.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="Rapportsiden Filtrer på enhedskontrol" lightbox="images/devicecontrolreportfilter.png":::

Hvis du vil se aktivitet i realtid for dette medie på tværs af organisationen, skal du vælge knappen **Åbn avanceret jagt** . Dette omfatter en integreret, foruddefineret forespørgsel.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="Rapportsiden Forespørgsel på enhedskontrol" lightbox="images/Devicecontrolreportquery.png":::

Hvis du vil se sikkerheden for enheden, skal du vælge knappen **Åbn enhedside** på pop op-vinduet. Denne knap åbner enhedens enhedsside.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="Enhedsenhedssiden" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>Rapporteringsforsinkelser

Der kan være en forsinkelse på op til 12 timer fra det tidspunkt, hvor en medieforbindelse indtræffer, til hændelsen afspejles på kortet eller på domænelisten.
