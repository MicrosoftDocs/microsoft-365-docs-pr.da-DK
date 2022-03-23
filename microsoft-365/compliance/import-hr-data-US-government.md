---
title: Konfigurer en forbindelse til at importere HR-data til den amerikanske regerings sky
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
description: Administratorer i den amerikanske regerings sky kan konfigurere en dataforbindelse til at importere medarbejderdata fra organisationens HR-system (HUMAN) for at Microsoft 365. Dette giver dig mulighed for at bruge HR-data i insider-risikostyringspolitikker til at hjælpe dig med at registrere aktivitet fra bestemte brugere, der kan udgøre en intern trussel mod din organisation.
ms.openlocfilehash: c342499c2ea18f4d6ad2f737db3d1dc32bb9fb3f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588453"
---
# <a name="set-up-a-connector-to-import-hr-data-in-us-government"></a>Konfigurer en forbindelse til at importere HR-data i den amerikanske stat

Du kan konfigurere en dataforbindelse i Microsoft 365 Overholdelsescenter at importere HR-data (HUMAN Resources) til din amerikanske myndigheds organisation. HR-relaterede data omfatter den dato, hvor en medarbejder indsendte sine oplysninger samt datoen for medarbejderens sidste dag. Disse HR-data kan derefter bruges af Microsoft-beskyttelse af oplysninger-løsninger, f.eks [Insider-risikostyringsløsningen](insider-risk-management.md), som hjælper med at beskytte din organisation mod ondsindet aktivitet eller datatyveri inden for organisationen. Konfiguration af en HR-forbindelse består i at oprette en app i Azure Active Directory, der bruges til godkendelse af forbindelse, oprettelse af CSV-tilknytningsfiler, der indeholder dine HR-data, oprettelse af en dataforbindelse i overholdelsescenteret og derefter kørsel af et script (på planlagt basis), som ingests hr-dataene i CSV-filen til Microsoft-skyen. Derefter bruges dataforbindelsesværktøjet af Insider-risikostyringsværktøjet til at få adgang til de HR-data, der blev importeret til din Microsoft 365 amerikanske regerings organisation.

## <a name="before-you-begin"></a>Før du begynder

