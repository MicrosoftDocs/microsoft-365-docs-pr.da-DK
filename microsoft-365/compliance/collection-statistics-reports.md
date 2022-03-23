---
title: Indsamling af statistik og rapporter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du får adgang til og bruger statistik og rapporter til kladdesamlinger og samlinger, der har været engageret i en gennemgang i Advanced eDiscovery.
ms.openlocfilehash: 4b5cf37639d497d615a0772e084507018cb829cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591972"
---
# <a name="collection-statistics-and-reports-in-advanced-ediscovery"></a>Indsamling af statistik og rapporter i Advanced eDiscovery

Når du har oprettet en kladdesamling, kan du få vist statistik for de hentede elementer, f.eks. de indholdsplaceringer, der indeholder de fleste elementer, der matcher søgekriterierne, og antallet af elementer, der returneres af søgeforespørgslen. Du kan også få vist et eksempel på et undersæt af resultaterne.

Når du har identificeret det sæt af dokumenter, du vil undersøge nærmere, kan du føje søgeresultaterne til et korrektursæt, der skal indsamles og behandles.

## <a name="statistics-and-reports-for-draft-collections"></a>Statistik og rapporter for kladdesamlinger

I dette afsnit beskrives den statistik, der er tilgængelig for kladdesamlinger. Disse statistikker er tilgængelige på **fanen Søgestatistik** på pop op-siden i en kladdesamling.

### <a name="collection-estimates"></a>Anslåede samlinger

I dette afsnit vises en grafisk oversigt over de anslåede elementer, der returneres af samlingen. Dette angiver antallet af elementer, der opfylder søgekriterierne for samlingen. Disse oplysninger giver dig en ide om det anslåede antal elementer, der returneres af samlingen.

![Anslåede samlinger for en kladdesamling.](../media/AeDCollectionEstimates.png)

- **Anslåede elementer efter placeringer**: Det samlede antal anslåede elementer, der returneres af samlingen. Det specifikke antal elementer, der er placeret i postkasser og placeret på websteder, vises også.

- **Anslåede placeringer med hits**: Det samlede antal indholdsplaceringer, der indeholder elementer, der returneres af samlingen. Det specifikke antal postkasser og webstedsplaceringer vises også.

- **Datamængde efter placering (i MB)**: Den samlede størrelse af alle anslåede elementer, der returneres af samlingen. Den specifikke størrelse på postkasseelementer og webstedselementer vises også.

### <a name="condition-report"></a>Betingelsesrapport

Dette afsnit viser statistik om søgeforespørgslen for samlingen og antallet af estimerede elementer, der matcher forskellige dele af søgeforespørgslen. Du kan bruge denne statistik til at analysere antallet af elementer, der svarer til hver komponent i søgeforespørgslen. Dette kan hjælpe dig med at afgrænse søgekriterierne for samlingen og, hvis det er nødvendigt, begrænse omfanget af samlingen.

- **Placeringstype**: Den type indholdsplacering, forespørgselsstatistikken gælder for. Værdien af en **Exchange** angiver en postkasseplacering; en værdi på **SharePoint** angiver en webstedsplacering.

- **Del**: Den del af søgeforespørgslen, statistikken gælder for. **Primær** angiver hele søgeforespørgslen. **Nøgleord** angiver, at statistikken i rækken er for et bestemt nøgleord. Hvis du bruger en liste med nøgleord, når du skal bruge søgeforespørgslen i samlingen, medtages statistik for hver komponent i forespørgslen i denne tabel.

- **Betingelse**: Den faktiske komponent (nøgleord eller betingelse) for søgeforespørgslen, der blev kørt for kladdesamlingen, som returnerede den statistik, der blev vist i den tilsvarende række.

- **Placeringer med hits**: Antallet af placeringer af indhold (angivet af kolonnen Placeringstype),  der indeholder elementer, der svarer til den primære forespørgsel eller nøgleordsforespørgslen, der er angivet i **kolonnen** Betingelse.

