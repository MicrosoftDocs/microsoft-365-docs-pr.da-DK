---
title: Få vist statistik for eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.search: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du bruger funktionen søgestatistik til at vise statistik for indholdssøgninger og -søgninger, der er knyttet til en grundlæggende eDiscovery-sag Microsoft 365 Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 04d24020cd22d40d6706295ccb53578bf3aef756
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587514"
---
# <a name="view-statistics-for-ediscovery-search-results"></a>Få vist statistik for eDiscovery-søgeresultater

Når du har oprettet og kørt en indholdssøgning eller en søgning, der er knyttet til en core eDiscovery-sag, kan du få vist statistik for de anslåede søgeresultater. Dette omfatter en oversigt over søgeresultaterne (svarende til en oversigt over de anslåede søgeresultater, der vises på pop op-siden med søgninger), forespørgselsstatistik, f.eks. antallet af indholdsplaceringer med elementer, der svarer til søgeforespørgslen, og identiteten af indholdsplaceringer, der har de mest matchende elementer.
  
Desuden kan du bruge listen over nøgleord til at konfigurere en søgning til at returnere statistik for hvert nøgleord i en søgeforespørgsel. Det gør det muligt at sammenligne antallet af resultater, der returneres af hvert nøgleord i en forespørgsel.
  
Du kan også hente søgestatistik til en CSV-fil. Dette giver dig mulighed for at bruge filtrerings- og sorteringsfunktionerne i Excel til at sammenligne resultater og forberede rapporter til dine søgeresultater.
  
## <a name="get-statistics-for-searches"></a>Få statistik for søgninger

Sådan får du vist statistik for en indholdssøgning eller en søgning, der er knyttet til en core eDiscovery-sag:
  
1. Klik på Microsoft 365 Overholdelsescenter i **dialogboksen Vis** alle, og gør derefter et af følgende:

   - Klik **på Indholdssøgning** , og vælg derefter en søgning for at få vist pop op-siden.

     ELLER

   - Klik **på eDiscoveryCore** > , vælg en sag, og vælg derefter en søgning på  fanen Søgninger for at få vist pop op-siden.

2. Klik på fanen Søgestatistik på pop op-siden **for den valgte** søgning.
  
   ![Fanen Søg i statistik.](../media/SearchStatistics1.png)

Fanen **Søgestatistik** indeholder følgende afsnit, der indeholder forskellige typer statistik om søgningen.

### <a name="search-content"></a>Søg i indhold

I dette afsnit vises en grafisk oversigt over de anslåede elementer, der returneres af søgningen. Dette angiver antallet af elementer, der opfylder søgekriterierne. Disse oplysninger giver dig en ide om det anslåede antal elementer, der returneres af søgningen.

![Søgeestimimater for en søgning.](../media/SearchContentReport.png)

- **Anslåede elementer efter placeringer**: Det samlede antal anslåede elementer, der returneres af søgningen. Det specifikke antal elementer, der er placeret i postkasser og placeret på websteder, vises også.

- **Anslåede placeringer med hits**: Det samlede antal indholdsplaceringer, der indeholder elementer, der returneres af søgningen. Det specifikke antal postkasser og webstedsplaceringer vises også.

- **Datamængde efter placering (i MB)**: Den samlede størrelse af alle anslåede elementer, der returneres af søgningen. Den specifikke størrelse på postkasseelementer og webstedselementer vises også.

### <a name="condition-report"></a>Betingelsesrapport

Dette afsnit viser statistik om søgeforespørgslen og antallet af estimerede elementer, der matcher forskellige dele af søgeforespørgslen. Du kan bruge denne statistik til at analysere antallet af elementer, der svarer til hver komponent i søgeforespørgslen. Dette kan hjælpe dig med at afgrænse søgekriterierne og om nødvendigt indsnævre omfanget af området. Du kan også downloade en kopi af denne rapport i CSV-format.

![Betingelsesrapport.](../media/SearchContentReportNoKeywordList.png)

- **Placeringstype**: Den type indholdsplacering, forespørgselsstatistikken gælder for. Værdien af en **Exchange** angiver en postkasseplacering; en værdi på **SharePoint** angiver en webstedsplacering.

