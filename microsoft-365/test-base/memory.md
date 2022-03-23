---
title: Regressionsanalyse af hukommelse
description: Sådan udleder du hukommelsesregression
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
ms.openlocfilehash: c4c6ec61ea96966237976ea71b82931e37efd278
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592269"
---
# <a name="memory-regression-analysis"></a>Regressionsanalyse af hukommelse

Testbase hjælper dig med tydeligere at bemærke betydelige hukommelsesforbrugsstigninger i test-VM'er, der kører dine apps. Målepunkter for ydeevnen, f.eks. hukommelsesforbrug, kan være effektive i den overordnede programstilstand, og vi mener, at denne tilføjelse i høj grad vil hjælpe dig med at sikre, at dine apps fungerer optimalt.

Læs videre for at få flere oplysninger, eller se denne video for at få en hurtig gennemgang af de nyeste forbedringer. 

Du kan finde flere oplysninger om Test Base for M365s mulighed for at hjælpe med regressionsanalyse under Regressionsresultater baseret på procespålidelighed.

<b>Tættere på hukommelsesregressioner</b>

Testbasen til M365-dashboard viser den hukommelse, der forbruges af dit program på en ny foruddefineret Windows-opdatering, og sammenligner den med den hukommelse, der blev brugt i den senest udgivne Windows-opdatering. 

Med denne måneds forbedringer er hukommelsesregressionsanalyse nu fremhævet i dine foretrukne processer. Programmer kan indeholde flere processer, og du kan manuelt vælge dine foretrukne processer via fanen Pålidelighed. Vores tjeneste identificerer derefter hukommelsesregressioner i disse foretrukne processer, mens testen kører på tværs af Windows forskellige opdateringsudgivelser. Hvis der registreres en regression, er det nemt at få oplysninger om regressionen.

Lad os nu se på denne funktion i detaljer og diskutere, hvordan du kan foretage fejlfinding af hukommelsesregressioner ved Windows Ydeevneanalyse.

Fejlsignalet, der skyldes en hukommelsesregression, vises i Test Base for M365-dashboardet på siden Testresultater under Udnyttelse af hukommelse:

![Resultater af hukommelsesudnyttelse.](Media/01_memory-utilization-results.png)


Fejl for programmet på grund af højere hukommelsesforbrug, vises også som ```Fail``` på siden Testoversigt:

![Testoversigtsresultater.](Media/02_test-summary.png)

Ved at levere disse fejlsignaler på forhånd er vores mål tydeligt at markere potentielle problemer, der kan forstyrre og påvirke slutbrugeroplevelsen for dit program. 

Du kan derefter hente logfilerne og bruge Windows Performance Analyzer eller din foretrukne værktøjspakke til at undersøge yderligere. Du kan også samarbejde med Test Base for M365-teamet om at løse problemet og hjælpe med at forhindre problemer, der påvirker slutbrugerne.

Hukommelsessignaler registreres under fanen Hukommelsesudnyttelse i Testbase for M365-tjenesten for alle test-køres. I eksemplet nedenfor vises en testkørsel med onboardingprogrammet "test af hukommelses stress" i forhold til den foreløbige sikkerhedsopdatering for august 2020. (Dette program er skrevet af vores team for at illustrere hukommelsesregressioner).

![Resultater af regression af hukommelse.](Media/03_memory-regression%20comparison.png)

I dette eksempel forbrugte favoritprocesprocessen "USLTestMemoryStress.exe" et gennemsnit på ca. 100 MB i den foreløbige augustopdatering sammenlignet med opdateringen for juli, og derfor identificerede Test Base for M365 en regression. 

De andre processer – der vises her som "USLTestMemoryStress_Aux1.exe" og "USLTestMemoryStress_Aux2.exe", hører også til det samme program, men har brugt cirka den samme mængde hukommelse til de to udgivelser, så de blev "overført", og blev betragtet som sunde.

Regressionen på hovedprocessen blev fastlagt til at være "statistisk signifikant", så tjenesten kommunikerede og fremhævede denne forskel for brugeren. Hvis sammenligningen ikke var statistisk signifikant, blev den ikke fremhævet. Hukommelsesudnyttelse kan være støjende, så vi bruger statistiske modeller til at skelne mellem builds og udgivelser og meningsfulde forskelle fra inkontiventielle forskelle. 

En sammenligning kan sjældent markeres, når der ikke er nogen sand forskel (en falsk positiv), men dette er en nødvendig kompromis for at forbedre sandsynligheden for korrekt identifikation af regressioner (eller sande positive).

Næste trin er at forstå, hvad der forårsagede hukommelsesregressionen. Du kan hente zip-filerne til begge udførelser fra indstillingen Download logfiler, som vist nedenfor. 

Disse zip-filer indeholder resultaterne af testkørslen, herunder scriptresultater og hukommelse og CPU-ydeevnedata, som er inkluderet i ETL-filen.

![Hukommelsesregressions-testfiler.](Media/04_memory-regression-test-files.png)

Du kan downloade og udpakke logfilerne for de to testkørsel og derefter finde ETL-filen i hver mappe og omdøbe dem som target.etl (for testen køre på den foreløbige opdatering) og baseline.etl (for testkørslen ved seneste udgivelsesopdatering) for at forenkle udforskning og navigation.
 
## <a name="next-steps"></a>Næste trin

Gå videre til næste artikel for at komme i gang med at forstå intelligent CPU-regressionsanalyse.
> [!div class="nextstepaction"]
> [Næste trin](cpu.md)

<!---
Add button for next page
-->
