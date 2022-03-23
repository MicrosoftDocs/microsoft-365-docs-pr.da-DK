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
description: Få mere at vide om, hvilke hændelser der logføres, når brugere, der er tildelt eDiscovery-tilladelser, udfører indholdssøgning, kerne eDiscovery og Advanced eDiscovery opgaver i Microsoft 365 Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eb1a6f1ee0ff9c84f4dbfc7f42427ae9dda499de
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63588944"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Søg efter eDiscovery-aktiviteter i overvågningsloggen

Indholdssøgning og eDiscovery-relaterede aktiviteter (for Core eDiscovery og Advanced eDiscovery), der udføres i Microsoft 365 Overholdelsescenter eller ved at køre de tilsvarende PowerShell-cmdlet'er, logføres i overvågningsloggen. Hændelser logføres, når administratorer eller eDiscovery-ledere (eller enhver bruger, der er tildelt eDiscovery-tilladelser), udfører følgende indholdssøgning og grundlæggende eDiscovery-opgaver i Microsoft 365 Overholdelsescenter:
  
- Oprettelse og administration af kerne- og Advanced eDiscovery sager

- Oprettelse, start og redigering af indholdssøgninger

- Udføre søgehandlinger, f.eks. vise, eksportere og slette søgeresultater

- Administration af ledende og korrekturlæsere i Advanced eDiscovery

- Konfiguration af filtrering af tilladelser for indholdssøgning

- Administrere eDiscovery-administratorrollen
  
Du kan finde flere oplysninger om søgning i overvågningsloggen, de påkrævede tilladelser og eksport af søgeresultater i Søg i [overvågningsloggen i Microsoft 365 Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md).
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Sådan søger du efter og får vist eDiscovery-aktiviteter

I øjeblikket skal du gøre et par specifikke ting for at få vist eDiscovery-aktiviteter i overvågningsloggen. Sådan gør du.
  
1. Gå til og <https://compliance.microsoft.com> log på med din arbejds- eller skolekonto.

2. Klik på Overvågning i venstre navigationsrude Microsoft 365 Overholdelsescenter **navigationsruden**.

3. På **rullelisten Aktiviteter** under **eDiscovery-aktiviteter eller eDiscovery-aktiviteter** **Advanced eDiscovery du** klikke på en eller flere aktiviteter, du vil søge efter.

    > [!NOTE]
    > **Rullelisten** Aktiviteter omfatter også en gruppe af aktiviteter kaldet **eDiscovery-cmdlet-aktiviteter**, der returnerer poster fra cmdlet-overvågningsloggen.
  
4. Vælg en dato og et tidsinterval for at få vist eDiscovery-hændelser, der er opstået inden for den pågældende periode.

5. I feltet **Brugere skal** du vælge en eller flere brugere, der skal vises søgeresultater for. Lad dette felt være tomt for at returnere poster for alle brugere.

6. Klik **på Søg** for at køre søgningen ved hjælp af dine søgekriterier.

7. Når søgeresultaterne vises, kan du klikke på Filtrer resultater **for** at filtrere eller sortere de resulterende aktivitetsposter. Desværre kan du ikke bruge filtrering til udtrykkeligt at udelade visse aktiviteter. 

