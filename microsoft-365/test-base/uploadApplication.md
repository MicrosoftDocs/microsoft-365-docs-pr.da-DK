---
title: Upload din pakke
description: Sådan overfører du dit program, dine binære og afhængigheder til Test base
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
ms.openlocfilehash: 99b25757b3f7b0b3d4fcd43f97bab2ac303de6fa
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/22/2021
ms.locfileid: "63592472"
---
# <a name="step-2-uploading-a-package"></a>Trin 2: Uploade en pakke

På siden Test Base-portal skal du gå **til Upload ny** pakkeindstilling i venstre navigationslinje som vist nedenfor:

:::image type="content" alt-text="Upload en ny pakke." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Når du er der, skal du følge trinnene nedenfor for at uploade en ny pakke.

## <a name="enter-details-for-your-package"></a>Angiv oplysninger om din pakke

På fanen Testdetaljer skal du skrive pakkens navn, version og andre oplysninger, som du har anmodet om.

**Out of Box- og** **Functional-test** kan udføres via dette dashboard.

Nedenstående trin indeholder en vejledning til, hvordan du udfylder dine pakkeoplysninger:

1. Skriv det navn, der skal gives din pakke i `Package name` feltet.

    > [!NOTE]
    > Pakkenavnet og den angivne versionskombination skal være entydig inden for organisationen. Dette valideres af markeringen, sådan som det er vist nedenfor.

    - Hvis du vælger at genbruge en pakkes navn, skal versionsnummeret være entydigt (det vil sige, at den aldrig har været brugt sammen med en pakke, der har det pågældende navn).

    - Hvis kombinationen af pakkenavnet + version ikke består entydighedskontrollen, får du vist en fejlmeddelelse, hvor der står *"Pakke med denne pakkeversion findes allerede"*.

    :::image type="content" alt-text="Billede til overførsel af pakkeinstruktioner." source="Media/Instructions.png":::

2. Angiv en version i feltet "Pakkeversion".

    :::image type="content" alt-text="Pakkeversion." source="Media/ApplicationVersion.png":::

3. Vælg den type test, du vil køre på denne pakke.

    En **OOB-test (Out of Box)** udfører en *installation*, *start*, *lukning* og *fjernelse* af pakken. Efter installationen gentages start-luk-rutinen 30 gange, før en enkelt afinstallation køres.

    Denne OOB-test giver dig standardiseret telemetri på din pakke for at sammenligne på tværs Windows builds.

    En **funktionel test ville** udføre dine uploadede test script(er) på din pakke. Scriptene køres i overførselssekvens, og en fejl i et bestemt script vil stoppe efterfølgende scripts i at blive udført.

    > [!NOTE]
    > **Alle** scripts kører højst i 80 minutter.

4. Vælg opdateringstypen for operativsystemet.

    - "Sikkerhedsopdateringer" gør det muligt at teste pakken mod trinvise skakter af Windows foreløbige månedlige sikkerhedsopdateringer.
    - "Funktionsopdateringer" gør det muligt at teste pakken i forhold til Windows foreløbige, halvårlige funktionsopdateringer fra Windows Insider Program.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Opdateringstype for operativsystem." source="Media/OSUpdateType.png":::

5. Vælg operativsystemets version(er) til sikkerhedsopdateringstest.

    I rullemenuen Vælg flere skal du vælge OS-version(er) Windows din pakke installeres på.

    - Hvis du kun vil teste pakken mod Windows Client-operativsystemer, skal du vælge de Windows versioner af klientoperativsystemet på menulisten.
    - Hvis du kun vil teste pakken mod Windows Server-operativsystemer, skal du vælge de Windows Server OS-versioner på menulisten.
    - Hvis du vil teste pakken mod Windows Client og Windows Server-operativsystemer, skal du markere alle operativsystemer på menulisten.

    > [!NOTE]
    > Hvis du vælger at teste pakken mod både server- og klient-OSes, skal du kontrollere, at pakken er kompatibel og kan køre på begge OSes

    :::image type="content" alt-text="Valg af en version af operativsystemet." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Vælg indstillinger for test af funktionsopdateringer:

    - På indstillingen "Vælg Insider-kanal" skal du vælge `Windows Insider Program Channel` det build, som dine pakker skal testes i forhold til.

      Vi bruger i øjeblikket builds, der er flightet i Insider Beta-kanalen.

    - På indstillingen "Vælg operativsystemets grundlinje for Insight" skal du vælge den Windows OPERATIVSYSTEM-version, der skal bruges som grundlinje til sammenligning af dine testresultater.

    > [!NOTE]
    > Vi understøtteR IKKE funktionsopdateringstest for server-OSes på nuværende tidspunkt
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Test af funktionsopdateringer." source="Media/FeatureUpdate.png":::

7. En udfyldt side med testdetaljer bør se sådan ud:

    :::image type="content" alt-text="Visning af testdetaljer." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Næste trin

Vores næste artikel omhandler Upload af dine binære til vores tjeneste.

> [!div class="nextstepaction"]
> [Næste trin](binaries.md)

<!---
Add button for next page
-->
