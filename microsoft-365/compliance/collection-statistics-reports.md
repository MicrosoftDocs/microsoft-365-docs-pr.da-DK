---
title: Indsamlingsstatistik og -rapporter
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: nickrob
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du får adgang til og bruger statistikker og rapporter til kladdesamlinger og samlinger, der er blevet bekræftet til en gennemgang, der er angivet i Microsoft Purview eDiscovery (Premium).
ms.openlocfilehash: 1f9047a047e5c2c4abd01f0cac39ab6cb97e27da
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626837"
---
# <a name="collection-statistics-and-reports-in-microsoft-purview-ediscovery-premium"></a>Indsamlingsstatistik og -rapporter i Microsoft Purview eDiscovery (Premium)

Når du har oprettet en kladdesamling, kan du få vist statistikker over de hentede elementer, f.eks. de indholdsplaceringer, der indeholder de fleste elementer, der opfylder søgekriterierne, og antallet af elementer, der returneres af søgeforespørgslen. Du kan også få vist et undersæt af resultaterne.

Når du har identificeret det sæt dokumenter, du vil undersøge nærmere, kan du føje søgeresultaterne til et korrektursæt for at indsamle og behandle dem.

## <a name="statistics-and-reports-for-draft-collections"></a>Statistik og rapporter for kladdesamlinger

I dette afsnit beskrives de statistikker, der er tilgængelige for kladdesamlinger. Disse statistikker er tilgængelige under fanen **Søg efter statistik** på pop op-siden i en kladdesamling.

### <a name="collection-estimates"></a>Samlingsestimater

I dette afsnit vises en grafisk oversigt over de anslåede elementer, der returneres af samlingen. Dette angiver antallet af elementer, der opfylder søgekriterierne i samlingen. Disse oplysninger giver dig en idé om det anslåede antal elementer, der returneres af samlingen.

![Indsamlingsestimater for en kladdesamling.](../media/AeDCollectionEstimates.png)

- **Anslåede varer efter lokationer**: Det samlede antal anslåede varer, der returneres af samlingen. Det specifikke antal elementer, der er placeret i postkasser og placeret på websteder, vises også.

- **Anslåede placeringer med forekomster**: Det samlede antal indholdsplaceringer, der indeholder elementer, der returneres af samlingen. Det specifikke antal postkasser og webstedsplaceringer vises også.

- **Datamængde efter placering (i MB)**: Den samlede størrelse af alle anslåede elementer, der returneres af samlingen. Den specifikke størrelse af postkasseelementer og webstedselementer vises også.

### <a name="condition-report"></a>Betingelsesrapport

I dette afsnit vises statistik om søgeforespørgslen for samlingen og antallet af anslåede elementer, der matcher forskellige dele af søgeforespørgslen. Du kan bruge disse statistikker til at analysere antallet af elementer, der stemmer overens med hver komponent i søgeforespørgslen. Dette kan hjælpe dig med at tilpasse søgekriterierne for samlingen og om nødvendigt indsnævre omfanget af samlingen.

- **Placeringstype**: Den type indholdsplacering, som forespørgselsstatistikken gælder for. Værdien af **Exchange** angiver en postkasses placering. en værdi i **SharePoint** angiver en webstedsplacering.

- **Del**: Den del af søgeforespørgslen, som statistikkerne gælder for. **Primary** angiver hele søgeforespørgslen. **Nøgleordet** angiver, at statistikkerne i rækken er for et bestemt nøgleord. Hvis du bruger en nøgleordsliste til søgeforespørgslen i samlingen, medtages statistik for hver komponent i forespørgslen i denne tabel.

- **Betingelse**: Den faktiske komponent (nøgleord eller betingelse) for den søgeforespørgsel, der blev kørt for den kladdesamling, der returnerede de statistikker, der vises i den tilsvarende række.

- **Placeringer med forekomster**: Antallet af indholdsplaceringer (angivet af kolonnen **Placeringstype** ), der indeholder elementer, der svarer til den primære forespørgsel eller nøgleordsforespørgsel, der er angivet i kolonnen **Betingelse** .

