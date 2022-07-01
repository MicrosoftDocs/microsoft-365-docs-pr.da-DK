---
title: Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Compliance Manager hjælper organisationer med at forenkle og automatisere risikovurderinger og foreslår anbefalede handlinger for at hjælpe med at håndtere risici.
ms.openlocfilehash: dc08d38da7c02ef0c02401244934b7d2338ab5f7
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574090"
---
# <a name="microsoft-purview-compliance-manager"></a>Microsoft Purview Compliance Manager

> [!TIP]
> *Vidste du, at du kan prøve premiumversionerne af alle ni Microsoft Purview-løsninger gratis?* Brug den 90-dages prøveversion af Purview-løsninger til at udforske, hvordan robuste Purview-funktioner kan hjælpe din organisation med at opfylde sine behov for overholdelse af angivne standarder. Microsoft 365 E3 og Office 365 E3 kunder kan starte nu ved [Microsoft Purview-compliance-portal prøvehubben](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Få mere at vide om [, hvem der kan tilmelde sig og prøvevilkår](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**I denne artikel:** Få mere at vide om, hvad Overholdelsesstyring er, hvordan det hjælper med at forenkle overholdelse og reducere risikoen og dens vigtigste komponenter.

## <a name="what-is-compliance-manager"></a>Hvad er Overholdelsesstyring?

[Microsoft Purview Compliance Manager](https://compliance.microsoft.com/compliancemanager) er en funktion i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, der hjælper dig med at administrere organisationens overholdelseskrav nemmere og nemmere. Overholdelsesstyring kan hjælpe dig gennem hele overholdelsesrejsen, lige fra opgørelse af dine databeskyttelsesrisici til administration af kompleksiteten ved implementering af kontroller, overholdelse af regler og certificeringer og rapportering til auditører.

Se videoen nedenfor for at få mere at vide om, hvordan Overholdelsesstyring kan hjælpe med at forenkle, hvordan din organisation administrerer overholdelse af angivne standarder:
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4VdoO]

Overholdelsesstyring hjælper med at forenkle overholdelse af angivne standarder og reducere risikoen ved at levere:

- Færdigbyggede vurderinger af almindelige branchestandarder og regionale standarder og forskrifter eller brugerdefinerede vurderinger, der opfylder dine unikke behov for overholdelse af angivne standarder (tilgængelige vurderinger afhænger af din licensaftale; [få mere at vide](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)).

- Arbejdsprocesfunktioner, der kan hjælpe dig med effektivt at fuldføre dine risikovurderinger via et enkelt værktøj.

- Detaljeret trinvis vejledning om foreslåede forbedringshandlinger, der hjælper dig med at overholde de standarder og bestemmelser, der er mest relevante for din organisation. For handlinger, der administreres af Microsoft, kan du se implementeringsoplysninger og overvågningsresultater.

- En risikobaseret overholdelsesscore, der kan hjælpe dig med at forstå din overholdelse af angivne standarder ved at måle dine fremskridt i fuldførelse af forbedringshandlinger.

Oversigtssiden Overholdelsesstyring viser din aktuelle overholdelsesscore, hjælper dig med at se, hvad der kræver opmærksomhed, og hjælper dig med at udføre vigtige forbedringshandlinger. Nedenfor er et eksempel på oversigtssiden:

![Overholdelsesstyring – dashboard.](../media/compliance-manager-overview.png "Oversigtsside for Overholdelsesstyring")

## <a name="understanding-your-compliance-score"></a>Om din overholdelsesscore

Overholdelsesstyring tildeler dig point for at fuldføre forbedringshandlinger, der er truffet for at overholde en forordning, standard eller politik, og kombinerer disse punkter til en samlet score for overholdelse af angivne standarder. Hver handling har forskellig indvirkning på din score afhængigt af de potentielle risici. Din score for overholdelse af angivne standarder kan hjælpe med at prioritere, hvilken handling du skal fokusere på for at forbedre din overordnede overholdelse af angivne standarder.

Overholdelsesstyring giver dig en indledende score baseret på microsoft 365-grundlinjen til databeskyttelse. Denne grundlinje er et sæt kontrolelementer, der omfatter vigtige bestemmelser og standarder for databeskyttelse og generel datastyring.

##### <a name="learn-more"></a>Lær mere

[Forstå, hvordan din overholdelsesscore beregnes](compliance-score-calculation.md).

[Få mere at vide om, hvordan du arbejder med forbedringshandlinger](compliance-manager-improvement-actions.md).

## <a name="key-elements-controls-assessments-templates-improvement-actions"></a>Nøgleelementer: kontrolelementer, vurderinger, skabeloner, forbedringshandlinger

Overholdelsesstyring bruger flere dataelementer til at hjælpe dig med at administrere dine aktiviteter for overholdelse af angivne standarder. Når du bruger Overholdelsesstyring til at tildele, teste og overvåge aktiviteter for overholdelse af angivne standarder, er det nyttigt at have en grundlæggende forståelse af de vigtigste elementer: kontrolelementer, vurderinger, skabeloner og forbedringshandlinger.

### <a name="controls"></a>Kontrol

Et kontrolelement er et krav i en forordning, standard eller politik. Den definerer, hvordan du vurderer og administrerer systemkonfiguration, organisationsproces og personer, der er ansvarlige for at opfylde et specifikt krav i en forordning, standard eller politik.

Overholdelsesstyring sporer følgende typer kontrolelementer:

1. **Microsoft-administrerede kontrolelementer**: kontrolelementer til Microsoft-cloudtjenester, som Microsoft er ansvarlig for at implementere
2. **Dine kontrolelementer**: Nogle gange kaldet kundeadministrerede kontrolelementer, er disse kontrolelementer implementeret og administreret af din organisation
3. **Delte kontrolelementer**: Dette er kontrolelementer, som både din organisation og Microsoft deler ansvaret for at implementere

##### <a name="learn-more"></a>Lær mere

[Overvåg status for dine kontrolelementer](compliance-manager-assessments.md#monitor-assessment-progress-and-controls).

[Få mere at vide om, hvordan Overholdelsesstyring løbende vurderer kontrolelementer](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

### <a name="assessments"></a>Vurderinger

En vurdering er gruppering af kontroller fra en bestemt forordning, standard eller politik. Fuldførelse af handlingerne i en vurdering hjælper dig med at opfylde kravene i en standard, forordning eller lov. Du kan f.eks. have en vurdering af, at når du fuldfører alle handlinger i den, hjælper det at bringe dine Microsoft 365-indstillinger i overensstemmelse med ISO 27001-kravene.

Vurderinger har flere komponenter:

- **Tjenester i omfang**: det specifikke sæt Microsoft-tjenester, der gælder for vurderingen
- **Microsoft-administrerede kontrolelementer**: kontrolelementer til Microsoft-cloudtjenester, som Microsoft implementerer på dine vegne
- **Dine kontrolelementer**: Nogle gange kaldet kundeadministrerede kontrolelementer, er disse kontrolelementer implementeret og administreret af din organisation
- **Delte kontrolelementer**: Dette er kontrolelementer, som både din organisation og Microsoft deler ansvaret for at implementere
- **Vurderingsscore**: Viser dine fremskridt med at opnå samlede mulige point fra handlinger i den vurdering, der administreres af din organisation og af Microsoft

Når du opretter vurderinger, skal du tildele dem til en gruppe. Du kan konfigurere grupper på den måde, der er mest logisk for din organisation. Du kan f.eks. gruppere vurderinger efter revisionsår, område, løsning, teams i din organisation eller på en anden måde. Når du har oprettet grupper, kan du [filtrere dashboardet Overholdelsesstyring](compliance-manager-setup.md#filtering-your-dashboard-view) for at få vist din score efter en eller flere grupper.

##### <a name="learn-more"></a>Lær mere

[Byg og administrer vurderinger i Overholdelsesstyring](compliance-manager-assessments.md).

### <a name="templates"></a>Skabeloner

Overholdelsesstyring indeholder skabeloner, der kan hjælpe dig med hurtigt at oprette vurderinger. Du kan ændre disse skabeloner for at oprette en vurdering, der er optimeret til dine behov. Du kan også oprette en brugerdefineret vurdering ved at oprette en skabelon med dine egne kontrolelementer og handlinger. Det kan f.eks. være, at du ønsker, at en skabelon dækker et internt forretningsproceskontrolelement eller en regional databeskyttelsesstandard, der ikke er dækket af en af vores færdigbyggede vurderingsskabeloner på 325+

##### <a name="learn-more"></a>Lær mere

[Få vist listen over vurderingsskabeloner, der leveres af Overholdelsesstyring](compliance-manager-templates-list.md).

[Få detaljerede instruktioner til oprettelse og ændring af skabeloner til vurderinger](compliance-manager-templates.md).

### <a name="improvement-actions"></a>Forbedringshandlinger

Forbedringshandlinger hjælper med at centralisere dine aktiviteter for overholdelse af angivne standarder. Hver forbedringshandling indeholder anbefalede vejledninger, der er beregnet til at hjælpe dig med at justere i forhold til regler og standarder for databeskyttelse. Forbedringshandlinger kan tildeles til brugere i din organisation for at udføre implementerings- og testarbejde. Du kan også gemme dokumentation, noter og poststatusopdateringer i forbedringshandlingen.

##### <a name="learn-more"></a>Lær mere

[Brug forbedringshandlinger til at administrere arbejdsprocessen for overholdelse af angivne standarder](compliance-manager-improvement-actions.md).

[Få mere at vide om, hvordan handlinger påvirker din score for overholdelse af angivne standarder](compliance-score-calculation.md#action-types-and-points).

## <a name="supported-languages"></a>Understøttede sprog

Overholdelsesstyring er tilgængelig på følgende sprog:

- English
- Bahasa indonesisk
- Bahasa Malaysisk
- Kinesisk (forenklet)
- Kinesisk (traditionelt)
- Czech
- Danish
- Dutch
- Finnish
- French
- German
- Hebrew
- Hungarian
- Italian
- Japanese
- Korean
- Norsk
- Polish
- Portugisisk (Brasiliansk)
- Russian
- Spanish
- Swedish
- Thai
- Turkish

## <a name="next-steps-set-up-and-customize"></a>Næste trin: Konfigurer og tilpas

Få mere at vide om, hvordan du logger på, tildeler tilladelser og roller, konfigurerer indstillinger og tilpasser din dashboardvisning under [Kom i gang med Overholdelsesstyring](compliance-manager-setup.md).

Begynd derefter at tilpasse Overholdelsesstyring for at hjælpe dig med at overholde branchestandarder, der betyder mest for din organisation, ved [at konfigurere vurderinger](compliance-manager-assessments.md).

For at hjælpe dig med at overholde reglerne for beskyttelse af personlige oplysninger har vi udviklet en arbejdsproces, der guider dig gennem en komplette proces for at planlægge og implementere funktioner på tværs af Microsoft 365, herunder ved hjælp af Overholdelsesstyring. Du kan få flere oplysninger under [Udrul beskyttelse af personlige oplysninger for at få regler for beskyttelse af personlige oplysninger med Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy). 
