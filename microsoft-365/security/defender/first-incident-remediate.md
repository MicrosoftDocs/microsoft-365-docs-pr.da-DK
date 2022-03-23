---
title: Trin 2. Afhjælp din første hændelse
description: Sådan kommer du i gang med at løse din første hændelse Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb
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
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2837b6009c143ea724d8c13d2548eeeca80e431d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593857"
---
# <a name="step-2-remediate-your-first-incident"></a>Trin 2. Afhjælp din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender indeholder ikke blot registrerings- og analysefunktioner, men indeholder også muligheder for at inddæmme og sprede malware. Indeholder trin til at reducere effekten af angrebene, mens det er muligt at sikre, at alle sporinger af hackeraktivitet fjernes fra netværket. Microsoft 365 Defender tilbyder adskillige afhjælpningshandlinger, der kan konfigureres til automatisk afhjælpning afhængigt af operativsystemet for de påvirkede enheder og angrebstypen.[](m365d-autoir.md)

Microsoft 365 Defender tilbyder flere afhjælpningshandlinger, som analytikere kan starte manuelt. Handlinger er opdelt i to kategorier, Handlinger på enheder og handlinger på filer. Nogle handlinger kan bruges til straks at stoppe truslen, mens andre handlinger hjælper med yderligere analyse af analyse.

## <a name="actions-on-devices"></a>Handlinger på enheder

- **Isoler enheden** – Denne aktivitet blokerer straks al netværkstrafik (internet og intern) for at minimere malwares spredning og tillade, at analytikere fortsætter analyser, uden at en ondsindet agent kan fortsætte et angreb. Den eneste forbindelse, der er tilladt, er microsoft Defender for Identity-tjenesteskyen, så Microsoft Defender for Identity fortsat kan overvåge enheden. 
- **Begræns** eksekvering af apps – Hvis du vil begrænse kørsel af et program, anvendes en politik for kodeintegritet, der kun tillader, at filer kan køres, hvis de er signeret af et certifikat, der er udstedt af Microsoft. Denne metode til begrænsning kan hjælpe med at forhindre en hacker i at styre kompromitterede enheder og udføre yderligere ondsindede aktiviteter.
- **Kør antivirusscanning** – en Microsoft Defender Antivirus scanning kan køre sammen med andre antivirusløsninger, uanset om Defender Antivirus er den aktive antivirusløsning eller ej. Hvis et andet antivirusleverandørprodukt er den primære løsning til slutpunktsbeskyttelse, kan du køre Defender Antivirus i passiv tilstand.
- **Initier automatiseret** undersøgelse – Du kan starte en ny, generel, automatisk undersøgelse af enheden. Mens en undersøgelse kører, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatisk undersøgelse, indtil undersøgelsen er afsluttet. Hvis den samme trussel kan ses på andre enheder, føjes disse enheder til undersøgelsen.
- **Initier** live-svar – Direkte svar er en funktion, der giver dig øjeblikkelig adgang til en enhed ved hjælp af en ekstern shell-forbindelse. Dette giver dig mulighed for at udføre en dybdegående indsats og straks reagere på handlinger, der omgående skal indeholde identificerede trusler i realtid. Liverespons er designet til at forbedre undersøgelser ved at give dig mulighed for at indsamle analysere data, køre scripts, sende mistænkelige enheder til analyse, løse trusler og proaktivt lede efter nye trusler.
- **Indsamle undersøgelsespakke** – Som en del af undersøgelsen eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Ved at indsamle undersøgelsespakken kan du identificere enhedens aktuelle tilstand og yderligere forstå de værktøjer og teknikker, der bruges af hackeren. 
- **Kontakt en trusselsekspert** (tilgængelig både i Handlinger på enheder og filer) – Du kan kontakte en Microsoft-trusselsekspert for at få mere at vide om potentielt kompromitterede enheder eller enheder, der allerede er kompromitteret. Microsoft-trusselseksperter kan blive engageret direkte fra Microsoft 365 Defender for at få et rettidigt og nøjagtigt svar. 

## <a name="actions-on-files"></a>Handlinger på filer

- **Stop- og karantænefil** – Denne handling omfatter at stoppe kørsel af processer, kvarte filer og slette permanente data, f.eks. registreringsdatabasenøgler. Denne handling træder i kraft på enheder med Windows 11 eller Windows 10 version 1703 eller nyere, hvor filen er blevet observeret inden for de seneste 30 dage. 
- **Tilføj indikatorer for at blokere eller tillade** filer – Undgå yderligere overførsel af et angreb i organisationen ved at udelukke potentielt skadelige filer eller potentielt malware. Denne handling forhindrer filen i at blive læst, skrevet eller udført på enheder i organisationen.
- **Download eller indsaml** fil – Denne handling giver analytikere mulighed for at downloade en fil i en adgangskodebeskyttet .zip arkivfil til yderligere analyse i organisationen.
- **Dybdegående** analyse – Denne handling udfører en fil i et sikkert, fuldt instrumenteret skymiljø. Grundige analyseresultater viser filens aktiviteter, observerede funktionsmåder og tilknyttede artefakter, f.eks. afbrudte filer, ændringer i registreringsdatabasen og kommunikation med IP-adresser. 

I eksemplet med [Registrer, triage og analysér](first-incident-analyze.md#analyze-your-first-incident) hændelser kan en analytiker afhjælpe denne hændelse med disse handlinger:

1. Nulstil adgangskoden til brugerkontoen med det samme
2. Isoler enheden i Microsoft 365 Defender indtil dybdegående analyse er fuldført
3. Kontrollér, at den skadelige fil blev sat i karantæne fra SharePoint
4. Kontrollér, hvilke slutpunkter der er blevet påvirket af malware
5. Genopbyg systemer
6. Kontrollér, om der er tilsvarende Microsoft Defender for skyapps-beskeder for andre brugere
7. Opret en brugerdefineret indikator i Microsoft Defender til slutpunkt for at blokere en Tor IP-adresse
8. Opret en styringshandling i Microsoft Defender til skyapps for denne type besked, f.eks. dem, der er vist på følgende billede:

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Eksempel på styringshandlinger i portalen Microsoft Defender for Cloud Apps.":::

De fleste af afhjælpningshandlingerne kan anvendes og registreres i Microsoft 365 Defender.

## <a name="using-playbooks"></a>Brug af lærebøger

Desuden kan automatiseret afhjælpning oprettes ved hjælp af lærebøger. Microsoft har i øjeblikket [skabeloner til lærebøger på GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks) der leverer lærebøger til følgende scenarier:

- Fjern følsom fildeling, efter du har anmodet om brugervalidering
- Automatisk triage beskeder om sjældne lande
- Anmod om managerhandling, før du deaktiverer en konto
- Deaktivere skadelige indbakkeregler

Playbooks bruger Power Automate til at oprette brugerdefinerede automationsflows til at automatisere visse aktiviteter, når der er blevet udløst bestemte kriterier. Organisationer kan oprette lærebøger enten fra eksisterende skabeloner eller fra bunden. 

Her er et eksempel.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Eksempel på et Power Automate brugerdefineret proces automatiseringsflow."::: 
 
Der kan også oprettes playbooks under gennemgang efter [hændelsen for](first-incident-post.md) at oprette afhjælpningshandlinger fra løste hændelser. 

## <a name="next-step"></a>Næste trin

[![Trin 3: Lær, hvordan du udfører en vurdering af en hændelse efter hændelsen.](../../media/first-incident-overview/first-incident-path-step3.png)](first-incident-post.md)

Få mere at vide [om, hvordan du udfører en vurdering efter hændelsen af en hændelse](first-incident-post.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
