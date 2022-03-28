---
title: Teams arbejdsproces i Advanced eDiscovery
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
description: Lær at bevare, indsamle, gennemse og eksportere indhold fra Microsoft Teams i Advanced eDiscovery.
ms.openlocfilehash: 27f3ada633f7af37b657e59cce64ef1c8e102177
ms.sourcegitcommit: b71a8fdda2746f18fde2c94d188be89f9cab45f2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/21/2021
ms.locfileid: "63598031"
---
# <a name="advanced-ediscovery-workflow-for-content-in-microsoft-teams"></a>Advanced eDiscovery arbejdsproces for indhold i Microsoft Teams

Denne artikel indeholder et omfattende sæt procedurer, retningslinjer og bedste fremgangsmåder til brug af Advanced eDiscovery til at bevare, indsamle, gennemgå og eksportere indhold fra Microsoft Teams. Formålet med denne artikel er at hjælpe dig med at optimere din eDiscovery-arbejdsproces til Teams indhold.

Der er fire kategorier af indhold Teams, som du kan indsamle og behandle ved hjælp af Advanced eDiscovery:

- **Teams chatsamtaler med 1:1**. Chatbeskeder, indlæg og vedhæftede filer, der deles Teams en samtale mellem to personer.  Teams 1:1-chats kaldes også *samtaler*.

- **Teams gruppechats**. Chatbeskeder, indlæg og vedhæftede filer, der er delt Teams en samtale mellem tre eller flere personer. Kaldes også *1:N-chatsamtaler* *eller gruppesamtaler*.

- **Teams kanaler**. Chatmeddelelser, indlæg, svar og vedhæftede filer, der er delt i Teams kanal.

- **Private Teams kanaler**. Meddelelsesopslag, svar og vedhæftede filer, der er delt i en Teams kanal.

## <a name="where-teams-content-is-stored"></a>Hvor Teams indhold gemmes

En forudsætning for at administrere Teams-indhold i Advanced eDiscovery er at forstå typen af Teams-indhold, du kan indsamle, behandle og gennemgå i Advanced eDiscovery, og hvor indholdet er gemt i Microsoft 365. I følgende tabel vises Teams indholdstype, og hvor hver indholdstype er gemt.

||Placering af chatmeddelelser og indlæg  |Placering af filer og vedhæftede filer |
|:---------|:---------|:---------|
|Teams chatsamtaler med 1:1     |Meddelelser i 1:1-chats gemmes i Exchange Online for alle chatdeltagere. |Filer, der deles i en 1:1-chat, gemmes OneDrive for Business den person, der har delt filen. |
|Teams gruppechats     |Meddelelser i gruppechats gemmes i Exchange Online for alle chatdeltagere. |Filer, der deles i gruppechats, gemmes OneDrive for Business den person, der har delt filen. |
|Teams kanaler     |Alle kanalmeddelelser og -indlæg gemmes i den Exchange Online, der er knyttet til teamet.|Filer, der deles i en kanal, gemmes på det SharePoint Online-websted, der er knyttet til teamet.           |
|Private Teams kanaler     |Meddelelser, der sendes i en privat kanal, gemmes i Exchange Online for alle medlemmer af den private kanal.|Filer, der deles i en privat kanal, gemmes i et dedikeret SharePoint Online-websted, der er knyttet til den private kanal.|
||||

## <a name="create-a-case-for-teams-content"></a>Oprette en sag til Teams indhold

Det første trin til at administrere Teams indhold i Advanced eDiscovery er at oprette en sag ved hjælp af det nye sagsformat, der er optimeret til administration af Teams indhold. Her er fordelene ved at bruge det nye format for store og små bogstaver til Teams indhold:

- Understøttelse af samtaletråde, hvor flere meddelelser i den samme samtale, der indeholder dynamiske elementer, automatisk indsamles og tilføjes til korrektursæt.

- Teams tilføjes chatsamtaler automatisk for at gennemgå sæt som en HTML-afskriftsfil. Vedhæftede skybaserede filer, der deles i samtaler, føjes også til korrektursættet. Dette hjælper med at give kontekst til samtaler med hurtige elementer og reducere det samlede antal elementer, der er produceret af chatbaseret indhold.

- Samlinger på op til 1 TB kan tilføjes til korrektursæt, som gør det muligt at indsamle og beløbe store mængder indhold Teams i en sag.

