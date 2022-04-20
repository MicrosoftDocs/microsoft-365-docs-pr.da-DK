---
title: Brug Overholdelsesstyring til at administrere forbedringshandlinger
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
description: Få mere at vide om, hvordan du bruger Overholdelsesscore og Overholdelsesstyring til at forbedre dit beskyttelsesniveau for personlige data.
ms.openlocfilehash: 469584abbf784fe6c556aab14a49a5ed44280a69
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947445"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Brug Overholdelsesstyring til at administrere forbedringshandlinger

Microsoft Purview Compliance Manager kan hjælpe dig med at administrere forbedringer relateret til bestemmelser om beskyttelse af personlige oplysninger, f.eks. EU's [generelle forordning om databeskyttelse (GDPR),](/compliance/regulatory/gdpr) [California Consumer Protection Act CCPA)](/compliance/regulatory/ccpa-faq), HIPAA-HITECH (US Health Care Privacy Act) og LGPD (Brasilien Data Protection Act).

Denne artikel indeholder en vejledning i brugen af dette værktøj til beskyttelse af personlige oplysninger.

> [!NOTE]
> Anbefalinger fra Overholdelsesstyring skal ikke fortolkes som en garanti for overholdelse. Det er op til dig at evaluere og validere effektiviteten af kundekontroller i henhold til dit lovgivningsmæssige miljø. Disse tjenester er underlagt vilkårene og betingelserne i [vilkår og betingelser for onlinetjenester](https://go.microsoft.com/fwlink/?linkid=2108910). Se også [Microsoft 365 licensvejledning for sikkerhed og overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Introduktion til Overholdelsesstyring

#### <a name="what-is-compliance-manager"></a>Hvad er Overholdelsesstyring

[Overholdelsesstyring](../compliance/compliance-manager.md) er et arbejdsprocesbaseret risikovurderingsværktøj på Microsoft Purview-overholdelsesportalen til administration af aktiviteter for lovmæssig overholdelse af angivne standarder, der er relateret til Microsoft-cloudtjenester. Som en del af dit azure AD-abonnement (Microsoft 365 eller Azure Active Directory) hjælper Overholdelsesstyring dig med at administrere lovmæssig overholdelse inden for modellen med delt ansvar for Microsofts cloudtjenester.

**Klar til brug af vurderinger**

Overholdelsesstyring indeholder færdigbyggede skabeloner til [oprettelse af vurderinger](../compliance/compliance-manager-assessments.md) , der er justeret i forhold til bestemmelser vedrørende beskyttelse af personlige oplysninger, f.eks. GDPR og HIPAA/HITECH. Skabelonerne har indbygget kontroltilknytning, der kan hjælpe dig med at udføre forbedringshandlinger for at opfylde forordningens krav. Hver vurdering indeholder oplysninger om de kontrolelementer, som hver forordning kræver, og som er specifikke for måltjenesten, opdelt efter kontrolelementer, du administrerer og styrer, som Microsoft administrerer.

Brug af en færdigbygget skabelon hjælper dig med hurtigt at komme i gang med risikovurderinger. Efterhånden som du bliver mere kvalificeret til at bruge Overholdelsesstyring, kan du tilpasse en færdigbygget skabelon ved at tilføje dine egne kontrolelementer og forbedringshandlinger, eller du kan oprette dine egne brugerdefinerede vurderinger, der passer til din organisations behov.

Få vist den [komplette liste over vurderingsskabeloner](../compliance/compliance-manager-templates-list.md) , der leveres af Overholdelsesstyring.

**Score for overholdelse af angivne standarder i realtid**

Overholdelsesstyring giver dig også en overholdelsesscore, der måler dit fremskridt med at fuldføre de anbefalede forbedringshandlinger i kontrolelementerne. Du kan bruge denne score til at overvåge din status og prioritere handlinger baseret på deres potentiale for at reducere risikoen.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Brug hurtig start-vejledningen til Overholdelsesstyring

Vejledning til [hurtig start i Overholdelsesstyring](../compliance/compliance-manager-quickstart.md) indeholder trinvise trin og links til vigtige ressourcer, der kan hjælpe dig med at arbejde med Overholdelsesstyring:

- [Første besøg: Bliv fortrolig med Overholdelsesstyring](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Arbejde med dashboardet Overholdelsesstyring
    - Om din overholdelsesscore
    - Learning om forbedringshandlinger
    - Om vurderinger og skabeloner
- [Oprulning: Konfigurer Overholdelsesstyring til at administrere dine aktiviteter for overholdelse af angivne standarder](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Oprettelse og administration af din første vurdering
    - Udførelse af implementerings- og testarbejde på forbedringshandlinger for at fuldføre kontrolelementer i dine vurderinger
    - Forstå, hvordan forskellige handlinger påvirker din score for overholdelse af angivne standarder
- [Opskalering: Brug avanceret funktionalitet til at opfylde dine brugerdefinerede behov](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Oprettelse af dine brugerdefinerede vurderinger for at spore produkter, der ikke er Microsoft 365
    - Ændring af eksisterende skabeloner for at tilføje eller fjerne kontrolelementer
    - Konfiguration af automatiseret test af forbedringshandlinger

## <a name="how-your-compliance-score-is-calculated"></a>Få mere at vide om, hvordan din overholdelsesscore beregnes

Din overholdelsesscore beregnes på baggrund af en kombination af Microsoft- og kundeadministrerede kontrolimplementeringer. Se [beregningen af overholdelsesscoren](../compliance/compliance-score-calculation.md) for at få en detaljeret forklaring.

Kontrolelementer tildeles en scoreværdi baseret på, om de er obligatoriske eller efter skøn, og om de er forebyggende, detektiv eller korrigerende. Disse repræsenterer tilsammen risikoen for ikke at implementere den i forhold til andre kontrolelementer.

Som vist i artiklen om beregning af overholdelsesscoren får forebyggende kontrolelementer en højere score end detektiv- og korrigerende kontrolelementer, og obligatoriske kontroller får en højere score end efter skøn.

Brugergrænsefladen for administration af overholdelsesscorer indeholder ikke disse parametre og giver heller ikke mulighed for at filtrere efter dem. Men hvis du downloader den tilknyttede skabelon fra Overholdelsesstyring, vises disse parametre for de fleste regler i det resulterende datasæt.

I forbindelse med tekniske kontrolelementer opdaterer Overholdelsesstyring automatisk forbedringshandlingsscoren, når handlingen er blevet implementeret og testet. Andre ikke-tekniske kontrolhandlinger&mdash;, f.eks. handlinger, der er driftsrelaterede eller relateret til dokumentation&mdash;, skal registreres manuelt som implementeret, før punkter tæller med i din score.

Du mange implementerer også visse forbedringshandlinger til andre formål&mdash;, f.eks. brug af opbevaringsmærkater af andre årsager end overholdelse af regler&mdash; for beskyttelse af personlige oplysninger, så du ville få kredit for at bruge en sådan funktion, selvom den bruges til andre formål og ikke er en del af en bevidst overholdelseshandling.

Din overholdelsesscore bør betragtes som en relativ måling til sporing af forbedringer i stor skala. Du bør ikke forfølge en perfekt score.

## <a name="additional-guidance"></a>Yderligere vejledning

Her er nogle få vigtige tip til, hvordan du bruger Overholdelsesstyring til at hjælpe dig med at opnå overholdelse af regler for beskyttelse af personlige oplysninger:

- Hver forordning om beskyttelse af personlige oplysninger har en kombination af tekniske kontroller, dokumentationsspecifikationer og driftsmæssige, proces- og rapporteringskrav. Alle disse vises i forbedringshandlinger.

- Hvis du vil fokusere visningen af forbedringshandlinger på dit interesseområde, kan du filtrere efter handlingstype under fanen **Løsninger** i administratoren af Overholdelsesstyring. Få mere at vide om [filtrering af dashboardvisningen Overholdelsesstyring](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- Den relative vigtighed og prioritet af forbedringshandlinger, der er identificeret i Overholdelsesstyring, bør betragtes som en del af en bredere risikogennemgang sammen med den risiko for beskyttelse af personlige oplysninger, du har bestemt, at din organisation skal administrere.

- Selv med sammenlægning af forbedringshandlinger på tværs af flere lovmæssige krav, vil næsten 400 forbedringshandlinger blive angivet i Overholdelsesstyring, hvis skabeloner til vurdering af regulering for GDPR, LGPD, CCPA og HIPAA-HITECH vælges. Hvis du bedre vil håndtere denne lange liste, skal du bruge handlingsfilteret til forbedring for at reducere resultatsættet til en liste, der kan administreres.

- Filteret Kategorier er en metode til at filtrere forbedringshandlinger efter logisk gruppering, som artiklerne Spor, Undgå, Beskyt, Bevar og Undersøg i denne overordnede løsning justeres i forhold til.

- Nogle af de kontroller, der er opført i forbedringsaktionerne, kan betragtes som mere direkte knyttet til en bestemt regelartikel, mens andre kontroller kan være mere indirekte forbundet med ånden i en forordning, og mange gange er blot anbefalede aktiviteter eller bedste praksis.