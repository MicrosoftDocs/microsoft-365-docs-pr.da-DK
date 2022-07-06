---
title: Sådan identificerer du ventepositionen på en Exchange Online postkasse
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du identificerer de forskellige typer venteposition, der kan placeres i en Exchange Online postkasse i Microsoft 365.
ms.openlocfilehash: d7a174d267897f37fa113a51e138ec68def65b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638295"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Sådan identificeres den type venteposition, der er placeret i en Exchange Online postkasse

I denne artikel forklares det, hvordan du identificerer ventepositioner, der er placeret på Exchange Online postkasser i Microsoft 365.

Microsoft 365 indeholder flere måder, som din organisation kan forhindre, at postkasseindhold slettes permanent. Dette gør det muligt for din organisation at bevare indhold for at overholde angivne standarder eller under juridiske og andre typer undersøgelser. Her er en liste over opbevaringsfunktionerne (også kaldet *ventepositioner*) i Office 365:

- **[Venteposition for procesførelse](create-a-litigation-hold.md):** Ventepositioner, der anvendes på brugerpostkasser i Exchange Online.

- **[eDiscovery-venteposition](create-ediscovery-holds.md):** Ventepositioner, der er knyttet til et Microsoft Purview eDiscovery (Standard)-tilfælde i Security and Compliance Center. eDiscovery-ventepositioner kan anvendes på brugerpostkasser og på den tilsvarende postkasse for Microsoft 365-grupper og Microsoft Teams.

- **[Bevarelse på stedet](/Exchange/security-and-compliance/create-or-remove-in-place-holds):** Ventepositioner, der anvendes på brugerpostkasser ved hjælp af værktøjet In-Place eDiscovery & Venteposition i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> i Exchange Online. 

   > [!NOTE]
   > In-Place Ventepositioner er udgået, og du kan ikke længere oprette In-Place Ventepositioner eller anvende dem på postkasser. Men In-Place Ventepositioner kan stadig anvendes på postkasser i din organisation, og derfor er de inkluderet i denne artikel. Du kan finde flere oplysninger under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Microsoft 365-opbevaringspolitikker](retention.md):** Kan konfigureres til at bevare (eller bevare og derefter slette) indhold i brugerpostkasser i Exchange Online og i den tilsvarende postkasse for Microsoft 365-grupper og Microsoft Teams. Du kan også oprette en opbevaringspolitik for at bevare Skype for Business Samtaler, der er gemt i brugerpostkasser.

  Der er to typer opbevaringspolitikker for Microsoft 365, som kan tildeles til postkasser.

    - **Specifikke politikker for placeringsopbevaring:** Dette er politikker, der er tildelt bestemte brugeres indholdsplaceringer. Du kan bruge **Get-Mailbox-cmdlet'en** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker, der er tildelt til bestemte postkasser. Du kan få flere oplysninger om denne type opbevaringspolitik i afsnittet [En politik med specifikke medtagelser eller udeladelser](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) fra dokumentationen til opbevaringspolitikken.

    - **Opbevaringspolitikker for hele organisationen:** Dette er politikker, der er tildelt til alle indholdsplaceringer i din organisation. Du kan bruge cmdlet'en **Get-OrganizationConfig** i Exchange Online PowerShell til at få oplysninger om opbevaringspolitikker for hele organisationen. Du kan få flere oplysninger om denne type opbevaringspolitik i afsnittet [En politik, der gælder for hele placeringer](retention-settings.md#a-policy-that-applies-to-entire-locations) fra dokumentationen til opbevaringspolitikken.

- **[Microsoft 365-opbevaringsmærkater](retention.md):** Hvis en bruger anvender en Microsoft 365-opbevaringsmærkat (en, der er konfigureret til at bevare indhold eller bevare og derefter slette indhold) på *en mappe* eller et element i deres postkasse, placeres der en venteposition på postkassen, som om postkassen blev sat i retslig venteposition eller tildelt en Microsoft 365-opbevaringspolitik. Du kan finde flere oplysninger i afsnittet [Identificere postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) i denne artikel.

