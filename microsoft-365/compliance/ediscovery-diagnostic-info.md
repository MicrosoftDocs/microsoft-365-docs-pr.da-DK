---
title: Indsamle diagnostiske eDiscovery-oplysninger
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Få mere at vide om, hvordan du indsamler diagnostiske eDiscovery-oplysninger om en Microsoft Support-sag.
ms.openlocfilehash: cab21c71168119b27a478b99a19ad5693ffb678e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63590694"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Indsamle diagnostiske eDiscovery-oplysninger

Nogle gange kræver Microsoft-supportteknikere specifikke oplysninger om dit problem, når du åbner en supportsag, der er relateret til Core eDiscovery eller Advanced eDiscovery. Denne artikel indeholder vejledning til at indsamle diagnostiske oplysninger for at hjælpe supportteknikere med at undersøge og løse problemer. Typisk behøver du ikke at indsamle disse oplysninger, før du bliver bedt om det af en Microsoft-supporttekniker.

> [!IMPORTANT]
> Outputtet fra cmdlet'er og diagnostiske oplysninger, der er beskrevet i denne artikel, kan omfatte følsomme oplysninger om procesførelse eller interne undersøgelser i din organisation. Før du sender de rå diagnostiske oplysninger til Microsoft Support, skal du gennemse oplysningerne og redigere eventuelle følsomme oplysninger (f.eks. navne eller andre oplysninger om parter i procesførelse eller undersøgelse) ved at erstatte dem med `XXXXXXX`. Hvis du bruger denne metode, vil det også angive over for Microsoft-supportteknikeren, at oplysningerne blev benyttet igen.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>Indsamle diagnostiske oplysninger til Core eDiscovery

Indsamling af diagnostiske oplysninger til Core eDiscovery er cmdlet-baseret, så du skal bruge Security & Compliance Center PowerShell. Følgende PowerShell-eksempler kører cmdlet'er og gemmer derefter outputtet i en bestemt tekstfil. I de fleste supporttilfælde bør du kun skulle køre en af disse kommandoer.

For at køre følgende cmdlet'er skal [du oprette forbindelse til Security & Compliance Center PowerShell</span>](/powershell/exchange/connect-to-scc-powershell). Når du har forbindelse, skal du køre en eller flere af følgende kommandoer og sørge for at erstatte pladsholdere med de faktiske objektnavne.

Når du har gennemset den genererede tekstfil og redigeret følsomme oplysninger igen, kan du sende den til den Microsoft Support-tekniker, der arbejder på din sag.

> [!NOTE]
> Du kan også køre kommandoerne i dette afsnit for at indsamle diagnostiske oplysninger om de søgninger og eksporter, der  er angivet på siden Indholdssøgning i Microsoft 365 Overholdelsescenter.

### <a name="collect-information-about-searches"></a>Indsamle oplysninger om søgninger

Følgende kommando indsamler oplysninger, der er nyttige, når du undersøger problemer med en indholdssøgning eller en søgning, der er knyttet til en core eDiscovery-sag.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Indsamle oplysninger om søgehandlinger

Følgende kommando indsamler oplysninger for at undersøge problemer med forhåndsvisning, eksport eller slette resultaterne af en indholdssøgning eller en søgning, der er knyttet til en Core eDiscovery-sag. Du kan identificere navnet på søgehandlingen ved at klikke på en eksport, der er angivet under **fanen Eksporter** . Hvis du vil identificere navnene på eksempel- og slettehandlinger, kan du køre **cmdlet'en Get-ComplianceSearchAction** for at få vist en liste over alle handlinger. Formatet for navnet på søgehandlingen er opbygget ved at tilføje `_Preview`, `_Export`eller til `_Purge` navnet på den tilsvarende søgning.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Indsamle oplysninger om eDiscovery-ventende data

Når en eDiscovery-venteposition, der er knyttet til en Core eDiscovery-sag, ikke fungerer som forventet, skal du køre følgende kommando for at indsamle oplysninger om politikken for sags hold og den tilknyttede regel for sags hold for eDiscovery-ventepositionen. *Politiknavnet til sags* hold i følgende kommando er det samme som navnet på eDiscovery-ventepositionen. Du kan identificere dette navn på **fanerne ventende** funktioner i Core eDiscovery-sagen.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Indsamle alle oplysninger om sagen

Nogle gange fremgår det ikke tydeligt, hvilke oplysninger Microsoft Support kræver for at undersøge problemet. I denne situation kan du indsamle alle diagnosticeringsoplysninger til en central eDiscovery-sag. Det *grundlæggende navn på eDiscovery-sag* i følgende kommando er det samme som navnet på en sag, der vises på core **eDiscovery-siden** i Microsoft 365 Overholdelsescenter.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>Indsamle diagnostiske oplysninger til Advanced eDiscovery

Under **Indstillinger** i en Advanced eDiscovery case kan du hurtigt kopiere de diagnostiske oplysninger for sagen. Diagnosticeringsoplysningerne gemmes i Udklipsholder, så du kan indsætte dem i en tekstfil og sende dem til Microsoft Support.

1. Gå til Microsoft 365 Overholdelsescenter, og vælg **eDiscoveryAdvanced** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. Markér en sag, og klik derefter **på Indstillinger** store og små bogstaver.

3. Klik **på Vælg under** Oplysninger om **sag**.

4. Klik på ActionsCopy-supportoplysninger **på** >  **pop op-siden** for at kopiere oplysningerne til Udklipsholder.

5. Åbn en tekstfil (i Notesblok), og indsæt derefter oplysningerne i tekstfilen.

6. Gem tekstfilen, og navngive den noget i f.eks `AeD Diagnostic Info YYYY.MM.DD` . (f.eks `AeD Diagnostic Info 2020.11.03`. ).

Når du har gennemset filen og redigeret følsomme oplysninger igen, kan du sende den til den Microsoft-supporttekniker, der arbejder på din sag.
