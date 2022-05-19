---
title: Teamets arbejdsgange i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Få mere at vide om, hvordan du bevarer, indsamler, gennemser og eksporterer indhold fra Microsoft Teams i eDiscovery (Premium).
ms.openlocfilehash: 46fe8491533f6d2fa6954eab76758213eaa7d30d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65414860"
---
# <a name="ediscovery-premium-workflow-for-content-in-microsoft-teams"></a>eDiscovery-arbejdsgangen (Premium) til indhold i Microsoft Teams

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denne artikel indeholder en række omfattende procedurer, retningslinjer og bedste praksis for brug af Microsoft Purview eDiscovery (Premium), så du kan bevare, indsamle, gennemgå og eksportere indhold fra Microsoft Teams. Målet med denne artikel er at hjælpe dig med at optimere din eDiscovery-arbejdsgang for indhold i Teams.

Der er fem kategorier af indhold i Teams, som du kan indsamle og behandle ved hjælp af eDiscovery (Premium):

- **Teams 1:1-chatsamtaler**. Chatmeddelelser, indlæg og vedhæftede filer, der deles i en Teams-samtale mellem to personer.  Teams 1:1-chatsamtaler kaldes også for *samtaler*.

- **Teams: Gruppechat**. Chatmeddelelser, indlæg og vedhæftede filer, der deles i en Teams-samtale mellem tre eller flere personer. Kaldes også for *1:N* chatsamtaler eller *gruppesamtaler*.

- **Teams-kanaler**. Chatmeddelelser, indlæg, svar og vedhæftede filer, der deles i en standardkanal i Teams.

- **Private kanaler**. Meddelelsesindlæg, svar og vedhæftede filer, der deles i en privat kanal i Teams.

- **Delte kanaler**. Meddelelsesindlæg, svar og vedhæftede filer, der deles i en delt kanal i Teams.

## <a name="where-teams-content-is-stored"></a>Hvor Teams-indholdet er gemt

En forudsætning for at kunne administrere Teams-indhold i eDiscovery (Premium) er at forstå den type Teams-indhold, som du kan indsamle, behandle og gennemgå i eDiscovery (Premium), og hvor dette indhold er gemt i Microsoft 365. I følgende tabel er der en liste over indholdstyper i Teams, og hvor de hver især er gemt.

|&nbsp;|Placering af chatbeskeder og indlæg|Placering af filer og vedhæftede filer|
|---|---|---|
|Teams 1:1-chatsamtaler|Meddelelser i 1:1-chatsamtaler gemmes i Exchange Online-postkassen for alle chatdeltagere.|Filer, der deles i en 1:1-chatsamtaler, gemmes på OneDrive for Business-kontoen for personen, der delte filen.|
|Teams: Gruppechats|Meddelelser i gruppechats gemmes i Exchange Online-postkassen for alle chatdeltagere.|Filer, der deles i gruppechats, gemmes på OneDrive for Business-kontoen for personen, der delte filen.|
|Teams-kanaler|Alle kanalbeskeder og -indlæg gemmes i den Exchange Online-postkasse, der er knyttet til teamet.|Filer, der deles i en kanal, gemmes på det SharePoint Online-websted, der er knyttet til teamet.|
|Private kanaler|Meddelelser, der sendes i en privat kanal, gemmes i Exchange Online-postkasserne hos alle medlemmer af den private kanal.|Filer, der deles i en privat kanal, gemmes i et dedikeret SharePoint Online-websted, der er tilknyttet den private kanal.|
|Delte kanaler|Meddelelser, der sendes i en delt kanal, gemmes i en systempostkasse, der er tilknyttet den delte kanal. <sup>1</sup>|Filer, der deles i en delt kanal, gemmes i et dedikeret SharePoint Online-websted, der er tilknyttet den delte kanal.|

> [!NOTE]
> <sup>1</sup> Hvis du vil søge efter (og bevare) meddelelser, der er sendt i en delt kanal, skal du søge i eller angive Exchange Online-postkassen for det overordnede team.

## <a name="create-a-case-for-teams-content"></a>Opret en sag for Teams-indhold

Det første skridt til at administrere Teams-indhold i eDiscovery (Premium) er at oprette en sag ved hjælp af det nye sagsformat, der er optimeret til at administrere Teams-indhold. Her er fordelene ved at bruge det nye sagsformat til Teams-indhold:

- Understøttelse af samtaletråde, hvor yderligere meddelelser i den samme samtale, der indeholder svarelementer, indsamles automatisk og tilføjes til valideringssæt.

