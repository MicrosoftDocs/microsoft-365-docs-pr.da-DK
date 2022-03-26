---
title: Kør dit Microsoft 365 Defender projekt
description: Kør dit Microsoft 365 Defender i produktion for effektivt at bestemme fordelene og indføringen af Microsoft 365 Defender.
keywords: Microsoft 365 Defender pilotprojekt, kør Microsoft 365 Defender projekt, evaluer Microsoft 365 Defender i produktion, Microsoft 365 Defender  pilotprojekt, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fd84ef93d679be6e1e42f823dcac1f2d5181f1e9
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63595842"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Kør dit Microsoft 365 Defender projekt 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender


Denne vejledning hjælper dig med at køre et pilotprojekt ved at angive markører for at sikre, at du har en velstruktureret plan, der guider dig gennem brugen af simuleringsfunktionen til angreb og til sidst afslutter pilotprojektet med vigtige take-aways, så du kan reflektere over og dokumentere resultaterne.

![Faser i kørsel af et Microsoft 365 Defender pilot](../../media/pilotphases.png)


At køre et pilotprojekt hjælper dig effektivt med at afgøre fordelen ved Microsoft 365 Defender. Før du aktiverer Microsoft 365 Defender i produktionsmiljøet og starter dine use cases, er det bedst at planlægge at fastlægge de opgaver, der skal udføres for dit pilotprojekt, og angive succeskriterierne. 


## <a name="how-to-use-this-pilot-playbook"></a>Sådan bruger du denne pilotspilbog

Denne vejledning giver en oversigt over Microsoft 365 Defender og en trinvis vejledning i, hvordan du konfigurerer dit pilotprojekt. 

Microsoft 365 Defender er en samlet forsvarspakke til virksomheder, der før og efter sikkerhedsbrudet indbygget koordinerer beskyttelse, registrering, forebyggelse, undersøgelse og svar på tværs af slutpunkter, identiteter, mail og programmer for at yde integreret beskyttelse mod avancerede angreb. Det gør den ved at kombinere og samle følgende funktioner i en enkelt sikkerhedsløsning:

- Microsoft Defender til slutpunkt (slutpunkter)
- Microsoft Defender til Office 365 (mail)
- Microsoft Defender til identitet (identitet)
- Microsoft Cloud App Security (apps)

![Billede of_Microsoft 365 Defender-løsning til brugere, Microsoft Defender for Identity, til slutpunkter Microsoft Defender til slutpunkter, til skyapps, Microsoft Cloud App Security og til data, Microsoft Defender til Office 365](../../media/mtp/m365pillars.png)

Med den integrerede Microsoft 365 Defender-løsning kan sikkerhedsfagfolk arbejde tæt sammen om trusselssignalerne, som signalerer, at Microsoft Defender til Slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til identitet og Microsoft Cloud App Security  modtage og fastslå den fulde omfang og indvirkning af truslen, hvordan den har indtastet miljøet, hvad det påvirkes, og hvordan det i øjeblikket påvirker organisationen. Microsoft 365 Defender automatisk handling for at forhindre eller stoppe angreb og selvkørende postkasser, slutpunkter og brugeridentiteter. Se [oversigten Microsoft 365 Defender, hvis du](microsoft-365-defender.md) vil have mere at vide.

Følgende eksempeltidslinje varierer, afhængigt af om du har de rigtige ressourcer i dit miljø. Nogle registreringer og arbejdsprocesser har måske brug for mere tid til at lære mere end de andre.

![Eksempel på tidslinjen i at køre Microsoft 365 Defender pilot](../../media/phase-diagrams/pilot-phases.png)

> [!IMPORTANT]
> Følg pilotinstruktionerne så tæt som muligt for at opnå optimale resultater.

### <a name="pilot-playbook-phases"></a>Pilotfaser i playbook

Der er fire faser i at køre et Microsoft 365 Defender pilotprojekt:

|Fase | Beskrivelse |
|:-------|:-----|
| [Planlægning](m365d-pilot-plan.md)<br> ~ 1 dag| Få mere at vide om, hvad du skal overveje, før du Microsoft 365 Defender dit pilotprojekt: <br><br>- Omfang <br> - Use cases <br>- Krav <br>- Testplan <br> - Succeskriterier <br> - Scorecard 
| [Forberedelse](m365d-evaluation.md) <br>~ 2 dage|  Access Microsoft 365 Security Center for at konfigurere dit Microsoft 365 Defender pilotmiljø. Du bliver vejledt i at:<br><br>- Identificere interessenter og søge efter at få afmeldt dit pilotprojekt <br> - Miljøovervejelser <br>- Access <br>- Azure Active Directory konfiguration <br> - Konfigurationsrækkefølge <br> - Tilmeld dig Microsoft 365 E5 prøveversion <br> - Konfigurer domæne <br>- Tildel Microsoft 365 E5 licenser <br> - Fuldfør konfigurationsguiden på portalen|
| [Angrebssimulering](m365d-pilot-simulate.md) <br>~ 2 dage| Hvis du vil simulere et angreb, bliver du vejledt i at:<br><br>- Bekræft kravene til testmiljøet <br>- Kør simulering <br>- Undersøg en hændelse <br>- løse hændelsen 
| [Lukning og oversigt](m365d-pilot-close.md) <br>~ 1 dag| Når du har nået slutningen af processen, bliver du vejledt i at:<br><br>- Gennemgå dit endelige output<br>- Præsentere dine output for dine interessenter <br>- Giv feedback <br>– Tag de næste skridt 

## <a name="next-step"></a>Næste trin

|[Planlægningsfase](m365d-pilot-plan.md) | Planlæg dit Microsoft 365 Defender pilotprojekt 
|:-------|:-----|
