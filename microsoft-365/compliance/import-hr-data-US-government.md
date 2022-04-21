---
title: Konfigurer en connector for at importere HR-data til US Government-cloudmiljøet
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
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorer i US Government-cloudmiljøet kan konfigurere en dataconnector til at importere medarbejderdata fra organisationens HR-system for at Microsoft 365. Dette giver dig mulighed for at bruge HR-data i politikker for styring af insiderrisiko for at hjælpe dig med at registrere aktiviteter fra bestemte brugere, der kan udgøre en intern trussel for din organisation.
ms.openlocfilehash: 3f3873830caea109cf09987a21791bb299a4bdaf
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000020"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Konfigurer en connector for at importere HR-data i US Government

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan konfigurere en dataconnector på Microsoft Purview-overholdelsesportalen for at importere HR-data til din US Government-organisation. HR-relaterede data omfatter den dato, hvor en medarbejder sendte sin fratræden og dato for medarbejderens sidste dag. Disse HR-data kan derefter bruges af Microsofts løsninger til beskyttelse af oplysninger, f.eks [. løsningen til styring af insiderrisiko](insider-risk-management.md), til at beskytte din organisation mod ondsindet aktivitet eller datatyveri i din organisation. Konfiguration af en HR-connector består i at oprette en app i Azure Active Directory, der bruges til godkendelse af connector, oprette en CSV-tilknytningsfil, der indeholder dine HR-data, oprette en dataconnector i Overholdelsescenter og derefter køre et script (efter en tidsplan), der overfører HR-dataene i CSV-filen til Microsoft-cloudmiljøet. Derefter bruges dataconnectoren af værktøjet til styring af insiderrisiko til at få adgang til de HR-data, der blev importeret til din Microsoft 365 US Government-organisation.

## <a name="before-you-begin"></a>Før du begynder

