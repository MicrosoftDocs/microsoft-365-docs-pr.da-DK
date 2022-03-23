---
title: Undersøg og svar med Microsoft 365 Defender
description: Undersøg og svar på hændelser, der har de samme Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsessvar, cyberangreb
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-incidentresponse
- m365solution-scenario
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c54d2989941d5c91cc2626941af36cf6cdf205ce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593626"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Undersøg og svar med Microsoft 365 Defender

Her er de primære undersøgelses- og svaropgaver for Microsoft 365 Defender:

- [Svar på hændelser](#incident-response)
- [Gennemse og godkende automatiske afhjælpningshandlinger](#automated-investigation-and-remediation)
- [Søge efter kendte trusler i dine data](#proactive-search-for-threats-with-advanced-hunting)
- [Forstå de seneste cyberangreb](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Få hjælp](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Hændelsessvar

Microsoft 365 og apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Men angreb anvender typisk forskellige teknikker mod forskellige typer enheder, f.eks enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer. Da det kan være udfordrende og tidskrævende at sammenlægge de enkelte beskeder for at få indsigt i et angreb, samler Microsoft 365 Defender automatisk beskederne og deres tilknyttede oplysninger i en hændelse.

Du skal løbende identificere de hændelser, der har højeste prioritet, til analyse og løsning i hændelseskøen og gøre dem klar til svar. Dette er en kombination af:

- [Prioritering af fastlæggelse](incident-queue.md) af hændelser med højeste prioritet gennem filtrering og sortering af hændelseskøen. Dette kaldes også for triaging.
- [Administrer](manage-incidents.md) hændelser ved at ændre deres titel, tildele dem til en analytiker, tilføje mærker og kommentarer, og når de løses, klassificere dem.

For hver hændelse skal du bruge arbejdsprocessen for hændelsesrespons til at analysere hændelsen og dens beskeder og data, så den kan indeholde angrebene, komme ud for truslerne, komme tilbage efter angrebene og lære af den. Se [eksemplet](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) for Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

Hvis din organisation bruger en Microsoft 365 Defender, modtager dit sikkerhedsteam en besked i Microsoft 365 Defender-portalen, når der registreres skadelig eller mistænkelig aktivitet eller artefakt. I lyset af den konstante strøm af trusler, der kan komme ind, står sikkerhedsteams ofte over for udfordringen med at tage hånd om den store mængde vigtige beskeder. Heldigvis omfatter Microsoft 365 Defender automatiseret undersøgelse og svarmuligheder (AIR), som kan hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt.

Når en automatiseret undersøgelse er afsluttet, opnås der en konklusion for hvert enkelt bevis på en hændelse. Afhængigt af konklusionen identificeres afhjælpningshandlinger. I nogle tilfælde løses afhjælpningshandlinger automatisk. I andre tilfælde afventer afhjælpningshandlinger godkendelse via Microsoft 365 Defender Handlingscenter. 

Se [Automatiseret undersøgelse og svar Microsoft 365 Defender](m365d-autoir.md) for at få flere oplysninger.

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Proaktiv søgning efter trusler med avanceret jagt

Det er ikke nok at reagere på angreb, mens de opstår. Ved udvidede multifaseangreb som f.eks. ransomware skal du proaktivt søge efter beviserne for et igangværende angreb og gøre noget for at stoppe det, før det er fuldført.

Avanceret jagt er et forespørgselsbaseret trusselsbaseret jagtværktøj i Microsoft 365 Defender, hvor du kan udforske op til 30 dages rå data. Du kan proaktivt undersøge hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Denne fleksible adgang til Microsoft 365 Defender muliggør ubegrænset jagt på både kendte og potentielle trusler.

Du kan bruge de samme trusselsforespørgsler til at opbygge brugerdefinerede registreringsregler. Disse regler køres automatisk for at søge efter og derefter reagere på mistænkelige sikkerhedsbrud, forkert konfigurerede computere og andre resultater.

Se [Proaktivt på jagt efter trusler med avanceret jagt på Microsoft 365 Defender](advanced-hunting-overview.md) for at få flere oplysninger.

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Kom i gang med nye trusler med trusselsanalyse

Trusselsanalyse er en funktionalitet til trusselsintelligens i Microsoft 365 Defender udviklet til at hjælpe dit sikkerhedsteam med at være så effektivt som muligt, mens de står over for nye trusler. Den indeholder detaljerede analyser og oplysninger om:

- Aktive trusler og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sårbarheder
- Almindelige angrebsoverflader
- Mest udbredte malware

Trusselsanalyse indeholder også oplysninger om relaterede hændelser og påknyttede aktiver i din Microsoft 365 lejer for hver identificeret trussel.

Hver identificerede trussel omfatter en analytikerrapport, en omfattende analyse af den trussel, der er skrevet af Microsofts sikkerhedseksperter, som er på forkant med registrering og analyse af cybersikkerhed. Disse rapporter kan også give oplysninger om, hvordan angrebene vises i Microsoft 365 Defender.

Du kan finde flere oplysninger [i Trusselsanalyse i Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Samarbejd med Microsoft-eksperter

Microsoft-trusselseksperter – Målrettede angrebsmeddelelser er en administreret trussels-jagttjeneste. Når du anvender og er blevet accepteret, modtager du målrettede angrebsmeddelelser fra Microsofts trusselseksperter, så du ikke går glip af vigtige trusler til dit miljø. Disse meddelelser hjælper dig med at beskytte din organisations slutpunkter, mail og identiteter. Microsoft-trusselseksperter – Med Eksperter efter behov kan du få ekspertråd om trusler, som din organisation oplever, og du kan tage kontakt for at få hjælp til trusler, som din organisation står over for. Den er tilgængelig som en ekstra abonnementstjeneste.

Du kan finde flere oplysninger [Microsoft-trusselseksperter i Microsoft 365 oversigt](/security/mtp/microsoft-threat-experts.md).