Du kan finde flere oplysninger om de øgede sagsgrænser [i Brug det nye sagsformat Advanced eDiscovery](advanced-ediscovery-new-case-format.md).

Sådan oprettes en sag:

1. Gå til <https://compliance.microsoft.com> , og log på.

2. Klik på **eDiscovery Microsoft 365 Overholdelsescenter avanceret i navigations > ruden i venstre side**.

3. På siden **Advanced eDiscovery** skal du klikke på **fanen Sager** og derefter klikke på **Opret en sag**.

   Pop **op-siden Ny eDiscovery-sag** vises. Sektionen **Sagsformat** giver mulighed for at oprette en sag ved hjælp af det nye sagsformat.

   ![Indstillingen Store sag på siden Ny eDiscovery-sag.](..\media\AeDNewCaseFormat1.png)

4. Når du har navngivet sagen, skal du **vælge** indstillingen Ny og derefter klikke **på Gem** for at oprette sagen.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Tilføje Teams datakilder, der skal beskyttes, og Teams indhold  

Det næste trin er at identificere de brugere, der er databehandlere i undersøgelsen, og tilføje dem og deres indholdsplaceringer som kontrolere til den sag, du oprettede i forrige afsnit. Når du tilføjer ledende kilder, kan du angive deres postkasse og konto OneDrive somkonto som datakilder, der er tillid til. Du kan også angive Teams-indholdsplaceringer som datakilder, der er under kontrol, for hurtigt at placere disse placeringer i retslig venteposition for at bevare indhold under undersøgelsen. Det gør det også nemt at indsamle indhold og føje det til et korrektursæt.

Sådan føjer du ledende leverandører til en sag og bevarer datakilder, der er følsomme for sagen:

1. Gå til den Advanced eDiscovery, du oprettede i forrige afsnit, og klik derefter på **Datakilder**.

2. På siden **Datakilder skal** du klikke på **Tilføj datakilderFængsere** >  **nye tilføjelsesere**.

3. I guiden **Ny kontaktperson skal** du tilføje en eller flere brugere som brugere, der skal være hjælpere til sagen, ved at skrive den første del af brugerens navn eller alias. Når du har fundet den rigtige person, skal du vælge personens navn for at føje vedkommende til listen.  

4. Udvid hver medarbejder for at få vist de primære datakilder, der er blevet automatisk knyttet til assistenten, og for at vælge andre placeringer, der skal knyttes til den person, der skal vises.

   ![Datakilder, der er understiansk.](..\media\TeamsCustodialDataLocations1.png)

5. Følg disse retningslinjer for at føje datakilder til indsamling af oplysninger Teams indhold. Klik **på Rediger** for at tilføje en dataplacering.

   - **Postkasser**. Den andens postkasse er valgt som standard. Sørg for, at dette er valgt for at tilføje (og bevare) 1:1-chats, gruppechats og private kanalchats som oplysninger om din hjælp.

   - **OneDrives**. Den OneDrive OneDrive konto er valgt som standard. Sørg for, at dette vælges for at tilføje (og bevare) filer, der deles i 1:1-chats og gruppechats, som følsomme data.

   - **SharePoint**. Tilføj det SharePoint websted, der er knyttet til en privat kanal, som den, der er tilknyttet, er medlem af for at tilføje (og bevare) som arkiveringsdata for de filer, der deles i den private kanal. Klik **på Rediger**, og tilføj derefter URL-adressen til det SharePoint, der er knyttet til en privat kanal. Du kan få mere at vide om, hvordan du finder de private kanaler, en bruger er medlem af, [under eDiscovery til private kanaler](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels).

   - **Teams**. Tilføj de teams, som din leder er medlem af, for at tilføje (og bevare) som arkiveringsdata for alle kanalmeddelelser og alle filer, der deles på en Teams kanal. Når du klikker **på Rediger**, vises den postkasse og det websted, der er knyttet til hvert team, som teamets leder er medlem af, på en liste. Vælg de teams, du vil knytte til assistenten. Du skal vælge både den tilsvarende postkasse og webstedet for hvert team.

   > [!NOTE]
   > Du kan også tilføje postkassen og webstedet for de Teams, som familiemedlemmer ikke er medlemmer af som en placering, hvor dataene skal vises. Det gør du ved **at klikke på** **Rediger Exchange** gruppen **SharePoint** derefter tilføje postkassen og webstedets tilknytning til teamet.

