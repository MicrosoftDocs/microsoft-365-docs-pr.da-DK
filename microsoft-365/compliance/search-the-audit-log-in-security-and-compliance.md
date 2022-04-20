---
title: Søg i overvågningsloggen på Microsoft Purview-overholdelsesportalen
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
description: Brug Microsoft Purview-overholdelsesportalen til at søge i den samlede overvågningslog for at få vist bruger- og administratoraktivitet i din organisation.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: f35bfbbe299495e912d018bd00615964f883031e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936263"
---
# <a name="search-the-audit-log-in-the-compliance-center"></a>Søg i overvågningsloggen i Overholdelsescenter

Har du brug for at finde ud af, om en bruger fik vist et bestemt dokument eller fjernede et element fra sin postkasse? Hvis det er tilfældet, kan du bruge søgeværktøjet til overvågningslog på Microsoft Purview-overholdelsesportalen til at søge i den samlede overvågningslog for at få vist bruger- og administratoraktivitet i din organisation. Tusindvis af bruger- og administratorhandlinger, der udføres i mange Microsoft 365 tjenester og løsninger, registreres, registreres og bevares i din organisations samlede overvågningslog. Brugere i din organisation kan bruge søgeværktøjet til overvågningslog til at søge efter, få vist og eksportere overvågningsposterne for disse handlinger til en CSV-fil.

## <a name="microsoft-365-services-that-support-auditing"></a>Microsoft 365 tjenester, der understøtter overvågning

Hvorfor en samlet overvågningslog? Da du kan søge i overvågningsloggen efter aktiviteter, der er udført i forskellige Microsoft 365 tjenester. I følgende tabel vises de Microsoft 365 tjenester og funktioner (i alfabetisk rækkefølge), der understøttes af den samlede overvågningslog.

