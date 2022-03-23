---
title: Automatiseret undersøgelse og svar i Microsoft 365 Defender
description: Få et overblik over automatiserede undersøgelses- og svarfunktioner, også kaldet selvbetjening, i Microsoft 365 Defender
keywords: automatiseret, undersøgelse, besked, udløser, handling, afhjælpning, selvbetjening
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
ms.openlocfilehash: 180599007a47fe9cfa9ae68d6647f7494dd2f410
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592103"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Automatiseret undersøgelse og svar i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Hvis din organisation bruger en [Microsoft 365 Defender](microsoft-365-defender.md), modtager dit sikkerhedsteam en besked i Microsoft 365 Defender-portalen, når der registreres skadelig eller mistænkelig aktivitet eller artefakt. På grund af den tilsyneladende aldrig-endende strøm af trusler, der kan komme ind, står sikkerhedsteams ofte over for udfordringen med at tage hånd om den store mængde af beskeder. Heldigvis omfatter Microsoft 365 Defender automatiseret undersøgelse og svarmuligheder (AIR), som kan hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt.

Denne artikel indeholder en oversigt over AIR og indeholder links til næste trin og yderligere ressourcer.

> [!TIP]
> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).

## <a name="how-automated-investigation-and-self-healing-works"></a>Sådan fungerer automatiseret undersøgelse og selvbetjening

Når der udløses sikkerhedsadvarsler, er det op til dit sikkerhedsteam at undersøge disse vigtige beskeder og tage skridt til at beskytte din organisation. Det kan være meget tidskrævende at prioritere og undersøge vigtige beskeder, især når nye beskeder bliver ved med at komme, mens en undersøgelse finder sted. Sikkerhedsteams kan føle sig overvældet af mængden af trusler, de skal overvåge og beskytte sig mod. Automatiserede undersøgelses- og svarfunktioner i selvbetjening kan Microsoft 365 Defender hjælpe.

Se følgende video for at se, hvordan selvbetjening fungerer: <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

I Microsoft 365 Defender fungerer automatiseret undersøgelse og svar med selvbetjeningsfunktioner på tværs af dine enheder, & indhold og identiteter.
 
> [!TIP]
> Denne artikel beskriver, hvordan automatiseret undersøgelse og svar fungerer. Hvis du vil konfigurere disse funktioner, skal [du se Konfigurer automatiseret undersøgelse og svarmuligheder Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Din egen virtuelle analytiker

Imagine har en virtuel analytiker i dit sikkerhedsteam på niveau 1 eller niveau 2. Den virtuelle analytiker efterligner de ideelle trin, som sikkerhedshandlinger ville tage for at undersøge og afhjælpe trusler. Den virtuelle analytiker kan arbejde døgnet rundt med ubegrænset kapacitet og tage en stor mængde undersøgelser og afhjælpe trusler. En sådan virtuel analytiker kan reducere tiden til at reagere betydeligt, hvilket vil frigøre dit sikkerhedsteam til andre vigtige trusler eller strategiske projekter. Hvis dette scenarie lyder som science fiction, er det ikke! Sådan en virtuel analytiker er en del af din Microsoft 365 Defender pakke, og navnet er *automatiseret undersøgelse og svar*.

Automatiserede undersøgelses- og svarfunktioner gør det muligt for dit sikkerhedsteam markant at øge organisationens kapacitet til at håndtere sikkerhedsadvarsler og hændelser. Med automatiseret undersøgelse og svar kan du reducere omkostningerne til undersøgelse og svaraktiviteter og få mest muligt ud af din trusselsbeskyttelsespakke. Automatiserede undersøgelses- og svarfunktioner hjælper dit sikkerhedsteam ved at:

1. Afgøre, om en trussel kræver handling.
2. At (eller anbefale) eventuelle nødvendige afhjælpningshandlinger.
3. Afgøre, om og hvilke andre undersøgelser der skal foretages.
4. Gentag processen efter behov for andre beskeder.

## <a name="the-automated-investigation-process"></a>Den automatiserede undersøgelsesproces

En besked opretter en hændelse, som kan starte en automatisk undersøgelse. Den automatiserede undersøgelse giver en konklusion for hvert enkelt bevis. Bedømmelser kan være:
- *Ondsindet*
- *Mistænkelig* 
- *Der blev ikke fundet nogen trusler* 

Afhjælpningshandlinger for skadelige eller mistænkelige enheder identificeres. Eksempler på afhjælpningshandlinger omfatter:

- Sende en fil til karantæne
- Stoppe en proces
- Isolere en enhed
- Blokering af en URL-adresse 
- Andre handlinger

Få mere at vide under [Afhjælpningshandlinger i Microsoft 365 Defender](m365d-remediation-actions.md).

Afhængigt [af hvordan automatiserede](m365d-configure-auto-investigation-response.md) undersøgelses- og svarfunktioner er konfigureret for din organisation, udføres afhjælpningshandlinger automatisk eller kun efter godkendelse fra dit sikkerhedsteam. Alle handlinger, uanset om de er ventende eller fuldførte, vises i [Handlingscenter](m365d-action-center.md).

Mens en undersøgelse kører, føjes alle andre relevante relevante beskeder til undersøgelsen, indtil den er færdig. Hvis en berørt enhed ses et andet sted, udvides omfanget af den automatiske undersøgelse til at omfatte den pågældende enhed, og undersøgelsesprocessen gentages. 

I Microsoft 365 Defender korrelerer hver automatiseret undersøgelse signaler på tværs af Microsoft Defender for Identity, Microsoft Defender til slutpunkt og Microsoft Defender Office 365, som opsummeret i følgende tabel: 

|Enheder |Trusselsbeskyttelsestjenester  |
|:---------|:---------|
|Enheder (også kaldet slutpunkter eller maskiner) |[Defender til Slutpunkt](../defender-endpoint/automated-investigations.md) |      
|Lokale Active Directory-brugere, enhedsfunktionsmåde og aktiviteter     |[Defender for Identity](/azure-advanced-threat-protection/what-is-atp) |      
|Mailindhold (mails, der kan indeholde filer og URL-adresser)     |[Defender til Office 365](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Ikke alle beskeder udløser en automatisk undersøgelse, og ikke enhver undersøgelse resulterer i automatiserede afhjælpningshandlinger. Det afhænger af, hvordan automatiseret undersøgelse og svar er konfigureret for din organisation. Se [Konfigurer automatiserede undersøgelses- og svarfunktioner](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Visning af en liste over undersøgelser

Hvis du vil se undersøgelser, skal du gå **til siden** Hændelser. Vælg en hændelse, og vælg **derefter fanen** Undersøgelser. Du kan få mere at vide [under Detaljer og resultater af en automatisk undersøgelse](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Kurser til sikkerhedsanalytikere

Brug dette læringsmodul fra Microsoft Learn til at forstå, Microsoft 365 Defender bruger automatiseret selvbetjening til undersøgelse og svar af hændelser.

|Kursus:|Automatiser selvhjulpen med Microsoft 365 Defender|
|---|---|
|![Automatiser selvbetjening med Microsoft 365 Defender undervisningsikon.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender bruger AI til at automatisere afhjælpning af hændelser, hvilket hjælper dit sikkerhedsteam med at håndtere trusler mere effektivt. <p> 11 min- 5 enheder |

> [!div class="nextstepaction"]
> [Start >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Næste trin

- [Se forudsætningerne for automatiseret undersøgelse og svar](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Konfigurer automatiseret undersøgelse og svar til din organisation](m365d-configure-auto-investigation-response.md)
- [Få mere at vide om handlingscenter](m365d-action-center.md)
