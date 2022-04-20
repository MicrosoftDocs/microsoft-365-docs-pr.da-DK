---
title: Konfigurer en connector til import af HR-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: Administratorer kan konfigurere en dataconnector til at importere medarbejderdata fra organisationens HR-system for at Microsoft 365. Dette giver dig mulighed for at bruge HR-data i politikker for styring af insiderrisiko for at hjælpe dig med at registrere aktiviteter fra bestemte brugere, der kan udgøre en intern trussel for din organisation.
ms.openlocfilehash: e1539661c987de8642639df777602fbcf05bdcc4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944805"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>Konfigurer en connector til import af HR-data

Du kan konfigurere en dataconnector på Microsoft Purview-overholdelsesportalen for at importere HR-data (Human Resources), der er relateret til hændelser, f.eks. en brugers fratræden eller en ændring i en brugers jobniveau. HR-dataene kan derefter bruges af [insiderrisikostyringsløsningen](insider-risk-management.md) til at generere risikoindikatorer, der kan hjælpe dig med at identificere mulig ondsindet aktivitet eller datatyveri af brugere i din organisation.

Konfiguration af en connector til HR-data, som politikker for styring af insiderrisiko kan bruge til at generere risikoindikatorer, består i at oprette en CSV-fil, der indeholder HR-dataene, oprette en app i Azure Active Directory, der bruges til godkendelse, oprette en HR-dataconnector i overholdelsesportalen og derefter køre et script (efter en tidsplan), der overfører HR-dataene i CSV-filer til Microsoft-cloudmiljøet, så de er tilgængelige  til løsningen til styring af insiderrisiko.

