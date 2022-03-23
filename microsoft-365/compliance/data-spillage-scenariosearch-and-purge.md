---
title: Scenarie for dataoverløb i eDiscovery-løsningsserier – Søg og tøm
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Brug eDiscovery og søgeværktøjer til at administrere og reagere på en dataoverløbshændelse i organisationen.
ms.openlocfilehash: 98dbb4ec36b7fb8166732aa855eefe3db6c5bbdc
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63587886"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>eDiscovery-løsningsserie: Scenarie med dataoverløb – Søg og tøm

 **Hvad er dataudløb, og hvorfor skal du være forsigtig?** Dataoverløb er, når et fortroligt dokument frigives til et upålideligt miljø. Når der registreres en hændelse med dataspild, er det vigtigt hurtigt at vurdere størrelsen og placeringen af overløbet, undersøge brugeraktiviteter omkring det og derefter slette overløbsdataene fra systemet permanent. 
  
## <a name="data-spillage-scenario"></a>Scenarie med dataudløb

Du er lead information security officer hos Contoso. Du er orienteret om en dataoverløbssituation, hvor en medarbejder ukendt har delt et meget fortroligt dokument med flere personer via mail. Du vil hurtigt vurdere, hvem der har modtaget dokumentet internt og eksternt. Når du har identificeret dem, vil du gerne dele case findings med andre brugere, så du kan gennemse dem, og derefter fjerne dataene Office 365. Når undersøgelsen er afsluttet, vil du oprette en rapport med beviserne for permanent fjernelse og andre sagsoplysninger til fremtidig brug.
  
### <a name="scope-of-this-article"></a>Denne artikels omfang

