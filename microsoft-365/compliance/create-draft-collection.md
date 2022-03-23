---
title: Opret en kladdesamling
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: En kladdesamling er en eDiscovery-søgning af dataindsamlingskilder, der ikke er tillid til, i en Advanced eDiscovery-sag, der returnerer et søgeoverslag, der svarer til søgeforespørgslen i samlingen. Du kan gennemse søgestatistik, få vist et eksempel på et udvalg af elementer og redigere og køre samlingen igen, før du har bekræftet resultaterne i et korrektursæt.
ms.openlocfilehash: 5a65bc97f44b2b5bf32f57f52000e66d68dc428a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591738"
---
# <a name="create-a-draft-collection-in-advanced-ediscovery"></a>Opret en kladdesamling i Advanced eDiscovery

Når du har identificeret registrerede og eventuelle ikke-registrerede datakilder for sagen, er du klar til at identificere og finde et sæt af dokumenter, der er relevante. Det gør du ved hjælp af værktøjet Samlinger til at søge efter relevant indhold fra datakilder. Det gør du ved at oprette en samling, der søger efter bestemt datakilder for indhold, der svarer til dine søgekriterier. Du har mulighed for at oprette en *kladdesamling, som* er et skøn over elementerne, der findes, eller du kan oprette en samling, der automatisk føjer elementerne til et gennemsynssæt. Når du opretter en kladdesamling, kan du få vist oplysninger om de anslåede resultater, der matchede søgeforespørgslen, f.eks. det samlede antal og størrelsen af elementer, der blev fundet, de forskellige datakilder, hvor de blev fundet, samt statistik om søgeforespørgslen. Du kan også få vist et eksempel på et eksempel på elementer, der er returneret af samlingen. Ved hjælp af denne statistik kan du ændre søgeforespørgslen og køre kladdesamlingen igen for at indsnævre dine resultater. Når du er tilfreds med indsamlingsresultaterne, kan du bekræfte samlingen i et gennemsynssæt. Når du har bekræftet en kladdesamling, føjes de elementer, der returneres af samlingen, til et korrektursæt til gennemsyn, analyse og eksport.

## <a name="before-you-create-a-draft-collection"></a>Før du opretter en kladdesamling

- Føj inkassoere og ikke-registrerede datakilder til sagen, før du opretter en kladdesamling. Dette er påkrævet, så du kan vælge datakilderne, når du opretter en kladdesamling. Du kan finde flere oplysninger under:

  - [Føj ydsere til en sag](add-custodians-to-case.md)

  - [Føj ikke-registrerede datakilder til en sag](non-custodial-data-sources.md)

- Du kan søge efter yderligere datakilder (dem, der ikke er blevet føjet til sagen som sted, hvor der ikke er nogen, der er til at lede) i en kladdesamling efter indhold, der kan være relevant for sagen. Disse datakilder kan omfatte postkasser, SharePoint websteder og Teams. Hvis denne situation er relevant for din sag, skal du samle en liste over disse datakilder, så du kan føje dem til samlingen.

## <a name="create-a-draft-collection"></a>Opret en kladdesamling

1. I Microsoft 365 Overholdelsescenter skal du åbne Advanced eDiscovery store og små bogstaver og derefter **vælge fanen** Samlinger.

2. På siden **Samlinger skal** du vælge Ny **samlingStandard-samling** > .

3. Skriv et navn (påkrævet) og en beskrivelse (valgfrit) til samlingen. Når samlingen er oprettet, kan du ikke ændre navnet, men du kan ændre beskrivelsen.

4. På siden **Forseende datakilder** skal du gøre et af følgende for at identificere, hvilke datakilder der skal indsamles indhold fra:

   - Klik **på Vælg** y-2-4-4 for at søge efter specifikke øverere, der blev føjet til sagen. Hvis du bruger denne indstilling, vises der en liste over sagsbrugerne. Vælg en eller flere y-øvrere. Når du har valgt og tilføjet hjælpere, kan du også vælge de bestemte datakilder for at søge efter hver søger efter hver søger. Disse datakilder, der vises, blev angivet, da der blev føjet en leder til sagen.

   - Klik på **til/fra-knappen** Markér alle for at søge i alle øvriske brugere, der blev føjet til sagen. Når du vælger denne indstilling, søges der i alle datakilder for alle y-1-2-2016.

5. På siden **Ikke-registrerede datakilder** skal du gøre et af følgende for at identificere de ikke-vigtigste datakilder, der skal indsamles indhold fra:

   - Klik **på Vælg ikke-registrerede datakilder for** at vælge bestemte ikke-registrerede datakilder, der blev føjet til sagen. Hvis du bruger denne indstilling, vises der en liste over datakilder. Vælg en eller flere af disse datakilder.

   - Klik på **til/fra-knappen** Markér alle for at vælge alle ikke-registrerede datakilder, der blev føjet til sagen.

