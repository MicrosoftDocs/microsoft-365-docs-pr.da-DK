---
title: Konfigurer en forbindelse til at importere generiske sundhedsrevisionsdata
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
description: Administratorer kan konfigurere en dataforbindelse til at importere elektroniske sundhedsjournaler (EHR) fra deres sundhedssystem for at Microsoft 365. Dette giver dig mulighed for at bruge EHR-data i insider-risikostyringspolitikker for at hjælpe dig med at registrere uautoriseret adgangsaktivitet til patientdata fra dine medarbejdere.
ms.openlocfilehash: 7fac743afe76e0cc3f5ae44cbd1236a2f7b3c0d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594065"
---
# <a name="set-up-a-connector-to-import-healthcare-ehr-audit-data-preview"></a>Konfigurer en forbindelse til at importere sundhedssundhedssektorens EHR-overvågningsdata (forhåndsvisning)

Du kan konfigurere en dataforbindelse i Microsoft 365 Overholdelsescenter til at importere overvågningsdata for brugeraktivitet i organisationens system med elektroniske sundhedsjournaler (EHR). Overvågning af data fra dit sundhedssystem EHR-systemet omfatter data for hændelser, der har med at få adgang til en patients sundhedsjournaler. Healthcare EHR-overvågningsdata kan bruges af Microsoft 365 insider-risikostyringsløsningen for at beskytte din organisation mod uautoriseret adgang til patientoplysninger. [](insider-risk-management.md)

Konfiguration af en sundhedsforbindelse består af følgende opgaver:

- Oprettelse af en app i Azure Active Directory (Azure AD) til at få adgang til et API-slutpunkt, der accepterer en tabulatorsepareret tekstfil, der indeholder sundheds-EHR-overvågningsdata.

- Oprettelse af en tekstfil med alle de påkrævede felter som defineret i forbindelsesskemaet.

- Oprettelse af en sundhedsforbindelsesforekomst i Microsoft 365 Overholdelsescenter.

- Kørsel af et script for at skubbe sundhedssundhedssektorens EHR-overvågningsdata til API-slutpunktet.

- Du kan også planlægge, at scriptet skal køre automatisk for at importere overvågningsdataene.

## <a name="before-you-set-up-the-connector"></a>Før du konfigurerer forbindelsen

- Den bruger, der opretter sundhedsforbindelse i trin 3, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Du skal bestemme, hvordan du henter eller eksporterer data fra din organisations sundhedssundhedssektoren EHR-system (dagligt) og oprette en tekstfil, der er beskrevet i trin 2. Det script, du kører i trin 4, skubber dataene i tekstfilen til API-slutpunktet.

- Eksempelscriptet, som du kører i trin 4, skubber sundheds-EHR-overvågningsdata fra tekstfilen til forbindelses-API'en, så den kan bruges af insider-risikostyringsløsningen. Dette eksempelscript understøttes ikke i nogen Microsoft-standardsupportprogram eller -tjeneste. Eksempelscriptet leveres som det er, uden garantier af nogen art. Microsoft fraskriver sig yderligere alle stiltiende garantier, herunder, men ikke begrænset til stiltiende garantier for salgbarhed eller egnethed til bestemte formål. Den samlede risiko ved anvendelse eller ydeevne af eksempelscriptet og dokumentationen forbliver hos dig. I intet tilfælde kan Microsoft, dets forfattere eller andre involverede i oprettelse, produktion eller levering af scripts holdes ansvarlige for erstatning (herunder, men ikke begrænset til, erstatning for tabt forretningsfortjenester, driftstab, tabt erhvervsinformation eller andre økonomiske tab) som følge af brug af eller manglende mulighed for at bruge eksempelscripts eller dokumentation,  også selvom Microsoft er blevet underrettet om risikoen for sådanne skader.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at oprette og registrere en ny app i Azure Active Directory (Azure AD). Appen svarer til den sundhedsforbindelse, du opretter i trin 3. Oprettelse af denne app gør det muligt for Azure AD at godkende pushanmodningen for en tekstfil, der indeholder sundheds-EHR-overvågningsdata. Sørg for at gemme følgende oplysninger under oprettelsen af denne Azure AD-app. Disse værdier skal bruges i senere trin.

- Azure AD-program-id (også kaldet *app-id eller* *klient-id*)

- Azure AD programhemmelighed (også kaldet *klienthemmelighed*)

- Lejer-id (også kaldet *katalog-id*)

