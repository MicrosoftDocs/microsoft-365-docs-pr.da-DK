---
title: Konfigurer en forbindelse til at importere HR-data
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
description: Administratorer kan konfigurere en dataforbindelse til at importere medarbejderdata fra organisationens HR-system (HUMAN Resources) for at Microsoft 365. Dette giver dig mulighed for at bruge HR-data i insider-risikostyringspolitikker til at hjælpe dig med at registrere aktivitet fra bestemte brugere, der kan udgøre en intern trussel mod din organisation.
ms.openlocfilehash: 64822b8ea5952f4fb6787dfd7832879c2e84c2d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587763"
---
# <a name="set-up-a-connector-to-import-hr-data"></a>Konfigurer en forbindelse til at importere HR-data

Du kan konfigurere en dataforbindelse i Microsoft 365 Overholdelsescenter til at importere HR-data (HUMAN Resources) i forbindelse med hændelser som f.eks. en brugers arbejdsplads eller en ændring i en brugers jobniveau. HR-data kan derefter bruges af [insider-risikostyringsløsningen](insider-risk-management.md) til at generere risikoindikatorer, der kan hjælpe dig med at få identiteter af mulig ondsindet aktivitet eller datatyveri af brugere i organisationen.

Konfiguration af en forbindelse til HR-data, som insider-politikker for risikostyring kan bruge til at generere risikoindikatorer, består i at oprette en CSV-fil, der indeholder HR-data, oprette en app i Azure Active Directory, der bruges til godkendelse, oprette en HR-dataforbindelse i Microsoft 365 Overholdelsescenter og derefter køre et script (på planlagt basis), som ingests the HR data in CSV files to the Microsoft cloud so it's available to the insider risk management solution.