- Den bruger, der opretter HR-connectoren i trin 3, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Rollen dataconnectoradministrator understøttes i øjeblikket ikke i GCC High- og DoD-miljøer for US Government. Derfor skal den bruger, der opretter HR-connectoren i GCC High- og DoD-miljøer, tildeles rollen Importeksport af postkasse i Exchange Online. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration i Exchange Online. Du kan også oprette en ny rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje de relevante brugere som medlemmer. Du kan få flere oplysninger i afsnittene [Opret rollegrupper](/Exchange/permissions-exo/role-groups#create-role-groups) eller [Rediger rollegrupper](/Exchange/permissions-exo/role-groups#modify-role-groups) i artiklen "Administrer rollegrupper i Exchange Online".

- Du skal afgøre, hvordan du henter eller eksporterer dataene fra organisationens HR-system (regelmæssigt) og føjer dem til den CSV-fil, der er beskrevet i trin 2. Det script, du kører i trin 4, uploader HR-dataene i CSV-filen til Microsoft-cloudmiljøet.

- Det eksempelscript, du kører i trin 4, uploader HR-data til Microsoft-cloudmiljøet, så de kan bruges af andre Microsoft-værktøjer, f.eks. løsningen til styring af insiderrisiko. Dette eksempelscript understøttes ikke under noget Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den HR-connector, du opretter i trin 3. Når du opretter denne app, kan Azure AD godkende HR-connectoren, når den kører, og forsøger at få adgang til din organisation. Denne app bruges også til at godkende det script, du kører i trin 4, for at uploade dine HR-data til Microsoft-cloudmiljøet. Under oprettelsen af denne Azure AD-app skal du gemme følgende oplysninger. Disse værdier bruges i senere trin.

- Azure AD-program-id (også kaldet *app-id* eller *klient-id*)

- Azure AD-programhemmelighed (også kaldet *klienthemmeligheden*)

- Lejer-id (også kaldet *mappe-id*)

Du kan finde en trinvis vejledning til, hvordan du opretter en app i Azure AD, under [Registrer et program med Microsoft-identitetsplatformen](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Trin 2: Forbered en CSV-fil med dine HR-data

Det næste trin er at oprette en CSV-fil, der indeholder oplysninger om medarbejdere, der har forladt din organisation. Som forklaret i afsnittet Før du begynder, skal du bestemme, hvordan du genererer denne CSV-fil ud fra din organisations HR-system. I følgende eksempel vises en fuldført CSV-fil (åbnet i Noteblok), der indeholder de tre påkrævede parametre (kolonner). Det er meget nemmere at redigere CSV-filen i Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

I den første række eller kolonneoverskrift i CSV-filen vises de påkrævede kolonnenavne. Det navn, der bruges i hver kolonneoverskrift, er op til dig (dem i det forrige eksempel er forslag). De samme kolonnenavne, du bruger i CSV-filen, *skal* dog angives, når du opretter HR-connectoren i Trin 3. Medtag ikke mellemrum i kolonnenavnene.

I følgende tabel beskrives hver kolonne i CSV-filen:

| Kolonnenavn | Beskrivelse |
|:-----|:-----|
| **Emailaddress** <br/> |Angiver mailadressen på den fratrådte medarbejder.|
| **Slutdato** <br/> |Angiver den dato, hvor personens ansættelse officielt blev afsluttet i organisationen. Dette kan f.eks. være den dato, hvor medarbejderen gav besked om at forlade din organisation. Denne dato kan være forskellig fra datoen for personens sidste arbejdsdag. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**Sidstearbejdsdato**|Angiver den sidste arbejdsdag for den fratrådte medarbejder. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Når du har oprettet CSV-filen med de påkrævede HR-data, skal du gemme dem på det samme system som det script, du kører i trin 4. Sørg for at implementere en opdateringsstrategi, så CSV-filen altid indeholder de mest aktuelle oplysninger. Hvis du gør det, sikrer du, at de mest aktuelle data om medarbejderes opsigelse uploades til Microsoft-cloudmiljøet, uanset hvad du kører scriptet.

## <a name="step-3-create-the-hr-connector"></a>Trin 3: Opret HR-connectoren

Det næste trin er at oprette en HR-connector på overholdelsesportalen. Når du har kørt scriptet i trin 4, overfører den HR-connector, du opretter, HR-dataene fra CSV-filen til din Microsoft 365 organisation. I dette trin skal du sørge for at kopiere det job-id, der genereres, når du opretter connectoren. Du skal bruge job-id'et, når du kører scriptet.

1. Gå til overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">siden **Dataconnectors**</a>.

2. Klik på **Vis** på siden **Dataconnectors** under **HR**.

3. Klik på **Tilføj connector** på siden **HR**.

4. Gør følgende på siden **Legitimationsoplysninger til godkendelse** , og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 1.

   1. Skriv et navn til HR-connectoren.

5. På siden **Filtilknytning** skal du skrive navnene på de tre kolonneoverskrifter (også kaldet *parametre*) fra den CSV-fil, du oprettede i trin 2, i hver af de relevante felter. Der skelnes ikke mellem store og små bogstaver i navnene. Som tidligere forklaret skal de navne, du skriver i disse felter, stemme overens med parameternavnene i CSV-filen. Følgende skærmbillede viser f.eks. parameternavnene fra eksemplet i CSV-eksempelfilen, der vises i trin 2.

   ![Kolonneoverskriftsnavnene stemmer overens med navnene i CSV-filen.](../media/HRConnectorWizard3.png)

6. Gennemse dine indstillinger på siden **Gennemse** , og klik derefter på **Udfør** for at oprette connectoren.

   Der vises en statusside, der bekræfter, at connectoren blev oprettet. Denne side indeholder to vigtige ting, som du skal udføre i næste trin for at køre eksempelscriptet for at uploade dine HR-data.

   ![Gennemse siden med job-id og link til GitHub for eksempelscript.](../media/HRConnector_Confirmation.png)

   1. **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere den fra denne side eller fra connector-pop op-siden.
   
   1. **Link til eksempelscript.** Klik på **linket her** for at gå til GitHub-webstedet for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Du kan også angive et bogmærke for destinationen eller kopiere URL-adressen, så du kan få adgang til den igen i trin 4. Dette link er også tilgængeligt på connector-pop op-siden.

7. Klik på **Udført**.

   Den nye connector vises på listen under fanen **Forbindelser** . 

8. Klik på den HR-connector, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om connectoren.

   ![Pop op-side for ny HR-connector.](../media/HRConnectorWizard7.png)

   Hvis du ikke allerede har gjort det, kan du kopiere værdierne for **job-id'et for Azure App ID** og **Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller downloade det ved hjælp af linket i næste trin).

   Du kan også klikke på **Rediger** for at ændre Det Azure App-id eller de kolonneoverskrifter, du har defineret på siden **Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine HR-data

Det sidste trin i konfiguration af en HR-connector er at køre et eksempelscript, der uploader HR-dataene i CSV-filen (som du oprettede i trin 2) til Microsoft-cloudmiljøet. Scriptet uploader specifikt dataene til HR-connectoren. Når du har kørt scriptet, importerer den HR-connector, du oprettede i trin 3, HR-dataene til din Microsoft 365 organisation, hvor andre værktøjer til overholdelse af angivne standarder kan få adgang til dem, f.eks. Insider Risk Management-løsningen. Når du har kørt scriptet, kan du overveje at planlægge en opgave for at køre den automatisk dagligt, så de mest aktuelle data om medarbejderafslutning uploades til Microsoft-cloudmiljøet. Se [Planlæg, at scriptet skal køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

1. Gå til det vindue, du lod åbne fra det forrige trin, for at få adgang til GitHub-webstedet med eksempelscriptet. Du kan også åbne webstedet med bogmærker eller bruge den URL-adresse, du kopierede.

2. Klik på knappen **Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjerne i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell-scriptfil ved hjælp af et filnavnssuffiks af `.ps1`, f.eks `HRConnector.ps1`. .

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at overføre HR-dataene i CSV-filen til Microsoft-cloudmiljøet. f.eks.:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   I følgende tabel beskrives de parametre, der skal bruges sammen med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

   | Parameter | Beskrivelse |
   |:-----|:-----|:-----|
   |`tenantId`|Id'et for din Microsoft 365 organisation, som du fik i trin 1. Du kan også hente lejer-id'et for din organisation på bladet **Oversigt** i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |`appId` |Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation. |
   |`appSecret`|Azure AD-programhemmeligheden for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
   |`jobId`|Job-id'et for den HR-connector, du oprettede i trin 3. Dette bruges til at knytte de HR-data, der uploades til Microsoft-cloudmiljøet, til HR-connectoren.|
   |`csvFilePath`|Filstien til CSV-filen (gemt på det samme system som scriptet), som du oprettede i trin 2. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
   |||
   
   Her er et eksempel på syntaksen for HR-connectorscriptet, der bruger faktiske værdier for hver parameter:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
    ```

   Hvis overførslen lykkes, viser scriptet meddelelsen **Upload fuldført** .

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

Hvis du ikke har kørt scriptet i trin 4, vises der et link til download af scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene i Trin 4 for at køre det.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg, at scriptet kører automatisk

Hvis du vil sikre dig, at de nyeste HR-data fra din organisation er tilgængelige for værktøjer som insiderrisikostyringsløsningen, anbefaler vi, at du planlægger, at scriptet kører automatisk på tilbagevendende basis, f.eks. én gang om dagen. Dette kræver også, at du opdaterer HR-dataene i CSV-filen efter en lignende (hvis ikke den samme) tidsplan, så de indeholder de nyeste oplysninger om medarbejdere, der forlader din organisation. Målet er at uploade de mest aktuelle HR-data, så HR-connectoren kan gøre dem tilgængelige for insiderrisikostyringsløsningen.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen **Start** i Windows på den lokale computer, og skriv derefter **Opgavestyring**.

2. Klik på appen **Opgavestyring** for at åbne den.

3. Klik på **Opret opgave** i afsnittet **Handlinger**.

4. Skriv et beskrivende navn på den planlagte opgave under fanen **Generelt** . f.eks. **HR Connector Script**. Du kan også tilføje en valgfri beskrivelse.

5. Under **Sikkerhedsindstillinger** skal du gøre følgende:

   1. Find ud af, om du kun vil køre scriptet, når du er logget på computeren eller kører det, når du er logget på eller ej.
   
   1. Sørg for, at afkrydsningsfeltet **Kør med de højeste rettigheder** er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

   1. Under **Indstillinger** skal du vælge indstillingen **Dagligt** og derefter vælge en dato og et klokkeslæt for at køre scriptet for første gang. Scriptet kører hver dag på det samme angivne tidspunkt.
   
   1. Under **Avancerede indstillinger** skal du kontrollere, at afkrydsningsfeltet **Aktiveret** er markeret.
   
   1. Klik på **OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger til oprettelse af en ny planlagt opgave til HR-connectorscriptet.](../media/HRConnectorScheduleTask1.png)

   1. På rullelisten **Handling** skal du kontrollere, at **Start et program** er valgt.

   1. Klik på **Gennemse** i feltet **Program/script**, gå til følgende placering, og vælg den, så stien vises i feltet: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`.

   1. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. Det kan f.eks. `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. For eksempel `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Klik på **OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK** i vinduet **Opret opgave** for at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i opgavestyringsbiblioteket.

   ![Den nye opgave vises i opgavestyringsbiblioteket.](../media/HRConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt til at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden for den tilsvarende HR-connector i Overholdelsescenter.