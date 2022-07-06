---
title: Hash og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der stemmer overens med typer af følsomme oplysninger
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
description: Hash og upload tabellen med følsomme oplysninger for at få præcise data til at matche følsomme oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd484f10cf8dad76132ed2a68a34f87b253e76b3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641290"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Hash og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der stemmer overens med typer af følsomme oplysninger

I denne artikel kan du se, hvordan du hashkode og uploader din tabel med følsomme oplysninger.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Hash og upload den følsomme informationskildetabel

I denne fase skal du:

1. konfigurer en brugerdefineret sikkerhedsgruppe og en brugerkonto
2. konfigurer værktøjet EDM Upload Agent
3. Brug værktøjet EDM Upload Agent til at hashkode den følsomme informationskildetabel med en saltværdi og uploade den.

Hash- og uploadhandlingen kan udføres ved hjælp af én computer, eller du kan adskille hashtrinnet fra overførselstrinnet for større sikkerhed.

Hvis du vil hashen og uploade fra én computer, skal du gøre det fra en computer, der kan oprette direkte forbindelse til din Microsoft 365-lejer. Dette kræver, at filen med datakildetabellen til følsomme oplysninger i klartekst findes på computeren til hashen.

Hvis du ikke vil vise din fil med en klartekstfølsom datakilde på computeren med direkte adgang, kan du hashkode den på en computer, der er på en sikker placering, og derefter kopiere hashfilen og saltfilen til en computer, der kan oprette direkte forbindelse til din Microsoft 365-lejer til upload. I det adskilte hash- og uploadscenarie skal du bruge EDMUploadAgent på begge computere.

> [!IMPORTANT]
> Hvis du har brugt guiden Nøjagtigt datamatch-skema og følsomme oplysninger til at oprette skemafilen, ***skal*** du hente skemaet til denne procedure, hvis du ikke allerede har gjort det. Se [Eksport af EDM-skemafilen i XML-format](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Hvis din organisation har konfigureret [kundenøgle til Microsoft 365 på lejerniveau](customer-key-overview.md), bruger Nøjagtigt datamatch automatisk krypteringsfunktionen. Dette er kun tilgængeligt for E5-licenserede lejere i Commercial-cloudmiljøet.

### <a name="best-practices"></a>Anbefalede fremgangsmåder

Adskil processerne for hashing og upload af følsomme data, så du nemmere kan isolere eventuelle problemer i processen.

Når du er i produktion, skal du i de fleste tilfælde holde de to trin adskilt. Udførelse af hashprocessen på en isoleret computer og derefter overføre filen til upload til en computer med adgang til internettet sikrer, at de faktiske data aldrig er tilgængelige i klartekstform på en computer, der kunne være blevet kompromitteret på grund af forbindelsen til internettet.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Sørg for, at der ikke er problemer med formateringen i din følsomme datatabel

Før du hashoverfør og uploader dine følsomme data, skal du foretage en søgning for at validere tilstedeværelsen af specialtegn, der kan medføre problemer med fortolkning af indholdet.
Du kan validere, at tabellen er i et format, der er egnet til brug med EDM, ved hjælp af EDM-uploadagenten med følgende syntaks:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]
```

Hvis værktøjet angiver en uoverensstemmelse i antallet af kolonner, kan det skyldes tilstedeværelsen af kommaer eller anførselstegn i værdier i tabellen, som forveksles med kolonneafgrænsere. Medmindre de omgiver en hel værdi, kan enkelte og dobbelte anførselstegn medføre, at værktøjet angiver forkert, hvor en enkelt kolonne starter eller slutter.

**Hvis du finder enkelte eller dobbelte anførselstegn omkring hele værdier**: Du kan lade dem være, som de er.

**Hvis du finder enkelte anførselstegn eller kommaer i en værdi**, f.eks. personens navn Tom O'Neil eller byen 's-Gravenhage, der starter med et apostrof-tegn, skal du ændre den dataeksportproces, der bruges til at generere den følsomme informationstabel, der omgiver sådanne kolonner med dobbelte anførselstegn.

**Hvis der findes dobbelte anførselstegn i værdier**, kan det være en fordel at bruge det tabulatorseparerede format for tabellen, som er mindre modtagelig for sådanne problemer.

### <a name="prerequisites"></a>Forudsætninger

- en arbejds- eller skolekonto til Microsoft 365, der føjes til sikkerhedsgruppen **EDM\_DataUploaders**
- en Windows 10- eller Windows Server 2016-computer med .NET version 4.6.2 <!--4.7.2 un comment this around 9/29-->til kørsel af EDMUploadAgent
- en mappe på overførselscomputeren til:
  - [EDM-uploadagent](#links-to-edm-upload-agent-by-subscription-type)
  - din fil med følsomme elementer i .csv-, .tsv- eller pipeformat (|), **PatientRecords.csv** i vores eksempler
  - outputhash- og saltfiler, der er oprettet i denne procedure
  - datalagernavnet fra **denedm.xml** fil, f.eks. `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Konfigurer sikkerhedsgruppen og brugerkontoen

