---
title: Byg og administrer vurderinger i Microsoft Compliance Manager
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
description: Byg vurderinger i Microsoft Compliance Manager for at hjælpe dig med at opfylde de krav til forskrifter og certificeringer, der er vigtige for din organisation.
ms.openlocfilehash: 9fbea59eae103e2ce9715fda6c7b7a97d38eb855
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759009"
---
# <a name="build-and-manage-assessments-in-compliance-manager"></a>Byg og administrer vurderinger i Overholdelsesstyring

**I denne artikel:** Få mere at vide om, hvordan du tilpasser Overholdelsesstyring for din organisation ved at oprette og administrere **vurderinger**. I denne artikel gennemgår vi, hvordan du opretter vurderinger, hvordan du organiserer dem i **grupper**, arbejder med **kontrolelementer**, accepterer **opdateringer** og eksporterer **vurderingsrapporter**.

## <a name="introduction-to-assessments"></a>Introduktion til vurderinger

Overholdelsesstyring hjælper dig med at oprette vurderinger, der evaluerer din overholdelse af brancheregler og regionale bestemmelser, der gælder for din organisation. Vurderinger er baseret på rammerne af vurderingsskabeloner, som indeholder de nødvendige kontroller, forbedringshandlinger og, hvor det er relevant, Microsoft-handlinger til fuldførelse af vurderingen. Konfiguration af de mest relevante vurderinger for din organisation kan hjælpe dig med at implementere politikker og driftsprocedurer for at begrænse din risiko for overholdelse af angivne standarder.

