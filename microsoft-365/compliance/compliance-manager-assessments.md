---
title: Byg og administrer bedømmelser i Microsoft Compliance Manager
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
search.appverid:
- MOE150
- MET150
description: Opbyg vurderinger i Microsoft Compliance Manager, som kan hjælpe dig med at overholde kravene til bestemmelser og certificeringer, der er vigtige for din organisation.
ms.openlocfilehash: fb30fd8f55172890507b82910630e7202de0d996
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63591459"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Opbygge og administrere bedømmelser i Overholdelsesstyring

**I denne artikel:** Få mere at vide om, hvordan du tilpasser Overholdelsesstyring for din organisation ved at oprette **og administrere bedømmelser**. I denne artikel får du en gennemgang af, hvordan du opretter bedømmelser, hvordan du organiserer dem i **grupper, arbejder** med **kontrolelementer, accepterer** opdateringer og eksporterer **bedømmelsesrapporter**.

## <a name="introduction-to-assessments"></a>Introduktion til bedømmelser

Overholdelsesstyring hjælper dig med at oprette vurderinger, der evaluerer din overholdelse af branche og regionale bestemmelser, der gælder for din organisation. Bedømmelser er bygget på rammen af bedømmelsesskabeloner, som indeholder de nødvendige kontrolelementer, forbedringshandlinger og, hvor det er relevant, Microsoft-handlinger til at fuldføre vurderingen. Konfiguration af de mest relevante evalueringer for organisationen kan hjælpe dig med at implementere politikker og driftsprocedurer for at begrænse risikoen for overholdelse.

