---
title: Konfigurer søge- og analyseindstillinger – eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.custom: seo-marvel-mar2020
description: Konfigurer indstillinger for Microsoft Purview eDiscovery (Premium), der gælder for alle korrektursæt i en sag. Dette omfatter indstillinger for analyse og optisk tegngenkendelse.
ms.openlocfilehash: 315448606e99a768bacd8d7d4ac7f858c79c7bed
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624559"
---
# <a name="configure-search-and-analytics-settings-in-ediscovery-premium"></a>Konfigurer søge- og analyseindstillinger i eDiscovery (Premium)

Du kan konfigurere indstillinger for hver Microsoft Purview eDiscovery (Premium) sag for at styre følgende funktionalitet.

- Næsten dubletter og mailtråde

- Temaer

- Automatisk genereret forespørgsel for korrektursæt

- Ignorer tekst

- Optisk tegngenkendelse

Sådan konfigurerer du søge- og analyseindstillinger for en sag:

1. Vælg sagen på siden **eDiscovery (Premium).**

2. Klik på **Vælg** under **Søg & analyse** under fanen **Indstillinger**.

   Siden med indstillinger for sag vises. Disse indstillinger anvendes på alle korrektursæt i en sag.

   ![Konfigurer analyse- og søgeindstillinger for en eDiscovery-sag (Premium).](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Næsten dubletter og mailtråde

I dette afsnit kan du angive parametre for registrering af dubletter i nærheden af registrering af dubletter og mailtrådning. Du kan få flere oplysninger [under Næsten registrering af dubletter](near-duplicate-detection-in-advanced-ediscovery.md) og [Mailtrådning](email-threading-in-advanced-ediscovery.md).

- **Næsten dubletter/mailtrådning:** Når funktionen er slået til, medtages registrering af dubletter i nærheden af registrering af dubletter og mailtråde som en del af arbejdsprocessen, når du kører analyse af dataene i et korrektursæt.

- **Tærskel for dokument- og mail-lighed:** Hvis lighedsniveauet for to dokumenter er over tærsklen, placeres begge dokumenter i det samme næsten duplikerede sæt.

- **Minimum-/maksimumantal ord:** Disse indstillinger angiver, at der i nærheden af dubletter og mailtrådanalyse kun udføres på dokumenter, der har mindst det mindste antal ord og højst det maksimale antal ord.

## <a name="themes"></a>Temaer

I dette afsnit kan du angive parametre for temaer. Du kan få flere oplysninger under [Temaer](themes-in-advanced-ediscovery.md).

- **Temaer:** Når den er slået til, udføres temaerklynger som en del af arbejdsprocessen, når du kører analyser på dataene i et korrektursæt.

- **Maksimalt antal temaer:** Angiver det maksimale antal temaer, der kan genereres, når du kører analyser på dataene i et korrektursæt.

- **Medtag tal i temaer:** Når funktionen er slået til, medtages tal (der identificerer et tema) ved generering af temaer. 

- **Juster det maksimale antal temaer dynamisk:** I visse situationer er der muligvis ikke nok dokumenter i et korrektursæt til at producere det ønskede antal temaer. Når denne indstilling er aktiveret, justerer eDiscovery (Premium) det maksimale antal temaer dynamisk i stedet for at forsøge at gennemtvinge det maksimale antal temaer.

## <a name="review-set-query"></a>Gennemse sætforespørgsel

Hvis du markerer afkrydsningsfeltet **Opret automatisk en gemt søgning til gennemsyn efter analyse** , genererer eDiscovery (Premium) automatisk forespørgsel, der er angivet til gennemsyn, med navnet **Til gennemsyn.** 

![Den automatisk genererede forespørgsel til gennemsyn.](../media/AeDForReviewQuery.png)

Denne forespørgsel filtrerer grundlæggende dubletelementer fra korrektursættet. Det giver dig mulighed for at gennemse de entydige elementer i korrektursættet. Denne forespørgsel oprettes kun, når du kører analyser for et gennemsynssæt i dette tilfælde. Du kan få flere oplysninger om forespørgsler i korrektursæt under [Forespørg om dataene i et korrektursæt](review-set-search.md).

## <a name="ignore-text"></a>Ignorer tekst

Der er situationer, hvor bestemt tekst vil forringe kvaliteten af analyser, f.eks. lange ansvarsfraskrivelser, der føjes til mails, uanset indholdet af mailen. Hvis du kender til tekst, der skal ignoreres, kan du udelade den fra analyse ved at angive tekststrengen og analysefunktionen (næsten dubletter, Mailtråde, Temaer og Relevans), som teksten skal udelades for. Brug af regulære udtryk (RegEx) som ignoreret tekst understøttes også.

## <a name="optical-character-recognition-ocr"></a>Optisk tegngenkendelse (OCR)

Når denne indstilling er slået til, køres OCR-behandling på billedfiler. OCR-behandling køres i følgende situationer:

- Når tilsynsførende og [ikke-frihedsberøvende datakilder](non-custodial-data-sources.md) føjes til en sag. Når OCR anvendes på billedfiler, kan der søges i teksten i disse filer under en samling. OCR-behandling udføres under [den avancerede indekseringsproces](indexing-custodian-data.md) . OCR køres kun på elementer, der behandles under avanceret indeksering. Hvis en stor PDF-fil, der er delvist indekseret eller har andre indekseringsfejl, f.eks. behandles under avanceret indeksering, anvendes OCR også for filen. OCR-behandling sker med andre ord kun på filer, der indekseres igen under den avancerede indekseringsproces. Det betyder, at der kan være situationer, hvor tilsynsførende føjes til en sag, men nogle vedhæftede filer i mails behandles ikke for OCR, fordi disse filer ikke behandles under avanceret indeksering.

- Når indhold fra andre datakilder (der ikke er knyttet til en tilsynsførende og føjet til sagen i en datakilde, der ikke er frihedsberøvende), føjes til et korrektursæt.

Når data er føjet til et korrektursæt, kan billedtekst gennemses, søges, mærkes og analyseres. Du kan få vist den udtrukne tekst i Tekstfremviser for den valgte billedfil i korrektursættet. Du kan finde flere oplysninger under:

- [Avanceret indeksering af data fra tilsynsførende](indexing-custodian-data.md)

- [Føj søgeresultater til et korrektursæt](add-data-to-review-set.md#optical-character-recognition)

- [Understøttede billedfiltyper](supported-filetypes-ediscovery20.md#image)