6. På siden **Yderligere datakilder** kan du vælge andre postkasser og websteder, der skal søges i som en del af samlingen. Disse typer datakilder blev ikke tilføjet som opbevarings- eller ikke-opbevaringsbaserede dataplaceringer i sagen. Du har også to muligheder, når du søger efter yderligere datakilder:

   - Hvis du vil søge efter alle indholdsplaceringer for en bestemt tjeneste (Exchange-postkasser, SharePoint- og OneDrive-websteder eller Exchange offentlige mapper), skal du klikke på den tilsvarende indstilling for Markér  alt i **kolonnen Status**. Denne indstilling søger efter alle indholdsplaceringer i den valgte tjeneste.

   - Hvis du vil søge efter en bestemt indholdsplacering for en  tjeneste, skal du klikke på den tilhørende Vælg alt-funktion i kolonnen **Status** og derefter klikke på Brugere **,** grupper eller teams (for Exchange-postkasser) eller Vælge **websteder til (** SharePoint- og OneDrive-websteder) for at søge efter bestemte indholdsplaceringer.

7. På siden **Betingelser** kan du oprette den søgeforespørgsel, der bruges til at indsamle elementer fra de datakilder, du har identificeret i de forrige sider i guiden. Du kan søge efter nøgleord, par af egenskab:værdi eller bruge en liste med nøgleord. Du kan også tilføje forskellige søgebetingelser for at begrænse omfanget af samlingen. Du kan finde flere oplysninger [i Oprette søgeforespørgsler efter samlinger](building-search-queries.md).

8. På siden **Gem som kladde eller Tilføj for at gennemse sæt skal** du vælge **Gem samling som kladde**.

   > [!NOTE]
   > Den anden indstilling på denne side gør det muligt at indsamle elementer og føje dem direkte til et korrektursæt. I stedet for at oprette en kladdesamling, som du kan gennemse statistik for og få vist et eksempel på resultaterne af samlingen, springer denne indstilling denne proces over og føjer automatisk samlingen til et gennemsynssæt. Hvis du vælger den anden mulighed for at føje samlingen til et korrektursæt, har du yderligere indstillinger, du skal konfigurere, f.eks. indsamling af hele chatsamtaletråde i Microsoft Teams og Yammer og indsamling af vedhæftede skybaserede filer (også kaldet moderne vedhæftede *filer).* Du kan finde flere oplysninger om disse indstillinger i [Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md).

9. På siden **Gennemse din samling** kan du gennemse og opdatere de samlingsindstillinger, du konfigurerede på de forrige sider.

   - **Fanen** Oversigt: Gennemse og rediger navnet på og beskrivelsen af samlingen, søgekriterierne for samlingen, yderligere dataplaceringer og samlingstypen.

   - **Fanen** Kilder: Gennemse og ændre de datakilder, der ikke er til at få adgang til, for samlingen.

10. Klik **på Send** for at oprette kladdesamlingen. Der vises en side, der bekræfter, at samlingen blev oprettet.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Hvad sker der, når du har oprettet en kladdesamling

Når du har oprettet en kladdesamling, vises den på  siden Samlinger for sagen, og status viser, at den er i gang. Et job med **navnet Forberedelse af forhåndsvisning af** søgning og estimater oprettes **og vises også** på siden Jobs i sagen.

Under processen med at indsamle udkast udfører Advanced eDiscovery et søgeoverslag ud fra de søgekriterier og datakilder, du har angivet i samlingen. Advanced eDiscovery forbereder også en stikprøve af elementer, du kan få vist. Når samlingen er fuldført, opdateres følgende kolonner og tilsvarende værdier **på siden** Samling:

![Statustilstande for en kladdesamling.](../media/DraftCollectionStatus.png)

- **Status**: Angiver status og type for indsamling. En værdi af **Anslået** angiver, at en kladdesamling er fuldført. Denne samme værdi indikerer også, at samlingen er en kladdesamling, og at den ikke er blevet føjet til et gennemsynssæt. En værdi af **Bindende** i **kolonnen Status** angiver, at samlingen er føjet til et korrektursæt.

- **Estimeret status**: Angiver status for de estimerede søgeresultater, og hvorvidt de anslåede søgeresultater og statistik er klar til gennemsyn. En værdi af **Vellykket** angiver, at resultaterne af kladdesamlingen er klar til gennemsyn. Når du første gang sender en kladdesamling, vises **en værdi** for I gang for at angive, at samlingen stadig kører

- **Eksempelstatus**: Angiver status for de eksempelelementer, du kan få vist. En værdi af **Vellykket angiver** , at elementerne er klar til forhåndsvisning. Når du første gang sender en kladdesamling, vises **en værdi** for I gang for at angive, at samlingen stadig kører.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Næste trin, når en kladdesamling er fuldført

