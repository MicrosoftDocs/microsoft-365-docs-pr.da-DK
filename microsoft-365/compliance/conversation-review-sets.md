---
title: Gennemse samtaler i Advanced eDiscovery
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
description: Få mere at vide om funktionen til samtaleovertrædelse i Advanced eDiscovery (kaldet samtaletrådning) for at genoprette, gennemgå og eksportere chatsamtaler i Microsoft Teams og Yammer grupper.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7bd13bdb01298d0cf1f37671f044a3405a2de0b6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587891"
---
# <a name="conversation-threading-in-advanced-ediscovery"></a>Samtaletråde i Advanced eDiscovery

Chat er en nem metode til at stille spørgsmål, dele ideer eller hurtigt kommunikere på tværs af store målgrupper. Som chatplatforme, f.eks. Microsoft Teams og Yammer-grupper, bliver kernen i virksomhedsamarbejde, skal organisationer evaluere, hvordan deres eDiscovery-arbejdsproces adresserer disse nye former for kommunikation og samarbejde.

Funktionen til samtalekontekster i Advanced eDiscovery er designet til at hjælpe dig med at identificere kontekstafhængigt indhold og producere særskilte samtalevisninger. Denne funktion giver dig mulighed for effektivt og hurtigt at gennemgå komplette chatsamtaler (også kaldet samtaler med tråde), der *genereres* i platforme som f.eks. Microsoft Teams.

Med samtaler, der er forskellige, kan du bruge indbyggede funktioner til at genoprette, gennemgå og eksportere samtaler med tråde. Brug Advanced eDiscovery samtale om at:

- Bevar unikke metadata på meddelelsesniveau på tværs af alle meddelelser i en samtale.

- Indsaml kontekstafhængige meddelelser omkring dine søgeresultater.

- Gennemse, anmærke og redigere samtaler med tråde igen.

- Eksportér individuelle meddelelser eller samtaler med tråde

## <a name="terminology"></a>Terminologi

Her er nogle få definitioner, der kan hjælpe dig med at komme i gang med at bruge samtalerne.

- **Meddelelser:** Repræsenterer den mindste enhed af en samtale. Meddelelser kan variere i størrelse, struktur og metadata.

- **Samtale:** Repræsenterer en gruppering af en eller flere meddelelser. Samtaler kan være repræsenteret på forskellige måder på tværs af forskellige programmer. I nogle programmer er der en eksplicit handling, der kommer fra at besvare en eksisterende meddelelse. Samtaler oprettes eksplicit som et resultat af denne brugerhandling. Her er f.eks. et skærmbillede af en kanalsamtale i Microsoft Teams.

   ![Microsoft Teams kanalsamtale.](../media/threadedchat.png)

   I andre apps (f.eks. gruppechatmeddelelser i Teams) er der ikke en formel svarkæde, og i stedet vises meddelelser som en "flad flod af meddelelser" i en enkelt tråd. I disse typer apps udledes samtaler fra en gruppe af meddelelser, der forekommer inden for et bestemt tidspunkt. Denne "blød gruppering" af meddelelser (i modsætning til en svarkæde) repræsenterer "frem og tilbage"-samtalen om et bestemt interessant emne.

## <a name="step-1-create-a-draft-collection"></a>Trin 1: Opret en kladdesamling