Alle dine bedømmelsesvurderinger er anført på fanen bedømmelser i Overholdelsesstyring. Få mere at [vide om, hvordan du filtrerer din visning af dine bedømmelser og fortolker statustilstande](compliance-manager-setup.md#assessments-page).

> [!IMPORTANT]
> De skabeloner, der er tilgængelige for din organisation til evaluering af bygninger, afhænger af din licensaftale. [Gennemgå licensoplysningerne](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="data-protection-baseline-default-assessment"></a>Standardvurdering for standardvurdering for databeskyttelse

For at komme i gang giver Microsoft en **standardvurdering** i Compliance Manager for Microsoft 365 **grundlinjen til databeskyttelse**. Denne oprindelige vurdering har et sæt kontrolelementer til vigtige bestemmelser og standarder for databeskyttelse og generel datastyring. Denne grundlinje tegner elementer primært fra NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) og ISO (International Organization for Standardization) samt fra FedRAMP (Federal Risk and Authorization Management Program) og GDPR (General Data Protection Regulation of the EU).

Denne vurdering bruges til at beregne dit første overholdelsesresultat, første gang du kommer til Overholdelsesstyring, før du konfigurerer andre vurderinger. Overholdelsesstyring indsamler indledende signaler fra dine Microsoft 365 løsninger. Du kan få et hurtigt overblik over, hvordan din organisation klarer sig i forhold til centrale standarder og bestemmelser for databeskyttelse, og se forslag til forbedringshandlinger, der skal udføres.

Overholdelsesstyring bliver mere praktisk, når du opbygger og administrerer dine egne bedømmelser, der opfylder din organisations særlige behov.

## <a name="understand-groups-before-creating-assessments"></a>Forstå grupper, før du opretter bedømmelser

Når du opretter en bedømmelsesvurdering, skal du tildele den til en gruppe. Grupper er beholdere, som giver dig mulighed for at organisere bedømmelser på en måde, der er logisk for dig, f.eks. efter år eller lovgivning eller baseret på din organisations divisioner eller geografiske områder. Derfor anbefaler vi, at du planlægger en grupperingsstrategi, før du opretter vurderinger.

Nedenfor finder du eksempler på to grupper og deres underliggende vurderinger:

- **FFIEC IS assessment 2020**
  - FFIEC IS
- **Vurdering af datasikkerhed og beskyttelse af personlige oplysninger**
  - ISO 27001:2013
  - ISO 27018:2014

Forskellige bedømmelser inden for en gruppe eller grupper kan dele forbedringshandlinger. Forbedringshandlinger kan være ændringer, du foretager inden for tekniske løsninger, der er knyttet til din lejer, f.eks. aktivering af tofaktorgodkendelse eller ikke-tekniske handlinger, du udfører uden for systemet, f.eks. Eventuelle opdateringer i detaljer eller status, som du foretager af en teknisk forbedring, vil blive valgt af bedømmelser på tværs af alle grupper. Ikke-tekniske handlingsopdateringer genkendes af bedømmelser i den gruppe, hvor du anvender dem. Dette giver dig mulighed for at implementere én forbedringshandling og opfylde flere krav på samme tid.

### <a name="create-a-group"></a>Opret en gruppe

Du kan oprette en gruppe, mens du opretter en ny vurdering. Grupper kan ikke oprettes som enkeltstående enheder.

### <a name="what-to-know-when-working-with-groups"></a>Hvad du skal vide, når du arbejder med grupper

- En gruppe skal indeholde mindst én vurdering.
- Gruppenavne skal være entydige i din organisation.
- Grupper har ikke sikkerhedsegenskaber. Alle tilladelser er knyttet til bedømmelser.
- Når du har føjet en bedømmelsesvurdering til en gruppe, kan gruppering ikke ændres.
- Hvis du føjer en ny vurdering til en eksisterende gruppe, kopieres fælles oplysninger fra bedømmelser i den pågældende gruppe til den nye vurdering.
- Relaterede kontrolfunktioner til bedømmelser i forskellige bedømmelser i den samme gruppe opdateres automatisk, når de er gennemført.
- Grupper kan indeholde bedømmelser for den samme certificering eller forordning, men hver gruppe kan kun indeholde én vurdering for et bestemt produktcertificeringspar. En gruppe kan f.eks. ikke indeholde to bedømmelser for Office 365 og NIST CSF. En gruppe kan kun indeholde flere bedømmelser for det samme produkt, hvis den tilsvarende certificering eller forordning for hver enkelt er forskellig.
- Hvis du sletter en bedømmelsesvurdering, brydes relationen mellem den pågældende bedømmelsesvurdering og gruppen.
- Grupper kan ikke slettes.

## <a name="understand-templates-before-creating-assessments"></a>Forstå skabeloner, før du opretter bedømmelser

Bedømmelsesskabeloner indeholder kontrolelementer og handlingsanbefalinger til bedømmelser, der er baseret på certificeringer til forskellige regler og standarder for beskyttelse af personlige oplysninger. Din organisations tilgængelige skabeloner kan indeholde en eller flere skabeloner, som blev inkluderet som en del af din licensaftale, sammen med eventuelle yderligere førsteklasses skabeloner, du har købt.

Hver skabelon, uanset om den er inkluderet eller premium, findes i to versioner: én til brug med Microsoft 365 (eller andre Microsoft-produkter, som tilgængelige), og en universel version, der kan skræddersyet til at vurdere andre produkter, du bruger. Du kan vælge den relevante skabelontype for det produkt, du vil vurdere.

Du kan få mere at vide om skabeloner under [Arbejde med bedømmelsesskabeloner](compliance-manager-templates.md).

## <a name="create-assessments"></a>Opret bedømmelser

> [!NOTE]
> Kun brugere, der har en global administrator, overholdelsesstyringsadministration eller overholdelsesadministratorvurderingsrolle kan oprette og ændre bedømmelser. Få mere at [vide om roller og tilladelser](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

Før du begynder, skal du sikre dig, at du ved, hvilken gruppe du vil tildele den til, eller være forberedt på at oprette en ny gruppe til denne vurdering. Læs mere om [grupper og bedømmelser](#understand-groups-before-creating-assessments).

For at oprette en bedømmelsesvurdering bruger du en guidet proces til at vælge en skabelon og angive det tilknyttede produkt. På siden **Bedømmelser** anbefaler vi, at du starter med Tilføj anbefalede bedømmelser **, som** hjælper dig med at identificere og hurtigt konfigurere de mest relevante bedømmelser for din organisation på én gang. Du kan også konfigurere bedømmelsesvurderinger én ad gangen ved at vælge **Tilføj bedømmelsesvurdering**. Følg nedenstående trin for at begynde at opbygge vurderinger.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Opret bedømmelser baseret på anbefalinger til din organisationstype

Overholdelsesstyring kan angive, hvilke bedømmelser der kan være mest relevante for din organisation. Når du giver grundlæggende oplysninger om din organisations branche og placeringer, anbefaler vi, hvilke skabeloner du kan bruge fra vores bibliotek med mere end 300 skabeloner. Du skal blot vælge mellem de anbefalede skabeloner til hurtig konfiguration af flere bedømmelsesvurderinger på én gang. 

Hvis du vil oprette en eller flere bedømmelser baseret på vores anbefalinger, skal du vælge Tilføj anbefalede bedømmelser fra **siden Bedømmelser** og følge disse trin:
   - Vælg en eller flere brancher, der identificerer din organisation, og vælg derefter **Næste**
   - Vælg et eller flere områder til din organisations placering, og vælg derefter **Næste**
   - På **skærmbilledet Vælg bedømmelsesvurdering** skal du vælge rullepilen  ud for Anbefalede skabeloner for at få vist en liste over bedømmelser, vi mener gælder for din organisation. Markér afkrydsningsfelterne ud for de skabeloner, du vil bruge til at oprette bedømmelsesvurderinger, og vælg derefter **Næste**.
   - Gennemgå dine endelige valg, og vælg **Tilføj anbefalede bedømmelser for** at oprette dine nye bedømmelser.

#### <a name="create-an-assessment-using-a-guided-process"></a>Opret en bedømmelsesvurdering ved hjælp af en guidet proces

1. På siden **Bedømmelser** skal du vælge **Tilføj bedømmelse.** Dette sætter dig i guiden til oprettelse af bedømmelsesvurderinger.

2. På skærmen **Basisskabelon skal** du vælge **Vælg skabelon for** at vælge skabelonen til din bedømmelse.

3. På pop op-ruden skal du vælge skabelonen til den forordning eller certificering, som bedømmelsen skal baseres på. Listen over skabeloner, der er opdelt i kategorier medfølger og premium-kategorier ([få oplysninger](compliance-manager-templates.md#template-availability-and-licensing)). Tælleren Aktiverede **/Licenserede** skabeloner øverst i pop op-ruden viser dig, hvordan skabeloner du bruger ud af det samlede antal, der er tilgængelige, eller din organisation kan [bruge (få](compliance-manager-templates.md#active-and-inactive-templates) mere at vide).) Vælg alternativknappen ud for den valgte skabelon, og vælg derefter **Gem**. Du kommer tilbage til skærmen **basisskabelon,** hvor du kan gennemse skabelondetaljerne og derefter fortsætte ved at vælge **Næste**.

4. **Produkt, navn og gruppe:** Angiv disse egenskaber for at identificere din vurdering, vælg, hvilket produkt den skal evaluere, og tildel den til en gruppe.

    - **Produkt**: Vælg det produkt, du vil have din vurdering til at gælde for. Hvis du bruger en Microsoft-skabelon, f.eks. en, der er Microsoft 365, udfyldes dette felt for dig for at angive det relevante produkt og kan ikke ændres. Hvis du bruger en universel skabelon, skal du vælge, om du opretter denne vurdering for et nyt produkt eller et brugerdefineret produkt, du allerede har defineret i Overholdelsesstyring. Hvis du vælger et nyt produkt, skal du angive dets navn. Bemærk, at du ikke kan vælge et foruddefineret Microsoft-produkt, når du bruger en universel skabelon.
    - **Bedømmelsesnavn**: Angiv et navn til din vurdering i **feltet Bedømmelsesnavn** . Vurderingsnavne skal være entydige i grupper. Hvis navnet på din bedømmelsesvurdering svarer til navnet på en anden bedømmelsesvurdering i en given gruppe, modtager du en fejl, der beder dig om at oprette et andet navn.
    - **Gruppe**: Tildel din vurdering til en gruppe. Du kan enten:
        - Vælg **Brug eksisterende gruppe for** at tildele den til en gruppe, du allerede har oprettet. eller
        - Vælg **Opret ny gruppe** for at oprette en ny gruppe og tildele denne vurdering til den:
            - Find et navn til din gruppe, og angiv det i feltet under alternativknappen.
            - Du kan **kopiere data fra en eksisterende gruppe**, f.eks. implementering og testoplysninger og dokumenter, ved at vælge de relevante felter.

    Vælg Næste, når du **er færdig**.

5. **Gennemse og afslut:** Gennemse dine valg, og foretag de nødvendige ændringer. Når du er tilfreds, skal du vælge **Opret vurdering**.

Det næste skærmbillede bekræfter, at vurderingen blev oprettet. Når du vælger **Udført**, bliver du ført til siden med oplysninger om din nye vurdering.

Hvis du får vist **skærmbilledet Vurdering mislykkedes** , når du har **valgt Opret vurdering**, **skal du vælge Prøv** igen for at oprette din vurdering igen.

Du kan ændre navnet på din vurdering, efter du har oprettet den, ved at  vælge knappen Rediger navn i øverste højre hjørne af siden med [oplysninger om vurderingen](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Overvåge status og kontrolelementer for vurdering

Hver vurdering har en detaljeside, der giver et hurtigt overblik over dine fremskridt med at fuldføre vurderingen. Siden viser status for fuldførelse af kontrolelementer og teststatus for vigtige forbedringshandlinger inden for disse kontrolelementer.

### <a name="overview-tab"></a>Fanen Oversigt

Fanen Oversigt indeholder en graf, der viser din procentdel mod færdiggørelse af vurderingen. Denne graf indeholder en oversigt over point fra de handlinger, du ejer, og point fra handlinger, der ejes af Microsoft, så du kan se, hvor mange flere point du skal bruge for at fuldføre vurderingen.

De vigtigste forbedringshandlinger for kontrolelementer i vurderingen er angivet i rækkefølge med størst mulig virkning for at optjene point. Den tilknyttede graf viser den aggregerede teststatus for dine forbedringshandlinger, så du hurtigt kan vurdere, hvad der er blevet testet, og hvad der stadig skal gøres.

Hvis du vil have adgang til individuelle forbedringshandlinger, **skal** du gå til **fanen Kontrolelementer eller fanen Dine forbedringshandlinger** .

### <a name="controls-tab"></a>Fanen Kontrolelementer

Fanen Kontrolelementer viser detaljerede oplysninger for hvert kontrolelement, der er knyttet til vurderingen. Et **diagram over kontrolstatussen** viser status for kontrolelementer efter familie, så du hurtigt kan se, hvilke grupper af kontrolelementer der kræver opmærksomhed.

Under diagrammet viser en tabel detaljerede oplysninger om hvert kontrolelement i vurderingen. Kontrolelementer er grupperet efter kontrolfamilie. Udvid hvert familienavn for at få vist de enkelte kontrolelementer, den indeholder. De oplysninger, der er angivet for hvert kontrolelement, omfatter:

- **Kontrolelementtitel**
- **Status**: Afspejler teststatus for forbedringshandlinger inden for kontrolelementet 
    - **Bestået** – alle forbedringshandlinger har teststatus "overskredet", eller der overføres mindst én, og resten er "uden for omfanget"
    -  **Mislykkedes** – mindst én forbedringshandling har teststatussen "mislykket"
    - **Ingen** – alle forbedringshandlinger er ikke blevet testet
    - **Uden for omfanget** – alle forbedringshandlinger er uden for området for denne vurdering
    - **I gang** – forbedringshandlinger har en anden status end dem, der er angivet ovenfor, og som kan omfatte "igangværende", "delvis kredit" eller "ikke registreret"
- **Kontrol-id**: kontrolelementens identifikationsnummer, der tildeles af det tilsvarende kontrolelement, standard eller politik
- **Point,** der er opnået: antallet af point, der er optjent ved at udføre handlinger, ud af det samlede antal opnåelige point 
- **Dine handlinger**: antallet af fuldførte handlinger ud af det samlede antal handlinger, der skal udføres
- **Microsoft-handlinger**: antallet af handlinger, der udføres af Microsoft

Hvis du vil have vist oplysninger om et kontrolelement, skal du markere det fra dets række i tabellen. Siden med kontrolelementdetaljer viser en graf, der angiver teststatus for handlingerne i det pågældende kontrolelement. En tabel under grafen viser vigtige forbedringshandlinger for det pågældende kontrolelement.

Vælg en forbedringshandling på listen for at analysere detaljesiden for forbedringshandlingen. Detaljesiden viser teststatus og implementeringsnoter og starter ind i den anbefalede løsning.

### <a name="your-improvement-actions-tab"></a>Fanen Dine forbedringshandlinger

Fanen til dine forbedringshandlinger viser alle de kontrolelementer i bedømmelsesvurderingen, der administreres af din organisation. Statuslinjen viser den aggregerede teststatus for dine forbedringshandlinger i vurderingen, så du hurtigt kan vurdere, hvad der er blevet testet, og hvad der stadig skal gøres. Under linjen finder du en komplet liste over forbedringshandlinger og vigtige detaljer, herunder: teststatus, antallet af potentielle og oparbejdet point, tilknyttede bestemmelser og standarder, gældende løsning, handlingstype og familiekontrol. Få mere at vide [om, hvordan handlinger bidrager til din vurdering af overholdelse](compliance-score-calculation.md#action-types-and-points).

Vælg en forbedringshandling for at få vist detaljesiden, og vælg **linket Start nu** for at åbne løsningen for at gøre noget.

### <a name="microsoft-actions-tab"></a>Fanen Microsoft-handlinger

Fanen Microsoft-handlinger vises for bedømmelser baseret på skabeloner, der understøtter Microsoft-produkter. Den viser alle handlinger i den vurdering, der administreres af Microsoft. Listen viser vigtige handlingsoplysninger, herunder: teststatus, punkter, der bidrager til dit overordnede overholdelsesresultat, tilknyttede bestemmelser og standarder, gældende løsning, handlingstype og kontrolfamilie. Vælg en forbedringshandling for at få vist detaljesiden.

Få mere at vide [om, hvordan kontrolelementer og forbedringshandlinger registreres og får point.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Acceptér opdateringer til bedømmelser

Når en opdatering er tilgængelig til en vurdering, får du vist en meddelelse og har mulighed for at acceptere opdateringen eller udskyde den til et senere tidspunkt.

Der er tilgængelige opdateringer til bedømmelser baseret på Microsoft-skabeloner, f.eks. dem, der er udviklet til brug Microsoft 365. Hvis din organisation bruger universelle skabeloner til vurdering af andre produkter, understøttes nedarvning muligvis ikke. Få mere at vide under [Udvid bedømmelsesskabeloner](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Årsagen til en opdatering

Der foretages en vurderingsopdatering, når der er underliggende skabelonændringer, der påvirker pointtal. Ændringer kan omfatte justering af kontroltilknytning eller andre retningslinjer baseret på lovmæssige ændringer eller produktændringer. Opdateringer til bedømmelser kan komme fra din organisation (f.eks. når [en brugerdefineret](compliance-manager-templates-modify.md) skabelon ændres) og fra Microsoft.

Hvis Microsoft opdaterer en udvidet skabelon til Overholdelsesstyring, arver din vurdering disse opdateringer, når du har accepteret dem. Din vurdering bevarer de yderligere attributter, du anvendte til vurderingen, da du udvidede den.

Brugerdefinerede bedømmelsesvurderinger, som du opretter, modtager ikke nogen skabelonopdateringer fra Microsoft. Brugerdefinerede bedømmelsesvurderinger kan modtage opdateringer om forbedringshandlinger, men eventuelle Microsoft-opdateringer til styring af tilknytning mellem evalueringer og forbedringshandlinger gælder ikke for brugerdefinerede skabeloner.

> [!NOTE]
> Opdateringer af bedømmelser gælder kun på gruppeniveau. Hvis du har to bedømmelser opbygget ud fra den samme skabelon, der findes i to forskellige grupper, har hver vurdering en afventende opdateringsmeddelelse, og du skal acceptere opdateringen for hver vurdering i dens respektive gruppe individuelt.

#### <a name="where-youll-see-assessment-update-notifications"></a>Hvor du får vist meddelelser om opdatering af bedømmelsesvurdering

Siden med oplysninger om bedømmelsesvurderingen viser **også en ventende** opdateringsmærkat ud for bedømmelsesvurderingen med en opdatering. Vælg den pågældende vurdering for at få adgang til dens detaljeside.

En meddelelse øverst på siden med bedømmelsesdetaljer viser, at der er en tilgængelig opdatering for den pågældende vurdering. Vælg knappen **Gennemse opdatering** i banneret for at gennemgå de specifikke ændringer og acceptere eller udskyde opdateringen.

Siden med oplysninger om bedømmelse kan også vise forbedringshandlinger, der har etiketten **Ventende** opdatering ud for sig. Disse opdateringer er til specifikke ændringer af selve forbedringshandlingerne og skal accepteres separat. Besøg [Accepter opdateringer for forbedringshandlinger for at](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) få mere at vide.

#### <a name="review-update-to-accept-or-defer"></a>Gennemse opdateringen for at acceptere eller udsætte

Når du har **valgt Gennemse** opdatering på siden med vurderingsdetaljer, vises en pop op-rude i højre side af skærmen. Pop op-ruden indeholder de vigtigste oplysninger nedenfor om den ventende opdatering:

- Skabelonens titel
- Kilde til opdateringen (Microsoft, din organisation eller en bestemt bruger)
- Den dato, hvor opdateringen blev oprettet
- En oversigt, der forklarer opdateringen
- Specifikke oplysninger om ændringerne, herunder påvirkningen af dit overholdelsesresultat, mængden af fremskridt i forbindelse med fuldførelsen af vurderingen og det specifikke antal ændringer i forbedringshandlinger og -kontrolelementer.

Når du vælger **linket Opdateret skabelon**, hentes en Excel fil, der indeholder kontroldata for versionen af skabelonen med de ventende opdateringer. Når du vælger **linket Aktuel** skabelon, hentes en fil med den eksisterende skabelon uden ændringerne.

Hvis du vil acceptere opdateringen og foretage ændringerne i din vurdering, skal du vælge **Acceptér opdatering**. Accepterede ændringer er permanente.

Hvis du **vælger Annuller**, anvendes opdateringen ikke på bedømmelsesvurderingen. Du vil dog fortsat få vist meddelelsen **Afventer opdatering** , indtil du accepterer opdateringen.

**Derfor anbefaler vi, at du accepterer opdateringer**

Accept af opdateringer er med til at sikre, at du har den mest opdaterede vejledning til brug af løsninger og tager de relevante forbedringshandlinger, der kan hjælpe dig med at opfylde kravene i den certificering, du er i gang med.

**Derfor kan det være en ide at udskyde en opdatering**

Hvis du er midt i en bedømmelsesvurdering, kan det være en god ide at sikre dig, at du er færdig med at arbejde på den, før du accepterer en opdatering til vurderingen, der kan forstyrre styringen af tilknytningen. Du kan udskyde opdateringen til et senere tidspunkt ved at vælge **Annuller** i pop op-ruden med gennemsynsopdateringen.

## <a name="export-an-assessment-report"></a>Eksportere en vurderingsrapport

Du kan eksportere en vurdering til en Excel for interessenter i organisationen eller for eksterne revisorer og kontrolorganer. På siden med oplysninger om din vurdering skal  du vælge knappen Generér rapport øverst på siden, som opretter en Excel, du kan gemme og dele.

Rapporten er et øjebliksbillede af vurderingen på datoen og klokkeslættet for eksporten. Den indeholder oplysninger om kontrolelementer, der administreres af både dig og Microsoft, herunder implementeringsstatus, testdato og testresultater.

## <a name="delete-an-assessment"></a>Slet en bedømmelsesvurdering

Når du sletter en bedømmelsesvurdering, fjernes den fra listen på siden Bedømmelser. Bemærk disse vigtige punkter vedrørende sletning af bedømmelser:

- **Når du sletter en bedømmelsesvurdering, er det en permanent løsning. kan du ikke få den tilbage.** Hvis du vil bruge den samme vurdering igen, skal du oprette den igen.
- Hvis forbedringshandlingerne i vurderingen ikke vises i nogen anden vurdering, slettes de, når bedømmelsesvurderingen slettes.
- Vi anbefaler [, at du eksporterer](#export-an-assessment-report) en rapport af vurderingen, før du sletter den permanent.

Hvis du vil slette en bedømmelsesvurdering, skal du følge nedenstående trin:

1. På siden **bedømmelser** skal du vælge den bedømmelsesvurdering, du vil slette, for at åbne siden med oplysninger om den pågældende bedømmelse.

2. Vælg **Slet bedømmelsesvurdering** i øverste højre hjørne af skærmen.

3. Der vises et vindue, hvor du bliver bedt om at bekræfte, at du vil slette bedømmelsesvurderingen permanent. Vælg **Slet bedømmelsesvurdering** for at lukke vinduet. Du får et bekræftelsesvindue, der bekræfter, at din vurdering er blevet slettet fra Overholdelsesstyring.

> [!NOTE]
> Du kan ikke slette alle dine bedømmelsesvurderinger. Organisationer skal have mindst én vurdering, for at Overholdelsesstyring kan fungere korrekt. Hvis den vurdering, du vil slette, er den eneste, skal du tilføje en anden vurdering, før du sletter den anden vurdering.
