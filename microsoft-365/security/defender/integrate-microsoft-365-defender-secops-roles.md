---
title: Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og oversigt
description: Grundlæggende om at definere roller, ansvarsområder og oversigter, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, Microsoft 365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
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
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 7562eca50b905bf70f17844cf8fe3079fbf3fc14
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593966"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og oversigt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Din organisation skal etablere ejerskab og ansvar for Microsoft 365 Defender licenser, konfigurationer og administration som indledende opgaver, før driftsroller kan defineres. Typisk falder ejerskabet af licenser, abonnementsomkostninger og administration af Microsoft 365- og Enterprise Security + Mobility-tjenester (som kan omfatte Microsoft 365 Defender) uden for SOC-teams (Security Operations Center). SOC-teams bør arbejde sammen med disse personer for at sikre ordentligt opsyn med Microsoft 365 Defender. 

Mange moderne socs tildeler dens teammedlemmer kategorier baseret på deres færdigheder og funktioner. Eksempel:

- Et trusselsintelligens-team, der er tildelt opgaver i forbindelse med administration af livscyklus for trussels- og analysefunktioner.
- Et overvågningsteam bestående af SOC-analytikere, der er ansvarlige for at vedligeholde logfiler, beskeder, begivenheder og overvågningsfunktioner.
- Et teknisk &, der er tildelt til at manipulere og optimere sikkerhedsenheder.

SOC-teamroller og -ansvarsområder Microsoft 365 Defender integrer naturligt i disse teams.

Følgende tabel opdeler hvert SOC-teams roller og ansvarsområder, og hvordan deres roller integreres med Microsoft 365 Defender.

| SOC-team | Roller og ansvarsområder | Microsoft 365 Defender opgaver  |
|:-------|:-----|:-------|
| SOC-oversigt | <ul><li>Udfører SOC-styring</li><li>Etablerer daglige, ugentlige og månedlige processer</li><li>Giver oplæring og opmærksomhed</li><li>Medarbejdere, deltager i peer-grupper og møder</li><li>Udfører øvelser i blåt, rødt og lilla team</ul>  | <ul><li>Microsoft 365 Defender portaladgangskontrolelementer</li><li>Vedligeholder funktion/URL-adresse og registrering af licenseringsopdatering</li><li>Vedligeholder kommunikationen med it-, juridiske, overholdelses- og privacy-interessenter</li><li>Deltager i møder med kontrol over ændringer for nye Microsoft 365 eller Microsoft Azure tiltag</ul> |
| Threat Intelligence & Analytics  | <ul><li>Administration af Threat Intel-feed</li><li>Tilskrivelse af virus og malware</li><li>Kategorisering & trusselshændelser</li><li>Insider threat Attribute development </li><li>Threat Intel-integration med Risk Management-program</li><li>Integrerer dataindsigt med datavidenskab, BI og analyse på tværs af HR, juridiske, IT og sikkerhedsteams<ul> | <ul><li>Vedligeholder modellering af Microsoft Defender for Identity-trusler</li><li>Vedligeholder Microsoft Defender for Office 365 trusselsmodellering</li><li>Vedligeholder Microsoft Defender til trusselsmodellering i slutpunkter</ul> |
| Overvågning | <ul><li>Niveau 1, 2, 3 analytikere</li><li>Vedligeholdelse og teknik for logfiler</li><li>Datakildeindtrindelse </li><li>SIEM-fortolkninger, påmindelser, korrelation, optimering</li><li>Generering af begivenheder og beskeder</li><li>Analyse af begivenheder og beskeder</li><li>Rapportering af hændelser og beskeder</li><li>Systemvedligeholdelse af billetsystem</ul> | Bruger: <ul><li>Security & Compliance Center</li><li>Microsoft 365 Defender-portal</ul> |
| Teknisk & SecOps | <ul><li>Administration af sikkerhedsrisiko for apps, systemer og slutpunkter</li><li>XDR/SOAR-automatisering</li><li>Test af overholdelse</li><li>Phishing og DLP-teknik</li><li>Teknik</li><li>Kontrolelement for ændring af koordinater</li><li>Koordinatopdateringer til kørselsbogen</li><li>Test af test af test med test af<ul> | <ul><li>Microsoft Defender til skyapps</li><li>Defender til Slutpunkt</li><li>Defender for Identity</ul> |
| Team til svar på computersikkerhedshændelse (CSIRT) | <ul><li>Undersøger og reagerer på cyberhændelser</li><li>Udfører det, der lige er ved at blive beskrifet</li><li>**Kan ofte isoleres fra SOC**</ul> | Samarbejd og vedligehold Microsoft 365 Defender svar om hændelser |
||||


## <a name="next-step"></a>Næste trin

[Trin 5. Udvikle og teste use cases](integrate-microsoft-365-defender-secops-use-cases.md)
