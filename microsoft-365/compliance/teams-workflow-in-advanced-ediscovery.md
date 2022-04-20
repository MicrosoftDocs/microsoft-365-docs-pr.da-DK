---
title: Teams arbejdsproces i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.openlocfilehash: 4dc516037e1ccad41c7ed93f280d698ca6bd164c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991902"
---
# <a name="ediscovery-premium-workflow-for-content-in-microsoft-teams"></a>eDiscovery-arbejdsproces (Premium) for indhold i Microsoft Teams

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denne artikel indeholder et omfattende sæt procedurer, retningslinjer og bedste praksis for brug af Microsoft Purview eDiscovery (Premium) til at bevare, indsamle, gennemse og eksportere indhold fra Microsoft Teams. Målet med denne artikel er at hjælpe dig med at optimere din eDiscovery-arbejdsproces til Teams indhold.

Der er fem kategorier af Teams indhold, som du kan indsamle og behandle ved hjælp af eDiscovery (Premium):

- **Teams 13:1 chats**. Chatbeskeder, indlæg og vedhæftede filer, der deles i en Teams samtale mellem to personer.  Teams 1:1 kaldes også *samtaler*.

- **Teams gruppechats**. Chatbeskeder, indlæg og vedhæftede filer, der deles i en Teams samtale mellem tre eller flere personer. Kaldes også *1:N-chats* eller *gruppesamtaler*.

- **Teams kanaler**. Chatbeskeder, indlæg, svar og vedhæftede filer, der deles i en standardkanal Teams.

- **Private kanaler**. Meddelelsesindlæg, svar og vedhæftede filer, der deles i en privat Teams kanal.

- **Delte kanaler**. Meddelelsesindlæg, svar og vedhæftede filer, der deles i en delt Teams kanal.

## <a name="where-teams-content-is-stored"></a>Hvor Teams indhold gemmes

En forudsætning for at administrere Teams indhold i eDiscovery (Premium) er at forstå, hvilken type Teams indhold du kan indsamle, behandle og gennemse i eDiscovery (Premium), og hvor indholdet er gemt i Microsoft 365. I følgende tabel vises Teams indholdstype, og hvor hver enkelt er gemt.

|&nbsp;|Placering af chatbeskeder og -indlæg|Placering af filer og vedhæftede filer|
|---|---|---|
|Teams 1:1 chats|Meddelelser i 1:1 chats gemmes i Exchange Online-postkassen for alle chatdeltagere.|Filer, der deles i en 1:1-chat, gemmes på den OneDrive for Business konto for den person, der har delt filen.|
|Teams gruppechats|Meddelelser i gruppechat gemmes i Exchange Online-postkassen for alle chatdeltagere.|Filer, der deles i gruppechats, gemmes på den OneDrive for Business konto for den person, der har delt filen.|
|Teams kanaler|Alle kanalmeddelelser og -indlæg gemmes i den Exchange Online-postkasse, der er knyttet til teamet.|Filer, der deles i en kanal, gemmes på det SharePoint Online-websted, der er knyttet til teamet.|
|Private kanaler|Meddelelser, der sendes i en privat kanal, gemmes i Exchange Online-postkasser for alle medlemmer af den private kanal.|Filer, der deles i en privat kanal, gemmes på et dedikeret SharePoint Online-websted, der er knyttet til den private kanal.|
|Delte kanaler|Meddelelser, der sendes i en delt kanal, gemmes i en systempostkasse, der er knyttet til den delte kanal. <sup>1</sup>|Filer, der deles i en delt kanal, gemmes på et dedikeret SharePoint Online-websted, der er knyttet til den delte kanal.|

> [!NOTE]
> <sup>1</sup> Hvis du vil søge efter (og bevare) meddelelser, der sendes i en delt kanal, skal du søge efter eller angive Exchange Online-postkassen for det overordnede team.

## <a name="create-a-case-for-teams-content"></a>Opret en sag for Teams indhold

Det første trin til administration af Teams indhold i eDiscovery (Premium) er at oprette en sag ved hjælp af det nye sagsformat, der er optimeret til administration af Teams indhold. Her er fordelene ved at bruge det nye sagsformat til Teams indhold:

- Understøttelse af samtaletrådning, hvor yderligere meddelelser i den samme samtale, der omfatter dynamiske elementer, automatisk indsamles og føjes til korrektursæt.