- Chatsamtaler i Teams føjes automatisk til valideringssæt som en HTML-afskriftsfil. Vedhæftede filer i skyen, der deles i samtaler, føjes også til valideringssættet. Dette er med til at give kontekst til samtaler med svarelementer og reducere det samlede antal elementer, der produceres af chatbaseret indhold.

- Datasæt på op til 1 TB kan tilføjes til valideringssæt, så du kan samle og indsamle store mængder Teams-indhold i en sag.

Du kan finde flere oplysninger om de øgede sagsgrænser under [Brug det nye sagsformat i eDiscovery (Premium)](advanced-ediscovery-new-case-format.md).

Sådan opretter du en sag:

1. Gå til <https://compliance.microsoft.com>, og log på.

2. Klik på **eDiscovery > Avanceret** i venstre navigationsrude på Microsoft Purview-overholdelsesportalen.

3. Klik på fanen **Sager** på siden **eDiscovery (Premium)** og klik derefter på **Opret en sag**.

   Pop op-vinduet **Ny eDiscovery-sag** vises. Afsnittet **Sagsformat** giver mulighed for at oprette en sag ved hjælp af det nye sagsformat.

   ![Indstillingen Store bogstaver på siden Ny eDiscovery-sag.](..\media\AeDNewCaseFormat1.png)

4. Når du har navngivet sagen, skal du vælge indstillingen **Ny** og derefter klikke på **Gem** for at oprette sagen.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Tilføj datakilder for ansvarlige i Teams, og bevar Teams-indhold  

Det næste trin er at identificere de brugere, der er dataansvarlige i din undersøgelse, og tilføje dem og deres indholdssteder som ansvarlige til den sag, du oprettede i det foregående afsnit. Når du tilføjer ansvarlige, kan du angive deres postkasse og OneDrive-konto som datakilder for ansvarlige. Du kan også angive placeringer af Teams-indhold som datakilder for ansvarlige for hurtigt at placere disse placeringer i juridisk fastfrysning for at bevare indhold under din undersøgelse. Det gør det også nemt at indsamle indhold og føje det til et valideringssæt.

Sådan føjer du ansvarlige til en sag og bevarer datakilder med ansvarlige:

1. Gå til den eDiscovery-sag (Premium), du oprettede i forrige afsnit, og klik derefter på **Datakilder**.

2. På siden **Datakilder** skal du klikke på **Tilføj datakilde** > **Tilføj nye ansvarlige**.

3. I guiden **Ny ansvarlig** skal du føje en eller flere brugere som ansvarlige til sagen ved at skrive den første del af brugerens navn eller alias. Når du har fundet den rigtige person, skal du vælge personens navn for at føje vedkommende til listen.  

4. Du kan udvide hver dataansvarlig, så vedkommende kan få vist de primære datakilder, der automatisk er blevet knyttet til den pågældende dataansvarlige, og for at vælge andre steder, der skal tilknyttes den pågældende dataansvarlige.

   ![Datakilder for dataansvarlig.](..\media\TeamsCustodialDataLocations1.png)