Du kan finde en trinvis vejledning til oprettelse af en app i Azure AD under [Registrer et program Microsoft-identitetsplatform](\azure\active-directory\develop\quickstart-register-app).

## <a name="step-2-prepare-a-text-file-with-healthcare-ehr-auditing-data"></a>Trin 2: Forbered en tekstfil med sundheds-EHR-overvågningsdata

Næste trin er at oprette en tekstfil, der indeholder oplysninger om medarbejdernes adgang til patientjournaler i organisationens sundhedssystem EHR. Som beskrevet tidligere skal du afgøre, hvordan du opretter denne tekstfil fra dit sundhedssystem EHR. Arbejdsprocessen for sundhedsforbindelser kræver en tekstfil med tabulatorseparerede værdier for at knytte disse data i tekstfilen med det påkrævede forbindelsesskema. Det understøttede filformat er et komma (.csv), et pipe (.psv) eller en tabulatorsepareret tekstfil (.tsv).

> [!NOTE]
> Den maksimale størrelse på tekstfilen, der indeholder overvågningsdataene, er 3 GB. Det maksimale antal rækker er 5 millioner. Sørg også for kun at medtage de relevante overvågningsdata fra dit sundhedssystem EHR.

I følgende tabel vises de felter, der skal bruges til at aktivere Insider Risk Management-scenarier. Et undersæt af disse felter er obligatorisk. Disse felter er fremhævet med en stjerne (*). Hvis nogen af de obligatoriske felter mangler i tekstfilen, valideres filen ikke, og dataene i filen importeres ikke.

|Felt|Kategori|
|:----|:----------|
| *Oprettelses-timeEventnavn<br/>*<br/>Arbejdsstations-id<br/>Hændelsessektion<br/>Hændelseskategori |Disse felter bruges til at identificere adgangsaktivitetshændelser i sundhedssektoren EHR-systemet.|
| Patient Reg Id<br/>Patient-fornavn *<br/>Patient-mellemnavn <br/>Patient-efternavn* <br/>Patientadresse linje 1* <br/>Patientadresse linje 2<br/>Patient City* <br/>Patientnr. postnummer*  <br/>Patienttilstand <br/>Patient Country <br/>Patientafdeling              | Disse felter bruges til at identificere patientprofiloplysninger.|
| Årsag til begrænset adgang*<br/> Kommentar med begrænset adgang | Disse felter bruges til at identificere adgang til begrænsede poster.|
| Mailadresse (UPN) eller SamAccountName*<br/>Medarbejderbrugernavn <br/> Medarbejder-id <br/> Medarbejders efternavn <sup>1</sup> <br/> Medarbejders fornavn <sup>1</sup> | Disse felter bruges til at identificere medarbejderprofiloplysninger for adresse og matchende navn, der kræves for at bestemme adgang til poster af samme navn/familie/medarbejder. |
|||

> [!NOTE] 
> <sup>1</sup> Dette felt er muligvis ikke tilgængeligt som standard i dit sundhedssundhedssektoren EHR-system. Du skal konfigurere eksporten for at sikre dig, at tekstfilen indeholder dette felt.

## <a name="step-3-create-the-healthcare-connector"></a>Trin 3: Opret forbindelseskomponent til sundhedssektoren

Næste trin er at oprette en sundhedsforbindelse i Microsoft 365 Overholdelsescenter. Når du kører scriptet i trin 4, bliver tekstfilen, som du oprettede i trin 2, behandlet og flyttet til det API-slutpunkt, du konfigurerede i trin 1. I dette trin skal du sørge for at kopiere det JobId, der genereres, når du opretter forbindelsen. Du skal bruge JobId'et, når du kører scriptet.

1. Gå til <https://compliance.microsoft.com> og klik derefter **på Dataforbindelser** i venstre navigationslinje.

2. På fanen **Oversigt skal** du klikke på **Sundhedssektoren (forhåndsvisning)**.

3. Klik på **Tilføj forbindelse på siden Sundhedssektoren (****forhåndsvisning**).

4. Acceptér servicebetingelserne.

5. Gør følgende **på siden Legitimationsoplysninger** for godkendelse, og klik derefter på **Næste**:

    1. Skriv eller indsæt Azure AD-program-id'et for den Azure-app, du oprettede i trin 1.

    2. Skriv et navn til sundhedsforbindelse.

