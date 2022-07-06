---
title: Opret en kladdesamling
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: En kladde til en samling er en eDiscovery-søgning af datakilder med frihedsberøvelse og ingen frihedsberøvelse i en eDiscovery-sag (Premium), der returnerer et søgeestimat, der svarer til søgeforespørgslen i samlingen. Du kan gennemse søgestatistik, få vist et eksempel på et udsnit af elementer og revidere og køre samlingen igen, før du sender resultaterne til et korrektursæt.
ms.openlocfilehash: 979573503e448a731c487018b525d6ddb1d7d08f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630163"
---
# <a name="create-a-draft-collection-in-ediscovery-premium"></a>Opret en kladdesamling i eDiscovery (Premium)

Når du har identificeret tilsynsførende og andre datakilder, der ikke er tilsynsførende for sagen, er du klar til at identificere og finde et sæt dokumenter, der er relevante. Det gør du ved hjælp af værktøjet Samlinger til at søge efter relevant indhold fra datakilder. Det gør du ved at oprette en samling, der søger i angivne datakilder efter indhold, der opfylder dine søgekriterier. Du har mulighed for at oprette en *kladdesamling*, som er et estimat over elementerne, eller du kan oprette en samling, der automatisk føjer elementerne til et korrektursæt. Når du opretter en kladdesamling, kan du få vist oplysninger om de anslåede resultater, der matcher søgeforespørgslen, f.eks. det samlede antal og den samlede størrelse af fundne elementer, de forskellige datakilder, hvor de blev fundet, og statistikker om søgeforespørgslen. Du kan også få vist et eksempel på elementer, der blev returneret af datasættet. Ved hjælp af disse statistikker kan du ændre søgeforespørgslen og køre kladdesamlingen igen for at indsnævre dine resultater. Når du er tilfreds med resultaterne af samlingen, kan du bekræfte samlingen til et korrektursæt. Når du bekræfter et kladde-datasæt, føjes de elementer, der returneres af datasættet, til et valideringssæt til gennemsyn, analyse og eksport.

## <a name="before-you-create-a-draft-collection"></a>Før du opretter en kladdesamling

- Føj tilsynsførende og ikke-frihedsberøvende datakilder til sagen, før du opretter en kladdesamling. Dette er påkrævet, så du kan vælge datakilderne, når du opretter en kladdesamling. Du kan finde flere oplysninger under:

  - [Føj ansvarlige til en sag](add-custodians-to-case.md)

  - [Føj datakilder uden ansvarlige til en sag](non-custodial-data-sources.md)

- Du kan søge i flere datakilder (dem, der ikke er føjet til sagen som placeringer med frihedsberøvelse eller som ikke-frihedsberøvende) i en kladdesamling for indhold, der kan være relevant for sagen. Disse datakilder kan omfatte postkasser, SharePoint-websteder og Teams. Hvis denne situation gælder for din sag, skal du kompilere en liste over disse datakilder, så du kan føje dem til samlingen.

## <a name="create-a-draft-collection"></a>Opret en kladdesamling

1. I Microsoft Purview-compliance-portal skal du åbne sagen eDiscovery (Premium) og derefter vælge fanen **Samlinger**.

2. På siden **Datasæt** skal du vælge **Nyt datasæt** > **Standard datasæt**.

3. Skriv et navn (påkrævet) og en beskrivelse (valgfrit) for datasættet. Når samlingen er oprettet, kan du ikke ændre navnet, men du kan ændre beskrivelsen.

4. På siden **Frihedsberøvende datakilder** skal du gøre en af følgende ting for at identificere de datakilder, der er til indsamling af indhold fra:

   - Klik på **Vælg tilsynsførende** for at søge efter bestemte tilsynsførende, der blev føjet til sagen. Hvis du bruger denne indstilling, vises der en liste over sagsvogterne. Vælg en eller flere tilsynsførende. Når du har valgt og tilføjet vogterne, kan du også vælge de specifikke datakilder, der skal søges efter hver tilsynsførende. Disse datakilder, der vises, blev angivet, da tilsynsførende blev føjet til sagen.

   - Klik på til/fra-knappen **Markér alle** for at søge efter alle tilsynsførende, der er føjet til sagen. Når du vælger denne indstilling, søges der i alle datakilder for alle tilsynsførende.

5. På siden **Datakilder uden frihedsberøvelse** skal du gøre en af følgende ting for at identificere de datakilder, der ikke er frihedsberøvende, for at indsamle indhold fra:

   - Klik på **Vælg datakilder uden frihedsberøvelse** for at vælge bestemte datakilder, der ikke er frihedsberøvende, som er føjet til sagen. Hvis du bruger denne indstilling, vises der en liste over datakilder. Vælg en eller flere af disse datakilder.

   - Klik på til/fra-knappen **Markér alle** for at vælge alle datakilder, der ikke er frihedsberøvende, og som er føjet til sagen.