- **Elementer**: Antallet af elementer (fra den angivne indholdsplacering), der svarer til den forespørgsel, der er angivet i **kolonnen** Betingelse. Som tidligere nævnt tælles det kun én gang i denne kolonne, hvis et element indeholder flere forekomster af et nøgleord, der søges efter.

- **Størrelse (MB)**: Den samlede størrelse af alle de elementer, der blev fundet (på den angivne indholdsplacering), der svarer til søgeforespørgslen i **kolonnen** Betingelse.

### <a name="top-locations"></a>Vigtigste placeringer

Dette afsnit viser statistik om de specifikke indholdsplaceringer med de fleste elementer, der returneres af samlingen.

- Navnet på placeringens navn (mailadressen på postkasser og URL'en til websteder).

- Placeringstype (en postkasse eller et websted).

- Anslået antal elementer på den indholdsplacering, der returneres af samlingen.

- Den samlede størrelse af anslåede elementer for hver indholdsplacering.

## <a name="statistics-and-reports-for-committed-collections"></a>Statistik og rapporter for bindende samlinger

I dette afsnit beskrives den statistik, der er tilgængelig, når du har bekræftet en samling i et korrektursæt, herunder det faktiske antal elementer, der er føjet til korrektursættet. Disse statistikker (ud over oplysninger om indlæsningssæt) giver historiske oplysninger om indhold, der føjes til en sag.

Når du har bekræftet en samling i et korrektursæt, vises følgende faner på pop op-siden for bekræftet forbindelse. Hver af disse faner indeholder forskellige typer oplysninger om samlingen.

![Faner på pop op-siden til indsamling af tilsagn.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Indhold i samling

Denne sektion på fanen **Oversigt** indeholder statistik og andre oplysninger om de elementer, der blev indsamlet fra datakilderne i samlingen og føjet til gennemsynssættet.

- **Samlet udtrukne elementer**. Det samlede antal elementer føjet til korrektursættet. Dette tal angiver summen af overordnede elementer og underordnede elementer, der er føjet til korrektursættet.

  > [!TIP]
  > Hold markøren over de overordnede eller underordnede elementlinjer for at få vist det samlede antal overordnede eller underordnede elementer.

- **Overordnede elementer**. Antallet af elementer, der returneres af samlingen, der blev brugt til at indsamle de elementer, der blev føjet til gennemsynssættet. Dette tal svarer til (og er lig med) det anslåede antal elementer, der vises i **sektionen Samlingsparametre** . Antallet af overordnede elementer, han indsamler oplysninger om, der blev brugt til at indsamle de elementer, der blev føjet til gennemsynssættet.
 
   Et overordnet element kan indeholde flere underordnede elementer. En mail er f.eks. et overordnet element, hvis den indeholder en vedhæftet fil eller har en vedhæftet skyfil. I dette tilfælde anses den vedhæftede fil eller destinationsfilen for den vedhæftede skyfil for at være et underordnet element. Når du har bekræftet en samling, føjes overordnede elementer og tilsvarende underordnede elementer (f.eks. vedhæftede filer og skybaserede vedhæftede filer) til gennemsynssættet som individuelle elementer eller filer.

- **Underordnede elementer**. Antallet af underordnede elementer, der er føjet til korrektursættet. Kun underordnede elementer, der er vedhæftede filer og vedhæftede skyfiler, føjes til gennemsynssættet som individuelle filer. Andre typer underordnede elementer, f.eks. mailsignaturer og billeder, udtrækkes fra et overordnet element og behandles derefter af Optical Character Recognition (OCR) for at udtrække tekst fra det underordnede element. Tekst, der udtrækkes fra disse typer underordnede elementer, føjes derefter til det overordnede element, så du kan se det i korrektursættet. Når du ikke føjer underordnede elementer til korrektursættet som en separat fil, hjælper Advanced eDiscovery dig med at strømline gennemsynsprocessen ved at begrænse antallet af potentielt uønskede elementer i gennemsynssættet.

- **Unikke elementer**. Antallet af entydige elementer, der er føjet til gennemsynssættet. Unikke elementer er unikke for korrektursættet. Alle elementer er entydige, når den første samling føjes til et nyt korrektursæt, fordi der ikke var nogen tidligere elementer i korrektursættet.

- **Identificerede dublerede elementer**. Antallet af elementer fra samlingen, der ikke blev føjet til korrektursættet, fordi det samme element allerede findes i gennemsynssættet. Statistik om dublerede elementer kan hjælpe med at forklare forskellene mellem antallet af anslåede elementer fra en kladdesamling og det faktiske antal elementer, der er føjet til gennemsynssættet.

### <a name="indexing"></a>Indeksering

Afsnittet **Indeksering på** fanen Oversigt i **et** korrektursæt indeholder indekseringsoplysninger om de elementer, der er føjet til korrektursættet.

**Nye indekserede elementer**. Antallet af elementer, der blev indekseret for nylig, før de blev føjet til korrektursættet. Eksempler på et nyligt indekseret element er underordnede elementer, der er hentet fra et overordnet element og derefter indekseret, før de føjes til korrektursættet. Desuden indekseres elementer, der ikke er placeret i oversigter over datakilder og ikke-registrerede indholdsplaceringer,  der er angivet på fanen Datakilder i sagen, før de føjes til anmeldelsen. Eksempelvis vil nyligt indekserede elementer indeholde elementer, der er indsamlet fra yderligere placeringer.

**Indekserede elementer blev opdateret**. Antallet af delvist indekserede elementer, der blev indekseret og føjet til korrektursættet. Denne statistik angiver de delvist indekserede elementer fra fanen for ikke-tilladte **indholdskilder** Datakilder, der blev indekseret, da samlingen blev forpligtet til gennemsynssættet.

**Indekseringsfejl**. Antallet af delvist indekserede elementer, der ikke kunne indekseres, før de blev føjet til korrektursættet. Disse elementer kan kræve fejl afhjælpning.

### <a name="collection-parameters"></a>Samlingsparametre

I dette afsnit vises de samlingsoplysninger, der blev brugt til at indsamle de elementer, der blev føjet til gennemsynssættet. Denne fane viser oplysninger, der svarer til oplysningerne på **fanen Søgestatistik** . Dette afsnit indeholder et hurtigt billede af den søgeforespørgsel, der bruges af samlingen, de indholdsplaceringer, der blev søgt på, og de anslåede indsamlingsresultater. Som beskrevet tidligere vil antallet af anslåede elementer i denne sektion være lig med antallet af overordnede elementer, der vises i **sektionen Samlingsindhold** .

### <a name="search-statistics-tab"></a>Fanen Søgestatistik

Den statistik, der vises på **fanen Søgestatistik** , er den samme statistik fra sidste gang, der blev kørt en kladdesamling. Dette omfatter anslåede samlinger, betingelsesrapport og de øverste placeringer. Disse oplysninger bevares fra kladdesamlingen til historisk reference og kan sammenlignes med den faktiske samling, der blev forpligtet til gennemsynssættet.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Forskelle mellem estimater på kladdesamlinger og den faktiske bindende samling

Når du kører en kladdesamling, vises der et skøn over antallet af elementer (og deres samlede størrelse), der opfylder samlingskriterierne, på fanen Oversigt og  i sektionen Samlingerestimat på fanen Søgestatistik. Når du har bekræftet en kladdesamling i et korrektursæt, er det faktiske antal elementer (og deres samlede størrelse) tilføjet gennemsynssættet ofte forskellige fra overslagene. I de fleste tilfælde føjes flere elementer til korrektursættet, end det forventes af kladdesamlingen. Følgende liste beskriver de mest almindelige årsager til disse forskelle og tip til at identificere dem:

- **Underordnede elementer**. Underordnede elementer (f.eks. vedhæftede filer og vedhæftede skyfiler), der udtrækkes fra deres overordnede elementer og tilføjes som individuelle filer. Antallet af underordnede elementer kan øge antallet af elementer, der faktisk er føjet til korrektursættet. Generelt skal antallet af overordnede elementer identificeret i sektionen Samlingsindhold på fanen Oversigt  for en bindende samling være lig med antallet af anslåede elementer fra kladdesamlingen.

- **Dublerede elementer**. Elementer fra kladdesamlingen, der allerede er blevet føjet til korrektursættet i en tidligere samling, vil ikke blive tilføjet. Som tidligere nævnt vises antallet af dublerede elementer i samlingen i **sektionen Samlingsindhold** på **fanen** Oversigt.

- **Konfigurationsindstillinger for samling**. Når du har bekræftet en kladdesamling i et korrektursæt, har du mulighed for at medtage samtaletråde, vedhæftede skybaserede filer og dokumentversioner. Alle disse elementer, der er føjet til korrektursættet, medtages ikke i overslagene for kladdesamlingen. De identificeres og indsamles kun, når du har bekræftet samlingen. Hvis du vælger disse indstillinger, øges antallet af elementer, der føjes til korrektursættet, højst sandsynligt. 

    For eksempel medtages flere versioner SharePoint dokumenter ikke i estimatet for kladdesamlingen. Men hvis du vælger at medtage alle dokumentversioner, når du har bekræftet en kladdesamling, øges det faktiske antal (og samlede størrelse) elementer, der føjes til korrektursættet.

    Du kan finde flere oplysninger om disse indstillinger under [Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery). 

Her er andre årsager til, at de anslåede resultater fra en kladdesamling kan være anderledes end de faktiske bindende resultater.

- **Måden, hvorpå resultaterne estimeres for kladdesamlinger**. Et estimat af søgeresultaterne, der returneres af en kladdesamling, er netop det, et estimat (og ikke et faktisk antal) af de elementer, der opfylder kriterierne for samlingens forespørgsel. For at samle estimatet for mailelementer, anmodes der om en liste over de meddelelses-Exchange, der opfylder søgekriterierne. Men når du binder samlingen til et gennemsynssæt, køres samlingen igen, og de faktiske meddelelser hentes fra Exchange databasen. Der kan derfor være forskelle på grund af, hvordan det anslåede antal elementer og det faktiske antal elementer bestemmes.

- **Ændringer, der sker mellem tidspunktet for beregning og bekræftelse af kladdesamlinger**. Når du har bekræftet en kladdesamling i et gennemsynssæt, køres søgningen igen for at indsamle de seneste elementer i søgeindekset, der opfylder søgekriterierne. Det er muligt, at der er oprettet, sendt eller slettet yderligere elementer, der opfylder søgekriterierne i tiden mellem, hvornår kladdesamlingen sidst blev kørt, og hvornår kladdesamlingen er forpligtet til et gennemsynssæt. Det er også muligt, at elementer, der var i søgeindekset, da kladdesamlingsresultaterne blev anslået, ikke længere er der, fordi de blev slettet fra en datakilde, før samlingen blev bekræftet. En måde at afhjælpe dette problem på er at angive et datointerval for en samling. En anden måde er at placere en venteposition på indholdsplaceringer, så elementer bevares og ikke kan slettes.

- **Uindsiddedede elementer**. Hvis kladdesamlingen indeholdt søgning i alle Exchange-postkasser eller alle SharePoint-websteder, føjes kun uindsiderede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder samlingskriterierne, til korrektursættet. Med andre ord, hvis der ikke findes nogen resultater i en postkasse eller et websted, så føjes elementer, der ikke er inddæmt i den pågældende postkasse eller websted, ikke til korrektursættet. Dog medtages ikke-identificerede elementer fra alle indholdsplaceringer (også dem, der ikke indeholder elementer, der svarer til samlingsforespørgslen) i de anslåede indsamlingsresultater.

    Alternativt kan du, hvis kladdesamlingen indeholdt bestemte placeringer af indhold (hvilket betyder, at bestemte postkasser eller websteder, hvor det er angivet på siden Yderligere placeringer i guiden til kladdesamling), eksporteres uindsiderede elementer (der ikke er udeladt af samlingskriterierne) fra de **indholdsplaceringer** , der er angivet i søgningen. I dette tilfælde skal det anslåede antal ikke-xede elementer og antallet af ikke-xede elementer, der føjes til korrektursættet, være det samme.