> [!IMPORTANT]
> En ny version af HR-connectoren er nu tilgængelig til offentlig prøveversion. Hvis du vil oprette en ny HR-connector eller importere data til det [nye scenarie for medarbejderprofilen](#csv-file-for-employee-profile-data-preview) for scenariet for administration af insiderrisiko, skal du gå til siden **Dataconnectors på overholdelsesportalen** , vælge fanen **Forbindelser** og derefter klikke på **Tilføj en connector > HR (prøveversion)** for at starte opsætningen. Eksisterende HR-connectors fungerer fortsat uden afbrydelser.

## <a name="before-you-begin"></a>Før du begynder

- Find ud af, hvilke HR-scenarier og -data der skal importeres til Microsoft 365. Dette hjælper dig med at bestemme, hvor mange CSV-filer og HR-connectors du skal oprette, og hvordan du genererer og strukturerer CSV-filerne. De HR-data, du importerer, bestemmes af de politikker for styring af insiderrisiko, du vil implementere. Du kan få flere oplysninger under Trin 1.

- Bestem, hvordan du henter eller eksporterer dataene fra organisationens HR-system (og regelmæssigt), og føj dem til de CSV-filer, du opretter i trin 1. Det script, du kører i trin 4, uploader HR-dataene i CSV-filerne til Microsoft-cloudmiljøet.

- Den bruger, der opretter HR-connectoren i trin 3, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Det eksempelscript, du kører i trin 4, uploader dine HR-data til Microsoft-cloudmiljøet, så de kan bruges af løsningen til styring af insiderrisiko. Dette eksempelscript understøttes ikke under noget Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

- Denne connector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible. Du kan finde en trinvis vejledning til konfiguration af en HR-connector i et GCC miljø under [Konfigurer en connector til import af HR-data i US Government](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Trin 1: Forbered en CSV-fil med dine HR-data

Det første trin er at oprette en CSV-fil, der indeholder de HR-data, som connectoren importerer til Microsoft 365. Disse data bruges af insiderrisikoløsningen til at generere potentielle risikoindikatorer. Data til følgende HR-scenarier kan importeres til Microsoft 365:

- Medarbejderens fratræden. Oplysninger om medarbejdere, der har forladt din organisation.

- Jobniveauændringer. Oplysninger om ændringer på jobniveau for medarbejdere, f.eks. forfremmelser og sænkninger.

- Ydeevnegennemgange. Oplysninger om medarbejderydeevne.

- Planer til forbedring af ydeevnen. Oplysninger om planer for forbedring af ydeevnen for medarbejdere.

- Medarbejderprofil (prøveversion). Generelle oplysninger om en medarbejder.

Den type HR-data, der skal importeres, afhænger af politikken for styring af insiderrisiko og den tilsvarende politikskabelon, du vil implementere. I følgende tabel kan du se, hvilken HR-datatype der kræves til hver politikskabelon:

|  Politikskabelon |  HR-datatype |
|:------------------------------|:--------------------------------|
| Datatyveri foretaget af afrejsende brugere | Fratrædede medarbejdere|
| Generelle datalækager                             | Ikke relevant|
| Datalækager fra prioriterede brugere                   | Ikke relevant |
| Datalækager fra utilfredse brugere                | Ændringer på jobniveau, ydeevnegennemgange, planer for forbedring af ydeevnen|
| Overtrædelser af den generelle sikkerhedspolitik             | Ikke relevant |
| Sikkerhedspolitikovertrædelser af afrejsende brugere  | Fratrædede medarbejdere|
| Sikkerhedspolitiske overtrædelser af prioriterede brugere   | Ikke relevant|
| Sikkerhedspolitiske overtrædelser af utilfredse brugere| Ændringer på jobniveau, ydeevnegennemgange, planer for forbedring af ydeevnen |
| Stødende sprog i mail                    | Ikke relevant |
| Sundhedspolitik| Medarbejderprofil |
|||

Du kan få flere oplysninger om politikskabeloner til styring af insiderrisiko under [Politikker for styring af insiderrisiko](insider-risk-management-policies.md#policy-templates).

For hvert HR-scenarie skal du angive de tilsvarende HR-data i en eller flere CSV-filer. Det antal CSV-filer, der skal bruges til implementering af styring af insiderrisiko, beskrives senere i dette afsnit.

Når du har oprettet CSV-filen med de påkrævede HR-data, skal du gemme dem på den lokale computer, som du kører scriptet på i trin 4. Du skal også implementere en opdateringsstrategi for at sikre, at CSV-filen altid indeholder de mest aktuelle oplysninger, så uanset hvad du kører scriptet, uploades de nyeste HR-data til Microsoft-cloudmiljøet og bliver tilgængelige for løsningen til styring af insiderrisiko.

> [!IMPORTANT]
> De kolonnenavne, der er beskrevet i følgende afsnit, er ikke obligatoriske parametre, men kun eksempler. Du kan bruge et hvilket som helst kolonnenavn i dine CSV-filer. De kolonnenavne, du bruger i en CSV-fil, *skal* dog knyttes til datatypen, når du opretter HR-connectoren i trin 3. Bemærk også, at CSV-eksempelfilerne i følgende afsnit vises i NotePad-visning. Det er meget nemmere at få vist og redigere CSV-filer i Microsoft Excel.

I følgende afsnit beskrives de påkrævede CSV-data for hvert HR-scenarie.

### <a name="csv-file-for-employee-resignation-data"></a>CSV-fil for data om medarbejders fratræden

Her er et eksempel på en CSV-fil til data om medarbejders fratræden.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

I følgende tabel beskrives hver kolonne i CSV-filen for data om medarbejders fratræden.

|  Kolonne   |   Beskrivelse |
|:------------|:----------------|
|**Emailaddress**| Angiver mailadressen (UPN) for den afbrudte bruger.|
| **Fratrædelsesdato** | Angiver den dato, hvor brugerens ansættelse officielt blev afsluttet i organisationen. Dette kan f.eks. være den dato, hvor brugeren gav besked om at forlade din organisation. Denne dato kan være forskellig fra datoen for personens sidste arbejdsdag. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Sidstearbejdsdato** | Angiver den sidste arbejdsdag for den afbrudte bruger. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>CSV-fil til jobniveau ændrer data

Her er et eksempel på en CSV-fil til dataændringer på jobniveau.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 - Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 - Director,Level 60- Sr. Manager
```

I følgende tabel beskrives hver kolonne i CSV-filen for data om jobændringer.

|  Kolonne | Beskrivelse |
|:--------- |:------------- |
| **Emailaddress**  | Angiver brugerens mailadresse (UPN).|
| **Ikrafttrædelsesdato** | Angiver den dato, hvor brugerens jobniveau blev ændret officielt. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver de bemærkninger, som evaluator har angivet om ændring af jobniveau. Du kan angive en grænse på 200 tegn. Denne parameter er valgfri. Du behøver ikke at inkludere den i CSV-filen.|
| **Gammelt niveau**| Angiver brugerens jobniveau, før det blev ændret. Dette er en fritekstparameter og kan indeholde hierarkisk taksonomi for din organisation. Denne parameter er valgfri. Du behøver ikke at inkludere den i CSV-filen.|
| **Nyt niveau**| Angiver brugerens jobniveau, efter at det blev ændret. Dette er en fritekstparameter og kan indeholde hierarkisk taksonomi for din organisation. Denne parameter er valgfri. Du behøver ikke at inkludere den i CSV-filen.|
|||

### <a name="csv-file-for-performance-review-data"></a>CSV-fil til data til gennemsyn af ydeevne

Her er et eksempel på en CSV-fil til ydeevnedata.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

I følgende tabel beskrives hver kolonne i CSV-filen for data til gennemsyn af ydeevne.

|  Kolonne | Beskrivelse |
|:----------|:--------------|
| **Emailaddress**  | Angiver brugerens mailadresse (UPN).|
| **Ikrafttrædelsesdato** | Angiver den dato, hvor brugeren officielt blev informeret om resultatet af gennemgangen af ydeevnen. Dette kan være den dato, hvor cyklussen for gennemsyn af ydeevne sluttede. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver eventuelle bemærkninger, som evaluator har givet brugeren til gennemgang af ydeevnen. Dette er en tekstparameter med en grænse på 200 tegn. Denne parameter er valgfri. Du behøver ikke at inkludere den i CSV-filen.|
| **Rating**| Angiver den bedømmelse, der er angivet for gennemgangen af ydeevnen. Dette er en tekstparameter og kan indeholde en hvilken som helst frihåndstekst, som din organisation bruger til at genkende evalueringen. Det kan f.eks. være "3 opfyldte forventninger" eller "2 under middel". Dette er en tekstparameter med en grænse på 25 tegn. Denne parameter er valgfri. Du behøver ikke at inkludere den i CSV-filen.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>CSV-fil til data til forbedring af ydeevnen

Her er et eksempel på en CSV-fil til dataene til data til forbedring af ydeevnen.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

I følgende tabel beskrives hver kolonne i CSV-filen for data til gennemsyn af ydeevne.

|  Kolonne |  Beskrivelse |
|:----------|:---------------|
| **Emailaddress**  | Angiver brugerens mailadresse (UPN).|
| **Ikrafttrædelsesdato** | Angiver den dato, hvor brugeren officielt blev informeret om sin plan til forbedring af ydeevnen. Du skal bruge følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver eventuelle bemærkninger, som evaluator har angivet om planen for forbedring af ydeevnen. Dette er en tekstparameter med en grænse på 200 tegn. Dette er en valgfri parameter. Du behøver ikke at inkludere den i CSV-filen. |
| **Rating**| Angiver en hvilken som helst bedømmelse eller andre oplysninger, der er relateret til gennemgangen af ydeevnen. Dette er en tekstparameter og kan indeholde en hvilken som helst frihåndstekst, som din organisation bruger til at genkende evalueringen. Det kan f.eks. være "3 opfyldte forventninger" eller "2 under middel". Dette er en tekstparameter med en grænse på 25 tegn. Dette er en valgfri parameter. Du behøver ikke at inkludere den i CSV-filen.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>CSV-fil til medarbejderprofildata (prøveversion)

> [!NOTE]
> Muligheden for at oprette en HR-connector til medarbejderprofildata findes i en offentlig prøveversion. Hvis du vil oprette en HR-connector, der understøtter medarbejderprofildata, skal du gå til siden **Dataconnectors på overholdelsesportalen**, vælge fanen **Forbindelser** og derefter klikke på **Tilføj en connectorHR** >  **(prøveversion).** Følg trinnene for at oprette en connector i [Trin 3: Opret HR-connectoren](#step-3-create-the-hr-connector).

Her er et eksempel på en CSV-fil til dataene for medarbejderprofildataene.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

I følgende tabel beskrives hver kolonne i CSV-filen for medarbejderprofildata.

|  Kolonne |  Beskrivelse |
|:----------|:---------------|
| Emailaddress<sup>*</sup>    | Brugerens hovednavn (UPN) eller mailadressen på medarbejderen.|
| EmployeeFirstName<sup>*</sup>   | Medarbejderens fornavn.|
| EmployeeLastName<sup>*</sup>   | Medarbejderens efternavn.|
| EmployeeAddressLine1<sup>*</sup>    | Medarbejderens adresse.|
| EmployeeAddressLine2   | Sekundære adresseoplysninger, f.eks. lejlighedsnummer, for medarbejder.|
| Medarbejdercity | Bopælsby for medarbejder.|
| Medarbejdertilstand | Bopælsstat for medarbejder.|
| EmployeeZipCode<sup>*</sup>  | Bopælsnummeret for medarbejderen. |
| Antal medarbejdere| Bopælsland for medarbejder.|
| Medarbejderdepartment | Medarbejderens afdeling i organisationen.|
| Medarbejdertype |Ansættelsestype for medarbejder, f.eks. Almindelig, Undtaget eller Underleverandør.|
| Medarbejderrolle |Medarbejdernes rolle, betegnelse eller stilling i organisationen.|
|||

> [!NOTE]
> <sup>*</sup> Denne kolonne er obligatorisk. Hvis der mangler en obligatorisk kolonne, valideres CSV-filen ikke, og andre data i filen importeres ikke.

Vi anbefaler, at du opretter en HR-connector, der kun importerer medarbejderprofildata. For denne connector skal du sørge for ofte at opdatere medarbejderprofildataene, helst hver 15. til 20. dag. Medarbejderprofilposter slettes, hvis de ikke opdateres inden for de seneste 30 dage.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Sådan afgør du, hvor mange CSV-filer der skal bruges til HR-data

I trin 3 kan du vælge at oprette separate forbindelser for hver HR-datatype, eller du kan vælge at oprette en enkelt connector for alle datatyper. Du kan bruge separate CSV-filer, der indeholder data til ét HR-scenarie (f.eks. eksemplerne på de CSV-filer, der er beskrevet i de forrige afsnit). Du kan også bruge en enkelt CSV-fil, der indeholder data til to eller flere HR-scenarier. Her er nogle retningslinjer, der kan hjælpe dig med at bestemme, hvor mange CSV-filer der skal bruges til HR-data.

- Hvis den insiderrisikostyringspolitik, du vil implementere, kræver flere HR-datatyper, kan du overveje at bruge en enkelt CSV-fil, der indeholder alle de påkrævede datatyper.

- Metoden til generering eller indsamling af HR-data kan bestemme antallet af CSV-filer. Hvis de forskellige typer HR-data, der bruges til at konfigurere en HR-connector, f.eks. er placeret i et enkelt HR-system i din organisation, kan du muligvis eksportere dataene til en enkelt CSV-fil. Men hvis data distribueres på tværs af forskellige HR-systemer, kan det være nemmere at eksportere data til forskellige CSV-filer. Data om medarbejders fratræden kan f.eks. være placeret i et andet HR-system end data for jobniveau eller gennemsyn af ydeevne. I dette tilfælde kan det være nemmere at have separate CSV-filer i stedet for manuelt at kombinere dataene i en enkelt CSV-fil. Derfor kan den måde, du henter eller eksporterer data fra dine HR-systemer på, bestemme, hvor mange CSV-filer du har brug for.

- Det antal HR-connectors, du skal oprette, bestemmes som regel af datatyperne i en CSV-fil. Hvis en CSV-fil f.eks. indeholder alle de datatyper, der kræves for at understøtte implementering af insiderrisikostyring, skal du kun bruge én HR-connector. Men hvis du har to separate CSV-filer, der hver især indeholder en enkelt datatype, skal du oprette to HR-connectors. En undtagelse til dette er, at hvis du føjer en **HRScenario-kolonne** til en CSV-fil (se næste afsnit), kan du konfigurere en enkelt HR-connector, der kan behandle forskellige CSV-filer.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Konfiguration af en enkelt CSV-fil til flere HR-datatyper

Du kan føje flere HR-datatyper til en enkelt CSV-fil. Dette er nyttigt, hvis den løsning til styring af insiderrisiko, du implementerer, kræver flere HR-datatyper, eller hvis datatyperne er placeret i et enkelt HR-system i din organisation. Hvis du har færre CSV-filer, kan du altid have færre HR-connectors at oprette og administrere.

Her er kravene til konfiguration af en CSV-fil med flere datatyper:

- Du skal tilføje de påkrævede kolonner (og valgfrit, hvis du bruger dem) for hver datatype og det tilsvarende kolonnenavn i kolonneoverskriften. Hvis en datatype ikke svarer til en kolonne, kan du lade værdien være tom.

- Hvis du vil bruge en CSV-fil med flere typer HR-data, skal HR-connectoren vide, hvilke rækker i CSV-filen der indeholder typen HR-data. Dette opnås ved at føje en ekstra **HRScenario-kolonne** til CSV-filen. Værdierne i denne kolonne identificerer typen af HR-data i hver række. Værdier, der svarer til de fire HR-scenarier, kan f.eks. være Fratræden, Ændring af jobniveau, \`Gennemgang\` af ydeevne, \`Plan for\` forbedring af ydeevnen og \`Medarbejderprofil\`.\`\`\`\`

- Hvis du har flere CSV-filer, der indeholder kolonnen HRScenario**, skal du sørge for, at hver fil bruger det samme kolonnenavn og de samme værdier, som identificerer de specifikke HR-scenarier.

I følgende eksempel vises en CSV-fil, der indeholder kolonnen **HRScenario** . Værdierne i kolonnen HRScenario identificerer datatypen i den tilsvarende række.

```text
HRScenario,EmailAddress,ResignationDate,LastWorkingDate,EffectiveDate,Remarks,Rating,OldLevel,NewLevel
Resignation,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30,,,,
Resignation,pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540,,,,
Job level change,sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 61 Sr. Manager, Level 60 Manager
Job level change,pillarp@contoso.com,2019-04-23T15:18:02.4675041+05:30,,,,,Level 62 Director,Level 60 Sr Manager
Performance review,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2 Below expectations,,
Performance review,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team,,
Performance improvement plan,sarad@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2 Below expectations,,
Performance improvement plan,pillarp@contoso.com,,,2019-04-23T15:18:02.4675041+05:30,Multiple conflicts with the team,,
```

> [!NOTE]
> Du kan bruge et hvilket som helst navn til den kolonne, der identificerer HR-datatypen, da du vil knytte navnet på kolonnen i CSV-filen til den kolonne, der identificerer HR-datatypen, når du konfigurerer connectoren i trin 3. Du skal også tilknytte de værdier, der bruges til datatypekolonnen, når du konfigurerer connectoren.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Tilføjelse af kolonnen HRScenario til en CSV-fil, der indeholder en enkelt datatype

Baseret på din organisations HR-systemer, og hvordan du eksporterer HR-data til CSV-fil, skal du muligvis oprette flere CSV-filer, der indeholder en enkelt HR-datatype. I dette tilfælde kan du stadig oprette en enkelt HR-connector for at importere data fra forskellige CSV-filer. Hvis du vil gøre dette, skal du blot føje en HRScenario-kolonne til CSV-filen og angive HR-datatypen. Derefter kan du køre scriptet for hver CSV-fil, men bruge det samme job-id for connectoren. Se [trin 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Trin 2: Opret en app i Azure Active Directory

Det næste trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den HR-connector, du opretter i trin 3. Når du opretter denne app, kan Azure AD godkende HR-connectoren, når den kører, og forsøger at få adgang til din organisation. Denne app bruges også til at godkende det script, du kører i trin 4, for at uploade dine HR-data til Microsoft-cloudmiljøet. Under oprettelsen af denne Azure AD-app skal du gemme følgende oplysninger. Disse værdier bruges i trin 3 og trin 4.

- Azure AD-program-id (også kaldet *app-id* eller *klient-id*)

- Azure AD-programhemmelighed (også kaldet *klienthemmeligheden*)

- Lejer-id (også kaldet *mappe-id*)

Du kan finde en trinvis vejledning i, hvordan du opretter en app i Azure AD, under [Registrer et program med Microsoft-identitetsplatform](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-3-create-the-hr-connector"></a>Trin 3: Opret HR-connectoren

Det næste trin er at oprette en HR-connector på overholdelsesportalen. Når du har kørt scriptet i trin 4, overfører den HR-connector, du opretter, HR-dataene fra CSV-filen til din Microsoft 365 organisation. Før du opretter en connector, skal du sørge for, at du har en liste over HR-scenarierne og de tilsvarende CSV-kolonnenavne for hver enkelt. Du skal knytte de data, der kræves til hvert scenarie, til de faktiske kolonnenavne i din CSV-fil, når du konfigurerer connectoren. Du kan også uploade en CSV-eksempelfil, når du konfigurerer connectoren, så hjælper guiden dig med at knytte navnet på kolonnerne til de påkrævede datatyper.

Når du har fuldført dette trin, skal du sørge for at kopiere det job-id, der genereres, når du opretter connectoren. Du skal bruge job-id'et, når du kører scriptet.

1. Gå til overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataconnectors**</a>.

2. Klik på **HR (prøveversion)** på siden **Dataconnectors**.

3. Klik på **Tilføj connector** på siden **HR (prøveversion**).

4. Gør følgende på siden **Konfigurer forbindelsen** , og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 2.

   2. Skriv et navn til HR-connectoren.

5. På siden HR-scenarier skal du vælge et eller flere HR-scenarier, som du vil importere data for, og derefter klikke på **Næste**.

   ![Vælg et eller flere HR-scenarier.](../media/HRConnectorScenarios.png)

6. Vælg en filtype, hvis det er nødvendigt, på siden med metoden til filtilknytning, vælg derefter en af følgende indstillinger, og klik derefter på **Næste**.

   - **Upload en eksempelfil**. Hvis du vælger denne indstilling, skal du klikke på **Upload eksempelfil** for at uploade den CSV-fil, du forberedte i trin 1. Med denne indstilling kan du hurtigt vælge kolonnenavne i CSV-filen på en rulleliste for at knytte dem til datatyperne for de HR-scenarier, du tidligere har valgt.

   ELLER

   - **Angiv tilknytningsoplysningerne manuelt**. Hvis du vælger denne indstilling, skal du skrive navnet på kolonnerne i CSV-filen for at knytte dem til datatyperne for de HR-scenarier, du tidligere har valgt.

7. På siden Oplysninger om filtilknytning skal du gøre et af følgende, afhængigt af om du har uploadet en eksempel-CSV-fil, og om du konfigurerer connectoren til et enkelt HR-scenarie eller til flere scenarier. Hvis du har uploadet en eksempelfil, behøver du ikke skrive kolonnenavnene. Du vælger dem på en rulleliste.

    - Hvis du valgte et enkelt HR-scenarie i det forrige trin, skal du skrive kolonneoverskriftsnavnene (også kaldet *parametre*) fra den CSV-fil, du oprettede i trin 1, i hvert af de relevante felter. De kolonnenavne, du skriver, skelner ikke mellem store og små bogstaver, men husk at inkludere mellemrum, hvis kolonnenavnene i CSV-filen indeholder mellemrum. Som tidligere forklaret skal de navne, du skriver i disse felter, svare til parameternavnene i CSV-filen. På følgende skærmbillede kan du f.eks. se parameternavnene fra CSV-eksempelfilen for HR-scenariet for medarbejderfratræden, der vises i trin 1.

    - Hvis du har valgt flere datatyper i trin ovenfor, skal du angive navnet på id-kolonnen, der identificerer HR-datatypen i din CSV-fil. Når du har angivet navnet på id-kolonnen, skal du skrive den værdi, der identificerer denne HR-datatype, og skrive kolonneoverskriftsnavnene for de valgte datatyper fra den eller de CSV-filer, du oprettede i trin 1, i hver af de relevante felter for hver valgt datatype. Som tidligere forklaret, skal de navne, du skriver i disse felter, stemme overens med kolonnenavnene i CSV-filen.

8. Gennemse dine indstillinger på siden **Gennemse** , og klik derefter på **Udfør** for at oprette connectoren.

   Der vises en statusside, der bekræfter, at connectoren blev oprettet. Denne side indeholder to vigtige ting, som du skal udføre i næste trin for at køre eksempelscriptet for at uploade dine HR-data.

   ![Gennemse siden med job-id og link til GitHub for eksempelscript.](../media/HRConnector_Confirmation.png)

   1. **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere den fra denne side eller fra connector-pop op-siden.

   2. **Link til eksempelscript.** Klik på linket **her** for at gå til GitHub websted for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Du kan også angive et bogmærke for destinationen eller kopiere URL-adressen, så du kan få adgang til den igen, når du kører scriptet. Dette link er også tilgængeligt på connector-pop op-siden.

9. Klik på **Udført**.

   Den nye connector vises på listen under fanen **Forbindelser** .

10. Klik på den HR-connector, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om connectoren.

   ![Pop op-side for ny HR-connector.](../media/HRConnectorWizard7.png)

Hvis du ikke allerede har gjort det, kan du kopiere værdierne for **job-id'et for Azure App ID** og **Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller downloade det ved hjælp af linket i næste trin).

Du kan også klikke på **Rediger** for at ændre Det Azure App-id eller de kolonneoverskrifter, du har defineret på siden **Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine HR-data

Det sidste trin i konfiguration af en HR-connector er at køre et eksempelscript, der uploader HR-dataene i CSV-filen (som du oprettede i trin 1) til Microsoft-cloudmiljøet. Scriptet uploader specifikt dataene til HR-connectoren. Når du har kørt scriptet, importerer den HR-connector, du oprettede i trin 3, HR-dataene til din Microsoft 365 organisation, hvor andre værktøjer til overholdelse af angivne standarder kan få adgang til dem, f.eks. Insider Risk Management-løsningen. Når du har kørt scriptet, kan du overveje at planlægge en opgave for at køre den automatisk dagligt, så de mest aktuelle data om medarbejderafslutning uploades til Microsoft-cloudmiljøet. Se [Planlæg, at scriptet skal køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

1. Gå til det vindue, du lod åbne fra det forrige trin, for at få adgang til GitHub websted med eksempelscriptet. Du kan også åbne webstedet med bogmærker eller bruge den URL-adresse, du kopierede. Du kan også få adgang til scriptet [her](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Klik på knappen **Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjerne i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af `.ps1`, f.eks. `HRConnector.ps1`. Du kan også bruge GitHub filnavn til scriptet, som er `upload_termination_records.ps1`.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at overføre HR-dataene i CSV-filen til Microsoft-cloudmiljøet. f.eks.:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   I følgende tabel beskrives de parametre, der skal bruges sammen med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

   | Parameter | Beskrivelse |
   |:-----|:-----|:-----|
   |`tenantId`|Dette er id'et for din Microsoft 365 organisation, som du fik i trin 2. Du kan også hente lejer-id'et for din organisation på bladet **Oversigt** i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |`appId` |Dette er Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 2. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation. | 
   |`appSecret`|Dette er Azure AD-programhemmeligheden for den app, du oprettede i Azure AD i trin 2. Dette bruges også til godkendelse.|
   |`jobId`|Dette er job-id'et for den HR-connector, du oprettede i trin 3. Dette bruges til at knytte de HR-data, der uploades til Microsoft-cloudmiljøet, til HR-connectoren.|
   |`filePath`|Dette er filstien til filen (gemt på det samme system som scriptet), som du oprettede i trin 1. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
   |||

   Her er et eksempel på syntaksen for HR-connectorscriptet, der bruger faktiske værdier for hver parameter:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Hvis overførslen lykkes, viser scriptet **meddelelsen Upload fuldført**.

   > [!NOTE]
   > Hvis du har problemer med at køre den forrige kommando på grund af kørselspolitikker, skal du se [Om kørselspolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies) og [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) for at få vejledning til, hvordan du angiver kørselspolitikker.

## <a name="step-5-monitor-the-hr-connector"></a>Trin 5: Overvåg HR-connectoren

Når du har oprettet HR-connectoren og kørt scriptet for at uploade dine HR-data, kan du få vist connectoren og uploade status på overholdelsesportalen. Hvis du planlægger, at scriptet skal køre automatisk regelmæssigt, kan du også få vist den aktuelle status efter sidste gang scriptet kørte.

1. Gå til overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataconnectors**</a>.

2. Klik på fanen **Forbindelser,** og vælg derefter HR-connectoren for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

   ![Pop op-side med HR-connector med egenskaber og status.](../media/HRConnectorFlyout1.png)

3. Under **Status** skal du klikke på linket **Downloadlog** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om, hver gang scriptet kører, og uploader dataene fra CSV-filen til Microsoft-cloudmiljøet. 

   ![Logfilen for HR-connectoren viser talrækker fra den CSV-fil, der blev overført.](../media/HRConnectorLogFile.png)

   Feltet `RecordsSaved` angiver antallet af rækker i den CSV-fil, der er overført. Hvis CSV-filen f.eks. indeholder fire rækker, er værdien af `RecordsSaved` felterne 4, hvis scriptet overførte alle rækkerne i CSV-filen.

Hvis du ikke har kørt scriptet i trin 4, vises der et link til download af scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene for at køre scriptet.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg, at scriptet kører automatisk

Hvis du vil sikre dig, at de nyeste HR-data fra din organisation er tilgængelige for værktøjer som insiderrisikostyringsløsningen, anbefaler vi, at du planlægger, at scriptet kører automatisk på tilbagevendende basis, f.eks. én gang om dagen. Dette kræver også, at du opdaterer HR-dataene i CSV-filen efter en lignende (hvis ikke den samme) tidsplan, så de indeholder de nyeste oplysninger om medarbejdere, der forlader din organisation. Målet er at uploade de mest aktuelle HR-data, så HR-connectoren kan gøre dem tilgængelige for insiderrisikostyringsløsningen.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen Windows **Start** på den lokale computer, og skriv derefter **Opgavestyring**.

2. Klik på appen **Opgavestyring** for at åbne den.

3. Klik på **Opret opgave** i afsnittet **Handlinger**.

4. Skriv et beskrivende navn på den planlagte opgave under fanen **Generelt** . f.eks. **HR Connector Script**. Du kan også tilføje en valgfri beskrivelse.

5. Under **Sikkerhedsindstillinger** skal du gøre følgende:

   1. Find ud af, om du kun vil køre scriptet, når du er logget på computeren eller kører det, når du er logget på eller ej.

   1. Sørg for, at afkrydsningsfeltet **Kør med de højeste rettigheder** er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

   1. Under **Indstillinger** skal du vælge indstillingen **Dagligt** og derefter vælge en dato og et klokkeslæt, hvor scriptet skal køres første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

   1. Under **Avancerede indstillinger** skal du kontrollere, at afkrydsningsfeltet **Aktiveret** er markeret.

   1. Klik på **OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger til oprettelse af en ny planlagt opgave til HR-connectorscriptet.](../media/HRConnectorScheduleTask1.png)

   1. På rullelisten **Handling** skal du kontrollere, at **Start et program** er valgt.

   1. Klik på **Gennemse** i feltet **Program/script**, gå til følgende placering, og vælg den, så stien vises i feltet: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. Det kan f.eks. `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. For eksempel `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Klik på **OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK** i vinduet **Opret opgave** for at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i opgavestyringsbiblioteket.

   ![Den nye opgave vises i opgavestyringsbiblioteket.](../media/HRConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt til at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden for den tilsvarende HR-connector i Overholdelsescenter.

## <a name="existing-hr-connectors"></a>Eksisterende HR-connectors

Den 13. december 2021 frigav vi scenariet med medarbejderprofildata for HR-connectors. Hvis du har oprettet en HR-connector før denne dato, overfører vi de eksisterende forekomster eller organisationens HR-connectors, så dine HR-data fortsat importeres til Microsoft-cloudmiljøet. Du behøver ikke at gøre noget for at bevare denne funktionalitet. Du kan fortsætte med at bruge disse connectors uden afbrydelse.

Hvis du vil implementere scenariet med medarbejderprofildata, skal du oprette en ny HR-connector og konfigurere den efter behov. Når du har oprettet en ny HR-connector, skal du køre scriptet ved hjælp af job-id'et for den nye connector og CSV-filer med [medarbejderprofildata](#csv-file-for-employee-profile-data-preview) , der tidligere er beskrevet i denne artikel.
