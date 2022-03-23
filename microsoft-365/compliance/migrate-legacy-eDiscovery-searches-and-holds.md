---
title: Overfør ældre eDiscovery-søgninger og -ventende funktioner til Microsoft 365 Overholdelsescenter
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
ms.openlocfilehash: fe3f65e2545b71f8cfbaea76dfd34fd2720a790f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63587762"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-microsoft-365-compliance-center"></a>Overfør ældre eDiscovery-søgninger og -ventende funktioner til Microsoft 365 Overholdelsescenter

Microsoft 365 Overholdelsescenter giver en forbedret oplevelse i forbindelse med eDiscovery-brug, herunder: større pålidelighed, bedre ydeevne og mange funktioner, der er skræddersyet til eDiscovery-arbejdsprocesser, herunder sager til at organisere dit indhold efter sag, gennemse sæt til at gennemse indhold og analyser for at hjælpe med at cullere data til gennemsyn, f.eks. nær duplikeret gruppering, mailtrådning, temaers analyse og forudsigelig kodning.

For at hjælpe kunderne med at drage fordel af den nye og forbedrede funktionalitet giver denne artikel grundlæggende vejledning til at overføre In-Place eDiscovery-søgninger og -ventefunktioner fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration til Microsoft 365 Overholdelsescenter.

> [!NOTE]
> Da der er mange forskellige scenarier, giver denne artikel generel vejledning til overgangssøgninger og indeholder en grundlæggende eDiscovery-sag i Microsoft 365 Overholdelsescenter. Brug af eDiscovery-sager er ikke altid påkrævet, men de tilføjer et ekstra lag af sikkerhed ved at give dig tilladelse til at give dig tilladelse til at styre, hvem der har adgang til eDiscovery-sager i din organisation.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være medlem af eDiscovery Manager-rollegruppen i gruppen Microsoft 365 Overholdelsescenter at køre de PowerShell-kommandoer, der er beskrevet i denne artikel. Du skal også være medlem af rollegruppen Søgeadministration i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

- Denne artikel indeholder vejledning til, hvordan du opretter et eDiscovery-venteposition. Politikken til venteposition anvendes på postkasser via en asynkron proces. Når du opretter en eDiscovery-venteposition, skal du oprette både en CaseHoldPolicy og CaseHoldRule, ellers oprettes ventepositionen ikke, og indholdsplaceringer sættes ikke i venteposition.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-center-powershell"></a>Trin 1: Forbind Exchange Online PowerShell og Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Exchange Online PowerShell og Security & Compliance Center PowerShell. Du kan kopiere følgende script, indsætte det i et PowerShell-vindue og derefter køre det. Du bliver bedt om legitimationsoplysninger for den organisation, du vil oprette forbindelse til. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $sccSession -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

Du skal køre kommandoerne i følgende trin i denne PowerShell-session.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>Trin 2: Få en liste over In-Place eDiscovery-søgninger ved hjælp af Get-MailboxSearch

Når du har godkendt, kan du få en liste over In-Place eDiscovery-søgninger ved at køre cmdlet'en **Get-MailboxSearch** . Kopiér og indsæt følgende kommando i PowerShell, og kør den derefter. Der vises en liste over søgninger med deres navne og status for alle In-Place hold.

```powershell
Get-MailboxSearch
```

Cmdlet-outputtet vil ligne følgende:

