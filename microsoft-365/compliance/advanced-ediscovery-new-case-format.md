---
title: Nyt format for store og små bogstaver i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: ninachen
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
description: Brug det nye caseformat i Advanced eDiscovery så du kan tilføje flere elementer for at gennemse sæt og drage fordel af andre øgede begrænsninger og nye funktioner.
ms.openlocfilehash: 9b0e87e7d24565bb89444fe5b1e5cbf43d915e42
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/22/2021
ms.locfileid: "63601049"
---
# <a name="use-the-new-case-format-in-advanced-ediscovery"></a>Brug det nye format for store og små bogstaver i Advanced eDiscovery

Flere organisationer bruger løsningen Advanced eDiscovery til Microsoft 365 til kritiske eDiscovery-processer. Dette omfatter besvarelse af lovgivningsmæssige anmodninger, undersøgelser og procesførelse. I Advanced eDiscovery af indhold øges, er et almindeligt kundekrav at udvide den samlede mængde indhold, der kan administreres i en enkelt Advanced eDiscovery tilfælde. For at tage højde for væsentlige stigninger i sagsstørrelsen, både for den samlede datamængde og det samlede antal elementer, kan du nu vælge det nye caseformat, når du opretter en Advanced eDiscovery sag.  

## <a name="create-a-case"></a>Opret en sag

Sådan oprettes en Advanced eDiscovery ved hjælp af det nye sagsformat:

1. Gå til <https://compliance.microsoft.com> , og log på.

2. Klik på **eDiscovery Microsoft 365 Overholdelsescenter avanceret i navigations > ruden i venstre side**.

3. På siden **Advanced eDiscovery** skal du klikke på **fanen Sager** og derefter klikke på **Opret en sag**.

   Pop **op-siden Ny eDiscovery-sag** vises. Sektionen **Caseformat giver** mulighed for at oprette en sag ved hjælp af det nye format.

   ![Indstillingen Nyt sagsformat på siden Ny eDiscovery-sag.](..\media\AeDNewCaseFormat1.png)

4. Når du har navngivet sagen, skal du **vælge indstillingen** Ny og derefter klikke på **Gem** for at oprette sagen ved hjælp af det nye format.

## <a name="benefits-of-the-new-case-format"></a>Fordele ved det nye sagsformat

Det nye sagsformat gør det muligt at administrere sager, der indeholder mere end 40 millioner elementer. Denne funktion hjælper dig med effektivt at administrere store mængder sagsdata gennem hele eDiscovery-arbejdsprocessen.

Her er en liste over andre fordele ved store sager i Advanced eDiscovery arbejdsproces.

- **Samling**: I det nye sagsformat kan du indsamle op til 1 TB data for en enkelt samling.

   For hver sag vil indstillingerne for indsamling som standard indsamle vedhæftede filer fra skyen og kontekstafhængige Teams og Yammer indhold. Disse indstillinger hjælper med at indsamle det fulde billede af digital kommunikation i en undersøgelse. For Teams- og Yammer-kontekstafhængige samtaler konverterer det nye sagsformat tidsbaserede øjebliksbilleder af 1:1, 1: N- og kanalsamtaler til HTML-afskrifter for at give kontekst til samtaler og reducere det samlede antal elementer, der produceres af chatbaseret indhold.  

- **Gennemse**: Hvert korrektursæt understøtter op til 1 TB forududvidelsesindhold. Der vil være flere metadata tilgængelige for filtre og forespørgsler, herunder Teamnavn, kanalnavn og samtalenavn for Teams indhold. Hver udskrift indeholder tidsbaseret indhold til før og efter det dynamiske element. I forbindelse med kanalsamtaler indsamles rodopslag og alle svar for dynamisk indhold. Du kan finde flere oplysninger [Advanced eDiscovery arbejdsprocessen for indhold i Microsoft Teams (forhåndsvisning)](teams-workflow-in-advanced-ediscovery.md)

- **Eksportér**: Du kan eksportere store sæt indhold i et enkelt eksportjob. Med det nye case-format kan du eksportere 5 millioner dokumenter eller 500 GB, alt efter hvad der er mindre i et eksportjob.

Desuden indeholder det nye case-format en opdateret brugergrænseflade, der viser den samlede størrelse af hvert korrektursæt i sagen. Størrelse på korrektursæt vises i en kolonne på **fanen Korrektursæt** .

![Ny statistik for revisionssæt Advanced eDiscovery brugergrænsefladen.](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Virker det, hvis jeg forsøger at indsamle mere end 1 TB i en enkelt samling?**

Ydeevnen påvirkes negativt og kan medføre ustabilitet i nogle tilfælde.

**Hvis vedhæftede filer fra skyen som standard er inkluderet i formatet store bogstaver; hvordan kan jeg fjerne indholdet fra min gennemsynsoplevelse?**  

Brug filtre for korrektursæt til at filtrere efter meddelelses type eller til at udelade vedhæftede filer i skyen ved hjælp af hasAttachment-filteret. Få mere at vide under [Forespørg og filtrer indhold i et gennemsynssæt](review-set-search.md).

**Vil indlæsningsfilen ved eksport af chatsamtaler indeholde alle de udvidede metadata og et enkelt element for hver afskrift?**

Alle metadata for en samtale integreres i HTML-afskriftsfilen.  Mange af de fælles felter er tilgængelige i indlæsningsfilen. Du kan finde flere oplysninger om eksporterede metadata [i Dokumentmetadatafelter Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).
