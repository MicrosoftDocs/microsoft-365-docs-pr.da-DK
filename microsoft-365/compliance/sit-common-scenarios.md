---
title: Almindelige brugsscenarier for følsomme oplysningstyper
f1.keywords:
- NOCSH
ms.author: chrfox
author: v-tophillips
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
description: Sådan implementeres almindelige følsomme oplysningstyper use case-scenarier
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39afa17fc7bf258848de9d5554b3dd56a1ce21b5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63607445"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Almindelige brugsscenarier for følsomme oplysningstyper

Denne artikel beskriver, hvordan du implementerer nogle almindelige scenarier med brug af store og små bogstaver (SIT) med følsomme oplysninger. Du kan bruge disse procedurer som eksempler og tilpasse dem til dine specifikke behov.

## <a name="protect-credit-card-numbers"></a>Beskyt kreditkortnumre

Contoso Bank skal klassificere de kreditkortnumre, de udsteder, som følsomme. Deres kreditkort starter med et sæt sekscifrede mønstre. De vil tilpasse standardkreditkortdefinitionen til kun at registrere kreditkortnumre, der starter med deres sekscifrede mønstre.

**Foreslået løsning**

1. Opret en kopi af kreditkortet SIT. Brug disse trin til [at kopiere og ændre en type af følsomme oplysninger](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) for at kopiere kreditkortet SIT.
1. Rediger mønsteret med høj tillid. Følg trinnene i redigere [eller slette det følsomme oplysningstypemønster](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Tilføj 'starter med'-tjek, og tilføj listen over placeringscifre (formateret & uformateret). Hvis du f.eks. vil sikre, at kun kreditkort, der starter med 411111 & 433512, betragtes som gyldige, skal du tilføje følgende på listen 4111 11, 4111-11, 411111, 4335 12, 4335-12 433512.
1. Gentag trin 2 & 3 for mønsteret med lille tillid.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Testnumre svarende til CPR-numre

Contoso har identificeret et par nicifrede testnumre, der udløser falske positive match i SSN-politikken til forebyggelse af datatab (DLP). De vil gerne udelade disse tal fra listen over gyldige matches for SSN.

**Foreslået løsning**

1. Opret en kopi af SSN SIT. Brug trinnene til at [kopiere og ændre en type af følsomme oplysninger for](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) at kopiere SSN SIT.
1. Rediger mønsteret med høj tillid. Følg trinnene i redigere [eller slette det følsomme oplysningstypemønster](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Adder de tal, der skal udelades, i den 'ekskluder bestemte værdier'-kontrol. Hvis du f.eks. vil udelukke 239-23-532-& 23923532, er det kun tilstrækkeligt 23923532 tilføjes
1. Gentag trin 2 & 3 for også at få andre tillidsmønstre

## <a name="phone-numbers-in-signature-trigger-match"></a>Telefon i match til signaturudløser

Australien baseret på Contoso finder, at telefonnumre i mailsignaturer udløser et match for deres DLP-politik for australiens firmanummer.

**Foreslået løsning**

Tilføj en "ikke"-gruppe i understøttende elementer ved hjælp af en nøgleordsliste, der indeholder ofte anvendte nøgleord i en mailsignatur, f.eks. "Telefon", "Mobil", "mail", "Tak, mange tak" osv. Bevar nærheden af denne liste med nøgleord til en mindre værdi som f.eks. 50 tegn for bedre nøjagtighed. Få mere at vide under [Introduktion til brugerdefinerede typer af følsomme oplysninger](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>Det er ikke muligt at udløse ABA-routingpolitik

DLP-politik kan ikke udløse ABA-routingnummerpolitik i store Excel-filer, fordi det nødvendige nøgleord ikke findes inden for 300 tegn.

**Foreslået løsning**

Opret en kopi af det indbyggede SIT, og rediger den for at ændre afstanden mellem listen over nøgleord fra "300 tegn" til "Hvor som helst i dokumentet".

> [!TIP]
> Du kan redigere listen over nøgleord for at medtage/udelade nøgleord, der er relevante for din organisation.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Det er ikke muligt at registrere kreditkortnumre med usædvanlige afgrænsere

Contoso Bank har bemærket, at nogle af medarbejderne deler kreditkortnumre med "/" som en afgrænser, f.eks. 4111/1111/1111/1111, som ikke registreres af standardkreditkortdefinitionen. Contoso vil gerne definere deres egen regex og validere den ved hjælp af LuhnCheck.

**Foreslået løsning**

1. Opret en kopi af kreditkort-SIT ved hjælp af trinnene [i Tilpasse en indbygget følsom oplysningstype](customize-a-built-in-sensitive-information-type.md).
1. Tilføje et nyt mønster
1. Vælg regulært udtryk i det primære element
1. Definer det regulære udtryk, der omfatter '/" som en del af det regulære udtryk, og vælg derefter validator, og vælg luhncheck eller func_credit_card for at sikre, at regex også videregiver LuhnCheck.

## <a name="ignore-a-disclaimer-notice"></a>Ignorer en meddelelse om ansvarsfraskrivelse

Mange organisationer tilføjer ansvarsfraskrivelser, hemmeligholdelseserklæringer, signaturer eller andre oplysninger øverst eller nederst i mails, der indtaster eller forlader deres organisationer og i nogle tilfælde også i organisationer. Medarbejderne selv sætter signaturer, herunder – motiverende citater, sociale beskeder osv. En ansvarsfraskrivelse eller signatur kan indeholde de udtryk, der findes i lexiconet for en CC, og kan generere en masse falske positive.  

En typisk ansvarsfraskrivelse kan f.eks. indeholde ord som f.eks. følsom eller fortrolig, og en politik, der søger efter følsomme oplysninger, vil registrere den som en hændelse, hvilket fører til mange falske positive. Hvis du giver kunderne mulighed for at ignorere ansvarsfraskrivelse, kan det reducere falske positive og øge effektiviteten af teamet til overholdelse af regler og standarder.

### <a name="example-of-disclaimer"></a>Eksempel på ansvarsfraskrivelse

Overvej følgende ansvarsfraskrivelse:

VIGTIG MEDDELELSE: Denne mail er kun beregnet til at blive modtaget af personer, der er berettiget til at modtage fortrolige oplysninger, som den kan indeholde. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er den tilsigtede modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Hvis SIT er konfigureret til at registrere et nøgleord fortroligt, vil mønsteret fremkalde et match, hver gang en ansvarsfraskrivelse bruges i mailen, hvilket fører til mange falske positive.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignorer ansvarsfraskrivelse ved hjælp af præfiks og suffiks i SIT

En måde at ignorere forekomster af nøgleord i ansvarsfraskrivelsen er ved at udelukke forekomster af nøgleord, der indledes med et præfiks og efterfulgt af et suffiks.

Overvej denne ansvarsfraskrivelse:

VIGTIG MEDDELELSE: Denne mail er kun beregnet til at blive modtaget af personer, der er berettiget til *at modtage fortrolige* **oplysninger, som den kan indeholde**. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er den tilsigtede modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Vi har to forekomster af nøgleordet "fortroligt", og hvis vi konfigurerer SIT til at ignorere forekomster af dette nøgleord med præfikser (kursiv i eksemplet) og efterfulgt af suffikser (med fed skrift i eksemplet), kan vi i de fleste tilfælde opnå ignorering af ansvarsfraskrivelser.

Sådan ignorerer du ansvarsfraskrivelsen ved hjælp af præfiks og suffiks:

1. Tilføj yderligere kontroller i den aktuelle SIT for at udelukke præfiks- og suffikstekst til nøgleordet, som vi vil ignorere i ansvarsfraskrivelsen.
1. Vælg at udelade præfikset, og skriv **indeholder** oplysninger i tekstfeltet **Præfikser**.
1. Vælg at udelade suffikset, og angiv **og** juridisk i tekstfeltet **Suffikser**.
1. Gentag denne proces for andre forekomster af nøgleordene i ansvarsfraskrivelsen, som vist i følgende grafik.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignorer ansvarsfraskrivelse ved at udelukke sekundære elementer

En anden måde at tilføje en liste over understøttende elementer (forekomster i ansvarsfraskrivelse), som skal udelades, er at udelukke sekundære elementer.

Overvej denne ansvarsfraskrivelse:

VIGTIG MEDDELELSE: Denne mail er kun beregnet til at blive modtaget af personer, der er berettiget til at modtage fortrolige oplysninger, som den kan indeholde. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er den tilsigtede modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Vi har to forekomster af nøgleordet "fortroligt" i dette eksempel. Hvis vi konfigurerer SIT til at ignorere forekomster af dette nøgleord i ansvarsfraskrivelsen (understreget med rødt), kan vi i de fleste tilfælde opnå at ignorere ansvarsfraskrivelser.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Du kan føje flere betingelser til mønsteret for at udelukke yderligere forekomster i ansvarsfraskrivelsen.":::

Sådan ignorerer du ansvarsfraskrivelsen ved hjælp af sekundære elementer:

1. Vælg **Ikke nogen af disse grupper** i de supplerende elementer.
1. Tilføj de forekomster af ansvarsfraskrivelse, som vi vil ignorere som en nøgleordsliste/ordbog.
1. Tilføj nøgleordene som en ny linje, som vi vil ignorere. Husk, at længden af hver tekst ikke må være mere end 50 tegn.
1. Angiv, at nærheden af dette element skal være inden for 50-60 tegn i det primære element.
