---
title: Test et nøjagtigt datamatch for typen af følsomme oplysninger
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
description: konfigurer tjenester
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 31f51a0bfe3833fb45132d1a9f9093b1dcccf285
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622079"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Test et nøjagtigt datamatch for typen af følsomme oplysninger

Når din EDM (Sensitive Information Type) er blevet oprettet, og en time efter at have kontrolleret, at tabellen med følsomme oplysninger er færdig med at uploade og indeksere, kan du teste, at den registrerer de oplysninger, du vil registrere, ved hjælp af testfunktionen i afsnittet Følsomme informationstyper i Compliance Center.
 
>[! BEMÆRK!] Det kan tage et stykke tid, før ændringer i et EDM SIT, der allerede er oprettet, overføres på tværs af systemet. Hvis du foretager ændringer i en EDM-type følsomme oplysninger i forbindelse med fejlfinding af registreringsproblemer, skal du sørge for at vente mindst én time efter, at du har foretaget disse ændringer, før du bruger testfunktionen til at validere virkningen.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Test dit EDM SIT i Compliance Center

1. Åbn **Compliance Center** > **Dataklassificering** > **Følsomme oplysningstyper**.

2. Vælg dit EDM SIT på listen, og vælg derefter **Test** i pop op-ruden. Denne indstilling findes kun under følsomme oplysningstyper.
 
3. Overfør et element, der indeholder data, du vil registrere. Du kan f.eks. oprette et element, der indeholder et undersæt af rækkerne i tabellen med følsomme oplysninger. Hvis du har brugt den konfigurerbare matchfunktion i skemaet til at definere ignorerede afgrænsere, skal du sørge for, at elementet indeholder eksempler med og uden disse afgrænsere.

4. Når filen er blevet uploadet og scannet, skal du kontrollere, om den passer til dit EDM SIT.

5. Hvis funktionen **Test** i SIT registrerer et match, skal du kontrollere, at den ikke trimmes eller udtrækkes forkert. For eksempel ved kun at udtrække en delstreng af den fulde streng, det er meningen at registrere, eller samle op kun det første ord i en flerords streng, eller herunder ekstra symboler eller tegn i udtrækningen. Se [Sprog til regulært udtryk – Hurtig reference](/dotnet/standard/base-types/regular-expression-language-quick-reference) til sprogreferencen til regulære udtryk. 

5. Du kan også bruge følgende PowerShell-cmdlet:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Når du opretter eller redigerer en EDM-følsom informationstype eller det primære SIT, som en EDM-type er baseret på, gennemsøges alt nyt indhold og indhold, der ændres efter ændringerne af SIT'erne, efter tekst, der svarer til de nye definitioner, men eksisterende indhold gennemsøges ikke, før det ændres eller gendexes. 

