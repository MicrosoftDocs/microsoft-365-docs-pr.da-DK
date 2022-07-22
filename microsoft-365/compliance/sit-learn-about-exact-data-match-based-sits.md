---
title: Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger
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
description: Få mere at vide om præcise datamatchbaserede følsomme oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 25a48a13e66803dec592680c0ad0e9c01b611dc0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949277"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger

[Følsomme oplysningstyper](sensitive-information-type-learn-about.md) bruges til at hjælpe med at identificere følsomme elementer, så du kan forhindre, at de deles utilsigtet eller upassende, for at hjælpe med at finde relevante data i eDiscovery og anvende styringshandlinger på visse typer oplysninger. Du definerer en brugerdefineret type følsomme oplysninger (SIT) baseret på:

- Mønstre
- nøgleord, f.eks *. medarbejder*, *cpr-nummer* eller *id*
- karakter nærhed til beviser i et bestemt mønster
- tillidsniveauer

Men hvad nu, hvis du vil have en brugerdefineret type følsomme oplysninger (SIT), der bruger nøjagtige eller næsten nøjagtige dataværdier i stedet for en, der blev fundet match baseret på generiske mønstre? Med EDM-baseret klassificering (Exact Data Match) kan du oprette en brugerdefineret type følsomme oplysninger, der er designet til at:

- være dynamisk og nemt opdateres
- være mere skalerbar
- resultere i færre falske positiver
- arbejd med strukturerede følsomme data
- håndtere følsomme oplysninger mere sikkert og ikke dele dem med nogen, herunder Microsoft
- bruges sammen med flere Microsoft-cloudtjenester

![EDM-baseret klassificering.](../media/EDMClassification.png)

