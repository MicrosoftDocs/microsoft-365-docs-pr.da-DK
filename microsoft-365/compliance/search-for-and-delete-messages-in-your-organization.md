---
title: Søg efter og slet mails i din organisation
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: Brug funktionen til søgning og tømning i Microsoft 365 Overholdelsescenter til at søge efter og slette en mail fra alle postkasser i organisationen.
ms.openlocfilehash: 9361f7dea0e1b12d50733b9b1d1e91ac15577ab9
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63587876"
---
# <a name="search-for-and-delete-email-messages"></a>Søge efter og slette mails

**Denne artikel gælder for administratorer. Forsøger du at finde elementer i din postkasse, som du vil slette? Se [Finde en meddelelse eller et element med Hurtigsøgning](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

Du kan bruge funktionen Indholdssøgning til at søge efter og slette mails fra alle postkasser i organisationen. Dette kan hjælpe dig med at finde og fjerne potentielt skadelige mails eller mails med høj risiko, f.eks.:

- Meddelelser, der indeholder skadelige vedhæftede filer eller virus

- Phishingmeddelelser

- Meddelelser, der indeholder følsomme data

> [!TIP]
> Hvis din organisation har et Defender for Office 365 Plan 2-abonnement, anbefaler vi, at du bruger den fremgangsmåde, der er beskrevet i Afhjulpet skadelig mail i [Office 365](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365), i stedet for at følge den fremgangsmåde, der er beskrevet i denne artikel.

## <a name="before-you-begin"></a>Før du begynder

- Arbejdsprocessen for søgning og sletning, som er beskrevet i denne artikel, sletter ikke chatmeddelelser eller andet indhold Microsoft Teams. Hvis den indholdssøgning, du opretter i trin 2, returnerer elementer fra Microsoft Teams, slettes disse elementer ikke, når du fjerner elementer i trin 3.

- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af **rollegruppen eDiscovery Manager** eller være tildelt rollen  Overholdelsessøgning i Microsoft 365 Overholdelsescenter. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen Organisationsadministration eller være tildelt rollen Søg  og tøm i overholdelsescenteret Du kan finde oplysninger om at føje brugere til en rollegruppe under Tildele [eDiscovery-tilladelser](assign-ediscovery-permissions.md).

  > [!NOTE]
  > **Rollegruppen Organisationsadministration** findes både i Exchange Online og i Microsoft 365 Overholdelsescenter. Disse er separate rollegrupper, der giver forskellige tilladelser. At være medlem **af organisationsadministrationen** i Exchange Online giver ikke de nødvendige tilladelser til at slette mails. Hvis du ikke har fået tildelt rollen  Søg og tøm i overholdelsescenteret (enten direkte eller via en rollegruppe som f.eks. Organisationsadministration **), modtager** du fejlen i trin 3, når du kører cmdlet'en **New-ComplianceSearchAction** med meddelelsen "Der blev ikke fundet en parameter, der svarer til parameternavnet 'Tøm'".

- Du skal bruge Security & Compliance Center PowerShell til at slette meddelelser. Se [Trin 1 for at](#step-1-connect-to-security--compliance-center-powershell) få en vejledning i, hvordan du opretter forbindelse.

- Der kan maksimalt fjernes 10 elementer pr. postkasse på én gang. Da muligheden for at søge efter og fjerne meddelelser er beregnet til at være et værktøj til hændelsesrespons, hjælper denne grænse med at sikre, at meddelelser hurtigt fjernes fra postkasser. Denne funktion er ikke beregnet til at rydde op i brugerpostkasser.

- Det maksimale antal postkasser i en indholdssøgning, som du kan bruge til at slette elementer ved at udføre en søgning og sletning, er 50.000. Hvis søgningen (som du opretter i trin [2](#step-2-create-a-content-search-to-find-the-message-to-delete) søger i mere end 50.000 postkasser), mislykkes handlingen for tømning (som du opretter i trin 3). Søgning i mere end 50.000 postkasser i en enkelt søgning kan typisk ske, når du konfigurerer søgningen til at medtage alle postkasser i organisationen. Denne begrænsning gælder stadig, selvom mindre end 50.000 postkasser indeholder elementer, der svarer til søgeforespørgslen. Se afsnittet [Flere oplysninger](#more-information) for at få vejledning i at bruge filtre til søgetilladelser til at søge efter og fjerne elementer fra mere end 50.000 postkasser.

- Fremgangsmåden i denne artikel kan kun bruges til at slette elementer i Exchange Online postkasser og offentlige mapper. Du kan ikke bruge den til at slette indhold fra SharePoint eller OneDrive for Business websteder.

- Mailelementer i et gennemsynssæt i Advanced eDiscovery en sag kan ikke slettes ved hjælp af procedurerne i denne artikel. Det skyldes, at elementer i et korrektursæt gemmes på Azure Storage placering og ikke i livetjenesten. Det betyder, at de ikke returneres af den indholdssøgning, du opretter i trin 1. Hvis du vil slette elementer i et korrektursæt, skal du slette Advanced eDiscovery, der indeholder korrektursættet. Du kan få mere at vide [under Luk eller slet Advanced eDiscovery en sag](close-or-delete-case.md).

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Trin 1: Forbind til Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Security & Compliance Center PowerShell for organisationen. Du kan finde en trinvis vejledning under [Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>Trin 2: Opret en indholdssøgning for at finde den meddelelse, du vil slette

Det andet trin er at oprette og køre en indholdssøgning for at finde den meddelelse, du vil fjerne fra postkasser i organisationen. Du kan oprette søgningen ved hjælp af Microsoft 365 Overholdelsescenter eller ved at køre cmdlet'erne **New-ComplianceSearch** og **Start-ComplianceSearch** i Security & Compliance PowerShell. De meddelelser, der svarer til forespørgslen for denne søgning, slettes ved at køre kommandoen **New-ComplianceSearchAction -Tøm** i [trin 3](#step-3-delete-the-message). Hvis du vil have mere at vide om at oprette en indholdssøgning og konfigurere søgeforespørgsler, skal du se følgende emner:

- [Indholdssøgning i Office 365](content-search.md)

- [Nøgleordsforespørgsler til indholdssøgning](keyword-queries-and-search-conditions.md)

- [New-ComplianceSearch](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> De indholdsplaceringer, der søges i i Indholdssøgning, som du opretter i dette trin, kan ikke SharePoint eller OneDrive for Business websteder. Du kan kun medtage postkasser og offentlige mapper i en indholdssøgning, der skal bruges til mails. Hvis Indholdssøgning omfatter websteder, modtager du en fejl i trin 3, når du kører **cmdlet'en New-ComplianceSearchAction** .

### <a name="tips-for-finding-messages-to-remove"></a>Tips, hvordan du finder meddelelser, der skal fjernes

Formålet med søgeforespørgslen er at indsnævre resultaterne af søgningen til kun at være den eller de meddelelser, du vil fjerne. Her er nogle tip:

- Hvis du kender nøjagtigt den tekst eller det udtryk, der bruges i emnelinjen i meddelelsen, kan du bruge **egenskaben** Emne i søgeforespørgslen.

- Hvis du kender den nøjagtige dato (eller datointerval) for meddelelsen, skal du medtage **egenskaben Modtaget** i søgeforespørgslen.

- Hvis du ved, hvem der har sendt meddelelsen, skal du **medtage** egenskaben Fra i søgeforespørgslen.

- Gennemse søgeresultaterne for at bekræfte, at søgningen kun returnerede den meddelelse (eller de meddelelser), du vil slette.

- Brug statistik for vurdering af søgning (vises i detaljeruden for søgningen i Microsoft 365 Overholdelsescenter eller ved at bruge cmdlet'en [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)) for at få en optælling af det samlede antal resultater.

Her er to eksempler på forespørgsler til at finde mistænkelige mails.

- Denne forespørgsel returnerer meddelelser, der er modtaget af brugere mellem 13. april 2016 og 14. april 2016, og som indeholder ordene "handling" og "påkrævet" i emnelinjen.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- Denne forespørgsel returnerer meddelelser, der er sendt af chatsuwloginsset12345@outlook.com, og som indeholder det præcise udtryk "Opdater dine kontooplysninger" i emnelinjen.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

Her er et eksempel på, hvordan du bruger en forespørgsel til at oprette og starte en søgning ved at køre cmdlet'erne **New-ComplianceSearch** og **Start-ComplianceSearch** for at søge i alle postkasser i organisationen:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>Trin 3: Slet meddelelsen

Når du har oprettet og tilpasset en indholdssøgning for at returnere de meddelelser, du vil fjerne, er det sidste trin at køre **kommandoen New-ComplianceSearchAction -Purge** i Security & Compliance PowerShell for at slette meddelelsen. Du kan blød- eller hård slette meddelelsen. En blød-slettet meddelelse flyttes til en brugers mappe med genoprettelige elementer og bevares, indtil opbevaringsperioden for slettede elementer udløber. Permanent slettede meddelelser er markeret til permanent fjernelse fra postkassen og fjernes permanent, næste gang postkassen behandles af den administrerede mappeassistent. Hvis gendannelse af et enkelt element er aktiveret for postkassen, fjernes elementer permanent, når opbevaringsperioden for slettede elementer udløber. Hvis en postkasse er sat i venteposition, bevares slettede meddelelser, indtil varigheden for elementet udløber, eller indtil ventepositionen fjernes fra postkassen.

> [!NOTE]
> Som tidligere nævnt slettes elementer fra Microsoft Teams, der returneres af indholdssøgning, ikke, når du kører kommandoen **New-ComplianceSearchAction -Tømning**.

Hvis du vil køre følgende kommandoer for at slette meddelelser, skal du sørge for, at du har forbindelse til [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

### <a name="soft-delete-messages"></a>Blød sletning af meddelelser

I følgende eksempel sletter kommandoen de søgeresultater, der returneres af indholdssøgning med navnet "Fjern phishingmeddelelse".

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>Slette meddelelser på en hård måde

Hvis du vil slette de elementer, der returneres af indholdssøgningen "Fjern phishingmeddelelse", på en hård måde, skal du køre denne kommando:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

Når du kører de forrige kommandoer til blød- eller permanent sletning, er den søgning, der er angivet af  *parameteren SearchName*  , den Indholdssøgning, du oprettede i trin 1.

Du kan finde flere oplysninger [under New-ComplianceSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Flere oplysninger

- **Hvordan får du status for søgningen og fjernelsen?**

  Kør **Get-ComplianceSearchAction for** at få status på sletningen. Det objekt, der oprettes, når du kører **New-ComplianceSearchAction-cmdlet'en** , navngives ved hjælp af dette format:  `<name of Content Search>_Purge`.

- **Hvad sker der, når du har slettet en meddelelse?**

  En meddelelse, der er blevet slettet med  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` kommandoen, flyttes til mappen Fjernet og kan ikke åbnes af brugeren. Når meddelelsen flyttes til mappen Fjernet, bevares meddelelsen i hele varigheden af opbevaringsperioden for slettede elementer, hvis gendannelse af et enkelt element er aktiveret for postkassen. (I Microsoft 365 er gendannelse af enkelt element aktiveret som standard, når der oprettes en ny postkasse). Når opbevaringsperioden for det slettede element udløber, markeres meddelelsen til permanent sletning og slettes fra Microsoft 365 næste gang postkassen behandles af assistenten til administreret mappe.

  Hvis du bruger `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` kommandoen, flyttes meddelelser til mappen Sletninger i brugerens mappe med genoprettelige elementer. Den bliver ikke øjeblikkeligt fjernet fra Microsoft 365. Brugeren kan gendanne meddelelser i mappen Slettet post under hele varigheden baseret på den opbevaringsperiode for slettede elementer, der er konfigureret for postkassen. Når denne opbevaringsperiode udløber (eller hvis brugeren fjerner meddelelsen, før den udløber), flyttes meddelelsen til mappen Fjernet og kan ikke længere tilgås af brugeren. Når meddelelsen ligger i mappen Fjernet, bevares den i denne periode baseret på den opbevaringsperiode for slettede elementer, der er konfigureret for postkassen, hvis gendannelse af enkelte elementer er aktiveret for postkassen. (I Microsoft 365 er gendannelse af enkelt element aktiveret som standard, når der oprettes en ny postkasse). Når opbevaringsperioden for det slettede element udløber, markeres meddelelsen til permanent sletning og slettes fra Microsoft 365 næste gang postkassen behandles af assistenten til administrerede mapper.

- **Hvad nu, hvis du skal slette en meddelelse fra mere end 50.000 postkasser?**

  Som tidligere nævnt kan du udføre en søgning og tømning på maksimalt 50.000 postkasser (selvom mindre end 50.000 indeholder elementer, der svarer til søgeforespørgslen). Hvis du skal udføre en søgning og tømning på mere end 50.000 postkasser, bør du overveje at oprette filtre for midlertidige søgetilladelser, der reducerer antallet af postkasser, der skal søges i, til mindre end 50.000 postkasser. Hvis din organisation f.eks. indeholder postkasser i forskellige afdelinger, stater eller lande, kan du oprette et filter til søgning i postkasser baseret på en af disse postkasseegenskaber for at søge i et undersæt af postkasser i organisationen. Når du har oprettet filteret for søgetilladelser, skal du oprette søgningen (beskrevet i trin 1) og derefter slette meddelelsen (beskrevet i trin 3). Derefter kan du redigere filteret for at søge efter og fjerne meddelelser i et andet sæt postkasser. Du kan finde flere oplysninger om at oprette filtre for søgetilladelser [under Konfigurer filtrering af tilladelser for indholdssøgning](permissions-filtering-for-content-search.md).

- **Slettes elementer, der ikke er identificeret i søgeresultaterne?**

  Nej, kommandoen "New-ComplianceSearchAction -Tømning sletter ikke ikke-inderede elementer.

- **Hvad sker der, hvis en meddelelse slettes fra en postkasse, som er blevet sat i venteposition In-Place retslig tilbageholdelse eller er tildelt en Microsoft 365 opbevaringspolitik?**

  Når meddelelsen er blevet fjernet og flyttet til mappen Fjernet, bevares meddelelsen, indtil varigheden af ventepositionen udløber. Hvis varigheden af ventepositionen er ubegrænset, bevares elementer, indtil ventepositionen fjernes, eller varigheden af ventepositionen ændres.

- **Hvorfor er søge- og fjern arbejdsprocessen opdelt mellem forskellige rollegrupper for sikkerheds- og overholdelsescenter?**

  Som beskrevet tidligere skal en person være medlem af rollegruppen eDiscovery Manager eller være tildelt rollen som styring af overholdelsessøgning til at søge i postkasser. Hvis du vil slette meddelelser, skal en person være medlem af rollegruppen Organisationsadministration eller være tildelt administrationsrollen Søg og tøm. Det gør det muligt at styre, hvem der kan søge i postkasser i organisationen, og hvem der kan slette meddelelser.
