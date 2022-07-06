---
title: Opret en forespørgsel for at finde følsomme data, der er gemt på websteder
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
description: Brug DLP (forebyggelse af datatab) i SharePoint Online til at finde dokumenter, der indeholder følsomme data i hele lejeren.
ms.openlocfilehash: 1bb3ed0286f719f9ea9210b4952044081213914f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638317"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Opret en forespørgsel for at finde følsomme data, der er gemt på websteder

Brugere gemmer ofte følsomme data, f.eks. kreditkortnumre, cpr-numre eller personlige, på deres websteder, og med tiden kan det udsætte en organisation for betydelig risiko for tab af data. Dokumenter, der er gemt på websteder – herunder OneDrive for Business websteder – kan deles med personer uden for organisationen, som ikke skal have adgang til oplysningerne. Med Microsoft Purview Forebyggelse af datatab (DLP) i SharePoint Online kan du finde dokumenter, der indeholder følsomme data i hele lejeren. Når du har fundet dokumenterne, kan du samarbejde med dokumentejerne om at beskytte dataene. Dette emne kan hjælpe dig med at oprette en forespørgsel for at søge efter følsomme data.

> [!NOTE]
> Elektronisk registrering eller eDiscovery og DLP er premiumfunktioner, der kræver [SharePoint Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>Danner en grundlæggende DLP-forespørgsel

Der er tre dele, der udgør en grundlæggende DLP-forespørgsel: SensitiveType, antalintervaller og konfidensinterval. Som vist i følgende grafik kræves **SensitiveType:"\<type\>"** og begge **|\<count range\>** dele og **|\<confidence range\>** er valgfrie.

![Eksempelforespørgsel opdelt i påkrævet og valgfri.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Følsom type – påkrævet

Så hvad er hver del? SharePoint DLP-forespørgsler starter typisk med egenskaben  `SensitiveType:"` og et navn på oplysningstypen fra [lageret for følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) og slutter med en  `"`. Du kan også bruge navnet på en [brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md) , som du har oprettet for din organisation. Du kan f.eks. søge efter dokumenter, der indeholder kreditkortnumre. I en sådan forekomst skal du bruge følgende format:  `SensitiveType:"Credit Card Number"`. Da du ikke inkluderede optællingsinterval eller konfidensinterval, returnerer forespørgslen alle dokumenter, hvor der registreres et kreditkortnummer. Dette er den enkleste forespørgsel, du kan køre, og den returnerer de fleste resultater. Vær opmærksom på, at stavemåden og afstanden mellem den følsomme type er vigtig.

### <a name="ranges---optional"></a>Intervaller – valgfri

Begge de næste to dele er områder, så lad os hurtigt undersøge, hvordan et område ser ud. I SharePoint DLP-forespørgsler repræsenteres et grundlæggende område af to tal adskilt af to perioder, som ser sådan ud:  `[number]..[number]`. Hvis  `10..20` bruges, vil dette interval f.eks. hente tal fra 10 til og med 20. Der er mange forskellige intervalkombinationer, og flere er beskrevet i dette emne.

Lad os føje et optællingsområde til forespørgslen. Du kan bruge optællingsområdet til at definere det antal forekomster af følsomme oplysninger, et dokument skal indeholde, før det medtages i forespørgselsresultaterne. Hvis forespørgslen f.eks. kun skal returnere dokumenter, der indeholder præcis fem kreditkortnumre, skal du bruge følgende:  `SensitiveType:"Credit Card Number|5"`. Optællingsinterval kan også hjælpe dig med at identificere dokumenter, der udgør en høj risiko. Din organisation kan f.eks. betragte dokumenter med fem eller flere kreditkortnumre som en høj risiko. Hvis du vil finde dokumenter, der opfylder dette kriterium, skal du bruge denne forespørgsel:  `SensitiveType:"Credit Card Number|5.."`. Du kan også finde dokumenter med fem eller færre kreditkortnumre ved hjælp af denne forespørgsel:  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Konfidensinterval

Endelig er konfidensintervallet tillidsniveauet for, at den registrerede følsomme type faktisk stemmer overens. Værdierne for konfidensområdet fungerer på samme måde som optællingsområdet. Du kan oprette en forespørgsel uden at inkludere et optællingsområde. Hvis du f.eks. vil søge efter dokumenter med et vilkårligt antal kreditkortnumre – så længe konfidensintervallet er 85 % eller højere – skal du bruge denne forespørgsel:  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> Stjernen ( `*` ) er et jokertegn, der betyder, at alle værdier fungerer. Du kan bruge jokertegnet ( `*` ) enten i optællingsområdet eller i konfidensintervallet, men ikke i en følsom type.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Yderligere forespørgselsegenskaber og søgeoperatorer, der er tilgængelige i eDiscovery Center

DLP i SharePoint introducerer også egenskaben LastSensitiveContentScan, som kan hjælpe dig med at søge efter filer, der er scannet inden for en bestemt tidsramme. Du kan finde eksempler på forespørgsler med  `LastSensitiveContentScan` egenskaben i [Eksempler på komplekse forespørgsler](#examples-of-complex-queries) i næste afsnit.

Du kan ikke kun bruge DLP-specifikke egenskaber til at oprette en forespørgsel, men også standardegenskaber for eDiscovery-søgning i SharePoint, f.eks  `Author` . eller  `FileExtension`. Du kan bruge operatorer til at oprette komplekse forespørgsler. Du kan finde en liste over tilgængelige egenskaber og operatorer i blogindlægget [Brug af søgeegenskaber og operatorer med eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) .

## <a name="examples-of-complex-queries"></a>Eksempler på komplekse forespørgsler

I følgende eksempler bruges forskellige følsomme typer, egenskaber og operatorer til at illustrere, hvordan du kan tilpasse dine forespørgsler for at finde præcis det, du leder efter.

<br>

****

|Forespørgsel|Forklaring|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Navnet kan virke mærkeligt, fordi det er så langt, men det er det korrekte navn for den følsomme type. Sørg for at bruge præcise navne fra [lageret med følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Du kan også bruge navnet på en [brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md) , som du har oprettet for din organisation.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Dette returnerer dokumenter med mindst ét match til den følsomme type "Kreditkortnummer". Værdierne for hvert område er de respektive minimum- og maksimumværdier. En enklere måde at skrive denne forespørgsel på er  `SensitiveType:"Credit Card Number"`, men hvor er det sjovt i det?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Dette returnerer dokumenter med 5-25 kreditkortnumre, der blev scannet fra 11. august 2018 til 13. august 2018.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Dette returnerer dokumenter med 5-25 kreditkortnumre, der blev scannet fra 11. august 2018 til 13. august 2018. Filer med et XLSX-filtypenavn er ikke inkluderet i forespørgselsresultaterne.  `FileExtension` er en af de mange egenskaber, du kan inkludere i en forespørgsel. Du kan finde flere oplysninger under [Brug af søgeegenskaber og operatorer med eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Dette returnerer dokumenter, der enten indeholder et kreditkortnummer eller et CPR-nummer.|
|

## <a name="examples-of-queries-to-avoid"></a>Eksempler på forespørgsler, der skal undgås

Ikke alle forespørgsler oprettes ens. Følgende tabel indeholder eksempler på forespørgsler, der ikke fungerer med DLP i SharePoint, og beskriver hvorfor.

<br>

****

|Ikke-understøttet forespørgsel|Grund|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|Du skal tilføje mindst ét tal.|
|`SensitiveType:"NotARule"`|"NotARule" er ikke et gyldigt navn på en følsom type. Det er kun navne i de [følsomme informationstyper, der fungerer](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) i DLP-forespørgsler.|
|`SensitiveType:"Credit Card Number|0"`|Nul er ikke gyldigt som enten minimumværdien eller maksimumværdien i et interval.|
|`SensitiveType:"Credit Card Number"`|Det kan være svært at se, men der er ekstra mellemrum mellem "Kredit" og "Kort", der gør forespørgslen ugyldig. Brug nøjagtige navne på følsomme typer fra [lageret med følsomme oplysningstyper](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|Delen med to punktum må ikke være adskilt af et mellemrum.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Der er for mange pipeafgrænsere (\|). Følg i stedet dette format: `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Da tillidsværdier repræsenterer en procentdel, kan de ikke overstige 100. Vælg i stedet et tal mellem 1 og 100.|
|

## <a name="for-more-information"></a>Du kan få flere oplysninger

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Kør en indholdssøgning](content-search.md)
- [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md)