6. Når du har tilføjet ledende leverandører og konfigurerer de sikkerhedsdatakilder, du skal bruge, skal du klikke på **Næste** for at **få vist siden med indstillinger for** Venteposition.

   Der vises en liste over personer, der skal anvendes, og afkrydsningsfeltet i **kolonnen Venteposition** er markeret som standard. Dette angav, at der ville blive sat en venteposition på de datakilder, du har knyttet til hver modtager. Lad disse afkrydsningsfelter være markeret for at bevare disse data.

7. På siden **med indstillinger for Venteposition** skal du klikke **på Næste for** at gennemgå indstillingerne for y-ne. Klik **på Send** for at føje anmodningsboerne til sagen.

Du kan finde flere oplysninger om at tilføje og bevare datakilder Advanced eDiscovery en ny sag under:

- [Føje Advanced eDiscovery ere til Advanced eDiscovery sag](add-custodians-to-case.md)

- [Føj ikke-registrerede datakilder til en Advanced eDiscovery sag](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Indsaml Teams indhold, og tilføj for at gennemse sættet

Når du har føjet kontrolere til sagen og bevarer indhold i datakilder, der er under kontrol, er næste trin i arbejdsprocessen at søge efter Teams-indhold, der er relevant for din undersøgelse, og føje det til et gennemgangssæt til yderligere gennemgang og analyse. Selvom det typisk er at indsamle Teams-indhold sammen med indhold fra andre Microsoft 365-tjenester som f.eks. mail i Exchange og dokumenter i SharePoint, fokuserer dette afsnit specifikt på indsamling af Teams-indhold i en samling. Du kan oprette flere samlinger, der indsamler ikke-Teams indhold, der skal føjes til et korrektursæt.

Når du indsamler Teams indhold for en sag, er der to trin i arbejdsprocessen:

1. **Opret en kladdesamling**.  Det første trin er at oprette en *kladdesamling*, som er et estimat af de elementer, der opfylder dine søgekriterier. Du kan få vist oplysninger om de resultater, der matchede søgeforespørgslen, f.eks. det samlede antal og størrelsen af elementer, der blev fundet, de forskellige datakilder, hvor de blev fundet, og statistik om søgeforespørgslen. Du kan også få vist et eksempel på et eksempel på elementer, der er returneret af samlingen. Ved hjælp af disse statistikker kan du ændre søgeforespørgslen og køre kladdesamlingen igen så mange gange, som det er nødvendigt for at indsnævre resultaterne, indtil du er tilfreds med, at du indsamler det indhold, der er relevant for din sag.

2. **Bestil en kladdesamling til et korrektursæt**. Når du er tilfreds med resultaterne af en kladdesamling, kan du bekræfte samlingen i et gennemsynssæt. Når du har bekræftet en kladdesamling, føjes de elementer, der returneres af samlingen, til et korrektursæt til gennemsyn, analyse og eksport.

Du har også mulighed for ikke at køre en kladdesamling og føje resultaterne af samlingen direkte til et korrektursæt, når du opretter og kører samlingen.

Sådan opretter du en samling Teams indhold:

1. Gå til den Advanced eDiscovery, som du har føjet ydsere til i forrige afsnit, og klik derefter **på Samlinger**.

2. På siden **Samlinger skal** du vælge Ny **samlingStandard-samling** > .

3. Skriv et navn (påkrævet) og en beskrivelse (valgfrit) til samlingen.

4. Klik på **Vælg y-y-væsner**, du har føjet til sagen, på sidenYydatakilder for at vælge de ydsianianer, du har føjet til sagen.

   Listen over de personer, der skal anvendes, bliver vist på pop **op-siden Vælg** y-personer.

5. Vælg en eller flere førere, og klik derefter **på Tilføj**.

   Når du har føjet bestemte personer, der skal anvendes, til samlingen, vises der en liste over bestemte datakilder for hver person, der er tillid til. Dette er de datakilder, du konfigurerede, da du føjede den person, der skal have sagen, til sagen. Alle datakilder, der er under hjælp til hjælp, er valgt som standard. Dette omfatter alle Teams og private kanaler, som du har knyttet til en person, der er tilknyttet en person, der er tilknyttet.

   Vi anbefaler, at du gør følgende, når du indsamler Teams indhold:

   - Fjern OneDrive konti fra samlingsomfanget (ved at fjerne markeringen i afkrydsningsfeltet i kolonnen Med hjælp til **OneDrive** for hver kontrolplum). Dette forhindrer indsamling af dublerede filer, der blev vedhæftet 1:1-chats og gruppechats. Vedhæftede skybaserede filer indsamles automatisk fra hver samtale, der findes i samlingen, når du opbevarer kladdesamlingen i gennemsynssættet. Ved at bruge denne metode (i stedet OneDrive søge på konti som en del af samlingen) grupperes filer, der er vedhæftet 1:1 og gruppechats, i den samtale, de blev delt i.

   - Fjern markeringen i afkrydsningsfeltet i kolonnen Yderligere **websted for at fjerne** markeringen af de websteder SharePoint der indeholder filer, der er delt i private kanaler. Dette fjerner indsamling af dublerede filer, der blev vedhæftet private kanalsamtaler, fordi vedhæftede skyfiler, der er vedhæftet private kanalsamtaler, automatisk føjes til gennemsynssættet, når du arkiverer kladdesamlingen og grupperes i de samtaler, der blev delt i.

6. Hvis du tidligere har fulgt trinnene for at tilføje Teams som datakilder, der skal følges, kan du springe dette trin over og vælge **Næste**. Ellers kan du på siden for guider for **ikke-registrerede datakilder vælge ikke-registrerede** datakilder, der indeholder Teams indhold, som du måske har føjet til sagen for at søge i samlingen.

7. Hvis du tidligere har fulgt trinnene for at tilføje Teams som datakilder, der skal følges, kan du springe dette trin over og vælge **Næste**. Ellers kan du **på siden med** guiden Yderligere placeringer tilføje andre datakilder for at søge i samlingen. Du kan f.eks. tilføje postkassen og webstedet for et team, der ikke blev tilføjet som en selvbeholdende eller ikke-arkivende datakilde. Ellers skal du **vælge Næste** og springe dette trin over.

8. På siden **med guiden** Betingelser skal du konfigurere søgeforespørgslen til at indsamle Teams fra de datakilder, du angav på de forrige sider i guiden. Du kan bruge forskellige nøgleord og søgebetingelser for at begrænse omfanget af samlingen. Du kan finde flere oplysninger [i Oprette søgeforespørgsler efter samlinger](building-search-queries.md).

   For at sikre den mest omfattende samling af Teams-chatsamtaler (herunder 1:1, gruppe-, kanal- og private chatsamtaler) skal du bruge betingelsen **Type** og vælge indstillingen **Chatbeskeder.** Vi anbefaler også, at du med medtage et datointerval eller flere nøgleord for at begrænse omfanget af samlingen til elementer, der er relevante for din undersøgelse. Her er et skærmbillede af en eksempelforespørgsel, der bruger **indstillingerne Type** **og** Dato:

   ![Forespørgsel til indsamling Teams indhold.](..\media\TeamsConditionsQueryType.png)

9. På siden **Gem kladde eller** indsaml guide skal du gøre et af følgende, afhængigt af om du vil oprette en kladdesamling eller gemme samlingen i et gennemsynssæt.

   ![Gem kladdesamling, eller begået samling.](..\media\TeamsDraftCommitCollection.png)

   1. **Gem samling som kladde**. Vælg denne indstilling for at oprette en kladdesamling. Som tidligere beskrevet føjer en kladdesamling ikke samlingsresultaterne til et korrektursæt. Den returnerer et estimat af de søgeresultater, der svarer til søgeforespørgslen for datakilderne i samlingens omfang. Dette giver dig mulighed for at få vist [samlingsstatistik og rapporter[(samlingsstatistik-reports.md)] og redigere og køre kladdesamlingen igen. Når du er tilfreds med resultatet af en kladdesamling, kan du bekræfte den i et gennemsynssæt. Få mere at vide under [Opret en kladdesamling](create-draft-collection.md).

   2. **Indsaml elementer, og føj til et korrektursæt**. Vælg denne indstilling for at køre samlingen, og føj derefter resultaterne til et korrektursæt. Du kan føje samlingen til et nyt eller eksisterende korrektursæt. Indstillingerne til at indsamle kontekstafhængige Teams samtalemeddelelser (også kaldet samtaletrådning *) og* indsamle vedhæftede skybaserede filer er valgt som standard og kan ikke fravælges. Disse indstillinger anvendes automatisk på grund af det nye sagsformat, du brugte, da du først oprettede sagen for Teams indhold. Du kan finde flere oplysninger om at bekræfte samlinger i et korrektursæt under [Bekræfte en kladdesamling i et gennemsynssæt](commit-draft-collection.md).

10. Når du er færdig med at konfigurere samlingen, skal du sende samlingen for at oprette en kladdesamling eller samle elementer og føje dem til et korrektursæt.

   Når processen med at føje samlingen til korrektursættet er fuldført, er statusværdien for samlingen under fanen Samlinger angivet  til **Bindende**.

## <a name="review-teams-content-in-a-review-set"></a>Gennemse Teams i et korrektursæt

Når du har føjet samlinger af Teams indhold til et korrektursæt, er næste trin at gennemgå indholdets relevans for din undersøgelse og annullere det, hvis det er nødvendigt. En vigtig forudsætning for at gennemgå Teams indhold er at forstå, hvordan Advanced eDiscovery behandler Teams chatsamtaler og vedhæftede filer, når du føjer dem til et korrektursæt. Denne behandling af Teams indhold resulterer i følgende tre ting:

- **[Gruppering](#grouping)**. Hvordan meddelelser, indlæg og svar Teams samtaler grupperes og præsenteres i korrektursættet. Dette omfatter også vedhæftede filer i chatsamtaler udtrækkes og grupperes i samtalen.

- **[Afskrift af samtaletråde](#transcript-conversation-threading)**. Hvordan Advanced eDiscovery afgør, hvilket ekstra indhold fra en samtale, der skal indsamles for at give kontekst omkring elementer, der matcher samlingskriterierne.

- **[Deduplikering](#deduplication-of-teams-content)**. Sådan Advanced eDiscovery dubletter Teams indhold.

- **[Metadata](#metadata-for-teams-content)**. Metadataegenskaber, Advanced eDiscovery føjer til Teams, efter det er blevet indsamlet og føjet til et korrektursæt.

Hvis du forstår gruppering, samtaletrådning, deduplikering og Teams metadata, kan det hjælpe dig med at optimere gennemgang og analyse Teams indhold. Dette afsnit indeholder også [tip til at få Teams indhold i et korrektursæt](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Gruppering

Når indhold fra Teams tilføjes chatsamtaler i et korrektursæt, samles meddelelser, indlæg og svar fra samtaler i HTML-afskriftsfiler. En enkelt chatsamtale kan have flere afskriftsfiler. En vigtig funktion af disse afskriftsfiler er at præsentere Teams indhold som kontinuerlige samtaler og ikke som individuelle (eller separate) meddelelser. Dette hjælper med at give kontekst til elementer, der svarer til søgekriterierne i dine samlinger i det forrige trin, og det reducerer antallet af elementer, der indsamles i korrektursættet. Afskrifter og tilknyttede elementer kan grupperes efter enten *familie* eller *samtale*. Elementer i samme familie har den samme værdi for **FamilyId-metadataegenskaben** . Elementer i den samme samtale har samme værdi for egenskaben **ConversationId-metadata** .

I følgende tabel beskrives det, hvordan de forskellige typer Teams chatindhold grupperes efter familie og samtale.

| Teams indholdstype|Gruppere efter familie  |Gruppere efter samtale  |
|:---------|:---------|:---------|
|Teams 1:1 og gruppechats   | En udskrift og alle dens vedhæftede filer og udpakkede elementer deler det samme **FamilyId**. Hver afskrift har et entydigt **FamilyId**. |Alle afskriftsfiler og deres familieelementer i den samme samtale deler det samme **ConversationId**. Dette omfatter følgende elementer:<br/><br/>  - Alle udtrukne elementer og vedhæftede filer af alle afskrifter, der deler det samme **ConversationId**. <br/> - Alle afskrifter for den samme chatsamtale<br/> - Alle udvisker kopier af hver afskrift<br/> - Afskrifter fra efterfølgende samlinger fra den samme chatsamtale <br/><br/>  I Teams 1:1 og gruppechatsamtaler kan du have flere afskriftsfiler, hver enkelt svarende til en anden tidsramme i samtalen. Da disse afskriftsfiler er fra den samme samtale med de samme deltagere, deler de det samme **ConversationId**.|
|Teams og private kanalchats    | Hvert indlæg og alle svar og vedhæftede filer gemmes i deres egen afskrift. Denne afskrift og alle dens vedhæftede filer og udpakkede elementer deler det samme **FamilyId**.         |Hvert indlæg og dets vedhæftede filer og udtrukne elementer har et entydigt **ConversationId**. Hvis der er efterfølgende samlinger eller nye svar fra det samme indlæg, vil de delta-afskrifter, der fremkommer ved disse samlinger, også have det samme **ConversationId**.|
||||

Brug **kontrolelementet Gruppe** i kommandolinjen i et korrektursæt for at få vist Teams indhold grupperet efter familie eller samtale.

![Gruppekontrolelement på kommandolinjen.](..\media\TeamsGroupControl.png)

- Vælg **Vedhæftede gruppefamilier for** at få Teams indhold grupperet efter familie. Hver afskriftsfil vises på en linje på listen over korrektursætelementer. Vedhæftede filer er indlejret under elementet.

- Vælg **Gruppeindhold Teams eller Yammer for at** få vist Teams indhold grupperet efter samtale. Hver samtale vises på en linje på listen over gennemsynssætelementer. Afskriftsfiler og vedhæftede filer er indlejret under samtalen på øverste niveau.

> [!NOTE]
> Vedhæftede skybaserede filer grupperes med de samtaler, de vises i. Denne gruppering opnås ved at tildele det samme **FamilyId** som afskriftsfilen for den meddelelse, filen blev vedhæftet, og det samme **ConversationId** som den samtale, meddelelsen blev vist i. Det betyder, at der kan føjes flere kopier af vedhæftede filer fra skyen til korrektursættet, hvis de var knyttet til forskellige samtaler.

#### <a name="viewing-transcript-files-for-conversations"></a>Få vist afskriftsfiler til samtaler

Når du får vist udskriftsfiler i et korrektursæt, er nogle af meddelelserne fremhævet med lilla. De meddelelser, der fremhæves, afhænger af, hvilken kopi af afskriften, der anvendes af den afskrift, du får vist. I en 1:1-chat mellem Bruger4 og Bruger2 er meddelelserne fra Bruger4 f.eks. fremhævet med lilla, når du får vist den afskrift, der er indsamlet fra bruger4's postkasse. Når du får vist bruger2's afskrift af den samme samtale, fremhæves meddelelser, der er skrevet af Bruger2, med lilla. Denne fremhævning er baseret på den samme Teams klientoplevelse, hvor en brugers indlæg er fremhævet med lilla i Teams klient.

Følgende skærmbilleder viser et eksempel på en samtale i Teams-klienten og afskriftsfilen for den samme samtale i korrektursættet. Den lilla fremhævning i afskriftsfilen angiver, at afskriften blev indsamlet fra bruger2's postkasse.

##### <a name="conversation-in-teams-client"></a>Samtale i Teams klient

![Samtale vist i afskriftsfilen i korrektursættet.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Samtale i afskriftsfil

![Den samme samtale, der vises Teams klienten.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Afskrift af samtaletråde

Funktionalitet til samtaletråde i det nye sagsformat i Advanced eDiscovery hjælper dig med at identificere kontekstafhængigt indhold, der er relateret til elementer, som kan være relevante for din undersøgelse. Denne funktion frembringer særskilte samtalevisninger, der omfatter chatmeddelelser, der kommer før og følger elementerne, svarer til søgeforespørgslen under samlingen. Denne funktion giver dig mulighed for effektivt og hurtigt at gennemgå komplette chatsamtaler (kaldet samtaler med *tråde*) Microsoft Teams. Som beskrevet tidligere genoprettes chatsamtaler i HTML-afskriftsfiler, når Advanced eDiscovery tilføjer Teams indhold i et korrektursæt.

Her er den logik, der bruges af Advanced eDiscovery til at medtage yderligere meddelelser og svarafskriftsfiler, der giver kontekst omkring elementerne, der svarer til den samlingsforespørgsel (kaldet svarsvar *), du* brugte ved indsamling af Teams indhold. Forskellige trådfunktionsmåder er baseret på chattyperne og den søgeforespørgsel, der bruges til at indsamle svarpunkter. Der er to almindelige samlingsscenarier:

- Forespørgsler, der bruger søgeparametre, f.eks. nøgleord og egenskab:værdi-par

- Forespørgsler, der kun bruger datointervaller

| Teams indholdstype|Forespørgsler med søgeparametre  |Forespørgsler med datointervaller  |
|:---------|:---------|:---------|
|Teams 1:1 og gruppechats   |Meddelelser, der blev sendt 12 timer før og 12 timer efter, at dynamiske elementer er grupperet med svartidselementet i en enkelt afskriftsfil.   |Meddelelser i et 24-timers vindue grupperes i en enkelt afskriftsfil.|
|Teams og private kanalchats    |Hvert indlæg, der indeholder svarsvar og alle tilsvarende svar, grupperes i en enkelt afskriftsfil. |Hvert indlæg, der indeholder svarsvar og alle tilsvarende svar, grupperes i en enkelt afskriftsfil.|
||||

### <a name="deduplication-of-teams-content"></a>Deduplikering af Teams indhold

Følgende liste beskriver funktionsmåden for deduplikering (og duplikering), når du Teams indholdet i et korrektursæt.

- Hver afskriftsfil, der føjes til et korrektursæt, skal være en en til en-tilknytning til indhold, der er gemt på dataplaceringer. Det betyder Advanced eDiscovery indsamler ikke nogen oplysninger Teams, der allerede er blevet føjet til gennemsynssættet. Hvis en chatmeddelelse allerede er indsamlet i et gennemsynssæt, tilføjer Advanced eDiscovery ikke den samme meddelelse fra den samme dataplacering til gennemsynssættet i efterfølgende samlinger.

- Ved 1:1- og gruppechats gemmes kopier af meddelelser i hver samtaledeltagers postkasse. Kopier af den samme samtale, der findes i forskellige deltageres postkasser, indsamles med forskellige metadata. Som resultat behandles hver forekomst af samtalen som entydig og ført ind i gennemsynssættet i separate afskriftsfiler. Så hvis alle deltagere i en 1:1- eller gruppechat tilføjes som personer, der bruger programmet, og er medtaget i omfanget af en samling, føjes kopier af hver udskrift (for den samme modtager) til korrektursættet og grupperes sammen med det samme **ConversationId**. Hver af disse kopier er knyttet til en tilsvarende udvisker. **Tip**: Kolonnen **til kontrolvurderingen** på listen over korrektursæt identificerer den relevante vismand for den tilsvarende afskriftsfil.

- I efterfølgende samlinger af elementer fra den samme samtale føjes kun det deltaindhold, der ikke tidligere blev indsamlet tidligere, til korrektursættet og grupperes (ved at dele det samme **ConversationId**) med de tidligere indsamlede udskrifter fra den samme samtale. Her er et eksempel på denne funktionsmåde:

   1. Samling A indsamler meddelelser i en samtale mellem Bruger1 og Bruger2 og tilføjes for at gennemse sættet.

   2. Samling B indsamler meddelelser fra den samme samtale, men der er nye meddelelser mellem Bruger1 og Bruger2, siden Samling A blev kørt.

   3. Kun de nye meddelelser i Samling B føjes til korrektursættet. Disse meddelelser føjes til en separat afskriftsfil, men den nye afskrift grupperes med afskrifterne fra Samling A efter det samme **ConversationId**.

   Denne funktionsmåde gælder for alle typer af Teams chatsamtaler.

### <a name="metadata-for-teams-content"></a>Metadata for Teams indhold

I store korrektursæt med tusindvis eller millioner af elementer kan det være svært at begrænse omfanget af din gennemgang til at Teams indhold. For at hjælpe dig med at fokusere din gennemgang Teams indhold, er der metadataegenskaber, der er specifikke for Teams indhold. Du kan bruge disse egenskaber til at organisere kolonnerne på listen over gennemse [](review-set-search.md) og konfigurere filtre og forespørgsler for at optimere gennemgangen af Teams indhold. Disse metadataegenskaber er også inkluderet, når du eksporterer Teams indhold fra Advanced eDiscovery for at hjælpe dig med at organisere og få vist indhold efter eksport eller i eDiscovery-værktøjer fra tredjepart.

I følgende tabel beskrives metadataegenskaber for Teams indhold.

|Egenskaben Metadata  |Beskrivelse  |
|:---------|:---------|
|ContainsEditedMessage      | Angiver, om en afskriftsfil indeholder en redigeret meddelelse. Redigerede meddelelser identificeres ved visning af afskriftsfilen.|
|ConversationId|Et GUID, der identificerer den samtale, som elementet er knyttet til. Afskrift af filer og vedhæftede filer fra den samme samtale har den samme værdi for denne egenskab.|
|Samtalenavn     | Navnet på samtalen, som afskriftsfilen eller den vedhæftede fil er knyttet til. For Teams 1:1 og gruppechats er værdien af denne egenskab UPN for alle deltagere i samtalen. F.eks. `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams kanal- og private kanalchats skal bruge følgende format for samtalenavn: `<Team name>,<Channel name>`.F.eks. `eDiscovery vNext, General`.          |
|ConversationType     | Angiver typen af Teamchat. For Teams 1:1 og gruppechats er værdien for denne egenskab `Group`. For Teams kanal og private kanalchats er værdien `Channel`.|
|Dato | Tidsstemplet for den første meddelelse i udskriftsfilen.|
|FamilyId|Et GUID, der identificerer afskriftsfilen for en chatsamtale. Vedhæftede filer har samme værdi for denne egenskab som den afskriftsfil, der indeholder den meddelelse, som filen blev vedhæftet.|
|FileClass     |Angiver den pågældende type indhold. Elementer fra Teams chatsamtaler har værdien `Conversation`. I modsætning hertil Exchange mail har værdien `Email`.|          |
|MessageKind     | Egenskaben Meddelelsesegenskab. Teams indeholder værdien `microsoftteams , im`. |
|Modtagere     | En liste over alle brugere, der har modtaget en meddelelse i afskriftssamtalen.|
|TeamsChannelName     | Den Teams kanalnavn eller det private kanalnavn for afskriften.|
|||

Du kan finde beskrivelser Advanced eDiscovery af metadataegenskaber under [Felter til dokumentmetadata Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="export-teams-content"></a>Eksportere Teams indhold

Når du har gennemgået og Teams indholdet i et korrektursæt, kan du eksportere de afskriftsfiler, der indeholder indhold, som er dynamiske på din undersøgelse. Der er ikke nogen specifikke eksportindstillinger for Teams indhold. Hver afskriftsfil eksporteres som en HTML-meddelelsesfil. Denne fil indeholder også skjulte CDATA-koder med alle metadata for de enkelte chatmeddelelser. De metadataegenskaber, der er nævnt i forrige afsnit, medtages, Teams indholdet eksporteres.  

Der refereres til hver afskriftsfil i indlæsningsfilen og kan placeres ved hjælp af den relative sti Export_native_path feltet i indlæsningsfilen. Afskriftsfiler er placeret i mappen Samtaler i rodeksportmappen.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Tips til visning Teams indhold i et korrektursæt

Her er nogle tip og bedste fremgangsmåder til visning Teams indhold i et korrektursæt.

- Brug **kontrolelementet Tilpas kolonner** på kommandolinjen til at tilføje og organisere kolonner for at optimere gennemgangen af Teams indhold.

  ![Brug pop op-siden Rediger kolonne til at tilføje, fjerne og organisere kolonner.](..\media\EditReviewSetColumns.png)

   Du kan tilføje og fjerne kolonner, der er nyttige ved Teams indhold. Du kan også rækkefølgen af kolonner ved at trække og slippe dem på pop **op-siden** Rediger kolonne. Du kan også sortere efter kolonner for at gruppere Teams indhold med lignende værdier for den kolonne, du sorterer på.

- Nyttige kolonner, der kan hjælpe dig med Teams gennemgå indholdet, omfatter **Arkiver****, Modtagere** **og Filtype eller** **Meddelelsestype**.

- Brug [filtre](review-set-search.md) til Teams egenskaber til hurtigt at få vist Teams indhold. Der er filtre for de fleste af de metadataegenskaber, der er beskrevet i forrige afsnit.

## <a name="reference-guide"></a>Referencevejledning

Her er en oversigtsvejledning til brug af Advanced eDiscovery til Microsoft Teams. Denne vejledning opsummerer nøglepunkterne for brug Advanced eDiscovery at bevare, indsamle, gennemse og eksportere indhold fra Microsoft Teams.

![Miniaturebillede af referencevejledning til brug Advanced eDiscovery til Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Download som en PDF-fil](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