- **Elementer**: Det antal elementer (fra den angivne indholdsplacering), der svarer til den forespørgsel, der er angivet i kolonnen **Betingelse** . Hvis et element indeholder flere forekomster af et nøgleord, der søges efter, tælles det som tidligere forklaret kun én gang i denne kolonne.

- **Størrelse (MB)**: Den samlede størrelse af alle elementer, der blev fundet (på den angivne indholdsplacering), som svarer til søgeforespørgslen i kolonnen **Betingelse** .

### <a name="top-locations"></a>Topplaceringer

I dette afsnit vises statistik om de specifikke indholdsplaceringer med de fleste elementer, der returneres af samlingen.

- Navnet på placeringen (mailadressen på postkasser og URL-adressen til websteder).

- Placeringstype (en postkasse eller et websted).

- Anslået antal elementer på indholdsplaceringen, der returneres af samlingen.

- Den samlede størrelse af anslåede elementer på hver indholdsplacering.

## <a name="statistics-and-reports-for-committed-collections"></a>Statistik og rapporter for bekræftede samlinger

I dette afsnit beskrives de statistikker, der er tilgængelige, når du har bekræftet en samling til et korrektursæt, herunder det faktiske antal elementer, der er føjet til korrektursættet. Disse statistikker (ud over at indlæse sætoplysninger) indeholder historiske oplysninger om indhold, der er føjet til en sag.

Når du har bekræftet en samling til et korrektursæt, vises følgende faner på pop op-siden for den bekræftede forbindelse. Hver af disse faner indeholder forskellige typer oplysninger om samlingen.

![Faner på pop op-siden med bindende samling.](../media/CommittedCollectionFlyoutPage.png)

### <a name="collection-contents"></a>Indhold i samling

Dette afsnit under fanen **Oversigt** indeholder statistik og andre oplysninger om de elementer, der blev indsamlet fra datakilderne i samlingen og føjet til korrektursættet.

- **Udtrukne elementer i alt**. Det samlede antal elementer, der er føjet til korrektursættet. Dette tal angiver summen af overordnede elementer og underordnede elementer, der er føjet til korrektursættet.

  > [!TIP]
  > Hold markøren over de overordnede eller underordnede elementlinjer for at få vist det samlede antal overordnede eller underordnede elementer.

- **Overordnede elementer**. Det antal elementer, der blev returneret af samlingen, som blev brugt til at indsamle de elementer, der blev føjet til korrektursættet. Dette tal svarer til (og er lig med) det anslåede antal elementer, der vises i afsnittet **Samlingsparametre** . Det antal overordnede elementer, han indsamler oplysninger om, som blev brugt til at indsamle de elementer, der blev føjet til korrektursættet.
 
   Et overordnet element kan indeholde flere underordnede elementer. En mail er f.eks. et overordnet element, hvis den indeholder en vedhæftet fil eller har en vedhæftet fil i skyen. I dette tilfælde betragtes den vedhæftede fil eller destinationsfilen for den vedhæftede fil i skyen som et underordnet element. Når du bekræfter en samling, føjes overordnede elementer og tilsvarende underordnede elementer (f.eks. vedhæftede filer og vedhæftede filer i skyen) til korrektursættet som individuelle elementer eller filer.

- **Underordnede elementer**. Det antal underordnede elementer, der er føjet til korrektursættet. Det er kun underordnede elementer, der er vedhæftede filer og vedhæftede filer i skyen, der føjes til korrektursættet som individuelle filer. Andre typer underordnede elementer, f.eks. mailsignaturer og billeder, udtrækkes fra et overordnet element og behandles derefter af OCR (Optical Character Recognition) for at udtrække tekst fra det underordnede element. Tekst, der udtrækkes fra disse typer underordnede elementer, føjes derefter til det overordnede element, så du kan se det i korrektursættet. Ved ikke at føje underordnede elementer til korrektursættet som en separat fil hjælper eDiscovery (Premium) med at strømline korrekturprocessen ved at begrænse antallet af potentielt immaterial elementer i korrektursættet.

- **Entydige elementer**. Antallet af entydige elementer, der er føjet til korrektursættet. Entydige elementer er entydige for korrektursættet. Alle elementer er entydige, når den første samling føjes til et nyt korrektursæt, fordi der ikke var nogen tidligere elementer i korrektursættet.

