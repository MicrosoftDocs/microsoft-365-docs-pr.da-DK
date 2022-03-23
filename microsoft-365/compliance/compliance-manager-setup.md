---
title: Introduktion til Microsoft Compliance Manager
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
description: Angiv brugertilladelser og -roller i Microsoft Compliance Manager, og konfigurer automatiserede test af handlinger. Administrer brugerhistorikken, og filtrer din dashboardvisning.
ms.openlocfilehash: a6a0d7c12b0f798b88d460517866c55862c56740
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594326"
---
# <a name="get-started-with-compliance-manager"></a>Introduktion til Overholdelsesstyring

**I denne artikel:** Denne artikel hjælper dig med at konfigurere Overholdelsesstyring. Få mere at vide **om, hvordan** du får **adgang til Overholdelsesstyring, angiver** roller og tilladelser og **konfigurerer automatisk test af forbedringshandlinger**. Gennemgå **dashboardet i Overholdelsesstyring** og forstå hovedsiderne: siden med forbedringshandlinger, siden med løsninger, siden med bedømmelsesvurderinger og siden med bedømmelsesskabeloner.

## <a name="who-can-access-compliance-manager"></a>Who kan få adgang til Overholdelsesstyring

Overholdelsesstyring er tilgængelig for organisationer med Office 365- og Microsoft 365-licenser og for amerikanske Government Community Cloud-kunder (GCC) Moderate, GCC High og Department of Defense (DoD). Mulighederne for vurdering af tilgængelighed og administration afhænger af din licensaftale.  [Vis oplysninger om tjenestebeskrivelse](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="before-you-begin"></a>Før du begynder

Organisationens Microsoft 365 vil sandsynligvis være den første bruger til at få adgang til Overholdelsesstyring. Vi anbefaler, at den globale administrator logger på og angiver brugertilladelser som beskrevet nedenfor, når du besøger Overholdelsesstyring for første gang.

## <a name="sign-in"></a>Log på

1. Gå til Microsoft 365 Overholdelsescenter <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">,</a> **og log på** med Microsoft 365 globale administratorkonto.
2. Vælg **Styring af overholdelse** i venstre navigationsrude. Du kommer til dashboardet [Overholdelsesstyring](#understand-the-compliance-manager-dashboard).

Det direkte link til at få adgang til Overholdelsesstyring er [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Angive brugertilladelser og tildele roller

Overholdelsesstyring anvender en rollebaseret tilladelsesmodel for adgangskontrol (RBAC). Kun brugere, der er tildelt en rolle, kan få adgang til Overholdelsesstyring, og de handlinger, der tillades af hver enkelt bruger, er begrænset af [rolletype](#role-types).

### <a name="where-to-set-permissions"></a>Hvor du kan angive tilladelser

Den person, der har organisationens globale administratorrolle, kan angive brugertilladelser for Overholdelsesstyring. Tilladelser kan angives i Microsoft 365 Overholdelsescenter samt i Azure Active Directory (Azure AD).

> [!NOTE]
> Kunder i det amerikanske government community (GCC) High- og Department of Defense-miljøer (DoD) kan kun angive brugertilladelser og roller for Overholdelsesstyring i Azure AD. Se vejledningen og rolletypedefinitioner for Azure AD nedenfor.

Hvis du vil angive tilladelser og tildele roller i Microsoft 365 Overholdelsescenter, skal du følge trinnene nedenfor:

1. Gå til Microsoft 365 Overholdelsescenter, og <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**vælg Tilladelser**</a>.

2. Under **rullelisten Overholdelsescenter** skal du vælge **Roller**.

3. Find den rollegruppe, du vil føje en eller flere brugere til, og markér afkrydsningsfeltet til venstre for gruppenavnet. (Se [listen over roller og relaterede funktioner nedenfor](#role-types). Rollegruppenavnene efterligner rollenavnet).

4. I pop op-ruden for den pågældende gruppe skal du **vælge Rediger** under **sidehovedet** Medlemmer.

5. Vælg **Vælg medlemmer**. Der vises et andet pop op-vindue.

6. Vælg **+ Tilføj for** at vælge en eller flere brugere at føje til gruppen.

7. Markér afkrydsningsfeltet ud for de navne, du vil tilføje, og vælg **derefter knappen** Tilføj nederst.

8. Når du er færdig med at tildele brugere, skal du **vælge Udført** og derefter **vælge Gem** og derefter **Luk**.

#### <a name="more-about-azure-ad"></a>Mere om Azure AD

Hvis du vil tildele roller og angive tilladelser i Azure AD, skal du se [Tildel administratorroller og ikke-administratorroller til brugere med Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Brugere med Azure AD-identiteter, der ikke har Office 365- eller Microsoft 365-abonnementer, vil ikke kunne få adgang til Overholdelsesstyring i Microsoft 365 Overholdelsescenter. Hvis du vil have hjælp til at få adgang til Overholdelsesstyring, [skal du cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Rolletyper

Tabellen nedenfor viser de funktioner, der er tilladt for hver rolle i Overholdelsesstyring. Tabellen viser også, hvordan hver [Azure AD-rolle tilknyttes](/azure/active-directory/roles/permissions-reference) overholdelsesstyringsroller. Brugere skal som minimum have læserrollen Compliance Manager eller den globale Azure AD-læserrolle for at få adgang til Overholdelsesstyring.

| Brugeren kan: | Overholdelsesstyringsrolle | Azure AD-rolle | 
| :------------- | :-------------: | :------------: |
| **Læse, men ikke redigere data**| Overholdelsesstyringslæser  | Azure AD Global læser, sikkerhedslæser |
| **Rediger data**| Bidrag til Overholdelsesstyring | Overholdelsesadministrator |
| **Rediger testresultater**| Compliance Manager Assessor | Overholdelsesadministrator |
| **Administrer bedømmelser, skabeloner og lejerdata**| Administration af overholdelsesstyring | Overholdelsesadministrator, dataadministrator for overholdelse af regler og standarder, sikkerhedsadministrator  |
| **Tildel brugere**| Global Administrator | Global Administrator |

## <a name="start-a-premium-assessments-trial"></a>Start en prøveversion af premiumvurderinger

Prøveversionen af Premium Assessments i Compliance Manager er en god måde til hurtigt at konfigurere bedømmelser, der er mest relevante for din organisation. Vores bibliotek med mere end 300 skabeloner svarer til statslige love og standarder og branchestandarder over hele verden.
Få mere at vide om [prøveversionen af Premium-bedømmelsesvurderinger](compliance-easy-trials-compliance-manager-assessments.md).

Du kan starte din prøveversion direkte fra Compliance Manager og konfigurere anbefalede bedømmelser ved at følge disse trin:

1. På siden Oversigt over **Overholdelsesstyring** skal du vælge **Start prøveversion**. Du skal angive en guide til aktivering af prøveversionen, som stiller spørgsmål, som kan hjælpe os med at anbefale vurderinger til din organisation.

2. På siden **Aktivér prøveversion** skal du vælge **Næste** for at starte din gratis prøveversion af 90 dages premium-bedømmelser og fortsætte med at oprette bedømmelser.

3. Vælg en eller flere brancher, der identificerer din organisation, og vælg derefter **Næste**.

4. Vælg et eller flere områder for din organisations placering, og vælg derefter **Næste**.

5. På **skærmbilledet Vælg bedømmelser** skal du vælge rullepilen ud for  Anbefalede skabeloner for at få vist en liste over bedømmelser, vi mener gælder for din organisation. Markér afkrydsningsfelterne ud for de skabeloner, du vil bruge til at oprette bedømmelsesvurderinger, og vælg derefter **Næste**.

6. Gennemgå dine endelige valg, og vælg **Tilføj anbefalede bedømmelser for** at oprette dine nye bedømmelser.

Få mere at vide om at komme i gang med bedømmelser ved at gå [til afsnittet med siden](#assessments-page) Bedømmelser nedenfor.

## <a name="settings-for-automated-testing-and-user-history"></a>Indstillinger til automatiseret test og brugerhistorik

Indstillingerne for Overholdelsesstyring i Microsoft 365 Overholdelsescenter du aktivere og deaktivere automatisk test af forbedringshandlinger. Indstillingerne giver dig også mulighed for at administrere data for brugere, der er knyttet til forbedringshandlinger, herunder muligheden for at tildele forbedringshandlinger til en anden bruger.  Kun personer med en global administrator- eller overholdelsesadministratorrolle kan få adgang til indstillingerne for Overholdelsesstyring.

> [!NOTE]
> Funktionen automatiserede test er ikke tilgængelig for kunder i GCC High- og DoD-miljøer, fordi Secure Score ikke er tilgængelig i disse miljøer. GCC High- og DoD-kunder skal implementere og teste deres forbedringshandlinger manuelt.

### <a name="set-up-automated-testing"></a>Konfigurer automatiserede test

Overholdelsesstyring registrerer signaler fra andre Microsoft 365-overholdelsesløsninger, som din organisation abonnerer på, herunder informationsstyring, beskyttelse af oplysninger, forebyggelse af datatab, kommunikationsoverholdelse og insider-risikostyring. På detaljesiden for hver forbedringshandling viser feltet  Testlogik på fanen  Test, hvad der kræves i den anden løsning, for at handlingen kan bestå og optjene point i din overholdelsesscore.

Overholdelsesstyring registrerer også signaler fra supplerende forbedringshandlinger, som også overvåges af [Microsoft Secure Score](../security/defender/microsoft-secure-score.md). Ved hjælp af disse signaler kan Overholdelsesstyring automatisk teste visse forbedringshandlinger for dig, hvilket er med til at maksimere effektiviteten i dine overholdelsesaktiviteter. Når en forbedringshandling er blevet testet og implementeret, modtager du det fulde antal point, som bliver krediteret dit overordnede pointtal for overholdelse af regler og standarder.

Automatisk test er slået til som standard for organisationer, der ikke har en ny organisation til overholdelse af regler og standarder. Når du først installerer Microsoft 365 eller Office 365, tager det ca. syv dage at samle data og faktoren fuldt ud i din overholdelsesscore. Når automatiserede test er slået til, opdateres handlingens testdato ikke, men dens teststatus opdateres. Når der oprettes nye bedømmelser, omfatter karakterer automatisk Microsofts kontrolresultater og integration af Secure Score.

#### <a name="manage-automated-testing-settings"></a>Administrer indstillinger for automatiserede test

Den globale administrator for din organisation kan når som helst ændre indstillingerne for automatiserede test. Du kan deaktivere automatiserede test for almindelige forbedringshandlinger eller aktivere det for individuelle handlinger. Følg vejledningen nedenfor for at ændre dine indstillinger for automatiserede test.

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> i Microsoft 365 Overholdelsescenter.

2. Vælg Overholdelsesstyring på **siden med indstillinger**.

3. Vælg **Automatiserede test** fra venstre navigationslinje.

4. Vælg den relevante knap for at slå automatisk test til for alle forbedringshandlinger, slå den fra for alle handlinger eller slå den til med individuel handling.

5. Hvis du vælger **Slå pr. forbedring til**, vises alle de tilgængelige forbedringshandlinger, du kan vælge mellem, på en liste.  Markér afkrydsningsfeltet ud for en handling, der skal testes automatisk.

6. Vælg **Gem** for at gemme dine indstillinger. Du modtager en bekræftelsesmeddelelse øverst på skærmen om, at dit valg blev gemt. Hvis du modtager en meddelelse om fejl, kan du prøve igen.

**Bemærk!** Kun den globale administrator kan aktivere eller deaktivere automatiske opdateringer for alle handlinger. Overholdelsesstyringsadministratoren kan aktivere automatiske opdateringer for individuelle handlinger, men ikke for alle handlinger globalt.

**Få mere at vide**
- [Få mere at vide om, hvordan løbende overvågning bidrager til din overholdelsesscore](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).
- [Få mere at vide om at designe en testkilde for en forbedringshandling](compliance-manager-improvement-actions.md#update-testing-source).

### <a name="manage-user-history"></a>Administrere brugerhistorik

Med **Administrer indstillinger for brugerhistorik** kan du hurtigt identificere, hvilke brugere der har arbejdet med forbedringshandlinger i Overholdelsesstyring. De identificerbare brugerdata, der er knyttet til forbedringshandlinger omfatter eventuelle implementerings- og testarbejde, de overførte dokumenter og eventuelle noter, de har angivet. Det kan være nødvendigt at forstå og hente denne type data for at opfylde din organisations egne behov for overholdelse af regler og standarder.

Indstillingerne for brugeroversigten giver dig også mulighed for at tildele alle forbedringshandlinger fra én bruger til en anden.

**Sådan finder du indstillingerne for brugeroversigten:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> i Microsoft 365 Overholdelsescenter.

2. Vælg Overholdelsesstyring på **siden med indstillinger**.

3. Vælg **Administrer brugerhistorik i** venstre navigationsrude.

Siden **Administrer brugerhistorik** viser en liste over alle brugere via mailadresse, der er tildelt en forbedringshandling. Brug knappen **Søg** til hurtigt at finde en bestemt bruger ved at skrive mailadressen.

Til højre for hver brugers mailadresse indeholder rullemenuen Vælg indstillinger  til at eksportere en rapport, tildele forbedringshandlinger eller slette oversigten. Se hver sektion nedenfor for at få mere at vide om hver indstilling.

#### <a name="export-a-report-of-user-history-data"></a>Eksportere en rapport over data i brugerhistorikken

Du kan eksportere en Excel fil, der indeholder en liste over forbedringshandlinger, der aktuelt er tildelt en bruger.  Rapporten viser også eventuelle bevisfiler, der er uploadet af den pågældende bruger. Disse oplysninger kan hjælpe dig med at tildele åbne forbedringshandlinger igen.

Rapporten afspejler forbedringshandlingens status fra oprettelsesdatoen. Det er ikke en historisk rapport over alle tidligere ændringer af dens status eller opgave (se, hvordan du eksporterer en rapport [fra siden med forbedringshandlinger](compliance-manager-improvement-actions.md#export-a-report)).

**Følg trinnene nedenfor for at eksportere en rapport efter bruger:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> i Microsoft 365 Overholdelsescenter.

2. Vælg Overholdelsesstyring på **siden med indstillinger**.

3. Vælg **Administrer brugerhistorik** på navigationslinjen til venstre.

4. Find den tilsigtede bruger ved at søge i listens mailadresser eller ved at **vælge** Søg og indtaste brugerens mailadresse.

5. Vælg **Eksportér** rapport i rullemenuen **Vælg**.

6. Når den Excel af rapporten er oprettet, kan du åbne den og gemme den på din lokale computer.

#### <a name="reassign-improvement-actions-to-another-user"></a>Tildele forbedringshandlinger til en anden bruger

Du kan omfordele forbedringshandlinger fra én bruger til en anden. Når du tildeler en handling igen, ændres overførselsoversigten for dokumentet ikke, men navnet på den bruger, der oprindeligt overførte dokumentationen, vises ikke længere i forbedringshandlingen.

**Følg trinnene nedenfor for at tildele forbedringshandlinger til en anden bruger:**

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> i Microsoft 365 Overholdelsescenter.

2. Vælg Overholdelsesstyring på **siden med indstillinger**.

3. Vælg **Administrer brugerhistorik** på navigationslinjen til venstre.

4. Find en bruger ved at søge i listens mailadresser eller ved **at vælge Søg** og angiv den pågældende brugers mailadresse.

5. I **rullemenuen** Vælg skal du vælge **Tildel forbedringshandlinger igen**. Pop **op-ruden Omfordele** forbedringshandlinger vises.

6. I feltet **Søg efter brugere** skal du skrive navnet eller mailadressen på den bruger, du vil tildele forbedringshandlingerne *til*.

7. Når du ser navnet på den tilsigtede bruger under Der **tildeles** forbedringshandlinger til, skal du vælge brugeren og derefter vælge **Tildel handlinger**.

8. Når omfordelingen er fuldført, vises der en bekræftelsesmeddelelse i pop op-ruden, der bekræfter, at alle forbedringshandlinger fra den forrige bruger er blevet tildelt den nye bruger igen. Hvis du modtager en meddelelse om ny tildelingsfejl, skal du lukke vinduet og prøve igen. Vælg Udført for at lukke pop **op-ruden**.

Den nye modtager modtager en mail om, at han/hun har fået tildelt en forbedringshandling. Mailen indeholder et direkte link til detaljesiden for forbedringshandlingen.

 > [!NOTE]
> Hvis du tildeler en handling, der har en ventende opdatering, brydes det direkte link til handlingen i mailen med en ny tildeling, hvis opdateringen accepteres efter en ny tildeling. Du kan løse dette problem ved at tildele handlingen til brugeren igen, når opdateringen er blevet accepteret. Få mere at vide [om opdateringer til forbedringshandlinger](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Slet brugerhistorik

Hvis du sletter en brugers historik, fjernes vedkommende som ejer af forbedringshandlinger, og vedkommendes navn fjernes fra alle andre felter i Overholdelsesstyring. Når du sletter en brugers historik, viser de forbedringshandlinger, brugeren ejer, ikke  en Tildelt til-værdi, før en ny bruger tildeles. Alle dokumenter, der uploades til **forbedringshandlingen, viser** brugeren, der er fjernet i stedet for den slettede brugers navn. Når du sletter brugerhistorikken, er det en permanent fejl.

Hvis du vil slette en brugers historik, skal du følge trinnene nedenfor:

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Indstillinger**</a> i Microsoft 365 Overholdelsescenter.

2. Vælg Overholdelsesstyring på **siden med indstillinger**.

3. Vælg **Administrer brugerhistorik** på navigationslinjen til venstre.

4. Find en bruger ved at søge i listens mailadresser eller ved **at vælge Søg** og angiv den pågældende brugers mailadresse.

5. Vælg **Slet** historik i rullemenuen **Vælg**.

6. Der vises et vindue, hvor du bliver bedt om at bekræfte den permanente sletning af brugerens oversigt. Hvis du vil fortsætte med sletningen, skal du **vælge Slet oversigt**. Hvis du vil forlade uden at slette oversigten, skal du vælge **Annuller**.

7. Du kommer tilbage til siden **Administrer brugerhistorik** med en bekræftelsesmeddelelse øverst om, at historikken for brugeren er blevet slettet.

## <a name="understand-the-compliance-manager-dashboard"></a>Forstå dashboardet i Overholdelsesstyring

Dashboardet Overholdelsesstyring er designet til at give dig et hurtigt overblik over din aktuelle overholdelsesoverholdelse.

:::image type="content" alt-text="Overholdelsesstyring – dashboard." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Samlet overholdelsesscore

Dit resultat af overholdelse af regler og standarder fremhæves fremtrædende øverst. Den viser en procentdel baseret på mulige punkter for at fuldføre forbedringshandlinger, der adresserer de vigtigste standarder og bestemmelser om databeskyttelse. Point fra [Microsoft-handlinger](compliance-manager-assessments.md#microsoft-actions-tab), som administreres af Microsoft, tæller også med i din overholdelsesscore.

Når du kommer til Overholdelsesstyring for første gang, er dit første resultat baseret på Microsoft 365 [grundlinjen for databeskyttelse](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Denne vurdering af grundlinje, som er tilgængelig for alle organisationer, er et sæt kontrolelementer, der omfatter fælles branchebestemmelser og -standarder. Compliance Manager scanner dine eksisterende Microsoft 365-løsninger og giver dig en indledende vurdering baseret på dine aktuelle indstillinger for beskyttelse af personlige oplysninger og sikkerhed. Når du tilføjer bedømmelser, der er relevante for din organisation, giver dine resultater mere mening for dig.

**Få mere at vide:** [Forstå, hvordan dit resultat for overholdelse beregnes](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Vigtige forbedringshandlinger

Dette afsnit viser de vigtigste forbedringshandlinger, du kan foretage lige nu for at gøre den største positive indvirkning på dit overordnede resultat af overholdelse. Vælg **Vis alle forbedringshandlinger for** at gå til siden med dine forbedringshandlinger.

### <a name="solutions-that-affect-your-score"></a>Løsninger, der påvirker din score

Dette afsnit fremhæver løsninger, der indeholder forbedringshandlinger, der kan have en positiv effekt på din score, og antallet af udestående forbedringshandlinger i disse løsninger. Vælg **Vis alle løsninger for** at besøge din løsningsside.

### <a name="compliance-score-breakdown"></a>Vurdering af overholdelsesscore

Dette afsnit giver dig en mere detaljeret oversigt over dine resultater på to forskellige måder:

- **Kategorier**: Viser procentdelen af dit samlede resultat inden for kategorier til databeskyttelse, f.eks. "beskyt oplysninger" eller "administrer enheder".
- **Bedømmelser**: Viser procentdelen af dit fremskridt med at administrere bedømmelser af bestemte overholdelses- og databeskyttelsesstandarder, bestemmelser eller lovgivning, f.eks. GDPR eller NIST 800-53.

### <a name="filtering-your-dashboard-view"></a>Filtrering af din dashboardvisning

Du kan filtrere din dashboardvisning for kun at få vist de elementer, der er relateret til bestemte regler og standarder, løsninger, handlingstype, bedømmelsesgrupper eller kategorier til databeskyttelse. Filtrering af din visning på denne måde filtrerer også scoren på dit dashboard og viser, hvor mange point du har opnået ud af de samlede mulige point baseret på dine filterkriterier.

Sådan anvender du filtre:

1. Vælg **Filter** i øverste højre side af dashboardet.
2. Vælg dine filterkriterier fra pop **op-ruden** Filtre, og vælg derefter **Anvend**.

Når du anvender et filter, justeres din score i realtid. Oplysninger om overholdelsesscore og opdeling samt forbedringshandlinger og løsninger gælder nu kun data, der er dækket af dine filterkriterier. Hvis du logger af Overholdelsesstyring, forbliver den filtrerede visning, når du logger på igen.

Sådan fjerner du filtre:

- I overskriften **Anvendte filtre** over din overholdelsesscore skal du vælge **X ud** for det individuelle filter, du vil fjerne. eller
- Vælg **Filter** i øverste højre side af dashboardet, og vælg derefter **Ryd** filtre i pop **op-ruden Filtre**.

## <a name="improvement-actions-page"></a>Siden Forbedringshandlinger

[Forbedringshandlinger](compliance-manager-improvement-actions.md) er handlinger, der administreres af din organisation. Hvis du arbejder med forbedringshandlinger, kan det centralisere dine overholdelsesaktiviteter og overholde regler og standarder inden for databeskyttelse. Hver forbedring giver detaljeret vejledning i implementering og et link til at sætte dig ind i den rette løsning. Forbedringshandlinger kan tildeles brugere i organisationen til at udføre implementerings- og testarbejde. Du kan også gemme dokumentation, noter og poststatusopdateringer i forbedringshandlingen.

### <a name="view-your-improvement-actions"></a>Få vist dine forbedringshandlinger

Dashboardet Overholdelsesstyring viser dine vigtigste forbedringshandlinger. Hvis du vil have vist alle dine forbedringshandlinger **, skal du** vælge fanen Forbedringshandlinger på dashboardet, som fører dig til siden med forbedringshandlinger. Du kan også vælge **Vis alle forbedringshandlinger** under listen over vigtige forbedringshandlinger på dit dashboard for at få adgang til siden med forbedringshandlinger.

Siden med forbedringshandlinger viser alle de forbedringshandlinger, der administreres af din organisation. Handlinger, der administreres af Microsoft, kan ses i hver vurdering (få mere at vide om [Microsoft-handlinger](compliance-manager-assessments.md#microsoft-actions-tab)).

Hvis du har en lang liste over handlinger på siden med forbedringshandlinger, kan det være nyttigt at filtrere din visning. Vælg **Filter** i øverste højre hjørne af listen handlinger. Når pop **op-ruden** Filtre vises, skal du vælge dine kriterier fra de tilgængelige indstillinger. Du kan også tilpasse din visning ved at **vælge** Gruppe i øverste højre hjørne. I rullemenuen skal du vælge at få vist efter gruppe, løsning, kategori, handlingstype eller status.

Standardvisningen for denne side viser ikke forbedringshandlinger med teststatus **Bestået**. Hvis du vil have vist handlinger, der er blevet testet, skal **du markere** afkrydsningsfeltet Bestået i pop op-ruden Filtre. Kun handlinger med teststatus **Bestået tæller** i din score. Nogle handlinger viser muligvis en **ventende opdateringsetiket.** Få mere at vide [om opdateringer til forbedringshandlinger](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

Siden med forbedringshandlinger viser følgende datapunkter for hver forbedringshandling:

- **Produkter**: det produkt, der evalueres.
- **Point, der er** opnået: det antal punkter, der er opnået i det tilgængelige total ved at fuldføre handlingen
- **Regulations**: the regulations or standards pertaining to the action
- **Gruppe**: den gruppe, som du tildelte handlingen
- **Løsninger**: den løsning, hvor du kan gå til at udføre handlingen
- **Bedømmelser**: De bedømmelser, der indeholder handlingen
- **Kategorier**: den relaterede kategori for databeskyttelse (f.eks. beskyttelse af oplysninger, administration af enheder osv.)
- **Teststatus**:
  - **Ingen** – ingen statusopdatering registreret
  - **Ikke vurderet** – testen er ikke startet
  - **Passed –** implementeringen er blevet testet
  - **Mislykkedes lav risiko** – test mislykkedes, lav risiko
  - **Mellemstor risiko mislykkedes** – test mislykkedes, mellemstor risiko
  - **Høj risiko mislykkedes** – test mislykkedes, høj risiko
  - **Uden for omfanget** – handlingen er ikke omfattet af vurderingen og påvirker ikke din score
  - **For at blive registreret –** for manuel test angiver det, at en handling er blevet implementeret, men ikke testet; for automatiseret test, angiver, at en handling venter på et automatiseringsresultat
  - **Kunne ikke findes –** automatiseret status kan ikke bestemmes
  - **Delvist testet** – automatiseret pointtal, der tildeler delvise point
- **Handlingstype**: angiver, om forbedringshandlingen er teknisk, dvs. den kan gennemføres inden for en løsning eller et produkt, eller ikke-teknisk, som skal implementeres uden for en teknisk løsning
- **Tildelt til**: den person, som denne handling er tildelt, hvis det er relevant
- **Testkilde**: Angiver, om testkilden for handlingen er manuel, automatisk eller nedarvet fra en overordnet

**Få mere at vide:** [Se, hvordan du tildeler og udfører arbejde på forbedringshandlinger](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Siden Løsninger

Siden med løsninger viser delingen af oparbejdet og potentielle point, som organiseret efter løsning. Visning af dine resterende punkter og forbedringshandlinger fra denne visning hjælper dig med at forstå, hvilke løsninger der kræver mere øjeblikkelig opmærksomhed.

Find siden med løsninger ved at vælge fanen **Løsninger på** dashboardet i Overholdelsesstyring. Du kan også vælge **Vis alle løsninger** under **Løsninger, der påvirker din score** i den øverste højre del af dit dashboard.

### <a name="filtering-your-solutions-view"></a>Filtrering af din løsningsvisning

Sådan filtrerer du din visning af løsninger:

1. Vælg **Filtrer** i øverste venstre hjørne af din bedømmelsesliste.
2. I pop **op-ruden** Filtre skal du markere ud for de ønskede kriterier (bestemmelser, løsninger, handlingstyper, grupper, kategorier).
3. Vælg **knappen Anvend** . Filterruden lukkes, og du får vist den filtrerede visning.

Du kan også ændre din visning for at få vist bedømmelser efter gruppe, produkt eller forordning ved at vælge typen af gruppering i rullemenuen Gruppe over din bedømmelsesliste.

### <a name="taking-action-from-the-solution-page"></a>Tage skridt fra løsningssiden

Løsningssiden viser organisationens løsninger, der har forbindelse til forbedringshandlinger. Tabellen viser hver løsnings bidrag til dit samlede resultat, de point, der er opnået og muligt i den pågældende løsning, og det resterende antal forbedringshandlinger, der er grupperet i den løsning, som kan øge din score.

Der er to måder, du kan handle på fra dette skærmbillede:

1. Vælg hyperlinknummeret i rækken af den **tilsigtede** løsning under kolonnen Resterende handlinger. Du får vist en filtreret visning af skærmbilledet med forbedringshandlinger, der viser utestede forbedringshandlinger for den pågældende løsning.

2. På rækken af din tilsigtede løsning skal du under **kolonnen Åbn løsning** vælge **Åbn**. Du får vist løsningen eller placeringen i Microsoft 365 og Office 365 overholdelsescenter, hvor du kan gøre den anbefalede handling.

## <a name="assessments-page"></a>Siden Bedømmelser

Siden Bedømmelser viser alle de [bedømmelser,](compliance-manager-assessments.md) du har konfigureret for din organisation. Din fællesnævner for overholdelse af regler og standarder bestemmes af alle dine registrerede bedømmelser. Efterhånden som du tilføjer flere bedømmelser, får du vist flere forbedringshandlinger på siden med dine forbedringshandlinger, og din fællesnævner for overholdelse af regler og standarder øges.

De **aktiverede skabeloner** tæller øverst på siden viser antallet af aktive bedømmelsesskabeloner, der aktuelt er i brug, ud af det samlede antal skabeloner, der er tilgængelige til brug for din organisation. Se Tilgængelighed [af skabeloner og licenser for](compliance-manager-templates.md#template-availability-and-licensing) at få flere oplysninger.

Siden med bedømmelsesvurderinger opsummerer vigtige oplysninger om hver vurdering:

- **Bedømmelse**: navnet på bedømmelsesvurderingen
- **Status**:
  - **Fuldført** – alle kontrolelementer har statussen "overskredet", eller mindst én overføres, og resten er "uden for området"
  - **Ufuldstændig** – mindst ét kontrolelement har statussen "mislykket"
  - **Ingen** – alle kontrolelementer er ikke blevet testet
  - **I gang** – forbedringshandlinger har alle andre statusser, herunder "i gang", "delvis kredit" eller "ikke opdaget"
- **Status for vurdering**: Procentdelen af det arbejde, der er udført mod fuldførelse, målt efter antallet af kontrolelementer, der er blevet testet
- **Dine forbedringshandlinger**: antallet af fuldførte handlinger, der opfylder implementeringen af dine kontrolelementer
- **Microsoft-handlinger**: antallet af fuldførte handlinger, der opfylder implementeringen af Microsoft-kontrolelementer
- **Gruppe**: navnet på den gruppe, vurderingen tilhører
- **Produkt**: tilknyttet produkt, f.eks. Microsoft 365 et andet produkt, der er defineret til vurdering
- **Forordning**: den lovgivningsmæssige standard, politik eller lovgivning, der gælder for bedømmelsen

### <a name="filtering-your-assessments-view"></a>Filtrering af din bedømmelsesvisning

Sådan filtrerer du visningen af bedømmelser:

1. Vælg **Filtrer** i øverste venstre hjørne af din bedømmelsesliste.
2. Markér **de ønskede** kriterier i pop op-ruden Filtre.
3. Vælg **knappen Anvend** . Filterruden lukkes, og du får vist den filtrerede visning.

Du kan også ændre din visning for at få vist bedømmelser efter gruppe, produkt eller forordning ved at vælge typen af gruppering i rullemenuen Gruppe over din bedømmelsesliste.

### <a name="default-assessment"></a>Standardvurdering

Som standard får du vist vurdering [af grundlinjer til databeskyttelse](compliance-manager-assessments.md#data-protection-baseline-default-assessment) på bedømmelsessiden. Overholdelsesstyring indeholder også adskillige færdigbyggede [skabeloner til](compliance-manager-templates-list.md) bedømmelser af bygninger.

## <a name="assessment-templates-page"></a>Side med bedømmelsesskabeloner

En skabelon er en ramme til at oprette en vurdering i Overholdelsesstyring. Siden med bedømmelsesskabeloner viser en liste over skabeloner og vigtige detaljer. Listen indeholder skabeloner fra Overholdelsesstyring samt alle skabeloner, din organisation har ændret eller oprettet. Du kan anvende filtre til at finde en skabelon, der er baseret på certificering, produktomfang, land, branche, og hvem der har oprettet den.

De **aktiverede skabeloner** tæller øverst på siden viser antallet af aktive bedømmelsesskabeloner, der aktuelt er i brug, ud af det samlede antal skabeloner, der er tilgængelige til brug for din organisation. Se Tilgængelighed [af skabeloner og licenser for](compliance-manager-templates.md#template-availability-and-licensing) at få flere oplysninger.

Vælg en skabelon fra dens række for at få vist dens detaljeside, som indeholder en beskrivelse af skabelonen og yderligere oplysninger om certificering, omfang og detaljer om kontrolelementer. Fra denne side kan du vælge de relevante knapper til at oprette en bedømmelsesvurdering, eksportere skabelondataene Excel eller redigere skabelonen.

**Få mere at vide:** [Læs, hvordan du arbejder med bedømmelsesskabeloner](compliance-manager-templates.md).

## <a name="next-step"></a>Næste trin

Tilpas Overholdelsesstyring [ved at konfigurere bedømmelser](compliance-manager-assessments.md).
