---
title: Automatiseret undersøgelse og svar i Microsoft 365 Defender
description: Få et overblik over automatiserede undersøgelses- og svarfunktioner, også kaldet selvhelbredende, i Microsoft 365 Defender
keywords: automatiseret, undersøgelse, alarm, udløser, handling, afhjælpning, selvhelbredende
search.appverid: met150
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
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 332802150235ec6f47c4bdea34b34edb94ea1b90
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731323"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Automatiseret undersøgelse og svar i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Hvis din organisation bruger [Microsoft 365 Defender](microsoft-365-defender.md), modtager dit sikkerhedsteam en besked på Microsoft 365 Defender portalen, når der registreres en skadelig eller mistænkelig aktivitet eller artefakt. I betragtning af det tilsyneladende uendelige strøm af trusler, der kan komme ind, står sikkerhedsteams ofte over for udfordringen med at håndtere den store mængde beskeder. Heldigvis indeholder Microsoft 365 Defender automatiserede undersøgelses- og svarfunktioner (AIR), der kan hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt og effektivt.

Denne artikel indeholder en oversigt over AIR og indeholder links til næste trin og yderligere ressourcer.

## <a name="how-automated-investigation-and-self-healing-works"></a>Sådan fungerer automatiseret undersøgelse og selvhelbredende

Når sikkerhedsbeskeder udløses, er det op til dit team af sikkerhedshandlinger at undersøge disse beskeder og tage skridt til at beskytte din organisation. Det kan være meget tidskrævende at prioritere og undersøge beskeder, især når nye beskeder bliver ved med at komme, mens en undersøgelse foregår. Sikkerhedsteams kan føle sig overvældet over den store mængde trusler, de skal overvåge og beskytte mod. Automatiserede undersøgelses- og svarfunktioner med selvhelbredende funktioner i Microsoft 365 Defender kan hjælpe.

Se følgende video for at se, hvordan selvhelbredende fungerer: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

I Microsoft 365 Defender fungerer automatiseret undersøgelse og svar med selvhelbredende funktioner på tværs af dine enheder, mail & indhold og identiteter.
 
> [!TIP]
> I denne artikel beskrives det, hvordan automatiseret undersøgelse og svar fungerer. Hvis du vil konfigurere disse funktioner, skal du se [Konfigurer automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Din egen virtuelle analytiker

Imagine have en virtuel analytiker i sikkerhedsteamet på niveau 1 eller niveau 2. Den virtuelle analytiker efterligner de ideelle trin, som sikkerhedshandlinger ville tage for at undersøge og afhjælpe trusler. Den virtuelle analytiker kan arbejde 24 x 7 med ubegrænset kapacitet og påtage sig en betydelig belastning af undersøgelser og trusselsafhjælpning. En sådan virtuel analytiker kan reducere den tid, det tager at svare, og frigøre dit sikkerhedsteam til andre vigtige trusler eller strategiske projekter. Hvis dette scenarie lyder som science fiction, er det ikke! En sådan virtuel analytiker er en del af din Microsoft 365 Defender-pakke, og navnet er *automatiseret undersøgelse og svar*.

Automatiserede undersøgelses- og svarfunktioner gør det muligt for dit team af sikkerhedshandlinger dramatisk at øge organisationens kapacitet til at håndtere sikkerhedsbeskeder og hændelser. Med automatiseret undersøgelse og svar kan du reducere omkostningerne ved at håndtere undersøgelses- og svaraktiviteter og få mest muligt ud af din pakke til trusselsbeskyttelse. Automatiserede undersøgelses- og svarfunktioner hjælper dit team med sikkerhedshandlinger ved at:

1. Fastlæggelse af, om en trussel kræver handling.
2. At tage (eller anbefale) nødvendige afhjælpningshandlinger.
3. Fastlæggelse af, om og hvilke andre undersøgelser der skal finde sted.
4. Gentager processen efter behov for andre beskeder.

## <a name="the-automated-investigation-process"></a>Den automatiserede undersøgelsesproces

En besked opretter en hændelse, som kan starte en automatisk undersøgelse. Den automatiserede undersøgelse resulterer i en dom for hvert bevis. Dommene kan være:
- *Skadelig*
- *Mistænkelige* 
- *Der blev ikke fundet nogen trusler* 

Afhjælpningshandlinger for skadelige eller mistænkelige enheder identificeres. Eksempler på afhjælpningshandlinger omfatter:

- Afsendelse af en fil til karantæne
- Standsning af en proces
- Isolering af en enhed
- Blokering af en URL-adresse 
- Andre handlinger

Du kan få flere oplysninger under [Afhjælpningshandlinger i Microsoft 365 Defender](m365d-remediation-actions.md).

Afhængigt af [hvordan automatiserede undersøgelses- og svarfunktioner er konfigureret](m365d-configure-auto-investigation-response.md) for din organisation, udføres afhjælpningshandlinger automatisk eller kun efter godkendelse af dit team for sikkerhedshandlinger. Alle handlinger, uanset om de venter eller er fuldført, vises i [Løsningscenter](m365d-action-center.md).

Mens der kører en undersøgelse, føjes alle andre relaterede beskeder, der opstår, til undersøgelsen, indtil den er fuldført. Hvis et berørt objekt vises et andet sted, udvider den automatiserede undersøgelse dens omfang til at omfatte det pågældende objekt, og undersøgelsesprocessen gentages. 

I Microsoft 365 Defender korrelerer hver automatiseret undersøgelse signaler på tværs af Microsoft Defender for Identity, Microsoft Defender for Endpoint og Microsoft Defender for Office 365 som opsummeret i følgende tabel: 

|Enheder |Trusselsbeskyttelsestjenester  |
|:---------|:---------|
|Enheder (også kaldet slutpunkter eller maskiner) |[Defender for Endpoint](../defender-endpoint/automated-investigations.md) |      
|Active Directory-brugere, objektfunktionsmåder og aktiviteter i det lokale miljø     |[Defender for Identity](/azure-advanced-threat-protection/what-is-atp) |      
|Mailindhold (mails, der kan indeholde filer og URL-adresser)     |[Defender for Office 365](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Det er ikke alle beskeder, der udløser en automatiseret undersøgelse, og ikke alle undersøgelser resulterer i automatiserede afhjælpningshandlinger. Det afhænger af, hvordan automatiseret undersøgelse og svar er konfigureret for din organisation. Se [Konfigurer automatiserede undersøgelses- og svarfunktioner](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Visning af en liste over undersøgelser

Hvis du vil have vist undersøgelser, skal du gå til siden **Hændelser** . Vælg en hændelse, og vælg derefter fanen **Undersøgelser** . Du kan få mere at vide under [Detaljer og resultater af en automatiseret undersøgelse](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Oplæring af sikkerhedsanalytikere

Brug dette læringsmodul fra Microsoft Learn til at forstå, hvordan Microsoft 365 Defender bruger automatisk selvhelbredelse til undersøgelse og svar på hændelser.

|Uddannelse:|Automatiser selvhelbredende med Microsoft 365 Defender|
|---|---|
|![Automatiser selvhelbredende med Microsoft 365 Defender træningsikon.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender bruger kunstig intelligens til at automatisere afhjælpning af hændelser og hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt og effektivt. <p> 11 min. - 5 enheder |

> [!div class="nextstepaction"]
> [Start >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Næste trin

- [Se forudsætningerne for automatiseret undersøgelse og svar](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Konfigurer automatiseret undersøgelse og svar for din organisation](m365d-configure-auto-investigation-response.md)
- [Få mere at vide om Løsningscenter](m365d-action-center.md)
