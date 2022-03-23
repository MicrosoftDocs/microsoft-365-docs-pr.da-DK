---
title: Søg i overvågningsloggen i Microsoft 365 Overholdelsescenter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
description: Brug søgefunktionen Microsoft 365 Overholdelsescenter søge i den samlede overvågningslog for at få vist bruger- og administratoraktivitet i organisationen.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: ea440ac03c648a7ae77d99d0a7be091d4f72fa64
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63589504"
---
# <a name="search-the-audit-log-in-the-compliance-center"></a>Søg i overvågningsloggen i overholdelsescenteret

Har du brug for at finde ud af, om en bruger har set et bestemt dokument eller fjernet et element fra sin postkasse? Hvis det er ja, kan du bruge søgeværktøjet til overvågningslogfiler i Microsoft 365 Overholdelsescenter til at søge i den samlede overvågningslog for at få vist bruger- og administratoraktivitet i organisationen. Tusindvis af bruger- og administratorhandlinger udført i masser af Microsoft 365-tjenester og -løsninger registreres, registreres og bevares i din organisations samlede overvågningslog. Brugerne i organisationen kan bruge søgeværktøjet til overvågningslogfiler til at søge efter, få vist og eksportere (til en CSV-fil) overvågningsposterne for disse handlinger.

## <a name="microsoft-365-services-that-support-auditing"></a>Microsoft 365 tjenester, der understøtter overvågning

Hvorfor bruge en samlet overvågningslog? Da du kan søge i overvågningsloggen efter aktiviteter, der er udført i Microsoft 365 tjenester. I følgende tabel vises de Microsoft 365 og funktioner (i alfabetisk rækkefølge), der understøttes af den samlede overvågningslog.

