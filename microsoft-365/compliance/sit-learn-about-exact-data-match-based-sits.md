---
title: Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger
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
description: Få mere at vide om nøjagtige datamatchingbaserede typer af følsomme oplysninger.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 21e6f3c12d7c401562a1ee1915e1e1c266724b1b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63601033"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger

[](sensitive-information-type-learn-about.md) Typer af følsomme oplysninger bruges til at identificere følsomme elementer, så du kan forhindre dem i utilsigtet eller upassende at blive delt, for at finde relevante data i eDiscovery og for at anvende styringshandlinger på visse typer oplysninger. Du definerer en brugerdefineret type af følsomme oplysninger (SIT) baseret på:

- mønstre
- *nøgleordslegitimation som* *f.eks. medarbejder*, CPR-nummer eller *id*
- Tegn afstand til beviser i et bestemt mønster
- tillidsniveauer

Men hvad nu, hvis du gerne vil have en brugerdefineret følsom informationstype (SIT), der bruger nøjagtige eller næsten nøjagtige dataværdier i stedet for en, der finder forekomster baseret på generiske mønstre? Med EDM-baseret klassificering (Exact Data Match) kan du oprette en brugerdefineret type af følsomme oplysninger, der er designet til at:

- være dynamisk og nemt opdateres
- være mere skalerbar
- giver færre falske positive
- arbejde med strukturerede følsomme data
- håndtere følsomme oplysninger på en mere sikker måde, ikke dele dem med andre, herunder Microsoft
- kan bruges sammen med flere Microsoft-skytjenester

![EDM-baseret klassificering.](../media/EDMClassification.png)