Når du har identificeret relevante forældre og indholdsplaceringer, kan du oprette en søgning for at finde potentielt relevant indhold. På fanen **Samlinger i** alle Advanced eDiscovery kan du oprette en samling ved at klikke **på Ny samling** og følge guiden. Du kan finde oplysninger om, hvordan du opretter en samling, opbygger en søgeforespørgsel og får vist søgeresultaterne under [Opret en kladdesamling](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Trin 2: Bestil en kladdesamling til et korrektursæt

Når du har gennemset og færdiggjort søgeforespørgslen i en samling, kan du føje søgeresultaterne til et gennemsynssæt. Når du tilføjer dine søgeresultater i et korrektursæt, kopieres de oprindelige data til et Azure Storage-område for at muliggøre gennemsyns- og analyseprocessen. Du kan finde flere oplysninger om at føje søgeresultater til et korrektursæt under [Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md).

Når du føjer elementer fra samtaler til et korrektursæt, kan du bruge indstillingen Samtaler med tråde til at indsamle kontekstafhængige meddelelser fra samtaler, der indeholder elementer, der opfylder søgekriterierne i samlingen. Når du har valgt indstillingen Samtaler i tråd, kan følgende ske:

  ![Hentning af samtale.](../media/messagesandconversations.png)

1. Ved hjælp af et nøgleord og en datoområdeforespørgsel returnerede søgningen et hit *på Meddelelse 3*. Denne meddelelse var en del af en større samtale illustreret af *CRC1*.

2. Når du tilføjer dataene i et gennemsynssæt og aktiverer indstillingerne for hentning af samtaler, Advanced eDiscovery gå tilbage og indsamle andre elementer i *CRC1*.

3. Når elementerne er blevet føjet til korrektursættet, kan du gennemse alle de enkelte meddelelser fra *CRC1*.

Hvis du vil aktivere indstillingen Samtaler med tråde, skal du se [Bekræfte en kladdesamling i et korrektursæt](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>Trin 3: Gennemse og eksportér samtaler med tråde

Når indholdet er blevet behandlet og føjet til korrektursættet, kan du begynde at gennemgå dataene i korrektursættet. Individuelle meddelelser trådes sammen og præsenteres som samtaler. Dette giver dig mulighed for at gennemse og eksportere kontekstafhængige samtaler.

  ![Samtalegennemsyn indstillet.](../media/ConversationRSOptions.PNG)

I de følgende afsnit beskrives gennemgang og eksport af samtaler.

### <a name="reviewing-conversations"></a>Gennemgå samtaler

I et korrektursæt kan du bruge følgende indstillinger til at lette gennemsynsprocessen.

- **Gruppere efter samtale:** Grupperer meddelelser i den samme samtale sammen for at gøre det nemmere for brugerne at forenkle og fremskynde gennemsynsprocessen.

- **Oversigtsvisning:** Viser samtalen med tråde. I denne visning kan du se hele samtalen og også få adgang til metadataene for hver enkelt meddelelse.

   - Få vist metadata for individuelle meddelelser

   - Download individuelle meddelelser

- **Tekstvisning:** Leverer den udtrukne tekst til hele samtalen.

- **Anmærkningsvisning:** Gør det muligt at markere en trådopdetalt visning af samtalen. Alle meddelelser i samtalen deler det samme kommenterede dokument.

- **Mærkning:** Når du får vist samtaler i et gennemsynssæt, kan du få vist og anvende mærker ved at klikke **på** Mærkningspanel i panelet Kodning.

- **Kør samtalekonvertering igen:** Når meddelelser føjes til et samtalegennemsynssæt, køres der automatisk et konverteringsjob for at oprette oversigtstråde og anmærkevisninger. Hvis jobbet Samtalebeskæmpning mislykkes, kan du køre dette job igen ved at klikke på **handling > Opret PDF-filer** til samtaler i gennemsynssættet.

### <a name="exporting-conversations"></a>Eksport af samtaler

Du kan se de indstillinger, du kan vælge, når du eksporterer samtaler fra et korrektursæt, under [Eksportere dokumenter fra et gennemsynssæt](export-documents-from-review-set.md#export-options).

Du kan eksportere hele chatsamtaler i en enkelt PDF-fil, eller du kan eksportere hver chatmeddelelse i en samtale som en individuel fil.

## <a name="more-information"></a>Flere oplysninger

Du kan få mere at vide om, hvordan du gennemser sagsdata Advanced eDiscovery, i følgende artikler:

- [Forespørg og filtrer indhold i et korrektursæt](review-set-search.md)
- [Tag dokumenter i et korrektursæt](tagging-documents.md)
- [Få vist sagsdata](view-documents-in-review-set.md)
- [Analysere sagsdata](analyzing-data-in-review-set.md)
- [Eksportere sagsdata](exporting-data-ediscover20.md)
