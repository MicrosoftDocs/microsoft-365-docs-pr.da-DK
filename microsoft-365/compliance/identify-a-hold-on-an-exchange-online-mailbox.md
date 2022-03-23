---
title: Sådan identificeres den type venteposition, der er sat på en Exchange Online postkasse
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du identificerer de forskellige typer venteposition, der kan placeres i en Exchange Online i Microsoft 365.
ms.openlocfilehash: 0ad2a1a4479c2de667b23ee29ee321912e7d18e9
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63587479"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Sådan identificeres den type venteposition, der er sat på en Exchange Online postkasse

I denne artikel forklares det, hvordan du kan identificere Exchange Online postkasser i Microsoft 365.

Microsoft 365 på flere måder, som organisationen kan forhindre postkasseindhold i at blive slettet permanent på. Dette giver din organisation mulighed for at bevare indhold, så det opfylder overholdelsesreglerne eller under juridiske og andre typer undersøgelser. Her er en liste over opbevaringsfunktionerne (også kaldet *ventende funktioner*) i Office 365:

- **[Retslig venteposition](create-a-litigation-hold.md):** Ventende funktioner, der anvendes til brugerpostkasser i Exchange Online.

- **[eDiscovery hold](create-ediscovery-holds.md):** Vente hold, der er knyttet til en core eDiscovery-sag i Security and Compliance Center. eDiscovery-ventende funktioner kan anvendes på brugerpostkasser og den tilsvarende postkasse til Microsoft 365 Grupper og Microsoft Teams.

- **[Direkte](/Exchange/security-and-compliance/create-or-remove-in-place-holds) hold:** Ventepositioner, der anvendes på brugerpostkasser ved hjælp af værktøjet In-Place eDiscovery & Hold <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a> i Exchange Online. 

   > [!NOTE]
   > In-Place ventende funktioner er udgået, og du kan ikke længere In-Place ventende funktioner eller anvende dem i postkasser. Ventende In-Place kan dog stadig anvendes på postkasser i organisationen, hvilket er grunden til, at de er inkluderet i denne artikel. Få mere at vide under [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Microsoft 365 opbevaringspolitikker](retention.md):** Kan konfigureres til at bevare (eller bevare og derefter slette) indhold i brugerpostkasser i Exchange Online og i den tilsvarende postkasse til Microsoft 365 Groups og Microsoft Teams. Du kan også oprette en opbevaringspolitik for at bevare Skype for Business samtaler, der er gemt i brugerpostkasser.

  Der findes to typer af Microsoft 365 opbevaringspolitikker, der kan tildeles postkasser.

    - **Specifikke opbevaringspolitikker for placeringer:** Dette er politikker, der er tildelt indholdsplaceringer for bestemte brugere. Du kan bruge **Get-Mailbox-cmdlet'en** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker, der er tildelt til bestemte postkasser. Du kan finde flere oplysninger om denne type opbevaringspolitik i afsnittet En politik med specifikke medtagelser eller [undtagelser](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) fra dokumentationen for opbevaringspolitikken.

    - **Opbevaringspolitikker for hele organisationen:** Dette er politikker, der er tildelt til alle indholdsplaceringer i organisationen. Du kan bruge **get-OrganizationConfig-cmdlet'en** Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker for hele organisationen. Du kan finde flere oplysninger om denne type opbevaringspolitik i afsnittet En politik, der gælder for hele placeringer [fra](retention-settings.md#a-policy-that-applies-to-entire-locations) dokumentationen til opbevaringspolitikken.

