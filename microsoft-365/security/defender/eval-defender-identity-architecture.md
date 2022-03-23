---
title: Gennemgå arkitekturkrav og den tekniske ramme for Microsoft Defender for Identity
description: Det tekniske diagram for Microsoft Defender for Identity i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365 før du opbygger dit prøvelaboratorium eller pilotmiljø.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e534211008ea560642ba306844b9223170ac0140
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593947"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Gennemgå arkitekturkrav og nøglekoncepter for Microsoft Defender for Identity


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 1 af 3](eval-defender-identity-overview.md) i oprettelsen af evalueringsmiljøet for Microsoft Defender for Identity. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-identity-overview.md).

Før du aktiverer Microsoft Defender for Identity, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene.

Microsoft Defender for Identity bruger maskinlæring og adfærdsanalyse til at identificere angreb på tværs af dit lokale netværk samt til at registrere og proaktivt forhindre brugersikkerhedsrisikoen i forbindelse med skyidentiteter. Du kan få mere at vide [under Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)

Defender til identitet beskytter dine lokale Active Directory-brugere og/eller brugere, der er synkroniseret til din Azure Active Directory (Azure AD). Hvis du vil beskytte et miljø, der kun består af Azure AD-brugere, skal du [se Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Følgende diagram illustrerer grundlinjearkitekturen for Defender for Identity. 

![Arkitektur for Microsoft Defender til identitet.](../../media/defender/m365-defender-identity-architecture.png)

I denne illustration:
- De sensorer, der er installeret på AD-domænecontrollere, fortolker logge og netværkstrafik og sender dem til Microsoft Defender for Identity til analyse og rapportering.
-  Sensorerne kan også fortolke Active Directory Federation Services (AD FS), når Azure AD er konfigureret til at bruge federated authentication (stiplede linje i illustration). 
- Microsoft Defender til identitet deler signaler Microsoft 365 Defender til udvidet registrering og svar (XDR).


Defender til identitetssensorer kan installeres direkte på følgende servere:

- Domænecontrollere: Sensoren overvåger direkte domænecontrollerens trafik uden brug af en dedikeret server eller konfiguration af portspejling.
- AD FS: Sensoren overvåger netværkstrafik og godkendelseshændelser direkte.

Se nærmere på arkitekturen for Defender for Identity, herunder integration med Defender til skyapps, under [Microsoft Defender for Identity-arkitektur](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Forstå nøglekoncepter

Følgende tabel identificerede nøglekoncepter, som er vigtige at forstå, når de skal evaluere, konfigurere og udrulle Microsoft Defender for Identity.


|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
| Overvågede aktiviteter | Defender til identitet overvåger signaler, der genereres fra din organisation til at registrere mistænkelig eller ondsindet aktivitet, og hjælper dig med at afgøre gyldigheden af hver potentielle trussel, så du effektivt kan undersøge og reagere.  |  [Overvågede aktiviteter for Microsoft Defender til identitet](/defender-for-identity/monitored-activities)       |
| Sikkerhedsadvarsler    | Defender for Identity Security-beskeder forklarer de mistænkelige aktiviteter, der registreres af sensorerne på dit netværk sammen med de aktører og computere, der er involveret i hver trussel.   | [Microsoft Defender for Identity Security Alerts](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Enhedsprofiler    | Enhedsprofiler giver en omfattende dybdegående undersøgelse af brugere, computere, enheder og ressourcer sammen med deres adgangshistorik.   | [Forstå enhedsprofiler](/defender-for-identity/entity-profiles)  |
| Laterale bevægelsesstier    | En vigtig komponent i MDI-sikkerhedsindsigt er at identificere laterale bevægelsesstier, hvor en hacker bruger ikke-følsomme konti til at få adgang til følsomme konti eller computere i hele netværket.  | [Microsoft Defender for Identity Lateral Movement Paths (LMP'er)](/defender-for-identity/use-case-lateral-movement-path)  |
| Netværksnavnsopløsning    |  Network Name Resolution (NNR) er en komponent af MDI-funktionalitet, der registrerer aktiviteter baseret på netværkstrafik, Windows-hændelser, ETW osv. og korrelerer disse rå data til de relevante computere, der er involveret i hver aktivitet.       | [Hvad er netværksnavnsopløsning?](/defender-for-identity/nnr-policy)      |
| Rapporter    | Defender for Identity-rapporter giver dig mulighed for at planlægge eller straks generere og downloade rapporter, der leverer system- og enhedsstatusoplysninger.  Du kan oprette rapporter om systemsikkerhed, sikkerhedsadvarsler og potentielle senere bevægelsesstier, der er registreret i dit miljø.   | [Microsoft Defender for Identity Reports ](/defender-for-identity/reports)       |
| Rollegrupper    | Defender for Identity giver rollebaserede grupper og delegeret adgang til at beskytte data i henhold til organisationens specifikke behov for sikkerhed og overholdelse, som omfatter Administratorer, Brugere og Seere.        |  [Microsoft Defender for Identity-rollegrupper](/defender-for-identity/role-groups)       |
| Administrativ portal    |  Ud over portalen Microsoft 365 Defender, kan Defender for Identity-portalen bruges til at overvåge og reagere på mistænkelig aktivitet.      | [Arbejde med Microsoft Defender for Identity-portalen](/defender-for-identity/workspace-portal)        |
| Integration af Microsoft Defender til skyapps   | Microsoft Defender til skyapps integreres med Microsoft Defender for Identity for at levere brugerenheds behavioral analytics (UEBA) på tværs af et hybridmiljø – både skyapp og lokalt miljø   | Integration af Microsoft Defender for Identity  |
| | | |


## <a name="review-prerequisites"></a>Gennemgå forudsætninger

Defender for Identity kræver noget påkrævet arbejde for at sikre, at din lokale identitet og netværkskomponenter opfylder minimumskravene. Brug denne artikel som tjekliste for at sikre, at dit miljø er klar: [Forudsætninger for Microsoft Defender til identitet](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet Defender for Identity](eval-defender-identity-enable-eval.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Identity](eval-defender-identity-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md) 
