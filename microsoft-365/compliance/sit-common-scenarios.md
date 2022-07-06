---
title: Almindelige brugsscenarier for typer af følsomme oplysninger
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
description: Sådan implementerer du almindelige typer følsomme oplysninger ved hjælp af scenarier med store og små bogstaver
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 54945a3ac6f13ed541cef212305f713d8b5d2b73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633361"
---
# <a name="common-usage-scenarios-for-sensitive-information-types"></a>Almindelige brugsscenarier for typer af følsomme oplysninger

I denne artikel beskrives det, hvordan du implementerer nogle almindelige scenarier med brugsscenarier for følsomme oplysninger (SIT). Du kan bruge disse procedurer som eksempler og tilpasse dem til dine specifikke behov.

## <a name="protect-credit-card-numbers"></a>Beskyt kreditkortnumre

Contoso Bank skal klassificere de kreditkortnumre, de udsteder, som følsomme. Deres kreditkort starter med et sæt sekscifrede mønstre. De vil gerne tilpasse out of the box kreditkortdefinitionen til kun at registrere kreditkortnumre startende med deres sekscifrede mønstre.

**Foreslået løsning**

1. Opret en kopi af kreditkortet SIT. Brug trinnene til at [kopiere og redigere en type følsomme oplysninger](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) for at kopiere kreditkortet SIT.
1. Rediger mønsteret med høj genkendelsessikkerhed. Følg trinnene i [redigering eller sletning af mønsteret for følsomme oplysninger](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Tilføj afkrydsningsfeltet "starter med", og tilføj listen over bin-ciffer (formateret & ikke-formateret). Hvis du f.eks. vil sikre, at det kun er kreditkort, der starter med 411111 & 433512, der skal anses for gyldige, skal du føje følgende til listen 4111 11, 4111-11, 411111, 4335 12, 4335-12, 433512.
1. Gentag trin 2 & 3 for mønsteret med lav konfidens.

## <a name="test-numbers-similar-to-social-security-numbers"></a>Testnumre svarende til cpr-numre

Contoso har identificeret et par nicifrede testnumre, der udløser falske positive matches i SSN-politikken (Social Security Number) Microsoft Purview data loss prevention (DLP). De vil gerne udelade disse tal fra listen over gyldige matches for SSN.

**Foreslået løsning**

1. Opret en kopi af SSN SIT. Brug trinnene til at [kopiere og redigere en type følsomme oplysninger](create-a-custom-sensitive-information-type.md#copy-and-modify-a-sensitive-information-type) for at kopiere SSN SIT.
1. Rediger mønsteret med høj genkendelsessikkerhed. Følg trinnene i [redigering eller sletning af mønsteret for følsomme oplysninger](sit-get-started-exact-data-match-create-rule-package.md#edit-or-delete-the-sensitive-information-type-pattern).
1. Tilføj de tal, der skal udelades, i den ekstra kontrol "udelad specifikke værdier". Hvis du f.eks. vil udelade 239-23-532-& 23923532, er det tilstrækkeligt blot at tilføje 23923532
1. Gentag trin 2 & 3 for andre konfidensmønstre

## <a name="phone-numbers-in-signature-trigger-match"></a>Match af telefonnumre i signaturudløser

Contoso, der er baseret i Australien, finder ud af, at telefonnumre i mailsignaturer udløser et match for deres DLP-politik for virksomhedsnummer i Australien.

**Foreslået løsning**

Tilføj en "ikke"-gruppe i supplerende elementer ved hjælp af en nøgleordsliste, der indeholder almindeligt anvendte nøgleord i mailsignatur, f.eks. "Telefon", "Mobil", "mail", "Tak og hilsen" osv. Hold nærheden til denne nøgleordsliste til en mindre værdi, f.eks. 50 tegn, for at opnå en bedre nøjagtighed. Du kan få flere oplysninger under [Kom i gang med brugerdefinerede typer følsomme oplysninger](create-a-custom-sensitive-information-type.md).

## <a name="unable-to-trigger-aba-routing-policy"></a>ABA-routingpolitikken kan ikke udløses

DLP-politikken kan ikke udløse ABA-routingnummerpolitik i store Excel-filer, fordi det påkrævede nøgleord ikke findes inden for 300 tegn.

**Foreslået løsning**

Opret en kopi af det indbyggede SIT, og rediger den for at ændre nærhed på nøgleordslisten fra "300 tegn" til "Hvor som helst i dokumentet".

> [!TIP]
> Du kan redigere nøgleordslisten for at inkludere/udelade nøgleord, der er relevante for din organisation.

## <a name="unable-to-detect-credit-card-numbers-with-unusual-delimiters"></a>Det var ikke muligt at registrere kreditkortnumre med usædvanlige afgrænsere

Contoso Bank har bemærket, at nogle af deres medarbejdere deler kreditkortnumre med '/' som afgrænser, f.eks. 4111/1111/1111/1111, som ikke registreres af definitionen af kreditkortet, der ikke er registreret i kassen. Contoso vil gerne definere deres egen regex og validere den ved hjælp af LuhnCheck.

**Foreslået løsning**

1. Opret en kopi af Kreditkort-SIT ved hjælp af trinnene i [Tilpas en indbygget type følsomme oplysninger](customize-a-built-in-sensitive-information-type.md).
1. Tilføj et nyt mønster
1. Vælg regulært udtryk i det primære element
1. Definer det regulære udtryk, der indeholder '/' som en del af det regulære udtryk, og vælg derefter validator, og vælg luhncheck eller func_credit_card for at sikre, at regex også overfører LuhnCheck.

## <a name="ignore-a-disclaimer-notice"></a>Ignorer en meddelelse om ansvarsfraskrivelse

Mange organisationer føjer juridiske ansvarsfraskrivelser, afsløringserklæringer, signaturer eller andre oplysninger til toppen eller bunden af mails, der indtaster eller forlader deres organisationer og i nogle tilfælde endda inden for organisationerne. De ansatte selv sætte underskrifter herunder - motiverende citater, sociale beskeder, og så videre. En ansvarsfraskrivelse eller signatur kan indeholde de vilkår, der findes i leksikonet i et CC og kan generere en masse falske positiver.  

En typisk ansvarsfraskrivelse kan f.eks. indeholde ord som følsomme eller fortrolige, og en politik, der leder efter følsomme oplysninger, registrerer den som en hændelse, hvilket fører til mange falske positiver. Således giver kunderne en mulighed for at ignorere ansvarsfraskrivelse kan reducere falske positiver og øge effektiviteten af overholdelse team.

### <a name="example-of-disclaimer"></a>Eksempel på ansvarsfraskrivelse

Overvej følgende ansvarsfraskrivelse:

VIGTIG BEMÆRKNING: Denne e-mail er kun beregnet til at blive modtaget af personer, der har ret til at modtage de fortrolige oplysninger, den kan indeholde. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er tiltænkt modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Hvis SIT er konfigureret til at registrere et nøgleord, der er fortroligt, aktiverer mønsteret et match, hver gang en ansvarsfraskrivelse bruges i mailen, hvilket fører til en masse falske positiver.

### <a name="ignore-disclaimer-using-prefix-and-suffix-in-sit"></a>Ignorer ansvarsfraskrivelse ved hjælp af præfiks og suffiks i SIT

En måde at ignorere forekomster af nøgleord på i ansvarsfraskrivelsen er ved at udelade de forekomster af nøgleord, der har et præfiks foranstillet og efterfulgt af et suffiks.

Overvej denne ansvarsfraskrivelse:

VIGTIG BEMÆRKNING: Denne e-mail er kun beregnet til at blive modtaget af personer, der *har ret til at modtage de* fortrolige **oplysninger, den kan indeholde**. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er tiltænkt modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Vi har to forekomster af nøgleordet "fortroligt", og hvis vi konfigurerer SIT til at ignorere forekomster af dette nøgleord med præfikser foran (kursiv i eksemplet) og efterfulgt af suffikser (med fed i eksemplet), kan vi opnå at ignorere ansvarsfraskrivelser i de fleste tilfælde.

Sådan ignorerer du ansvarsfraskrivelsen ved hjælp af præfiks og suffiks:

1. Føj yderligere kontroller i det aktuelle SIT for at udelade præfiks og suffikstekst til det nøgleord, som vi vil ignorere i ansvarsfraskrivelsen.
1. Vælg at udelade præfikset, og angiv **oplysninger** i tekstfeltet **Præfikser**.
1. Vælg at udelade suffikset, og angiv **og juridisk privilegerede** i **tekstfeltet Suffiks**.
1. Gentag denne proces for andre forekomster af nøgleordene i ansvarsfraskrivelsen som vist i følgende grafik.

### <a name="ignore-disclaimer-by-excluding-secondary-elements"></a>Ignorer ansvarsfraskrivelse ved at udelade sekundære elementer

En anden måde at tilføje en liste over supplerende elementer (forekomster i ansvarsfraskrivelse), som skal udelades, er ved at udelade sekundære elementer.

Overvej denne ansvarsfraskrivelse:

VIGTIG BEMÆRKNING: Denne e-mail er kun beregnet til at blive modtaget af personer, der har ret til at modtage de fortrolige oplysninger, den kan indeholde. Mails til Contoso-klienter kan indeholde oplysninger, der er fortrolige og juridisk privilegerede. Undlad at læse, kopiere, videresende eller gemme denne meddelelse, medmindre du er tiltænkt modtager af den. Hvis du har modtaget denne meddelelse ved en fejl, skal du videresende den til afsenderen og slette den helt fra computersystemet.

Vi har to forekomster af nøgleordet "fortroligt" i dette eksempel. Hvis vi konfigurerer SIT til at ignorere forekomster af dette nøgleord i ansvarsfraskrivelsen (understreget som rød), kan vi opnå at ignorere ansvarsfraskrivelser i de fleste tilfælde.

:::image type="content" source="../media/sit-scenario-edit-pattern.png" alt-text="Du kan føje flere betingelser til mønsteret for at udelade yderligere forekomster i ansvarsfraskrivelsen.":::

Sådan ignorerer du ansvarsfraskrivelsen ved hjælp af sekundære elementer:

1. Vælg **Ikke nogen af disse** grupper i de understøttende elementer.
1. Tilføj de forekomster af ansvarsfraskrivelse, som vi vil ignorere som en nøgleordsliste/ordbog.
1. Tilføj nøgleordene som en ny linje, som vi vil ignorere. Husk, at længden af hver tekst ikke må være på mere end 50 tegn.
1. Angiv, at nærheden af dette element skal være inden for 50-60 tegn fra det primære element.
