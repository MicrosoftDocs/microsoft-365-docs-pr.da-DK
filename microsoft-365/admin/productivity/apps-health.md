---
title: Produktivitetsscore og tilstanden for dine Microsoft 365 apps
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Microsoft 365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
monikerRange: o365-worldwide
search.appverid:
- MET150
- MOE150
description: Detaljer om Microsoft 365 Apps tilstand – teknologi giver produktivitetsscore.
ms.openlocfilehash: a87bd49ace301eeb6f48edc31fba5a02d0386de6
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466366"
---
# <a name="microsoft-365-apps-health--technology-experiences"></a>Microsoft 365 Apps sundhed – teknologioplevelser

Produktivitetsscore giver indsigt i din organisations digitale transformationsrejse gennem brugen af Microsoft 365 og de teknologioplevelser, der understøtter den. Din organisations score afspejler målinger af personer og teknologioplevelser og kan sammenlignes med benchmarks fra organisationer, der ligner dine. Kategorien Apps-tilstand er en del af de målinger, der er omfattet af teknologioplevelser. Du kan få mere at vide ved at se [oversigten over produktivitetsscore](productivity-score.md) og læse [Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

## <a name="why-your-organizations-microsoft-365-apps-health-score-matters"></a>Derfor er tilstandsscoren for din organisations Microsoft 365 apps vigtig

Din organisations produktivitet afhænger af et sundt programmiljø. Enheder, der kører de fleste aktuelle versioner af Microsoft 365 apps på den anbefalede kanal, er mere sikre og hjælper personer i din organisation med at få mest muligt ud af funktionerne i Microsoft 365.

## <a name="how-we-calculate-the-microsoft-365-apps-health-score"></a>Sådan beregner vi tilstandsscoren for Microsoft 365 apps

Vi beregner din tilstandsscore for Microsoft 365 apps ved at måle antallet af enheder på hver opdateringskanal. Vi bestemmer også, om enhederne kører en understøttet version, og den mest aktuelle version af Microsoft 365 apps.

Vi giver en primær indsigt i oplevelsen, der indeholder de vigtigste målepunkter for denne kategori. Derefter bruges en resultatstruktur, der er beskrevet i følgende afsnit, til at beregne din score.

### <a name="primary-insight"></a>Primær indsigt

Den primære indsigt beregnes ud fra enheder, der kører Microsoft 365 Apps på den anbefalede opdaterede kanal.

:::image type="content" source="../../media/appshealth-primary.png" alt-text="Primær visualisering med sigte for Microsoft 365 apps.":::

Oplysninger, der tages i betragtning til dette, omfatter Microsoft 365 appskanal, build og version, der kører på enheden.

1. **Header:**  Viser procentdelen af enheder på anbefalet opdateringskanal
1. **Kroppen:**  Indeholder flere oplysninger om, hvordan kørsel af enhederne på anbefalet opdateringskanal hjælper med at hente de nyeste opdateringer og køre aktuelle versioner på enheder.
1. **Visualisering (aktuel tilstand):**
    - Vandrette streger, hvor de blåfarvede dele repræsenterer procentdelen af enheder, der kører anbefalet opdateret kanal.
    - Fremhæv (tæller/nævner) for den brøk, der bruges til at beregne procentdelen udtrykt i vandrette streger.
    - Peer Benchmark-værdien for enheder, der kører på den anbefalede opdaterede kanal, vises også som en procentdel.

#### <a name="trend-visualization-of-the-primary-insight"></a>Tendensvisualisering af den primære indsigt

I følgende diagram vises antallet af enheder i den anbefalede opdateringskanal i løbet af de sidste 180 dage. Datapunktet i kurvediagrammet er en aggregering af aktivitet for de sidste 28 dage.

:::image type="content" source="../../media/appshealth-primarytrend.png" alt-text="Diagram, der viser tendensen for enheder, der kører en anbefalet opdateringskanal.":::

### <a name="scoring-framework"></a>Resultatstruktur

Tilstandsscoren for Microsoft 365 apps måler, om enheder kører Microsoft 365 apps på den anbefalede kanal og på de nyeste versioner.

## <a name="explore-your-organization-microsoft-365-app-channels-and-versions"></a>Udforsk din organisation Microsoft 365 appkanaler og -versioner

Vi leverer også supplerende oplysninger, der hjælper dig med at få yderligere indsigt i, hvilke kanaler og versioner enheder i din organisation kører i øjeblikket. Disse ekstra målepunkter bidrager ikke til din produktivitetsscore, men kan hjælpe dig med at oprette en handlingsplan for at øge tilstandsscoren for dine Microsoft 365 apps ved at sikre, at enheder kører Microsoft 365 apps på anbefalede kanaler.

### <a name="devices-on-current-channel-and-running-supported-versions"></a>Enheder på den aktuelle kanal og kører understøttede versioner

:::image type="content" source="../../media/devices-current-suppported-channel.png" alt-text="Diagram, der viser antallet af enheder i den aktuelle understøttede kanal.":::

1. **Header:**  Fremhæver procentdelen af enheder på den aktuelle kanal, der kører understøttede versioner af Microsoft 365 Apps
1. **Kroppen:**  Indeholder oplysninger om værdien af enheder, der kører Microsoft 365 apps på den anbefalede kanal.
1. **Visualisering:**  Opdelingen i visualiseringen repræsenterer omfanget af, hvor stor en procentdel af enhederne på de nyeste og understøttede versioner af Microsoft 365 apps på tværs af forskellige kanaler), som følger:
    - **Understøttede versioner:** Den blå linje repræsenterer procentdelen af enheder, der kører på den understøttede version af Microsoft 365 apps.
    - **Seneste udgivelser:** Den blå farvelinje repræsenterer procentdelen af enheder på de seneste udgivelser.
