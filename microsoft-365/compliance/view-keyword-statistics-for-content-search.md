---
title: Vis statistik for eDiscovery-søgeresultater
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 05/10/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.search: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du bruger funktionen til søgestatistik til at få vist statistik for indholdssøgninger og søgninger, der er knyttet til en eDiscovery-sag (Standard) i Microsoft Purview-compliance-portal.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cc8e249f62b0dbfbeaa6bcf32e7873ca2ff5b36d
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318066"
---
# <a name="view-statistics-for-ediscovery-search-results"></a>Vis statistik for eDiscovery-søgeresultater

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har oprettet og kørt en indholdssøgning eller en søgning, der er knyttet til en Microsoft Purview eDiscovery (Standard), kan du få vist statistikker om de anslåede søgeresultater. Dette omfatter en oversigt over søgeresultaterne (svarende til oversigten over de anslåede søgeresultater, der vises på søgevinduets side), forespørgselsstatistikken, f.eks. antallet af indholdsplaceringer med elementer, der stemmer overens med søgeforespørgslen, og identiteten af indholdsplaceringer, der har de mest matchende elementer.
  
Du kan også bruge listen over nøgleord til at konfigurere en søgning til at returnere statistikker for hvert nøgleord i en søgeforespørgsel. Her kan du sammenligne antallet af resultater, der returneres af hvert nøgleord i en forespørgsel.
  
Du kan også downloade søgestatistik til en CSV-fil. Det giver dig mulighed for at bruge filtrerings- og sorteringsfunktionerne i Excel til at sammenligne resultater og forberede rapporter til dine søgeresultater.
  
## <a name="get-statistics-for-searches"></a>Hent statistik for søgninger

Sådan får du vist statistikker for en indholdssøgning eller en søgning, der er knyttet til en eDiscovery-sag (Standard).
  
1. Klik på **Vis alle** i Microsoft Purview-compliance-portal, og benyt derefter en af følgende fremgangsmåder:

   - Klik på **Indholdssøgning** , og vælg derefter en søgning for at få vist pop op-siden.

     ELLER

   - Klik på **eDiscoveryeDiscovery** >  **(Standard),** vælg en sag, og vælg derefter en søgning på fanen **Søgninger** for at få vist pop op-siden.

2. Klik på fanen **Søg efter statistik** på pop op-siden i den valgte søgning.
  
   ![Fanen Søg efter statistik.](../media/SearchStatistics1.png)

Fanen **Søg efter statistik** indeholder følgende afsnit, der indeholder forskellige typer statistik om søgningen.

### <a name="search-content"></a>Søg efter indhold

I dette afsnit vises en grafisk oversigt over de anslåede elementer, der returneres af søgningen. Dette angiver antallet af elementer, der opfylder søgekriterierne. Disse oplysninger giver dig en idé om det anslåede antal elementer, der returneres af søgningen.

![Søg efter estimater for en søgning.](../media/SearchContentReport.png)

- **Anslåede elementer efter lokationer**: Det samlede antal anslåede elementer, der returneres af søgningen. Det specifikke antal elementer, der er placeret i postkasser og placeret på websteder, vises også.

- **Anslåede placeringer med forekomster**: Det samlede antal indholdsplaceringer, der indeholder elementer, der returneres af søgningen. Det specifikke antal postkasser og webstedsplaceringer vises også.

- **Datamængde efter placering (i MB)**: Den samlede størrelse af alle anslåede elementer, der returneres af søgningen. Den specifikke størrelse af postkasseelementer og webstedselementer vises også.

### <a name="condition-report"></a>Betingelsesrapport

I dette afsnit vises statistik om søgeforespørgslen og antallet af anslåede elementer, der matcher forskellige dele af søgeforespørgslen. Du kan bruge disse statistikker til at analysere antallet af elementer, der stemmer overens med hver komponent i søgeforespørgslen. Dette kan hjælpe dig med at tilpasse søgekriterierne og om nødvendigt begrænse omfanget af området. Du kan også downloade en kopi af denne rapport i CSV-format.

![Betingelsesrapport.](../media/SearchContentReportNoKeywordList.png)

- **Placeringstype**: Den type indholdsplacering, som forespørgselsstatistikken gælder for. Værdien af **Exchange** angiver placeringen af en postkasse. Værdien **SharePoint** angiver placeringen af webstedet.