Med EDM-baseret klassificering kan du oprette brugerdefinerede typer følsomme oplysninger, der refererer til præcise værdier i en database med følsomme oplysninger. Databasen kan opdateres dagligt og indeholde op til 100 millioner rækker med data. Så efterhånden som medarbejdere, patienter eller klienter kommer og går, og registrerer ændringer, forbliver dine brugerdefinerede følsomme oplysningstyper aktuelle og relevante. Og du kan bruge EDM-baseret klassificering med politikker, f.eks[. Microsoft Purview-politikker til forebyggelse af datatab](dlp-learn-about-dlp.md) eller [Microsoft Cloud App Security filpolitikker](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft Purview Information Protection understøtter sprog med dobbeltbytetegnsæt for:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne understøttelse er tilgængelig for typer af følsomme oplysninger. Se [Produktbemærkninger til beskyttelse af oplysninger for dobbeltbytetegnsæt (prøveversion)](mip-dbcs-relnotes.md) for at få flere oplysninger.

## <a name="whats-different-in-an-edm-sit"></a>Hvad er anderledes i et EDM SIT

Når du arbejder med EDM SITs, er det nyttigt at forstå nogle få begreber, der er unikke for dem.  

### <a name="schema"></a>Skema

Skemaet er en XML-fil, der definerer:

- Navnet på skemaet, der senere kaldes *DataStore*. 
- De feltnavne, som din datakildetabel med følsomme oplysninger indeholder. Der er en 1:1-tilknytning af skemafeltnavnet til kolonnenavnet på den følsomme informationskildetabel.
- Hvilke felter der kan søges i.
- Enhver søgning, der ændrer parametre, som kaldes *konfigurerbart match*, f.eks. at ignorere afgrænsere og store og små bogstaver i de værdier, der søges efter.

### <a name="sensitive-information-source-table"></a>Kildetabel med følsomme oplysninger

Den følsomme kildetabel indeholder de følsomme oplysningsværdier, som EDM SIT søger efter. Det består af kolonner og rækker. Kolonneoverskrifterne er feltnavnene, rækkerne er en forekomst af data, og hver celle indeholder værdierne for den pågældende forekomst for det pågældende felt.

Her er et simpelt eksempel på en tabel med følsomme oplysninger.

|Fornavn|Efternavn|Fødselsdag|
|---|---|---|
|Esajas|Langer| 05-05-1960|
|Ana|Bowman|11-24-1971|
|Oscar|Ward|02-12-1998|

### <a name="rule-package"></a>Regelpakke

Alle SIT'er har en regelpakke. Du bruger regelpakken i et EDM SIT til at definere:

- Matches, som angiver det felt, der skal være det primære element, der skal bruges i nøjagtigt opslag. Det kan være et regulært udtryk med eller uden en kontrolsumsvalidering, en nøgleordsliste, en nøgleordsordbog eller en funktion.
- Klassificering, som angiver det match af følsomme typer, der udløser EDM-opslag.
- Understøttende element, der er elementer, der, når de findes, leverer dokumentation, der hjælper med at øge tilliden til kampen. Nøgleordet "SSN" i nærheden af et SSN-tal. Det kan være et regulært udtryk med eller uden kontrolsum, nøgleordsliste, nøgleordsordbog.
- Konfidensniveauer (høj, mellem, lav) afspejler, hvor meget understøttende beviser der blev registreret sammen med det primære element. Jo flere beviser et element indeholder, jo større er tilliden til, at et matchende element indeholder de følsomme oplysninger, du leder efter. Se [Grundlæggende dele af en type følsomme oplysninger](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) for at få mere at vide om tillidsniveauer.
Proximity – Antallet af tegn mellem primært og understøttende element

### <a name="you-supply-your-own-schema-and-data"></a>Du angiver dit eget skema og dine egne data

[Microsoft Purview leveres med mere end 200 SITS](sensitive-information-type-entity-definitions.md) med foruddefinerede skemaer, regex-mønstre, nøgleord og tillidsniveauer. Med EDM SIT'er er du ansvarlig for at definere skemaet samt primære og sekundære felter, der identificerer følsomme elementer. Da skemaet og de primære og sekundære dataværdier er meget følsomme, krypterer du dem via en [hashfunktion](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) , der indeholder en tilfældigt genereret eller selvleveret [saltværdi](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) . Disse hashkodede værdier uploades derefter til tjenesten, så dine følsomme data aldrig er åbne.

### <a name="primary-and-secondary-support-elements"></a>Primære og sekundære supportelementer

Når du opretter et EDM SIT, definerer du et *primært elementfelt* i regelpakken. Primære felter er de elementer, som alt dit indhold søges efter, og som skal følge et defineret mønster for at kunne identificeres. Når det primære element findes i scannede elementer, søger EDM derefter efter de *sekundære* eller understøttende elementer, som ikke behøver at følge et mønster, og deres nærhed til det primære element. EDM kræver, at det primære element først kan findes via et eksisterende SIT. Se [Objektdefinitioner for følsomme oplysninger for](sensitive-information-type-entity-definitions.md) at få en komplet liste over de tilgængelige SIT'er. Du bliver nødt til at finde en af dem, der registrerer den klasse, du vil have din EDM SIT til at registrere. Hvis dit EDM SIT-skema f.eks. har det amerikanske cpr-nummer som det primære element, ville du knytte EDM-skemaet til det [amerikanske CPR-nummer (SSN)](sit-defn-us-social-security-number.md) SIT.

## <a name="how-matching-works"></a>Sådan fungerer matchende

EDM finder resultater ved at sammenligne indhold, der findes, med en tabel med følsomme data, som du definerer. Matchtestene udføres ved hjælp af en kombination af traditionelle regler og mønstre for at sikre, at de matchede data er en faktisk forekomst af data, du vil finde og beskytte. EDM arbejder i sin kerne ved at sammenligne strenge i dine dokumenter og mails med værdier i en tabel med følsomme data, du angiver, for at finde ud af, om værdierne i dit indhold findes i tabellen, ved at sammenligne kryptografiske envejshashs.

> [!TIP]
> En almindelig praksis er at kombinere brugen af EDM Følsomme informationstyper og de almindelige følsomme oplysningstyper, som de er baseret på i DLP-regler, med forskellige tærskler. Du kan f.eks. bruge en EDM-følsom informationstype, der søger efter cpr-numre og andre data, med strenge krav og lav tolerance, hvor et eller flere matches vil forårsage en DLP-besked, og bruge den almindelige følsomme informationstype, f.eks. det indbyggede CPR-nummer til højere antal.  

## <a name="services-that-edm-supports"></a>Tjenester, som EDM understøtter


|Tjeneste  |Steder  |
|---------|---------|
| Microsoft Purview Forebyggelse af datatab    | - SharePoint Online </br>- OneDrive for Business </br>- Teams-chat </br>- Exchange Online </br>- Enheder       |
|Microsoft Defender for Cloud Apps     | - SharePoint Online </br>- OneDrive for Business        |
|Automatisk mærkning (tjenesteside)     |- SharePoint Online </br>- OneDrive for Business </br>- Exchange Online         |
|Automatisk mærkning (klientside)     |- Ord </br>- Excel </br>- PowerPoint </br>- Exchange Desktop-klienter         |
|Kundeadministrer nøgle     |- SharePoint Online </br>- OneDrive for Business </br>- Teams-chat </br>- Exchange Online </br>- Ord </br>- Excel </br>- PowerPoint </br>- Exchange Desktop-klienter </br>- Enheder         |
|eDiscovery     |- SharePoint Online </br>- OneDrive for Business </br>- Teams-chat </br>- Exchange Online </br>- Ord </br>- Excel </br>- PowerPoint </br>- Exchange Desktop-klienter  |
|Styring af insiderrisiko     |- SharePoint Online </br>- OneDrive for Business </br>- Teams-chat </br>- Exchange Online </br>- Ord </br>- Excel </br>- PowerPoint </br>- Exchange Desktop-klienter      |

## <a name="see-also"></a>Se også

- [Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
