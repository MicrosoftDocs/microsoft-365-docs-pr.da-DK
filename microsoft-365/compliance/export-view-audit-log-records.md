---
title: Eksportere, konfigurere og få vist overvågningslogposter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: I denne artikel kan du se, hvordan du eksporterer, konfigurerer og får vist Microsoft 365 overvågningslogposter.
ms.openlocfilehash: efb71ea0ff0b7098c3524707cff101d7ba25877f
ms.sourcegitcommit: 678e827a1c3bc9f4edfc48003f9b29f7bbf20ab5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/31/2021
ms.locfileid: "63588712"
---
# <a name="export-configure-and-view-audit-log-records"></a>Eksportere, konfigurere og få vist overvågningslogposter

Når du har søgt i overvågningsloggen og hentet søgeresultaterne til en CSV-fil, indeholder filen en kolonne med navnet **AuditData**, som indeholder flere oplysninger om hver hændelse. Dataene i denne kolonne er formateret som et JSON-objekt, der indeholder flere egenskaber, der er konfigureret som *egenskab:* værdipar adskilt af kommaer. Du kan bruge JSON-transformeringsfunktionen i Power Query Editor i Excel til at opdele hver egenskab i JSON-objektet i **kolonnen AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. På den måde kan du sortere og filtrere efter en eller flere af disse egenskaber, hvilket kan hjælpe dig med hurtigt at finde de specifikke overvågningsdata, du leder efter.

## <a name="step-1-export-audit-log-search-results"></a>Trin 1: Eksportér søgeresultater fra overvågningsloggen

Det første trin er at søge i overvågningsloggen og derefter eksportere resultaterne i en fil med kommaseparerede værdier (CSV) til din lokale computer.
  
1. Kør en søgning [i overvågningsloggen,](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) og revidere søgekriterierne, hvis det er nødvendigt, indtil du har de ønskede resultater.

2. På siden med søgeresultater skal du klikke på **Eksportdownload** >  **alle resultater**.

   ![Klik på Hent alle resultater.](../media/ExportAuditSearchResults.png)

   Denne indstilling eksporterer alle overvågningsposterne fra den søgning i overvågningsloggen, du kørte i trin 1, og føjer rådataene fra overvågningsloggen til en CSV-fil. Det tager et stykke tid at forberede downloadfilen til en stor søgning. Der kommer store filer, når du søger efter alle aktiviteter eller bruger et bredt datointerval.

3. Når eksporten er fuldført, vises der en meddelelse øverst i vinduet, der beder dig om at åbne CSV-filen og gemme den på din lokale computer. Du kan også få adgang til CSV-filen i mappen Downloads.

   > [!NOTE]
   > Du kan hente maksimalt 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis der downloades 50.000 poster til CSV-filen, kan du sandsynligvis antage, at mere end 50.000 hændelser opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et smallere datoområde for at reducere antallet af overvågningslogposter. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>Trin 2: Formatere den eksporterede overvågningslog ved hjælp af Power-forespørgselseditoren

Næste trin er at bruge JSON-transformeringsfunktionen i Power Query Editor i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i sin egen kolonne. Derefter filtrerer du kolonner for at få vist poster baseret på værdierne i bestemte egenskaber. Dette kan hjælpe dig med hurtigt at finde de specifikke overvågningsdata, du leder efter.

1. Åbn en tom projektmappe i Excel for Office 365, Excel 2019 eller Excel 2016.

2. Klik på **Fra** tekst **/CSV** **& gruppen Transformér data** under fanen Data.

    ![Klik på Fra tekst/CSV under fanen Data.](../media/JSONTransformOpenCSVFile.png)

3. Åbn den CSV-fil, du hentede i trin 1.

4. Klik på Transformér data i det vindue, der **vises**.

   ![Klik på Transformér data.](../media/JSONOpenPowerQuery.png)

   CSV-filen åbnes i **Forespørgselseditor**. Der er fire kolonner: **CreationDate**, **UserIds**, **Operations** og **AuditData**. Kolonnen **AuditData** er et JSON-objekt, der indeholder flere egenskaber. Næste trin er at oprette en kolonne for hver egenskab i JSON-objektet.

5. Højreklik på titlen i kolonnen **AuditData,** klik på **Transformér**, og klik derefter på **JSON**. 

   ![Højreklik på kolonnen AuditData, klik på Transformér, og vælg derefter JSON.](../media/JSONTransform.png)

6. Klik på udvidelsesikonet i øverste højre hjørne af kolonnen **AuditData** .

   ![Klik på udvidelsesikonet i kolonnen AuditData.](../media/JSONTransformExpandIcon.png)

   Der vises en delvis liste over egenskaberne i JSON-objekterne i kolonnen **AuditData** .

