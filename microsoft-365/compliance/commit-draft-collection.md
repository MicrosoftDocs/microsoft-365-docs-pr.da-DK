---
title: Bekræft en kladdesamling til et valideringssæt
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
description: Når du har oprettet og gentaget en kladdesamling, kan du bekræfte den til et korrektursæt. Når du bekræfter en kladde til en samling, tilføjes de indsamlede elementer for at gennemse dem, der er angivet i sagen. Når de indsamlede elementer er i korrektursættet, kan du analysere, gennemse og eksportere dem.
ms.openlocfilehash: c798981d485b6128e76ea3f0c0fbf189b4f9634a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090467"
---
# <a name="commit-a-draft-collection-to-a-review-set-in-ediscovery-premium"></a>Send en kladdesamling til et korrektursæt i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du er tilfreds med de elementer, du har indsamlet i en kladdesamling, og er klar til at analysere, mærke og gennemse dem, kan du føje en samling til et korrektursæt i tilfælde af. Når du bekræfter en kladde af en samling til et korrektursæt, kopieres indsamlede elementer fra deres oprindelige indholdsplacering i Microsoft 365 til et korrektursæt. Et anmeldelsessæt er en sikker, Microsoft-leveret Azure Storage placering i Microsoft-cloudmiljøet.

## <a name="commit-a-draft-collection-to-a-review-set"></a>Bekræft en kladdesamling til et valideringssæt

1. Åbn sagen Microsoft Purview eDiscovery (Premium) på Microsoft Purview-overholdelsesportalen, og vælg derefter fanen **Samlinger** for at få vist en liste over samlingerne i sagen.

   ![Liste over samlinger i en sag.](../media/CommitDraftCollections1.png)

   > [!TIP]
   > En værdi for `Estimated` i kolonnen **Status** identificerer kladdesamlinger, der kan føjes til et korrektursæt. En status for `Committed` angiver, at en samling allerede er føjet til et korrektursæt.

2. På siden **Samlinger** skal du vælge den kladdesamling, du vil bekræfte til et gennemsynssæt.

3. Nederst på pop op-siden skal du vælge **HandlingerVælg** >  samling.

4. Klik på **Næste** i guiden til redigering af samlinger, indtil siden **Gem kladde eller indsaml** vises.

