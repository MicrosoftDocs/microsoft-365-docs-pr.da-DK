---
title: Opret brugerdefinerede typer følsomme oplysninger
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du opretter, redigerer, fjerner og tester brugerdefinerede typer følsomme oplysninger i Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 733e043ed92e601812046dd5e50405ee28ee33da
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638604"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Opret brugerdefinerede typer følsomme oplysninger i Overholdelsescenter

Hvis de forudkonfigurerede typer af følsomme oplysninger ikke opfylder dine behov, kan du oprette dine egne brugerdefinerede typer følsomme oplysninger, som du definerer fuldt ud, eller du kan kopiere en af de forudkonfigurerede og redigere den.

De brugerdefinerede typer følsomme oplysninger, du opretter ved hjælp af denne metode, føjes til regelpakken med navnet `Microsoft.SCCManaged.CustomRulePack`.

Der er to måder at oprette en ny type følsomme oplysninger på:

- [fra bunden, hvor du definerer alle elementer fuldt ud](#create-a-custom-sensitive-information-type)
- [kopiér og rediger en eksisterende type følsomme oplysninger](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Før du begynder

- Du bør have kendskab til følsomme informationstyper, og hvad de er sammensat af. Se Få [mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md). Det er vigtigt at forstå rollerne for:
  - [regulære udtryk](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) – Microsoft 365-følsomme informationstyper bruger Boost.RegEx 5.1.3-programmet
  - nøgleordslister – du kan oprette dine egne, når du definerer din type følsomme oplysninger eller vælger fra eksisterende nøgleordslister
  - [nøgleordsordbog](create-a-keyword-dictionary.md)
  - [Funktioner for type af følsomme oplysninger](sit-functions.md)
  - [tillidsniveauer](sensitive-information-type-learn-about.md#more-on-confidence-levels)

- Organisationen skal have et abonnement, f.eks. Office 365 Enterprise, der omfatter Microsoft Purview Forebyggelse af datatab (DLP). Se [Meddelelsespolitik og OverholdelsestjenesteBeskrivelse](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 

- Din organisation skal have et abonnement, f.eks. Office 365 Enterprise, der omfatter forebyggelse af datatab (DLP). Se [Meddelelsespolitik og OverholdelsestjenesteBeskrivelse](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc).

> [!IMPORTANT]
> Microsoft Customer Service & Support kan ikke hjælpe med at oprette brugerdefinerede klassificeringer eller regulære udtryksmønstre. Supportteknikere kan yde begrænset support til funktionen, f.eks. ved at levere eksempler på mønstre for regulære udtryk til testformål eller hjælpe med fejlfinding af et eksisterende mønster for regulære udtryk, der ikke udløses som forventet, men som ikke kan give forsikringer om, at enhver brugerdefineret udvikling, der matcher indhold, vil opfylde dine krav eller forpligtelser.

## <a name="create-a-custom-sensitive-information-type"></a>Opret en brugerdefineret type følsomme oplysninger

Brug denne procedure til at oprette en ny type følsomme oplysninger, som du definerer fuldt ud.

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Typer af følsomme oplysninger** og vælge **Opret type af følsomme oplysninger**.

2. Udfyld værdier for **Navn** og **Beskrivelse,** og vælg **Næste**.

3. Vælg **Opret mønster**. Du kan oprette flere mønstre, der hver især har forskellige elementer og tillidsniveauer, når du definerer din nye type følsomme oplysninger.

4. Vælg mønsterets standardsikkerhedsniveau. Værdierne er **Lav tillid**, **Mellem tillid** og **Høj tillid**.

5. Vælg og definer **Primært element**. Det primære element kan være et **regulært udtryk** med en valgfri validator, en **nøgleordsliste**, en **nøgleordsordbog** eller en af de forudkonfigurerede **funktioner**. Du kan få flere oplysninger om DLP-funktioner under [Funktioner til følsomme oplysninger.](sit-functions.md) Du kan finde flere oplysninger om datoen og kontrolsumevalidatorer under [Validatorer af regulære udtryk af følsomme oplysninger](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Udfyld en værdi for **Tegn nærhed**.

7. (Valgfrit) Tilføj eventuelle supplerende elementer. Understøttende elementer kan være et regulært udtryk med en valgfri validator, en nøgleordsliste, en nøgleordsordbog eller en af de foruddefinerede funktioner. Understøttende elementer kan have deres egen konfiguration **af Character proximity** .

8. (Valgfrit) Tilføj [**eventuelle yderligere kontroller**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) fra listen over tilgængelige kontroller.

9. Vælg **Opret**.

10. Vælg **Næste**.

11. Vælg det **anbefalede tillidsniveau** for denne type følsomme oplysninger.

12. Kontrollér din indstilling, og vælg **Send**.

    > [!IMPORTANT]
    > Microsoft 365 bruger søgecrawleren til at identificere og klassificere følsomme oplysninger på SharePoint Online- og OneDrive for Business websteder. Hvis du vil identificere den nye brugerdefinerede type følsomme oplysninger i eksisterende indhold, skal indholdet gennemsøges igen. Indhold gennemsøges efter en tidsplan, men du kan manuelt gennemsøge indhold for en gruppe af websteder, en liste eller et bibliotek. Du kan få flere oplysninger under [Anmod manuelt om gennemsøgning og genindeksering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

13. På siden **Dataklassificering** kan du se alle typer følsomme oplysninger på listen. Vælg **Opdater** , og søg derefter efter eller brug søgeværktøjet til at finde den type følsomme oplysninger, du har oprettet.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Kopiér og rediger en type følsomme oplysninger

Brug denne procedure til at oprette en ny type følsomme oplysninger, der er baseret på en eksisterende type følsomme oplysninger.

> [!NOTE]
> Disse SIT'er kan ikke kopieres:
>
> - Canadas kørekortsnummer
> - EU-kørekortsnummer
> - EU-nationalt identifikationsnummer
> - EU-pasnummer
> - EU-cpr-nummer eller tilsvarende identifikation
> - EU-skatteidentifikationsnummer
> - International klassificering af sygdomme (ICD-10-CM)
> - International klassificering af sygdomme (ICD-9-CM)
> - Amerikansk kørekortsnummer

Du kan også oprette brugerdefinerede typer følsomme oplysninger ved hjælp af PowerShell og funktionerne Exact Data Match. Du kan få mere at vide om disse metoder under:

- [Opret en brugerdefineret type følsomme oplysninger i Microsoft Purview PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Typer af følsomme oplysninger** og vælge den type følsomme oplysninger, du vil kopiere.

2. Vælg **Kopiér** i pop op-vinduet.

3. Vælg **Opdater** på listen over følsomme oplysningstyper, og gennemse eller søg efter den kopi, du lige har oprettet. Delvise stingsøgninger fungerer, så du kan bare søge efter `copy` , og søgning returnerer alle følsomme oplysningstyper med ordet `copy` i navnet.

4. Udfyld værdier for **Navn** og **Beskrivelse,** og vælg **Næste**.

5. Vælg kopien af typen følsomme oplysninger, og vælg **Rediger**.

6. Giv den nye type følsomme oplysninger et nyt **navn** og en ny **beskrivelse**.

7. Du kan vælge at redigere eller fjerne de eksisterende mønstre og tilføje nye. Vælg standardsikkerhedsniveauet for det nye mønster. Værdierne er **Lav tillid**, **Mellem tillid** og **Høj tillid**.

8. Vælg og definer **Primært element**. Det primære element kan være et **regulært udtryk**, en **nøgleordsliste**, en **nøgleordsordbog** eller en af de forudkonfigurerede **funktioner**. Se [Funktioner af typen følsomme oplysninger](sit-functions.md).

9. Udfyld en værdi for **Tegn nærhed**.

10. (Valgfrit) Hvis du har **understøttende elementer** eller [**yderligere kontroller**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) , skal du tilføje dem. Hvis det er nødvendigt, kan du **gruppere dine understøttende elementer**.

11. Vælg **Opret**.

12. Vælg **Næste**.

13. Vælg det **anbefalede tillidsniveau** for denne type følsomme oplysninger.

14. Kontrollér din indstilling, og vælg **Send**.

## <a name="test-a-sensitive-information-type"></a>Test en type følsomme oplysninger

Du kan teste en hvilken som helst type følsomme oplysninger på listen. Vi foreslår, at du tester alle følsomme oplysninger, som du opretter, før du bruger den i en politik.

1. Forbered to filer, f.eks. et Word-dokument. En med indhold, der svarer til de elementer, du har angivet i din følsomme oplysningstype, og et, der ikke stemmer overens.

2. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Følsomme infotyper** og vælge typen af følsomme oplysninger på listen for at åbne detaljeruden og vælge **Test**.

3. Upload en fil, og vælg **Test**.

4. Gennemse resultaterne på siden **Matches resultater** , og vælg **Udfør**.

## <a name="custom-sensitive-information-types-limits"></a>Grænser for brugerdefinerede følsomme oplysningstyper

Der er begrænsninger i brugerdefinerede SIT-konfigurationer for at sikre høj ydeevne og lavere ventetid.

|Grænse|Værdi|
|---|---|
|maksimalt antal brugerdefinerede SIT'er, der er oprettet via Overholdelsescenter| 500 |
|maksimal længde på regulært udtryk| 1024 tegn|
|maksimumlængde for et givet ord på en nøgleordsliste| 50 tegn|
|maksimalt antal ord på nøgleordslisten| 2048|
|maksimalt antal entydige regexes pr. følsom oplysningstype| 20|
|maksimumstørrelse for en nøgleordsordbog (efter komprimering)| 1 MB (~1.000.000 tegn)|
|maksimalt antal nøgleordsordbogsbaserede SIT'er i en lejer|50 |

> [!NOTE]
> Hvis du har et forretningsbehov for at oprette mere end 500 brugerdefinerede SIT'er, skal du rejse en supportanmodning.

### <a name="instance-count-supported-values-for-sit"></a>Antal understøttede værdier for FOREKOMST

Optællingsgrænsen for SIT-forekomster gælder, når SIT'er bruges i disse løsninger:

- DLP-politikker
- Information Protection
- Administration af datalivscyklus
- Kommunikation med overholdelse af angivne standarder
- Datastyring
- Microsoft Defender for Cloud Apps
- Microsoft Priva

Hvis et scannet element skal opfylde regelkriterierne, skal antallet af entydige forekomster af et SIT i et enkelt element falde mellem minimum- og maksimumværdierne. Dette kaldes antallet af **forekomster**.

- **Minimumfelt** : den nedre grænse (minimumantal) af entydige forekomster af et SIT, der skal findes i et element for at udløse et match. Feltet min. understøtter værdier af:
  - 1 til 500
- **Maks** . felt: Den øvre grænse for antallet af entydige forekomster af et SIT, der kan findes i et element og stadig udløser et match. Det maksimale felt understøtter værdier af:
  - 1 til 500 – Bruges, når du vil angive en specifik øvre grænse på 500 eller mindre for antallet af forekomster af et SIT i et element.
  - Any – Bruges `Any` , når du vil have, at det entydige antal forekomster skal være opfyldt, når der findes et udefineret antal entydige forekomster af et SIT i et scannet element, og det antal entydige forekomster opfylder eller overstiger det mindste antal entydige forekomster. Det vil sige, at de entydige kriterier for antal forekomster er opfyldt, så længe minimumværdien er opfyldt.

Hvis reglen f.eks. skal udløse et match, når der findes mindst 500 entydige forekomster af et SIT i et enkelt element, skal du angive **minimumværdien** til `500` og den **maksimale** værdi til `Any`.

> [!NOTE]
> Microsoft 365 Information Protection understøtter sprog med dobbeltbytetegnsæt for:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne understøttelse er tilgængelig for typer af følsomme oplysninger. Se [Produktbemærkninger til beskyttelse af oplysninger for dobbeltbytetegnsæt (prøveversion)](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkeltbytetegn, eller for at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex.
>
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet. en med et mellemrum mellem japansk og engelsk tekst og en anden uden et mellemrum mellem japansk og engelsk tekst. De nøgleord, der skal tilføjes i SIT, skal derfor være "机密的 document" og "机密的document". På samme måde bør der bruges to varianter for at registrere udtrykket "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
>
> Sammen med kinesisk/japansk/dobbeltbytetegn anbefales det at oprette to ordbøger/nøgleordslister, hvis listen over nøgleord/udtryk også indeholder ikke-kinesiske/japanske ord (f.eks. kun engelsk). Et til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn, og et til kun engelsk.
>
> - Hvis du f.eks. vil oprette en nøgleordsordbog/liste med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to nøgleordslister.
>   1. Meget fortroligt
>   2. 機密性が高い, 机密的document og 机密的 dokument
>
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undslippe begge tegn, som man ville undslippe en bindestreg eller et punktum i en regex. Her er et eksempel på et regex som reference:
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4})`
>
> Specialtegn med dobbeltbyte må ikke bruges i nøgleordet.
>
> Vi anbefaler, at du bruger et strengmatch i stedet for et ordmatch på en nøgleordsliste.