Hvis du vil gennemtvinge gengennemsøgning af eksisterende indhold på et SharePoint-websted eller -bibliotek eller i OneDrive, skal du følge vejledningen i [Manuelt anmode om gennemsøgning og omdexering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

## <a name="test-your-edm-sit-with-information-protection-policies"></a>Test dit EDM SIT med politikker for beskyttelse af oplysninger

Du kan se, hvor dit EDM SIT bruges, og hvor nøjagtigt det er i produktionen, ved at bruge dem i politikker:

1. Opret en [politik for automatisk mærkning,](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) og kør den i **oversigt over simulering**.

1. Tilføj noget indhold, der udløser EDM SIT og noget indhold, der ikke udløser EDM SIT til en placering, som din politik overvåger.

1. Åbn fanen **Elementer, der skal gennemses** for at kontrollere matchene.

1. Juster dine politikker efter behov. 

Når du er tilfreds med resultaterne af din test og justering, er dit EDM-baserede brugerdefinerede SIT klar til brug i politikker for beskyttelse af oplysninger, f.eks.:

- [DLP-politikker](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Fejlfindingstip

Hvis du ikke finder nogen resultater, er her nogle tip til fejlfinding.

|Problem  |Tip til fejlfinding  |
|---------|---------|
|Der blev ikke fundet nogen resultater     |  Bekræft, at dine følsomme data blev overført korrekt ved hjælp af de kommandoer, der er forklaret i [Hash, og upload tabellen med følsomme oplysninger for at få præcise data til at matche følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Der blev ikke fundet nogen resultater   | Test det SIT, du brugte, da du konfigurerede det primære element i hvert af dine mønstre. Dette bekræfter, at SIT kan matche eksemplerne i elementet. Hvis du bruger et FORKERT defineret SIT som klassificeringselement i en EDM-type følsomme oplysninger, er det den mest almindelige årsag til registreringsfejl i EDM.         |
|Det SIT, du har valgt for et primært element i EDM-typen, kan ikke finde et match i elementet eller finder færre forekomster, end du forventede.    |  Kontrollér, at den understøtter de separatorer og afgrænsere, der findes i indholdet. Sørg for at medtage de ignorerede afgrænsere, der er defineret i skemaet.       |
|Det primære element SIT finder forekomster i et element, men det gør EDM SIT ikke.     | – Kontrollér, om dine REGEX-sætninger starter eller afslutter hentning af mellemrumsafgrænsere, f.eks. \s. Mellemrumstegnene stemmer ikke overens med den hashkodede værdi i datatabellen. Brug i stedet et ordafgrænser, f.eks. \b. </br> – Kontrollér dine REGEX-sætninger for at sikre, at de registrerer hele den streng, du vil registrere, ikke kun en understreng. Dette mønster for mailadresser \b[a-zA-Z]{2,30}@[a-zA-Z]{2,20}.[ a-zA-Z]{2,3}\b matcher *user@contoso.com* korrekt, men registrerer kun *user@contoso.co.jp* i ufuldstændig form.
|Et EDM SIT med primære elementer og ingen definerede sekundære elementer registrerer elementer, men registrerer ikke eller registrerer færre match end forventet, når der kræves primære og sekundære elementer.  | Hvis værdier i en kolonne, der bruges til sekundært bevis, ikke består af et enkelt ord eller strenge, der ikke indeholder mellemrum, kommaer eller andre ordseparatorer, skal du knytte dem til en følsom infotype, der bruger enten en REGEX, der er udviklet til at registrere strenge med flere ord, der følger det ønskede mønster (f.eks. et fast antal ord efter hinanden, der starter med et stort tegn),  eller en nøgleordsordbog, der viser alle de entydige værdier i den pågældende kolonne. Hvis der f.eks. er en ekstra beviskolonne for en persons by eller bopæl, kan du oprette en liste med alle de entydige bynavne fra tabellen og bruge den til at oprette en ordbogsbaseret følsom oplysningstype. Brug dette SIT som klassificeringselement for den tilsvarende kolonne i din følsomme EDM-oplysningstype ved at eksportere og redigere EDM SIT-definitionen i XML. Se [Opret en regelpakke manuelt](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually).|
|Testfunktionen SIT registrerer slet ikke nogen match.   | Kontrollér, om det SIT, du har valgt, indeholder krav til yderligere nøgleord eller andre valideringer. Hvis du vil se de indbyggede SIT'er, skal du se [Objektdefinitioner for følsomme oplysninger](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) for at kontrollere, hvad minimumskravene er for at matche hver type.        |
|Testfunktionen fungerer, men dine SharePoint- eller OneDrive-elementer registreres ikke i DLP- eller regler for automatisk mærkning     | Kontrollér, om de dokumenter, du forventer at matche, vises i Indholdsoversigt. Hvis de ikke er der, skal du huske, at kun indhold, der er oprettet efter ændringerne af typen af følsomme oplysninger, vises som match. Du skal gennemsøg webstederne og bibliotekerne igen, før eksisterende elementer vises. Se [Anmodning om gennemsøgning og gensøgning af et websted, et bibliotek eller en liste manuelt](/sharepoint/crawl-site-content) for at få oplysninger om gennemsøgning af SharePoint og OneDrive.        |
|DLP- eller regler for automatisk mærkning, der kræver flere forekomster, udløses ikke     |Kontrollér, at nærhedskravene for både din EDM-type og de grundlæggende følsomme oplysningstyper er opfyldt. Hvis den maksimale afstand mellem det primære element og de understøttende nøgleord f.eks. er 300 tegn, men nøgleordene kun findes i den første række i en lang tabel, er det sandsynligvis kun de første få rækker med tilsvarende værdier, der opfylder nærhedskravene. Rediger dine SIT-definitioner for at understøtte mere afslappede nærhedsregler, eller brug indstillingen hvor som helst i dokumentet til yderligere bevisbetingelser.         |
|Registrering af en EDM-type er inkonsistent eller uregelmæssig     |Kontrollér, at den type følsomme oplysninger, du brugte som basis for det primære element i din EDM-type, ikke registrerer unødvendigt indhold. Hvis du bruger et SIT, der matcher for meget ikke-relateret indhold, f.eks. et hvilket som helst ord, et vilkårligt tal eller alle mailadresser, kan tjenesten blive mættet og ignorere relevante matches. Kontrollér antallet af indholdsdele, der svarer til den følsomme type, du brugte til dine primære elementer i Indholdsoversigt. </br> Sådan estimerer du, om SIT matcher for meget indhold: </br> – Opdeling af antallet af indholdselementer i Indholdsoversigt med antallet af dage, siden den følsomme type blev oprettet. </br> – Hvis antallet af matches pr. dag er inden for intervallet hundredtusindvis eller millioner, er det muligt, at det primære SIT er for bredt. Se [Få mere at vide om præcise datamatchbaserede følsomme informationstyper](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) for at få anbefalinger og bedste praksis for valg af den rette type følsomme oplysninger til en EDM-type.         |
