---
title: Upload pakken
description: Sådan uploader du dit program, dine binære filer og dine afhængigheder til testbasen
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 9ee299c0972ed4e286e5a660f5082dd5632167e4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934263"
---
# <a name="upload-your-test-base-package-zip"></a>Upload din Test Base-pakke (Zip) 

På siden Test Base-portalen skal du navigere til indstillingen **Upload ny pakke** på navigationslinjen til venstre som vist nedenfor:

:::image type="content" alt-text="Upload en ny pakke." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Når du er der, skal du følge nedenstående trin for at uploade en ny pakke.

## <a name="enter-details-for-your-package"></a>Angiv oplysninger om pakken

Under fanen Testoplysninger skal du skrive pakkens navn, version og andre oplysninger som ønsket.

**Køreklar** og **funktionel test** kan udføres via dette dashboard.

Nedenstående trin indeholder en vejledning i, hvordan du udfylder dine pakkeoplysninger:

1. Angiv det navn, pakken skal have, i feltet `Package name` .

    > [!NOTE]
    > Det angivne pakkenavn og den angivne versionskombination skal være entydig i din organisation. Dette valideres af fluebenet som vist nedenfor.

    - Hvis du vælger at genbruge navnet på en pakke, skal versionsnummeret være entydigt (dvs. det er aldrig blevet brugt med en pakke med det pågældende navn).

    - Hvis kombinationen af pakkenavnet + versionen ikke passerer entydighedskontrollen, får du vist en fejlmeddelelse, hvor der står *"Pakke med denne pakkeversion findes allerede"*.

    :::image type="content" alt-text="Billede til overførsel af pakkeinstruktioner." source="Media/Instructions.png":::

2. Angiv en version i feltet "Pakkeversion".

    :::image type="content" alt-text="Pakkeversion." source="Media/ApplicationVersion.png":::

3. Vælg den testtype, du vil køre på denne pakke.

    En **OOB-test (Out-of-Box)** udfører en *installation*, *start*, *lukning* og *fjernelse* af pakken. Efter installationen gentages startlukningsrutinen 30 gange, før der køres en enkelt fjernelse.

    Denne OOB-test giver dig standardiseret telemetri på din pakke, så du kan sammenligne på tværs af Windows builds.

    En **funktionel test** udfører dine uploadede testscript(r) på pakken. Scriptene køres i overførselssekvensen, og en fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.

    > [!NOTE]
    > **Alle** scripts kører højst i 80 minutter.

4. Vælg opdateringstypen for operativsystemet.

    - 'Sikkerhedsopdateringer' gør det muligt for din pakke at blive testet i forhold til trinvise fald i Windows foreløbige månedlige sikkerhedsopdateringer.
    - 'Funktionsopdateringer' gør det muligt for din pakke at blive testet i forhold til Windows foreløbige toårige funktionsopdateringer builds fra Windows Insider Program.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Opdateringstype for operativsystem." source="Media/OSUpdateType.png":::

5. Vælg operativsystemversionerne til test af sikkerhedsopdatering.

    På rullelisten med flere valg skal du vælge operativsystemversionerne af Windows pakken installeres på.

    - Hvis du kun vil teste pakken i forhold til Windows klientoperativsystemer, skal du vælge de relevante Windows klientoperativsystemer på menulisten.
    - Hvis du kun vil teste pakken i forhold til Windows Server-operativsystemer, skal du vælge de relevante Windows Server OS-versioner på menulisten.
    - Hvis du vil teste pakken i forhold til Windows klient- og Windows serveroperativsystemer, skal du vælge alle relevante operativsystemer på menulisten.

    > [!NOTE]
    > Hvis du vælger at teste pakken mod både server- og klient-OSes, skal du sørge for, at pakken er kompatibel og kan køre på begge OSes

    :::image type="content" alt-text="Valg af en operativsystemversion." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Vælg indstillinger for test af funktionsopdatering:

    - I indstillingen "Vælg insiderkanal" skal du vælge `Windows Insider Program Channel` som det build, som dine pakker skal testes mod.

      Vi bruger i øjeblikket builds, der flightes i Insider Beta Channel.

    - Vælg den Windows os-version, der skal bruges som baseline, når du sammenligner dine testresultater, i indstillingen "Vælg os-baseline for Insight".

    > [!NOTE]
    > Vi understøtter ikke funktionsopdateringstest for server-OSes på nuværende tidspunkt
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Test af funktionsopdatering." source="Media/FeatureUpdate.png":::

7. En side med fuldførte testoplysninger bør se sådan ud:

    :::image type="content" alt-text="Visning af testoplysninger." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Næste trin

Vores næste artikel dækker Upload af dine binære filer til vores tjeneste.

> [!div class="nextstepaction"]
> [Næste trin](binaries.md)

<!---
Add button for next page
-->