Alle dine vurderinger er angivet under fanen Vurderinger i Overholdelsesstyring. Få mere at vide om [, hvordan du filtrerer din visning af dine vurderinger og fortolker statustilstande](compliance-manager-setup.md#assessments-page).

> [!IMPORTANT]
> De skabeloner, der er tilgængelige for din organisation til oprettelse af vurderinger, afhænger af din licensaftale. [Gennemse licensoplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="data-protection-baseline-default-assessment"></a>Vurdering af standardvurdering af grundlæggende databeskyttelse

For at komme i gang giver Microsoft en **standardvurdering** i Overholdelsesstyring for **Microsoft 365 baseline til databeskyttelse**. Denne grundlæggende vurdering har et sæt kontroller af vigtige bestemmelser og standarder for databeskyttelse og generel datastyring. Denne baseline henter elementer primært fra NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) og ISO (International Organization for Standardization) samt fra FedRAMP (Federal Risk and Authorization Management Program) og GDPR (General Data Protection Regulation of the European Union).

Denne vurdering bruges til at beregne din første overholdelsesscore, første gang du kommer til Overholdelsesstyring, før du konfigurerer andre vurderinger. Overholdelsesstyring indsamler indledende signaler fra dine Microsoft 365 løsninger. Du kan hurtigt se, hvordan din organisation klarer sig i forhold til vigtige standarder og bestemmelser for databeskyttelse, og se foreslåede forbedringshandlinger.

Overholdelsesstyring bliver mere nyttig, når du opretter og administrerer dine egne vurderinger, så de opfylder organisationens særlige behov.

## <a name="understand-groups-before-creating-assessments"></a>Forstå grupper, før du opretter vurderinger

Når du opretter en vurdering, skal du tildele den til en gruppe. Grupper er objektbeholdere, der giver dig mulighed for at organisere vurderinger på en måde, der er logisk for dig, f.eks. efter år eller regulering eller baseret på organisationens afdelinger eller geografiske områder. Derfor anbefaler vi, at du planlægger en grupperingsstrategi, før du opretter vurderinger.

Nedenfor er eksempler på to grupper og deres underliggende vurderinger:

- **FFIEC IS-vurdering 2020**
  - FFIEC ER
- **Vurderinger af datasikkerhed og beskyttelse af personlige oplysninger**
  - ISO 27001:2013
  - ISO 27018:2014

Forskellige vurderinger i en eller flere grupper kan dele forbedringshandlinger. Forbedringshandlinger kan være ændringer, du foretager i tekniske løsninger, der er knyttet til din lejer, f.eks. aktivering af tofaktorgodkendelse eller ikke-tekniske handlinger, du udfører uden for systemet, f.eks. oprettelse af en ny arbejdspladspolitik. Alle opdateringer i detaljer eller status, som du foretager af en teknisk forbedringshandling, vil blive samlet op af vurderinger på tværs af alle grupper. Ikke-tekniske forbedringer af handlingsopdateringer genkendes af vurderinger i den gruppe, hvor du anvender dem. Dette giver dig mulighed for at implementere én forbedringshandling og opfylde flere krav samtidigt.

### <a name="create-a-group"></a>Opret en gruppe

Du kan oprette en gruppe, mens du opretter en ny vurdering. Grupper kan ikke oprettes som separate enheder.

### <a name="what-to-know-when-working-with-groups"></a>Hvad du skal vide, når du arbejder med grupper

- En gruppe skal indeholde mindst én vurdering.
- Gruppenavne skal være entydige i din organisation.
- Grupper har ikke sikkerhedsegenskaber. Alle tilladelser er knyttet til vurderinger.
- Når du føjer en vurdering til en gruppe, kan gruppering ikke ændres.
- Hvis du føjer en ny vurdering til en eksisterende gruppe, kopieres almindelige oplysninger fra vurderinger i den pågældende gruppe til den nye vurdering.
- Relaterede vurderingskontrolelementer i forskellige vurderinger i den samme gruppe opdateres automatisk, når de er fuldført.
- Grupper kan indeholde vurderinger for den samme certificering eller regulering, men hver gruppe kan kun indeholde én vurdering for et bestemt produktcertificeringspar. En gruppe kan f.eks. ikke indeholde to vurderinger for Office 365 og NIST CSF. En gruppe kan kun indeholde flere vurderinger for det samme produkt, hvis den tilsvarende certificering eller regulering for hver enkelt er forskellig.
- Hvis du sletter en vurdering, brydes relationen mellem den pågældende vurdering og gruppen.
- Grupper kan ikke slettes.

## <a name="understand-templates-before-creating-assessments"></a>Forstå skabeloner, før du opretter vurderinger

Vurderingsskabeloner indeholder kontrol- og handlingsanbefalinger til vurderinger baseret på certificeringer for forskellige bestemmelser og standarder for beskyttelse af personlige oplysninger. Organisationens tilgængelige skabeloner kan indeholde en eller flere skabeloner, der er inkluderet som en del af din licensaftale, sammen med eventuelle yderligere Premium-skabeloner, du har købt.

Hver skabelon, uanset om den er inkluderet eller premium, findes i to versioner: én til brug sammen med Microsoft 365 (eller andre Tilgængelige Microsoft-produkter) og en universel version, der kan skræddersyes til at vurdere andre produkter, du bruger. Du kan vælge den relevante skabelontype for det produkt, du vil vurdere.

Du kan få mere at vide om skabeloner under [Arbejde med vurderingsskabeloner](compliance-manager-templates.md).

## <a name="create-assessments"></a>Opret vurderinger

> [!NOTE]
> Det er kun brugere, der har rollen Global administrator, Overholdelsesstyring eller Vurdering af overholdelsesstyring, der kan oprette og redigere vurderinger. Få mere at vide om [roller og tilladelser](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

Før du begynder, skal du være sikker på, at du ved, hvilken gruppe du tildeler den til, eller vær forberedt på at oprette en ny gruppe til denne vurdering. Læs detaljer om [grupper og vurderinger](#understand-groups-before-creating-assessments).

Hvis du vil oprette en vurdering, skal du bruge en guidet proces til at vælge en skabelon og angive det tilknyttede produkt. På siden **Vurderinger** foreslår vi, at du starter med **Tilføj anbefalede vurderinger**, som hjælper dig med at identificere og hurtigt konfigurere de mest relevante vurderinger for din organisation på én gang. Du kan også konfigurere vurderinger én ad gangen ved at vælge **Tilføj vurdering**. Følg nedenstående trin for at begynde at oprette vurderinger.

#### <a name="create-assessments-based-on-recommendations-for-your-org-type"></a>Opret vurderinger baseret på anbefalinger til din organisationstype

Overholdelsesstyring kan angive, hvilke vurderinger der kan være mest relevante for din organisation. Når du angiver grundlæggende oplysninger om din organisations branche og placeringer, anbefaler vi, hvilke skabeloner der skal bruges fra vores bibliotek med over 300 skabeloner. Du skal blot vælge mellem de anbefalede skabeloner til hurtig konfiguration af flere vurderinger på én gang.

Hvis du vil oprette en eller flere vurderinger baseret på vores anbefalinger, skal du vælge **Tilføj anbefalede vurderinger** fra siden **Vurderinger** og følge disse trin:

- Vælg en eller flere brancher, der identificerer din organisation, og vælg derefter **Næste**
- Vælg et eller flere områder til din organisations placering, og vælg derefter **Næste**
- På skærmbilledet **Vælg vurdering** skal du vælge rullepilen ud for **Anbefalede skabeloner** for at se listen over vurderinger, som vi mener gælder for din organisation. Markér afkrydsningsfelterne ud for de skabeloner, du vil bruge til oprettelse af vurderinger, og vælg derefter **Næste**.
- Gennemse dine endelige valg, og vælg **Tilføj anbefalede vurderinger** for at oprette dine nye vurderinger.

#### <a name="create-an-assessment-using-a-guided-process"></a>Opret en vurdering ved hjælp af en guidet proces

1. Vælg **Tilføj vurdering** på siden **Vurderinger**. Dette fører dig ind i guiden til oprettelse af vurdering.

2. På **skærmbilledet Basisskabelon** skal du vælge **Vælg skabelon** for at vælge skabelonen til din vurdering.

3. Vælg skabelonen til den forordning eller certificering, som vurderingen skal baseres på, i pop op-vinduet. Listen over skabeloner, der er opdelt i inkluderede og Premium-kategorier ([få detaljer](compliance-manager-templates.md#template-availability-and-licensing)). Tælleren **Aktiverede/licenserede skabeloner** øverst i pop op-ruden viser dig, hvordan du kan bruge skabeloner, som du bruger ud af det samlede antal tilgængelige skabeloner, eller som din organisation kan bruge ([få mere at vide](compliance-manager-templates.md#active-and-inactive-templates)). Vælg alternativknappen ud for den valgte skabelon, og vælg derefter **Gem**. Du vender tilbage til **skærmbilledet med basisskabelonen** , hvor du kan gennemse skabelondetaljerne og derefter fortsætte ved at vælge **Næste**.

4. **Produkt, navn og gruppe:** Angiv disse egenskaber for at identificere din vurdering, vælg, hvilket produkt den skal evaluere, og tildel den til en gruppe.

    - **Produkt**: Vælg det produkt, din vurdering skal gælde for. Hvis du bruger en Microsoft-skabelon, f.eks. en, der er designet til Microsoft 365, udfyldes dette felt, så du kan angive det relevante produkt, og det kan ikke ændres. Hvis du bruger en universel skabelon, skal du vælge, om du opretter denne vurdering for et nyt produkt eller et brugerdefineret produkt, du allerede har defineret i Overholdelsesstyring. Hvis du vælger et nyt produkt, skal du angive dets navn. Bemærk, at du ikke kan vælge et foruddefineret Microsoft-produkt, når du bruger en universel skabelon.
    - **Vurderingsnavn**: Angiv et navn til din vurdering i feltet **Vurderingsnavn** . Vurderingsnavne skal være entydige i grupper. Hvis navnet på din vurdering stemmer overens med navnet på en anden vurdering i en given gruppe, får du vist en fejl, hvor du bliver bedt om at oprette et andet navn.
    - **Gruppe**: Tildel din vurdering til en gruppe. Du kan enten:
        - Vælg **Brug eksisterende gruppe** til at tildele den til en gruppe, du allerede har oprettet. Eller
        - Vælg **Opret ny gruppe** for at oprette en ny gruppe, og tildel den denne vurdering:
            - Fastlæg et navn til din gruppe, og angiv det i feltet under alternativknappen.
            - Du kan **kopiere data fra en eksisterende gruppe**, f.eks. implementering og test af detaljer og dokumenter, ved at vælge de relevante felter.

    Når du er færdig, skal du vælge **Næste**.

5. **Gennemse og afslut:** Gennemse dine valg, og foretag de nødvendige ændringer. Når du er klar, skal du vælge **Opret vurdering**.

Det næste skærmbillede bekræfter, at vurderingen blev oprettet. Når du vælger **Udført**, føres du til siden med oplysninger om din nye vurdering.

Hvis du får vist **skærmbilledet Vurdering mislykkedes** , efter du har valgt **Opret vurdering**, skal du vælge **Prøv igen** for at genoprette din vurdering.

Du kan ændre navnet på din vurdering, når du har oprettet den, ved at vælge knappen **Rediger navn** i øverste højre hjørne af [siden med oplysninger om vurderingen](#monitor-assessment-progress-and-controls).

## <a name="monitor-assessment-progress-and-controls"></a>Overvåg status og kontrolelementer for vurdering

Hver vurdering har en side med detaljer, der giver et hurtigt overblik over dine fremskridt i fuldførelsen af vurderingen. På siden kan du se, hvordan du fuldfører kontrolelementer, og teststatussen for nøgleforbedringshandlinger i disse kontrolelementer.

### <a name="overview-tab"></a>Fanen Oversigt

Fanen Oversigt indeholder en graf, der viser din procentdel mod afslutningen af vurderingen. Denne graf indeholder en opdeling af punkter fra de handlinger, du ejer, og peger på handlinger, der ejes af Microsoft, så du kan se, hvor mange flere punkter du skal bruge for at fuldføre vurderingen.

De vigtigste forbedringsforanstaltninger for kontroller i vurderingen er opført i rækkefølge efter den største potentielle indvirkning for at optjene point. Den tilknyttede graf indeholder oplysninger om den samlede teststatus for dine forbedringshandlinger, så du hurtigt kan måle, hvad der er blevet testet, og hvad der stadig skal gøres.

Hvis du vil have adgang til individuelle forbedringshandlinger, skal du gå til fanen **Kontrolelementer** eller fanen **Handlinger til forbedring** .

### <a name="controls-tab"></a>Fanen Kontrolelementer

Fanen Kontrolelementer viser detaljerede oplysninger om hvert kontrolelement, der er knyttet til vurderingen. Et **oversigtsdiagram over kontrolelementers status** viser status for kontrolelementer efter familie, så du hurtigt kan se, hvilke grupperinger af kontrolelementer der kræver opmærksomhed.

Under diagrammet vises en tabel med detaljerede oplysninger om hvert kontrolelement i vurderingen. Kontrolelementerne grupperes efter kontrolelementfamilie. Udvid hvert familienavn for at få vist de enkelte kontrolelementer, det indeholder. De oplysninger, der er angivet for hvert kontrolelement, omfatter:

- **Titel på kontrolelement**
- **Status**: afspejler teststatussen for forbedringshandlinger i kontrolelementet
  - **Bestået** – alle forbedringshandlinger har teststatussen "bestået", eller mindst én er bestået, og resten er "uden for omfanget"
  - **Mislykkedes** – mindst én forbedringshandling har teststatussen "mislykkedes"
  - **Ingen** – alle forbedringshandlinger er ikke blevet testet
  - **Uden for omfanget** – alle forbedringshandlinger er ikke omfattet af denne vurdering
  - **Igangværende** – forbedringsaktioner har en anden status end dem, der er angivet ovenfor, og som kan omfatte "igangværende", "delvis kredit" eller "uopdaget"
- **Kontrol-id**: kontrolelementets identifikationsnummer, der er tildelt af dets tilsvarende regulering, standard eller politik
- **Opnåede point**: antallet af point, der er optjent ved at gennemføre handlinger, ud af det samlede antal opnåelige point
- **Dine handlinger**: Antallet af udførte handlinger ud af det samlede antal handlinger, der skal udføres
- **Microsoft-handlinger**: antallet af handlinger, der er fuldført af Microsoft

Hvis du vil have vist oplysninger om et kontrolelement, skal du vælge det på dets række i tabellen. På siden med oplysninger om kontrolelementet vises en graf, der angiver teststatussen for handlingerne i det pågældende kontrolelement. En tabel under grafen viser de vigtigste forbedringshandlinger for det pågældende kontrolelement.

Vælg en forbedringshandling på listen for at få detaljeadgang til detaljesiden for forbedringshandlingen. Detaljesiden viser teststatus og implementeringsnoter og starter i den anbefalede løsning.

### <a name="your-improvement-actions-tab"></a>Fanen Forbedringshandlinger

Fanen for dine forbedringshandlinger viser alle de kontrolelementer i vurderingen, der administreres af din organisation. Statuslinjen indeholder oplysninger om den samlede teststatus for dine forbedringshandlinger i vurderingen, så du hurtigt kan måle, hvad der er blevet testet, og hvad der stadig skal gøres. Under linjen er den komplette liste over forbedringshandlinger og vigtige detaljer, herunder: teststatus, antallet af potentielle og optjente point, tilknyttede regler og standarder, relevant løsning, handlingstype og kontrolfamilie. Få mere at vide om [, hvordan handlinger bidrager til din overholdelsesscore](compliance-score-calculation.md#action-types-and-points).

Vælg en forbedringshandling for at få vist siden med detaljer, og vælg linket **Start nu** for at åbne løsningen for at udføre en handling.

### <a name="microsoft-actions-tab"></a>Fanen Microsoft-handlinger

Fanen Microsoft-handlinger vises for vurderinger, der er baseret på skabeloner, der understøtter Microsoft-produkter. Den viser alle de handlinger i vurderingen, der administreres af Microsoft. Listen viser detaljer om nøglehandlinger, herunder: teststatus, punkter, der bidrager til din overordnede overholdelsesscore, tilknyttede regler og standarder, relevant løsning, handlingstype og kontrolfamilie. Vælg en forbedringshandling for at få vist siden med detaljer.

Få mere at vide om [, hvordan kontrolelementer og forbedringshandlinger spores og scores.](compliance-score-calculation.md)

## <a name="accept-updates-to-assessments"></a>Acceptér opdateringer til vurderinger

Når en opdatering er tilgængelig til en vurdering, får du vist en meddelelse og har mulighed for at acceptere opdateringen eller udskyde den et senere tidspunkt.

Der er tilgængelige opdateringer til vurderinger, der er baseret på Microsoft-skabeloner, f.eks. dem, der er designet til brug sammen med Microsoft 365. Hvis din organisation bruger universelle skabeloner til at vurdere andre produkter, understøttes nedarvning muligvis ikke. Du kan få flere oplysninger under [Udvid vurderingsskabeloner](compliance-manager-templates-extend.md).

### <a name="what-causes-an-update"></a>Hvad er årsagen til en opdatering

En vurderingsopdatering forekommer, når der er underliggende skabelonændringer, der påvirker scoring. Ændringer kan omfatte justering af kontroltilknytning eller anden vejledning baseret på lovmæssige ændringer eller produktændringer. Vurderingsopdateringer kan stamme fra din organisation (f.eks. når en [brugerdefineret skabelon ændres](compliance-manager-templates-modify.md)) samt fra Microsoft.

Hvis Microsoft opdaterer en skabelon for Overholdelsesstyring, som du har udvidet, arver din vurdering disse opdateringer, når du har accepteret dem. Din vurdering bevarer de yderligere attributter, du anvendte på vurderingen, da du udvidede den.

Brugerdefinerede vurderinger, du opretter, modtager ikke nogen skabelonopdateringer fra Microsoft. Brugerdefinerede vurderinger kan modtage opdateringer af forbedringshandlinger, men alle Microsoft-opdateringer til styring af tilknytning mellem vurderinger og forbedringshandlinger gælder ikke for brugerdefinerede skabeloner.

> [!NOTE]
> Opdateringer til vurderinger gælder kun på gruppeniveau. Hvis du har to vurderinger, der er bygget ud fra den samme skabelon, som findes i to forskellige grupper, har hver vurdering en ventende opdateringsmeddelelse, og du skal acceptere opdateringen til hver vurdering i dens respektive gruppe individuelt.

#### <a name="where-youll-see-assessment-update-notifications"></a>Her kan du se meddelelser om vurderingsopdatering

Siden med vurderingsoplysninger viser også mærkaten **Ventende opdatering** ud for vurderingen med en opdatering. Vælg denne vurdering for at få vist siden med oplysninger.

En meddelelse nær toppen af siden med vurderingsoplysninger viser, at der er en opdatering tilgængelig for den pågældende vurdering. Vælg knappen **Gennemse opdatering** på banneret for at gennemse de specifikke ændringer og acceptere eller udskyde opdateringen.

Siden med vurderingsoplysninger kan også vise forbedringshandlinger, der har mærkaten **Ventende opdatering** ud for dem. Disse opdateringer er til specifikke ændringer af selve forbedringshandlingerne og skal accepteres separat. Besøg [Acceptér opdateringer til forbedringshandlinger](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) for at få mere at vide.

#### <a name="review-update-to-accept-or-defer"></a>Gennemse opdatering for at acceptere eller udskyde

Når du har valgt **Gennemse opdatering** på siden med vurderingsoplysninger, vises der en pop op-rude i højre side af skærmen. Pop op-ruden indeholder de vigtigste oplysninger nedenfor om den ventende opdatering:

- Skabelonens titel
- Kilde til opdateringen (Microsoft, din organisation eller en bestemt bruger)
- Den dato, hvor opdateringen blev oprettet
- En oversigt, der forklarer opdateringen
- Specifikke oplysninger om ændringerne, herunder indvirkningen på din overholdelsesscore, mængden af fremskridt mod afslutningen af vurderingen og det specifikke antal ændringer af forbedringshandlinger og kontroller.

Hvis du vælger linket **Opdateret skabelon, downloades** en Excel fil, der indeholder kontroldata, til versionen af skabelonen med de ventende opdateringer. Hvis du vælger linket **Aktuel skabelon** , hentes en fil med den eksisterende skabelon uden ændringerne.

Hvis du vil acceptere opdateringen og foretage ændringer i din vurdering, skal du vælge **Acceptér opdatering**. Accepterede ændringer er permanente.

Hvis du vælger **Annuller**, anvendes opdateringen ikke på vurderingen. Du vil dog fortsat se meddelelsen **Ventende opdatering** , indtil du accepterer opdateringen.

**Derfor anbefaler vi, at du accepterer opdateringer**

Accept af opdateringer hjælper med at sikre, at du har den mest opdaterede vejledning i at bruge løsninger og træffe passende forbedringshandlinger for at hjælpe dig med at opfylde kravene til den certificering, der er ved hånden.

**Derfor kan det være en god idé at udskyde en opdatering**

Hvis du er ved at fuldføre en vurdering, kan det være en god idé at sikre dig, at du er færdig med at arbejde på den, før du accepterer en opdatering til vurderingen, der kan afbryde kontroltilknytningen. Du kan udskyde opdateringen til et senere tidspunkt ved at vælge **Annuller** i pop op-vinduet til gennemsynsopdatering.

## <a name="export-an-assessment-report"></a>Eksportér en vurderingsrapport

Du kan eksportere en vurdering til en Excel fil for interessenter i forbindelse med overholdelse af angivne standarder i din organisation eller for eksterne auditører og regulatorer. På siden med vurderingsoplysninger skal du vælge knappen **Generér rapport** øverst på siden, hvor der oprettes en Excel fil, du kan gemme og dele.

Rapporten er et snapshot af vurderingen fra og med datoen og klokkeslættet for eksporten. Den indeholder oplysninger om kontrolelementer, der administreres af både dig og Microsoft, herunder implementeringsstatus, testdato og testresultater.

## <a name="delete-an-assessment"></a>Slet en vurdering

Hvis du sletter en vurdering, fjernes den fra listen på din vurderingsside. Bemærk disse vigtige punkter om sletning af vurderinger:

- **Sletning af en vurdering er permanent. Du kan ikke få den tilbage.** Hvis du vil bruge den samme vurdering igen, skal du genoprette den.
- Hvis forbedringshandlingerne i vurderingen ikke vises i nogen anden vurdering, slettes de, når vurderingen slettes.
- Vi anbefaler, at [du eksporterer en rapport](#export-an-assessment-report) over vurderingen, før du sletter den permanent.

Hvis du vil slette en vurdering, skal du følge nedenstående trin:

1. Vælg den vurdering, du vil slette, på siden **med vurderinger** for at åbne den pågældende vurderings detaljeside.

2. Vælg **Slet vurdering** i øverste højre hjørne af skærmen.

3. Der vises et vindue, hvor du bliver bedt om at bekræfte, at du vil slette vurderingen permanent. Vælg **Slet vurdering** for at lukke vinduet. Du får vist et bekræftelsesvindue for, at din vurdering blev slettet fra Overholdelsesstyring.

> [!NOTE]
> Du kan ikke slette alle dine vurderinger. Organisationer skal bruge mindst én vurdering, for at Overholdelsesstyring fungerer korrekt. Hvis den vurdering, du vil slette, er den eneste, skal du tilføje en anden vurdering, før du sletter den anden vurdering.