5. Følg disse retningslinjer for at tilføje datakilder med ansvarlige for Teams-indhold. Klik på **Rediger** for at tilføje en dataplacering.

   - **Postkasser**. Den ansvarliges postkasse er valgt som standard. Hold dette markeret for at tilføje (og bevare) 1:1-chatsamtaler, gruppechats og private kanalchats som data til ansvarlige.

   - **OneDrives**. Den ansvarliges OneDrive-konto er valgt som standard. Hold dette markeret for at tilføje (og bevare) filer, der deles i 1:1-chatsamtaler, gruppechats som data til ansvarlige.

   - **SharePoint**. Tilføj det SharePoint-websted, der er knyttet til en privat eller delt kanal, som den ansvarlige er medlem af, for at tilføje (og bevare) de filer, der deles i en kanal, som data til ansvarlige. Klik på **Rediger**, og tilføj derefter URL-adressen for det SharePoint-websted, der er knyttet til en privat eller delt kanal. Du kan få mere at vide om, hvordan du finder de private og delte kanaler, som en bruger er medlem af, i [eDiscovery for private og delte kanaler](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

   - **Teams**. Tilføj de teams, som den ansvarlige er medlem af, for at tilføje (og bevare) alle kanalmeddelelser og alle filer, der deles med en Teams-kanal, som data til ansvarlige. Dette omfatter tilføjelse af postkassen for en delt kanals overordnede team, som den ansvarlige er medlem af. Når du klikker på **Rediger**, vises den postkasse og det websted, der er knyttet til hvert team, som den ansvarlige er medlem af, på en liste. Vælg de teams, du vil knytte til den ansvarlige. Du skal vælge både den tilsvarende postkasse og det tilhørende websted for hvert team.

   > [!NOTE]
   > Du kan også tilføje postkassen og webstedet for Teams, som ansvarlige ikke er medlemmer af, som en placering med opbevaringsdata. Det gør du ved at klikke på **Rediger** ud for **Exchange** og **SharePoint** og derefter tilføje den postkasse og det websted, der er knyttet til teamet.

6. Når du har tilføjet ansvarlige og konfigureret datakilder med ansvarlige, skal du klikke på **Næste** for at få vist siden **Indstillinger for venteposition**.

   Der vises en liste over de ansvarlige, og afkrydsningsfeltet i kolonnen **Fastfrysning** er markeret som standard. Dette indikerer, at der placeres en fastfrysning på de datakilder, du har knyttet til hver ansvarlig. Lad disse afkrydsningsfelter være markeret for at bevare disse data.

7. På siden **Indstillinger for fastfrysning** skal du klikke på **Næste** for at gennemgå indstillingerne for de ansvarlige. Klik på **Indsend** for at føje de ansvarlige til sagen.

Du kan finde flere oplysninger om at tilføje og bevare datakilder i en eDiscovery-sag (Premium) under:

- [Føj ansvarlige til en eDiscovery-sag (Premium)](add-custodians-to-case.md)

- [Føj kilder til ikke-datakilder med ansvarlige til en eDiscovery-sag (Premium)](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Teams-indhold skal indsamles og føjes til valideringssættet

Når du har føjet ansvarlige til sagen og bevaret indhold i datakilder for ansvarlige, er næste trin i arbejdsprocessen at søge efter Teams-indhold, der er relevant for din undersøgelse, og føje det til et valideringssæt med henblik på yderligere gennemgang og analyse. Selvom det er typisk at indsamle Teams-indhold sammen med indhold fra andre Microsoft 365 tjenester, f.eks. mail i Exchange og dokumenter i SharePoint, fokuserer dette afsnit specifikt på at indsamle Teams-indhold i et datasæt. Du kan oprette yderligere datasæt, der indsamler indhold, der ikke er fra Teams, og som skal føjes til et valideringssæt.

Når du indsamler Teams-indhold til en sag, er der to trin i arbejdsprocessen:

1. **Opret et kladde-datasæt**.  Det første trin er at oprette et *kladde-datasæt*, som er et estimat over de elementer, der matcher dine søgekriterier. Du kan få vist oplysninger om de resultater, der matcher søgeforespørgslen, f.eks. det samlede antal og størrelsen af fundne elementer, de forskellige datakilder, hvor de blev fundet, og statistik om søgeforespørgslen. Du kan også få vist et eksempel på elementer, der blev returneret af datasættet. Ved hjælp af disse statistikker kan du ændre søgeforespørgslen og køre kladde-datasættet så mange gange, som det er nødvendigt for at indsnævre resultaterne, indtil du er tilfreds med, at du indsamler det indhold, der er relevant for din sag.

2. **Bekræft et kladde-datasæt, som du kan bruge som et valideringssæt**. Når du er tilfreds med et kladde-datasæts resultater, kan du sende datasættet til et valideringssæt. Når du bekræfter et kladde-datasæt, føjes de elementer, der returneres af datasættet, til et valideringssæt til gennemsyn, analyse og eksport.

Du har også mulighed for ikke at køre et kladde-datasæt og føje datasættets resultater direkte til et valideringssæt, når du opretter og kører datasættet.

Sådan opretter du et datasæt fra Teams-indhold:

1. Gå til den eDiscovery-sag (Premium), du tilføjede til de ansvarlige i forrige afsnit, og klik derefter på **Datasæt**.

2. På siden **Datasæt** skal du vælge **Nyt datasæt** > **Standard datasæt**.

3. Skriv et navn (påkrævet) og en beskrivelse (valgfrit) for datasættet.

4. På siden **Datakilder med ansvarlige** skal du klikke på **Vælg ansvarlige** for at vælge de ansvarlige, du har føjet til sagen.

   Listen over de ansvarlige for sagen vises på pop op-siden **Vælg ansvarlige**.

5. Vælg én eller flere ansvarlige, og klik derefter på **Tilføj**.

   Når du har tilføjet specifikke ansvarlige til datasættet, vises en liste over specifikke datakilder for hver enkelt ansvarlige. Det er de datakilder, som du konfigurerede, da du føjede den ansvarlige til sagen. Alle datakilder for ansvarlige er valgt som standard. Dette omfatter alle Teams eller kanaler, som du har knyttet til en ansvarlig.

   Vi anbefaler, at du gør følgende, når du indsamler indhold fra Teams:

   - Fjern de ansvarliges OneDrive-konti fra datasættets område (ved at fjerne markeringen i afkrydsningsfeltet i den **ansvarliges OneDrive-**-kolonne for hver ansvarlig). Dette forhindrer indsamling af dublerede filer, der var vedhæftet 1:1-chatsamtaler og gruppechats. Vedhæftede filer i skyen indsamles automatisk fra hver samtale, der findes i datasættet, når du sender kladde-datasættet til valideringssættet. Ved at bruge denne metode (i stedet for at søge efter OneDrive-konti som en del af datasættet) grupperes filer, der er knyttet til 1:1-chatsamtaler og gruppechats, i den samtale, de blev delt i.

   - Fjern markeringen i afkrydsningsfeltet i kolonnen **Ekstra websted** for at fjerne de SharePoint-websteder, der indeholder filer, der er delt i private eller delte kanaler. Dette eliminerer indsamling af dublerede filer, der blev vedhæftet private eller delte kanalers samtaler, fordi disse vedhæftede filer i skyen automatisk føjes til valideringssættet, når du bekræfter kladde-datasættet og grupperer dem i de samtaler, de blev delt i.

6. Hvis du tidligere har fulgt trinnene til at tilføje Teams-indhold som datakilder for ansvarlige, kan du springe dette trin over og vælge **Næste**. Ellers kan du på siden med guiden **ikke-datakilder med ansvarlige** vælge datakilder, der indeholder Teams-indhold, som du måske har føjet til sagen for at søge i datasættet.

7. Hvis du tidligere har fulgt trinnene til at tilføje Teams-indhold som datakilder for ansvarlige, kan du springe dette trin over og vælge **Næste**. Ellers kan du på siden med guiden **Flere placeringer** tilføje andre datakilder for at søge i datasættet. Du kan f.eks. føje postkassen og webstedet til et team, der ikke blev tilføjet som en datakilde med eller uden ansvarlige. Ellers skal du vælge **Næste** og springe dette trin over.

8. På siden med guiden **Betingelser** skal du konfigurere søgeforespørgslen til at indsamle Teams-indhold fra de datakilder, du har angivet på de forrige sider i guiden. Du kan bruge forskellige nøgleord og søgebetingelser til at begrænse omfanget af indsamlingen. Du kan finde flere oplysninger under [Opret søgeforespørgsler for datasæt](building-search-queries.md).

   For at hjælpe med at sikre det mest omfattende datasæt af Teams-chatsamtaler (herunder 1:1, gruppe- og kanalchats) skal du bruge betingelsen **Type** og vælge indstillingen **Instant-meddelelser**. Vi anbefaler også, at du inkluderer et datointerval eller flere nøgleord for at begrænse omfanget af datasættet til elementer, der er relevante for din undersøgelse. Her er et skærmbillede af et eksempel på en forespørgsel, der bruger **Type** og **Dato**-indstillingerne:

   ![Forespørgsel til indsamling af Teams-indhold.](..\media\TeamsConditionsQueryType.png)

9. Gør et af følgende på siden med vejledningen **Gem kladde eller foretag indsamling**, afhængigt af om du vil oprette et kladde-datasæt eller sende datasættet til et valideringssæt.

   ![Gem datasættet, eller bekræft valideringssæt.](..\media\TeamsDraftCommitCollection.png)

   1. **Gem samling som kladde**. Vælg denne indstilling for at oprette en kladde-datasæt. Som tidligere forklaret føjer et kladde-datasæt ikke datasætsresultaterne til et valideringssæt. Det returnerer et estimat af de søgeresultater, der svarer til søgeforespørgslen for datakilderne i datasætsområdet. Dette giver dig mulighed for at få vist [datasætstatistik og -rapporter[(collection-statistics-reports.md)] og redigere og køre kladde-datasættet igen. Når du er tilfreds med kladde-datasættets resultat, kan du sende datasættet til et valideringssæt. Få mere at vide under [Opret et kladde-datasæt](create-draft-collection.md).

   2. **Indsaml elementer, og føj til et valideringssæt**. Vælg denne indstilling for at køre datasættet og derefter føje resultaterne til et valideringssæt. Du kan føje datasættet til et nyt eller eksisterende valideringssæt. Indstillingerne til at indsamle kontekstafhængige Teams-samtalemeddelelser (også kaldet *samtaletrådning*) og indsamle vedhæftede filer i skyen er valgt som standard og kan ikke fravælges. Disse indstillinger anvendes automatisk på grund af det nye sagsformat, du brugte, da du oprindeligt oprettede sagen for Teams-indhold. Du kan få mere at vide om at bekræfte datasæt til et valideringssæt under [Bekræft et kladde-datasæt, som du kan bruge som et valideringssæt](commit-draft-collection.md).

10. Når du er færdig med at konfigurere datasættet, skal du sende datasættet for at oprette en kladde-datasæt eller indsamle elementer og føje dem til et valideringssæt.

   Når processen med at føje datasættet til valideringssættet er fuldført, er statusværdien for datasættet under fanen **Datasæt** angivet til **Bekræftet**.

## <a name="review-teams-content-in-a-review-set"></a>Gennemse Teams-indhold i et valideringssæt

Når du har føjet datasæt af Teams-indhold til et valideringssæt, er det næste trin at gennemgå indholdet for dets relevans for din undersøgelse og om nødvendigt frasortere det. En vigtig forudsætning for at gennemgå Teams-indhold er at forstå, hvordan eDiscovery (Premium) behandler Teams-chatsamtaler og vedhæftede filer, når du føjer dem til et valideringssæt. Denne behandling af Teams-indhold resulterer i følgende tre ting:

- **[Gruppering](#grouping)**. Sådan grupperes og præsenteres meddelelser, indlæg og svar i Teams-samtaler i valideringssættet. Dette omfatter også vedhæftede filer i chatsamtaler, der udtrækkes og grupperes i samtalen.

- **[Afskrift af samtaletrådning](#transcript-conversation-threading)**. Hvordan eDiscovery (Premium) fastslår, hvilket yderligere indhold fra en samtale, der skal indsamles, for at give kontekst omkring elementer, der matcher indsamlingskriterierne.

- **[Deduplikering](#deduplication-of-teams-content)**. Sådan håndterer eDiscovery (Premium) duplikeret Teams-indhold.

- **[Metadata](#metadata-for-teams-content)**. Metadataegenskaber, som eDiscovery (Premium) føjer til Teams-indhold, når det er indsamlet og føjet til et valideringssæt.

Gruppering, konversationstråde, deduplikation og Teams-metadata hjælper dig med at optimere gennemgangen og analysen af Teams-indhold. Dette afsnit indeholder også [tips til visning af Teams-indhold i et valideringssæt](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Gruppering

Når indhold fra Teams-chatsamtaler føjes til et valideringssæt, samles meddelelser, indlæg og svar fra samtaler i HTML-afskriftsfiler. En enkelt chatsamtale kan have flere afskriftsfiler. En vigtig funktion i disse afskriftsfiler er at præsentere Teams-indhold som kontinuerlige samtaler og ikke som individuelle (eller separate) meddelelser. Dette hjælper med at give kontekst til elementer, der matchede søgekriterierne for dine datasæt i det forrige trin, og reducerer antallet af elementer, der indsamles i valideringssættet. Afskrifter og tilknyttede elementer kan grupperes efter enten *familie* eller *samtale*. Elementer i den samme familie har den samme værdi for egenskaben **FamilyId**-metadata. Elementer i den samme samtale har den samme værdi for egenskaben **ConversationId**-metadata.

I følgende tabel beskrives det, hvordan de forskellige typer af Teams-chatindhold grupperes efter familie og samtale.

|Teams-indholdstype|Gruppér efter familie|Gruppér efter samtale|
|---|---|---|
|1:1-chatsamtaler og gruppechats i Teams |En afskrift og alle dens vedhæftede filer og udtrukne elementer deler det samme **FamilyId**. Hver afskrift har et entydigt **FamilyId**.|Alle afskriftsfiler og deres familieelementer i den samme samtale deler det samme **ConversationId**. Dette omfatter følgende elementer: <ul><li>Alle udtrukne elementer og vedhæftede filer i alle afskrifter, der deler det samme **ConversationId**.</li><li>Alle afskrifter for den samme chatsamtale</li><li>Alle kopier af hver afskrift</li><li>Afskrifter fra efterfølgende indsamlinger fra den samme chatsamtale</li></ul> <br/> For Teams 1:1- og gruppechatsamtaler kan du have flere afskriftsfiler, der hver især svarer til en anden tidsramme i samtalen. Da disse afskriftsfiler stammer fra den samme samtale med de samme deltagere, deler de det samme **ConversationId**.|
|Standard-, private og delte kanalchats|Hvert indlæg og alle svar og vedhæftede filer gemmes i sin egen afskrift. Denne afskrift og alle dens vedhæftede filer og udtrukne elementer deler det samme **FamilyId**.|Hvert indlæg og dets vedhæftede filer og udtrukne elementer har et entydigt **ConversationId**. Hvis der er efterfølgende indsamlinger eller nye svar fra det samme indlæg, har de delta-afskrifter, der stammer fra disse samlinger, også det samme **ConversationId**.|

Brug kontrolelementet **Gruppe** på kommandolinjen i et valideringssæt til at få vist Teams-indhold grupperet efter familie eller samtale.

![Gruppekontrolelement på kommandolinjen.](..\media\TeamsGroupControl.png)

- Vælg **Gruppér familievedhæftninger** for at få vist Teams-indhold grupperet efter familie. Hver afskriftsfil vises på en linje på listen over elementer i valideringssættet. Vedhæftede filer er indlejret under elementet.

- Vælg **Gruppér Teams- eller Yammer-samtaler** for at få vist Teams-indhold grupperet efter samtale. Hver samtale vises på en linje på listen over elementer i valideringssættet. Afskriftsfiler og vedhæftede filer indlejres under samtalen på øverste niveau.

> [!NOTE]
> Vedhæftede filer i skyen grupperes med de samtaler, de vises i. Denne gruppering opnås ved at tildele det samme **FamilyId** som afskriftsfilen for den meddelelse, filen blev vedhæftet, og det samme **ConversationId** som den samtale, meddelelsen blev vist i. Det betyder, at flere kopier af vedhæftede filer i skyen kan føjes til valideringssættet, hvis de er knyttet til forskellige samtaler.

#### <a name="viewing-transcript-files-for-conversations"></a>Visning af afskriftsfiler til samtaler

Når du får vist afskriftsfiler i et valideringssæt, fremhæves nogle af meddelelserne med lilla. De meddelelser, der er fremhævet, afhænger af, hvilken kopi af afskriften du får vist. I en 1:1-chatsamtaler mellem User4 og User2 fremhæves de meddelelser, der er slået op af User4, f.eks. med lilla, når du får vist afskriften, der er indsamlet fra User4s postkasse. Når du får vist User2's afskrift af den samme samtale, fremhæves meddelelser, der er slået op af User2, med lilla. Denne fremhævningsfunktion er baseret på den samme Teams-klientoplevelse, hvor en brugers indlæg fremhæves med lilla i Teams-klienten.

Følgende skærmbilleder viser et eksempel på en samtale i Teams-klienten og afskriftsfilen for den samme samtale i valideringssættet. Den lilla fremhævning i afskriftsfilen angiver, at afskriften blev indsamlet fra User2's postkasse.

##### <a name="conversation-in-teams-client"></a>Samtale i Teams-klient

![Samtale, der vises i afskriftsfilen i valideringssættet.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Samtale i afskriftsfilen

![Samme samtale, der vises i Teams-klienten.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Afskrift af samtaletrådning

Funktionen til trådning af samtaler i det nye sagsformat i eDiscovery (Premium) hjælper dig med at identificere kontekstafhængigt indhold, der er relateret til elementer, der kan være relevant for din undersøgelse. Denne funktion producerer særskilte samtalevisninger, der omfatter chatmeddelelser, der står foran og følger efter elementerne, der matcher søgeforespørgslen under indsamlingen. Denne funktion giver dig mulighed for effektivt og hurtigt at gennemse komplette chatsamtaler (kaldet *trådede samtaler*) i Microsoft Teams. Som tidligere forklaret rekonstrueres chatsamtaler i HTML-afskriftsfiler, når eDiscovery (Premium) føjer Teams-indhold til et gennemgangssæt.

Følgende logik anvendes af eDiscovery (Premium) til at inkludere yderligere meddelelser og afskriftfiler over svar, der giver kontekst til de elementer, der matcher den indsamlingsforespørgsel (kaldet *responsive elementer*), som du brugte, da du indsamlede Teams-indhold. Forskellige fremgangsmåder for trådning er baseret på typerne af chats og den søgeforespørgsel, der bruges til at indsamle de responsive elementer. Der er to almindelige indsamlingsscenarier:

- Forespørgsler, der bruger søgeparametre, f.eks. nøgleord og egenskab: værdi-par

- Forespørgsler, der kun bruger datointervaller

|Teams-indholdstype|Forespørgsler med søgeparametre|Forespørgsler med datointervaller|
|---|---|---|
|1:1-chatsamtaler og gruppechats i Teams |Meddelelser, der blev sendt 12 timer før og 12 timer efter responsive emner, grupperes sammen med det responsive emne i en enkelt afskriftsfil.|Meddelelser i et 24-timers vindue er grupperet i en enkelt afskriftsfil.|
|Standard-, private og delte Teams-kanalchats|Hvert indlæg, der indeholder dynamiske elementer og alle tilsvarende svar, er grupperet i en enkelt afskriftsfil.|Hvert indlæg, der indeholder dynamiske elementer og alle tilsvarende svar, er grupperet i en enkelt afskriftsfil.|

### <a name="deduplication-of-teams-content"></a>Deduplikering af Teams-indhold

På følgende liste beskrives funktionsmåden for deduplikering (og duplikering), når du indsamler Teams-indhold i et valideringssæt.

- Hver afskriftsfil, der føjes til et valideringssæt, skal være en en-til-en-tilknytning til indhold, der er gemt på dataplaceringer. Det betyder, at eDiscovery (Premium) ikke indsamler noget Teams-indhold, der allerede er føjet til valideringssættet. Hvis en chatmeddelelse allerede er indsamlet i et valideringssæt, tilføjer eDiscovery (Premium) ikke den samme meddelelse fra den samme dataplacering til valideringssættet i efterfølgende indsamlinger.

- For 1:1- og gruppechats gemmes kopier af meddelelser i postkassen for hver samtaledeltager. Kopier af den samme samtale, der findes i forskellige deltageres postkasser, indsamles med forskellige metadata. Derfor behandles hver forekomst af samtalen som entydig og føres ind i valideringssættet i separate afskriftsfiler. Så hvis alle deltagere i en 1:1- eller gruppechat tilføjes som ansvarlige i en sag og er inkluderet i omfanget af et datasæt, føjes kopier af hver afskrift (for den samme bevarelse) til valideringssættet og grupperes sammen med det samme **ConversationId**. Hver af disse kopier er knyttet til en tilsvarende ansvarlig. **Tip**: Kolonnen **Ansvarlig** på listen over valideringssæt identificerer den ansvarlige for den tilsvarende afskriftsfil.

- I efterfølgende samlinger af elementer fra den samme samtale føjes kun det deltaindhold, der ikke tidligere blev indsamlet, til valideringssættet og grupperes (ved at dele det samme **ConversationId**) med de tidligere indsamlede afskrifter fra den samme samtale. Her er et eksempel på denne adfærd:

   1. Indsamling A indsamler meddelelser i en samtale mellem User1 og User2 og føjer dem til valideringssættet.

   2. Indsamling B indsamler meddelelser fra den samme samtale, men der er nye meddelelser mellem User1 og User2, siden samling A blev kørt.

   3. Kun de nye meddelelser i indsamling B føjes til valideringssættet. Disse meddelelser føjes til en separat afskriftsfil, men den nye afskrift er grupperet med afskrifterne fra Indsamling A med det samme **ConversationId**.

   Denne funktionsmåde gælder for alle typer Teams-chats.

### <a name="metadata-for-teams-content"></a>Metadata for Teams-indhold

I store valideringssæt med tusindvis eller millioner af elementer kan det være svært at begrænse omfanget af din anmeldelse til Teams-indhold. For at hjælpe dig med at fokusere din gennemgang på Teams-indhold er der metadataegenskaber, der er specifikke for Teams-indhold. Du kan bruge disse egenskaber til at organisere kolonnerne på gennemgangslisten og [konfigurere filtre og forespørgsler](review-set-search.md) for at optimere gennemgangen af Teams-indhold. Disse metadataegenskaber er også inkluderet, når du eksporterer Teams-indhold fra eDiscovery (Premium). Det hjælper dig med at organisere og få vist indhold efter eksport eller i eDiscovery-værktøjer fra tredjepart.

I følgende tabel beskrives metadataegenskaber for Teams-indhold.

|Metadataegenskab|Beskrivelse|
|---|---|
|ContainsEditedMessage|Angiver, om en afskriftsfil indeholder en redigeret meddelelse. Redigerede meddelelser identificeres, når afskriftsfilen vises.|
|ConversationId|Et GUID, der identificerer den samtale, som elementet er knyttet til. Afskriftsfiler og vedhæftede filer fra den samme samtale har samme værdi for denne egenskab.|
|Samtalenavn|Navnet på den samtale, som afskriftsfilen eller den vedhæftede fil er knyttet til. For Teams 1:1- og gruppechats er værdien af denne egenskab UPN for alle deltagere i samtalen sammenkædet. Det kunne f.eks. være `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams-kanalchats (standard, private og delte) bruger følgende format til samtalenavn: `<Team name>,<Channel name>`. Det kunne f.eks. være `eDiscovery vNext, General`.|
|Samtaletype|Angiver typen af teamchat. For Teams 1:1- og gruppechats er værdien for denne egenskab `Group`. For standard-, private og delte kanalchats er værdien `Channel`|
|Dato|Tidsstemplet for den første meddelelse i afskriftsfilen.|
|FamilyId|Et GUID, der identificerer transskriptionsfilen for en chatsamtale. Vedhæftede filer har samme værdi for denne egenskab som den afskriftsfil, der indeholder den meddelelse, som filen blev vedhæftet.|
|FileClass|Angiver denne type indhold. Elementer fra Teams-chatsamtaler har værdien `Conversation`. Exchange-mails meddelelser har derimod værdien `Email`.|
|MessageKind|Meddelelsestypeegenskaben. Teams-indhold har værdien `microsoftteams , im`.|
|Modtagere|En liste over alle brugere, der har modtaget en meddelelse i afskriftssamtalen.|
|TeamsChannelName|Afskriftens Teams-kanalnavn.|

Du kan finde beskrivelser af andre egenskaber for eDiscovery-metadata (Premium) i [Dokumentmetadatafelter i eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="export-teams-content"></a>Eksportér Teams-indhold

Når du har gennemset og frasorteret Teams-indhold i et valideringssæt, kan du eksportere de afskriftsfiler, der indeholder indhold, der svarer til din undersøgelse. Der er ikke nogen specifikke eksportindstillinger for Teams-indhold. Hver afskriftsfil eksporteres som en HTML-meddelelsesfil. Denne fil indeholder også skjulte CDATA-koder med alle metadata for de enkelte chatmeddelelser. De metadataegenskaber, der er beskrevet i forrige afsnit, medtages, når Teams-indhold eksporteres.  

Der refereres til hver afskriftsfil i indlæsningsfilen, og den kan findes ved hjælp af den relative sti i feltet Export_native_path i indlæsningsfilen. Afskriftsfiler er placeret i mappen Samtaler i rodeksportmappen.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Tip til visning af Teams-indhold i et valideringssæt

Her er nogle tip og bedste fremgangsmåder til visning af Teams-indhold i et gennemgangssæt.

- Brug kontrolelementet **Tilpas kolonner** på kommandolinjen til at tilføje og organisere kolonner for at optimere gennemgangen af Teams-indhold.

  ![Brug pop op-siden Rediger kolonne til at tilføje, fjerne og organisere kolonner.](..\media\EditReviewSetColumns.png)

   Du kan tilføje og fjerne kolonner, der er nyttige for Teams-indhold. Du kan også sortere rækkefølgen af kolonner ved at trække og slippe dem på pop op-siden **Rediger kolonne**. Du kan også sortere efter kolonner for at gruppere Teams-indhold med lignende værdier for den kolonne, du sorterer efter.

- Nyttige kolonner, der kan hjælpe dig med at gennemse Teams-indhold, omfatter **Ansvarlige**, **Modtagere** og **Filtype** eller **Meddelelsestype**.

- Brug [filtre](review-set-search.md) til Teams-relaterede egenskaber til hurtigt at få vist Teams-indhold. Der er filtre for de fleste af de metadataegenskaber, der er beskrevet i forrige afsnit.

## <a name="deleting-teams-chat-messages"></a>Sådan sletter du chatmeddelelser i Teams

Du kan bruge eDiscovery (Premium) og Microsoft Graph Explorer til at reagere på datalækager, når indhold, der indeholder fortrolige eller skadelige oplysninger, frigives via Teams-chatmeddelelser. Administratorer i din organisation kan søge efter og slette chatmeddelelser i Microsoft Teams. Dette kan hjælpe dig med at fjerne følsomme oplysninger eller upassende indhold i Teams-chatmeddelelser. Du kan finde flere oplysninger under [Søg efter og fjern chatmeddelelser i Teams](search-and-delete-Teams-chat-messages.md).

## <a name="reference-guide"></a>Referencevejledning

Her er en hurtig referencevejledning til brug af eDiscovery (Premium) til Microsoft Teams. Denne vejledning opsummerer nøglepunkterne for brug af eDiscovery (Premium), så du kan bevare, indsamle, gennemse og eksportere indhold fra Microsoft Teams.

![Miniaturebillede af referencevejledning til brug af eDiscovery (Premium) for Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Download som en PDF-fil](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
