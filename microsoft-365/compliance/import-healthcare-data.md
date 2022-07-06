---
title: Konfigurer en connector til import af generiske overvågningsdata til sundhedssektoren
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en dataconnector til at importere EHR-data (Electronic Healthcare Records) fra deres sundhedssystem til Microsoft 365. Dette giver dig mulighed for at bruge EHR-data i politikker for styring af insiderrisiko til at hjælpe dig med at registrere uautoriseret adgang til patientdata af dine medarbejdere.
ms.openlocfilehash: be5429ea1a5fb4e2e2be6a7029f2401fcbdab94e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641378"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Konfigurer en connector til import af ehr-overvågningsdata til sundhedssektoren (prøveversion)

Du kan konfigurere en dataconnector i Microsoft Purview-compliance-portal til at importere overvågningsdata for brugeraktivitet i organisationens EHR-system (Electronic Healthcare Records). Overvågningsdata fra dit ehr-system til sundhedssektoren omfatter data for hændelser, der er relateret til at få adgang til en patients sundhedsjournaler. Ehr-overvågningsdata til sundhedssektoren kan bruges af Microsoft [365-løsningen til styring af insiderrisiko](insider-risk-management.md) for at beskytte din organisation mod uautoriseret adgang til patientoplysninger.

Konfiguration af en Healthcare-connector består af følgende opgaver:

- Oprettelse af en app i Azure Active Directory (Azure AD) for at få adgang til et API-slutpunkt, der accepterer en tabulatorsepareret tekstfil, der indeholder ehr-overvågningsdata til sundhedssektoren.

- Oprettelse af en tekstfil med alle de påkrævede felter, som defineret i connectorskemaet.

- Oprettelse af en forekomst af healthcare-connectoren på overholdelsesportalen.

- Kørsel af et script til push af EHR-overvågningsdata for sundhedssektoren til API-slutpunktet.

- Du kan eventuelt planlægge, at scriptet køres automatisk for at importere overvågningsdataene.

## <a name="before-you-set-up-the-connector"></a>Før du konfigurerer connectoren

- Den bruger, der opretter healthcare-connectoren i trin 3, skal tildeles rollen Dataconnector Administration. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Data Connector Administration og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Du skal finde ud af, hvordan du henter eller eksporterer dataene fra organisationens EHR-system (dagligt) og opretter en tekstfil, der er beskrevet i trin 2. Det script, du kører i trin 4, overfører dataene i tekstfilen til API-slutpunktet.

- Det eksempelscript, du kører i trin 4, sender ehr-overvågningsdataene for sundhedssektoren fra tekstfilen til connector-API'en, så de kan bruges af løsningen til styring af insiderrisiko. Dette eksempelscript understøttes ikke under noget Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den Healthcare-connector, du opretter i trin 3. Oprettelse af denne app gør det muligt for Azure AD at godkende pushanmodningen for tekstfilen, der indeholder sundheds-EHR-overvågningsdata. Under oprettelsen af denne Azure AD app skal du gemme følgende oplysninger. Disse værdier bruges i senere trin.

- Azure AD program-id (også kaldet *app-id* eller *klient-id*)

- Azure AD programhemmelighed (også kaldet *klienthemmeligheden*)

- Lejer-id (også kaldet *mappe-id*)