6. På siden **Metode til filtilknytning** skal du vælge en af følgende indstillinger og derefter klikke på **Næste**.

   - **Upload en eksempelfil**. Hvis du vælger denne indstilling, skal du **klikke Upload eksempelfil for** at overføre den fil, du forberedte i trin 2. Denne indstilling giver dig mulighed for hurtigt at vælge kolonnenavne i din tekstfil på en rulleliste for at knytte kolonnerne til det skema, der kræves til sundhedsforbindelse. 

    Eller

   - **Angiv tilknytningsdetaljerne manuelt**. Hvis du vælger denne indstilling, skal du skrive navnet på kolonnerne i tekstfilen for at knytte kolonnerne til det skema, der kræves for sundhedsforbindelse.

7. På siden **Oplysninger om tilknytning af** fil skal du gøre et af følgende, afhængigt af om du har uploadet en eksempelfil eller ej i det forrige trin:

   - Brug rullelisterne til at knytte kolonnerne fra eksempelfilen til hvert felt, der skal bruges til sundhedssundhedssektoren.

    Eller

   - For hvert felt skal du skrive kolonnenavnet fra den fil, du forberedte i trin 2, der svarer til feltet for sundhedsforbindelse.

8. Gennemgå dine **indstillinger på** siden Gennemse, og klik derefter på **Udfør for** at oprette forbindelsen.

   Der vises en statusside, der bekræfter, at forbindelsen blev oprettet. Denne side indeholder to vigtige ting, du skal bruge for at fuldføre næste trin for at køre eksempelscriptet for at uploade dine sundheds-EHR-overvågningsdata.

    - **Job-id.** Du skal bruge dette job-id for at køre scriptet i næste trin. Du kan kopiere det fra denne side eller fra pop op-siden for forbindelser.

    - **Link til eksempelscript.** Klik på **linket her** for at gå til webstedet GitHub for at få adgang til eksempelscriptet (linket åbner et nyt vindue). Hold dette vindue åbent, så du kan kopiere scriptet i trin 4. Alternativt kan du bogmærke destinationen eller kopiere URL-adressen, så du kan få adgang til den igen, når du kører scriptet. Dette link er også tilgængeligt på pop op-siden med forbindelser.

9. Klik **på Udført**.

   Den nye forbindelse vises på listen under **fanen** Forbindelser.

10. Klik på den sundhedsforbindelse, du lige har oprettet, for at få vist pop op-siden, som indeholder egenskaber og andre oplysninger om forbindelsen.

Hvis du ikke allerede har gjort det, kan du kopiere værdierne for job-id'et for **Azure App** **og Connector**. Du skal bruge disse for at køre scriptet i næste trin. Du kan også downloade scriptet fra pop op-siden (eller hente det ved hjælp af linket i næste trin).

Du kan også klikke på **Rediger for** at ændre Azure App-id'et eller kolonneoverskriftsnavnene, du har defineret på **siden Filtilknytning** .

## <a name="step-4-run-the-sample-script-to-upload-your-healthcare-ehr-auditing-data"></a>Trin 4: Kør eksempelscriptet for at uploade dine sundheds-EHR-overvågningsdata