> [!IMPORTANT]
> En ny version af HR-forbindelsen er nu tilgængelig til offentlig prøveversion. Hvis du vil oprette en ny HR-forbindelse eller importere data for scenariet for den nye medarbejderprofil [for scenariet](#csv-file-for-employee-profile-data-preview) for sundhedspolitik for insider-risikostyring, skal du gå til siden **Dataforbindelser** i Microsoft 365 Overholdelsescenter, vælge  fanen Forbindelser og derefter klikke på Tilføj en forbindelse **> HR (preview)** for at starte opsætningen. Eksisterende HR-forbindelser vil fortsat fungere uden afbrydelser.

## <a name="before-you-begin"></a>Før du begynder

- Afgør, hvilke HR-scenarier og -data, der skal importeres Microsoft 365. Dette hjælper dig med at afgøre, hvor mange CSV-filer og HR-forbindelser du skal oprette, og hvordan du opretter og strukturerer CSV-filerne. De HR-data, du importerer, bestemmes af de Insider Risk Management-politikker, du vil implementere. Du kan finde flere oplysninger i Trin 1.

- Find ud af, hvordan du henter eller eksporterer data fra organisationens HR-system (og med jævne mellemrum), og føj dem til de CSV-filer, du opretter i trin 1. Det script, du kører i trin 4, overfører HR-dataene i CSV-filerne til Microsoft-skyen.

- Den bruger, der opretter HR-forbindelsen i trin 3, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Eksempelscriptet, som du kører i trin 4, uploader dine HR-data til Microsoft-skyen, så de kan bruges af Insider Risk Management-løsningen. Dette eksempelscript understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

- Denne forbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible. Du kan finde en trinvis vejledning til konfiguration af en HR-forbindelse i et GCC-miljø under Konfigurer en forbindelse til at importere [HR-data i den amerikanske stat](import-hr-data-US-government.md).

## <a name="step-1-prepare-a-csv-file-with-your-hr-data"></a>Trin 1: Forbered en CSV-fil med dine HR-data

Det første trin er at oprette en CSV-fil, der indeholder de HR-data, som forbindelsen skal importere til Microsoft 365. Disse data bruges af Insider-risikoløsningen til at generere potentielle risikoindikatorer. Data for følgende HR-scenarier kan importeres til Microsoft 365:

- Medarbejdersnage. Oplysninger om medarbejdere, der har forladt din organisation.

- Ændringer på jobniveau. Oplysninger om ændringer på jobniveau for medarbejdere, f.eks. kampagner og degraderinger.

- Evaluering af ydeevne. Oplysninger om medarbejdernes ydeevne.

- Planer til forbedring af ydeevnen. Oplysninger om planer til forbedring af ydeevnen for medarbejdere.

- Medarbejderprofil (eksempel). Generelle oplysninger om en medarbejder.

Typen af HR-data, der skal importeres, afhænger af politikken for insider-risikostyring og den tilsvarende politikskabelon, du vil implementere. Følgende tabel viser, hvilken HR-datatype der kræves til hver politikskabelon:

|  Politikskabelon |  HR-datatype |
|:------------------------------|:--------------------------------|
| Datatyveri ved at brugere, der forlader brugere | Medarbejdermedarbejdere|
| Generelle datalækager                             | Ikke relevant|
| Datalækager efter prioritetsbrugere                   | Ikke relevant |
| Datalækager fra forskellige brugere                | Ændringer på jobniveau, evaluering af resultater, planer til forbedring af ydeevnen|
| Generelle overtrædelser af sikkerhedspolitik             | Ikke relevant |
| Brud på sikkerhedspolitik ved brugere, der forlader os  | Medarbejdermedarbejdere|
| Prioritetsbrugeres brud på sikkerhedspolitik   | Ikke relevant|
| Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens| Ændringer på jobniveau, evaluering af resultater, planer til forbedring af ydeevnen |
| Stødende sprog i mail                    | Ikke relevant |
| Sundhedspolitik| Medarbejderprofil |
|||

Du kan finde flere oplysninger om politikskabeloner til insider-risikostyring [i Insider-politikker for risikostyring](insider-risk-management-policies.md#policy-templates).

For hvert HR-scenarie skal du angive de tilsvarende HR-data i en eller flere CSV-filer. Antallet af CSV-filer, der skal bruges til din implementering af Insider Risk Management, gennemgås senere i dette afsnit.

Når du har oprettet CSV-filen med de nødvendige HR-data, skal du gemme den på den lokale computer, som du kører scriptet på i trin 4. Du bør også implementere en opdateringsstrategi for at sikre, at CSV-filen altid indeholder de mest aktuelle oplysninger, så uanset hvad du kører scriptet, vil de nyeste HR-data blive uploadet til Microsoft-skyen og tilgængelige for Insider-risikostyringsløsningen.

> [!IMPORTANT]
> Kolonnenavnene, der er beskrevet i de følgende afsnit, er ikke påkrævede parametre, men kun eksempler. Du kan bruge et hvilket som helst kolonnenavn i CSV-filerne. Men de kolonnenavne, du bruger i en CSV-fil, skal være knyttet til datatypen, når du opretter HR-forbindelsen i trin 3. Bemærk også, at CSV-eksempelfilerne i følgende afsnit vises i NotePad-visning. Det er meget nemmere at få vist og redigere CSV-filer i Microsoft Excel.

I de følgende afsnit beskrives de nødvendige CSV-data for hvert HR-scenarie.

### <a name="csv-file-for-employee-resignation-data"></a>CSV-fil til medarbejderoplysninger

Her er et eksempel på en CSV-fil, hvor medarbejderen kan se data, du arbejder på.

```text
EmailAddress,ResignationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

I følgende tabel beskrives hver kolonne i CSV-filen for medarbejderens data, der skal vises.

|  Kolonne   |   Beskrivelse |
|:------------|:----------------|
|**Mailadresse**| Angiver den opsagte brugers mailadresse (UPN).|
| **Date** | Angiver den dato, hvor brugerens ansættelse officielt blev afsluttet i din organisation. Dette kan f.eks. være den dato, hvor brugeren har givet besked om at forlade organisationen. Denne dato kan være forskellig fra datoen for personens sidste arbejdsdag. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **LastWorkingDate** | Angiver den sidste dags arbejde for den opsagte bruger. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

### <a name="csv-file-for-job-level-changes-data"></a>CSV-fil til jobniveau ændrer data

Her er et eksempel på en CSV-fil til ændringer af data på jobniveau.

```text
EmailAddress,EffectiveDate,OldLevel,NewLevel
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 61 – Sr. Manager,Level 60- Manager
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30,Level 62 – Director,Level 60- Sr. Manager
```

I følgende tabel beskrives hver kolonne i CSV-filen for data, der ændres på jobniveau.

|  Kolonne | Beskrivelse |
|:--------- |:------------- |
| **Mailadresse**  | Angiver brugerens mailadresse (UPN).|
| **EffectiveDate** | Angiver den dato, hvor brugerens jobniveau officielt blev ændret. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver de bemærkninger, evaluatoren har leveret om ændringen af jobniveau. Du kan angive en grænse på 200 tegn. Denne parameter er valgfri. Du behøver ikke at medtage den i CSV-filen.|
| **OldLevel**| Angiver brugerens jobniveau, før det blev ændret. Dette er en parameter med fri tekst og kan indeholde hierarkisk taksonomi for organisationen. Denne parameter er valgfri. Du behøver ikke at medtage den i CSV-filen.|
| **NewLevel**| Angiver brugerens jobniveau, efter det blev ændret. Dette er en parameter med fri tekst og kan indeholde hierarkisk taksonomi for organisationen. Denne parameter er valgfri. Du behøver ikke at medtage den i CSV-filen.|
|||

### <a name="csv-file-for-performance-review-data"></a>CSV-fil til data for evaluering af ydeevne

Her er et eksempel på en CSV-fil til data om ydeevne.

```text
EmailAddress,EffectiveDate,Remarks,Rating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectations but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

I følgende tabel beskrives hver kolonne i CSV-filen til gennemgang af ydeevne.

|  Kolonne | Beskrivelse |
|:----------|:--------------|
| **Mailadresse**  | Angiver brugerens mailadresse (UPN).|
| **EffectiveDate** | Angiver den dato, hvor brugeren officielt blev orienteret om resultatet af sin evaluering. Dette kan være den dato, hvor cyklussen for evalueringsgennemsyn er afsluttet. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver eventuelle bemærkninger, evaluatoren har givet til brugeren til evalueringsgennemssynet. Dette er en tekstparameter med en grænse på 200 tegn. Denne parameter er valgfri. Du behøver ikke at medtage den i CSV-filen.|
| **Bedømmelse**| Angiver den bedømmelse, der er angivet for evalueringsvurderingen. Dette er en tekstparameter og kan indeholde eventuel fri tekst, som organisationen bruger til at genkende evalueringen. F.eks. "3  opfyldte forventninger" eller "2 under gennemsnittet". Dette er en tekstparameter med en grænse på 25 tegn. Denne parameter er valgfri. Du behøver ikke at medtage den i CSV-filen.|
|||

### <a name="csv-file-for-performance-improvement-plan-data"></a>CSV-fil til data i en plan for forbedring af ydeevnen

Her er et eksempel på en CSV-fil til dataene i planen til forbedring af ydeevnen.

```text
EmailAddress,EffectiveDate,ImprovementRemarks,PerformanceRating
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,Met expectation but bad attitude,2-Below expectation
pillar@contoso.com,2019-04-23T15:18:02.4675041+05:30, Multiple conflicts with the team
```

I følgende tabel beskrives hver kolonne i CSV-filen til gennemgang af ydeevne.

|  Kolonne |  Beskrivelse |
|:----------|:---------------|
| **Mailadresse**  | Angiver brugerens mailadresse (UPN).|
| **EffectiveDate** | Angiver den dato, hvor brugeren officielt blev informeret om sin plan for forbedring af ydeevnen. Du skal bruge følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
| **Bemærkninger**| Angiver eventuelle bemærkninger, evaluatoren har leveret om planen for forbedring af ydeevnen. Dette er en tekstparameter med en grænse på 200 tegn. Dette er en valgfri parameter. Du behøver ikke at medtage den i CSV-filen. |
| **Bedømmelse**| Angiver en eventuel bedømmelse eller andre oplysninger, der er relateret til evalueringsvurderingen. Dette er en tekstparameter og kan indeholde eventuel gratis tekst i formularen, som din organisation bruger til at genkende evalueringen. F.eks. "3  opfyldte forventninger" eller "2 under gennemsnittet". Dette er en tekstparameter med en grænse på 25 tegn. Dette er en valgfri parameter. Du behøver ikke at medtage den i CSV-filen.|
|||

### <a name="csv-file-for-employee-profile-data-preview"></a>CSV-fil til medarbejderprofildata (eksempel)

> [!NOTE]
> Muligheden for at oprette en HR-forbindelse til medarbejderprofildata er i offentlig prøveversion. Hvis du vil oprette en HR-forbindelse, der understøtter medarbejderprofildata, skal du gå til siden Dataforbindelser i Microsoft 365 Overholdelsescenter, vælge fanen Forbindelser og derefter klikke på Tilføj en **forbindelseshr** >  **(****forhåndsvisning**). Følg trinnene for at oprette en forbindelse i [Trin 3: Opret HR-forbindelsen](#step-3-create-the-hr-connector).

Her er et eksempel på en CSV-fil til dataene til medarbejderprofildataene.

```text
EmailAddress,UserName,EmployeeFirstName,EmployeeLastName,EmployeeAddLine1,EmployeeAddLine2,EmployeeCity,EmployeeState,EmployeeZipCode,EmployeeDept,EmployeeType,EmployeeRole
jackq@contoso.com,jackq,jack,qualtz,50 Oakland Ave,#206,City,Florida,32104,Orthopaedic,Regular,Nurse
```

I følgende tabel beskrives hver kolonne i CSV-filen til medarbejderprofildata.

|  Kolonne |  Beskrivelse |
|:----------|:---------------|
| Mailadresse<sup>*</sup>    | Brugerens hovednavn (UPN) eller medarbejderens mailadresse.|
| EmployeeFirstName<sup>*</sup>   | Medarbejderens fornavn.|
| EmployeeLastName<sup>*</sup>   | Medarbejderens efternavn.|
| EmployeeAddressLine1<sup>*</sup>    | Medarbejderens adresse.|
| EmployeeAddressLine2   | Oplysninger om sekundær adresse, f.eks. lejlighedsnummer, for medarbejderen.|
| EmployeeCity | Bopælsby for medarbejder.|
| EmployeeState | Bopælsland for medarbejder.|
| EmployeeZipCode<sup>*</sup>  | Postnummer for medarbejderens bopælsland. |
| EmployeeCountry| Bopælsland for medarbejder.|
| Medarbejderdepartment | Medarbejdernes afdeling i organisationen.|
| EmployeeType |Ansættelsestype for medarbejdere, f.eks. Almindelig, Undtaget eller Entreprenør.|
| EmployeeRole |Medarbejdernes rolle, angivelse eller stilling i organisationen.|
|||

> [!NOTE]
> <sup>*</sup> Denne kolonne er obligatorisk. Hvis der mangler en obligatorisk kolonne, valideres CSV-filen ikke, og andre data i filen importeres ikke.

Vi anbefaler, at du opretter en HR-forbindelse, der kun importerer medarbejderprofildata. For denne forbindelse skal du sørge for ofte at opdatere medarbejderprofildataene, helst hver 15.til 20. dag. Medarbejderprofilposter slettes, hvis de ikke er opdateret inden for de seneste 30 dage.

### <a name="determining-how-many-csv-files-to-use-for-hr-data"></a>Afgøre, hvor mange CSV-filer der skal bruges til HR-data

I trin 3 kan du vælge at oprette separate forbindelser for hver HR-datatype, eller du kan vælge at oprette en enkelt forbindelse for alle datatyper. Du kan bruge separate CSV-filer, der indeholder data til ét HR-scenarie (som eksemplerne på CSV-filerne beskrevet i de forrige afsnit). Alternativt kan du bruge en enkelt CSV-fil, der indeholder data til to eller flere HR-scenarier. Her er nogle retningslinjer, der kan hjælpe dig med at afgøre, hvor mange CSV-filer du skal bruge til HR-data.

- Hvis den Insider-politik for risikostyring, du vil implementere, kræver flere HR-datatyper, kan du overveje at bruge en enkelt CSV-fil, der indeholder alle de nødvendige datatyper.

- Metoden til at generere eller indsamle HR-data kan bestemme antallet af CSV-filer. Hvis de forskellige typer HR-data, der bruges til at konfigurere en HR-forbindelse, f.eks. findes i et enkelt HR-system i din organisation, kan du eksportere dataene til en enkelt CSV-fil. Men hvis data er fordelt på tværs af forskellige HR-systemer, kan det være nemmere at eksportere data til forskellige CSV-filer. Medarbejderdata kan f.eks. være placeret i et andet HR-system end jobniveau eller data for evaluering af ydeevne. I dette tilfælde kan det være nemmere at have separate CSV-filer i stedet for at skulle kombinere dataene manuelt i en enkelt CSV-fil. Så hvordan du henter eller eksporterer data fra dine HR-systemer, kan afgøre, hvordan antallet af CSV-filer, du skal bruge.

- Som en generel regel bestemmes antallet af HR-forbindelser, du skal oprette, af datatyperne i en CSV-fil. Hvis en CSV-fil f.eks. indeholder alle de datatyper, der kræves for at understøtte din insider-implementering af risikostyring, skal du kun bruge én HR-forbindelse. Men hvis du har to separate CSV-filer, der hver indeholder en enkelt datatype, skal du oprette to HR-forbindelser. En undtagelse til dette er, at hvis du føjer en **HRScenario-kolonne** til en CSV-fil (se næste afsnit), kan du konfigurere en enkelt HR-forbindelse, der kan behandle forskellige CSV-filer.

### <a name="configuring-a-single-csv-file-for-multiple-hr-data-types"></a>Konfiguration af en enkelt CSV-fil til flere HR-datatyper

Du kan føje flere HR-datatyper til en enkelt CSV-fil. Dette er nyttigt, hvis den Insider Risk Management-løsning, du implementerer, kræver flere HR-datatyper, eller hvis datatyperne er placeret i et enkelt HR-system i din organisation. Færre CSV-filer giver dig altid færre HR-forbindelser til at oprette og administrere.

Her er kravene til konfiguration af en CSV-fil med flere datatyper:

- Du skal tilføje de nødvendige kolonner (og valgfrit, hvis du bruger dem) for hver datatype og det tilsvarende kolonnenavn i kolonneoverskriften. Hvis en datatype ikke svarer til en kolonne, kan du lade værdien være tom.

- Hvis du vil bruge en CSV-fil med flere typer HR-data, skal HR-forbindelsen vide, hvilke rækker i CSV-filen, der indeholder hvilke typer HR-data. Det gør du ved at føje en ekstra **HRScenario-kolonne** til CSV-filen. Værdierne i denne kolonne identificerer typen af HR-data i hver række. Eksempelvis kan værdier, der svarer til de fire HR-scenarier, være Scenarier på medarbejderniveau, \`Ændring af jobniveau\`,\`\` Evaluering af ydeevne, \`Forbedring af ydeevne og\` Medarbejderprofil\`\`.\`\`

- Hvis du har flere CSV-filer, der indeholder en HRScenario**-kolonne, skal du sørge for, at hver fil bruger det samme kolonnenavn og de samme værdier, der identificerer de specifikke HR-scenarier.

I følgende eksempel vises en CSV-fil, der indeholder **kolonnen HRScenario** . Værdierne i kolonnen HRScenario identificerer typen af data i den tilsvarende række.

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
> Du kan bruge et hvilket som helst navn til den kolonne, der identificerer HR-datatypen, fordi du skal tilknytte navnet på kolonnen i CSV-filen som den kolonne, der identificerer HR-datatypen, når du konfigurerer forbindelsen i trin 3. Du kan også tilknytte de værdier, der bruges til datatypekolonnen, når du konfigurerer forbindelsen.

### <a name="adding-the-hrscenario-column-to-a-csv-file-that-contains-a-single-data-type"></a>Tilføjelse af kolonnen HRScenario i en CSV-fil, der indeholder en enkelt datatype

Baseret på din organisations HR-systemer, og hvordan du eksporterer HR-data til CSV-filer, kan det være nødt til at oprette flere CSV-filer, der indeholder en enkelt HR-datatype. I dette tilfælde kan du stadig oprette en enkelt HR-forbindelse til at importere data fra forskellige CSV-filer. For at gøre dette skal du bare føje en HRScenario-kolonne til CSV-filen og angive HR-datatypen. Derefter kan du køre scriptet for hver CSV-fil, men bruge det samme job-id for forbindelsen. Se [Trin 4](#step-4-run-the-sample-script-to-upload-your-hr-data).

## <a name="step-2-create-an-app-in-azure-active-directory"></a>Trin 2: Opret en app i Azure Active Directory

Næste trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den HR-forbindelse, du opretter i trin 3. Oprettelse af denne app giver Azure AD tilladelse til at godkende HR-forbindelsen, når den kører og forsøger at få adgang til din organisation. Denne app bruges også til at godkende det script, du kører i trin 4, til at overføre dine HR-data til Microsoft-skyen. Sørg for at gemme følgende oplysninger under oprettelsen af denne Azure AD-app. Disse værdier skal bruges i trin 3 og trin 4.

- Azure AD-program-id (også kaldet *app-id eller* *klient-id*)

- Azure AD programhemmelighed (også kaldet *klienthemmelighed*)

- Lejer-id (også kaldet *katalog-id*)

Du kan finde en trinvis vejledning til oprettelse af en app i Azure AD under [Registrer et program Microsoft-identitetsplatform](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-3-create-the-hr-connector"></a>Trin 3: Opret HR-forbindelsen

Næste trin er at oprette en HR-forbindelse i Microsoft 365 Overholdelsescenter. Når du har kørt scriptet i trin 4, vil den HR-forbindelse, du opretter, ingest the HR-data fra CSV-filen til din Microsoft 365 organisation. Før du opretter en forbindelse, skal du sørge for, at du har en liste over HR-scenarierne og de tilsvarende CSV-kolonnenavne for hver enkelt. Du skal knytte de data, der kræves for hvert scenarie, til de faktiske kolonnenavne i CSV-filen, når du konfigurerer forbindelsen. Du kan også overføre en CSV-eksempelfil, når du konfigurerer forbindelsen, så hjælper guiden dig med at knytte kolonnenavnet til de nødvendige datatyper.

Når du har udført dette trin, skal du sørge for at kopiere det job-id, der genereres, når du opretter forbindelsen. Du skal bruge job-id'et, når du kører scriptet.

1. Gå til Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataforbindelser**</a>.

2. På siden **Dataforbindelser skal** du klikke **på HR (preview)**.

3. På **siden HR (preview)** skal du klikke **på Tilføj forbindelse**.

4. Gør følgende **på siden Konfigurer** forbindelsen, og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 2.

   2. Skriv et navn til HR-forbindelsen.

5. På siden HR-scenarier skal du vælge et eller flere HR-scenarier, du vil importere data for, og derefter klikke på **Næste**.

   ![Vælg et eller flere HR-scenarier.](../media/HRConnectorScenarios.png)

6. På siden filtilknytningsmetode skal du vælge en filtype, hvis det er nødvendigt, og derefter vælge en af følgende indstillinger og derefter klikke på **Næste**.

   - **Upload en eksempelfil**. Hvis du vælger denne indstilling, skal du **klikke Upload en eksempelfil** for at overføre den CSV-fil, du forberedte i trin 1. Denne indstilling giver dig mulighed for hurtigt at vælge kolonnenavne i csv-filen på en rulleliste for at knytte dem til datatyperne for de HR-scenarier, du tidligere har valgt.

   ELLER

   - **Angiv tilknytningsdetaljerne manuelt**. Hvis du vælger denne indstilling, skal du skrive navnet på kolonnerne i CSV-filen for at knytte dem til datatyperne for de HR-scenarier, du tidligere har valgt.

7. På siden Med tilknytning af fil skal du gøre et af følgende, afhængigt af om du har uploadet en CSV-eksempelfil, og om du konfigurerer forbindelsen for et enkelt HR-scenarie eller for flere scenarier. Hvis du har overført en eksempelfil, behøver du ikke at skrive kolonnenavnene. Du vælger dem på en rulleliste.

    - Hvis du valgte et enkelt HR-scenarie i forrige trin, skal du skrive kolonneoverskriftsnavnene (også kaldet *parametre) fra* den CSV-fil, du oprettede i trin 1, i hvert af de relevante felter. De kolonnenavne, du indtaster, tager ikke hensyn til store og små bogstaver, men sørg for at medtage mellemrum, hvis kolonnenavnene i CSV-filen indeholder mellemrum. Som beskrevet tidligere skal de navne, du skriver i disse felter, svare til parameternavnene i CSV-filen. Følgende skærmbillede viser f.eks. parameternavnene fra CSV-eksempelfilen for medarbejderens hr-scenario vist i trin 1.

    - Hvis du har valgt flere datatyper i trin ovenfor, skal du angive kolonnenavnet for identifikatoren, som identificerer HR-datatypen i CSV-filen. Når du har indtastet kolonnenavnet i id, skal du skrive den værdi, der identificerer denne HR-datatype, og skrive kolonneoverskriftsnavnene for de valgte datatyper fra csv-filen/de CSV-filer, du oprettede i trin 1, i hvert af de relevante felter for hver valgt datatype. Som tidligere nævnt skal de navne, du skriver i disse felter, svare til kolonnenavnene i CSV-filen.

8. Gennemgå dine **indstillinger på** siden Gennemse, og klik derefter på **Udfør for** at oprette forbindelsen.

   Der vises en statusside, der bekræfter, at forbindelsen blev oprettet. Denne side indeholder to vigtige ting, som du skal bruge for at fuldføre næste trin for at køre eksempelscriptet til overførsel af dine HR-data.

   ![Siden Gennemse med job-id og link til github for eksempelscript.](../media/HRConnector_Confirmation.png)

   1. **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere det fra denne side eller fra pop op-siden for forbindelser.

   2. **Link til eksempelscript.** Klik på **linket her** for at gå til webstedet GitHub for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Alternativt kan du bogmærke destinationen eller kopiere URL-adressen, så du kan få adgang til den igen, når du kører scriptet. Dette link er også tilgængeligt på pop op-siden med forbindelser.

9. Klik **på Udført**.

   Den nye forbindelse vises på listen under **fanen** Forbindelser.

10. Klik på den HR-forbindelse, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om forbindelsen.

   ![Pop op-side for ny HR-forbindelse.](../media/HRConnectorWizard7.png)

Hvis du ikke allerede har gjort det, kan du kopiere værdierne for job-id'et for **Azure App** **og Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller hente det ved hjælp af linket i næste trin).

Du kan også klikke på **Rediger for** at ændre Azure App-id'et eller kolonneoverskriftsnavnene, du har defineret på **siden Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine HR-data

Det sidste trin i konfigurationen af en HR-forbindelse er at køre et eksempelscript, der overfører HR-dataene i CSV-filen (som du oprettede i trin 1) til Microsoft-skyen. Specifikt overfører scriptet dataene til HR-forbindelsen. Når du har kørt scriptet, importerer den HR-forbindelse, du oprettede i trin 3, HR-dataene til din Microsoft 365-organisation, hvor de kan tilgås af andre overholdelsesværktøjer, f.eks. Insider-risikostyringsløsningen. Når du har kørt scriptet, bør du overveje at planlægge en opgave til at køre den automatisk dagligt, så de nyeste data om medarbejders afslutning uploades til Microsoft-skyen. Se [Planlæg scriptet til at køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

1. Gå til det vindue, du slap, fra det forrige trin for at få adgang GitHub websted med eksempelscriptet. Alternativt kan du åbne webstedet med bogmærket eller bruge den URL-adresse, du kopierede. Du kan også få adgang til [scriptet her](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Klik på **knappen Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjer i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af `.ps1`; for eksempel `HRConnector.ps1`. Alternativt kan du bruge GitHub filnavnet for scriptet, som er `upload_termination_records.ps1`.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at uploade HR-dataene i CSV-filen til Microsoft-skyen; for eksempel:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
    ```

   I følgende tabel beskrives de parametre, der skal bruges med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

   | Parameter | Beskrivelse |
   |:-----|:-----|:-----|
   |`tenantId`|Dette er id'et for din Microsoft 365 organisation, du fik i trin 2. Du kan også hente lejer-id'et for din organisation på **oversigtsbladet** i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |`appId` |Dette er Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 2. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation. | 
   |`appSecret`|Dette er Azure AD-programhemmelighed for den app, du oprettede i Azure AD i trin 2. Dette bruges også til godkendelse.|
   |`jobId`|Dette er job-id'et for den HR-forbindelse, du oprettede i trin 3. Dette bruges til at knytte de HR-data, der uploades til Microsoft-skyen, til HR-forbindelsen.|
   |`filePath`|Dette er filstien til filen (gemt på det samme system som scriptet), som du oprettede i trin 1. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
   |||

   Her er et eksempel på syntaksen for hr-forbindelsesscriptet, der bruger faktiske værdier for hver parameter:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Hvis overførslen lykkes, viser scriptet meddelelsen **Upload vellykket**.

   > [!NOTE]
   > Hvis du har problemer med at køre den forrige kommando på grund af [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) eksekveringspolitikker, skal du se Om eksekveringspolitikker og [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) for at få en vejledning til at angive eksekveringspolitikker.

## <a name="step-5-monitor-the-hr-connector"></a>Trin 5: Overvåg HR-forbindelsen

Når du har oprettet HR-forbindelsen og kørt scriptet til at overføre dine HR-data, kan du få vist forbindelsen og overføre status Microsoft 365 Overholdelsescenter. Hvis du planlægger at køre scriptet automatisk med jævne mellemrum, kan du også få vist den aktuelle status efter sidste gang, scriptet kørte.

1. Gå til Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataforbindelser**</a>.

2. Klik på **fanen Forbindelser,** og vælg derefter HR-forbindelsen for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

   ![POP-side med pop op-sider for HR-forbindelser med egenskaber og status.](../media/HRConnectorFlyout1.png)

3. Under **Status** skal du klikke **på linket Download** log for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om hver gang scriptet kører og uploader dataene fra CSV-filen til Microsoft-skyen. 

   ![HR-forbindelseslogfilen viser talrækker fra CSV-fil, der blev overført.](../media/HRConnectorLogFile.png)

   Feltet `RecordsSaved` angiver antallet af rækker i csv-filen, der er overført. Hvis CSV-filen f.eks. indeholder fire rækker, `RecordsSaved` er værdien af felterne 4, hvis scriptet har overført alle rækkerne i CSV-filen.

Hvis du ikke har kørt scriptet i trin 4, vises et link til at downloade scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene for at køre scriptet.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg scriptet til at køre automatisk

For at sikre at de nyeste HR-data fra din organisation er tilgængelige for værktøjer som insider-risikostyringsløsningen, anbefaler vi, at du planlægger scriptet til at køre automatisk med tilbagevendende mellemrum, f.eks. en gang om dagen. Dette kræver også, at du opdaterer HR-dataene i CSV-filen på en lignende (hvis ikke den samme) tidsplan, så den indeholder de seneste oplysninger om medarbejdere, der forlader organisationen. Målet er at uploade de mest aktuelle HR-data, så HR-forbindelsen kan gøre dem tilgængelige for Insider Risk Management-løsningen.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen Start på din lokale Windows **skriv** derefter **Opgavestyring**.

2. Klik på **appen Opgavestyring** for at åbne den.

3. Klik på **Opret** opgave i **sektionen Handlinger**.

4. Skriv et **beskrivende** navn til den planlagte opgave under fanen Generelt. Eksempelvis **HR-forbindelsesscript**. Du kan også tilføje en valgfri beskrivelse.

5. Gør **følgende under** Sikkerhedsindstillinger:

   1. Find ud af, om scriptet kun skal køres, når du er logget på computeren, eller om du skal køre det, når du er logget på.

   1. Sørg for, at **afkrydsningsfeltet Kør med de højeste** rettigheder er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

   1. Under **Indstillinger** skal du **vælge indstillingen** Dagligt og derefter vælge en dato og et klokkeslæt for at køre scriptet for første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

   1. Sørg **for, at** afkrydsningsfeltet **Aktiveret er markeret** under Avancerede indstillinger.

   1. Klik **på OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger for at oprette en ny planlagt opgave for HR-forbindelsesscriptet.](../media/HRConnectorScheduleTask1.png)

   1. Sørg for **,** at Start et program er markeret **på rullelisten** Handling.

   1. I feltet **Program/script** skal du klikke på Gennemse og gå til følgende placering og vælge den, så stien vises i feltet: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

   1. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. For eksempel `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. F.eks. `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Klik **på OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK i** vinduet Opret opgave **for** at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i biblioteket Opgavestyring.

   ![Den nye opgave vises i biblioteket Opgavestyring.](../media/HRConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden på den tilsvarende HR-forbindelse i overholdelsescenteret.

## <a name="existing-hr-connectors"></a>Eksisterende HR-forbindelser

Den 13. december 2021 udsendte vi scenariet med medarbejderprofildata for HR-forbindelser. Hvis du har oprettet en HR-forbindelse før denne dato, overfører vi de eksisterende forekomster eller din organisations HR-forbindelser, så dine HR-data fortsat importeres til Microsoft-skyen. Du behøver ikke at gøre noget for at bevare denne funktionalitet. Du kan fortsætte med at bruge disse forbindelser uden afbrydelse.

Hvis du vil implementere datascenariet for medarbejderprofilen, skal du oprette en ny HR-forbindelse og konfigurere den efter behov. Når du har oprettet en ny HR-forbindelse, skal du køre scriptet med job-id'et for den nye forbindelse og CSV-filer med [medarbejderprofildata](#csv-file-for-employee-profile-data-preview) , der er beskrevet tidligere i denne artikel.
