---
title: Kontrollér din søgeforespørgsel for fejl
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
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan du registrerer fejl og slåfejl i din nøgleordsforespørgsel til eDiscovery-søgninger, før du kører søgningen.
ms.openlocfilehash: c820b72ea54e338d4f2fde475568bf2b1c22ba3b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587278"
---
# <a name="check-your-search-query-for-errors"></a>Kontrollér din søgeforespørgsel for fejl
  
Her er en liste over de tegn, der ikke understøttes, som vi kontrollerer for i søgeforespørgsler om indholdssøgning og grundlæggende eDiscovery. Ikke-understøttede tegn skjules ofte, og de medfører typisk en søgefejl eller returnerer utilsigtede resultater.
  
- **Intelligente anførselstegn** – Smarte enkelte og dobbelte anførselstegn (også kaldet krøllede) understøttes ikke. Du kan kun bruge lige anførselstegn i en søgeforespørgsel. 

- **Tegn, der ikke kan udskrives** , og kontroltegn – Tegn, der ikke kan udskrives, og kontroltegn repræsenterer ikke et skrevet symbol, f.eks. et alfanumerisk tegn. Eksempler på tegn, der ikke kan udskrives, og kontroltegn omfatter tegn, der formaterer tekst eller separate tekstlinjer. 

- **Venstre mod** højre- og højre mod venstre-tegn – Disse mærker er kontroltegn, der bruges til at angive tekstretningen for venstre mod højre-sprog (f.eks. engelsk og spansk) og højre mod venstre-sprog (f.eks. arabisk og hebraisk).

- **Små booleske** operatorer – Hvis du bruger en boolesk operator, f.eks. **OG**, **ELLER** og IKKE i en søgeforespørgsel, skal den indeholde store bogstaver. Når vi kontrollerer en forespørgsel for slåfejl, indikerer forespørgselssyntaksen ofte, at der bruges en boolesk operator, selvom der bruges små operatorer. f.eks.  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Hvad sker der, hvis en forespørgsel indeholder et ikke-understøttet tegn?

Hvis der ikke findes understøttede tegn i din forespørgsel, vises der en advarsel, hvor der står, at der blev fundet ikke-understøttede tegn, og foreslår et alternativ. Derefter har du mulighed for at beholde den oprindelige forespørgsel eller erstatte den med den foreslåede reviderede forespørgsel.

Her er et eksempel på den advarsel, der vises, når du klikker på Kontrollér **forespørgsel for** slåfejl i søgeforespørgslen i det forrige skærmbillede. Bemærk, at den oprindelige forespørgsel brugte intelligente anførselstegn og små booleske operatorer.
  
![Der vises en advarselsmeddelelse med en foreslået ændring af forespørgslen.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Sådan forhindrer du ikke-understøttede tegn i dine søgeforespørgsler

Ikke-understøttede tegn føjes typisk til en forespørgsel, når du kopierer forespørgslen eller dele af forespørgslen fra andre programmer (f.eks. Microsoft Word eller Microsoft Excel) og indsætter dem i nøgleordsfeltet på forespørgselssiden for en indholdssøgning. Den bedste måde at forhindre ikke-understøttede tegn på er ved blot at skrive forespørgslen i feltet nøgleord. Eller du kan kopiere en forespørgsel fra Word eller Excel og derefter indsætte den i en almindelig teksteditor, f.eks Microsoft Notesblok. Gem tekstfilen, **og vælg ANSI** **på rullelisten** Kodning. Dette fjerner eventuel formatering og tegn, der ikke understøttes. Derefter kan du kopiere og indsætte forespørgslen fra tekstfilen i forespørgselsfeltet nøgleord.
