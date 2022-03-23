---
title: Oprette brugerdefinerede typer af følsomme oplysninger
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
description: Få mere at vide om, hvordan du opretter, redigerer, fjerner og tester brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e21e77fdd113942618c021f69c2cf8be64ac742f
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63587890"
---
# <a name="create-custom-sensitive-information-types-in-the-compliance-center"></a>Opret brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter

Hvis de forudkonfigurerede typer af følsomme oplysninger ikke opfylder dine behov, kan du oprette dine egne brugerdefinerede typer af følsomme oplysninger, som du definerer fuldt ud, eller du kan kopiere en af de forudkonfigurerede typer og redigere den.

De brugerdefinerede typer af følsomme oplysninger, du opretter ved hjælp af denne metode, føjes til regelpakken, der hedder `Microsoft.SCCManaged.CustomRulePack`.

Der er to måder at oprette en ny type af følsomme oplysninger på:

- [fra bunden, hvor du definerer alle elementer fuldt ud](#create-a-custom-sensitive-information-type)
- [kopiér og rediger en eksisterende type af følsomme oplysninger](#copy-and-modify-a-sensitive-information-type)


## <a name="before-you-begin"></a>Før du begynder

- Du bør være fortrolig med typer af følsomme oplysninger, og hvad de består af. Se Få [mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md). Det er vigtigt at forstå rollerne ved:
    - [regulære udtryk](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/) – Microsoft 365 typer af følsomme oplysninger bruger programmet Boost.RegEx 5.1.3
    - lister over nøgleord – du kan oprette dine egne, når du definerer din type af følsomme oplysninger eller vælge mellem eksisterende lister med nøgleord
    - [nøgleordsordbog](create-a-keyword-dictionary.md)
    - [Funktioner af typen Følsomme oplysninger](sit-functions.md)
    - [tillidsniveauer](sensitive-information-type-learn-about.md#more-on-confidence-levels)
 
- Du skal have tilladelsen Global administrator eller Overholdelsesadministrator for at oprette, teste og installere en brugerdefineret type af følsomme oplysninger via brugergrænsefladen. Se [Om administratorroller](/office365/admin/add-users/about-admin-roles) i Office 365.

- Din organisation skal have et abonnement, f.eks. Office 365 Enterprise, der omfatter forebyggelse af datatab (DLP). Se [Beskedpolitik og OverholdelsestjenesteBeskrivelse](/office365/servicedescriptions/exchange-online-protection-service-description/messaging-policy-and-compliance-servicedesc). 


> [!IMPORTANT]
> Microsofts kundeservicemedarbejdere & ikke hjælpe med at oprette brugerdefinerede klassificeringer eller regulære udtryksmønstre. Supportteknikere kan yde begrænset support til funktionen, f.eks. give eksempler på regulære udtryksmønstre til testformål eller hjælpe med at foretage fejlfinding af et eksisterende regulært udtryksmønster, der ikke udløser som forventet, men kan ikke give forsikringer om, at en tilpasset udvikling af indholdssammenholdelse opfylder dine krav eller forpligtelser.

## <a name="create-a-custom-sensitive-information-type"></a>Oprette en brugerdefineret type af følsomme oplysninger

Brug denne fremgangsmåde til at oprette en ny type af følsomme oplysninger, som du definerer fuldt ud. 

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Typer af følsomme** oplysninger og **vælge Opret følsom oplysningstype**.

2. Udfyld værdierne for Navn **og Beskrivelse****, og** vælg **Næste**.

3. Vælg **Opret mønster**. Du kan oprette flere mønstre, hver med forskellige elementer og tillidsniveauer, efterhånden som du definerer din nye type af følsomme oplysninger.

4. Vælg standardtillidsniveauet for mønsteret. Værdierne er Lav tillid **,** **Mellem tillid og** **Høj tillid**.

5. Vælg og definer **Primært element**. Det primære element kan være et  Regulært udtryk med en valgfri validator, en liste med **Nøgleord, en** ordbog til Nøgleord eller en af de forudkonfigurerede **funktioner**. Du kan finde flere oplysninger om DLP-funktioner [under Funktioner til følsomme oplysninger.](sit-functions.md) Du kan finde flere oplysninger om dato og validatorer for kontrolsum under Validatorer til [regulære udtryk af typen Følsomme oplysninger](sit-regex-validators-additional-checks.md#sensitive-information-type-regular-expression-validators).

6. Udfyld en værdi for Tegn **afstand**.

7. (Valgfrit) Tilføj supplerende elementer, hvis du har nogen. Supplerende elementer kan være et regulært udtryk med en valgfri validator, en liste med nøgleord, en ordbog til nøgleord eller en af de foruddefinerede funktioner. Understøttende elementer kan have deres egen **konfiguration af Tegn afstand** . 

8. (Valgfrit) Tilføj eventuelle [**yderligere kontroller**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) fra listen over tilgængelige kontroller.

9. Vælg **Opret**.

10. Vælg **Næste**.

11. Vælg det **anbefalede tillidsniveau** for denne type af følsomme oplysninger.

12. Kontrollér din indstilling, og vælg **Send**.

    > [!IMPORTANT]
    > Microsoft 365 bruger søge crawleren til at identificere og klassificere følsomme oplysninger i SharePoint Online og OneDrive for Business websteder. For at identificere din nye type af brugerdefinerede følsomme oplysninger i eksisterende indhold skal indholdet gennemsøges igen. Indhold gennemsøges baseret på en tidsplan, men du kan manuelt gennemsøge indhold for en gruppe af websteder, en liste eller et bibliotek. Få mere at vide under [Anmod manuelt om gennemsøgning og genindeksering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

13. På siden **Dataklassificering** får du vist alle typer af følsomme oplysninger. Vælg **Opdater** , og søg efter eller brug søgeværktøjet til at finde den type af følsomme oplysninger, du har oprettet.

### <a name="copy-and-modify-a-sensitive-information-type"></a>Kopiér og rediger en følsom oplysningstype

Brug denne fremgangsmåde til at oprette en ny type af følsomme oplysninger, der er baseret på en eksisterende type af følsomme oplysninger. 

> [!NOTE]
> Disse SIT'er kan ikke kopieres:
> - Canada-kørekortnummer
> - EU-kørekortnummer
> - EU-national identifikationsnummer
> - EU-pasnummer
> - EU-nummer til personnummer eller tilsvarende identifikation
> - EU-skatte-id
> - International klassificering af klassifikationer (ICD-10-CM)
> - International klassificering af klassifikationer (ICD-9-CM)
> - USA kørekortnummer

Du kan også oprette brugerdefinerede typer af følsomme oplysninger ved hjælp af PowerShell og egenskaberne Nøjagtig dataoverensstemmelse. Hvis du vil have mere at vide om disse metoder, skal du se:
- [Opret en brugerdefineret type af følsomme oplysninger i Security & Compliance Center PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> Typer af følsomme oplysninger og vælge den type af følsomme oplysninger, du vil kopiere.

2. Vælg Kopiér i pop **op-menuen**.

3. Vælg **Opdater** på listen over typer af følsomme oplysninger, og enten gennemse eller søg efter den kopi, du lige har lavet. Delvise søgninger fungerer, så `copy` du kan bare søge efter og søge ville returnere alle typer af følsomme oplysninger med ordet `copy` i navnet. 

4. Udfyld værdierne for Navn **og Beskrivelse****, og** vælg **Næste**.

5. Vælg kopiér følsomme oplysninger, og vælg **Rediger**. 

6. Giv dine nye følsomme oplysninger et nyt Navn **og** **beskrivelse**.

7. Du kan vælge at redigere eller fjerne de eksisterende mønstre og tilføje nye. Vælg standardtillidsniveauet for det nye mønster. Værdierne er Lav tillid **,** **Mellem tillid og** **Høj tillid**.

8. Vælg og definer **Primært element**. Det primære element kan være et **regulært udtryk**, en **liste** med nøgleord, en ordbog til **nøgleord** eller en af de forudkonfigurerede **funktioner**. Se [Funktioner til type af følsomme oplysninger](sit-functions.md).

9. Udfyld en værdi for Tegn **afstand**.

10. (Valgfrit) Hvis du har **Understøttende elementer** eller yderligere [**kontroller, skal**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) du tilføje dem. Hvis det er nødvendigt, kan du gruppere **dine Supplerende elementer**.

11. Vælg **Opret**.

12. Vælg **Næste**.

13. Vælg det **anbefalede tillidsniveau** for denne type af følsomme oplysninger.

14. Kontrollér din indstilling, og vælg **Send**.

## <a name="test-a-sensitive-information-type"></a>Teste en følsom oplysningstype

Du kan teste følsomme oplysninger på listen. Vi anbefaler, at du tester alle typer af følsomme oplysninger, som du opretter, før du bruger den i en politik.

1. Forbered to filer, f.eks. et Word-dokument. Et med indhold, der svarer til de elementer, du har angivet i din type af følsomme oplysninger, og et, der ikke stemmer overens.

2. I Overholdelsescenter skal du gå til **Dataklassificering** \> Følsomme oplysningstyper og vælge typen af følsomme oplysninger på listen for at åbne detaljeruden og vælge **Test**.

3. Upload en fil, og vælg **Test**.

4. På siden **Matches results** skal du gennemse resultaterne og vælge **Udfør**.

## <a name="custom-sensitive-information-types-limits"></a>Begrænsninger for brugerdefinerede typer af følsomme oplysninger

For at sikre høj ydeevne og lavere ventetid er der begrænsninger i brugerdefinerede SIT'ers konfigurationer.

|Grænse|Værdi|
|--------|--------|
|maksimalt antal brugerdefinerede SIT'er oprettet via Overholdelsescenter| 500 |
|maksimal længde af regulært udtryk| 1024 tegn|
|maksimal længde for et givet ord på en liste med nøgleord| 50 tegn|
|maksimalt antal ord på listen over nøgleord| 2048|
|maksimale antal forskellige regexes pr. følsom oplysningstype| 20|
|Maksimal størrelse på en ordbog til nøgleord (efter komprimering)| 1MB (~1.000.000 tegn)|
|maksimalt antal ordbøger baseret på nøgleord i en lejer|50 |

> [!NOTE] 
> Hvis du har brug for at oprette mere end 500 brugerdefinerede SIT'er til virksomheder, skal du oprette en supportanmodning.

### <a name="instance-count-supported-values-for-sit"></a>Antal forekomster af understøttede værdier for SIT

Grænsen for SIT-forekomster gælder, når SIT'er bruges i disse løsninger:

- DLP-politikker
- Beskyttelse af oplysninger
- Information Governance
- Kommunikationsoverholdelse
- Datastyring
- Microsoft Defender til skyapps
- Microsoft Prkon

Hvis et scannet element skal opfylde regelkriterier, skal antallet af entydige forekomster af et SIT i et enkelt element falde mellem min. og maks. værdier. Dette kaldes antal **forekomster**.

- **Feltet Min** : den nedre grænse (minimumantallet) for entydige forekomster af et SIT-element, der skal findes i et element for at udløse et match. Feltet min understøtter værdier på:
    - 1 til 500
- **Maks** . felt: den øvre grænse for antallet af entydige forekomster af et SIT, der kan findes i et element og stadig udløse et match. Feltet Maks. understøtter værdier af:
    - 1 til 500 – Brug denne, når du vil angive en bestemt øvre grænse, der er 500 eller mindre for antallet af forekomster af et SIT i et element.
    - Enhver – `Any` Bruges, når du ønsker, at kriteriet for antallet af entydige forekomster skal være opfyldt, når et ikke-defineret antal entydige forekomster af et SIT findes i et scannet element, og det pågældende antal entydige forekomster opfylder eller overstiger minimumantallet af entydige forekomster værdi. Det vil sige, at kriteriet for antallet af entydige forekomster er opfyldt, så længe min-værdien er opfyldt.

Hvis reglen f.eks. skal udløse et match, når der findes mindst 500 entydige forekomster af et SIT i et enkelt element, skal du indstille **min-værdien** `500` til og den  maksimale værdi til `Any`.

> [!NOTE]
> Microsoft 365 Information Protection understøtter dobbelte byte tegnsætsprog til:
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
>Denne support er tilgængelig for typer af følsomme oplysninger. Se Understøttelse af [beskyttelse af oplysninger for dobbelt byte-tegnsæt produktbemærkninger (forhåndsvisning)](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkelte bytetegn eller til at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex. 
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet; et med et mellemrum mellem den japanske og engelske tekst og et andet uden mellemrum mellem den japanske og engelske tekst. Så de nøgleord, der skal tilføjes i SIT, bør være "机密的 dokument" og "机密的dokument". På samme måde skal der bruges to varianter til 東京オリ "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
>
> Sammen med kinesisk/japansk/dobbelt byte tegn, hvis listen over nøgleord/sætninger også indeholder ikke-kinesiske/japanske ord (som kun engelsk), anbefales det at oprette to ordbøger/nøgleordslister. En til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn og et andet til kun engelsk. 
> - Hvis du f.eks. vil oprette en ordbog/liste med nøgleord med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to lister med nøgleord. 
>     1. Meget fortrolig
>     2. 機密性が高い, 机密的dokument og 机密的 dokument
>
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undgå begge tegn, som om den ene ville escape en bindestreg eller punktum i en regex. Her er en eksempelre regex til reference:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4})
>
> Dobbelt-byte-specialtegn bør ikke bruges i nøgleordet.
> 
> Vi anbefaler, at du bruger et strengmatch i stedet for et ordmatch i en nøgleordsliste.
