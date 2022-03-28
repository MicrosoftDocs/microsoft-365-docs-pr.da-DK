---
title: Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper
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
description: Hashtag og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d3effe3d46375ffcaec268e4b3fc6d53fc5044e
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596944"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper

I denne artikel kan du se, hvordan du hashhenter og overfører kildetabellen med følsomme oplysninger.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Hashtag og upload kildetabellen med følsomme oplysninger

I denne fase kan du:

1. konfigurere en brugerdefineret sikkerhedsgruppe og brugerkonto
2. konfigurer værktøjet EDM Upload Agent
3. Brug værktøjet EDM Upload agent til at hashe med en saltværdi, kildetabellen med følsomme oplysninger og uploade den.

Hashing og overførsel kan udføres på én computer, eller du kan adskille hashingstrinnet fra overførselstrinnet for at opnå større sikkerhed.

Hvis du vil hash hash hashe og overføre fra én computer, skal du gøre det fra en computer, der kan oprette direkte forbindelse til din Microsoft 365 lejer. Dette kræver, at din kildetabelfil med følsomme oplysninger om klar tekst findes på computeren som hashing.

Hvis du ikke vil blotlægge din kildetabelfil med følsomme oplysninger om klar tekst på computeren med direkte adgang, kan du hash hashe den på en computer, der er på et sikkert sted, og derefter kopiere hash-filen og saltfilen til en computer, der kan oprette direkte forbindelse til din Microsoft 365-lejer til overførsel. I det separerede hash- og uploadscenarie skal du bruge EDMUploadAgent på begge computere.

> [!IMPORTANT]
> Hvis du har brugt guiden Nøjagtig datamatching og guiden Til følsomme oplysninger til at oprette din skemafil, skal du hente skemaet for denne procedure, hvis du ikke allerede har gjort det. Se [Eksportér EDM-skemafilen i XML-format](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Hvis din organisation har konfigureret [kundenøgle til Microsoft 365 på lejerniveau](customer-key-overview.md), gør nøjagtigt dataoverensstemmelse automatisk brug af dens krypteringsfunktionalitet. Dette er kun tilgængeligt for E5-licenserede lejere i den kommercielle sky.

### <a name="best-practices"></a>Anbefalede fremgangsmåder

Adskil processerne for hashing og upload af følsomme data, så du nemmere kan isolere eventuelle problemer i processen.
 
Når de er i produktion, skal du holde de to trin adskilt i de fleste tilfælde. Når du udfører hashingsprocessen på en isoleret computer og derefter overfører filen til overførsel til en computer, der er vendt mod internettet, sikrer du, at de faktiske data aldrig er tilgængelige i klar tekst-form på en computer, der kunne være blevet kompromitteret på grund af dens forbindelse til internettet.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Sørg for, at din følsomme datatabel ikke har formateringsproblemer. 

Før du hashbehandler og uploader dine følsomme data, skal du udføre en søgning for at validere tilstedeværelsen af specialtegn, der kan medføre problemer med fortolkning af indholdet. Du kan validere, om tabellen er i et format, der er egnet til brug med EDM, ved hjælp af EDM-overførselsagenten med følgende syntaks:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file] 
```

Hvis værktøjet angiver en uoverensstemmelse i antal kolonner, kan det skyldes forekomsten af kommaer eller anførselstegn i værdier i tabellen, som forveksles med kolonneafgrænsere. Medmindre de omgiver en hel værdi, kan enkelte og dobbelte anførselstegn få værktøjet til at fejlidentificere, hvor en enkelt kolonne starter eller slutter. 

**Hvis du finder enkelte eller dobbelte anførselstegn omkring fulde værdier**: du kan lade dem være, som de er.

Hvis du finder enkelt anførselstegn eller kommaer inde i en **værdi:** f.eks. personens navn Tom O'øg eller byen 's-Gravenhage, som starter med et apostroftegn, skal du ændre processen for dataeksporten, der bruges til at generere tabellen med følsomme oplysninger, så disse kolonner omgives af dobbelte anførselstegn.

**Hvis der findes dobbelte anførselstegn** i værdier, kan det være at foretrække at bruge tabulatorsepareret format for tabellen, som er mindre udsat for sådanne problemer.

### <a name="prerequisites"></a>Forudsætninger

- en arbejds- eller skolekonto Microsoft 365, der føjes til **sikkerhedsgruppen EDMDataUploaders\_**
- en Windows 10 eller Windows Server 2016-computer med .NET version 4.6.2 <!--4.7.2 un comment this around 9/29-->for at køre EDMUploadAgent
- en mappe på din uploadmaskine til:
  - [EDM Upload agent](#links-to-edm-upload-agent-by-subscription-type)
  - din følsomme fil i .csv.tsv- eller pipe-,|- ( **PatientRecords.csv** ) i vores eksempler
  - outputhash og saltfiler, der er oprettet i denne procedure
  - navnet på datastore fra den **edm.xml** fil, i dette eksempel dens `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Konfigurere sikkerhedsgruppen og brugerkontoen

