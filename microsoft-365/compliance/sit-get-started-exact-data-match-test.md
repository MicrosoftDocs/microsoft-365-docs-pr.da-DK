---
title: Teste en nøjagtig datatype, der matcher følsomme oplysninger
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
description: konfigurere tjenester
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0870cda205168e73d40adef7cdab333c7f0abdf
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679934"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Teste en nøjagtig datatype, der matcher følsomme oplysninger

Når du har oprettet din nøjagtige datamatchingtype (EDM) sensitive information type (SIT), og en time efter at have kontrolleret, at din tabel med følsomme oplysninger er uploadet og indekseret, kan du teste, at den registrerer de oplysninger, du vil registrere, ved hjælp af testfunktionen i sektionen med følsomme oplysningstyper i Overholdelsescenter.
 
>[! BEMÆRK!] Ændringer i et allerede oprettet EDM SIT kan tage lidt tid at overføres på tværs af systemet. Hvis du foretager ændringer i en type af EDM-følsomme oplysninger til fejlfinding af problemer med registrering, skal du sørge for at vente mindst en time efter, at du har foretaget disse ændringer, før du bruger testfunktionen til at validere deres virkning.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Test din EDM SIT i Overholdelsescenter

1. Åbn **OverholdelsescenterDataklassificeringSensitive** >  >  **informationstyper**.

2. Vælg dit EDM SIT på listen, og vælg **derefter Test** i pop op-ruden. Denne indstilling findes kun under typer af følsomme oplysninger.
 
3. Upload element, der indeholder data, du vil registrere. Du kan f.eks. oprette et element, der indeholder et undersæt af rækkerne i tabellen med følsomme oplysninger. Hvis du har brugt funktionen match, der kan konfigureres, i dit skema til at definere ignorerede afgrænsere, skal du sikre dig, at elementet indeholder eksempler med og uden disse afgrænsere.

4. Når filen er blevet uploadet og scannet, skal du kontrollere, om der er forekomster i din EDM SIT.

5. Hvis funktionen **Test** i SIT registrerer et match, skal du kontrollere, at den ikke trimmes, eller at den udtrækkes forkert. For eksempel ved kun at udtrække en understreng af den fulde streng, som den skal registrere, eller ved kun at hente det første ord i en streng med flere ord eller medtage ekstra symboler eller tegn i udtrækningen. Se [Sprog til regulært udtryk – Hurtig reference](/dotnet/standard/base-types/regular-expression-language-quick-reference) for referencen til regulære udtryk. 

5. Alternativt kan du bruge følgende PowerShell-cmdlet:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Når du opretter en eller redigerer en EDM-følsom oplysningstype eller den primære SIT, som en EDM-type er baseret på, vil alt nyt indhold og alt nyt indhold, der ændres, efter ændringerne af SIT'erne blive gennemsøgt for tekst, der svarer til de nye definitioner, men eksisterende indhold gennemsøges ikke, før det ændres eller indekseres igen. 

Hvis du vil gennemtvinge gennemsøgning af eksisterende indhold på et SharePoint-websted eller -bibliotek eller i OneDrive, skal du følge instruktionerne i Anmod manuelt om gennemsøgning og gensøgning af et websted[,](/sharepoint/crawl-site-content) et bibliotek eller en liste.

## <a name="test-your-edm-sit-in-mip-policies"></a>Test din EDM SIT i MIP-politikker

Du kan se, hvor din EDM SIT bruges, og hvor nøjagtig den er i produktion, ved hjælp af dem i politikker:

1. Opret en [politik for automatisk mærkning, og kør](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) den i **Simuleringsoversigt**.

1. Tilføj noget indhold, der udløser EDM SIT og noget indhold, der ikke udløser EDM SIT, til en placering, som din politik overvåger.

1. Åbn fanen **Elementer for at gennemse** for at kontrollere matchene.

1. Finjuster dine politikker efter behov. 

Når du er tilfreds med resultaterne af din test og justering, er dit EDM-baserede brugerdefinerede SIT klar til brug i politikker for beskyttelse af oplysninger, f.eks.:

