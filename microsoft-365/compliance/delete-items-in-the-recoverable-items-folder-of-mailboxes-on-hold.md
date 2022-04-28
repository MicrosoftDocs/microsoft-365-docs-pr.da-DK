---
title: Slet elementer i mappen Elementer, der kan gendannes
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: a85e1c87-a48e-4715-bfa9-d5275cde67b0
description: Få mere at vide om, hvordan administratorer kan slette elementer i en brugers mappe med gendanbare elementer for en Exchange Online postkasse, også selvom denne postkasse er sat i juridisk venteposition.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 808bc02eb711ff72ec8bd329b1367145d2d991a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091737"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Slet elementer i mappen Gendan elementer i skybaserede postkasser i venteposition

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Mappen Gendanbare elementer for en Exchange Online postkasse findes for at beskytte mod utilsigtet eller skadelig sletning. Den bruges også til at gemme elementer, der bevares og tilgås af funktioner til overholdelse af angivne standarder, f.eks. ventepositioner og eDiscovery-søgninger. I nogle situationer kan organisationer dog have data, der utilsigtet bevares i mappen Gendanbare elementer, som de skal slette. En bruger kan f.eks. ubevidst sende eller videresende en mail, der indeholder følsomme oplysninger eller oplysninger, der kan have alvorlige forretningsmæssige konsekvenser. Selvom meddelelsen slettes permanent, kan den bevares på ubestemt tid, fordi der er placeret en juridisk venteposition på postkassen. Dette scenarie kaldes *dataspild*, fordi data utilsigtet er blevet *spildt* i Office 365. I disse situationer kan du slette elementer i en brugers mappe med gendanbare elementer for en Exchange Online postkasse, selvom postkassen er sat i venteposition med en af de forskellige ventepositionsfunktioner i Office 365. Disse typer ventepositioner omfatter tvister, In-Place ventepositioner, eDiscovery-ventepositioner og opbevaringspolitikker, der er oprettet i Sikkerheds- og overholdelsescenter i Office 365 eller Microsoft 365.

I denne artikel forklares det, hvordan administratorer kan slette elementer fra mappen Gendanbare elementer for skybaserede postkasser, der er i venteposition. Denne procedure omfatter deaktivering af adgang til postkassen og deaktivering af gendannelse af enkelte elementer, deaktivering af assistenten til administrerede mapper fra behandling af postkassen, midlertidig fjernelse af venteposition, sletning af elementer fra mappen Gendan elementer og derefter gendannelse af postkassen til den tidligere konfiguration. Her er processen:
  
