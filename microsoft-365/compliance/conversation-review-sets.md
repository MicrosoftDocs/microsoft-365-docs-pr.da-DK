---
title: Gennemse samtaler i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.assetid: ''
description: Få mere at vide om funktionen til genopbygning af samtaler i Microsoft Purview eDiscovery (Premium) (kaldet samtaletrådning) for at genskabe, gennemse og eksportere chatsamtaler i Microsoft Teams og Yammer grupper.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 9bfd87de95449ab30b8a33c9f7f96db458e809d1
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64950263"
---
# <a name="conversation-threading-in-ediscovery-premium"></a>Samtaletrådning i eDiscovery (Premium)

Chat er en nem måde at stille spørgsmål, dele ideer eller hurtigt kommunikere på tværs af store målgrupper. Efterhånden som chatplatforme, f.eks. Microsoft Teams og Yammer grupper, bliver kerne i virksomhedssamarbejde, skal organisationer evaluere, hvordan deres eDiscovery-arbejdsproces håndterer disse nye former for kommunikation og samarbejde.

Funktionen til genopbygning af samtaler i Microsoft Purview eDiscovery (Premium) er designet til at hjælpe dig med at identificere kontekstuelt indhold og oprette forskellige samtalevisninger. Denne funktion giver dig mulighed for effektivt og hurtigt at gennemse komplette chatsamtaler (også kaldet *trådede samtaler*), der genereres på platforme som Microsoft Teams.

Med genopbygning af samtaler kan du bruge indbyggede funktioner til at genskabe, gennemse og eksportere gevindsamtaler. Brug genopbygning af eDiscovery-samtaler (Premium) til at:

- Bevar entydige metadata på meddelelsesniveau på tværs af alle meddelelser i en samtale.

- Indsaml kontekstafhængige meddelelser omkring dine søgeresultater.

- Gennemse, anmærk og gentegn gevindsamtaler.

- Eksportér individuelle meddelelser eller gevindsamtaler

## <a name="terminology"></a>Terminologi

Her er nogle definitioner, der kan hjælpe dig med at komme i gang med at bruge genopbygning af samtaler.

- **Meddelelser:** Repræsenter den mindste enhed i en samtale. Meddelelser kan variere i størrelse, struktur og metadata.

- **Samtale:** Repræsenterer en gruppering af en eller flere meddelelser. Samtaler kan repræsenteres på forskellige måder på tværs af forskellige programmer. I nogle programmer er der en eksplicit handling, der skyldes svar på en eksisterende meddelelse. Samtaler dannes eksplicit som et resultat af denne brugerhandling. Her er f.eks. et skærmbillede af en kanalsamtale i Microsoft Teams.

   ![Microsoft Teams kanalsamtale.](../media/threadedchat.png)

   I andre apps (f.eks. gruppechatbeskeder i Teams) er der ikke en formel svarkæde, og meddelelser vises i stedet som en "flad flod af meddelelser" i en enkelt tråd. I disse typer apps udledes samtaler fra en gruppe meddelelser, der forekommer inden for et bestemt tidspunkt. Denne "blød gruppering" af meddelelser (i modsætning til en svarkæde) repræsenterer "frem og tilbage"-samtalen om et bestemt emne af interesse.

## <a name="step-1-create-a-draft-collection"></a>Trin 1: Opret en kladdesamling