Når kladdesamlingen er fuldført, kan du udføre forskellige opgaver. For at udføre de fleste af disse opgaver skal du  blot gå til fanen Samlinger og klikke på navnet på kladdesamlingen for at få vist pop op-siden.

![Pop op-side til en kladdesamling.](../media/DraftCollectionFlyoutPage.png)

Her er en liste over ting, du kan gøre fra pop op-siden med samlinger:

- Vælg fanen **Oversigt** for at få vist oversigtsoplysninger om samlingen og de anslåede søgeresultater, der returneres af samlingen. Dette omfatter det samlede antal elementer og størrelsen af de anslåede søgeresultater, antallet af postkasser og websteder indeholdt søgeresultater og søgebetingelserne (hvis det bruges) bruges til at begrænse samlingen.

- Vælg fanen **Datakilder for** at få vist en liste over inkassoikere og ikke-oversigtsbaserede datakilder), der er blevet søgt i samlingen. Alle andre indholdsplaceringer, der blev søgt på **, vises** under Placeringer på **fanen** Oversigt.

- Vælg fanen **Søgestatistik** for at få vist statistik om samlingen. Dette omfatter det samlede antal og størrelsen af elementer, der findes i hver tjeneste (f.eks. Exchange-postkasser eller SharePoint-websteder), og en betingelsesrapport, der viser statistik over antallet af elementer, der returneres af forskellige komponenter i søgeforespørgslen, der bruges af samlingen. Få mere at vide under [Indsamling af statistik og rapporter](collection-statistics-reports.md).

- Klik **på Gennemse eksempel** (placeret nederst på pop op-siden) for at få vist et eksempel på et eksempel på de elementer, der returneres af samlingen.

- Bestil kladdesamlingen til et korrektursæt (ved at klikke **på** **ActionsEdit-samling** > ). Det betyder, at du kører samlingen igen (ved hjælp af de aktuelle indstillinger) og tilføjer de elementer, der returneres af samlingen, i et gennemsynssæt. Som tidligere nævnt kan du også konfigurere yderligere indstillinger (f.eks samtaletråde og skybaserede vedhæftede filer), når du føjer samlingen til et korrektursæt. Du kan finde flere oplysninger og en trinvis vejledning i Bekræfte [en kladdesamling i et gennemsynssæt](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Administrer en kladdesamling

Du kan bruge indstillingerne i menuen Handlinger **på pop** op-siden i en kladdesamling til at udføre forskellige administrationsopgaver.

![Indstillinger i menuen Handlinger for samling af kladder.](../media/DraftCollectionActionsMenu.png)

Her er beskrivelser af administrationsindstillingerne.

- **Rediger samling**: Rediger indstillingerne for kladdesamlingen. Når du har foretaget ændringer, kan du køre samlingen igen og opdatere de anslåede søgninger og statistikken. Som tidligere beskrevet bruger du denne indstilling til at bekræfte en kladdesamling i et korrektursæt.  

- **Slet samling**: Slet en kladdesamling. Bemærk, at når en kladdesamling er blevet forpligtet til et korrektursæt, kan den ikke slettes.

- **Opdater estimater**: Kør forespørgslen (mod de datakilder), der er angivet i kladdesamlingen, for at opdatere søgeestimimater og statistik.

- **Eksportér som rapport**: Eksporterer oplysninger om kladdesamlingen til en CSV-fil, som du kan downloade til din lokale computer. Eksportrapporten indeholder følgende oplysninger:

  - Identiteten for hver indholdsplacering, der indeholder elementer, der svarer til søgeforespørgslen i kladdesamlingen. Disse placeringer er typisk postkasser eller websteder.
  
  - Det samlede antal elementer på hver indholdsplacering.
  
  - Den samlede størrelse (i byte) af elementerne på hver indholdsplacering.

  - Tjenesten (f.eks Exchange eller SharePoint), hvor indholdsplaceringen er placeret.

- **Kopiér** samling: Opret en ny kladdesamling ved at kopiere indstillingerne fra en eksisterende samling. Du skal bruge et andet navn til den nye samling. Du har også mulighed for at ændre indstillingerne, før du sender den nye samling. Når du har indsendt den, køres søgeforespørgslen, og der genereres nye estimater og statistikker. Det er en god metode til hurtigt at oprette flere kladdesamlinger og derefter ændre de valgte indstillinger efter behov, mens oplysningerne stadig bevares i den oprindelige samling. Dette giver dig også mulighed for nemt at sammenligne resultaterne af to ensartede samlinger.

> [!NOTE]
> Når en kladdesamling er blevet forpligtet til et gennemsynssæt, kan du kun kopiere samlingen og eksportere en rapport.
