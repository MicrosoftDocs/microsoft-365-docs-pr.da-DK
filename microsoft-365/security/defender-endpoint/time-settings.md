---
title: Microsoft 365 Defender tidszoneindstillinger
description: Brug de oplysninger, der er indeholdt her, Microsoft 365 Defender indstillingerne for tidszone og få vist licensoplysninger.
keywords: indstillinger, Microsoft Defender, cybersikkerhedstrusler, Microsoft Defender til slutpunkt, tidszone, utc, lokal tid, licens
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
ms.openlocfilehash: 4353bbfc0ce11c4a767ca599ecb23a1ab4f77a56
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63591250"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender tidszoneindstillinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Brug menuen **Tidszone Ikonet** ![Tidszoneindstillinger1.](images/atp-time-zone.png) for at konfigurere tidszonen og få vist licensoplysninger.

## <a name="time-zone-settings"></a>Indstillinger for tidszone

Aspekterne af tid er vigtig i forbindelse med vurdering og analyse af opfattede og faktiske cyberangreb.

Cyberforensiske undersøgelser er ofte afhængige af tidsstempler til at sammensætte rækkefølgen af begivenheder. Det er vigtigt, at systemet afspejler de korrekte tidszoneindstillinger.

Microsoft Defender til slutpunkt kan vise enten UTC (Coordinated Universal Time) eller lokal tid.

Din aktuelle tidszoneindstilling vises i indstillingerne for Microsoft Defender. Du kan ændre den viste tidszone i menuen **Tidszone** under **Indstillinger > Sikkerhedscenter**.

### <a name="utc-time-zone"></a>UTC-tidszone

Microsoft Defender til slutpunkt bruger UTC-tid som standard.

Når du angiver tidszonen for Microsoft Defender for Slutpunkt til UTC, vises alle systemets tidsstempler (beskeder, begivenheder og andre) i UTC for alle brugere. Det kan hjælpe sikkerhedsanalytikere, der arbejder forskellige steder i hele verden, med at bruge de samme tidsstempler, mens de undersøger begivenheder.

### <a name="local-time-zone"></a>Lokal tidszone

Du kan vælge at få Microsoft Defender til slutpunktet til at bruge lokale tidszoneindstillinger. Alle beskeder og begivenheder vises ved hjælp af din lokale tidszone.

Den lokale tidszone tages fra enhedens internationale indstillinger. Hvis du ændrer de internationale indstillinger, ændres tidszonen for Microsoft Defender til slutpunkt også. Hvis du vælger denne indstilling, betyder det, at de tidsstempler, der vises i Microsoft Defender til slutpunkt, justeres til lokal tid for alle Brugere af Microsoft Defender for slutpunkter. Analytikere, der er placeret på forskellige globale placeringer, vil nu få vist microsoft Defender for Endpoint-beskeder i henhold til deres internationale indstillinger.

Det kan være nyttigt at vælge at bruge lokal tid, hvis analytikerne er placeret på et enkelt sted. I dette tilfælde kan det være nemmere at korrelere begivenheder til lokal tid, f.eks. når en lokal bruger klikkede på et mistænkeligt maillink.

### <a name="set-the-time-zone"></a>Angive tidszonen

Tidszonen Microsoft Defender for Slutpunkt er som standard indstillet til UTC. Angivelse af tidszonen ændrer også klokkeslæt for alle Microsoft Defender for slutpunktsvisninger.

Sådan angives tidszonen:

1. Klik på **Indstillinger** i Microsoft 365 Defender [for](https://security.microsoft.com/) ![tidszoneindstillinger for portal3](images/atp-time-zone.png).
2. Vælg **Sikkerhedscenter**.
3. Vælg **Tidszone,** og angiv tidszonen til enten UTC eller din lokale tidszone.

### <a name="regional-settings"></a>Internationale indstillinger

Hvis du vil anvende forskellige datoformater for Microsoft Defender til slutpunkt, skal du bruge de internationale indstillinger for Internet Explorer (IE) og Microsoft Edge (Edge). Hvis du bruger en anden browser, f.eks Google Chrome, skal du følge de nødvendige trin for at ændre indstillinger for dato og klokkeslæt for den pågældende browser. 

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