- Teams chatsamtaler føjes automatisk til korrektursæt som en HTML-transskriptionsfil. Vedhæftede filer i skyen, der deles i samtaler, føjes også til korrektursættet. Dette hjælper med at give kontekst til samtalerne med dynamiske elementer og reducere det samlede antal elementer, der produceres af chatbaseret indhold.

- Samlinger på op til 1 TB kan føjes til korrektursæt, som giver dig mulighed for at indsamle og beløbe store mængder Teams indhold i en sag.

Du kan finde flere oplysninger om de øgede sagsgrænser under [Brug det nye sagsformat i eDiscovery (Premium)](advanced-ediscovery-new-case-format.md).

Sådan opretter du en sag:

1. Gå til , <https://compliance.microsoft.com> og log på.

2. Klik på **eDiscovery > Avanceret** i navigationsruden til venstre på Microsoft Purview-overholdelsesportalen.

3. Klik på fanen **Sager** på siden **eDiscovery (Premium),** og klik derefter på **Opret en sag**.

   Siden **Ny eDiscovery-sag** vises. I afsnittet **Sagsformat** kan du oprette en sag ved hjælp af det nye sagsformat.

   ![Indstillingen Store sager på siden Ny eDiscovery-sag.](..\media\AeDNewCaseFormat1.png)

4. Når du har navngivet sagen, skal du vælge indstillingen **Ny** og derefter klikke på **Gem** for at oprette sagen.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Tilføj Teams datakilder, og bevar Teams indhold  

Det næste trin er at identificere de brugere, der er datavogterne i din undersøgelse, og tilføje dem og deres indholdsplaceringer som tilsynsførende i den sag, du oprettede i det forrige afsnit. Når du tilføjer tilsynsførende, kan du angive deres postkasse og OneDrive konto som datakilder til varetægtsfængsling. Du kan også angive Teams indholdsplaceringer som tilsynsførende datakilder for hurtigt at placere disse placeringer i juridisk venteposition for at bevare indhold under din undersøgelse. Det gør det også nemt at indsamle indhold og føje det til et anmeldelsessæt.

Sådan føjer du tilsynsførende til en sag og bevarer datakilder med frihedsberøvelse:

1. Gå til den eDiscovery (Premium)-sag, du oprettede i forrige afsnit, og klik derefter på **Datakilder**.

2. På siden **Datakilder** skal du klikke på **Tilføj** **datakildeTilføj** >  nye tilsynsførende.

3. Føj en eller flere brugere til sagen i guiden **Ny tilsynsførende** ved at skrive den første del af brugerens navn eller alias. Når du har fundet den korrekte person, skal du vælge vedkommendes navn for at føje vedkommende til listen.  

4. Udvid hver tilsynsførende for at få vist de primære datakilder, der automatisk er knyttet til tilsynsførende, og for at vælge andre placeringer, der skal knyttes til tilsynsførende.

   ![Tilsynsførende datakilder.](..\media\TeamsCustodialDataLocations1.png)