- **Del**: Den del af søgeforespørgslen, statistikken gælder for. **Primær** angiver hele søgeforespørgslen. **Nøgleord** angiver, at statistikken i rækken er for et bestemt nøgleord. Hvis du bruger en liste med nøgleord til søgeforespørgsel, medtages statistik for hver komponent i forespørgslen i denne tabel. Du kan finde flere oplysninger [i Få statistik for nøgleord for søgninger](#get-keyword-statistics-for-searches).

- **Betingelse**: Den faktiske komponent (nøgleordet eller betingelsen) for den søgeforespørgsel, der returnerede den statistik, der blev vist i den tilsvarende række.

- **Placeringer med hits**: Antallet af placeringer af indhold (angivet af kolonnen Placeringstype),  der indeholder elementer, der svarer til den primære forespørgsel eller nøgleordsforespørgslen, der er angivet i **kolonnen** Betingelse.

- **Elementer**: Antallet af elementer (fra den angivne indholdsplacering), der svarer til den forespørgsel, der er angivet i **kolonnen** Betingelse. Som tidligere nævnt tælles det kun én gang i denne kolonne, hvis et element indeholder flere forekomster af et nøgleord, der søges efter.

- **Størrelse (MB)**: Den samlede størrelse af alle de elementer, der blev fundet (på den angivne indholdsplacering), der svarer til søgeforespørgslen i **kolonnen** Betingelse.

### <a name="top-locations"></a>Vigtigste placeringer

Dette afsnit viser statistik om de specifikke placeringer af indhold med de fleste elementer, der returneres af søgningen. De øverste 1.000 placeringer vises. Du kan også downloade en kopi af denne rapport i CSV-format.

- Navnet på placeringens navn (mailadressen på postkasser og URL'en til websteder).

- Placeringstype (en postkasse eller et websted).

- Anslået antal elementer på den indholdsplacering, der returneres af søgningen.

- Den samlede størrelse af anslåede elementer for hver indholdsplacering.

## <a name="get-keyword-statistics-for-searches"></a>Få nøgleordsstatistik for søgninger

Som beskrevet tidligere viser **sektionen Betingelsesrapport** søgeforespørgslen og antallet (og størrelsen) af elementer, der svarer til forespørgslen. Hvis du bruger en liste med nøgleord, når du opretter eller redigerer en søgeforespørgsel, kan du få forbedret statistik, der viser, hvor mange elementer der matcher hvert nøgleord eller nøgleordsudtryk. Dette kan hjælpe dig med hurtigt at identificere, hvilke dele af forespørgslen der er mest (og mindst) effektive. Hvis et nøgleord f.eks. returnerer et stort antal elementer, kan du vælge at indskrænke nøgleordsforespørgslen for at indsnævre søgeresultaterne.

Sådan opretter du en nøgleordsliste og får vist nøgleordsstatistik for en søgning:
  
1. På internettet Microsoft 365 Overholdelsescenter oprette en ny indholdssøgning eller en søgning, der er knyttet til en core eDiscovery-sag.

2. På **siden Betingelser** i søgeguiden. skal du **markere afkrydsningsfeltet Vis** listen over nøgleord.

   ![Afkrydsningsfeltet Vis nøgleordsliste.](../media/SearchKeywordsList1.png)

3. Skriv et nøgleord eller en nøgleordsfase i en række i tabellen med nøgleord. Skriv **f.eks. budget** i den første række,  skriv sikkerhed i den anden række, og skriv **FY2021** i den tredje række.

   ![Skriv op til 20 nøgleord eller nøgleordsudtryk på listen.](../media/SearchKeywordsList2.png)

   > [!NOTE]
   > For at reducere problemer, der skyldes lister med store nøgleord, er du begrænset til maksimalt 20 rækker på listen med nøgleord i en søgeforespørgsel.

4. Når du har føjet nøgleordene til listen, som du vil søge efter og hente statistik for, skal du køre søgningen.

5. Når søgningen er fuldført, skal du vælge den for at få vist pop op-siden.

6. På fanen **Søgestatistik** skal du klikke på **betingelsesrapporten** for at få vist nøgleordsstatistikken for søgningen.

    ![Statistikken for hvert nøgleord vises.](../media/SearchKeywordsList3.png)
  
    Som vist på det forrige skærmbillede vises statistikken for hvert nøgleord. dette omfatter:

    - Nøgleordsstatistikken for hver type indholdsplacering, der medtages i søgningen.

    - Antallet af ikke-identificerede postkasseelementer.

    - Den faktiske søgeforespørgsel og resultater for hvert nøgleord (identificeret som  **Nøgleord** i kolonnen Del), som indeholder alle betingelser fra søgeforespørgslen.

    - Den komplette søgeforespørgsel ( **identificeret** **som primær** i kolonnen Del) og statistikken for den komplette forespørgsel for hver placeringstype. Bemærk, at dette er de samme statistikker, der vises på **fanen** Oversigt.
