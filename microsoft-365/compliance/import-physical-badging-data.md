---
title: Konfigurere en forbindelse til at importere fysiske ugyldige data
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
description: Administratorer kan konfigurere en dataforbindelse til at importere data fra deres organisations fysiske badging-system for at Microsoft 365. Dette giver dig mulighed for at bruge disse data i politikker for insider-risikostyring til at hjælpe dig med at registrere, at bestemte brugere har adgang til dine fysiske bygninger, som kan betyde en mulig intern trussel mod din organisation.
ms.openlocfilehash: e70217fa98e283883ab70bbe924d6f01f27613b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590659"
---
# <a name="set-up-a-connector-to-import-physical-badging-data-preview"></a>Konfigurer en forbindelse til at importere fysiske ugyldige data (eksempel)

Du kan konfigurere en dataforbindelse i Microsoft 365 Overholdelsescenter til at importere fysiske ugyldige data, f.eks. medarbejdernes rå fysiske adgangshændelser eller fysiske adgangs alarmer, der genereres af organisationens badging-system. Eksempler på fysiske adgangspunkter er en post i en bygning eller en post i serverrum eller datacenter. Fysisk badging-data kan bruges af Microsoft 365 [insider-risikostyringsløsning](insider-risk-management.md) til at beskytte din organisation mod skadelig aktivitet eller datatyveri inden for organisationen.

Konfiguration af en fysisk dårlig forbindelse består af følgende opgaver:

- Oprettelse af en app i Azure Active Directory (Azure AD) til at få adgang til et API-slutpunkt, der accepterer en JSON-nyttedata, der indeholder fysiske ugyldige data.

- Oprettelse af JSON-nyttedata med et skema, der er defineret ved en fysisk ugyldig dataforbindelse.

- Oprettelse af en fysisk dårlig dataforbindelse i Microsoft 365 Overholdelsescenter.

- Kørsel af et script for at skubbe de fysiske ugyldige data til API-slutpunktet.

- Du kan også planlægge, at scriptet skal køre automatisk til at importere aktuelle fysiske ugyldige data.

## <a name="before-you-set-up-the-connector"></a>Før du konfigurerer forbindelsen