- **Del**: Den del af søgeforespørgslen, som statistikkerne gælder for. **Primary** angiver hele søgeforespørgslen. **Nøgleordet** angiver, at statistikkerne i rækken er for et bestemt nøgleord. Hvis du bruger en nøgleordsliste til søgeforespørgslen, medtages statistik for hver komponent i forespørgslen i denne tabel. Du kan finde flere oplysninger under [Hent nøgleordsstatistik for søgninger](#get-keyword-statistics-for-searches).

- **Betingelse**: Den faktiske komponent (nøgleord eller betingelse) for søgeforespørgslen, der returnerede de statistikker, der vises i den tilsvarende række.

- **Placeringer med forekomster**: Antallet af indholdsplaceringer (angivet af kolonnen **Placeringstype** ), der indeholder elementer, der svarer til den primære forespørgsel eller nøgleordsforespørgsel, der er angivet i kolonnen **Betingelse** .

- **Elementer**: Det antal elementer (fra den angivne indholdsplacering), der svarer til den forespørgsel, der er angivet i kolonnen **Betingelse** . Hvis et element indeholder flere forekomster af et nøgleord, der søges efter, tælles det som tidligere forklaret kun én gang i denne kolonne.

- **Størrelse (MB)**: Den samlede størrelse af alle elementer, der blev fundet (på den angivne indholdsplacering), som svarer til søgeforespørgslen i kolonnen **Betingelse** .

### <a name="top-locations"></a>Topplaceringer

I dette afsnit vises statistik om de specifikke indholdsplaceringer med de fleste elementer, der returneres af søgningen. De øverste 1.000 placeringer vises. Du kan også downloade en kopi af denne rapport i CSV-format.

- Navnet på placeringen (mailadressen på postkasser og URL-adressen til websteder).

- Placeringstype (en postkasse eller et websted).

- Anslået antal elementer på indholdsplaceringen, der returneres af søgningen.

- Den samlede størrelse af anslåede elementer på hver indholdsplacering.

## <a name="get-keyword-statistics-for-searches"></a>Hent nøgleordsstatistik for søgninger

Som tidligere forklaret viser afsnittet **Betingelsesrapport** søgeforespørgslen og antallet (og størrelsen) af elementer, der stemmer overens med forespørgslen. Hvis du bruger en nøgleordsliste, når du opretter eller redigerer en søgeforespørgsel, kan du få forbedret statistik, der viser, hvor mange elementer der matcher hvert nøgleord eller nøgleordsudtryk. Dette kan hjælpe dig med hurtigt at identificere, hvilke dele af forespørgslen der er mest (og mindst) effektive. Hvis et nøgleord f.eks. returnerer et stort antal elementer, kan du vælge at afgrænse nøgleordsforespørgslen for at indsnævre søgeresultaterne.

Sådan opretter du en nøgleordsliste og får vist nøgleordsstatistik for en søgning:
  
1. På overholdelsesportalen skal du oprette en ny indholdssøgning eller en søgning, der er knyttet til en eDiscovery(Standard)-sag.

2. På siden **Betingelser** i søgeguiden. markér afkrydsningsfeltet **Vis nøgleordsliste** .

   ![Vis afkrydsningsfeltet Liste over nøgleord.](../media/SearchKeywordsList1.png)

3. Skriv et nøgleord eller en nøgleordsfase i en række i nøgleordstabellen. Du kan f.eks. skrive **budget** i den første række, skrive **sikkerhed** i den anden række og skrive **FY2021** i den tredje række.

   ![Skriv op til 20 nøgleord eller nøgleordsudtryk på listen.](../media/SearchKeywordsList2.png)

   > [!NOTE]
   > For at hjælpe med at reducere problemer, der skyldes store nøgleordslister, er du begrænset til maksimalt 20 rækker på nøgleordslisten i en søgeforespørgsel.

4. Når du har føjet nøgleordene til den liste, du vil søge efter og hente statistikker for, skal du køre søgningen.

5. Når søgningen er fuldført, skal du vælge den for at få vist pop op-siden.

6. Klik på **rapporten Betingelse** under fanen **Søg efter statistik** for at få vist nøgleordsstatistikken for søgningen.

    ![Statistikkerne for hvert nøgleord vises.](../media/SearchKeywordsList3.png)
  
    Som vist på det forrige skærmbillede vises statistikkerne for hvert nøgleord. dette omfatter:

    - Nøgleordsstatistikken for hver type indholdsplacering, der er inkluderet i søgningen.

    - Antallet af elementer i en ikke-indekseret postkasse.

    - Den faktiske søgeforespørgsel og de faktiske resultater for hvert nøgleord (identificeret som **nøgleord** i kolonnen **Del** ), som indeholder alle betingelser fra søgeforespørgslen.

    - Den komplette søgeforespørgsel (identificeret som **Primær** i kolonnen **Del** ) og statistikkerne for den komplette forespørgsel for hver placeringstype. Bemærk, at dette er de samme statistikker, der vises under fanen **Oversigt** .
