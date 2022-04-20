---
title: Overfør ældre eDiscovery-søgninger og ventepositioner til Microsoft Purview-overholdelsesportalen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: 28f110c6b236721debdb5585263dd835f2a5a658
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993134"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-compliance-portal"></a>Overfør ældre eDiscovery-søgninger og ventepositioner til overholdelsesportalen

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview-overholdelsesportalen giver en forbedret oplevelse i forbindelse med eDiscovery-brug, herunder: højere pålidelighed, bedre ydeevne og mange funktioner, der er skræddersyet til eDiscovery-arbejdsprocesser, herunder sager til at organisere dit indhold efter sag, gennemgå sæt for at gennemse indhold og analyser for at hjælpe med at kassere data til gennemsyn, f.eks. næsten identisk gruppering, mailtrådning, temaanalyse og forudsigende kodning.

Denne artikel indeholder en grundlæggende vejledning i, hvordan du overfører In-Place eDiscovery-søgninger og ventepositioner fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til overholdelsesportalen for at hjælpe kunder med at drage fordel af den nye og forbedrede funktionalitet.

> [!NOTE]
> Da der er mange forskellige scenarier, indeholder denne artikel en generel vejledning til at overføre søgninger og ventepositioner til en eDiscovery(Standard)-sag i overholdelsesportalen. Brug af eDiscovery-sager er ikke altid påkrævet, men de tilføjer et ekstra lag af sikkerhed ved at give dig tilladelse til at tildele tilladelser til at styre, hvem der har adgang til eDiscovery-sager i din organisation.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være medlem af rollegruppen eDiscovery Manager på overholdelsesportalen for at køre de PowerShell-kommandoer, der er beskrevet i denne artikel. Du skal også være medlem af rollegruppen Registreringsadministration i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

- Denne artikel indeholder en vejledning i, hvordan du opretter en eDiscovery-venteposition. Politikken for venteposition anvendes på postkasser via en asynkron proces. Når du opretter en eDiscovery-venteposition, skal du oprette både en CaseHoldPolicy og CaseHoldRule, ellers oprettes ventepositionen ikke, og indholdsplaceringer sættes ikke i venteposition.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-center-powershell"></a>Trin 1: Opret forbindelse til Exchange Online PowerShell og Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Exchange Online PowerShell og Security & Compliance Center PowerShell. Du kan kopiere følgende script, indsætte det i et PowerShell-vindue og derefter køre det. Du bliver bedt om at angive legitimationsoplysninger for den organisation, du vil oprette forbindelse til. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $sccSession -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

Du skal køre kommandoerne i følgende trin i denne PowerShell-session.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>Trin 2: Hent en liste over In-Place eDiscovery-søgninger ved hjælp af Get-MailboxSearch

Når du er godkendt, kan du få vist en liste over In-Place eDiscovery-søgninger ved at køre Cmdlet'en **Get-MailboxSearch** . Kopiér og indsæt følgende kommando i PowerShell, og kør den derefter. En liste over søgninger vises med deres navne og status for alle In-Place Ventepositioner.

```powershell
Get-MailboxSearch
```

Cmdlet-outputtet ligner følgende:

![PowerShell-eksempel Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>Trin 3: Hent oplysninger om de In-Place eDiscovery-søgninger og In-Place ventepositioner, du vil overføre

Igen skal du bruge Cmdlet'en **Get-MailboxSearch** , men denne gang skal du hente egenskaberne for søgningen. Du kan gemme disse egenskaber i en variabel til senere brug. I følgende eksempel gemmes resultaterne af Cmdlet'en **Get-MailboxSearch** i en variabel, og egenskaberne for søgningen vises derefter.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

Outputtet af disse to kommandoer svarer til følgende:

![Eksempel på PowerShell-output fra brug af Get-MailboxSearch til en individuel søgning.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> Varigheden af den In-Place venteposition i dette eksempel er ubestemt (*ItemHoldPeriod: Unlimited*). Dette er typisk for eDiscovery- og juridiske undersøgelsesscenarier. Hvis varigheden af ventepositionen har en anden værdi end ubestemt, skyldes det sandsynligvis, at ventepositionen bruges til at bevare indhold i et opbevaringsscenarie. I stedet for at bruge eDiscovery-cmdlet'erne i Security & Compliance Center PowerShell til opbevaringsscenarier anbefaler vi, at du bruger [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) og [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) til at bevare indhold. Resultatet af at bruge disse cmdlet'er svarer til at bruge **New-CaseHoldPolicy** og **New-CaseHoldRule**, men du kan angive en opbevaringsperiode og en opbevaringshandling, f.eks. sletning af indhold, når opbevaringsperioden udløber. Brug af opbevarings-cmdlet'er kræver heller ikke, at du knytter opbevaringsholdningerne til en eDiscovery-sag.

## <a name="step-4-create-a-case-in-the-microsoft-purview-compliance-portal"></a>Trin 4: Opret en sag på Microsoft Purview-overholdelsesportalen

Hvis du vil oprette en eDiscovery-venteposition, skal du oprette en eDiscovery-sag, som ventepositionen skal knyttes til. I følgende eksempel oprettes der en eDiscovery-sag ved hjælp af et navn efter eget valg. Vi gemmer egenskaberne for den nye sag i en variabel til senere brug. Du kan få vist disse egenskaber ved at køre `$case | FL` kommandoen , når du har oprettet sagen.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```
![Eksempel på kørsel af kommandoen New-ComplianceCase.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>Trin 5: Opret eDiscovery-venteposition

Når sagen er oprettet, kan du oprette ventepositionen og knytte den til den sag, du oprettede i det forrige trin. Det er vigtigt at huske, at du skal oprette både en politik for saghold og en regel for saghold. Hvis reglen for sag venteposition ikke oprettes, efter at du har oprettet en politik for sag venteposition, oprettes eDiscovery-ventepositionen ikke, og indhold sættes ikke i venteposition.

Kør følgende kommandoer for at genoprette den eDiscovery-venteposition, du vil overføre. I disse eksempler bruges egenskaberne fra In-Place Venteposition fra trin 3, som du vil overføre. Den første kommando opretter en ny politik for sagslagring og gemmer egenskaberne i en variabel. Med den anden kommando oprettes den tilsvarende regel for sag i venteposition.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![Eksempel på brug af NewCaseHoldPolicy- og NewCaseHoldRule-cmdlet'er.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>Trin 6: Kontrollér eDiscovery-ventepositionen

Hvis du vil sikre dig, at der ikke var problemer med at oprette ventepositionen, er det godt at kontrollere, at status for distribution af venteposition er fuldført. Distribution betyder, at ventepositionen er anvendt på alle de indholdsplaceringer, der er angivet i parameteren *ExchangeLocation* i det forrige trin. Det gør du ved at køre cmdlet'en **Get-CaseHoldPolicy** . Da de egenskaber, der er gemt i den *$policy* variabel, som du oprettede i det forrige trin, ikke opdateres automatisk i variablen, skal du køre cmdlet'en igen for at kontrollere, at distributionen er fuldført. Det kan tage mellem 5 minutter og 24 timer, før politikker for sags bevarelse distribueres korrekt.

Kør følgende kommando for at kontrollere, at eDiscovery-ventepositionen er blevet distribueret.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

Værdien af **Succes** for egenskaben *DistributionStatus* angiver, at ventepositionen blev placeret på indholdsplaceringerne. Hvis distributionen endnu ikke er fuldført, vises værdien **Afventer** .

![PowerShell Get-CaseHoldPolicy eksempel.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>Trin 7: Opret søgningen

Det sidste trin er at genoprette den søgning, du identificerede i trin 3, og knytte den til sagen. Når du har oprettet søgningen, kan du køre den ved hjælp af **Start-ComplianceSearch-cmdlet'en** eller køre på et senere tidspunkt.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![PowerShell New-ComplianceSearch eksempel.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-compliance-portal"></a>Trin 8: Kontrollér sagen, hold og søg i overholdelsesportalen

Hvis du vil sikre dig, at alt er konfigureret korrekt, skal du gå til overholdelsesportalen på [https://compliance.microsoft.com](https://compliance.microsoft.com)og klikke på **eDiscovery > Core**.

![Microsoft Purview-overholdelsesportal eDiscovery.](../media/MigrateLegacyeDiscovery7.png)

Den sag, du oprettede i trin 3, vises på siden **eDiscovery (Standard).** Åbn sagen, og læg derefter mærke til den venteposition, du oprettede i trin 4 på listen under fanen **Venteposition** . Du kan vælge ventepositionen for at få vist detaljer på pop op-siden, herunder antallet af postkasser, som ventepositionen anvendes på, og distributionsstatus.

![eDiscovery findes i overholdelsesportalen.](../media/MigrateLegacyeDiscovery8.png)

Den søgning, du oprettede i trin 7, vises under fanen **Søgninger** i sagen.

![eDiscovery-sagssøgning på overholdelsesportalen.](../media/MigrateLegacyeDiscovery9.png)

Hvis du overfører en In-Place eDiscovery-søgning, men ikke knytter den til en eDiscovery-sag, vises den på siden Indholdssøgning på overholdelsesportalen.

## <a name="more-information"></a>Flere oplysninger

- Du kan finde flere oplysninger om In-Place eDiscovery & Ventepositioner i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> i:
  
  - [EDiscovery på stedet](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Bevarelse på stedet og procesførelse](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Du kan få flere oplysninger om de PowerShell-cmdlet'er, der bruges i artiklen, i:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)
  
  - [Sag om ny overholdelse](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)
  
  - [Ny-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
  
  - [Nyt overholdelsessøg](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Du kan få flere oplysninger om overholdelsesportalen under [Oversigt over Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center.md).