1. **Lær mere:**   Vælg dette link for at få vist Hjælp-indhold.

### <a name="devices-running-latest-and-supported-versions"></a>Enheder, der kører nyeste og understøttede versioner

:::image type="content" source="../../media/device-supported-versions.png" alt-text="Diagram, der viser antallet af enheder, der kører nyeste og understøttede versioner af apps.":::

1. **Header:**  Fremhæver procentdelen af enheder, der kører understøttede versioner, og enheder, der kører de nyeste versioner.
1. **Kroppen:**  Indeholder oplysninger om den værdi, der kører enheder på anbefalede kanaler og understøttede/nyeste versioner.
1. **Visualisering:** Opdelingen i visualiseringen er beregnet til at repræsentere omfanget for at vise, hvor mange enheder der kører understøttede versioner og de nyeste versioner af Microsoft 365 apps):
    - **Understøttede versioner:** Den blå (farvede) del af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af enheder, der kører understøttet version af Microsoft 365 apps.
        - Tæller: Antallet af enheder på understøttede versioner af Microsoft 365 apps inden for de seneste 28 dage
        - Nævner: Antallet af enheder, der bruger Microsoft 365 apps inden for de seneste 28 dage
    - **Seneste versioner:** Tealdelen (farvet) af linjen og brøken (tæller/nævner) på linjen repræsenterer procentdelen af enheder, der kører seneste versioner af Microsoft 365 apps.
        - Tæller: Antallet af enheder i de seneste versioner af Microsoft 365 apps inden for de seneste 28 dage
        - Nævner: Antallet af enheder, der bruger Microsoft 365 apps inden for de seneste 28 dage
1. **Lær mere:**   Vælg dette link for at få vist Hjælp-indhold.

#### <a name="trend-visualization-of-the-devices"></a>Trendvisualisering af enhederne

I dette diagram vises tendenslinjen for de enheder, der kører understøttede versioner og seneste versioner af Microsoft 365 apps i løbet af de sidste 180 dage.

:::image type="content" source="../../media/trendline-devices-supportedversions.png" alt-text="Diagram, der viser, hvor mange enheder der kører understøttede og nyeste versioner af apps over tid.":::

## <a name="devices-in-your-organization"></a>Enheder i din organisation

Dette afsnit hjælper dig med at reagere på de målepunkter, du vil fokusere på, ved at angive relevante oplysninger til alle målepunkterne for Microsoft 365 apps tilstand – teknologioplevelser.

Følgende kolonner vises i tabellen på kanal-/versionsniveau:

- **Kanal**: Aktuel Microsoft 365 apps-kanal på enhederne.
- **Status**: Microsoft 365 apps understøtter enhedernes tilstand baseret på den aktuelle kanal og version.
- **Versioner**: Aktuelle Microsoft 365 appsversioner på enhederne.
- **Antal enheder**: Antal enheder.

## <a name="related-content"></a>Relateret indhold

[Kommunikation – personoplevelser](communication.md) (artikel)\
[Indholdssamarbejde – personoplevelser](content-collaboration.md) (artikel)\
[Møder – personoplevelser](meetings.md) (artikel)\
[Mobilitet – personoplevelser](mobility.md) (artikel)\
[Kontrolelementer til beskyttelse af personlige oplysninger for Produktivitetsscore](privacy.md) (artikel)\
[Teamwork – personoplevelser](teamwork.md) (artikel)