5. Følg disse retningslinjer for at tilføje datakilder til frihedsberøvelse for Teams indhold. Klik på **Rediger** for at tilføje en dataplacering.

   - **Postkasser**. Forældremyndighedens postkasse er valgt som standard. Hold dette markeret for at tilføje (og bevare) 1:1 chats, gruppechats og private kanalchats som frihedsberøvende data.

   - **OneDrives**. Forældremyndighedens OneDrive konto er valgt som standard. Hold dette markeret for at tilføje (og bevare) filer, der deles i 1:1-chats og gruppechats som frihedsberøvende data.

   - **SharePoint**. Tilføj det SharePoint websted, der er knyttet til en privat eller delt kanal, som vogteren er medlem af for at tilføje (og bevare) som frihedsberøvende data, som filerne deles i en kanal. Klik på **Rediger**, og tilføj derefter URL-adressen for det SharePoint websted, der er knyttet til en privat eller delt kanal. Hvis du vil vide mere om, hvordan du finder de private og delte kanaler, som en bruger er medlem af, skal du se [eDiscovery af private og delte kanaler](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

   - **Teams**. Tilføj de teams, som vogteren er medlem af, for at tilføje (og bevare) som frihedsberøvende data for alle kanalmeddelelser og alle filer, der deles med en Teams kanal. Dette omfatter tilføjelse af postkassen for det overordnede team for en delt kanal, som vogteren er medlem af. Når du klikker på **Rediger**, vises den postkasse og det websted, der er knyttet til hvert team, som tilsynsførende er medlem af, på en liste. Vælg de teams, du vil knytte til tilsynsførende. Du skal vælge både den tilsvarende postkasse og det tilsvarende websted for hvert team.

   > [!NOTE]
   > Du kan også tilføje postkassen og webstedet for Teams, som tilsynsførende ikke er medlem af som dataplacering for tilsynsførende. Det gør du ved at klikke på **Rediger** **ud for Exchange** og **SharePoint** og derefter tilføje den postkasse og det websted, der er knyttet til teamet.

6. Når du har tilføjet tilsynsførende og konfigureret datakilderne til frihedsberøvelse, skal du klikke på **Næste** for at få vist siden **Indstillinger for venteposition** .

   Der vises en liste over tilsynsførende, og afkrydsningsfeltet i kolonnen **Venteposition** er som standard markeret. Dette indikerede, at der vil blive sat en venteposition på de datakilder, du har knyttet til hver tilsynsførende. Lad disse afkrydsningsfelter være markeret for at bevare disse data.

7. Klik på **Næste** på siden **Indstillinger for venteposition** for at gennemse indstillingerne for vogtere. Klik på **Send** for at føje vogterne til sagen.

Du kan finde flere oplysninger om tilføjelse og bevarelse af datakilder i en eDiscovery-sag (Premium) i:

- [Føj tilsynsførende til en eDiscovery-sag (Premium)](add-custodians-to-case.md)

- [Føj datakilder uden frihedsberøvelse til en eDiscovery-sag (Premium)](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Indsaml Teams indhold, og føj til korrektursæt

Når du har føjet tilsynsførende til sagen og bevaret indhold i tilsynsførende datakilder, er det næste trin i arbejdsprocessen at søge efter Teams indhold, der er relevant for din undersøgelse, og føje det til et korrektursæt med henblik på yderligere gennemgang og analyse. Selvom det er typisk at indsamle Teams indhold sammen med indhold fra andre Microsoft 365 tjenester, f.eks. mail i Exchange og dokumenter i SharePoint, fokuserer dette afsnit specifikt på at indsamle Teams indhold i en samling. Du kan oprette yderligere samlinger, der indsamler indhold, der ikke er Teams, for at føje dem til et korrektursæt.

Når du indsamler Teams indhold for en sag, er der to trin i arbejdsprocessen:

1. **Opret en kladdesamling**.  Det første trin er at oprette en *kladdesamling*, som er et estimat over de elementer, der opfylder dine søgekriterier. Du kan få vist oplysninger om de resultater, der matcher søgeforespørgslen, f.eks. det samlede antal og størrelsen af fundne elementer, de forskellige datakilder, hvor de blev fundet, og statistikker om søgeforespørgslen. Du kan også få vist et eksempel på elementer, der blev returneret af samlingen. Ved hjælp af disse statistikker kan du ændre søgeforespørgslen og køre kladdesamlingen igen så mange gange, det er nødvendigt for at indsnævre resultaterne, indtil du er tilfreds med, at du indsamler det indhold, der er relevant for din sag.

2. **Send en kladdesamling til et korrektursæt**. Når du er tilfreds med resultaterne af en kladdesamling, kan du bekræfte samlingen til et korrektursæt. Når du bekræfter en kladdesamling, føjes de elementer, der returneres af samlingen, til et gennemsynssæt til gennemsyn, analyse og eksport.

Du har også mulighed for ikke at køre en kladdesamling og føje samlingsresultaterne direkte til et korrektursæt, når du opretter og kører samlingen.

Sådan opretter du en samling Teams indhold:

1. Gå til eDiscovery(Premium)-sagen, som du føjede vogterne til i det forrige afsnit, og klik derefter på **Samlinger**.

2. På siden **Samlinger** skal du vælge **Ny** **samlingStandardsamling** > .

3. Skriv et navn (obligatorisk) og en beskrivelse (valgfrit) for samlingen.

4. På siden **Frihedsberøvende datakilder** skal du klikke på **Vælg tilsynsførende** for at vælge de tilsynsførende, du har føjet til sagen.

   Listen over sagsvogterne vises på siden **Vælg tilsynsførende** .

5. Vælg en eller flere tilsynsførende, og klik derefter på **Tilføj**.

   Når du har føjet specifikke tilsynsførende til samlingen, vises der en liste over specifikke datakilder for hver tilsynsførende. Dette er de datakilder, du konfigurerede, da du føjede vogteren til sagen. Alle datakilder med frihedsberøvelse er valgt som standard. Dette omfatter alle Teams eller kanaler, som du har knyttet til en tilsynsførende.

   Vi anbefaler, at du gør følgende, når du indsamler Teams indhold:

   - Fjern tilsynsførendes OneDrive konti fra indsamlingsområdet (ved at fjerne markeringen af afkrydsningsfeltet i kolonnen **OneDrive** for hver tilsynsførende). Dette forhindrer, at der findes dublerede filer, der er knyttet til 1:1-chats og gruppechats. Vedhæftede filer i skyen indsamles automatisk fra hver samtale, der findes i samlingen, når du overfører kladdesamlingen til korrektursættet. Ved hjælp af denne metode (i stedet for at søge efter OneDrive konti som en del af samlingen) grupperes filer, der er knyttet til 1:1, og gruppechats i den samtale, de blev delt i.

   - Fjern markeringen i afkrydsningsfeltet i kolonnen **Yderligere websted** for at fjerne de SharePoint websteder, der indeholder filer, der deles i private eller delte kanaler. Dette eliminerer indsamling af dubletfiler, der er knyttet til private eller delte kanalsamtaler, fordi disse vedhæftede filer i skyen automatisk føjes til korrektursættet, når du bekræfter kladdesamlingen og grupperes i de samtaler, de blev delt i.

6. Hvis du tidligere har fulgt trinnene for at tilføje Teams indhold som tilsynsførende datakilder, kan du springe dette trin over og vælge **Næste**. Ellers kan du på siden med guiden **Datakilder uden frihedsberøvelse** vælge datakilder, der indeholder Teams indhold, som du måske har føjet til sagen, for at søge i samlingen.

7. Hvis du tidligere har fulgt trinnene for at tilføje Teams indhold som tilsynsførende datakilder, kan du springe dette trin over og vælge **Næste**. Ellers kan du tilføje andre datakilder, der skal søges i i samlingen, på siden med guiden **Flere placeringer** . Du kan f.eks. tilføje postkassen og webstedet for et team, der ikke blev tilføjet som en datakilde med frihedsberøvelse eller som en datakilde uden frihedsberøvelse. Ellers skal du vælge **Næste** og springe dette trin over.

8. På siden med guiden **Betingelser** skal du konfigurere søgeforespørgslen for at indsamle Teams indhold fra de datakilder, du angav på de forrige guidesider. Du kan bruge forskellige nøgleord og søgebetingelser til at indsnævre omfanget af samlingen. Du kan finde flere oplysninger under [Opret søgeforespørgsler for samlinger](building-search-queries.md).

   For at sikre den mest omfattende samling af Teams chatsamtaler (herunder 1:1, gruppe- og kanalchat) skal du bruge betingelsen **Type** og vælge indstillingen **Chatbeskeder**. Vi anbefaler også, at du inkluderer et datointerval eller flere nøgleord for at begrænse omfanget af samlingen til elementer, der er relevante for din undersøgelse. Her er et skærmbillede af en eksempelforespørgsel, der bruger indstillingerne **Type** og **Dato** :

   ![Forespørgsel, der skal indsamle Teams indhold.](..\media\TeamsConditionsQueryType.png)

9. Gør et af følgende på siden **Med guiden Gem kladde eller Indsaml indsamling** , afhængigt af om du vil oprette en kladdesamling eller sende samlingen til et korrektursæt.

   ![Gem kladdesamling eller bekræftelsessamling.](..\media\TeamsDraftCommitCollection.png)

   1. **Gem samling som kladde**. Vælg denne indstilling for at oprette en kladdesamling. Som tidligere forklaret føjer en kladdesamling ikke samlingsresultaterne til et korrektursæt. Den returnerer et estimat af de søgeresultater, der svarer til søgeforespørgslen for datakilderne i samlingens område. Det giver dig mulighed for at få vist [samlingsstatistik og -rapporter[(collection-statistics-reports.md)] og redigere og køre kladdesamlingen igen. Når du er tilfreds med resultatet af en kladdesamling, kan du sende den til et korrektursæt. Du kan få flere oplysninger under [Opret en kladdesamling](create-draft-collection.md).

   2. **Indsaml elementer, og føj til et korrektursæt**. Vælg denne indstilling for at køre samlingen, og føj derefter resultaterne til et korrektursæt. Du kan føje samlingen til et nyt eller eksisterende korrektursæt. Indstillingerne til at indsamle kontekstafhængige Teams samtalemeddelelser (også kaldet *samtaletrådning*) og indsamle vedhæftede filer i skyen er valgt som standard og kan ikke fjernes. Disse indstillinger anvendes automatisk på grund af det nye sagsformat, som du brugte, da du oprettede sagen til Teams indhold. Du kan få flere oplysninger om, hvordan du binder samlinger til et korrektursæt, under [Anvend en kladdesamling på et korrektursæt](commit-draft-collection.md).

10. Når du er færdig med at konfigurere samlingen, skal du sende samlingen for at oprette en kladdesamling eller indsamle elementer og føje dem til et korrektursæt.

   Når processen med at føje samlingen til korrektursættet er fuldført, angives statusværdien for samlingen under fanen **Samlinger** til **Bekræftet**.

## <a name="review-teams-content-in-a-review-set"></a>Gennemse Teams indhold i et korrektursæt

Når du har føjet samlinger af Teams indhold til et anmeldelsessæt, er det næste trin at gennemse indholdet for at se dets relevans for din undersøgelse og om nødvendigt udsætte det. En vigtig forudsætning for at gennemse Teams indhold er at forstå, hvordan eDiscovery (Premium) behandler Teams chatsamtaler og vedhæftede filer, når du føjer dem til et korrektursæt. Denne behandling af Teams indhold resulterer i følgende tre ting:

- **[Gruppering](#grouping)**. Sådan grupperes meddelelser, indlæg og svar Teams samtaler sammen og præsenteres i korrektursættet. Dette omfatter også vedhæftede filer i chatsamtaler, der udtrækkes og grupperes i samtalen.

- **[Transskriptionssamtaletråde](#transcript-conversation-threading)**. Hvordan eDiscovery (Premium) bestemmer, hvilket yderligere indhold fra en samtale der skal indsamles, for at give kontekst omkring elementer, der opfylder kriterierne for samlingen.

- **[Deduplication](#deduplication-of-teams-content)**. Sådan håndterer eDiscovery (Premium) duplikeret Teams indhold.

- **[Metadata](#metadata-for-teams-content)**. Metadataegenskaber, som eDiscovery (Premium) føjer til Teams indhold, når det er indsamlet og føjet til et korrektursæt.

Forstå gruppering, samtaletrådning, deduplikering og Teams metadata hjælper dig med at optimere gennemgangen og analysen af Teams indhold. Dette afsnit indeholder også [tip til visning af Teams indhold i et anmeldelsessæt](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Gruppering

Når indhold fra Teams chatsamtaler føjes til et korrektursæt, samles meddelelser, indlæg og svar fra samtaler i HTML-transskriptionsfiler. En enkelt chatsamtale kan have flere transskriptionsfiler. En vigtig funktion i disse transskriptionsfiler er at præsentere Teams indhold som fortløbende samtaler og ikke som individuelle (eller separate) meddelelser. Dette hjælper med at give kontekst for elementer, der opfylder søgekriterierne i dine samlinger i det forrige trin, og reducere antallet af elementer, der indsamles i korrektursættet. Transskriptioner og tilknyttede elementer kan grupperes efter enten *familie* eller *samtale*. Elementer i samme serie har samme værdi for egenskaben **FamilyId-metadata** . Elementer i den samme samtale har samme værdi for metadataegenskaben **ConversationId** .

I følgende tabel beskrives det, hvordan de forskellige typer Teams chatindhold grupperes efter familie og samtale.

|Teams indholdstype|Gruppér efter familie|Gruppér efter samtale|
|---|---|---|
|Teams 1:1 og gruppechats|En transskription og alle dens vedhæftede filer og udtrukne elementer deler det samme **FamilyId**. Hver transskription har et entydigt **FamilyId**.|Alle transskriptionsfiler og deres familieelementer i den samme samtale deler det samme **Samtale-id**. Dette omfatter følgende elementer: <ul><li>Alle udtrukne elementer og vedhæftede filer i alle transskriptioner, der deler det samme **Samtale-id**.</li><li>Alle transskriptioner for den samme chatsamtale</li><li>Alle forældremyndighedskopier af hver transskription</li><li>Transskriptioner fra efterfølgende samlinger fra den samme chatsamtale</li></ul> <br/> I forbindelse med Teams 1:1 og gruppechatsamtaler kan du have flere transskriptionsfiler, som hver især svarer til en anden tidsramme i samtalen. Da disse transskriptionsfiler er fra den samme samtale med de samme deltagere, deler de det samme **Samtale-id**.|
|Chats om standardkanaler, private og delte kanaler|Hvert indlæg og alle svar og vedhæftede filer gemmes i deres egen transskription. Transskriptionen og alle dens vedhæftede filer og udtrukne elementer deler det samme **FamilyId**.|Hvert indlæg og dets vedhæftede filer og udtrukne elementer har et entydigt **Samtale-id**. Hvis der er efterfølgende samlinger eller nye svar fra det samme indlæg, har delta-transskriptionerne fra disse samlinger også det samme **Samtale-id**.|

Brug kontrolelementet **Gruppe** på kommandolinjen i et korrektursæt til at få vist Teams indhold grupperet efter familie eller samtale.

![Kontrolelementet Gruppér på kommandolinjen.](..\media\TeamsGroupControl.png)

- Vælg **Gruppér vedhæftede filer i familien** for at få vist Teams indhold grupperet efter familie. Hver transskriptionsfil vises på en linje på listen over elementer, der er angivet til gennemsyn. Vedhæftede filer er indlejret under elementet.

- Vælg **Gruppér Teams eller Yammer samtaler** for at få vist Teams indhold grupperet efter samtale. Hver samtale vises på en linje på listen over elementer, der er angivet til gennemsyn. Transskriptionsfiler og vedhæftede filer indlejres under samtalen på øverste niveau.

> [!NOTE]
> Vedhæftede filer i skyen grupperes sammen med de samtaler, de vises i. Denne gruppering opnås ved at tildele det samme **FamilyId** som transskriptionsfilen for den meddelelse, filen blev knyttet til, og det samme **Samtale-id** som den samtale, som meddelelsen blev vist i. Det betyder, at der kan føjes flere kopier af vedhæftede filer i skyen til korrektursættet, hvis de var knyttet til forskellige samtaler.

#### <a name="viewing-transcript-files-for-conversations"></a>Visning af transskriptionsfiler til samtaler

Når du får vist transskriptionsfiler i et korrektursæt, fremhæves nogle af meddelelserne i lilla. De meddelelser, der fremhæves, afhænger af, hvilken tilsynsførende kopi af transskriptionen du får vist. I en 1:1-chat mellem User4 og User2 fremhæves de meddelelser, der er sendt af User4, f.eks. i lilla, når du får vist transskriptionen indsamlet fra User4s postkasse. Når du får vist User2s transskription af den samme samtale, fremhæves meddelelser, der er sendt af User2, med lilla. Denne fremhævning er baseret på den samme Teams klientoplevelse, hvor en brugers indlæg fremhæves i lilla i Teams-klienten.

Følgende skærmbilleder viser et eksempel på samtale i Teams-klienten og transskriptionsfilen for den samme samtale i korrektursættet. Den lilla fremhævning i transskriptionsfilen angiver, at transskriptionen blev indsamlet fra User2s postkasse.

##### <a name="conversation-in-teams-client"></a>Samtale i Teams klient

![Samtale, der vises i transskriptionsfilen i korrektursættet.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Samtale i transskriptionsfil

![Samme samtale, der vises i Teams klient.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Transskriptionssamtaletråde

Funktionen Til samtaletrådning i det nye sagsformat i eDiscovery (Premium) hjælper dig med at identificere kontekstafhængigt indhold, der er relateret til elementer, der kan være relevant for din undersøgelse. Denne funktion producerer forskellige samtalevisninger, der omfatter chatmeddelelser, der kommer før og følger elementerne, svarer til søgeforespørgslen under samlingen. Denne funktion giver dig mulighed for effektivt og hurtigt at gennemse komplette chatsamtaler (kaldet *gevindsamtaler*) i Microsoft Teams. Som tidligere forklaret genskabes chatsamtaler i HTML-transskriptionsfiler, når eDiscovery (Premium) føjer Teams indhold til et korrektursæt.

Her er den logik, der bruges af eDiscovery (Premium) til at inkludere yderligere meddelelser og svar transskriptionsfiler, der giver kontekst omkring elementerne, der svarer til den samlingsforespørgsel (kaldet *dynamiske elementer*), du brugte til at indsamle Teams indhold. Forskellige funktionsmåder for trådning er baseret på typerne af chats og den søgeforespørgsel, der bruges til at indsamle de dynamiske elementer. Der er to almindelige samlingsscenarier:

- Forespørgsler, der bruger søgeparametre, f.eks. nøgleord og egenskab:værdipar

- Forespørgsler, der kun bruger datointervaller

|Teams indholdstype|Forespørgsler med søgeparametre|Forespørgsler med datointervaller|
|---|---|---|
|Teams 1:1 og gruppechats|Meddelelser, der blev sendt 12 timer før og 12 timer efter dynamiske elementer, grupperes med det dynamiske element i en enkelt transskriptionsfil.|Meddelelser i et 24-timers vindue er grupperet i en enkelt transskriptionsfil.|
|Standardchat, privat og delt Teams kanalchat|Hvert indlæg, der indeholder dynamiske elementer og alle tilsvarende svar, grupperes i en enkelt transskriptionsfil.|Hvert indlæg, der indeholder dynamiske elementer og alle tilsvarende svar, grupperes i en enkelt transskriptionsfil.|

### <a name="deduplication-of-teams-content"></a>Deduplikering af Teams indhold

På følgende liste beskrives funktionsmåden for deduplikering (og duplikering), når du indsamler Teams indhold i et korrektursæt.

- Hver transskriptionsfil, der føjes til et korrektursæt, skal være en en til en-tilknytning til indhold, der er gemt på dataplaceringer. Det betyder, at eDiscovery (Premium) ikke indsamler Teams indhold, der allerede er føjet til korrektursættet. Hvis en chatmeddelelse allerede er indsamlet i et korrektursæt, føjer eDiscovery (Premium) ikke den samme meddelelse fra den samme dataplacering til korrektursættet i efterfølgende samlinger.

- I forbindelse med 1:1- og gruppechat gemmes kopier af meddelelser i hver samtaledeltagers postkasse. Kopier af den samme samtale, der findes i forskellige deltageres postkasser, indsamles med forskellige metadata. Derfor behandles hver forekomst af samtalen som entydig og overføres til korrektursættet i separate transskriptionsfiler. Så hvis alle deltagere i en 1:1- eller gruppechat tilføjes som tilsynsførende i en sag og inkluderes i omfanget af en samling, føjes der kopier af hver transskription (for den samme bevarelse) til korrektursættet og grupperes sammen med det samme **Samtale-id**. Hver af disse kopier er knyttet til en tilsvarende tilsynsførende. **Tip**! Kolonnen **Custodian** på listen over korrektursæt identificerer tilsynsførende for den tilsvarende transskriptionsfil.

- I efterfølgende samlinger af elementer fra den samme samtale er det kun deltaindholdet, der ikke tidligere blev indsamlet, der føjes til korrektursættet og grupperes (ved at dele det samme **Samtale-id**) med de tidligere indsamlede transskriptioner fra den samme samtale. Her er et eksempel på denne funktionsmåde:

   1. Collection A indsamler meddelelser i en samtale mellem User1 og User2 og føjer til korrektursættet.

   2. Samling B indsamler meddelelser fra den samme samtale, men der er nye meddelelser mellem User1 og User2, siden Samling A blev kørt.

   3. Det er kun de nye meddelelser i Samling B, der føjes til korrektursættet. Disse meddelelser føjes til en separat transskriptionsfil, men den nye transskription grupperes med transskriptionerne fra Samling A efter det samme **Samtale-id**.

   Denne funktionsmåde gælder for alle typer Teams chats.

### <a name="metadata-for-teams-content"></a>Metadata for Teams indhold

I store korrektursæt med tusindvis eller millioner af elementer kan det være svært at indsnævre omfanget af din anmeldelse for at Teams indhold. For at hjælpe dig med at fokusere din anmeldelse på Teams indhold er der metadataegenskaber, der er specifikke for Teams indhold. Du kan bruge disse egenskaber til at organisere kolonnerne på listen over [korrekturer og konfigurere filtre og forespørgsler](review-set-search.md) for at optimere gennemgangen af Teams indhold. Disse metadataegenskaber medtages også, når du eksporterer Teams indhold fra eDiscovery (Premium) for at hjælpe dig med at organisere og få vist indhold efter eksport eller i eDiscovery-værktøjer fra tredjepart.

I følgende tabel beskrives metadataegenskaber for Teams indhold.

|Metadataegenskab|Beskrivelse|
|---|---|
|ContainsEditedMessage|Angiver, om en transskriptionsfil indeholder en redigeret meddelelse. Redigerede meddelelser identificeres, når transskriptionsfilen vises.|
|Samtale-id|Et GUID, der identificerer den samtale, som elementet er knyttet til. Transskriptionsfiler og vedhæftede filer fra den samme samtale har samme værdi for denne egenskab.|
|Samtalenavn|Navnet på den samtale, som transskriptionsfilen eller den vedhæftede fil er knyttet til. For Teams 1:1 og gruppechats er værdien af denne egenskab UPN for alle deltagere i samtalen sammenkædes. For eksempel `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams-kanalchats (standardchat, private og delte) chats bruger følgende format som samtalenavn: `<Team name>,<Channel name>`. For eksempel `eDiscovery vNext, General`.|
|Samtaletype|Angiver typen af teamchat. For Teams 1:1 og gruppechats er `Group`værdien for denne egenskab . For chats med almindelige, private og delte kanaler er `Channel`værdien .|
|Dato|Tidsstemplet for den første meddelelse i transskriptionsfilen.|
|FamilyId|Et GUID, der identificerer transskriptionsfilen for en chatsamtale. Vedhæftede filer har samme værdi for denne egenskab som den transskriptionsfil, der indeholder den meddelelse, filen blev vedhæftet.|
|FileClass|Angiver denne type indhold. Elementer fra Teams chats har værdien `Conversation`. I modsætning hertil har Exchange mails værdien `Email`.|
|Meddelelseskind|Egenskaben meddelelsestype. Teams indhold har værdien `microsoftteams , im`.|
|Modtagere|En liste over alle brugere, der har modtaget en meddelelse i transskriptionssamtalen.|
|TeamsChannelName|Transskriptionens Teams kanalnavn.|

Du kan finde beskrivelser af andre egenskaber for eDiscovery-metadata (Premium) [under Dokumentmetadatafelter i eDiscovery (Premium).](document-metadata-fields-in-Advanced-eDiscovery.md)

## <a name="export-teams-content"></a>Eksportér Teams indhold

Når du har gennemgået og slettet Teams indhold i et anmeldelsessæt, kan du eksportere de transskriptionsfiler, der indeholder indhold, som reagerer på din undersøgelse. Der er ikke nogen specifikke eksportindstillinger for Teams indhold. Hver transskriptionsfil eksporteres som en HTML-meddelelsesfil. Denne fil indeholder også skjulte CDATA-koder med alle metadata for de enkelte chatbeskeder. De metadataegenskaber, der er beskrevet i forrige afsnit, medtages, når Teams indhold eksporteres.  

Der refereres til hver transskriptionsfil i indlæsningsfilen, og den kan findes ved hjælp af den relative sti i feltet Export_native_path i indlæsningsfilen. Transskriptionsfiler findes i mappen Samtaler i rodeksportmappen.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Tip til visning Teams indhold i et anmeldelsessæt

Her er nogle tip og bedste praksis for visning Teams indhold i et anmeldelsessæt.

- Brug kontrolelementet **Tilpas kolonner** på kommandolinjen til at tilføje og organisere kolonner for at optimere gennemgangen af Teams indhold.

  ![Brug pop op-siden Rediger kolonne til at tilføje, fjerne og organisere kolonner.](..\media\EditReviewSetColumns.png)

   Du kan tilføje og fjerne kolonner, der er nyttige til Teams indhold. Du kan også sortere rækkefølgen af kolonner ved at trække og slippe dem på siden **Rediger kolonne** . Du kan også sortere efter kolonner for at gruppere Teams indhold med lignende værdier for den kolonne, du sorterer efter.

- Nyttige kolonner, der kan hjælpe dig med at gennemse Teams indhold, omfatter **Tilsynsførende**, **Modtagere** og **Filtype** eller **Meddelelsestype**.

- Brug [filtre](review-set-search.md) til Teams-relaterede egenskaber til hurtigt at få vist Teams indhold. Der er filtre for de fleste metadataegenskaber, der er beskrevet i forrige afsnit.

## <a name="deleting-teams-chat-messages"></a>Sletter Teams chatbeskeder

Du kan bruge eDiscovery (Premium) og Microsoft Graph Explorer til at reagere på dataspildhændelser, når indhold, der indeholder fortrolige eller skadelige oplysninger, frigives via Teams chatbeskeder. Administratorer i din organisation kan søge efter og slette chatbeskeder i Microsoft Teams. Dette kan hjælpe dig med at fjerne følsomme oplysninger eller upassende indhold i Teams chatbeskeder. Du kan finde flere oplysninger [under Søg efter og fjern chatbeskeder i Teams](search-and-delete-Teams-chat-messages.md).

## <a name="reference-guide"></a>Referencevejledning

Her er en vejledning i, hvordan du bruger eDiscovery (Premium) til Microsoft Teams. I denne vejledning opsummeres nøglepunkterne for brug af eDiscovery (Premium) til at bevare, indsamle, gennemse og eksportere indhold fra Microsoft Teams.

![Miniature til referencevejledning til brug af eDiscovery (Premium) til Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Download som en PDF-fil](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
