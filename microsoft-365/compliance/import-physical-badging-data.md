---
title: Konfigurer en connector for at importere data om fysisk badging
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
description: Administratorer kan konfigurere en dataconnector til at importere data fra organisationens fysiske badgingsystem til Microsoft 365. Dette giver dig mulighed for at bruge disse data i politikker for styring af insiderrisiko for at hjælpe dig med at registrere adgang til dine fysiske bygninger af bestemte brugere, der kan indikere en mulig intern trussel mod din organisation.
ms.openlocfilehash: 7b6161cfc8f712082303641f9da7345edf5e24df
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937933"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Konfigurer en connector for at importere data om dårlig fysisk skrivning (eksempelvisning)

Du kan konfigurere en dataconnector på Microsoft Purview-overholdelsesportalen for at importere fysiske badging-data, f.eks. medarbejderens rå fysiske adgangshændelser eller eventuelle fysiske adgangsalarmer, der genereres af din organisations badgingsystem. Eksempler på fysiske adgangspunkter er en post i en bygning eller en post i serverrum eller datacenter. Fysiske badging-data kan bruges af Microsoft 365 [løsning til styring af insiderrisiko](insider-risk-management.md) for at beskytte din organisation mod skadelig aktivitet eller datatyveri i din organisation.

Konfiguration af en fysisk dårlig connector består af følgende opgaver:

- Oprettelse af en app i Azure Active Directory (Azure AD) for at få adgang til et API-slutpunkt, der accepterer en JSON-nyttedata, der indeholder fysiske badging-data.

- Oprettelse af JSON-nyttedata med et skema, der er defineret af den fysiske forkerte dataconnector.

- Oprettelse af en fysisk dårlig dataconnector på overholdelsesportalen.

- Kørsel af et script for at overføre de fysiske badging-data til API-slutpunktet.

- Du kan eventuelt planlægge, at scriptet køres automatisk for at importere data om aktuelt fysisk dårligging.

## <a name="before-you-set-up-the-connector"></a>Før du konfigurerer connectoren

