---
title: Oprette en nøjagtig dataoverensstemmelse mellem følsomme oplysningstype/regelpakke
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
description: Oprette en nøjagtig dataoverensstemmelse mellem følsomme oplysningstype/regelpakke
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e44d18bc1a779ace95fb2f64171ff0bf91de57ed
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594673"
---
# <a name="create-exact-data-match-sensitive-information-typerule-package"></a>Oprette en nøjagtig dataoverensstemmelse mellem følsomme oplysningstype/regelpakke

Du kan oprette en nøjagtig data match (EDM) sensitive information type (SIT) ved hjælp af [EDM-skemaet og SIT-guiden](#use-the-edm-schema-and-sit-wizard) i Overholdelsescenter, eller du kan oprette XML-filen med regelpakken [manuelt](#create-a-rule-package-manually). Du kan også kombinere begge ved at bruge én metode til at oprette skemaet og senere redigere det ved hjælp af den anden metode.

Hvis du ikke kender til EDM-baseret SITS eller deres implementering, bør du gøre dig bekendt med:

- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

## <a name="use-the-edm-schema-and-sit-wizard"></a>Brug af EDM-skemaet og GUIDEN SIT

Du kan bruge denne guide til at oprette dine FILER (Sensitive Information Type) til at forenkle processen.

Typen Følsomme oplysninger i EDM består af et eller flere mønstre. Hvert mønster beskriver en kombination af beviser (felter fra skemaet), der skal bruges til at identificere følsomt indhold i et dokument eller en mail.

## <a name="pre-requisites"></a>Forudsætninger

Udfør trinnene i følgende artikler:

1. [Eksportér kildedata for en nøjagtig dataoverensstemmelsesbaseret type af følsomme oplysninger](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
2. [Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)
3. [Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)

- Uanset om du skal oprette en EDM-følsom oplysningstype ved hjælp af guiden eller XML-filen med regelpakken via PowerShell, skal du have tilladelsen Global administrator eller Overholdelsesadministrator for at oprette, teste og installere en brugerdefineret type af følsomme oplysninger via brugergrænsefladen. Se [Om administratorroller i Office 365](/office365/admin/add-users/about-admin-roles).
- Identificer en af de indbyggede SIT'er, der skal bruges som følsomme oplysningstype for primære elementer.
  - Hvis ingen af de indbyggede følsomme oplysningstyper stemmer overens med dataene i den kolonne, du har valgt, skal du oprette en brugerdefineret type af følsomme oplysninger, der gør.
  - Hvis du har valgt indstillingen Ignorerede afgrænsere for kolonnen med det primære element i dit skema, skal du sikre dig, at det brugerdefinerede SIT, du opretter, matcher dataene med og uden de valgte afgrænsere.
  - Hvis du bruger en indbygget SIT, skal du sikre dig, at den registrerer præcis de strenge, du vil markere, og ikke omfatter nogen omgivende tegn eller udelader nogen gyldig del af strengen som gemt i din tabel med følsomme oplysninger.

Se [Enhedsdefinitioner for typer af følsomme oplysninger](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) [og Opret brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter](create-a-custom-sensitive-information-type.md).

### <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Brug af skemaet for nøjagtigt datamatchingskema og guiden til typen af følsomme oplysninger

1. I overholdelsescenteret Microsoft 365 for din lejer skal du gå til **DataklassificeringOversæt** >  **dataoverensstemmelser**.

2. Vælg **EDM-følsomme oplysningstyper og** **Opret EDM-følsom oplysningstype** for at åbne konfigurationsguiden til følsomme oplysninger.

3. Vælg **Vælg et eksisterende EDM-skema,** og vælg det skema, du oprettede i Opret skemaet [for nøjagtige datamatchebaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

4. Vælg **Næste,** og vælg **Opret mønster**.

5. Vælg confidence **level og** **Primary-elementet**. Du kan få mere at vide om tillidsniveauer [under Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).

6. Vælg typen **Af følsom** information for det primære element for at knytte det til det for at definere, hvilken tekst i dokumentet der skal sammenlignes med alle værdierne i det primære elementfelt. Se [Enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md) for at få mere at vide om de tilgængelige typer af følsomme oplysninger.

   > [!IMPORTANT]
   > Vælg en type af følsomme oplysninger, der passer tæt til formatet af det indhold, du vil finde. Valg af en type af følsomme oplysninger, der matcher unødvendigt indhold, f.eks. en, der svarer til alle tekststrenge, eller alle tal kan medføre overdreven belastning i systemet, hvilket kan medføre, at følsomme oplysninger mistes. Se afsnittet Bedste fremgangsmåder i artiklen Introduktion til nøjagtig datasammenholdelse i denne dokumentation for at få anbefalinger til at vælge en type af følsomme oplysninger, der skal bruges her.

7. Vælg dine **Understøttende elementer,** og match indstillinger.

8. Vælg **Udført** og **Næste**.

9. Vælg det ønskede **Tillidsniveau og tegn afstand**. Dette er standardværdien for hele EDM-følsomme oplysningstyper.

10. Vælg **Opret mønster** , hvis du vil oprette flere mønstre til din følsomme oplysningstype i EDM.

11. Vælg **Næste** , og angiv **et Navn** **og en Beskrivelse til administratorer**.

12. Gennemse og vælg **Send**.

### <a name="edit-or-delete-the-sensitive-information-type-pattern"></a>Redigere eller slette et mønster af typen af følsomme oplysninger

1. Åbn **OverholdelsescenterDataklassificeringExact-dataoverensstemmelser** >  > .

2. Vælg **EDM-følsomme oplysningstyper**.

3. Vælg den EDM SIT, du vil redigere.

4. Vælg **Rediger EDM-følsom oplysningstype** **eller Slet EDM-følsom oplysningstype** i pop op-pop-op-pop-op-menuen.

## <a name="create-a-rule-package-manually"></a>Opret en regelpakke manuelt

Denne procedure viser, hvordan du opretter en fil i XML-format, der kaldes en regelpakke (med Unicode-kodning), og derefter overfører den til Microsoft 365 ved hjælp af Compliance Center PowerShell-cmdlet'er.

> [!NOTE]
> Hvis det SIT, som du tilknytter for at registrere bekræftende multiord, kan de sekundære elementer, du definerer i en manuelt oprettet regelpakke, knyttes til SIT. Navnet stemmer f.eks. ikke overens som et sekundært element `John` `Smith` `John Smith`, fordi vi ville sammenligne og findes i indholdet separat med det udtryk, `John Smith` der blev uploadet i et af felterne, hvis det bekræftende bevisfelt ikke var knyttet til et SIT, der kan registrere det pågældende mønster.
>
> Der er en grænse på 10 regelpakker i en Microsoft 365 lejer. Da en regelpakke kan indeholde et vilkårligt antal typer af følsomme oplysninger, kan du undgå at oprette en ny regelpakke, hver gang du vil definere en ny type af følsomme oplysninger ved hjælp af denne metode, i stedet eksportere en eksisterende regelpakke og føje dine typer af følsomme oplysninger til XML'en, før du overfører den igen.

1. Opret en regelpakke i XML-format (med Unicode-kodning) som i følgende eksempel. (Du kan kopiere, redigere og bruge vores eksempel.)

   Når du konfigurerer din regelpakke, skal du sørge for at henvise korrekt til din .csv-, .tsv- eller pipe-(|)-afgrænsede kildetabelfil med følsomme oplysninger **edm.xml** ogedm.xmlskemafil. Du kan kopiere, redigere og bruge vores eksempel. I dette eksempel på XML skal følgende felter tilpasses for at oprette din EDM-følsomme type:

   - **RulePack-id & ExactMatch-id**: Brug [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) til at oprette et GUID.

   - **Datastore**: Dette felt angiver, at et EDM-opslagsdatalager skal bruges. Du skal angive datakildenavnet for det konfigurerede EDM-skema.

   - **idMatch**: Dette felt peger på det primære element for EDM.
   - **Forekomster**: Angiver det felt, der skal bruges i nøjagtigt opslag. Du angiver et søgbart feltnavn i EDM-skema for DataStore.
   - **Klassificering**: Dette felt angiver matchet for typen af følsomme oplysninger, der udløser EDM-opslag. Du kan bruge navnet eller GUID for en eksisterende indbygget eller brugerdefineret følsom oplysningstype.

   > [!NOTE]
   > Vær opmærksom på, at alle strenge, der svarer til det angivne SIT, bliver hashet og sammenlignet med hver post i kildetabellen med følsomme oplysninger. For at undgå problemer med ydeevnen, hvis du vælger et brugerdefineret SIT som klassificeringselement, skal du ikke bruge et, der svarer til en stor procentdel af indholdet. For eksempel et ord, der svarer til "et vilkårligt tal" eller "et ord med fem bogstaver". Du kan skelne det fra hinanden ved at tilføje understøttende nøgleord eller medtage formatering i definitionen af den brugerdefinerede klassifikations-SIT.

   - **Match**: Dette felt peger på yderligere beviser, der er fundet i nærheden af idMatch.
   - **Forekomster**: Du angiver et hvilket som helst feltnavn i EDM-skema for DataStore.
   - **Ressource-idRef:** Denne sektion angiver navn og beskrivelse for følsom type i flere lande/områder
     - Du angiver GUID for ExactMatch-id.
     - **Navn** &  **beskrivelse**: tilpas efter behov.

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
> Syntaksen for regelpakkefilen er den samme som for andre typer af følsomme oplysninger. Du kan finde detaljerede oplysninger om syntaksen for regelpakkefilen og for yderligere konfigurationsindstillinger og for at få en vejledning i, hvordan du ændrer og sletter typer af følsomme oplysninger ved hjælp af PowerShell, ved at oprette en brugerdefineret type af følsomme oplysninger ved hjælp af [PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md#create-a-custom-sensitive-information-type-using-powershell).

## <a name="next-step"></a>Næste trin

- [Teste en nøjagtig datatype, der matcher følsomme oplysninger](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)
