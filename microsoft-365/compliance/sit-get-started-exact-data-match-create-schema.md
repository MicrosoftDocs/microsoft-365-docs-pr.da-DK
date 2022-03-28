---
title: Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper
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
description: Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6bd411411c3075259bd3b9fc74ec3f558171fce7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596945"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper

Du kan oprette skemaet og EDM SIT ved hjælp af guiden Brug det nøjagtige datamatchingskema og guiden til følsomme [oplysningstypemønster](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) eller [manuelt](#create-exact-data-match-schema-manually-and-upload). Du kan også kombinere begge ved at bruge én metode til at oprette skemaet og senere redigere det ved hjælp af den anden metode.

Hvis du ikke kender til EDM-baseret SITS eller deres implementering, bør du gøre dig bekendt med:

- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Et enkelt EDM-skema kan bruges i flere typer af følsomme oplysninger, der bruger den samme følsomme datatabel. Du kan oprette op til 10 forskellige EDM-skemaer i en Microsoft 365 lejer.

## <a name="working-with-specific-types-of-data"></a>Arbejde med bestemte datatyper

Af hensyn til ydeevnen er det vigtigt, at du bruger mønstre, der minimerer antallet af unødvendige forekomster. Du kan f.eks. bruge en type af følsomme oplysninger, der er baseret på det regulære udtryk.

`\b\w*\b`

Dette ville matche hvert enkelt ord eller tal i et dokument eller en mail. Dette ville medføre, at tjenesten blev overbelastet med matches, og at der ikke kunne registreres sande matches. Brug af mere præcise mønstre kan undgå denne situation. Her er nogle anbefalinger til at identificere den rigtige konfiguration for nogle almindelige typer data.

**Mailadresser**: Mailadresser kan være nemme at identificere, men fordi de er så almindelige i indhold, kan de medføre en betydelig belastning i systemet, hvis de bruges som et primært felt. Brug dem kun som sekundære beviser. Hvis de skal bruges som primære beviser, `From` `To` kan du prøve at definere en brugerdefineret type af følsomme oplysninger, der bruger logik til at udelukke brugen af disse som eller felter i mails og til at udelukke personer med firmaets mailadresse for at reducere antallet af unødvendige strenge, der skal matches.

**Telefon tal**: Telefon tal kan være i mange forskellige formater, herunder eller uden landepræfikser, områdekoder og separatorer. Hvis du vil reducere de falske negative og samtidig holde belastningen på et minimum, skal du kun bruge dem som sekundære elementer, udelukke alle sandsynlige separatorer, f.eks. parenteser og tankestreger og kun medtage den del i din følsomme datatabel, der altid vil være til stede i telefonnummeret.

**Personers** navne: Brug ikke personens navne som primære elementer, hvis du bruger en følsom oplysningstype, der er baseret på et regulært udtryk som klassificeringselementet for denne EDM-type, da det er svært at skelne fra almindelige ord.

Hvis du skal bruge et primært element, der er svært at identificere med et bestemt mønster, f.eks. et projektkodenavn, der kan generere mange forekomster, der skal behandles, skal du sørge for at medtage nøgleord i den type af følsomme oplysninger, du bruger som klassificeringselement for din EDM-type. Hvis du f.eks. bruger projektkodenavne, der kan være almindelige ord, `project` kan du bruge ordet som påkrævet yderligere beviser i nærheden af projektnavnets regulære udtryksbaserede mønster i den følsomme type, der bruges som klassificeringselementet for din EDM-type. Eller du kan overveje at bruge en følsom type, der er baseret på en almindelig ordbog, som klassificeringselementet til din EDM SIT.

Når du forsøger at matche numeriske strenge, skal du angive de tilladte talintervaller, f.eks. antallet af cifre eller startcifrene, hvis de kendes. Hvis du skal matche et relativt fleksibelt interval af tal, kan du bruge nøgleord i det grundlæggende SIT til at reducere antallet af resultater. Hvis du f.eks. forsøger at matche kontonumre bestående af 7-11 cifre, `account`skal du tilføje ordene , `customer``acct.` , til SIT som påkrævet yderligere bevis. Dette reducerer sandsynligheden for unødvendige matches, der kan medføre, at EDM overskrider grænsen for matches, der skal behandles af EDM.

Hvis et felt, du skal bruge som primært element, følger et simpelt mønster, der kan medføre et stort antal forekomster, og du ikke kan tilføje tilstedeværelsen af nøgleord som yderligere bevis i typen af følsomme oplysninger, kan du alternativt kræve et minimum antal forekomster af det pågældende mønster. Du kan f.eks. bruge en brugerdefineret type af følsomme oplysninger, der er defineret på følgende måde til at registrere mindst 29 andre femcifrede tal, der omgiver et potentielt femcifret tal, der skal matche med EDM:

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

I nogle tilfælde kan det være en god ide at identificere visse konto- eller postidentifikationsnumre, som af historiske årsager ikke følger et standardiseret mønster. Kan f.eks `Medical Record Numbers` . bestå af mange forskellige permutationer af bogstaver og tal inden for samme organisation. Selvom det kan være svært i starten at identificere et mønster, kan du ved nærmere kontrol ofte indskrænke et mønster, der beskriver alle gyldige værdier uden at forårsage et stort antal ugyldige match. Det kan f.eks. være, at "alle MN'er er mindst syv tegn lange, har mindst to numeriske cifre i sig, og hvis der er bogstaver i dem, starter de med et". Hvis du opretter et regulært udtryk, der er baseret på sådanne kriterier, bør det gøre det muligt at minimere unødvendige match, samtidig med at du tager alle de ønskede værdier med, og yderligere analyser kan give en bedre præcision ved at definere separate mønstre, der beskriver forskellige formater.

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Brug af skemaet for nøjagtig dataoverensstemmelse og guiden Type af følsomme oplysninger

Du kan bruge denne guide til at forenkle processen til oprettelse af skemafilen.

## <a name="pre-requisites"></a>Forudsætninger

- Udfør trinnene i Eksportér [kildedata for nøjagtig dataoverensstemmelse baseret på en følsom oplysningstype](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Brug af skemaet for nøjagtigt datamatchingskema og guiden til typen af følsomme oplysninger

1. I Microsoft 365 overholdelsescenter for din lejer skal du gå til **DataklassificeringExact-data** >  **svarer** **tilEDM-skemaer** > .

2. Vælg **Opret EDM-skema for** at åbne pop op-pop op-menuen til konfiguration af skemaguiden.

   ![Pop op-pop-op-fil med konfiguration af EDM-skemaoprettelse.](../media/edm-schema-wizard-1.png)

3. Udfyld et passende **Navn** og **Beskrivelse**.

4. Vælg **Ignorer afgrænsere og tegnsætning for alle skemafelter,** hvis du vil have denne funktionsmåde for hele skemaet. Hvis du vil have mere at vide om at konfigurere EDM til at ignorere store og små bogstaver eller [afgrænsere](#using-the-caseinsensitive-and-ignoreddelimiters-fields) , skal du se Brug af felterne store og små bogstaver og ignoreredeAfgrænsere for at få mere at vide om denne funktion.

5. Udfyld dine ønskede værdier for dit **skemafelt #1,** og tilføj flere felter efter behov. Hvert skemafelt skal være identisk med kolonneoverskrifterne i kildefilen med følsomme oplysninger.

6. Hvis du vil, kan du angive værdierne pr. felt for:
    1. **Feltet kan søges i**
    1. **Der kan ikke arbejdes med store og små bogstaver i feltet**
    1. **Vælg afgrænsere og tegnsætning, der skal ignoreres for dette felt**
    1. **Angive brugerdefinerede afgrænsere og tegnsætning for dette felt**

   > [!IMPORTANT]
   > Mindst ét, men ikke flere end fem af dine skemafelter skal angives som søgbare.

7. Vælg **Gem**. Dit skema er nu angivet og tilgængeligt til brug.

   > [!IMPORTANT]
   > Hvis du vil fjerne et skema, og det allerede er knyttet til en EDM-følsom oplysningstype, skal du først slette den følsomme EDM-infotype, og derefter kan du slette skemaet. Hvis du sletter et skema, der har et tilknyttet datalager, slettes datalageret også inden for 24 timer.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>Eksport af EDM-skemafilen i XML-format

Hvis du har oprettet EDM-skemaet i guiden EDM-skema, skal du eksportere EDM-skemafilen i XML-format. Du skal bruge den i [hashtagget og overføre kildetabellen for følsomme oplysninger for at finde fasen, hvor følsomme oplysningstyper stemmer nøjagtigt overens](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Brug denne syntaks til at eksportere EDM-skemafilen:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Gem denne fil til senere brug.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>Opret nøjagtigt skema for datamatching manuelt, og overfør

I skemafilen skal du konfigurere en post for hver kolonne i kildetabellen med følsomme oplysninger ved hjælp af syntaksen:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Brug af felterne caseInsensitive og ignoreredeAfgrænsere

I følgende skema gør XML-eksemplet brug af *felterne caseInsensitive* og *ignoreredeAfgrænsere* .

Når du medtager feltet *forskel* `true` på store og små bogstaver, der er angivet til værdien af i din skemadefinition, udelukker EDM ikke et element baseret på forskelle i mellem store og små bogstaver. EDM vil f.eks. se værdierne **FOO-1234** og **fOo-1234** som identiske for `PatientID` feltet.

Når du medtager *feltet ignorerede Afgrænsere* med understøttede tegn, ignorerer EDM disse tegn. Så EDM vil se værdierne **FOO-1234** og **FOO#1234 som** identiske for `PatienID` feltet.

I dette eksempel, `caseInsensitive` `ignoredDelimiters` hvor både og anvendes, ville EDM se **FOO-1234** og **fOo#1234** som identiske og klassificere elementet som en type af følsomme oplysninger for patientjournaler.

Begge disse parametre bruges på grundlag af de forskellige felter.

> [!IMPORTANT]
> Hvis du *konfigurerer mellemrum* til at blive ignoreret, vil dette kun være effektivt for primære feltkolonner, og for hvilke en følsom oplysningstype, der kan registrere flerordsstrenge, er defineret. Ellers foretages der en sammenligning af hvert enkelt ord i det indhold, der analyseres.

*Flaget ignoreredeAfgrænsere* understøtter alle ikke-alfanumeriske tegn, her er nogle eksempler:

- \.
- \-
- \/
- \_
- \*
- \^
- \#
- \!
- \?
- \[
- \]
- \{
- \}
- \\
- \~
- \;

Flaget `ignoredDelimiters` understøtter ikke:

- tegn 0-9
- A-Z
- a-z
- \"
- \,

> [!IMPORTANT]
> Når du definerer typen af følsomme oplysninger i EDM, påvirker *ignorerAfgrænsere* ikke, hvordan typen Klassificering af følsomme oplysninger, der er knyttet til det primære element i et EDM-mønster, identificerer indhold i et element. Så hvis du konfigurerer *ignorerAfgrænsere* for et søgbart felt, skal du sikre dig, at typen af følsomme oplysninger, der bruges til et primært element, der er baseret på det pågældende felt, vælger strenge både med og uden disse tegn.
>
> Antallet af kolonner i kildetabellen med følsomme oplysninger og antallet af felter i dit skema skal matche, rækkefølgen er ligegyldig.

1. Definer skemaet i XML-format (svarende til eksemplet nedenfor). Name this schema file **edm.xml**, and configure it such that for each column in the sensitive information source table, there is a line that uses the syntax:

      `\<Field name="" searchable=""/\>`.

      - Brug kolonnenavne til *feltnavneværdier* .
      - Brug *søgbare = "sand"* for de felter, der skal være søgbare og primære felter op til maksimalt 5 felter. Der skal kunne søges i mindst ét felt.

      Som eksempel definerer følgende XML-fil skemaet for en database over patientjournaler med fem felter, der er angivet som søgbare: *PatientID*, *MRN*, *SSN*, *Telefon* og *DOB*.

      (Du kan kopiere, redigere og bruge vores eksempel.)

      ```xml
      <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
            <DataStore name="PatientRecords" description="Schema for patient records" version="1">
                  <Field name="PatientID" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
                  <Field name="MRN" searchable="true" />
                  <Field name="FirstName" />
                  <Field name="LastName" />
                  <Field name="SSN" searchable="true" />
                  <Field name="Phone" searchable="true" />
                  <Field name="DOB" searchable="true" />
                  <Field name="Gender" />
                  <Field name="Address" />
            </DataStore>
      </EdmSchema>
      ```

   Når du har oprettet EDM-skemafilen i XML-format, skal du overføre den til skytjenesten.

2. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. For at overføre databaseskemaet skal du køre følgende kommando:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Du bliver bedt om at bekræfte på følgende måde:

      > Bekræft
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > Det nye EDM-skema for datalageret "patientposter" importeres.
      >
      > \[Y Ja A Ja til alle \[N\] Nej \[L\] nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

   > [!TIP]
   > Hvis du vil have dine ændringer til at ske uden bekræftelse, skal du ikke `-Confirm:$true` bruge i trin 3.

> [!NOTE]
> Det kan tage mellem 10-60 minutter at opdatere EDMSchema med tilføjelser. Opdateringen skal udføres, før du udfører trin, der bruger tilføjelserne.

## <a name="next-step"></a>Næste trin

- [Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)