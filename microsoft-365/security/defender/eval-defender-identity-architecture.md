---
title: Gennemse arkitekturkrav og den tekniske struktur for Microsoft Defender for Identity
description: Det tekniske diagram til Microsoft Defender for Identity i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365, før du bygger dit prøvelaboratorium eller pilotmiljø.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: e92fa629b49664b6f87c8e72c23a2f9cae74afe6
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750226"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-identity"></a>Gennemse arkitekturkrav og nøglebegreber for Microsoft Defender for Identity


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 1 af 3](eval-defender-identity-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Identity. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-identity-overview.md).

Før du aktiverer Microsoft Defender for Identity, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene.

Microsoft Defender for Identity bruger maskinel indlæring og adfærdsanalyser til at identificere angreb på tværs af dit lokale netværk sammen med at registrere og proaktivt forhindre brugerlogonrisici, der er knyttet til cloudidentiteter. Du kan få flere oplysninger under [Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)

Defender for Identity beskytter dine Active Directory i det lokale miljø brugere og/eller brugere, der er synkroniseret med dit Azure Active Directory (Azure AD). Hvis du vil beskytte et miljø, der kun består af Azure AD brugere, skal du se [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

## <a name="understand-the-architecture"></a>Forstå arkitekturen

I følgende diagram illustreres grundarkitekturen for Defender for Identity. 

:::image type="content" source="../../media/defender/m365-defender-identity-architecture.png" alt-text="Identitetsarkitekturen for Microsoft Defender for Identity" lightbox="../../media/defender/m365-defender-identity-architecture.png":::

I denne illustration:

- Sensorer, der er installeret på AD-domænecontrollere, fortolker logge og netværkstrafik og sender dem til Microsoft Defender for Identity til analyse og rapportering.
-  Sensorer kan også fortolke Active Directory Federation Services (AD FS), når Azure AD er konfigureret til at bruge godkendelse i organisationsnetværket (stiplede linjer i illustration). 
- Microsoft Defender for Identity deler signaler til Microsoft 365 Defender for udvidet registrering og svar (XDR).

Defender for Identity-sensorer kan installeres direkte på følgende servere:

- Domænecontrollere: Sensoren overvåger direkte trafikken på domænecontrollere uden behov for en dedikeret server eller konfiguration af portspejling.
- AD FS: Sensoren overvåger direkte netværkstrafik og godkendelseshændelser.

Hvis du vil vide mere om arkitekturen i Defender for Identity, herunder integration med Defender for Cloud Apps, [skal du se Microsoft Defender for Identity arkitektur](/defender-for-identity/architecture).


## <a name="understand-key-concepts"></a>Forstå vigtige begreber

I følgende tabel identificeres vigtige begreber, der er vigtige at forstå, når du evaluerer, konfigurerer og udruller Microsoft Defender for Identity.

|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
| Overvågede aktiviteter | Defender for Identity overvåger signaler, der genereres fra din organisation, for at registrere mistænkelig eller skadelig aktivitet og hjælper dig med at fastslå gyldigheden af hver potentiel trussel, så du effektivt kan triage og reagere.  |  [Microsoft Defender for Identity overvågede aktiviteter](/defender-for-identity/monitored-activities)       |
| Sikkerhedsadvarsler    | Sikkerhedsbeskeder fra Defender for Identity forklarer de mistænkelige aktiviteter, der registreres af sensorer på dit netværk, sammen med de aktører og computere, der er involveret i hver trussel.   | [sikkerhedsbeskeder Microsoft Defender for Identity](/defender-for-identity/suspicious-activity-guide?tabs=external)    |
| Enhedsprofiler    | Enhedsprofiler giver en omfattende detaljeret gennemgang af brugere, computere, enheder og ressourcer sammen med deres adgangshistorik.   | [Om enhedsprofiler](/defender-for-identity/entity-profiles)  |
| Tværgående bevægelsesstier    | En vigtig komponent i MDI-sikkerhedsindsigt er at identificere tværgående bevægelsesstier, hvor en hacker bruger ikke-følsomme konti til at få adgang til følsomme konti eller computere på hele netværket.  | [Microsoft Defender for Identity tværgående bevægelsesstier](/defender-for-identity/use-case-lateral-movement-path)  |
| Løsning af netværksnavn    |  NNR (Network Name Resolution) er en komponent i MDI-funktionalitet, der registrerer aktiviteter, der er baseret på netværkstrafik, Windows-hændelser, ETW osv., og korrelerer disse rådata med de relevante computere, der er involveret i hver aktivitet.       | [Hvad er løsning på netværksnavn?](/defender-for-identity/nnr-policy)      |
| Rapporter    | Defender for Identity-rapporter giver dig mulighed for at planlægge eller straks generere og downloade rapporter, der indeholder oplysninger om system- og enhedsstatus.  Du kan oprette rapporter om systemtilstand, sikkerhedsbeskeder og potentielle tværgående bevægelsesstier, der er registreret i dit miljø.   | [Microsoft Defender for Identity rapporter](/defender-for-identity/reports)       |
| Rollegrupper    | Defender for Identity tilbyder rollebaserede grupper og uddelegeret adgang for at beskytte data i henhold til organisationens specifikke behov for sikkerhed og overholdelse af angivne standarder, som omfatter administratorer, brugere og seere.        |  [Microsoft Defender for Identity rollegrupper](/defender-for-identity/role-groups)       |
| Administrationsportal    |  Ud over Microsoft 365 Defender-portalen kan Defender for Identity-portalen bruges til at overvåge og reagere på mistænkelig aktivitet.      | [Arbejde med Microsoft Defender for Identity-portalen](/defender-for-identity/workspace-portal)        |
| Microsoft Defender for Cloud Apps integration   | Microsoft Defender for Cloud Apps kan integreres med Microsoft Defender for Identity for at levere UEBA (user entity behavioral analytics) på tværs af et hybridmiljø – både cloudapp og i det lokale miljø   | Microsoft Defender for Identity integration  |

## <a name="review-prerequisites"></a>Gennemse forudsætninger

Defender for Identity kræver noget forudsætningsarbejde for at sikre, at dine identitets- og netværkskomponenter i det lokale miljø opfylder minimumskravene. Brug denne artikel som en tjekliste til at sikre, at dit miljø er klar: [Microsoft Defender for Identity forudsætninger](/defender-for-identity/prerequisites).


## <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet Defender for Identity](eval-defender-identity-enable-eval.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Identity](eval-defender-identity-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md) 
