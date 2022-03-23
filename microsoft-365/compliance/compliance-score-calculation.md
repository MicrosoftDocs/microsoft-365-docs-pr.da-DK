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
description: Få mere at vide om, hvordan Microsoft Overholdelsesstyring beregner et personligt score baseret på handlinger, der er taget for at håndtere risici og forbedre din overholdelsesoverholdelse.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9c6667ad9be6164639e65e23fb136de1bc196f60
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589816"
---
# <a name="compliance-score-calculation"></a>Beregning af overholdelsesscore

**I denne artikel:** Få mere at vide om, hvordan Overholdelsesstyring beregner en overholdelsesscore for organisationen. Denne artikel forklarer, hvordan du fortolker dine **resultater**, hvad vurderingen af oprindelig databeskyttelse  **omfatter,** fortløbende overvågning, og hvordan forskellige typer handlinger administreres **og scores**.

> [!IMPORTANT]
> Anbefalinger overholdelsesstyring skal ikke fortolkes som en garanti for overholdelse. Det er op til dig at evaluere og validere effektiviteten af kundekontrolelementer i henhold til dit lovgivningsmiljø. Disse tjenester er underlagt vilkårene og betingelserne i vilkårene [for onlinetjenester](https://go.microsoft.com/fwlink/?linkid=2108910). Se også [Microsoft 365 licenseringsvejledning for sikkerhed og overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="how-to-read-your-compliance-score"></a>Sådan læser du din vurdering af overholdelse

Dashboardet Overholdelsesstyring viser dit overordnede resultat af overholdelse. Dette resultat måler din status for fuldførelse af anbefalede forbedringshandlinger inden for kontrolelementer. Dine resultater kan hjælpe dig med at forstå din aktuelle overholdelsesoverholdelsesoverholdelse. Det kan også hjælpe dig med at prioritere handlinger baseret på deres risiko for at reducere risikoen.

En scoreværdi tildeles på tre niveauer:

1. **Forbedringshandlingsresultat**: Hver handling har forskellige indvirkning på din score afhængigt af den potentielle risiko, der er involveret

2. **Kontrolscore**: Denne score er summen af point, der er optjent ved at fuldføre forbedringshandlinger i kontrolelementet. Denne sum anvendes i sin helhed på dit overordnede overholdelsesresultat, når kontrolelementet opfylder begge følgende betingelser:
    - **Status for implementering** er **lig med** **Implementeret eller Alternativ** implementering, og
    - **Testresultat er** lig med **Bestået**.

3. **Vurderingsresultat**: Dette score er summen af dine kontrolresultater. Det beregnes ved hjælp af handlingsresultater. Hver Microsoft-handling og hver forbedringshandling, der administreres af din organisation, tælles én gang, uanset hvor ofte der refereres til den i et kontrolelement.

Det overordnede pointtal for overholdelse beregnes ved hjælp af handlingsresultater, hvor hver Microsoft-handling tælles én gang, hver teknisk handling, du administrerer, tælles én gang, og hver ikke-teknisk handling, du administrerer, tælles én gang pr. gruppe. Denne logik er designet til at give den mest nøjagtige bogføring af, hvordan handlinger implementeres og testes i organisationen. Du bemærker muligvis, at dette kan medføre, at dit overordnede overholdelsesresultat adskiller sig fra gennemsnittet af dine vurderingsresultater. Læs mere nedenfor om [, hvordan der bliver scoret på handlinger](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Første pointtal baseret på Microsoft 365 grundlinje for databeskyttelse
  
Overholdelsesstyring giver dig et indledende resultat, der er baseret Microsoft 365 grundlinjen for databeskyttelse. Denne grundlinje er et sæt kontrolelementer, der indeholder vigtige bestemmelser og standarder for databeskyttelse og generel datastyring. Denne grundlinje tegner elementer primært fra NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) og ISO (International Organization for Standardization) samt fra FedRAMP (Federal Risk and Authorization Management Program) og GDPR (General Data Protection Regulation of the EU).

Dit første resultat beregnes i henhold til den standardvurdering for oprindelige databeskyttelse, der er leveret til alle organisationer. Ved dit første besøg indsamler Compliance Manager allerede signaler fra dine Microsoft 365 løsninger. Du kan få et hurtigt overblik over, hvordan din organisation klarer sig i forhold til centrale standarder og bestemmelser for databeskyttelse, og se forslag til forbedringshandlinger, der skal udføres.

Da alle organisationer har specifikke behov, er Overholdelsesstyring afhængig af, at du konfigurerer og administrerer vurderinger for at minimere og reducere risikoen så omfattende som muligt.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Sådan vurderer Overholdelsesstyring løbende kontrolelementer

Overholdelsesstyring identificerer automatisk indstillinger i dit Microsoft 365, der hjælper med at bestemme, hvornår visse konfigurationer opfylder krav til implementering af forbedringshandling. Overholdelsesstyring registrerer signaler fra andre løsninger, du muligvis har implementeret, herunder informationsstyring, informationsbeskyttelse, kommunikationsoverholdelse og insider-risikostyring, og udnytter også Microsoft Secure Score-overvågning af supplerende forbedringshandlinger.

Din handlingsstatus opdateres på dashboardet inden for 24 timer efter, at der er foretaget en ændring. Når du følger en anbefaling om at implementere et kontrolelement, vil du normalt få vist status for kontrolelementet opdateret næste dag.

Hvis du f.eks. slår Multi-Factor Authentication (MFA) til i Azure AD-portalen, registrerer Overholdelsesstyring indstillingen og afspejler den i oplysningerne om adgangskontrolløsningen. Hvis du derimod ikke har aktiveret MFA, markerer Overholdelsesstyring denne som en anbefalet handling, du kan gøre.

Få mere at vide [om Secure Score, og hvordan det fungerer](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Handlingstyper og -punkter

Overholdelsesstyring sporer to typer handlinger:

1. **Dine forbedringshandlinger**: handlinger, som din organisation administrerer.
2. **Microsoft-handlinger**: handlinger, som Microsoft administrerer.

Begge typer handlinger har point, der tæller med i dit samlede resultat, når du er færdig.

### <a name="technical-and-non-technical-actions"></a>Tekniske og ikke-tekniske handlinger

Handlinger grupperes efter, om de er af teknisk eller ikke-teknisk karakter. Pointpåvirkningen af hver handling varierer efter type.

- **Tekniske handlinger** implementeres ved at interagere med teknologien i en løsning (f.eks. ved at ændre en konfiguration). Pointene for tekniske handlinger tildeles én gang pr. handling, uanset hvor mange grupper de tilhører.

- **Ikke-tekniske handlinger** administreres af din organisation og implementeres på andre måder end ved arbejde med teknologien i en løsning. Der findes to typer ikke-tekniske handlinger: **dokumentation** og **drift**. Pointene for disse handlinger anvendes på dit overholdelsesresultat på et gruppeniveau. Det betyder, at hvis der findes en handling i flere grupper, modtager du handlingens pointværdi, hver gang du implementerer den i en gruppe.

**Eksempel på, hvordan tekniske og ikke-tekniske handlinger scores:**

Lad os sige, at du har en teknisk handling til 3 point, der findes i 5 grupper, og du har en ikke-teknisk handling, der er 3 point værd, som findes i de samme 5 grupper.

Hvis du har implementeret den tekniske handling, er det samlede antal point, du modtager, 3. Dette skyldes, at du kun behøver at implementere handlingen én gang for din lejer. Status for implementering og test for den tekniske handling vises på samme måde i alle forekomster af den pågældende handling i hver gruppe, den tilhører.

Hvis du implementerer den ikke-tekniske handling i hver af de 5 grupper, er det samlede antal point, du modtager, 15. Dette skyldes, at du skal implementere handlingen i hver gruppe. Status for implementering og test for den ikke-tekniske handling varierer på tværs af grupper, fordi handlingen gennemføres separat i hver af dens grupper.

Denne pointlogik er udviklet til at give den mest nøjagtige bogføring af, hvordan handlinger implementeres og testes i organisationen.

### <a name="how-score-values-are-determined"></a>Sådan bestemmes scoreværdier

Handlinger tildeles en scoreværdi baseret på, om de er obligatoriske eller skønsmæssige, og om de er preventative, resultatbaserede eller afhjælpende.

### <a name="mandatory-and-discretionary-actions"></a>Obligatoriske og efter skønsmæssige handlinger

- **Obligatoriske handlinger** kan ikke tilsidesættes, hverken bevidst eller ved et uheld. Et eksempel på en obligatorisk handling er en centralt administreret adgangskodepolitik, der angiver krav til adgangskodelængde, kompleksitet og udløb. Brugerne skal følge disse krav for at få adgang til systemet.
  
- **Skønsmæssige handlinger** er afhængige af, at brugerne forstår og overholder en politik. En politik, der kræver, at brugerne låser deres computer, når de forlader den, er f.eks. en skønsmæssig handling, fordi den afhænger af brugeren.
  
### <a name="preventative-detective-and-corrective-actions"></a>Undgående, konkrete og afhjælpende handlinger
  
- **Undgående handlinger tager** hånd om specifikke risici. Beskyttelse af in rest-oplysninger ved brug af kryptering er f.eks. en forhindrende handling mod angreb og brud. Adskillelse af pligter er en forhindrende handling til at administrere interessekonflikter og beskytte mod svindel.
  
- **Aktive handlinger overvåger** aktivt systemer for at identificere uregelmæssige betingelser eller funktionsmåder, der repræsenterer risici, eller som kan bruges til at registrere indtrængen eller overtrædelser. Eksempler omfatter overvågning af systemadgang og administrative handlinger med rettigheder. Lovgivningsmæssige revisioner af overholdelse er en slags handling, der anvendes som følge af nye handlinger til at finde procesproblemer.
  
- **Afhjælpende handlinger** forsøger at holde den negative effekt af en sikkerhedshændelse på et minimum, tage korrigerende skridt for at reducere den øjeblikkelige effekt og omvende skaden, hvis det er muligt. Svar på hændelse i forbindelse med beskyttelse af personlige oplysninger er en afhjælpende handling til at begrænse skades- og gendannelsessystemer til en driftstilstand efter brud.
  
Hver handling har en tildelt værdi i Overholdelsesstyring baseret på den risiko, den repræsenterer:

|**Type**|**Tildelt score**|
|:-----|:-----|
| Obligatorisk | 27 |
| Forhindrende skøn | 9 |
| Obligatorisk( (arbejdende) | 3 |
| Efter skøn | 1 |
| Obligatorisk korrigerende | 3 |
| Skøn over afhjælpende | 1 |
  
![Værdier for overholdelsesstyringshandlingspunkt.](../media/compliance-score-action-scoring.png "Handlingspunktværdier i Overholdelsesstyring")