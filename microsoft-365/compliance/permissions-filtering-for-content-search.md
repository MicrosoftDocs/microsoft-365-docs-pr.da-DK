---
title: Konfigurer filtrering af tilladelser for eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: Brug filtrering af søgetilladelser til kun at lade eDiscovery-ledere søge i et undersæt af postkasser og websteder i din organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba8cfaaec45ceefff89b17b561a5e80bebbdade6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098796"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>Konfigurer filtrering af tilladelser for eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge filtrering af søgetilladelser til kun at lade en eDiscovery-leder søge i et undersæt af postkasser og websteder i din organisation. Du kan også bruge filtrering af tilladelser til at lade den samme eDiscovery-administrator søge efter postkasse eller webstedsindhold, der opfylder et bestemt søgekriterium. Du kan f.eks. lade en eDiscovery-leder søge i postkasser for brugere på en bestemt placering eller afdeling. Det gør du ved at oprette et filter, der bruger et understøttet modtagerfilter til at begrænse, hvilke postkasser en bestemt bruger eller gruppe af brugere kan søge i. Du kan også oprette et filter, der angiver, hvilket postkasseindhold en bruger kan søge efter. Dette gøres ved at oprette et filter, der bruger en meddelelsesegenskab, der kan søges i. På samme måde kan du lade en eDiscovery-leder søge efter bestemte SharePoint websteder i din organisation. Det gør du ved at oprette et filter, der begrænser, hvilket websted der kan søges på. Du kan også oprette et filter, der angiver, hvilket webstedsindhold der kan søges i. Dette gøres ved at oprette et filter, der bruger en webstedsegenskab, der kan søges i.

Der anvendes filtre for søgetilladelser, når du søger efter indhold ved hjælp af indholdssøgning, Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium) på Microsoft Purview-overholdelsesportalen. Når der anvendes et filter for søgetilladelser for en bestemt bruger, kan den pågældende bruger udføre følgende søgerelaterede handlinger:

- Søg efter indhold

- Vis søgeresultater

- Eksportér søgeresultater

- Fjern elementer, der returneres af en søgning

Du kan også bruge filtrering af søgetilladelser til at oprette logiske grænser (kaldet *overholdelsesgrænser*) i en organisation, der styrer placeringen af brugerindhold (f.eks. postkasser, SharePoint websteder og OneDrive konti), som bestemte eDiscovery-ledere kan søge efter. Du kan finde flere oplysninger under [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md).
  
Følgende fire cmdlet'er i Security & Compliance PowerShell giver dig mulighed for at konfigurere og administrere filtre for søgetilladelser:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Krav til konfiguration af filtrering af tilladelser

- Hvis du vil køre cmdlet'erne til overholdelse af sikkerhed, skal du være medlem af rollegruppen Organisationsadministration på overholdelsesportalen. Du kan få flere oplysninger [under Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Du skal oprette forbindelse til både Exchange Online og Security & Compliance Center PowerShell for at bruge cmdlet'erne til overholdelse af sikkerhed. Dette er nødvendigt, fordi disse cmdlet'er kræver adgang til postkasseegenskaber, og derfor skal du oprette forbindelse til Exchange Online PowerShell. Se trinnene i næste afsnit.

