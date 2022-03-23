---
title: Bekræfte en kladdesamling i et korrektursæt
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
description: Når du har oprettet og genaktiveret en kladdesamling, kan du bekræfte den i et gennemsynssæt. Når du opbevarer en kladdesamling, tilføjes de indsamlede elementer for at gennemgå de i sagen. Når de indsamlede elementer er i korrektursættet, kan du analysere, gennemse og eksportere dem.
ms.openlocfilehash: d74d1b062101973d2d3cb055700c59a2d25c0d14
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63591969"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-advanced-ediscovery"></a>Bestil en kladdesamling til et korrektursæt i Advanced eDiscovery

Når du er tilfreds med de elementer, du har indsamlet i en kladdesamling, og er klar til at analysere, mærke og gennemgå dem, kan du føje en samling til et gennemsynssæt i sagen. Når du opbevarer en kladdesamling i et korrektursæt, kopieres indsamlede elementer fra deres oprindelige indholdsplacering Microsoft 365 til et korrektursæt. Et korrektursæt er en sikker, Microsoft-leveret Azure Storage i Microsoft-skyen.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Bekræfte en kladdesamling i et korrektursæt

1. I Microsoft 365 Overholdelsescenter skal du åbne Advanced eDiscovery store og små bogstaver og derefter vælge fanen Samlinger for at få vist  en liste over samlinger i sagen.

   ![Liste over samlinger i en sag.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > En værdi i `Estimated` kolonnen **Status** identificerer de kladdesamlinger, der kan føjes til et korrektursæt. En status angiver `Committed` , at en samling allerede er blevet føjet til et gennemsynssæt.

2. På siden **Samlinger skal** du vælge den kladdesamling, du vil bekræfte til et korrektursæt.

3. Nederst på pop op-siden skal du vælge **ActionsEdit** >  Collection.

4. I guiden til redigering af samling skal du **klikke på** Næste **, indtil siden Gem kladde** eller indsaml vises.

5. Konfigurer følgende indstillinger:

   1. Vælg **Indsaml elementer, og tilføj for at gennemse sættet**.

   2. Beslut, om du vil føje samlingen til et nyt korrektursæt (som er oprettet, når du har indsendt samlingen), eller føj den til et eksisterende korrektursæt. Udfyld denne sektion ud fra din beslutning.

   3. Konfigurer de ekstra indstillinger for samling:

      ![Konfigurer flere indstillinger for samling.](../media/AeDAdditionalCollectionSettings.png).

       a. **Teams og Yammer** meddelelser: Vælg denne indstilling for at føje samtaletråde til samlingen, der indeholder de chatelementer, der returneres af søgeforespørgslen i samlingen. Det betyder, at den chatsamtale, der indeholder elementer, der opfylder søgekriterierne, genoprettes. Dette giver dig mulighed for at gennemse chatelementer i konteksten for frem og tilbage-samtalen. Du kan få mere at [vide under Samtaletråde i Advanced eDiscovery](conversation-review-sets.md).

       b. **Vedhæftede skyfiler**: Vælg denne indstilling for at medtage moderne vedhæftede filer eller sammenkædede filer, når resultaterne af samlingen føjes til korrektursættet. Det betyder, at destinationsfilen for en moderne vedhæftet eller sammenkædet fil føjes til korrektursættet.

       > [!NOTE]
       > De to muligheder for at indsamle kontekstafhængige Teams og Yammer-meddelelser og vedhæftede skybaserede filer er valgt som standard (og nedtonet) for tilfælde, der blev oprettet ved hjælp af det nye sagsformat. Du kan få mere at vide [under Brug det nye format for store og små bogstaver](advanced-ediscovery-new-case-format.md).

       c. **Delvist indekserede elementer**: Vælg denne indstilling for at tilføje delvist indekserede elementer fra yderligere datakilder til gennemsynssættet. Hvis samlingen har søgt efter yderligere datakilder (som angivet på siden  Yderligere placeringer i guiden Samlinger), kan der være delvist indekserede elementer fra disse placeringer, som du vil føje til korrektursættet. Opbevaringsbaserede og ikke-oversigtsbaserede datakilder har typisk ikke delvist indekserede elementer. Det skyldes, at processen Avanceret indeksering genindfinder elementer, når du føjer datakilder, der ikke er til opbevaring, til en sag. Tilføjelse af delvist indekserede elementer øger desuden antallet af elementer, der føjes til korrektursættet. <p> Når delvist indekserede elementer er føjet til korrektursættet, kan du anvende et filter til specifikt at få vist disse elementer. Få mere at vide under [Filtrer delvist indekserede elementer](review-set-search.md#filter-partially-indexed-items)

      d. **SharePoint versioner**: Vælg denne indstilling for at aktivere samlingen af alle versioner af et SharePoint-dokument pr. versionsgrænser og søgeparametre i samlingen. Hvis du vælger denne indstilling, øges størrelsen på elementer, der føjes til korrektursættet betydeligt. Når dokumentversionerne er føjet til korrektursættet, 

   4. Konfigurer indstillingerne til at definere skalaen på samlingen, der skal føjes til korrektursættet:

      - **Tilføj alle samlingsresultater**: Vælg denne indstilling for at føje alle de elementer, der opfylder søgekriterierne i samlingen, til gennemsynssættet.

      - **Tilføj et eksempel på samlingsresultaterne**: Vælg denne indstilling for at føje et eksempel på resultaterne af samlingen til gennemsynssættet i stedet for at tilføje alle resultater. Hvis du vælger denne indstilling, skal du **klikke på Rediger eksempelparametre** og vælge en af følgende indstillinger:

         - **Stikprøve baseret på tillid**: Elementer fra samlingen føjes til korrektursættet bestemmes af de statistiske parametre, du angiver. Hvis du typisk bruger et tillidsniveau og interval, når der anvendes stikprøveresultater, skal du angive dem i rullelisten. Ellers skal du bruge standardindstillingerne.

         - **Tilfældigt eksempel**: Elementer fra samlingen føjes til korrektursættet baseret på et tilfældigt udvalg af den angivne procentdel af det samlede antal elementer, der returneres af søgningen.

6. På siden **Gennemse din samling** kan du gennemgå indstillingerne for samlingen, som du konfigurerede på den forrige side. Klik **på** Rediger, hvis du vil ændre dem.

7. Klik **på Send** for at oprette kladdesamlingen. Der vises en side, der bekræfter, at samlingen blev oprettet.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Hvad sker der, når du har bekræftet en kladdesamling

Når du har bekræftet en kladdesamling i et gennemsynssæt, sker følgende:

- Hvis du har oprettet et nyt korrektursæt, som samlingen skal bekræftes for, oprettes og vises korrektursættet på **fanen Gennemse sæt** i sagen. Status for det nye korrektursæt er **klar**. Denne statusværdi betyder, at gennemsynssættet er blevet oprettet. betyder det ikke, at samlingen er blevet føjet til gennemsynssættet. Status for tilføjelse af elementer i samlingen til korrektursættet vises på **fanen** Samlinger.

- Søgeforespørgslen for en samling køres igen. Det betyder, at de faktiske søgeresultater, der kopieres til korrektursættet, kan være anderledes end de anslåede resultater, der blev returneret, da søgningen efter samling sidst blev kørt.

- Alle elementer i søgeresultaterne kopieres fra den oprindelige datakilde i livetjenesten og kopieres til en sikker placering Azure Storage Microsoft-skyen.

- Krypterede SharePoint og OneDrive og krypterede filer vedhæftede mails, der returneres i søgeresultaterne, dekrypteres, når du binder samlingen til et gennemsynssæt. Du kan gennemse og forespørge de dekrypterede filer i gennemsynssættet. Få mere at vide under [Dekryptering i Microsoft 365 eDiscovery-værktøjer](ediscovery-decryption.md).

- Optisk tegngenkendelsesfunktionalitet (OCR) udtrækker tekst fra billeder og medtager billedteksten med det indhold, der er føjet til et korrektursæt. Du kan finde flere oplysninger i [afsnittet Optisk tegngenkendelse](#optical-character-recognition) i denne artikel.

- Når bekræftelsen er fuldført, ændres værdien af statuskolonnen i **fanen Samlinger** til `Committed`.

## <a name="optical-character-recognition"></a>Optisk tegngenkendelse

Når du har bekræftet en samling af et gennemsynssæt, udtrækker OCR-funktionalitet (Optical Character Recognition) i Advanced eDiscovery automatisk tekst fra billeder og inkluderer billedteksten med det indhold, der er føjet til et korrektursæt. Du kan få vist den udpakkede tekst i Tekstvisning for den valgte billedfil i korrektursættet. Dette giver dig mulighed for yderligere gennemgang og analyse af tekst i billeder. OCR understøttes til løse filer, vedhæftede filer i mails og integrerede billeder. Du kan finde en liste over billedfilformater, der understøttes af OCR, under [Understøttede filtyper Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Du skal aktivere OCR-funktionalitet for hvert tilfælde, som du opretter i Advanced eDiscovery. Få mere at vide under [Konfigurer indstillinger for søgning og analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