7. Klik **på Indlæs** flere for at få vist alle egenskaberne i JSON-objekterne **i kolonnen AuditData** .

   ![Klik på Indlæs flere for at få vist alle egenskaber i JSON-objektet.](../media/JSONTransformLoadJSONProperties.png)

   Du kan fjerne markeringen i afkrydsningsfeltet ud for en hvilken som helst egenskab, du ikke vil medtage. At fjerne kolonner, der ikke er nyttige i din undersøgelse, er en god måde at reducere mængden af data, der vises i overvågningsloggen. 

   > [!NOTE]
   > JSON-egenskaberne, der vises i det forrige skærmbillede (når du klikker på Indlæs **flere), er** baseret på de egenskaber, der findes i kolonnen **AuditData** fra de første 1.000 rækker i CSV-filen. Hvis der er forskellige JSON-egenskaber i poster efter de første 1.000 rækker, medtages disse egenskaber (og en tilsvarende kolonne) ikke, når **kolonnen AuditData** er opdelt i flere kolonner. For at undgå dette skal du overveje at køre overvågningsloggen igen og indsnævre søgekriterierne, så der returneres færre poster. En anden løsning er at filtrere elementer i  kolonnen Handlinger for at reducere antallet af rækker (før du udfører trin 5 ovenfor), før du transformerer JSON-objektet i **kolonnen AuditData**.

   > [!TIP]
   > Hvis du vil have vist en attribut på en liste, f.eks. AuditData.AffectedItems, skal du klikke på ikonet Udvid i øverste højre hjørne af den kolonne, du vil trække en attribut fra, og derefter vælge Udvid til **ny række**.  Derfra bliver det en post, og du kan klikke på  ikonet Udvid i øverste højre hjørne af kolonnen, få vist attributterne og vælge den, du vil have vist eller udtrække.

8. Gør et af følgende for at formatere titlen på de kolonner, der tilføjes for hver JSON-egenskab, der er markeret.

    - Fjern markeringen i **afkrydsningsfeltet Brug det** oprindelige kolonnenavn som præfiks for at bruge navnet på JSON-egenskaben som kolonnenavne. For eksempel **RecordType** eller **SourceFileName**.

    - Lad **afkrydsningsfeltet Brug det oprindelige kolonnenavn som præfiks** være markeret for at føje AuditData-præfikset til kolonnenavnene. eksempelvis **AuditData.RecordType eller** **AuditData.SourceFileName**.

9. Klik på **OK**.

    Kolonnen **AuditData** er opdelt i flere kolonner. Hver ny kolonne svarer til en egenskab i AuditData JSON-objektet. Hver række i kolonnen indeholder værdien for egenskaben. Hvis egenskaben ikke indeholder en værdi, *vises null-værdien* . I Excel er celler med Null-værdier tomme.
  
10. På fanen **Hjem skal** du klikke på **Luk & Indlæs** for at lukke Power-forespørgselseditoren og åbne den transformerede CSV-fil i Excel projektmappe.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Brug PowerShell til at søge efter og eksportere overvågningslogposter

I stedet for at bruge søgeværktøjet til overvågningslogfiler i Microsoft 365 Overholdelsescenter kan du bruge [Search-UnifiedAuditLog-cmdlet'en](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell til at eksportere resultaterne af en søgning i overvågningsloggen til en CSV-fil. Derefter kan du følge den fremgangsmåde, der er beskrevet i trin 2, for at formatere overvågningsloggen ved hjælp af Power-forespørgselseditoren. En af fordelene ved at bruge PowerShell-cmdlet'en er, at du kan søge efter begivenheder fra en bestemt tjeneste ved hjælp af *RecordType-parameteren* . Her er nogle få eksempler på brug af PowerShell til at eksportere overvågningsposter til en CSV-fil, så du kan bruge Editor til Power-forespørgsel til at transformere JSON-objektet i kolonnen **AuditData** som beskrevet i trin 2.

I dette eksempel skal du køre følgende kommandoer for at returnere alle poster, der er relateret SharePoint delingshandlinger.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Søgeresultaterne eksporteres til en CSV-fil med navnet *PowerShellAuditlog* , som indeholder fire kolonner: CreationDate, UserIds, RecordType, AuditData).

Du kan også bruge navnet eller enum-værdien for posttypen som værdien for *RecordType-parameteren* . Du kan finde en liste over posttypenavne og deres tilsvarende enum-værdier i *tabellen AuditLogRecordType* [i Office 365 Management Activity API-skema](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32).

Du kan kun medtage en enkelt værdi for *RecordType-parameteren* . Hvis du vil søge efter overvågningsposter efter andre posttyper, skal du køre de to forrige kommandoer igen for at angive en anden posttype og føje disse resultater til den oprindelige CSV-fil. Du skal f.eks. køre følgende to kommandoer for at SharePoint filaktiviteter fra det samme datoområde til PowerShellAuditlog.csv fil.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Tips til at eksportere og få vist overvågningsloggen

Her er nogle tip og eksempler på eksport og visning af overvågningsloggen, før og efter du bruger funktionen JSON-transformering til at opdele **kolonnen AuditData** i flere kolonner.

- Filtrer **kolonnen RecordType** for kun at få vist poster fra en bestemt tjeneste eller et funktionsområde. Hvis du f.eks. vil vise hændelser SharePoint deling, skal du vælge **14** (enum-værdien for poster, der er udløst SharePoint delingsaktiviteter). Hvis du vil se en liste over de tjenester, der svarer til enum-værdierne, der vises i kolonnen **RecordType** , skal du se Detaljerede [egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md).

- Filtrer **kolonnen Handlinger** for at få vist posterne for bestemte aktiviteter. Du kan finde en liste over de fleste handlinger, der svarer til en søgbar aktivitet i overvågningsloggens søgeværktøj i Microsoft 365 Overholdelsescenter, i afsnittet "Overvågede aktiviteter" i Søg i [overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities).