- Den bruger, der opretter HR-forbindelsen i trin 3, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Administratorrollen Dataforbindelse understøttes i øjeblikket ikke i us Government GCC High- og DoD-miljøer. Den bruger, der opretter HR-forbindelsen i GCC High- og DoD-miljøer, skal derfor have tildelt rollen Postkasse Import Eksport i Exchange Online. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration i Exchange Online. Eller du kan oprette en ny rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje de relevante brugere som medlemmer. Du kan finde flere oplysninger i [afsnittene](/Exchange/permissions-exo/role-groups#create-role-groups) Opret [](/Exchange/permissions-exo/role-groups#modify-role-groups) rollegrupper eller Rediger rollegrupper i artiklen "Administrer rollegrupper Exchange Online".

- Du skal bestemme, hvordan du henter eller eksporterer data fra din organisations HR-system (med jævne mellemrum) og føjer dem til CSV-filen, der er beskrevet i trin 2. Det script, du kører i trin 4, overfører HR-dataene i CSV-filen til Microsoft-skyen.

- Eksempelscriptet, som du kører i trin 4, overfører HR-data til Microsoft-skyen, så de kan bruges af andre Microsoft-værktøjer, f.eks. Insider Risk Management-løsningen. Dette eksempelscript understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den HR-forbindelse, du opretter i trin 3. Oprettelse af denne app giver Azure AD tilladelse til at godkende HR-forbindelsen, når den kører og forsøger at få adgang til din organisation. Denne app bruges også til at godkende det script, du kører i trin 4, til at overføre dine HR-data til Microsoft-skyen. Sørg for at gemme følgende oplysninger under oprettelsen af denne Azure AD-app. Disse værdier skal bruges i senere trin.

- Azure AD-program-id (også kaldet *app-id eller* *klient-id*)

- Azure AD programhemmelighed (også kaldet *klienthemmelighed*)

- Lejer-id (også kaldet *katalog-id*)

Du kan finde en trinvis vejledning til oprettelse af en app i Azure AD under [Registrer et program Microsoft-identitetsplatform](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-csv-file-with-your-hr-data"></a>Trin 2: Forbered en CSV-fil med dine HR-data

Næste trin er at oprette en CSV-fil, der indeholder oplysninger om medarbejdere, der har forladt organisationen. Som beskrevet i afsnittet Før du går i gang skal du afgøre, hvordan denne CSV-fil skal genereres ud fra organisationens HR-system. I følgende eksempel vises en færdig CSV-fil (åbnet i Note Pad), der indeholder de tre påkrævede parametre (kolonner). Det er meget nemmere at redigere CSV-filen i Microsoft Excel.

```text
EmailAddress,TerminationDate,LastWorkingDate
sarad@contoso.com,2019-04-23T15:18:02.4675041+05:30,2019-04-29T15:18:02.4675041+05:30
pilarp@contoso.com,2019-04-24T09:15:49Z,2019-04-29T15:18:02.7117540
```

I den første række, eller kolonneoverskriften, i CSV-filen vises de påkrævede kolonnenavne. Det navn, der bruges i hver kolonneoverskrift, er op til dig (dem i det forrige eksempel er forslag). Men de samme kolonnenavne, du bruger i CSV-filen, skal angives, når du opretter HR-forbindelsen i trin 3. Medtag ikke mellemrum i kolonnenavnene.

I følgende tabel beskrives hver kolonne i CSV-filen:

| Kolonnenavn | Beskrivelse |
|:-----|:-----|
| **Mailadresse** <br/> |Angiver mailadressen på den opsagte medarbejder.|
| **TerminationDate** <br/> |Angiver den dato, hvor personens ansættelse officielt blev afsluttet i din organisation. Det kan f.eks. være den dato, hvor medarbejderen har givet besked om at forlade organisationen. Denne dato kan være forskellig fra datoen for personens sidste arbejdsdag. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|**LastWorkingDate**|Angiver den sidste dags arbejde for den opsagte medarbejder. Brug følgende datoformat: `yyyy-mm-ddThh:mm:ss.nnnnnn+|-hh:mm`, som er [ISO 8601-dato- og klokkeslætsformatet](https://www.iso.org/iso-8601-date-and-time-format.html).|
|||

Når du har oprettet CSV-filen med de nødvendige HR-data, skal du gemme den på det samme system som det script, du kører i trin 4. Sørg for at implementere en opdateringsstrategi, så CSV-filen altid indeholder de mest aktuelle oplysninger. Når du gør det, sikrer du, at uanset hvad du kører scriptet, uploades de nyeste data om medarbejders afslutning til Microsoft-skyen.

## <a name="step-3-create-the-hr-connector"></a>Trin 3: Opret HR-forbindelsen

Næste trin er at oprette en HR-forbindelse i Microsoft 365 Overholdelsescenter. Når du har kørt scriptet i trin 4, vil den HR-forbindelse, du opretter, ingest the HR-data fra CSV-filen til din Microsoft 365 organisation. I dette trin skal du sørge for at kopiere det job-id, der genereres, når du opretter forbindelsen. Du skal bruge job-id'et, når du kører scriptet.

1. Gå til siden Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**siden Dataforbindelser**</a>.

2. På siden **Dataforbindelser under** HR skal **du klikke** på **Vis**.

3. Klik på **Tilføj** forbindelse på **hr-siden**.

4. Gør følgende **på siden Legitimationsoplysninger** for godkendelse, og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 1.

   1. Skriv et navn til HR-forbindelsen.

5. På siden **Filtilknytning** skal du skrive navnene på de tre kolonneoverskrifter (også kaldet *parametre) fra* CSV-filen, du oprettede i trin 2, i hvert af de relevante felter. Der er ikke store og små bogstaver i navnene. Som tidligere nævnt skal de navne, du skriver i disse felter, svare til parameternavnene i CSV-filen. Følgende skærmbillede viser f.eks. parameternavnene fra eksemplet i CSV-eksempelfilen vist i trin 2.

   ![Kolonneoverskriftsnavne svarer til dem i CSV-filen.](../media/HRConnectorWizard3.png)

6. Gennemgå dine **indstillinger på** siden Gennemse, og klik derefter på **Udfør for** at oprette forbindelsen.

   Der vises en statusside, der bekræfter, at forbindelsen blev oprettet. Denne side indeholder to vigtige ting, som du skal bruge for at fuldføre næste trin for at køre eksempelscriptet til overførsel af dine HR-data.

   ![Siden Gennemse med job-id og link til github for eksempelscript.](../media/HRConnector_Confirmation.png)

   1. **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere det fra denne side eller fra pop op-siden for forbindelser.
   
   1. **Link til eksempelscript.** Klik på **linket her** for at gå til webstedet GitHub for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Alternativt kan du bogmærke destinationen eller kopiere URL-adressen, så du kan få adgang til den igen i trin 4. Dette link er også tilgængeligt på pop op-siden med forbindelser.

7. Klik **på Udført**.

   Den nye forbindelse vises på listen under **fanen** Forbindelser. 

8. Klik på den HR-forbindelse, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om forbindelsen.

   ![Pop op-side for ny HR-forbindelse.](../media/HRConnectorWizard7.png)

   Hvis du ikke allerede har gjort det, kan du kopiere værdierne for job-id'et for **Azure App** **og Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller hente det ved hjælp af linket i næste trin).

   Du kan også klikke på **Rediger for** at ændre Azure App-id'et eller kolonneoverskriftsnavnene, du har defineret på **siden Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-hr-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine HR-data

Det sidste trin i konfigurationen af en HR-forbindelse er at køre et eksempelscript, der overfører HR-dataene i CSV-filen (som du oprettede i trin 2) til Microsoft-skyen. Specifikt overfører scriptet dataene til HR-forbindelsen. Når du har kørt scriptet, importerer den HR-forbindelse, du oprettede i trin 3, HR-dataene til din Microsoft 365-organisation, hvor de kan tilgås af andre overholdelsesværktøjer, f.eks. Insider-risikostyringsløsningen. Når du har kørt scriptet, bør du overveje at planlægge en opgave til at køre den automatisk dagligt, så de nyeste data om medarbejders afslutning uploades til Microsoft-skyen. Se [Planlæg scriptet til at køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

1. Gå til det vindue, du slap, fra det forrige trin for at få adgang GitHub websted med eksempelscriptet. Alternativt kan du åbne webstedet med bogmærket eller bruge den URL-adresse, du kopierede.

2. Klik på **knappen Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjer i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af `.ps1`; for eksempel `HRConnector.ps1`.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at uploade HR-dataene i CSV-filen til Microsoft-skyen; for eksempel:

    ```powershell
    .\HRConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -csvFilePath '<csvFilePath>'
    ```

   I følgende tabel beskrives de parametre, der skal bruges med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

   | Parameter | Beskrivelse |
   |:-----|:-----|:-----|
   |`tenantId`|Id'et for din Microsoft 365, du fik i trin 1. Du kan også hente lejer-id'et for din organisation på **oversigtsbladet** i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |`appId` |Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation. |
   |`appSecret`|Azure AD-programhemmelighed for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
   |`jobId`|Job-id'et for den HR-forbindelse, du oprettede i trin 3. Dette bruges til at knytte de HR-data, der uploades til Microsoft-skyen, til HR-forbindelsen.|
   |`csvFilePath`|Filstien til CSV-filen (gemt på det samme system som scriptet), som du oprettede i trin 2. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
   |||
   
   Her er et eksempel på syntaksen for hr-forbindelsesscriptet, der bruger faktiske værdier for hver parameter:

   ```powershell
    .\HRConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -csvFilePath 'C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv'
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

Hvis du ikke har kørt scriptet i trin 4, vises et link til at downloade scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene i trin 4 for at køre det.

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

   1. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. For eksempel `.\HRConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn"  -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -csvFilePath "C:\Users\contosoadmin\Desktop\Data\employee_termination_data.csv"`

   1. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. F.eks. `C:\Users\contosoadmin\Desktop\Scripts`.

   1. Klik **på OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK i** vinduet Opret opgave **for** at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i biblioteket Opgavestyring.

   ![Den nye opgave vises i biblioteket Opgavestyring.](../media/HRConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden på den tilsvarende HR-forbindelse i overholdelsescenteret.