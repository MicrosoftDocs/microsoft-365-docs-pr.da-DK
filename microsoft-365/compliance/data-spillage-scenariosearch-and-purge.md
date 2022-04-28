---
title: eDiscovery-løsningsserie Dataspildscenarie – Søg og fjern
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Brug eDiscovery- og søgeværktøjer til at administrere og reagere på en dataspildhændelse i din organisation.
ms.openlocfilehash: 9be20d6c8eab99206a5510be6f21d3ca24114e0e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65086947"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>eDiscovery-løsningsserie: Dataspildscenarie – Søg og fjern

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

 **Hvad er dataspild, og hvorfor skal du pleje det?** Dataspild er, når et fortroligt dokument frigives i et miljø, der ikke er tillid til. Når der registreres en dataspildhændelse, er det vigtigt hurtigt at vurdere størrelsen og placeringen af spildet, undersøge brugeraktiviteterne omkring den og derefter fjerne de spildte data permanent fra systemet.
  
## <a name="data-spillage-scenario"></a>Dataspildscenarie

Du er leder af informationssikkerhedsofficeren hos Contoso. Du bliver informeret om en dataspildsituation, hvor en medarbejder ubevidst delte et meget fortroligt dokument med flere personer via mail. Du vil hurtigt vurdere, hvem der har modtaget dette dokument internt og eksternt. Når de er identificeret, vil du gerne dele resultaterne af sagen med andre efterforskere for at gennemse dem og derefter permanent fjerne dataene fra Office 365. Når undersøgelsen er fuldført, vil du generere en rapport med beviser for permanent fjernelse og andre sagsdetaljer til enhver fremtidig reference.
  
### <a name="scope-of-this-article"></a>Omfanget af denne artikel