- Den bruger, der opretter den fysiske dårligging-connector i trin 3, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Rollen dataconnectoradministrator understøttes i øjeblikket ikke i US Government-GCC high- og dod-miljøer. Derfor skal den bruger, der opretter HR-connectoren i GCC high- og dod-miljøer, tildeles rollen Importér eksport af postkasse i Exchange Online. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration i Exchange Online. Du kan også oprette en ny rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje de relevante brugere som medlemmer. Du kan få flere oplysninger i afsnittene [Opret rollegrupper](/Exchange/permissions-exo/role-groups#create-role-groups) eller [Rediger rollegrupper](/Exchange/permissions-exo/role-groups#modify-role-groups) i artiklen "Administrer rollegrupper i Exchange Online".

- Du skal finde ud af, hvordan du henter eller eksporterer dataene fra organisationens fysiske badgingsystem (dagligt) og opretter en JSON-fil, der er beskrevet i trin 2. Det script, du kører i trin 4, overfører dataene i JSON-filen til API-slutpunktet.

- Det eksempelscript, du kører i trin 4, overfører de fysiske badging-data fra JSON-filen til connector-API'en, så det kan bruges af løsningen til styring af insiderrisiko. Dette eksempelscript understøttes ikke under noget Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres SOM IS uden nogen form for garanti. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, uden begrænsning, eventuelle stiltiende garantier for salgbarhed eller egnethed til et bestemt formål. Hele risikoen som følge af brugen eller ydeevnen af eksempelscriptet og dokumentationen forbliver hos dig. Under ingen omstændigheder må Microsoft, microsofts ophavsmænd eller andre, der er involveret i oprettelse, produktion eller levering af scripts, være ansvarlige for eventuelle skader overhovedet (herunder, uden begrænsning, skader for tab af forretningsoverskud, forretningsafbrydelser, tab af forretningsoplysninger eller andre økonomiske tab), der opstår som følge af brugen af eller manglende evne til at bruge eksempelscripts eller dokumentation,  selv om Microsoft er blevet underrettet om muligheden for sådanne skader.

- Denne connector er tilgængelig i GCC miljøer i Microsoft 365 US Government-cloudmiljøet. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365 infrastruktur og derfor ikke er omfattet af Microsofts forpligtelser til beskyttelse af personlige oplysninger og databeskyttelse. Microsoft gør ingen repræsentation af, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer indebærer, at disse tredjepartsprogrammer er FEDRAMP-kompatible.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den fysiske badging-connector, du opretter i trin 3. Når du opretter denne app, kan Azure AD godkende pushanmodningen for JSON-nyttedata, der indeholder fysiske badgingdata. Under oprettelsen af denne Azure AD-app skal du gemme følgende oplysninger. Disse værdier bruges i senere trin.

- Azure AD-program-id (også kaldet *app-id* eller *klient-id*)

- Azure AD-programhemmelighed (også kaldet *klienthemmeligheden*)

- Lejer-id (også kaldet *mappe-id*)

Du kan finde en trinvis vejledning i, hvordan du opretter en app i Azure AD, under [Registrer et program med Microsoft-identitetsplatform](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Trin 2: Forbered en JSON-fil med fysiske badging-data

Det næste trin er at oprette en JSON-fil, der indeholder oplysninger om medarbejdernes fysiske adgangsdata. Som forklaret i afsnittet før du begynder, skal du bestemme, hvordan du genererer denne JSON-fil ud fra din organisations fysiske badging-system.

JSON-filen skal overholde den skemadefinition, der kræves af connectoren. Her er beskrivelser af de påkrævede skemaegenskaber for JSON-filen:

|Ejendom|Beskrivelse|Datatype|
|---|---|---|
|Userid|En medarbejder kan have flere digitale identiteter på tværs af systemerne. Inputtet skal have Azure AD-id'et allerede løst af kildesystemet.|UPN eller mailadresse|
|Aktiv-id|Reference-id'et for det fysiske aktiv eller det fysiske adgangspunkt.|Alfanumerisk streng|
|Aktivnavn|Det fulde navn på det fysiske aktiv eller det fysiske adgangspunkt.|Alfanumerisk streng|
|EventTime|Tidsstemplet for adgang.|Dato og klokkeslæt i UTC-format|
|AccessStatus|Værdi af `Success` eller `Failed`|String|
|||

Her er et eksempel på en JSON-fil, der er i overensstemmelse med det påkrævede skema:

```json
[
    {
        "UserId":"sarad@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T01:57:49",
        "AccessStatus":"Failed"
    },
    {
        "UserId":"pilarp@contoso.com",
        "AssetId":"Mid-Sec-7",
        "AssetName":"Main Building 1st Floor Mid Section",
        "EventTime":"2019-07-04T02:57:49",
        "AccessStatus":"Success"
    }
]
```

Du kan også hente følgende skemadefinition for JSON-filen fra guiden, når du opretter den fysiske badging-connector i trin 3.

```text
{
   "title" : "Physical Badging Signals",
   "description" : "Access signals from physical badging systems",
   "DataType" : {
      "description" : "Identify what is the data type for input signal",
      "type" : "string",
   },
   "type" : "object",
   "properties": {
      "UserId" : {
         "description" : "Unique identifier AAD Id resolved by the source system",
         "type" : "string",
      },
      "AssetId": {
         "description" : "Unique ID of the physical asset/access point",
         "type" : "string",
      },
      "AssetName": {
         "description" : "friendly name of the physical asset/access point",
         "type" : "string",
      },
      "EventTime" : {
         "description" : "timestamp of access",
         "type" : "string",
      },
      "AccessStatus" : {
         "description" : "what was the status of access attempt - Success/Failed",
         "type" : "string",
      },
   }
   "required" : ["UserId", "AssetId", "EventTime" "AccessStatus"]
}
```

## <a name="step-3-create-the-physical-badging-connector"></a>Trin 3: Opret den fysiske dårligging-connector

Det næste trin er at oprette en fysisk badging-connector på overholdelsesportalen. Når du har kørt scriptet i trin 4, behandles og pushes den JSON-fil, du oprettede i trin 3, til det API-slutpunkt, du konfigurerede i trin 1. I dette trin skal du sørge for at kopiere det JobId, der genereres, når du opretter connectoren. Du skal bruge JobId, når du kører scriptet.

1. Gå til overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataconnectors**</a>.

2. Klik på **Vis** på siden **Dataconnectors** under **Fysisk badging**.

3. Klik på **Tilføj connector** på siden **Fysisk badging**.

4. Gør følgende på siden **Legitimationsoplysninger til godkendelse** , og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 1.

   2. Download eksempelskemaet for din reference for at oprette JSON-filen.

   3. Skriv et entydigt navn til den fysiske badging-connector.

5. Gennemse dine indstillinger på siden **Gennemse** , og klik derefter på **Udfør** for at oprette connectoren.

6. Der vises en statusside, der bekræfter, at connectoren blev oprettet. Denne side indeholder også job-id'et. Du kan kopiere job-id'et fra denne side eller fra pop op-siden for connectoren. Du skal bruge dette job-id, når du kører scriptet.

   Statussiden indeholder også et link til scriptet. Se dette script for at forstå, hvordan du sender JSON-filen til API-slutpunktet.

7. Klik på **Udført**.

   Den nye connector vises på listen under fanen **Forbindelser** .

8. Klik på den fysiske dårligging-connector, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om connectoren.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Trin 4: Kør scriptet for at POSTe din JSON-fil, der indeholder fysiske badging-data

Det næste trin i konfiguration af en fysisk badging-connector er at køre et script, der sender de fysiske badging-data i JSON-filen (som du oprettede i trin 2) til det API-slutpunkt, du oprettede i trin 1. Vi leverer et eksempelscript til din reference, og du kan vælge at bruge det eller oprette dit eget script for at sende JSON-filen til API-slutpunktet.

Når du har kørt scriptet, sendes den JSON-fil, der indeholder de fysiske badging-data, til din Microsoft 365 organisation, hvor insiderrisikostyringsløsningen kan få adgang til den. Vi anbefaler, at du slår fysiske badging-data op dagligt. Det kan du gøre ved at automatisere processen for at generere JSON-filen hver dag ud fra dit fysiske badgingsystem og derefter planlægge scriptet til at pushoverføre dataene.

> [!NOTE]
> Det maksimale antal poster i JSON-filen, der kan behandles af API'en, er 50.000 poster.

1. Gå til [dette GitHub websted](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) for at få adgang til eksempelscriptet.

2. Klik på knappen **Rå** for at få vist scriptet i tekstvisning

3. Kopiér alle linjerne i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks med .ps1, f.eks. PhysicalBadging.ps1.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at overføre de fysiske badging-data i JSON-filen til Microsoft-cloudmiljøet. f.eks.:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   I følgende tabel beskrives de parametre, der skal bruges sammen med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

   |Parameter|Beskrivelse|
   |---|---|
   |tenantId|Dette er id'et for din Microsoft 365 organisation, som du fik i trin 1. Du kan også hente tenantId for din organisation på bladet **Oversigt** i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |Appid|Dette er Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation.|
   |appSecret|Dette er Azure AD-programhemmeligheden for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
   |job-id|Dette er job-id'et for den fysiske dårligging-connector, som du oprettede i trin 3. Dette bruges til at knytte de fysiske badging-data, der pushes til Microsoft-cloudmiljøet, med den fysiske badging-connector.|
   |JsonFilePath|Dette er filstien på den lokale computer (den, du bruger til at køre scriptet) for den JSON-fil, du oprettede i trin 2. Denne fil skal følge det eksempelskema, der er beskrevet i trin 3.|
   |||

   Her er et eksempel på syntaksen for connectorscriptet til den fysiske badging ved hjælp af faktiske værdier for hver parameter:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Hvis overførslen lykkes, viser scriptet **meddelelsen Upload fuldført**.

   Hvis du har flere JSON-filer, skal du køre scriptet for hver fil.

> [!NOTE]
> Du kan også vælge at overføre de fysiske badging-data til API-slutpunktet ved hjælp af andre metoder end at køre det forrige script. Her er f.eks. et eksempel på, hvordan du bruger Postman til at overføre dine data til API-slutpunktet.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Trin 5: Overvåg den fysiske dårligging-connector

Når du har oprettet den fysiske dårligging-connector og pushoverføre dine fysiske badging-data, kan du få vist connectoren og uploade status på overholdelsesportalen. Hvis du planlægger, at scriptet skal køre automatisk regelmæssigt, kan du også få vist den aktuelle status efter sidste gang scriptet kørte.

1. Gå til overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataconnectors**</a>.

2. Klik på fanen **Forbindelser,** og vælg derefter den fysiske dårligging-connector for at få vist pop op-siden. Denne side indeholder egenskaberne og oplysningerne om connectoren.

   ![Status-pop op-side for fysisk dårlig forbindelse.](..\media\PhysicalBadgingStatusFlyout.png)

3. Under **Seneste import** skal du klikke på linket **Download log** for at åbne (eller gemme) statusloggen for connectoren. Denne log indeholder oplysninger om, hver gang scriptet kører, og uploader dataene fra JSON-filen til Microsoft-cloudmiljøet.

   ![Logfilen for den fysiske badgingforbindelse viser antallet af objekter fra den JSON-fil, der blev overført.](..\media\PhysicalBadgingConnectorLogFile.png)

   Feltet **RecordsSaved** angiver antallet af objekter i den JSON-fil, der blev overført. Hvis JSON-filen f.eks. indeholder fire objekter, er værdien af felterne **RecordsSaved** 4, hvis scriptet overførte alle objekterne i JSON-filen.

Hvis du ikke har kørt scriptet i trin 4, vises der et link til download af scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene i Trin 4 for at køre det.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg, at scriptet kører automatisk

Hvis du vil sikre, at de nyeste fysiske badging-data fra din organisation er tilgængelige for værktøjer som f.eks. løsningen til styring af insiderrisiko, anbefaler vi, at du planlægger, at scriptet kører automatisk på tilbagevendende basis, f.eks. én gang om dagen. Dette kræver også, at du opdaterer de fysiske badging-data til JSON-filen efter en lignende (hvis ikke den samme) tidsplan, så den indeholder de nyeste oplysninger om medarbejdere, der forlader din organisation. Målet er at uploade de mest aktuelle fysiske badging-data, så den fysiske badging-connector kan gøre den tilgængelig for løsningen til styring af insiderrisiko.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen Windows **Start** på den lokale computer, og skriv derefter **Opgavestyring**.

2. Klik på appen **Opgavestyring** for at åbne den.

3. Klik på **Opret opgave** i afsnittet **Handlinger**.

4. Skriv et beskrivende navn på den planlagte opgave under fanen **Generelt** . f.eks. **scriptet for den fysiske badging-connector**. Du kan også tilføje en valgfri beskrivelse.

5. Under **Sikkerhedsindstillinger** skal du gøre følgende:

   1. Find ud af, om du kun vil køre scriptet, når du er logget på computeren eller kører det, når du er logget på eller ej.

   2. Sørg for, at afkrydsningsfeltet **Kør med de højeste rettigheder** er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

   1. Under **Indstillinger** skal du vælge indstillingen **Dagligt** og derefter vælge en dato og et klokkeslæt, hvor scriptet skal køres første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

   2. Under **Avancerede indstillinger** skal du kontrollere, at afkrydsningsfeltet **Aktiveret** er markeret.

   3. Klik på **OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger til oprettelse af en ny planlagt opgave for connectorscriptet til fysisk dårlig skrivning.](..\media\SchedulePhysicalBadgingScript1.png)

   1. På rullelisten **Handling** skal du kontrollere, at **Start et program** er valgt.

   2. Klik på **Gennemse** i feltet **Program/script**, gå til følgende placering, og vælg den, så stien vises i feltet: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. Det kan f.eks. .\PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. F.eks. C:\Users\contosoadmin\Desktop\Scripts.

   5. Klik på **OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK** i vinduet **Opret opgave** for at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i opgavestyringsbiblioteket.

   ![Den nye opgave vises i opgavestyringsbiblioteket.](..\media\SchedulePhysicalBadgingScript2.png)

Sidste gang scriptet kørte, og næste gang det er planlagt til at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden for den tilsvarende fysiske badging-connector i overholdelsescenteret.
