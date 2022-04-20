---
title: Søg efter eDiscovery-aktiviteter i overvågningsloggen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 67cc7f42-a53d-4751-b929-6005c80798f7
description: Få mere at vide om, hvilke hændelser der logføres, når brugere, der har fået tildelt eDiscovery-tilladelser, udfører indholdssøgning, eDiscovery (Standard) og eDiscovery-opgaver (Premium) på Microsoft Purview-overholdelsesportalen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 519347ed8f074fc15c8618f6ceb84159314c5915
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941825"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Søg efter eDiscovery-aktiviteter i overvågningsloggen

Indholdssøgning og eDiscovery-relaterede aktiviteter (for Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium)), der udføres i Microsoft Purview-overholdelsesportalen eller ved at køre de tilsvarende PowerShell-cmdlet'er, logføres i overvågningsloggen. Hændelser logføres, når administratorer eller eDiscovery-ledere (eller alle brugere, der har fået tildelt eDiscovery-tilladelser), udfører følgende indholdssøgnings- og eDiscovery-opgaver (Standard) på overholdelsesportalen:
  
- Oprettelse og administration af core- og eDiscovery-sager (Premium)

- Oprettelse, start og redigering af indholdssøgninger

- Udførelse af søgehandlinger, f.eks. visning, eksport og sletning af søgeresultater

- Administration af tilsynsførende og korrektursæt i eDiscovery (Premium)

- Konfiguration af filtrering af tilladelser til indholdssøgning

- Administration af rollen eDiscovery-administrator
  
Du kan finde flere oplysninger om søgning i overvågningsloggen, de nødvendige tilladelser og eksport af søgeresultater under [Søg i overvågningsloggen på overholdelsesportalen](search-the-audit-log-in-security-and-compliance.md).
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Sådan søger og får du vist eDiscovery-aktiviteter

I øjeblikket skal du gøre et par specifikke ting for at få vist eDiscovery-aktiviteter i overvågningsloggen. Sådan gør du.
  
1. Gå til , <https://compliance.microsoft.com> og log på med din arbejds- eller skolekonto.

2. Klik på **Overvåg** i navigationsruden til venstre på overholdelsesportalen.

3. Klik på en eller flere aktiviteter, du vil søge efter, under **eDiscovery-aktiviteter** eller **eDiscovery-aktiviteter (Premium)** på rullelisten **Aktiviteter**.

    > [!NOTE]
    > Rullelisten **Aktiviteter** indeholder også en gruppe aktiviteter med navnet **eDiscovery-cmdlet-aktiviteter** , der returnerer poster fra cmdlet-overvågningsloggen.
  
4. Vælg et dato- og klokkeslætsinterval for at få vist eDiscovery-hændelser, der fandt sted inden for den pågældende periode.

5. I feltet **Brugere** skal du vælge en eller flere brugere, der skal vises søgeresultater for. Lad dette felt være tomt for at returnere poster for alle brugere.

6. Klik på **Søg** for at køre søgningen ved hjælp af dine søgekriterier.

7. Når søgeresultaterne vises, kan du klikke på **Filtrer resultater** for at filtrere eller sortere de resulterende aktivitetsposter. Du kan desværre ikke bruge filtrering til eksplicit at udelade visse aktiviteter. 

