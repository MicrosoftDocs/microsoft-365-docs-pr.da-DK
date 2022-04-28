---
title: Kontrollér søgeforespørgslen for fejl
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
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan du registrerer fejl og stavefejl i din nøgleordsforespørgsel for eDiscovery-søgninger, før du kører søgningen.
ms.openlocfilehash: 858db046cf78482e8540425a3f826f2ce28e78cd
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091781"
---
# <a name="check-your-search-query-for-errors"></a>Kontrollér søgeforespørgslen for fejl

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Her er en liste over de tegn, der ikke understøttes, som vi søger efter i søgeforespørgsler for Indholdssøgning og Microsoft Purview eDiscovery (Standard). Tegn, der ikke understøttes, er ofte skjult, og de medfører typisk en søgefejl eller returnerer utilsigtede resultater.
  
- **Smarte anførselstegn** – Smarte enkelte og dobbelte anførselstegn (også kaldet krøllede anførselstegn) understøttes ikke. Der kan kun bruges lige anførselstegn i en søgeforespørgsel. 

- **Tegn, der ikke kan udskrives, og styretegn** – Tegn, der ikke kan udskrives, og kontroltegn repræsenterer ikke et skrevet symbol, f.eks. et alfanumerisk tegn. Eksempler på tegn, der ikke kan udskrives, og styretegn omfatter tegn, der formaterer tekst eller adskiller tekstlinjer. 

- **Venstre mod højre- og højre mod venstre-mærker** – Disse mærker er kontroltegn, der bruges til at angive tekstretning for venstre mod højre-sprog (f.eks. engelsk og spansk) og højre mod venstre-sprog (f.eks. arabisk og hebraisk).

- **Booleske operatorer med små bogstaver** – Hvis du bruger en boolesk operator, f.eks **. AND**, **OR** og **NOT** i en søgeforespørgsel, skal den være med store bogstaver. Når vi kontrollerer en forespørgsel for stavefejl, angiver forespørgselssyntaksen ofte, at der bruges en boolesk operator, selvom der kan bruges små bogstaver. f.eks.  `(WordA or WordB) and (WordC or WordD)`.

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Hvad sker der, hvis en forespørgsel har et tegn, der ikke understøttes?

Hvis der findes tegn, der ikke understøttes, i forespørgslen, vises der en advarsel, hvor der står, at der blev fundet tegn, der ikke understøttes, og foreslår et alternativ. Du har derefter mulighed for at beholde den oprindelige forespørgsel eller erstatte den med den foreslåede reviderede forespørgsel.

Her er et eksempel på den advarselsmeddelelse, der vises, når du klikker på **Kontrollér forespørgsel for stavefejl** for søgeforespørgslen på det forrige skærmbillede. Bemærk, at den oprindelige forespørgsel brugte krøllede anførselstegn og booleske operatorer med små bogstaver.
  
![Der vises en advarsel med en foreslået revision af forespørgslen.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Sådan forhindrer du tegn, der ikke understøttes, i dine søgeforespørgsler

Ikke-understøttede tegn føjes typisk til en forespørgsel, når du kopierer forespørgslen eller dele af forespørgslen fra andre programmer (f.eks. Microsoft Word eller Microsoft Excel) og indsætter dem i nøgleordsfeltet på forespørgselssiden i en indholdssøgning. Den bedste måde at forhindre tegn, der ikke understøttes, er ved blot at skrive forespørgslen i nøgleordsfeltet. Du kan også kopiere en forespørgsel fra Word eller Excel og derefter indsætte den i en almindelig teksteditor, f.eks. Microsoft Notesblok. Gem tekstfilen, og vælg **ANSI** på rullelisten **Kodning** . Dette vil fjerne al formatering og tegn, der ikke understøttes. Derefter kan du kopiere og indsætte forespørgslen fra tekstfilen i forespørgselsfeltet med nøgleord.