6. På siden **Flere datakilder** kan du vælge andre postkasser og websteder, der skal søges i som en del af samlingen. Disse typer datakilder blev ikke tilføjet som dataplaceringer med frihedsberøvelse eller som ikke-frihedsberøvende i tilfælde. Du har også to muligheder, når du søger i flere datakilder:

   - Hvis du vil søge på alle indholdsplaceringer efter en bestemt tjeneste (Exchange-postkasser, SharePoint- og OneDrive-websteder eller offentlige Exchange-mapper), skal du klikke på den tilsvarende til/ **fra-knap Vælg alle** i kolonnen **Status** . Denne indstilling søger i alle indholdsplaceringer i den valgte tjeneste.

   - Hvis du vil søge efter en bestemt indholdsplacering for en tjeneste, skal du klikke på den tilsvarende Til/fra-knap **Vælg alle** i kolonnen **Status** og derefter klikke på **Brugere, grupper eller teams** (for Exchange-postkasser) eller **Vælg websteder** til (SharePoint- og OneDrive-websteder) for at søge efter bestemte indholdsplaceringer.

7. På siden **Betingelser** kan du oprette den søgeforespørgsel, der bruges til at indsamle elementer fra de datakilder, du har identificeret på de forrige guidesider. Du kan søge efter nøgleord, egenskab:værdipar eller bruge en nøgleordsliste. Du kan også tilføje forskellige søgebetingelser for at indsnævre omfanget af samlingen. Du kan finde flere oplysninger under [Opret søgeforespørgsler for datasæt](building-search-queries.md).

8. På siden **Gem som kladde, eller tilføj for at gennemse sæt** skal du vælge **Gem samling som kladde**.

   > [!NOTE]
   > Med den anden indstilling på denne side kan du indsamle elementer og føje dem direkte til et korrektursæt. I stedet for at oprette en kladdesamling, som du kan gennemse statistikker for og få vist et eksempel på resultaterne af samlingen, springer denne indstilling denne proces over og føjer automatisk samlingen til et gennemsynssæt. Hvis du vælger den anden indstilling for at føje samlingen til et anmeldelsessæt, har du yderligere indstillinger, der skal konfigureres, f.eks. indsamling af hele chatsamtaletråde i Microsoft Teams og Yammer og indsamling af vedhæftede filer i skyen (også kaldet *moderne vedhæftede filer*). Du kan få flere oplysninger om disse indstillinger under [Send en kladdesamling til et korrektursæt](commit-draft-collection.md).

9. På siden **Gennemse din samling** kan du gennemse og opdatere de samlingsindstillinger, du konfigurerede på de forrige sider.

   - **Fanen Oversigt** : Gennemse og rediger navnet og beskrivelsen af samlingen, søgekriterierne for samlingen, yderligere dataplaceringer og samlingstypen.

   - Fanen **Kilder**: Gennemse og rediger datakilderne til frihedsberøvelse og ikke-frihedsberøvelse for samlingen.

10. Klik på **Send** for at oprette kladdesamlingen. Der vises en side, der bekræfter, at samlingen blev oprettet.

## <a name="what-happens-after-you-create-a-draft-collection"></a>Hvad sker der, når du har oprettet en kladdesamling?

Når du har oprettet en kladdesamling, vises den på siden **Samlinger** i sagen, og status viser, at den er i gang. Der oprettes og vises også et job med navnet **Forberedelse af søgeeksempel og estimater** på siden **Job** .

Under kladdeindsamlingsprocessen udfører eDiscovery (Premium) et søgeestimat ved hjælp af de søgekriterier og datakilder, du har angivet i samlingen. eDiscovery (Premium) forbereder også et udsnit af elementer, som du kan få vist. Når samlingen er fuldført, opdateres følgende kolonner og tilsvarende værdier på siden **Samling** :

![Statustilstande for en kladdesamling.](../media/DraftCollectionStatus.png)

- **Status**: Angiver status og type af samling. Værdien **Anslået** angiver, at en kladdesamling er fuldført. Den samme værdi angiver også, at samlingen er en kladdesamling, og at den ikke er føjet til et korrektursæt. Værdien **Bekræftet** i kolonnen **Status** angiver, at samlingen er føjet til et gennemsynssæt.

- **Estimatstatus**: Angiver status for de anslåede søgeresultater, og om søgeestimaterne og statistikkerne er klar til gennemsyn eller ej. Værdien **Vellykket** angiver, at resultaterne af kladdesamlingen er klar til gennemsyn. Når du har sendt en kladdesamling første gang, vises værdien **I gang** for at angive, at samlingen stadig kører

- **Status for eksempelvisning**: Angiver status for de eksempelelementer, du kan få vist. Værdien **Vellykket** angiver, at elementerne er klar til eksempelvisning. Når du har sendt en kladdesamling første gang, vises værdien **Igangværende** for at angive, at samlingen stadig kører.

