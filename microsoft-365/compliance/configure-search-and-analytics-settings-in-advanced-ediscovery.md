---
title: Konfigurer indstillinger for søgning og analyse – Advanced eDiscovery
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
ms.custom: seo-marvel-mar2020
description: Konfigurer Advanced eDiscovery, der gælder for alle gennemsynssæt i en sag. Dette omfatter indstillinger for analyse og optisk tegngenkendelse.
ms.openlocfilehash: 65175950a430dd6b43cac207e16a17cf02d1bbbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589513"
---
# <a name="configure-search-and-analytics-settings-in-advanced-ediscovery"></a>Konfigurer indstillinger for søgning og analyse i Advanced eDiscovery

Du kan konfigurere indstillingerne for hver Advanced eDiscovery store og små bogstaver for at styre følgende funktioner.

- Nær dubletter og mailtrådning

- Temaer

- Autogenereret forespørgsel for korrektursæt

- Ignorer tekst

- Optisk tegngenkendelse

Sådan konfigureres indstillinger for søgning og analyse for en sag:

1. Vælg **Advanced eDiscovery** under fanen Store og små bogstaver.

2. På fanen **Indstillinger** under **Søgeanalyser skal & klikke** på **Vælg**.

   Siden med indstillinger for store og små bogstaver vises. Disse indstillinger anvendes på alle korrektursæt i en sag.

   ![Konfigurer analyse- og søgeindstillinger for en Advanced eDiscovery sag.](../media/AeDCaseSettings.png)

## <a name="near-duplicates-and-email-threading"></a>Nær dubletter og mailtrådning

I dette afsnit kan du angive parametre for registrering af dubletter, registrering af dubletter og mailtrådning. Få mere at vide under [Nær duplikering af](near-duplicate-detection-in-advanced-ediscovery.md) registrering [og Mailtrådning](email-threading-in-advanced-ediscovery.md).

- **Nær dubletter/mailtrådning:** Når denne er slået til, medtages registrering af dubletter, registrering af nær dubletter og mailtrådning som en del af arbejdsprocessen, når du kører analyser af dataene i et gennemsynssæt.

- **Grænseværdi for lighed mellem dokumenter og mails:** Hvis lighedsniveauet for to dokumenter er over grænsen, sættes begge dokumenter i det samme nær dublerede sæt.

- **Antal ord for minimum/maksimum:** Disse indstillinger angiver, at nær dubletter og mailtrådning kun udføres på dokumenter, der har mindst det mindste antal ord og højst det maksimale antal ord.

## <a name="themes"></a>Temaer

I denne sektion kan du angive parametre for temaer. Du kan finde flere oplysninger under [Temaer](themes-in-advanced-ediscovery.md).

- **Temaer:** Når den er slået til, udføres gruppering af temaer som en del af arbejdsprocessen, når du kører analyser på dataene i et korrektursæt.

- **Maksimale antal temaer:** Angiver det maksimale antal temaer, der kan genereres, når du kører analyser på dataene i et gennemsynssæt.

- **Medtag tal i temaer:** Når det er slået til, medtages tal (der identificerer et tema), når du genererer temaer. 

- **Juster det maksimale antal temaer dynamisk:** I visse situationer er der måske ikke nok dokumenter i et korrektursæt til at oprette det ønskede antal temaer. Når denne indstilling er aktiveret, Advanced eDiscovery indstiller indstillingen det maksimale antal temaer dynamisk i stedet for at forsøge at gennemtvinge det maksimale antal temaer.

## <a name="review-set-query"></a>Gennemse sætforespørgsel

Hvis du markerer **afkrydsningsfeltet** Opret automatisk en gemt søgning til gennemsyn efter analyse, skal Advanced eDiscovery autogenerates gennemsynssætforespørgsel **navngivet Til gennemsyn.** 

![Den autogenererede forespørgsel Til gennemsyn.](../media/AeDForReviewQuery.png)

Denne forespørgsel filtrerer dubletter fra gennemsynssættet. Dette giver dig mulighed for at gennemse de entydige elementer i gennemsynssættet. Denne forespørgsel oprettes kun, når du kører analyser for et gennemsynssæt i sagen. Hvis du vil have mere at vide om gennemsynssætforespørgsler, skal [du se Forespørge dataene i et gennemsynssæt](review-set-search.md).

## <a name="ignore-text"></a>Ignorer tekst

Der er situationer, hvor bestemt tekst vil forringe kvaliteten af analyser, f.eks. lange ansvarsfraskrivelser, der føjes til mails uanset indholdet af mailen. Hvis du kender til tekst, der skal ignoreres, kan du udelukke den fra analyser ved at angive tekststrengen og analysefunktionaliteten (næsten dubletter, Mailtrådning, Temaer og Relevans), som teksten skal udelades for. Brug af regulære udtryk (RegEx) som ignoreret tekst understøttes også.

## <a name="optical-character-recognition-ocr"></a>Optisk tegngenkendelse (OCR)

Når denne indstilling er slået til, køres OCR-behandling på billedfiler. OCR-behandling køres i følgende situationer:

- Når ledende leverandører [og ikke-registrerede datakilder føjes](non-custodial-data-sources.md) til en sag. Når OCR anvendes på billedfiler, vil teksten i disse filer være søgbar under en samling. OCR-behandling udføres under [den avancerede indekseringsproces](indexing-custodian-data.md) . OCR køres kun på elementer, der behandles under avanceret indeksering. Hvis f.eks. en stor PDF-fil, der er delvist indekseret eller har andre indekseringsfejl, behandles under avanceret indeksering, vil filen også have OCR anvendt. Med andre ord sker OCR-behandling kun på filer, der indekseres igen under avanceret indekseringsproces. Det betyder, at der kan være situationer, hvor hæftninger føjes til en sag, men nogle vedhæftede filer i mails ikke behandles for OCR, fordi disse filer ikke behandles under avanceret indeksering.

- Når indhold fra andre datakilder (som ikke er knyttet til en inficator og føjet til sagen i en ikke-vigtig datakilde) føjes til et gennemsynssæt.

Når dataene er føjet til et korrektursæt, kan billedtekst gennemses, søges, mærkes og analyseres. Du kan få vist den udpakkede tekst i Tekstvisning for den valgte billedfil i korrektursættet. Du kan finde flere oplysninger under:

- [Avanceret indeksering af data for oversigter](indexing-custodian-data.md)

- [Føje søgeresultater til et korrektursæt](add-data-to-review-set.md#optical-character-recognition)

- [Understøttede billedfiltyper](supported-filetypes-ediscovery20.md#image)
