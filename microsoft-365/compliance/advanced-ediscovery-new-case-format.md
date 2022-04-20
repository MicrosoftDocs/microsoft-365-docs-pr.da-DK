---
title: Nyt sagsformat i eDiscovery (Premium)
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
description: Brug det nye sagsformat i eDiscovery (Premium), så du kan tilføje flere elementer for at gennemse sæt og drage fordel af andre øgede grænser og ny funktionalitet.
ms.openlocfilehash: 6c3e9f86cac5424ae9d9610a9c715c2f86563f64
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993551"
---
# <a name="use-the-new-case-format-in-ediscovery-premium"></a>Brug det nye sagsformat i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Flere organisationer bruger eDiscovery-løsningen (Premium) i Microsoft Purview til kritiske eDiscovery-processer. Dette omfatter besvarelse af lovmæssige anmodninger, undersøgelser og retssager. I takt med at brugen af eDiscovery (Premium) øges, er et almindeligt kundekrav at udvide den samlede mængde indhold, der kan administreres i et enkelt eDiscovery-tilfælde (Premium). For at hjælpe med at imødekomme betydelige stigninger i sagsstørrelsen, både for den samlede datamængde og det samlede antal elementer, kan du nu vælge det nye sagsformat, når du opretter en eDiscovery-sag (Premium).  

## <a name="create-a-case"></a>Opret en sag

Sådan opretter du en eDiscovery-sag (Premium) ved hjælp af det nye sagsformat:

1. Gå til , <https://compliance.microsoft.com> og log på.

2. Klik på **eDiscovery > Avanceret** i navigationsruden til venstre på Microsoft Purview-overholdelsesportalen.

3. Klik på fanen **Sager** på siden **eDiscovery (Premium),** og klik derefter på **Opret en sag**.

   Siden **Ny eDiscovery-sag** vises. Afsnittet **Sagsformat** giver mulighed for at oprette en sag ved hjælp af det nye format.

   ![Ny indstilling for sagsformat på siden Ny eDiscovery-sag.](..\media\AeDNewCaseFormat1.png)

4. Når du har navngivet sagen, skal du vælge indstillingen **Ny** og derefter klikke på **Gem** for at oprette sagen i det nye format.

## <a name="benefits-of-the-new-case-format"></a>Fordele ved det nye sagsformat

Det nye sagsformat giver dig mulighed for at administrere sager, der indeholder mere end 40 millioner elementer. Denne funktion hjælper dig med effektivt at administrere store mængder sagsdata via hele eDiscovery-arbejdsprocessen.

Her er en liste over andre fordele ved store sager i arbejdsprocessen for eDiscovery (Premium).

- **Samling**: I det nye sagsformat kan du indsamle op til 1 TB data for en enkelt samling.

   For hver sag vil samlingsindstillingerne som standard indsamle vedhæftede filer i skyen og kontekstafhængig Teams og Yammer indhold. Disse indstillinger hjælper med at indsamle det fulde billede af digital kommunikation i en undersøgelse. For Teams og Yammer kontekstafhængige samtaler konverterer det nye sagsformat tidsbaserede snapshots af 1:1, 1: N- og Kanalsamtaler til HTML-transskriptioner for at hjælpe med at levere kontekst for samtaler og reducere det samlede antal elementer, der produceres af chatbaseret indhold.  

- **Anmeldelse**: Hvert anmeldelsessæt understøtter op til 1 TB indhold før udvidelse. Der er yderligere metadata tilgængelige for filtre og forespørgsler, herunder teamnavn, kanalnavn og samtalenavn for Teams indhold. Hver transskription indeholder tidsbaseret indhold for før og efter det dynamiske element. I forbindelse med kanalsamtaler indsamles rodindlægget og alle svar for dynamisk indhold. Du kan finde flere oplysninger [i arbejdsprocessen for eDiscovery (Premium) for indhold i Microsoft Teams (prøveversion)](teams-workflow-in-advanced-ediscovery.md)

- **Eksportér**: Du kan eksportere store indholdssæt i et enkelt eksportjob. Med det nye sagsformat kan du eksportere 5 millioner dokumenter eller 500 GB, alt efter hvad der er mindre i et eksportjob.

Det nye caseformat indeholder desuden en opdateret brugergrænseflade, der viser den samlede størrelse af hvert anmeldelsessæt i sagen. Størrelser på korrektursæt vises i en kolonne under fanen **Gennemse sæt** .

![Ny statistik for gennemgangssæt i brugergrænsefladen i eDiscovery (Premium).](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvis jeg forsøger at indsamle mere end 1 TB i en enkelt samling, vil det så fungere?**

Ydeevnen vil blive negativt påvirket og kan medføre ustabilitet i nogle tilfælde.

**Hvis vedhæftede filer i skyen som standard er inkluderet i stort format. hvordan kan jeg fjerne dette indhold fra min gennemgangsoplevelse?**  

Brug filtre for korrektursæt til at filtrere efter meddelelsestype eller til at udelade vedhæftede filer i skyen ved hjælp af filteret HasAttachment. Du kan få flere oplysninger under [Forespørg om og filtrer indhold i et anmeldelsessæt](review-set-search.md).

**Når du eksporterer transskriptioner af chatsamtaler, indeholder indlæsningsfilen så alle de udvidede metadata og et enkelt element for hver transskription?**

Alle metadata for en samtale er integreret i HTML-transskriptionsfilen.  Mange af de almindelige felter er tilgængelige i indlæsningsfilen. Du kan finde flere oplysninger om eksporterede metadata [under Dokumentmetadatafelter i eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md).