Hvis du vil administrere postkasser i venteposition, skal du muligvis identificere den type venteposition, der er placeret i en postkasse, så du kan udføre opgaver, f.eks. ændre varigheden af ventepositionen, midlertidigt eller permanent fjerne ventepositionen eller udelade en postkasse fra en Microsoft 365-opbevaringspolitik. I disse tilfælde er det første trin at identificere den type venteposition, der er placeret i postkassen. Og da flere ventepositioner (og forskellige typer ventepositioner) kan placeres i en enkelt postkasse, skal du identificere alle ventepositioner, der er placeret i en postkasse, hvis du vil fjerne eller ændre en venteposition.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Trin 1: Hent GUID'et for ventepositioner, der er placeret i en postkasse

Du kan køre følgende to cmdlet'er i Exchange Online PowerShell for at få GUID for de ventepositioner, der er placeret i en postkasse. Når du har fået et GUID, kan du bruge det til at identificere den specifikke venteposition i trin 2. En procesførelsesventeposition identificeres ikke af et GUID. Retsførelse ventepositioner er enten aktiveret eller deaktiveret for en postkasse.

- **Hent postkasse:** Brug denne cmdlet til at bestemme, om procesførelsesholdning er aktiveret for en postkasse, og til at hente GUID'erne for eDiscovery-ventepositioner, In-Place ventepositioner og Microsoft 365-opbevaringspolitikker, der specifikt er tildelt til en postkasse. Outputtet af denne cmdlet angiver også, om en postkasse udtrykkeligt er blevet udelukket fra en opbevaringspolitik for hele organisationen.

- **Get-OrganizationConfig:** Brug denne cmdlet til at hente GUID'erne for opbevaringspolitikker for hele organisationen.

Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Kør følgende kommando for at få oplysninger om de ventepositioner og Microsoft 365-opbevaringspolitikker, der er anvendt på en postkasse.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> Hvis der er for mange værdier i egenskaben InPlaceHolds, og ikke alle af dem vises, kan du køre `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` kommandoen for at få vist hvert GUID på en separat linje.

I følgende tabel beskrives det, hvordan du identificerer forskellige typer ventepositioner baseret på værdierne i egenskaben *InPlaceHolds* , når du kører cmdlet'en **Get-Mailbox** .

| Ventepositionstype                                                          | Eksempelværdi                                                                                  | Sådan identificerer du ventepositionen                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Procesførelse - venteposition                                                    | `True`                                                                                         | Procesførelse i venteposition er aktiveret for en postkasse, når egenskaben *LitigationHoldEnabled* er angivet til `True`.                                                                                                                                                                                                                                         |
| eDiscovery-venteposition                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | *Egenskaben InPlaceHolds* indeholder GUID'et for alle ventepositioner, der er knyttet til en eDiscovery-sag i Sikkerheds- og overholdelsescenter. Du kan se, at dette er en eDiscovery-venteposition, fordi GUID'et starter med præfikset `UniH` (hvilket angiver en Unified Venteposition).                                                                                   |
| In-Place venteposition                                                      | `c0ba3ce811b6432a8751430937152491` <br/> Eller <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | Egenskaben *InPlaceHolds* indeholder GUID'et for den In-Place venteposition, der er placeret i postkassen. Du kan se, at dette er en In-Place Venteposition, fordi GUID enten ikke starter med et præfiks, eller fordi det starter med præfikset `cld` .                                                                                                               |
| Microsoft 365-opbevaringspolitik, der specifikt er anvendt på postkassen | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> Eller <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | Egenskaben InPlaceHolds indeholder GUID'er for en hvilken som helst specifik opbevaringspolitik for placering, der anvendes på postkassen. Du kan identificere opbevaringspolitikker, fordi GUID'et starter med `mbx` præfikset `skp` eller . Præfikset `skp` angiver, at opbevaringspolitikken anvendes på Skype for Business samtaler i brugerens postkasse. |
| Udelukket fra en Microsoft 365-opbevaringspolitik for hele organisationen  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Hvis en postkasse udelades fra en Microsoft 365-opbevaringspolitik for hele organisationen, vises GUID'et for den opbevaringspolitik, som postkassen er udelukket fra, i egenskaben InPlaceHolds og identificeres af præfikset `-mbx` .                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Hvis egenskaben *InPlaceHolds* er tom, når du kører **Get-Mailbox-cmdlet'en** , kan der stadig være anvendt en eller flere Microsoft 365-opbevaringspolitikker for hele organisationen på postkassen. Kør følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få en liste over GUID'er for microsoft 365-opbevaringspolitikker for hele organisationen.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> Hvis der er for mange værdier i egenskaben InPlaceHolds, og ikke alle af dem vises, kan du køre `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` kommandoen for at få vist hvert GUID på en separat linje.