| Microsoft 365 tjeneste eller funktion | Posttyper|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| Kommunikationsoverholdelse|ComplianceSuperVisionExchange|
| Indholdsoversigt|LabelContentExplorer|
| Forebyggelse af datatab (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| eDiscovery|Discovery, AeD|
| Nøjagtigt datamatch|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Former|MicrosoftForms|
| Informationsbarrierer|InformationBarrierPolicyApplication|
| Microsoft 365 Defender|AirInvestigation, AirManualInvestigation, AirAdminActionInvestigation, MS365DCustomDetection|
| Microsoft Teams|MicrosoftTeams|
| MyAnalytics|Indstillinger for MyAnalytics|
| OneDrive for Business|OneDrive|
| Power Apps|PowerAppsApp, PowerAppsPlan|
| Power Automate|MicrosoftFlow|
| Power BI|PowerBIAudit|
| Karantæne|Karantæne|
| Opbevaringspolitikker og opbevaringsmærkater|MIPLabel, MipAutoLabelExchangeItem, MipAutoLabelSharePointItem, MipAutoLabelSharePointPolicyLocation|
| Typer af følsomme oplysninger|DlpSensitiveInformationType|
| Følsomhedsmærkater|MIPLabel, SensitivityLabelAction, SensitivityLabeledFileAction, SensitivityLabelPolicyMatch|
| SharePoint Online|SharePoint, SharePointFileOperation,SharePointSharingOperation, SharePointListOperation, SharePointCommentOperation |
| Stream|MicrosoftStream|
| Threat Intelligence|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|
|||

Du kan få flere oplysninger om de handlinger, der overvåges i hver af de tjenester, der er angivet i den forrige tabel, i afsnittet [Overvågede aktiviteter](#audited-activities) i denne artikel.

Den forrige tabel identificerer også den posttypeværdi, der skal bruges til at søge i overvågningsloggen efter aktiviteter i den tilsvarende tjeneste ved hjælp af cmdlet'en **Search-UnifiedAuditLog** i Exchange Online PowerShell eller ved hjælp af et PowerShell-script. Nogle tjenester har flere posttyper til forskellige typer aktiviteter i den samme tjeneste. Du kan få en mere komplet liste over overvågningsposttyper [under Office 365 API-skema til administrationsaktivitet](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Du kan finde flere oplysninger om, hvordan du bruger PowerShell til at søge i overvågningsloggen, i:

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Før du søger i overvågningsloggen

Sørg for at læse følgende elementer, før du begynder at søge i overvågningsloggen.

- Søgning i overvågningslog er som standard slået til for Microsoft 365 og Office 365 virksomhedsorganisationer. Hvis du vil kontrollere, at søgning i overvågningslog er slået til, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  Værdien for `True` egenskaben *UnifiedAuditLogIngestionEnabled* angiver, at søgning i overvågningslog er slået til. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

- Du skal have tildelt rollen View-Only overvågningslogge eller overvågningslogge i Exchange Online for at søge i overvågningsloggen. Disse roller tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden **Tilladelser** i Exchange Administration. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Hvis du vil give en bruger mulighed for at søge i overvågningsloggen med minimumsniveauet for rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only Overvågningslogge eller Overvågningslogge og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan få flere oplysninger under [Administrer rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

  > [!IMPORTANT]
  > Hvis du tildeler en bruger rollen View-Only overvågningslogge eller overvågningslogge på siden **Tilladelser på overholdelsesportalen** , kan vedkommende ikke søge i overvågningsloggen. Du skal tildele tilladelserne i Exchange Online. Det skyldes, at den underliggende cmdlet, der bruges til at søge i overvågningsloggen, er en Exchange Online-cmdlet.

- Når en overvåget aktivitet udføres af en bruger eller administrator, oprettes der en overvågningspost, som gemmes i overvågningsloggen for din organisation. Den tid, en overvågningspost opbevares (og kan søges i i overvågningsloggen), afhænger af dit Office 365 eller Microsoft 365 Enterprise abonnement, og specifikt den licenstype, der er tildelt til bestemte brugere.

  - For brugere, der har fået tildelt en Office 365 E5- eller Microsoft 365 E5-licens (eller brugere med en Microsoft 365 E5 Overholdelse- eller Microsoft 365 E5 licens til eDiscovery- og overvågningstilføjelsesprogram), overvåges poster for Azure Active Directory, Exchange og SharePoint aktiviteter bevares som standard i et år. Organisationer kan også oprette opbevaringspolitikker for overvågningslog for at bevare overvågningsposter for aktiviteter i andre tjenester i op til et år. Du kan få flere oplysninger under [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md).

    > [!NOTE]
    > Hvis din organisation har deltaget i det private prøveversionsprogram for opbevaring af overvågningsposter i ét år, nulstilles opbevaringsvarigheden for de overvågningsposter, der blev genereret før udrulningsdatoen for generel tilgængelighed.

  - For brugere, der har fået tildelt andre (ikke-E5) Office 365 eller Microsoft 365 licens, bevares overvågningsposter i 90 dage. Du kan se en liste over Office 365 og Microsoft 365 abonnementer, der understøtter samlet overvågningslogføring, [i tjenestebeskrivelsen for Security and Compliance Center](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Selvom overvågning af postkasser som standard er slået til, vil du måske bemærke, at overvågningshændelser for postkasser for nogle brugere ikke findes i søgninger i overvågningsloggen på overholdelsesportalen eller via API'en for Office 365 administrationsaktiviteter. Du kan få flere oplysninger under [Flere oplysninger om logføring af overvågning af postkasser](enable-mailbox-auditing.md#more-information).

- Hvis du vil slå søgning i overvågningslog for din organisation fra, kan du køre følgende kommando i den eksterne PowerShell, der er forbundet med din Exchange Online organisation:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Hvis du vil aktivere overvågningssøgning igen, kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Du kan finde flere oplysninger under [Slå søgning i overvågningslog fra](turn-audit-log-search-on-or-off.md).

- Som tidligere nævnt er den underliggende cmdlet, der bruges til at søge i overvågningsloggen, en Exchange Online-cmdlet, som er **Search-UnifiedAuditLog**. Det betyder, at du kan bruge denne cmdlet til at søge i overvågningsloggen i stedet for at bruge søgeværktøjet på siden **Overvågning** på overholdelsesportalen. Du skal køre denne cmdlet i Exchange Online PowerShell. Du kan finde flere oplysninger under [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  Du kan finde oplysninger om eksport af de søgeresultater, der **returneres af Search-UnifiedAuditLog-cmdlet'en**, til en CSV-fil i afsnittet "Tips til eksport og visning af overvågningsloggen" i [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Hvis du vil downloade data fra overvågningsloggen programmeringsmæssigt, anbefaler vi, at du bruger API'en Office 365 Management Activity i stedet for at bruge et PowerShell-script. API'en Office 365 managementaktivitet er en REST-webtjeneste, som du kan bruge til at udvikle løsninger til overvågning af drift, sikkerhed og overholdelse af angivne standarder for din organisation. Du kan få flere oplysninger under [Office 365 API-reference til administrationsaktivitet](/office/office-365-management-api/office-365-management-activity-api-reference).

- Azure Active Directory (Azure AD) er katalogtjenesten til Microsoft 365. Den samlede overvågningslog indeholder bruger-, gruppe-, program-, domæne- og katalogaktiviteter, der udføres i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> eller i Azure-administrationsportalen. Du kan se en komplet liste over Azure AD-hændelser [under Azure Active Directory Hændelser i overvågningsrapport](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Microsoft garanterer ikke et bestemt tidspunkt, efter at der opstår en hændelse, for at den tilsvarende overvågningspost returneres i resultaterne af en søgning i overvågningsloggen. For kernetjenester (f.eks. Exchange, SharePoint, OneDrive og Teams) er tilgængeligheden af overvågningsposter typisk 60-90 minutter, efter at en hændelse forekommer. For andre tjenester kan tilgængeligheden af overvågningsposter være længere. Nogle problemer, der er uundgåelige (f.eks. serverafbrydelser), kan dog opstå uden for overvågningstjeneste, der forsinker tilgængeligheden af overvågningsposter. Af denne grund forpligter Microsoft sig ikke til et bestemt tidspunkt.

- Overvågningslogføring for Power BI er ikke aktiveret som standard. Hvis du vil søge efter Power BI aktiviteter i overvågningsloggen, skal du aktivere overvågning på Power BI administrationsportal. Du kan finde instruktioner i afsnittet "Overvågningslogge" i [Power BI administrationsportal](/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Søgning i overvågningsloggen

Her er processen til søgning i overvågningsloggen i Microsoft 365.

[Trin 1: Kør en søgning i overvågningsloggen](#step-1-run-an-audit-log-search)

[Trin 2: Få vist søgeresultaterne](#step-2-view-the-search-results)

[Trin 3: Eksportér søgeresultaterne til en fil](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>Trin 1: Kør en søgning i overvågningsloggen

1. Gå til , <https://compliance.microsoft.com> og log på.

    > [!TIP]
    > Brug en privat browsersession (ikke en almindelig session) til at få adgang til overholdelsesportalen, da det forhindrer, at de legitimationsoplysninger, du i øjeblikket er logget på med, bruges. Tryk på **CTRL+SKIFT+N** for at åbne en InPrivate-browsingsession i Microsoft Edge eller en privat browsersession i Google Chrome (kaldet et inkognitovindue).

2. Klik på **Overvågning** i venstre rude på overholdelsesportalen.

    Siden **Overvågning** vises.

    ![Konfigurer kriterier, og klik derefter på Søg for at køre rapporten.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > Hvis linket **Start optagelse af bruger- og administratoraktivitet** vises, skal du klikke på det for at aktivere overvågning. Hvis du ikke kan se dette link, er overvågning slået til for din organisation.

3. Konfigurer følgende søgekriterier under fanen **Søg** :

   1. **Startdato** og **Slutdato**: De seneste syv dage er valgt som standard. Vælg et dato- og klokkeslætsinterval for at få vist de hændelser, der opstod inden for den pågældende periode. Dato og klokkeslæt vises i lokaltid. Det maksimale datointerval, du kan angive, er 90 dage. Der vises en fejl, hvis det valgte datointerval er større end 90 dage.

    > [!TIP]
    > Hvis du bruger det maksimale datointerval på 90 dage, skal du vælge det aktuelle klokkeslæt for **startdatoen**. Ellers får du vist en fejl, hvor der står, at startdatoen ligger før slutdatoen. Hvis du har slået overvågning til inden for de seneste 90 dage, kan det maksimale datointerval ikke starte før den dato, hvor overvågning blev slået til.

   2. **Aktiviteter**: Klik på rullelisten for at få vist de aktiviteter, du kan søge efter. Bruger- og administratoraktiviteter er organiseret i grupper af relaterede aktiviteter. Du kan vælge bestemte aktiviteter, eller du kan klikke på navnet på aktivitetsgruppen for at vælge alle aktiviteter i gruppen. Du kan også klikke på en valgt aktivitet for at rydde markeringen. Når du har kørt søgningen, er det kun overvågningslogposterne for de valgte aktiviteter, der vises. Hvis du vælger **Vis resultater for alle aktiviteter** , vises resultaterne for alle de aktiviteter, der er udført af den valgte bruger eller gruppe af brugere.<br/><br/>Der logføres mere end 100 bruger- og administratoraktiviteter i overvågningsloggen. Klik på fanen **Overvågede aktiviteter** under emnet i denne artikel for at se beskrivelserne af hver aktivitet i hver af de forskellige tjenester.

   3. **Brugere**: Klik i dette felt, og vælg derefter en eller flere brugere, der skal vises søgeresultater for. Overvågningslogposterne for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i din organisation.

   4. **Fil, mappe eller websted**: Skriv et eller hele navnet på en fil eller mappe for at søge efter aktivitet, der er relateret til filen med den mappe, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse, skal du sørge for at skrive hele URL-stien, eller hvis du skriver en del af URL-adressen, skal du ikke inkludere specialtegn eller mellemrum (brug af jokertegn (\*) understøttes.<br/><br/>Lad dette felt være tomt for at returnere poster for alle filer og mapper i din organisation.

    > [!TIP]
    >
    > - Hvis du leder efter alle aktiviteter, der er relateret til et **websted**, skal du tilføje jokertegnet (\*) efter URL-adressen for at returnere alle poster for det pågældende websted, `"https://contoso-my.sharepoint.com/personal*"`f.eks. .
    >
    > - Hvis du leder efter alle aktiviteter, der er relateret til en **fil**, skal du tilføje jokertegnet (\*) før filnavnet for at returnere alle poster for den pågældende fil, `"*Customer_Profitability_Sample.csv"`f.eks. .

4. Klik på **Søg** for at køre søgningen ved hjælp af dine søgekriterier.

   Søgeresultaterne indlæses, og efter et øjeblik vises de på en ny side. Når søgningen er fuldført, vises antallet af fundne resultater. Der vises maksimalt 50.000 hændelser i intervaller af 150 hændelser. Hvis mere end 50.000 hændelser opfylder søgekriterierne, er det kun de 50.000 usorterede hændelser, der returneres, der vises.

   ![Antallet af resultater vises, når søgningen er fuldført.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Tips til søgning i overvågningsloggen

- Du kan vælge bestemte aktiviteter, du vil søge efter, ved at klikke på aktivitetsnavnet. Du kan også søge efter alle aktiviteter i en gruppe (f.eks **. fil- og mappeaktiviteter**) ved at klikke på gruppenavnet. Hvis der er valgt en aktivitet, kan du klikke på den for at annullere markeringen. Du kan også bruge søgefeltet til at få vist de aktiviteter, der indeholder det nøgleord, du skriver.

  ![Klik på navnet på aktivitetsgruppen for at vælge alle aktiviteter.](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Du skal vælge **Vis resultater for alle aktiviteter** på listen **Aktiviteter** for at få vist hændelser fra Exchange administratorens overvågningslog. Hændelser fra denne overvågningslog viser et cmdlet-navn (f.eks **. Set-Mailbox**) i kolonnen **Aktivitet** i resultaterne. Du kan få flere oplysninger ved at klikke på fanen **Overvågede aktiviteter** i dette emne og derefter klikke på **Exchange administratoraktiviteter**.

  På samme måde er der nogle overvågningsaktiviteter, der ikke har et tilsvarende element på listen **Aktiviteter** . Hvis du kender navnet på handlingen for disse aktiviteter, kan du søge efter alle aktiviteter og derefter filtrere handlingerne, når du har eksporteret søgeresultaterne til en CSV-fil.

- Klik på **Ryd** for at rydde de aktuelle søgekriterier. Datointervallet vender tilbage til standarden for de seneste syv dage. Du kan også klikke på **Ryd alle for at få vist resultater for alle aktiviteter for** at annullere alle valgte aktiviteter.

- Hvis der findes 50.000 resultater, kan du sandsynligvis antage, at der er mere end 50.000 hændelser, der opfylder søgekriterierne. Du kan enten afgrænse søgekriterierne og køre søgningen igen for at returnere færre resultater, eller du kan eksportere alle søgeresultaterne ved at vælge **Eksportér resultater** \> **Download alle resultater**.

### <a name="step-2-view-the-search-results"></a>Trin 2: Få vist søgeresultaterne

Resultaterne af en søgning i overvågningsloggen vises under **Resultater** på **siden Søgning i overvågningslog** . Som tidligere nævnt vises der maksimalt 50.000 (nyeste) hændelser i intervaller af 150 hændelser. Brug rullepanelet, eller tryk på **Skift + End** for at få vist de næste 150 hændelser.

Resultaterne indeholder følgende oplysninger om hver hændelse, der returneres af søgningen:

- **Dato**: Den dato og det klokkeslæt (i dit lokale klokkeslæt), da hændelsen fandt sted.

- **IP-adresse**: IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.

   > [!NOTE]
  > For nogle tjenester kan den værdi, der vises i dette felt, være IP-adressen for et program, der er tillid til (f.eks. Office på internettet apps), der ringer til tjenesten på vegne af en bruger, og ikke IP-adressen på den enhed, der bruges af den person, der udførte aktiviteten. Desuden logføres IP-adressen ikke for administratoraktivitet (eller aktivitet, der udføres af en systemkonto) for Azure Active Directory-relaterede hændelser, og den værdi, der vises i dette felt, er `null`.

- **Bruger**: Den bruger (eller tjenestekonto), der udførte den handling, der udløste hændelsen.

- **Aktivitet**: Den aktivitet, der udføres af brugeren. Denne værdi svarer til de aktiviteter, du har valgt på rullelisten **Aktiviteter** . For en hændelse fra Exchange administratorens overvågningslog er værdien i denne kolonne en Exchange cmdlet.

- **Element**: Det objekt, der blev oprettet eller ændret som følge af den tilsvarende aktivitet. Det kan f.eks. være den fil, der blev vist eller ændret, eller den brugerkonto, der blev opdateret. Ikke alle aktiviteter har en værdi i denne kolonne.

- **Detaljer**: Flere oplysninger om en aktivitet. Det er ikke alle aktiviteter, der har en værdi.

> [!TIP]
> Klik på en kolonneoverskrift under **Resultater** for at sortere resultaterne. Du kan sortere resultaterne fra A til Å eller Å til A. Klik på overskriften **Dato** for at sortere resultaterne fra ældste til nyeste eller nyeste til ældste.

#### <a name="view-the-details-for-a-specific-event"></a>Få vist detaljerne for en bestemt hændelse

Du kan få vist flere oplysninger om en hændelse ved at klikke på hændelsesposten på listen over søgeresultater. Der vises en pop op-side, der indeholder de detaljerede egenskaber fra hændelsesposten. De egenskaber, der vises, afhænger af den tjeneste, hvor hændelsen forekommer. 

### <a name="step-3-export-the-search-results-to-a-file"></a>Trin 3: Eksportér søgeresultaterne til en fil

Du kan eksportere resultaterne af en søgning i overvågningsloggen til en kommasepareret værdifil (CSV) på din lokale computer. Du kan åbne denne fil i Microsoft Excel og bruge funktioner som f.eks. søgning, sortering, filtrering og opdeling af en enkelt kolonne (der indeholder flere egenskaber) i flere kolonner.

1. Kør en søgning i overvågningsloggen, og rediger derefter søgekriterierne, indtil du har de ønskede resultater.

2. Klik på **EksportérDownload** >  **alle resultater** på siden med søgeresultater.

   Alle poster fra overvågningsloggen, der opfylder søgekriterierne, eksporteres til en CSV-fil. Rådata fra overvågningsloggen gemmes i en CSV-fil. Yderligere oplysninger fra posten i overvågningsloggen er inkluderet i en kolonne med navnet **AuditData** i CSV.

     > [!IMPORTANT]
     > Du kan maksimalt downloade 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis 50.000 poster downloades til CSV-filen, kan du sandsynligvis antage, at der er mere end 50.000 hændelser, der opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et datointerval til at reducere antallet af overvågningslogposter. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.

3. Når eksporten er fuldført, vises der en meddelelse øverst i vinduet, hvor du bliver bedt om at åbne CSV-filen og gemme den på din lokale computer. Du kan også få adgang til CSV-filen i mappen Downloads.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Flere oplysninger om eksport og visning af søgeresultater i overvågningsloggen

- Når du downloader alle søgeresultater, indeholder CSV-filen kolonnerne **CreationDate**, **UserIds**, **Operations** og **AuditData**. Kolonnen **AuditData** indeholder yderligere oplysninger om hver enkelt hændelse (svarer til de detaljerede oplysninger, der vises på pop op-siden, når du får vist søgeresultaterne i Overholdelsescenter). Dataene i denne kolonne består af et JSON-objekt, der indeholder flere egenskaber fra overvågningslogposten. Hvert *property:value-par* i JSON-objektet er adskilt af et komma. Du kan bruge JSON-transformeringsværktøjet i Power Query-editor i Excel til at opdele kolonnen **AuditData** i flere kolonner, så hver egenskab i JSON-objektet har sin egen kolonne. Det giver dig mulighed for at sortere og filtrere på en eller flere af disse egenskaber. Du kan finde en trinvis vejledning i, hvordan du bruger Power Query-editor til at transformere JSON-objektet, under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

  Når du har opdelt kolonnen **AuditData** , kan du filtrere kolonnen **Handlinger** for at få vist de detaljerede egenskaber for en bestemt type aktivitet.

- Når du downloader alle resultater fra en søgeforespørgsel, der indeholder hændelser fra forskellige tjenester, indeholder kolonnen **AuditData** i CSV-filen forskellige egenskaber, afhængigt af hvilken tjeneste handlingen blev udført i. Poster fra Exchange og Azure AD-overvågningslogge omfatter f.eks. en egenskab med navnet **ResultStatus**, der angiver, om handlingen lykkedes eller ej. Denne egenskab er ikke inkluderet for hændelser i SharePoint. På samme måde har SharePoint hændelser en egenskab, der identificerer WEBSTEDETs URL-adresse for fil- og mapperelaterede aktiviteter. Du kan afhjælpe denne funktionsmåde ved at overveje at bruge forskellige søgninger til at eksportere resultaterne for aktiviteter fra en enkelt tjeneste.

  Du kan finde en beskrivelse af mange af de egenskaber, der er angivet i kolonnen **AuditData** i CSV-filen, når du downloader alle resultater, og den tjeneste, som hver enkelt gælder for, [under Detaljerede egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Overvågede aktiviteter

Tabellerne i dette afsnit beskriver de aktiviteter, der overvåges i Microsoft 365. Du kan søge efter disse hændelser ved at søge i overvågningsloggen i Security and Compliance Center.

Disse tabeller grupperer relaterede aktiviteter eller aktiviteter fra en bestemt tjeneste. Tabellerne indeholder det fulde navn, der vises på rullelisten **Aktiviteter** , og navnet på den tilsvarende handling, der vises i detaljerede oplysninger om en overvågningspost og i CSV-filen, når du eksporterer søgeresultaterne. Du kan finde beskrivelser af de detaljerede oplysninger [under Detaljerede egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md).

Klik på et af følgende links for at gå til en bestemt tabel.

:::row:::
    :::column:::
        [Fil- og sideaktiviteter](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Mappeaktiviteter](#folder-activities)
    :::column-end:::
    :::column:::
        [SharePoint listeaktiviteter](#sharepoint-list-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Delings- og adgangsanmodningsaktiviteter](#sharing-and-access-request-activities)
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
        [Webstedsadministrationsaktiviteter](#site-administration-activities)
    :::column-end:::
    :::column:::
        [Exchange postkasseaktiviteter](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Brugeradministrationsaktiviteter](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Administrationsaktiviteter for Azure AD-grupper](#azure-ad-group-administration-activities)
    :::column-end:::
    :::column:::
        [Programadministrationsaktiviteter](#application-administration-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter til rolleadministration](#role-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter til administration af adresseliste](#directory-administration-activities)
    :::column-end:::
    :::column:::
        [eDiscovery-aktiviteter](#ediscovery-activities)
    :::column-end:::
    :::column:::
        [eDiscovery-aktiviteter (Premium)](#ediscovery-premium-activities)
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
        [Microsoft Teams skiftaktiviteter](#microsoft-teams-shifts-activities)
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
        [Microsoft Stream aktiviteter](#microsoft-stream-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter i Indholdsoversigt](#content-explorer-activities)
    :::column-end:::
    :::column:::
        [Karantæneaktiviteter](#quarantine-activities)
    :::column-end:::
    :::column:::
        [Microsoft Forms aktiviteter](#microsoft-forms-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter med følsomhedsmærkater](#sensitivity-label-activities)
    :::column-end:::
    :::column:::
        [Opbevaringspolitik og aktiviteter med opbevaringsmærkater](#retention-policy-and-retention-label-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter i briefingmail](#briefing-email-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [MyAnalytics-aktiviteter](#myanalytics-activities)
    :::column-end:::
    :::column:::
        [Aktiviteter inden for informationsbarrierer](#information-barriers-activities)
    :::column-end:::
    :::column:::
        [Dispositionsgennemgangsaktiviteter](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Aktiviteter i forbindelse med overholdelse af angivne standarder for kommunikation](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Rapportaktiviteter](#report-activities)
    :::column-end:::
    :::column:::
        [Exchange administratoraktiviteter](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Fil- og sideaktiviteter

I følgende tabel beskrives fil- og sideaktiviteterne i SharePoint Online og OneDrive for Business.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Åbnet fil|FileAccessed|Bruger- eller systemkonto får adgang til en fil. Når en bruger har adgang til en fil, logføres hændelsen FileAccessed ikke igen for den samme bruger for samme fil i de næste fem minutter.|
|(ingen)|FileAccessedExtended|Dette er relateret til aktiviteten "Tilgået fil" (FileAccessed). En FileAccessedExtended-hændelse logføres, når den samme person til stadighed får adgang til en fil i en længere periode (op til 3 timer). <br/><br/> Formålet med logføring af FileAccessedExtended-hændelser er at reducere antallet af FileAccessed-hændelser, der logføres, når en fil tilgås løbende. Dette hjælper med at reducere støjen fra flere FileAccessed-poster for det, der i bund og grund er den samme brugeraktivitet, og giver dig mulighed for at fokusere på den indledende (og vigtigere) FileAccessed-hændelse.|
|Ændret opbevaringsmærkat for en fil|ComplianceSettingChanged|Der blev anvendt en opbevaringsmærkat på eller fjernet fra et dokument. Denne hændelse udløses, når en opbevaringsmærkat anvendes manuelt eller automatisk på en meddelelse.|
|Poststatus er ændret til låst|LåsPost|Poststatussen for en opbevaringsmærkat, der klassificerer et dokument som en post, var låst. Det betyder, at dokumentet ikke kan redigeres eller slettes. Det er kun brugere, der som minimum har tilladelsen som bidragyder for et websted, der kan ændre poststatus for et dokument.|
|Poststatus er ændret til ulåst|Låspost op|Poststatussen for en opbevaringsmærkat, der klassificerer et dokument som en post, blev låst op. Det betyder, at dokumentet kan redigeres eller slettes. Det er kun brugere, der som minimum har tilladelsen som bidragyder for et websted, der kan ændre poststatus for et dokument.|
|Filen tjekket ind|FileCheckedIn|Brugeren tjekker et dokument ind, som brugeren har tjekket ud fra et dokumentbibliotek.|
|Tjekket ud-fil|FileCheckedOut|Brugeren tjekker et dokument, der er placeret i et dokumentbibliotek, ud. Brugerne kan tjekke dokumenter ud og foretage ændringer, der er blevet delt med dem.|
|Kopieret fil|Filkopieret|Brugeren kopierer et dokument fra et websted. Den kopierede fil kan gemmes i en anden mappe på webstedet.|
|Slettede fil|FileDeleted|Brugeren sletter et dokument fra et websted.|
|Slettede fil fra papirkurv|FileDeletedFirstStageRecycleBin|Brugeren sletter en fil fra papirkurven på et websted.|
|Slettede fil fra papirkurven i anden fase|FileDeletedSecondStageRecycleBin|Brugeren sletter en fil fra papirkurven i andet trin på et websted.|
|Slettede fil, der er markeret som en post|Postsletning|Et dokument eller en mail, der er markeret som en post, blev slettet. Et element betragtes som en post, når der anvendes en opbevaringsmærkat, der markerer elementer som en post, på indhold.|
|Registreret uoverensstemmelse i dokumentfølsomhed|DokumentfølsomhedMismatchDetected|Brugeren uploader et dokument til et websted, der er beskyttet med en følsomhedsmærkat, og dokumentet har en følsomhedsmærkat med højere prioritet end den følsomhedsmærkat, der er anvendt på webstedet. Et dokument med navnet Fortroligt uploades f.eks. til et websted med navnet Generelt. <br/><br/> Denne hændelse udløses ikke, hvis dokumentet har en følsomhedsmærkat med lavere prioritet end den følsomhedsmærkat, der er anvendt på webstedet. Et dokument med navnet Generelt uploades f.eks. til et websted med navnet Fortroligt. Du kan få flere oplysninger om prioriteten af følsomhedsmærkaten under [Mærkatprioritet (order matters)](sensitivity-labels.md#label-priority-order-matters).|
|Registreret malware i filen|FileMalwareDetected|SharePoint antivirusprogram registrerer malware i en fil.|
|Udtjekning af slettede filer|FileCheckOutDiscarded|Brugeren sletter (eller fortryder) en fil, der er tjekket ud. Det betyder, at de ændringer, de har foretaget i filen, da den blev tjekket ud, kasseres og ikke gemmes i dokumentets version i dokumentbiblioteket.|
|Downloadet fil|FileDownloaded|Brugeren downloader et dokument fra et websted.|
|Ændret fil|Ændret fil|Bruger- eller systemkonto ændrer indholdet eller egenskaberne for et dokument på et websted. Systemet venter fem minutter, før der logføres en anden FileModified-hændelse, når den samme bruger ændrer indholdet eller egenskaberne for det samme dokument.|
|(ingen)|FileModifiedExtended|Dette er relateret til aktiviteten "Ændret fil" (FileModified). En FileModifiedExtended-hændelse logføres, når den samme person hele tiden ændrer en fil i en længere periode (op til 3 timer). <br/><br/> Formålet med logføring af FileModifiedExtended-hændelser er at reducere antallet af FileModified-hændelser, der logføres, når en fil ændres løbende. Dette hjælper med at reducere støjen fra flere FileModified-poster for det, der i bund og grund er den samme brugeraktivitet, og giver dig mulighed for at fokusere på den indledende (og vigtigere) FileModified-hændelse.|
|Flyttet fil|FileMoved|Brugeren flytter et dokument fra den aktuelle placering på et websted til en ny placering.|
|(ingen)|Filen er forældet|Brugeren gennemser filer på et SharePoint eller OneDrive for Business websted. Disse hændelser forekommer typisk i store mængder baseret på en enkelt aktivitet, f.eks. visning af et billedgalleri.|
|Udført søgeforespørgsel|SearchQueryPerformed|Bruger- eller systemkonto udfører en søgning i SharePoint eller OneDrive for Business. Nogle almindelige scenarier, hvor en tjenestekonto udfører en søgeforespørgsel, omfatter anvendelse af eDiscovery-ventepositioner og opbevaringspolitik på websteder og OneDrive konti og automatisk anvendelse af opbevarings- eller følsomhedsmærkater på webstedsindhold.|
|Genbrug en fil | FileRecycled | Brugeren flytter en fil til papirkurv SharePoint. |
|Genbrug en mappe | Mapperecycled | Brugeren flytter en mappe til papirkurv SharePoint. |
|Genbrug alle mindre versioner af filen|FileVersionsAllMinorsRecycled|Brugeren sletter alle underordnede versioner fra versionshistorikken for en fil. De slettede versioner flyttes til webstedets papirkurv.|
|Genanvendt alle versioner af filen|FileVersionsAllRecycled|Brugeren sletter alle versioner fra versionshistorikken for en fil. De slettede versioner flyttes til webstedets papirkurv.|
|Genanvendt version af fil|FileVersionRecycled|Brugeren sletter en version fra versionshistorikken for en fil. Den slettede version flyttes til webstedets papirkurv.|
|Omdøbt fil|Filnavnet er navngivet|Brugeren omdøber et dokument på et websted.|
|Gendannet fil|Filerrestored|Brugeren gendanner et dokument fra papirkurven på et websted.|
|Overført fil|Filen er indlæst|Brugeren overfører et dokument til en mappe på et websted.|
|Vist side|Sidevisning|Brugeren får en side på et websted. Dette omfatter ikke brug af en webbrowser til at få vist filer, der er placeret i et dokumentbibliotek. Når en bruger får vist en side, logføres hændelsen PageViewed ikke igen for den samme bruger for samme side i de næste fem minutter.|
|(ingen)|PageViewedExtended|Dette er relateret til aktiviteten "Set side" (PageViewed). En PageViewedExtended-hændelse logføres, når den samme person hele tiden får vist en webside i en længere periode (op til 3 timer). <br/><br/> Formålet med logføring af PageViewedExtended-hændelser er at reducere antallet af PageViewed-hændelser, der logføres, når en side hele tiden vises. Dette hjælper med at reducere støjen fra flere PageViewed-poster for det, der i bund og grund er den samme brugeraktivitet, og giver dig mulighed for at fokusere på den indledende (og vigtigere) PageViewed-hændelse.|
|Visning, der signaleres af klienten|ClientViewSignaled|En brugers klient (f.eks. websted eller mobilapp) har signaleret, at den angivne side er blevet set af brugeren. Denne aktivitet logføres ofte efter en hændelse, der er forudrådet for en side. <br/><br/>**BEMÆRK**! Da clientViewSignaled-hændelser signaleres af klienten i stedet for serveren, er det muligt, at hændelsen ikke logføres af serveren og derfor ikke vises i overvågningsloggen. Det er også muligt, at du ikke har tillid til oplysningerne i overvågningsposten. Men da brugerens identitet valideres af det token, der bruges til at oprette signalet, er brugerens identitet angivet i den tilsvarende overvågningspost korrekt. Systemet venter fem minutter, før det logfører den samme hændelse, når den samme brugers klient signalerer, at siden er blevet vist igen af brugeren.|
|(ingen)|Side forside er forældet|En brugers klient (f.eks. websted eller mobilapp) har anmodet om den angivne side for at hjælpe med at forbedre ydeevnen, hvis brugeren går til den. Denne hændelse logføres for at angive, at sideindholdet er blevet leveret til brugerens klient. Denne hændelse er ikke en endelig indikation af, at brugeren har navigeret til siden. <br/><br/> Når sideindholdet gengives af klienten (i henhold til brugerens anmodning), skal der oprettes en ClientViewSignaled-hændelse. Det er ikke alle klienter, der understøtter angivelse af en forudhentning, og derfor logføres nogle af de aktiviteter, der allerede er hentet, i stedet som PageViewed-hændelser.|
||||

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>Ofte stillede spørgsmål om FileAccessed- og FilePreviewed-hændelser

**Kan andre aktiviteter udløse overvågningsposter, der ikke er fra brugeren, og som indeholder en brugeragent, f.eks. "OneDriveMpc-Transform_Thumbnail"?**

Vi er ikke opmærksomme på scenarier, hvor ikke-brugerhandlinger genererer hændelser som disse. Brugerhandlinger som f.eks. at åbne et brugerprofilkort (ved at klikke på deres navn eller mailadresse i en meddelelse i Outlook på internettet) ville generere lignende hændelser.

**Udløses kald til OneDriveMpc-Transform_Thumbnail altid bevidst af brugeren?**

Nej. Men lignende hændelser kan logføres som et resultat af forudhentning af browseren.

**Hvis vi ser en FilePreviewed-hændelse, der kommer fra en Microsoft-registreret IP-adresse, betyder det så, at prøveversionen blev vist på skærmen på brugerens enhed?**

Nej. Hændelsen kan være logført som et resultat af forudhentning af browseren.

**Er der scenarier, hvor en bruger, der får forhåndsvist et dokument, genererer FileAccessed-hændelser?**

Både hændelserne FilePreviewed og FileAccessed angiver, at en brugers opkald førte til en læsning af filen (eller en læsning af en miniaturegengivelse af filen). Selvom disse hændelser er beregnet til at være i overensstemmelse med hensigten med prøveversionen i forhold til adgangsformål, er forskellen mellem begivenheder ikke en garanti for brugerens hensigt.

#### <a name="the-appsharepoint-user-in-audit-records"></a>Appsharepoint-brugeren\@ i overvågningsposter

I overvågningsposter for nogle filaktiviteter (og andre SharePoint-relaterede aktiviteter) kan du bemærke, at den bruger, der udførte aktiviteten (identificeret i felterne Bruger og UserId), er app@sharepoint. Dette angiver, at den "bruger", der udførte aktiviteten, var et program. I dette tilfælde blev programmet tildelt tilladelser i SharePoint til at udføre handlinger for hele organisationen (f.eks. søge på et SharePoint websted eller en OneDrive konto) på vegne af en bruger, administrator eller tjeneste. Denne proces med at give tilladelser til et program kaldes *SharePoint kun programadgang*. Dette angiver, at den godkendelse, der blev præsenteret for SharePoint til at udføre en handling, blev foretaget af et program i stedet for en bruger. Det er derfor, at den app@sharepoint bruger identificeres i visse overvågningsposter. Du kan få flere oplysninger under [Tildel adgang ved hjælp af SharePoint kun program](/sharepoint/dev/solution-guidance/security-apponly-azureacs).

App@sharepoint identificeres f.eks. ofte som brugeren for hændelserne "Udført søgeforespørgsel" og "Tilgået fil". Det skyldes, at et program med SharePoint App-Only adgang i din organisation udfører søgeforespørgsler og får adgang til filer, når der anvendes opbevaringspolitikker på websteder og OneDrive konti.

Her er nogle andre scenarier, hvor app@sharepoint kan identificeres i en overvågningspost som den bruger, der udførte en aktivitet:

- Microsoft 365-grupper. Når en bruger eller administrator opretter en ny gruppe, oprettes der overvågningsposter for at oprette en gruppe af websteder, opdatere lister og føje medlemmer til en SharePoint gruppe. Disse opgaver udføres et program på vegne af den bruger, der oprettede gruppen.

- Microsoft Teams. På samme måde som med Microsoft 365-grupper genereres overvågningsposter til oprettelse af en gruppe af websteder, opdatering af lister og tilføjelse af medlemmer til en SharePoint gruppe, når der oprettes et team.

- Funktioner til overholdelse af angivne standarder. Når en administrator implementerer funktioner til overholdelse af angivne standarder, f.eks. opbevaringspolitikker, eDiscovery-bevarelse og automatisk anvendelse af følsomhedsmærkater.

I disse og andre scenarier vil du også bemærke, at flere overvågningsposter med app@sharepoint, da den angivne bruger blev oprettet inden for en kort tidsramme, ofte inden for nogle få sekunder fra hinanden. Dette angiver også, at de sandsynligvis blev udløst af den samme brugerinitierede opgave. Felterne ApplicationDisplayName og EventData i overvågningsposten kan også hjælpe dig med at identificere det scenarie eller program, der udløste hændelsen.

### <a name="folder-activities"></a>Mappeaktiviteter

I følgende tabel beskrives mappeaktiviteterne i SharePoint Online og OneDrive for Business. Som tidligere forklaret angiver overvågningsposter for nogle SharePoint aktiviteter, at den app@sharepoint bruger udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan finde flere oplysninger under [AppSharePoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Kopieret mappe|FolderCopied|Brugeren kopierer en mappe fra et websted til en anden placering i SharePoint eller OneDrive for Business.|
|Oprettet mappe|Mappeoprettet|Brugeren opretter en mappe på et websted.|
|Mappen Slettet|Mappedeleted|Brugeren sletter en mappe fra et websted.|
|Slettede mappe fra papirkurv|FolderDeletedFirstStageRecycleBin|Brugeren sletter en mappe fra papirkurven på et websted.|
|Mappen er slettet fra papirkurven i anden fase|FolderDeletedSecondStageRecycleBin|Brugeren sletter en mappe fra papirkurven i anden fase på et websted.|
|Mappen Ændret|Ændret mappe|Brugeren ændrer en mappe på et websted. Dette omfatter ændring af mappemetadata, f.eks. ændring af mærker og egenskaber.|
|Flyttet mappe|MappeFlytning|Brugeren flytter en mappe til en anden placering på et websted.|
|Omdøbt mappe|MappeNavngivet|Brugeren omdøber en mappe på et websted.|
|Gendannet mappe|Mapperestored|Brugeren gendanner en slettet mappe fra papirkurven på et websted.|
||||

### <a name="sharepoint-list-activities"></a>SharePoint listeaktiviteter

I følgende tabel beskrives aktiviteter, der er relateret til, når brugerne interagerer med lister og listeelementer i SharePoint Online. Som tidligere forklaret angiver overvågningsposter for nogle SharePoint aktiviteter, at den app@sharepoint bruger udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan finde flere oplysninger under [AppSharePoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Oprettet liste|Listeoprettet|En bruger har oprettet en SharePoint liste.|
|Oprettet listekolonne|ListColumnCreated|En bruger oprettede en SharePoint listekolonne. En listekolonne er en kolonne, der er knyttet til en eller flere SharePoint lister.|
|Oprettet listeindholdstype|ListContentTypeCreated|En bruger har oprettet en listeindholdstype. En listeindholdstype er en indholdstype, der er knyttet til en eller flere SharePoint lister.|
|Oprettet listeelement|ListItemCreated|En bruger har oprettet et element på en eksisterende SharePoint liste.|
|Oprettet webstedskolonne|Webstedskolonneoprettet|En bruger har oprettet en SharePoint webstedskolonne. En webstedskolonne er en kolonne, der ikke er knyttet til en liste. En webstedskolonne er også en metadatastruktur, der kan bruges af en hvilken som helst liste på et bestemt websted.|
|Indholdstype for oprettet websted|Webstedsindholdstype er oprettet|En bruger har oprettet en webstedsindholdstype. En webstedsindholdstype er en indholdstype, der er knyttet til det overordnede websted.|
|Slettet liste|Listedeleted|En bruger slettede en SharePoint liste.|
|Slettede listekolonne|Listekolonne slettet|En bruger slettede en SharePoint listekolonne.|
|Slettet listeindholdstype|ListContentTypeDeleted|En bruger slettede en listeindholdstype.|
|Slettet listeelement|Listeelement slettet|En bruger slettede et SharePoint listeelement.|
|Slettede webstedskolonne|Webstedskolonnedeleted|En bruger slettede en SharePoint webstedskolonne.|
|Indholdstype for slettet websted|SiteContentTypeDeleted|En bruger slettede en webstedsindholdstype.|
|Genanvendt listeelement|ListItemRecycled|En bruger har flyttet et SharePoint listeelement til Papirkurven.|
|Gendannet liste|ListRestored|En bruger har gendannet en SharePoint liste fra Papirkurven.|
|Gendannet listeelement|ListItemRestored|En bruger gendannede et SharePoint listeelement fra Papirkurven.|
|Opdateret liste|ListUpdated|En bruger har opdateret en SharePoint liste ved at ændre en eller flere egenskaber.|
|Opdateret listekolonne|ListColumnUpdated|En bruger har opdateret en SharePoint listekolonne ved at ændre en eller flere egenskaber.|
|Opdateret listeindholdstype|ListContentTypeUpdated|En bruger har opdateret en listeindholdstype ved at ændre en eller flere egenskaber.|
|Opdateret listeelement|ListItemUpdated|En bruger har opdateret et SharePoint listeelement ved at ændre en eller flere egenskaber.|
|Opdateret webstedskolonne|SiteColumnUpdated|En bruger har opdateret en SharePoint webstedskolonne ved at ændre en eller flere egenskaber.|
|Opdateret webstedsindholdstype|SiteContentTypeUpdated|En bruger har opdateret en webstedsindholdstype ved at ændre en eller flere egenskaber.|
|Vist listeelement|ListItemViewed|En bruger fik vist et SharePoint listeelement. Når en bruger får vist et listeelement, logføres hændelsen ListItemViewed ikke igen for den samme bruger for samme listeelement i de næste fem minutter.|
||||

### <a name="sharing-and-access-request-activities"></a>Delings- og adgangsanmodningsaktiviteter

I følgende tabel beskrives aktiviteter for brugerdelings- og adgangsanmodninger i SharePoint Online og OneDrive for Business. I forbindelse med deling af hændelser identificerer kolonnen **Detaljer** under **Resultater** navnet på den bruger eller gruppe, elementet blev delt med, og om den pågældende bruger eller gruppe er medlem eller gæst i din organisation. Du kan få flere oplysninger under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).

> [!NOTE]
> Brugere kan være enten  *medlemmer*  eller  *gæster*  baseret på egenskaben UserType for brugerobjektet. Et medlem er normalt en medarbejder, og en gæst er normalt en samarbejdspartner uden for din organisation. Når en bruger accepterer en invitation til deling (og ikke allerede er en del af din organisation), oprettes der en gæstekonto til vedkommende i organisationens mappe. Når gæstebrugeren har en konto i din mappe, kan ressourcer deles direkte med dem (uden at der kræves en invitation).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilladelsesniveauet er føjet til gruppen af websteder|PermissionLevelAdded|Der blev føjet et tilladelsesniveau til en gruppe af websteder.|
|Accepteret anmodning om adgang|AccessRequestAccepted|En anmodning om adgang til et websted, en mappe eller et dokument blev accepteret, og den anmodende bruger har fået tildelt adgang.|
|Invitation til accepteret deling|SharingInvitationAccepted|Brugeren (medlem eller gæst) accepterede en invitation til deling og fik adgang til en ressource. Denne hændelse indeholder oplysninger om den bruger, der blev inviteret, og den mailadresse, der blev brugt til at acceptere invitationen (de kan være forskellige). Denne aktivitet ledsages ofte af en anden hændelse, der beskriver, hvordan brugeren blev tildelt adgang til ressourcen, f.eks. tilføjelse af brugeren til en gruppe, der har adgang til ressourcen.|
|Invitation til blokeret deling|SharingInvitationBlocked|En invitation til deling, der sendes af en bruger i din organisation, er blokeret på grund af en ekstern delingspolitik, der enten tillader eller afviser ekstern deling baseret på destinationsbrugerens domæne. I dette tilfælde blev invitationen til deling blokeret, fordi: <br/> Destinationsbrugerens domæne er ikke inkluderet på listen over tilladte domæner. <br/> Eller <br/> Destinationsbrugerens domæne er inkluderet på listen over blokerede domæner. <br/> Du kan få flere oplysninger om, hvordan du tillader eller blokerer ekstern deling baseret på domæner, [under Begrænset deling af domæner i SharePoint Online og OneDrive for Business](/sharepoint/restricted-domains-sharing).|
|Oprettede anmodning om adgang|AccessRequestCreated|Brugeren anmoder om adgang til et websted, en mappe eller et dokument, som brugeren ikke har tilladelse til at få adgang til.|
|Oprettede et link, der kan deles af virksomheden|Firmalinkoprettet|Brugeren har oprettet et link til en ressource i hele virksomheden. Links til hele virksomheden kan kun bruges af medlemmer i organisationen. De kan ikke bruges af gæster.|
|Oprettede et anonymt link|Anonymt link blevoprettet|Brugeren har oprettet et anonymt link til en ressource. Alle med dette link kan få adgang til ressourcen uden at skulle godkendes.|
|Oprettet sikkert link|SecureLinkCreated|Der blev oprettet et sikkert delingslink til dette element.|
|Invitation til deling er oprettet|SharingInvitationCreated|Brugeren delte en ressource i SharePoint Online eller OneDrive for Business med en bruger, der ikke er i organisationens mappe.|
|Slettede et sikkert link|SecureLinkDeleted|Et link til sikker deling blev slettet.|
|Anmodning om nægtet adgang|AccessRequestDenied|En anmodning om adgang til et websted, en mappe eller et dokument blev nægtet.|
|Fjernede et link, der kan deles af virksomheden|CompanyLinkRemoved|Brugeren fjernede et link for hele virksomheden til en ressource. Linket kan ikke længere bruges til at få adgang til ressourcen.|
|Fjernede et anonymt link|AnonymousLinkRemoved|Brugeren fjernede et anonymt link til en ressource. Linket kan ikke længere bruges til at få adgang til ressourcen.|
|Delt fil, mappe eller websted|Delingssæt|Brugeren (medlem eller gæst) delte en fil, en mappe eller et websted i SharePoint eller OneDrive for Business med en bruger i organisationens mappe. Værdien i kolonnen **Detaljer** for denne aktivitet identificerer navnet på den bruger, som ressourcen blev delt med, og om brugeren er medlem eller gæst. <br/><br/> Denne aktivitet ledsages ofte af en anden hændelse, der beskriver, hvordan brugeren blev tildelt adgang til ressourcen. Det kan f.eks. være at føje brugeren til en gruppe, der har adgang til ressourcen.|
|Opdateret anmodning om adgang|AccessRequestUpdated|En anmodning om adgang til et element blev opdateret.|
|Opdaterede et anonymt link|AnonymousLinkUpdated|Brugeren har opdateret et anonymt link til en ressource. Det opdaterede felt er inkluderet i egenskaben EventData, når du eksporterer søgeresultaterne.|
|Opdateret invitation til deling|SharingInvitationUpdated|En invitation til ekstern deling blev opdateret.|
|Brugte et anonymt link|AnonymousLinkUsed|En anonym bruger har åbnet en ressource ved hjælp af et anonymt link. Brugerens identitet kan være ukendt, men du kan få andre oplysninger, f.eks. brugerens IP-adresse.|
|Ikke-delt fil, mappe eller websted|Deling er tilbagekaldt|Brugeren (medlem eller gæst) har ikke delt en fil, en mappe eller et websted, der tidligere er delt med en anden bruger.|
|Brugte et link, der kan deles af virksomheden|CompanyLinkUsed|Brugeren har åbnet en ressource ved hjælp af et firmalink.|
|Brugt sikkert link|SecureLinkUsed|En bruger brugte et sikkert link.|
|Brugeren er føjet til et sikkert link|AddedToSecureLink|En bruger blev føjet til listen over enheder, der kan bruge et sikkert delingslink.|
|Brugeren er fjernet fra et sikkert link|RemovedFromSecureLink|En bruger blev fjernet fra listen over enheder, der kan bruge et sikkert delingslink.|
|Tilbagekald invitation til deling|SharingInvitationRevoked|Brugeren trak en invitation til deling tilbage til en ressource.|
||||

### <a name="synchronization-activities"></a>Synkroniseringsaktiviteter

I følgende tabel vises en liste over aktiviteter til synkronisering af filer i SharePoint Online og OneDrive for Business.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tillader, at computeren synkroniserer filer|ManagedSyncClientAllowed|Brugeren etablerer en synkroniseringsrelation med et websted. Synkroniseringsrelationen lykkedes, fordi brugerens computer er medlem af et domæne, der er føjet til listen over domæner (kaldet *listen over sikre modtagere*), som kan få adgang til dokumentbiblioteker i din organisation. <br/><br/> Du kan få flere oplysninger om denne funktion under [Brug Windows PowerShell-cmdlet'er til at aktivere OneDrive-synkronisering for domæner, der er på listen over sikre modtagere](/powershell/module/sharepoint-online/).|
|Blokeret computer fra synkronisering af filer|Ikke-administreretSyncClientBlocked|Brugeren forsøger at etablere en synkroniseringsrelation med et websted fra en computer, der ikke er medlem af organisationens domæne, eller som er medlem af et domæne, der ikke er føjet til listen over domæner (kaldet  *listen over modtagere*  , der er tillid til), som kan få adgang til dokumentbiblioteker i din organisation. Synkroniseringsrelationen er ikke tilladt, og brugerens computer er blokeret fra at synkronisere, downloade eller overføre filer i et dokumentbibliotek. <br/><br/> Du kan få oplysninger om denne funktion under [Brug Windows PowerShell-cmdlet'er til at aktivere OneDrive-synkronisering for domæner, der er på listen over sikre modtagere](/powershell/module/sharepoint-online/).|
|Downloadede filer til computer|FileSyncDownloadedFull|Brugeren downloader en fil til sin computer fra et SharePoint dokumentbibliotek eller OneDrive for Business ved hjælp af OneDrive-synkronisering app (OneDrive.exe).|
|Downloadede filændringer på computeren|FileSyncDownloadedPartial|Denne hændelse frarådes sammen med den gamle OneDrive for Business synkroniseringsapp (Groove.exe).|
|Overførte filer til dokumentbiblioteket|FileSyncUploadedFull|Brugeren uploader en ny fil eller ændringer til en fil i SharePoint dokumentbibliotek eller OneDrive for Business ved hjælp af OneDrive-synkronisering app (OneDrive.exe).|
|Overførte filændringer til dokumentbiblioteket|FileSyncUploadedPartial|Denne hændelse frarådes sammen med den gamle OneDrive for Business synkroniseringsapp (Groove.exe).|
||||

### <a name="site-permissions-activities"></a>Aktiviteter for webstedstilladelser

I følgende tabel vises hændelser, der er relateret til tildeling af tilladelser i SharePoint og brug af grupper til at give (og tilbagekalde) adgang til websteder. Som tidligere forklaret angiver overvågningsposter for nogle SharePoint aktiviteter, at den app@sharepoint bruger udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan finde flere oplysninger under [AppSharePoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet administrator af gruppe af websteder|WebstedsamlingAdminTilføj|Administratoren eller ejeren af gruppen af websteder tilføjer en person som administrator af en gruppe af websteder for et websted. Administratorer af gruppen af websteder har fuld kontrol over tilladelser til gruppen af websteder og alle underordnede websteder. Denne aktivitet logføres også, når en administrator giver sig selv adgang til en brugers OneDrive-konto (ved at redigere brugerprofilen i SharePoint Administration eller ved [hjælp af Microsoft 365 Administration](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)).|
|Føjede bruger eller gruppe til SharePoint gruppe|AddedToGroup|Brugeren føjede et medlem eller en gæst til en SharePoint gruppe. Dette kan have været en bevidst handling eller resultatet af en anden aktivitet, f.eks. en delingshændelse.|
|Afbrød nedarvning af tilladelsesniveau|PermissionLevelsInheritanceBroken|Et element blev ændret, så det ikke længere nedarver tilladelsesniveauer fra det overordnede element.|
|Deling af nedarvning blev ikke brudt|SharingInheritanceBroken|Et element blev ændret, så det ikke længere nedarver delingstilladelser fra det overordnede element.|
|Oprettet gruppe|Gruppetilføjet|Webstedsadministratoren eller -ejeren opretter en gruppe for et websted eller udfører en opgave, der medfører, at der oprettes en gruppe. Første gang en bruger f.eks. opretter et link til deling af en fil, føjes der en systemgruppe til brugerens OneDrive for Business websted. Denne hændelse kan også være et resultat af, at en bruger opretter et link med redigeringstilladelser til en delt fil.|
|Slettet gruppe|Gruppérflytning|Brugeren sletter en gruppe fra et websted.|
|Ændrede indstilling for adgangsanmodning|WebRequestAccessModified|Indstillingerne for anmodning om adgang blev ændret på et websted.|
|Ændrede indstillingen 'Medlemmer kan dele'|WebMembersCanShareModified|Indstillingen **Medlemmer kan dele** blev ændret på et websted.|
|Ændret tilladelsesniveau for en gruppe af websteder|PermissionLevelModified|Et tilladelsesniveau blev ændret i en gruppe af websteder.|
|Ændrede webstedstilladelser|Ændring af webstedstilladelser|Webstedsadministratoren eller ejeren (eller systemkontoen) ændrer det tilladelsesniveau, der er tildelt til en gruppe på et websted. Denne aktivitet logføres også, hvis alle tilladelser fjernes fra en gruppe. <br/><br/> **BEMÆRK**! Denne handling frarådes i SharePoint Online. Hvis du vil finde relaterede hændelser, kan du søge efter andre tilladelsesrelaterede aktiviteter, f.eks **. Tilføjet administrator af gruppe af websteder**, **Føjet bruger eller gruppe til SharePoint gruppe**, **Tilladt bruger til at oprette grupper**, **Oprettet gruppe** og **Slettet gruppe.**|
|Tilladelsesniveauet er fjernet fra gruppen af websteder|PermissionLevelRemoved|Et tilladelsesniveau blev fjernet fra en gruppe af websteder.|
|Fjernede administratoren for gruppen af websteder|WebstedsamlingAdminRemoved|Administratoren eller ejeren af gruppen af websteder fjerner en person som administrator af en gruppe af websteder for et websted. Denne aktivitet logføres også, når en administrator fjerner sig selv fra listen over administratorer af grupper af websteder for en brugers OneDrive konto (ved at redigere brugerprofilen i SharePoint Administration).  Hvis du vil returnere denne aktivitet i søgeresultaterne i overvågningsloggen, skal du søge efter alle aktiviteter.|
|Brugeren eller gruppen er fjernet fra SharePoint gruppe|RemovedFromGroup|Brugeren fjernede et medlem eller en gæst fra en SharePoint gruppe. Dette kan have været en bevidst handling eller resultatet af en anden aktivitet, f.eks. en uforlignelig hændelse.|
|Anmodede tilladelser som webstedsadministrator|Anmodning om ændring af webstedsændring|Brugeranmodninger om at blive tilføjet som administrator af en gruppe af websteder for en gruppe af websteder. Administratorer af gruppen af websteder har fuld kontrol over tilladelser til gruppen af websteder og alle underordnede websteder.|
|Gendannet nedarvning af deling|DelinginheritanceReset|Der blev foretaget en ændring, så et element nedarver delingstilladelser fra det overordnede element.|
|Opdateret gruppe|GroupUpdated|Webstedsadministratoren eller -ejeren ændrer indstillingerne for en gruppe for et websted. Dette kan omfatte ændring af gruppens navn, hvem der kan få vist eller redigere gruppemedlemskabet, og hvordan anmodninger om medlemskab håndteres.|
||||

### <a name="site-administration-activities"></a>Webstedsadministrationsaktiviteter

I følgende tabel vises hændelser, der stammer fra administrationsopgaver for websteder i SharePoint Online. Som tidligere forklaret angiver overvågningsposter for nogle SharePoint aktiviteter, at den app@sharepoint bruger udførte aktiviteten på vegne af den bruger eller administrator, der startede handlingen. Du kan finde flere oplysninger under [AppSharePoint-brugeren\@ i overvågningsposter](#the-appsharepoint-user-in-audit-records).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet tilladt dataplacering|AllowedDataLocationAdded|En SharePoint eller global administrator har tilføjet en tilladt dataplacering i et multi-geo-miljø.|
|Tilføjet brugeragent, der er undtaget|ExemptUserAgentSet|En SharePoint eller global administrator føjede en brugeragent til listen over brugeragenter, der er undtaget, i SharePoint Administration.|
|Tilføjet administrator af geografisk placering|GeoAdminAdded|En SharePoint eller global administrator tilføjede en bruger som geoadministrator af en placering.|
|Tilladt bruger at oprette grupper|AllowGroupCreationSet|Webstedsadministratoren eller -ejeren føjer et tilladelsesniveau til et websted, der giver en bruger, der har tildelt denne tilladelse, tilladelse til at oprette en gruppe for det pågældende websted.|
|Annulleret geografisk flytning af websted|SiteGeoMoveCancelled|En SharePoint eller global administrator annullerer en geografisk flytning af et SharePoint eller OneDrive websted. Multi-Geo-funktionen gør det muligt for en organisation at spænde over flere geografiske områder i Microsoft-datacentre, som kaldes geos. Du kan få flere oplysninger [under Multi-Geo-funktioner i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Ændrede en delingspolitik|SharingPolicyChanged|En SharePoint eller global administrator ændrede en politik for deling af SharePoint ved hjælp af Microsoft 365 Administration, SharePoint Administration eller SharePoint Shell til onlineadministration. Alle ændringer af indstillingerne i delingspolitikken i din organisation logføres. Den politik, der blev ændret, identificeres i feltet **ModifiedProperties** i de detaljerede egenskaber for hændelsesposten.|
|Ændrede politik for enhedsadgang|DeviceAccessPolicyChanged|En SharePoint eller global administrator ændrede politikken for ikke-administrerede enheder for din organisation. Denne politik styrer adgangen til SharePoint, OneDrive og Microsoft 365 fra enheder, der ikke er tilmeldt din organisation. Konfiguration af denne politik kræver et Enterprise Mobility + Security abonnement. Få mere at vide under [Kontrollér adgang fra ikke-administrerede enheder](/sharepoint/control-access-from-unmanaged-devices).|
|Ændrede brugeragenter, der er undtaget|TilpasExemptUsers|En SharePoint eller global administrator har tilpasset listen over brugeragenter, der er undtaget, i SharePoint Administration. Du kan angive, hvilke brugeragenter der skal fritages fra at modtage en hel webside til indeksering. Det betyder, at når en brugeragent, du har angivet som undtaget, støder på en InfoPath-formular, returneres formularen som en XML-fil i stedet for en hel webside. Det gør indeksering af InfoPath-formularer hurtigere.|
|Ændret politik for netværksadgang|NetworkAccessPolicyChanged|En SharePoint eller global administrator ændrede den placeringsbaserede adgangspolitik (også kaldet en netværksgrænse, der er tillid til) i SharePoint Administration eller ved hjælp af SharePoint Online PowerShell. Denne type politik styrer, hvem der kan få adgang til SharePoint og OneDrive ressourcer i din organisation baseret på godkendte IP-adresseintervaller, som du angiver. Du kan få flere oplysninger under [Kontrollér adgang til SharePoint Online og OneDrive data, der er baseret på netværksplacering](/sharepoint/control-access-based-on-network-location).|
|Fuldført geografisk flytning af websted|SiteGeoMoveCompleted|Et geografisk webstedsflytning, der er planlagt af en global administrator i din organisation, blev fuldført. Multi-Geo-funktionen gør det muligt for en organisation at spænde over flere geografiske områder i Microsoft-datacentre, som kaldes geos. Du kan få flere oplysninger [under Multi-Geo-funktioner i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Oprettet sendt til forbindelse|SendToConnectionTilføj|En SharePoint eller global administrator opretter en ny Send til-forbindelse på siden Datastyring i SharePoint Administration. En Send til-forbindelse angiver indstillinger for et dokumentlager eller et datacenter. Når du opretter en Send til-forbindelse, kan en liste over indhold sende dokumenter til den angivne placering.|
|Oprettet gruppe af websteder|SiteCollectionCreated|En SharePoint eller global administrator opretter en gruppe af websteder i din SharePoint Online-organisation, eller en bruger klargør sit OneDrive for Business websted.|
|Slettede tabte hubwebsteder|HubSiteOrphanHubDeleted|En SharePoint eller global administrator slettede et mistet hubwebsted, som er et hubwebsted, der ikke har nogen tilknyttede websteder. En mistet hub er sandsynligvis forårsaget af sletningen af det oprindelige hubwebsted.|
|Slettet sendt til forbindelse|SendToConnectionRemoved|En SharePoint eller global administrator sletter en Send til-forbindelse på siden Datastyring i SharePoint Administration.|
|Slettet websted|Webstedsdeleted|Webstedsadministratoren sletter et websted.|
|Aktiveret dokumentvisning|PreviewModeEnabledSet|Webstedsadministratoren aktiverer dokumentvisning for et websted.|
|Aktiveret ældre arbejdsproces|ÆldrearbejdsflowEnabledSet|Webstedsadministratoren eller -ejeren føjer indholdstypen SharePoint 2013 Arbejdsprocesopgave til webstedet. Globale administratorer kan også aktivere arbejdsflow for hele organisationen i SharePoint Administration.|
|Aktiveret Office efter behov|OfficeOnDemandSet|Webstedsadministratoren aktiverer Office efter behov, hvilket giver brugerne adgang til den nyeste version af Office skrivebordsprogrammer. Office on Demand er aktiveret i SharePoint Administration og kræver et Microsoft 365 abonnement, der omfatter fulde, installerede Office programmer.|
|Aktiveret resultatkilde for personsøgninger|PeopleResultsScopeSet|Webstedsadministratoren opretter resultatkilden for personsøgninger på et websted.|
|Aktiverede RSS-kilder|NyhedsstrømEnabledSet|Webstedsadministrator eller -ejer aktiverer RSS-feeds for et websted. Globale administratorer kan aktivere RSS-feeds for hele organisationen i SharePoint Administration.|
|Joinforbundet websted til hubwebsted|HubSiteJoined|En webstedsejer knytter deres websted til et hubwebsted.|
|Kvote for ændret gruppe af websteder|Webstedssamling -quotamodified|Webstedsadministratoren ændrer kvoten for en gruppe af websteder.|
|Registreret hubwebsted|HubSiteRegistered|En SharePoint eller global administrator opretter et hubwebsted. Resultaterne er, at webstedet er registreret til at være et hubwebsted.|
|Fjernede tilladt dataplacering|AllowedDataLocationDeleted|En SharePoint eller global administrator fjernede en tilladt dataplacering i et multi-geo-miljø.|
|Fjernede administratoren for geografisk placering|GeoAdminDeleted|En SharePoint eller global administrator fjernede en bruger som geoadministrator af en placering.|
|Omdøbt websted|Navn på websted|Webstedsadministratoren eller -ejeren omdøber et websted|
|Planlagt geografisk flytning af websted|SiteGeoMoveScheduled|En SharePoint eller global administrator planlægger en SharePoint eller OneDrive websteds geoflytning. Multi-Geo-funktionen gør det muligt for en organisation at spænde over flere geografiske områder i Microsoft-datacentre, som kaldes geos. Du kan få flere oplysninger [under Multi-Geo-funktioner i OneDrive og SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Angiv værtswebsted|Værtswebstedssæt|En SharePoint eller global administrator ændrer det angivne websted, så det er vært for personlige eller OneDrive for Business websteder.|
|Angiv lagerkvote for geografisk placering|GeoQuotaAllocated|En SharePoint eller global administrator konfigurerede lagerkvoten for en geografisk placering i et multi-geo-miljø.|
|Ikke-sluttet websted fra hubwebsted|HubSite Er ikke sluttet til|En webstedsejer fjerner tilknytningen fra sit websted fra et hubwebsted.|
|Ikke-registreret hubwebsted|HubSiteDet er ikke registreret|En SharePoint eller global administrator fjerner registreringen af et websted som et hubwebsted. Når et hubwebsted ikke er registreret, fungerer det ikke længere som et hubwebsted.|
||||

### <a name="exchange-mailbox-activities"></a>Exchange postkasseaktiviteter

I følgende tabel vises de aktiviteter, der kan logføres af logføring af overvågning af postkasser. Postkasseaktiviteter, der udføres af ejeren af postkassen, en delegeret bruger eller en administrator, logføres automatisk i overvågningsloggen i op til 90 dage. Det er muligt for en administrator at deaktivere logføring af overvågning af postkasser for alle brugere i organisationen. I dette tilfælde logføres ingen postkassehandlinger for nogen bruger. Du kan få flere oplysninger under [Administrer overvågning af postkasser](enable-mailbox-auditing.md).

 Du kan også søge efter postkasseaktiviteter ved hjælp af cmdlet'en [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Elementer i en postkasse, der er åbnet|MailItemsAccessed|Meddelelser blev læst eller åbnet i postkassen. Overvågningsposter for denne aktivitet udløses på en af to måder: Når en mailklient (f.eks. Outlook) udfører en bindingshandling på meddelelser, eller når mailprotokoller (f.eks. Exchange ActiveSync eller IMAP) synkroniserer elementer i en mailmappe. Denne aktivitet logføres kun for brugere med en Office 365 eller Microsoft 365 E5 licens. Det er nyttigt at analysere overvågningsposter for denne aktivitet, når du undersøger kompromitteret mailkonto. Du kan få flere oplysninger i afsnittet "Overvågningshændelser (Premium) under [Overvågning (Premium)](advanced-audit.md#audit-premium-events). |
|Tilføjede tilladelser til stedfortræderpostkasse|Add-MailboxPermission|En administrator har tildelt tilladelsen til FullAccess-postkassen til en bruger (kaldet stedfortræder) til en anden persons postkasse. Tilladelsen FullAccess gør det muligt for stedfortræderen at åbne den anden persons postkasse og læse og administrere indholdet af postkassen. Overvågningsposten for denne aktivitet genereres også, når en systemkonto i Microsoft 365-tjenesten jævnligt udfører vedligeholdelsesopgaver på vegne af din organisation. En almindelig opgave, der udføres af en systemkonto, er at opdatere tilladelserne for systempostkasser. Du kan få flere oplysninger under [Systemkonti i Exchange postkassens overvågningsposter](#system-accounts-in-exchange-mailbox-audit-records).|
|Tilføjet eller fjernet bruger med stedfortræderadgang til kalendermappen|UpdateCalendarDelegation|En bruger blev tilføjet eller fjernet som stedfortræder for kalenderen i en anden brugers postkasse. Kalenderdelegering giver en anden i den samme organisation tilladelse til at administrere postkasseejerens kalender.|
|Føjede tilladelser til mappen|AddFolderPermissions|Der blev tilføjet en mappetilladelse. Mappetilladelser styrer, hvilke brugere i din organisation der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|
|Kopierede meddelelser til en anden mappe|Kopiere|En meddelelse blev kopieret til en anden mappe.|
|Oprettet postkasseelement|Opret|Der oprettes et element i mappen Kalender, Kontakter, Noter eller Opgaver i postkassen. Der oprettes f.eks. en ny mødeindkaldelse. Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke. Desuden overvåges oprettelse af en postkassemappe ikke.|
|Oprettede en ny indbakkeregel i Outlook webapp|New-InboxRule|En postkasseejer eller en anden bruger med adgang til postkassen oprettede en indbakkeregel i Outlook webapp.|
|Slettede meddelelser fra mappen Slettet post|Blød sletning|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Disse elementer flyttes til mappen Elementer, der kan gendannes. Meddelelser flyttes også til mappen Elementer, der kan gendannes, når en bruger vælger den og trykker på **Skift+Slet**.|
|Navngivet meddelelse som en post|AnvendPostLabel|En meddelelse blev klassificeret som en post. Dette sker, når en opbevaringsmærkat, der klassificerer indhold som en post, anvendes manuelt eller automatisk på en meddelelse.|
|Flyttede meddelelser til en anden mappe|Flytte|En meddelelse blev flyttet til en anden mappe.|
|Flyttede meddelelser til mappen Slettet post|FlyttilDeletedItems|En meddelelse blev slettet og flyttet til mappen Slettet post.|
|Tilladelse til ændret mappe|UpdateFolderPermissions|En mappetilladelse blev ændret. Mappetilladelser styrer, hvilke brugere i din organisation der kan få adgang til postkassemapper og meddelelserne i mappen.|
|Ændret indbakkeregel fra Outlook webapp|Set-InboxRule|En postkasseejer eller en anden bruger med adgang til postkassen ændrede en indbakkeregel ved hjælp af Outlook webappen.|
|Fjernede meddelelser fra postkassen|HardDelete|En meddelelse blev fjernet fra mappen Gendan elementer (slettet permanent fra postkassen).|
|Fjernede tilladelser til stedfortræderpostkasse|Remove-MailboxPermission|En administrator fjernede FullAccess-tilladelsen (som blev tildelt til en stedfortræder) fra en persons postkasse. Når FullAccess-tilladelsen er fjernet, kan stedfortræderen ikke åbne den anden persons postkasse eller få adgang til noget indhold i den.|
|Fjernede tilladelser fra mappen|RemoveFolderPermissions|En mappetilladelse blev fjernet. Mappetilladelser styrer, hvilke brugere i din organisation der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|
|Sendt meddelelse|Send|En meddelelse blev sendt, besvaret eller videresendt. Denne aktivitet logføres kun for brugere med en Office 365 eller Microsoft 365 E5 licens. Du kan få flere oplysninger i afsnittet "Overvågningshændelser (Premium) under [Overvågning (Premium)](advanced-audit.md#audit-premium-events).|
|Sendt meddelelse med tilladelserne Send som|Send som|Der blev sendt en meddelelse ved hjælp af tilladelsen SendAs. Det betyder, at en anden bruger har sendt meddelelsen, som om den kom fra ejeren af postkassen.|
|Sendt meddelelse med tilladelsen Send på vegne|SendOnBehalf|Der blev sendt en meddelelse ved hjælp af tilladelsen SendOnBehalf. Det betyder, at en anden bruger sendte meddelelsen på vegne af ejeren af postkassen. Meddelelsen angiver til den modtager, som meddelelsen blev sendt på vegne af, og hvem der rent faktisk sendte meddelelsen.|
|Opdaterede indbakkeregler fra Outlook klient|UpdateInboxRules|En postkasseejer eller en anden bruger med adgang til den postkasse, der er oprettet, ændret eller fjernet en indbakkeregel ved hjælp af Outlook-klienten.|
|Opdateret meddelelse|Opdater|En meddelelse eller dens egenskaber blev ændret.|
|Brugeren er logget på postkassen|MailboxLogin|Brugeren er logget på sin postkasse.|
|Mærk meddelelsen som en post||En bruger har anvendt en opbevaringsmærkat på en mail, og denne etiket er konfigureret til at markere elementet som en post. |
||||

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Systemkonti i Exchange postkassens overvågningsposter

I overvågningsposter for nogle postkasseaktiviteter (især **TilføjelsespostkasserTilladelser**) vil du måske bemærke, at den bruger, der udførte aktiviteten (og er identificeret i felterne Bruger og UserId), er NT AUTHORITY\SYSTEM eller NT AUTHORITY\SYSTEM(Microsoft.Exchange. Servicehost). Dette angiver, at den "bruger", der udførte aktiviteten, var en systemkonto i Exchange-tjenesten i Microsoft-cloudmiljøet. Denne systemkonto udfører ofte planlagte vedligeholdelsesopgaver på vegne af din organisation. Det kan f.eks. være en almindelig overvåget aktivitet, der udføres af NT AUTHORITY\SYSTEM(Microsoft.Exchange. ServiceHost)-kontoen er at opdatere tilladelserne til DiscoverySearchMailbox, som er en systempostkasse. Formålet med denne opdatering er at bekræfte, at FullAccess-tilladelsen (som er standarden) er tildelt rollegruppen Registreringsadministration for DiscoverySearchMailbox. Dette sikrer, at eDiscovery-administratorer kan udføre de nødvendige opgaver i deres organisation.

En anden systembrugerkonto, der kan identificeres i en overvågningspost for **Add-MailboxPermission** , er Administrator@apcprd03.prod.outlook.com. Denne tjenestekonto er også inkluderet i overvågningsposter for postkasser, der er relateret til bekræftelse og opdatering af FullAccess-tilladelsen, og den er tildelt rollegruppen Registreringsstyring for DiscoverySearchMailbox-systempostkassen. Overvågningsposter, der identificerer den Administrator@apcprd03.prod.outlook.com konto, udløses typisk, når Microsofts supportmedarbejdere kører et værktøj til diagnosticering af rollediagnosticering i RBAC på vegne af din organisation.

### <a name="user-administration-activities"></a>Brugeradministrationsaktiviteter

I følgende tabel vises de brugeradministrationsaktiviteter, der logføres, når en administrator tilføjer eller ændrer en brugerkonto ved hjælp af [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er angivet i kolonnen **Operation** i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i handlingsnavnet, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for overvågningsopbevaring, opretter politikker for beskeder eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde handlingsnavnet.

|Aktivitet|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet bruger|Tilføj bruger.|Der blev oprettet en brugerkonto.|
|Ændret brugerlicens|Skift brugerlicens.|Den licens, der er tildelt en bruger, hvad der er ændret. Hvis du vil se, hvilke licenser der var ændringer, skal du se den tilsvarende **opdaterede brugeraktivitet** .|
|Ændret brugeradgangskode|Skift brugeradgangskode.|En bruger ændrer sin adgangskode. Selvbetjent nulstilling af adgangskode skal aktiveres (for alle eller udvalgte brugere) i din organisation for at give brugerne tilladelse til at nulstille deres adgangskode. Du kan også spore selvbetjeningsaktivitet for nulstilling af adgangskode i Azure Active Directory. Du kan få flere oplysninger under [Rapporteringsindstillinger for administration af Azure AD-adgangskoder](/azure/active-directory/authentication/howto-sspr-reporting).
|Slettet bruger|Slet bruger.|En brugerkonto blev slettet.|
|Nulstil brugeradgangskode|Nulstil brugeradgangskoden.|Administratoren nulstiller adgangskoden for en bruger.|
|Angiv en egenskab, der tvinger brugeren til at ændre adgangskode|Angiv gennemtving ændring af brugeradgangskode.|Administratoren angiver den egenskab, der tvinger en bruger til at ændre sin adgangskode, næste gang brugeren logger på Microsoft 365.|
|Angiv licensegenskaber|Angiv licensegenskaber.|Administratoren ændrer egenskaberne for en licens, der er tildelt en bruger.|
|Opdateret bruger|Opdater bruger.|Administratoren ændrer en eller flere egenskaber for en brugerkonto. Du kan se en liste over de brugeregenskaber, der kan opdateres, i afsnittet "Opdater brugerattributter" i [Azure Active Directory Hændelser i overvågningsrapport](/azure/active-directory/reports-monitoring/concept-audit-logs).|
||||

### <a name="azure-ad-group-administration-activities"></a>Administrationsaktiviteter for Azure AD-grupper

I følgende tabel vises de gruppeadministrationsaktiviteter, der logføres, når en administrator eller en bruger opretter eller ændrer en Microsoft 365 gruppe, eller når en administrator opretter en sikkerhedsgruppe ved hjælp af [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller Azure-administrationsportalen. Du kan få flere oplysninger om grupper i Microsoft 365 under [Få vist, opret og slet grupper i Microsoft 365 Administration](../admin/create-groups/create-groups.md).

> [!NOTE]
> De handlingsnavne, der er angivet i kolonnen **Operation** i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i handlingsnavnet, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for overvågningsopbevaring, opretter politikker for beskeder eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde handlingsnavnet.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet gruppe|Tilføj gruppe.|Der blev oprettet en gruppe.|
|Medlemmet er føjet til gruppen|Føj medlem til gruppe.|Et medlem blev føjet til en gruppe.|
|Slettet gruppe|Slet gruppe.|En gruppe blev slettet.|
|Fjernede medlem fra gruppe|Fjern medlem fra gruppe.|Et medlem blev fjernet fra en gruppe.|
|Opdateret gruppe|Opdater gruppe.|En egenskab for en gruppe blev ændret.|
||||

### <a name="application-administration-activities"></a>Programadministrationsaktiviteter

I følgende tabel vises de programadministratoraktiviteter, der logføres, når en administrator tilføjer eller ændrer et program, der er registreret i Azure AD. Alle programmer, der er baseret på Azure AD til godkendelse, skal registreres i mappen.

> [!NOTE]
> De handlingsnavne, der er angivet i kolonnen **Operation** i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i handlingsnavnet, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for overvågningsopbevaring, opretter politikker for beskeder eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde handlingsnavnet.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Tilføjet delegeringspost|Tilføj delegeringspost.|Der blev oprettet/tildelt en godkendelsestilladelse til et program i Azure AD.|
|Tjenesteprincipalen er tilføjet|Tilføj tjenesteprincipal.|Et program blev registreret i Azure AD. Et program repræsenteres af en tjenesteprincipal i mappen.|
|Føjede legitimationsoplysninger til en tjenesteprincipal|Tilføj legitimationsoplysninger for tjenesteprincipal.|Legitimationsoplysningerne blev føjet til en tjenesteprincipal i Azure AD. Et tjenesteprincip repræsenterer et program i mappen.|
|Fjernede delegeringsindtastning|Fjern delegeringsindtastning.|En godkendelsestilladelse blev fjernet fra et program i Azure AD.|
|Fjernede en tjenesteprincipal fra mappen|Fjern tjenesteprincipalen.|Et program blev slettet/fjernet fra Azure AD. Et program repræsenteres af en tjenesteprincipal i mappen.|
|Fjernede legitimationsoplysninger fra en tjenesteprincipal|Fjern legitimationsoplysningerne for tjenesteprincipalen.|Legitimationsoplysningerne blev fjernet fra en tjenesteprincipal i Azure AD. Et tjenesteprincip repræsenterer et program i mappen.|
|Angiv delegeringsindtastning|Angiv delegeringsindtastning.|En godkendelsestilladelse blev opdateret for et program i Azure AD.|
||||

### <a name="role-administration-activities"></a>Aktiviteter til rolleadministration

I følgende tabel vises de azure AD-rolleadministrationsaktiviteter, der logføres, når en administrator administrerer administratorroller i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller på Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er angivet i kolonnen **Operation** i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i handlingsnavnet, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for overvågningsopbevaring, opretter politikker for beskeder eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde handlingsnavnet.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Føj medlem til rolle|Føj medlem til rolle.|Føjede en bruger til en administratorrolle i Microsoft 365.|
|Fjernede en bruger fra en mapperolle|Fjern medlem fra rolle.|Fjernede en bruger til fra en administratorrolle i Microsoft 365.|
|Angiv firmakontaktoplysninger|Angiv firmakontaktoplysninger.|Opdaterede organisationens kontaktindstillinger på virksomhedsniveau. Dette omfatter mailadresser til abonnementsrelaterede mails, der sendes af Microsoft 365, og tekniske meddelelser om tjenester.|
||||

### <a name="directory-administration-activities"></a>Aktiviteter til administration af adresseliste

I følgende tabel vises Azure AD-mappen og domænerelaterede aktiviteter, der logføres, når en administrator administrerer deres organisation i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) eller på Azure-administrationsportalen.

> [!NOTE]
> De handlingsnavne, der er angivet i kolonnen **Operation** i følgende tabel, indeholder et punktum ( `.` ). Du skal medtage perioden i handlingsnavnet, hvis du angiver handlingen i en PowerShell-kommando, når du søger i overvågningsloggen, opretter politikker for overvågningsopbevaring, opretter politikker for beskeder eller opretter aktivitetsbeskeder. Sørg også for at bruge dobbelte anførselstegn (`" "`) til at indeholde handlingsnavnet.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Domæne føjet til firma|Føj domæne til firma.|Føjede et domæne til din organisation.|
|Føjede en partner til mappen|Føj partner til virksomheden.|En partner (delegeret administrator) er føjet til din organisation.|
|Fjernede domæne fra firma|Fjern domæne fra firma.|Fjernede et domæne fra din organisation.|
|Fjernede en partner fra mappen|Fjern partner fra firmaet.|Fjernede en partner (uddelegeret administrator) fra din organisation.|
|Angiv firmaoplysninger|Angiv firmaoplysninger.|Opdaterede firmaoplysningerne for din organisation. Dette omfatter mailadresser til abonnementsrelaterede mails, der sendes af Microsoft 365, og tekniske meddelelser om Microsoft 365 tjenester.|
|Angiv domænegodkendelse|Angiv domænegodkendelse.|Ændrede indstillingen for domænegodkendelse for din organisation.|
|Opdaterede indstillingerne for sammenslutning for et domæne|Angiv indstillinger for sammenslutning på domænet.|Indstillingerne for organisationsnetværket (ekstern deling) er ændret.|
|Angiv adgangskodepolitik|Angiv adgangskodepolitik.|Ændrede længden og tegnbegrænsningerne for brugeradgangskoder i din organisation.|
|Slået Azure AD-synkronisering til|Angiv flaget DirSyncEnabled.|Angiv den egenskab, der aktiverer en mappe til Azure AD-synkronisering.|
|Opdateret domæne|Opdater domæne.|Opdaterede indstillingerne for et domæne i din organisation.|
|Bekræftet domæne|Kontrollér domænet.|Bekræftet, at din organisation er ejer af et domæne.|
|Bekræftet mailbekræftet domæne|Bekræft mailbekræftet domæne.|Brugte mailbekræftelse til at bekræfte, at din organisation er ejer af et domæne.|
||||

### <a name="ediscovery-activities"></a>eDiscovery-aktiviteter

Indholdssøgning og eDiscovery-relaterede aktiviteter, der udføres i Security and Compliance Center eller ved at køre de tilsvarende PowerShell-cmdlet'er, logføres i overvågningsloggen. Dette omfatter følgende aktiviteter:

- Oprettelse og administration af eDiscovery-sager

- Oprettelse, start og redigering af indholdssøgninger

- Udførelse af handlinger til indholdssøgning, f.eks. visning, eksport og sletning af søgeresultater

- Konfiguration af filtrering af tilladelser til indholdssøgning

- Administration af rollen eDiscovery-administrator

Du kan finde en liste og en detaljeret beskrivelse af de eDiscovery-aktiviteter, der logføres, [under Søg efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Det tager op til 30 minutter, før hændelser, der stammer fra de aktiviteter, der er angivet under **eDiscovery-aktiviteter** og **eDiscovery-aktiviteter (Premium)** på rullelisten **Aktiviteter**, vises i søgeresultaterne. Omvendt tager det op til 24 timer, før de tilsvarende hændelser fra eDiscovery-cmdlet-aktiviteter vises i søgeresultaterne.

### <a name="ediscovery-premium-activities"></a>eDiscovery-aktiviteter (Premium)

Du kan også søge i overvågningsloggen efter aktiviteter i Microsoft Purview eDiscovery (Premium). Du kan finde en beskrivelse af disse aktiviteter i afsnittet "eDiscovery(Premium)-aktiviteter" i [Søg efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-premium-activities).

### <a name="power-bi-activities"></a>Power BI aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Power BI. Du kan få oplysninger om Power BI aktiviteter i afsnittet "Aktiviteter, der overvåges af Power BI" under [Brug af overvågning i din organisation](/power-bi/service-admin-auditing#activities-audited-by-power-bi).

Overvågningslogføring for Power BI er ikke aktiveret som standard. Hvis du vil søge efter Power BI aktiviteter i overvågningsloggen, skal du aktivere overvågning på Power BI administrationsportal. Du kan finde instruktioner i afsnittet "Overvågningslogge" i [Power BI administrationsportal](/power-bi/service-admin-portal#audit-logs).

### <a name="workplace-analytics-activities"></a>Workplace Analytics-aktiviteter

Workplace Analytics giver indsigt i, hvordan grupper samarbejder på tværs af din organisation. I følgende tabel vises de aktiviteter, der udføres af brugere, der har fået tildelt rollen Administrator eller Analytiker i Workplace Analytics. Brugere, der har fået tildelt rollen Analytiker, har fuld adgang til alle tjenestefunktioner og bruger produktet til at foretage analyser. Brugere, der er tildelt rollen Administrator, kan konfigurere indstillinger for beskyttelse af personlige oplysninger og systemstandarder og kan forberede, uploade og bekræfte organisationsdata i Workplace Analytics. Du kan få flere oplysninger under [Workplace Analytics](/workplace-analytics/index-orig).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Adgang til OData-link|AccessedOdataLink|Analytiker har åbnet OData-linket for en forespørgsel.|
|Annulleret forespørgsel|CanceledQuery|Analytikeren annullerede en kørende forespørgsel.|
|Mødeudeladelse er oprettet|MeetingExclusionCreated|Analytiker oprettede en regel for mødeudeladelse.|
|Slettede resultat|DeletedResult|Analytiker slettede et forespørgselsresultat.|
|Downloadet rapport|DownloadedReport|Analytiker downloadede en fil med forespørgselsresultatet.|
|Udført forespørgsel|ExecutedQuery|Analytiker kørte en forespørgsel.|
|Opdaterede indstillingen for dataadgang|UpdatedDataAccessSetting|Administratoren opdaterede indstillingerne for dataadgang.|
|Opdateret indstilling for beskyttelse af personlige oplysninger|UpdatedPrivacySetting|Administratoren opdaterede indstillingerne for beskyttelse af personlige oplysninger. f.eks. minimumgruppestørrelse.|
|Overførte organisationsdata|UploadedOrgData|Administratoren har uploadet en organisationsdatafil.|
|Bruger, der er logget på<sup>*</sup>| UserLoggedIn |En bruger er logget på sin Microsoft 365 brugerkonto.|
|Brugeren er logget af<sup>*</sup>| UserLoggedOff |En bruger loggede af sin Microsoft 365 brugerkonto.
|Set udforsk|ViewedExplore|Analytiker fik vist visualiseringer under en eller flere udforsk sidefaner.|
||||

> [!NOTE]
> <sup>*</sup>Disse er Azure Active Directory logon- og log af-aktiviteter. Disse aktiviteter logføres, selvom du ikke har Workplace Analytics slået til i din organisation. Du kan finde flere oplysninger om brugerlogføringsaktiviteter under [Logge på Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>Microsoft Teams aktiviteter

Du kan søge i overvågningsloggen efter bruger- og administratoraktiviteter i Microsoft Teams. Teams er et chatbaseret arbejdsområde i Microsoft 365. Det samler et teams samtaler, møder, filer og noter på ét sted. Du kan finde beskrivelser af de Teams aktiviteter, der overvåges, [under Søg i overvågningsloggen efter hændelser i Microsoft Teams](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Microsoft Teams sundhedsaktiviteter

Hvis din organisation bruger [programmet Patienter](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) i Microsoft Teams, kan du søge i overvågningsloggen efter aktiviteter, der er relateret til appen Patienter. Hvis dit miljø er konfigureret til at understøtte appen Patienter, er der en yderligere aktivitetsgruppe for disse aktiviteter tilgængelig på listen **Aktivitetsvælger** .

![Microsoft Teams Sundhedstjenester på listen over aktivitetsvælgere.](../media/TeamsHealthcareAuditActivities.png)

Du kan finde en beskrivelse af aktiviteterne i appen Patienter i [appen Overvågningslogge for patienter](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Microsoft Teams skiftaktiviteter

Hvis din organisation bruger appen Shifts i Microsoft Teams, kan du søge i overvågningsloggen efter aktiviteter, der er relateret til appen Skifts. Hvis dit miljø er konfigureret til at understøtte Skift-apps, er der en ekstra aktivitetsgruppe for disse aktiviteter tilgængelig på listen **Aktivitetsvælger** .

Du kan finde en beskrivelse af aktiviteter i Appen Skift under [Søg i overvågningsloggen efter hændelser i Microsoft Teams](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Yammer aktiviteter

I følgende tabel vises de bruger- og administratoraktiviteter i Yammer, der er logført i overvågningsloggen. Hvis du vil returnere Yammer-relaterede aktiviteter fra overvågningsloggen, skal du vælge **Vis resultater for alle aktiviteter** på listen **Aktiviteter**. Brug datoområdefelterne og listen **Brugere** til at indsnævre søgeresultaterne.

> [!NOTE]
> Nogle Yammer overvågningsaktiviteter er kun tilgængelige under Overvågning (Premium). Det betyder, at brugerne skal tildeles den relevante licens, før disse aktiviteter logføres i overvågningsloggen. Du kan få flere oplysninger om aktiviteter, der kun er tilgængelige under Overvågning (Premium), under [Overvågning (Premium) i Microsoft 365](advanced-audit.md#audit-premium-events). Du kan finde oplysninger om overvågningskrav (Premium) [under Overvågning af løsninger i Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>I følgende tabel fremhæves overvågningsaktiviteter (Premium) med en stjerne (*).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Ændrede politik for dataopbevaring|SoftDeleteSettingsUpdated|Den bekræftede administrator opdaterer indstillingen for politikken for opbevaring af netværksdata til enten Hard Delete eller Soft Delete. Det er kun bekræftede administratorer, der kan udføre denne handling.|
|Ændrede netværkskonfiguration|NetworkConfigurationUpdated|Netværk eller bekræftet administrator ændrer Yammer netværkets konfiguration. Dette omfatter angivelse af intervallet for eksport af data og aktivering af chat.|
|Ændrede indstillinger for netværksprofil|ProcessProfileFields|Netværk eller bekræftet administrator ændrer de oplysninger, der vises på medlemsprofiler for netværkets brugere.|
|Ændret tilstand for privat indhold|SupervisorAdminToggled|Bekræftet administrator slår  *tilstanden Privat indhold til*  eller fra. I denne tilstand kan en administrator få vist meddelelserne i private grupper og få vist private meddelelser mellem individuelle brugere (eller grupper af brugere). Det er kun bekræftede administratorer, der kan udføre denne handling.|
|Ændret sikkerhedskonfiguration|NetworkSecurityConfigurationUpdated|Den bekræftede administrator opdaterer Yammer netværks sikkerhedskonfiguration. Dette omfatter angivelse af politikker for udløb af adgangskode og begrænsninger for IP-adresser. Det er kun bekræftede administratorer, der kan udføre denne handling.|
|Oprettet fil|Filoprettet|Brugeren uploader en fil.|
|Oprettet gruppe|Gruppeoprettelse|Brugeren opretter en gruppe.|
|Oprettet meddelelse<sup>*</sup>|Meddelelsesoprettet|Brugeren opretter en meddelelse.|
|Slettet gruppe|GroupDeletion|En gruppe slettes fra Yammer.|
|Slettet meddelelse|Meddelelsesdeleted|Brugeren sletter en meddelelse.|
|Downloadet fil|FileDownloaded|Brugeren downloader en fil.|
|Eksporterede data|Dataeksport|Bekræftet administrator eksporterer Yammer netværksdata. Det er kun bekræftede administratorer, der kan udføre denne handling.|
|Det lykkedes ikke at få adgang til community'et<sup>*</sup>|CommunityAccessFailure|Brugeren kunne ikke få adgang til et community.|
|Det lykkedes ikke at få adgang til filen<sup>*</sup>|FileAccessFailure|Brugeren kunne ikke få adgang til en fil.|
|Det lykkedes ikke at få adgang til meddelelsen<sup>*</sup>|MessageAccessFailure|Brugeren kunne ikke få adgang til en meddelelse.|
|Delt fil|Fildelt|Brugeren deler en fil med en anden bruger.|
|Afbrudt netværksbruger|NetworkUserSuspended|Netværk eller bekræftet administrator afbryder (deaktiverer) en bruger fra Yammer.|
|Afbrudt bruger|UserSuspension|Brugerkontoen er suspenderet (deaktiveret).|
|Opdateret filbeskrivelse|FileUpdateDescription|Brugeren ændrer beskrivelsen af en fil.|
|Opdateret filnavn|Navn på filopdatering|Brugeren ændrer navnet på en fil.|
|Opdateret meddelelse<sup>*</sup>|Meddelelse er blevet gemt|Brugeren opdaterer en meddelelse.|
|Vist fil|FilVisited|Brugeren får en fil til at se.|
|Vist meddelelse<sup>*</sup>|Meddelelse vist|Brugeren får vist en meddelelse.|
||||

### <a name="microsoft-power-automate-activities"></a>Microsoft Power Automate aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Power Automate (tidligere kaldet Microsoft Flow). Disse aktiviteter omfatter oprettelse, redigering og sletning af flow og ændring af flowtilladelser. Du kan få oplysninger om overvågning af Power Automate aktiviteter på bloggen [Power Automate overvågningshændelser, der nu er tilgængelige på overholdelsesportalen](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Microsoft Power Apps aktiviteter

Du kan søge i overvågningsloggen efter apprelaterede aktiviteter i Power Apps. Disse aktiviteter omfatter oprettelse, start og publicering af en app. Tildeling af tilladelser til apps overvåges også. Du kan få en beskrivelse af alle Power Apps aktiviteter under [Logføring af aktivitet for at få vist Power Apps](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Microsoft Stream aktiviteter

Du kan søge i overvågningsloggen efter aktiviteter i Microsoft Stream. Disse aktiviteter omfatter videoaktiviteter, der udføres af brugere, gruppekanalaktiviteter og administratoraktiviteter, f.eks. administration af brugere, administration af organisationsindstillinger og eksport af rapporter. Du kan finde en beskrivelse af disse aktiviteter i afsnittet "Handlinger, der er logget på Stream" i [Overvågningslogge i Microsoft Stream](/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>Aktiviteter i Indholdsoversigt

I følgende tabel vises de aktiviteter i Indholdsoversigt, der er logført i overvågningsloggen. Indholdsoversigt, som du kan få adgang til i værktøjet Dataklassificering på overholdelsesportalen. [Du kan få flere oplysninger under Brug af indholdsoversigt til dataklassificering](data-classification-content-explorer.md).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Element, der er åbnet|LabelContentExplorerAccessedItem|En administrator (eller en bruger, der er medlem af rollegruppen Indholdsoversigt i Indholdsoversigt) bruger Indholdsoversigt til at få vist en mail eller SharePoint/OneDrive dokument.|
||||

### <a name="quarantine-activities"></a>Karantæneaktiviteter

I følgende tabel vises de karantæneaktiviteter, du kan søge efter i overvågningsloggen. Du kan få flere oplysninger om karantæne under [Karantænemails](../security/office-365-security/quarantine-email-messages.md).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Slettet karantænemeddelelse|Karantæneslete|En bruger slettede en mail, der blev anset for at være skadelig.|
|Eksporteret karantænemeddelelse|Karantæneeksport|En bruger eksporterede en mail, der blev anset for at være skadelig.|
|Eksempel på karantænemeddelelse|Eksempel på karantæne|En bruger fik forhåndsvist en mail, der blev anset for at være skadelig.|
|Frigivet karantænemeddelelse|Karantænerelease|En bruger har frigivet en mail fra karantæne, der blev anset for at være skadelig.|
|Fik vist karantænemeddelelsens brevhoved|QuarantineViewHeader|En bruger fik vist overskriften i en mail, der blev anset for at være skadelig.|
||||

### <a name="microsoft-forms-activities"></a>Microsoft Forms aktiviteter

Tabellerne i dette afsnit bruger- og administratoraktiviteterne i Microsoft Forms, der er logført i overvågningsloggen. Microsoft Forms er et formular-/quiz-/undersøgelsesværktøj, der bruges til at indsamle data til analyse. Hvis det er angivet nedenfor i beskrivelserne, indeholder nogle handlinger yderligere aktivitetsparametre.

Hvis en formularaktivitet udføres af en medforfatter eller en anonym responder, logføres den lidt anderledes. Du kan få flere oplysninger i afsnittet [Formularaktiviteter udført af medforfattere og anonyme respondere](#forms-activities-performed-by-coauthors-and-anonymous-responders) .

> [!NOTE]
> Nogle formularovervågningsaktiviteter er kun tilgængelige i Overvågning (Premium). Det betyder, at brugerne skal tildeles den relevante licens, før disse aktiviteter logføres i overvågningsloggen. Du kan få flere oplysninger om aktiviteter, der kun er tilgængelige under Overvågning (Premium), under [Overvågning (Premium) i Microsoft 365](advanced-audit.md#audit-premium-events). Du kan finde oplysninger om overvågningskrav (Premium) [under Overvågning af løsninger i Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>I følgende tabel fremhæves overvågningsaktiviteter (Premium) med en stjerne (*).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Oprettet kommentar|Opretkommentar|Formularejeren føjer en kommentar eller score til en quiz.|
|Oprettet formular|Opretformular|Formularejeren opretter en ny formular. <br><br>Property DataMode:string angiver, at den aktuelle formular er indstillet til at synkronisere med en ny eller eksisterende Excel projektmappe, hvis egenskabsværdien er lig med DataSync. Egenskaben ExcelWorkbookLink:string angiver det tilknyttede Excel projektmappe-id for den aktuelle formular.|
|Redigeret formular|Redigerformular|Ejeren af formularen redigerer en formular, f.eks. oprettelse, fjernelse eller redigering af et spørgsmål. Egenskaben *EditOperation:string* angiver navnet på redigeringshandlingen. De mulige handlinger er:<br/>- Opretanmodning<br/>- CreateQuestionChoice <br/>- Sletanmodning <br/>- DeleteQuestionChoice <br/>- DeleteFormImage <br/>- DeleteQuestionImage <br/>- UpdateQuestion <br/>- UpdateQuestionChoice <br/>- UploadFormImage/Bing/Onedrive <br/>- UploadQuestionImage <br/>- SkiftTema <br><br>FormImage indeholder et hvilket som helst sted i Formularer, som brugeren kan uploade et billede, f.eks. i en forespørgsel eller som et baggrundstema.|
|Flyttet formular|Flytformular|Ejeren af formularen flytter en formular. <br><br>Property DestinationUserId:string angiver bruger-id'et for den person, der flyttede formularen. Property NewFormId:string er det nye id for den nyligt kopierede formular. Egenskaben IsDelegateAccess:boolesk angiver, at den aktuelle handling for flytning af en formular udføres via administrationsstedfortrædersiden.|
|Slettet formular|Sletformular|Ejeren af formularen sletter en formular. Dette omfatter SoftDelete (indstillingen Slet bruges, og formularen flyttes til papirkurven) og HardDelete (Papirkurv tømmes).|
|Vist formular (designtidspunkt)|Visformular|Formularejeren åbner en eksisterende formular til redigering. <br><br>AccessDenied:boolesk egenskab angiver, at adgang til den aktuelle formular er nægtet pga. tilladelseskontrol. Property FromSummaryLink:boolean angiver, at den aktuelle anmodning kommer fra oversigtslinksiden.|
|Formular, der er forhåndsvist|Eksempelformular|Formularejeren får vist et eksempel på en formular ved hjælp af funktionen Preview.|
|Eksporteret formular|Eksportformular|Formularejeren eksporterer resultater til Excel. <br><br>Property ExportFormat:string angiver, om den Excel fil er Download eller Online.|
|Tilladt delingsformular til kopiering|AllowShareFormForCopy|Ejeren af formularen opretter et skabelonlink til deling af formularen med andre brugere. Denne hændelse logføres, når formularens ejer klikker for at generere skabelonens URL-adresse.|
|Ikke-tilladt delingsformular til kopiering|Tillad ikkeShareFormForCopy|Formularejeren sletter skabelonlinket.|
|Medforfatter af tilføjet formular|AddFormCoauthor|En bruger bruger et samarbejdslink til at designe/få vist svar. Denne hændelse logføres, når en bruger bruger en URL-adresse til sorteringslab (ikke når URL-adressen til sorteringslab oprettes første gang).|
|Medforfatter af fjernet formular|RemoveFormCoauthor|Formularejeren sletter et samarbejdslink.|
|Vist svarside|ViewRuntimeForm|Brugeren har åbnet en svarside for at få vist. Denne hændelse logføres, uanset om brugeren sender et svar eller ej.|
|Oprettet svar|OpretRespons|Svarer til at modtage et nyt svar.  En bruger har sendt et svar til en formular. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym responder vil egenskaben ResponderId være null.|
|Opdateret svar|UpdateResponse|Ejeren af formularen har opdateret en kommentar eller score i en quiz. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym responder vil egenskaben ResponderId være null.|
|Alle svar er slettet|SletAllesletninger|Ejeren af formularen sletter alle svardata.|
|Slettet svar|SletRespons|Formularejeren sletter ét svar. <br><br>Property ResponseId:string angiver det svar, der slettes.|
|Viste svar|VisResponser|Ejeren af formularen får vist den samlede liste over svar. <br><br>Property ViewType:string angiver, om formularens ejer får vist detaljer eller samlinger|
|Vist svar|VisRespons|Formularejeren får et bestemt svar. <br><br>Property ResponseId:string og Property ResponderId:string angiver, hvilket resultat der vises. <br><br>For en anonym responder vil egenskaben ResponderId være null.|
|Link til oprettet oversigt|HentSummaryLink|Formularejeren opretter link til oversigtsresultater for at dele resultater.|
|Link til slettet oversigt|Sletsumelink|Formularejeren sletter linket med oversigtsresultater.|
|Opdateret phishingstatus for formular|UpdatePhishingStatus|Denne hændelse logføres, når den detaljerede værdi for den interne sikkerhedsstatus blev ændret, uanset om dette ændrede den endelige sikkerhedstilstand (formularen er f.eks. nu Lukket eller Åbnet). Det betyder, at du kan se dublethændelser uden en endelig ændring af sikkerhedstilstanden. De mulige statusværdier for denne hændelse er:<br/>- Tag ned <br/>- Tag ned af administratoren <br/>- Blokeringen af administratoren er fjernet <br/>- Automatisk blokeret <br/>- Automatisk fjernelse af blokering <br/>- Kunde rapporteret <br/>- Nulstil kunde rapporteret|
|Opdateret bruger phishing-status|UpdateUserPhishingStatus|Denne hændelse logføres, hver gang værdien for brugerens sikkerhedsstatus blev ændret. Værdien af brugerstatussen i overvågningsposten **bekræftes som Phisher** , da brugeren oprettede en phishing-formular, der blev fjernet af Microsoft Online-sikkerhedsteamet. Hvis en administrator fjerner blokeringen af brugeren, angives værdien af brugerens status til **Nulstil som normal bruger**.|
|Invitation til sendte formularer Pro|Invitation til proinvitation|Brugeren klikker for at aktivere en Pro prøveversion.|
|Opdateret formularindstilling<sup>*</sup> |UpdateFormSetting|Formularejeren opdaterer en eller flere formularindstillinger. <br><br>Property FormSettingName:string angiver opdaterede følsomme indstillingers navn. Property NewFormSettings:string angiver opdaterede indstillingers navn og nye værdi. Property thankYouMessageContainsLink:boolean angiver, at den opdaterede takkemeddelelse indeholder et URL-link.|
|Opdateret brugerindstilling|UpdateUserSetting|Formularejeren opdaterer en brugerindstilling. <br><br>Property UserSettingName:string angiver indstillingens navn og nye værdi|
|Viste formularer<sup>*</sup>|ListForms|Ejeren af formularen får vist en liste over formularer. <br><br>Property ViewType:string angiver, hvilken visning formularens ejer ser på: Alle formularer, Delt med mig eller Gruppeformularer|
|Indsendt svar|SendResponse|En bruger sender et svar til en formular. <br><br>Egenskaben IsInternalForm:boolesk angiver, om responderen er i samme organisation som formularejeren.|
|Indstillingen Aktiveret for alle kan svare<sup>*</sup>|AllowAnonymousResponse|Ejeren af formularen slår indstillingen til, så alle kan svare på formularen.|
|Indstillingen Deaktiveret for alle kan svare<sup>*</sup>|DisallowAnonymousResponse|Ejeren af formularen slår indstillingen fra, så alle kan svare på formularen.|
|Indstilling for aktiverede bestemte personer kan svare<sup>*</sup>|EnableSpecificResponse|Formularejeren slår indstillingen til, så det kun er bestemte personer eller bestemte grupper i den aktuelle organisation, der kan svare på formularen.|
|Indstillingen Deaktiverede bestemte personer kan svare<sup>*</sup>|DisableSpecificResponse|Ejeren af formularen slår indstillingen fra, så det kun er bestemte personer eller bestemte grupper i den aktuelle organisation, der kan svare på formularen.|
|Tilføjet specifik responder<sup>*</sup>|AddSpecificResponder|Formularejeren føjer en ny bruger eller gruppe til den specifikke liste over besvarere.|
|Fjernede en bestemt responder<sup>*</sup>|RemoveSpecificResponder|Ejeren af formularen fjerner en bruger eller gruppe fra den specifikke liste over de personer, der besvarer formularen.|
|Deaktiveret samarbejde<sup>*</sup>|DisableCollaboration|Ejeren af formularen slår indstillingen for samarbejde i formularen fra.|
|Aktiveret samarbejde Office 365 arbejds- eller skolekonto<sup>*</sup>|Aktivér arbejde eller skolesamling|Ejeren af formularen slår indstillingen til, så brugere med en Microsoft 365 arbejds- eller skolekonto kan få vist og redigere formularen.|
|Aktiverede personer i mit organisationssamarbejde<sup>*</sup>|EnableSameOrgCollaboration|Ejeren af formularen slår indstillingen til, så brugere i den aktuelle organisation kan få vist og redigere formularen.|
|Aktiveret samarbejde om bestemte personer<sup>*</sup>|EnableSpecificCollaboaration|Ejeren af formularen slår indstillingen til, så det kun er bestemte personer eller bestemte grupper i den aktuelle organisation, der kan få vist og redigere formularen.|
|Der er oprettet forbindelse til Excel projektmappe<sup>*</sup>|ConnectToExcelWorkbook|Forbundet formularen med en Excel projektmappe. <br><br>Egenskaben ExcelWorkbookLink:string angiver det tilknyttede Excel projektmappe-id for den aktuelle formular.|
|Oprettede en samling|Samling oprettet|Formularejeren oprettede en samling.|
|Opdaterede en samling|CollectionUpdated|Ejeren af formularen opdaterede en samlingsegenskab.|
|Slettede samling fra Papirkurv|CollectionHardDeleted|Formularejeren har slettet en samling fra papirkurven.|
|Flyttede samlingen til Papirkurven|CollectionSoftDeleted|Ejeren af formularen flyttede en samling til Papirkurven.|
|Omdøbte en samling|CollectionRenamed|Formularejeren ændrede navnet på en samling.|
|Flyttede en formular til en samling|MovedFormIntoCollection|Ejeren af formularen flyttede en formular til en samling.|
|Flyttede en formular ud af samlingen|MovedFormOutofCollection|Ejeren af formularen flyttede en formular ud af en samling.|
||||

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Formularaktiviteter udført af medforfattere og anonyme respondere

Formularer understøtter samarbejde, når formularer er designet, og når svar analyseres. En formularsamarbejdspartner kaldes en *medforfatter*. Medforfattere kan gøre alt, hvad en formularejer kan gøre, bortset fra at slette eller flytte en formular. Formularer giver dig også mulighed for at oprette en formular, der kan besvares anonymt. Det betyder, at den, der svarer, ikke behøver at være logget på din organisation for at svare på en formular.

I følgende tabel beskrives overvågningsaktiviteterne og oplysningerne i overvågningsposten for aktiviteter, der udføres af medforfattere og anonyme respondere.

|Aktivitetstype|Intern eller ekstern bruger|Bruger-id, der er logført|Organisationen er logget på|Formularbrugertype|
|:-----|:-----|:-----|:-----|:-----|
|Samtidig redigering af aktiviteter|Interne|UPN|Formularejerens organisation|Medforfatter|
|Samtidig redigering af aktiviteter|Eksterne|UPN<br>|Medforfatters organisation<br>|Medforfatter|
|Samtidig redigering af aktiviteter|Eksterne|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(Den anden del af id'et er et hash, som vil variere for forskellige brugere)|Formularejerens organisation<br>|Medforfatter|
|Svaraktiviteter|Eksterne|UPN<br>|Responderens organisation<br>|Responder|
|Svaraktiviteter|Eksterne|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(Den anden del af bruger-id'et er et hash, som vil variere for forskellige brugere)|Formularejerens organisation|Responder|
|Svaraktiviteter|Anonym|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(Den anden del af bruger-id'et er et hash, som vil variere for forskellige brugere)|Formularejerens organisation|Responder|
||||

### <a name="sensitivity-label-activities"></a>Aktiviteter med følsomhedsmærkater

I følgende tabel vises hændelser, der skyldes brug af [følsomhedsmærkater](sensitivity-labels.md).

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
|Anvendte følsomhedsmærkat på webstedet|SensitivityLabelApplied|Der blev anvendt en følsomhedsmærkat på et SharePoint eller Teams websted.|
|Følsomhedsmærkaten er fjernet fra webstedet|SensitivityLabelRemoved|En følsomhedsmærkat blev fjernet fra et SharePoint eller Teams websted.|
|Anvendte følsomhedsmærkat på fil|FileSensitivityLabelApplied|Der blev anvendt en følsomhedsmærkat på et dokument ved hjælp af Microsoft 365 apps Office på internettet. eller en politik for automatisk mærkning.|
|Ændret følsomhedsmærkat anvendt på fil|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|Der blev anvendt en anden følsomhedsmærkat på et dokument. <br /><br>Handlingerne for denne aktivitet er forskellige, afhængigt af hvordan mærkaten blev ændret:<br /> - Office på internettet eller en politik for automatisk mærkning (FileSensitivityLabelChanged) <br /> – Microsoft 365 apps (SensitivityLabelUpdated)|
|Ændret følsomhedsmærkat på et websted|SensitivityLabelChanged|Der blev anvendt en anden følsomhedsmærkat på et SharePoint eller Teams websted.|
|Følsomhedsmærkaten er fjernet fra filen|FileSensitivityLabelRemoved|En følsomhedsmærkat blev fjernet fra et dokument ved hjælp af Microsoft 365 apps, Office på internettet, en politik for automatisk mærkning eller cmdlet'en [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile).|
||||

### <a name="retention-policy-and-retention-label-activities"></a>Opbevaringspolitik og aktiviteter med opbevaringsmærkater

I følgende tabel beskrives konfigurationsaktiviteterne for [opbevaringspolitikker og opbevaringsmærkater](retention.md) , da de blev oprettet, omkonfigureret eller slettet.

|Fuldt navn|Drift|Beskrivelse|
|:-----|:-----|:-----|
| Ændrede medlemskab af adaptivt omfang |ApplicableAdaptiveScopeChange |Brugere, websteder eller grupper blev føjet til eller fjernet fra det tilpassede område. Disse ændringer er resultatet af at køre områdets forespørgsel. Da ændringerne er systeminitieret, vises den rapporterede bruger som et GUID i stedet for en brugerkonto.|
| Konfigurerede indstillinger for en opbevaringspolitik |NyRetentionComplianceRule |Administratoren har konfigureret opbevaringsindstillingerne for en ny opbevaringspolitik. Opbevaringsindstillinger omfatter, hvor længe elementer bevares, og hvad der sker med elementer, når opbevaringsperioden udløber (f.eks. sletning af elementer, bevarelse af elementer eller opbevaring og derefter sletning af dem). Denne aktivitet svarer også til at køre cmdlet'en [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) .|
| Oprettet tilpasset omfang |NewAdaptiveScope |Administratoren har oprettet et adaptivt omfang.|
| Oprettet opbevaringsmærkat |NewComplianceTag |Administratoren har oprettet en ny opbevaringsmærkat.|
| Oprettet opbevaringspolitik |NewRetentionCompliancePolicy|Administratoren har oprettet en ny opbevaringspolitik.|
| Slettet adaptivt område | RemoveAdaptiveScope| Administratoren slettede et adaptivt område.|
| Slettede indstillinger fra en opbevaringspolitik| RemoveRetentionComplianceRule<br/>| Administratoren slettede konfigurationsindstillingerne for en opbevaringspolitik. Denne aktivitet logføres sandsynligvis, når en administrator sletter en opbevaringspolitik eller kører cmdlet'en [Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule) .|
| Slettede opbevaringsmærkat |RemoveComplianceTag | Administratoren slettede en opbevaringsmærkat.|
| Slettede opbevaringspolitik |RemoveRetentionCompliancePolicy<br/> |Administratoren slettede en opbevaringspolitik. |
| Aktiveret indstilling for lovmæssig post for opbevaringsmærkater<br/> |SetRestrictiveRetentionUI |Administratoren kørte cmdlet'en [Set-RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) , så en administrator derefter kan vælge konfigurationsindstillingen for brugergrænsefladen for en opbevaringsmærkat for at markere indhold som en lovmæssig post.|
| Opdateret tilpasset omfang | SetAdaptiveScope | Administratoren har ændret beskrivelsen eller forespørgslen for et eksisterende tilpasset område. |
| Opdaterede indstillinger for en opbevaringspolitik | SetRetentionComplianceRule | Administratoren ændrede opbevaringsindstillingerne for en eksisterende opbevaringspolitik. Opbevaringsindstillinger omfatter, hvor længe elementer bevares, og hvad der sker med elementer, når opbevaringsperioden udløber (f.eks. sletning af elementer, bevarelse af elementer eller opbevaring og derefter sletning af dem). Denne aktivitet svarer også til at køre cmdlet'en [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) . |
| Opdateret opbevaringsmærkat |SetComplianceTag  | Administratoren har opdateret en eksisterende opbevaringsmærkat.|
| Opdateret opbevaringspolitik |SetRetentionCompliancePolicy |Administratoren har opdateret en eksisterende opbevaringspolitik. Opdateringer, der udløser denne hændelse, omfatter tilføjelse eller udeladelse af indholdsplaceringer, som opbevaringspolitikken anvendes på.|
||||

### <a name="briefing-email-activities"></a>Aktiviteter i briefingmail

I følgende tabel vises de aktiviteter i Briefing-mail, der er logført i Microsoft 365 overvågningslog. Du kan få flere oplysninger om Briefing-mail under:

- [Oversigt over Briefing-mail](/Briefing/be-overview)

- [Konfigurer Briefing-mail](/Briefing/be-admin)

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:----|:-----|:-----|
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for organisationen|UpdatedOrganizationBriefingSettings|Administratoren opdaterer organisationens indstillinger for beskyttelse af personlige oplysninger for Briefing-mail. |
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for brugeren|UpdatedUserBriefingSettings|Administratoren opdaterer indstillingerne for beskyttelse af personlige oplysninger for Briefing-mail.
||||

### <a name="myanalytics-activities"></a>MyAnalytics-aktiviteter

I følgende tabel vises de aktiviteter i MyAnalytics, der er logført i Microsoft 365 overvågningslog. Du kan få flere oplysninger om MyAnalytics under [MyAnalytics for administratorer](/workplace-analytics/myanalytics/overview/mya-for-admins).

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdaterede indstillingerne for MyAnalytics for organisationen|UpdatedOrganizationMyAnalyticsSettings|Administratoren opdaterer indstillinger på organisationsniveau for MyAnalytics. |
|Opdaterede brugerindstillinger for MyAnalytics|UpdatedUserMyAnalyticsSettings|Administratoren opdaterer brugerindstillingerne for MyAnalytics.|
||||

### <a name="information-barriers-activities"></a>Aktiviteter inden for informationsbarrierer

I følgende tabel vises de aktiviteter i informationsbarrierer, der logføres i Microsoft 365 overvågningslog. Du kan finde flere oplysninger om informationsbarrierer [under Få mere at vide om informationsbarrierer i Microsoft 365](information-barriers.md).

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:----------------|:------------|:--------------|
| Føjede segmenter til et websted | SegmenterTilføj | En SharePoint, global administrator eller webstedsejer har føjet et eller flere informationsbarrierer til et websted. |
| Ændrede segmenter på et websted | Segment ændret | En SharePoint eller global administrator ændrede et eller flere informationsbarrieresegmenter for et websted. |
| Fjernede segmenter fra et websted | Segmentflytning | En SharePoint eller global administrator fjernede et eller flere informationsbarrieresegmenter fra et websted. |
||||

### <a name="disposition-review-activities"></a>Dispositionsgennemgangsaktiviteter

I følgende tabel vises de aktiviteter, som en dispositionslæser tog, da et element nåede slutningen af den konfigurerede opbevaringsperiode. Du kan få flere oplysninger under [Visning og bortskaffelse af indhold](disposition.md#viewing-and-disposing-of-content).

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:-----|:-----|:-----|
|Godkendt bortskaffelse|GodkendDisposal|En dispositionslæser godkendte fordelingen af elementet for at flytte det til næste dispositionsfase. Hvis elementet var i den eneste eller sidste fase af dispositionsgennemgangen, markerede dispositionsgodkendelsen elementet som kvalificeret til permanent sletning.|
|Forlænget opbevaringsperiode|UdvidRetention|En dispositionslæser udvidede opbevaringsperioden for elementet.|
|Element, der er navngivet igen|RelabelItem|En dispositionslæser har navngivet opbevaringsmærkaten igen.|
|Tilføjede korrekturlæsere|AddReviewer|En dispositionslæser føjede en eller flere brugere til den aktuelle fase i dispositionsgennemgangen.|
||||

### <a name="communication-compliance-activities"></a>Aktiviteter i forbindelse med overholdelse af angivne standarder for kommunikation

I følgende tabel vises aktiviteter for kommunikation med overholdelse af angivne standarder, der er logført i Microsoft 365 overvågningslog. Du kan finde flere oplysninger [under Få mere at vide om overholdelse af angivne standarder for kommunikation i Microsoft 365](communication-compliance.md).

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdatering af politik|TilsynspolitikOprettet, TilsynSpolitikOpdatering, TilsynspolitikDeleted|En administrator af kommunikationsoverholdelse har udført en politikopdatering.|
|Politikmatch|TilsynSregelmatch|En bruger har sendt en meddelelse, der svarer til en politiks betingelse.|
|Mærke, der er anvendt på meddelelser|Tilsynsvisningsmærke|Mærker anvendes på meddelelser, eller meddelelser fortolkes.|
||||

### <a name="report-activities"></a>Rapportaktiviteter

I følgende tabel vises de aktiviteter for forbrugsrapporter, der er logført i Microsoft 365 overvågningslog.

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:-----|:-----|:-----|
|Opdaterede indstillinger for beskyttelse af personlige oplysninger for forbrugsrapport|UpdateUsageReportsPrivacySetting|Administratoren opdaterede indstillingerne for beskyttelse af personlige oplysninger for forbrugsrapporter. |
||||

### <a name="exchange-admin-audit-log"></a>Exchange administratorens overvågningslog

Exchange administrator overvågningslogføring (som som standard er aktiveret i Microsoft 365) logfører en hændelse i overvågningsloggen, når en administrator (eller en bruger, der har fået tildelt administrative tilladelser) foretager en ændring i din Exchange Online organisation. Ændringer, der foretages ved hjælp af Exchange Administration eller ved at køre en cmdlet i Exchange Online PowerShell, logføres i Exchange administratorens overvågningslog. Cmdlet'er, der starter med verberne **Get-**, **Search-eller** **Test,** logføres ikke i overvågningsloggen. Du kan finde flere detaljerede oplysninger om logføring af administratorovervågning i Exchange under [Logføring af administratorrevision](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Nogle Exchange Online cmdlet'er, der ikke er logget på Exchange administratorens overvågningslog (eller i overvågningsloggen). Mange af disse cmdlet'er er relateret til vedligeholdelse af tjenesten Exchange Online og køres af Microsofts datacenterpersonale eller tjenestekonti. Disse cmdlet'er logføres ikke, fordi de ville resultere i et stort antal "støjende" overvågningshændelser. Hvis der er en Exchange Online cmdlet, der ikke overvåges, skal du sende en dcr-anmodning (designændring) til Microsoft Support.

Her er nogle tip til søgning efter Exchange administratoraktiviteter, når du søger i overvågningsloggen:

- Hvis du vil returnere poster fra Exchange administratorens overvågningslog, skal du vælge **Vis resultater for alle aktiviteter** på listen **Aktiviteter**. Brug datoområdefelterne og listen **Brugere** til at indsnævre søgeresultaterne for cmdlet'er, der køres af en bestemt Exchange administrator inden for et bestemt datointerval.

- Hvis du vil have vist hændelser fra Exchange administratorens overvågningslog, skal du klikke på kolonnen **Aktivitet** for at sortere navnene på cmdlet'en i alfabetisk rækkefølge.

- Hvis du vil have oplysninger om, hvilken cmdlet der blev kørt, hvilke parametre og parameterværdier der blev brugt, og hvilke objekter der blev påvirket, kan du eksportere søgeresultaterne ved at vælge indstillingen **Download alle resultater** . Du kan finde flere oplysninger under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

- Du kan også bruge kommandoen `Search-UnifiedAuditLog -RecordType ExchangeAdmin` i Exchange Online PowerShell til kun at returnere overvågningsposter fra Exchange administratorens overvågningslog. Det kan tage op til 30 minutter, efter en Exchange cmdlet køres, før den tilsvarende post i overvågningsloggen returneres i søgeresultaterne. Du kan finde flere oplysninger under [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). Du kan finde oplysninger om eksport af de søgeresultater, der **returneres af Search-UnifiedAuditLog-cmdlet'en**, til en CSV-fil i afsnittet "Tips til eksport og visning af overvågningsloggen" i [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Du kan også få vist hændelser i Exchange administratorens overvågningslog ved hjælp af Exchange Administration eller ved at køre **Search-AdminAuditLog** i Exchange Online PowerShell. Dette er en god måde specifikt at søge efter aktivitet, der udføres af Exchange Online administratorer. Du kan finde instruktioner under:

  - [Vis administratorens overvågningslog](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Vær opmærksom på, at de samme Exchange administratoraktiviteter er logget på både Exchange administratorens overvågningslog og overvågningslog.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Hvad er forskellige Microsoft 365 tjenester, der overvåges i øjeblikket?**

De mest anvendte tjenester som Exchange Online, SharePoint Online, OneDrive for Business, Azure Active Directory, Microsoft Teams, Dynamics 365, Defender for Office 365, og Power BI overvåges. Du kan se en liste over de tjenester, der overvåges, i [starten af denne artikel](search-the-audit-log-in-security-and-compliance.md) .

**Hvilke aktiviteter overvåges af overvågningstjeneste i Microsoft 365?**

Se afsnittet [Overvågede aktiviteter](#audited-activities) i denne artikel for at få en liste over og en beskrivelse af de aktiviteter, der overvåges.

**Hvor lang tid tager det, før en overvågningspost er tilgængelig, når en hændelse er opstået?**

De fleste overvågningsdata er tilgængelige inden for 30 minutter, men det kan tage op til 24 timer, efter en hændelse indtræffer, før den tilsvarende post i overvågningsloggen vises i søgeresultaterne. Se tabellen i afsnittet [Før du søger i overvågningsloggen](#before-you-search-the-audit-log) i denne artikel, der viser, hvor lang tid det tager for hændelser i de forskellige tjenester at være tilgængelige.

**Hvor længe opbevares overvågningsposterne?**

Som tidligere forklaret bevares overvågningsposter for aktiviteter, der udføres af brugere, der har fået tildelt en Office 365 E5- eller Microsoft E5-licens (eller brugere med en Microsoft 365 E5 tilføjelsesprogramlicens) i et år. For alle andre abonnementer, der understøtter samlet overvågningslogføring, bevares overvågningsposter i 90 dage.

**Kan jeg få adgang til overvågningsdataene programmatisk?**

Ja. API'en til administration af Office 365 bruges til at hente overvågningslogfilerne programmatisk.  For at komme i gang skal du se [Kom i gang med Office 365 Management API'er](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Er der andre måder at hente overvågningslogge på end ved hjælp af Security and Compliance Center eller API'en til Office 365 Management Activity?**

Nej. Dette er de eneste to måder at hente data fra overvågningstjeneste på.

**Skal jeg aktivere overvågning individuelt for hver tjeneste, som jeg vil registrere overvågningslogge for?**

I de fleste tjenester aktiveres overvågning som standard, når du først har aktiveret overvågning for din organisation (som beskrevet i afsnittet [Før du søger i overvågningsloggen](#before-you-search-the-audit-log) i denne artikel).

**Understøtter overvågningstjeneste deduplikering af poster?**

Nej. Overvågningstjenestens pipeline er næsten i realtid og kan derfor ikke understøtte deduplikering.

**Hvor gemmes overvågningsdata?**

Vi har i øjeblikket udrulninger af overvågningspipelines i områderne NA (Nordamerika), EMEA (Europa, Mellemøsten og Afrika) og APAC (Asien og Stillehavsområdet). De lejere, der er placeret i disse områder, har deres overvågningsdata gemt i området. For multi-geo-lejere gemmes de overvågningsdata, der indsamles fra alle områder i lejeren, kun i lejerens lokale område. Vi kan dog overføre dataene på tværs af disse områder for belastningsjustering og kun under problemer med livewebstedet. Når vi udfører disse aktiviteter, krypteres de data, der er under overførsel. 

**Er overvågningsdata krypteret?**

Overvågningsdata gemmes i Exchange postkasser (inaktive data) i det samme område, hvor den samlede overvågningspipeline udrulles. Hvilede postkassedata krypteres ikke af Exchange. Kryptering på tjenesteniveau krypterer dog alle postkassedata, fordi Exchange servere i Microsoft-datacentre krypteres via BitLocker. Du kan få flere oplysninger [under Microsoft 365 Encryption for Skype for Business, OneDrive for Business, SharePoint Online og Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Maildata under overførsel krypteres altid.
