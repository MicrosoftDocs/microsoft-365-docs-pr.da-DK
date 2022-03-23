---
title: Slet elementer i mappen Genoprettelige elementer i skypostkassen i venteposition
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om, hvordan administratorer kan slette elementer i en brugers mappe med genoprettelige elementer for en Exchange Online-postkasse, også selvom postkassen er sat i retslig venteposition.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: c349166477b610e48fd3a1b63c27d4dd4188012c
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63588905"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition

Mappen genoprettelige elementer for en postkasse Exchange Online beskyttes mod utilsigtede eller skadelige sletninger. Den bruges også til at gemme elementer, der bevares og tilgås via overholdelsesfunktioner, f.eks. ventende eller eDiscovery-søgninger. I nogle situationer kan organisationer dog have data, der utilsigtet er bevaret i mappen Genoprettelige elementer, som de skal slette. En bruger kan f.eks. ukendt sende eller videresende en mail, der indeholder følsomme oplysninger eller oplysninger, der kan have alvorlige forretningsmæssige konsekvenser. Selvom meddelelsen slettes permanent, kan den bevares på ubestemt tid, fordi postkassen er sat i retslig venteposition. Dette scenarie er kendt *som dataoverløb*, fordi data utilsigtet er overløbt *Office 365*. I disse situationer kan du slette elementer i en brugers mappe genoprettelige elementer for en Exchange Online-postkasse, også selvom postkassen er sat i venteposition med en af de forskellige funktioner til venteposition i Office 365. Disse typer af vente ventende funktioner omfatter retslige tilbageholdelser, In-Place vente hold, eDiscovery-ventende funktioner og opbevaringspolitikker, der er oprettet i Security and Compliance Center i Office 365 eller Microsoft 365.

I denne artikel forklares det, hvordan administratorer kan slette elementer fra mappen Genoprettelige elementer for skybaserede postkasser, der er i venteposition. Denne fremgangsmåde indebærer deaktivering af adgang til postkassen og deaktivering af gendannelse af enkelte elementer, deaktivering af administreret mappeassistent i at behandle postkassen, midlertidig fjernelse af ventepositionen, sletning af elementer fra mappen Genoprettelige elementer og derefter tilbageføring af postkassen til dens tidligere konfiguration. Sådan gør du:
  
