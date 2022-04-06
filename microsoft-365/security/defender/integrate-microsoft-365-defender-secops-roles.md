---
title: Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og tilsyn
description: Det grundlæggende ved at definere roller, ansvarsområder og tilsyn, når Microsoft 365 Defender integreres i dine sikkerhedsoperationer.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, Microsoft 365, svar på hændelser, cyberangreb, secops, sikkerhedshandlinger, soc
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
ms.openlocfilehash: 5410db413ece81a39453070985e6c744e8b684a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664056"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og tilsyn

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Din organisation skal etablere ejerskab og ansvarlighed for de Microsoft 365 Defender licenser, konfigurationer og administration som indledende opgaver, før der kan defineres driftsroller. Ejerskabet af licenser, abonnementsomkostninger og administration af Microsoft 365- og EMS-tjenester (Enterprise Security + Mobility), som kan omfatte Microsoft 365 Defender, falder typisk uden for SOC-teams (Security Operations Center). SOC-teams bør samarbejde med disse personer for at sikre korrekt tilsyn med Microsoft 365 Defender. 

Mange moderne soc'er tildeler deres teammedlemmer til kategorier baseret på deres færdigheder og funktioner. Eksempel:

- Et trusselsintelligensteam, der er tildelt opgaver, der er relateret til livscyklusstyring af trussels- og analysefunktioner.
- Et overvågningsteam bestående af SOC-analytikere, der er ansvarlige for at vedligeholde logge, beskeder, hændelser og overvågningsfunktioner.
- Et teknisk & driftsteam, der er tildelt tekniker og optimere sikkerhedsenheder.

SOC-teamroller og -ansvar for Microsoft 365 Defender vil naturligvis blive integreret i disse teams.

I følgende tabel beskrives de enkelte SOC-teams roller og ansvarsområder, og hvordan deres roller integreres med Microsoft 365 Defender.

| SOC-team | Roller og ansvarsområder | Microsoft 365 Defender opgaver  |
|:-------|:-----|:-------|
| SOC-tilsyn | <ul><li>Udfører SOC-styring</li><li>Etablerer daglige, ugentlige, månedlige processer</li><li>Giver uddannelse og opmærksomhed</li><li>Ansætter medarbejdere, deltager i peer-grupper og møder</li><li>Udfører blå, rød og lilla holdøvelser</ul>  | <ul><li>Microsoft 365 Defender portaladgangskontrolelementer</li><li>Vedligeholder funktions-/URL-adresse og licensopdateringsregister</li><li>Vedligeholder kommunikation med it-, juridiske, overholdelses- og beskyttelse af personlige oplysninger</li><li>Deltager i ændringskontrolmøder for nye Microsoft 365 eller Microsoft Azure initiativer</ul> |
| Threat Intelligence & Analytics  | <ul><li>Administration af Threat Intel-feed</li><li>Tilskrivning af virus og malware</li><li>Trusselsmodellering & kategoriseringer af trusselshændelser</li><li>Udvikling af attribut for insidertrusler </li><li>Threat Intel Integration with Risk Management-program</li><li>Integrerer dataindsigt med datavidenskab, BI og analyse på tværs af HR-, juridiske, it- og sikkerhedsteams<ul> | <ul><li>Vedligeholder Microsoft Defender for Identity trusselsmodellering</li><li>Vedligeholder Microsoft Defender for Office 365 trusselsmodellering</li><li>Vedligeholder Microsoft Defender for Endpoint trusselsmodellering</ul> |
| Overvågning | <ul><li>Niveau 1, 2, 3 analytikere</li><li>Logfør kildevedligeholdelse og -teknik</li><li>Datakildeindtagelse </li><li>SIEM-fortolkning, beskeder, korrelation, optimering</li><li>Oprettelse af hændelse og besked</li><li>Analyse af hændelser og beskeder</li><li>Rapportering af hændelser og beskeder</li><li>Vedligeholdelse af billetsystem</ul> | Bruger: <ul><li>Security & Compliance Center</li><li>Microsoft 365 Defender portal</ul> |
| Teknisk & SecOps | <ul><li>Administration af sårbarheder for apps, systemer og slutpunkter</li><li>XDR-/SOAR-automatisering</li><li>Test af overholdelse af angivne standarder</li><li>Phishing- og DLP-teknikerarbejde</li><li>Engineering</li><li>Kontrolelementet Koordinater ændres</li><li>Koordinater for opdateringer af runbook</li><li>Indtrængningstest<ul> | <ul><li>Microsoft Defender for Cloud Apps</li><li>Defender for Endpoint</li><li>Defender for Identity</ul> |
| Computer Security Incident Response Team (CSIRT) | <ul><li>Undersøger og reagerer på cyberhændelser</li><li>Udfører tekniske undersøgelser</li><li>**Kan ofte isoleres fra SOC**</ul> | Samarbejd og vedligehold Microsoft 365 Defender playbooks om svar på hændelser |
||||


## <a name="next-step"></a>Næste trin

[Trin 5. Udvikl og test use cases](integrate-microsoft-365-defender-secops-use-cases.md)
