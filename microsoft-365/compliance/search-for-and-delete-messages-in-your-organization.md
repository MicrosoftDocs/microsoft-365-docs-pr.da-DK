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
description: Brug funktionen Søg og fjern på Microsoft Purview-overholdelsesportalen til at søge efter og slette en mail fra alle postkasser i organisationen.
ms.openlocfilehash: 23eeff8078dbd7ab65b0bddb9684aa81d65aab94
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936241"
---
# <a name="search-for-and-delete-email-messages"></a>Søg efter og slet mails

**Denne artikel er til administratorer. Forsøger du at finde elementer i postkassen, som du vil slette? Se [Find en meddelelse eller et element med Hurtigsøgning](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

Du kan bruge funktionen Indholdssøgning til at søge efter og slette mails fra alle postkasser i din organisation. Dette kan hjælpe dig med at finde og fjerne potentielt skadelige eller højrisikomails, f.eks.:

- Meddelelser, der indeholder farlige vedhæftede filer eller virus

- Phishing-meddelelser

- Meddelelser, der indeholder følsomme data

> [!TIP]
> Hvis din organisation har et abonnement på Defender for Office 365 Plan 2, anbefaler vi, at du bruger den procedure, der er beskrevet i [Afhjælpning af skadelig mail, der leveres i Office 365, i](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) stedet for at følge den procedure, der er beskrevet i denne artikel.

## <a name="before-you-begin"></a>Før du begynder

- Den arbejdsproces til søgning og tømning, der er beskrevet i denne artikel, sletter ikke chatbeskeder eller andet indhold fra Microsoft Teams. Hvis den indholdssøgning, du opretter i trin 2, returnerer elementer fra Microsoft Teams, slettes disse elementer ikke, når du fjerner elementer i trin 3. Hvis du vil søge efter og slette chatmeddelelser, skal du se [Søg efter og fjern chatbeskeder i Teams](search-and-delete-Teams-chat-messages.md).

- Hvis du vil oprette og køre en indholdssøgning, skal du være medlem af **rollegruppen eDiscovery Manager** eller være tildelt rollen **Søgning efter overholdelse** på Microsoft Purview-overholdelsesportalen. Hvis du vil slette meddelelser, skal du være medlem af rollegruppen **Organisationsadministration** eller tildeles rollen **Søg og fjern** i overholdelsescenteret Du kan finde oplysninger om, hvordan du føjer brugere til en rollegruppe, under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).

  > [!NOTE]
  > Rollegruppen **Organisationsadministration** findes både i Exchange Online og på overholdelsesportalen. Dette er separate rollegrupper, der giver forskellige tilladelser. Når du er medlem af **Organisationsadministration** i Exchange Online giver du ikke de nødvendige tilladelser til at slette mails. Hvis du ikke har fået tildelt rollen **Søg og fjern** i Overholdelsescenter (enten direkte eller via en rollegruppe, f.eks **. Organisationsadministration**), får du vist en fejl i trin 3, når du kører Cmdlet'en **New-ComplianceSearchAction** med meddelelsen "Der blev ikke fundet en parameter, der svarer til parameternavnet "Fjern".

