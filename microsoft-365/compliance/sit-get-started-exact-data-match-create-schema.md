---
title: Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger
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
description: Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9eb4e69aa833e8a355115115e1c965e57d65716c
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435275"
---
# <a name="create-the-schema-for-exact-data-match-based-sensitive-information-types"></a>Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan oprette skemaet og EDM SIT ved hjælp af [guiden Brug det nøjagtige datamatreringsskema og mønsteret for følsomme oplysninger eller](#use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard) [manuelt](#create-exact-data-match-schema-manually-and-upload). Du kan også kombinere begge ved hjælp af én metode til at oprette skemaet og senere redigere det ved hjælp af den anden metode.

Hvis du ikke er bekendt med EDM-baseret SITS eller deres implementering, skal du gøre dig bekendt med:

- [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)

Et enkelt EDM-skema kan bruges i flere følsomme informationstyper, der bruger den samme følsomme datatabel. Du kan oprette op til 10 forskellige EDM-skemaer i en Microsoft 365 lejer.



## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Brug guiden Nøjagtigt datamatchskema og følsomme oplysninger

Du kan bruge denne guide til at forenkle processen til oprettelse af skemafiler.

## <a name="pre-requisites"></a>Forudsætninger

- Udfør trinnene i [Eksportér kildedata for nøjagtigt datamatch baseret på følsomme oplysninger.](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Brug guiden Med det nøjagtige datamatchskema og mønsteret for følsomme oplysninger

1. I Microsoft Purview-compliance-portal for din lejer skal du gå til **DataklassificeringEksportér** >  **data, der stemmer overens** **medEDM-skemaer** > .

2. Vælg **Opret EDM-skema** for at åbne konfigurationsvinduet til skemaguiden.

   ![Konfigurations-pop op-vindue til guiden til oprettelse af EDM-skema.](../media/edm-schema-wizard-1.png)

3. Udfyld et passende **navn** **og en** beskrivelse.

4. Vælg **Ignorer afgrænsere og tegnsætning for alle skemafelter** , hvis du vil have denne funktionsmåde for hele skemaet. Hvis du vil vide mere om konfiguration af EDM til at ignorere store og små bogstaver eller afgrænsere, skal du se [Brug af felterne caseInsensitive og ignoredDelimiters](#using-the-caseinsensitive-and-ignoreddelimiters-fields) for at få flere oplysninger om denne funktion.

5. Udfyld de ønskede værdier for **skemafeltet #1,** og tilføj flere felter efter behov. Hvert skemafelt skal være identisk med kolonneoverskrifterne i din følsomme informationskildefil.

6. Hvis du vil, skal du angive værdierne pr. felt for:
    1. **Der kan søges i feltet**
    1. **Der skelnes mellem store og små bogstaver i feltet**
    1. **Vælg afgrænsere og tegnsætning, der skal ignoreres for dette felt**
    1. **Angiv brugerdefinerede afgrænsere og tegnsætning for dette felt**

   > [!IMPORTANT]
   > Mindst ét, men ikke mere end fem af skemafelterne skal være angivet som søgbare.

7. Vælg **Gem**. Skemaet vises nu og kan bruges.

   > [!IMPORTANT]
   > Hvis du vil fjerne et skema, og det allerede er knyttet til en EDM-følsom infotype, skal du først slette typen af følsomme EDM-oplysninger, så kan du slette skemaet. Hvis du sletter et skema, der har et tilknyttet datalager, slettes datalageret også inden for 24 timer.

## <a name="export-of-the-edm-schema-file-in-xml-format"></a>Eksport af EDM-skemafilen i XML-format

Hvis du har oprettet EDM-skemaet i guiden EDM-skema, skal du eksportere EDM-skemafilen i XML-format. Du skal bruge den i fasen [Hash og uploade den følsomme informationskildetabel for at finde præcise data, der matcher følsomme informationstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) .

1. [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

2. Hvis du vil eksportere EDM-skemafilen, skal du bruge denne syntaks:

   ```powershell
   $Schema = Get-DlpEdmSchema -Identity "[your EDM Schema name]"
   Set-Content -Path ".\Schemafile.xml" -Value $Schema.EdmSchemaXML
   ```

3. Gem filen til senere brug.

## <a name="create-exact-data-match-schema-manually-and-upload"></a>Opret skemaet for nøjagtigt datamatch manuelt, og upload

Konfigurer en post for hver kolonne i tabellen med følsomme oplysninger i skemafilen ved hjælp af syntaksen:

```xml
<Field name="FieldName" searchable="true/false" caseInsensitive="true/false" ignoredDelimiters="delimiter characters" />
```

### <a name="using-the-caseinsensitive-and-ignoreddelimiters-fields"></a>Brug felterne caseInsensitive og ignoredDelimiters

I følgende XML-skemaeksempel bruges felterne *caseInsensitive* og *ignoredDelimiters* .

Når du medtager feltet forskel på store og *små bogstaver* , der er angivet til værdien af `true` i skemadefinitionen, udelader EDM ikke et element baseret på forskel i store og små bogstaver. EDM kan f.eks. se, at værdierne **FOO-1234** og **fOo-1234** er identiske for feltet `PatientID` .

Når du medtager feltet *ignoredDelimiters* med understøttede tegn, ignorerer EDM disse tegn. Derfor kan EDM se, at værdierne **FOO-1234** og **FOO#1234** er identiske for feltet `PatienID` .

I dette eksempel, hvor både `caseInsensitive` og `ignoredDelimiters` bruges, vil EDM se **FOO-1234** og **fOo#1234** som identiske og klassificere elementet som en type følsomme oplysninger for patientpost.

Begge disse parametre bruges pr. felt.

> [!IMPORTANT]
> Hvis du konfigurerer *mellemrum* , der skal ignoreres, vil det kun være effektivt for primære feltkolonner, og for hvilke der er defineret en følsom oplysningstype, der kan registrere strenge med flere ord. Ellers foretages sammenligningen med hvert enkelt ord i det indhold, der analyseres.

Flaget *ignoredDelimiters* understøtter alle tegn, der ikke er alfanumeriske. Her er nogle eksempler:

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
- A-Å
- a-z
- \"
- \,

> [!IMPORTANT]
> Når du definerer typen af følsomme EDM-oplysninger, påvirker *ignoreDelimiters* ikke, hvordan den følsomme klassificeringstype, der er knyttet til det primære element i et EDM-mønster, identificerer indholdet i et element. Så hvis du konfigurerer *ignoreDelimiters* for et felt, der kan søges i, skal du sikre dig, at den følsomme oplysningstype, der bruges til et primært element, der er baseret på dette felt, vælger strenge både med og uden disse tegn.
>
> Antallet af kolonner i tabellen med følsomme oplysninger og antallet af felter i skemaet skal stemme overens. Det er lige meget, om rækkefølgen er angivet.

1. Definer skemaet i XML-format (svarer til vores eksempel nedenfor). Navngiv denne skemafil **edm.xml**, og konfigurer den, så der for hver kolonne i tabellen med følsomme oplysninger er en linje, der bruger syntaksen:

      `\<Field name="" searchable=""/\>`.

      - Brug kolonnenavne til *feltnavneværdier* .
      - Brug *searchable="true"* for de felter, der skal kunne søges i, og primære felter op til maksimalt 5 felter. Der skal kunne søges i mindst ét felt.

      Følgende XML-fil definerer f.eks. skemaet for en database med patientposter med fem felter, der er angivet som søgbare: *PatientID*, *MRN*, *SSN*, *Telefon* og *DOB*.

      Du kan kopiere, redigere og bruge vores eksempel.

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

   Når du har oprettet EDM-skemafilen i XML-format, skal du uploade den til cloudtjenesten.

2. [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

3. Kør følgende kommando for at uploade databaseskemaet:

      ```powershell
      New-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Du bliver bedt om at bekræfte følgende:

      > Bekræfte
      >
      > Er du sikker på, at du vil udføre denne handling?
      >
      > Der importeres et nyt EDM-skema til datalageret 'patientrecords'.
      >
      > \[Y Ja et ja til alle \[N\] Nej \[L\] Nej til alle\[?\]\] \[\] Hjælp (standard er "Y"):

   > [!TIP]
   > Hvis dine ændringer skal ske uden bekræftelse, skal du ikke bruge `-Confirm:$true` i trin 3.

> [!NOTE]
> Det kan tage mellem 10-60 minutter at opdatere EDMSchema med tilføjelser. Opdateringen skal fuldføres, før du udfører trin, der bruger tilføjelserne.

## <a name="next-step"></a>Næste trin

- [Hash og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der stemmer overens med typer af følsomme oplysninger](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)
