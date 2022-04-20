---
title: Kom i gang med Microsoft Purview Compliance Manager
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
description: Angiv brugertilladelser og roller til Microsoft Purview Compliance Manager, og konfigurer automatisk test af handlinger. Administrer brugerhistorik, og filtrer dashboardvisningen.
ms.openlocfilehash: e691aefdeaf3c2e1c1398bf71b74006aff4d1f6f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973635"
---
# <a name="get-started-with-compliance-manager"></a>Kom i gang med Overholdelsesstyring

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**I denne artikel:** Denne artikel hjælper dig med at konfigurere Overholdelsesstyring. Få mere at vide om, hvordan du **får adgang til** Overholdelsesstyring, **angiver roller og tilladelser** og konfigurerer **automatisk test af forbedringshandlinger**. Gennemgå **dashboardet Overholdelsesstyring** , og forstå hovedsiderne: siden forbedringshandlinger, løsningssiden, vurderingssiden og siden med vurderingsskabeloner.

## <a name="who-can-access-compliance-manager"></a>Who har adgang til Overholdelsesstyring

Overholdelsesstyring er tilgængelig for organisationer med Office 365- og Microsoft 365-licenser og for kunder med amerikanske Government Community Cloud (GCC) Moderate, GCC High og DoD (Department of Defense). Tilgængeligheds- og administrationsfunktioner til vurdering afhænger af din licensaftale.  [Vis oplysninger om tjenestebeskrivelse](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="before-you-begin"></a>Før du begynder

Den Microsoft 365 globale administrator for din organisation vil sandsynligvis være den første bruger, der har adgang til Overholdelsesstyring. Vi anbefaler, at den globale administrator logger på og angiver brugertilladelser som beskrevet nedenfor, første gang de besøger Overholdelsesstyring.

## <a name="sign-in"></a>Log på

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>, og **log på** med din Microsoft 365 globale administratorkonto.
2. Vælg **Overholdelsesstyring** i venstre navigationsrude. Du ankommer til [dashboardet Overholdelsesstyring](#understand-the-compliance-manager-dashboard).

Det direkte link til Overholdelse af adgang er [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Angiv brugertilladelser, og tildel roller

Overholdelsesstyring bruger en rollebaseret RBAC-tilladelsesmodel (Access Control). Det er kun brugere, der har fået tildelt en rolle, der har adgang til Overholdelsesstyring, og de handlinger, der tillades af hver enkelt bruger, er begrænset af [rolletypen](#role-types).

### <a name="where-to-set-permissions"></a>Hvor skal tilladelser angives?

Den person, der har den globale administratorrolle for din organisation, kan angive brugertilladelser for Overholdelsesstyring. Tilladelser kan angives i Microsoft Purview-overholdelsesportalen samt i Azure Active Directory (Azure AD).

> [!NOTE]
> Kunder i miljøer med GCC (US Government Community) High and Department of Defense (DoD) kan kun angive brugertilladelser og roller for Overholdelsesstyring i Azure AD. Nedenfor kan du se azure AD-instruktioner og rolletypedefinitioner.

Hvis du vil angive tilladelser og tildele roller på Microsoft Purview-overholdelsesportalen, skal du følge nedenstående trin:

1. Gå til Microsoft Purview-overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a>.

2. Under rullelisten med overholdelsesportalen skal du vælge **Roller**.

3. Find den rollegruppe, du vil føje en eller flere brugere til, og markér afkrydsningsfeltet til venstre for gruppenavnet. (Se [listen over roller og relaterede funktioner nedenfor](#role-types). Rollegruppenavnene efterligner rollenavnet.)

4. I pop op-vinduet for den pågældende gruppe skal du vælge **Rediger** under overskriften **Medlemmer** .

5. Vælg **Vælg medlemmer**. Der vises et andet pop op-vindue.

6. Vælg **+ Tilføj** for at vælge en eller flere brugere, der skal føjes til gruppen.

7. Markér afkrydsningsfeltet ud for de navne, du vil tilføje, og vælg derefter knappen **Tilføj** nederst.

8. Når du er færdig med at tildele brugere, skal du vælge **Udført** og derefter vælge **Gem** og derefter **Luk**.

#### <a name="more-about-azure-ad"></a>Få mere at vide om Azure AD

Hvis du vil tildele roller og angive tilladelser i Azure AD, skal du se [Tildel administrator- og ikke-administratorroller til brugere med Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Brugere med Azure AD-identiteter, der ikke har Office 365 eller Microsoft 365 abonnementer, kan ikke få adgang til Overholdelsesstyring på Microsoft Purview-overholdelsesportalen. Kontakt [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com) for at få hjælp til at få adgang til Overholdelsesstyring.

### <a name="role-types"></a>Rolletyper

I nedenstående tabel vises de funktioner, der er tilladt af hver rolle i Overholdelsesstyring. I tabellen kan du også se, hvordan hver enkelt [Azure AD-rolle](/azure/active-directory/roles/permissions-reference) knyttes til overholdelsesstyringsroller. Brugerne skal som minimum have læserrollen Overholdelsesstyring eller rollen Global læser i Azure AD for at få adgang til Overholdelsesstyring.

| Brugeren kan: | Rollen Overholdelsesstyring | Azure AD-rolle | 
| :------------- | :-------------: | :------------: |
| **Læs, men rediger ikke data**| Læser til Overholdelsesstyring  | Global læser af Azure AD, Sikkerhedslæser |
| **Rediger data**| Bidrag til Overholdelsesstyring | Administrator for overholdelse af angivne standarder |
| **Rediger testresultater**| Vurdering af overholdelsesstyring | Administrator for overholdelse af angivne standarder |
| **Administrer vurderinger samt skabelon- og lejerdata**| Administration af Overholdelsesstyring | Overholdelsesadministrator, Administrator af overholdelsesdata, Sikkerhedsadministrator  |
| **Tildel brugere**| Global administrator | Global administrator |

## <a name="start-a-premium-assessments-trial"></a>Start en prøveversion af premiumvurderinger

Prøveversionen af Premium-vurderinger i Overholdelsesstyring er en fantastisk måde til hurtigt at konfigurere vurderinger, der er mest relevante for din organisation. Vores bibliotek med mere end 300 skabeloner svarer til statslige regler og branchestandarder rundt om i verden.
Få mere at vide om [prøveversionen af Premium-vurderinger](compliance-easy-trials-compliance-manager-assessments.md).

Du kan starte din prøveversion direkte fra Overholdelsesstyring og konfigurere anbefalede vurderinger ved at følge disse trin:

1. På siden **Oversigt over** Overholdelsesstyring skal du vælge **Start prøveversion**. Du skal angive en guide til aktivering af prøveversioner, som stiller spørgsmål, der kan hjælpe os med at anbefale vurderinger for din organisation.

2. På siden **Aktivér prøveversion** skal du vælge **Næste** for at starte din gratis 90-dages prøveversion af Premium-vurderinger og fortsætte med at oprette vurderinger.

3. Vælg en eller flere brancher, der identificerer din organisation, og vælg derefter **Næste**.

4. Vælg et eller flere områder til din organisations placering, og vælg derefter **Næste**.

5. På skærmbilledet **Vælg vurderinger** skal du vælge rullepilen ud for **Anbefalede skabeloner** for at se listen over vurderinger, som vi mener gælder for din organisation. Markér afkrydsningsfelterne ud for de skabeloner, du vil bruge til oprettelse af vurderinger, og vælg derefter **Næste**.

6. Gennemse dine endelige valg, og vælg **Tilføj anbefalede vurderinger** for at oprette dine nye vurderinger.

Få mere at vide om, hvordan du kommer i gang med vurderinger, ved at gå til afsnittet [Vurderinger](#assessments-page) nedenfor.

## <a name="settings-for-automated-testing-and-user-history"></a>Indstillinger til automatiseret test og brugerhistorik

Indstillingerne for Overholdelsesstyring i Microsoft Purview-overholdelsesportalen giver dig mulighed for at aktivere og deaktivere automatisk test af forbedringshandlinger. Indstillingerne giver dig også mulighed for at administrere dataene for de brugere, der er knyttet til forbedringshandlinger, herunder muligheden for at tildele forbedringshandlinger til en anden bruger.  Det er kun personer med en global administrator- eller overholdelsesadministratorrolle, der kan få adgang til indstillingerne for Overholdelsesstyring.

> [!NOTE]
> Den automatiserede testfunktion er ikke tilgængelig for kunder i GCC miljøer med høj og dod, fordi Secure Score ikke er tilgængelig i disse miljøer. GCC High- og DoD-kunder skal manuelt implementere og teste deres forbedringshandlinger.

### <a name="set-up-automated-testing"></a>Konfigurer automatiseret test

Overholdelsesstyring registrerer signaler fra andre Microsoft Purview-løsninger, som din organisation abonnerer på, herunder administration af datalivscyklus, beskyttelse af oplysninger, Forebyggelse af datatab i Microsoft Purview, overholdelse af kommunikation og styring af insiderrisiko. På detaljesiden for hver forbedringshandling viser feltet **Testlogik** under fanen **Test** , hvad der kræves i den anden løsning, for at handlingen kan overføre og optjene point mod din overholdelsesscore.

Overholdelsesstyring registrerer også signaler fra komplementære forbedringshandlinger, der også overvåges af [Microsoft Secure Score](../security/defender/microsoft-secure-score.md). Ved hjælp af disse signaler kan Overholdelsesstyring automatisk teste visse forbedringshandlinger for dig, hvilket hjælper med at maksimere effektiviteten i dine aktiviteter for overholdelse af angivne standarder. Når en forbedringshandling er blevet testet og implementeret, modtager du det fulde antal point, som krediteres din samlede score for overholdelse af angivne standarder.

Automatisk test er som standard slået til for organisationer, der ikke har arbejdet med Overholdelsesstyring. Når du udruller Microsoft 365 eller Office 365 første gang, tager det ca. syv dage at indsamle data fuldt ud og indregne dem i din overholdelsesscore. Når automatiseret test er slået til, opdateres handlingens testdato ikke, men teststatussen opdateres. Når der oprettes nye vurderinger, omfatter scorer automatisk Microsofts kontrolscores og secure score-integration.

#### <a name="manage-automated-testing-settings"></a>Administrer indstillinger for automatiseret test

Den globale administrator for din organisation kan når som helst ændre indstillingerne for automatiseret test. Du kan deaktivere automatiseret test for almindelige forbedringshandlinger eller slå den til for individuelle handlinger. Følg vejledningen nedenfor for at ændre dine automatiserede testindstillinger.

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> på Microsoft Purview-overholdelsesportalen.

2. Vælg **Overholdelsesstyring** på siden Indstillinger.

3. Vælg **Automatiseret test** i venstre navigationsrude.

4. Vælg den relevante knap for at aktivere automatisk test for alle forbedringshandlinger, slå den fra for alle handlinger, eller slå den til ved individuel handling.

5. Hvis du vælger **Slå handling til pr. forbedring**, viser en liste alle de tilgængelige forbedringshandlinger, du kan vælge imellem.  Markér afkrydsningsfeltet ud for en handling, du vil teste automatisk.

6. Vælg **Gem** for at gemme indstillingerne. Du modtager en bekræftelse øverst på skærmen om, at dit valg blev gemt. Hvis du modtager en meddelelse om fejl, kan du prøve igen.

**Bemærk:** Det er kun den globale administrator, der kan slå automatiske opdateringer til eller fra for alle handlinger. Administratoren af Overholdelsesstyring kan aktivere automatiske opdateringer for individuelle handlinger, men ikke for alle handlinger globalt.

**Få mere at vide**
- [Få mere at vide om, hvordan kontinuerlig overvågning bidrager til din overholdelsesscore](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).
- [Få mere at vide om, hvordan du designer en testkilde til en forbedringshandling](compliance-manager-improvement-actions.md#update-testing-source).

### <a name="manage-user-history"></a>Administrer brugerhistorik

Indstillingerne **Administrer brugerhistorik** hjælper dig med hurtigt at identificere, hvilke brugere der har arbejdet med forbedringshandlinger i Overholdelsesstyring. De identificerbare brugerdata, der er knyttet til forbedringshandlinger, omfatter alt udført implementerings- og testarbejde, dokumenter, de har uploadet, og eventuelle noter, de har angivet. Det kan være nødvendigt at forstå og hente denne type data for at opfylde organisationens egne behov for overholdelse af angivne standarder.

Indstillingerne for brugerhistorik giver dig også mulighed for at omfordele alle forbedringshandlinger fra én bruger til en anden.

**Sådan finder du indstillingerne for brugerhistorik:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> på Microsoft Purview-overholdelsesportalen.

2. Vælg **Overholdelsesstyring** på siden Indstillinger.

3. Vælg **Administrer brugerhistorik** i venstre navigationsrude.

På siden **Administrer brugerhistorik** vises en liste over alle brugere efter mailadresse, der er tildelt en forbedringshandling. Brug knappen **Søg** til hurtigt at finde en bestemt bruger ved at skrive vedkommendes mailadresse.

Til højre for hver brugers mailadresse indeholder rullemenuen **Vælg** indstillinger til eksport af en rapport, omfordeling af forbedringshandlinger eller sletning af historik. Se hvert afsnit nedenfor for at få oplysninger om hver indstilling.

#### <a name="export-a-report-of-user-history-data"></a>Eksportér en rapport over brugerhistorikdata

Du kan eksportere en Excel fil, der indeholder en liste over forbedringshandlinger, der i øjeblikket er tildelt en bruger.  Rapporten viser også eventuelle dokumentationsfiler, der er uploadet af den pågældende bruger. Disse oplysninger kan hjælpe dig med at omfordele handlinger til forbedring af åbne filer.

Rapporten afspejler status for forbedringshandlingen fra oprettelsesdatoen. Det er ikke en historisk rapport over alle tidligere ændringer af dens status eller tildeling (få mere at vide om, hvordan du [eksporterer en rapport fra siden forbedringshandlinger](compliance-manager-improvement-actions.md#export-a-report)).

**Følg nedenstående trin for at eksportere en rapport efter bruger:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> på Microsoft Purview-overholdelsesportalen.

2. Vælg **Overholdelsesstyring** på siden Indstillinger.

3. Vælg **Administrer brugerhistorik** i navigationen til venstre.

4. Find den ønskede bruger ved at søge på listens mailadresser eller ved at vælge **Søg** og angive brugerens mailadresse.

5. Vælg **Eksportér rapport** i rullemenuen **Vælg**.

6. Når rapportens Excel fil er genereret, kan du åbne den og gemme den på din lokale computer.

#### <a name="reassign-improvement-actions-to-another-user"></a>Overdrag forbedringshandlinger til en anden bruger

Du kan tildele forbedringshandlinger fra én bruger til en anden. Når du tildeler en handling igen, ændres historikken for dokumentoverførsler ikke, men navnet på den bruger, der oprindeligt uploadede dokumentationen, vises ikke længere i forbedringshandlingen.

**Følg nedenstående trin for at tildele forbedringshandlinger til en anden bruger:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> på Microsoft Purview-overholdelsesportalen.

2. Vælg **Overholdelsesstyring** på siden Indstillinger.

3. Vælg **Administrer brugerhistorik** i navigationen til venstre.

4. Find en bruger ved at søge i listens mailadresser eller ved at vælge **Søg** og angive den pågældende brugers mailadresse.

5. Vælg **Overdrag forbedringshandlinger** i rullemenuen **Vælg**. Pop op-vinduet **Videretildel forbedringshandlinger** vises.

6. I feltet **Søg efter brugere** skal du angive navnet eller mailadressen på den bruger, du vil tildele forbedringshandlingerne *til*.

7. Når du ser navnet på den ønskede bruger under **Forbedringshandlinger tildeles,** skal du vælge brugeren og derefter vælge **Tildel handlinger**.

8. Når omfordeling er fuldført, får du vist en bekræftelsesmeddelelse i pop op-ruden, der bekræfter, at alle forbedringshandlinger fra den forrige bruger er blevet tildelt den nye bruger. Hvis du modtager en meddelelse om omfordelingsfejl, skal du lukke vinduet og prøve igen. Hvis du vil lukke pop op-ruden, skal du vælge **Udført**.

Den nye modtager modtager en mail om, at vedkommende er blevet tildelt en forbedringshandling. Mailen indeholder et direkte link til detaljesiden for forbedringshandlingen.

 > [!NOTE]
> Hvis du tildeler en handling, der har en ventende opdatering, afbrydes det direkte link til handlingen i mailen om omfordeling, hvis opdateringen accepteres efter omfordeling. Du kan løse dette problem ved at tildele handlingen til brugeren igen, når opdateringen er accepteret. Få mere at vide om [opdateringer til forbedringshandlinger](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Slet brugerhistorik

Hvis du sletter en brugers historik, fjernes vedkommende som ejer af forbedringshandlinger og fjerner navnet fra alle andre felter i Overholdelsesstyring. Når du sletter en brugers historik, viser de forbedringshandlinger, vedkommende ejede, ikke værdien **Tildelt til** , før en ny bruger er tildelt. Alle dokumenter, der er overført til forbedringshandlingen, viser **, at Brugeren er fjernet** i stedet for den slettede brugers navn. Sletning af brugerhistorik er permanent.

Hvis du vil slette en brugers historik, skal du følge nedenstående trin:

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> på Microsoft Purview-overholdelsesportalen.

2. Vælg **Overholdelsesstyring** på siden Indstillinger.

3. Vælg **Administrer brugerhistorik** i navigationen til venstre.

4. Find en bruger ved at søge i listens mailadresser eller ved at vælge **Søg** og angive den pågældende brugers mailadresse.

5. Vælg **Slet historik** i rullemenuen **Vælg**.

6. Der vises et vindue, hvor du bliver bedt om at bekræfte den permanente sletning af brugerhistorikken. Hvis du vil fortsætte med at slette, skal du vælge **Slet historik**. Hvis du vil forlade uden at slette oversigten, skal du vælge **Annuller**.

7. Du kommer tilbage på siden **Administrer brugerhistorik** med en bekræftelsesmeddelelse øverst om, at historikken for brugeren er blevet slettet.

## <a name="understand-the-compliance-manager-dashboard"></a>Forstå dashboardet Overholdelsesstyring

Dashboardet Overholdelsesstyring er designet til at give dig et hurtigt overblik over din aktuelle overholdelse af angivne standarder.

:::image type="content" alt-text="Overholdelsesstyring – dashboard." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Samlet score for overholdelse af angivne standarder

Din overholdelsesscore er fremhævet øverst. Den viser en procentdel baseret på punkter, der er opnåelige for fuldførelse af forbedringshandlinger, der omhandler vigtige standarder og bestemmelser for databeskyttelse. Punkter fra [Microsoft-handlinger](compliance-manager-assessments.md#microsoft-actions-tab), som administreres af min Microsoft, tæller også med i din score for overholdelse af angivne standarder.

Første gang, du kommer til Overholdelsesstyring, er din oprindelige score baseret på [Microsoft 365 baseline for databeskyttelse](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Denne grundlæggende vurdering, som er tilgængelig for alle organisationer, er et sæt kontrolelementer, der indeholder fælles brancheregler og -standarder. Overholdelsesstyring scanner dine eksisterende Microsoft 365 løsninger og giver dig en indledende vurdering baseret på dine aktuelle indstillinger for beskyttelse af personlige oplysninger og sikkerhed. Når du tilføjer vurderinger, der er relevante for din organisation, bliver din score mere meningsfuld for dig.

**Få mere at vide:** [Forstå, hvordan din overholdelsesscore beregnes](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Nøgleforbedringshandlinger

I dette afsnit beskrives de vigtigste forbedringshandlinger, du kan udføre lige nu for at få den største positive indvirkning på din overordnede score for overholdelse af angivne standarder. Vælg **Vis alle forbedringshandlinger** for at gå til siden forbedringshandlinger.

### <a name="solutions-that-affect-your-score"></a>Løsninger, der påvirker din score

I dette afsnit fremhæves løsninger, der indeholder forbedringshandlinger, som kan have positiv indvirkning på din score, og antallet af udestående forbedringshandlinger i disse løsninger. Vælg **Få vist alle løsninger** for at besøge din løsningsside.

### <a name="compliance-score-breakdown"></a>Opdeling af overholdelsesscore

I dette afsnit får du en mere detaljeret visning af din score på to forskellige måder:

- **Kategorier**: Viser procentdelen af din overordnede score inden for databeskyttelseskategorier, f.eks. "Beskyt oplysninger" eller "Administrer enheder".
- **Vurderinger**: Viser procentdelen af dine fremskridt i administrationen af vurderinger for bestemte standarder og databeskyttelsesstandarder, -forordninger eller -love, f.eks. GDPR eller NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrering af dashboardvisningen

Du kan filtrere din dashboardvisning for kun at se de elementer, der er relateret til bestemte regler og standarder, løsninger, handlingstype, vurderingsgrupper eller databeskyttelseskategorier. Hvis du filtrerer visningen på denne måde, filtreres scoren også på dit dashboard, så det vises, hvor mange point du har opnået ud af det samlede antal mulige point baseret på dine filterkriterier.

Sådan anvender du filtre:

1. Vælg **Filtrer** i øverste højre side af dashboardet.
2. Vælg dine filterkriterier i pop op-vinduet **Filtre** , og vælg derefter **Anvend**.

Når du har anvendt et filter, kan du se, at din score er justeret i realtid. Procent- og opdelingsoplysninger for overholdelse af angivne standarder og forbedringshandlinger og -løsninger vedrører nu kun data, der er omfattet af dine filterkriterier. Hvis du logger af Overholdelsesstyring, forbliver din filtrerede visning, når du logger på igen.

Sådan fjerner du filtre:

- I overskriften **Anvendte filtre** over din overholdelsesscore skal du vælge **X** ud for det individuelle filter, du vil fjerne. Eller
- Vælg **Filtrer** i øverste højre side af dashboardet, og vælg derefter **Ryd filtre** i pop op-ruden **Filtre**.

## <a name="improvement-actions-page"></a>Siden Forbedringshandlinger

[Forbedringshandlinger](compliance-manager-improvement-actions.md) er handlinger, der administreres af din organisation. Arbejde med forbedringshandlinger hjælper med at centralisere dine aktiviteter for overholdelse af angivne standarder og tilpasse sig databeskyttelsesreglerne og -standarderne. Hver forbedringshandling giver detaljeret implementeringsvejledning og et link til at starte dig i den relevante løsning. Forbedringshandlinger kan tildeles til brugere i din organisation for at udføre implementerings- og testarbejde. Du kan også gemme dokumentation, noter og poststatusopdateringer i forbedringshandlingen.

### <a name="view-your-improvement-actions"></a>Vis dine forbedringshandlinger

Dashboardet Overholdelsesstyring viser dine vigtigste forbedringshandlinger. Hvis du vil have vist alle dine forbedringshandlinger, skal du vælge fanen **Forbedringshandlinger** på dit dashboard, hvilket fører dig til siden forbedringshandlinger. Du kan også vælge **Vis alle forbedringshandlinger** under listen over handlinger til forbedring af vigtige forbedringer på dit dashboard for at få adgang til siden med forbedringshandlinger.

Siden Forbedringshandlinger viser alle de forbedringshandlinger, der administreres af din organisation. Handlinger, der administreres af Microsoft, kan ses i hver vurdering (få mere at vide om [Microsoft-handlinger](compliance-manager-assessments.md#microsoft-actions-tab)).

Hvis du har en lang liste over handlinger på siden forbedringshandlinger, kan det være nyttigt at filtrere visningen. Vælg **Filtrer** i øverste højre hjørne af handlingslisten. Når pop op-vinduet **Filtre** vises, skal du vælge dine kriterier fra de tilgængelige indstillinger. Du kan også tilpasse visningen ved at vælge **Gruppér** i øverste højre hjørne. Vælg i rullemenuen for at få vist efter gruppe, løsning, kategori, handlingstype eller status.

Standardvisningen for denne side viser ikke forbedringshandlinger med **teststatussen Bestået**. Hvis du vil have vist handlinger, der har bestået testen, skal du markere afkrydsningsfeltet **Bestået** i pop op-vinduet Filtre. Kun handlinger med **teststatussen Bestået** antal mod din score. Nogle handlinger kan vise en **ventende opdateringsmærkat.** Få mere at vide om [opdateringer til forbedringshandlinger](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

Siden forbedringshandlinger viser følgende datapunkter for hver forbedringshandling:

- **Produkter**: det produkt, der evalueres.
- **Opnåede point**: antallet af point, der er opnået ud af det samlede antal tilgængelige ved at gennemføre
- **Forordninger**: de forordninger eller standarder, der gælder for handlingen
- **Gruppe**: den gruppe, du har tildelt handlingen
- **Løsninger**: Den løsning, du kan gå til for at udføre handlingen
- **Vurderinger**: de vurderinger, der indeholder handlingen
- **Kategorier**: den relaterede databeskyttelseskategori (f.eks. beskytte oplysninger, administrere enheder osv.)
- **Teststatus**:
  - **Ingen** – ingen statusopdatering er registreret
  - **Ikke vurderet** – testen er ikke startet
  - **Bestået** – implementeringen blev testet
  - **Lav risiko mislykkedes** – test mislykkedes, lav risiko
  - **Mislykket mellemstor risiko** - test mislykkedes, mellem risiko
  - **Mislykket høj risiko** - test mislykkedes, høj risiko
  - **Uden for omfanget** – handlingen er ikke omfattet af vurderingen og påvirker ikke din score
  - **At blive opdaget** – til manuel test angiver, at en handling er blevet implementeret, men ikke testet. angiver, at en handling venter på et automatiseringsresultat i forbindelse med automatiseret test
  - **Kunne ikke registreres** - automatiseret status kan ikke bestemmes
  - **Delvist testet** – automatisk pointtildeling, der tildeler delvise point
- **Handlingstype**: Angiver, om forbedringshandlingen er teknisk, hvilket betyder, at den kan implementeres i en løsning eller et produkt eller ikke-teknisk, som vil blive implementeret uden for en teknisk løsning
- **Tildelt til**: Den person, denne handling er tildelt til, hvis det er relevant
- **Testkilde**: Angiver, om testkilden for handlingen er manuel, automatisk eller nedarvet fra en overordnet

**Få mere at vide:** [Se, hvordan du tildeler og udfører arbejde på forbedringshandlinger](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Siden Løsninger

På løsningssiden kan du se andelen af optjente og potentielle point, som organiseret efter løsning. Visning af dine resterende punkter og forbedringshandlinger fra denne visning hjælper dig med at forstå, hvilke løsninger der kræver mere øjeblikkelig opmærksomhed.

Find siden Løsninger ved at vælge fanen **Løsninger** på dashboardet Overholdelsesstyring. Du kan også vælge **Få vist alle løsninger** under **Løsninger, der påvirker din score** , i øverste højre afsnit af dashboardet.

### <a name="filtering-your-solutions-view"></a>Filtrering af din løsningsvisning

Sådan filtrerer du visningen af løsninger:

1. Vælg **Filtrer** i øverste venstre hjørne af listen over vurderinger.
2. I pop op-vinduet **Filtre** skal du markere de ønskede kriterier (regler, løsninger, handlingstyper, grupper og kategorier).
3. Vælg knappen **Anvend** . Filterruden lukkes, og du kan se din filtrerede visning.

Du kan også ændre visningen for at få vist vurderinger efter gruppe, produkt eller regulering ved at vælge grupperingstypen i rullemenuen **Gruppe** over listen over vurderinger.

### <a name="taking-action-from-the-solution-page"></a>Handling fra løsningssiden

På løsningssiden vises organisationens løsninger, der er forbundet med forbedringshandlinger. Tabellen viser hver løsnings bidrag til din overordnede score, de opnåede point og mulige i den pågældende løsning samt det resterende antal forbedringshandlinger, der er grupperet i den pågældende løsning, som kan øge din score.

Der er to måder, du kan udføre handlinger på fra dette skærmbillede:

1. I rækken i den ønskede løsning skal du under kolonnen **Resterende handlinger** vælge linkets nummer. Du får vist en filtreret visning af skærmbilledet forbedringshandlinger, der viser utestede forbedringshandlinger for den løsning.

2. Vælg **Åbn** i rækken i den ønskede løsning under kolonnen **Åbn løsning**. Du kan se løsningen eller placeringen i Microsoft 365 og Office 365 sikkerheds- og overholdelsescentre, hvor du kan udføre den anbefalede handling.

## <a name="assessments-page"></a>Siden Vurderinger

På siden vurderinger vises alle de [vurderinger](compliance-manager-assessments.md) , du har konfigureret for din organisation. Nævneren for din overholdelsesscore bestemmes af alle dine sporede vurderinger. Når du tilføjer flere vurderinger, kan du se flere forbedringshandlinger angivet på siden forbedringshandlinger, og nævneren for overholdelse af angivne standarder øges.

Tælleren **med aktiverede skabeloner** øverst på siden viser antallet af aktive vurderingsskabeloner, der i øjeblikket bruges ud af det samlede antal skabeloner, der er tilgængelige for din organisation. Se [Skabelontilgængelighed og licenser](compliance-manager-templates.md#template-availability-and-licensing) for at få flere oplysninger.

Vurderingssiden opsummerer vigtige oplysninger om hver vurdering:

- **Vurdering**: Vurderingsnavnet
- **Status**:
  - **Fuldført** – alle kontrolelementer har statussen "bestået", eller mindst ét er bestået, og resten er "uden for omfanget"
  - **Ufuldstændig** – mindst ét kontrolelement har statussen "mislykkedes"
  - **Ingen** – alle kontrolelementer er ikke blevet testet
  - **Igangværende** – forbedringshandlinger har en anden status, herunder "igangværende", "delvis kredit" eller "uopdaget
- **Vurderingsstatus**: Procentdelen af det arbejde, der udføres mod færdiggørelse, målt i antallet af vellykkede kontroller
- **Dine forbedringshandlinger**: Antallet af fuldførte handlinger, der opfylder implementeringen af dine kontrolelementer
- **Microsoft-handlinger**: Antallet af fuldførte handlinger, der skal opfylde implementeringen af Microsoft-kontrolelementer
- **Gruppe**: Navnet på den gruppe, som vurderingen tilhører
- **Produkt**: tilknyttet produkt, f.eks. Microsoft 365 eller et andet produkt, der er defineret til vurdering
- **forordning**: den lovgivningsmæssige standard, politik eller lovgivning, der gælder for vurderingen

### <a name="filtering-your-assessments-view"></a>Filtrering af din vurderingsvisning

Sådan filtrerer du visningen af vurderinger:

1. Vælg **Filtrer** i øverste venstre hjørne af listen over vurderinger.
2. Kontrollér de ønskede kriterier i pop op-vinduet **Filtre** .
3. Vælg knappen **Anvend** . Filterruden lukkes, og du kan se din filtrerede visning.

Du kan også ændre visningen for at få vist vurderinger efter gruppe, produkt eller regulering ved at vælge grupperingstypen i rullemenuen **Gruppe** over listen over vurderinger.

### <a name="default-assessment"></a>Standardvurdering

Som standard kan du se vurderingen af [den grundlæggende databeskyttelse](compliance-manager-assessments.md#data-protection-baseline-default-assessment) på siden vurderinger. Overholdelsesstyring indeholder også flere færdigbyggede [skabeloner](compliance-manager-templates-list.md) til oprettelse af vurderinger.

## <a name="assessment-templates-page"></a>Siden Vurderingsskabeloner

En skabelon er en struktur til oprettelse af en vurdering i Overholdelsesstyring. På siden med vurderingsskabeloner vises en liste over skabeloner og vigtige oplysninger. Listen indeholder skabeloner, der leveres af Overholdelsesstyring, samt alle skabeloner, din organisation har ændret eller oprettet. Du kan anvende filtre til at finde en skabelon, der er baseret på certificering, produktområde, land, branche og hvem der har oprettet den.

Tælleren **med aktiverede skabeloner** øverst på siden viser antallet af aktive vurderingsskabeloner, der i øjeblikket bruges ud af det samlede antal skabeloner, der er tilgængelige for din organisation. Se [Skabelontilgængelighed og licenser](compliance-manager-templates.md#template-availability-and-licensing) for at få flere oplysninger.

Vælg en skabelon fra rækken for at få vist detaljesiden, som indeholder en beskrivelse af skabelonen og yderligere oplysninger om certificering, omfang og kontrolelementer. På denne side kan du vælge de relevante knapper for at oprette en vurdering, eksportere skabelondataene til Excel eller redigere skabelonen.

**Få mere at vide:** [Læs, hvordan du arbejder med vurderingsskabeloner](compliance-manager-templates.md).

## <a name="next-step"></a>Næste trin

Tilpas Overholdelsesstyring ved [at konfigurere vurderinger](compliance-manager-assessments.md).
