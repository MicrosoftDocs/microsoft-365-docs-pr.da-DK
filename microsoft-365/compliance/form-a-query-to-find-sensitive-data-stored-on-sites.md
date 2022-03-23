---
title: Oprette en forespørgsel for at finde følsomme data, der er gemt på websteder
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Brug forebyggelse af datatab (DLP) i SharePoint Online til at finde dokumenter, der indeholder følsomme data i hele din lejer.
ms.openlocfilehash: af1ca8f28f80d58c0f366e1a002181e23db3d552
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588711"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Oprette en forespørgsel for at finde følsomme data, der er gemt på websteder

Brugere gemmer ofte følsomme data, f.eks. kreditkortnumre, personnumre eller personnumre, på deres websteder, og med tiden kan dette udsætte en organisation for en betydelig risiko for datatab. Dokumenter, der er gemt på websteder – OneDrive for Business websteder – kan deles med personer uden for organisationen, som ikke bør have adgang til oplysningerne. Med forebyggelse af datatab (DLP) i SharePoint Online kan du finde dokumenter, der indeholder følsomme data i hele din lejer. Når du har opdaget dokumenterne, kan du arbejde sammen med dokumentejerne om at beskytte dataene. Dette emne kan hjælpe dig med at oprette en forespørgsel for at søge efter følsomme data.