- **Identificerede dubletelementer**. Antallet af elementer fra samlingen, der ikke blev føjet til korrektursættet, fordi det samme element allerede findes i korrektursættet. Statistikker om dubletelementer kan hjælpe med at forklare forskellene mellem antallet af anslåede elementer fra en kladdesamling og det faktiske antal elementer, der er føjet til korrektursættet.

### <a name="indexing"></a>Indeksering

Afsnittet **Indeksering** under fanen **Oversigt** i et bekræftet korrektursæt indeholder indekseringsoplysninger om de elementer, der er føjet til korrektursættet.

**Nye indekserede elementer**. Det antal elementer, der for nylig blev indekseret, før de blev føjet til korrektursættet. Eksempler på et nyligt indekseret element er underordnede elementer, der er udtrukket fra et overordnet element og derefter indekseret, før de føjes til korrektursættet. Desuden indekseres elementer, der ikke er placeret i datakilder med frihedsberøvelse, og placeringer med indhold, der ikke er frihedsberøvende, på fanen **Datakilder** , før de føjes til gennemsynet. Nyligt indekserede elementer omfatter f.eks. elementer, der indsamles fra yderligere placeringer.

**Opdaterede indekserede elementer**. Antallet af delvist indekserede elementer, der blev indekseret og føjet til gennemsynssættet. Denne statistik angiver de delvist indekserede elementer fra placeringerne med frihedsberøvende og ikke-frihedsberøvende indhold Fanen **Datakilder** , der blev indekseret korrekt, da samlingen blev bekræftet til gennemsynssættet.

**Indekseringsfejl**. Antallet af delvist indekserede elementer, der ikke kunne indekseres, før de blev føjet til korrektursættet. Disse elementer kan kræve fejlafhjælpning.

### <a name="collection-parameters"></a>Samlingsparametre

I dette afsnit vises de samlingsoplysninger, der blev brugt til at indsamle de elementer, der blev føjet til korrektursættet. Under denne fane vises oplysninger, der ligner oplysningerne under fanen **Søg efter statistik** . Dette afsnit indeholder et hurtigt øjebliksbillede af den søgeforespørgsel, der bruges af samlingen, de indholdsplaceringer, der blev søgt efter, og de anslåede resultater af samlingen. Som tidligere forklaret, vil antallet af anslåede elementer i dette afsnit svare til antallet af overordnede elementer, der vises i afsnittet **Samlingsindhold** .

### <a name="search-statistics-tab"></a>Fanen Søg efter statistik

De statistikker, der vises under fanen **Søg efter statistik** , er de samme statistikker fra sidste gang, der blev kørt en kladdesamling. Dette omfatter estimater for samlinger, betingelsesrapport og øverste placeringer. Disse oplysninger bevares fra kladdesamlingen til historisk reference og kan sammenlignes med den faktiske samling, der blev bekræftet i korrektursættet.

## <a name="differences-between-draft-collection-estimates-and-the-actual-committed-collection"></a>Forskelle mellem udkast til indsamlingsestimater og den faktiske bekræftede samling

Når du kører en kladdesamling, vises et estimat over antallet af elementer (og deres samlede størrelse), der opfylder indsamlingskriterierne, under fanen **Oversigt** og afsnittet **Estimater for samling** under fanen **Søg efter statistik** . Når du har bekræftet en kladde af en samling til et korrektursæt, er det faktiske antal elementer (og deres samlede størrelse), der er tilføjet korrektursættet, ofte forskellige fra estimaterne. I de fleste tilfælde føjes der flere elementer til korrektursættet, end det blev anslået fra kladdesamlingen. På følgende liste beskrives de mest almindelige årsager til disse forskelle og tip til identifikation af dem:

- **Underordnede elementer**. Underordnede elementer (f.eks. vedhæftede filer og vedhæftede filer i skyen), der udpakkes fra deres overordnede elementer og tilføjes som individuelle filer. Antallet af underordnede elementer kan øge antallet af elementer, der faktisk føjes til korrektursættet. Generelt skal antallet af overordnede elementer, der er identificeret i afsnittet **Samlingsindhold** under fanen **Oversigt** for en bekræftet samling, svare til antallet af anslåede elementer fra kladdesamlingen.

