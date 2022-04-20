---
title: Eksportér, konfigurer og få vist data fra overvågningsloggen
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
description: I denne artikel får du mere at vide om, hvordan du eksporterer, konfigurerer og får vist Microsoft 365 overvågningslogposter.
ms.openlocfilehash: 9403ead4c7fd6bd27bcc3848d367749e00beed3c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994386"
---
# <a name="export-configure-and-view-audit-log-records"></a>Eksportér, konfigurer og få vist data fra overvågningsloggen

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har søgt i overvågningsloggen og downloadet søgeresultaterne til en CSV-fil, indeholder filen en kolonne med navnet **AuditData**, som indeholder yderligere oplysninger om hver enkelt hændelse. Dataene i denne kolonne er formateret som et JSON-objekt, der indeholder flere egenskaber, der er konfigureret som *property:value-par* adskilt af kommaer. Du kan bruge transformationsfunktionen JSON i Power Query-editor i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. Det giver dig mulighed for at sortere og filtrere på en eller flere af disse egenskaber, hvilket kan hjælpe dig med hurtigt at finde de specifikke overvågningsdata, du leder efter.

## <a name="step-1-export-audit-log-search-results"></a>Trin 1: Eksportér søgeresultater i overvågningsloggen

Det første trin er at søge i overvågningsloggen og derefter eksportere resultaterne i en fil med kommaseparerede værdier (CSV) til din lokale computer.
  
1. Kør en [søgning i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) , og rediger søgekriterierne, hvis det er nødvendigt, indtil du har de ønskede resultater.

2. Klik på **EksportérDownload** >  **alle resultater** på siden med søgeresultater.

   ![Klik på Download alle resultater.](../media/ExportAuditSearchResults.png)

   Denne indstilling eksporterer alle overvågningsposter fra den søgning i overvågningsloggen, du kørte i trin 1, og føjer rådata fra overvågningsloggen til en CSV-fil. Det tager et stykke tid at forberede downloadfilen til en stor søgning. Store filer vil blive resultatet, når du søger efter alle aktiviteter eller bruger et bredt datointerval.

3. Når eksporten er fuldført, vises der en meddelelse øverst i vinduet, hvor du bliver bedt om at åbne CSV-filen og gemme den på din lokale computer. Du kan også få adgang til CSV-filen i mappen Downloads.

   > [!NOTE]
   > Du kan maksimalt downloade 50.000 poster til en CSV-fil fra en enkelt søgning i overvågningsloggen. Hvis 50.000 poster downloades til CSV-filen, kan du sandsynligvis antage, at der er mere end 50.000 hændelser, der opfylder søgekriterierne. Hvis du vil eksportere mere end denne grænse, kan du prøve at bruge et smallere datointerval til at reducere antallet af overvågningslogposter. Du skal muligvis køre flere søgninger med mindre datointervaller for at eksportere mere end 50.000 poster.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>Trin 2: Formatér den eksporterede overvågningslog ved hjælp af Power Query-editor

Det næste trin er at bruge JSON-transformeringsfunktionen i Power Query-editor i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i sin egen kolonne. Derefter kan du filtrere kolonner for at få vist poster baseret på værdierne for bestemte egenskaber. Dette kan hjælpe dig med hurtigt at finde de specifikke overvågningsdata, du leder efter.

1. Åbn en tom projektmappe i Excel for Office 365, Excel 2019 eller Excel 2016.

2. Klik på **Fra tekst/CSV** i båndgruppen **Hent & Transformér data** under fanen **Data**.

    ![Klik på Fra tekst/CSV under fanen Data.](../media/JSONTransformOpenCSVFile.png)

3. Åbn den CSV-fil, du downloadede i Trin 1.

4. Klik på **Transformér data** i det viste vindue.

   ![Klik på Transformér data.](../media/JSONOpenPowerQuery.png)

   CSV-filen åbnes i **Power Query-editor**. Der er fire kolonner: **CreationDate**, **UserIds**, **Operations** og **AuditData**. Kolonnen **AuditData** er et JSON-objekt, der indeholder flere egenskaber. Det næste trin er at oprette en kolonne for hver egenskab i JSON-objektet.

5. Højreklik på titlen i kolonnen **AuditData** , klik på **Transformér**, og klik derefter på **JSON**. 

   ![Højreklik på kolonnen AuditData, klik på Transformér, og vælg derefter JSON.](../media/JSONTransform.png)

6. Klik på udvidelsesikonet i øverste højre hjørne af kolonnen **AuditData** .

   ![Klik på udvidelsesikonet i kolonnen AuditData.](../media/JSONTransformExpandIcon.png)

   Der vises en delvis liste over egenskaberne i JSON-objekterne i kolonnen **AuditData** .