> [!NOTE]
> Electronic Discovery, eller eDiscovery, og DLP er førsteklasses funktioner, der [kræver SharePoint Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>Oprette en grundlæggende DLP-forespørgsel

Der er tre dele, der udgør en grundlæggende DLP-forespørgsel: SensitiveType, count range og confidence range. Som det fremgår af følgende grafik er **SensitiveType:"\<type\>"** påkrævet, og begge er **|\<count range\>** **|\<confidence range\>** valgfrie.

![Eksempelforespørgsel opdelt i påkrævet og valgfri.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Følsom type – påkrævet

Så hvad er hver del? SharePoint DLP-forespørgsler starter typisk med egenskaben og et oplysningstypenavn `SensitiveType:"` fra lageret med følsomme [oplysninger og slutter](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) med et `"`. Du kan også bruge navnet på en [brugerdefineret type af følsomme oplysninger,](create-a-custom-sensitive-information-type.md) du har oprettet for organisationen. Du kan f.eks. være på udkig efter dokumenter, der indeholder kreditkortnumre. I sådan en forekomst skal du bruge følgende format:  `SensitiveType:"Credit Card Number"`. Da du ikke medtager antal områder eller tillidsområde, returnerer forespørgslen alle dokumenter, hvor der er registreret et kreditkortnummer. Dette er den mest enkle forespørgsel, du kan køre, og den returnerer de fleste resultater. Husk, at stavningen og afstanden for den følsomme type har betydning.

### <a name="ranges---optional"></a>Områder – valgfrit

Begge de næste to dele er områder, så lad os hurtigt undersøge, hvordan et område ser ud. I SharePoint DLP-forespørgsler er et grundlæggende område repræsenteret af to tal adskilt af to punktummer, som ser sådan ud: `[number]..[number]`. Hvis det f.eks  `10..20` . bruges, registrerer dette område tal fra 10 til 20. Der findes mange forskellige områdekombinationer, og flere er dækket i dette emne.

Lad os føje et antal områder til forespørgslen. Du kan bruge antal områder til at definere antallet af forekomster af følsomme oplysninger, som et dokument skal indeholde, før det medtages i forespørgselsresultaterne. Hvis du f.eks. kun vil have forespørgslen til at returnere dokumenter, der indeholder præcis fem kreditkortnumre, skal du bruge følgende:  `SensitiveType:"Credit Card Number|5"`. Antal områder kan også hjælpe dig med at identificere dokumenter, der udgør høje risikograder. Din organisation kan f.eks. overveje dokumenter med fem eller flere kreditkortnumre, der er forbundet med en høj risiko. For at finde dokumenter, der passer til dette kriterium, skal du bruge denne forespørgsel:  `SensitiveType:"Credit Card Number|5.."`. Du kan også finde dokumenter med fem eller færre kreditkortnumre ved hjælp af denne forespørgsel:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Tillidsområde

Endelig er tillidsområdet det tillidsniveau, som den registrerede følsomme type faktisk er ens. Værdierne for tillidsområdet fungerer på samme måde som antal områder. Du kan oprette en forespørgsel uden at medtage et antal områder. Hvis du f.eks. vil søge efter dokumenter med et vilkårligt antal kreditkortnumre – så længe tillidsintervallet er 85 % eller højere – skal du bruge denne forespørgsel:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Stjernen ( ) er `*` et jokertegn, der betyder, at enhver værdi fungerer. Du kan bruge jokertegnet ( `*` ) enten i optællingsområdet eller i tillidsområdet, men ikke i en følsom type.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Yderligere forespørgselsegenskaber og søgeoperatorer, der er tilgængelige i eDiscovery-center

DLP i SharePoint introducerer også egenskaben LastSensitiveContentScan, som kan hjælpe dig med at søge efter filer, der er scannet inden for en bestemt tidsramme. Se eksempler på forespørgsler med  `LastSensitiveContentScan` egenskaben i [Eksempler på komplekse forespørgsler](#examples-of-complex-queries) i næste afsnit.

Du kan ikke kun bruge DLP-specifikke egenskaber til at oprette en forespørgsel, men også SharePoint eDiscovery-søgeegenskaber som f.eks. `Author` eller `FileExtension`. Du kan bruge operatorer til at opbygge komplekse forespørgsler. Du kan finde en liste over tilgængelige egenskaber og operatorer i [Brug af søgeegenskaber og operatorer med eDiscovery-blogindlægget](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) .

## <a name="examples-of-complex-queries"></a>Eksempler på komplekse forespørgsler

Følgende eksempler bruger forskellige følsomme typer, egenskaber og operatorer til at illustrere, hvordan du kan afgrænse dine forespørgsler for at finde præcis det, du leder efter.

<br>

****

|Forespørgsel|Forklaring|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Navnet kan se mærkelig ud, fordi det er så langt, men det er det korrekte navn for den pågældende følsomme type. Sørg for at bruge nøjagtige navne fra lageret [med følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Du kan også bruge navnet på en [brugerdefineret type af følsomme oplysninger,](create-a-custom-sensitive-information-type.md) du har oprettet for organisationen.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Dette returnerer dokumenter med mindst ét match til den følsomme type "Kreditkortnummer". Værdierne for hvert område er de respektive minimum- og maksimumværdier. En enklere måde at skrive denne forespørgsel på er  `SensitiveType:"Credit Card Number"`, men hvor er det sjovt i det?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Dette returnerer dokumenter med 5-25 kreditkortnumre, der er scannet fra 11. august 2018 til den 13. august 2018.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Dette returnerer dokumenter med 5-25 kreditkortnumre, der er scannet fra 11. august 2018 til den 13. august 2018. Filer med filtypenavnet XLSX medtages ikke i forespørgselsresultaterne.  `FileExtension` er en af mange egenskaber, som du kan medtage i en forespørgsel. Få mere at vide under [Brug af søgeegenskaber og operatorer med eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Dette returnerer dokumenter, der indeholder enten et kreditkortnummer eller et CPR-nummer.|
|

## <a name="examples-of-queries-to-avoid"></a>Eksempler på forespørgsler, du kan undgå

Ikke alle forespørgsler er ens. Følgende tabel indeholder eksempler på forespørgsler, der ikke fungerer med DLP i SharePoint og beskriver hvorfor.

<br>

****

|Ikke-understøttet forespørgsel|Årsag|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|Du skal tilføje mindst ét tal.|
|`SensitiveType:"NotARule"`|"NotARule" er ikke et gyldigt navn på følsom type. Kun navne i [beholdningen af følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) fungerer i DLP-forespørgsler.|
|`SensitiveType:"Credit Card Number|0"`|Nul er ikke gyldig som enten minimumværdien eller maksimumværdien i et område.|
|`SensitiveType:"Credit Card Number"`|Det kan være svært at se, men der er ekstra mellemrum mellem "Kredit" og "Kort", der gør forespørgslen ugyldig. Brug nøjagtige følsomme typenavne fra lageret [med følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|De to periodedel skulle ikke være adskilt af et mellemrum.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Der er for mange pipe-afgrænsere (\|). Følg i stedet dette format: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Da tillidsværdier repræsenterer en procentdel, kan de ikke overstige 100. Vælg et tal mellem 1 og 100 i stedet.|
|

## <a name="for-more-information"></a>Du kan finde flere oplysninger

- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Køre en indholdssøgning](content-search.md)
- [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)