1. Som global administrator skal du gå til Administration ved hjælp af det relevante [link til dit abonnement](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) og [](/office365/admin/email/create-edit-or-delete-a-security-group) oprette en sikkerhedsgruppe kaldet **EDMDataUploadere\_**.

2. Føj en eller flere brugere til **sikkerhedsgruppen EDMDataUploaders\_**. (Disse brugere administrerer databasen med følsomme oplysninger).

### <a name="hash-and-upload-from-one-computer"></a>Hash og upload fra én computer

Denne computer skal have direkte adgang til din Microsoft 365 lejer.

> [!NOTE]
> Før du starter denne procedure, skal du kontrollere, at du er medlem af **sikkerhedsgruppen EDMDataUploaders\_**.

> [!TIP] 
>Du kan også køre en validering i forhold til kildetabelfilen med følsomme oplysninger for at kontrollere, om der er fejl, før du uploader, ved at køre:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Du kan finde flere oplysninger om alle de EdmUploadAgent.exe understøttede parametre kører
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Links til EDM-uploadagent efter abonnementstype

- [Kommerciel + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - de fleste kommercielle kunder skal bruge dette
- [GCC-High –](https://go.microsoft.com/fwlink/?linkid=2137521) Dette er specifikt for skyabonn abonnenter på den offentlige højsikkerhed
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) – dette er specifikt for kunder fra det amerikanske forsvarsministerium i skyen

1. Opret en arbejdsmappe til EDMUploadAgent. F.eks **. C:\EDM\Data**. Placer **PatientRecords.csv** fil der.

2. Download og installér den [relevante EDM Upload agent](#links-to-edm-upload-agent-by-subscription-type) til dit abonnement i den mappe, du oprettede i trin 1.

   > [!NOTE]
   > EDMUploadAgenten ved ovenstående links er blevet opdateret til automatisk at føje en saltværdi til de gemte data. Alternativt kan du angive din egen saltværdi. Når du har brugt denne version, vil du ikke kunne bruge den tidligere version af EDMUploadAgent.
   >
   > Du kan kun uploade data med EDMUploadAgent til et givent datalager to gange pr. dag.

3. Godkend EDM Upload-agent, åbn kommandopromptvinduet som administrator, skift til **mappen C:\EDM\Data**, og kør derefter følgende kommando:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Du skal køre **EdmUploadAgent** fra den mappe, hvor den er installeret, og angive den fulde sti til dine datafiler. 

4. Log på med din arbejds- eller skolekonto for Microsoft 365, der blev føjet EDM_DataUploaders sikkerhedsgruppen. Dine lejeroplysninger udtrækkes fra brugerkontoen for at oprette forbindelsen.

   VALGFRIT: Hvis du har brugt guiden Nøjagtig dataoverensstemmelse og guiden til følsomme oplysninger til at oprette dit skema, skal du hente det til brug i disse procedurer, hvis du ikke allerede har gjort det. Kør denne kommando i et kommandopromptvindue:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Hvis du vil hashhash og overføre de følsomme data, skal du køre følgende kommando i vinduet Kommandoprompt:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```
   > [!NOTE]
> Standardformatet for den følsomme datafil er kommaseparerede værdier. Du kan angive en tabulatorsepareret fil ved at angive indstillingen "{Tab}" med parameteren /ColumnSeparator, eller du kan angive en pipe-separated fil ved at angive indstillingen "|".

   Eksempel: **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5**

Hvis tabellen med følsomme oplysninger har nogle forkert formaterede værdier, men du alligevel vil importere de resterende data, mens ugyldige rækker ignoreres, kan du bruge parameteren */AllowedBadLinesPercentage* i kommandoen. Eksemplet ovenfor angiver en grænseværdi på fem procent. Det betyder, at værktøjet hashtagker og overfører tabellen med følsomme oplysninger, selvom op til fem procent af rækkerne er ugyldige. 

Denne kommando føjer automatisk en tilfældigt genereret saltværdi til hash'en for at opnå større sikkerhed. Hvis du vil bruge din egen saltværdi, kan du føje **/Salt <saltvalue>** til kommandoen. Denne værdi skal være på 64 tegn og må kun indeholde a-z-tegn og 0-9 tegn.

6. Kontrollér overførselsstatussen ved at køre denne kommando:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Eksempel: **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   Se efter, om status er **i ProcessingInProgress**. Kontrollér igen med få minutter, indtil status ændres til **Fuldført**. Når status er fuldført, er dine EDM-data klar til brug. Afhængigt af størrelsen på kildetabelfilen med følsomme oplysninger kan det tage fra et par minutter til flere timer. 

> [!TIP]
> Hvis du vil have besked, når de overførte følsomme data er klar til brug, skal du følge procedurerne i [Oprette meddelelser for aktiviteter med nøjagtigt dataoverensstemmelse](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Separat hash og upload

Udføre hash-værdien på en computer i et sikkert miljø. Du skal have **EDMUploadAgent installeret** på begge computere.

VALGFRIT: Hvis du har brugt guiden Nøjagtig dataoverensstemmelse og guiden til følsomme oplysninger til at oprette dit skema, og du ikke allerede har hentet det, skal du køre følgende kommando i vinduet Kommandoprompt for at hente filen i XML-format:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. På computeren i det sikre miljø skal du køre følgende kommando i vinduer med kommandoprompt:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Eksempel:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

> [!NOTE]
> Standardformatet for den følsomme datafil er kommaseparerede værdier. Du kan angive en tabulatorsepareret fil ved at angive indstillingen "{Tab}" med parameteren /ColumnSeparator, eller du kan angive en pipe-separated fil ved at angive indstillingen "|".


   Dette vil få en hashed fil og en salt fil med disse filtypenavne, hvis du ikke har angivet **indstillingen /Salt <saltvalue>** :

   - . EdmHash
   - . EdmSalt


2. Kopiér disse filer på en sikker måde til den computer, du vil bruge til at uploade din kildetabelfil med følsomme oplysninger (PatientRecords) til din lejer.

3. Godkend EDM Upload-agent, åbn kommandopromptvinduet som administrator, skift til **mappen C:\EDM\Data**, og kør derefter følgende kommando:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> Du skal køre **EdmUploadAgent** fra den mappe, hvor den er installeret, og angive den fulde sti til dine datafiler. 

4. Log på med din arbejds- eller skolekonto for Microsoft 365, der blev føjet EDM_DataUploaders sikkerhedsgruppen. Dine lejeroplysninger udtrækkes fra brugerkontoen for at oprette forbindelsen.

5. For at overføre de gemte data skal du køre følgende kommando i Windows Kommandoprompt:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Eksempel:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Kør følgende kommando i vinduet Kommandoprompt for at bekræfte, at dine følsomme data er blevet overført:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```
   Du får vist en liste over datalagre, og hvornår de sidst blev opdateret.

7. Hvis du vil se alle dataoverførsler til et bestemt lager, skal du køre følgende kommando i en Windows-kommandoprompt for at få vist en liste over alle datalagrene, og hvornår de blev opdateret:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```
     
## <a name="next-step"></a>Næste trin

- [Oprette en nøjagtig dataoverensstemmelse mellem følsomme oplysningstype/regelpakke](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)