- Du skal bruge Security & Compliance Center PowerShell til at slette meddelelser. Se [Trin 1](#step-1-connect-to-security--compliance-center-powershell) for at få instruktioner om, hvordan du opretter forbindelse.

- Der kan maksimalt fjernes 10 elementer pr. postkasse på én gang. Da funktionen til at søge efter og fjerne meddelelser er beregnet til at være et værktøj til svar på hændelser, hjælper denne grænse med at sikre, at meddelelser hurtigt fjernes fra postkasser. Denne funktion er ikke beregnet til at rydde op i brugerpostkasser.

- Det maksimale antal postkasser i en indholdssøgning, som du kan bruge til at slette elementer ved at udføre en søge- og tømningshandling, er 50.000. Hvis søgningen (som du opretter i [trin 2](#step-2-create-a-content-search-to-find-the-message-to-delete) , søger i mere end 50.000 postkasser, mislykkes handlingen Fjern (som du opretter i trin 3). Søgning i mere end 50.000 postkasser i en enkelt søgning kan typisk ske, når du konfigurerer søgningen til at omfatte alle postkasser i din organisation. Denne begrænsning gælder stadig, selvom mindre end 50.000 postkasser indeholder elementer, der svarer til søgeforespørgslen. Se afsnittet [Flere oplysninger](#more-information) for at få vejledning i, hvordan du bruger filtre for søgetilladelser til at søge efter og fjerne elementer fra mere end 50.000 postkasser.

- Proceduren i denne artikel kan kun bruges til at slette elementer i Exchange Online postkasser og offentlige mapper. Du kan ikke bruge den til at slette indhold fra SharePoint eller OneDrive for Business websteder.

- Mailelementer i et korrektursæt i en eDiscovery-sag (Premium) kan ikke slettes ved hjælp af procedurerne i denne artikel. Det skyldes, at elementer i et korrektursæt er gemt på en Azure Storage placering og ikke i livetjenesten. Det betyder, at de ikke returneres af den indholdssøgning, du opretter i trin 1. Hvis du vil slette elementer i et korrektursæt, skal du slette eDiscovery-sagen (Premium), der indeholder korrektursættet. Du kan finde flere oplysninger under [Luk eller slet en eDiscovery-sag (Premium).](close-or-delete-case.md)

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>Trin 1: Forbind til Security & Compliance Center PowerShell

Det første trin er at oprette forbindelse til Security & Compliance Center PowerShell for din organisation. Du kan finde en trinvis vejledning under [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>Trin 2: Opret en indholdssøgning for at finde den meddelelse, der skal slettes

Det andet trin er at oprette og køre en indholdssøgning for at finde den meddelelse, du vil fjerne fra postkasser i din organisation. Du kan oprette søgningen ved hjælp af overholdelsesportalen eller ved at køre **New-ComplianceSearch** - og **Start-ComplianceSearch-cmdlet'erne** i Security & Compliance PowerShell. De meddelelser, der stemmer overens med forespørgslen for denne søgning, slettes ved at køre kommandoen **New-ComplianceSearchAction -Purge** i [trin 3](#step-3-delete-the-message). Du kan finde oplysninger om oprettelse af en indholdssøgning og konfiguration af søgeforespørgsler i følgende emner:

- [Indholdssøgning i Office 365](content-search.md)

- [Nøgleordsforespørgsler for indholdssøgning](keyword-queries-and-search-conditions.md)

- [Nyt overholdelsessøg](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> De indholdsplaceringer, der søges i i den indholdssøgning, du opretter i dette trin, må ikke indeholde SharePoint eller OneDrive for Business websteder. Du kan kun inkludere postkasser og offentlige mapper i en indholdssøgning, der bruges til mails. Hvis indholdssøgningen indeholder websteder, får du vist en fejl i trin 3, når du kører Cmdlet'en **New-ComplianceSearchAction** .

### <a name="tips-for-finding-messages-to-remove"></a>Tips til søgning efter meddelelser, der skal fjernes

Målet med søgeforespørgslen er kun at begrænse resultaterne af søgningen til den eller de meddelelser, du vil fjerne. Her er nogle tip:

- Hvis du kender den nøjagtige tekst eller det udtryk, der bruges i emnelinjen i meddelelsen, skal du bruge egenskaben **Subject** i søgeforespørgslen.

- Hvis du ved, at nøjagtig dato (eller datointerval) for meddelelsen, skal du medtage egenskaben **Received** i søgeforespørgslen.

- Hvis du ved, hvem der har sendt meddelelsen, skal du medtage egenskaben **From** i søgeforespørgslen.

- Gennemse søgeresultaterne for at bekræfte, at søgningen kun returnerede den eller de meddelelser, du vil slette.

- Brug statistik for søgeestimater (der vises i detaljeruden for søgningen på overholdelsesportalen eller ved hjælp af [Get-ComplianceSearch-cmdlet'en](/powershell/module/exchange/get-compliancesearch) ) til at få et antal af det samlede antal resultater.

Her er to eksempler på forespørgsler til at finde mistænkelige mails.

- Denne forespørgsel returnerer meddelelser, der blev modtaget af brugere mellem den 13. april 2016 og den 14. april 2016, og som indeholder ordene "handling" og "påkrævet" i emnelinjen.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- Denne forespørgsel returnerer meddelelser, der er sendt af chatsuwloginsset12345@outlook.com, og som indeholder det nøjagtige udtryk "Opdater dine kontooplysninger" i emnelinjen.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

Her er et eksempel på, hvordan du bruger en forespørgsel til at oprette og starte en søgning ved at køre Cmdlet'erne **New-ComplianceSearch** og **Start-ComplianceSearch** for at søge i alle postkasser i organisationen:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>Trin 3: Slet meddelelsen

Når du har oprettet og tilpasset en indholdssøgning for at returnere de meddelelser, du vil fjerne, er det sidste trin at køre kommandoen **New-ComplianceSearchAction -Purge** i Security & Compliance PowerShell for at slette meddelelsen. Du kan blød- eller hard-slette meddelelsen. En blød slettet meddelelse flyttes til en brugers mappe med elementer, der kan gendannes, og bevares, indtil opbevaringsperioden for slettede elementer udløber. Hårdt slettede meddelelser er markeret til permanent fjernelse fra postkassen og fjernes permanent, næste gang postkassen behandles af Assistent til administrerede mapper. Hvis gendannelse af enkelt element er aktiveret for postkassen, fjernes hårdt slettede elementer permanent, når opbevaringsperioden for slettede elementer udløber. Hvis en postkasse sættes i venteposition, bevares slettede meddelelser, indtil elementets varighed af venteposition udløber, eller indtil ventepositionen fjernes fra postkassen.

> [!NOTE]
> Som tidligere nævnt slettes elementer fra Microsoft Teams, der returneres af indholdssøgning, ikke, når du kører kommandoen **New-ComplianceSearchAction -Purge**.

Hvis du vil køre følgende kommandoer til at slette meddelelser, skal du sørge for, at du har [forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

### <a name="soft-delete-messages"></a>Meddelelser med blød sletning

I følgende eksempel sletter kommandoen de søgeresultater, der returneres af en indholdssøgning med navnet "Fjern phishing-meddelelse".

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>Meddelelser, der er blevet slettet hårdt

Hvis du vil slette de elementer, der returneres af indholdssøgningen "Fjern phishing-meddelelse", skal du køre denne kommando:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

Når du kører de forrige kommandoer til meddelelser med blød eller hård sletning, er den søgning, der er angivet i parameteren  *SearchName*  , den indholdssøgning, du oprettede i trin 1.

Du kan få flere oplysninger i [New-ComplianceSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Flere oplysninger

- **Hvordan får du status på søge- og fjernhandlingen?**

  Kør **Get-ComplianceSearchAction** for at få status på slettehandlingen. Det objekt, der oprettes, når du kører **New-ComplianceSearchAction-cmdlet'en** , navngives ved hjælp af dette format:  `<name of Content Search>_Purge`.

- **Hvad sker der, når du har slettet en meddelelse?**

  En meddelelse, der slettes med kommandoen,  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` flyttes til mappen Rensede og kan ikke åbnes af brugeren. Når meddelelsen er flyttet til mappen Renser, bevares meddelelsen, så længe den slettede elementopbevaringsperiode varer, hvis genoprettelse af et enkelt element er aktiveret for postkassen. (I Microsoft 365 aktiveres genoprettelse af enkelte elementer som standard, når der oprettes en ny postkasse). Når opbevaringsperioden for slettede elementer udløber, markeres meddelelsen til permanent sletning og fjernes fra Microsoft 365 næste gang postkassen behandles af assistenten til administrerede mapper.

  Hvis du bruger kommandoen `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` , flyttes meddelelser til mappen Sletninger i brugerens mappe Genoprettelige elementer. Den fjernes ikke fra Microsoft 365 med det samme. Brugeren kan gendanne meddelelser i mappen Slettet post i varigheden baseret på den opbevaringsperiode for slettet element, der er konfigureret for postkassen. Når denne opbevaringsperiode udløber (eller hvis brugeren fjerner meddelelsen, før den udløber), flyttes meddelelsen til mappen Udtømning og kan ikke længere tilgås af brugeren. Når meddelelsen er i mappen Renser, bevares den i varigheden baseret på den opbevaringsperiode for slettet element, der er konfigureret for postkassen, hvis gendannelse af enkelte elementer er aktiveret for postkassen. (I Microsoft 365 aktiveres genoprettelse af enkelte elementer som standard, når der oprettes en ny postkasse). Når opbevaringsperioden for slettede elementer udløber, markeres meddelelsen til permanent sletning og fjernes fra Microsoft 365 næste gang, postkassen behandles af assistenten til administrerede mapper.

- **Hvad nu, hvis du skal slette en meddelelse fra mere end 50.000 postkasser?**

  Som tidligere angivet kan du udføre en søge- og tømshandling på maksimalt 50.000 postkasser (også selvom mindre end 50.000 indeholder elementer, der svarer til søgeforespørgslen). Hvis du skal udføre en søge- og tømningshandling på mere end 50.000 postkasser, kan du overveje at oprette midlertidige søgetilladelsesfiltre, der reducerer antallet af postkasser, der søges i, til mindre end 50.000 postkasser. Hvis din organisation f.eks. indeholder postkasser i forskellige afdelinger, stater eller lande, kan du oprette et filter for søgetilladelser for en postkasse baseret på en af disse postkasseegenskaber for at søge i et undersæt af postkasser i din organisation. Når du har oprettet filteret for søgetilladelser, skal du oprette søgningen (beskrevet i trin 1) og derefter slette meddelelsen (beskrevet i trin 3). Derefter kan du redigere filteret for at søge efter og fjerne meddelelser i et andet sæt postkasser. Du kan finde flere oplysninger om oprettelse af filtre for søgetilladelser under [Konfigurer filtrering af tilladelser for indholdssøgning](permissions-filtering-for-content-search.md).

- **Vil ikke-indekserede elementer, der er inkluderet i søgeresultaterne, blive slettet?**

  Nej, kommandoen 'New-ComplianceSearchAction -Purge sletter ikke ikke ikke-indekserede elementer.

- **Hvad sker der, hvis en meddelelse slettes fra en postkasse, der er placeret i venteposition In-Place eller procesførelse, eller som er tildelt en Microsoft 365 opbevaringspolitik?**

  Når meddelelsen er fjernet og flyttet til mappen Renser, bevares meddelelsen, indtil varigheden af ventepositionen udløber. Hvis varigheden af ventepositionen er ubegrænset, bevares elementer, indtil ventepositionen fjernes, eller varigheden af ventepositionen ændres.

- **Hvorfor er arbejdsprocessen for søgning og fjernelse opdelt mellem forskellige rollegrupper for Sikkerheds- og Overholdelsescenter?**

  Som tidligere forklaret skal en person være medlem af rollegruppen eDiscovery Manager eller tildeles rollen Styring af overholdelsessøgning til søgepostkasser. Hvis du vil slette meddelelser, skal en person være medlem af rollegruppen Organisationsadministration eller tildeles administrationsrollen Søg og fjern. Det gør det muligt at styre, hvem der kan søge i postkasser i organisationen, og hvem der kan slette meddelelser.
