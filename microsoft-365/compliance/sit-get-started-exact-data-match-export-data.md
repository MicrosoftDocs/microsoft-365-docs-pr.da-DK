---
title: Eksportér kildedata for en nøjagtig dataoverensstemmelsesbaseret type af følsomme oplysninger
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
description: Få mere at vide om, hvordan du eksporterer kildedata for en nøjagtig dataoverensstemmelsesbaseret følsom oplysningstype.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9a1ee56708018ddfddf141499bf4cf5f9ee02449
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63601034"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Eksportér kildedata for en nøjagtig dataoverensstemmelsesbaseret type af følsomme oplysninger


Den følsomme datatabel er en tekstfil, der indeholder rækker med værdier, som du skal sammenligne indhold i dine dokumenter med for at identificere følsomme data. Disse værdier kan være personligt identificerbare oplysninger, produktposter eller andre følsomme data i tekstform, som du vil registrere i indhold og udføre beskyttende handlinger på.

Når dataene er blevet eksporteret i et af de understøttede formater, kan du fortsætte med oprettelsen af et EDM-skema.

## <a name="defining-your-edm-sensitive-type"></a>Definition af din EDM-følsomme type

Når du definerer din EDM-følsomme type, er en af de mest kritiske beslutninger, hvilke felter der skal være primære felter. Primære felter skal følge et registrereligt mønster og defineres som søgbare felter (kolonner) i dit EDM-skema. Sekundære felter behøver ikke at følge et mønster, da de sammenlignes med al den tekst, der omgiver felterne, til de primære felter.

Brug disse regler som en hjælp til at beslutte, hvilke kolonner du skal bruge som primære felter:

- Hvis du skal registrere følsomme data baseret på tilstedeværelsen af en enkelt værdi, der matcher et felt i din følsomme datatabel, uanset tilstedeværelsen af andre følsomme data, der omgiver den, skal kolonnen defineres som et primært element for en EDM-type. 
- Hvis der skal registreres flere kombinationer af forskellige felter i din følsomme datatabel i indhold, skal du identificere de kolonner, der er fælles for de fleste af disse kombinationer, og angive dem som primære elementer og kombinationer af de andre felter som sekundære elementer.
- Hvis en kolonne, du vil bruge som primært felt, ikke følger et registreret mønster, f.eks. en tekststreng eller følger registrerbare mønstre, der findes et sted i en stor procentdel af dokumenter eller mails, kan du prøve at vælge andre bedre strukturerede kolonner som primære elementer.

`full name`Hvis du f.eks. har kolonnerne , `date of birth`, `account number``Social Security Number`og , selvom fornavne og efternavne er de kolonner, der skal være fælles for de forskellige kombinationer af data, du vil registrere, følger disse strenge ikke let identificerbare mønstre og kan være svære at definere som en følsom oplysningstype. Dette skyldes, at nogle navne måske ikke engang starter med store bogstaver, de kan være udformet med to, tre eller flere ord og kan endda indeholde tal eller andre ikke-alfabetiske tegn. Fødselsdato kan nemmere identificeres, men da alle mails og de fleste dokumenter indeholder mindst én dato, er det heller ikke en god kandidat. CPR-numre og kontonumre er gode kandidater til brug som primært felt.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Gem følsomme data i .csv.tsv- eller pipe-separated format

1. Identificer de følsomme oplysninger, du vil bruge. Eksportér dataene til en app, f.eks. Microsoft Excel, og gem filen i en tekstfil. Filen kan gemmes i .csv (kommaseparerede værdier), .tsv-format (tabulatorseparerede værdier) eller i |-format. Formatet .tsv anbefales i tilfælde, hvor dine dataværdier kan inkludere kommaer, f.eks. postadresser.
Datafilen kan maksimalt indeholde:
   - Op til 100 millioner rækker med følsomme data
   - Op til 32 kolonner (felter) pr. datakilde
   - Op til 5 kolonner (felter), der er markeret som søgbare

2. Strukturere de følsomme data i .csv- eller .tsv-filen, så den første række indeholder navnene på de felter, der bruges til EDM-baseret klassificering. I filen har du muligvis feltnavne som "ssn", "fødselsdato", "fornavn", "efternavn". Kolonneoverskriftsnavnene må ikke indeholde mellemrum eller understregningstegn. Eksempelfilen .csv, som vi bruger i denne artikel, hedder *f.eks.PatientRecords.csv*, og kolonnerne inkluderer *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN* og meget mere.

3. Vær opmærksom på formatet af de følsomme datafelter. Felter, der kan indeholde kommaer i deres indhold, f.eks. en postadresse, der indeholder værdien "Seattle,WA", bliver fortolket som to separate felter, når fortolkes, hvis formatet .csv valgt. Du kan undgå dette ved at bruge .tsv-formatet eller omgive kommaet, der indeholder værdier, ved hjælp af dobbelte anførselstegn i den følsomme datatabel. Hvis komma, der indeholder værdier, også indeholder mellemrum, skal du oprette et brugerdefineret SIT, der svarer til det tilsvarende format. Eksempelvis en SIT, der registrerer streng med flere ord med kommaer og mellemrum i den.

## <a name="next-step"></a>Næste trin

- [Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Se også

- [Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