Dette dokument indeholder en liste over instruktioner til, hvordan du permanent fjerner en meddelelse fra Microsoft 365, så den ikke er tilgængelig eller kan genoprettes. Hvis du vil slette en meddelelse og gøre den genoprettelig, indtil opbevaringsperioden for slettede elementer udløber, skal du se [Søg efter og slet mails i din organisation](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Arbejdsproces til administration af dataspildhændelser

Sådan administrerer du en dataspildhændelse:

![8-trinsarbejdsprocessen til administration af dataspildhændelser.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(Valgfrit) Trin 1: Administrer, hvem der kan få adgang til sagen, og angiv grænser for overholdelse af regler og standarder](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[Trin 2: Opret en eDiscovery-sag](#step-2-create-an-ediscovery-case)<br/>
[Trin 3: Søg efter de spildte data](#step-3-search-for-the-spilled-data)<br/>
[Trin 4: Gennemse og valider resultaterne af sagen](#step-4-review-and-validate-case-findings)<br/>
[Trin 5: Brug meddelelsessporingsloggen til at kontrollere, hvordan spildte data blev delt](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[Trin 6: Forbered postkasserne](#step-6-prepare-the-mailboxes)<br/>
[Trin 7: Slet de spildte data permanent](#step-7-permanently-delete-the-spilled-data)<br/>
[Trin 8: Kontrollér, angiv et bevis for sletning og overvågning](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Ting, du skal vide, før du starter

- Den arbejdsproces for dataspild, der er beskrevet i denne artikel, sletter ikke chatbeskeder i Microsoft Teams. Hvis du vil søge efter og slette Teams chatbeskeder, skal du se [Søg efter og fjern chatbeskeder i Teams](search-and-delete-Teams-chat-messages.md).

- Når en postkasse er i venteposition, forbliver en slettet meddelelse i mappen Gendanbare elementer, indtil opbevaringsperioden udløber, eller ventepositionen frigives. [Trin 6](#step-6-prepare-the-mailboxes) beskriver, hvordan du fjerner venteposition fra postkasserne. Kontakt datastyringen eller de juridiske afdelinger, før du fjerner ventepositionen. Din organisation kan have en politik, der definerer, om en postkasse i venteposition eller en dataspildhændelse har prioritet. 

- Hvis du vil styre, hvilke brugerpostkasser en dataspildsøger kan søge efter og administrere, hvem der kan få adgang til sagen, kan du konfigurere overholdelsesgrænser og oprette en brugerdefineret rollegruppe, som er beskrevet i [trin 1](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries). Hvis du vil gøre dette, skal du være medlem af rollegruppen Organisationsadministration eller tildeles rolleadministrationsrollen. Hvis du eller en administrator i din organisation allerede har angivet grænser for overholdelse af regler og standarder, kan du springe trin 1 over.

- Hvis du vil oprette en sag, skal du være medlem af rollegruppen eDiscovery Manager eller være medlem af en brugerdefineret rollegruppe, der har fået tildelt rollen Sagsstyring. Hvis du ikke er medlem, kan du bede en Microsoft 365 administrator [om at føje dig til rollegruppen eDiscovery-leder](assign-ediscovery-permissions.md).

- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af rollegruppen eDiscovery Manager eller tildeles rollen Styring af overholdelsessøgning. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen Organisationsadministration eller tildeles administrationsrollen Søg og fjern. Du kan finde oplysninger om, hvordan du føjer brugere til en rollegruppe, under [Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

- Hvis du vil søge i eDiscovery-aktiviteter i overvågningsloggen i trin 8, skal overvågning være aktiveret for din organisation. Du kan søge efter aktiviteter, der er udført inden for de sidste 90 dage. Hvis du vil vide mere om, hvordan du aktiverer og bruger overvågning, skal du se afsnittet [Overvågning af undersøgelsesprocessen for dataspild](#auditing-the-data-spillage-investigation-process) i Trin 8.

## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(Valgfrit) Trin 1: Administrer, hvem der kan få adgang til sagen, og angiv grænser for overholdelse af regler og standarder

Afhængigt af din organisations praksis skal du styre, hvem der kan få adgang til eDiscovery-sagen, der bruges til at undersøge en dataspildhændelse og konfigurere overholdelsesgrænser. Den nemmeste måde at gøre dette på er at tilføje efterforskere som medlemmer af en eksisterende rollegruppe på Microsoft Purview-overholdelsesportalen og derefter tilføje rollegruppen som medlem af eDiscovery-sagen. Du kan finde oplysninger om de indbyggede eDiscovery-rollegrupper, og hvordan du føjer medlemmer til en eDiscovery-sag, under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).
  
Du kan også oprette en ny rollegruppe, der opfylder organisationens behov. Det kan f.eks. være, at du gerne vil have, at en gruppe dataspildsøgere i organisationen får adgang til og samarbejder om alle dataspildsager. Det kan du gøre ved at oprette en rollegruppe af typen "Data Spillage Investigator", tildele de relevante roller (Eksport, RMS Decrypt, Review, Preview, Compliance Search og Case Management), føje dataspildetektiverne til rollegruppen og derefter tilføje rollegruppen som medlem af dataspillage-eDiscovery-sagen. Se [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser i Office 365](set-up-compliance-boundaries.md) for at få en detaljeret vejledning i, hvordan du gør dette. 
  
## <a name="step-2-create-an-ediscovery-case"></a>Trin 2: Opret en eDiscovery-sag

En eDiscovery-sag er en effektiv måde at administrere din undersøgelse af dataspild på. Du kan føje medlemmer til den rollegruppe, du oprettede i trin 1, tilføje rollegruppen som medlem af en ny eDiscovery-sag, udføre iterative søgninger for at finde de spildte data, eksportere en rapport til deling, spore status for sagen og derefter gå tilbage til detaljerne om sagen, hvis det er nødvendigt. Overvej at oprette en navngivningskonvention for eDiscovery-sager, der bruges til dataspildhændelser, og angiv så mange oplysninger, som du kan i sagsnavnet og beskrivelsen, så du kan finde og referere til i fremtiden, hvis det er nødvendigt.
  
Hvis du vil oprette en ny sag, kan du bruge eDiscovery i Security and Compliance Center. Se "Opret en ny sag" i [Kom i gang med eDiscovery (Standard).](get-started-core-ediscovery.md#step-3-create-a-ediscovery-standard-case)
  
## <a name="step-3-search-for-the-spilled-data"></a>Trin 3: Søg efter de spildte data

Nu, hvor du har oprettet en sag og administreret adgang, kan du bruge sagen til at søge iterativt for at finde de spildte data og identificere de postkasser, der indeholder de spildte data. Du skal bruge den samme søgeforespørgsel, som du brugte til at finde mailmeddelelserne, til at slette de samme meddelelser i [trin 7](#step-7-permanently-delete-the-spilled-data).
  
Hvis du vil oprette en indholdssøgning, der er knyttet til en eDiscovery-sag, skal du se [Søg efter indhold i en eDiscovery-sag (Standard).](search-for-content-in-core-ediscovery.md)
  
> [!IMPORTANT]
> De nøgleord, du bruger i søgeforespørgslen, kan indeholde de faktiske spildte data, du søger efter. Hvis du f.eks. søger efter dokumenter, der indeholder et CPR-nummer, og du bruger det som søgenøgleord, skal du slette forespørgslen bagefter for at undgå yderligere spild. Se [Sletning af søgeforespørgslen](#deleting-the-search-query) i trin 8.
  
## <a name="step-4-review-and-validate-case-findings"></a>Trin 4: Gennemse og valider resultaterne af sagen

Når du har oprettet en indholdssøgning, skal du gennemse og validere, at søgeresultaterne og kontrollere, at de kun består af de mails, der skal slettes. I en indholdssøgning kan du få vist et tilfældigt udsnit af 1.000 mails uden at eksportere søgeresultaterne for at undgå yderligere dataspild. Du kan læse mere om begrænsningerne i prøveversionen under [Grænser for indholdssøgning](limits-for-content-search.md).
  
Hvis du har mere end 1.000 postkasser eller mere end 100 mails pr. postkasse, der skal gennemses, kan du opdele den indledende søgning i flere søgninger ved hjælp af yderligere nøgleord eller betingelser, f.eks. datointerval eller afsender/modtager og gennemse resultaterne af hver søgning enkeltvis. Sørg for at notere alle de søgeforespørgsler, der skal bruges, når du sletter meddelelser i [trin 7](#step-7-permanently-delete-the-spilled-data), ned.

Når du finder en mail, der indeholder spildte data, skal du kontrollere modtagerne af meddelelsen for at finde ud af, om den blev delt eksternt. Hvis du vil spore en meddelelse yderligere, kan du indsamle afsenderoplysninger og datointervaller, så du kan bruge meddelelsessporingslogfilerne. Denne proces er beskrevet i [trin 5](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared).

Når du har bekræftet søgeresultaterne, kan du dele dine resultater med andre for at få en sekundær gennemgang. Personer, du har tildelt sagen i trin 1, kan gennemse sagsindholdet i både eDiscovery og Microsoft Purview eDiscovery (Premium) og godkende resultaterne af sagen. Du kan også generere en rapport uden at eksportere det faktiske indhold. Du kan også bruge den samme rapport som et bevis for sletning, som er beskrevet i [trin 8](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **Sådan opretter du en statistisk rapport:**
  
1. Gå til siden **Søg** i eDiscovery-sagen, og klik på den søgning, du vil oprette en rapport for. 
    
2. Klik på **Flere > Eksportér rapport** på pop op-siden.
 
      Siden Eksportér rapport vises.

    ![Vælg søgningen, og klik derefter på Flere > Eksportér rapport på pop op-siden.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. Vælg **Alle elementer, herunder elementer, der ikke genkendes, krypteres eller ikke er indekseret af andre årsager,** og klik derefter på **Generér rapport**.

4. I eDiscovery-sagen skal du klikke på **Eksportér** for at få vist listen over eksportjob. Du skal muligvis klikke på **Opdater** for at opdatere listen for at få vist det eksportjob, du har oprettet.

5. Klik på eksportjobbet, og klik derefter på **Download** rapport på pop op-siden.
 
    ![Klik på eksporten på siden Eksportér, og klik derefter på "Download rapport".](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Rapporten **Eksportoversigt** indeholder antallet af fundne placeringer med resultater og størrelsen af søgeresultaterne. Du kan bruge dette til at sammenligne med den rapport, der er genereret efter sletning, og angive som et bevis på sletning. **Resultatrapporten** indeholder en mere detaljeret oversigt over søgeresultaterne, herunder emne, afsender, modtagere, hvis mailen blev læst, datoer og størrelsen på hver meddelelse. Hvis nogle af oplysningerne i denne rapport indeholder de faktiske spildte data, skal du slette den Results.csv fil permanent, når undersøgelsen er fuldført.

Du kan finde flere oplysninger om eksport af rapporter under [Eksportér en rapport til indholdssøgning](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>Trin 5: Brug meddelelsessporingsloggen til at kontrollere, hvordan spildte data blev delt

Hvis du vil undersøge yderligere, om mail med spildte data blev delt, kan du eventuelt forespørge meddelelsessporingslogfilerne med afsenderoplysningerne og de datointervaloplysninger, du indsamlede i trin 4. Opbevaringsperioden for meddelelsessporing er 30 dage for data i realtid og 90 dage for historiske data.
  
Du kan bruge Meddelelsessporing i Security and Compliance Center eller bruge de tilsvarende cmdlet'er i Exchange Online PowerShell. Det er vigtigt at bemærke, at sporing af meddelelser ikke giver fuld garanti for, om de returnerede data er fuldstændige. Du kan finde flere oplysninger om brug af meddelelsessporing under: 
  
- [Meddelelsessporing i Security & Compliance Center](../security/office-365-security/message-trace-scc.md)
    
- [Ny meddelelsessporing i Security & Compliance Center](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>Trin 6: Forbered postkasserne

Når du har gennemset og valideret, at søgeresultaterne kun indeholder de meddelelser, der skal slettes, skal du indsamle en liste over mailadresserne på de berørte postkasser, der skal bruges i trin 7, når du sletter de spildte data. Du skal muligvis også forberede postkasserne, før du kan slette mails permanent, afhængigt af om genoprettelse af enkelte elementer er aktiveret på de postkasser, der indeholder de spildte data, eller om nogen af disse postkasser er i venteposition.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Hent en liste over adresser på postkasser med spildte data

Der er to måder at indsamle en liste over mailadresser på postkasser med spildte data på.

**Mulighed 1: Hent en liste over adresser på postkasser med spildte data**

1. Åbn eDiscovery-sagen, gå til siden **Søg** , og vælg den relevante indholdssøgning. 
    
2. Klik på **Vis resultater på pop op-siden**.
    
3. Klik på **Søgestatistik** på rullelisten **Individuelle resultater**.
    
4. Klik på **Øverste placeringer** på rullelisten **Type**.
    
    ![Hent en liste over postkasser, der indeholder søgeresultater, på siden Topplaceringer i søgestatistikken.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Der vises en liste over postkasser, der indeholder søgeresultater. Antallet af elementer i hver postkasse, der svarer til søgeforespørgslen, vises også.
    
5. Kopiér oplysningerne på listen, og gem dem i en fil, eller klik på **Download** for at downloade oplysningerne til en CSV-fil. 
    
**Mulighed 2: Hent postkasseplaceringer fra eksportrapporten**

Åbn rapporten Eksportoversigt, som du downloadede i [trin 4](#step-4-review-and-validate-case-findings). I den første kolonne i rapporten vises mailadressen for hver postkasse under **Placeringer**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Forbered postkasserne, så du kan slette de spildte data

Hvis genoprettelse af et enkelt element er aktiveret, eller hvis en postkasse er sat i venteposition, bevares en permanent slettet (slettet) meddelelse i mappen Gendanbare elementer. Så før du kan fjerne spildte data, skal du kontrollere de eksisterende postkassekonfigurationer og deaktivere gendannelse af enkelte elementer og fjerne enhver politik for bevarelse eller opbevaring. Vær opmærksom på, at du kan forberede én postkasse ad gangen og derefter køre den samme kommando på forskellige postkasser eller oprette et PowerShell-script for at forberede flere postkasser på samme tid.

- Se "Trin 1: Indsaml oplysninger om postkassen" i [Slet elementer i mappen Gendan elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) for at få oplysninger om, hvordan du kontrollerer, om genoprettelse af enkelte elementer er aktiveret, eller om postkassen er sat i venteposition, eller om den er tildelt en opbevaringspolitik. 

- Se "Trin 2: Forbered postkassen" i [Slet elementer i mappen Gendanbare elementer i skybaserede postkasser, der er i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) for at få oplysninger om deaktivering af gendannelse af enkelte elementer. 

- Se "Trin 3: Fjern alle ventepositioner fra postkassen" i [Mappen Slet elementer i mappen Gendanbare elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) for at få oplysninger om, hvordan du fjerner en venteposition eller opbevaringspolitik fra en postkasse. 

- Se "Trin 4: Fjern forsinkelsesventepositionen fra postkassen" i [Slet elementer i mappen Gendanbare elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) for at få oplysninger om, hvordan du fjerner den forsinkelsesposition, der er placeret i postkassen, når en hvilken som helst type venteposition er fjernet.

> [!IMPORTANT]
> Kontakt datastyringen eller de juridiske afdelinger, før du fjerner en politik for bevarelse eller bevarelse. Din organisation kan have en politik, der definerer, om en postkasse i venteposition eller en dataspildhændelse har prioritet. 
  
Sørg for at gendanne postkassen til tidligere konfigurationer, når du har kontrolleret, at de spildte data er blevet slettet permanent. Se detaljerne i [trin 7](#step-7-permanently-delete-the-spilled-data).

## <a name="step-7-permanently-delete-the-spilled-data"></a>Trin 7: Slet de spildte data permanent

Du kan nu slette de spildte data permanent ved hjælp af de postkasseplaceringer, du har indsamlet og forberedt i trin 6 og den søgeforespørgsel, der blev oprettet og tilpasset i trin 3, for at finde mails, der indeholder de spildte data.  Som tidligere forklaret skal du for at slette meddelelser være medlem af rollegruppen Organisationsadministration eller have tildelt rollen Administration af søgning og fjern administration. Du kan finde oplysninger om, hvordan du føjer brugere til en rollegruppe, under [Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

Hvis du vil slette de spildte meddelelser, skal du se [Søg efter og slet mails](search-for-and-delete-messages-in-your-organization.md).

Vær opmærksom på følgende grænser, når du sletter spildte data:

- Det maksimale antal postkasser i en søgning, som du kan bruge til at slette elementer ved at udføre en søge- og tømningshandling, er 50.000. Hvis den søgning, du opretter i trin 3, søger i mere end 50.000 postkasser, mislykkes sletningen. Søgning i mere end 50.000 postkasser i en enkelt søgning kan typisk ske, når du konfigurerer søgningen til at omfatte alle postkasser i din organisation. Denne begrænsning gælder stadig, selvom mindre end 50.000 postkasser indeholder elementer, der svarer til søgeforespørgslen.

- Der kan maksimalt fjernes 10 elementer pr. postkasse på én gang. Da funktionen til at søge efter og fjerne meddelelser er beregnet til at være et værktøj til svar på hændelser, hjælper denne grænse med at sikre, at meddelelser hurtigt fjernes fra postkasser. Denne funktion er ikke beregnet til at rydde op i brugerpostkasser.

> [!IMPORTANT]
> Mailelementer i et korrektursæt i en eDiscovery-sag (Premium) kan ikke slettes ved hjælp af procedurerne i denne artikel. Det skyldes, at elementer i et korrektursæt er kopier af elementer i livetjenesten, der kopieres og gemmes på en Azure Storage placering. Det betyder, at de ikke returneres af en indholdssøgning, som du opretter i trin 3. Hvis du vil slette elementer i et korrektursæt, skal du slette eDiscovery-sagen (Premium), der indeholder korrektursættet. Du kan finde flere oplysninger under [Luk eller slet en eDiscovery-sag (Premium).](close-or-delete-case.md)
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>Trin 8: Kontrollér, angiv et bevis for sletning og overvågning

Det sidste trin i arbejdsprocessen til at administrere en dataspildhændelse er at bekræfte, at de spildte data er blevet fjernet permanent fra postkassen ved at gå til eDiscovery-sagen og køre den samme søgeforespørgsel, der blev brugt til at slette disse data, for at bekræfte, at der ikke returneres nogen resultater. Når du har bekræftet, at de spildte data er blevet fjernet permanent, kan du eksportere en rapport og inkludere den (sammen med den oprindelige rapport) som et bevis på sletning. Derefter kan du [lukke sagen](close-reopen-delete-core-ediscovery-cases.md) , hvilket giver dig mulighed for at genåbne den, hvis du skal henvise til den i fremtiden. Derudover kan du også gendanne postkasser til deres tidligere tilstand, slette den søgeforespørgsel, der bruges til at finde de spildte data, og søge efter overvågningsposter for opgaver, der udføres, når du administrerer dataspildhændelsen.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Tilbagefør postkasserne til deres forrige tilstand

Hvis du har ændret konfigurationen af en postkasse i Trin 6 for at forberede postkasserne, før de data, der blev spildt, blev slettet, skal du gendanne dem til deres tidligere tilstand. Se "Trin 6: Genindlæs postkassen til dens forrige tilstand" i [Slet elementer i mappen Gendan elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state).
  
### <a name="deleting-the-search-query"></a>Sletter søgeforespørgslen

Hvis nøgleordene i den søgeforespørgsel, du oprettede og brugte i trin 3, indeholder nogle af alle de faktiske spildte data, skal du slette søgeforespørgslen for at forhindre yderligere dataspild.
  
1. Åbn eDiscovery-sagen i Sikkerheds- og overholdelsescenter, gå til siden **Søg** , og vælg den relevante indholdssøgning.

2. Klik på **Slet** på pop op-siden.

    ![Vælg søgningen, og klik derefter på Slet på pop op-siden.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Overvågning af undersøgelsesprocessen for dataspild

Du kan søge i overvågningsloggen efter de eDiscovery-aktiviteter, der blev udført under undersøgelsen. Du kan også søge i overvågningsloggen for at returnere overvågningsposterne for kommandoen **New-ComplianceSearchAction -Purge** , som du kørte i trin 7, for at slette de spildte data. Du kan finde flere oplysninger under:

- [Søgning i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md)

- [Søg efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md)
