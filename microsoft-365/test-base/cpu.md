---
title: Regressionsanalyse for CPU
description: Forstå regressionsresultater og målepunkter for CPU-forbrug
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 935781e929c159918f8a0aec3b4a551ab974480f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593925"
---
# <a name="intelligent-cpu-regression-analysis"></a>Intelligent CPU-regressionsanalyse

CPU-udnyttelse kan angive, om et program påvirkes af en opdatering af operativsystemet. 

Testbase til Microsoft 365 giver softwareudviklere indsigt i REGREssioner af CPU-ydeevnen, der opstår, når deres program kører på forskellige versioner af en kommende opdatering til Windows-operativsystemet (OS). 

Disse CPU-regressioner gør det muligt for udviklere at registrere og løse programproblemer (og potentielle fejl), før operativsystemets opdatering implementeres bredt, hvilket forhindrer en dårlig oplevelse for slutbrugeren.


### <a name="how-cpu-regression-analysis-works"></a>Sådan fungerer CPU-regressionsanalyse ###

Som Test Base-bruger kan du uploade dit programs binære (i en enkelt .zip-fil) sammen med tilknyttede testscripts og vælge den Windows OS-version, som du vil teste dit program på Test Base-portalen på Azure i. 

Tjenesten Testbase kører derefter testscriptene og udfører **CPU-regressionsanalysen**. 

Tjenesten kontrollerer, om CPU-anvendelsen for programmet på den foreløbige version af opdateringen til destinationsoperativsystemet er i overensstemmelse med CPU-anvendelsen for den frigivne version af operativsystemet. 

CPU-udnyttelse er ikke en 100 % like-for-like-sammenligning, fordi de processer, der kører på de to versioner af operativsystemet, muligvis eller ikke er et nøjagtigt match på grund af forskellige os-versioner; Men den analyse, der udføres af Test Base, kan vise dig, om ANVENDELSEN AF CPU'en til dit program er påvirket af en kommende opdatering af operativsystemet, og specifikt hvilke processer der har regregeret fra tidligere test.

I det nedenstående øjebliksbillede er der to os-udgivelser, som CPU-udnyttelse sammenlignes med for det samme program. 
-   Fanen CPU-udnyttelse viser de øvre og nedre grænser for anvendelsen for begge udgivelser ved henholdsvis 90. og 10. fraktil. 
-   Graferne viser tidsserien for CPU-udnyttelse sammen med den gennemsnitlige udnyttelse. 

Kunder kan nu bruge funktionen til at afgøre, om deres programs CPU-udnyttelse påvirkes af OS-opdateringer og specifikt hvilke processer, der er regregeret fra deres tidligere udførelse.


![Regressionsanalyse for CPU.](Media/cpu-regression-analysis.jpg)

### <a name="relevant-process-identification"></a>Relevant procesidentifikation ###

Her beskriver vi, hvordan man identificerer regresserede processer i programmet. 

Analyse af ydeevneregression kræver sporing af forskellige typer ydeevnetællere for hver proces, der kører på en virtuel maskine under testkørslen. 

En sådan analyse registrerer en masse variabler for en masse processer for et givet program. Ikke alle processer er knyttet til en kørsel eller et program. For at løse denne udfordring anvendes en algoritme til rangering af fælles oplysninger ved hjælp af sandsynlighed og informationsori for at finde ud af, hvilke processer der er mest relevante for et givet program. 

Et program kan betragtes som én type diskret tilfældig variabel, mens en proces betragtes som en anden type diskret tilfældig variabel. Tilknytningen af de to tilfældige variabler måles ved hjælp af betingede sandsynligheder for relevans. 

Processer vises derefter i rækkefølge efter deres relevans for hvert program. Du kan også angive, at et undersæt af processer, der kan overvåges, vises som standard sammen med de relevante processer til regressionsanalyse af CPU'en. Når der registreres en regression, kan du hente værktøjspakken til Ydeevneanalyse i Windows og analysere årsager til regressioner af CPU-ydeevnen. 

Windows Performance Analyzer tager hændelsessporingsloggen (ETL), som input, og disse .etl-filer er tilgængelige i de logfiler, der kan downloades, og test kan køres på portalen. Hvis du gerne vil vide mere om fejlfinding af CPU-ydeevnen, skal du se dokumentationen til Windows Performance Analyzer.

