---
title: Upload din pakke
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
ms.openlocfilehash: cd0d463e234c439d8b57576375fd6a91e512f753
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995262"
---
# <a name="upload-your-test-base-package-zip"></a>Upload din Test Base-pakke (Zip) 

På siden Test Base-portalen skal du gå til indstillingen **Ny pakke** på navigationslinjen til venstre og derefter klikke på **Ældre overførselsoplevelse** for at aktivere zip-overførselsoplevelsen som vist nedenfor:

:::image type="content" alt-text="Upload en ny pakke." source="Media/testapplication01.png" lightbox="Media/testapplication01.png":::

:::image type="content" alt-text="Anvend handlingen." source="Media/testapplication21.png" lightbox="Media/testapplication21.png":::

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

    Denne OOB-test giver dig standardiseret telemetri på din pakke, så du kan sammenligne på tværs af Windows-builds.

    En **funktionel test** udfører dine uploadede testscript(r) på pakken. Scriptene køres i overførselssekvensen, og en fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.

    > [!NOTE]
    > **Alle** scripts kører højst i 80 minutter.

4. Vælg opdateringstypen for operativsystemet.

    - 'Sikkerhedsopdateringer' gør det muligt for din pakke at blive testet i forhold til trinvise fald i månedlige sikkerhedsopdateringer, der udgives før udgivelsen af Windows.
    - 'Funktionsopdateringer' gør det muligt for din pakke at blive testet i forhold til de foreløbige Windows-foreløbige funktionsopdateringer fra Windows Insider Program.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Opdateringstype for operativsystem." source="Media/OSUpdateType.png":::

5. Vælg operativsystemversionerne til test af sikkerhedsopdatering.

    Vælg operativsystemversionerne af Windows, som pakken skal installeres på, på rullelisten med flere valg.

    - Hvis du kun vil teste pakken i forhold til Windows-klientoperativsystemer, skal du vælge de relevante versioner af Windows-klientoperativsystemet på menulisten.
    - Hvis du kun vil teste pakken i forhold til Windows Server-operativsystemer, skal du vælge de relevante Windows Server OS-versioner på menulisten.
    - Hvis du vil teste pakken i forhold til Windows-klient- og Windows Server-operativsystemer, skal du vælge alle relevante operativsystemer på menulisten.

    > [!NOTE]
    > Hvis du vælger at teste pakken mod både server- og klient-OSes, skal du sørge for, at pakken er kompatibel og kan køre på begge OSes

    :::image type="content" alt-text="Valg af en operativsystemversion." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Vælg indstillinger for test af funktionsopdatering:

    - I indstillingen "Vælg insiderkanal" skal du vælge `Windows Insider Program Channel` som det build, som dine pakker skal testes mod.

      Vi bruger i øjeblikket builds, der flightes i Insider Beta Channel.

    - I indstillingen "Vælg OS baseline for Insight" skal du vælge den Windows OS-version, der skal bruges som baseline, når du sammenligner dine testresultater.

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