- Den bruger, der opretter den fysiske kantforbindelse i trin 3, skal have tildelt rollen Som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

   > [!NOTE]
   > Administratorrollen Dataforbindelse understøttes i øjeblikket ikke i us Government GCC High- og DoD-miljøer. Den bruger, der opretter HR-forbindelsen i GCC High- og DoD-miljøer, skal derfor have tildelt rollen Postkasse Import Eksport i Exchange Online. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration i Exchange Online. Eller du kan oprette en ny rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje de relevante brugere som medlemmer. Du kan finde flere oplysninger i [afsnittene](/Exchange/permissions-exo/role-groups#create-role-groups) Opret [](/Exchange/permissions-exo/role-groups#modify-role-groups) rollegrupper eller Rediger rollegrupper i artiklen "Administrer rollegrupper Exchange Online".

- Du skal finde ud af, hvordan du henter eller eksporterer data fra din organisations fysiske kantsystem (dagligt) og oprette en JSON-fil, der er beskrevet i trin 2. Det script, du kører i trin 4, skubber dataene i JSON-filen til API-slutpunktet.

- Eksempelscriptet, som du kører i trin 4, skubber de fysiske ugyldige data fra JSON-filen til forbindelses-API'en, så de kan bruges af insider-risikostyringsløsningen. Dette eksempelscript understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

- Denne forbindelse er tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Tredjepartsprogrammer og -tjenester kan omfatte lagring, overførsel og behandling af din organisations kundedata på tredjepartssystemer, der er uden for Microsoft 365-infrastrukturen, og som derfor ikke er omfattet af Microsoft 365-overholdelses- og databeskyttelsesforpligtelserne. Microsoft påser ikke, at brugen af dette produkt til at oprette forbindelse til tredjepartsprogrammer antyder, at disse tredjepartsprogrammer er FEDRAMP kompatible.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den fysiske kantforbindelse, du opretter i trin 3. Hvis du opretter denne app, kan Azure AD godkende pushanmodningen om JSON-nyttedata, der indeholder fysiske ugyldige data. Sørg for at gemme følgende oplysninger under oprettelsen af denne Azure AD-app. Disse værdier skal bruges i senere trin.

- Azure AD-program-id (også kaldet *app-id eller* *klient-id*)

- Azure AD programhemmelighed (også kaldet *klienthemmelighed*)

- Lejer-id (også kaldet *katalog-id*)

Du kan finde en trinvis vejledning til oprettelse af en app i Azure AD under [Registrer et program Microsoft-identitetsplatform](/azure/active-directory/develop/quickstart-register-app).

## <a name="step-2-prepare-a-json-file-with-physical-badging-data"></a>Trin 2: Forbered en JSON-fil med fysiske ugyldige data

Næste trin er at oprette en JSON-fil, der indeholder oplysninger om medarbejdernes fysiske adgangsdata. Som beskrevet i sektionen før du begynder skal du afgøre, hvordan denne JSON-fil skal genereres ud fra organisationens fysiske badging-system.

JSON-filen skal overholde den skemadefinition, der kræves af forbindelsen. Her er beskrivelser af de påkrævede skemaegenskaber for JSON-filen:

|Egenskab|Beskrivelse|Datatype|
|---|---|---|
|UserId|En medarbejder kan have flere digitale identiteter på tværs af systemer. Inputtet skal have Azure AD-id'et løst af kildesystemet.|UPN eller mailadresse|
|AssetId|Reference-id'et for det fysiske aktiv eller fysiske adgangspunkt.|Alfanumerisk streng|
|Aktivnavn|Det fulde navn på det fysiske aktiv eller fysiske adgangspunkt.|Alfanumerisk streng|
|EventTime|Adgangsstempel.|Dato og klokkeslæt i UTC-format|
|AccessStatus|Værdi af `Success` eller `Failed`|String|
|||

Her er et eksempel på en JSON-fil, der overholder det påkrævede skema:

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

Du kan også hente følgende skemadefinition for JSON-filen fra guiden, når du opretter den fysiske ugyldige forbindelse i trin 3.

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

## <a name="step-3-create-the-physical-badging-connector"></a>Trin 3: Opret den fysiske kantforbindelse

Næste trin er at oprette en fysisk kantforbindelse i Microsoft 365 Overholdelsescenter. Når du kører scriptet i trin 4, behandles den JSON-fil, du oprettede i trin 3, og skubbes til det API-slutpunkt, du konfigurerede i trin 1. I dette trin skal du sørge for at kopiere det JobId, der genereres, når du opretter forbindelsen. Du skal bruge JobId'et, når du kører scriptet.

1. Gå til Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataforbindelser**</a>.

2. Klik på **Vis under Fysisk** **badging på siden Dataforbindelser****.**

3. Klik på **Tilføj forbindelse på** siden Fysisk **badging**.

4. Gør følgende **på siden Legitimationsoplysninger** for godkendelse, og klik derefter på **Næste**:

   1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 1.

   2. Download eksempelskemaet for din reference for at oprette JSON-filen.

   3. Skriv et entydigt navn til den fysiske kantforbindelse.

5. Gennemgå dine **indstillinger på** siden Gennemse, og klik derefter på **Udfør for** at oprette forbindelsen.

6. Der vises en statusside, der bekræfter, at forbindelsen blev oprettet. Denne side indeholder også job-id'et. Du kan kopiere job-id'et fra denne side eller fra pop op-siden for forbindelsen. Du skal bruge dette job-id, når du kører scriptet.

   Statussiden indeholder også et link til scriptet. Se dette script for at forstå, hvordan du sender JSON-filen til API-slutpunktet.

7. Klik **på Udført**.

   Den nye forbindelse vises på listen under **fanen** Forbindelser.

8. Klik på den fysiske forbindelse, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om forbindelsen.

## <a name="step-4-run-the-script-to-post-your-json-file-containing-physical-badging-data"></a>Trin 4: Kør scriptet for at POSTe din JSON-fil, der indeholder fysiske ugyldige data

Det næste trin i konfigurationen af en fysisk ugyldig forbindelse er at køre et script, der skubber de fysiske ugyldige data i JSON-filen (som du oprettede i trin 2) til API-slutpunktet, du oprettede i trin 1. Vi leverer et eksempelscript til din reference, og du kan vælge at bruge det eller oprette dit eget script til at sende JSON-filen til API-slutpunktet.

Når du kører scriptet, skubbes JSON-filen, der indeholder de fysiske badging-data, til din Microsoft 365-organisation, hvor den kan tilgås af insider-risikostyringsløsningen. Vi anbefaler, at du slår fysiske ugyldige data op dagligt. Du kan gøre dette ved at automatisere processen med at generere JSON-filen hver dag ud fra dit fysiske badgingsystem og derefter planlægge scriptet for at skubbe dataene.

> [!NOTE]
> Det maksimale antal poster i JSON-filen, der kan behandles af API'en, er 50.000 poster.

1. Gå til [dette GitHub for at få](https://github.com/microsoft/m365-physical-badging-connector-sample-scripts/blob/master/push_physical_badging_records.ps1) adgang til eksempelscriptet.

2. Klik på **knappen Raw** for at få vist scriptet i tekstvisning

3. Kopiér alle linjer i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af .ps1, f.eks. PhysicalBadging.ps1.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at skubbe de fysiske ugyldige data i JSON-filen til Microsoft-skyen. for eksempel:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId "<Tenant Id>" -appId "<Azure AD App Id>" -appSecret "<Azure AD App Secret>" -jobId "Job Id" -jsonFilePath "<records file path>"
   ```

   I følgende tabel beskrives de parametre, der skal bruges med dette script, og de påkrævede værdier. De oplysninger, du indhentede i de forrige trin, bruges i værdierne for disse parametre.

   |Parameter|Beskrivelse|
   |---|---|
   |tenantId|Dette er id'et for din Microsoft 365, du fik i trin 1. Du kan også hente lejer-id'et for organisationen på **oversigts** bladet i Azure AD Administration. Dette bruges til at identificere din organisation.|
   |appId|Dette er Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation.|
   |appSecret|Dette er Azure AD-programhemmelighed for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
   |jobId|Dette er Job-id'et for den fysiske kantforbindelse, du oprettede i trin 3. Dette bruges til at knytte de fysiske ugyldige data, der er rykket til Microsoft-skyen, til den fysiske badging-forbindelse.|
   |JsonFilePath|Dette er filstien på den lokale computer (den, du bruger til at køre scriptet) til den JSON-fil, du oprettede i trin 2. Denne fil skal følge det eksempelskema, der er beskrevet i trin 3.|
   |||

   Her er et eksempel på syntaksen for scriptet til en fysisk ugyldig forbindelse ved hjælp af faktiske værdier for hver parameter:

   ```powershell
   .\PhysicalBadging.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -jsonFilePath 'C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json'
   ```

   Hvis overførslen lykkes, viser scriptet meddelelsen **Upload vellykket**.

   Hvis du har flere JSON-filer, skal du køre scriptet for hver fil.

> [!NOTE]
> Du kan også vælge at skubbe de fysiske ugyldige data til API-slutpunktet ved hjælp af andre metoder end at køre det forrige script. Her er f.eks. et eksempel på, hvordan du bruger Postman til at skubbe dine data til API-slutpunktet.

## <a name="step-5-monitor-the-physical-badging-connector"></a>Trin 5: Overvåg den fysiske kantforbindelse

Når du har oprettet den fysiske dårligt kantforbindelse og skubber dine fysiske badging-data, kan du få vist forbindelsen og overføre status Microsoft 365 Overholdelsescenter. Hvis du planlægger at køre scriptet automatisk med jævne mellemrum, kan du også få vist den aktuelle status efter sidste gang, scriptet kørte.

1. Gå til Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataforbindelser**</a>.

2. Klik på **fanen Forbindelser,** og vælg derefter den fysiske kantforbindelse for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

   ![Pop op-side med status for fysisk ugyldig forbindelse.](..\media\PhysicalBadgingStatusFlyout.png)

3. Under **Sidste import** skal du klikke **på linket Download** log for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om hver gang scriptet kører og uploader data fra JSON-filen til Microsoft-skyen.

   ![Fysisk badging-forbindelseslogfil viser antallet af objekter fra JSON-filen, der blev overført.](..\media\PhysicalBadgingConnectorLogFile.png)

   Feltet **Gemt af poster** angiver antallet af objekter i den JSON-fil, der blev overført. Hvis JSON-filen f.eks. indeholder fire objekter, er værdien af felterne  Gemt af poster 4, hvis scriptet har overført alle objekterne i JSON-filen.

Hvis du ikke har kørt scriptet i trin 4, vises et link til at downloade scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene i trin 4 for at køre det.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg scriptet til at køre automatisk

For at sikre, at de nyeste fysiske badging-data fra din organisation er tilgængelige for værktøjer som f.eks. Insider Risk Management-løsningen, anbefaler vi, at du planlægger scriptet til at køre automatisk med tilbagevendende mellemrum, f.eks. en gang om dagen. Dette kræver også, at du opdaterer de fysiske ugyldige data til JSON-filen på en lignende (hvis ikke den samme) tidsplan, så den indeholder de seneste oplysninger om medarbejdere, der forlader organisationen. Målet er at overføre de mest aktuelle fysiske ugyldige data, så den fysiske forbindelse kan gøre den tilgængelig for insider-risikostyringsløsningen.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen Start på din lokale Windows **skriv** derefter **Opgavestyring**.

2. Klik på **appen Opgavestyring** for at åbne den.

3. Klik på **Opret** opgave i **sektionen Handlinger**.

4. Skriv et **beskrivende** navn til den planlagte opgave under fanen Generelt. for eksempel script **for fysisk badging-forbindelse**. Du kan også tilføje en valgfri beskrivelse.

5. Gør **følgende under** Sikkerhedsindstillinger:

   1. Find ud af, om scriptet kun skal køres, når du er logget på computeren, eller om du skal køre det, når du er logget på.

   2. Sørg for, at **afkrydsningsfeltet Kør med de højeste** rettigheder er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

   1. Under **Indstillinger** skal du **vælge indstillingen** Dagligt og derefter vælge en dato og et klokkeslæt for at køre scriptet for første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

   2. Sørg **for, at** afkrydsningsfeltet **Aktiveret er markeret** under Avancerede indstillinger.

   3. Klik **på OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger for at oprette en ny planlagt opgave for det fysiske badging-forbindelsesscript.](..\media\SchedulePhysicalBadgingScript1.png)

   1. Sørg for **,** at Start et program er markeret **på rullelisten** Handling.

   2. I feltet **Program/script** skal du klikke på Gennemse og gå til følgende placering og vælge den, så stien vises i feltet: C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe.

   3. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. For eksempel .\PhysicalBadging.ps1-tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -jsonFilePath "C:\Users\contosoadmin\Desktop\Data\physical_badging_data.json"

   4. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. For eksempel C:\Users\contosoadmin\Desktop\Scripts.

   5. Klik **på OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK i** vinduet Opret opgave **for** at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i biblioteket Opgavestyring.

   ![Den nye opgave vises i biblioteket Opgavestyring.](..\media\SchedulePhysicalBadgingScript2.png)

Sidste gang scriptet kørte, og næste gang det er planlagt at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden for den tilsvarende fysiske ugyldighedsforbindelse i overholdelsescenteret.
