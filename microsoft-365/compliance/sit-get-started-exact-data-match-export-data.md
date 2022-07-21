---
title: Eksportér kildedata for at finde nøjagtigt datamatch baseret på følsom oplysningstype
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du eksporterer kildedata til præcise datamatchbaserede følsomme oplysninger.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 644c62dce3069899aba33737dd1e6452c81fee24
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66918062"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Eksportér kildedata for at finde nøjagtigt datamatch baseret på følsom oplysningstype


Den følsomme datatabel er en tekstfil, der indeholder rækker med værdier, som du sammenligner indholdet i dine dokumenter med for at identificere følsomme data. Disse værdier kan være personlige identificerbare oplysninger, produktposter eller andre følsomme data i tekstformat, som du vil registrere i indhold og udføre beskyttende handlinger på.

Når dataene er blevet eksporteret i et af de understøttede formater, kan du fortsætte med oprettelsen af et EDM-skema.

## <a name="defining-your-edm-sensitive-type"></a>Definition af din EDM-følsomme type

Når du definerer din EDM-følsomme type, er en af de vigtigste beslutninger at definere, hvilke felter der skal være primære felter. Primære felter skal følge et mønster, der kan registreres, og defineres som søgbare felter (kolonner) i EDM-skemaet. Sekundære felter behøver ikke at følge et mønster, da de sammenlignes med al den tekst, der omgiver, svarer til de primære felter.

Brug disse regler som en hjælp til at bestemme, hvilke kolonner du skal bruge som primære felter:

- Hvis du skal registrere følsomme data baseret på tilstedeværelsen af en enkelt værdi, der svarer til et felt i din følsomme datatabel, uanset om der er andre følsomme data omkring dem, skal kolonnen defineres som et primært element for en EDM-type. 
- Hvis der skal registreres flere kombinationer af forskellige felter i din følsomme datatabel i indhold, skal du identificere de kolonner, der er fælles for de fleste af disse kombinationer, og angive dem som primære elementer og kombinationer af de andre felter som sekundære elementer.
- Hvis en kolonne, du vil bruge som et primært felt, ikke følger et mønster, der kan registreres, f.eks. en hvilken som helst tekststreng eller følger mønstre, der kan registreres, og som ville være til stede et sted i en stor procentdel af dokumenter eller mails, kan du prøve at vælge andre bedre strukturerede kolonner som primære elementer.

Hvis du f.eks. har kolonnerne `full name`, `date of birth`, `account number`og `Social Security Number`, selvom for- og efternavne er de kolonner, der er fælles for de forskellige kombinationer af data, du vil registrere, følger disse strenge ikke let identificerbare mønstre og kan være svære at definere som en følsom oplysningstype. Det skyldes, at nogle navne måske ikke engang starter med store bogstaver, de kan være udformet med to, tre eller flere ord og kan endda indeholde tal eller andre ikke-alfabetiske tegn. Fødselsdato kan lettere identificeres, men da hver e-mail og de fleste dokumenter vil indeholde mindst én dato, er det heller ikke en god kandidat. Cpr-numre og kontonumre er velegnede til brug som primært felt.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Gem følsomme data i formatet .csv, .tsv eller pipesepareret

1. Identificer de følsomme oplysninger, du vil bruge. Eksportér dataene til en app, f.eks. Microsoft Excel, og gem filen i en tekstfil. Filen kan gemmes i .csv(kommaseparerede værdier), .tsv-format (tabulatorseparerede værdier) eller pipeseparerede (|). .tsv-formatet anbefales i de tilfælde, hvor dine dataværdier kan indeholde kommaer, f.eks. gadeadresser.
Datafilen kan maksimalt indeholde:
   - Op til 100 millioner rækker følsomme data
   - Op til 32 kolonner (felter) pr. datakilde
   - Op til 5 kolonner (felter), der er markeret som søgbare

2. Strukturér de følsomme data i filen .csv eller .tsv, så den første række indeholder navnene på de felter, der bruges til EDM-baseret klassificering. I filen kan du have feltnavne, f.eks. "ssn", "fødselsdato", "fornavn", "efternavn". Kolonneoverskriftsnavne må ikke indeholde mellemrum eller understregningstegn. Eksempelfilen .csv, som vi bruger i denne artikel, hedder *f.eks.PatientRecords.csv*, og kolonnerne omfatter *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN* med mere.

3. Vær opmærksom på formatet af de følsomme datafelter. felter, der kan indeholde kommaer i deres indhold. En adresse, der indeholder værdien "Seattle,WA", fortolkes f.eks. som to separate felter, når den fortolkes, hvis formatet .csv vælges. For at undgå dette skal du bruge formatet .tsv eller omgivet af kommaet, der indeholder værdier, med dobbelte anførselstegn i den følsomme datatabel. Hvis komma, der indeholder værdier, også indeholder mellemrum, skal du oprette et brugerdefineret SIT, der svarer til det tilsvarende format. For eksempel et SIT, der registrerer streng med flere ord med kommaer og mellemrum i den.

## <a name="next-step"></a>Næste trin

- [Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Se også

- [Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