8. Hvis du vil have vist detaljer om en aktivitet, skal du klikke på aktivitetsposten på listen over søgeresultater. 

    Der **vises** en side med pop op-siden Detaljer, der indeholder de detaljerede egenskaber fra hændelsesposten. Hvis du vil have vist flere oplysninger, skal du **klikke på Flere oplysninger**. Du kan finde en beskrivelse af disse egenskaber i [afsnittet Detaljerede egenskaber for eDiscovery-aktiviteter](#detailed-properties-for-ediscovery-activities) .

9. Hvis du ønsker det, kan du eksportere overvågningsloggens søgeresultater til en CSV-fil og derefter bruge funktionen Excel Power-forespørgsel til at formatere og filtrere disse poster. Få mere at vide under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>eDiscovery-aktiviteter

I følgende tabel beskrives indholdssøgning og kerne eDiscovery-aktiviteter, der logføres, når en administrator eller eDiscovery-leder udfører en eDiscovery-relateret aktivitet ved hjælp af Microsoft 365 Overholdelsescenter. Nogle aktiviteter, der udføres Advanced eDiscovery, kan blive returneret, når du søger efter aktiviteter på denne liste.
  
> [!NOTE]
> De eDiscovery-aktiviteter, der er beskrevet i dette afsnit, giver lignende oplysninger som de eDiscovery-cmdlet-aktiviteter, der er beskrevet i næste afsnit. Vi anbefaler, at du bruger de eDiscovery-aktiviteter, der er beskrevet i dette afsnit, da de vises i overvågningsloggens søgeresultater inden for 30 minutter. Det kan tage op til 24 timer, før eDiscovery-cmdlet-aktiviteter vises i overvågningsloggens søgeresultater.
  
|**Brugervenligt navn**|**Handling**|**Tilsvarende cmdlet**|**Beskrivelse**|
|:-----|:-----|:-----|:-----|
|Medlem føjet til eDiscovery-sag  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |En bruger blev tilføjet som medlem af en eDiscovery-sag. Som medlem af en sag kan en bruger udføre forskellige sagsrelaterede opgaver, afhængigt af om de har fået tildelt de nødvendige tilladelser.  <br/> |
|Ændret indholdssøgning  <br/> |SøgningOpdateret  <br/> |Set-ComplianceSearch  <br/> |En eksisterende indholdssøgning blev ændret. Ændringer kan omfatte at tilføje eller fjerne indholdsplaceringer eller at redigere søgeforespørgslen.  <br/> |
|Ændret eDiscovery-administratormedlemskab  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |Listen over eDiscovery-administratorer i din organisation er blevet ændret. Denne aktivitet logføres, når listen over eDiscovery-administratorer erstattes med en gruppe af nye brugere. Hvis en enkelt bruger tilføjes eller fjernes, logføres handlingen CaseAdminAdded.  <br/> |
|Ændret eDiscovery-sag  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |En eDiscovery-sag blev ændret. Ændringerne omfatter lukning af en åben sag eller genåbning af en lukket sag.  <br/> |
|Ændret medlemskab af eDiscovery-sag  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |Medlemskabslisten for en eDiscovery-sag blev ændret. Denne aktivitet logføres, når alle medlemmer erstattes med en gruppe af nye brugere. Hvis et enkelt medlem tilføjes eller fjernes, logføres handlingen CaseMemberAdded eller CaseMemberRemoved.  <br/> |
|Ændret filter for søgetilladelser  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Et filter for søgetilladelser blev ændret.  <br/> |
|Ændret søgeforespørgsel til eDiscovery-sags venteposition  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, er blevet ændret. Mulige ændringer omfatter redigering af forespørgslen eller datointervallet for en forespørgselsbaseret venteposition.  <br/> |
|Indholdssøgning på eksempelelement hentet  <br/> |PreviewItemDownloaded  <br/> |I/T  <br/> |En bruger har hentet et element til sin lokale computer (ved at klikke på **linket Download det oprindelige** element), når søgeresultaterne vises.  <br/> |
|Liste over indholdssøgningseksempelelement  <br/> |PreviewItemListed  <br/> |I/T  <br/> |En bruger klikkede **på Vis søgeresultater** for at få vist siden med søgeresultater, som viser op til 1.000 elementer fra resultaterne af en søgning.  <br/> |
|Indholdssøgning i eksempelvisning af element vist  <br/> |PreviewItemRendered  <br/> |I/T  <br/> |En eDiscovery-leder har set et element ved at klikke på det, når søgeresultaterne vises.  <br/> |
|Indholdssøgning oprettet  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Der blev oprettet en ny indholdssøgning.  <br/> |
|Oprettet eDiscovery-administrator  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |En bruger blev tilføjet som eDiscovery-administrator i organisationen.  <br/> |
|Oprettet eDiscovery-sag  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Der blev oprettet en eDiscovery-sag. Når der oprettes en sag, behøver du kun at give den et navn. Andre sagsrelaterede opgaver såsom at tilføje medlemmer, oprette ventende funktioner og oprette indholdssøgninger, der er knyttet til sagen, medfører, at der logføres flere hændelser.  <br/> |
|Filter for søgetilladelser oprettet  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Et søgetilladelsesfilter blev oprettet.  <br/> |
|Oprettede søgeforespørgsel til eDiscovery-sags hold  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |Der blev oprettet en forespørgselsbaseret venteposition knyttet til en eDiscovery-sag.  <br/> |
|Slettet indholdssøgning  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |En eksisterende indholdssøgning blev slettet.  <br/> |
|Slettet eDiscovery-administrator  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |En eDiscovery-administrator er blevet slettet fra din organisation.  <br/> |
|Slettet eDiscovery-sag  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |En eDiscovery-sag blev slettet. Eventuelle ventepositioner, der er knyttet til sagen, skal fjernes, før sagen kan slettes.  <br/> |
|Filter for slettede søgetilladelser  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Et filter for søgetilladelser er blevet slettet.  <br/> |
|Slettede søgeforespørgsel til eDiscovery-sags hold  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, er blevet slettet. At fjerne forespørgslen fra ventepositionen er ofte resultatet af at slette en venteposition. Når en ventepositions- eller ventepositionsforespørgsel slettes, frigives de indholdsplaceringer, der var i venteposition.  <br/> |
|Downloadet eksport af indholdssøgning  <br/> |SearchExportDownloaded  <br/> |I/T  <br/> |En bruger hentede resultaterne af en indholdssøgning til sin lokale computer. En **startet eksport af indholdssøgningsaktivitet** skal startes, før søgeresultaterne kan downloades.  <br/> |
|Viste resultater af indholdssøgning  <br/> |Søgevisning  <br/> |I/T  <br/> |En bruger har gennemset resultaterne af en indholdssøgning.  <br/> |
|Fjernede resultater af indholdssøgning  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |En bruger har fjernet resultaterne af en indholdssøgning ved at køre kommandoen **New-ComplianceSearchAction -Tømning** .  <br/> |
|Analyse af indholdssøgning fjernet  <br/> |FjernedeSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |En handling til forberedelse af indholdssøgning (for at forberede søgeresultaterne Advanced eDiscovery søgning) blev slettet. Hvis forberedelseshandlingen var mindre end to uger gammel, slettes søgeresultaterne, der er forberedt til Advanced eDiscovery fra den Microsoft Azure lagringsområde. Hvis forberedelseshandlingen var ældre end 2 uger, indikerer denne hændelse, at kun den tilsvarende forberedelseshandling blev slettet.  <br/> |
|Eksport af indholdssøgning fjernet  <br/> |FjernedeSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |En eksporthandling for indholdssøgning er blevet slettet. Hvis eksporthandlingen var mindre end to uger gammel, slettes de søgeresultater, der blev overført til Microsoft Azure på lagerområdet. Hvis eksporthandlingen var ældre end 2 uger, indikerer denne hændelse, at kun den tilsvarende eksporthandling blev slettet.  <br/> |
|Medlem fjernet fra eDiscovery-sag  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |En bruger blev fjernet som medlem af en eDiscovery-sag.  <br/> |
|Vis eksempelresultater for indholdssøgning fjernet  <br/> |FjernetSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |En handling til forhåndsvisning af indholdssøgning er blevet slettet.  <br/> |
|Fjernede handlingen tømning, der blev udført på indholdssøgning  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |En handling med sletning af indholdssøgning er blevet slettet.  <br/> |
|Søgerapport fjernet  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |En rapporthandling for eksport af indholdssøgning er blevet slettet.  <br/> |
|Startet analyse af indholdssøgning  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Resultaterne af en indholdssøgning er forberedt til analyse i Advanced eDiscovery.  <br/> |
|Startet indholdssøgning  <br/> |SøgStartet  <br/> |Start-ComplianceSearch  <br/> |En indholdssøgning blev startet. Når du opretter eller ændrer en indholdssøgning ved hjælp Microsoft 365 Overholdelsescenter søgefeltet, startes søgningen automatisk.<br/> |
|Eksport af indholdssøgning startet  <br/> |SøgEkporteret  <br/> |New-ComplianceSearchAction  <br/> |En bruger eksporterede resultaterne af en indholdssøgning.  <br/> |
|Eksporteret rapport startet  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |En bruger eksporterede en rapport for indholdssøgning.  <br/> |
|Stoppet indholdssøgning  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |En bruger stoppede en indholdssøgning.  <br/> |
|(ingen)|CaseViewed|Get-ComplianceCase|En bruger så en Core eDiscovery-sag i overholdelsescenteret. Overvågningsposten for denne hændelse indeholder navnet på den sag, der blev vist. |
|(ingen)|SearchViewed|Get-ComplianceSearch|En bruger har set en indholdssøgning i overholdelsescenteret ved at få adgang  til søgningen under fanen Søgninger i en core eDiscovery-sag eller ved at få adgang til den på siden **Indholdssøgning**. Overvågningsposten for denne hændelse omfatter identiteten af den søgning, der blev vist.|
|(ingen)|VistSøgningEkporteret|Get-ComplianceSearchAction -Eksportér|En bruger har fået vist en eksport af indholdssøgning i overholdelsescenteret ved at åbne **eksporten på fanen** Eksporter på **siden Indholdssøgning** . Denne aktivitet logføres også, når en bruger får en eksport, der er knyttet til en central eDiscovery-sag.|
|(ingen)|VistSøgning VistForsynet|Get-ComplianceSearchAction -Preview|En bruger har forhåndsvist resultaterne af en indholdssøgning i overholdelsescenteret. Denne aktivitet logføres også, når en bruger får vist resultaterne af en søgning, der er knyttet til en Core eDiscovery-sag.|
|||||
  
## <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery aktiviteter

I følgende tabel beskrives de Advanced eDiscovery, der er logført i overvågningsloggen. Disse aktiviteter kan bruges til at hjælpe dig med at spore forløbet af aktiviteten i en Advanced eDiscovery sag.

|**Brugervenligt navn**|**Handling**|**Beskrivelse**|
|:-----|:-----|:-----|
|Tilføjede data i et andet korrektursæt|AddWorkingSetQueryToWorkingSet|Brugeren har tilføjet dokumenter fra ét korrektursæt til et andet korrektursæt.|
|Tilføjede data til gennemsynssættet|AddQueryToWorkingSet|Brugeren har føjet søgeresultaterne fra en indholdssøgning, der er knyttet Advanced eDiscovery en sag, til et gennemsynssæt.|
|Tilføjede ikke-Microsoft 365 til gennemsynssættet|AddNonOffice365DataToWorkingSet|Brugeren har føjet Microsoft 365 data til et korrektursæt.|
|Tilføjede afhjælpede dokumenter til gennemsyn af sæt|AddRemediatedData|Brugeren overfører dokumenter, der havde indeksfejl, som blev rettet i et gennemsynssæt.|
|Analyserede data i korrektursæt|RunAlgo|Brugeren kørte analyser på dokumenterne i et gennemsynssæt.|
|Anmærkninger i korrektursæt|AnnotateDocument|Brugeren anmærkede et dokument i et korrektursæt. Anmærkning omfatter at skrive indhold i et dokument igen.|
|Sammenlignede indlæsningssæt|LoadComparisonJob|Brugeren sammenlignede to forskellige indlæsningssæt i et korrektursæt. Et indlæsningssæt er, når data fra en indholdssøgning, der er knyttet til sagen, føjes til et gennemsynssæt.|
|Konverterede dokumenter, der er redigeret på ny, til PDF|BurnJob|Brugeren har konverteret alle dokumenter, der er redigeret igen, i et gennemsynssæt til PDF-filer.|
|Oprettet korrektursæt|CreateWorkingSet|Brugeren har oprettet et korrektursæt.|
|Oprettede søgning efter gennemsynssæt|CreateWorkingSetSearch|Brugeren har oprettet en søgeforespørgsel, der søger i dokumenterne i et gennemsynssæt.|
|Oprettet mærke|CreateTag|Brugeren oprettede en mærkegruppe i et korrektursæt. En mærkegruppe kan indeholde et eller flere underordnede mærker. Disse mærker bruges derefter til at mærke dokumenter i korrektursættet.|
|Søgning i gennemsynssæt slettet|DeleteWorkingSetSearch|Brugeren har slettet en søgeforespørgsel i et gennemsynssæt.|
|Slettet mærke|DeleteTag|Brugeren har slettet et mærke eller en mærkegruppe i et korrektursæt.|
|Hentet dokument|DownloadDocument|Brugeren hentede et dokument fra et korrektursæt.|
|Redigeret mærke|UpdateTag|Brugeren har ændret et mærke i et korrektursæt.|
|Eksporterede dokumenter fra korrektursæt|ExportJob|Bruger eksporterede dokumenter fra et korrektursæt.|
|Indstilling for ændring af store og små bogstaver|UpdateCaseSettings|Brugeren har ændret indstillingerne for en sag. Sagsindstillinger omfatter oplysninger om store og små bogstaver, adgangstilladelser og indstillinger, der styrer søge- og analysefunktionsmåden.|
|Søgning i ændrede gennemsynssæt|UpdateWorkingSetSearch|Brugeren har redigeret en søgeforespørgsel i et gennemsynssæt.|
|Gennemset søgning efter korrektursæt|PreviewWorkingSetSearch|Brugeren har gennemset resultaterne af en søgeforespørgsel i et gennemsynssæt.|
|Afhjælpede fejldokumenter|ErrorRemediationJob|Brugeren retter filer, der indeholdt indekseringsfejl.|
|Mærket dokument|TagFiles|Brugeren mærker et dokument i et korrektursæt.|
|Mærkede resultater af en forespørgsel|TagJob|Brugeren mærker alle de dokumenter, der opfylder søgeforespørgslens kriterier i et korrektursæt.|
|Viste dokument i korrektursæt|ViewDocument|Brugeren har set et dokument i et gennemsynssæt.|
|||

## <a name="ediscovery-cmdlet-activities"></a>eDiscovery-cmdlet-aktiviteter

I følgende tabel vises de cmdlet-overvågningslogposter, der logføres, når en administrator eller bruger udfører en eDiscovery-relateret aktivitet ved hjælp af overholdelsescenteret eller ved at køre den tilsvarende cmdlet i Security & Compliance Center PowerShell. De detaljerede oplysninger i overvågningslogposten er forskellige for de cmdlet-aktiviteter, der er angivet i denne tabel, og de eDiscovery-aktiviteter, der er beskrevet i forrige afsnit.
  
Som nævnt tidligere kan det tage op til 24 timer, før eDiscovery-cmdlet-aktiviteter vises i overvågningsloggens søgeresultater.
  
> [!TIP]
> Cmdlet'erne i kolonnen **Handling** i følgende tabel er kædet sammen med det tilsvarende emne i Hjælp til cmdlet på TechNet. Gå til hjælp-emnet for cmdlet'en for at få en beskrivelse af de tilgængelige parametre for hver cmdlet. Parameteren og parameterværdien, der blev brugt sammen med en cmdlet, er inkluderet i overvågningslogposten for hver eDiscovery-cmdlet-aktivitet, der logføres. 
  
|**Brugervenligt navn**|**Handling (cmdlet)**|**Beskrivelse**|
|:-----|:-----|:-----|
|Oprettet venteposition i eDiscovery-sag  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Der er oprettet en venteposition for en eDiscovery-sag. En venteposition kan oprettes med eller uden at angive en indholdskilde. Hvis indholdskilder er angivet, identificeres de i overvågningslogposten.  <br/> |
|Slettet venteposition fra eDiscovery-sag  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |En venteposition, der er knyttet til en eDiscovery-sag, er blevet slettet. Når du sletter en venteposition, frigives alle indholdsplaceringerne fra ventepositionen. Hvis du sletter ventepositionen, sletter du også de regler for venteposition, der er knyttet til ventepositionen (se **Remove-CaseHoldRule** nedenfor).  <br/> |
|Ændret venteposition i eDiscovery-sag  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |En venteposition, der er knyttet til en eDiscovery, er blevet ændret. Mulige ændringer omfatter at tilføje eller fjerne indholdsplaceringer eller at deaktivere (deaktivere) ventepositionen.  <br/> |
|Oprettede søgeforespørgsel til eDiscovery-sags hold  <br/> |[New-CaseHoldrule](/powershell/module/exchange/new-caseholdrule) <br/> |Der blev oprettet en forespørgselsbaseret venteposition knyttet til en eDiscovery-sag.  <br/> |
|Slettede søgeforespørgsel til eDiscovery-sags hold  <br/> |[Remove-CaseHoldrule](/powershell/module/exchange/remove-caseholdrule) <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, er blevet slettet. At fjerne forespørgslen fra ventepositionen er ofte resultatet af at slette en venteposition. Når en ventepositions- eller ventepositionsforespørgsel slettes, frigives de indholdsplaceringer, der var i venteposition.  <br/> |
|Ændret søgeforespørgsel til eDiscovery-sags venteposition  <br/> |[Set-CaseHoldrule](/powershell/module/exchange/set-caseholdrule) <br/> |En forespørgselsbaseret venteposition, der er knyttet til en eDiscovery-sag, er blevet ændret. Mulige ændringer omfatter redigering af forespørgslen eller datointervallet for en forespørgselsbaseret venteposition.  <br/> |
|Oprettet eDiscovery-sag  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Der blev oprettet en eDiscovery-sag. Når der oprettes en sag, behøver du kun at give den et navn. Andre sagsrelaterede opgaver såsom at tilføje medlemmer, oprette ventende funktioner og oprette indholdssøgninger, der er knyttet til sagen, medfører, at der logføres flere hændelser.  <br/> |
|Slettet eDiscovery-sag  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |En eDiscovery-sag blev slettet. Eventuelle ventepositioner, der er knyttet til sagen, skal fjernes, før sagen kan slettes.  <br/> |
|Ændret eDiscovery-sag  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |En eDiscovery-sag blev ændret. Ændringerne omfatter lukning af en åben sag eller genåbning af en lukket sag.  <br/> |
|Medlem føjet til eDiscovery-sag  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |En bruger blev tilføjet som medlem af en eDiscovery-sag. Som medlem af en sag kan en bruger udføre forskellige sagsrelaterede opgaver, afhængigt af om de har fået tildelt de nødvendige tilladelser.  <br/> |
|Medlem fjernet fra eDiscovery-sag  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |En bruger blev fjernet som medlem af en eDiscovery-sag.  <br/> |
|Ændret medlemskab af eDiscovery-sag  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |Medlemskabslisten for en eDiscovery-sag blev ændret. Denne aktivitet logføres, når alle medlemmer erstattes med en gruppe af nye brugere. Hvis et enkelt medlem tilføjes eller fjernes, logføres handlingen **Add-ComplianceCaseMember** eller **Remove-ComplianceCaseMember** .  <br/> |
|Indholdssøgning oprettet  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Der blev oprettet en ny indholdssøgning.  <br/> |
|Slettet indholdssøgning  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |En eksisterende indholdssøgning blev slettet.  <br/> |
|Ændret indholdssøgning  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |En eksisterende indholdssøgning blev ændret. Ændringer kan omfatte at tilføje eller fjerne indholdsplaceringer, der søges i, og at redigere søgeforespørgslen.  <br/> |
|Startet indholdssøgning  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |En indholdssøgning blev startet. Når du opretter eller ændrer en indholdssøgning ved hjælp af  GUI i Overholdelsescenter, startes søgningen automatisk. Hvis du opretter eller ændrer en søgning ved hjælp af cmdlet'en **New-ComplianceSearch** eller **Set-ComplianceSearch** , skal du køre **cmdlet'en Start-ComplianceSearch** for at starte søgningen.  <br/> |
|Stoppet indholdssøgning  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |En indholdssøgning, der kørte, blev stoppet.  <br/> |
|Handling til søgning efter indhold oprettet  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Der blev oprettet en handling til indholdssøgning. Handlinger til indholdssøgning omfatter visning af søgeresultater, eksport af søgeresultater, forberedelse af søgeresultater til analyse i Advanced eDiscovery og permanent sletning af elementer, der opfylder søgekriterierne i en indholdssøgning.  <br/> |
|Handling for søgning efter slettet indhold  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |En handling til indholdssøgning er blevet slettet.  <br/> |
|Filter for søgetilladelser oprettet  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Et søgetilladelsesfilter blev oprettet.  <br/> |
|Filter for slettede søgetilladelser  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Et filter for søgetilladelser er blevet slettet.  <br/> |
|Ændret filter for søgetilladelser  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Et filter for søgetilladelser blev ændret.  <br/> |
|Oprettet eDiscovery-administrator  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |En bruger blev tilføjet som eDiscovery-administrator i din organisation.  <br/> |
|Slettet eDiscovery-administrator  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |En eDiscovery-administrator er blevet slettet fra din organisation.  <br/> |
|Ændret eDiscovery-administratormedlemskab  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |Listen over eDiscovery-administratorer i din organisation er blevet ændret. Denne aktivitet logføres, når listen over eDiscovery-administratorer erstattes med en gruppe af nye brugere. Hvis en enkelt bruger tilføjes eller fjernes, logføres handlingen **Add-eDiscoveryCaseAdmin** eller **Remove-eDiscoveryCaseAdmin** .  <br/> |
|(ingen)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Denne aktivitet logføres, når en bruger får vist en liste over Core eDiscovery- Advanced eDiscovery-sager. Denne aktivitet logføres også, når en bruger får en specifik sag i Core eDiscovery. Når en bruger får vist en bestemt sag, indeholder overvågningsposten identiteten på den sag, der blev vist. Hvis brugeren kun har fået vist en liste over sager, indeholder overvågningsposten ikke en sagsidentitet.|
|(ingen)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Denne aktivitet logføres, når en bruger får vist en liste over indholdssøgninger eller søgninger, der er knyttet til en core eDiscovery-sag. Denne aktivitet logføres også, når en bruger får en bestemt indholdssøgning eller får en bestemt søgning, der er knyttet til en core eDiscovery-sag, til. Når en bruger får vist en bestemt søgning, indeholder overvågningsposten identiteten for den søgning, der blev vist. Hvis brugeren kun har fået vist en liste over søgninger, indeholder overvågningsposten ikke en søgeidentitet.
|(ingen)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Denne aktivitet logføres, når en bruger får vist en liste over søgehandlinger til overholdelse (f.eks. eksporter, forhåndsvisninger eller fjernede filer) eller handlinger, der er knyttet til en grundlæggende eDiscovery-sag. Denne aktivitet logføres også, når en bruger får en bestemt søgning i overensstemmelse med angivne standarder (f.eks. en eksport) eller får en bestemt handling knyttet til en grundlæggende eDiscovery-sag. Når en bruger får vist en søgehandling, indeholder overvågningsposten identiteten for den viste søgehandling. Hvis brugeren kun har fået vist en liste over handlinger, indeholder overvågningsposten ikke en handlingsidentitet.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Detaljerede egenskaber for eDiscovery-aktiviteter

I følgende tabel beskrives de egenskaber, der er inkluderet på pop op-siden for en eDiscovery-aktivitet, der er angivet i søgeresultaterne. Disse egenskaber er også inkluderet i CSV-filen, når du eksporterer søgeresultaterne fra overvågningsloggen. En overvågningslogpost for en eDiscovery-aktivitet omfatter ikke alle de detaljerede egenskaber, der er angivet nedenfor.
  
> [!TIP]
> Når du eksporterer søgeresultaterne, indeholder CSV-filen en kolonne med navnet **AudtiData**, som indeholder de detaljerede egenskaber, der er beskrevet i følgende tabel i en egenskab med flere værdier. Du kan bruge funktionen Power-forespørgsel i Excel at opdele denne kolonne i flere kolonner, så hver egenskab har sin egen kolonne. På den måde kan du sortere og filtrere efter en eller flere af disse egenskaber. Du kan finde flere oplysninger i afsnittet "Eksportér søgeresultaterne til en fil" i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Egenskab**|**Beskrivelse**|
|:-----|:-----|
|Sag  <br/> |Identiteten (GUID) for eDiscovery-sagen, der blev oprettet, ændret eller slettet.  <br/> |
|Klientanvisning  <br/> |eDiscovery-cmdlet-aktiviteter har en værdi **af EMC** for denne egenskab. Dette angiver, at aktiviteten blev udført ved hjælp af compliance center GUI eller ved at køre cmdlet'en i PowerShell.  <br/> |
|ClientIP  <br/> |IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.  <br/> |
|ClientRequestId  <br/> | For eDiscovery-aktiviteter er denne egenskab typisk tom.  <br/> |
|CmdletVersion  <br/> |Buildnummeret for den version af overholdelsescenter, der kører i organisationen.  <br/> |
|CreationTime  <br/> |Dato og klokkeslæt i UTC-tid (Coordinated Universal Time), da eDiscovery-aktiviteten blev fuldført.  <br/> |
|EffectiveOrganization  <br/> |Navnet på Microsoft 365-organisationen.  <br/> |
|ExchangeLocations  <br/> |De Exchange Online postkasser, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|Udeladelser  <br/> |Postkasser eller webstedsplaceringer, der er udelukket fra en indholdssøgning eller venteposition i en eDiscovery-sag.  <br/> |
|ExtendedProperties  <br/> |Yderligere egenskaber fra en indholdssøgning, en handling til indholdssøgning eller venteposition i en eDiscovery-sag, f.eks. objektet GUID og de tilsvarende cmdlet- og cmdlet-parametre, der blev brugt, da aktiviteten blev udført.  <br/> |
|Id  <br/> |Id'et for rapportposten. Id'et identificerer overvågningslogposten entydigt.  <br/> |
|IkkePII-parameterer  <br/> |En liste over de parametre (uden værdier), der blev brugt sammen med cmdlet'en identificeret i egenskaben Operation. De parametre, der er angivet i denne egenskab, er de samme som dem, der er angivet i egenskaben Parametre.  <br/> |
|ObjectId  <br/> |GUID'et eller navnet på objektet (f.eks. en indholdssøgning eller en Core eDiscovery-sag), der blev oprettet, åbnet, ændret eller slettet af den aktivitet, der er angivet i egenskaben Operation. Dette objekt identificeres også i kolonnen Element i overvågningsloggens søgeresultater.  <br/> |
|ObjectType  <br/> |Den type eDiscovery-objekt, brugeren har oprettet, slettet eller ændret. eksempelvis en handling til indholdssøgning (forhåndsvisning, eksportér eller tøm), en eDiscovery-sag eller en indholdssøgning.  <br/> |
|Handling  <br/> |Navnet på den handling, der svarer til den eDiscovery-aktivitet, der blev udført.  <br/> |
|OrganizationId  <br/> |GUID for din Microsoft 365 organisation.  <br/> |
|Parametre  <br/> |Navn og værdi for de parametre, der blev brugt sammen med den tilsvarende cmdlet.  <br/> |
|PublicFolderLocations  <br/> |De offentlige mappeplaceringer i Exchange Online, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|Forespørgsel  <br/> |Den søgeforespørgsel, der er knyttet til aktiviteten, f.eks. en indholdssøgning eller en forespørgselsbaseret venteposition.  <br/> |
|RecordType  <br/> |Den type handling, der er angivet af posten. Værdien **18 angiver en hændelse** , der er relateret til en aktivitet, der er angivet i [afsnittet eDiscovery-cmdlet-aktiviteter](#ediscovery-cmdlet-activities) . En værdi på **24** angiver en hændelse, der er relateret til en aktivitet, der er angivet i afsnittet Sådan søger du efter og [får vist eDiscovery-aktiviteter](#how-to-search-for-and-view-ediscovery-activities) .  <br/> |
|ResultStatus  <br/> |Angiver, om handlingen (angivet i egenskaben Operation) blev gennemført eller ej.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Angiver, at aktiviteten var en overholdelsescenterhændelse. Alle eDiscovery-aktiviteter har en værdi **på 0** for denne egenskab.  <br/> |
|SharepointLocations  <br/> |Indholdssøgning SharePoint Online-websteder, der er inkluderet i en indholdssøgning eller sat i venteposition i en eDiscovery-sag.  <br/> |
|StartTime  <br/> |Dato og klokkeslæt i UTC-tid (Coordinated Universal Time), da eDiscovery-aktiviteten blev startet.  <br/> |
|UserId  <br/> |Den bruger, der udførte aktiviteten (angivet i egenskaben Handling), som resulterede i, at posten blev logført. Poster for eDiscovery-aktivitet, der udføres af systemkonti (f.eks NT AUTHORITY\SYSTEM), medtages også i overvågningsloggen.  <br/> |
|UserKey  <br/> |Et alternativt id for den bruger, der er identificeret i egenskaben UserId. For eDiscovery-aktiviteter er værdien for denne egenskab typisk det samme som egenskaben UserId.  <br/> |
|UserServicePlan  <br/> |Det abonnement, der bruges af din organisation. For eDiscovery-aktiviteter er denne egenskab typisk tom.  <br/> |
|UserType  <br/> |Den type bruger, der udførte handlingen. Følgende værdier angiver brugertypen.  <br/> 0 En almindelig bruger. 2 En administrator i din organisation. 3 En Microsoft-datacenteradministrator eller datacentersystemkonto. 4 En systemkonto. 5 Et program. 6 En tjenesteinspektør. |
|Version  <br/> |Angiver versionsnummeret for den aktivitet (identificeres ved hjælp af egenskaben Operation), der logføres.  <br/> |
|Arbejdsbelastning  <br/> |Den tjeneste, hvor aktiviteten forekom. For eDiscovery-aktiviteter er værdien **SecurityComplianceCenter**.  <br/> |
