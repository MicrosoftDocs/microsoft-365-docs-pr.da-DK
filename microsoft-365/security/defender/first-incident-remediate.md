---
title: Trin 2. Afhjælp din første hændelse
description: Sådan kommer du i gang med at afhjælpe din første hændelse i Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f55cdc31dbf8a74395a232340cc8d273e9927dc0
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893535"
---
# <a name="step-2-remediate-your-first-incident"></a>Trin 2. Afhjælp din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender leverer ikke kun opdagelses- og analysefunktioner, men leverer også opbevaring og udryddelse af malware. Opbevaring omfatter trin til at reducere virkningen af angrebet, mens udryddelse sikrer, at alle spor af hackeraktivitet fjernes fra netværket. Microsoft 365 Defender tilbyder flere afhjælpningshandlinger, der kan konfigureres til [automatisk afhjælpning](m365d-autoir.md), afhængigt af operativsystemet på berørte enheder og angrebstypen.

Microsoft 365 Defender tilbyder flere afhjælpningshandlinger, som analytikere kan starte manuelt. Handlinger er opdelt i to kategorier: Handlinger på enheder og handlinger på filer. Nogle handlinger kan bruges til straks at stoppe truslen, mens andre handlinger hjælper med yderligere retsmedicinske analyser.

## <a name="actions-on-devices"></a>Handlinger på enheder

- **Isoler enheden** - Denne aktivitet blokerer straks al netværkstrafik (internet og intern) for at minimere spredningen af malware og give analytikere mulighed for at fortsætte analysen, uden at en ondsindet aktør kan fortsætte et angreb. Den eneste tilladte forbindelse er til Microsoft Defender for Identity-tjenesteskyen, så Microsoft Defender for Identity kan fortsætte med at overvåge enheden. 
- **Begræns udførelse af apps** – Hvis du vil forhindre et program i at køre, anvendes der en kodeintegritetspolitik, der kun tillader, at filer køres, hvis de er signeret af et Certifikat, der er udstedt af Microsoft. Denne begrænsningsmetode kan hjælpe med at forhindre en hacker i at kontrollere kompromitterede enheder og udføre yderligere skadelige aktiviteter.
- **Kør antivirusscanning** – En Microsoft Defender Antivirus-scanning kan køre sammen med andre antivirusløsninger, uanset om Defender Antivirus er den aktive antivirusløsning eller ej. Hvis et andet antivirusprogram er den primære løsning til beskyttelse af slutpunkter, kan du køre Defender Antivirus i passiv tilstand.
- **Start en automatiseret undersøgelse** – Du kan starte en ny automatiseret undersøgelse til generelle formål på enheden. Mens der kører en undersøgelse, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatisk undersøgelse, indtil undersøgelsen er fuldført. Hvis den samme trussel ses på andre enheder, føjes disse enheder desuden til undersøgelsen.
- **Initier live-svar** – Direkte svar er en funktion, der giver dig øjeblikkelig adgang til en enhed ved hjælp af en ekstern shellforbindelse. Dette giver dig mulighed for at udføre dybdegående undersøgelsesarbejde og reagere øjeblikkeligt for straks at indeholde identificerede trusler i realtid. Liverespons er designet til at forbedre undersøgelser ved at gøre det muligt for dig at indsamle retsmedicinske data, køre scripts, sende mistænkelige enheder til analyse, afhjælpe trusler og proaktivt jage efter nye trusler.
- **Indsaml undersøgelsespakke** – Som en del af undersøgelses- eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Ved at indsamle undersøgelsespakken kan du identificere enhedens aktuelle tilstand og yderligere forstå de værktøjer og teknikker, der bruges af hackeren. 
- **Kontakt en trusselsekspert** (tilgængelig i både handlinger på enheder og filer) – Du kan kontakte en Microsoft-trusselsekspert for at få mere indsigt i potentielt kompromitterede enheder eller enheder, der allerede er kompromitteret. Microsoft-trusselseksperter kan engageres direkte fra Microsoft 365 Defender for at få et rettidigt og nøjagtigt svar. 

## <a name="actions-on-files"></a>Handlinger på filer

- **Stop- og sæt fil i karantæne** – Denne handling omfatter stop af kørende processer, quarantinering af filer og sletning af vedvarende data, f.eks. alle registreringsdatabasenøgler. Denne handling træder i kraft på enheder med Windows 11 eller Windows 10, version 1703 eller nyere, hvor filen blev observeret inden for de sidste 30 dage. 
- **Tilføj indikatorer for at blokere eller tillade filer** – Undgå yderligere overførsel af et angreb i din organisation ved at forbyde potentielt skadelige filer eller mistanke om malware. Denne handling forhindrer, at filen læses, skrives eller udføres på enheder i din organisation.
- **Download eller indsaml fil** – denne handling giver analytikere mulighed for at downloade en fil i en adgangskodebeskyttet .zip arkivfil til yderligere analyse af organisationen.
- **Detaljeret analyse** – denne handling udfører en fil i et sikkert, fuldt instrumenteret cloudmiljø. Detaljerede analyseresultater viser filens aktiviteter, observerede funktionsmåder og tilknyttede artefakter, f.eks. mistede filer, ændringer i registreringsdatabasen og kommunikation med IP-adresser. 

I forlængelse af eksemplet i [Registrer, triage og analysér hændelser](first-incident-analyze.md#analyze-your-first-incident) kan en analytiker afhjælpe denne hændelse med disse handlinger:

1. Nulstil straks adgangskoden til brugerkontoen
2. Isoler enheden i Microsoft 365 Defender, indtil den dybe analyse er fuldført
3. Kontrollér, at den skadelige fil blev sat i karantæne fra SharePoint
4. Kontrollér, hvilke slutpunkter der blev påvirket af malware
5. Byg systemer igen
6. Søg efter lignende Microsoft Defender for Cloud Apps beskeder til andre brugere
7. Opret en brugerdefineret indikator i Microsoft Defender for Endpoint for at blokere en Tor IP-adresse
8. Opret en styringshandling i Microsoft Defender for Cloud Apps for denne type besked, f.eks. dem, der vises på følgende billede:

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Styringshandlinger på Microsoft Defender for Cloud Apps-portalen" lightbox="../../media/first-incident-remediate/first-incident-mcas-governance.png":::

De fleste afhjælpningshandlinger kan anvendes og spores i Microsoft 365 Defender.

## <a name="using-playbooks"></a>Brug af playbooks

Desuden kan automatiseret afhjælpning oprettes ved hjælp af playbooks. I øjeblikket har Microsoft [Playbook-skabeloner på GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks) , der indeholder playbooks til følgende scenarier:

- Fjern følsom fildeling efter anmodning om brugervalidering
- Automatisk triage af sjældne landebeskeder
- Anmodning om en overordnet handling, før du deaktiverer en konto
- Deaktiver regler for skadelig indbakke

Playbooks bruger Power Automate til at oprette brugerdefinerede automatiseringsflow for robotprocesser for at automatisere visse aktiviteter, når bestemte kriterier er blevet udløst. Organisationer kan oprette playbooks enten fra eksisterende skabeloner eller fra bunden. 

Her er et eksempel.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Et automatiseret flow for brugerdefineret robotproces i Power Automate" lightbox="../../media/first-incident-remediate/first-incident-power-automate.png"::: 
 
Der kan også oprettes playbooks under [gennemgang efter hændelser](first-incident-post.md) for at oprette afhjælpningshandlinger fra løste hændelser. 

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan [du udfører en gennemgang af en hændelse efter en hændelse](first-incident-post.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