Når du har identificeret relevante tilsynsførende og indholdsplaceringer, kan du oprette en søgning for at finde potentielt relevant indhold. Under fanen **Samlinger** i eDiscovery-sagen (Premium) kan du oprette en samling ved at klikke på **Ny samling** og følge guiden. Du kan finde oplysninger om, hvordan du kan oprette en samling, oprette en søgeforespørgsel og få vist søgeresultaterne i [Opret en kladdesamling](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Trin 2: Send en kladdesamling til et gennemsynssæt

Når du har gennemset og færdiggjort søgeforespørgslen i en samling, kan du føje søgeresultaterne til et korrektursæt. Når du føjer dine søgeresultater til et korrektursæt, kopieres de oprindelige data til et Azure Storage område for at lette korrektur- og analyseprocessen. Du kan finde flere oplysninger om, hvordan du føjer søgeresultater til et korrektursæt, under [Send en kladdesamling til et korrektursæt](commit-draft-collection.md).

Når du føjer elementer fra samtaler til et korrektursæt, kan du bruge indstillingen gevindsamtaler til at indsamle kontekstafhængige meddelelser fra samtaler, der indeholder elementer, der opfylder søgekriterierne i samlingen. Når du har valgt indstillingen trådsamtaler, kan følgende ting ske:

  ![Hentning af samtale.](../media/messagesandconversations.png)

1. Ved hjælp af en forespørgsel med nøgleord og datointerval returnerede søgningen et hit på *Meddelelse 3*. Denne meddelelse var en del af en større samtale, der illustreres af *CRC1*.

2. Når du føjer dataene til et korrektursæt og aktiverer indstillingerne for hentning af samtaler, går eDiscovery (Premium) tilbage og indsamler andre elementer i *CRC1*.

3. Når elementerne er føjet til korrektursættet, kan du gennemse alle de enkelte meddelelser fra *CRC1*.

Hvis du vil aktivere indstillingen trådede samtaler, skal du se [Send en kladdesamling til et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>Trin 3: Gennemse og eksportér gevindsamtaler

Når indholdet er blevet behandlet og føjet til korrektursættet, kan du begynde at gennemse dataene i korrektursættet. Individuelle meddelelser er sammentrådet og præsenteret som samtaler. Det giver dig mulighed for at gennemse og eksportere kontekstafhængige samtaler.

  ![Samtalegennemgangssæt.](../media/ConversationRSOptions.PNG)

I de følgende afsnit beskrives det, hvordan du gennemgår og eksporterer samtaler.

### <a name="reviewing-conversations"></a>Gennemgå samtaler

I et korrektursæt kan du bruge følgende indstillinger til at lette korrekturprocessen.

- **Gruppér efter samtale:** Grupperer meddelelser i den samme samtale for at hjælpe brugerne med at forenkle og fremskynde deres korrekturproces.

- **Oversigtsvisning:** Viser den trådede samtale. I denne visning kan du se hele samtalen og også få adgang til metadataene for hver enkelt meddelelse.

   - Få vist metadata for individuelle meddelelser

   - Download individuelle meddelelser

- **Tekstvisning:** Leverer den udtrukne tekst til hele samtalen.

- **Anmærk visning:** Gør det muligt at markere en trådet visning af samtalen. Alle meddelelser i samtalen deler det samme anmærkede dokument.

- **Tagging:** Når du får vist samtaler i et korrektursæt, kan du få vist og anvende mærker ved at klikke på **panelet Tagging** i panelet Kodning.

- **Kør samtalekonvertering igen:** Når meddelelser føjes til et samtalegennemsynssæt, køres der automatisk et konverteringsjob for at oprette den gevindrede oversigt og anmærke visninger. Hvis jobbet Til genopbygning af samtale mislykkes, kan du køre jobbet igen ved at klikke på **Handling > Opret samtale-PDF-filer** i korrektursættet.

### <a name="exporting-conversations"></a>Eksporterer samtaler

Du kan finde de indstillinger, du kan vælge, når du eksporterer samtaler fra et korrektursæt, under [Eksportér dokumenter fra et korrektursæt](export-documents-from-review-set.md#export-options).

Du kan især eksportere hele chatsamtaler i en enkelt PDF-fil, eller du kan eksportere hver enkelt chatmeddelelse i en samtale som en enkelt fil.

## <a name="more-information"></a>Flere oplysninger

Du kan få mere at vide om, hvordan du gennemser sagsdata i eDiscovery (Premium), i følgende artikler:

- [Forespørg om og filtrer indhold i et valideringssæt](review-set-search.md)
- [Markér dokumenter i et valideringssæt](tagging-documents.md)
- [Vis sagsdata](view-documents-in-review-set.md)
- [Analysér sagsdata](analyzing-data-in-review-set.md)
- [Eksportér sagsdata](exporting-data-ediscover20.md)