Dette dokument indeholder en liste over instruktioner om, hvordan du fjerner en meddelelse fra en Microsoft 365 så den ikke er tilgængelig eller kan gendannes. Hvis du vil slette en meddelelse og gøre den genoprettelig, indtil opbevaringsperioden for slettede elementer udløber, skal du se Søg [efter og slet mails i organisationen](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Arbejdsproces til administration af hændelser med overløb af data

Sådan administreres en dataoverløbshændelse:

![8-trins arbejdsproces til administration af hændelser med overløb af data.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(Valgfrit) Trin 1: Administrere, hvem der kan få adgang til sagen og angive overholdelsesgrænser](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[Trin 2: Opret en eDiscovery-sag](#step-2-create-an-ediscovery-case)<br/>
[Trin 3: Søg efter de oversatte data](#step-3-search-for-the-spilled-data)<br/>
[Trin 4: Gennemse og valider case findings](#step-4-review-and-validate-case-findings)<br/>
[Trin 5: Brug log over meddelelsessporing til at kontrollere, hvordan overspilte data blev delt](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[Trin 6: Klargør postkasserne](#step-6-prepare-the-mailboxes)<br/>
[Trin 7: Slet de overgåede data permanent](#step-7-permanently-delete-the-spilled-data)<br/>
[Trin 8: Bekræft, angiv en bekræftelse af sletning og overvågning](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Værd at vide, før du starter

- Når en postkasse er i venteposition, forbliver en slettet meddelelse i mappen Genoprettelige elementer, indtil opbevaringsperioden udløber, eller ventepositionen frigives. [Trin 6](#step-6-prepare-the-mailboxes) beskriver, hvordan du fjerner venteposition fra postkasserne. Kontakt din datastyring eller juridiske afdeling, før du fjerner ventepositionen. Din organisation har muligvis en politik, der definerer, om en postkasse i venteposition eller en dataudløbshændelse har forrang. 
    
- Hvis du vil styre, hvilke brugerpostkasser en dataoverløbspostkasse kan søge efter og administrere, hvem der kan få adgang til sagen, kan du konfigurere overholdelsesgrænser og oprette en brugerdefineret rollegruppe, som er beskrevet i trin [1](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries). For at gøre dette skal du være medlem af rollegruppen Organisationsadministration eller være tildelt rollestyringsrollen. Hvis du eller en administrator i organisationen allerede har angivet overholdelsesgrænser, kan du springe trin 1 over.
    
- Hvis du vil oprette en sag, skal du være medlem af rollegruppen eDiscovery Manager eller være medlem af en brugerdefineret rollegruppe, der er tildelt rollen som sagsadministration. Hvis du ikke er medlem, skal du bede Microsoft 365 administrator om at føje dig til [rollegruppen eDiscovery-leder](assign-ediscovery-permissions.md).
    
- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af rollegruppen eDiscovery Manager eller være tildelt rollen som styring af overholdelsessøgning. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen Organisationsadministration eller være tildelt administrationsrollen Søg og tøm. Du kan finde oplysninger om at føje brugere til en rollegruppe [under Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).
    
- Hvis du vil søge i overvågningsloggens eDiscovery-aktiviteter i trin 8, skal overvågning være aktiveret for din organisation. Du kan søge efter aktiviteter, der blev udført inden for de seneste 90 dage. Hvis du vil have mere at vide om, hvordan du aktiverer og bruger overvågning, skal du se afsnittet Overvågning af undersøgelsesprocessen for [dataudløb](#auditing-the-data-spillage-investigation-process) i trin 8. 
    
## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(Valgfrit) Trin 1: Administrere, hvem der kan få adgang til sagen og angive overholdelsesgrænser

Afhængigt af din virksomheds praksis skal du kontrollere, hvem der kan få adgang til eDiscovery-sagen, der bruges til at undersøge en dataoverløbshændelse og konfigurere overholdelsesgrænser. Den nemmeste måde at gøre dette på er at tilføje medlemmer som medlemmer af en eksisterende rollegruppe i Microsoft 365 Overholdelsescenter og derefter tilføje rollegruppen som medlem af eDiscovery-sagen. Du kan finde oplysninger om de indbyggede eDiscovery-rollegrupper, og hvordan du føjer medlemmer til en eDiscovery-sag, under Tildel [eDiscovery-tilladelser](assign-ediscovery-permissions.md).
  
Du kan også oprette en ny rollegruppe, der passer til dine organisationsbehov. Det kan f.eks. være, at du vil have en gruppe af dataudløb i organisationen til at få adgang til og samarbejde om alle dataudløbstilfælde. Det kan du gøre ved at oprette en rollegruppe for "Data Spillage Oversigt", tildele de relevante roller (Eksportér, RMS dekryptere, gennemse, forhåndsvisning, overholdelsessøgning og sagsstyring), føje dataoverløb til rollegruppen og derefter tilføje rollegruppen som medlem af eDiscovery-dataoverløbssagn. Se [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser i Office 365](set-up-compliance-boundaries.md) for detaljerede oplysninger om, hvordan du gør dette. 
  
## <a name="step-2-create-an-ediscovery-case"></a>Trin 2: Opret en eDiscovery-sag

En eDiscovery-sag er en effektiv måde at administrere undersøgelse af dataoverløb på. Du kan føje medlemmer til den rollegruppe, du oprettede i trin 1, tilføje rollegruppen som medlem af en ny eDiscovery-sag, udføre iterative søgninger for at finde de oversatte data, eksportere en rapport for at dele, spore status for sagen og derefter gå tilbage til detaljerne i sagen, hvis det er nødvendigt. Overvej at etablere en navngivningskonvention for eDiscovery-sager, der bruges til dataoverløbshændelser, og angiv så mange oplysninger som muligt i casenavnet og beskrivelsen, så du kan finde og henvise til i fremtiden, hvis det er nødvendigt.
  
Hvis du vil oprette en ny sag, kan du bruge eDiscovery i Security and Compliance Center. Se "Opret en ny sag" i [Introduktion til Core eDiscovery](get-started-core-ediscovery.md#step-3-create-a-core-ediscovery-case).
  
## <a name="step-3-search-for-the-spilled-data"></a>Trin 3: Søg efter de oversatte data

Nu hvor du har oprettet en sag og administreret adgang, kan du bruge sagen til at søge igen for at finde dataene, der er overdæmmet, og identificere de postkasser, der indeholder de overgåede data. Du skal bruge den samme søgeforespørgsel, som du brugte til at finde mails til at slette de samme meddelelser [i trin 7](#step-7-permanently-delete-the-spilled-data).
  
Hvis du vil oprette en indholdssøgning, der er knyttet til en eDiscovery-sag, skal du se Søge efter indhold [i en Core eDiscovery-sag](search-for-content-in-core-ediscovery.md).
  
> [!IMPORTANT]
> De nøgleord, du bruger i søgeforespørgslen, kan indeholde de faktiske oversatte data, du søger efter. Hvis du f.eks. søger efter dokumenter, der indeholder et CPR-nummer, og du bruger det som søgeord, skal du efterfølgende slette forespørgslen for at undgå yderligere overløb. Se [Slette søgeforespørgslen](#deleting-the-search-query) i trin 8.
  
## <a name="step-4-review-and-validate-case-findings"></a>Trin 4: Gennemse og valider case findings

Når du har oprettet en indholdssøgning, skal du gennemse og validere, at søgeresultaterne og kontrollere, at de kun består af de mails, der skal slettes. I en indholdssøgning kan du få vist et tilfældigt udvalg af 1.000 mails uden at eksportere søgeresultaterne for at undgå yderligere overløb af data. Du kan læse mere om begrænsningerne for eksempelvisning [under Begrænsninger for indholdssøgning](limits-for-content-search.md).
  
Hvis du har mere end 1.000 postkasser eller mere end 100 mails pr. postkasse, der skal gennemgås, kan du inddele den indledende søgning i flere søgninger ved hjælp af flere nøgleord eller betingelser, f.eks. datoområde eller afsender/modtager, og gennemse resultaterne af hver søgning enkeltvis. Husk at notere alle søgeforespørgsler til brug, når du sletter meddelelser i [trin 7](#step-7-permanently-delete-the-spilled-data).

Når du finder en mail, der indeholder overspilede data, skal du kontrollere modtagerne af meddelelsen for at finde ud af, om den blev delt eksternt. Hvis du vil spore en meddelelse yderligere, kan du indsamle afsenderoplysninger og datointervaller, så du kan bruge sporingslogfilerne for meddelelser. Denne proces er beskrevet i [trin 5](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared).

Når du har bekræftet søgeresultaterne, kan det være en god ide at dele dine resultater med andre i en sekundær gennemgang. Personer, som du tildelte til sagen i trin 1, kan gennemse sagsindholdet i både eDiscovery og Advanced eDiscovery godkende case-fund. Du kan også oprette en rapport uden at eksportere det faktiske indhold. Du kan også bruge denne rapport som en dokumentation for sletning, som er beskrevet i [trin 8](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **Sådan genereres en statistisk rapport:**
  
1. Gå til siden **Søg** i eDiscovery-sagen, og klik på den søgning, du vil oprette en rapport til. 
    
2. På pop op-siden skal du klikke **på Mere > Eksportér rapport**.
 
      Siden Eksportér rapport vises.

    ![Vælg søgningen, og klik derefter på Mere > Eksportér på pop op-siden.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. Markér **Alle elementer,** herunder elementer, der har ukendt format, er krypteret eller ikke blev indekseret af andre årsager, og klik derefter på **Generér rapport**.

4. I eDiscovery-sagen skal du klikke **på Eksportér** for at få vist listen over eksportjob. Du skal muligvis klikke på Opdater **for at** opdatere listen for at få vist det eksportjob, du har oprettet.

5. Klik på eksportjobbet, og klik derefter **på Hent** rapport på pop op-siden.
 
    ![På siden Eksportér skal du klikke på eksporten og derefter klikke på "Download rapport".](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Rapporten **Eksportoversigt** indeholder antallet af placeringer, der blev fundet med resultater og størrelsen af søgeresultaterne. Du kan bruge den til at sammenligne med den rapport, der genereres efter sletningen, og angive den som en bekræftelse på sletningen. **Resultatrapporten** indeholder en mere detaljeret oversigt over søgeresultaterne, herunder emne, afsender, modtagere, hvis mailen blev læst, datoer og størrelse for hver meddelelse. Hvis nogen af oplysningerne i denne rapport indeholder de faktiske overgåede data, skal du sørge for at slette filen Results.csv, når undersøgelsen er afsluttet.

Du kan finde flere oplysninger om at eksportere rapporter under [Eksportere en rapport til indholdssøgning](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>Trin 5: Brug log over meddelelsessporing til at kontrollere, hvordan overspilte data blev delt

Hvis du vil undersøge yderligere, om mail med data, der er overset, er blevet delt, kan du vælge at forespørge i meddelelsessporingslogfilerne med afsenderoplysningerne og de datoområdeoplysninger, du indsamlede i trin 4. Opbevaringsperioden for meddelelsessporing er 30 dage for realtidsdata og 90 dage for historiske data.
  
Du kan bruge Meddelelsessporing i sikkerheds- og overholdelsescenteret eller bruge de tilsvarende cmdlet'er Exchange Online PowerShell. Det er vigtigt at bemærke, at meddelelsessporing ikke giver fuld garanti for fuldstændigheden af de returnerede data. Du kan finde flere oplysninger om brug af meddelelsessporing i: 
  
- [Meddelelsessporing i Security & Compliance Center](../security/office-365-security/message-trace-scc.md)
    
- [Ny meddelelsessporing i Security & Compliance Center](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>Trin 6: Klargør postkasserne

Når du har gennemset og valideret, at søgeresultaterne kun indeholder de meddelelser, der skal slettes, skal du indsamle en liste over mailadresserne på de påsatte postkasser, som skal bruges i trin 7, når du sletter de oversatte data. Det kan også være nødvendigt at forberede postkasserne, før du kan slette mails permanent, afhængigt af om gendannelse af enkeltelement er aktiveret på de postkasser, der indeholder de overgåede data, eller hvis nogen af disse postkasser er sat i venteposition.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Få en liste over adresser på postkasser med overdædede data

Der er to måder at indsamle en liste over mailadresser på postkasser med overspilede data.

**Mulighed 1: Få en liste over adresser på postkasser med overspilede data**

1. Åbn eDiscovery-sagen, gå til siden **Søg,** og vælg den relevante indholdssøgning. 
    
2. Klik på Vis resultater på pop **op-siden**.
    
3. Klik på **Søgestatistik** på rullelisten **Individuelle resultater**.
    
4. Klik **på** Øverste placeringer på **rullelisten Type**.
    
    ![Få en liste over postkasser, der indeholder søgeresultater, på siden Øverste placeringer i søgestatistikken.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Der vises en liste over postkasser, der indeholder søgeresultater. Antallet af elementer i hver postkasse, der svarer til søgeforespørgslen, vises også.
    
5. Kopiér oplysningerne på listen, og gem dem i en fil, eller klik på **Download for** at hente oplysningerne til en CSV-fil. 
    
**Mulighed 2: Hent postkasseplaceringer fra eksportrapporten**

Åbn rapporten Eksportoversigt, som du hentede i [trin 4](#step-4-review-and-validate-case-findings). I den første kolonne i rapporten er mailadressen for hver postkasse angivet under **Placeringer**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Klargør postkasserne, så du kan slette de overgåede data

Hvis gendannelse af et enkelt element er aktiveret, eller hvis en postkasse er sat i venteposition, bevares en permanent slettet (slettet) meddelelse i mappen Genoprettelige elementer. Så før du kan fjerne oversatte data, skal du kontrollere de eksisterende postkassekonfigurationer og deaktivere gendannelse af enkeltelement og fjerne eventuelle ventepositions- eller opbevaringspolitik. Husk, at du kan forberede én postkasse ad gangen og derefter køre den samme kommando på forskellige postkasser eller oprette et PowerShell-script for at forberede flere postkasser på samme tid.

- Se "Trin 1: Indsaml oplysninger om postkassen" i mappen Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition [for at](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) få en vejledning til at kontrollere, om gendannelse af et enkelt element er aktiveret, eller om postkassen er sat i venteposition, eller om den er tildelt en opbevaringspolitik. 

- Se "Trin 2: Forbered postkassen" i Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition [for at](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) få en vejledning til deaktivering af gendannelse af et enkelt element. 

- Se "Trin 3: Fjern alle ventepositioner fra postkassen" i Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i [venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) for at få en vejledning til, hvordan du fjerner en venteposition eller opbevaringspolitik fra en postkasse. 

- Se "Trin 4: Fjern forsinkelsen fra postkassen" i Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition [for at](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) få en vejledning i at fjerne den forsinkelse, der er sat i venteposition i postkassen, når en hvilken som helst type venteposition er fjernet.

> [!IMPORTANT]
> Kontakt din datastyring eller juridiske afdeling, før du fjerner en ventepositions- eller opbevaringspolitik. Din organisation har muligvis en politik, der definerer, om en postkasse i venteposition eller en dataudløbshændelse har prioritet. 
  
Sørg for at gendanne postkassen til tidligere konfigurationer, når du har kontrolleret, at de overgåede data er blevet slettet permanent. Se oplysningerne i [trin 7](#step-7-permanently-delete-the-spilled-data).

## <a name="step-7-permanently-delete-the-spilled-data"></a>Trin 7: Slet de overgåede data permanent

Ved hjælp af de postkasseplaceringer, du indsamlede og forberedte i trin 6, og den søgeforespørgsel, der blev oprettet og finjusteret i trin 3, for at finde mails, der indeholder de overgåede data, kan du nu slette de overgåede data permanent.  Som tidligere nævnt skal du, for at slette meddelelser, være medlem af rollegruppen organisationsadministration eller have fået tildelt rollen søg og tømning. Du kan finde oplysninger om at føje brugere til en rollegruppe [under Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

Hvis du vil slette overgåede meddelelser, [skal du se Søg efter og slet mails](search-for-and-delete-messages-in-your-organization.md).

Husk følgende grænser, når du sletter oversatte data:

- Det maksimale antal postkasser i en søgning, som du kan bruge til at slette elementer ved at udføre en søgning og sletning, er 50.000. Hvis den søgning, du opretter i trin 3, søger i mere end 50.000 postkasser, mislykkes handlingen for tømning. Søgning i mere end 50.000 postkasser i en enkelt søgning kan typisk ske, når du konfigurerer søgningen til at medtage alle postkasser i organisationen. Denne begrænsning gælder stadig, selvom mindre end 50.000 postkasser indeholder elementer, der svarer til søgeforespørgslen.

- Der kan maksimalt fjernes 10 elementer pr. postkasse på én gang. Da muligheden for at søge efter og fjerne meddelelser er beregnet til at være et værktøj til hændelsesrespons, hjælper denne grænse med at sikre, at meddelelser hurtigt fjernes fra postkasser. Denne funktion er ikke beregnet til at rydde op i brugerpostkasser.

> [!IMPORTANT]
> Mailelementer i et gennemsynssæt i Advanced eDiscovery en sag kan ikke slettes ved hjælp af procedurerne i denne artikel. Det skyldes, at elementer i et gennemsynssæt er kopier af elementer i den live-tjeneste, der kopieres og gemmes på Azure Storage placering. Det betyder, at de ikke returneres af en indholdssøgning, som du opretter i trin 3. Hvis du vil slette elementer i et korrektursæt, skal du slette Advanced eDiscovery, der indeholder korrektursættet. Du kan få mere at vide [under Luk eller slet Advanced eDiscovery en sag](close-or-delete-case.md).
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>Trin 8: Bekræft, angiv en bekræftelse af sletning og overvågning

Det sidste trin i arbejdsprocessen til at administrere en dataoverløbshændelse er at bekræfte, at de overløbne data blev fjernet permanent fra postkassen ved at gå til eDiscovery-sagen og køre den samme søgeforespørgsel igen, som blev brugt til at slette disse data for at bekræfte, at der ikke returneres nogen resultater. Når du har bekræftet, at overgåede data er blevet fjernet permanent, kan du eksportere en rapport og medtage den (sammen med den oprindelige rapport) som en bekræftelse på sletningen. Derefter kan du [lukke sagen,](close-reopen-delete-core-ediscovery-cases.md) så du kan åbne den igen, hvis du er nødt til at henvise til den fremover. Desuden kan du også gendanne postkasser til deres tidligere tilstand, slette den søgeforespørgsel, der bruges til at finde de overløbsdata, og søge efter overvågningsposter for opgaver, der udføres, når du administrerer dataløbshændelsen.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Gendan postkasserne til deres tidligere tilstand

Hvis du har ændret en postkassekonfiguration i trin 6 for at forberede postkasserne, før de overgåede data blev slettet, skal du gendanne dem til deres tidligere tilstand. Se "Trin 6: Gendan postkassen til dens tidligere tilstand" i Slet elementer i mappen Genoprettelige elementer i skybaserede [postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state).
  
### <a name="deleting-the-search-query"></a>Slette søgeforespørgslen

Hvis nøgleordene i den søgeforespørgsel, du oprettede og brugte i trin 3, indeholder nogle af alle de faktiske overløbsdata, skal du slette søgeforespørgslen for at forhindre yderligere overløb af data.
  
1. I Security and Compliance Center skal du åbne eDiscovery-sagen, gå til siden **Søg** og vælge den relevante indholdssøgning.

2. Klik på Slet på pop **op-siden**.

    ![Vælg søgningen, og klik derefter på Slet på pop op-siden.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Overvågning af undersøgelsesprocessen for overløb af data

Du kan søge i overvågningsloggen efter de eDiscovery-aktiviteter, der blev udført under undersøgelsen. Du kan også søge i overvågningsloggen for at returnere overvågningsposterne for kommandoen **New-ComplianceSearchAction -Tøm** , som du kørte i trin 7 for at slette de overgåede data. Du kan finde flere oplysninger under:

- [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md)

- [Søg efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md)