1. Som global administrator skal du gå til Administration ved hjælp af det relevante [link til dit abonnement](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) og [oprette en sikkerhedsgruppe](/office365/admin/email/create-edit-or-delete-a-security-group) med navnet **EDM\_DataUploaders**.

2. Føj en eller flere brugere til sikkerhedsgruppen **EDM\_DataUploaders** . Disse brugere administrerer databasen med følsomme oplysninger.

### <a name="hash-and-upload-from-one-computer"></a>Hash og upload fra én computer

Denne computer skal have direkte adgang til din Microsoft 365-lejer.

> [!NOTE]
> Før du begynder på denne procedure, skal du sørge for, at du er medlem af sikkerhedsgruppen **EDM\_DataUploaders** .

> [!TIP]
>Du kan eventuelt køre en validering mod din følsomme datakildetabelfil for at kontrollere, om der er fejl i den, før du overfører den, ved at køre:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Du kan få flere oplysninger om alle de EdmUploadAgent.exe understøttede parametre, der køres
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Links til EDM-uploadagent efter abonnementstype

- [Commercial + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) – de fleste kommercielle kunder skal bruge dette
- [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) – Dette er specielt beregnet til cloudabonnenter med høj sikkerhed for offentlige myndigheder
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) – dette er specifikt til USA cloudkunder i forsvarsministeriet

1. Opret en arbejdsmappe til EDMUploadAgent. F.eks. **C:\EDM\Data**. Placer **denPatientRecords.csv** fil der.

