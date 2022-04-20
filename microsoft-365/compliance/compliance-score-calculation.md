---
title: Beregning af overholdelsesscore
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Forstå, hvordan Microsoft Purview Compliance Manager beregner en tilpasset score baseret på handlinger, der udføres for at håndtere risici og forbedre din overholdelse af angivne standarder.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 07a168bd32e73502380260db748fd145648c69ae
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971170"
---
# <a name="compliance-score-calculation"></a>Beregning af overholdelsesscore

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**I denne artikel:** Få mere at vide om, hvordan Overholdelsesstyring beregner en score for overholdelse af angivne standarder for din organisation. I denne artikel forklares det, hvordan **du fortolker din score**, hvad **den grundlæggende vurdering af databeskyttelse** omfatter, **løbende overvågning**, og **hvordan forskellige typer handlinger administreres og scores**.

> [!IMPORTANT]
> Anbefalinger fra Overholdelsesstyring skal ikke fortolkes som en garanti for overholdelse. Det er op til dig at evaluere og validere effektiviteten af kundekontroller i henhold til dit lovgivningsmæssige miljø. Disse tjenester er underlagt vilkårene og betingelserne i [produktvilkårene](https://go.microsoft.com/fwlink/?linkid=2108910). Se også [Microsoft 365 licensvejledning for sikkerhed og overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="how-to-read-your-compliance-score"></a>Sådan læser du din overholdelsesscore

Dashboardet Overholdelsesstyring viser din overordnede score for overholdelse af angivne standarder. Denne score måler dine fremskridt med at fuldføre de anbefalede forbedringshandlinger i kontrolelementerne. Din score kan hjælpe dig med at forstå din nuværende overholdelse af angivne standarder. Det kan også hjælpe dig med at prioritere handlinger baseret på deres potentiale for at reducere risikoen.

En scoreværdi tildeles på tre niveauer:

1. **Score for forbedringshandling**: Hver handling har forskellig indvirkning på din score, afhængigt af den potentielle risiko, der er involveret

2. **Kontrolscore**: Denne score er summen af point, der er optjent ved at gennemføre forbedringshandlinger i kontrolelementet. Denne sum anvendes i sin helhed på din overordnede score for overholdelse af angivne standarder, når kontrolelementet opfylder begge følgende betingelser:
    - **Implementeringsstatus** er lig med **Implementeret** eller **Alternativ implementering**, og
    - **Testresultat er** lig med **Bestået**.

3. **Vurderingsscore**: Denne score er summen af dine kontrolscores. Den beregnes ved hjælp af handlingsscores. Hver Microsoft-handling og hver forbedringshandling, der administreres af din organisation, tælles én gang, uanset hvor ofte der refereres til den i et kontrolelement.

Den overordnede score for overholdelse af angivne standarder beregnes ved hjælp af handlingsscores, hvor hver Microsoft-handling tælles én gang, hver teknisk handling, du administrerer, tælles én gang, og hver ikke-teknisk handling, du administrerer, tælles én gang pr. gruppe. Denne logik er designet til at give den mest nøjagtige bogføring af, hvordan handlinger implementeres og testes i din organisation. Du vil måske bemærke, at det kan medføre, at din overordnede score for overholdelse af angivne standarder afviger fra gennemsnittet af dine vurderingsscores. Læs mere nedenfor om [, hvordan handlinger scores](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Indledende score baseret på Microsoft 365 baseline for databeskyttelse
  
Overholdelsesstyring giver dig en indledende score baseret på Microsoft 365 baseline for databeskyttelse. Denne grundlinje er et sæt kontrolelementer, der omfatter vigtige bestemmelser og standarder for databeskyttelse og generel datastyring. Denne baseline henter elementer primært fra NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) og ISO (International Organization for Standardization) samt fra FedRAMP (Federal Risk and Authorization Management Program) og GDPR (General Data Protection Regulation of the European Union).

Din indledende score beregnes i henhold til standardvurderingen af databeskyttelsesbaser til alle organisationer. Ved dit første besøg indsamler Overholdelsesstyring allerede signaler fra dine Microsoft 365 løsninger. Du kan hurtigt se, hvordan din organisation klarer sig i forhold til vigtige standarder og bestemmelser for databeskyttelse, og se foreslåede forbedringshandlinger.

Da alle organisationer har specifikke behov, er Overholdelsesstyring afhængig af, at du konfigurerer og administrerer vurderinger for at hjælpe med at minimere og reducere risikoen så omfattende som muligt.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Sådan vurderer Overholdelsesstyring løbende kontrolelementer

Overholdelsesstyring identificerer automatisk indstillinger i dit Microsoft 365 miljø, der hjælper med at bestemme, hvornår visse konfigurationer opfylder implementeringskravene til forbedringshandlinger. Overholdelsesstyring registrerer signaler fra andre løsninger til overholdelse af angivne standarder, som du kan have implementeret, herunder administration af datalivscyklus, information beskyttelse, kommunikation med overholdelse af angivne standarder og styring af insiderrisiko, og udnytter også Microsoft Secure Score-overvågning af supplerende forbedringshandlinger.

Din handlingsstatus opdateres på dashboardet inden for 24 timer, efter at der er foretaget en ændring. Når du følger en anbefaling om at implementere et kontrolelement, vil du typisk se, at kontrolelementets status opdateres næste dag.

Hvis du f.eks. aktiverer multifaktorgodkendelse på Azure AD-portalen, registrerer Overholdelsesstyring indstillingen og afspejler den i oplysningerne om adgangsløsningen for kontrolelementet. Omvendt, hvis du ikke aktiverede MFA, markerer Overholdelsesstyring det som en anbefalet handling, du skal udføre.

Få mere at vide om [Secure Score, og hvordan det fungerer](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Handlingstyper og -punkter

Overholdelsesstyring sporer to typer handlinger:

1. **Dine forbedringshandlinger**: handlinger, som din organisation administrerer.
2. **Microsoft-handlinger**: handlinger, som Microsoft administrerer.

Begge typer handlinger har point, der tæller med i din overordnede score, når den er fuldført.

### <a name="technical-and-non-technical-actions"></a>Tekniske og ikke-tekniske foranstaltninger

Handlinger grupperes efter, om de er af teknisk eller ikke-teknisk art. Scorevirkningen af hver handling varierer efter type.

- **Tekniske handlinger** implementeres ved at interagere med teknologien i en løsning (f.eks. ændre en konfiguration). Pointene for tekniske handlinger tildeles én gang pr. handling, uanset hvor mange grupper den tilhører.

- **Ikke-tekniske handlinger** administreres af din organisation og implementeres på andre måder end at arbejde med teknologien i en løsning. Der findes to typer ikke-tekniske handlinger: **dokumentation** og **drift**. Pointene for disse handlinger anvendes på din overholdelsesscore på gruppeniveau. Det betyder, at hvis der findes en handling i flere grupper, modtager du handlingens punktværdi, hver gang du implementerer den i en gruppe.

**Eksempel på, hvordan tekniske og ikke-tekniske handlinger bedømmes:**

Lad os sige, at du har en teknisk handling til en værdi af 3 punkter, der findes i 5 grupper, og at du har en ikke-teknisk handling til en værdi af 3 punkter, der findes i de samme 5 grupper.

Hvis du implementerer den tekniske handling korrekt, er det samlede antal point, du modtager, 3. Det skyldes, at du kun behøver at implementere handlingen én gang for din lejer. Implementerings- og teststatussen for den tekniske handling viser det samme i alle forekomster af den pågældende handling i hver gruppe, den tilhører.

Hvis du implementerer den ikke-tekniske handling i hver af de 5 grupper, er det samlede antal point, du modtager, 15. Det skyldes, at du skal implementere handlingen i hver gruppe. Implementerings- og teststatussen for den ikke-tekniske handling varierer på tværs af grupper, fordi handlingen implementeres separat inden for hver af dens grupper.

Denne resultatlogik er designet til at give den mest nøjagtige bogføring af, hvordan handlinger implementeres og testes i din organisation.

### <a name="how-score-values-are-determined"></a>Sådan bestemmes scoreværdier

Handlinger tildeles en scoreværdi baseret på, om de er obligatoriske eller efter skøn, og om de er forebyggende, detektiv eller korrigerende.

### <a name="mandatory-and-discretionary-actions"></a>Obligatoriske og skønsmæssige handlinger

- **Obligatoriske handlinger** kan ikke tilsidesættes, hverken bevidst eller utilsigtet. Et eksempel på en obligatorisk handling er en centralt administreret adgangskodepolitik, der angiver krav til adgangskodelængde, kompleksitet og udløb. Brugerne skal følge disse krav for at få adgang til systemet.
  
- **Efter skønsmæssige handlinger** er brugerne afhængige af at forstå og overholde en politik. En politik, der f.eks. kræver, at brugerne låser deres computer, når de forlader den, er en skønsmæssig handling, fordi den er afhængig af brugeren.
  
### <a name="preventative-detective-and-corrective-actions"></a>Forebyggende, detektiv- og korrigerende handlinger
  
- **Forebyggende handlinger** håndterer bestemte risici. Beskyttelse af inaktive oplysninger ved hjælp af kryptering er f.eks. en forebyggende handling mod angreb og brud. Adskillelse af opgaver er en forebyggende foranstaltning til at styre interessekonflikter og beskytte mod svig.
  
- **Detektivhandlinger** overvåger aktivt systemer for at identificere uregelmæssige forhold eller adfærd, der udgør en risiko, eller som kan bruges til at opdage indtrængen eller brud. Eksempler omfatter overvågning af systemadgang og privilegerede administrative handlinger. Overvågning af overholdelse af angivne standarder er en type detektivhandling, der bruges til at finde procesproblemer.
  
- **Afhjælpende foranstaltninger** forsøger at holde de negative virkninger af en sikkerhedshændelse på et minimum, træffe korrigerende foranstaltninger for at reducere den øjeblikkelige virkning og vende skaden, hvis det er muligt. Svar på privatlivshændelser er en korrigerende handling for at begrænse skader og gendanne systemer til en driftstilstand efter et brud.
  
Hver handling har en tildelt værdi i Overholdelsesstyring baseret på den risiko, den repræsenterer:

|**Type**|**Tildelt resultat**|
|:-----|:-----|
| Præventivt obligatorisk | 27 |
| Forebyggende skøn | 9 |
| Obligatorisk detektiv | 3 |
| Detektiv efter skøn | 1 |
| Korrigerende krav | 3 |
| Skønsmæssigt korrigerende | 1 |
  
![Værdier for handlingspunkt i Overholdelsesstyring.](../media/compliance-score-action-scoring.png "Værdier for handlingspunkt i Overholdelsesstyring")