- **[Microsoft 365 opbevaringsnavne](retention.md):** Hvis en bruger anvender en Microsoft 365-opbevaringsmærkat (en, der er konfigureret til at bevare indhold eller bevare og derefter slette indhold) på  en hvilken som helst mappe eller et element i sin postkasse, sættes en venteposition i postkassen, som om postkassen var sat i retslig tilbageholdelse eller tildelt en Microsoft 365-opbevaringspolitik. Du kan finde flere oplysninger i [afsnittet Identificere postkasser](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element i denne artikel.

Hvis du vil administrere postkasser i venteposition, skal du muligvis identificere den type venteposition, der er sat i en postkasse, så du kan udføre opgaver som f.eks. at ændre varigheden af venteposition, midlertidigt eller permanent fjerne ventepositionen eller udelade en postkasse fra en Microsoft 365-opbevaringspolitik. I disse tilfælde er det første trin at identificere typen af venteposition, der er sat på postkassen. Og fordi flere ventepositioner (og forskellige typer af ventepositioner) kan placeres i en enkelt postkasse, skal du identificere alle ventepositioner, der er sat i en postkasse, hvis du vil fjerne eller ændre en venteposition.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Trin 1: Hent GUID'et for ventende anbringes i en postkasse

Du kan køre følgende to cmdlet'er i Exchange Online PowerShell for at få GUID for de ventepositioner, der er placeret i en postkasse. Når du har fået et GUID, skal du bruge det til at identificere det specifikke venteposition i trin 2. En retslig venteposition identificeres ikke af et GUID. Retslig ventende proces er enten aktiveret eller deaktiveret for en postkasse.

- **Get-Mailbox:** Brug denne cmdlet til at afgøre, om retslig tilbageholdelse er aktiveret for en postkasse og til at få GUID'er til eDiscovery-ventepositioner, In-Place-ventepositioner og Microsoft 365-opbevaringspolitikker, der specifikt er tildelt en postkasse. Outputtet fra denne cmdlet angiver også, om en postkasse udtrykkeligt er udeladt af en opbevaringspolitik for hele organisationen.

- **Get-OrganizationConfig:** Brug denne cmdlet til at hente GUID'erne til opbevaringspolitikker for hele organisationen.

Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Kør følgende kommando for at få oplysninger om ventende og Microsoft 365 opbevaringspolitikker anvendt på en postkasse.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> Hvis der er for mange værdier i egenskaben InPlaceHolds, og ikke dem alle vises, `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` kan du køre kommandoen for at få vist hvert GUID på en separat linje.

I følgende tabel beskrives det, hvordan du identificerer forskellige typer ventende indhold baseret på værdierne i egenskaben *InPlaceHolds* , når du kører **Get-Mailbox-cmdlet'en** .

| Ventepositionstype                                                          | Eksempelværdi                                                                                  | Sådan identificeres ventepositionen                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Retslig venteposition                                                    | `True`                                                                                         | Retslig tilbageholdelse er aktiveret for en postkasse, når *egenskaben LitigationHoldEnabled* er angivet til `True`.                                                                                                                                                                                                                                         |
| eDiscovery hold                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | Egenskaben *InPlaceHolds* indeholder GUID for eventuelle ventepositioner, der er knyttet til en eDiscovery-sag i sikkerheds- og overholdelsescenteret. Du kan se, at dette er en eDiscovery-venteposition, fordi GUID'et `UniH` starter med præfikset (som angiver en samlet venteposition).                                                                                   |
| In-Place venteposition                                                      | `c0ba3ce811b6432a8751430937152491` <br/> eller <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | Egenskaben *InPlaceHolds* indeholder GUID'et for In-Place hold, der er placeret i postkassen. Du kan se, at dette In-Place et venteposition, fordi GUID'et enten ikke starter med et præfiks, eller det starter med præfikset `cld` .                                                                                                               |
| Microsoft 365 opbevaringspolitik, der specifikt gælder for postkassen | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> eller <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | Egenskaben InPlaceHolds indeholder GUID'er for en hvilken som helst bestemt opbevaringspolitik for placeringer, der anvendes på postkassen. Du kan identificere opbevaringspolitikker, fordi GUID'et starter med `mbx` eller præfikset `skp` . Præfikset `skp` angiver, at opbevaringspolitikken anvendes Skype for Business samtaler i brugerens postkasse. |
| Er udelukket fra en opbevaringspolitik for Microsoft 365 hele organisationen  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Hvis en postkasse er udelukket fra en Microsoft 365-opbevaringspolitik for hele organisationen, vises GUID'et for den opbevaringspolitik, som postkassen er udeladt fra, i egenskaben InPlaceHolds og identificeres `-mbx` af præfikset.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Hvis egenskaben *InPlaceHolds* er tom, når du kører **Cmdlet'en Get-Mailbox**, kan der stadig være en eller flere Microsoft 365-opbevaringspolitikker for postkassen. Kør følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få en liste over GUID'er til opbevaringspolitikker for Microsoft 365 hele organisationen.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> Hvis der er for mange værdier i egenskaben InPlaceHolds, og ikke dem alle vises, `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` kan du køre kommandoen for at få vist hvert GUID på en separat linje.

I følgende tabel beskrives de forskellige typer vente hold for hele organisationen, og hvordan du identificerer hver type baseret på GUID'erne, der er indeholdt i *egenskaben InPlaceHolds* , når du kører cmdlet'en **Get-OrganizationConfig** .

| Ventepositionstype                                                                                                | Eksempelværdi                           | Beskrivelse                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365 opbevaringspolitikker anvendt på Exchange postkasser, Exchange offentlige mapper og Teams chatsamtaler | `mbx7cfb30345d454ac0a989ab3041051209:2` | Opbevaringspolitikker for hele organisationen, som anvendes på Exchange-postkasser, Exchange offentlige mapper og 1xN-chats i Microsoft Teams, identificeres `mbx` af GUID'er, der starter med præfikset. Bemærk! 1xN-chats gemmes i de enkelte chatdeltageres postkasse.  |
| Microsoft 365 opbevaringspolitik anvendt på Microsoft 365 grupper og Teams kanalmeddelelser                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Opbevaringspolitikker gældende for hele organisationen Microsoft 365 grupper og kanalmeddelelser i Microsoft Teams af GUID'er, der starter med præfikset`grp`. Bemærk, at kanalmeddelelser gemmes i den gruppepostkasse, der er knyttet til et Microsoft-team. |

Du kan finde flere oplysninger om opbevaringspolitikker, der Microsoft Teams opbevaringspolitikker, i [Få mere at vide om opbevaringspolitikker for Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Forstå formatet af InPlaceHolds-værdien for opbevaringspolitikker

Ud over præfikset (mbx, skp eller grp), der identificerer et element i egenskaben InPlaceHolds som en Microsoft 365-opbevaringspolitik, indeholder værdien også et suffiks, der identificerer den type opbevaringshandling, der er konfigureret til politikken. Eksempelvis er handlingens suffiks fremhævet med fed skrift i følgende eksempler:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

Følgende tabel definerer de tre mulige opbevaringshandlinger:

| Værdi | Beskrivelse                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Angiver, at opbevaringspolitikken er konfigureret til at slette elementer. Politikken bevarer ikke elementer.                                  |
| **2** | Angiver, at opbevaringspolitikken er konfigureret til at indeholde elementer. Politikken sletter ikke elementer, når en opbevaringsperiode udløber. |
| **3** | Angiver, at opbevaringspolitikken er konfigureret til at indeholde elementer og derefter slette dem, når en opbevaringsperiode udløber.             |

Du kan finde flere oplysninger om opbevaringshandlinger [i afsnittet Opbevaring af indhold for en bestemt](retention-settings.md#retaining-content-for-a-specific-period-of-time) tidsperiode.
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Trin 2: Brug GUID'et til at identificere ventepositionen

Når du har anskaffet GUID'et for en venteposition, der anvendes på en postkasse, er næste trin at bruge det pågældende GUID til at identificere ventepositionen. I de følgende afsnit kan du se, hvordan du kan identificere navnet på ventepositionen (og andre oplysninger) ved hjælp af ventepositions-GUID'et.

### <a name="ediscovery-holds"></a>eDiscovery-vente hold

Kør følgende kommandoer i Security & Compliance Center PowerShell for at identificere en eDiscovery-venteposition, der anvendes til postkassen. Brug GUID'et (herunder ikke UniH-præfikset) for den eDiscovery-venteposition, som du identificerede i trin 1. 

Hvis du vil oprette forbindelse & Security & Compliance Center PowerShell, [skal du Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

Den første kommando opretter en variabel, der indeholder oplysninger om ventepositionen. Denne variabel bruges i de andre kommandoer. Den anden kommando viser navnet på den eDiscovery-sag, som ventepositionen er knyttet til. Den tredje kommando viser navnet på ventepositionen og en liste over de postkasser, ventepositionen gælder for.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place ventende del

Kør følgende kommando i Exchange Online PowerShell for at identificere In-Place hold, der anvendes til postkassen. Brug GUID'et for In-Place venteposition, som du identificerede i trin 1. Kommandoen viser navnet på ventepositionen og en liste over de postkasser, ventepositionen gælder for.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Hvis GUID'et for In-Place sættet `cld` i venteposition med præfikset, skal du sørge for at medtage præfikset, når du kører den forrige kommando.

> [!IMPORTANT]
> Efterhånden som vi fortsætter med at investere på forskellige måder for at bevare postkasseindhold, annoncerer vi tilbagetrækningen af In-Place-ventende beløb i Exchange Administration (EAC). Fra den 1. juli 2020 kan du ikke oprette nye In-Place i Exchange Online. Men du vil stadig kunne administrere In-Place ventepositioner i EAC eller ved hjælp af **Set-MailboxSearch-cmdlet'en** Exchange Online PowerShell. Men fra den 1. oktober 2020 kan du ikke administrere de In-Place hold. Du kan kun fjerne dem i EAC eller ved hjælp af **cmdlet'en Remove-MailboxSearch** . Du kan finde flere oplysninger om tilbagetrækningen In-Place ventende funktioner i [Tilbagetrækning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365 opbevaringspolitikker

[Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell), og kør følgende kommando for at identitete den Microsoft 365-opbevaringspolitik (organisation for hele organisationen eller en bestemt placering), der anvendes til postkassen. Brug GUID'et (ikke inklusive præfikset mbx, skp eller grp eller handlingens suffiks), som du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identificere postkasser i venteposition, fordi en opbevaringsetiket er blevet anvendt på en mappe eller et element

Når en bruger anvender et opbevaringsnavn, der er konfigureret  til at  bevare eller bevare og derefter slette indhold i en mappe eller et element i sin postkasse, så er *complianceTagHoldApplied-postkasseegenskaben* indstillet til **Sand**. Når dette sker, behandles postkassen på samme måde, som hvis den var sat i venteposition, f.eks. når den er tildelt en Microsoft 365-opbevaringspolitik eller placeres i Retslig tilbageholdelse, men med nogle advarselsforanstaltninger. Når egenskaben *ComplianceTagHoldApplied* er angivet til **Sand**, sker følgende:

- Hvis postkassen eller brugerens konto Microsoft 365, bliver postkassen en [inaktiv postkasse](inactive-mailboxes-in-office-365.md).
- Du kan ikke deaktivere postkassen (enten den primære postkasse eller arkivpostkassen, hvis den er aktiveret).
- Elementer, der er blevet slettet fra postkassen, følger en af to stier, afhængigt af om de er mærket eller ej:
    - **Elementer uden navn følger den** samme sti, som slettede elementer bruger, når der ikke er ventende elementer for postkassen.  Den tid, det tager for disse elementer at blive slettet permanent, bestemmes af opbevaringskonfigurationen af slettede elementer, og [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) om gendannelse af et enkelt element er aktiveret for postkassen eller ej.[](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention)
    - **Mærkede elementer** bevares i mappen med [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) genoprettelige elementer på samme måde, som de ville være, hvis en Microsoft 365 opbevaringspolitik anvendt, men på det individuelle elementniveau.  Hvis flere elementer har forskellige etiketter, der er konfigureret  til at  bevare eller bevare og derefter slette indhold med forskellige intervaller, bevares hvert element baseret på konfigurationen af den anvendte etiket.
- Andre ventepositioner, f.eks. Microsoft 365 opbevaringspolitikker, ventepositioner i eDiscovery eller retslig tilbageholdelse, kan forlænge, hvor længe etikette elementer bevares ud fra principperne [for opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence).

For at få vist værdien af *egenskaben ComplianceTagHoldApplied* for en enkelt postkasse skal du køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Du kan finde flere oplysninger om opbevaringsnavne under [Opbevaringsnavne](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Administration af postkasser i venteposition

Når en hvilken som helst type venteposition fjernes fra en postkasse, anvendes *der en forsinkelses hold* . Det betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre data i at blive slettet permanent (slettet) fra postkassen. Dette giver administratorer mulighed for at søge efter eller gendanne postkasseelementer, der vil blive slettet, når en venteposition er fjernet. En forsinkelse er placeret i en postkasse, næste gang den administrerede mappeassistent behandler postkassen og registrerer, at en venteposition er blevet fjernet. Specifikt anvendes en forsinkelse i venteposition på en postkasse, når Den administrerede mappeassistent indstiller en af følgende postkasseegenskaber til **Sand**:

- **ForsinkelseHoldApplied:** Denne egenskab gælder for mailrelateret indhold (der genereres af personer, Outlook Outlook på internettet), der er gemt i en brugers postkasse.

- **DelayReleaseHoldApplied:** Denne egenskab gælder for skybaseret indhold (genereres af ikke-Outlook-apps som Microsoft Teams, Microsoft Forms og Microsoft Yammer), der er gemt i en brugers postkasse. Skydata, der genereres af en Microsoft-app, gemmes typisk i en skjult mappe i en brugers postkasse.

Når en forsinkelse er sat i venteposition i postkassen (når en af de forrige egenskaber er angivet til **Sand), betragtes** postkassen stadig som værende i venteposition i ubegrænset tid, som hvis postkassen var i retslig venteposition. Efter 30 dage udløber forsinkelsen, og Microsoft 365 forsøger automatisk at fjerne forsinkelses ventepositionen (ved at indstille egenskaben DelayHoldApplied eller DelayReleaseHoldApplied til **Falsk**), så ventepositionen fjernes. Når en af disse egenskaber er angivet til **Falsk, fjernes** de tilsvarende elementer, der er markeret til fjernelse, næste gang postkassen behandles af den administrerede mappeassistent.

Hvis du vil have vist værdierne for egenskaberne DelayHoldApplied og DelayReleaseHoldApplied for en postkasse, skal du køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Hvis du vil fjerne forsinkelsen, før den udløber, kan du køre en (eller begge) følgende kommandoer i Exchange Online PowerShell, afhængigt af hvilken egenskab du vil ændre:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Eller

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Du skal være tildelt rollen Juridisk tilbageholdelse i Exchange Online for at bruge *parametrene RemoveDelayHoldApplied* eller *RemoveDelayReleaseHoldApplied*. 

Hvis du vil fjerne forsinkelsen i en inaktiv postkasse, skal du køre en af følgende kommandoer i Exchange Online PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Eller

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Den bedste måde at angive en inaktiv postkasse på i den forrige kommando er at bruge værdien Distinguished Name Exchange GUID. Brug af en af disse værdier hjælper med at forhindre utilsigtet angivelse af den forkerte postkasse. 

Du kan finde flere oplysninger om brug af disse parametre til administration af ventende forsinkelse [under Set-Mailbox](/powershell/module/exchange/set-mailbox).

Vær opmærksom på følgende, når du administrerer en postkasse i venteposition:

- Hvis enten egenskaben DelayHoldApplied eller DelayReleaseHoldApplied er angivet til Sand, og en postkasse (eller den tilsvarende brugerkonto) slettes, bliver postkassen til en inaktiv postkasse. Det skyldes, at en postkasse betragtes som sat i venteposition **, hvis** en af egenskaberne er angivet til Sand, og hvis du sletter en postkasse i venteposition, resulterer det i en inaktiv postkasse. Hvis du vil slette en postkasse og ikke gøre den til en inaktiv postkasse, skal du angive begge egenskaber til **Falsk**.

- Som nævnt tidligere betragtes en postkasse som værende sat i venteposition i et ubegrænset tidsrum, hvis enten egenskaben DelayHoldApplied eller DelayReleaseHoldApplied er angivet til **Sand**. Men det betyder ikke, at *alt* indhold i postkassen bevares. Det afhænger af den værdi, der er angivet for hver egenskab. Lad os f.eks. sige, at begge egenskaber er angivet til **Sand** , fordi ventende indstillinger fjernes fra postkassen. Derefter fjerner du kun forsinkelses hold, der anvendes på ikke-Outlook skydata (ved hjælp af *parameteren RemoveDelayReleaseHoldApplied*). Næste gang den administrerede mappeassistent behandler postkassen, fjernes de ikke-Outlook elementer, der er markeret til fjernelse. Alle Outlook elementer, der er markeret til fjernelse, vil ikke blive fjernet, fordi egenskaben DelayHoldApplied stadig er angivet til **Sand**. Det modsatte ville også være sandt: hvis DelayHoldApplied er angivet til **Falsk****, og** DelayReleaseHoldApplied er angivet til Sand, vil kun Outlook elementer, der er markeret til fjernelse, blive fjernet.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Sådan bekræftes det, at en opbevaringspolitik for hele organisationen anvendes på en postkasse

Når en opbevaringspolitik for hele organisationen anvendes eller fjernes til en postkasse, kan du ved at eksportere diagnosticeringslogfilerne for postkassen være sikker på, at Exchange Online faktisk har anvendt eller fjernet opbevaringspolitikken for postkassen. For at få vist disse oplysninger skal du først validere et par ting ved hjælp [Exchange Online Powershell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Hent GUID'erne for eventuelle opbevaringspolitikker, der udtrykkeligt er anvendt på en postkasse

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Hent GUID'erne for alle opbevaringspolitikker, der gælder for postkasser for hele organisationen

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>Hent Postkassediagnosticering til HoldTracking

Diagnosticeringslogfilerne til Ventepositionspostkasse vedligeholder en historik over de ventepositioner, der anvendes på en brugerpostkasse.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Gennemse resultaterne af postkassediagnosticeringslogfilerne

Hvis du indsamler data fra det forrige trin, ser de resulterende data muligvis sådan ud:

> **ed**`  : 0001-01-01T00:00:00.0000000`
>  **hid**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **ht**`  : 4`
>  **lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **osd**` : 2020-03-23T18:24:37.1884606Z`

Brug tabellen nedenfor til at hjælpe dig med at forstå hver af de tidligere værdier, der er angivet i diagnosticeringsloggen.

| Værdi   | Beskrivelse |
|:------- |:----------- |
| **ed**  | Angiver Slutdatoen, som er den dato, hvor opbevaringspolitikken blev deaktiveret. MinValue betyder, at politikken stadig er tildelt til postkassen. |
| **hid** | Angiver GUID'et for opbevaringspolitikken. Denne værdi korrelerer med de GUID'er, du har indsamlet for de eksplicitte eller hele organisationen opbevaringspolitikker, der er tildelt postkassen.|
| **lsd** | Angiver Den sidste startdato, som er den dato, som opbevaringspolitikken blev tildelt til postkassen.|
| **osd** | Angiver den oprindelige startdato, som er den dato, Exchange de første registrerede oplysninger om opbevaringspolitikken. |
|||

Når en opbevaringspolitik ikke længere anvendes på en postkasse, anbringer vi en midlertidig forsinkelse i venteposition for brugeren for at forhindre udrømning af indhold. En forsinkelse i venteposition kan deaktiveres ved at køre `Set-Mailbox -RemoveDelayHoldApplied` kommandoen.

## <a name="next-steps"></a>Næste trin

Når du har identificeret de ventepositioner, der er anvendt på en postkasse, kan du udføre opgaver som f.eks. at ændre varigheden af ventepositionen, midlertidigt eller permanent fjerne ventepositionen eller udelade en inaktiv postkasse fra en Microsoft 365 opbevaringspolitik. Hvis du vil have mere at vide om at udføre opgaver, der er relateret til ventende opgaver, skal du se et af følgende emner:

- Kør [kommandoen Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) i [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at udelukke en postkasse fra en Microsoft 365 opbevaringspolitik for hele organisationen. Denne kommando kan kun bruges til opbevaringspolitikker, hvor værdien for *egenskaben ExchangeLocation er* lig med `All`.

- [Ændre varigheden af ventepositionen for en inaktiv postkasse](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md)

- [Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
