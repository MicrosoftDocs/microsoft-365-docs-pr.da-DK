---
title: Undersøg og reager med Microsoft 365 Defender
description: Undersøg og reager på hændelser med funktionerne i Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, analysere, svar, korrelation, angreb, maskiner, enheder, brugere, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb
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
ms.openlocfilehash: a4edb82291ff01a4876ad93d688dbbbf19416c05
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435363"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Undersøg og reager med Microsoft 365 Defender

Her er de primære undersøgelses- og svaropgaver for Microsoft 365 Defender:

- [Reager på hændelser](#incident-response)
- [Gennemse og godkend automatiske afhjælpningshandlinger](#automated-investigation-and-remediation)
- [Søg efter kendte trusler i dine data](#proactive-search-for-threats-with-advanced-hunting)
- [Forstå de nyeste cyberangreb](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Få hjælp](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Svar på hændelse

Microsoft 365 tjenester og apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Angreb anvender dog typisk forskellige teknikker mod forskellige typer enheder, f.eks. enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer. Da det kan være udfordrende og tidskrævende at samle de enkelte beskeder for at få indsigt i et angreb, Microsoft 365 Defender samler automatisk beskederne og deres tilknyttede oplysninger i en hændelse.

Du skal løbende identificere de højeste prioritetshændelser til analyse og løsning i hændelseskøen og gøre dem klar til svar. Dette er en kombination af:

- [Prioritering af](incident-queue.md) fastlæggelse af hændelser med højeste prioritet gennem filtrering og sortering af hændelseskøen. Dette kaldes også triaging.
- [Administration af](manage-incidents.md) hændelser ved at ændre deres titel, tildele dem til en analytiker, tilføje mærker og kommentarer og klassificere dem, når de løses.

For hver hændelse skal du bruge din arbejdsproces for svar på hændelser til at analysere hændelsen og dens beskeder og data for at indeholde angrebet, udrydde truslen, komme sig efter angrebet og lære af den. Se [dette eksempel](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) for Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

Hvis din organisation bruger Microsoft 365 Defender, modtager dit sikkerhedsteam en besked på Microsoft 365 Defender-portalen, når der registreres en skadelig eller mistænkelig aktivitet eller artefakt. I betragtning af det uendelige strøm af trusler, der kan komme ind, står sikkerhedsteams ofte over for udfordringen med at håndtere den høje mængde beskeder. Heldigvis indeholder Microsoft 365 Defender automatiserede undersøgelses- og svarfunktioner (AIR), der kan hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt og effektivt.

Når en automatiseret undersøgelse er afsluttet, bliver der afsagt en dom for hvert eneste bevis for en hændelse. Afhængigt af dommen identificeres afhjælpningshandlinger. I nogle tilfælde udføres afhjælpningshandlinger automatisk. i andre tilfælde afventer afhjælpningshandlinger godkendelse via Microsoft 365 Defender Løsningscenter. 

Se [Automatiseret undersøgelse og svar i Microsoft 365 Defender](m365d-autoir.md) for at få flere oplysninger.

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Proaktiv søgning efter trusler med avanceret jagt

Det er ikke nok at reagere på angreb, efterhånden som de opstår. For udvidede, flerfasede angreb som ransomware, skal du proaktivt søge efter beviserne for et igangværende angreb og træffe foranstaltninger for at stoppe det, før det fuldføres.

Avanceret jagt er et forespørgselsbaseret trusselsjagtværktøj i Microsoft 365 Defender, der giver dig mulighed for at udforske op til 30 dages rådata. Du kan proaktivt inspicere hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Denne fleksible adgang til de Microsoft 365 Defender data gør det muligt at jagte både kendte og potentielle trusler uden begrænsninger.

Du kan bruge de samme trusselsjagtforespørgsler til at oprette brugerdefinerede registreringsregler. Disse regler kører automatisk for at kontrollere for og derefter reagere på mistanke om brudaktivitet, forkert konfigurerede maskiner og andre resultater.

Se [Proaktiv jagt efter trusler med avanceret jagt i Microsoft 365 Defender for](advanced-hunting-overview.md) at få flere oplysninger.

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Kom foran nye trusler med trusselsanalyse

Trusselsanalyse er en trusselsintelligensfunktion i Microsoft 365 Defender, der er designet til at hjælpe dit sikkerhedsteam med at være så effektivt som muligt, mens du står over for nye trusler. Den indeholder detaljerede analyser og oplysninger om:

- Aktive trusselsaktører og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sikkerhedsrisici
- Almindelige angrebsoverflader
- Udbredt malware

Trusselsanalyser indeholder også oplysninger om relaterede hændelser og påvirkede aktiver i din Microsoft 365 lejer for hver identificeret trussel.

Hver identificeret trussel inkluderer en analytikerrapport, en omfattende analyse af truslen skrevet af Microsoft-sikkerhedsforskere, der er på forkant med opdagelse og analyse af cybersikkerhed. Disse rapporter kan også give oplysninger om, hvordan angrebene vises i Microsoft 365 Defender.

Du kan få flere oplysninger [under Trusselsanalyse i Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Samarbejd med Microsoft-eksperter

Microsoft-trusselseksperter – Målrettede angrebsmeddelelser er en administreret trusselsjagttjeneste. Når du ansøger og er accepteret, modtager du målrettede angrebsmeddelelser fra Microsoft-trusselseksperter, så du ikke går glip af kritiske trusler mod dit miljø. Disse meddelelser hjælper dig med at beskytte organisationens slutpunkter, mail og identiteter. Microsoft-trusselseksperter – Eksperter on Demand giver dig ekspertråd om trusler, som din organisation står overfor, og du kan kontakte for at få hjælp til trusler, som din organisation står overfor. Den er tilgængelig som en ekstra abonnementstjeneste.

Du kan få flere oplysninger [under Microsoft-trusselseksperter i Microsoft 365 oversigt](/microsoft-365/security/defender/microsoft-threat-experts).