2. Download og installér den relevante [EDM-uploadagent](#links-to-edm-upload-agent-by-subscription-type) for dit abonnement i den mappe, du oprettede i trin 1.

   > [!NOTE]
   > EDMUploadAgent på ovenstående links er blevet opdateret for automatisk at føje en saltværdi til hashkodedataene. Alternativt kan du angive din egen saltværdi. Når du har brugt denne version, kan du ikke bruge den tidligere version af EDMUploadAgent.
   >
   > Du kan kun uploade data med EDMUploadAgent til et givent datalager to gange om dagen.

3. Godkend EDM-uploadagenten, åbn vinduet Kommandoprompt som administrator, skift til mappen **C:\EDM\Data** , og kør derefter følgende kommando:

   `EdmUploadAgent.exe /Authorize`

   > [!IMPORTANT]
   > Du skal køre **EdmUploadAgent** fra den mappe, hvor den er installeret, og angive den fulde sti til dine datafiler.

4. Log på med din arbejds- eller skolekonto til Microsoft 365, der blev føjet til sikkerhedsgruppen EDM_DataUploaders. Dine lejeroplysninger udtrækkes fra brugerkontoen for at oprette forbindelse.

   VALGFRIT: Hvis du har brugt guiden Nøjagtigt datamatch-skema og følsomme oplysninger til at oprette skemaet, ***skal*** du hente det til brug i disse procedurer, hvis du ikke allerede har brugt det. Kør denne kommando i et kommandopromptvindue:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Hvis du vil hashene og overføre de følsomme data, skal du køre følgende kommando i kommandopromptvinduet:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```

   > [!NOTE]
   > Standardformatet for den følsomme datafil er kommaseparerede værdier. Du kan angive en fanesepareret fil ved at angive indstillingen "{Tab}" med parameteren /ColumnSeparator, eller du kan angive en pipesepareret fil ved at angive indstillingen "|".
   >
   > Eksempel: `EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5`

   Hvis tabellen med følsomme oplysninger har nogle forkert formaterede værdier, men du vil importere de resterende data, samtidig med at du alligevel ignorerer ugyldige rækker, kan du bruge parameteren */AllowedBadLinesPercentage* i kommandoen. Ovenstående eksempel angiver en grænse på fem procent. Det betyder, at værktøjet hashen og uploader tabellen med følsomme oplysninger, selvom op til fem procent af rækkerne er ugyldige.

   Denne kommando føjer automatisk en tilfældigt genereret saltværdi til hashen for større sikkerhed. Hvis du vil bruge din egen saltværdi, kan du eventuelt tilføje **/Salt \<saltvalue\>** til kommandoen . Denne værdi skal være 64 tegn lang og må kun indeholde a-z-tegn og 0-9 tegn.

6. Kontrollér overførselsstatussen ved at køre denne kommando:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Eksempel: `EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords`

   Se, om status er i **ProcessingInProgress**. Kontrollér igen hvert par minutter, indtil status ændres til **Fuldført**. Når status er fuldført, er dine EDM-data klar til brug. Afhængigt af størrelsen på din følsomme datakildetabelfil kan det tage fra et par minutter til flere timer.

> [!TIP]
> Hvis du vil have besked, når de overførte følsomme data er klar til brug, skal du følge procedurerne i [Opret meddelelser for aktiviteter, der matcher præcise data](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Adskil hash og upload

Udfør hashen på en computer i et sikkert miljø. **EDMUploadAgent** skal være installeret på begge computere.

VALGFRIT: Hvis du har brugt guiden Nøjagtigt datamatch-skema og følsomme oplysninger til at oprette skemaet, og du ikke allerede har hentet det, skal du køre følgende kommando i et kommandopromptvindue for at hente filen i XML-format:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. Kør følgende kommando i kommandopromptvinduer på computeren i det sikre miljø:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Eksempel:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

   > [!NOTE]
   > Standardformatet for den følsomme datafil er kommaseparerede værdier. Du kan angive en fanesepareret fil ved at angive indstillingen "{Tab}" med parameteren /ColumnSeparator, eller du kan angive en pipesepareret fil ved at angive indstillingen "|".

   Dette vil sende en hashkodet fil og en saltfil med disse filtypenavne, hvis du ikke har angivet indstillingen **/Salt \<saltvalue\>** :

   - . EdmHash
   - . EdmSalt

2. Kopiér disse filer på en sikker måde til den computer, du vil bruge til at uploade din følsomme kildetabelfil (PatientRecords) til din lejer.

3. Godkend EDM-uploadagenten, åbn vinduet Kommandoprompt som administrator, skift til mappen **C:\EDM\Data** , og kør derefter følgende kommando:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

   > [!IMPORTANT]
   > Du skal køre **EdmUploadAgent** fra den mappe, hvor den er installeret, og angive den fulde sti til dine datafiler.

4. Log på med din arbejds- eller skolekonto til Microsoft 365, der blev føjet til sikkerhedsgruppen EDM_DataUploaders. Dine lejeroplysninger udtrækkes fra brugerkontoen for at oprette forbindelse.

5. Hvis du vil overføre de hashkodede data, skal du køre følgende kommando i Windows-kommandoprompten:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Eksempel:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Hvis du vil kontrollere, at dine følsomme data er blevet overført, skal du køre følgende kommando i kommandopromptvinduet:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```

   Du får vist en liste over datalagre, og hvornår de sidst blev opdateret.

7. Hvis du vil se alle dataoverførsler til et bestemt lager, skal du køre følgende kommando i en Windows-kommandoprompt for at få vist en liste over alle datalagrene, og hvornår de blev opdateret:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```

> [!NOTE]
> Hvis du vil automatisere hash- og uploadprocessen, når du har oprettet den første gang, skal du se [Opdater den nøjagtige datamatch af tabellen med følsomme oplysninger](sit-use-exact-data-refresh-data.md).

## <a name="next-step"></a>Næste trin

- [Opret nøjagtigt datamatch for typer/regelpakker af følsomme oplysninger](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)