I følgende tabel beskrives de forskellige typer ventepositioner for hele organisationen, og hvordan du identificerer hver type baseret på GUID'erne i egenskaben *InPlaceHolds* , når du kører cmdlet'en **Get-OrganizationConfig** .

| Ventepositionstype                                                                                                | Eksempelværdi                           | Beskrivelse                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365-opbevaringspolitikker, der anvendes på Exchange-postkasser, offentlige Exchange-mapper og Teams-chats | `mbx7cfb30345d454ac0a989ab3041051209:2` | Opbevaringspolitikker for hele organisationen, der anvendes på Exchange-postkasser, offentlige Exchange-mapper og 1xN-chats i Microsoft Teams, identificeres af GUID'er, der starter med præfikset `mbx` . Note 1xN-chats gemmes i de enkelte chatdeltageres postkasse.  |
| Microsoft 365-opbevaringspolitik anvendt på Microsoft 365-grupper- og Teams-kanalmeddelelser                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Opbevaringspolitikker for hele organisationen, der anvendes på Microsoft 365-grupper og kanalmeddelelser i Microsoft Teams, identificeres af GUID'er, der starter med præfikset `grp` . Meddelelser på notekanalen gemmes i den gruppepostkasse, der er knyttet til et Microsoft-team. |

Du kan finde flere oplysninger om opbevaringspolitikker, der anvendes på Microsoft Teams, under [Få mere at vide om opbevaringspolitikker for Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Om formatet af værdien InPlaceHolds for opbevaringspolitikker

Ud over præfikset (mbx, skp eller grp), der identificerer et element i egenskaben InPlaceHolds som en Microsoft 365-opbevaringspolitik, indeholder værdien også et suffiks, der identificerer den type opbevaringshandling, der er konfigureret for politikken. Handlingssuffikset er f.eks. fremhævet med fed i følgende eksempler:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

I følgende tabel defineres de tre mulige opbevaringshandlinger:

| Værdi | Beskrivelse                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Angiver, at opbevaringspolitikken er konfigureret til at slette elementer. Politikken bevarer ikke elementer.                                  |
| **2** | Angiver, at opbevaringspolitikken er konfigureret til at indeholde elementer. Politikken sletter ikke elementer, når opbevaringsperioden udløber. |
| **3** | Angiver, at opbevaringspolitikken er konfigureret til at indeholde elementer og derefter slette dem, når opbevaringsperioden udløber.             |

Du kan få flere oplysninger om opbevaringshandlinger i afsnittet [Bevarelse af indhold i en bestemt tidsperiode](retention-settings.md#retaining-content-for-a-specific-period-of-time) .
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Trin 2: Brug GUID'et til at identificere ventepositionen

Når du har fået GUID'et for en venteposition, der er anvendt på en postkasse, er det næste trin at bruge guid'et til at identificere ventepositionen. I følgende afsnit kan du se, hvordan du identificerer navnet på ventepositionen (og andre oplysninger) ved hjælp af GUID'et for ventepositionen.

### <a name="ediscovery-holds"></a>eDiscovery-ventepositioner

Kør følgende kommandoer i Security & Compliance PowerShell for at identificere en eDiscovery-venteposition, der er anvendt på postkassen. Brug GUID (inklusive ikke UniH-præfikset) for den eDiscovery-venteposition, du identificerede i trin 1. 

Hvis du vil oprette forbindelse til PowerShell til & overholdelse af angivne standarder, skal du se [Opret forbindelse til PowerShell til sikkerhed & overholdelse](/powershell/exchange/connect-to-scc-powershell).

Den første kommando opretter en variabel, der indeholder oplysninger om ventepositionen. Denne variabel bruges i de andre kommandoer. Den anden kommando viser navnet på den eDiscovery-sag, som ventepositionen er knyttet til. Den tredje kommando viser navnet på ventepositionen og en liste over de postkasser, som ventepositionen gælder for.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place ventepositioner

Kør følgende kommando i Exchange Online PowerShell for at identificere den In-Place venteposition, der er anvendt på postkassen. Brug GUID'et for den In-Place venteposition, som du identificerede i trin 1. Kommandoen viser navnet på ventepositionen og en liste over de postkasser, som ventepositionen gælder for.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Hvis GUID'et for den In-Place Venteposition starter med præfikset `cld` , skal du sørge for at medtage præfikset, når du kører den forrige kommando.

> [!IMPORTANT]
> Da vi fortsætter med at investere på forskellige måder for at bevare postkasseindhold, annoncerer vi, at In-Place ventepositioner udgår i Exchange Administration (EAC). Fra og med den 1. juli 2020 kan du ikke oprette nye In-Place Ventepositioner i Exchange Online. Men du kan stadig administrere In-Place Ventepositioner i EAC eller ved hjælp af **Set-MailboxSearch-cmdlet'en** i Exchange Online PowerShell. Fra den 1. oktober 2020 kan du dog ikke administrere In-Place ventepositioner. Du kan kun fjerne dem i EAC eller ved hjælp af cmdlet'en **Remove-MailboxSearch** . Du kan finde flere oplysninger om udfasning af In-Place ventepositioner under [Udfasning af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365-opbevaringspolitikker

[Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) , og kør følgende kommando for at identificere den Microsoft 365-opbevaringspolitik (for hele organisationen eller en bestemt placering), der er anvendt på postkassen. Brug guid'et (inklusive ikke præfikset mbx, skp eller grp eller det handlingssuffiks), du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identificerer postkasser i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element

Når en bruger anvender en opbevaringsmærkat, der er konfigureret til at *bevare* eller *bevare og derefter slette* indhold til en mappe eller et element i sin postkasse, angives egenskaben *ComplianceTagHoldApplied* for postkassen til **Sand**. Når det sker, behandles postkassen på samme måde, som hvis den blev sat i venteposition, f.eks. når den er tildelt en Opbevaringspolitik for Microsoft 365 eller er sat i procesventevent, men med nogle advarsler. Når egenskaben *ComplianceTagHoldApplied* er angivet til **Sand**, sker følgende ting:

- Hvis postkassen eller brugerens Microsoft 365-konto slettes, bliver postkassen en [inaktiv postkasse](inactive-mailboxes-in-office-365.md).
- Du kan ikke deaktivere postkassen (enten den primære postkasse eller arkivpostkassen, hvis den er aktiveret).
- Elementer, der er blevet slettet fra postkassen, følger én af to stier, afhængigt af om de er forsynet med mærkater eller ej:
    - **Elementer, der ikke er navngivet** , følger den samme sti, som slettede elementer benytter, når der ikke er nogen ventepositioner for postkassen.  Den tid, det tager at slette disse elementer permanent, bestemmes af konfigurationen af [opbevaring af slettede elementer](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) , og om [gendannelse af enkelte elementer](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) er aktiveret for postkassen eller ej.
    - **Navngivne elementer** bevares i [mappen elementer, der kan gendannes](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) , på samme måde, som hvis der anvendes en Microsoft 365-opbevaringspolitik, men på individuelt elementniveau.  Hvis flere elementer har forskellige mærkater, der er konfigureret til at *bevare* eller *bevare og derefter slette* indhold med forskellige intervaller, bevares hvert element baseret på konfigurationen af den anvendte mærkat.
- Andre ventepositioner, f.eks. Microsoft 365-opbevaringspolitikker, eDiscovery-bevarelse eller procesførelse, kan forlænge, hvor længe mærkede elementer bevares, baseret på [principperne for opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence).

Hvis du vil have vist værdien af egenskaben *ComplianceTagHoldApplied* for en enkelt postkasse, skal du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Du kan få flere oplysninger om opbevaringsmærkater under [Opbevaringsmærkater](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Administration af postkasser i forsinkelsesventeposition

Når en hvilken som helst type venteposition er fjernet fra en postkasse, anvendes der en *forsinkelsesventeposition* . Det betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre, at data slettes permanent (fjernes) fra postkassen. Dette giver administratorer mulighed for at søge efter eller gendanne postkasseelementer, der fjernes, når en venteposition er fjernet. Der placeres en forsinkelse i en postkasse, næste gang Assistent til administreret mappe behandler postkassen og registrerer, at en venteposition er fjernet. Der anvendes specifikt forsinkelse på en postkasse, når Assistent til administreret mappe angiver en af følgende postkasseegenskaber til **Sand**:

- **DelayHoldApplied:** Denne egenskab gælder for mailrelateret indhold (genereret af personer, der bruger Outlook og Outlook på internettet), som er gemt i en brugers postkasse.

- **DelayReleaseHoldApplied:** Denne egenskab gælder for skybaseret indhold (genereret af ikke-Outlook-apps, f.eks. Microsoft Teams, Microsoft Forms og Microsoft Yammer), der er gemt i en brugers postkasse. Clouddata, der genereres af en Microsoft-app, gemmes typisk i en skjult mappe i en brugers postkasse.

Når der er placeret en forsinkelse i postkassen (når en af de forrige egenskaber er angivet til **Sand**), anses postkassen stadig for at være i venteposition i ubegrænset varighed, som om postkassen var i procesretlig venteposition. Efter 30 dage udløber forsinkelsesventetiden, og Microsoft 365 forsøger automatisk at fjerne forsinkelsen (ved at angive egenskaben DelayHoldApplied eller DelayReleaseHoldApplied til **Falsk**), så ventepositionen fjernes. Når en af disse egenskaber er angivet til **Falsk**, fjernes de tilsvarende elementer, der er markeret til fjernelse, næste gang postkassen behandles af Assistent til administrerede mapper.

Hvis du vil have vist værdierne for egenskaberne DelayHoldApplied og DelayReleaseHoldApplied for en postkasse, skal du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

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

Du skal være tildelt rollen Juridisk venteposition i Exchange Online for at bruge parametrene *RemoveDelayHoldApplied* eller *RemoveDelayReleaseHoldApplied*. 

Hvis du vil fjerne forsinkelsen i en inaktiv postkasse, skal du køre en af følgende kommandoer i Exchange Online PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Eller

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Den bedste måde at angive en inaktiv postkasse i den forrige kommando på er ved at bruge værdien Entydigt navn eller Exchange GUID. Brug af en af disse værdier hjælper med at forhindre, at den forkerte postkasse angives ved et uheld. 

Du kan få flere oplysninger om, hvordan du bruger disse parametre til administration af forsinkelsespositioner, i [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Vær opmærksom på følgende ting, når du administrerer en postkasse i forsinkelsesventeposition:

- Hvis enten egenskaben DelayHoldApplied eller DelayReleaseHoldApplied er angivet til **Sand** , og en postkasse (eller den tilsvarende brugerkonto) slettes, bliver postkassen en inaktiv postkasse. Det skyldes, at en postkasse anses for at være i venteposition, hvis en af egenskaberne er angivet til **Sand**, og sletning af en postkasse i venteposition resulterer i en inaktiv postkasse. Hvis du vil slette en postkasse og ikke gøre den til en inaktiv postkasse, skal du angive begge egenskaber til **Falsk**.

- Som tidligere angivet anses en postkasse for at være i venteposition i en ubegrænset varighed, hvis egenskaben DelayHoldApplied eller DelayReleaseHoldApplied er angivet til **Sand**. Det betyder dog ikke, at *alt* indhold i postkassen bevares. Det afhænger af den værdi, der er angivet for hver egenskab. Lad os f.eks. sige, at begge egenskaber er angivet til **Sand** , fordi ventepositioner fjernes fra postkassen. Derefter fjerner du kun den forsinkelsesventeposition, der er anvendt på clouddata, der ikke er Outlook-data (ved hjælp af parameteren *RemoveDelayReleaseHoldApplied* ). Næste gang Assistent til administreret mappe behandler postkassen, fjernes de elementer, der ikke er Outlook-elementer, som er markeret til fjernelse. Outlook-elementer, der er markeret til fjernelse, fjernes ikke, fordi egenskaben DelayHoldApplied stadig er angivet til **Sand**. Det modsatte ville også være tilfældet: Hvis DelayHoldApplied er angivet til **Falsk** , og DelayReleaseHoldApplied er angivet til **Sand**, er det kun Outlook-elementer, der er markeret til fjernelse, der fjernes, der fjernes.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Sådan bekræfter du, at der anvendes en opbevaringspolitik for hele organisationen på en postkasse

Når der anvendes eller fjernes en opbevaringspolitik for hele organisationen i en postkasse, kan eksport af diagnosticeringslogfilerne for postkassen hjælpe dig med at sikre, at Exchange Online rent faktisk har anvendt eller fjernet opbevaringspolitikken i postkassen. Hvis du vil have vist disse oplysninger, skal du først validere et par ting ved hjælp af [Exchange Online Powershell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Hent GUID'erne for alle opbevaringspolitikker, der udtrykkeligt er anvendt på en postkasse

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Hent GUID'erne for alle opbevaringspolitikker for hele organisationen, der anvendes på postkasser

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>Hent postkassediagnosticering til HoldTracking

Logfilerne til sporing af postkassediagnosticering i venteposition bevarer en oversigt over de ventepositioner, der er anvendt på en brugerpostkasse.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Gennemse resultaterne af logfilerne for postkassediagnosticering

Hvis du indsamler data fra det forrige trin, kan de resulterende data se nogenlunde sådan ud:

> **Red**`  : 0001-01-01T00:00:00.0000000`
>  **Hid**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **Ht**`  : 4`
>  **Lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **Osd**` : 2020-03-23T18:24:37.1884606Z`

Brug følgende tabel til at hjælpe dig med at forstå hver af de tidligere værdier, der er angivet i diagnosticeringsloggen.

| Værdi   | Beskrivelse |
|:------- |:----------- |
| **Red**  | Angiver slutdatoen, som er den dato, hvor opbevaringspolitikken blev deaktiveret. MinValue betyder, at politikken stadig er tildelt postkassen. |
| **Hid** | Angiver GUID'et for opbevaringspolitikken. Denne værdi svarer til de GUID'er, du har indsamlet for de eksplicitte opbevaringspolitikker eller opbevaringspolitikker for hele organisationen, der er tildelt postkassen.|
| **Lsd** | Angiver den sidste startdato, som er den dato, hvor opbevaringspolitikken blev tildelt til postkassen.|
| **Osd** | Angiver den oprindelige startdato, som er den dato, hvor Exchange første gang registrerede oplysninger om opbevaringspolitikken. |
|||

Når der ikke længere anvendes en opbevaringspolitik på en postkasse, placerer vi en midlertidig forsinkelse på brugeren for at forhindre sletning af indhold. En forsinkelsesventeposition kan deaktiveres ved at køre `Set-Mailbox -RemoveDelayHoldApplied` kommandoen .

## <a name="next-steps"></a>Næste trin

Når du har identificeret de ventepositioner, der er anvendt på en postkasse, kan du udføre opgaver, f.eks. ændre varigheden af ventepositionen, midlertidigt eller permanent fjerne ventepositionen eller udelade en inaktiv postkasse fra en Microsoft 365-opbevaringspolitik. Du kan få flere oplysninger om at udføre opgaver, der er relateret til ventepositioner, i et af følgende emner:

- Kør kommandoen [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) i [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) for at udelukke en postkasse fra en Microsoft 365-opbevaringspolitik for hele organisationen. Denne kommando kan kun bruges til opbevaringspolitikker, hvor værdien for egenskaben *ExchangeLocation* er lig med `All`.

- [Rediger varigheden af fastfrysning for en inaktiv postkasse](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Slet en inaktiv postkasse](delete-an-inactive-mailbox.md)

- [Slet elementer i mappen Gendan elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