EDM-baseret klassificering giver dig mulighed for at oprette brugerdefinerede typer af følsomme oplysninger, der refererer til nøjagtige værdier i en database med følsomme oplysninger. Databasen kan opdateres dagligt og indeholde op til 100 millioner rækker med data. Så når medarbejdere, patienter eller kunder kommer og går, og posterne ændres, forbliver dine brugerdefinerede typer af følsomme oplysninger aktuelle og gældende. Og du kan bruge EDM-baseret klassificering med politikker, f.eks politikker til forebyggelse af [datatab](dlp-learn-about-dlp.md) [eller Microsoft Cloud App Security-filpolitikker](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft 365 Information Protection understøtter dobbelte byte tegnsætsprog til:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne support er tilgængelig for typer af følsomme oplysninger. Se Understøttelse af [beskyttelse af oplysninger for dobbelt byte-tegnsæt produktbemærkninger (forhåndsvisning)](mip-dbcs-relnotes.md) for at få flere oplysninger.

## <a name="whats-different-in-an-edm-sit"></a>Hvad er anderledes i et EDM SIT

Når du arbejder med EDM-SIT'er, er det nyttigt at forstå et par begreber, der er unikke for dem.  

### <a name="schema"></a>Skema

Skemaet er en xml-fil, der definerer:

- Navnet på skemaet, der senere blev kaldt *DataStore*. 
- De feltnavne, som kildetabellen med følsomme oplysninger indeholder. Der er en 1:1-tilknytning af skemafeltnavn til kildetabelkolonnenavnet for følsomme oplysninger.
- Hvilke felter der kan søges i.
- Enhver søgning, der ændrer parametre, kaldet *konfigurerbar match*, såsom at ignorere afgrænsere og case i søgeværdier.

### <a name="sensitive-information-source-table"></a>Kildetabel med følsomme oplysninger

Den følsomme kildetabel indeholder de følsomme oplysningsværdier, som EDM SIT søger efter. Det består af kolonner og rækker. Kolonneoverskrifterne er feltnavnene, rækkerne er en forekomst af data, og hver celle indeholder værdierne for den pågældende forekomst for det pågældende felt.

Her er et simpelt eksempel på en kildetabel med følsomme oplysninger.

|Fornavn  |Efternavn  |Fødselsdag  |
|---------|---------|---------|
|Isaæder   |Langer  | 05-05-1960 |
|Ana   |Bowman         |11-24-1971 |
|1.   |Ikke-for-stor         |02-12-1998 |


### <a name="rule-package"></a>Regelpakke

Hvert SIT har en regelpakke. Du kan bruge regelpakken i et EDM SIT til at definere:

- Finder forekomster, som angiver det felt, der skal være det primære element, der skal bruges i nøjagtigt opslag. Det kan være et regulært udtryk med eller uden kontrolsumvalidering, en liste med nøgleord, en ordbog til nøgleord eller en funktion.
- Klassificering, som angiver matchet for den følsomme type, der udløser EDM-opslag.
- Understøttende element, som er elementer, som, når der findes dokumentation, der hjælper med at øge matchens tillid. Nøgleordet "SSN" i nærheden af et SSN-tal. Det kan være et regulært udtryk med eller uden kontrolsumvalidering, nøgleordsliste eller nøgleordsordbog.
- Confidence levels (high, medium, low) reflect how much supporting evidence wasected along with the primary element. Jo mere støttedokumentdokument, et element indeholder, jo højere er tillid til, at et tilsvarende element indeholder de følsomme oplysninger, du leder efter. Se Grundlæggende [dele af en følsom oplysningstype for at få](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) mere at vide om tillidsniveauer.
Afstand – Antallet af tegn mellem primært og understøttende element

### <a name="you-supply-your-own-schema-and-data"></a>Du angiver dit eget skema og dine egne data

[Microsoft 365 leveres med mere end 200 SITS](sensitive-information-type-entity-definitions.md) med foruddefinerede skemaer, regex-mønstre, nøgleord og tillidsniveauer. Med EDM SIT'er er du ansvarlig for at definere skemaet samt primære og sekundære felter, der identificerer følsomme elementer. Da skemaet og de primære og sekundære dataværdier er meget følsomme, krypterer du dem via en [hash-funktion](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) , der indeholder en tilfældigt genereret eller selvopret [saltværdi](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) . Disse hashede værdier uploades derefter til tjenesten, så dine følsomme data aldrig er åbne.

### <a name="primary-and-secondary-support-elements"></a>Primære og sekundære supportelementer

Når du opretter et EDM SIT, definerer du *et primært elementfelt* i regelpakken. Primære felter er de elementer, som der søges i alt dit indhold for, og som skal følge et defineret mønster for at blive identificeret. Når det primære element findes i scannede elementer, leder EDM derefter efter de sekundære eller  supplerende elementer, som ikke behøver at følge et mønster, og deres afstand til det primære element. EDM kræver, at det primære element først kan findes via et eksisterende SIT. Se [Enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md) for at få en komplet liste over de tilgængelige SIT'er. Du er nødt til at finde en af dem, der registrerer den klasse, du vil have din EDM SIT til at registrere. Hvis f.eks. dit EDM SIT-skema har amerikanske CPR-nummer som det primære element, ville du, når du opretter dit EDM-skema, knytte det til det amerikanske [CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) SIT.


## <a name="how-matching-works"></a>Sådan fungerer matchende

EDM finder forekomster ved at sammenligne indhold, det finder, med en tabel med følsomme data, som du definerer. Test af match udføres ved hjælp af en kombination af traditionelle regler og mønstre for at sikre, at de matchede data er en faktisk forekomst af data, du vil finde og beskytte. EDM fungerer som det centrale element ved at sammenligne strenge i dine dokumenter og mails med værdier i en tabel med følsomme data, du angiver, for at finde ud af, om værdierne i dit indhold findes i tabellen, ved at sammenligne krypterede hashs.

> [!TIP]
> En almindelig fremgangsmåde er at kombinere brugen af typer af følsomme oplysninger i EDM og de almindelige typer af følsomme oplysninger, som de er baseret på i DLP-regler, med forskellige grænseværdier. Du kan f.eks. bruge en EDM-følsom oplysningstype, der søger efter CPR-numre og andre data, med strenge krav og lav tolerance, hvor en eller flere matches medfører en DLP-besked, og bruge den almindelige type af følsomme oplysninger, f.eks. DET amerikanske CPR-nummer, der er indbygget i et højere antal.  

## <a name="see-also"></a>Se også

- [Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
   