- Se afsnittet [Flere oplysninger](#more-information) for at få flere oplysninger om filtre for søgetilladelser.

- Filtrering af søgetilladelser gælder for inaktive postkasser, hvilket betyder, at du kan bruge filtrering af postkasse- og postkasseindhold til at begrænse, hvem der kan søge i en inaktiv postkasse. Se afsnittet [Flere oplysninger](#more-information) for at få flere oplysninger om filtrering af tilladelser og inaktive postkasser.

- Filtrering af søgetilladelser kan ikke bruges til at begrænse, hvem der kan søge i offentlige mapper i Exchange.

- Der er ingen grænse for antallet af filtre for søgetilladelser, der kan oprettes i en organisation. En søgeforespørgsel kan dog højst have 100 betingelser. I dette tilfælde defineres en betingelse som noget, der er forbundet til forespørgslen af en boolesk operator (f.eks **. AND**, **OR** og **NEAR**). Grænsen for antallet af betingelser omfatter selve søgeforespørgslen plus alle filtre for søgetilladelser, der anvendes på den bruger, der kører søgningen. Jo flere søgetilladelser du har (især hvis disse filtre anvendes på den samme bruger eller gruppe af brugere), jo større er chancen for at overskride det maksimale antal betingelser for en søgning. Hvis du vil forhindre din organisation i at nå betingelsesgrænsen, skal du holde antallet af søgetilladelsersfiltre i din organisation så få som muligt, så de opfylder dine forretningskrav. Du kan finde flere oplysninger under [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Forbind til Exchange Online og security & Compliance Center PowerShell i en enkelt session

Før du kan køre scriptet i dette afsnit, skal du downloade og installere Exchange Online PowerShell V2-modulet. Du kan få flere oplysninger [under Om Exchange Online PowerShell V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnssuffiks af **.ps1**. Du kan f.eks. gemme den i en fil med navnet **ConnectEXO-SCC.ps1**.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. Åbn Windows PowerShell på din lokale computer, gå til den mappe, hvor det script, du oprettede i det forrige trin, er placeret, og kør derefter scriptet, f.eks.:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Hvordan ved du, om det virkede? Når du har kørt scriptet, importeres cmdlet'er fra Exchange Online og security & Compliance PowerShell til din lokale Windows PowerShell session. Hvis du ikke modtager nogen fejl, har du oprettet forbindelse. En hurtig test er at køre PowerShell-cmdlet'er Exchange Online & Compliance Center. Du kan f.eks. køre og **Get-Mailbox** og **Get-ComplianceSearch**.

Hvis du vil foretage fejlfinding af PowerShell-forbindelsesfejl, skal du se:

- [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

**New-ComplianceSecurityFilter** bruges til at oprette et filter for søgetilladelser. Her er den grundlæggende syntaks for denne cmdlet:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

I følgende afsnit beskrives parametrene for denne cmdlet. Alle parametre er påkrævet for at oprette et filter for søgetilladelser.

### <a name="filtername"></a>*FilterName*

Parameteren  _FilterName_ angiver navnet på tilladelsesfilteret. Dette navn bruges til at identificere et filter, når du bruger cmdlet'erne **Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** og **Remove-ComplianceSecurityFilter** .

### <a name="filters"></a>*Filtre*

Parameteren  _Filters_ angiver søgekriterierne for sikkerhedsfilteret for overholdelse. Du kan oprette tre forskellige typer filtre:  

- **Postkasse eller OneDrive filtrering:** Denne type filter angiver, hvilke postkasser og OneDrive konti de tildelte brugere (angivet af parameteren _Brugere_) kan søge efter. Denne type filter kaldes et filter *for indholdsplacering* , fordi det definerer de indholdsplaceringer, som en bruger kan søge efter. Syntaksen for denne type filter er **Mailbox_** _MailboxPropertyName_, hvor _MailboxPropertyName_ angiver en postkasseegenskab, der bruges til at omfatte postkasserne og OneDrive konti, der kan søges i. Postkassefilteret `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` gør det f.eks. muligt for brugeren, der er tildelt dette filter, kun at søge i de postkasser og OneDrive konti, der har værdien "OttawaUsers" i egenskaben CustomAttribute10.

  Alle understøttede modtageregenskaber, der kan filtreres, kan bruges til egenskaben _MailboxPropertyName_ i en postkasse eller OneDrive filter. I følgende tabel vises fire almindeligt anvendte modtageregenskaber, der bruges til at oprette en postkasse eller et OneDrive filter. Tabellen indeholder også et eksempel på brug af egenskaben i et filter.

  |Egenskabsnavn  |Eksempel  |
  |---------|---------|
  |Alias    |`"Mailbox_Alias -like 'v-'"`         |
  |Virksomhed  |`"Mailbox_Company -eq 'Contoso'"`        |
  |Land eller område |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Institut |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Filtrering af postkasseindhold:** Denne type filter anvendes på det indhold, der kan søges i. Denne type filter kaldes et *indholdsfilter* , fordi det angiver det postkasseindhold eller de søgbare mailegenskaber, som de tildelte brugere kan søge efter. Syntaksen for denne type filter er **MailboxContent_** _SearchablePropertyName, hvor  _SearchablePropertyName_ angiver en KQL-egenskab (Keyword Query Language), som kan angives i en søgning. Indholdsfilteret `"MailboxContent_Recipients  -like 'contoso.com'"` for postkassen gør det f.eks. muligt for brugeren at tildele dette filter til kun at søge efter meddelelser, der er sendt til modtagere i det contoso.com domæne. Du kan finde en liste over søgbare mailegenskaber under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Et enkelt søgefilter må ikke indeholde et postkassefilter og et indholdsfilter for en postkasse. Hvis du vil kombinere disse i et enkelt filter, skal du bruge en [filterliste](#using-a-filters-list-to-combine-filter-types).  Men et filter kan indeholde en mere kompleks forespørgsel af samme type. Det kan f.eks. `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Filtrering af websteds- og webstedsindhold:** Der er to SharePoint- og OneDrive-relaterede filtre, som du kan bruge til at angive, hvilket websted eller webstedsindhold de tildelte brugere kan søge efter.

  - **Site_**_Egenskab for søgbart websted_
  
  - **SiteContent_**_Søgebart webstedEgenskab_
  
   Disse to filtre er udskiftelige. Og returnerer f.eks `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"`  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` . de samme resultater. Du kan finde en liste over søgbare webstedsegenskaber under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties) Du finder en mere komplet liste under [Oversigt over gennemsøgte og administrerede egenskaber i SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Egenskaber, der er markeret med **Ja** i kolonnen **Kan forespørges** , kan bruges til at oprette et websteds- eller webstedsindholdsfilter.  

  > [!IMPORTANT]
  > Konfiguration af et webstedsfilter med en af de understøttede egenskaber betyder ikke, at webstedsegenskaben i filteret overføres til alle dokumenter på det pågældende websted. Det betyder, at brugeren stadig er ansvarlig for at udfylde de specifikke egenskabsfelter, der er knyttet til dokumenterne på det pågældende websted, for at webstedsfilteret kan fungere og registrere det rigtige indhold. Hvis brugeren f.eks. har anvendt et sikkerhedsfilter "Site_RefineableString00 -eq 'abc'", og derefter kører brugeren en søgning ved hjælp af nøgleordsforespørgslen "xyz". Sikkerhedsfilteret føjes til forespørgslen, og den faktiske forespørgsel, der kører, vil være "xyz **AND RefineableString0:'abc'**". Brugeren skal sikre, at dokumenter på webstedet har værdier i feltet RefineableString00 som "abc". Hvis ikke, returnerer søgeforespørgslen ikke nogen resultater.

Vær opmærksom på følgende, når du konfigurerer parameteren *Filtre* for filtre for filtre for søgetilladelser:

- I modsætning til postkasser er der ikke et indholdsplaceringsfilter for websteder, selvom filteret *Websted* ligner et placeringsfilter. Alle filtre for SharePoint og OneDrive er indholdsfiltre (hvilket også er grunden til *, at Site_* og *SiteContent_* filtre er synonyme), fordi webstedsrelaterede egenskaber som *Path* stemples direkte på dokumenterne. Hvorfor er det her? Det er et resultat af den måde, SharePoint er designet på. I SharePoint findes der ikke et "webstedsobjekt" med egenskaber, f.eks. med Exchange postkasser. Derfor stemples egenskaben *Path* på dokumentet og indeholder URL-adressen på det websted, hvor dokumentet er placeret. Derfor anses et *webstedsfilter* for at være et indholdsfilter og ikke et filter for indholdsplacering.

- Du skal oprette et filter for søgetilladelser for udtrykkeligt at forhindre brugerne i at søge i indholdsplaceringer i en bestemt tjeneste (f.eks. forhindre en bruger i at søge i en Exchange postkasse eller et SharePoint websted). Det vil sige, at oprettelse af et filter for søgetilladelser, der giver en bruger mulighed for at søge på alle SharePoint websteder i organisationen, ikke forhindrer brugeren i at søge i postkasser. Hvis du f.eks. vil tillade, at SharePoint administratorer kun søger SharePoint websteder, skal du oprette et filter, der forhindrer dem i at søge i postkasser. På samme måde skal du oprette et filter, der forhindrer Exchange administratorer i kun at søge i postkasser, så de ikke kan søge på websteder.

### <a name="users"></a>*Brugere*

Parameteren  _Users_ angiver de brugere, der anvender dette filter på deres søgninger. Identificer brugere efter deres alias eller primære SMTP-adresse. Du kan angive flere værdier adskilt af kommaer, eller du kan tildele filteret til alle brugere ved hjælp af værdien **Alle**.

Du kan også bruge parameteren  _Brugere_ til at angive en rollegruppe for overholdelsesportalen. Det giver dig mulighed for at oprette en brugerdefineret rollegruppe og derefter tildele denne rollegruppe et søgetilladelsesfilter. Lad os f.eks. sige, at du har en brugerdefineret rollegruppe for eDiscovery-ledere for det amerikanske datterselskab af et multinationalt selskab. Du kan bruge parameteren  _Users_ til at angive denne rollegruppe (ved hjælp af egenskaben Name for rollegruppen) og derefter bruge parameteren  _Filter_ til kun at søge i postkasser i USA. Du kan ikke angive distributionsgrupper med denne parameter.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Brug af en filterliste til at kombinere filtertyper

En *filterliste* er et filter, der indeholder et postkassefilter og et webstedsfilter adskilt af et komma. Dette komma fungerer også som en **OR-operator** . Brug af en filterliste er den eneste understøttede metode til kombination af forskellige filtertyper. I følgende eksempel kan du se, at et komma adskiller **filtrene Postkasse** og **Websted** :

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Når et filter, der indeholder en filterliste, behandles under kørsel af en søgning, oprettes der to filtre for søgetilladelser fra listen over filtre: Et for hvert filter, der er adskilt af et komma. I det forrige eksempel ville der derfor blive oprettet et filter for søgetilladelser for én postkasse og ét filter for webstedssøgningstilladelser. Disse filtre er forbundet af operatoren **OR** .

Et alternativ til at bruge en filterliste kan være at oprette to separate søgetilladelsesfiltre. I det forrige eksempel skulle du oprette ét filter for postkasseattributten og ét filter for webstedsattributten. I begge tilfælde er resultaterne de samme. Det er en præference at bruge en filterliste eller oprette separate filtre for søgetilladelser.

Vær opmærksom på følgende, når du bruger en filterliste:

- Du skal bruge en filterliste til at oprette et filter, der indeholder et **postkassefilter** og et filter **af typen MailboxContent** .

- Hver komponent på en filterliste kan indeholde en kompleks filtersyntaks. Filtrene for postkassen og webstedet kan f.eks. indeholde flere filtre adskilt af en **-eller-operator** :

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Eksempler på oprettelse af filtre for søgetilladelser

Her er eksempler på, hvordan du bruger cmdlet'en **New-ComplianceSecurityFilter** til at oprette et filter for søgetilladelser.

I dette eksempel kan medlemmer af rollegruppen "US Discovery Managers" kun søge i postkasser og OneDrive konti i USA.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
I dette eksempel kan brugeren annb@contoso.com kun udføre søgehandlinger for postkasser og OneDrive konti i Canada. Dette filter indeholder den trecifrede numeriske landekode for Canada fra ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

I dette eksempel kan brugerne kun søge i de postkasser og OneDrive konti, der har værdien 'Marketing' for postkasseegenskaben CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

I dette eksempel kan medlemmer af rollegruppen "Fourth Coffee eDiscovery Managers" kun søge i de postkasser og OneDrive konti, der har værdien 'FourthCoffee' for egenskaben Afdelingspostkasse. Filteret gør det også muligt for medlemmer af rollegruppen at søge efter dokumenter på webstedet fjerde kaffe SharePoint.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> I det forrige eksempel skal der medtages et ekstra webstedsindholdsfilter (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`), så medlemmer af rollegruppen kan søge efter dokumenter i OneDrive konti. Hvis dette filter ikke er inkluderet, tillader filteret kun, at medlemmer af rollegruppen søger efter dokumenter, der er placeret i `https://contoso.sharepoint.com/sites/FourthCoffee`.

I dette eksempel kan medlemmer af rollegruppen eDiscovery Manager kun søge i postkasser og OneDrive konti for medlemmer af ottawa-brugerdistributionsgruppen. Den Get-DistributionGroup cmdlet i Exchange Online PowerShell bruges til at finde medlemmerne af Ottawa Users-gruppen.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

Dette eksempel forhindrer alle brugere i at udføre søgehandlinger på postkasserne og OneDrive konti for medlemmer af distributionsgruppen Executive Team. Det betyder, at brugerne kan slette indhold fra disse postkasser. Get-DistributionGroup-cmdlet'en i Exchange Online PowerShell bruges til at finde medlemmerne af gruppen Executive Team.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

I dette eksempel kan medlemmer af den brugerdefinerede rollegruppe OneDrive eDiscovery-ledere kun søge efter indhold i OneDrive konti i organisationen.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
I dette eksempel begrænses brugeren til kun at udføre søgehandlinger på mails, der sendes i løbet af kalenderåret 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

I lighed med det forrige eksempel begrænser dette eksempel brugeren til kun at udføre søgehandlinger på dokumenter, der senest blev ændret på et tidspunkt i kalenderåret 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

I dette eksempel forhindres medlemmer af rollegruppen "OneDrive registreringsadministratorer" i at udføre søgehandlinger på en hvilken som helst postkasse i organisationen.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

Dette eksempel forhindrer, at nogen i organisationen udfører søgehandlinger på mails, der er sendt eller modtaget af janets eller sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

I dette eksempel bruges en filterliste til at kombinere postkasse- og webstedsfiltre. I dette eksempel er postkassefilteret et indholdsplaceringsfilter, og webstedsfilteret er et indholdsfilter.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter** bruges til at returnere en liste over søgetilladelsers filtre. Brug parameteren  _FilterName_ til at returnere oplysninger om et bestemt søgefilter.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter** bruges til at redigere et eksisterende filter for søgetilladelser. I følgende afsnit beskrives parametrene for denne cmdlet. Den eneste påkrævede parameter er  _FilterName_.
  
### <a name="filtername"></a>*FilterName*

Parameteren  _FilterName_ angiver navnet på tilladelsesfilteret.

### <a name="users"></a>*Brugere*

Parameteren  _Users_ angiver de brugere, der anvender dette filter på deres søgninger. Da dette er en egenskab med flere værdier, overskriver angivelse af en bruger eller gruppe af brugere med denne parameter den eksisterende liste over brugere. Se følgende eksempler for at få vist syntaksen for at tilføje og fjerne de valgte brugere.

Du kan også bruge parameteren  _Brugere_ til at angive en rollegruppe for overholdelsesportalen. Det giver dig mulighed for at oprette en brugerdefineret rollegruppe og derefter tildele denne rollegruppe et søgetilladelsesfilter. Lad os f.eks. sige, at du har en brugerdefineret rollegruppe for eDiscovery-ledere for det amerikanske datterselskab af et multinationalt selskab. Du kan bruge parameteren  _Users_ til at angive denne rollegruppe (ved hjælp af egenskaben Name for rollegruppen) og derefter bruge parameteren  _Filter_ til kun at søge i postkasser i USA. Du kan ikke angive distributionsgrupper med denne parameter.

### <a name="filters"></a>*Filtre*

Parameteren  _Filters_ angiver søgekriterierne for sikkerhedsfilteret for overholdelse. Du kan oprette tre forskellige typer filtre:

- **Filtrering af postkasser og OneDrive:** Denne type filter angiver, hvilke postkasser og OneDrive konti de tildelte brugere (angivet af parameteren _Brugere_) kan søge efter. Syntaksen for denne type filter er **Mailbox_** _MailboxPropertyName_, hvor  _MailboxPropertyName_ angiver en postkasseegenskab, der bruges til at omfatte de postkasser, der kan søges i. Postkassefilteret  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` giver f.eks. brugeren, der er tildelt dette filter, tilladelse til kun at søge i de postkasser, der har værdien "OttawaUsers" i egenskaben CustomAttribute10.  Alle understøttede modtageregenskaber, der kan filtreres, kan bruges til egenskaben  _MailboxPropertyName_ . Du kan se en liste over understøttede egenskaber under [Egenskaber, der kan filtreres for parameteren -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **Filtrering af postkasseindhold:** Denne type filter anvendes på det indhold, der kan søges i. Den angiver det postkasseindhold, som de tildelte brugere kan søge efter. Syntaksen for denne type filter er **MailboxContent_**_SearchablePropertyName_, hvor  _SearchablePropertyName_ angiver en KQL-egenskab (Keyword Query Language), som kan angives i en søgning. Indholdsfilteret `"MailboxContent_Recipients  -like 'contoso.com'"` for postkassen gør det f.eks. muligt for brugeren at tildele dette filter til kun at søge efter meddelelser, der er sendt til modtagere i det contoso.com domæne.  Du kan finde en liste over søgbare mailegenskaber under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

- **Filtrering af websteds- og webstedsindhold:** Der er to SharePoint og OneDrive for Business webstedsrelaterede filtre, som du kan bruge til at angive, hvilket websted eller webstedsindhold de tildelte brugere kan søge efter:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Disse to filtre er udskiftelige. Og returnerer f.eks  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"`  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` . de samme resultater. Du kan finde en liste over søgbare webstedsegenskaber [under Oversigt over gennemsøgte og administrerede egenskaber i SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Egenskaber, der er markeret med **Ja** i kolonnen **Kan forespørges** , kan bruges til at oprette et websteds- eller webstedsindholdsfilter.

### <a name="examples-of-changing-search-permissions-filters"></a>Eksempler på ændring af filtre for søgetilladelser

Disse eksempler viser, hvordan du bruger cmdlet'erne **Get-ComplianceSecurityFilter** og **Set-ComplianceSecurityFilter** til at tilføje eller fjerne en bruger til den eksisterende liste over brugere, som filteret er tildelt. Når du tilføjer eller fjerner brugere fra et filter, skal du angive brugeren ved hjælp af deres SMTP-adresse.
  
I dette eksempel føjes en bruger til filteret.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

I dette eksempel fjernes en bruger fra filteret.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>Remove-ComplianceSecurityFilter

**Remove-ComplianceSecurityFilter** bruges til at slette et søgefilter. Brug parameteren  _FilterName_ til at angive det filter, du vil slette.
  
## <a name="more-information"></a>Flere oplysninger

- **Hvordan fungerer filtrering af søgetilladelser?** Tilladelsesfilteret føjes til søgeforespørgslen, når der køres en søgning. Tilladelsesfilteret er joinforbundet til søgeforespørgslen af den booleske **OPERATOR AND** . Forespørgselslogikken for søgeforespørgslen og tilladelsesfilteret vil se sådan ud:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Du har f.eks. et tilladelsesfilter, der gør det muligt for Bob at udføre alle søgehandlinger på postkasserne for medlemmer af distributionsgruppen Arbejdere. Derefter kører Bob en søgning på alle postkasser i organisationen med søgeforespørgslen  `sender:jerry@adatum.com`. Da tilladelsesfilteret og søgeforespørgslen logisk kombineres af en **AND-operator** , returnerer søgningen alle meddelelser, der sendes af jerry@adatum.com til et medlem af arbejderdistributionsgruppen. 

- **Hvad sker der, hvis du har flere søgetilladelsesfiltre?** I en søgeforespørgsel kombineres flere tilladelsesfiltre af **BOOleske** operatorer. Resultaterne returneres derfor, hvis nogle af filtrene er sande. I en søgning kombineres alle filtre (kombineret af **OR-operatorer** ) derefter med søgeforespørgslen af operatoren **AND** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Lad os tage det forrige eksempel, hvor et søgefilter gør det muligt for Bob kun at søge i postkasserne for medlemmerne af distributionsgruppen Arbejdere. Derefter opretter vi et andet filter, der forhindrer Bob i at søge i Phils postkasse ("Mailbox_Alias -ne "Phil"). Og lad os også antage, at Phil er medlem af arbejdergruppen. Når Bob kører en søgning (fra det forrige eksempel) på alle postkasser i organisationen, returneres der søgeresultater for Phils postkasse, selvom du har anvendt filteret for at forhindre Bob i at søge i Phils postkasse. Det skyldes, at det første filter, som giver Bob mulighed for at søge i gruppen Arbejdere, er sandt. Og da Phil er medlem af gruppen Arbejdere, kan Bob søge i Phils postkasse.

- **Fungerer filtrering af søgetilladelser for inaktive postkasser?** Ja, du kan bruge indholdsfiltre for postkasser og postkasser til at begrænse, hvem der kan søge i inaktive postkasser i din organisation. På samme måde som en almindelig postkasse skal en inaktiv postkasse konfigureres med den modtageregenskab, der bruges til at oprette et tilladelsesfilter. Hvis det er nødvendigt, kan du bruge kommandoen **Get-Mailbox -InactiveMailboxOnly** til at få vist egenskaberne for inaktive postkasser. Du kan få flere oplysninger under [Opret og administrer inaktive postkasser](create-and-manage-inactive-mailboxes.md).
  
- **Fungerer filtrering af søgetilladelser for offentlige mapper?** Nej. Som tidligere forklaret kan filtrering af søgetilladelser ikke bruges til at begrænse, hvem der kan søge i offentlige mapper i Exchange. Elementer på placeringer med offentlige mapper kan f.eks. ikke udelades fra søgeresultaterne af et tilladelsesfilter.

- **Forhindrer det også, at en bruger kan søge på alle indholdsplaceringer i en bestemt tjeneste, i at søge efter indholdsplaceringer i en anden tjeneste?** Nej. Som tidligere forklaret skal du oprette et filter for søgetilladelser for udtrykkeligt at forhindre brugerne i at søge i indholdsplaceringer i en bestemt tjeneste (f.eks. forhindre en bruger i at søge i en Exchange postkasse eller et SharePoint websted). Det vil sige, at oprettelse af et filter for søgetilladelser, der giver en bruger mulighed for at søge på alle SharePoint websteder i organisationen, ikke forhindrer brugeren i at søge i postkasser. Hvis du f.eks. vil tillade, at SharePoint administratorer kun søger SharePoint websteder, skal du oprette et filter, der forhindrer dem i at søge i postkasser. På samme måde skal du oprette et filter, der forhindrer Exchange administratorer i kun at søge i postkasser, så de ikke kan søge på websteder.

- **Tæller filtre for søgetilladelser i forhold til tegngrænser for søgeforespørgsler?** Ja. Filtre for søgetilladelser tæller i forhold til tegngrænsen for søgeforespørgsler. Du kan finde flere oplysninger [under Grænser i eDiscovery (Premium)](limits-ediscovery20.md).

**Hvad er det maksimale antal filtre for søgetilladelser, der kan oprettes i en organisation?**
  
Der er ingen grænse for antallet af filtre for søgetilladelser, der kan oprettes i en organisation. En søgeforespørgsel kan dog højst have 100 betingelser. I dette tilfælde defineres en betingelse som noget, der er forbundet til forespørgslen af en boolesk operator (f.eks **. AND**, **OR** og **NEAR**). Grænsen for antallet af betingelser omfatter selve søgeforespørgslen plus alle filtre for søgetilladelser, der anvendes på den bruger, der kører søgningen. Jo flere søgetilladelser du har (især hvis disse filtre anvendes på den samme bruger eller gruppe af brugere), jo større er chancen for at overskride det maksimale antal betingelser for en søgning.

Hvis du vil vide, hvordan denne grænse fungerer, skal du forstå, at søgetilladelsesfilteret føjes til søgeforespørgslen, når der køres en søgning. Et filter for søgetilladelser er joinforbundet til søgeforespørgslen af operatoren **AND** boolesk. Forespørgselslogikken for søgeforespørgslen og et enkelt filter for søgetilladelser vil se sådan ud:

```text
<SearchQuery> AND <PermissionsFilter>
```

Flere filtre for søgetilladelser kombineres af den booleske **OPERATOR OR** , og derefter forbindes disse betingelser med søgeforespørgslen af operatoren **AND** .

Forespørgselslogikken for søgeforespørgslen og flere filtre for søgetilladelser vil se sådan ud:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Det er muligt, at selve søgeforespørgslen består af flere betingelser, der er forbundet af booleske operatorer. Hver betingelse i søgeforespørgslen tæller også med i forhold til grænsen på 100 betingelser.

Antallet af filtre for søgetilladelser, der føjes til en forespørgsel, afhænger også af den bruger, der kører søgningen. Når en bestemt bruger kører en søgning, føjes de søgetilladelser, der er anvendt på brugeren (som er defineret af parameteren *Users* i filteret), til forespørgslen. Din organisation kan have hundredvis af søgetilladelsesfiltre, men hvis der anvendes mere end 100 filtre på de samme brugere, er det sandsynligt, at grænsen på 100 betingelser overskrides, når disse brugere kører søgninger.

Der er én ting mere, du skal være opmærksom på angående betingelsesgrænsen. Antallet af specifikke SharePoint websteder, der er inkluderet i søgeforespørgslen eller filtrene for søgetilladelser, tæller også i forhold til denne grænse. 

Hvis du vil forhindre din organisation i at nå betingelsesgrænsen, skal du holde antallet af søgetilladelsersfiltre i din organisation så få som muligt, så de opfylder dine forretningskrav.