Det sidste trin i konfigurationen af en sundhedsforbindelse er at køre et eksempelscript, der overfører dataene fra sundhedsvæsnet EHR i tekstfilen (som du oprettede i trin 1) til Microsoft-skyen. Specifikt overfører scriptet dataene til forbindelsen til Sundhedssektoren. Når du har kørt scriptet, importerer den forbindelseskomponent til sundhedssektoren, som du oprettede i trin 3, dataene fra sundhedssektoren EHR til din Microsoft 365-organisation, hvor de kan tilgås af andre overholdelsesværktøjer, f.eks. Insider-risikostyringsløsningen. Når du har kørt scriptet, bør du overveje at planlægge en opgave til at køre den automatisk dagligt, så de nyeste data om medarbejders afslutning uploades til Microsoft-skyen. Se [(Valgfrit) Trin 6: Planlæg scriptet til at køre automatisk](#optional-step-6-schedule-the-script-to-run-automatically).

> [!NOTE]
> Som nævnt tidligere er den maksimale størrelse af tekstfilen, der indeholder overvågningsdataene, 3 GB. Det maksimale antal rækker er 5 millioner. Det script, du kører i dette trin, tager ca. 30 til 40 minutter at importere overvågningsdata fra store tekstfiler. Desuden opdeler scriptet store tekstfiler i mindre blokke med 100.000 rækker og importerer derefter disse blokke sekventielt.

1. Gå til det vindue, du slap, fra det forrige trin for at få adgang GitHub websted med eksempelscriptet. Alternativt kan du åbne webstedet med bogmærket eller bruge den URL-adresse, du kopierede. Du kan også få adgang til [scriptet her](https://github.com/microsoft/m365-compliance-connector-sample-scripts/blob/main/sample_script.ps1).

2. Klik på **knappen Rå** for at få vist scriptet i tekstvisning.

3. Kopiér alle linjer i eksempelscriptet, og gem dem derefter i en tekstfil.

4. Rediger eksempelscriptet for din organisation, hvis det er nødvendigt.

5. Gem tekstfilen som en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks af `.ps1`; for eksempel `HealthcareConnector.ps1`.

6. Åbn en kommandoprompt på din lokale computer, og gå til den mappe, hvor du gemte scriptet.

7. Kør følgende kommando for at uploade sundhedsrevisionsdataene i tekstfilen til Microsoft Cloud; for eksempel:

   ```powershell
   .\HealthcareConnector.ps1 -tenantId <tenantId> -appId <appId>  -appSecret <appSecret>  -jobId <jobId>  -filePath '<filePath>'
   ```

I følgende tabel beskrives de parametre, der skal bruges med dette script, og de påkrævede værdier. De oplysninger, du fik i de forrige trin, bruges i værdierne for disse parametre.

|Parameter  |Beskrivelse|
|:----------|:----------|
|tenantId|Dette er id'et for din Microsoft 365, du fik i trin 1. Du kan også hente lejer-id'et for din organisation på **oversigtsbladet** i Azure AD Administration. Dette bruges til at identificere din organisation.|
|appId|Dette er Azure AD-program-id'et for den app, du oprettede i Azure AD i trin 1. Dette bruges af Azure AD til godkendelse, når scriptet forsøger at få adgang til din Microsoft 365 organisation.|
|appSecret|Dette er Azure AD-programhemmelighed for den app, du oprettede i Azure AD i trin 1. Dette bruges også til godkendelse.|
|jobId|Dette er job-id'et for den sundhedsforbindelse, du oprettede i trin 3. Dette bruges til at knytte de sundheds-EHR-overvågningsdata, der er overført til Microsoft-skyen, med forbindelsen til sundhedssektoren.|
|filePath|Dette er filstien til tekstfilen (gemt på det samme system som scriptet), som du oprettede i trin 2. Prøv at undgå mellemrum i filstien. ellers skal du bruge enkelte anførselstegn.|
|||

Her er et eksempel på syntaksen for scriptet til forbindelsesscriptet Til sundhedssektoren, der anvender faktiske værdier for hver parameter:

```powershell
.\HealthcareConnector.ps1 -tenantId d5723623-11cf-4e2e-b5a5-01d1506273g9 -appId 29ee526e-f9a7-4e98-a682-67f41bfd643e -appSecret MNubVGbcQDkGCnn -jobId b8be4a7d-e338-43eb-a69e-c513cd458eba -filePath 'C:\Users\contosoadmin\Desktop\Data\healthcare_audit_records.csv'
```

Hvis overførslen lykkes, viser scriptet meddelelsen **Upload vellykket**.

> [!NOTE]
> Hvis du har problemer med at køre den forrige kommando på grund af [](/powershell/module/microsoft.powershell.core/about/about_execution_policies) eksekveringspolitikker, skal du se Om eksekveringspolitikker og [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) for at få en vejledning til at angive eksekveringspolitikker.

## <a name="step-5-monitor-the-healthcare-connector"></a>Trin 5: Overvåg sundhedsstikket

Når du har oprettet sundhedsforbindelse og skubbet dine EHR-overvågningsdata, kan du få vist forbindelsen og overføre status i Microsoft 365 Overholdelsescenter. Hvis du planlægger at køre scriptet automatisk med jævne mellemrum, kan du også få vist den aktuelle status efter sidste gang, scriptet kørte.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **fanen Forbindelser** , og vælg derefter Sundhedsforbindelse for at få vist pop op-siden. Denne side indeholder egenskaber og oplysninger om forbindelsen.

3. Under **Sidste import** skal du klikke **på linket Download** log for at åbne (eller gemme) statusloggen for forbindelsen. Denne logfil indeholder oplysninger om hver gang scriptet kører og overfører data fra tekstfilen til Microsoft-skyen.

    Feltet `RecordsSaved` angiver antallet af rækker i tekstfilen, der er overført. Hvis tekstfilen f.eks. indeholder fire rækker, `RecordsSaved` er værdien af felterne 4, hvis scriptet har overført alle rækkerne i tekstfilen.

Hvis du ikke har kørt scriptet i trin 4, vises et link til at downloade scriptet under **Seneste import**. Du kan downloade scriptet og derefter følge trinnene for at køre scriptet.

## <a name="optional-step-6-schedule-the-script-to-run-automatically"></a>(Valgfrit) Trin 6: Planlæg scriptet til at køre automatisk

For at sikre at de nyeste overvågningsdata fra dit sundheds-EHR-system er tilgængelige for værktøjer som insider-risikostyringsløsningen, anbefaler vi, at du planlægger scriptet til at køre automatisk dagligt. Dette kræver også, at du opdaterer EHR-overvågningsdataene i den samme tekstfil på en lignende (hvis ikke den samme) tidsplan, så den indeholder de seneste oplysninger om dine medarbejderes adgang til patientjournaler. Målet er at uploade de mest aktuelle overvågningsdata, så sundheds-forbindelsen kan gøre dem tilgængelige for insider-risikostyringsløsningen.

Du kan bruge appen Opgavestyring i Windows til automatisk at køre scriptet hver dag.

1. Klik på knappen Start på din lokale Windows **skriv** derefter **Opgavestyring**.

2. Klik på **appen Opgavestyring** for at åbne den.

3. Klik på **Opret** opgave i **sektionen Handlinger**.

4. Skriv et **beskrivende** navn til den planlagte opgave under fanen Generelt. Eksempelvis **sundhedsforbindelsesscript**. Du kan også tilføje en valgfri beskrivelse.

5. Gør **følgende under** Sikkerhedsindstillinger:

    1. Find ud af, om scriptet kun skal køres, når du er logget på computeren, eller om du skal køre det, når du er logget på.

    2. Sørg for, at **afkrydsningsfeltet Kør med de højeste** rettigheder er markeret.

6. Vælg fanen **Udløsere** , klik på **Ny**, og gør derefter følgende:

    1. Under **Indstillinger** skal du **vælge indstillingen** Dagligt og derefter vælge en dato og et klokkeslæt for at køre scriptet for første gang. Scriptet kører hver dag på det samme angivne tidspunkt.

    2. Sørg **for, at** afkrydsningsfeltet **Aktiveret er markeret** under Avancerede indstillinger.

    3. Klik **på OK**.

7. Vælg fanen **Handlinger** , klik på **Ny**, og gør derefter følgende:

   ![Handlingsindstillinger for at oprette en ny planlagt opgave for scriptet til sundhedssundhedssektorens forbindelse.](../media/GenericHealthCareConnectorScheduleTask1.png)

    1. Sørg for **,** at Start et program er markeret **på rullelisten** Handling.

    2. I feltet **Program/script** skal du klikke på Gennemse og gå til følgende placering og vælge den, så stien vises i feltet: C:.0.exe.

    3. I feltet **Tilføj argumenter (valgfrit)** skal du indsætte den samme scriptkommando, som du kørte i trin 4. For eksempel `.\HealthcareConnector.ps1 -tenantId "d5723623-11cf-4e2e-b5a5-01d1506273g9" -appId "c12823b7-b55a-4989-faba-02de41bb97c3" -appSecret "MNubVGbcQDkGCnn" -jobId "e081f4f4-3831-48d6-7bb3-fcfab1581458" -filePath "C:\Healthcare\audit\records.txt"`

    4. I feltet **Start i (valgfrit)** skal du indsætte mappeplaceringen for det script, du kørte i trin 4. For eksempel C:\Healthcare\audit.

    5. Klik **på OK** for at gemme indstillingerne for den nye handling.

8. Klik på **OK i** vinduet Opret opgave **for** at gemme den planlagte opgave. Du bliver muligvis bedt om at angive legitimationsoplysningerne for din brugerkonto.

   Den nye opgave vises i biblioteket Opgavestyring.

   ![Den nye opgave for scriptet til sundhedssundhedssektorens forbindelse vises i Biblioteket Opgavestyring.](../media/HealthcareConnectorTaskSchedulerLibrary.png)

   Sidste gang scriptet kørte, og næste gang det er planlagt at køre, vises. Du kan dobbeltklikke på opgaven for at redigere den.

   Du kan også kontrollere, sidste gang scriptet kørte på pop op-siden på den tilsvarende Sundhedsforbindelse i overholdelsescenteret.