- [DLP-politikker](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Defender til skyapps](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Tip til fejlfinding

Hvis du ikke finder nogen resultater, er her nogle tip til fejlfinding.


|Problem  |Tip til fejlfinding  |
|---------|---------|
|Der blev ikke fundet nogen forekomster     |  Bekræft, at dine følsomme data blev overført korrekt ved hjælp af de kommandoer, der er forklaret i Hash, og overfør kildetabellen for følsomme oplysninger for at finde nøjagtige [data, der svarer til følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Der blev ikke fundet nogen forekomster   | Test det SIT, du brugte, da du konfigurerede det primære element i hver af dine mønstre. Dette bekræfter, at SIT kan matche eksemplerne i elementet. Brug af et forkert defineret SIT som klassificeringselementet i en type af EDM-følsomme oplysninger er den mest almindelige årsag til registreringsfejl i EDM.         |
|Det SIT, du valgte til det primære element i EDM-typen, finder ikke et match i elementet eller finder færre resultater end forventet    |  Kontrollér, at den understøtter de separatorer og separatorer, der findes i indholdet. Sørg for at medtage de ignorerede afgrænsere, der er defineret i dit skema.       |
|Det primære element SIT finder forekomster i et element, men EDM SIT gør det ikke.     | - Kontrollér dine REGEX-sætninger for at starte eller afslutte en registrering af mellemrumsafgrænser, f.eks. /s. Mellemrummet stemmer ikke overens med den gemte værdi i datatabellen. Brug en ordafgrænser som f.eks. /b i stedet. </br> - Kontrollér dine REGEX-sætninger for at sikre, at de registrerer hele den streng, du vil registrere, ikke kun en understreng. Dette mønster for mailadresser [a-zA-Z]{30}@[a-zA-Z]{20}.[ a-zA-Z]{2,3} matcher *user@contoso.com* *og user@contoso.co.jp*.  |
|Et EDM SIT med primære elementer og ingen definerede sekundære elementer registrerer elementer, men registrerer eller registrerer ikke færre end forventet, når primære og sekundære elementer er påkrævede.  | Sørg for, at værdierne for sekundære beviser består af et enkelt ord eller en enkelt streng, der ikke indeholder mellemrum, eller at bruge REGEX-sætninger, der registrerer flerordsstrenge. F.eks.: \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, som matcher sekvenserne et til fem fortløbende ord, der starter med et stort bogstav. Brug denne SIT som klassificeringselementet for de yderligere beviser i XML-følsomme oplysninger af EDM-typen. Se [Opret en regelpakke manuelt](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|SIT-testfunktionen registrerer slet ingen forekomster.   | Kontrollér, om det SIT, du har valgt, indeholder krav til yderligere nøgleord eller andre valideringer. For de indbyggede SIT'er skal du [](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) se Enhedsdefinitioner for følsomme oplysningstyper for at bekræfte, hvad minimumskravene er til at matche hver type.        |
|Funktionen Test fungerer, men dine SharePoint eller OneDrive elementer registreres ikke i DLP- eller automatisk mærkningsregler     | Kontrollér, om de dokumenter, du ville forvente, matcher, vises i Indholdsstifinder. Hvis de ikke er der, skal du huske, at det kun er indhold, der er oprettet efter ændringerne af typen af følsomme oplysninger, der vises som resultater. Du skal gengle webstederne og bibliotekerne, før eksisterende elementer vises. Se [Anmod manuelt](/sharepoint/crawl-site-content) om gennemsøgning og gensøgning af et websted, et bibliotek eller en liste for at få oplysninger om genkodning af SharePoint og OneDrive.        |
|DLP- eller regler for automatisk mærkater, der kræver flere matches, udløser ikke     |Kontrollér, at kravene til afstand for både din EDM-type og de grundlæggende følsomme oplysningstyper er opfyldt. Hvis f.eks. den maksimale afstand mellem det primære element og understøttende nøgleord er 300 tegn, men nøgleordene kun findes i den første række i en lang tabel, vil kun de første par rækker med matchende værdier sandsynligvis opfylde kravene til afstand. Rediger dine SIT-definitioner for at understøtte regler for mindre afstand, eller brug et vilkårligt sted i dokumentindstillingen til de yderligere bevisbetingelser.         |
|Registrering af en EDM-type er inkonsekvent eller fejlagtig     |Kontrollér, at den type af følsomme oplysninger, du har brugt som basis for det primære element i din EDM-type, ikke registrerer unødvendigt indhold. Hvis du bruger et SIT, der svarer til for meget indhold uden relation, f.eks. et hvilket som helst ord, et tal eller alle mailadresser, kan det medføre, at tjenesten bliver mættet og ignorerer relevante matches. Kontrollér antallet af indholdsstykker, der svarer til den følsomme type, du har brugt til dine primære elementer i indholdsstifinder. </br> Sådan estimerer du, om SIT matcher for meget indhold: </br> - Dividere antallet af indholdselementer i Indholdsstifinder med antallet af dage, siden den følsomme type blev oprettet. </br> - Hvis antallet af matches pr. dag er inden for området hundreder af tusinder eller millioner, er det muligt, at det primære SIT er for bredt. Se [Få mere at vide om nøjagtige datamatchingbaserede](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) typer af følsomme oplysninger for at få anbefalinger og bedste fremgangsmåder til at vælge den rigtige type af følsomme oplysninger til en EDM-type.         |