| Microsoft 365 tjeneste eller funktion | Posttyper|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| Kommunikationsoverholdelse|ComplianceSuperVisionExchange|
| Indholdsstifinder|LabelContentExplorer|
| Forebyggelse af datatab (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| eDiscovery|Discovery, AeD|
| Nøjagtig dataoverensstemmelse|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Formularer|MicrosoftForms|
| Informationsbarrierer|InformationBarrierPolicyApplication|
| Microsoft 365 Defender|AirInvestigation, AirManualInvestigation, AirAdminActionInvestigation, MS365DCustomDetection|
| Microsoft Teams|MicrosoftTeams|
| MyAnalytics|MyAnalyticsSettings|
| OneDrive for Business|OneDrive|
| Power Apps|PowerAppsApp, PowerAppsPlan|
| Power Automate|MicrosoftFlow|
| Power BI|PowerBIAudit|
| Karantæne|Karantæne|
| Opbevaringspolitikker og opbevaringsnavne|MIPLabel, MipAutoLabelExchangeItem, MipAutoLabelSharePointItem, MipAutoLabelSharePointPolicyLocation|
| Typer af følsomme oplysninger|DlpSensitiveInformationType|
| Følsomhedsmærkater|MIPLabel, SensitivityLabelAction, SensitivityLabeledFileAction, SensitivityLabelPolicyMatch|
| SharePoint Online|SharePoint, SharePointFileOperation,SharePointSharingOperation, SharePointListOperation, SharePointCommentOperation |
| Stream|MicrosoftStream|
| Threat Intelligence|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|
|||

Du kan finde flere oplysninger om de handlinger, der overvåges i hver af de tjenester, der er angivet i den forrige tabel, i afsnittet Overvågede [aktiviteter i](#audited-activities) denne artikel.

Den forrige tabel identificerer også den posttypeværdi, der skal bruges til at søge i overvågningsloggen efter aktiviteter i den tilsvarende tjeneste ved hjælp af **Search-UnifiedAuditLog-cmdlet'en** i Exchange Online PowerShell eller ved hjælp af et PowerShell-script. Nogle tjenester har flere posttyper til forskellige typer aktiviteter inden for den samme tjeneste. Du kan finde en mere komplet liste over overvågningsposttyper i [Office 365 Management Activity API-skema](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Du kan finde flere oplysninger om brug af PowerShell til at søge i overvågningsloggen i:

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Før du søger i overvågningsloggen

Sørg for at læse følgende elementer, før du begynder at søge i overvågningsloggen.

- Søgning i overvågningslogfiler er aktiveret som standard for Microsoft 365 og Office 365 virksomheder. For at bekræfte at søgning i overvågningsloggen er slået til, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Værdien af egenskaben `True` *UnifiedAuditLogIngestionEnabled* angiver, at søgning i overvågningsloggen er aktiveret. Du kan finde flere oplysninger [i Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

- Du skal have tildelt rollen View-Only overvågningslogfiler eller overvågningslogfiler i en Exchange Online at søge i overvågningsloggen. Disse roller **tildeles** som standard rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser i Exchange Administration. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Hvis du vil give en bruger mulighed for at søge i overvågningsloggen med det mindste niveau af rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only-overvågningslogfiler eller Overvågningslogfiler og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan finde flere oplysninger [i Administrere rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

  > [!IMPORTANT]
  > Hvis du tildeler en bruger rollen View-Only-overvågningslogfiler eller Overvågningslogfiler på siden Tilladelser i  Microsoft 365 Overholdelsescenter, kan de ikke søge i overvågningsloggen. Du skal tildele tilladelserne i Exchange Online. Dette skyldes, at den underliggende cmdlet, der bruges til at søge i overvågningsloggen, er en Exchange Online cmdlet.

- Når en overvåget aktivitet udføres af en bruger eller administrator, genereres og gemmes en overvågningspost i overvågningsloggen for organisationen. Hvor lang tid en overvågningspost opbevares (og søgbar i overvågningsloggen), afhænger af dit Office 365- eller Microsoft 365 Enterprise-abonnement og specifikt typen af den licens, der er tildelt til bestemte brugere.

  - For brugere, der er tildelt en Office 365 E5- eller Microsoft 365 E5-licens (eller brugere med en licens til Microsoft 365 E5 Overholdelse eller Microsoft 365 E5 eDiscovery og Overvågning), overvågningsposter for Azure Active Directory, Exchange og SharePoint bevares som standard i ét år. Organisationer kan også oprette opbevaringspolitikker for overvågningslogfiler for at bevare overvågningsposter for aktiviteter i andre tjenester i op til et år. Du kan få mere at vide under [Administrere opbevaringspolitikker for overvågningslogfiler](audit-log-retention-policies.md).

    > [!NOTE]
    > Hvis din organisation har deltaget i det private eksempelprogram for den etårige opbevaring af overvågningsposter, nulstilles opbevaringsvarigheden for overvågningsposter, der blev oprettet før udrulningsdatoen for den generelle tilgængelighed, ikke.

  - For brugere, der er tildelt andre (ikke-E5) Office 365 eller Microsoft 365 licens, bevares overvågningsposter i 90 dage. Du kan finde en liste Office 365 og Microsoft 365, der understøtter samlet overvågningslogføring, i sikkerheds- og [overholdelsescenterets tjenestebeskrivelse](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Selv når overvågning af postkasser som standard er slået til, bemærker du muligvis, at postkassekontrolhændelser for nogle brugere ikke findes i overvågningsloggens søgninger i Microsoft 365 Overholdelsescenter eller via Office 365 Management Activity API. Du kan få mere at vide under [Flere oplysninger om logføring af postkassekontrol](enable-mailbox-auditing.md#more-information).

- Hvis du vil deaktivere søgning i overvågningsloggen for din organisation, kan du køre følgende kommando i en ekstern PowerShell-forbindelse til din Exchange Online organisation:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Hvis du vil aktivere overvågningssøgning igen, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Du kan få mere at vide [under Slå søgning i overvågningslog fra](turn-audit-log-search-on-or-off.md).

- Som nævnt tidligere er den underliggende cmdlet, der bruges til at søge i overvågningsloggen, en Exchange Online cmdlet, som er **Search-UnifiedAuditLog**. Det betyder, at du kan bruge denne cmdlet til at søge i overvågningsloggen i stedet for at  bruge søgeværktøjet på siden Overvågning i Microsoft 365 Overholdelsescenter. Du skal køre denne cmdlet i Exchange Online PowerShell. Få mere at vide [under Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  Hvis du vil have mere at vide om at eksportere de søgeresultater, der returneres af cmdlet'en **Search-UnifiedAuditLog til en CSV-fil**, skal du se afsnittet "Tips til eksport og visning af overvågningsloggen" i Eksportere, konfigurere og få vist [overvågningslogposter](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Hvis du vil hente data fra overvågningsloggen via programmering, anbefaler vi, at du bruger Office 365 Management Activity API i stedet for at bruge et PowerShell-script. Management Activity API Office 365 er en REST-webtjeneste, du kan bruge til at udvikle operationer, sikkerhed og løsninger til overvågning af overholdelse af regler og standarder til din organisation. Du kan finde flere oplysninger [Office 365 Reference til Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference).

- Azure Active Directory (Azure AD) er katalogtjenesten for Microsoft 365. Den samlede overvågningslog indeholder bruger-, gruppe-, program-, domæne- og katalogaktiviteter, der er <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">udført på Microsoft 365 Administration</a> eller Azure-administrationsportalen. Du kan finde en komplet liste over Azure AD-hændelser [Azure Active Directory overvågningsrapporthændelser](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Det kan tage op til 30 minutter eller 24 timer, efter en hændelse forekommer, før den tilsvarende overvågningslogpost returneres i resultaterne af en søgning i overvågningsloggen. Følgende tabel viser den tid, det tager for de forskellige tjenester i Microsoft 365.

  |Microsoft 365 tjeneste eller funktion|30 minutter|24 timer|
  |---|:---:|:---:|
  |Defender til Microsoft 365 og Threat Intelligence|![Markering.](../media/checkmark.png)||
  |Azure Active Directory (brugerlogonhændelser)||![Markering.](../media/checkmark.png)|
  |Azure Active Directory (administratorhændelser)||![Markering.](../media/checkmark.png)|
  |Forebyggelse af datatab|![Markering.](../media/checkmark.png)||
  |Dynamics 365 CRM||![Markering.](../media/checkmark.png)|
  |eDiscovery|![Markering.](../media/checkmark.png)||
  |Exchange Online|![Markering.](../media/checkmark.png)||
  |Microsoft Power Automate||![Markering.](../media/checkmark.png)|
  |Microsoft Stream|![Markering.](../media/checkmark.png)||
  |Microsoft Teams|![Markering.](../media/checkmark.png)||
  |Power Apps||![Markering.](../media/checkmark.png)|
  |Power BI|![Markering.](../media/checkmark.png)||
  |Microsoft 365 Overholdelsescenter|![Markering.](../media/checkmark.png)||
  |Følsomhedsmærkater||![Markering.](../media/checkmark.png)|
  |SharePoint Online og OneDrive for Business|![Markering.](../media/checkmark.png)||
  |Workplace Analytics|![Markering.](../media/checkmark.png)||
  |Yammer||![Markering.](../media/checkmark.png)|
  |Microsoft Forms|![Markering.](../media/checkmark.png)||
  ||||

- Overvågningslogføring for Power BI ikke er aktiveret som standard. Hvis du vil Power BI efter alle aktiviteter i overvågningsloggen, skal du aktivere overvågning Power BI administrationsportalen. Du kan finde en vejledning i afsnittet "Overvågningslogfiler" [Power BI administrationsportalen](/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Søg i overvågningsloggen

Her er processen til søgning i overvågningsloggen i Microsoft 365.

[Trin 1: Kør en søgning i overvågningsloggen](#step-1-run-an-audit-log-search)

[Trin 2: Få vist søgeresultaterne](#step-2-view-the-search-results)

[Trin 3: Eksportér søgeresultaterne til en fil](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>Trin 1: Kør en søgning i overvågningsloggen

1. Gå til <https://compliance.microsoft.com> , og log på.

    > [!TIP]
    > Brug en privat browsersession (ikke en almindelig session) til at få adgang til Microsoft 365 Overholdelsescenter, da dette vil forhindre, at de legitimationsoplysninger, du aktuelt er logget på med, bruges. Tryk **på Ctrl+Skift+N** for at åbne en InPrivate-browsersession i Microsoft Edge eller en privat browsersession i Google Chrome (kaldet et incognito-vindue).

2. Klik på Overvågning i venstre rude Microsoft 365 Overholdelsescenter **navigationsruden**.

    **Siden Overvågning** vises.

    ![Konfigurer kriterier, og klik derefter på Søg for at køre rapporten.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > Hvis linket **Start optagelse af bruger- og administratoraktivitet** vises, skal du klikke på det for at aktivere overvågning. Hvis du ikke kan se dette link, er overvågning aktiveret for din organisation.

3. På fanen **Søg** skal du konfigurere følgende søgekriterier:

   1. **Startdato og** **Slutdato**: De sidste syv dage er valgt som standard. Vælg en dato og et tidsinterval for at få vist de hændelser, der er opstået inden for den pågældende periode. Dato og klokkeslæt vises lokalt. Det maksimale datointerval, du kan angive, er 90 dage. Der vises en fejl, hvis det valgte datointerval er større end 90 dage.

    > [!TIP]
    > Hvis du bruger det maksimale datointerval på 90 dage, skal du vælge det aktuelle klokkeslæt **som Startdato**. Ellers vises en fejlmeddelelse om, at startdatoen ligger tidligere end slutdatoen. Hvis du har aktiveret overvågning inden for de seneste 90 dage, kan det maksimale datointerval ikke starte før den dato, hvor overvågning blev aktiveret.

   2. **Aktiviteter**: Klik på rullelisten for at få vist de aktiviteter, du kan søge efter. Bruger- og administratoraktiviteter er organiseret i grupper af relaterede aktiviteter. Du kan vælge bestemte aktiviteter, eller du kan klikke på aktivitetens gruppenavn for at markere alle aktiviteter i gruppen. Du kan også klikke på en markeret aktivitet for at fjerne markeringen. Når du har kørt søgningen, vises kun posterne i overvågningsloggen for de markerede aktiviteter. Hvis du **vælger Vis resultater for alle aktiviteter, vises** resultaterne for alle aktiviteter, der er udført af den valgte bruger eller gruppe af brugere.<br/><br/>Mere end 100 bruger- og administratoraktiviteter logføres i overvågningsloggen. Klik på **fanen Overvågede** aktiviteter i denne artikels emne for at få vist beskrivelserne af hver enkelt aktivitet i hver af de forskellige tjenester.

   3. **Brugere**: Klik i dette felt, og vælg derefter en eller flere brugere, der skal vises søgeresultater for. Posterne i overvågningsloggen for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i organisationen.

   4. **Fil, mappe eller** websted: Skriv noget af eller hele navnet på en fil eller mappe for at søge efter aktivitet relateret til den fil i mappen, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse, skal du sørge for at skrive den fulde URL-adressesti, eller sørg for, at hvis du skriver en del af URL-adressen, skal du ikke medtage nogen specialtegn eller mellemrum (men brug af jokertegnet (\*) understøttes).<br/><br/>Lad dette felt være tomt for at returnere poster for alle filer og mapper i organisationen.

    > [!TIP]
    >
    > - Hvis du leder efter alle aktiviteter, der er relateret til et **websted, skal** du tilføje jokertegnet (\*) efter URL-adressen for at returnere alle poster for det pågældende websted, `"https://contoso-my.sharepoint.com/personal*"`f.eks. .
    >
    > - Hvis du leder efter alle aktiviteter, der er relateret til en **fil, skal** du tilføje jokertegnet (\*) før filnavnet for at returnere alle poster for den pågældende fil, f.eks. `"*Customer_Profitability_Sample.csv"`.

4. Klik **på Søg** for at køre søgningen ved hjælp af dine søgekriterier.

   Søgeresultaterne indlæses, og efter et øjeblik vises de på en ny side. Når søgningen er færdig, vises antallet af fundne resultater. Maksimalt 50.000 hændelser vises i intervaller på 150 hændelser. Hvis mere end 50.000 hændelser opfylder søgekriterierne, vil kun de 50.000 usorterede hændelser, der returneres, blive vist.

   ![Antallet af resultater vises, når søgningen er færdig.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Tips til søgning i overvågningsloggen

- Du kan vælge bestemte aktiviteter, der skal søges efter, ved at klikke på aktivitetens navn. Eller du kan søge efter alle aktiviteter i en gruppe (f.eks Fil **- og mappeaktiviteter**) ved at klikke på gruppenavnet. Hvis en aktivitet er markeret, kan du klikke på den for at annullere markeringen. Du kan også bruge søgefeltet til at vise de aktiviteter, der indeholder det nøgleord, du skriver.

  ![Klik på aktivitetens gruppenavn for at markere alle aktiviteter.](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Du skal markere Vis **resultater for alle aktiviteter på listen** Aktiviteter  for at få vist hændelser Exchange overvågningsloggen for administratorer. Hændelser fra denne overvågningslog viser et cmdlet-navn (**f.eks. Set-Mailbox****) i kolonnen** Aktivitet i resultaterne. Du kan få mere at vide ved **at klikke på fanen** Overvågede aktiviteter i dette emne og derefter **Exchange på Administratoraktiviteter**.

  På samme måde er der nogle overvågningsaktiviteter, som ikke har et tilsvarende element på **listen** Aktiviteter. Hvis du kender navnet på handlingen for disse aktiviteter, kan du søge efter alle aktiviteter og derefter filtrere handlingerne, når du eksporterer søgeresultaterne til en CSV-fil.

- Klik **på Ryd** for at fjerne de aktuelle søgekriterier. Datointervallet vender tilbage til standarden med de seneste syv dage. Du kan også klikke på **Ryd alle for at vise resultater for alle aktiviteter for** at annullere alle markerede aktiviteter.

- Hvis der findes 50.000 resultater, kan du sandsynligvis antage, at mere end 50.000 hændelser opfylder søgekriterierne. Du kan enten afgrænse søgekriterierne og køre søgningen igen for at returnere færre resultater, eller du kan eksportere alle søgeresultaterne ved at vælge Eksportér **resultater** \> **Hent alle resultater**.

### <a name="step-2-view-the-search-results"></a>Trin 2: Få vist søgeresultaterne

Resultaterne af en søgning i overvågningsloggen vises under **Resultater på** siden Søgning **i overvågningslogfil** . Som tidligere nævnt vises maksimalt 50.000 (nyeste) hændelser i intervaller på 150 hændelser. Brug rullepanelet eller tryk på **Skift+End for** at få vist de næste 150 hændelser.

Resultaterne indeholder følgende oplysninger om hver hændelse, der returneres af søgningen:

- **Dato**: Dato og klokkeslæt (i det lokale klokkeslæt), da hændelsen indtraf.

- **IP-adresse**: IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.

   > [!NOTE]
  > For nogle tjenester kan den værdi, der vises i dette felt, være IP-adressen for et pålideligt program (f.eks. Office på internettet-apps), der ringer til tjenesten på vegne af en bruger og ikke IP-adressen på den enhed, der bruges af den person, der udførte aktiviteten. Desuden logføres IP-adressen ikke for administratoraktivitet (eller aktivitet, der er udført af en systemkonto) for Azure Active Directory-relaterede hændelser, og den værdi, der vises i dette felt, er `null`.

- **Bruger**: Den bruger (eller tjenestekonto), der udførte den handling, der udløste hændelsen.

- **Aktivitet**: Den aktivitet, der er udført af brugeren. Denne værdi svarer til de aktiviteter, du har valgt **på** rullelisten Aktiviteter. For en hændelse fra Exchange for administrator er værdien i denne kolonne en Exchange cmdlet.

- **Element**: Det objekt, der blev oprettet eller ændret som et resultat af den tilsvarende aktivitet. For eksempel den fil, der blev vist eller ændret, eller den brugerkonto, der blev opdateret. Ikke alle aktiviteter har en værdi i denne kolonne.

- **Detalje**: Yderligere oplysninger om en aktivitet. Igen har ikke alle aktiviteter en værdi.

> [!TIP]
> Klik på en kolonneoverskrift under **Resultater** for at sortere resultaterne. Du kan sortere resultaterne fra A til Å eller Å til A. Klik på overskriften  Dato for at sortere resultaterne fra ældste til nyeste eller nyeste til ældste.

#### <a name="view-the-details-for-a-specific-event"></a>Få vist oplysninger om en bestemt hændelse

Du kan få vist flere oplysninger om en begivenhed ved at klikke på hændelsesposten på listen over søgeresultater. Der vises en pop op-side, der indeholder de detaljerede egenskaber fra hændelsesposten. De egenskaber, der vises, afhænger af den tjeneste, hvor hændelsen forekommer. 

### <a name="step-3-export-the-search-results-to-a-file"></a>Trin 3: Eksportér søgeresultaterne til en fil

Du kan eksportere resultaterne af en søgning i overvågningsloggen til en fil med kommaseparerede værdier (CSV) på din lokale computer. Du kan åbne denne fil i Microsoft Excel og bruge funktioner som f.eks søgning, sortering, filtrering og opdeling af en enkelt kolonne (der indeholder flere egenskaber) i flere kolonner.

1. Kør en søgning i overvågningsloggen, og revidere søgekriterierne, indtil du har de ønskede resultater.

2. På siden med søgeresultater skal du klikke på **Eksportdownload** >  **alle resultater**.

   Alle poster fra overvågningsloggen, der opfylder søgekriterierne, eksporteres til en CSV-fil. Rådataene fra overvågningsloggen gemmes i en CSV-fil. Yderligere oplysninger fra overvågningslogposten er inkluderet i en kolonne med **navnet AuditData** i CSV-programmet.

     > [!IMPORTANT]
     > Du kan hente maksimalt 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis der downloades 50.000 poster til CSV-filen, kan du sandsynligvis antage, at mere end 50.000 hændelser opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et datointerval for at reducere antallet af poster i overvågningsloggen. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.

3. Når eksporten er fuldført, vises der en meddelelse øverst i vinduet, der beder dig om at åbne CSV-filen og gemme den på din lokale computer. Du kan også få adgang til CSV-filen i mappen Downloads.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Flere oplysninger om at eksportere og få vist søgeresultater fra overvågningsloggen

- Når du henter alle søgeresultater, indeholder CSV-filen kolonnerne **CreationDate**, **UserIds**, **Operations** og **AuditData**. Kolonnen **AuditData** indeholder yderligere oplysninger om hver enkelt hændelse (svarende til de detaljerede oplysninger, der vises på pop op-siden, når du får vist søgeresultaterne i overholdelsescenteret). Dataene i denne kolonne består af et JSON-objekt, der indeholder flere egenskaber fra overvågningslogposten. Hvert *egenskab:værdi-par* i JSON-objektet er adskilt af et komma. Du kan bruge JSON-transformeringsværktøjet i Power Query Editor i Excel til at opdele **kolonnen AuditData** i flere kolonner, så hver egenskab i JSON-objektet har sin egen kolonne. Dette giver dig mulighed for at sortere og filtrere efter en eller flere af disse egenskaber. Du kan finde en trinvis vejledning i at bruge Power Query Editor til at transformere JSON-objektet under [Eksportere, konfigurere og få vist overvågningslogposter](export-view-audit-log-records.md).

  Når du opdeler **kolonnen AuditData** , kan du filtrere kolonnen **Handlinger** for at få vist de detaljerede egenskaber for en bestemt type aktivitet.

- Når du henter alle resultater fra en søgeforespørgsel, der indeholder hændelser fra forskellige tjenester, indeholder kolonnen **AuditData** i CSV-filen forskellige egenskaber, afhængigt af hvilken tjeneste handlingen blev udført i. For eksempel omfatter poster fra Exchange og Azure AD-overvågningslogfiler en egenskab med navnet **Resultatstatus**, der angiver, om handlingen blev gennemført eller ej. Denne egenskab er ikke inkluderet for begivenheder i SharePoint. På samme SharePoint have en egenskab, der identificerer webstedets URL-adresse for fil- og mapperelaterede aktiviteter. For at mindske denne funktionsmåde skal du overveje at bruge forskellige søgninger til at eksportere resultaterne af aktiviteter fra en enkelt tjeneste.

  Hvis du vil have en beskrivelse af mange af de egenskaber, der er angivet i kolonnen **AuditData** i CSV-filen, når du henter alle resultater, og den tjeneste, hver enkelt af dem gælder for, skal du se Detaljerede egenskaber i overvågningsloggen [.](detailed-properties-in-the-office-365-audit-log.md)

## <a name="audited-activities"></a>Overvågede aktiviteter

Tabellerne i dette afsnit beskriver de aktiviteter, der overvåges i Microsoft 365. Du kan søge efter disse hændelser ved at søge i overvågningsloggen i Security and Compliance Center.

Disse tabeller grupperer relaterede aktiviteter eller aktiviteter fra en bestemt tjeneste. Tabellerne indeholder det brugervenlige navn, der vises på rullelisten  Aktiviteter, og navnet på den tilsvarende handling, der vises i de detaljerede oplysninger for en overvågningspost og i CSV-filen, når du eksporterer søgeresultaterne. Du kan finde beskrivelser af de detaljerede oplysninger [i Detaljerede egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md).

Klik på et af følgende links for at gå til en bestemt tabel.

:::row:::
    :::column:::
        [Fil- og sideaktiviteter](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Mappeaktiviteter](#folder-activities)
    :::column-end:::
    :::column:::
        [SharePoint med listeaktiviteter](#sharepoint-list-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter for anmodning om deling og adgang](#sharing-and-access-request-activities)
    :::column-end:::
    :::column:::
        [Synkroniseringsaktiviteter](#synchronization-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for webstedstilladelser](#site-permissions-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter for webstedsadministration](#site-administration-activities)
    :::column-end:::
    :::column:::
        [Exchange postkasseaktiviteter](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for brugeradministration](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Azure AD - gruppeadministrationsaktiviteter](#azure-ad-group-administration-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for programadministration](#application-administration-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for rolleadministration](#role-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter for katalogadministration](#directory-administration-activities)
    :::column-end:::
    :::column:::
        [eDiscovery-aktiviteter](#ediscovery-activities)
    :::column-end:::
    :::column:::
        [Advanced eDiscovery aktiviteter](#advanced-ediscovery-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Power BI aktiviteter](#power-bi-activities)
    :::column-end:::
    :::column:::
        [Microsoft Workplace Analytics](#workplace-analytics-activities)
    :::column-end:::
    :::column:::
        [Microsoft Teams aktiviteter](#microsoft-teams-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Microsoft Teams sundhedsaktiviteter](#microsoft-teams-healthcare-activities)
    :::column-end:::
    :::column:::
        [Microsoft Teams vagtaktiviteter](#microsoft-teams-shifts-activities)
    :::column-end:::
    :::column:::
        [Yammer aktiviteter](#yammer-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Microsoft Power Automate aktiviteter](#microsoft-power-automate-activities)
    :::column-end:::
    :::column:::
        [Microsoft Power Apps aktiviteter](#microsoft-power-apps-activities)
    :::column-end:::
    :::column:::
        [Microsoft Stream-aktiviteter](#microsoft-stream-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter i Indholdsstifinder](#content-explorer-activities)
    :::column-end:::
    :::column:::
        [Karantæneaktiviteter](#quarantine-activities)
    :::column-end:::
    :::column:::
        [Microsoft Forms-aktiviteter](#microsoft-forms-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter for følsomhedsmærkat](#sensitivity-label-activities)
    :::column-end:::
    :::column:::
        [Opbevaringspolitik og opbevaringsmærkataktiviteter](#retention-policy-and-retention-label-activities)
    :::column-end:::
    :::column:::
        [Briefing af mailaktiviteter](#briefing-email-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [MyAnalytics-aktiviteter](#myanalytics-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for informationsbarrierer](#information-barriers-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter for dispositionsgennemsyn](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter til overholdelse af regler og standarder i kommunikation](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Rapportere aktiviteter](#report-activities)
    :::column-end:::
    :::column:::
        [Exchange administratoraktiviteter](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Fil- og sideaktiviteter

I følgende tabel beskrives fil- og sideaktiviteterne i SharePoint Online og OneDrive for Business.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Åbnet fil|FileAccessed|En bruger eller systemkonto får adgang til en fil. Når en bruger får adgang til en fil, logføres hændelsen FileAccessed ikke igen for den samme bruger for den samme fil i de næste fem minutter.|
|(ingen)|FileAccessedExtended|Dette er relateret til aktiviteten "Åbnet fil" (FileAccessed). En FileAccessedExtended-begivenhed logføres, når den samme person kontinuerligt får adgang til en fil i en længere periode (op til 3 timer). <br/><br/> Logføring af FileAccessedExtended-hændelser er at reducere antallet af FileAccessed-hændelser, der logføres, når der kontinuerligt opnås adgang til en fil. Dette er med til at reducere støj fra flere FileAccessed-poster for det, der i bund og grund er den samme brugeraktivitet, og gør det muligt at fokusere på den indledende (og mere vigtige) FileAccessed-begivenhed.|
|Ændret opbevaringsnavn for en fil|ComplianceSettingChanged|En opbevaringsetiket blev anvendt på eller fjernet fra et dokument. Denne hændelse udløses, når en opbevaringsetiket anvendes manuelt eller automatisk på en meddelelse.|
|Status for en post blev ændret til låst|LockRecord|Poststatus for et opbevaringsnavn, der klassificerer et dokument som en post, blev låst. Det betyder, at dokumentet ikke kan ændres eller slettes. Kun brugere, der som minimum er tildelt bidragydertilladelse til et websted, kan ændre poststatus for et dokument.|
|Status for en post blev ændret til ulåst|LåsPost op|Poststatus for et opbevaringsnavn, der klassificerer et dokument som en post, blev låst op. Det betyder, at dokumentet kan ændres eller slettes. Kun brugere, der som minimum er tildelt bidragydertilladelse til et websted, kan ændre poststatus for et dokument.|
|Fil tjekket ind|FileCheckedIn|Brugeren tjekker et dokument ind, som brugeren har tjekket ud fra et dokumentbibliotek.|
|Fil tjekket ud|FileCheckedOut|Brugeren tjekker et dokument ud, der er placeret i et dokumentbibliotek. Brugere kan tjekke dokumenter ud og foretage ændringer i dokumenter, der er blevet delt med dem.|
|Kopieret fil|FileCopied|Brugeren kopierer et dokument fra et websted. Den kopierede fil kan gemmes i en anden mappe på webstedet.|
|Slettet fil|FileDeleted|Brugeren sletter et dokument fra et websted.|
|Slettet fil fra papirkurv|FileDeletedFirstStageRecycleBin|Brugeren sletter en fil fra papirkurven på et websted.|
|Slettet fil fra papirkurv for anden fase|FileDeletedSecondStageRecycleBin|Brugeren sletter en fil fra papirkurven for andet trin på et websted.|
|Slettet fil markeret som en post|OptagSlette|Et dokument eller en mail, der blev markeret som en post, er blevet slettet. Et element betragtes som en post, når der anvendes en opbevaringsetiket, der markerer elementer som en post, på indholdet.|
|Registrerede dokumentfølsomhedsuoverensstemmelse|DocumentSensitivityMismatchDetected|Brugeren overfører et dokument til et websted, der er beskyttet med en følsomhedsmærkat, og dokumentet har en etiket med højere prioritetsfølsomhed end følsomhedsmærkatet, der er anvendt på webstedet. Eksempelvis uploades et dokument med navnet Fortroligt til et websted med navnet Generelt. <br/><br/> Denne hændelse udløses ikke, hvis dokumentet har en følsomhedsmærkat med lavere prioritet end det følsomhedsmærkat, der er anvendt på webstedet. Eksempelvis uploades et dokument med navnet Generelt til et websted med navnet Fortroligt. Du kan finde flere oplysninger om følsomhedsmærkatprioritet [under Etiketprioritet (ordre betyder noget)](sensitivity-labels.md#label-priority-order-matters).|
|Registreret malware i filen|FileMalwareDetected|SharePoint et antivirusprogram registrerer malware i en fil.|
|Udtjekning af fil kasseret|FileCheckOutDiscarded|Brugeren kasserer (eller fortryder) en fil, der er tjekket ud. Det betyder, at de ændringer, de har foretaget i filen, da den blev tjekket ud, kasseres og ikke gemmes i versionen af dokumentet i dokumentbiblioteket.|
|Downloadet fil|FileDownloaded|Brugeren downloader et dokument fra et websted.|
|Ændret fil|FilÆndret|Bruger- eller systemkonto ændrer indholdet eller egenskaberne for et dokument på et websted. Systemet venter fem minutter, før det logger en anden FilÆndret hændelse, når den samme bruger ændrer indholdet eller egenskaberne for det samme dokument.|
|(ingen)|FileModifiedExtended|Dette er relateret til aktiviteten "Ændret fil" (FilÆndret). En FilÆndretEkvent hændelse logføres, når den samme person kontinuerligt ændrer en fil i en længere periode (op til 3 timer). <br/><br/> Formålet med at logføre FileModifiedExtended-hændelser er at reducere antallet af FilÆndrede hændelser, der logføres, når en fil kontinuerligt ændres. Dette er med til at reducere støj fra flere filændrede poster for det, der i bund og grund er den samme brugeraktivitet, og gør det muligt at fokusere på den indledende (og mere vigtige) filændrede begivenhed.|
|Flyttet fil|FileMoved|Brugeren flytter et dokument fra dets aktuelle placering på et websted til en ny placering.|
|(ingen)|FilePreviewed|Brugeren får vist filer på et SharePoint eller OneDrive for Business websted. Disse hændelser sker typisk i meget trafik baseret på en enkelt aktivitet, f.eks. visning af et billedgalleri.|
|Udført søgeforespørgsel|SøgForespørgigFormular|Brugeren eller systemkonto udfører en søgning i SharePoint eller OneDrive for Business. Nogle almindelige scenarier, hvor en tjenestekonto udfører en søgeforespørgsel, omfatter anvendelse af en venteliste og opbevaringspolitik for eDiscovery på websteder og OneDrive-konti og automatisk anvendelse af opbevarings- eller følsomhedsmærkater på webstedsindhold.|
|En fil genbrugt | FileRecycled | Brugeren flytter en fil til SharePoint Papirkurv. |
|Genbrugt en mappe | FolderRecycled | Brugeren flytter en mappe til SharePoint Papirkurv. |
|Alle underordnede versioner af filen er genbrugt|FileVersionsAllMinorsRecycled|Brugeren sletter alle underordnede versioner i versionsoversigten for en fil. De slettede versioner flyttes til webstedets papirkurv.|
|Alle versioner af filen er genbrugt|FileVersionsAllRecycled|Brugeren sletter alle versioner i versionsoversigten for en fil. De slettede versioner flyttes til webstedets papirkurv.|
|Version af filen genbrugt|FileVersionRecycled|Brugeren sletter en version i versionsoversigten for en fil. Den slettede version flyttes til webstedets papirkurv.|
|Omdøbt fil|FileRenamed|Brugeren omdøber et dokument på et websted.|
|Gendannet fil|FilRestored|Brugeren gendanner et dokument fra papirkurven på et websted.|
|Uploadet fil|FilUploaded|Brugeren overfører et dokument til en mappe på et websted.|
|Vist side|PageViewed|Bruger får en side på et websted til at se. Dette omfatter ikke brug af en webbrowser til at få vist filer, der er placeret i et dokumentbibliotek. Når en bruger får vist en side, logføres hændelsen PageViewed ikke igen for den samme bruger for den samme side i de næste fem minutter.|
|(ingen)|PageViewedExtended|Dette er relateret til aktiviteten "Vist side" (Sidevisning). En PageViewedExtended-begivenhed logføres, når den samme person kontinuerligt får vist en webside i en længere periode (op til 3 timer). <br/><br/> Formålet med at logge PageViewedExtended-hændelser er at reducere antallet af PageViewed-hændelser, der logføres, når en side kontinuerligt vises. Dette er med til at reducere støj fra flere PageViewed-poster for, hvad der i bund og grund er den samme brugeraktivitet, og gør det muligt at fokusere på den indledende (og mere vigtige) PageViewed-begivenhed.|
|Visning signaleret af klient|ClientViewSignaled|En brugers klient (f.eks. websted eller mobilapp) har signaleret, at den angivne side er blevet set af brugeren. Denne aktivitet logføres ofte efter en Sidebegivenhed for en side. <br/><br/>**BEMÆRK**! Da ClientViewSignaled-hændelser er signalerede af klienten i stedet for serveren, er det muligt, at hændelsen ikke logføres af serveren og derfor muligvis ikke vises i overvågningsloggen. Det er også muligt, at oplysningerne i overvågningsposten muligvis ikke er troværdige. Men fordi brugerens identitet valideres af det token, der bruges til at oprette signalet, er brugerens identitet, der er angivet i den tilsvarende overvågningspost, nøjagtig. Systemet venter fem minutter, før den logføres den samme hændelse, når den samme brugers klient viser, at siden er blevet vist igen af brugeren.|
|(ingen)|PagePrefetched|En brugers klient (f.eks. websted eller mobilapp) har anmodet om den angivne side for at forbedre ydeevnen, hvis brugeren går til den. Denne hændelse logføres for at angive, at sideindholdet er blevet serveret for brugerens klient. Denne hændelse er ikke en endelig indikation af, at brugeren har navigeret til siden. <br/><br/> Når sideindholdet gengives af klienten (i henhold til brugerens anmodning), skal der genereres en ClientViewSignaled-hændelse. Ikke alle klienter understøtter, der angiver en forudhentning, og derfor kan nogle forudindstillede aktiviteter i stedet blive logført som PageViewed-hændelser.|
||||

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>Ofte stillede spørgsmål om FileAccessed- og FilePreviewed-begivenheder

**Kan alle ikke-brugeraktiviteter udløse overvågningsposter, der indeholder en brugeragent som f.eks. "OneDriveMpc-Transform_Thumbnail"?**

Vi er ikke opmærksomme på scenarier, hvor ikke-brugerhandlinger genererer hændelser som disse. Brugerhandlinger som at åbne et brugerprofilkort (ved at klikke på brugerens navn eller mailadresse i en meddelelse i Outlook på internettet) ville generere lignende hændelser.

**Er opkald til OneDriveMpc-Transform_Thumbnail tilsigtet at blive udløst af brugeren?**

Nej. Men lignende hændelser kan logføres som et resultat af en browserforhentning.

**Hvis vi ser en filePreviewed-hændelse, der kommer fra en Microsoft-registreret IP-adresse, betyder det så, at eksemplet blev vist på skærmen på brugerens enhed?**

Nej. Hændelsen er muligvis blevet logført som et resultat af en browserforhentning.

**Er der scenarier, hvor en brugers visning af et dokument genererer FileAccessed-hændelser?**

Både hændelserne FilePreviewed og FileAccessed angiver, at en brugers opkald har ført til læsning af filen (eller en læsning af en miniaturegengivelse af filen). Selvom disse hændelser er beregnet til at være i overensstemmelse med forhåndsvisning vs. adgang til formålet, er begivenheden ikke en garanti for brugerens formål.

#### <a name="the-appsharepoint-user-in-audit-records"></a>\@Appsharepoint-brugeren i overvågningsposter

I overvågningsposterne for nogle filaktiviteter (og andre SharePoint-relaterede aktiviteter) bemærker du muligvis, at den bruger, der udførte aktiviteten (identificeret i felterne Bruger og Bruger-id) er app@sharepoint. Dette angiver, at den "bruger", der udførte aktiviteten, var et program. I dette tilfælde har programmet fået tilladelse i SharePoint til at udføre handlinger for hele organisationen (f.eks. søge på et SharePoint-websted eller en OneDrive-konto) på vegne af en bruger, administrator eller tjeneste. Denne proces med at give tilladelser til et program kaldes SharePoint *kun appadgang*. Dette angiver, at den godkendelse, der præsenteres SharePoint at udføre en handling, blev foretaget af et program i stedet for en bruger. Dette er grunden til, app@sharepoint identificeres i visse overvågningsposter. Du kan finde flere oplysninger [i Tildele adgang SharePoint kun app](/sharepoint/dev/solution-guidance/security-apponly-azureacs).

Eksempelvis identificeres app@sharepoint ofte som brugeren ved hændelserne "Udført søgeforespørgsel" og "Åbnet fil". Det skyldes, at et program med SharePoint App-Only adgang i din organisation udfører søgeforespørgsler og adgang til filer, når du anvender opbevaringspolitikker på websteder og OneDrive konti.

Her er nogle andre scenarier, hvor app@sharepoint kan identificeres i en overvågningspost som den bruger, der udførte en aktivitet:

- Microsoft 365 grupper. Når en bruger eller administrator opretter en ny gruppe, oprettes der overvågningsposter for at oprette en gruppe af websteder, opdatere lister og føje medlemmer til SharePoint gruppe. Disse opgaver udføres et program på vegne af den bruger, der har oprettet gruppen.

- Microsoft Teams. Ligesom Microsoft 365 grupper genereres der overvågningsposter til oprettelse af en gruppe af websteder, opdatering af lister og tilføjelse af medlemmer til en SharePoint-gruppe, når der oprettes et team.

- Funktioner til overholdelse af regler og standarder. Når en administrator implementerer overholdelsesfunktioner, f.eks opbevaringspolitikker, eDiscovery-ventende elementer og automatisk anvendelse af følsomhedsmærkater.

I disse og andre scenarier vil du også bemærke, at flere overvågningsposter med app@sharepoint som den angivne bruger blev oprettet inden for en kort tidsramme, ofte inden for et par sekunder fra hinanden. Dette indikerer også, at de sandsynligvis blev udløst af den samme brugerinitierede opgave. Desuden kan felterne ApplicationDisplayName og EventData i overvågningsposten hjælpe dig med at identificere det scenarie eller program, der udløste hændelsen.

### <a name="folder-activities"></a>Mappeaktiviteter

I følgende tabel beskrives mappeaktiviteterne i SharePoint Online og OneDrive for Business. Som beskrevet tidligere angiver overvågningsposterne for nogle SharePoint-aktiviteter, at app@sharepoint-brugeren udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan få mere at vide [under Appsharepoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Kopieret mappe|FolderCopied|Brugeren kopierer en mappe fra et websted til en anden placering i SharePoint eller OneDrive for Business.|
|Oprettet mappe|FolderCreated|Brugeren opretter en mappe på et websted.|
|Slettet mappe|FolderDeleted|Brugeren sletter en mappe fra et websted.|
|Slettet mappe fra Papirkurv|FolderDeletedFirstStageRecycleBin|Brugeren sletter en mappe fra papirkurven på et websted.|
|Slettet mappe fra Papirkurv for anden fase|FolderDeletedSecondStageRecycleBin|Brugeren sletter en mappe fra papirkurven for andet trin på et websted.|
|Ændret mappe|FolderModified|Brugeren ændrer en mappe på et websted. Dette omfatter ændring af mappens metadata, f.eks. ændring af mærker og egenskaber.|
|Flyttet mappe|FolderMoved|Brugeren flytter en mappe til en anden placering på et websted.|
|Omdøbt mappe|FolderRenamed|Brugeren omdøber en mappe på et websted.|
|Gendannet mappe|FolderRestored|Brugeren gendanner en slettet mappe fra papirkurven på et websted.|
||||

### <a name="sharepoint-list-activities"></a>SharePoint med listeaktiviteter

I følgende tabel beskrives aktiviteter, der er relateret til, hvornår brugere interagerer med lister og listeelementer i SharePoint Online. Som beskrevet tidligere angiver overvågningsposterne for nogle SharePoint-aktiviteter, at app@sharepoint-brugeren udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan få mere at vide [under Appsharepoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Oprettet liste|ListCreated|En bruger oprettede en SharePoint liste.|
|Oprettet listekolonne|ListColumnCreated|En bruger har oprettet SharePoint kolonnelisten. En listekolonne er en kolonne, der er knyttet til en eller flere SharePoint lister.|
|Listeindholdstype oprettet|ListContentTypeCreated|En bruger har oprettet en listeindholdstype. En listeindholdstype er en indholdstype, der er knyttet til en eller flere SharePoint lister.|
|Oprettet listeelement|ListItemCreated|En bruger har oprettet et element på en eksisterende SharePoint liste.|
|Webstedskolonne oprettet|SiteColumnCreated|En bruger oprettede en SharePoint webstedskolonne. En webstedskolonne er en kolonne, der ikke er knyttet til en liste. En webstedskolonne er også en metadatastruktur, der kan bruges af en liste i et bestemt websted.|
|Webstedsindholdstype oprettet|Webstedsindholdstype oprettet|En bruger har oprettet en webstedsindholdstype. En webstedsindholdstype er en indholdstype, der er knyttet til det overordnede websted.|
|Slettet liste|ListDeleted|En bruger har slettet SharePoint liste.|
|Slettet listekolonne|Listekolonne slettet|En bruger har slettet SharePoint en listekolonne.|
|Slettet listeindholdstype|ListContentTypeDeleted|En bruger har slettet en listeindholdstype.|
|Slettet listeelement|Listeelement slettet|En bruger har slettet SharePoint et listeelement.|
|Kolonnen Slettet websted|SiteColumnDeleted|En bruger har slettet en SharePoint webstedskolonne.|
|Slettet webstedsindholdstype|SiteContentTypeDeleted|En bruger har slettet en webstedsindholdstype.|
|Genbrugt listeelement|ListItemRecycled|En bruger har flyttet SharePoint et listeelement til Papirkurv.|
|Gendannet liste|ListRestored|En bruger gendannede SharePoint liste fra Papirkurv.|
|Gendannet listeelement|ListItemRestored|En bruger gendannede SharePoint et listeelement fra Papirkurv.|
|Opdateret liste|ListeOpdateret|En bruger har opdateret SharePoint listen ved at ændre en eller flere egenskaber.|
|Opdateret listekolonne|ListColumnUpdated|En bruger har opdateret SharePoint kolonnelisten ved at ændre en eller flere egenskaber.|
|Listeindholdstype opdateret|ListContentTypeUpdated|En bruger har opdateret en listeindholdstype ved at ændre en eller flere egenskaber.|
|Opdateret listeelement|ListItemUpdated|En bruger har opdateret SharePoint et listeelement ved at ændre en eller flere egenskaber.|
|Webstedskolonne opdateret|SiteColumnUpdated|En bruger har opdateret SharePoint webstedskolonne ved at ændre en eller flere egenskaber.|
|Webstedsindholdstype opdateret|SiteContentTypeUpdated|En bruger har opdateret en webstedsindholdstype ved at ændre en eller flere egenskaber.|
|Vist listeelement|ListItemViewed|En bruger har set SharePoint et listeelement. Når en bruger får vist et listeelement, logføres hændelsen ListItemViewed ikke igen for den samme bruger for samme listeelement i de næste fem minutter.|
||||

### <a name="sharing-and-access-request-activities"></a>Aktiviteter for anmodning om deling og adgang

I følgende tabel beskrives aktiviteter for anmodning om deling og adgang i SharePoint Online og OneDrive for Business. Ved delingshændelser  identificerer kolonnen **Detaljer under Resultater** navnet på den bruger eller gruppe, som elementet blev delt med, og om den pågældende bruger eller gruppe er medlem eller gæst i organisationen. Få mere at vide under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).

> [!NOTE]
> Brugere kan enten  *være medlemmer*  eller  *gæster*  baseret på egenskaben UserType for brugerobjektet. Et medlem er som regel en medarbejder, og en gæst er som regel en samarbejdspartner uden for organisationen. Når en bruger accepterer en invitation til deling (og ikke allerede er en del af din organisation), oprettes der en gæstekonto til vedkommende i organisationens adresseliste. Når gæstebrugeren har en konto i kataloget, kan ressourcer deles direkte med vedkommende (uden at der kræves en invitation).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Tilladelsesniveau føjet til gruppen af websteder|PermissionLevelAdded|Et tilladelsesniveau blev føjet til en gruppe af websteder.|
|Anmodning om adgang accepteret|AccessRequestAccepted|En anmodning om adgang til et websted, en mappe eller et dokument er blevet accepteret, og brugeren har fået tildelt adgang.|
|Invitation til deling accepteret|SharingInvitationAccepted|Brugeren (medlem eller gæst) har accepteret en invitation til deling og har fået tildelt adgang til en ressource. Denne hændelse indeholder oplysninger om den bruger, der blev inviteret, og den mailadresse, der blev brugt til at acceptere invitationen (de kan være forskellige). Denne aktivitet ledsages ofte af en anden hændelse, der beskriver, hvordan brugeren blev tildelt adgang til ressourcen, f.eks. tilføjelse af brugeren til en gruppe, der har adgang til ressourcen.|
|Blokeret invitation til deling|SharingInvitationBlocked|En invitation til deling, der sendes af en bruger i organisationen, er blokeret på grund af en ekstern delingspolitik, der tillader eller afviser ekstern deling, der er baseret på domænet for målbrugeren. I dette tilfælde blev invitationen til deling blokeret, fordi: <br/> Destinationsbrugereens domæne er ikke medtaget på listen over tilladte domæner. <br/> Eller <br/> Destinationsbrugereens domæne er medtaget på listen over blokerede domæner. <br/> Du kan finde flere oplysninger om at tillade eller blokere ekstern deling baseret på domæner i Begrænset domænedeling [i SharePoint Online og OneDrive for Business](/sharepoint/restricted-domains-sharing).|
|Anmodning om adgang oprettet|AccessRequestCreated|Brugeren anmoder om adgang til et websted, en mappe eller et dokument, som brugeren ikke har adgangstilladelse til.|
|Link, der kan deles af virksomhed, oprettet|CompanyLinkCreated|Brugeren oprettede et link til en ressource for hele virksomheden. Links for hele virksomheden kan kun bruges af medlemmer af organisationen. De kan ikke bruges af gæster.|
|Et anonymt link oprettet|AnonymtLinkOprettet|Brugeren har oprettet et anonymt link til en ressource. Alle med dette link kan få adgang til ressourcen uden at skulle godkendes.|
|Et sikkert link er oprettet|SecureLinkCreated|Et sikkert link til deling blev oprettet til dette element.|
|Invitation til deling oprettet|SharingInvitationCreated|Brugeren har delt en ressource SharePoint Online eller OneDrive for Business med en bruger, der ikke findes i organisationens adresseliste.|
|Et sikkert link er blevet slettet|SecureLinkDeleted|Et sikkert link til deling blev slettet.|
|Anmodning om adgang nægtet|AccessRequestDenied|En anmodning om adgang til et websted, en mappe eller et dokument blev afvist.|
|Link, der kan deles af virksomhed, fjernet|CompanyLinkRemoved|Brugeren har fjernet et link til en ressource for hele virksomheden. Linket kan ikke længere bruges til at få adgang til ressourcen.|
|Et anonymt link fjernet|AnonymtLink Flyttet|Brugeren har fjernet et anonymt link til en ressource. Linket kan ikke længere bruges til at få adgang til ressourcen.|
|Delt fil, mappe eller websted|SharingSet|Brugeren (medlem eller gæst) har delt en fil, en mappe eller et websted i SharePoint eller OneDrive for Business med en bruger i organisationens adresseliste. Værdien i kolonnen **Detaljer** for denne aktivitet identificerer navnet på den bruger, ressourcen blev delt med, og om denne bruger er medlem eller gæst. <br/><br/> Denne aktivitet ledsages ofte af en anden hændelse, der beskriver, hvordan brugeren blev tildelt adgang til ressourcen. Det kan f.eks. være at føje brugeren til en gruppe, der har adgang til ressourcen.|
|Adgangsanmodning er blevet opdateret|AccessRequestUpdated|En adgangsanmodning til et element blev opdateret.|
|Et anonymt link opdateret|AnonymtLinkOpderet|Brugeren har opdateret et anonymt link til en ressource. Det opdaterede felt er medtaget i egenskaben EventData, når du eksporterer søgeresultaterne.|
|En invitation til deling er blevet opdateret|SharingInvitationUpdated|En ekstern invitation til deling er blevet opdateret.|
|Et anonymt link brugt|AnonymtLinkBrugt|En anonym bruger fik adgang til en ressource ved hjælp af et anonymt link. Brugerens identitet kan være ukendt, men du kan få andre oplysninger, f.eks. brugerens IP-adresse.|
|Ikke-delt fil, mappe eller websted|SharingRevoked|Brugeren (medlem eller gæst) har ophævet delingen af en fil, mappe eller et websted, der tidligere er blevet delt med en anden bruger.|
|Et link, der kan deles af virksomhed, brugt|CompanyLinkUsed|Brugeren fik adgang til en ressource ved hjælp af et link for hele virksomheden.|
|Et sikkert link er blevet brugt|SecureLinkUsed|En bruger brugte et sikkert link.|
|Brugeren er føjet til et sikkert link|AddedToSecureLink|En bruger blev føjet til listen over de enheder, der kan bruge et sikkert link til deling.|
|Brugeren er fjernet fra et sikkert link|RemovedFromSecureLink|En bruger blev fjernet fra listen over de enheder, der kan bruge et sikkert link til deling.|
|Invitation til deling trukket tilbage|SharingInvitationRevoked|Brugeren har trukket en invitation til deling af en ressource tilbage.|
||||

### <a name="synchronization-activities"></a>Synkroniseringsaktiviteter

I følgende tabel vises filsynkroniseringsaktiviteter i SharePoint Online og OneDrive for Business.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Computer tilladt at synkronisere filer|AdministreretSynkroniseringsklient Tilladt|Brugeren opretter en synkroniseringsrelation til et websted. Synkroniseringsrelationen er vellykket, fordi brugerens computer er medlem af et domæne, der er blevet føjet til listen over domæner (kaldet liste over modtagere, der er tillid til), der har adgang til dokumentbiblioteker i organisationen. <br/><br/> Du kan finde flere oplysninger om denne funktion i [Brug Windows PowerShell-cmdlet'er til at aktivere OneDrive-synkronisering for](/powershell/module/sharepoint-online/) domæner, der findes på listen over modtagere, der er tillid til.|
|Computer blokeret fra at synkronisere filer|Ikke-administreretSynkroniseringsklientBlokeret|Brugeren forsøger at etablere en synkroniseringsrelation til et websted fra en computer, der ikke er medlem af  *organisationens*  domæne eller er medlem af et domæne, der ikke er blevet føjet til listen over domæner (kaldet liste over modtagere, der er tillid til), der har adgang til dokumentbiblioteker i organisationen. Synkroniseringsrelationen er ikke tilladt, og brugerens computer er blokeret fra at synkronisere, hente eller uploade filer på et dokumentbibliotek. <br/><br/> Du kan finde oplysninger om denne funktion i [Brug Windows PowerShell-cmdlet'er til at OneDrive-synkronisering for](/powershell/module/sharepoint-online/) domæner, der findes på listen over modtagere, der er tillid til.|
|Filer hentet til computer|FilSynkroniseringDownloadedFull|Brugeren downloader en fil til sin computer fra et SharePoint dokumentbibliotek eller en OneDrive for Business ved hjælp OneDrive-synkronisering-app (OneDrive.exe).|
|Filændringer hentet til computer|FilSynkroniseringHentningDeltDelt|Denne hændelse frarådes sammen med den gamle OneDrive for Business -synkroniseringsapp (Groove.exe).|
|Filer sendt til dokumentbibliotek|FilSynkroniseringUploadedFull|Brugeren overfører en ny fil eller ændringer til en fil i SharePoint dokumentbibliotek eller OneDrive for Business ved hjælp OneDrive-synkronisering-app (OneDrive.exe).|
|Filændringer sendt til dokumentbibliotek|FilSynkroniseringUploadedPartial|Denne hændelse frarådes sammen med den gamle OneDrive for Business -synkroniseringsapp (Groove.exe).|
||||

### <a name="site-permissions-activities"></a>Aktiviteter for webstedstilladelser

I følgende tabel vises hændelser, der vedrører tildeling af tilladelser i SharePoint og brug af grupper til at give (og tilbagekalde) adgang til websteder. Som beskrevet tidligere angiver overvågningsposterne for nogle SharePoint-aktiviteter, at app@sharepoint-brugeren udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan få mere at vide [under Appsharepoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Administrator for gruppe af websteder tilføjet|SiteCollectionAdminAdded|Administratoren eller ejeren af gruppen af websteder tilføjer en person som administrator for en gruppe af websteder for et websted. Administratorer af grupper af websteder har alle kontroltilladelser til gruppen af websteder og alle underordnede websteder. Denne aktivitet logføres også, når en administrator giver sig selv adgang til en brugers OneDrive-konto (ved at redigere brugerprofilen i SharePoint Administration eller ved hjælp af [Microsoft 365 Administration](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)).|
|Bruger eller gruppe føjet SharePoint gruppe|AddedToGroup|Brugeren har føjet et medlem eller gæst til SharePoint gruppe. Dette kan have været en bevidst handling eller resultatet af en anden aktivitet, f.eks. en delingshændelse.|
|Brudt nedarvningen af tilladelsesniveau|PermissionLevelsInheritanceBroken|Et element blev ændret, så det ikke længere nedarver tilladelsesniveauer fra det overordnede element.|
|Brudt nedarvning af deling|SharingInheritanceBroken|Et element blev ændret, så det ikke længere nedarver delingstilladelser fra det overordnede element.|
|Oprettet gruppe|GruppeAdderet|Webstedets administrator eller ejer opretter en gruppe for et websted eller udfører en opgave, der resulterer i, at der oprettes en gruppe. Første gang en bruger opretter et link for at dele en fil, føjes en systemgruppe f.eks. til brugerens websted OneDrive for Business websted. Hændelsen kan også være resultatet af en bruger, der opretter et link med redigeringstilladelser til en delt fil.|
|Slettet gruppe|Gruppe Flyttet|Brugeren sletter en gruppe fra et websted.|
|Ændring af indstilling for adgangsanmodning|WebRequestAccessModified|Indstillingerne for adgangsanmodninger blev ændret på et websted.|
|Ændret indstilling for "Medlemmer kan dele"|WebMembersCanShareModified|Indstillingen **Medlemmer kan dele** er blevet ændret på et websted.|
|Ændret tilladelsesniveau for en gruppe af websteder|PermissionLevelModified|Et tilladelsesniveau blev ændret for en gruppe af websteder.|
|Webstedstilladelser ændret|SitePermissionsModified|Webstedets administrator eller ejer (eller systemkonto) ændrer det tilladelsesniveau, der er tildelt en gruppe på et websted. Denne aktivitet logføres også, hvis alle tilladelser fjernes fra en gruppe. <br/><br/> **BEMÆRK**! Denne handling frarådes i SharePoint Online. Hvis du vil finde relaterede hændelser, kan du søge efter andre tilladelsesrelaterede aktiviteter, f.eks. Administrator for gruppe af **websteder, Bruger** eller gruppe føjet til **SharePoint-gruppe****, Bruger** tilladt at oprette **grupper, Oprettet** gruppe og Slettet **gruppe.**|
|Fjernede tilladelsesniveau fra en gruppe af websteder|PermissionLevelRemoved|Et tilladelsesniveau blev fjernet fra en gruppe af websteder.|
|Administrator for gruppe af websteder fjernet|SiteCollectionAdminRemoved|Administratoren eller ejeren af gruppen af websteder fjerner en person som administrator for en gruppe af websteder for et websted. Denne aktivitet logføres også, når en administrator fjerner sig fra listen over administratorer af grupper af websteder for en brugers OneDrive-konto (ved at redigere brugerprofilen i SharePoint Administration).  Hvis du vil returnere denne aktivitet i overvågningsloggens søgeresultater, skal du søge efter alle aktiviteter.|
|Bruger eller gruppe fjernet SharePoint gruppe|FjernetFraGruppe|Brugeren har fjernet et medlem eller gæst fra SharePoint gruppe. Dette kan have været en bevidst handling eller resultatet af en anden aktivitet, f.eks. en hændelse med at dele.|
|Administratortilladelser for websted anmodet om|SiteAdminChangeRequest|Brugeren anmoder om at blive tilføjet som administrator for en gruppe af websteder for en gruppe af websteder. Administratorer af grupper af websteder har alle kontroltilladelser til gruppen af websteder og alle underordnede websteder.|
|Nedarvning af deling gendannet|SharingInheritanceReset|En ændring blev foretaget, så et element nedarver delingstilladelser fra det overordnede element.|
|Gruppe opdateret|GruppeOpdateret|Webstedets administrator eller ejer ændrer indstillingerne for en gruppe for et websted. Dette kan omfatte ændring af gruppens navn, hvem der kan se eller redigere gruppemedlemskabet, og hvordan anmodninger om medlemskab håndteres.|
||||

### <a name="site-administration-activities"></a>Aktiviteter for webstedsadministration

I følgende tabel vises hændelser, der skyldes webstedsadministrationsopgaver i SharePoint Online. Som beskrevet tidligere angiver overvågningsposterne for nogle SharePoint-aktiviteter, at app@sharepoint-brugeren udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan få mere at vide [under Appsharepoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet tilladt dataplacering|AllowedDataLocationAdded|En SharePoint eller en global administrator har tilføjet en tilladt dataplacering i et multi-geo-miljø.|
|Undtaget brugeragent tilføjet|UndtagetBrugerAgentSæt|En SharePoint eller en global administrator har føjet en brugeragent til listen over undtagede brugeragenter SharePoint Administration.|
|Tilføjede geoplaceringsadministrator|GeoAdminAdded|En SharePoint eller en global administrator har tilføjet en bruger som geoadministrator for en placering.|
|Bruger tilladt at oprette grupper|AllowGroupCreationSet|Webstedets administrator eller ejer føjer et tilladelsesniveau til et websted, så en bruger, der er tildelt denne tilladelse, kan oprette en gruppe for webstedet.|
|Annulleret webstedets geografiske flytning|SiteGeoMoveCancelled|En SharePoint eller global administrator annullerer et SharePoint eller OneDrive websteds geografiske flytning. Multi-Geo funktionen lader en organisation strække sig over flere Microsoft-datacentergege områder, der kaldes geos. Du kan finde flere [oplysninger under Multi-Geo Capabilities i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|En delingspolitik ændret|DelingspolitikÆndret|En SharePoint eller global administrator har ændret en SharePoint politik for deling ved hjælp af Microsoft 365 Administration, SharePoint Administration eller SharePoint Online Management Shell. Enhver ændring af indstillingerne i organisationens delingspolitik logføres. Politikken, der er blevet ændret, er **identificeret i feltet ModifiedProperties** i de detaljerede egenskaber for hændelsesposten.|
|Politik for enhedsadgang ændret|DeviceAccessPolicyChanged|En SharePoint eller global administrator har ændret politikken for ikke-administrerede enheder i organisationen. Denne politik styrer adgangen til SharePoint, OneDrive og Microsoft 365 fra enheder, der ikke er forbundet til din organisation. Konfiguration af denne politik kræver et Enterprise Mobility + Security abonnement. Få mere at vide under [Kontrollér adgang fra ikke-administrerede enheder](/sharepoint/control-access-from-unmanaged-devices).|
|Undtaget brugeragenter ændret|CustomizeExemptUsers|En SharePoint eller global administrator har tilpasset listen over undtagede brugeragenter SharePoint Administration. Du kan angive, hvilke brugeragenter, der skal fritages fra at modtage en hel webside, der skal indekseres. Det betyder, at når en brugeragent, du har angivet som undtaget, støder på en InfoPath-formular, returneres formularen som en XML-fil i stedet for en hel webside. Dette gør indeksering af InfoPath-formularer hurtigere.|
|Politik for netværksadgang ændret|NetworkAccessPolicyChanged|En SharePoint eller global administrator har ændret politikken for den placeringsbaserede adgang (også kaldet en pålidelig netværksgrænse) i SharePoint Administration eller ved hjælp af SharePoint Online PowerShell. Denne type politik styrer, hvem der kan få adgang SharePoint og OneDrive ressourcer i din organisation baseret på autoriserede IP-adresseintervaller, som du angiver. Få mere at vide under [Kontrollere adgang til SharePoint Online og OneDrive data baseret på netværksplacering](/sharepoint/control-access-based-on-network-location).|
|Webstedets geografiske flytning fuldført|SiteGeoMoveCompleted|Et websteds geografiske flytning, der blev planlagt af en global administrator i organisationen, blev fuldført. Multi-Geo funktionen lader en organisation strække sig over flere Microsoft-datacentergege områder, der kaldes geos. Du kan finde flere [oplysninger under Multi-Geo Capabilities i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Sendt til-forbindelse oprettet|SendToConnectionAdded|En SharePoint eller en global administrator opretter en ny Send til-forbindelse på siden til administration af poster SharePoint Administration. En Send til-forbindelse angiver indstillinger for et dokumentlager eller et datacenter. Når du opretter en Send til-forbindelse, kan en liste over indhold sende dokumenter til den angivne placering.|
|Gruppe af websteder oprettet|SiteCollectionCreated|En SharePoint eller global administrator opretter en gruppe af websteder i din SharePoint Online-organisation, eller en bruger gør sit OneDrive for Business websted.|
|Slettede uafhængige hubwebsted|HubSiteOrphanHubDeleted|En SharePoint eller global administrator har slettet et uafhængigt hubwebsted, som er et hubwebsted, der ikke har nogen tilknyttede websteder. En uafhængig hub er sandsynligvis forårsaget af sletningen af det oprindelige hubwebsted.|
|Sendt til-forbindelse slettet|SendToConnectionRemoved|En SharePoint eller en global administrator sletter en Send til-forbindelse på siden til administration af poster SharePoint Administration.|
|Slettet websted|WebstedSlettet|Webstedets administrator sletter et websted.|
|Dokumenteksempel aktiveret|PreviewModeEnabledSet|Webstedets administrator aktiverer dokumenteksempel for et websted.|
|Ældre arbejdsproces aktiveret|LegacyWorkflowEnabledSet|Webstedets administrator eller ejer føjer SharePoint 2013-indholdstypen Arbejdsprocesopgave til webstedet. Globale administratorer kan også aktivere arbejdsflows for hele organisationen SharePoint Administration.|
|Aktiveret Office on-demand|OfficeOnDemandSæt|Webstedets administrator aktiverer Office on-demand, hvilket giver brugere adgang til den nyeste version af Office-skrivebordsprogrammer. Office on Demand er aktiveret i SharePoint Administration og kræver et Microsoft 365, der omfatter komplette, installerede Office programmer.|
|Aktiveret resultatkilde til personer-søgninger|PeopleResultsScopeSet|Webstedets administrator opretter resultatkilden til personer-søgninger for et websted.|
|RSS-feeds aktiveret|NewsFeedEnabledSet|Webstedets administrator eller ejer aktiverer RSS-feeds for et websted. Globale administratorer kan aktivere RSS-feeds for hele organisationen SharePoint Administration.|
|Webstedet er forbundet til hubwebstedet|HubSiteJoined|En webstedsejer knytter deres websted til et hubwebsted.|
|Kvote for ændret gruppe af websteder|SiteCollectionQuotaModified|Webstedets administrator ændrer kvoten for en gruppe af websteder.|
|Registreret hubwebsted|HubSiteRegistered|En SharePoint eller en global administrator opretter et hubwebsted. Resultatet er, at webstedet er registreret som et hubwebsted.|
|Fjernede tilladt dataplacering|AllowedDataLocationDeleted|En SharePoint eller en global administrator har fjernet en tilladt dataplacering i et multi-geo-miljø.|
|Fjernede administrator for geoplacering|GeoAdminDeleted|En SharePoint eller global administrator har fjernet en bruger som geoadministrator for en placering.|
|Omdøbt websted|SiteRenamed|Webstedets administrator eller ejer omdøber et websted|
|Planlagt webstedets geografiske flytning|SiteGeoMoveScheduled|En SharePoint eller global administrator planlægger et SharePoint eller OneDrive websteds geografiske flytning. Multi-Geo funktionen lader en organisation strække sig over flere Microsoft-datacentergege områder, der kaldes geos. Du kan finde flere [oplysninger under Multi-Geo Capabilities i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Angiv værtswebsted|HostSiteSet|En SharePoint eller global administrator ændrer det angivne websted til at hoste personlige eller OneDrive for Business websteder.|
|Angiv lagerkvote for geoplacering|GeoQuotaAllocated|En SharePoint eller global administrator konfigurerede lagerkvoten for en geoplacering i et multi-geo-miljø.|
|Ikke-tilstødende websted fra hubwebsted|HubSiteUnjoined|En webstedsejer fraknytter sit websted til et hubwebsted.|
|Hubwebsted, der ikke er registrerede|HubSiteUnregistered|En SharePoint eller global administrator fjerne registreringer af et websted som et hubwebsted. Når et hubwebsted ikke registreres, fungerer det ikke længere som et hubwebsted.|
||||

### <a name="exchange-mailbox-activities"></a>Exchange postkasseaktiviteter

I følgende tabel vises de aktiviteter, der kan logføres ved logføring af postkassekontrol. Postkasseaktiviteter, der udføres af postkasseejeren, en delegeret bruger eller en administrator, logføres automatisk i overvågningsloggen i op til 90 dage. Det er muligt for en administrator at deaktivere logføring af postkassekontrol for alle brugere i organisationen. I dette tilfælde logføres ingen postkassehandlinger for nogen bruger. Du kan få mere at vide [under Administrere postkasserevision](enable-mailbox-auditing.md).

 Du kan også søge efter postkasseaktiviteter ved hjælp af [Search-MailboxAuditLog-cmdlet'en](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Postkasseelementer åbnet|MailItemsAccessed|Meddelelser blev læst eller åbnet i postkassen. Overvågningsposter for denne aktivitet udløses på en af to måder: når en mailklient (f.eks. Outlook) udfører en indbindingshandling på meddelelser, eller når mailprotokoller (f.eks. Exchange ActiveSync eller IMAP) synkroniserer elementer i en mailmappe. Denne aktivitet logføres kun for brugere med Office 365-Microsoft 365 E5-licens. Det er nyttigt at analysere overvågningsposterne for denne aktivitet, når du undersøger kompromitteret mailkonto. Du kan finde flere oplysninger i afsnittet "Avancerede overvågningshændelser" i [Avanceret overvågning](advanced-audit.md#advanced-audit-events). |
|Der er blevet tilføjet tilladelser for en stedfortræderpostkasse|Add-MailboxPermission|En administrator tildelte en bruger (kaldet en stedfortræder) postkassetilladelsen FullAccess til en anden persons postkasse. Tilladelsen FullAccess giver stedfortræderen mulighed for at åbne den anden persons postkasse samt læse og administrere indholdet af postkassen. Overvågningsposten for denne aktivitet genereres også, når en systemkonto i Microsoft 365-tjenesten med jævne mellemrum udfører vedligeholdelsesopgaver på vegne af din organisation. En almindelig opgave, der udføres af en systemkonto, er at opdatere tilladelserne for systempostkasser. Du kan få mere at vide [under Systemkonti Exchange postkassepostkasseposter](#system-accounts-in-exchange-mailbox-audit-records).|
|Bruger tilføjet eller fjernet med stedfortræderadgang til kalendermappen|UpdateCalendarDelegation|En bruger blev tilføjet eller fjernet som stedfortræder i kalenderen for en anden brugers postkasse. Kalenderdelegering giver andre i samme organisation tilladelse til at administrere postkasseejerens kalender.|
|Føjede tilladelser til mappen|AddFolderPermissions|En mappetilladelse blev tilføjet. Mappetilladelser styrer, hvilke brugere i organisationen der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|
|Meddelelser kopieret til en anden mappe|Kopiér|En meddelelse blev kopieret til en anden mappe.|
|Oprettet postkasseelement|Opret|Et element oprettes i mappen Kalender, Kontakter, Noter eller Opgaver i postkassen. Der oprettes f.eks. en ny mødeindkaldelse. Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke. Desuden overvåges oprettelse af en postkassemappe ikke.|
|Ny indbakkeregel oprettet i Outlook webapp|New-InboxRule|En postkasseejer eller en anden bruger med adgang til postkassen oprettede en indbakkeregel i Outlook-webappen.|
|Slettede meddelelser fra mappen Slettet post|BlødSlette|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Disse elementer flyttes til mappen Genoprettelige elementer. Meddelelser flyttes også til mappen Genoprettelige elementer, når en bruger vælger den og trykker på **Skift+Delete**.|
|Mærket meddelelse som en post|ApplyRecordLabel|En meddelelse blev klassificeret som en post. Dette sker, når et opbevaringsnavn, der klassificerer indhold som en post, anvendes manuelt eller automatisk på en meddelelse.|
|Meddelelser flyttet til en anden mappe|Flyt|En meddelelse blev flyttet til en anden mappe.|
|Meddelelser flyttet til mappen Slettet post|MoveToDeletedItems|En meddelelse blev slettet og flyttet til mappen Slettet post.|
|Ændret mappetilladelse|Opdater mappepapirer|En mappetilladelse blev ændret. Mappetilladelser styrer, hvilke brugere i organisationen der kan få adgang til postkassemapper og meddelelser i mappen.|
|Ændrede indbakkeregel fra Outlook webapp|Set-InboxRule|En postkasseejer eller en anden bruger med adgang til postkassen ændrede en indbakkeregel ved hjælp Outlook-webappen.|
|Meddelelser fjernet fra postkassen|HardDelete|En meddelelse blev slettet fra mappen Genoprettelige elementer (slettet permanent fra postkassen).|
|Stedfortrædertilladelser for postkasser fjernet|Remove-MailboxPermission|En administrator har fjernet tilladelsen FullAccess (som var tildelt en stedfortræder) fra en persons postkasse. Når tilladelsen FullAccess er fjernet, kan stedfortræderen ikke åbne eller få adgang til indholdet i den anden persons postkasse.|
|Fjernede tilladelser fra mappen|RemoveFolderPermissions|En mappetilladelse blev fjernet. Mappetilladelser styrer, hvilke brugere i organisationen der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|
|Sendt meddelelse|Send|En meddelelse blev sendt, besvaret eller videresendt. Denne aktivitet logføres kun for brugere med Office 365-Microsoft 365 E5-licens. Du kan finde flere oplysninger i afsnittet "Avancerede overvågningshændelser" i [Avanceret overvågning](advanced-audit.md#advanced-audit-events).|
|Meddelelse sendt ved hjælp af Send som-tilladelser|SendAs|En meddelelse blev sendt ved hjælp af SendAs-tilladelsen. Det betyder, at en anden bruger har sendt meddelelsen, som om den kom fra postkasseejeren.|
|Meddelelse sendt ved hjælp af Send på vegne af-tilladelser|SendOnBehalf|En meddelelse blev sendt ved hjælp af SendOnBehalf-tilladelsen. Det betyder, at en anden bruger har sendt meddelelsen på vegne af postkasseejeren. Meddelelsen angiver over for modtageren, hvem meddelelsen blev sendt på vegne af, og hvem der rent faktisk har sendt meddelelsen.|
|Opdaterede indbakkeregler fra Outlook klient|UpdateInboxRules|En postkasseejer eller en anden bruger med adgang til den postkasse, der er oprettet, ændret eller fjernet en indbakkeregel ved hjælp Outlook klienten.|
|Meddelelse opdateret|Opdater|En meddelelse eller dens egenskaber blev ændret.|
|Bruger, der er logget på postkasse|MailboxLogin|Brugeren er logget på sin postkasse.|
|Etiketmeddelelse som en post||En bruger har anvendt et opbevaringsnavn på en mail, og denne etiket er konfigureret til at markere elementet som en post. |
||||

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Systemkonti i Exchange overvågningsposter

I overvågningsposterne for nogle postkasseaktiviteter (især **tilføjelsespostkasser**) bemærker du muligvis, at den bruger, der udførte aktiviteten (og er identificeret i felterne Bruger og UserId) er NT AUTHORITY\SYSTEM eller NT AUTHORITY\SYSTEM(Microsoft.Exchange. Servicehost). Dette angiver, at den "bruger", der udførte aktiviteten, var en systemkonto i Exchange tjeneste i Microsoft-skyen. Denne systemkonto udfører ofte planlagte vedligeholdelsesopgaver på vegne af organisationen. Eksempelvis en almindelig overvåget aktivitet, der udføres af NT AUTHORITY\SYSTEM(Microsoft.Exchange. ServiceHost)-kontoen er at opdatere tilladelserne for DiscoverySearchMailbox, som er en systempostkasse. Formålet med denne opdatering er at bekræfte, at FullAccess-tilladelsen (som er standard) er tildelt rollegruppen Søgeadministration for DiscoverySearchMailbox. Dette sikrer, at eDiscovery-administratorer kan udføre de nødvendige opgaver i deres organisation.

En anden systembrugerkonto, der kan identificeres i en **overvågningspost for Add-MailboxPermission** , er Administrator@apcprd03.prod.outlook.com. Denne tjenestekonto er også inkluderet i postkassekontrolposter, der er relateret til bekræftelse og opdatering af tilladelsen FullAccess, der er tildelt rollegruppen Søgeadministration for systempostkassen DiscoverySearchMailbox. Specifikt udløses overvågningsposter, der identificerer Administrator@apcprd03.prod.outlook.com-kontoen, typisk, når Microsoft-supportmedarbejdere kører et RBAC-rollediagnosticeringsværktøj på vegne af organisationen.

### <a name="user-administration-activities"></a>Aktiviteter for brugeradministration

I følgende tabel vises brugeradministrationsaktiviteter, der logføres, når en administrator tilføjer eller ændrer en brugerkonto ved hjælp [af Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er **angivet** i kolonnen Handling i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i navnet på handlingen, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for opbevaring af overvågning, opretter påmindelsespolitikker eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde navnet på handlingen.

|Aktivitet|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Bruger tilføjet|Tilføj bruger.|Der blev oprettet en brugerkonto.|
|Brugerlicens ændret|Skift brugerlicens.|Den licens, der er tildelt en bruger, blev ændret. Se den tilsvarende aktivitet Opdateret bruger for at se, **hvilke licenser der blev ændret** .|
|Brugers adgangskode ændret|Skift brugeradgangskode.|En bruger ændrer sin adgangskode. Selvbetjening for nulstilling af adgangskode skal være aktiveret (for alle eller udvalgte brugere) i organisationen for at give brugerne mulighed for at nulstille deres adgangskode. Du kan også registrere aktivitet for nulstilling af adgangskode via selvbetjening Azure Active Directory. Få mere at vide under [Rapporteringsindstillinger for administration af adgangskoder til Azure AD](/azure/active-directory/authentication/howto-sspr-reporting).
|Slettet bruger|Slet bruger.|En brugerkonto er blevet slettet.|
|Nulstil brugerens adgangskode|Nulstil brugerens adgangskode.|Administrator nulstiller adgangskoden for en bruger.|
|Angiv egenskab, der tvinger brugeren til at ændre adgangskode|Angiv gennemtving ændring af brugerens adgangskode.|Administrator har indstillet den egenskab, der tvinger en bruger til at ændre sin adgangskode, næste gang brugeren logger på Microsoft 365.|
|Angiv licensegenskaber|Angiv licensegenskaber.|Administrator ændrer egenskaberne for en licens, der er tildelt en bruger.|
|Bruger opdateret|Opdater bruger.|Administrator ændrer en eller flere egenskaber for en brugerkonto. Du kan finde en liste over de brugeregenskaber, der kan opdateres, i afsnittet "Opdater brugerattributter" [Azure Active Directory overvågningsrapporthændelser](/azure/active-directory/reports-monitoring/concept-audit-logs).|
||||

### <a name="azure-ad-group-administration-activities"></a>Azure AD - gruppeadministrationsaktiviteter

I følgende tabel vises gruppeadministrationsaktiviteter, der logføres, når en administrator eller bruger opretter eller ændrer en Microsoft 365-gruppe, eller når en administrator opretter en sikkerhedsgruppe ved hjælp af [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339)- eller Azure-administrationsportalen. Du kan finde flere oplysninger om Microsoft 365 i [Få vist, opret og slet grupper i Microsoft 365 Administration](../admin/create-groups/create-groups.md).

> [!NOTE]
> De handlingsnavne, der er **angivet** i kolonnen Handling i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i navnet på handlingen, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for opbevaring af overvågning, opretter påmindelsespolitikker eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde navnet på handlingen.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Gruppe tilføjet|Tilføj gruppe.|En gruppe blev oprettet.|
|Medlem føjet til gruppe|Føj medlem til gruppe.|Et medlem blev føjet til en gruppe.|
|Slettet gruppe|Slet gruppe.|En gruppe er blevet slettet.|
|Medlem fjernet fra gruppe|Fjern medlem fra gruppe.|Et medlem blev fjernet fra en gruppe.|
|Gruppe opdateret|Opdater gruppe.|En egenskab for en gruppe blev ændret.|
||||

### <a name="application-administration-activities"></a>Aktiviteter for programadministration

I følgende tabel vises programadministrationsaktiviteter, der logføres, når en administrator tilføjer eller ændrer et program, der er registreret i Azure AD. Programmer, der er afhængige af Azure AD til godkendelse, skal registreres i kataloget.

> [!NOTE]
> De handlingsnavne, der er **angivet** i kolonnen Handling i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i navnet på handlingen, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for opbevaring af overvågning, opretter påmindelsespolitikker eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde navnet på handlingen.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Delegeringspost tilføjet|Tilføj delegeringspost.|En godkendelsestilladelse blev oprettet/tildelt et program i Azure AD.|
|Tjenesteinspektør tilføjet|Tilføj tjenesteinspektør.|Et program blev registreret i Azure AD. Et program er repræsenteret af en tjenesteinspektør i kataloget.|
|Legitimationsoplysninger føjet til en tjenesteinspektør|Tilføj legitimationsoplysninger for tjenesteinspektører.|Legitimationsoplysninger blev føjet til en tjenesteinspektør i Azure AD. Et tjenesteprincip repræsenterer et program i kataloget.|
|Delegeringspost fjernet|Fjern delegeringspost.|En godkendelsestilladelse blev fjernet fra et program i Azure AD.|
|En tjenesteinspektør blev fjernet fra kataloget|Fjern tjeneste principal.|Et program blev slettet/fik fjernet registrering fra Azure AD. Et program er repræsenteret af en tjenesteinspektør i kataloget.|
|Legitimationsoplysninger fjernet fra en tjenesteinspektør|Fjern legitimationsoplysninger for tjenesteinspektører.|Legitimationsoplysninger blev fjernet fra en tjeneste principal i Azure AD. Et tjenesteprincip repræsenterer et program i kataloget.|
|Angiv delegeringspost|Angiv delegeringspost.|En godkendelsestilladelse blev opdateret for et program i Azure AD.|
||||

### <a name="role-administration-activities"></a>Aktiviteter for rolleadministration

I følgende tabel vises Azure AD-rolleadministrationsaktiviteter, der logføres, når en administrator administrerer administratorroller i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller på Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er **angivet** i kolonnen Handling i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i navnet på handlingen, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for opbevaring af overvågning, opretter påmindelsespolitikker eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde navnet på handlingen.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Føj medlem til rolle|Føj medlem til rolle.|En bruger blev føjet til en administratorrolle i Microsoft 365.|
|En bruger blev fjernet fra en mapperolle|Fjern medlem fra rolle.|En bruger blev fjernet fra en administratorrolle i Microsoft 365.|
|Angive kontaktoplysninger for firmaet|Angiv kontaktoplysninger for firmaet.|Kontaktindstillingerne for din organisation på virksomhedsniveau blev opdateret. Dette omfatter mailadresser for abonnementsrelaterede mails, der sendes Microsoft 365, og tekniske meddelelser om tjenester.|
||||

### <a name="directory-administration-activities"></a>Aktiviteter for katalogadministration

I følgende tabel vises Azure AD-kataloger og domænerelaterede aktiviteter, der logføres, når en administrator administrerer deres organisation [på Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er **angivet** i kolonnen Handling i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i navnet på handlingen, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for opbevaring af overvågning, opretter påmindelsespolitikker eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde navnet på handlingen.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Domæne føjet til virksomhed|Føj domæne til virksomhed.|Et domæne blev føjet til organisationen.|
|En partner føjet til kataloget|Føj partner til virksomhed.|En partner (delegeret administrator) er blevet føjet til organisationen.|
|Domæne fjernet fra virksomhed|Fjern domæne fra virksomhed.|Et domæne blev fjernet fra din organisation.|
|En partner blev fjernet fra kataloget|Fjern partner fra virksomhed.|En partner (delegeret administrator) blev fjernet fra organisationen.|
|Angiv firmaoplysninger|Angiv firmaoplysninger.|Firmaoplysningerne for din organisation blev opdateret. Dette omfatter mailadresser for abonnementsrelaterede mails, der sendes Microsoft 365, og tekniske meddelelser om Microsoft 365 tjenester.|
|Angiv domænegodkendelse|Angiv domænegodkendelse.|Indstillingen for domænegodkendelse er blevet ændret for din organisation.|
|Indstillingerne for sammenslutning blev opdateret for et domæne|Angiv indstillinger for sammenslutning på domæne.|Indstillingerne for sammenslutning (ekstern deling) blev ændret for organisationen.|
|Angiv adgangskodepolitik|Angiv adgangskodepolitik.|Længde- og tegnbegrænsningerne blev ændret for brugeradgangskoder i organisationen.|
|Azure AD-synkronisering aktiveret|Angiv DirSyncEnabled-flag.|Angiv den egenskab, der aktiverer et katalog til Azure AD-synkronisering.|
|Domæne opdateret|Opdater domæne.|Indstillingerne for et domæne blev opdateret i organisationen.|
|Bekræftet domæne|Bekræft domæne.|Bekræftet, at din organisation er ejeren af et domæne.|
|Bekræftet domæne bekræftet via mail|Bekræft godkendt domæne via mail.|Mailbekræftelsen blev brugt til at bekræfte, at din organisation er ejeren af et domæne.|
||||

### <a name="ediscovery-activities"></a>eDiscovery-aktiviteter

Indholdssøgning og eDiscovery-relaterede aktiviteter, der udføres i sikkerheds- og overholdelsescenteret eller ved at køre de tilsvarende PowerShell-cmdlet'er, logføres i overvågningsloggen. Dette omfatter følgende aktiviteter:

- Oprettelse og administration af eDiscovery-sager

- Oprettelse, start og redigering af indholdssøgninger

- Udføre handlinger til indholdssøgning, f.eks. vise, eksportere og slette søgeresultater

- Konfiguration af filtrering af tilladelser for indholdssøgning

- Administrere eDiscovery-administratorrollen

Hvis du vil have en liste over og en detaljeret beskrivelse af de eDiscovery-aktiviteter, der logføres, skal du se Søge efter [eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Det tager op til 30 minutter for hændelser, der kommer fra de aktiviteter, der er angivet under **eDiscovery-aktiviteter** og **Advanced eDiscovery-aktiviteter** på rullelisten Aktiviteter, at blive vist i søgeresultaterne. Omvendt tager det op til 24 timer, før de tilhørende begivenheder fra eDiscovery cmdlet-aktiviteter vises i søgeresultaterne.

### <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery aktiviteter

Du kan også søge i overvågningsloggen efter aktiviteter i Advanced eDiscovery. Du kan finde en beskrivelse af disse aktiviteter i afsnittet "Advanced eDiscovery"-aktiviteter i Søge efter [eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md#advanced-ediscovery-activities).

### <a name="power-bi-activities"></a>Power BI aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Power BI. Du kan finde oplysninger Power BI aktiviteter i afsnittet "Aktiviteter, der Power BI" i Brug [overvågning inden for organisationen](/power-bi/service-admin-auditing#activities-audited-by-power-bi).

Overvågningslogføring for Power BI ikke er aktiveret som standard. Hvis du vil Power BI efter alle aktiviteter i overvågningsloggen, skal du aktivere overvågning Power BI administrationsportalen. Du kan finde en vejledning i afsnittet "Overvågningslogfiler" [Power BI administrationsportalen](/power-bi/service-admin-portal#audit-logs).

### <a name="workplace-analytics-activities"></a>Workplace Analytics-aktiviteter

Workplace Analytics giver indsigt i, hvordan grupper samarbejder på tværs af din organisation. I følgende tabel vises de aktiviteter, der udføres af brugere, der er tildelt administratorrollen eller analytikerrollerne i Workplace Analytics. Brugere, der er tildelt analytikerrollen, har fuld adgang til alle tjenestefunktioner og bruger produktet til analyse. Brugere, der er tildelt administratorrollen, kan konfigurere indstillinger for beskyttelse af personlige oplysninger og systemstandard samt forberede, uploade og bekræfte organisationsdata i Workplace Analytics. Du kan få mere at vide [under Workplace Analytics](/workplace-analytics/index-orig).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Adgang til OData-link|AccessedOdataLink|Analytikeren fik adgang til OData-linket for en forespørgsel.|
|Annulleret forespørgsel|AnnulleretForespørgig|En analytiker har annulleret en løbende forespørgsel.|
|Mødeudeudelse oprettet|MeetingExclusionCreated|Analytikeren oprettede en regel for udeladelse af møder.|
|Slettet resultat|DeletedResult|Analytikeren har slettet et forespørgselsresultat.|
|Downloadet rapport|DownloadedReport|En analytiker hentede en forespørgselsresultatfil.|
|Eksekveret forespørgsel|UdførtForespørgs|Analytikeren kørte en forespørgsel.|
|Opdaterede indstillinger for dataadgang|UpdatedDataAccessSetting|Administratoren har opdateret indstillingerne for dataadgang.|
|Indstilling for beskyttelse af personlige oplysninger opdateret|UpdatedPrivacySetting|Administrator har opdateret indstillingerne for beskyttelse af personlige oplysninger. For eksempel mindste gruppestørrelse.|
|Overførte organisationsdata|UploadedOrgData|Administrator overførte organisationsdatafil.|
|Bruger, der er logget på<sup>*</sup>| UserLoggedIn |En bruger er logget på Microsoft 365 sin brugerkonto.|
|Brugeren er logget af<sup>*</sup>| UserLoggedOff |En bruger logget af sin Microsoft 365 brugerkonto.
|Set Udforsk|ViewedExplore|Visualiseringer, som er set af en eller flere analytikere, i en eller flere sidefaner.|
||||

> [!NOTE]
> <sup>*</sup>Disse Azure Active Directory logge på og afmelde aktiviteter. Disse aktiviteter logføres, selvom du ikke har Workplace Analytics aktiveret i organisationen. Du kan finde flere oplysninger om brugerlogfilaktiviteter [i Logge på Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>Microsoft Teams aktiviteter

Du kan søge i overvågningsloggen efter bruger- og administratoraktiviteter i Microsoft Teams. Teams er et chatbaseret arbejdsområde i Microsoft 365. Det samler et teams samtaler, møder, filer og noter på ét sted. Du kan finde beskrivelser af Teams, der overvåges, under Søge i [overvågningsloggen efter hændelser i Microsoft Teams](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Microsoft Teams sundhedsaktiviteter

Hvis din organisation bruger programmet [Patienter](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) i Microsoft Teams, kan du søge i overvågningsloggen efter aktiviteter, der er relateret til brug af appen Patienter. Hvis dit miljø er konfigureret til at understøtte appen Patienter, findes en ekstra aktivitetsgruppe for disse aktiviteter på **listen** Aktivitetsvælger.

![Microsoft Teams sundhedsaktiviteter i listen Aktivitetsvælger.](../media/TeamsHealthcareAuditActivities.png)

Hvis du vil have en beskrivelse af appaktiviteterne patienter, [skal du se Overvågningslogfiler for appen Patienter](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Microsoft Teams vagtaktiviteter

Hvis din organisation bruger appen Vagter i Microsoft Teams, kan du søge i overvågningsloggen efter aktiviteter i forbindelse med brugen af appen Vagter. Hvis dit miljø er konfigureret til at understøtte Vagter-apps, findes en ekstra aktivitetsgruppe for disse aktiviteter på **listen** Aktivitetsvælger.

Hvis du vil have en beskrivelse af vagter-appaktiviteterne, [skal du se Søge i overvågningsloggen efter hændelser Microsoft Teams](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Yammer aktiviteter

I følgende tabel vises brugeres og administratorers aktiviteter i Yammer, der er logført i overvågningsloggen. Hvis du Yammer aktivitetsrelaterede aktiviteter fra overvågningsloggen, skal du markere **Vis resultater for alle** aktiviteter på **listen** Aktiviteter. Brug felterne for datoområde og **listen Brugere** til at indsnævre søgeresultaterne.

> [!NOTE]
> Nogle Yammer overvågningsaktiviteter er kun tilgængelige i Avanceret overvågning. Det betyder, at brugerne skal have tildelt den relevante licens, før disse aktiviteter logføres i overvågningsloggen. Du kan finde flere oplysninger om aktiviteter, der kun er tilgængelige i [Avanceret overvågning, under Avanceret overvågning Microsoft 365](advanced-audit.md#advanced-audit-events). Se Avancerede overvågningslicenskrav under [Overvågningsløsninger i Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>I følgende tabel er Avancerede overvågningsaktiviteter fremhævet med en stjerne (*).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Ændrede dataopbevaringspolitik|IndstillingerFor BlødSletningOpdelt|En bekræftet administrator opdaterer indstillingen for netværkets dataopbevaringspolitik til enten hård sletning eller blød sletning. Kun bekræftede administratorer kan udføre denne handling.|
|Ændrede netværkskonfiguration|NetværkskonfigurationOpdateret|Netværksadministrator eller bekræftet administrator ændrer Yammer netværkets konfiguration. Dette omfatter angivelse af intervallet for eksport af data og aktivering af chat.|
|Ændrede indstillinger for netværksprofil|ProcessProfileFields|Netværksadministrator eller bekræftet administrator ændrer de oplysninger, der vises på medlemsprofiler for brugerne i netværket.|
|Ændret privat indholdstilstand|SupervisorAdminToggled|Bekræftet administrator slår  *Privat indholdstilstand*  til eller fra. Med denne tilstand kan en administrator få vist indlæg i private grupper og få vist private meddelelser mellem individuelle brugere (eller grupper af brugere). Kun bekræftede administratorer kan udføre denne handling.|
|Ændrede sikkerhedskonfiguration|Konfiguration Af NetværkssikkerhedKonfigureretOpstillet|En bekræftet administrator opdaterer Yammer netværkets sikkerhedskonfiguration. Dette omfatter indstilling af udløbspolitikker for adgangskoder og begrænsninger for IP-adresser. Kun bekræftede administratorer kan udføre denne handling.|
|Oprettet fil|FileCreated|Brugeren overfører en fil.|
|Oprettet gruppe|GroupCreation|Brugeren opretter en gruppe.|
|Meddelelse oprettet<sup>*</sup>|MeddelelseOprettet|Brugeren opretter en meddelelse.|
|Slettet gruppe|GroupDeletion|En gruppe slettes fra Yammer.|
|Slettet meddelelse|MeddelelseSlettet|Brugeren sletter en meddelelse.|
|Downloadet fil|FileDownloaded|Brugeren downloader en fil.|
|Eksporterede data|DataExport|En bekræftet administrator eksporterer Yammer af netværksdata. Kun bekræftede administratorer kan udføre denne handling.|
|Kunne ikke få adgang til community<sup>*</sup>|CommunityAccessFailure|Brugeren kunne ikke få adgang til et community.|
|Kunne ikke få adgang til filen<sup>*</sup>|FileAccessFailure|Brugeren kunne ikke få adgang til en fil.|
|Meddelelsen Kunne ikke tilgås<sup>*</sup>|MessageAccessFailure|Brugeren kunne ikke få adgang til en meddelelse.|
|Delt fil|FileShared|Bruger deler en fil med en anden bruger.|
|Suspenderede netværksbruger|NetworkUserS suspendended|Netværksadministrator eller bekræftet administrator suspenderer (deaktiverer) en bruger Yammer.|
|Suspenderede bruger|UserSusinvest|Brugerkonto er suspenderet (deaktiveret).|
|Opdateret filbeskrivelse|FileUpdateDescription|Brugeren ændrer beskrivelsen af en fil.|
|Opdateret filnavn|FileUpdateName|Brugeren ændrer navnet på en fil.|
|Meddelelse opdateret<sup>*</sup>|MeddelelseOpdateret|Brugeren opdaterer en meddelelse.|
|Viste fil|FileVisited|Brugeren får en fil.|
|Vist meddelelse<sup>*</sup>|MessageViewed|Brugeren får vist en meddelelse.|
||||

### <a name="microsoft-power-automate-activities"></a>Microsoft Power Automate aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Power Automate (tidligere kaldet Microsoft Flow). Disse aktiviteter omfatter oprettelse, redigering og sletning af flows og ændring af flowtilladelser. Hvis du vil have mere at vide Power Automate overvågning af Power Automate, skal [du se bloggen Power Automate overvågningshændelser, der nu er tilgængelige Microsoft 365 Overholdelsescenter](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Microsoft Power Apps aktiviteter

Du kan søge i overvågningsloggen efter apprelaterede aktiviteter i Power Apps. Disse aktiviteter omfatter oprettelse, start og publicering af en app. Tildeling af tilladelser til apps overvåges også. Hvis du vil have en beskrivelse af Power Apps aktiviteter, skal du [se Aktivitetslogføring for Power Apps](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Microsoft Stream-aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Microsoft Stream. Disse aktiviteter omfatter videoaktiviteter, der udføres af brugere, gruppekanalaktiviteter og administratoraktiviteter som administration af brugere, administration af indstillinger for organisationen og eksport af rapporter. Du kan finde en beskrivelse af disse aktiviteter i afsnittet "Handlinger, der er logget i Stream" [i Overvågningslogfiler i Microsoft Stream](/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>Aktiviteter i Indholdsstifinder

I følgende tabel vises de aktiviteter i indholdsstifinder, der logføres i overvågningsloggen. Indholdsstifinder, som findes via værktøjet Dataklassificeringer i Microsoft 365 Overholdelsescenter. Du kan få mere at vide under [Brug af indholdsstifinder til dataklassificering](data-classification-content-explorer.md).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Element åbnet|LabelContentExplorerAccessedItem|En administrator (eller en bruger, der er medlem af rollegruppen indholdsvisning i Indholdsoversigt) bruger indholdsstifinder til at få vist en mail eller SharePoint/OneDrive dokument.|
||||

### <a name="quarantine-activities"></a>Karantæneaktiviteter

I følgende tabel vises de karantæneaktiviteter, du kan søge efter i overvågningsloggen. Du kan finde flere oplysninger om karantæne i [Af karantæne i mails](../security/office-365-security/quarantine-email-messages.md).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Meddelelse om slettet karantæne|KarantæneSlette|En bruger har slettet en mail, der anses for at være skadelig.|
|Meddelelse om eksporteret karantæne|KarantæneRapport|En bruger har eksporteret en mail, der anses for at være skadelig.|
|Meddelelse om forhåndsvisning af karantæne|QuarantinePreview|En bruger har forhåndsvist en mail, der anses for at være skadelig.|
|Meddelelse om frigivne karantæne|KarantæneRelease|En bruger har udgivet en mail fra karantæne, der anses for at være skadelig.|
|Viste karantænemeddelelses brevhoved|QuarantineViewHeader|En bruger fik vist sidehovedet en mail, der anses for at være skadelig.|
||||

### <a name="microsoft-forms-activities"></a>Microsoft Forms-aktiviteter

Tabellerne i dette afsnit bruger- og administratoraktiviteterne i Microsoft Forms, der er logført i overvågningsloggen. Microsoft Forms er et værktøj til formularer/test/undersøgelser, der bruges til at indsamle data til analyse. Hvor anført nedenfor i beskrivelserne indeholder nogle handlinger yderligere aktivitetsparametre.

Hvis en formularaktivitet udføres af en medordbog eller en anonym svarer, logføres den en smule anderledes. Du kan finde flere oplysninger i [afsnittet Formularer, der udføres af medordnere og anonyme svarere](#forms-activities-performed-by-coauthors-and-anonymous-responders) .

> [!NOTE]
> Nogle formularrevisionsaktiviteter er kun tilgængelige i Avanceret overvågning. Det betyder, at brugerne skal have tildelt den relevante licens, før disse aktiviteter logføres i overvågningsloggen. Du kan finde flere oplysninger om aktiviteter, der kun er tilgængelige i [Avanceret overvågning, under Avanceret overvågning Microsoft 365](advanced-audit.md#advanced-audit-events). Se Avancerede overvågningslicenskrav under [Overvågningsløsninger i Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>I følgende tabel er Avancerede overvågningsaktiviteter fremhævet med en stjerne (*).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Oprettet kommentar|CreateComment|Formularejeren føjer kommentarer eller point til en test.|
|Oprettet formular|OpretFormular|Formularejer opretter en ny formular. <br><br>Property DataMode:string angiver, at den aktuelle formular er indstillet til at synkronisere med en ny eller eksisterende Excel-projektmappe, hvis egenskabsværdien er lig med DataSync. Egenskab ExcelWorkbookLink:streng angiver det tilknyttede Excel-projektmappe-id for den aktuelle formular.|
|Redigeret formular|EditForm|Formularejer redigerer en formular som f.eks. at oprette, fjerne eller redigere et spørgsmål. Egenskaben *EditOperation:string angiver* navnet på redigeringshandlingen. De mulige handlinger er:<br/>- CreateQuestion<br/>- CreateQuestionChoice <br/>- DeleteQuestion <br/>- DeleteQuestionChoice <br/>- DeleteFormImage <br/>- DeleteQuestionImage <br/>- UpdateQuestion <br/>- UpdateQuestionChoice <br/>- UploadFormImage/Bing/OneDrive <br/>- UploadQuestionImage <br/>- ChangeTheme <br><br>FormImage omfatter et vilkårligt sted i Forms, som brugeren kan overføre et billede til, f.eks. i en forespørgsel eller som et baggrundstema.|
|Flyttet formular|FlytFormular|Formularejeren flytter en formular. <br><br>Property DestinationUserId:string angiver bruger-id'et for den person, der har flyttet formularen. Egenskaben NewFormId:string er det nye id for den netop kopierede formular. Egenskaben IsDelegateAccess:boolesk angiver, at den aktuelle flytningshandling for formularen udføres via siden stedfortræder for administratorer.|
|Slettet formular|SletFormular|Formularejer sletter en formular. Dette omfatter SoftDelete (indstillingen Slet brugt, og formular flyttet til Papirkurv) og HardDelete (Papirkurv tømmes).|
|Vist formular (designtid)|ViewForm|Formularejer åbner en eksisterende formular til redigering. <br><br>Property AccessDenied:boolesk angiver adgang til aktuel formular nægtet på grund af tilladelseskontrol. Egenskaben FromSummaryLink:boolesk angiver, at den aktuelle anmodning kommer fra oversigtslinksiden.|
|Formular vist|EksempelFormular|Formularejeren får vist et eksempel på en formular ved hjælp af funktionen Eksempel.|
|Eksporteret formular|ExportForm|Formularejer eksporterer resultater til Excel. <br><br>Egenskabseksportformat:streng angiver, om Excel er Download eller Online.|
|Tilladelse til delingsformular til kopi|AllowShareFormForCopy|Formularejeren opretter et skabelonlink for at dele formularen med andre brugere. Hændelsen logføres, når formularens ejer klikker for at generere url-adressen til skabelonen.|
|Delingsformular for ikke tilladt|ForbydeShareFormForCopy|Formularejer sletter skabelonlink.|
|Tilføjede samtidig redigering af formular|AddFormCoauthor|En bruger bruger bruger et samarbejdslink til at designe for/få vist svar. Hændelsen logføres, når en bruger bruger bruger en COLLAB-URL (ikke når COLLAB URL-adresse genereres første gang).|
|Fjernede samtidig redigering af formular|RemoveFormCoauthor|Formularejer sletter et samarbejdslink.|
|Viste svarside|ViewRuntimeForm|Brugeren har åbnet en svarside, der skal vises. Hændelsen logføres, uanset om brugeren sender et svar eller ej.|
|Oprettet svar|CreateResponse|Svarer til at modtage et nyt svar.  En bruger har sendt et svar til en formular. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym svarer er responderId-egenskaben null.|
|Opdateret svar|UpdateResponse|Formularejeren har opdateret en kommentar eller et pointtal i en test. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym svarer er responderId-egenskaben null.|
|Slettede alle svar|DeleteAllResponses|Formularejer sletter alle svardata.|
|Slettet svar|DeleteResponse|Formularejer sletter ét svar. <br><br>Egenskaben ResponseId:string angiver det svar, der slettes.|
|Viste svar|Visningsresponser|Formularejer får vist den samlede liste over svar. <br><br>EgenskabsvisningStype:streng angiver, om formularejeren får vist Detaljer eller Aggregat|
|Vist svar|ViewResponse|Formularejeren får et bestemt svar med. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym svarer er responderId-egenskaben null.|
|Oversigtslink oprettet|GetSummaryLink|Formularens ejer opretter et link til oversigtsresultater for at dele resultater.|
|Slettet oversigtslink|DeleteSummaryLink|Formularens ejer sletter linket med oversigtsresultater.|
|Opdateret status for phishing af formular|UpdatePhishingStatus|Hændelsen logføres, når den detaljerede værdi for den interne sikkerhedsstatus blev ændret, uanset om den endelige sikkerhedstilstand blev ændret (formularen er f.eks. nu Lukket eller Åbnet). Det betyder, at du kan få vist dublerede hændelser uden den endelige ændring af sikkerhedstilstanden. De mulige statusværdier for denne hændelse er:<br/>- Tag ned <br/>- Tage ned af administrator <br/>- Administrator har fjernet blokeringen <br/>- Automatisk blokeret <br/>- Fjern blokering automatisk <br/>- Kunde rapporteret <br/>- Nulstil kunde rapporteret|
|Opdateret status for brugerphishing|UpdateUserPhishingStatus|Hændelsen logføres, når værdien for brugersikkerhedsstatussen ændres. Værdien af brugerstatus i overvågningsposten er Bekræftet som **Phisher** , da brugeren oprettede en phishingformular, der blev taget ned af Microsoft Online-sikkerhedsteamet. Hvis en administrator fjerner blokeringen af brugeren, angives værdien af brugerens status til Nulstil **som normal bruger**.|
|Sendt formular Pro invitation|ProInvitation|Brugeren klikker for at aktivere en Pro prøveversion.|
|Opdateret formularindstilling<sup>*</sup> |Nulstilling af opdateringsformular|Formularejer opdaterer en eller flere formularindstillinger. <br><br>Property FormSettingName:string angiver navnet på opdaterede følsomme indstillinger. Egenskaben NewFormSettings:string angiver de opdaterede indstillingers navn og den nye værdi. Egenskab thankYouMessageContainsLink:boolean indicates updated thank-you message contains a URL link.|
|Brugerindstilling opdateret|OpdaterBrugersetting|Formularejer opdaterer en brugerindstilling. <br><br>Egenskaben UserSettingName:string angiver indstillingens navn og nye værdi|
|Viste formularer<sup>*</sup>|ListForms|Formularejer får vist en liste over formularer. <br><br>EgenskabsvisningStype:streng angiver, hvilken visning formularens ejer kigger på: Alle formularer, Delt med mig eller Gruppeformularer|
|Indsendt svar|SubmitResponse|En bruger sender et svar på en formular. <br><br>Egenskaben IsInternalForm:boolesk angiver, om svareren er inden for samme organisation som formularens ejer.|
|Indstillingen Alle kan svare aktiveret<sup>*</sup>|AllowAnonymousResponse|Formularejer slår indstillingen til, så en hvilken som helst kan svare på formularen.|
|Indstillingen Alle kan svare deaktiveret<sup>*</sup>|DisallowAnonymousResponse|Formularejer deaktiverer indstillingen, der tillader, at en af dem kan svare på formularen.|
|Aktiverede bestemte personer kan svare-indstilling<sup>*</sup>|EnableSpecificResponse|Formularejer slår indstillingen til, så kun bestemte personer eller bestemte grupper i den aktuelle organisation kan besvare formularen.|
|Deaktiverede bestemte personer kan svare-indstilling<sup>*</sup>|DisableSpecificResponse|Formularejer deaktiverer indstillingen, så kun bestemte personer eller bestemte grupper i den aktuelle organisation kan besvare formularen.|
|Tilføjede en bestemt svarer<sup>*</sup>|AddSpecificResponder|Formularejer føjer en ny bruger eller gruppe til den specifikke svarliste.|
|Et bestemt svar fjernet<sup>*</sup>|RemoveSpecificResponder|Formularejer fjerner en bruger eller gruppe fra den specifikke svarliste.|
|Deaktiveret samarbejde<sup>*</sup>|DisableCollaboration|Formularejer deaktiverer indstillingen for samarbejde i formularen.|
|Aktiveret Office 365 af arbejds- eller skolekontosamarbejde<sup>*</sup>|EnableWorkOrSchoolCollaboration|Formularejer slår indstillingen til, så brugere med Microsoft 365 arbejds- eller skolekonto kan få vist og redigere formularen.|
|Aktiverede personer i organisationens samarbejde<sup>*</sup>|EnableSameOrgCollaboration|Formularejer slår indstillingen til, så brugere i den aktuelle organisation kan få vist og redigere formularen.|
|Aktiveret samarbejde for bestemte personer<sup>*</sup>|EnableSpecificCollaboaration|Formularejer slår indstillingen til, så kun bestemte personer eller bestemte grupper i den aktuelle organisation kan få vist og redigere formularen.|
|Tilsluttet til Excel projektmappe<sup>*</sup>|ConnectToExcelWorkbook|Forbundne formularen til en Excel projektmappe. <br><br>Egenskab ExcelWorkbookLink:streng angiver det tilknyttede Excel-projektmappe-id for den aktuelle formular.|
|Oprettet en samling|SamlingOprettet|Formularejer har oprettet en samling.|
|En samling blev opdateret|SamlingOpdateret|Formularejeren har opdateret en samlingsegenskab.|
|Slettet samling fra papirkurven|CollectionHardDeleted|Formularejer har slettet en samling fra papirkurven permanent.|
|Flyttet samling til papirkurven|CollectionSoftDeleted|Formularejeren har flyttet en samling til Papirkurv.|
|Omdøbt en samling|CollectionRenamed|Formularejeren har ændret navnet på en samling.|
|Flyttet en formular til samling|MovedFormIntoCollection|Formularejeren har flyttet en formular til en samling.|
|Flyttet en formular ud af samlingen|MovedFormOutofCollection|Formularejeren har flyttet en formular ud af en samling.|
||||

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Forms activities performed by coauthors and anonymous responders

Formularer understøtter samarbejde, når formularer er designet, og når du analyserer svar. En formularsamarbejdspartner kaldes en *samtidig redigering*. Medejere kan gøre alt, hvad en formularejer kan gøre, undtagen at slette eller flytte en formular. Formularer giver dig også mulighed for at oprette en formular, der kan besvares anonymt. Det betyder, at svareren ikke behøver at være logget på din organisation for at svare på en formular.

I følgende tabel beskrives overvågningsaktiviteterne og oplysningerne i overvågningsposten for aktiviteter, der udføres af medordnere og anonyme respondenter.

|Aktivitetstype|Intern eller ekstern bruger|Bruger-id, der logføres|Organisation logget på|Brugertypen Formularer|
|:-----|:-----|:-----|:-----|:-----|
|Samtidig redigering|Intern|UPN|Formularejerens organisation|Samtidig redigering|
|Samtidig redigering|Ekstern|UPN<br>|Med samtidig redigering i organisationen<br>|Samtidig redigering|
|Samtidig redigering|Ekstern|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(Den anden del af id'et er en hash hash, som vil være forskellig for forskellige brugere)|Formularejerens organisation<br>|Samtidig redigering|
|Svaraktiviteter|Ekstern|UPN<br>|Responder's org<br>|Svarer|
|Svaraktiviteter|Ekstern|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(Den anden del af bruger-id'et er en hashtag, som vil være forskellig for forskellige brugere)|Formularejerens organisation|Svarer|
|Svaraktiviteter|Anonym|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(Den anden del af bruger-id'et er en hashtag, som vil være forskellig for forskellige brugere)|Formularejerens organisation|Svarer|
||||

### <a name="sensitivity-label-activities"></a>Aktiviteter for følsomhedsmærkat

I følgende tabel vises hændelser, der skyldes brug af [følsomhedsmærkater](sensitivity-labels.md).

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
|Anvendt følsomhedsmærkat på websted|SensitivityLabelApplied|Et følsomhedsmærkat blev anvendt på et SharePoint eller Teams websted.|
|Følsomhedsmærkatet fjernet fra webstedet|SensitivityLabelRemoved|En følsomhedsmærkat blev fjernet fra et SharePoint eller Teams websted.|
|Anvendt følsomhedsmærkat på fil|FileSensitivityLabelApplied|Et følsomhedsmærkat blev anvendt på et dokument ved hjælp Microsoft 365 apps og Office på internettet. eller en politik for automatisk mærkater.|
|Ændret følsomhedsmærkat anvendt på fil|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|En anden følsomhedsmærkat blev anvendt på et dokument. <br /><br>Handlingerne for denne aktivitet er forskellige, afhængigt af hvordan navnet er ændret:<br /> - Office på internettet eller en politik for automatisk mærkat (FileSensitivityLabelChanged) <br /> - Microsoft 365 apps (FølsomhedSLabelUpdated)|
|Ændret følsomhedsmærkat på et websted|SensitivityLabelChanged|En anden følsomhedsmærkat blev anvendt på et SharePoint eller Teams websted.|
|Følsomhedsmærkat fjernet fra filen|FileSensitivityLabelRemoved|Et følsomhedsmærkat blev fjernet fra et dokument ved hjælp af Microsoft 365-apps, Office på internettet, en politik for automatisk mærkning eller [Unlock-SPOSensitivityLabelEncryptedFile-cmdlet'en](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile).|
||||

### <a name="retention-policy-and-retention-label-activities"></a>Opbevaringspolitik og opbevaringsmærkataktiviteter

I følgende tabel beskrives konfigurationsaktiviteterne for [opbevaringspolitikker](retention.md) og opbevaringsetiketter, da de blev oprettet, omkonfigureret eller slettet.

|Brugervenligt navn|Handling|Beskrivelse|
|:-----|:-----|:-----|
| Medlemskab af tilpasset omfang ændret |ApplicableAdaptiveScopeChange |Brugere, websteder eller grupper blev føjet til eller fjernet fra det tilpassede omfang. Disse ændringer er resultaterne af at køre omfangets forespørgsel. Da ændringerne er systeminitieret, vises den rapporterede bruger som en GUID i stedet for en brugerkonto.|
| Konfigurerede indstillinger for en opbevaringspolitik |NewRetentionComplianceRule |Administrator har konfigureret opbevaringsindstillingerne for en ny opbevaringspolitik. Opbevaringsindstillinger omfatter, hvor længe elementer bevares, og hvad der sker med elementer, når en opbevaringsperiode udløber (f.eks. sletning af elementer, bevarelse af elementer eller bevarelse og sletning af dem). Denne aktivitet svarer også til at køre [New-RetentionComplianceRule-cmdlet'en](/powershell/module/exchange/new-retentioncompliancerule) .|
| Tilpasset omfang |NewAdaptiveScope |Administratoren har skabt et tilpasset omfang.|
| Oprettet opbevaringsnavn |NewComplianceTag |Administratoren har oprettet et nyt opbevaringsnavn.|
| Oprettet opbevaringspolitik |NewRetentionCompliancePolicy|Administratoren har oprettet en ny opbevaringspolitik.|
| Slettet tilpasset omfang | RemoveAdaptiveScope| Administratoren har slettet et tilpasset omfang.|
| Slettede indstillinger fra en opbevaringspolitik| RemoveRetentionComplianceRule<br/>| Administrator har slettet konfigurationsindstillingerne for en opbevaringspolitik. Denne aktivitet logføres højst sandsynligt, når en administrator sletter en opbevaringspolitik eller kører [cmdlet'en Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule) .|
| Slettet opbevaringsmærkat |RemoveComplianceTag | Administrator har slettet en opbevaringsmærkat.|
| Slettet opbevaringspolitik |RemoveRetentionCompliancePolicy<br/> |Administrator har slettet en opbevaringspolitik. |
| Aktiveret indstilling for lovgivningspost til opbevaringsnavne<br/> |SetRestrictiveRetentionUI |Administratoren kørte [cmdlet'en Set-RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) , så en administrator derefter kan vælge indstillingen til konfiguration af brugergrænsefladen for en opbevaringsetiket for at markere indhold som en lovgivningsmæssig post.|
| Opdateret tilpasset omfang | SetAdaptiveScope | Administratoren har ændret beskrivelsen eller forespørgslen for et eksisterende tilpasset omfang. |
| Opdaterede indstillinger for en opbevaringspolitik | SetRetentionComplianceRule | Administratoren har ændret opbevaringsindstillingerne for en eksisterende opbevaringspolitik. Opbevaringsindstillinger omfatter, hvor længe elementer bevares, og hvad der sker med elementer, når en opbevaringsperiode udløber (f.eks. sletning af elementer, bevarelse af elementer eller bevarelse og sletning af dem). Denne aktivitet svarer også til at køre [cmdlet'en Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) . |
| Opdateret opbevaringsmærkat |SetComplianceTag  | Administratoren har opdateret et eksisterende opbevaringsnavn.|
| Opdateret opbevaringspolitik |SetRetentionCompliancePolicy |Administratoren har opdateret en eksisterende opbevaringspolitik. Opdateringer, der udløser denne hændelse, omfatter tilføjelse eller udelukkelse af indholdsplaceringer, som opbevaringspolitikken anvendes på.|
||||

### <a name="briefing-email-activities"></a>Briefing af mailaktiviteter

I følgende tabel vises aktiviteterne i Briefing af mail, der er logført Microsoft 365 overvågningsloggen. Du kan finde flere oplysninger om Briefing af mail i:

- [Oversigt over Briefing af mail](/Briefing/be-overview)

- [Konfigurere Briefing-mail](/Briefing/be-admin)

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:----|:-----|:-----|
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for organisationen|UpdatedOrganizationBriefingSettings|Administratoren opdaterer organisationens indstillinger for beskyttelse af personlige oplysninger for Briefing af mail. |
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for brugere|OpdateredeBrugerBriefingSettings|Administratoren opdaterer brugernes indstillinger for beskyttelse af personlige oplysninger ved Briefing af mail.
||||

### <a name="myanalytics-activities"></a>MyAnalytics-aktiviteter

I følgende tabel vises de aktiviteter i MyAnalytics, der er logført Microsoft 365 overvågningsloggen. Du kan finde flere oplysninger om MyAnalytics [under MyAnalytics til administratorer](/workplace-analytics/myanalytics/overview/mya-for-admins).

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdaterede indstillinger for organisationen MyAnalytics|UpdatedOrganizationMyAnalyticsSettings|Administratoren opdaterer indstillingerne på organisationsniveau for MyAnalytics. |
|Opdaterede brugerindstillinger for MyAnalytics|OpdateredeBrugerMyAnalyticsSettings|Administratoren opdaterer brugerindstillinger for MyAnalytics.|
||||

### <a name="information-barriers-activities"></a>Aktiviteter for informationsbarrierer

I følgende tabel vises aktiviteterne i informationsbarrierer, der logføres i Microsoft 365 overvågningsloggen. Du kan finde flere oplysninger om [informationsbarrierer under Få mere at vide om informationsbarrierer Microsoft 365](information-barriers.md).

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:----------------|:------------|:--------------|
| Segmenter føjet til et websted | Segmenter, der er tilad | En SharePoint, global administrator eller webstedsejer har føjet et eller flere oplysningsbarrieresegmenter til et websted. |
| Ændrede segmenter på et websted | SegmenterÆndret | En SharePoint eller global administrator har ændret et eller flere informationsbarrieresegmenter for et websted. |
| Fjernede segmenter fra et websted | Segmenter Flyttet | En SharePoint eller en global administrator har fjernet et eller flere informationsbarrieresegmenter fra et websted. |
||||

### <a name="disposition-review-activities"></a>Aktiviteter for dispositionsgennemsyn

I følgende tabel vises de aktiviteter, som en dispositionsvurdering tog, da et element nåede slutningen af sin konfigurerede opbevaringsperiode. Du kan finde flere oplysninger [under Få vist og fjerne indhold](disposition.md#viewing-and-disposing-of-content).

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:-----|:-----|:-----|
|Godkendt afhændelse|ApproveDisposal|En fordelings gennemgår godkendte dispositionen af elementet for at flytte det til næste dispositionsfase. Hvis elementet var i den eneste eller sidste fase af gennemgangen af dispositionen, markerede godkendelse af disposition elementet som berettiget til permanent sletning.|
|Udvidet opbevaringsperiode|UdvidRetention|En dispositionsrevision forlængede opbevaringsperioden for elementet.|
|Element med navn|RelabelItem|En dispositionsrevision har omnavnet opbevaringsetiketten.|
|Tilføjede korrekturlæsere|AddReviewer|En korrekturlæser til disposition har føjet en eller flere andre brugere til den aktuelle dispositionsgennemsynsfase.|
||||

### <a name="communication-compliance-activities"></a>Aktiviteter til overholdelse af regler og standarder i kommunikation

I følgende tabel vises de aktiviteter til overholdelse af regler og standarder, der logføres Microsoft 365 overvågningsloggen. Få mere at vide under [Få mere at vide om overholdelse af kommunikationsoplysninger Microsoft 365](communication-compliance.md).

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdatering af politik|OvervågningspolitikOprettet, OvervågningspolitikOpdater, OvervågningspolitikSlettet|En administrator for kommunikationsoverholdelse har udført en opdatering af politikken.|
|Match af politik|OvervågningsregelMatch|En bruger har sendt en meddelelse, der opfylder en politiks betingelse.|
|Mærke anvendt på meddelelser|KontrolReviewTag|Mærker anvendes på meddelelser, eller meddelelser løses.|
||||

### <a name="report-activities"></a>Rapportere aktiviteter

I følgende tabel vises aktiviteterne for brugsrapporter, der logføres i Microsoft 365 overvågningsloggen.

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for brugsrapport|UpdateUsageReportsPrivacySetting|Administratoren har opdateret indstillingerne for beskyttelse af personlige oplysninger for brugsrapporter. |
||||

### <a name="exchange-admin-audit-log"></a>Exchange overvågningsloggen for administratorer

Exchange overvågningslogføring for administratorer (der er aktiveret som standard i Microsoft 365), registreres en hændelse i overvågningsloggen, når en administrator (eller en bruger, der har fået tildelt administrative rettigheder) foretager en ændring i Exchange Online organisation. Ændringer, der er foretaget ved hjælp af Exchange Administration eller ved at køre en cmdlet i Exchange Online PowerShell, logføres i Exchange-administratorrevisionsloggen. Cmdlet'er, der starter med verberne **Get-**, **Search-** eller **Test-** logføres ikke i overvågningsloggen. Du kan finde flere oplysninger om logføring af administratorkontrol i Exchange i [Overvågningslogføring for administratorer](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Nogle Exchange Online cmdlet'er, der ikke er logget i Exchange eller i overvågningsloggen. Mange af disse cmdlet'er er relateret til vedligeholdelse af Exchange Online-tjenesten og køres af medarbejdere eller tjenestekonti i Microsofts datacenter. Disse cmdlet'er logføres ikke, fordi de medfører et stort antal "støjende" overvågningshændelser. Hvis der er en Exchange Online-cmdlet, der ikke bliver overvåget, skal du sende en anmodning om designændring (DCR) til Microsoft Support.

Her er nogle tip til at søge efter Exchange administratoraktiviteter, når du søger i overvågningsloggen:

- Hvis du vil returnere poster Exchange overvågningsloggen for administratorer, skal du markere **Vis resultater for alle** aktiviteter på **listen** Aktiviteter. Brug felterne for datoområde og listen  Brugere til at indsnævre søgeresultaterne for cmdlet'er, der køres af en bestemt Exchange inden for et bestemt datoområde.

- Hvis du vil have vist hændelser Exchange overvågningsloggen for administratorer, skal  du klikke på kolonnen Aktivitet for at sortere cmdlet-navnene i alfabetisk rækkefølge.

- Hvis du vil have oplysninger om, hvilken cmdlet der blev kørt, hvilke parametre og parameterværdier der blev brugt, og hvilke objekter der blev påvirket, kan du eksportere søgeresultaterne ved at vælge indstillingen **Hent alle** resultater. Få mere at vide under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

- Du kan også bruge kommandoen i `Search-UnifiedAuditLog -RecordType ExchangeAdmin` Exchange Online PowerShell til kun at returnere overvågningsposter fra Exchange for administrator. Det kan tage op til 30 minutter, efter at Exchange en cmdlet køres, før den tilsvarende post i overvågningsloggen returneres i søgeresultaterne. Få mere at vide [under Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). Hvis du vil have mere at vide om at eksportere de søgeresultater, der returneres af cmdlet'en **Search-UnifiedAuditLog til en CSV-fil**, skal du se afsnittet "Tips til eksport og visning af overvågningsloggen" i Eksportere, konfigurere og få vist [overvågningslogposter](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Du kan også få vist hændelser i Exchange-administrator overvågningsloggen ved hjælp af Exchange Administration eller ved at køre **Search-AdminAuditLog** i Exchange Online PowerShell. Dette er en god metode til specifikt at søge efter aktivitet, der er udført Exchange Online administratorer. Du kan finde en vejledning under:

  - [Få vist overvågningsloggen for administratoren](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Husk, at de samme Exchange administratoraktiviteter logges på både overvågningsloggen Exchange og overvågningsloggen.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvad er forskellige Microsoft 365, der overvåges i øjeblikket?**

De mest anvendte tjenester som Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Dynamics 365, Defender til Office 365 og Power BI  overvåges. Se starten [af denne artikel for at](search-the-audit-log-in-security-and-compliance.md) få en liste over tjenester, der overvåges.

**Hvilke aktiviteter overvåges af overvågningstjenesten i Microsoft 365?**

Se afsnittet [Overvågede aktiviteter](#audited-activities) i denne artikel for at få en liste over og en beskrivelse af de aktiviteter, der overvåges.

**Hvor lang tid tager det, før en overvågningspost er tilgængelig, efter der er indtruffet en hændelse?**

De fleste overvågningsdata er tilgængelige inden for 30 minutter, men det kan tage op til 24 timer, efter en hændelse forekommer, før den tilsvarende post i overvågningsloggen vises i søgeresultaterne. Se tabellen i [afsnittet Før du](#before-you-search-the-audit-log) søger i overvågningsloggen i denne artikel, der viser den tid, det tager for hændelser i de forskellige tjenester at være tilgængelige.

**Hvor længe bevares overvågningsposterne for?**

Som beskrevet tidligere bevares overvågningsposter for aktiviteter, der udføres af brugere, der er tildelt en Office 365 E5- eller Microsoft E5-licens (eller brugere med Microsoft 365 E5-tilføjelseslicens), i et år. For alle andre abonnementer, der understøtter samlet overvågningslogføring, bevares overvågningsposter i 90 dage.

**Kan jeg få programmeringsadgang til overvågningsdataene?**

Ja. Administrationsaktivitets-API'en Office 365 bruges til at hente overvågningslogfilerne programmeringligt.  For at komme i gang skal [du se Introduktion til Office 365 administrations-API'er](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Er der andre måder at få overvågningslogfiler på end ved hjælp af Security and Compliance Center eller Office 365 Management Activity API?**

Nej. Dette er de eneste to måder, du kan hente data fra overvågningstjenesten på.

**Skal jeg aktivere overvågning individuelt for hver tjeneste, som jeg vil registrere overvågningslogfiler for?**

I de fleste tjenester er overvågning aktiveret som standard, efter at du har aktiveret overvågning for organisationen (som beskrevet i afsnittet [](#before-you-search-the-audit-log) Før du søger i overvågningsloggen i denne artikel).

**Understøtter overvågningstjenesten deplikering af poster?**

Nej. Overvågningstjenestens pipeline er næsten i realtid og kan derfor ikke understøtte duplikering.

**Hvor gemmes overvågningsdata?**

Vi har i øjeblikket installationer af overvågningspipeline i NA-områder (Nordamerika), EMEA (Europa, Mellemøsten og Afrika) og APAC (Asien/Stillehavsområdet). Lejere, der er hjem for disse områder, vil have deres overvågningsdata gemt i området. For lejere med flere geografiske områder gemmes de overvågningsdata, der indsamles fra alle områder af lejeren, kun i lejerens hjemmeområde. Vi kan dog flowe dataene på tværs af disse områder for at give belastningsjustering og kun under problemer med live-webstedet. Når vi udfører disse aktiviteter, krypteres dataene under overførsel. 

**Er overvågningsdata krypteret?**

Overvågningsdata gemmes i Exchange (in rest-data) i det samme område, hvor den samlede overvågningspipeline er installeret. Postkassedata, der er i hvile, krypteres ikke af Exchange. Kryptering på tjenesteniveau krypterer dog alle postkassedata, fordi Exchange servere i Microsofts datacentre er krypteret via BitLocker. Du kan finde flere [oplysninger Microsoft 365 kryptering til Skype for Business, OneDrive for Business, SharePoint Online og Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Maildata under overførsel er altid krypteret.
