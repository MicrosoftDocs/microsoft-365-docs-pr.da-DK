---
title: Forbered din sikkerhed på din første hændelse
description: Konfigurer din Microsoft 365 lejers sikkerhedsstilling for din første hændelse i Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
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
ms.openlocfilehash: c3b86a133b5126029378018fdac821d5423b2761
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593852"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>Forbered din sikkerhed på din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Forberedelse til hændelseshåndtering indebærer konfiguration af tilstrækkelig beskyttelse af en organisations netværk fra forskellige typer sikkerhedshændelser. For at reducere risikoen for sikkerhedshændelser anbefaler NIST (National Institute of Standards and Technology) flere sikkerhedsmetoder, herunder risikovurdering, hardening af værtssikkerhed, konfiguration af netværk på sikker måde og forhindring af malware. 

Microsoft 365 Defender kan hjælpe med at tage hånd om flere aspekter af forebyggelse af hændelser: 

- Implementering af en [nultillidsstruktur](/security/zero-trust/)
- Fastslå din sikkerhedsmæssige stilling ved at tildele en score med [Microsoft Secure Score](microsoft-secure-score.md)
- Forhindring af trusler via vurdering af sikkerhedsrisiko i administration [af trusler og sikkerhedsrisiko](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Forstå de nyeste sikkerhedstrusler, så du kan forberede dig på dem med [trusselsanalyse](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Trin 1. Implementer nultillids

[Zero Trust](/security/zero-trust/) er en integreret sikkerhedsintegreret og ende-til-ende-strategi, der tager højde for den komplekse karakter af et moderne miljø, herunder den mobile arbejdsstyrke og brugere, enheder, programmer og data, uanset hvor de befinder sig. Ved at have en enkelt rude med glas til at administrere alle registreringer på en ensartet måde kan Microsoft 365 Defender gøre det nemmere for dit sikkerhedsteam at implementere de styrende principper for Zero Trust.[](/security/zero-trust/#guiding-principles-of-zero-trust) 

Komponenter af Microsoft 365 Defender kan vise overtrædelser af regler, der er blevet implementeret for at oprette betingede access-politikker for Nul tillid ved at integrere data fra Microsoft Defender til Slutpunkt eller andre mobile sikkerhedsleverandører som en informationskilde til politikker for enhedsoverholdelse og implementering af enhedsbaserede betingede adgangspolitikker. 

Risiko for enheder påvirker direkte, hvilke ressourcer der vil være tilgængelige for brugeren af den pågældende enhed. Afvisning af adgang til ressourcer, der er baseret på bestemte kriterier, er hovedtemaet i Nul tillid, og Microsoft 365 Defender indeholder oplysninger, der er nødvendige for at bestemme kriterierne for tillidsniveau. Eksempelvis kan Microsoft 365 Defender levere softwareversionsniveauet for en enhed via siden til administration af trussel og sikkerhedsrisiko, mens politikker for betinget adgang begrænser enheder, der har forældede eller følsomme versioner.

Automatisering er en vigtig del af at implementere og vedligeholde et Zero Trust-miljø og samtidig reducere antallet af beskeder, der potentielt kan føre til hændelser med hændelsesrespons. Komponenter i Microsoft 365 Defender kan være automatiserede såsom afhjælpningshandlinger [(også](m365d-autoir.md) kaldet undersøgelser af en hændelse på Microsoft 365 Defender-portalen), meddelelseshandlinger og endda oprettelse af supportbilletter som f.eks. [i ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>Trin 2. Bestem din organisations sikkerhedsfunktioner

Derefter kan organisationer bruge [Microsoft Secure Score](microsoft-secure-score.md) i Microsoft 365 Defender til at bestemme din aktuelle sikkerhed og overveje anbefalinger til, hvordan du kan forbedre den. Jo højere pointen er, jo flere sikkerhedsanbefalinger og forbedringshandlinger har organisationen foretaget. Secure Score-anbefalinger kan tages på tværs af forskellige produkter og give organisationer mulighed for at øge deres pointtal endnu højere. 

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Eksempel på Microsoft Secure Score i Microsofts sikkerhedscenter.":::
 
## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Trin 3. Vurder din organisations eksponering for sikkerhedsrisikoen

At forhindre hændelser kan hjælpe med at strømline sikkerhedshandlinger for at fokusere på den on-going critical and important security incidents. Softwaresårbarheder er ofte et indgangspunkt, der kan forhindre angreb, der kan føre til datatyveri, datatab eller driftsafbrydelser. Hvis der ikke sker nogen angreb, skal sikkerhedshandlingerne forsøge at opnå og opretholde et acceptabelt niveau af [eksponering for](../defender-endpoint/tvm-exposure-score.md) sikkerhedsrisikoen i organisationen.

Hvis du vil se status for softwarerettelser, [](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) skal du gå til siden til administration af trussel og sikkerhedsrisiko i Defender til slutpunkt, som du kan få adgang Microsoft 365 Defender via **fanen Flere** ressourcer.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Eksempel på siden trussel og sikkerhedsrisiko i Microsofts sikkerhedscenter."::: 
 
## <a name="4-understand-emerging-threats"></a>4. Forstå fremspirende trusler

Brug [trusselsanalyser](threat-analytics.md) i Microsoft 365 Defender for at holde dig opdateret om det aktuelle liggende sikkerhedstrusler. Ekspert Microsoft-sikkerhedseksperter laver rapporter, der beskriver de seneste cybertrusler i detaljer, så du kan forstå, hvordan de kan påvirke dit Microsoft 365 abonnement, enheder og brugere. Disse rapporter kan omfatte:

- Aktive trusler og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sårbarheder
- Almindelige angrebsoverflader
- Mest udbredte malware

Trusselsanalyse ser også på din konfiguration og beskeder for at afgøre, hvor risiko du er, og om der er aktive beskeder, der er relevante for en rapport.

Du kan implementere anbefalingerne fra en fremspirende trussel for at styrke din sikkerhed og minimere dit angrebsområde.

Sørg for, at du har tid i din tidsplan til [regelmæssigt at tjekke afsnittet Threat Analytics](threat-analytics.md) på Microsoft 365 Defender-portalen. Se eksemplet [med sikkerhedshandlinger for at få Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) få mere at vide.

## <a name="next-step"></a>Næste trin

[![Trin 1: Lær, hvordan du triager og analyserer hændelser.](../../media/first-incident-overview/first-incident-path-step1.png)](first-incident-analyze.md)

Få mere at vide [om, hvordan du triager og analyserer hændelser](first-incident-analyze.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
