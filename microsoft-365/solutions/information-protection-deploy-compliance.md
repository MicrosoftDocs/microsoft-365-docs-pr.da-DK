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
description: Få mere at vide om, hvordan du bruger Compliance Score og Compliance Manager til at forbedre dit beskyttelsesniveau for personlige data.
ms.openlocfilehash: 5a655d504551e42398cdabbcf7a3f651d788c0ad
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588652"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Brug Overholdelsesstyring til at administrere forbedringshandlinger

Microsoft Compliance Manager kan hjælpe dig med at administrere forbedringer i forbindelse med bestemmelser om beskyttelse af data som f.eks. EU's generelle forordning om databeskyttelse [(GDPR),](/compliance/regulatory/gdpr) [CALIFORNIA Consumer Protection Act CCPA)](/compliance/regulatory/ccpa-faq), HIPAA-HITECH (US Health Care Privacy Act) og LGPD (Brazil Data Protection Act).

Denne artikel indeholder vejledning til brug af dette værktøj til beskyttelse af personlige oplysninger.

> [!NOTE]
> Anbefalinger overholdelsesstyring skal ikke fortolkes som en garanti for overholdelse. Det er op til dig at evaluere og validere effektiviteten af kundekontrolelementer i henhold til dit lovgivningsmiljø. Disse tjenester er underlagt vilkårene og betingelserne i vilkårene [for onlinetjenester](https://go.microsoft.com/fwlink/?linkid=2108910). Se også [Microsoft 365 licenseringsvejledning for sikkerhed og overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Introduktion til Overholdelsesstyring

#### <a name="what-is-compliance-manager"></a>Hvad er Overholdelsesstyring?

[Overholdelsesstyring](../compliance/compliance-manager.md) er et arbejdsprocesbaseret værktøj til risikovurdering i Microsoft 365 Overholdelsescenter til administration af lovgivningsmæssige overholdelsesaktiviteter relateret til Microsofts skytjenester. Som en del af dit Microsoft 365-eller Azure Active Directory-abonnement (Azure AD) hjælper Overholdelsesstyring dig med at administrere overholdelse af lovgivning inden for den fælles ansvarsmodel for Microsofts skytjenester.

**Klar til at bruge bedømmelser**

Compliance Manager indeholder indbyggede skabeloner til at [](../compliance/compliance-manager-assessments.md) opbygge vurderinger, der er justeret i forhold til regler, der er relateret til beskyttelse af personlige oplysninger, som f.eks. GDPR og HIPAA/HITECH. Skabelonerne har indbygget kontroltilknytning, som kan hjælpe dig med at træffe forbedringshandlinger, så du kan opfylde kravene i forordningen. Hver vurdering indeholder oplysninger om de kontrolelementer, som hver enkelt forordning kræver specifikt for destinationstjenesten, opdelt efter de kontrolelementer, du administrerer og styrer, som Microsoft administrerer.

Ved hjælp af en færdigbyggede skabelon kan du hurtigt komme i gang med risikovurderingr. Efterhånden som du bliver mere orienteret i brugen af Overholdelsesstyring, kan du tilpasse en indbygget skabelon ved at tilføje dine egne kontrolelementer og forbedringshandlinger, eller du kan oprette dine egne brugerdefinerede vurderinger, der passer til din organisations behov.

Få vist den [komplette liste over bedømmelsesskabeloner](../compliance/compliance-manager-templates-list.md) , der leveres af Overholdelsesstyring.

**Overholdelsesscore i realtid**

Overholdelsesstyring giver dig også et resultat af overholdelse, der måler dit fremskridt med at fuldføre anbefalede forbedringshandlinger inden for kontrolelementer. Du kan bruge denne score til at overvåge dine fremskridt og prioritere handlinger baseret på deres risiko for at reducere risikoen.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Brug startvejledningen til Overholdelsesstyring

[Startvejledningen til Overholdelsesstyring](../compliance/compliance-manager-quickstart.md) indeholder trinvise trin og links til vigtige ressourcer, der kan hjælpe dig med at arbejde med Overholdelsesstyring:

- [Første besøg: Bliv fortrolig med Overholdelsesstyring](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Arbejde med dashboardet i Overholdelsesstyring
    - Forstå din vurdering af overholdelse af regler og standarder
    - Learning om forbedringshandlinger
    - Forstå bedømmelser og skabeloner
- [Fremskyndet konfiguration: Konfigurer Overholdelsesstyring til at administrere dine overholdelsesaktiviteter](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Opbygning og administration af din første vurdering
    - Udføre implementerings- og testarbejde med forbedringshandlinger for at fuldføre kontrolelementer i dine bedømmelser
    - Forstå, hvordan forskellige handlinger påvirker dit resultat af overholdelse
- [Skalering: Brug avanceret funktionalitet til at opfylde dine brugerdefinerede behov](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Opret dine brugerdefinerede bedømmelser for at spore ikke-Microsoft 365 produkter
    - Ændring af eksisterende skabeloner for at tilføje eller fjerne kontrolelementer
    - Konfiguration af automatiserede test af forbedringshandlinger

## <a name="how-your-compliance-score-is-calculated"></a>Sådan beregnes din overholdelsesscore

Dit overholdelsesresultat beregnes på baggrund af en kombination af Microsoft- og kunde-administrerede kontrolimplementeringene. Se beregning [af overholdelsesscore](../compliance/compliance-score-calculation.md) for at få en detaljeret forklaring.

Kontrolelementer tildeles en scoreværdi baseret på, om de er obligatoriske eller skønsmæssige, og om de er preventative, resultatbaserede eller afhjælpende. Disse repræsenterer samlet risikoen ved ikke at implementere den i forhold til andre kontrolelementer.

Som det præsenteres i artiklen om beregning af overholdelsesscore, får forhindrende kontroller et resultat, der er højere end resultat, og obligatoriske kontroller får et resultat, der er højere end skønsmæssige.

Brugergrænsefladen for overholdelsesscore for administratorer viser ikke disse parametre, og den giver heller ikke mulighed for at filtrere efter dem. Men hvis du henter den tilknyttede skabelon fra Overholdelsesstyring, angiver det resulterende datasæt disse parametre for de fleste bestemmelser.

For tekniske kontroller opdaterer Overholdelsesstyring automatisk resultatet af forbedringshandlingen, når handlingen er blevet implementeret og testet. Andre ikke-tekniske&mdash; kontrolhandlinger, f.eks. handlinger, der er driftsrelaterede eller relateret til dokumentation, skal registreres&mdash; manuelt som implementeret før punkter tæller i din score.

&mdash;&mdash;Du kan også implementere visse forbedringshandlinger til andre formål, f.eks. brug af opbevaringsmærkater af andre årsager end overholdelse af regler om beskyttelse af personlige oplysninger, så du ville få kredit for at bruge en sådan funktion, selvom den bruges til andre formål og ikke en del af en velovervejet handling til overholdelse af regler og standarder.

Dit resultat af overholdelse af angivne standarder skal betragtes som en relativ måling til sporing af forbedringer i bred skala. Du bør ikke finde dig et perfekt resultat.

## <a name="additional-guidance"></a>Yderligere vejledning

Her er et par vigtige tip til, hvordan du kan bruge Overholdelsesstyring til at opnå overholdelse af regler og standarder for beskyttelse af personlige oplysninger for data:

- Hver forordning om beskyttelse af personlige oplysninger for data har en kombination af tekniske kontroller, specifikationer for dokumentation samt krav til drift, proces og rapportering. Alle disse vises i forbedringshandlingerne.

- Hvis du vil fokusere visningen af forbedringshandlinger til dit interesseområde, kan du filtrere efter handlingstype under  fanen Løsninger i administratoren af Overholdelsesstyring. Få mere at vide [om filtrering af dashboardvisningen i Overholdelsesstyring](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- Den relative betydning og prioritet af forbedringshandlinger, der identificeres i Overholdelsesstyring, bør tages i betragtning som en del af en bredere risikogennemgang sammen med den risiko for beskyttelse af personlige oplysninger, du har fastsat, at din organisation skal administrere.

- Selv med sammenlægning af forbedringshandlinger på tværs af flere lovmæssige krav, vil LGPD, CCPA og HIPAA-HITECH f.eks. blive markeret med næsten 400 forbedringshandlinger i Overholdelsesstyring. For bedre at håndtere denne lange liste skal du bruge filteret til forbedringshandling til at reducere resultatsættet til en liste, der er mere overskuelig.

- Filteret Kategorier giver dig en måde at filtrere forbedringshandlinger på ved hjælp af logisk gruppering, som artiklerne Spor, Forebyd, Beskyt, Behold og Undersøg i denne overordnede løsning er justeret efter.

- Nogle af de kontrolelementer, der er angivet i forbedringshandlingerne, kan betragtes som mere direkte forbundet med en bestemt lovgivningsartikel, mens andre kontroller kan være mere indirekte forbundet med lovgivningens mål, og mange gange er blot anbefalede aktiviteter eller bedste praksis.