## <a name="next-steps-after-a-draft-collection-is-complete"></a>Næste trin, når en kladdesamling er fuldført

Når kladdesamlingen er fuldført, kan du udføre forskellige opgaver. Hvis du vil udføre de fleste af disse opgaver, skal du blot gå til fanen **Samlinger** og klikke på navnet på kladdesamlingen for at få vist pop op-siden.

![Pop op-side for en kladdesamling.](../media/DraftCollectionFlyoutPage.png)

Her er en liste over ting, du kan gøre fra siden med samlingens pop op-vindue:

- Vælg fanen **Oversigt** for at få vist oversigtsoplysninger om samlingen og de anslåede søgeresultater, der returneres af samlingen. Dette omfatter det samlede antal elementer og størrelsen af de anslåede søgeresultater, antallet af postkasser og websteder, der indeholdt søgeresultater, og søgebetingelserne (hvis de bruges) til at afgrænse samlingen.

- Vælg fanen **Datakilder** for at få vist en liste over tilsynsførende og ikke-frihedsberøvende datakilder, der blev søgt i i samlingen. Alle yderligere indholdsplaceringer, der blev søgt efter, er angivet under **Placeringer** under fanen **Oversigt** .

- Vælg fanen **Søg efter statistik** for at få vist statistikker om samlingen. Dette omfatter det samlede antal og den samlede størrelse af elementer, der blev fundet i hver tjeneste (f.eks. Exchange-postkasser eller SharePoint-websteder) og en betingelsesrapport, der viser statistik om antallet af elementer, der returneres af forskellige komponenter i den søgeforespørgsel, der bruges af samlingen. Du kan få flere oplysninger under [Samlingsstatistik og -rapporter](collection-statistics-reports.md).

- Klik på **Gennemse eksempel** (placeret nederst på pop op-siden) for at få vist et eksempel på de elementer, der returneres af samlingen.

- Send kladdesamlingen til et korrektursæt (ved at klikke på **Handlinger** > **Rediger samling**). Det betyder, at du kører samlingen igen (ved hjælp af de aktuelle indstillinger) og føjer de elementer, der returneres af samlingen, til et korrektursæt. Som tidligere forklaret kan du også konfigurere yderligere indstillinger (f.eks. samtaletrådning og cloudbaserede vedhæftede filer), når du føjer samlingen til et korrektursæt. Du kan finde flere oplysninger og trinvise instruktioner under [Send en kladdesamling til et korrektursæt](commit-draft-collection.md).

## <a name="manage-a-draft-collection"></a>Administrer en kladdesamling

Du kan bruge indstillingerne i menuen **Handlinger** på pop op-siden i en kladdesamling til at udføre forskellige administrationsopgaver.

![Indstillinger i menuen Handlinger for kladdesamling.](../media/DraftCollectionActionsMenu.png)

Her er beskrivelser af administrationsmulighederne.

- **Rediger samling**: Rediger indstillingerne for kladdesamlingen. Når du har foretaget ændringer, kan du køre samlingen igen og opdatere søgeestimaterne og -statistikkerne. Som tidligere forklaret, skal du bruge denne indstilling til at bekræfte en kladdesamling til et korrektursæt.  

- **Slet samling**: Slet en kladdesamling. Bemærk, at når en kladdesamling er bekræftet i et korrektursæt, kan den ikke slettes.

- **Opdateringsestimater**: Kør forespørgslen igen (i forhold til de datakilder), der er angivet i kladdesamlingen, for at opdatere søgeestimaterne og -statistikkerne.

- **Eksportér som rapport**: Eksporterer oplysninger om kladdesamlingen til en CSV-fil, som du kan downloade til din lokale computer. Eksportrapporten indeholder følgende oplysninger:

  - Identiteten for hver indholdsplacering, der indeholder elementer, der svarer til søgeforespørgslen i kladdesamlingen. Disse placeringer er typisk postkasser eller websteder.
  
  - Det samlede antal elementer på hver indholdsplacering.
  
  - Den samlede størrelse (i byte) af elementerne på hver indholdsplacering.

  - Den tjeneste (f.eks. Exchange eller SharePoint), hvor indholdsplaceringen er placeret.

- **Kopiér samling**: Opret en ny kladdesamling ved at kopiere indstillingerne fra en eksisterende samling. Du skal bruge et andet navn til den nye samling. Du har også mulighed for at ændre indstillingerne, før du sender den nye samling. Når du har sendt den, køres søgeforespørgslen, og der genereres nye estimater og statistikker. er en god måde hurtigt at oprette yderligere kladdesamling og derefter ændre de valgte indstillinger efter behov, samtidig med at du bevarer oplysningerne i den oprindelige samling. Det gør det også nemt at sammenligne resultaterne af to lignende samlinger.

> [!NOTE]
> Når en kladdesamling er bekræftet i et korrektursæt, kan du kun kopiere samlingen og eksportere en rapport.