[Trin 1: Indsaml oplysninger om postkassen](#step-1-collect-information-about-the-mailbox)

[Trin 2: Forbered postkassen](#step-2-prepare-the-mailbox)

[Trin 3: Fjern alle ventepositioner fra postkassen](#step-3-remove-all-holds-from-the-mailbox)

[Trin 4: Fjern forsinkelsesventepositionen fra postkassen](#step-4-remove-the-delay-hold-from-the-mailbox)

[Trin 5: Slet elementer i mappen Gendanbare elementer](#step-5-delete-items-in-the-recoverable-items-folder)

[Trin 6: Genindlæs postkassen til den forrige tilstand](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> De procedurer, der er beskrevet i denne artikel, medfører, at data slettes permanent (fjernes) fra en Exchange Online postkasse. Det betyder, at meddelelser, du sletter fra mappen Elementer, der kan gendannes, ikke kan gendannes og vil ikke være tilgængelige til juridisk registrering eller andre overholdelsesformål. Hvis du vil slette meddelelser fra en postkasse, der er sat i venteposition som en del af en procesførelsesholdning, In-Place venteposition, eDiscovery-venteposition eller opbevaringspolitik, der er oprettet i Microsoft Purview-overholdelsesportalen, skal du kontakte datastyringen eller juridiske afdelinger, før du fjerner ventepositionen. Din organisation kan have en politik, der definerer, om en postkasse i venteposition eller en dataspildhændelse har prioritet.
  
## <a name="before-you-delete-items"></a>Før du sletter elementer

- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af rollegruppen eDiscovery Manager eller tildeles rollen Styring af overholdelsessøgning. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen Organisationsadministration eller tildeles administrationsrollen Søg og fjern. Du kan finde oplysninger om, hvordan du føjer brugere til en rollegruppe, under [Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

- Hvis en postkasse er tildelt en opbevaringspolitik for hele organisationen, skal du udelade postkassen fra politikken, før du kan slette elementer fra mappen Genoprettelige elementer. Det kan tage op til 24 timer at synkronisere politikændringen og fjerne postkassen fra politikken. Du kan få flere oplysninger under "Opbevaringspolitikker for hele organisationen" i afsnittet [Fjern alle ventepositioner fra postkassen](#organization-wide-retention-policies) i denne artikel.

- Du kan ikke udføre denne procedure for en postkasse, der er blevet tildelt opbevaringsindstillinger med en opbevaringspolitik, der er låst ved hjælp af Bevarelseslås. Det skyldes, at denne lås forhindrer dig i at fjerne eller udelade postkassen fra politikken og deaktivere Assistent for administrerede mapper i postkassen. Du kan få flere oplysninger om låsningspolitikker for opbevaring under [Brug bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

- Den procedure, der er beskrevet i denne artikel, understøttes ikke for inaktive postkasser. Det skyldes, at du ikke kan anvende en venteposition (eller opbevaringspolitik) på en inaktiv postkasse igen, når du har fjernet den. Når du fjerner en venteposition fra en inaktiv postkasse, ændres den til en normal blød slettet postkasse og slettes permanent fra din organisation, når den behandles af Assistent til administrerede mapper.

- Hvis en postkasse ikke er sat i venteposition (eller ikke har aktiveret genoprettelse af et enkelt element), kan du slette elementerne fra mappen Gendanbare elementer. Du kan finde flere oplysninger om, hvordan du gør dette, under [Søg efter og slet mails i din organisation](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>Trin 1: Indsaml oplysninger om postkassen

Dette første trin er at indsamle valgte egenskaber fra målpostkassen, der påvirker denne procedure. Sørg for at skrive disse indstillinger ned eller gemme dem i en tekstfil, fordi du ændrer nogle af disse egenskaber og derefter vender tilbage til de oprindelige værdier i trin 6, når du har slettet elementer fra mappen Gendanbare elementer. Her er en liste over de egenskaber for postkassen, du skal indsamle.
  
- *SingleItemRecoveryEnabled*  og  *RetainDeletedItemsFor*. Hvis det er nødvendigt, deaktiverer du enkelt gendannelse og øger opbevaringsperioden for slettede elementer i trin 3.

- *LitigationHoldEnabled*  og  *InPlaceHolds*. Du skal identificere alle de ventepositioner, der er placeret i postkassen, så du kan fjerne dem midlertidigt i trin 3. Se afsnittet [Flere oplysninger](#more-information) for at få tip til, hvordan du identificerer, hvilken type venteposition der kan være placeret i en postkasse.

Derudover skal du hente indstillingerne for klientadgang til postkassen, så du midlertidigt kan deaktivere dem, så ejeren (eller andre brugere) ikke kan få adgang til postkassen under denne procedure. Til sidst kan du hente den aktuelle størrelse og antallet af elementer i mappen Gendanbare elementer. Når du har slettet elementer i mappen Elementer, der kan gendannes i trin 5, skal du bruge disse oplysninger til at kontrollere, at elementerne er blevet fjernet.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Sørg for at bruge et brugernavn og en adgangskode til en administratorkonto, der har fået tildelt de relevante administrationsroller i Exchange Online.

2. Kør følgende kommando for at få oplysninger om gendannelse af enkelt element og opbevaringsperioden for slettet element.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Hvis gendannelse af et enkelt element er aktiveret, skal du deaktivere det i trin 2. Hvis opbevaringsperioden for slettede elementer ikke er angivet for 30 dage (den maksimale værdi i Exchange Online), kan du øge den i trin 2.

3. Kør følgende kommando for at hente indstillingerne for postkassens adgang til postkassen.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   Du deaktiverer alle disse adgangsmetoder i trin 2.

4. Kør følgende kommando for at få oplysninger om de ventepositioner og opbevaringspolitikker, der anvendes på postkassen.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > Hvis der er for mange værdier i egenskaben  *InPlaceHolds*  , og ikke alle af dem vises, kan du køre  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` kommandoen for at få vist hver værdi på en separat linje.
  
5. Kør følgende kommando for at få oplysninger om alle opbevaringspolitikker for hele organisationen. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Hvis din organisation har opbevaringspolitikker for hele organisationen, skal du udelade postkassen fra disse politikker i trin 3. Det kan tage op til 24 timer at replikere ændringen.

    > [!TIP]
    > Hvis der er for mange værdier i egenskaben  *InPlaceHolds*  , og ikke alle af dem vises, kan du køre  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` kommandoen for at få vist hver værdi på en separat linje. 
  
6. Kør følgende kommando for at afgøre, om der er anvendt en forsinkelse på postkassen.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Hvis værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* er angivet til **Sand**, anvendes der en forsinkelse på postkassen, og den skal fjernes. Du kan få flere oplysninger om ventepositioner i [Trin 4: Fjern forsinkelsesventepositionen fra postkassen](#step-4-remove-the-delay-hold-from-the-mailbox).

   Hvis værdien af begge egenskaber er angivet til **Falsk**, anvendes der ikke en forsinkelse på postkassen, og du kan springe trin 4 over.

7. Kør følgende kommando for at hente den aktuelle størrelse og det samlede antal elementer i mapper og undermapper i mappen Gendanbare elementer i brugerens primære postkasse.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Hvis brugerens arkivpostkasse er aktiveret, skal du køre følgende kommando for at hente størrelsen og det samlede antal elementer i mapper og undermapper i mappen Gendanbare elementer i deres arkivpostkasse. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Når du sletter elementer i trin 5, kan du vælge at slette eller ikke slette elementer i mappen Gendanbare elementer i brugerens primære arkivpostkasse. Hvis automatisk udvidelse af arkivering er aktiveret for postkassen, slettes elementer i en ekstra arkivpostkasse ikke.
  
## <a name="step-2-prepare-the-mailbox"></a>Trin 2: Forbered postkassen

Når du har indsamlet og gemt oplysninger om postkassen, er det næste trin at forberede postkassen ved at udføre følgende opgaver:
  
- **Deaktiver klientadgang til postkassen** , så ejeren af postkassen ikke kan få adgang til sin postkasse og foretage ændringer af postkassedataene under denne procedure.

- **Forøg opbevaringsperioden for slettede elementer** til 30 dage (den maksimale værdi i Exchange Online), så elementer ikke fjernes fra mappen Gendan elementer, før du kan slette dem i trin 5.

- **Deaktiver gendannelse af enkelt element** , så elementer ikke bevares (i varigheden af opbevaringsperioden for slettet element), når du har slettet dem fra mappen Elementer, der kan genoprettes i trin 5.

- **Deaktiver Assistent til administrerede mapper** , så den ikke behandler postkassen, og bevar de elementer, du sletter i trin 5.

Udfør følgende trin i Exchange Online PowerShell.
  
1. Kør følgende kommando for at deaktivere al klientadgang til postkassen. Kommandosyntaksen forudsætter, at alle klientadgangsmetoder er aktiveret i postkassen.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Det kan tage op til 60 minutter at deaktivere alle klientadgangsmetoder til postkassen. Bemærk, at deaktivering af disse adgangsmetoder ikke afbryder forbindelsen til ejeren af postkassen, hvis vedkommende i øjeblikket er logget på. Hvis ejeren ikke er logget på, kan vedkommende ikke få adgang til sin postkasse, når disse adgangsmetoder er deaktiveret.
  
2. Kør følgende kommando for at øge opbevaringsperioden for slettede elementer i højst 30 dage. Dette forudsætter, at den aktuelle indstilling er mindre end 30 dage.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Kør følgende kommando for at deaktivere gendannelse af enkelte elementer.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Det kan tage op til 240 minutter at deaktivere gendannelse af enkelte elementer. Slet ikke elementer i mappen Elementer, der kan gendannes, før denne periode er udløbet.
  
4. Kør følgende kommando for at forhindre, at assistenten til administrerede mapper behandler postkassen. Som tidligere forklaret kan du kun deaktivere assistenten til administrerede mapper, hvis der ikke anvendes en opbevaringspolitik med en bevarelseslås på postkassen.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Trin 3: Fjern alle ventepositioner fra postkassen

Det sidste trin, før du kan slette elementer fra mappen Gendanbare elementer, er at fjerne alle ventepositioner (som du identificerede i trin 1), der er placeret i postkassen. Alle ventepositioner skal fjernes, så elementerne ikke bevares, når du har slettet dem fra mappen Elementer, der kan gendannes. De følgende afsnit indeholder oplysninger om fjernelse af forskellige typer ventepositioner i en postkasse. Se afsnittet [Flere oplysninger](#more-information) for at få tip til, hvordan du identificerer, hvilken type venteposition der kan være placeret i en postkasse. Du kan finde flere oplysninger under [Sådan identificeres den type venteposition, der er placeret i en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Som tidligere nævnt skal du kontakte datastyringen eller de juridiske afdelinger, før du fjerner en venteposition fra en postkasse.
  
### <a name="litigation-hold"></a>Procesførelse - venteposition
  
Kør følgende kommando i Exchange Online PowerShell for at fjerne en litigation-venteposition fra postkassen.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> På samme måde som med deaktivering af gendannelse af enkelte elementer kan det tage op til 240 minutter at fjerne den retslige venteposition. Slet ikke elementer fra mappen Elementer, der kan gendannes, før denne periode er udløbet.
  
### <a name="in-place-hold"></a>In-Place venteposition
  
Kør følgende kommando i Exchange Online PowerShell for at identificere den In-Place venteposition, der er placeret i postkassen. Brug GUID'et for den In-Place venteposition, som du identificerede i trin 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Når du har identificeret In-Place Venteposition, kan du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> eller Exchange Online PowerShell til at fjerne postkassen fra ventepositionen. Du kan få flere oplysninger under [Opret eller fjern en In-Place Venteposition](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Opbevaringspolitikker, der anvendes på bestemte postkasser
  
Kør følgende kommando i [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at identificere den opbevaringspolitik, der anvendes på postkassen. Denne kommando returnerer også alle Teams politikker for samtaleopbevaring, der er anvendt på en postkasse. Brug GUID 'et (inklusive ikke præfikset `mbx` eller `skp` ) for den opbevaringspolitik, du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Når du har identificeret opbevaringspolitikken, skal du gå til siden Administration  >  af **datalivscyklusRetention** på overholdelsesportalen, redigere den opbevaringspolitik, du identificerede i det forrige trin, og fjerne postkassen fra listen over modtagere, der er inkluderet i opbevaringspolitikken.
  
### <a name="organization-wide-retention-policies"></a>Opbevaringspolitikker for hele organisationen
  
Opbevaringspolitikker, der gælder for hele organisationen, Exchange og Teams gælder for alle postkasser i organisationen. De anvendes på organisationsniveau (ikke på postkasseniveau) og returneres, når du kører cmdlet'en **Get-OrganizationConfig** i Trin 1. Kør følgende kommando i [Security & Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell) for at identificere opbevaringspolitikkerne for hele organisationen. Brug GUID 'et (inklusive ikke præfikset  `mbx` ) for de opbevaringspolitikker for hele organisationen, som du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Når du har identificeret opbevaringspolitikkerne for hele organisationen, skal du gå til siden Administration  >  af **datalivscyklusRetention** på overholdelsesportalen, redigere hver opbevaringspolitik for hele organisationen, som du identificerede i det forrige trin, og føje postkassen til listen over udeladte modtagere. Hvis du gør dette, fjernes brugerens postkasse fra opbevaringspolitikken.

> [!IMPORTANT]
> Når du har udelukket en postkasse fra en opbevaringspolitik for hele organisationen, kan det tage op til 24 timer at synkronisere denne ændring og fjerne postkassen fra politikken.

### <a name="retention-labels"></a>Opbevaringsmærkater

Når en bruger anvender en mærkat, der er konfigureret til at bevare indhold eller bevare og derefter slette indhold til en mappe eller et element i postkassen, angives egenskaben *ComplianceTagHoldApplied* for postkassen til **Sand**. Når det sker, anses postkassen for at være i venteposition, som om den blev sat i procesret eller tildelt en opbevaringspolitik.

Hvis du vil have vist værdien af egenskaben *ComplianceTagHoldApplied*, skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Når du har identificeret, at en postkasse er i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element, kan du bruge søgeværktøjet Indhold på overholdelsesportalen til at søge efter navngivne elementer ved hjælp af betingelsen **opbevaringsmærkat** . Du kan finde flere oplysninger under:

- Afsnittet "Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsmærkat" i [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Afsnittet "Søgebetingelser" i [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Du kan finde flere oplysninger om mærkater under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

### <a name="ediscovery-holds"></a>eDiscovery-ventepositioner
  
Kør følgende kommandoer i [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at identificere den venteposition, der er knyttet til en eDiscovery-sag (kaldet *eDiscovery-ventepositioner*), der er anvendt på postkassen. Brug GUID (inklusive ikke præfikset  `UniH` ) til den eDiscovery-venteposition, du identificerede i trin 1. Den anden kommando viser navnet på den eDiscovery-sag, som ventepositionen er knyttet til. den tredje kommando viser navnet på ventepositionen.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Når du har identificeret navnet på eDiscovery-sagen og ventepositionen, skal du gå til **eDiscovery** \> **eDiscovery-siden** i overholdelsescenter, åbne sagen og fjerne postkassen fra ventepositionen. Du kan finde flere oplysninger om identifikation af eDiscovery-ventepositioner i afsnittet "eDiscovery-ventepositioner" i [Sådan identificeres den type venteposition, der er placeret på en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Trin 4: Fjern forsinkelsesventepositionen fra postkassen

Når en hvilken som helst type venteposition er fjernet fra en postkasse, angives værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* for postkassen til **Sand**. Dette sker, næste gang Assistent til administreret mappe behandler postkassen og registrerer, at en venteposition er blevet fjernet. Dette kaldes *en forsinkelsesventetid* og betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre, at data slettes permanent fra postkassen. (Formålet med en forsinkelsesventeposition er at give administratorer mulighed for at søge efter eller gendanne postkasseelementer, der fjernes, når en venteposition er fjernet.  Når der er sat en forsinkelse i venteposition på postkassen, anses postkassen stadig for at være i venteposition i ubegrænset varighed, som om postkassen var i procesretlig venteposition. Efter 30 dage udløber forsinkelsesventetiden, og Microsoft 365 forsøger automatisk at fjerne forsinkelsesventetiden (ved at angive egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* til **Falsk**), så ventepositionen fjernes. Du kan finde flere oplysninger om en forsinkelsesventeposition i afsnittet "Administration af postkasser i forsinkelsesventeposition" i [Sådan identificeres den type venteposition, der er placeret på en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

Hvis værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* er angivet til **Sand**, skal du køre en af følgende kommandoer for at fjerne forsinkelsesventepositionen:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Eller

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Du skal være tildelt rollen Juridisk venteposition i Exchange Online for at bruge parameteren *RemoveDelayHoldApplied* eller *RemoveDelayReleaseHoldApplied*.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Trin 5: Slet elementer i mappen Gendanbare elementer

Nu er du klar til rent faktisk at slette elementer i mappen Gendanbare elementer ved hjælp af [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) - og [New-ComplianceSearchAction-cmdlet'erne](/powershell/module/exchange/new-compliancesearchaction) i Security & Compliance Center PowerShell.

Hvis du vil søge efter elementer, der er placeret i mappen Gendanbare elementer, anbefaler vi, at du udfører en *målrettet samling*. Det betyder, at du kun begrænser omfanget af søgningen til elementer, der er placeret i mappen Gendanbare elementer. Det kan du gøre ved at køre scriptet i artiklen [Brug indholdssøgning til målrettede samlinger](use-content-search-for-targeted-collections.md) . Dette script returnerer værdien af egenskaben mappe-id for alle undermapperne i destinationsmappen Gendanbare elementer. Derefter skal du bruge mappe-id'et i en søgeforespørgsel til at returnere elementer, der er placeret i den pågældende mappe.

Her er en oversigt over den proces, der skal bruges til at søge efter og slette elementer i en brugers mappe med genoprettelige elementer:

1. Kør det målrettede samlingsscript, der returnerer mappe-id'erne for alle mapper i destinationsbrugerens postkasse. Scriptet opretter forbindelse til Exchange Online PowerShell og Security & Compliance PowerShell i den samme PowerShell-session. Du kan få flere oplysninger [under Kør scriptet for at få en liste over mapper for en postkasse](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Kopiér mappe-id'erne for alle undermapper i mappen Elementer, der kan gendannes. Du kan også omdirigere outputtet fra scriptet til en tekstfil.

   Her er en liste over og en beskrivelse af undermapperne i mappen Gendanbare elementer, som du kan søge efter og slette elementer fra:

   - **Sletninger**: Indeholder elementer, der er slettet med blød sletning, og hvis opbevaringsperiode for slettet element ikke er udløbet. Brugerne kan gendanne elementer, der er slettet med blød adgang, fra denne undermappe ved hjælp af værktøjet Gendan slettet post i Outlook.

   - **DiscoveryHolds**: Indeholder hårdt slettede elementer, der er bevaret af en eDiscovery-venteposition eller en opbevaringspolitik. Denne undermappe er ikke synlig for slutbrugere.

   - **SubstrateHolds**: Indeholder hårdt slettede elementer fra Teams og andre skybaserede apps, der er bevaret af en opbevaringspolitik eller en anden type venteposition. Denne undermappe er ikke synlig for slutbrugere.

3. Brug **New-ComplianceSearch-cmdlet'en** (i Security & Compliance Center PowerShell) eller brug værktøjet til indholdssøgning i Overholdelsescenter til at oprette en indholdssøgning, der returnerer elementer fra destinationsbrugerens mappe Genoprettelige elementer. Det kan du gøre ved at medtage FolderId i søgeforespørgslen for alle de undermapper, du vil søge i. Følgende forespørgsel returnerer f.eks. alle meddelelser i undermapperne Sletninger og eDiscoveryHolds:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Du kan finde flere oplysninger og eksempler om kørsel af indholdssøgninger, der bruger egenskaben mappe-id, under [Brug et mappe-id eller til at udføre en målrettet samling](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Hvis du bruger **New-ComplianceSearch-cmdlet'en** til at søge i mappen Gendanbare elementer, skal du sørge for at bruge **Start-ComplianceSearch-cmdlet'en** til at køre søgningen.

4. Når du har oprettet en indholdssøgning og valideret, at den returnerer de elementer, du vil slette, skal du bruge `New-ComplianceSearchAction -Purge -PurgeType HardDelete` kommandoen (i Security & Compliance Center PowerShell) til permanent at slette de elementer, der returneres af den indholdssøgning, du oprettede i det forrige trin. Du kan f.eks. køre en kommando, der ligner følgende kommando:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Der slettes maksimalt 10 elementer pr. postkasse, når du kører den forrige kommando. Det betyder, at du muligvis skal køre `New-ComplianceSearchAction -Purge` kommandoen flere gange for at slette alle de elementer, du vil slette, i mappen Elementer, der kan gendannes. Hvis du vil slette flere elementer, skal du først fjerne den tidligere handling til fjernelse af overholdelse af angivne standarder. Det gør du ved at køre cmdlet'en `Remove-ComplianceSearchAction` . Hvis du f.eks. vil slette den tømningshandling, der blev kørt i det forrige trin, skal du køre følgende kommando:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Når du har gjort det, kan du oprette en ny handling til søgning efter overholdelse for at slette flere elementer. Du skal slette hver tømningshandling, før du opretter en ny.

   Hvis du vil hente en liste over søgehandlinger for overholdelse, kan du køre cmdlet'en `Get-ComplianceSearchAction` . Sletningshandlinger identificeres ved `_Purge` at føje dem til søgenavnet.

### <a name="verify-that-items-were-deleted"></a>Kontrollér, at elementerne er blevet slettet

Hvis du vil kontrollere, at du har slettet elementer fra mappen Gendanbare elementer i en postkasse, skal du bruge **Get-MailboxFolderStatistics-cmdlet'en** i Exchange Online PowerShell til at kontrollere størrelsen og antallet af elementer i mappen Gendanbare elementer. Du kan sammenligne disse statistikker med dem, du indsamlede i trin 1.
  
Kør følgende kommando i for at hente den aktuelle størrelse og det samlede antal elementer i mapper og undermapper i mappen Gendanbare elementer i brugerens primære postkasse.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Kør følgende kommando for at hente størrelsen og det samlede antal elementer i mapper og undermapper i mappen Gendanbare elementer i brugerens arkivpostkasse.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Trin 6: Genindlæs postkassen til den forrige tilstand

Det sidste trin er at gendanne postkassen til den tidligere konfiguration. Det betyder, at du nulstiller de egenskaber, du ændrede i trin 2, og genanvender de ventepositioner, du fjernede i trin 3. Dette omfatter:
  
- Ændring af opbevaringsperioden for det slettede element tilbage til den forrige værdi. Alternativt kan du bare lade dette sæt være 30 dage, den maksimale værdi i Exchange Online.

- Genaktiver gendannelse af enkelt element.

- Genaktiver klientadgangsmetoderne, så ejeren kan få adgang til deres postkasse.

- Genanvender de politikker for bevarelse og opbevaring, som du har fjernet.

- Genaktiverer Assistent til administrerede mapper for at behandle postkassen.

> [!IMPORTANT]
> Vi anbefaler, at du venter 24 timer efter genaktivering af en ventepositions- eller opbevaringspolitik (og kontrollerer, at den er på plads), før du genaktiverer Assistent til administreret mappe for at behandle postkassen.
  
Udfør følgende trin (i den angivne sekvens) i Exchange Online PowerShell.
  
1. Kør følgende kommando for at ændre opbevaringsperioden for det slettede element tilbage til den oprindelige værdi. Dette forudsætter, at den forrige indstilling er mindre end 30 dage. f.eks. 14 dage.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Kør følgende kommando for at genaktivere genoprettelse af enkelte elementer.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Kør følgende kommando for at aktivere alle klientadgangsmetoder til postkassen igen.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Anvend de ventepositioner, du fjernede i trin 3, igen. Afhængigt af typen af venteposition skal du bruge en af følgende procedurer.

    **Procesførelse - venteposition**

    Kør følgende kommando for at aktivere en venteposition for procesførelse for postkassen igen.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **Bevarelse på stedet**

    Brug EAC (eller Exchange Online PowerShell) til at føje postkassen tilbage til In-Place Venteposition.

    **Opbevaringspolitikker, der anvendes på bestemte postkasser**

    Brug overholdelsesportalen til at føje postkassen tilbage til opbevaringspolitikken. Gå til siden Administration  >  af **datalivscyklusRetention** i Overholdelsescenter, rediger opbevaringspolitikken, og føj postkassen tilbage til listen over modtagere, som opbevaringspolitikken anvendes på.

    **Opbevaringspolitikker for hele organisationen**

    Hvis du har fjernet en opbevaringspolitik for hele organisationen eller Exchange ved at udelade den fra politikken, skal du bruge overholdelsesportalen til at fjerne postkassen fra listen over udeladte brugere. Gå til siden **Administration af datalivscyklusRetention** i Overholdelsescenter, rediger opbevaringspolitikken for hele organisationen, og fjern postkassen fra listen over udeladte  >  modtagere. Hvis du gør dette, genbruges opbevaringspolitikken til brugerens postkasse.

    **eDiscovery-sag i venteposition**

    Brug overholdelsesportalen til at tilføje postkassen den venteposition, der er knyttet til en eDiscovery-sag, igen. Gå til siden **eDiscoveryCore** > , åbn sagen, og føj postkassen tilbage til ventepositionen. 

5. Kør følgende kommando for at tillade, at assistenten til administrerede mapper behandler postkassen igen. Som tidligere nævnt anbefaler vi, at du venter 24 timer efter genanvendelse af en ventepositions- eller opbevaringspolitik (og kontrollerer, at den er på plads), før du genaktiverer assistenten for administrerede mapper.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Hvis du vil kontrollere, at postkassen er gendannet til den tidligere konfiguration, kan du køre følgende kommandoer og derefter sammenligne indstillingerne med dem, du indsamlede i trin 1.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Flere oplysninger

Her er en tabel, der beskriver, hvordan du identificerer forskellige typer ventepositioner baseret på værdierne i egenskaben  *InPlaceHolds*  , når du kører **Get-Mailbox** - eller **Get-OrganizationConfig-cmdlet'erne** . Du kan finde flere detaljerede oplysninger under [Sådan identificeres den type venteposition, der er placeret i en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

Som tidligere forklaret, skal du fjerne alle ventepositioner og opbevaringspolitikker fra en postkasse, før du kan slette elementer i mappen Elementer, der kan genoprettes.
  
| Ventepositionstype | Eksempelværdi | Sådan identificerer du ventepositionen |
|:-----|:-----|:-----|
|Procesførelse - venteposition  <br/> | `True` <br/> |Egenskaben  *LitigationHoldEnabled*  er angivet til  `True`.  <br/> |
|In-Place venteposition  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |Egenskaben  *InPlaceHolds*  indeholder GUID'et for den In-Place venteposition, der er placeret i postkassen. Du kan se, at dette er en In-Place venteposition, fordi GUID'et ikke starter med et præfiks.  <br/> Du kan bruge kommandoen `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` i Exchange Online PowerShell til at få oplysninger om In-Place Venteposition på postkassen.  <br/> |
| Opbevaringspolitikker i overholdelsesportalen, der anvendes på bestemte postkasser  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> Eller  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Når du kører **cmdlet'en Get-Mailbox** , indeholder egenskaben  *InPlaceHolds*  også GUID'er for opbevaringspolitikker, der er anvendt på postkassen. Du kan identificere opbevaringspolitikker, fordi GUID'et starter med præfikset  `mbx` . Hvis GUID'et for opbevaringspolitikken starter med præfikset`skp`, angiver det, at opbevaringspolitikken anvendes på Skype for Business samtaler.  <br/> Hvis du vil identificere den opbevaringspolitik, der anvendes på postkassen, skal du køre følgende kommando i Security & Compliance Center PowerShell: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Sørg for at fjerne præfikset  `mbx` eller  `skp` , når du kører denne kommando.  <br/> |
|Opbevaringspolitikker for hele organisationen på overholdelsesportalen  <br/> |Ingen værdi  <br/> Eller  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (angiver, at postkassen er udelukket fra en politik for hele organisationen)  <br/> |Selvom egenskaben  *InPlaceHolds*  er tom, når du kører **Get-Mailbox-cmdlet'en** , kan der stadig anvendes en eller flere opbevaringspolitikker for hele organisationen på postkassen.  <br/> Du kan bekræfte dette ved at køre `Get-OrganizationConfig | FL InPlaceHolds` kommandoen i Exchange Online PowerShell for at få vist en liste over GUID'erne for opbevaringspolitikker for hele organisationen. GUID'et for opbevaringspolitikker for hele organisationen, der anvendes på Exchange postkasser starter med præfikset`mbx`, `mbxa3056bb15562480fadb46ce523ff7b02`f.eks. .  <br/> Hvis du vil identificere den opbevaringspolitik for hele organisationen, der anvendes på postkassen, skal du køre følgende kommando i Security & Compliance Center PowerShell: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Hvis en postkasse udelades fra en opbevaringspolitik for hele organisationen, vises GUID for opbevaringspolitikken i egenskaben  *InPlaceHolds*  for brugerens postkasse, når du kører **cmdlet'en Get-Mailbox** . det identificeres af præfikset  `-mbx`, f.eks.  `-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|eDiscovery-sag i overholdelsesportalen  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |Egenskaben  *InPlaceHolds*  indeholder også GUID'et for alle ventepositioner, der er knyttet til en eDiscovery-sag i overholdelsesportalen, som kan være placeret i postkassen. Du kan se, at dette er en eDiscovery-sag i venteposition, fordi GUID'et starter med præfikset  `UniH` .  <br/> Du kan bruge cmdlet'en  `Get-CaseHoldPolicy` i Security & Compliance Center PowerShell til at få oplysninger om den eDiscovery-sag, som ventepositionen på postkassen er knyttet til. Du kan f.eks. køre kommandoen  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` for at få vist navnet på sagspositionen i postkassen. Sørg for at fjerne præfikset  `UniH` , når du kører denne kommando.  <br/><br/> Kør følgende kommandoer for at identificere eDiscovery-sagen, som postkassens venteposition er knyttet til:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