![PowerShell-eksempel: Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>Trin 3: Få oplysninger om de In-Place eDiscovery-søgninger og -In-Place, du vil overføre

Igen skal du bruge **cmdlet'en Get-MailboxSearch** , men denne gang for at hente egenskaberne for søgningen. Du kan gemme disse egenskaber i en variabel til senere brug. I følgende eksempel gemmes resultaterne af **cmdlet'en Get-MailboxSearch** i en variabel og viser derefter egenskaberne for søgningen.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

Outputtet for disse to kommandoer vil ligne følgende:

![Eksempel på PowerShell-output fra brug Get-MailboxSearch til en individuel søgning.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> Varigheden af ventepositionen In-Place i dette eksempel er for altid (*ItemHoldPeriod: Unlimited*). Dette er typisk for scenarier med eDiscovery og juridisk undersøgelse. Hvis varigheden af ventepositionen har en anden værdi end ubestemt, skyldes årsagen sandsynligvis, at ventepositionen bruges til at bevare indhold i et opbevaringsscenarie. I stedet for at bruge eDiscovery-cmdletterne i Security & Compliance Center PowerShell til opbevaringsscenarier, anbefaler vi, at du bruger [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) og [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) til at bevare indhold. Resultatet af at bruge disse cmdlet'er svarer til at bruge **New-CaseHoldPolicy** og **New-CaseHoldRule**, men du kan angive en opbevaringsperiode og en opbevaringshandling, f.eks. sletning af indhold, når en opbevaringsperiode udløber. Desuden kræver brug af opbevarings-cmdletterne ikke, at du knytter opbevarings hold til en eDiscovery-sag.

## <a name="step-4-create-a-case-in-the-microsoft-365-compliance-center"></a>Trin 4: Opret en sag i Microsoft 365 Compliance Center

Hvis du vil oprette en eDiscovery-venteposition, skal du oprette en eDiscovery-sag, der skal knyttes til ventepositionen. I følgende eksempel oprettes der en eDiscovery-sag med et navn efter eget valg. Vi gemmer egenskaberne for den nye sag i en variabel til senere brug. Du kan få vist disse egenskaber ved at køre kommandoen `$case | FL` , når du har oprettet sagen.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```
![Eksempel på at køre New-ComplianceCase kommando.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>Trin 5: Opret eDiscovery-ventepositionen

Når sagen er oprettet, kan du oprette ventepositionen og knytte den til den sag, du oprettede i forrige trin. Det er vigtigt at huske, at du skal oprette både en politik for sags hold og en regel for venteposition. Hvis reglen om venteposition ikke oprettes, efter du har oprettet en politik for sags venteposition, oprettes eDiscovery-ventepositionen ikke, og indholdet sættes ikke i venteposition.

Kør følgende kommandoer for at oprette den eDiscovery-venteposition, du vil overføre, igen. I disse eksempler bruges egenskaberne fra In-Place Hold fra trin 3, som du vil overføre. Den første kommando opretter en ny politik for sags hold og gemmer egenskaberne i en variabel. Den anden kommando opretter den tilsvarende regel for venteposition for store og små bogstaver.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![Eksempel på brug af NewCaseHoldPolicy- og NewCaseHoldRule-cmdlet'er.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>Trin 6: Bekræft eDiscovery-ventepositionen

Hvis du vil sikre, at der ikke var nogen problemer med at oprette ventepositionen, kan du kontrollere, at status for ventepositionsdistributionen er fuldført. Fordeling betyder, at ventepositionen er blevet anvendt på alle de indholdsplaceringer, der er angivet i *ExchangeLocation-parameteren* i forrige trin. For at gøre dette kan du køre **Get-CaseHoldPolicy-cmdlet'en** . Da de egenskaber, der er gemt *i $policy* , som du oprettede i forrige trin, ikke opdateres automatisk i variablen, skal du køre cmdlet'en igen for at bekræfte, at fordelingen er vellykket. Det kan tage mellem 5 minutter og 24 timer, før politikker for ventepositioner fordeles korrekt.

Kør følgende kommando for at bekræfte, at eDiscovery-ventepositionen er blevet distribueret.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

Værdien af **Succes** for egenskaben *DistributionStatus* angiver, at ventepositionen blev placeret på indholdsplaceringerne. Hvis fordelingen endnu ikke er fuldført, vises en **værdi for** Afventer.

![PowerShell Get-CaseHoldPolicy eksempel.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>Trin 7: Opret søgningen

Det sidste trin er at oprette den søgning, du identificerede i trin 3, igen og knytte den til sagen. Når du har oprettet søgningen, kan du køre den ved hjælp af **cmdlet'en Start-ComplianceSearch** eller køre den på et senere tidspunkt.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![PowerShell New-ComplianceSearch eksempel.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-microsoft-365-compliance-center"></a>Trin 8: Bekræft sagen, hold og søg i Microsoft 365 Overholdelsescenter

For at sikre at alt er konfigureret korrekt, skal du gå til Microsoft 365 Overholdelsescenter på [https://compliance.microsoft.com](https://compliance.microsoft.com)og klikke **på eDiscovery > Core**.

![Microsoft 365 Compliance Center eDiscovery.](../media/MigrateLegacyeDiscovery7.png)

Den sag, du oprettede i trin 3, står anført på **Core eDiscovery-siden** . Åbn sagen, og bemærk derefter den venteposition, du oprettede i trin 4, som er angivet på **fanen Venteposition** . Du kan vælge ventepositionen for at få vist oplysninger på pop op-siden, herunder antallet af postkasser, ventepositionen anvendes på og distributionsstatus.

![eDiscovery-ventende oplysninger i Microsoft 365 Overholdelsescenter.](../media/MigrateLegacyeDiscovery8.png)

Den søgning, du oprettede i trin 7, vises **under fanen** Søgninger i sagen.

![søgning efter eDiscovery-sag i Microsoft 365 Overholdelsescenter.](../media/MigrateLegacyeDiscovery9.png)

Hvis du overfører en In-Place eDiscovery-søgning, men ikke knytter den til en eDiscovery-sag, vil den blive vist på siden Indholdssøgning i Microsoft 365 Overholdelsescenter.

## <a name="more-information"></a>Flere oplysninger

- Du kan finde flere In-Place om eDiscovery & i Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Administration i</a>:
  
  - [Direkte eDiscovery](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [In-Place Hold and Litigation Hold](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Du kan finde flere oplysninger om de PowerShell-cmdlet'er, der bruges i artiklen:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)
  
  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)
  
  - [New-CaseHoldrule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
  
  - [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Du kan finde flere oplysninger Microsoft 365 Overholdelsescenter under [Oversigt over Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center.md).