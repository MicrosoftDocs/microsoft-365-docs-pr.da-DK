---
title: Indsaml diagnosticeringsoplysninger i eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du indsamler eDiscovery-diagnosticeringsoplysninger for en Microsoft Support-sag.
ms.openlocfilehash: 2759156a3948339629ea7d988eaaa5464da197fa
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095878"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Indsaml diagnosticeringsoplysninger i eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Nogle gange kræver Microsofts supportteknikere specifikke oplysninger om dit problem, når du åbner en supportsag, der er relateret til Microsoft Purview eDiscovery (Standard) eller Microsoft Purview eDiscovery (Premium). Denne artikel indeholder en vejledning i, hvordan du indsamler diagnosticeringsoplysninger for at hjælpe supportteknikere med at undersøge og løse problemer. Du behøver normalt ikke at indsamle disse oplysninger, før du bliver bedt om det af en Microsoft Support-tekniker.

> [!IMPORTANT]
> Outputtet fra de cmdlet'er og diagnosticeringsoplysninger, der er beskrevet i denne artikel, kan omfatte følsomme oplysninger om procesførelse eller interne undersøgelser i din organisation. Før du sender rå diagnosticeringsoplysninger til Microsoft Support, skal du gennemse oplysningerne og redigere eventuelle følsomme oplysninger (f.eks. navne eller andre oplysninger om parter i tvister eller undersøgelse) ved at erstatte dem med `XXXXXXX`. Hvis du bruger denne metode, kan Microsoft Support-teknikere også se, at oplysningerne er blevet redigeret.

## <a name="collect-diagnostic-information-for-ediscovery-standard"></a>Indsaml diagnosticeringsoplysninger for eDiscovery (Standard)

Indsamling af diagnosticeringsoplysninger til eDiscovery (Standard) er cmdlet-baseret, så du skal bruge Security & Compliance Center PowerShell. Følgende PowerShell-eksempler kører cmdlet'er og gemmer derefter outputtet i en angivet tekstfil. I de fleste supporttilfælde skal du kun køre en af disse kommandoer.

Hvis du vil køre følgende cmdlet'er, skal du [oprette forbindelse til Security & Compliance Center PowerShell</span>](/powershell/exchange/connect-to-scc-powershell). Når du har forbindelse, skal du køre en eller flere af følgende kommandoer og sørge for at erstatte pladsholdere med de faktiske objektnavne.

Når du har gennemset den genererede tekstfil og redigeret følsomme oplysninger, skal du sende dem til Den Microsoft Support-tekniker, der arbejder på din sag.

> [!NOTE]
> Du kan også køre kommandoerne i dette afsnit for at indsamle diagnosticeringsoplysninger for de søgninger og eksporter, der er angivet på siden **Indholdssøgning** på Microsoft Purview-overholdelsesportalen.

### <a name="collect-information-about-searches"></a>Indsaml oplysninger om søgninger

Følgende kommando indsamler oplysninger, der er nyttige, når du undersøger problemer med en indholdssøgning eller en søgning, der er knyttet til en eDiscovery-sag (Standard).

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Indsaml oplysninger om søgehandlinger

Følgende kommando indsamler oplysninger for at undersøge problemer med eksempelvisning, eksport eller sletning af resultaterne af en indholdssøgning eller en søgning, der er knyttet til en eDiscovery-sag (Standard). Du kan identificere navnet på søgehandlingen ved at klikke på en eksport, der er angivet under fanen **Eksporter** . Hvis du vil identificere navnene på eksempel- og tømningshandlinger, kan du køre **Get-ComplianceSearchAction-cmdlet'en** for at få vist en liste over alle handlinger. Formatet for navnet på søgehandlingen oprettes ved at tilføje `_Preview`, `_Export`eller `_Purge` til navnet på den tilsvarende søgning.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Indsaml oplysninger om eDiscovery-ventepositioner

Når en eDiscovery-venteposition, der er knyttet til en eDiscovery-sag (Standard), ikke fungerer som forventet, skal du køre følgende kommando for at indsamle oplysninger om politikken for sag venteposition og den tilknyttede regel for sag venteposition for eDiscovery-venteposition. *Politiknavnet Case hold* i følgende kommando er det samme som navnet på eDiscovery-ventepositionen. Du kan identificere dette navn under fanerne **Ventepositioner** i eDiscovery -sagen (Standard).

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Indsaml alle sagsoplysninger

Nogle gange er det ikke tydeligt, hvilke oplysninger Der kræves af Microsoft Support for at undersøge dit problem. I denne situation kan du indsamle alle diagnosticeringsoplysninger for en eDiscovery-sag (Standard). Navnet *på eDiscovery-sagen (Standard)* i følgende kommando er det samme som navnet på en sag, der vises på siden **eDiscovery (Standard)** på overholdelsesportalen.

```powershell
Get-ComplianceCase "<eDiscovery (Standard) case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-ediscovery-premium"></a>Indsaml diagnosticeringsoplysninger for eDiscovery (Premium)

Under fanen **Indstillinger** i en eDiscovery-sag (Premium) kan du hurtigt kopiere diagnosticeringsoplysningerne for sagen. Diagnosticeringsoplysningerne gemmes i Udklipsholder, så du kan indsætte dem i en tekstfil og sende dem til Microsoft Support.

1. Gå til overholdelsesportalen, og vælg **eDiscoveryAvanceret** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. Vælg en sag, og klik derefter på fanen **Indstillinger**.

3. Klik på **Vælg** under **Sagsoplysninger**.

4. Klik på **HandlingerKopiér**  >  supportoplysninger på pop op-siden for at kopiere oplysningerne til Udklipsholder.

5. Åbn en tekstfil (i Notesblok), og indsæt derefter oplysningerne i tekstfilen.

6. Gem tekstfilen, `AeD Diagnostic Info 2020.11.03`og navngiv den noget i stil `AeD Diagnostic Info YYYY.MM.DD` med (f.eks. ).

Når du har gennemset filen og redigeret følsomme oplysninger, skal du sende dem til Den Microsoft Support-tekniker, der arbejder på din sag.