8. Hvis du vil have vist oplysninger om en aktivitet, skal du klikke på aktivitetsposten på listen over søgeresultater. 

    Siden **Detaljer** vises, der indeholder de detaljerede egenskaber fra hændelsesposten. Klik på **Flere oplysninger** for at få vist flere oplysninger. Du kan finde en beskrivelse af disse egenskaber i afsnittet [Detaljerede egenskaber for eDiscovery-aktiviteter](#detailed-properties-for-ediscovery-activities) .

9. Hvis du vil, kan du eksportere søgeresultaterne i overvågningsloggen til en CSV-fil og derefter bruge funktionen Excel Power Query til at formatere og filtrere disse poster. Du kan finde flere oplysninger under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>eDiscovery-aktiviteter

I følgende tabel beskrives de indholdssøgnings- og eDiscovery-aktiviteter (Standard), der logføres, når en administrator eller eDiscovery-leder udfører en eDiscovery-relateret aktivitet ved hjælp af overholdelsesportalen. Nogle aktiviteter, der udføres i eDiscovery (Premium), returneres muligvis, når du søger efter aktiviteter på denne liste.
  
> [!NOTE]
> De eDiscovery-aktiviteter, der er beskrevet i dette afsnit, indeholder lignende oplysninger som de eDiscovery-cmdlet-aktiviteter, der er beskrevet i næste afsnit. Vi anbefaler, at du bruger de eDiscovery-aktiviteter, der er beskrevet i dette afsnit, fordi de vises i søgeresultaterne i overvågningsloggen inden for 30 minutter. Det kan tage op til 24 timer, før eDiscovery-cmdlet-aktiviteter vises i søgeresultaterne i overvågningsloggen.
  
|**Fuldt navn**|**Drift**|**Tilsvarende cmdlet**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|Føjede medlem til eDiscovery-sag  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |En bruger blev tilføjet som medlem af en eDiscovery-sag. Som medlem af en sag kan en bruger udføre forskellige sagsrelaterede opgaver, afhængigt af om brugeren har fået tildelt de nødvendige tilladelser.  <br/> |
|Ændret indholdssøgning  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |En eksisterende indholdssøgning blev ændret. Ændringer kan omfatte tilføjelse eller fjernelse af indholdsplaceringer eller redigering af søgeforespørgslen.  <br/> |
|Har ændret eDiscovery-administratormedlemskab  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Listen over eDiscovery-administratorer i din organisation blev ændret. Denne aktivitet logføres, når listen over eDiscovery-administratorer erstattes med en gruppe nye brugere. Hvis en enkelt bruger tilføjes eller fjernes, logføres handlingen CaseAdminAdded.  <br/> |
|Ændrede eDiscovery-sag  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |En eDiscovery-sag blev ændret. Ændringerne omfatter lukning af en åben sag eller genåbning af en lukket sag.  <br/> |
|Har ændret eDiscovery-sagsmedlemskab  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |Medlemskabslisten for en eDiscovery-sag blev ændret. Denne aktivitet logføres, når alle medlemmer erstattes med en gruppe nye brugere. Hvis et enkelt medlem tilføjes eller fjernes, logføres handlingen CaseMemberAdded eller CaseMemberRemoved.  <br/> |
|Ændrede filteret for søgetilladelser  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Et filter for søgetilladelser blev ændret.  <br/> |
|Ændrede søgeforespørgslen for eDiscovery-sag i venteposition  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, blev ændret. Mulige ændringer omfatter redigering af forespørgslen eller datointervallet for en forespørgselsbaseret venteposition.  <br/> |
|Eksempelelementet til indholdssøgning er downloadet  <br/> |PreviewItemDownloaded  <br/> |NIELSEN  <br/> |En bruger har downloadet et element til sin lokale computer (ved at klikke på linket **Download oprindeligt element** ), når søgeresultaterne vises.  <br/> |
|Visningselement for indholdssøgning angivet  <br/> |PreviewItemListed  <br/> |NIELSEN  <br/> |En bruger har klikket på **Vis søgeresultater** for at få vist siden med eksempelsøgeresultater, som viser op til 1.000 elementer fra resultaterne af en søgning.  <br/> |
|Visning af eksempelelement til indholdssøgning  <br/> |PreviewItemRendered  <br/> |NIELSEN  <br/> |En eDiscovery-leder fik vist et element ved at klikke på det, når søgeresultaterne vises.  <br/> |
|Oprettelse af indholdssøgning  <br/> |Søgeoprettelse  <br/> |New-ComplianceSearch  <br/> |Der blev oprettet en ny indholdssøgning.  <br/> |
|Oprettede eDiscovery-administrator  <br/> |CaseAdminAdded  <br/> |Tilføj eDiscoveryCaseAdmin  <br/> |En bruger blev tilføjet som eDiscovery-administrator i organisationen.  <br/> |
|Oprettede eDiscovery-sag  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Der blev oprettet en eDiscovery-sag. Når der oprettes en sag, skal du kun give den et navn. Andre sagsrelaterede opgaver, f.eks. tilføjelse af medlemmer, oprettelse af ventepositioner og oprettelse af indholdssøgninger, der er knyttet til sagen, medfører, at der logføres yderligere hændelser.  <br/> |
|Oprettede filter for søgetilladelser  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Der blev oprettet et filter for søgetilladelser.  <br/> |
|Oprettede søgeforespørgsel for eDiscovery-sag i venteposition  <br/> |Ventepositionen er blevet genoprettet  <br/> |New-CaseHoldRule  <br/> |Der blev oprettet en forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag.  <br/> |
|Slettede indholdssøgning  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |En eksisterende indholdssøgning blev slettet.  <br/> |
|Slettede eDiscovery-administrator  <br/> |CaseAdminRemoved  <br/> |Fjern eDiscoveryCaseAdmin  <br/> |En eDiscovery-administrator blev slettet fra din organisation.  <br/> |
|Slettede eDiscovery-sag  <br/> |Sagflytning  <br/> |Remove-ComplianceCase  <br/> |En eDiscovery-sag blev slettet. Alle ventepositioner, der er knyttet til sagen, skal fjernes, før sagen kan slettes.  <br/> |
|Filter for slettede søgetilladelser  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Et filter for søgetilladelser blev slettet.  <br/> |
|Slettede søgeforespørgsel for eDiscovery-sag i venteposition  <br/> |Ventepositionflytning  <br/> |Remove-CaseHoldRule  <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, blev slettet. Hvis du fjerner forespørgslen fra ventepositionen, er det ofte resultatet af at slette en venteposition. Når en ventepositions- eller ventepositionsforespørgsel slettes, frigives de indholdsplaceringer, der var i venteposition.  <br/> |
|Downloadet eksport af indholdssøgning  <br/> |SearchExportDownloaded  <br/> |NIELSEN  <br/> |En bruger har downloadet resultaterne af en indholdssøgning til deres lokale computer. En **startet eksport af indholdssøgningsaktivitet** skal startes, før søgeresultaterne kan downloades.  <br/> |
|Resultater af indholdssøgning, der er forhåndsvist  <br/> |Søgning er gennemset  <br/> |NIELSEN  <br/> |En bruger har forhåndsvist resultaterne af en indholdssøgning.  <br/> |
|Slettede resultater af indholdssøgning  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |En bruger fjernede resultaterne af en indholdssøgning ved at køre kommandoen **New-ComplianceSearchAction -Purge** .  <br/> |
|Fjernet analyse af indholdssøgning  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |En forberedelseshandling for indholdssøgning (til forberedelse af søgeresultater til eDiscovery (Premium)) blev slettet. Hvis forberedelseshandlingen var mindre end to uger gammel, blev de søgeresultater, der blev forberedt til eDiscovery (Premium), slettet fra Microsoft Azure lagerområde. Hvis forberedelseshandlingen var ældre end 2 uger, angiver denne hændelse, at det kun er den tilsvarende forberedelseshandling, der blev slettet.  <br/> |
|Eksport af indholdssøgning er fjernet  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |En eksporthandling for indholdssøgning blev slettet. Hvis eksporthandlingen var mindre end to uger gammel, blev de søgeresultater, der blev overført til Microsoft Azure lagerområde, slettet. Hvis eksporthandlingen var ældre end 2 uger, angiver denne hændelse, at det kun er den tilsvarende eksporthandling, der blev slettet.  <br/> |
|Fjernede medlem fra eDiscovery-sag  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |En bruger blev fjernet som medlem af en eDiscovery-sag.  <br/> |
|Fjernede eksempelresultaterne af indholdssøgningen  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |En visningshandling for indholdssøgning blev slettet.  <br/> |
|Fjernede den slettede handling, der blev udført på indholdssøgning  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |En handling til sletning af indholdssøgning blev slettet.  <br/> |
|Fjernede søgerapport  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |En eksportrapporthandling for indholdssøgning blev slettet.  <br/> |
|Startet analyse af indholdssøgning  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Resultaterne af en indholdssøgning blev forberedt til analyse i eDiscovery (Premium).  <br/> |
|Indholdssøgning er startet  <br/> |Søg, der erstartet  <br/> |Start-ComplianceSearch  <br/> |En indholdssøgning blev startet. Når du opretter eller ændrer en indholdssøgning ved hjælp af overholdelsesportalen, startes søgningen automatisk.<br/> |
|Begyndte eksport af indholdssøgning  <br/> |Søg eksporteret  <br/> |New-ComplianceSearchAction  <br/> |En bruger eksporterede resultaterne af en indholdssøgning.  <br/> |
|Begyndte at eksportere rapporten  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |En bruger eksporterede en indholdssøgningsrapport.  <br/> |
|Stoppede indholdssøgning  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |En bruger har stoppet en indholdssøgning.  <br/> |
|(ingen)|CaseViewed|Get-ComplianceCase|En bruger fik vist en eDiscovery-sag (Standard) i Overholdelsescenter. Overvågningsposten for denne hændelse indeholder navnet på den sag, der blev vist. |
|(ingen)|SearchViewed|Get-ComplianceSearch|En bruger fik vist en indholdssøgning i Overholdelsescenter ved at få adgang til søgningen under fanen **Søgninger** i en eDiscovery(Standard)-sag eller ved at få adgang til den på siden **indholdssøgning** . Overvågningsposten for denne hændelse indeholder id'et for den søgning, der blev vist.|
|(ingen)|ViewedSearchExported|Get-ComplianceSearchAction -Eksportér|En bruger fik vist en eksport af indholdssøgning i Overholdelsescenter ved at få adgang til eksporten under fanen **Eksporter** på **siden Indholdssøgning** . Denne aktivitet logføres også, når en bruger får vist en eksport, der er knyttet til en eDiscovery-sag (Standard).|
|(ingen)|ViewedSearchPreviewed|Get-ComplianceSearchAction – eksempelvisning|En bruger har forhåndsvist resultaterne af en indholdssøgning i Overholdelsescenter. Denne aktivitet logføres også, når en bruger får vist resultaterne af en søgning, der er knyttet til en eDiscovery-sag (Standard).|
|||||
  
## <a name="ediscovery-premium-activities"></a>eDiscovery-aktiviteter (Premium)

I følgende tabel beskrives de eDiscovery-aktiviteter (Premium), der logføres i overvågningsloggen. Disse aktiviteter kan bruges til at hjælpe dig med at spore forløbet af aktiviteter i en eDiscovery-sag (Premium).

|**Fuldt navn**|**Drift**|**Beskrivelse**|
|:-----|:-----|:-----|
|Data er føjet til et andet korrektursæt|AddWorkingSetQueryToWorkingSet|Brugeren har føjet dokumenter fra ét korrektursæt til et andet korrektursæt.|
|Tilføjede data til gennemsynssættet|AddQueryToWorkingSet|Brugeren har føjet søgeresultaterne fra en indholdssøgning, der er knyttet til en eDiscovery-sag (Premium), til et korrektursæt.|
|Tilføjede data, der ikke Microsoft 365, for at gennemse sættet|AddNonOffice365DataToWorkingSet|Brugeren føjede ikke-Microsoft 365 data til et korrektursæt.|
|Tilføjede afhjælpede dokumenter for at gennemse sættet|AddRemediatedData|Brugeren overfører dokumenter, der havde indekseringsfejl, som var rettet til et korrektursæt.|
|Analyserede data i korrektursæt|RunAlgo|Brugeren kørte analyser på dokumenterne i et korrektursæt.|
|Anmærkede dokumenter i korrektursæt|Anmærkdokument|Brugeren anmærkede et dokument i et korrektursæt. Anmærkning omfatter ændring af indhold i et dokument.|
|Sammenlignede indlæsningssæt|LoadComparisonJob|Brugeren sammenlignede to forskellige indlæsningssæt i et korrektursæt. Et indlæsningssæt er, når data fra en indholdssøgning, der er knyttet til sagen, føjes til et korrektursæt.|
|Konverterede redigerede dokumenter til PDF|BurnJob|Brugeren konverterede alle de redigerede dokumenter i et korrektursæt til PDF-filer.|
|Oprettede korrektursæt|Opretarbejdssæt|Brugeren har oprettet et korrektursæt.|
|Oprettelse af søgning i gennemsynssæt|CreateWorkingSetSearch|Brugeren har oprettet en søgeforespørgsel, der søger i dokumenterne i et korrektursæt.|
|Oprettet mærke|CreateTag|Brugeren har oprettet en kodegruppe i et korrektursæt. En kodegruppe kan indeholde en eller flere underordnede mærker. Disse mærker bruges derefter til at mærke dokumenter i korrektursættet.|
|Slettede søgning i gennemsynssæt|DeleteWorkingSetSearch|Brugeren slettede en søgeforespørgsel i et korrektursæt.|
|Slettet mærke|DeleteTag|Brugeren slettede et mærke eller en kodegruppe i et korrektursæt.|
|Downloadet dokument|DownloadDocument|Brugeren har downloadet et dokument fra et korrektursæt.|
|Mærket Redigeret|UpdateTag|Brugeren har ændret et mærke i et korrektursæt.|
|Eksporterede dokumenter fra korrektursæt|Eksportjob|Brugeren eksporterede dokumenter fra et korrektursæt.|
|Indstilling for ændret sag|UpdateCaseSettings|Brugeren ændrede indstillingerne for en sag. Sagsindstillinger omfatter sagsoplysninger, adgangstilladelser og indstillinger, der styrer søge- og analysefunktionsmåden.|
|Ændret søgning i gennemsynssæt|UpdateWorkingSetSearch|Brugeren redigerede en søgeforespørgsel i et korrektursæt.|
|Søgning i gennemset sæt|PreviewWorkingSetSearch|Brugeren har forhåndsvist resultaterne af en søgeforespørgsel i et korrektursæt.|
|Afhjælpede fejldokumenter|ErrorRemediationJob|Brugeren retter filer, der indeholdt indekseringsfejl.|
|Markeret dokument|TagFiles|Brugeren mærker et dokument i et korrektursæt.|
|Mærkede resultater af en forespørgsel|TagJob|Brugeren mærker alle de dokumenter, der opfylder kriterierne for søgeforespørgslen i et gennemsynssæt.|
|Fik vist dokumentet i korrektursæt|ViewDocument|Brugeren fik vist et dokument i et korrektursæt.|
|||

## <a name="ediscovery-cmdlet-activities"></a>eDiscovery-cmdlet-aktiviteter

I følgende tabel vises de cmdlet-overvågningslogposter, der logføres, når en administrator eller bruger udfører en eDiscovery-relateret aktivitet ved hjælp af overholdelsescenter eller ved at køre den tilsvarende cmdlet i Security & Compliance Center PowerShell. De detaljerede oplysninger i overvågningslogposten er forskellige for de cmdlet-aktiviteter, der er angivet i denne tabel, og de eDiscovery-aktiviteter, der er beskrevet i det forrige afsnit.
  
Som tidligere nævnt kan det tage op til 24 timer, før eDiscovery-cmdlet-aktiviteter vises i søgeresultaterne i overvågningsloggen.
  
> [!TIP]
> Cmdlet'erne i kolonnen **Operation** i følgende tabel er sammenkædet med det tilsvarende emne i Hjælp-cmdlet'en på TechNet. Gå til emnet i Hjælp-cmdlet'en for at få en beskrivelse af de tilgængelige parametre for hver cmdlet. Parameteren og parameterværdien, der blev brugt sammen med en cmdlet, er inkluderet i posten i overvågningsloggen for hver eDiscovery-cmdlet-aktivitet, der er logført. 
  
|**Fuldt navn**|**Handling (cmdlet)**|**Beskrivelse**|
|:-----|:-----|:-----|
|Oprettede venteposition i eDiscovery-sag  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Der blev oprettet en venteposition for en eDiscovery-sag. Der kan oprettes en venteposition med eller uden at angive en indholdskilde. Hvis der er angivet indholdskilder, identificeres de i posten i overvågningsloggen.  <br/> |
|Slettede venteposition fra eDiscovery-sag  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |En venteposition, der er knyttet til en eDiscovery-sag, blev slettet. Hvis du sletter en venteposition, frigives alle indholdsplaceringer fra ventepositionen. Sletning af ventepositionen resulterer også i sletning af de regler for sags venteposition, der er knyttet til ventepositionen (se **Fjern-CaseHoldRule** nedenfor).  <br/> |
|Ændret venteposition i eDiscovery-sag  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |En venteposition, der er knyttet til en eDiscovery, blev ændret. Mulige ændringer omfatter tilføjelse eller fjernelse af indholdsplaceringer eller deaktivering af ventepositionen.  <br/> |
|Oprettede søgeforespørgsel for eDiscovery-sag i venteposition  <br/> |[Ny-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |Der blev oprettet en forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag.  <br/> |
|Slettede søgeforespørgsel for eDiscovery-sag i venteposition  <br/> |[Fjern-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, blev slettet. Hvis du fjerner forespørgslen fra ventepositionen, er det ofte resultatet af at slette en venteposition. Når en ventepositions- eller ventepositionsforespørgsel slettes, frigives de indholdsplaceringer, der var i venteposition.  <br/> |
|Ændrede søgeforespørgslen for eDiscovery-sag i venteposition  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, blev ændret. Mulige ændringer omfatter redigering af forespørgslen eller datointervallet for en forespørgselsbaseret venteposition.  <br/> |
|Oprettede eDiscovery-sag  <br/> |[Sag om ny overholdelse](/powershell/module/exchange/new-compliancecase) <br/> |Der blev oprettet en eDiscovery-sag. Når der oprettes en sag, skal du kun give den et navn. Andre sagsrelaterede opgaver, f.eks. tilføjelse af medlemmer, oprettelse af ventepositioner og oprettelse af indholdssøgninger, der er knyttet til sagen, medfører, at der logføres yderligere hændelser.  <br/> |
|Slettede eDiscovery-sag  <br/> |[Fjern overholdelse af regler og standarderCase](/powershell/module/exchange/remove-compliancecase) <br/> |En eDiscovery-sag blev slettet. Alle ventepositioner, der er knyttet til sagen, skal fjernes, før sagen kan slettes.  <br/> |
|Ændrede eDiscovery-sag  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |En eDiscovery-sag blev ændret. Ændringerne omfatter lukning af en åben sag eller genåbning af en lukket sag.  <br/> |
|Føjede medlem til eDiscovery-sag  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |En bruger blev tilføjet som medlem af en eDiscovery-sag. Som medlem af en sag kan en bruger udføre forskellige sagsrelaterede opgaver, afhængigt af om brugeren har fået tildelt de nødvendige tilladelser.  <br/> |
|Fjernede medlem fra eDiscovery-sag  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |En bruger blev fjernet som medlem af en eDiscovery-sag.  <br/> |
|Har ændret eDiscovery-sagsmedlemskab  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |Medlemskabslisten for en eDiscovery-sag blev ændret. Denne aktivitet logføres, når alle medlemmer erstattes med en gruppe nye brugere. Hvis et enkelt medlem tilføjes eller fjernes, logføres handlingen **Add-ComplianceCaseMember** eller **Remove-ComplianceCaseMember** .  <br/> |
|Oprettelse af indholdssøgning  <br/> |[Nyt overholdelsessøg](/powershell/module/exchange/new-compliancesearch) <br/> |Der blev oprettet en ny indholdssøgning.  <br/> |
|Slettede indholdssøgning  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |En eksisterende indholdssøgning blev slettet.  <br/> |
|Ændret indholdssøgning  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |En eksisterende indholdssøgning blev ændret. Ændringer kan omfatte tilføjelse eller fjernelse af indholdsplaceringer, der søges i, og redigering af søgeforespørgslen.  <br/> |
|Indholdssøgning er startet  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |En indholdssøgning blev startet. Når du opretter eller ændrer en indholdssøgning ved hjælp af GUI for Overholdelsescenter, startes søgningen automatisk. Hvis du opretter eller ændrer en søgning ved hjælp af **New-ComplianceSearch** - eller **Set-ComplianceSearch-cmdlet'en** , skal du køre **Start-ComplianceSearch-cmdlet'en** for at starte søgningen.  <br/> |
|Stoppede indholdssøgning  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |En indholdssøgning, der kørte, blev stoppet.  <br/> |
|Handlingen Oprettet indholdssøgning  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Der blev oprettet en indholdssøgningshandling. Handlinger til indholdssøgning omfatter visning af søgeresultater, eksport af søgeresultater, forberedelse af søgeresultater til analyse i eDiscovery (Premium) og permanent sletning af elementer, der opfylder søgekriterierne i en indholdssøgning.  <br/> |
|Slettede indholdssøgningshandling  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |En indholdssøgningshandling blev slettet.  <br/> |
|Oprettede filter for søgetilladelser  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Der blev oprettet et filter for søgetilladelser.  <br/> |
|Filter for slettede søgetilladelser  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Et filter for søgetilladelser blev slettet.  <br/> |
|Ændrede filteret for søgetilladelser  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Et filter for søgetilladelser blev ændret.  <br/> |
|Oprettede eDiscovery-administrator  <br/> |[Tilføj eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |En bruger blev tilføjet som eDiscovery-administrator i din organisation.  <br/> |
|Slettede eDiscovery-administrator  <br/> |[Fjern eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |En eDiscovery-administrator blev slettet fra din organisation.  <br/> |
|Har ændret eDiscovery-administratormedlemskab  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Listen over eDiscovery-administratorer i din organisation blev ændret. Denne aktivitet logføres, når listen over eDiscovery-administratorer erstattes med en gruppe nye brugere. Hvis en enkelt bruger tilføjes eller fjernes, logføres handlingen **Add-eDiscoveryCaseAdmin** eller **Remove-eDiscoveryCaseAdmin** .  <br/> |
|(ingen)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Denne aktivitet logføres, når en bruger får vist en liste over sager med eDiscovery (Standard) eller eDiscovery (Premium). Denne aktivitet logføres også, når en bruger får vist en bestemt sag i eDiscovery (Standard). Når en bruger får vist en bestemt sag, indeholder overvågningsposten id'et for den sag, der blev vist. Hvis brugeren kun fik vist en liste over sager, indeholder overvågningsposten ikke en sagsidentitet.|
|(ingen)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Denne aktivitet logføres, når en bruger får vist en liste over indholdssøgninger eller søgninger, der er knyttet til en eDiscovery-sag (Standard). Denne aktivitet logføres også, når en bruger får vist en bestemt indholdssøgning eller får vist en bestemt søgning, der er knyttet til en eDiscovery-sag (Standard). Når en bruger får vist en bestemt søgning, indeholder overvågningsposten identiteten for den søgning, der blev vist. Hvis brugeren kun fik vist en liste over søgninger, indeholder overvågningsposten ikke en søgeidentitet.
|(ingen)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Denne aktivitet logføres, når en bruger får vist en liste over søgehandlinger for overholdelse (f.eks. eksporter, prøveversioner eller sletninger) eller handlinger, der er knyttet til en eDiscovery-sag (Standard). Denne aktivitet logføres også, når en bruger får vist en bestemt søgehandling for overholdelse af angivne standarder (f.eks. en eksport) eller får vist en bestemt handling, der er knyttet til en eDiscovery-sag (Standard). Når en bruger får vist en søgehandling, indeholder overvågningsposten identiteten for den søgehandling, der blev vist. Hvis brugeren kun fik vist en liste over handlinger, indeholder overvågningsposten ikke en handlingsidentitet.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Detaljerede egenskaber for eDiscovery-aktiviteter

I følgende tabel beskrives de egenskaber, der er inkluderet på pop op-siden for en eDiscovery-aktivitet, der er angivet i søgeresultaterne. Disse egenskaber er også inkluderet i CSV-filen, når du eksporterer søgeresultaterne i overvågningsloggen. En overvågningslogpost for en eDiscovery-aktivitet indeholder ikke alle de detaljerede egenskaber, der er angivet nedenfor.
  
> [!TIP]
> Når du eksporterer søgeresultaterne, indeholder CSV-filen en kolonne med navnet **AudtiData**, som indeholder de detaljerede egenskaber, der er beskrevet i følgende tabel i en egenskab med flere værdier. Du kan bruge funktionen Power Query i Excel til at opdele denne kolonne i flere kolonner, så hver egenskab har sin egen kolonne. Det giver dig mulighed for at sortere og filtrere på en eller flere af disse egenskaber. Du kan finde flere oplysninger i afsnittet "Eksportér søgeresultaterne til en fil" i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Ejendom**|**Beskrivelse**|
|:-----|:-----|
|Tilfælde  <br/> |Id'et (GUID) for den eDiscovery-sag, der blev oprettet, ændret eller slettet.  <br/> |
|Klientprogram  <br/> |eDiscovery-cmdlet-aktiviteter har værdien **EMC** for denne egenskab. Dette angiver, at aktiviteten blev udført ved hjælp af GUI for overholdelsescenter eller kørsel af cmdlet'en i PowerShell.  <br/> |
|ClientIP  <br/> |IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.  <br/> |
|ClientRequestId  <br/> | Denne egenskab er typisk tom for eDiscovery-aktiviteter.  <br/> |
|CmdletVersion  <br/> |Buildnummeret for den version af Overholdelsescenter, der kører i din organisation.  <br/> |
|Oprettelsestid  <br/> |Den dato og det klokkeslæt i UTC (Coordinated Universal Time), hvor eDiscovery-aktiviteten blev fuldført.  <br/> |
|Effektiv organisation  <br/> |Navnet på Microsoft 365-organisationen.  <br/> |
|ExchangeLocations  <br/> |De Exchange Online postkasser, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|Udeladelser  <br/> |Postkasser eller webstedsplaceringer, der er udelukket fra en indholdssøgning eller en venteposition i en eDiscovery-sag.  <br/> |
|Udvidedeegenskaber  <br/> |Yderligere egenskaber fra en indholdssøgning, en indholdssøgningshandling eller venteposition i en eDiscovery-sag, f.eks. objekt-GUID og de tilsvarende cmdlet- og cmdlet-parametre, der blev brugt, da aktiviteten blev udført.  <br/> |
|Id  <br/> |Id'et for rapportposten. Id'et identificerer entydigt overvågningslogposten.  <br/> |
|Ikke-PIIParameters  <br/> |En liste over de parametre (uden nogen værdier), der blev brugt sammen med den cmdlet, der er identificeret i egenskaben Operation. De parametre, der er angivet i denne egenskab, er de samme som dem, der er angivet i egenskaben Parametre.  <br/> |
|Objectid  <br/> |OBJEKTETs GUID eller navn (f.eks. en indholdssøgning eller en eDiscovery (Standard)-sag, der blev oprettet, tilgået, ændret eller slettet af den aktivitet, der er angivet i egenskaben Operation. Dette objekt identificeres også i kolonnen Element i søgeresultaterne i overvågningsloggen.  <br/> |
|Objecttype  <br/> |Den type eDiscovery-objekt, som brugeren har oprettet, slettet eller ændret. f.eks. en indholdssøgningshandling (prøveversion, eksport eller fjernelse), en eDiscovery-sag eller en indholdssøgning.  <br/> |
|Drift  <br/> |Navnet på den handling, der svarer til den eDiscovery-aktivitet, der blev udført.  <br/> |
|Organisations-id  <br/> |GUID'et for din Microsoft 365 organisation.  <br/> |
|Parametre  <br/> |Navnet og værdien for de parametre, der blev brugt sammen med den tilsvarende cmdlet.  <br/> |
|PublicFolderLocations  <br/> |De offentlige mappeplaceringer i Exchange Online, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|Forespørgsel  <br/> |Den søgeforespørgsel, der er knyttet til aktiviteten, f.eks. en indholdssøgning eller en forespørgselsbaseret venteposition.  <br/> |
|Posttype  <br/> |Den type handling, der er angivet af posten. Værdien **18** angiver en hændelse, der er relateret til en aktivitet, der er angivet i afsnittet [eDiscovery-cmdletaktiviteter](#ediscovery-cmdlet-activities) . En værdi på **24** angiver en hændelse, der er relateret til en aktivitet, der er angivet i afsnittet [Sådan søger du efter og får vist eDiscovery-aktiviteter](#how-to-search-for-and-view-ediscovery-activities) .  <br/> |
|ResultStatus  <br/> |Angiver, om handlingen (angivet i egenskaben Operation) lykkedes eller ej.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Angiver, at aktiviteten var en hændelse i overholdelsescenter. Alle eDiscovery-aktiviteter har værdien **0** for denne egenskab.  <br/> |
|SharepointLocations  <br/> |De SharePoint Online-websteder, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|Starttidspunkt  <br/> |Den dato og det klokkeslæt i UTC (Coordinated Universal Time), hvor eDiscovery-aktiviteten blev startet.  <br/> |
|Userid  <br/> |Den bruger, der udførte den aktivitet (angivet i egenskaben Operation), som resulterede i, at posten blev logført. Poster for eDiscovery-aktivitet, der udføres af systemkonti (f.eks NT AUTHORITY\SYSTEM), medtages også i overvågningsloggen.  <br/> |
|UserKey  <br/> |Et alternativt id for den bruger, der er identificeret i egenskaben UserId. For eDiscovery-aktiviteter er værdien for denne egenskab typisk den samme som egenskaben UserId.  <br/> |
|UserServicePlan  <br/> |Det abonnement, der bruges af din organisation. Denne egenskab er typisk tom for eDiscovery-aktiviteter.  <br/> |
|UserType  <br/> |Den type bruger, der udførte handlingen. Følgende værdier angiver brugertypen.  <br/> 0 En almindelig bruger. 2 En administrator i din organisation. 3 En Microsoft-datacenteradministrator- eller datacentersystemkonto. 4 En systemkonto. 5 Et program. 6 En tjenesteprincipal. |
|Version  <br/> |Angiver versionsnummeret for den aktivitet (identificeret af egenskaben Operation), der er logført.  <br/> |
|Arbejdsbyrde  <br/> |Den tjeneste, hvor aktiviteten fandt sted. For eDiscovery-aktiviteter er værdien **SecurityComplianceCenter**.  <br/> |
