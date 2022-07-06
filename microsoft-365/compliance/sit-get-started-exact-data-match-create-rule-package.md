---
title: Opret nøjagtigt datamatch for typer/regelpakker af følsomme oplysninger
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
description: Opret nøjagtigt datamatch for typer/regelpakker af følsomme oplysninger
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 16da97f249eff856fd1b0e671d71d813b3cbac73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628501"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Opret nøjagtigt datamatch for typer/regelpakker af følsomme oplysninger

Du kan oprette et nøjagtigt datamatch (EDM) sensitive information type (SIT) ved hjælp af [EDM-skemaet og GUIDEN SIT](#use-the-edm-schema-and-sit-wizard) i Overholdelsescenter eller oprette XML-filen til regelpakken [manuelt](#create-a-rule-package-manually). Du kan også kombinere begge ved hjælp af én metode til at oprette skemaet og senere redigere det ved hjælp af den anden metode.

Hvis du ikke er bekendt med EDM-baseret SITS eller deres implementering, skal du gøre dig bekendt med:

- [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Brug EDM-skemaet og SIT-guiden

Du kan bruge denne guide til at oprette DINE SIT-filer (Sensitive Information Type) for at hjælpe med at forenkle processen.

En type følsomme EDM-oplysninger består af et eller flere mønstre. Hvert mønster beskriver en kombination af beviser (felter fra skemaet), der bruges til at identificere følsomt indhold i et dokument eller en mail.

## <a name="pre-requisites"></a>Forudsætninger

Udfør trinnene i disse artikler:

1. [Eksportér kildedata for at finde nøjagtigt datamatch baseret på følsom oplysningstype](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Hash og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der stemmer overens med typer af følsomme oplysninger](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Uanset om du opretter en EDM-følsom oplysningstype ved hjælp af guiden eller XML-regelpakken via PowerShell, skal du have tilladelser som global administrator eller overholdelsesadministrator for at oprette, teste og installere en brugerdefineret type følsomme oplysninger via brugergrænsefladen. Se [Om administratorroller i Office 365](/office365/admin/add-users/about-admin-roles).
- Identificer en af de indbyggede SIT'er, der skal bruges som den følsomme informationstype for primære elementer.
  - Hvis ingen af de indbyggede følsomme infotyper stemmer overens med dataene i den valgte kolonne, skal du oprette en brugerdefineret type følsomme oplysninger, der gør.
  - Hvis du har valgt indstillingen Ignorerede afgrænsere for den primære elementkolonne i skemaet, skal du sørge for, at det brugerdefinerede SIT, du opretter, vil matche data med og uden de valgte afgrænsere.
  - Hvis du bruger et indbygget SIT, skal du sørge for, at det registrerer præcis de strenge, du vil vælge, og ikke inkludere omgivende tegn eller udelade en gyldig del af strengen, som er gemt i din tabel med følsomme oplysninger.

Se [Objektdefinitioner for følsomme oplysninger og](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) [Opret brugerdefinerede følsomme oplysningstyper i Overholdelsescenter](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Brug guiden Med det nøjagtige datamatchskema og mønsteret for følsomme oplysninger

1. I Microsoft Purview-compliance-portal for din lejer skal du gå til **Dataklassificering** > **Præcise dataforekomster**.

2. Vælg **EDM-følsomme infotyper** og **Opret EDM-følsom infotype** for at åbne konfigurationsguiden til konfiguration af følsomme oplysninger.

3. Vælg **Vælg et eksisterende EDM-skema** , og vælg det skema, du oprettede i [Opret skemaet til præcise datamatchbaserede typer følsomme oplysninger](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Vælg **Næste** , og vælg **Opret mønster**.

5. Vælg **tillidsniveauet** og **det primære element**. Du kan få mere at vide om tillidsniveauer under [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Vælg det **primære elements følsomme oplysningstype** for at definere, hvilken tekst i dokumentet der skal sammenlignes med alle værdierne i feltet med det primære element. Se [Objektdefinitioner for følsomme oplysninger for](sensitive-information-type-entity-definitions.md) at få mere at vide om de tilgængelige typer følsomme oplysninger.

   > [!IMPORTANT]
   > Vælg en type følsomme oplysninger, der svarer til formatet af det indhold, du vil finde. Hvis du vælger en type følsomme oplysninger, der svarer til unødvendigt indhold, f.eks. et, der stemmer overens med alle tekststrenge, eller alle tal, kan det medføre en stor belastning i systemet, hvilket kan medføre, at følsomme oplysninger overses.

7. Vælg dine **understøttende elementer** , og match indstillinger.

8. Vælg **Udført** og **Næste**.

9. Vælg det ønskede **genkendelsesniveau og den ønskede nærhed af tegn**. Dette er standardværdien for hele typen af følsomme EDM-oplysninger.

10. Vælg **Opret mønster** , hvis du vil oprette yderligere mønstre for din EDM-følsomme infotype.

11. Vælg **Næste** , og udfyld et **navn** og en **beskrivelse til administratorer**.

12. Gennemse, og vælg **Send**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Rediger eller slet mønsteret for følsomme oplysninger

1. Open **Compliance Center** > **Dataklassificering** > **Præcise dataforekomster**.

2. Vælg **EDM-følsomme infotyper**.

3. Vælg det EDM SIT, du vil redigere.

4. Vælg **Rediger EDM-følsom infotype** eller **Slet EDM-følsom infotype** fra pop op-vinduet.

## <a name="working-with-specific-types-of-data"></a>Arbejde med bestemte datatyper

Af hensyn til ydeevnen er det afgørende, at du bruger mønstre, der minimerer antallet af unødvendige matches. Du kan f.eks. bruge en følsom oplysningstype, der er baseret på regulært udtryk.

`\b\w*\b`

Dette vil stemme overens med hvert enkelt ord eller nummer i et dokument eller en mail. Dette vil medføre, at tjenesten overbelastes med match og ikke registrerer sande match. Brug af mere præcise mønstre kan undgå denne situation. Her er nogle anbefalinger til, hvordan du identificerer den rigtige konfiguration for nogle almindelige datatyper.

**Mailadresser**: Mailadresser kan være nemme at identificere, men da de er så almindelige i indhold, kan de medføre en betydelig belastning i systemet, hvis de bruges som et primært felt. Brug dem kun som sekundære beviser. Hvis de skal bruges som det primære bevis, kan du forsøge at definere en brugerdefineret type følsomme oplysninger, der bruger logik til at udelukke brugen af dem som `From` eller `To` felter i mails og til at ekskludere dem med din virksomheds mailadresse for at reducere antallet af unødvendige strenge, der skal matches.

**Telefonnumre**: Telefonnumre kan fås i mange forskellige formater, herunder eller udelade landepræfikser, områdekoder og separatorer. Hvis du vil reducere de falske negativer, samtidig med at belastningen holdes på et minimum, skal du kun bruge dem som sekundære elementer, udelade alle sandsynlige separatorer, f.eks. parenteser og tankestreger og kun inkludere den del i din følsomme datatabel, der altid vil være til stede i telefonnummeret.

**Personnavne**: Brug ikke personens navne som primære elementer, hvis du bruger en følsom oplysningstype baseret på et regulært udtryk som klassificeringselement for denne EDM-type, fordi de er svære at skelne fra almindelige ord.

Hvis du skal bruge et primært element, der er svært at identificere med et bestemt mønster, f.eks. et projektkodenavn, der kan generere mange match, der skal behandles, skal du sørge for at medtage nøgleord i den følsomme oplysningstype, du bruger som klassificeringselement for din EDM-type. Hvis du f.eks. bruger projektkodenavne, der kan være almindelige ord, kan du bruge ordet `project` som yderligere påkrævede beviser i nærheden af det regulære mønster for projektnavnets regulære udtryk i den følsomme type, der bruges som klassificeringselement for din EDM-type. Eller du kan overveje at bruge en følsom type, der er baseret på en almindelig ordbog, som klassificeringselement for dit EDM SIT.

Når du forsøger at matche numeriske strenge, skal du angive de tilladte intervaller af tal, f.eks. antallet af cifre eller startcifrene, hvis det er kendt. Hvis du har brug for at matche et relativt fleksibelt interval af tal, kan du bruge nøgleord i basis-SIT til at reducere antallet af matches. Hvis du f.eks. forsøger at matche kontonumre, der består af 7-11 cifre, skal du føje ordene `account`, `customer`til `acct.` SIT som yderligere dokumentation. Dette reducerer sandsynligheden for unødvendige matches, der kan medføre, at grænserne for match, der behandles af EDM, overskrides.

Hvis et felt, du skal bruge som et primært element, følger et simpelt mønster, der kan medføre et stort antal match, og du ikke kan tilføje tilstedeværelsen af nøgleord som yderligere beviser i typen af følsomme oplysninger, kan du alternativt kræve et minimum antal forekomster af mønsteret. Du kan f.eks. bruge en brugerdefineret type følsomme oplysninger, der er defineret på følgende måde, til at registrere mindst 29 andre femcifrede tal omkring et potentielt femcifret tal, der stemmer overens med EDM:

```xml
 <Entity id="98703510-18b3-43d4-961f-15317594beb7"
                  patternsProximity="300"
                  recommendedConfidence="85"
                  relaxProximity="false">
                  <Pattern confidenceLevel="85"
                              proximity="300">
                              <IdMatch idRef="MRN"/>
                              <Match idRef="30 AccountNrs"
                                    minCount="30"
                                    proximity="3000"
                                    uniqueResults="true"/>
                  </Pattern>
      </Entity>
      <Regex id="30 AccountNrs">\d{5}</Regex>
```

I nogle tilfælde skal du muligvis identificere bestemte konto- eller postidentifikationsnumre, der af historiske årsager ikke følger et standardiseret mønster. Kan f.eks `Medical Record Numbers` . bestå af mange forskellige permutationer af bogstaver og tal i samme organisation. Selvom det i første omgang kan være svært at identificere et mønster, kan du ofte bruge tættere kontrol til at indsnævre et mønster, der beskriver alle gyldige værdier, uden at det medfører et stort antal ugyldige matches. Det kan f.eks. blive registreret, at "alle MRN'er er mindst syv tegn lange, har mindst to numeriske cifre i dem, og hvis de har bogstaver i dem, starter de med et". Hvis du opretter et regulært udtryk, der er baseret på sådanne kriterier, bør du kunne minimere unødvendige matches, samtidig med at du registrerer alle de ønskede værdier, og yderligere analyser kan give øget præcision ved at definere separate mønstre, der beskriver forskellige formater.

## <a name="create-a-rule-package-manually"></a>Opret en regelpakke manuelt

I denne procedure kan du se, hvordan du opretter en fil i XML-format, der kaldes en regelpakke (med Unicode-kodning), og derefter uploader den til Microsoft Purview ved hjælp af Security & Compliance PowerShell-cmdlet'er.

> [!NOTE]
> Hvis det SIT, du tilknytter til, kan registrere bekræftende beviser med flere ord, kan de sekundære elementer, du definerer i en manuelt oprettet regelpakke, knyttes til SIT. Navnet `John Smith` ville f.eks. ikke matche som et sekundært element, fordi vi ville sammenligne `John` og `Smith` finde det i indholdet separat med det ord `John Smith` , der blev uploadet i et af felterne, hvis dette bekræftelsesfelt ikke var knyttet til et SIT, der kan registrere mønsteret.
>
> Der er en grænse på 10 regelpakker i en Microsoft 365-lejer. Da en regelpakke kan indeholde et vilkårligt antal følsomme oplysningstyper, kan du undgå at oprette en ny regelpakke, hver gang du vil definere en ny type følsomme oplysninger ved hjælp af denne metode. Eksportér i stedet en eksisterende regelpakke, og føj dine følsomme oplysningstyper til XML'en, før du overfører den igen.

1. Opret en regelpakke i XML-format (med Unicode-kodning) i stil med følgende eksempel. Du kan kopiere, redigere og bruge vores eksempel.

   Når du konfigurerer regelpakken, skal du sørge for at referere korrekt til den .csv, .tsv eller pipefil (|) afgrænset tabelfil til følsomme oplysninger og **edm.xml** skemafil. Du kan kopiere, redigere og bruge vores eksempel. I dette xml-eksempel skal følgende felter tilpasses for at oprette den følsomme EDM-type:

   - **RulePack-id & ExactMatch-id**: Brug [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) til at generere et GUID.

   - **Datastore**: Dette felt angiver det EDM-opslagsdatalager, der skal bruges. Du angiver datakildenavnet på det konfigurerede EDM-skema.

   - **idMatch**: Dette felt peger på det primære element for EDM.
   - **Matches**: Angiver det felt, der skal bruges i nøjagtigt opslag. Du angiver et feltnavn, der kan søges i, i EDM-skemaet for DataStore.
   - **Klassificering**: Dette felt angiver, hvilken type følsomme oplysninger der udløser EDM-opslag. Du kan bruge navnet eller GUID'et for en eksisterende indbygget eller brugerdefineret type følsomme oplysninger.

   > [!NOTE]
   > Vær opmærksom på, at alle strenge, der svarer til det angivne SIT, hashkodes og sammenlignes med alle indtastninger i tabellen med følsomme oplysninger. Hvis du vil undgå problemer med ydeevnen, hvis du vælger et brugerdefineret SIT til klassificeringselementet, skal du ikke bruge et, der svarer til en stor procentdel af indholdet. For eksempel et, der svarer til "et vilkårligt tal" eller "et hvilket som helst ord på fem bogstaver". Du kan differentiere den ved at tilføje supplerende nøgleord eller inkludere formatering i definitionen af den brugerdefinerede klassificering SIT.

   - **Match**: Dette felt peger på yderligere beviser, der blev fundet i nærheden af idMatch.
   - **Matches**: Du angiver et vilkårligt feltnavn i EDM-skemaet for DataStore.
   - **Ressource-idRef:** I dette afsnit angives navnet og beskrivelsen for følsomme typer i flere landestandarder
     - Du angiver GUID for ExactMatch-id.
     - **Navn** &  **description**: tilpas efter behov.

      ```xml
      <RulePackage xmlns="http://schemas.microsoft.com/office/2018/edm">
        <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b11">
          <Version build="0" major="2" minor="0" revision="0" />
          <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
          <Details defaultLangCode="en-us">
            <LocalizedDetails langcode="en-us">
              <PublisherName>IP DLP</PublisherName>
              <Name>Health Care EDM Rulepack</Name>
              <Description>This rule package contains the EDM sensitive type for health care sensitive types.</Description>
            </LocalizedDetails>
          </Details>
        </RulePack>
        <Rules>
          <ExactMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB371" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
            <Pattern confidenceLevel="65">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
            </Pattern>
            <Pattern confidenceLevel="75">
              <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
              <Any minMatches ="3" maxMatches ="6">
                <match matches="PatientID" />
                <match matches="MRN"/>
                <match matches="FirstName"/>
                <match matches="LastName"/>
                <match matches="Phone"/>
                <match matches="DOB"/>
              </Any>
            </Pattern>
          </ExactMatch>
          <LocalizedStrings>
            <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB371">
              <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
              <Description default="true" langcode="en-us">EDM Sensitive type for detecting Patient SSN.</Description>
            </Resource>
          </LocalizedStrings>
        </Rules>
      </RulePackage>
      ```

2. Upload regelpakken ved at køre følgende PowerShell-kommando:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('.\\rulepack.xml'))
   ```

> [!NOTE]
> Syntaksen i regelpakkefilen er den samme som for andre følsomme oplysningstyper. [Opret en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell) for at få detaljerede oplysninger om syntaksen i regelpakkefilen og for yderligere konfigurationsindstillinger og for instruktioner om ændring og sletning af følsomme oplysningstyper ved hjælp af PowerShell.

## <a name="next-step"></a>Næste trin

- [Test et nøjagtigt datamatch for typen af følsomme oplysninger](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
