---
title: Microsoft 365 Defender tidszoneindstillinger
description: Brug de oplysninger, der er indeholdt her, Microsoft 365 Defender indstillingerne for tidszone og få vist licensoplysninger.
keywords: indstillinger, Microsoft Defender, cybertrusselsintelligens, Microsoft Defender for Endpoint, tidszone, utc, lokal tid, licens
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
ms.openlocfilehash: adf693bded45dcb44abd8d1e7892e5edc7b65585
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467153"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender tidszoneindstillinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Brug menuen **Tidszone til** at konfigurere tidszonen og få vist licensoplysninger.
:::image type="content" source="images/atp-time-zone.png" alt-text="Tidszoneindstillinger-1" lightbox="images/atp-time-zone.png":::

## <a name="time-zone-settings"></a>Indstillinger for tidszone

Aspekterne af tid er vigtig i forbindelse med vurdering og analyse af opfattede og faktiske cyberangreb.

Cyberforensiske undersøgelser er ofte afhængige af tidsstempler til at sammensætte rækkefølgen af begivenheder. Det er vigtigt, at systemet afspejler de korrekte tidszoneindstillinger.

Microsoft Defender for Endpoint kan vise enten UTC (Coordinated Universal Time) eller lokal tid.

Din aktuelle tidszoneindstilling vises i Microsoft Defender for Endpoint Tidszone. Du kan ændre den viste tidszone i **menuen** Tidszone.

:::image type="content" source="images/atp-time-zone-menu.png" alt-text="Tidszoneindstillinger-2" lightbox="images/atp-time-zone-menu.png":::

### <a name="utc-time-zone"></a>UTC-tidszone

Microsoft Defender for Endpoint bruger UTC-tid som standard.

Når du Microsoft Defender for Endpoint tidszone til UTC, vises alle systemets tidsstempler (beskeder, begivenheder og andre) i UTC for alle brugere. Det kan hjælpe sikkerhedsanalytikere, der arbejder forskellige steder i hele verden, med at bruge de samme tidsstempler, mens de undersøger begivenheder.

### <a name="local-time-zone"></a>Lokal tidszone

Du kan vælge at Microsoft Defender for Endpoint bruge lokale tidszoneindstillinger. Alle beskeder og begivenheder vises ved hjælp af din lokale tidszone.

Den lokale tidszone tages fra enhedens internationale indstillinger. Hvis du ændrer de internationale indstillinger, Microsoft Defender for Endpoint også tidszonen. Hvis du vælger denne indstilling, betyder det, at de tidsstempler, der vises i Microsoft Defender for Endpoint, justeres til lokal tid for alle Microsoft Defender for Endpoint brugere. Analytikere, der er placeret på forskellige globale placeringer, vil nu få vist Microsoft Defender for Endpoint i overensstemmelse med deres internationale indstillinger.

Det kan være nyttigt at vælge at bruge lokal tid, hvis analytikerne er placeret på et enkelt sted. I dette tilfælde kan det være nemmere at korrelere begivenheder til lokal tid, f.eks. når en lokal bruger klikkede på et mistænkeligt maillink.

### <a name="set-the-time-zone"></a>Angive tidszonen

Tidszonen Microsoft Defender for Endpoint som standard indstillet til UTC. Angivelse af tidszone ændrer også tiderne for alle Microsoft Defender for Endpoint visningerne.

Sådan angives tidszonen:

1. Klik på **menuen** Tidszone.
   :::image type="content" source="images/atp-time-zone.png" alt-text="Tidszoneindstillinger-3" lightbox="images/atp-time-zone.png":::
1. Vælg **Tidszone-indikatoren UTC** .
1. Vælg **Tidszone UTC eller** din lokale tidszone, f.eks. -7:00.

### <a name="regional-settings"></a>Internationale indstillinger

Hvis du vil anvende forskellige datoformater til Microsoft Defender for Endpoint, skal du bruge internationale indstillinger for Internet Explorer (IE) Microsoft Edge (Edge). Hvis du bruger en anden browser, f.eks Google Chrome, skal du følge de nødvendige trin for at ændre indstillinger for dato og klokkeslæt for den pågældende browser. 

#### <a name="internet-explorer-ie-and-microsoft-edge"></a>Internet Explorer (IE) og Microsoft Edge

IE og Microsoft Edge bruge **de områdeindstillinger**, der er konfigureret i indstillingen Forur **,** Sprog og Område i Kontrolpanel. 

#### <a name="known-issues-with-regional-formats"></a>Kendte problemer med regionale formater

##### <a name="date-and-time-formats"></a>Dato- og klokkeslætsformater

Der er nogle kendte problemer med formaterne for dato og klokkeslæt. Hvis du konfigurerer dine internationale indstillinger til noget andet end de understøttede formater, afspejler portalen muligvis ikke dine indstillinger korrekt.

Følgende dato- og klokkeslætsformater understøttes:

- Datoformat DD/MM/år-til-år
- Datoformat dd/MM/år-til-år
- Klokkeslætsformat tt:mm:ss (12-timersformat)

Følgende dato- og klokkeslætsformater understøttes ikke i øjeblikket:

- Datoformat yyyy-MM-dd
- Datoformat dd-MMM-yy
- Datoformat dd/MM/år
- Datoformat MM/dd/år
- Datoformat med yy. Viser kun yyyy.
- Klokkeslætsformat HH:mm:ss (24-timersformat)

##### <a name="decimal-symbol-used-in-numbers"></a>Decimalsymbol anvendt i tal

Det anvendte decimalsymbol er altid en prik, også selvom et komma er markeret i indstillingerne **for talformat** i **indstillinger for** område. Eksempelvis vises 15.5K som 15,5K.