Du kan finde en trinvis vejledning i, hvordan du opretter en app i Azure AD, under [Registrer et program med Microsoft-identitetsplatform](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>Trin 2: Forbered en tekstfil med ehr-overvågningsdata til sundhedssektoren

Næste trin er at oprette en tekstfil, der indeholder oplysninger om medarbejdernes adgang til patientjournaler i organisationens EHR-system til sundhed. Som tidligere forklaret, skal du finde ud af, hvordan du genererer denne tekstfil fra dit ehr-system til sundhedssektoren. Arbejdsprocessen for Healthcare-connectoren kræver en tekstfil med tabulatorseparerede værdier for at knytte disse data i tekstfilen til det påkrævede connectorskema. Det understøttede filformat er en kommafil (.csv), pipe-fil (.psv) eller tabulatorsepareret tekstfil (.tsv).

> [!NOTE]
> Den maksimale størrelse på den tekstfil, der indeholder overvågningsdataene, er 3 GB. Det maksimale antal rækker er 5 millioner. Sørg også for kun at inkludere de relevante overvågningsdata fra dit ehr-system til sundhedssektoren.

I følgende tabel vises de felter, der kræves for at aktivere insiderrisikostyringsscenarier. En delmængde af disse felter er obligatorisk. Disse felter er fremhævet med en stjerne (*). Hvis nogle af de obligatoriske felter mangler i tekstfilen, valideres filen ikke, og dataene i filen importeres ikke.

|Feltet|Kategori|
|:----|:----------|
| *Navn på oprettelsestidshændelse<br/>*<br/>Arbejdsstations-id<br/>Hændelsessektion<br/>Hændelseskategori |Disse felter bruges til at identificere adgangsaktivitetshændelser i dit ehr-system til sundhedssektoren.|
| Patient reg-id<br/>Patient fornavn *<br/>Patients mellemnavn <br/>Patient Efternavn* <br/>Patientadresselinje 1* <br/>Patientadresselinje 2<br/>Patientby* <br/>Postnummer til patient*  <br/>Patienttilstand <br/>Patientland <br/>Patientafdeling              | Disse felter bruges til at identificere patientprofiloplysninger.|
| Årsag til begrænset adgang*<br/> Kommentar med begrænset adgang | Disse felter bruges til at identificere adgang til begrænsede poster.|
| Mailadresse (UPN) eller SamAccountName*<br/>Brugernavn for medarbejder <br/> Medarbejder-id <br/> Medarbejderens efternavn <sup>1</sup> <br/> Medarbejderens fornavn <sup>1</sup> | Disse felter bruges til at identificere oplysninger om medarbejderprofil for adresse- og navnematchning, der kræves for at bestemme adgangen til poster af typen Family/Neighbor/Employee. |
|||

> [!NOTE] 
> <sup>1</sup> Dette felt er muligvis ikke tilgængeligt som standard i dit ehr-system til sundhedssektoren. Du skal konfigurere eksporten for at sikre, at tekstfilen indeholder dette felt.

## <a name="step-3-create-the-healthcare-connector"></a>Trin 3: Opret connectoren Healthcare

Det næste trin er at oprette en Healthcare-connector på overholdelsesportalen. Når du har kørt scriptet i trin 4, behandles og pushes den tekstfil, du oprettede i trin 2, til det API-slutpunkt, du konfigurerede i trin 1. I dette trin skal du sørge for at kopiere det JobId, der genereres, når du opretter connectoren. Du skal bruge JobId, når du kører scriptet.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Healthcare (prøveversion)** under fanen **Oversigt**.

3. På siden **Healthcare (prøveversion)** skal du klikke på **Tilføj connector**.

4. Acceptér servicebetingelserne.

5. Gør følgende på siden **Legitimationsoplysninger til godkendelse** , og klik derefter på **Næste**:

    1. Skriv eller indsæt Azure AD program-id for den Azure-app, du oprettede i trin 1.

    2. Skriv et navn til sundhedsconnectoren.

6. Vælg en af følgende indstillinger på siden **Filtilknytningsmetode** , og klik derefter på **Næste**.

   - **Upload en eksempelfil**. Hvis du vælger denne indstilling, skal du klikke på **Upload eksempelfil** for at uploade den fil, du forberedte i trin 2. Denne indstilling giver dig mulighed for hurtigt at vælge kolonnenavne i tekstfilen på en rulleliste for at knytte kolonnerne til det påkrævede skema for healthcare-connectoren. 

    Eller

   - **Angiv tilknytningsoplysningerne manuelt**. Hvis du vælger denne indstilling, skal du skrive navnet på kolonnerne i tekstfilen for at knytte kolonnerne til det påkrævede skema for sundhedsconnectoren.

7. På siden **Oplysninger om filtilknytning** skal du gøre et af følgende, afhængigt af om du har uploadet en eksempelfil eller ej i det forrige trin:

   - Brug rullelisterne til at knytte kolonnerne fra eksempelfilen til hvert påkrævet felt for sundhedsconnectoren.

    Eller

   - For hvert felt skal du skrive kolonnenavnet fra den fil, du forberedte i trin 2, som svarer til feltet for sundhedsconnectoren.

8. Gennemse dine indstillinger på siden **Gennemse** , og klik derefter på **Udfør** for at oprette connectoren.

   Der vises en statusside, der bekræfter, at connectoren blev oprettet. Denne side indeholder to vigtige ting, som du skal udføre i næste trin for at køre eksempelscriptet for at uploade dine ehr-overvågningsdata til sundhedssektoren.

    - **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere den fra denne side eller fra connector-pop op-siden.

    - **Link til eksempelscript.** Klik på **linket her** for at gå til GitHub-webstedet for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Du kan også angive et bogmærke for destinationen eller kopiere URL-adressen, så du kan få adgang til den igen, når du kører scriptet. Dette link er også tilgængeligt på connector-pop op-siden.

9. Klik på **Udført**.

   Den nye connector vises på listen under fanen **Forbindelser** .

10. Klik på den Healthcare-connector, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om connectoren.

Hvis du ikke allerede har gjort det, kan du kopiere værdierne for **job-id'et for Azure App ID** og **Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller downloade det ved hjælp af linket i næste trin).

Du kan også klikke på **Rediger** for at ændre Det Azure App-id eller de kolonneoverskrifter, du har defineret på siden **Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine EHR-overvågningsdata for sundhedssektoren

Det sidste trin i forbindelse med konfiguration af en Healthcare-connector er at køre et eksempelscript, der uploader sundhedsjJJR-overvågningsdataene i tekstfilen (som du oprettede i trin 1) til Microsoft-cloudmiljøet. Scriptet uploader specifikt dataene til Healthcare-connectoren. Når du har kørt scriptet, importerer den Healthcare-connector, du oprettede i trin 3, sundheds-EHR-overvågningsdataene til din Microsoft 365-organisation, hvor andre værktøjer til overholdelse af angivne standarder kan få adgang til dem, f.eks. insiderrisikostyringsløsningen. Når du har kørt scriptet, kan du overveje at planlægge en opgave for at køre den automatisk dagligt, så de mest aktuelle data om medarbejderafslutning uploades til Microsoft-cloudmiljøet. Se [(valgfrit) Trin 6: Planlæg, at scriptet skal køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Som tidligere nævnt er den maksimale størrelse på den tekstfil, der indeholder overvågningsdataene, 3 GB. Det maksimale antal rækker er 5 millioner. Det script, du kører i dette trin, tager ca. 30-40 minutter at importere overvågningsdataene fra store tekstfiler. Derudover opdeler scriptet store tekstfiler i mindre blokke på 100.000 rækker og importerer derefter disse blokke sekventielt.

1. Gå til det vindue, du lod åbne fra det forrige trin, for at få adgang til GitHub-webstedet med eksempelscriptet. Du kan også åbne webstedet med bogmærker eller bruge den URL-adresse, du kopierede. Du kan også få adgang til scriptet [her](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Klik på knappen **Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjerne i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af `.ps1`, f.eks. `HealthcareConnector.ps1`.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at uploade overvågningsdataene for sundhedssektoren i tekstfilen til Microsoft Cloud. f.eks.:

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

I følgende tabel beskrives de parametre, der skal bruges sammen med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

|Parameter  |Beskrivelse|
|:----------|:----------|
|tenantId|Dette er id'et for din Microsoft 365-organisation, som du fik i trin 1. Du kan også hente lejer-id'et for din organisation på bladet **Oversigt** i Azure AD Administration. Dette bruges til at identificere din organisation.|
|Appid|Dette er det Azure AD program-id for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365-organisation.|
|appSecret|Dette er Azure AD programhemmeligheden for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
|job-id|Dette er job-id'et for den Healthcare-connector, du oprettede i trin 3. Dette bruges til at knytte sundheds-EHR-overvågningsdata, der uploades til Microsoft-cloudmiljøet, med healthcare-connectoren.|
|filePath|Dette er filstien til tekstfilen (gemt i det samme system som scriptet), som du oprettede i trin 2. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
|||

Her er et eksempel på syntaksen for connectorscriptet healthcare ved hjælp af faktiske værdier for hver parameter:

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Hvis overførslen lykkes, viser scriptet meddelelsen **Upload fuldført** .

> [!NOTE]
> Hvis du har problemer med at køre den forrige kommando på grund af kørselspolitikker, skal du se [Om kørselspolitikker](/powershell/module/microsoft.powershell.core/about/about_execution_policies) og [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) for at få vejledning til, hvordan du angiver kørselspolitikker.

## <a name="step-5-monitor-the-healthcare-connector"></a>Trin 5: Overvåg connectoren Healthcare

Når du har oprettet Healthcare-connectoren og pushoverføre dine EHR-overvågningsdata, kan du få vist connectoren og uploade status på overholdelsesportalen. Hvis du planlægger, at scriptet skal køre automatisk regelmæssigt, kan du også få vist den aktuelle status efter sidste gang scriptet kørte.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på fanen **Forbindelser,** og vælg derefter connectoren Healthcare for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

3. Under **Seneste import** skal du klikke på linket **Download log** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om, hver gang scriptet kører, og uploader dataene fra tekstfilen til Microsoft-cloudmiljøet.

    Feltet `RecordsSaved` angiver antallet af rækker i den tekstfil, der er overført. Hvis tekstfilen f.eks. indeholder fire rækker, er værdien af `RecordsSaved` felterne 4, hvis scriptet overførte alle rækkerne i tekstfilen.

Hvis du ikke har kørt scriptet i trin 4, vises der et link til download af scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene for at køre scriptet.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg, at scriptet kører automatisk

Hvis du vil sikre dig, at de nyeste overvågningsdata fra dit ehr-system til sundhedssektoren er tilgængelige for værktøjer som f.eks. løsningen til styring af insiderrisiko, anbefaler vi, at du planlægger, at scriptet kører automatisk dagligt. Dette kræver også, at du opdaterer EHR-overvågningsdataene i den samme tekstfil i en lignende (hvis ikke den samme) tidsplan, så den indeholder de nyeste oplysninger om dine medarbejderes adgangsaktiviteter til patientjournaler. Målet er at uploade de mest aktuelle overvågningsdata, så Healthcare-connectoren kan gøre dem tilgængelige for løsningen til styring af insiderrisiko.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen **Start** i Windows på den lokale computer, og skriv derefter **Opgavestyring**.

2. Klik på appen **Opgavestyring** for at åbne den.

3. Klik på **Opret opgave** i afsnittet **Handlinger**.

4. Skriv et beskrivende navn på den planlagte opgave under fanen **Generelt** . f.eks. **healthcare-connectorscript**. Du kan også tilføje en valgfri beskrivelse.

5. Under **Sikkerhedsindstillinger** skal du gøre følgende:

    1. Find ud af, om du kun vil køre scriptet, når du er logget på computeren eller kører det, når du er logget på eller ej.

    2. Sørg for, at afkrydsningsfeltet **Kør med de højeste rettigheder** er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

    1. Under **Indstillinger** skal du vælge indstillingen **Dagligt** og derefter vælge en dato og et klokkeslæt for at køre scriptet for første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

    2. Under **Avancerede indstillinger** skal du kontrollere, at afkrydsningsfeltet **Aktiveret** er markeret.

    3. Klik på **OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger til oprettelse af en ny planlagt opgave til scriptet for connectoren til sundhedssektoren.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. På rullelisten **Handling** skal du kontrollere, at **Start et program** er valgt.

    2. Klik på **Gennemse** i feltet **Program/script**, gå til følgende placering, og vælg den, så stien vises i feltet: C:.0.exe.

    3. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. Det kan f.eks. `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. F.eks. C:\Healthcare\audit.

    5. Klik på **OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK** i vinduet **Opret opgave** for at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i opgavestyringsbiblioteket.

   ![Den nye opgave for scriptet for connectoren til sundhedssektoren vises i biblioteket Opgavestyring.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt til at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også bekræfte, sidste gang scriptet kørte på pop op-siden for den tilsvarende Healthcare-connector i Overholdelsescenter.