- **Dupliker elementer**. Elementer fra kladdesamlingen, der allerede er føjet til korrektursættet i en tidligere samling, tilføjes ikke. Som tidligere forklaret vises antallet af dubletelementer i samlingen i afsnittet **Indhold af samling** under fanen **Oversigt** .

- **Konfigurationsindstillinger for samling**. Når du overfører en kladdesamling til et korrektursæt, skal du vælge at inkludere samtaletråde, vedhæftede filer i skyen og dokumentversioner. Alle disse elementer, der føjes til korrektursættet, medtages ikke i estimaterne for kladdesamlingen. De identificeres og indsamles kun, når du bekræfter samlingen. Hvis du vælger disse indstillinger, øges antallet af elementer, der føjes til korrektursættet, sandsynligvis. 

    Flere versioner af SharePoint-dokumenter er f.eks. ikke inkluderet i estimatet for kladdesamlingen. Men hvis du vælger indstillingen for at medtage alle dokumentversioner, når du sender en kladdesamling, øges det faktiske antal (og den samlede størrelse) af elementer, der er føjet til korrektursættet.

    Du kan få flere oplysninger om disse indstillinger under [Send en kladdesamling til et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set-in-ediscovery-premium).

Her er andre årsager til, at de anslåede resultater fra en kladdesamling kan være anderledes end de faktiske bekræftede resultater.

- **Den måde, resultaterne anslås på for kladdesamlinger**. Et estimat over de søgeresultater, der returneres af en kladdesamling, er netop det, et estimat (og ikke et faktisk antal) af de elementer, der opfylder kriterierne for indsamlingsforespørgslen. Hvis du vil kompilere estimatet for mailelementer, anmodes der om en liste over de meddelelses-id'er, der opfylder søgekriterierne, fra Exchange-databasen. Men når du sender samlingen til et korrektursæt, kører samlingen igen, og de faktiske meddelelser hentes fra Exchange-databasen. Der kan derfor opstå forskelle på grund af, hvordan det anslåede antal elementer og det faktiske antal elementer bestemmes.

- **Ændringer, der sker mellem det tidspunkt, hvor kladdesamlinger estimeres og bindes**. Når du sender en kladde af en samling til et gennemsynssæt, kører søgningen igen for at indsamle de nyeste elementer i søgeindekset, der opfylder søgekriterierne. Det er muligt, at der blev oprettet, sendt eller slettet flere elementer, der opfylder søgekriterierne i tiden mellem sidste kørsel af kladdesamlingen og det tidspunkt, hvor kladdesamlingen er sendt til et korrektursæt. Det er også muligt, at elementer, der var i søgeindekset, da resultaterne af kladdesamlingen blev anslået, ikke længere findes, fordi de blev fjernet fra en datakilde, før samlingen blev sendt. En måde at afhjælpe dette problem på er ved at angive et datointerval for en samling. En anden måde er at placere en venteposition på indholdsplaceringer, så elementer bevares og ikke kan fjernes.

- **Ikke-indekserede elementer**. Hvis kladdesamlingen inkluderede søgning i alle Exchange-postkasser eller alle SharePoint-websteder, føjes der kun ikke-indekserede elementer fra indholdsplaceringer, der indeholder elementer, der opfylder indsamlingskriterierne, til gennemsynssættet. Det vil sige, at hvis der ikke findes nogen resultater i en postkasse eller et websted, føjes alle ikke-indekserede elementer i den pågældende postkasse eller det pågældende websted ikke til korrektursættet. Ikke-indekserede elementer fra alle indholdsplaceringer (også dem, der ikke indeholder elementer, der stemmer overens med forespørgslen om samling), medtages i de anslåede samlingsresultater.

    Hvis kladdesamlingen inkluderede specifikke indholdsplaceringer (hvilket betyder, at bestemte postkasser eller websteder, hvor det er angivet på siden **Yderligere placeringer** i guiden kladdesamling), eksporteres ikke-indekserede elementer (som ikke er udelukket af indsamlingskriterierne) fra de indholdsplaceringer, der er angivet i søgningen. I dette tilfælde skal det anslåede antal ikke-indekserede elementer og antallet af ikke-indekserede elementer, der føjes til korrektursættet, være det samme.