[Trin 1: Indsaml oplysninger om postkassen](#step-1-collect-information-about-the-mailbox)

[Trin 2: Klargør postkassen](#step-2-prepare-the-mailbox)

[Trin 3: Fjern alle ventende trin fra postkassen](#step-3-remove-all-holds-from-the-mailbox)

[Trin 4: Fjern forsinkelsen i venteposition fra postkassen](#step-4-remove-the-delay-hold-from-the-mailbox)

[Trin 5: Slet elementer i mappen Genoprettelige elementer](#step-5-delete-items-in-the-recoverable-items-folder)

[Trin 6: Tilbagedan postkassen til dens tidligere tilstand](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> De procedurer, der er beskrevet i denne artikel, medfører, at data slettes permanent (slettes) fra en Exchange Online postkasse. Det betyder, at meddelelser, som du sletter fra mappen Genoprettelige elementer, ikke kan gendannes og ikke vil være tilgængelige med henblik på juridisk registrering eller andre overholdelsesformål. Hvis du vil slette meddelelser fra en postkasse, der er sat i venteposition som en del af en retslig tilbageholdelse, In-Place Venteposition, eDiscovery-venteposition eller opbevaringspolitik, der er oprettet i Microsoft 365 Overholdelsescenter, skal du tale med din datastyring eller juridiske afdeling, før du fjerner ventepositionen. Din organisation har muligvis en politik, der definerer, om en postkasse i venteposition eller en dataudløbshændelse har forrang.
  
## <a name="before-you-delete-items"></a>Før du sletter elementer

- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af rollegruppen eDiscovery Manager eller være tildelt rollen som styring af overholdelsessøgning. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen Organisationsadministration eller være tildelt administrationsrollen Søg og tøm. Du kan finde oplysninger om at føje brugere til en rollegruppe [under Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

- Hvis en postkasse er tildelt en opbevaringspolitik for hele organisationen, skal du udelade postkassen fra politikken, før du kan slette elementer fra mappen Genoprettelige elementer. Det kan tage op til 24 timer at synkronisere ændringen af politikken og fjerne postkassen fra politikken. Få mere at vide under "Opbevaringspolitikker for hele organisationen" i [afsnittet Fjern alle ventende dele fra postkassen](#organization-wide-retention-policies) i denne artikel.

- Du kan ikke udføre denne procedure for en postkasse, der har fået tildelt opbevaringsindstillinger med en opbevaringspolitik, der er låst ved hjælp af Preservation Lock. Det skyldes, at denne lås forhindrer dig i at fjerne eller udelade postkassen fra politikken og i at deaktivere den administrerede mappeassistent i postkassen. Du kan finde flere oplysninger om låsningspolitikker for opbevaring i [Brug Opbevaringslås til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

- Fremgangsmåden, der er beskrevet i denne artikel, understøttes ikke for inaktive postkasser. Det skyldes, at du ikke kan genanvende en venteposition (eller opbevaringspolitik) på en inaktiv postkasse, når du har fjernet den. Når du fjerner en venteposition fra en inaktiv postkasse, ændres den til en normal blød-slettet postkasse og slettes permanent fra din organisation, når den er blevet behandlet af den administrerede mappeassistent.

- Hvis en postkasse ikke er sat i venteposition (eller ikke har aktiveret gendannelse af et enkelt element), kan du slette elementerne fra mappen Genoprettelige elementer. Du kan finde flere oplysninger om, hvordan du gør dette [, under Søge efter og slette mails i organisationen](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>Trin 1: Indsaml oplysninger om postkassen

Det første trin er at indsamle valgte egenskaber fra målpostkassen, som vil påvirke denne procedure. Sørg for at skrive disse indstillinger ned eller gemme dem i en tekstfil, da du vil ændre nogle af disse egenskaber og derefter vende tilbage til de oprindelige værdier i trin 6, når du har slettet elementer fra mappen Genoprettelige elementer. Her er en liste over de postkasseegenskaber, du skal indsamle.
  
- *SingleItemRecoveryEnabled*  og  *RetainDeletedItemsFor*. Hvis det er nødvendigt, deaktiverer du enkelt gendannelse og øger opbevaringsperioden for slettede elementer i trin 3.

- *LitigationHoldEnabled*  og  *InPlaceHolds*. Du skal identificere alle de ventende trin i postkassen, så du midlertidigt kan fjerne dem i trin 3. Se afsnittet [Flere oplysninger](#more-information) for at få tip til, hvordan du identificerer den type venteposition, der kan placeres i en postkasse.

Desuden skal du have adgangsindstillingerne for postkasseklienten, så du midlertidigt kan deaktivere dem, så ejeren (eller andre brugere) ikke kan få adgang til postkassen under denne procedure. Endelig kan du få den aktuelle størrelse og antallet af elementer i mappen Genoprettelige elementer. Når du har slettet elementer i mappen Genoprettelige elementer i trin 5, skal du bruge disse oplysninger til at bekræfte, at elementer er blevet fjernet.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Sørg for at bruge et brugernavn og en adgangskode til en administratorkonto, der er blevet tildelt de relevante administrationsroller i Exchange Online.

2. Kør følgende kommando for at få oplysninger om gendannelse af et enkelt element og opbevaringsperioden for slettede elementer.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Hvis gendannelse af et enkelt element er aktiveret, skal du deaktivere det i trin 2. Hvis opbevaringsperioden for slettede elementer ikke er angivet til 30 dage (den maksimale værdi i Exchange Online), kan du øge den i trin 2.

3. Kør følgende kommando for at få adgangsindstillingerne for postkassen.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   Du deaktiverer alle disse adgangsmetoder i trin 2.

4. Kør følgende kommando for at få oplysninger om de ventende og opbevaringspolitikker, der anvendes til postkassen.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > Hvis der er for mange værdier i egenskaben  *InPlaceHolds*  , og ikke dem alle vises,  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` kan du køre kommandoen for at få vist hver værdi på en separat linje.
  
5. Kør følgende kommando for at få oplysninger om opbevaringspolitikker for hele organisationen. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Hvis din organisation har opbevaringspolitikker for hele organisationen, er du nødt til at udelukke postkassen fra disse politikker i trin 3. Det kan tage op til 24 timer at replikere ændringen.

    > [!TIP]
    > Hvis der er for mange værdier i egenskaben  *InPlaceHolds*  , og ikke dem alle vises,  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` kan du køre kommandoen for at få vist hver værdi på en separat linje. 
  
6. Kør følgende kommando for at afgøre, om postkassen er blevet forsinket.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Hvis værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* er angivet til **Sand, anvendes** en forsinkelse i venteposition i postkassen og skal fjernes. Du kan finde flere oplysninger om forsinkelse i venteposition [i Trin 4: Fjern forsinkelses hold fra postkassen](#step-4-remove-the-delay-hold-from-the-mailbox).

   Hvis værdien af en af egenskaberne er angivet til **Falsk**, anvendes der ikke en forsinkelse i postkassen, og du kan springe trin 4 over.

7. Kør følgende kommando for at få den aktuelle størrelse og samlede antal elementer i mapper og undermapper i mappen Genoprettelige elementer i brugerens primære postkasse.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Hvis brugerens arkivpostkasse er aktiveret, skal du køre følgende kommando for at få størrelsen og det samlede antal elementer i mapper og undermapper i mappen Genoprettelige elementer i arkivpostkassen. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Når du sletter elementer i trin 5, kan du vælge at slette eller ikke slette elementer i mappen Genoprettelige elementer i brugerens primære arkivpostkasse. Hvis automatisk udvidende arkivering er aktiveret for postkassen, slettes elementer i en hjælpearkivpostkasse ikke.
  
## <a name="step-2-prepare-the-mailbox"></a>Trin 2: Klargør postkassen

Når du har samlet og gemt oplysninger om postkassen, er næste trin at forberede postkassen ved at udføre følgende opgaver:
  
- **Deaktiver klientadgang til postkasse** , så postkasseejeren ikke kan få adgang til sin postkasse og foretage ændringer i postkassedataene under denne procedure.

- **Øg** opbevaringsperioden for slettede elementer til 30 dage (den maksimale værdi i Exchange Online), så elementer ikke slettes fra mappen Genoprettelige elementer, før du kan slette dem i trin 5.

- **Deaktiver gendannelse af** et enkelt element, så elementer ikke bevares (i hele opbevaringsperioden for slettede elementer), efter at du har slettet dem fra mappen Genoprettelige elementer i trin 5.

- **Deaktiver assistenten til administrerede** mapper, så den ikke behandler postkassen og bevarer de elementer, du sletter i trin 5.

Udfør følgende trin i Exchange Online PowerShell.
  
1. Kør følgende kommando for at deaktivere al klientadgang til postkassen. Kommandosyntaksen forudsætter, at alle klientadgangsmetoder er aktiveret i postkassen.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Det kan tage op til 60 minutter at deaktivere alle klientadgangsmetoder til postkassen. Bemærk, at deaktivering af disse adgangsmetoder ikke afbryder postkasseejeren, hvis de aktuelt er logget på. Hvis ejeren ikke er logget på, kan han eller hun ikke få adgang til sin postkasse, efter disse adgangsmetoder er deaktiveret.
  
2. Kør følgende kommando for at øge opbevaringsperioden for slettede elementer maksimalt 30 dage. Dette forudsætter, at den aktuelle indstilling er mindre end 30 dage.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Kør følgende kommando for at deaktivere gendannelse af et enkelt element.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Det kan tage op til 240 minutter at deaktivere gendannelse af enkelte elementer. Slet ikke elementer i mappen Genoprettelige elementer, før denne periode er gået.
  
4. Kør følgende kommando for at forhindre den administrerede mappeassistent i at behandle postkassen. Som tidligere nævnt kan du kun deaktivere Administreret mappeassistent, hvis postkassen ikke har en opbevaringspolitik med en opbevaringslås.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Trin 3: Fjern alle ventende trin fra postkassen

Det sidste trin, før du kan slette elementer fra mappen Genoprettelige elementer, er at fjerne alle ventende elementer (som du identificerede i trin 1), som placeres i postkassen. Alle ventende elementer skal fjernes, så elementer ikke bevares, når du har slettet dem fra mappen Genoprettelige elementer. De følgende afsnit indeholder oplysninger om at fjerne forskellige typer ventende elementer i en postkasse. Se afsnittet [Flere oplysninger](#more-information) for at få tip til, hvordan du identificerer den type venteposition, der kan placeres i en postkasse. Du kan få mere at [vide under Sådan identificeres den type venteposition, der er placeret på Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Som tidligere nævnt skal du kontakt din datastyring eller juridiske afdeling, før du fjerner en venteposition fra en postkasse.
  
### <a name="litigation-hold"></a>Retslig venteposition
  
Kør følgende kommando i Exchange Online PowerShell for at fjerne en retslig venteposition fra postkassen.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Ligesom deaktivering af gendannelse af enkelte elementer kan det tage op til 240 minutter at fjerne retslig venteposition. Slet ikke elementer fra mappen Genoprettelige elementer, før denne periode er gået.
  
### <a name="in-place-hold"></a>In-Place venteposition
  
Kør følgende kommando i Exchange Online PowerShell for at identificere In-Place hold, der er placeret i postkassen. Brug GUID'et for In-Place venteposition, som du identificerede i trin 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Når du har identificeret In-Place-venteposition, kan du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> eller Exchange Online PowerShell til at fjerne postkassen fra ventepositionen. Få mere at vide under [Opret eller fjern en In-Place venteposition](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Opbevaringspolitikker anvendt på bestemte postkasser
  
Kør følgende kommando i [Security & Compliance Center PowerShell for at](/powershell/exchange/connect-to-scc-powershell) identificere den opbevaringspolitik, der anvendes på postkassen. Denne kommando returnerer også de samtaler Teams der er anvendt til en postkasse. Brug GUID'et (herunder ikke eller `mbx` præfikset `skp` ) for den opbevaringspolitik, du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Når du har identificeret opbevaringspolitikken, skal du gå til siden Information **governanceRetention**  >  i Microsoft 365 Overholdelsescenter, redigere opbevaringspolitikken, du identificerede i det forrige trin, og fjerne postkassen fra listen over modtagere, der er inkluderet i opbevaringspolitikken.
  
### <a name="organization-wide-retention-policies"></a>Opbevaringspolitikker for hele organisationen
  
Opbevaringspolitikker for Exchange og hele Teams gælder for alle postkasser i organisationen. De anvendes på organisationsniveau (ikke postkasseniveau) og returneres, når du kører **cmdlet'en Get-OrganizationConfig** i trin 1. Kør følgende kommando i [Security & Compliance Center PowerShell for](/powershell/exchange/exchange-online-powershell) at identificere opbevaringspolitikker for hele organisationen. Brug GUID'et (herunder ikke præfikset  `mbx` ) for opbevaringspolitikker for hele organisationen, som du identificerede i trin 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Når du har identificeret opbevaringspolitikker for hele organisationen, skal du gå til siden Information **governanceRetention**  >  i Microsoft 365 Overholdelsescenter, redigere hver opbevaringspolitik for hele organisationen, som du identificerede i det forrige trin, og føje postkassen til listen over udeladte modtagere. Hvis du gør dette, fjernes brugerens postkasse fra opbevaringspolitikken.

> [!IMPORTANT]
> Når du udelader en postkasse fra en opbevaringspolitik for hele organisationen, kan det tage op til 24 timer at synkronisere denne ændring og fjerne postkassen fra politikken.

### <a name="retention-labels"></a>Opbevaringsnavne

Når en bruger anvender en etiket, der er konfigureret til at bevare indhold eller bevare og derefter slette indhold i en mappe eller et element i sin postkasse, så er *egenskaben ComplianceTagHoldApplied-postkasse* angivet til **Sand**. Når dette sker, anses postkassen for at være sat i venteposition, som hvis den var sat i retslig tilbageholdelse eller var tildelt en opbevaringspolitik.

For at få vist værdien af *egenskaben ComplianceTagHoldApplied* skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Når du har identificeret, at en postkasse er i venteposition, fordi der er anvendt en opbevaringsmærkat på en mappe eller et element, kan du bruge værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter til at søge efter mærkede  elementer ved hjælp af Betingelse for opbevaringsetiket. Du kan finde flere oplysninger under:

- Afsnittet "Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsetiket" i Få mere at vide [om opbevaringspolitikker og opbevaringsnavne](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Afsnittet "Søgebetingelser" i [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Du kan finde flere oplysninger om navne i [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

### <a name="ediscovery-holds"></a>eDiscovery-vente hold
  
Kør følgende kommandoer i [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at identificere det venteposition, der er knyttet til en eDiscovery-sag (kaldet *eDiscovery-ventepositioner*), der anvendes til postkassen. Brug GUID'et (ikke inklusive præfikset  `UniH` ) for den eDiscovery-venteposition, du identificerede i trin 1. Den anden kommando viser navnet på den eDiscovery-sag, som ventepositionen er knyttet til. Den tredje kommando viser navnet på ventepositionen.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Når du har identificeret navnet på eDiscovery-sagen og ventepositionen, skal du gå til **siden eDiscovery** \> **eDiscovery** i overholdelsescenteret, åbne sagen og fjerne postkassen fra ventepositionen. Du kan finde flere oplysninger om, hvordan du identificerer eDiscovery-ventepositioner, i afsnittet "eDiscovery-ventepositioner" i Sådan identificerer du typen af venteposition i en [Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Trin 4: Fjern forsinkelsen i venteposition fra postkassen

Når en vilkårlig type venteposition fjernes fra en postkasse, angives værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* til **Sand**. Dette sker, næste gang den administrerede mappeassistent behandler postkassen og registrerer, at en venteposition er blevet fjernet. Dette kaldes en forsinkelse *og* betyder, at den faktiske fjernelse af ventepositionen forsinkes i 30 dage for at forhindre data i at blive slettet permanent fra postkassen. (Formålet med en forsinkelse i venteposition er at give administratorer mulighed for at søge efter eller gendanne postkasseelementer, der vil blive slettet, når en venteposition er fjernet.)  Når en forsinkelse er sat i venteposition i postkassen, betragtes postkassen stadig som værende i venteposition i ubegrænset tid, som hvis postkassen var i retslig venteposition. Efter 30 dage udløber forsinkelsen, og Microsoft 365 forsøger automatisk at fjerne forsinkelsen (ved at indstille egenskaben *ForsinkelseHoldAngivet* eller *ForsinkelseReleaseHoldApplied* til **Falsk**), så ventepositionen fjernes. Du kan finde flere oplysninger om forsinkelse i venteposition i afsnittet "Administration af postkasser i venteposition" i Sådan identificeres typen af venteposition i en [Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

Hvis værdien af egenskaben *DelayHoldApplied* eller *DelayReleaseHoldApplied* er angivet til **Sand**, skal du køre en af følgende kommandoer for at fjerne forsinkelsen i venteposition:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Eller

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Du skal være tildelt rollen Juridisk tilbageholdelse i Exchange Online at bruge *parameteren RemoveDelayHoldApplied* eller *RemoveDelayReleaseHoldApplied*.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Trin 5: Slet elementer i mappen Genoprettelige elementer

Nu er du klar til rent faktisk at slette elementer i mappen Genoprettelige elementer ved hjælp af Cmdlet'erne [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) og [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) i Security & Compliance Center PowerShell.

Hvis du vil søge efter elementer, der findes i mappen Genoprettelige elementer, anbefaler vi, at du udfører en *målrettet samling*. Det betyder, at du kun begrænser søgningens omfang til elementer, der er placeret i mappen Genoprettelige elementer. Du kan gøre dette ved at køre scriptet i [artiklen Brug indholdssøgning til målrettede samlinger](use-content-search-for-targeted-collections.md) . Dette script returnerer værdien af mappe-id-egenskaben for alle undermapper i målmappen Genoprettelige elementer. Derefter kan du bruge mappe-id'et i en søgeforespørgsel til at returnere elementer, der er placeret i den pågældende mappe.

Her er en oversigt over processen til at søge efter og slette elementer i en brugers mappe genoprettelige elementer:

1. Kør scriptet målrettet samling, der returnerer mappe-id'erne for alle mapper i målbrugerens postkasse. Scriptet opretter forbindelse til Exchange Online PowerShell og Security & Compliance PowerShell i den samme PowerShell-session. Få mere at vide under [Kør scriptet for at få en liste over mapper til en postkasse](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Kopiér mappe-iD'erne til alle undermapper i mappen Genoprettelige elementer. Du kan også omdirigere outputtet fra scriptet til en tekstfil.

   Her er en liste og beskrivelse af undermapperne i mappen Genoprettelige elementer, som du kan søge efter og slette elementer fra:

   - **Sletninger**: Indeholder ikke-slettede elementer, hvis opbevaringsperiode for slettede elementer ikke er udløbet. Brugere kan gendanne blød-slettede elementer fra denne undermappe ved hjælp af værktøjet Gendan slettede elementer Outlook.

   - **DiscoveryHolds**: Indeholder permanent slettede elementer, der er blevet bevaret af et eDiscovery-hold eller en opbevaringspolitik. Denne undermappe er ikke synlig for slutbrugere.

   - **SubstrateHolds**: Indeholder permanent slettede elementer fra Teams og andre skybaserede apps, der er bevaret af en opbevaringspolitik eller anden type venteposition. Denne undermappe er ikke synlig for slutbrugere.

3. Brug **New-ComplianceSearch-cmdlet'en** (i Security & Compliance Center PowerShell), eller brug værktøjet indholdssøgning i overholdelsescenteret til at oprette en indholdssøgning, der returnerer elementer fra målbrugeren mappe med genoprettelige elementer. Det kan du gøre ved at medtage folderid'et i søgeforespørgslen for alle undermapper, du vil søge i. Den følgende forespørgsel returnerer f.eks. alle meddelelser i undermapperne Sletninger og eDiscoveryHolds:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Du kan finde flere oplysninger og eksempler på kørende indholdssøgninger, der bruger egenskaben mappe-id, under Brug et [mappe-id eller til at udføre en målrettet samling](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Hvis du bruger **cmdlet'en New-ComplianceSearch** til at søge i mappen Genoprettelige elementer, skal du sørge for at bruge cmdlet'en **Start-ComplianceSearch** til at køre søgningen.

4. Når du har oprettet en indholdssøgning og valideret, at den returnerer de elementer, du vil slette, `New-ComplianceSearchAction -Purge -PurgeType HardDelete` skal du bruge kommandoen (i Security & Compliance Center PowerShell) til at slette de elementer, der returneres af indholdssøgningen, som du oprettede i forrige trin, permanent. Du kan f.eks. køre en kommando, der ligner følgende kommando:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Der kan maksimalt slettes 10 elementer pr. postkasse, når du kører den forrige kommando. Det betyder, at du muligvis skal køre `New-ComplianceSearchAction -Purge` kommandoen flere gange for at slette alle de elementer, du vil slette, i mappen Genoprettelige elementer. Hvis du vil slette flere elementer, skal du først fjerne den tidligere overholdelsessøgningshandling. Det gør du ved at køre `Remove-ComplianceSearchAction` cmdlet'en. Hvis du f.eks. vil slette handlingen tømning, der blev kørt i forrige trin, skal du køre følgende kommando:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Når du har gjort dette, kan du oprette en ny handling ved søgning efter overholdelse for at slette flere elementer. Du skal slette hver handling, før du opretter en ny.

   Du kan få en liste over søgehandlinger ved at køre `Get-ComplianceSearchAction` cmdlet'en. Handlinger for tømning identificeres `_Purge` ved at føje dem til navnet på søgningen.

### <a name="verify-that-items-were-deleted"></a>Kontrollér, at elementer er blevet slettet

For at bekræfte at du har slettet elementer fra mappen Genoprettelige elementer i en postkasse, skal du bruge **Get-MailboxFolderStatistics** cmdlet i Exchange Online PowerShell til at kontrollere størrelsen og antallet af elementer i mappen Genoprettelige elementer. Du kan sammenligne disse statistikker med dem, du indsamlede i trin 1.
  
Kør følgende kommando for at få den aktuelle størrelse og samlede antal elementer i mapper og undermapper i mappen Genoprettelige elementer i brugerens primære postkasse.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Kør følgende kommando for at få størrelsen og det samlede antal elementer i mapper og undermapper i mappen Genoprettelige elementer i brugerens arkivpostkasse.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Trin 6: Tilbagedan postkassen til dens tidligere tilstand

Det sidste trin er at vende tilbage til den tidligere konfiguration af postkassen. Det betyder, at du skal nulstille de egenskaber, du har ændret i trin 2, og genanvende de ventende indstillinger, du fjernede i trin 3. Dette omfatter:
  
- Ændring af opbevaringsperioden for slettede elementer tilbage til den forrige værdi. Alternativt kan du blot lade denne angive til 30 dage, den maksimale værdi i Exchange Online.

- Genaktivering af enkelt elementgendannelse.

- Genaktivering af klientadgangsmetoderne, så ejeren kan få adgang til sin postkasse.

- Genanvende de ventende og opbevaringspolitikker, du har fjernet.

- Genaktivering af Administreret mappeassistent for at behandle postkassen.

> [!IMPORTANT]
> Vi anbefaler, at du venter 24 timer efter genaktivering af en venteposition eller opbevaringspolitik (og bekræfter, at den er på plads), før du genaktiverer administreret mappeassistent til behandling af postkassen.
  
Udfør følgende trin (i den angivne rækkefølge) i Exchange Online PowerShell.
  
1. Kør følgende kommando for at ændre opbevaringsperioden for slettede elementer tilbage til den oprindelige værdi. Dette forudsætter, at den forrige indstilling er mindre end 30 dage; f.eks. 14 dage.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Kør følgende kommando for at genaktivere gendannelse af et enkelt element.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Kør følgende kommando for at genaktivere alle klientadgangsmetoder til postkassen.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Genanvende de ventende trin, du fjernede i trin 3. Afhængigt af typen af venteposition skal du bruge en af følgende procedurer.

    **Retslig venteposition**

    Kør følgende kommando for at genaktivere en retslig venteposition for postkassen.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **Direkte hold**

    Brug EAC (eller Exchange Online PowerShell) til at føje postkassen tilbage til In-Place Hold.

    **Opbevaringspolitikker anvendt på bestemte postkasser**

    Brug Microsoft 365 Overholdelsescenter til at føje postkassen tilbage til opbevaringspolitikken. Gå til siden **Information** **governanceRetention** >  i Overholdelsescenter, rediger opbevaringspolitikken, og føj postkassen tilbage til listen over modtagere, som opbevaringspolitikken anvendes på.

    **Opbevaringspolitikker for hele organisationen**

    Hvis du har fjernet en opbevaringspolitik for Exchange hele organisationen ved at udelade den fra politikken, skal du bruge Microsoft 365 Overholdelsescenter til at fjerne postkassen fra listen over ekskluderede brugere. Gå til siden **Information** **governanceRetention** >  i Overholdelsescenter, rediger opbevaringspolitikken for hele organisationen, og fjern postkassen fra listen over udeladte modtagere. Hvis du gør dette, genanvendes opbevaringspolitikken på brugerens postkasse.

    **ventende mails i eDiscovery-sag**

    Brug postkassen Microsoft 365 Overholdelsescenter tilføje postkassen i det venteposition, der er knyttet til en eDiscovery-sag. Gå til **eDiscoveryCore-siden** > , åbn sagen, og føj postkassen tilbage til ventepositionen. 

5. Kør følgende kommando for at give administreret mappeassistent tilladelse til at behandle postkassen igen. Som tidligere nævnt anbefaler vi, at du venter 24 timer efter anvendelse af en venteposition eller opbevaringspolitik (og bekræfter, at den er på plads), før du aktiverer administreret mappeassistent igen.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Hvis du vil bekræfte, at postkassen er blevet gendannet til den tidligere konfiguration, kan du køre følgende kommandoer og derefter sammenligne indstillingerne med dem, du indsamlede i trin 1.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Flere oplysninger

Her er en tabel, der beskriver, hvordan du identificerer forskellige typer ventende indhold baseret på værdierne i egenskaben  *InPlaceHolds*  , når du kører cmdlet'erne **Get-Mailbox** eller **Get-OrganizationConfig** . Du kan finde mere detaljerede oplysninger [under Sådan identificeres den type venteposition, der er placeret på Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

Som tidligere beskrevet skal du fjerne alle ventende elementer og opbevaringspolitikker fra en postkasse, før du kan slette elementer i mappen Genoprettelige elementer.
  
| Ventepositionstype | Eksempelværdi | Sådan identificeres ventepositionen |
|:-----|:-----|:-----|
|Retslig venteposition  <br/> | `True` <br/> |Egenskaben  *LitigationHoldEnabled*  er angivet til  `True`.  <br/> |
|In-Place venteposition  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |Egenskaben  *InPlaceHolds*  indeholder GUID'et for In-Place hold, der er placeret i postkassen. Du kan se, at dette In-Place i venteposition, fordi GUID'et ikke starter med et præfiks.  <br/> Du kan bruge kommandoen `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` i Exchange Online PowerShell til at få oplysninger om In-Place Hold på postkassen.  <br/> |
| Opbevaringspolitikker i Microsoft 365 Overholdelsescenter anvendt på bestemte postkasser  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> eller  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Når du kører **cmdlet'en Get-Mailbox** , indeholder egenskaben  *InPlaceHolds*  også GUID'er for opbevaringspolitikker, der anvendes på postkassen. Du kan identificere opbevaringspolitikker, fordi GUID'et starter med præfikset  `mbx` . Hvis GUID'et for opbevaringspolitikken starter `skp` med præfikset, der angiver, at opbevaringspolitikken anvendes på Skype for Business samtaler.  <br/> Hvis du vil finde identiteten af den opbevaringspolitik, der anvendes til postkassen, skal du køre følgende kommando i Security & Compliance Center PowerShell: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Sørg for at fjerne præfikset  `mbx`  `skp` eller præfikset, når du kører denne kommando.  <br/> |
|Opbevaringspolitikker for hele organisationen i Microsoft 365 Overholdelsescenter  <br/> |Ingen værdi  <br/> eller  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (angiver, at postkassen er udeladt af en politik for hele organisationen)  <br/> |Selvom egenskaben  *InPlaceHolds*  er tom, når du kører cmdlet'en **Get-Mailbox** , kan der stadig være anvendt en eller flere opbevaringspolitikker for hele organisationen på postkassen.  <br/> For at bekræfte dette kan `Get-OrganizationConfig | FL InPlaceHolds` du køre kommandoen i Exchange Online PowerShell for at få en liste over GUID'erne for opbevaringspolitikker for hele organisationen. GUID'et for opbevaringspolitikker for hele organisationen, der anvendes Exchange postkasser, starter med `mbx` præfikset, f.eks. `mbxa3056bb15562480fadb46ce523ff7b02`.  <br/> Hvis du vil finde identiteten af den opbevaringspolitik for hele organisationen, der anvendes til postkassen, skal du køre følgende kommando i Security & Compliance Center PowerShell: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Hvis en postkasse er udeladt fra en opbevaringspolitik for hele organisationen, vises GUID'et for opbevaringspolitikken i egenskaben  *InPlaceHolds*  for brugerens postkasse, når du kører cmdlet'en **Get-Mailbox** . det identificeres ved hjælp af præfikset, f.eks  `-mbx`.  `-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|eDiscovery-sags hold i Microsoft 365 Overholdelsescenter  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |Egenskaben *InPlaceHolds* indeholder også GUID for eventuelle ventepositioner, der er knyttet til en eDiscovery-sag i Microsoft 365 Overholdelsescenter, der kan placeres i postkassen. Du kan se, at dette er en eDiscovery-sag, fordi GUID'et starter med præfikset  `UniH` .  <br/> Du kan bruge  `Get-CaseHoldPolicy` cmdlet'en i Security & Compliance Center PowerShell til at få oplysninger om den eDiscovery-sag, som ventepositionen i postkassen er knyttet til. Du kan f.eks. køre kommandoen for  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` at få vist navnet på den venteposition, der findes i postkassen. Sørg for at fjerne præfikset  `UniH` , når du kører denne kommando.  <br/><br/> For at identiteten af den eDiscovery-sag, som ventepositionen i postkassen er knyttet til, skal du køre følgende kommandoer:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