5. Konfigurer følgende indstillinger:

   1. Vælg **Indsaml elementer, og føj til korrektursæt**.

   2. Beslut, om du vil føje samlingen til et nyt korrektursæt (som oprettes, når du har sendt samlingen) eller føje den til et eksisterende korrektursæt. Fuldfør dette afsnit baseret på din beslutning.

   3. Konfigurer yderligere indstillinger for samling:

      ![Konfigurer yderligere indstillinger for samling.](../media/AeDAdditionalCollectionSettings.png).

       a. **Teams og Yammer meddelelser**: Vælg denne indstilling for at føje samtaletråde til den samling, der indeholder de chatelementer, der returneres af søgeforespørgslen i samlingen. Det betyder, at chatsamtalen, der indeholder elementer, der stemmer overens med søgekriterierne, rekonstrueres. Dette giver dig mulighed for at gennemse chatelementer i konteksten af samtalen frem og tilbage. Du kan finde flere oplysninger [under Samtaletråd i eDiscovery (Premium)](conversation-review-sets.md).

       b. **Vedhæftede filer i skyen**: Vælg denne indstilling for at inkludere moderne vedhæftede filer eller sammenkædede filer, når samlingsresultaterne føjes til korrektursættet. Det betyder, at målfilen for en moderne vedhæftet fil eller sammenkædet fil føjes til korrektursættet.

       > [!NOTE]
       > De to muligheder for at indsamle kontekstafhængige Teams og Yammer meddelelser og vedhæftede filer i skyen er valgt som standard (og nedtonet) for sager, der blev oprettet ved hjælp af det nye sagsformat. Du kan få flere oplysninger under [Brug det nye sagsformat](advanced-ediscovery-new-case-format.md).

       c. **Delvist indekserede elementer**: Vælg denne indstilling for at føje delvist indekserede elementer fra flere datakilder til korrektursættet. Hvis samlingen søgte i flere datakilder (som angivet på siden **Yderligere placeringer** i guiden Samlinger), kan der være delvist indekserede elementer fra disse placeringer, som du vil føje til korrektursættet. Datakilder med frihedsberøvelse og ingen varetægtsfængsling har typisk ikke delvist indekserede elementer. Det skyldes, at den avancerede indekseringsproces omindekserer elementer, når datakilder med frihedsberøvelse og ingen varetægtsfængsling føjes til en sag. Hvis du tilføjer delvist indekserede elementer, øges antallet af elementer, der føjes til korrektursættet. <p> Når delvist indekserede elementer er føjet til korrektursættet, kan du anvende et filter for specifikt at få vist disse elementer. Du kan få flere oplysninger under [Filtrer delvist indekserede elementer](review-set-search.md#filter-partially-indexed-items)

      d. **SharePoint versioner**: Vælg denne indstilling for at aktivere samlingen af alle versioner af et SharePoint dokument i henhold til versionsgrænserne og søgeparametrene for samlingen. Hvis du vælger denne indstilling, øges størrelsen af elementer, der føjes til korrektursættet, markant. Når dokumentversionerne er føjet til korrektursættet, 

   4. Konfigurer indstillingerne for at definere skaleringen af samlingen, der skal føjes til korrektursættet:

      - **Tilføj alle resultater for samlingen**: Vælg denne indstilling for at føje alle de elementer, der opfylder søgekriterierne for samlingen, til korrektursættet.

      - **Tilføj et eksempel på resultaterne af samlingen**: Vælg denne indstilling for at føje et eksempel på resultaterne af samlingen til korrektursættet i stedet for at tilføje alle resultater. Hvis du vælger denne indstilling, skal du klikke på **Rediger eksempelparametre** og vælge en af følgende indstillinger:

         - **Eksempel baseret på tillid**: Elementer fra samlingen føjes til korrektursættet bestemmes af de statistiske parametre, du har angivet. Hvis du typisk bruger et konfidensniveau og et interval, når du prøver resultater, skal du angive dem på rullelistene. Ellers skal du bruge standardindstillingerne.

         - **Tilfældigt eksempel**: Elementer fra samlingen føjes til korrektursættet på baggrund af et tilfældigt valg af den angivne procentdel af det samlede antal elementer, der returneres af søgningen.

6. På siden **Gennemse din samling** kan du gennemse de samlingsindstillinger, du konfigurerede på den forrige side. Klik på **Rediger** , hvis du vil ændre dem.

7. Klik på **Send** for at oprette kladdesamlingen. Der vises en side, der bekræfter, at samlingen blev oprettet.

## <a name="what-happens-after-you-commit-a-draft-collection"></a>Hvad sker der, når du har bekræftet en kladdesamling?

Når du overfører en kladdesamling til et korrektursæt, sker der følgende:

- Hvis du har oprettet et nyt korrektursæt, som samlingen skal bekræftes i, oprettes korrektursættet, og det vises i dette tilfælde under fanen **Gennemse sæt** . Status for det nye korrektursæt er **Klar**. Denne statusværdi betyder, at korrektursættet er blevet oprettet. Det betyder ikke, at samlingen er føjet til korrektursættet. Status for tilføjelse af elementer i samlingen til korrektursættet vises under fanen **Samlinger** .

- Søgeforespørgslen for samlingen køres igen. Det betyder, at de faktiske søgeresultater, der kopieres til korrektursættet, kan være anderledes end de anslåede resultater, der blev returneret, da samlingens søgning sidst blev kørt.

- Alle elementer i søgeresultaterne kopieres fra den oprindelige datakilde i livetjenesten og kopieres til en sikker Azure Storage placering i Microsoft-cloudmiljøet.

- Krypterede SharePoint og OneDrive dokumenter og krypterede filer, der er vedhæftet mails, som returneres i søgeresultaterne, dekrypteres, når du sender samlingen til et gennemsynssæt. Du kan gennemse og forespørge de dekrypterede filer i korrektursættet. Du kan finde flere oplysninger [under Dekryptering i Microsoft 365 eDiscovery-værktøjer](ediscovery-decryption.md).

- OCR-funktionen (Optical Character Recognition) udtrækker tekst fra billeder og inkluderer billedteksten med det indhold, der er føjet til et korrektursæt. Du kan få flere oplysninger i afsnittet [Optisk tegngenkendelse](#optical-character-recognition) i denne artikel.

- Når bekræftelsen er fuldført, ændres værdien af statuskolonnen for under fanen **Samlinger** til `Committed`.

## <a name="optical-character-recognition"></a>Optisk tegngenkendelse

Når du sender en samling til et korrektursæt, udtrækker optisk tegngenkendelsesfunktionalitet (OCR) i eDiscovery (Premium) automatisk tekst fra billeder og inkluderer billedteksten med det indhold, der er føjet til et korrektursæt. Du kan få vist den udtrukne tekst i Tekstfremviser for den valgte billedfil i korrektursættet. Dette giver dig mulighed for at foretage yderligere gennemgang og analyse af tekst i billeder. OCR understøttes til løse filer, vedhæftede filer i mails og integrerede billeder. Du kan finde en liste over billedfilformater, der understøttes for OCR, [under Understøttede filtyper i eDiscovery (Premium)](supported-filetypes-ediscovery20.md#image).

Du skal aktivere OCR-funktionalitet for hver enkelt sag, du opretter i eDiscovery (Premium). Du kan finde flere oplysninger under [Konfigurer søge- og analyseindstillinger](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