7. Klik på **Indlæs mere** for at få vist alle egenskaber i JSON-objekterne i kolonnen **AuditData** .

   ![Klik på Indlæs mere for at få vist alle egenskaber i JSON-objektet.](../media/JSONTransformLoadJSONProperties.png)

   Du kan fjerne markeringen i afkrydsningsfeltet ud for en hvilken som helst egenskab, du ikke vil medtage. Fjernelse af kolonner, der ikke er nyttige i din undersøgelse, er en god måde at reducere mængden af data, der vises i overvågningsloggen. 

   > [!NOTE]
   > De JSON-egenskaber, der vises på det forrige skærmbillede (når du har **klikket på Indlæs mere**), er baseret på de egenskaber, der blev fundet i kolonnen **AuditData** fra de første 1.000 rækker i CSV-filen. Hvis der er forskellige JSON-egenskaber i poster efter de første 1.000 rækker, medtages disse egenskaber (og en tilsvarende kolonne) ikke, når kolonnen **AuditData** opdeles i flere kolonner. Du kan forhindre dette ved at overveje at køre søgningen i overvågningsloggen igen og begrænse søgekriterierne, så der returneres færre poster. En anden løsning er at filtrere elementer i kolonnen **Handlinger** for at reducere antallet af rækker (før du udfører trin 5 ovenfor), før du transformerer JSON-objektet i kolonnen **AuditData** .

   > [!TIP]
   > Hvis du vil have vist en attribut på en liste, f.eks. AuditData.AffectedItems, skal du klikke på ikonet **Udvid** i øverste højre hjørne af den kolonne, du vil hente en attribut fra, og derefter vælge **Udvid til ny række**.  Derfra vil det være en post, og du kan klikke på ikonet **Udvid** i øverste højre hjørne af kolonnen, få vist attributterne og vælge den, du vil have vist eller udtrække.

8. Gør en af følgende ting for at formatere titlen på de kolonner, der tilføjes for hver JSON-egenskab, der er valgt.

    - Fjern markeringen i afkrydsningsfeltet **Brug oprindeligt kolonnenavn som præfiks** for at bruge navnet på egenskaben JSON som kolonnenavne. for eksempel **RecordType** eller **SourceFileName**.

    - Lad afkrydsningsfeltet **Brug oprindeligt kolonnenavn som præfiks** være markeret for at føje præfikset AuditData til kolonnenavnene. **f.eks. AuditData.RecordType** eller **AuditData.SourceFileName**.

9. Klik på **OK**.

    Kolonnen **AuditData** er opdelt i flere kolonner. Hver ny kolonne svarer til en egenskab i AuditData JSON-objektet. Hver række i kolonnen indeholder værdien for egenskaben. Hvis egenskaben ikke indeholder en værdi, vises *null-værdien* . I Excel er celler med null-værdier tomme.
  
10. Klik på **Luk & Indlæs** under fanen **Hjem** for at lukke Power Query-editor og åbne den transformerede CSV-fil i en Excel projektmappe.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Brug PowerShell til at søge efter og eksportere overvågningslogposter

I stedet for at bruge søgeværktøjet til overvågningslog på Microsoft Purview-overholdelsesportalen kan du bruge cmdlet'en [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell til at eksportere resultaterne af en overvågningslogsøgning til en CSV-fil. Derefter kan du følge den samme procedure, der er beskrevet i trin 2, for at formatere overvågningsloggen ved hjælp af Power Query editor. En fordel ved at bruge PowerShell-cmdlet'en er, at du kan søge efter hændelser fra en bestemt tjeneste ved hjælp af parameteren *RecordType* . Her er nogle eksempler på, hvordan du bruger PowerShell til at eksportere overvågningsposter til en CSV-fil, så du kan bruge editoren Power Query til at transformere JSON-objektet i kolonnen **AuditData** som beskrevet i trin 2.

I dette eksempel skal du køre følgende kommandoer for at returnere alle poster, der er relateret til SharePoint delingshandlinger.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Søgeresultaterne eksporteres til en CSV-fil med navnet *PowerShellAuditlog* , der indeholder fire kolonner: CreationDate, UserIds, RecordType, AuditData).

Du kan også bruge navnet eller optællingsværdien for posttypen som værdien for parameteren *RecordType* . Du kan se en liste over navne på posttyper og deres tilsvarende optællingsværdier i tabellen *AuditLogRecordType* i [Office 365 API-skemaet til administrationsaktivitet](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32).

Du kan kun inkludere en enkelt værdi for parameteren *RecordType* . Hvis du vil søge efter overvågningsposter for andre posttyper, skal du køre de to forrige kommandoer igen for at angive en anden posttype og føje disse resultater til den oprindelige CSV-fil. Du kan f.eks. køre følgende to kommandoer for at føje SharePoint filaktiviteter fra det samme datointerval til PowerShellAuditlog.csv-filen.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Tip til eksport og visning af overvågningsloggen

Her er nogle tip og eksempler på eksport og visning af overvågningsloggen før og efter, du bruger JSON-transformationsfunktionen til at opdele kolonnen **AuditData** i flere kolonner.

- Filtrer kolonnen **RecordType** for kun at få vist posterne fra en bestemt tjeneste eller et bestemt funktionsområde. Hvis du f.eks. vil vise hændelser, der er relateret til SharePoint deling, skal du vælge **14** (optællingsværdien for poster, der udløses af SharePoint delingsaktiviteter). Du kan finde en liste over de tjenester, der svarer til de optællingsværdier, der vises i kolonnen **RecordType** , [under Detaljerede egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md).

- Filtrer kolonnen **Handlinger** for at få vist posterne for bestemte aktiviteter. Du kan finde en liste over de fleste handlinger, der svarer til en søgbar aktivitet i søgeværktøjet til overvågningslog på overholdelsesportalen, i afsnittet "Overvågede aktiviteter" i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities).
