---
title: Konfigurere filtrering af tilladelser for eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Brug filtrering af søgetilladelser for at lade eDiscovery-ledere søge i kun et undersæt af postkasser og websteder i organisationen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6310334bdbfd1a94456d5e826daebb9f2945af14
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63588945"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>Konfigurere filtrering af tilladelser for eDiscovery

Du kan bruge filtrering af søgetilladelser til at lade en eDiscovery-leder søge i kun et undersæt af postkasser og websteder i organisationen. Du kan også bruge tilladelsesfiltrering til at lade den samme eDiscovery-leder søge kun efter postkasse- eller webstedsindhold, der opfylder et bestemt søgekriterie. Du kan f.eks. lade en eDiscovery-leder søge i postkasser for brugere på et bestemt sted eller i en bestemt afdeling. Det gør du ved at oprette et filter, der bruger et understøttet modtagerfilter til at begrænse, hvilke postkasser en bestemt bruger eller gruppe af brugere kan søge i. Du kan også oprette et filter, der angiver, hvilket postkasseindhold en bruger kan søge efter. Dette gøres ved at oprette et filter, der bruger en søgbar meddelelsesegenskab. På samme måde kan du lade en eDiscovery-leder søge kun på bestemte SharePoint websteder i organisationen. Det gør du ved at oprette et filter, der begrænser, hvilket websted der kan søges i. Du kan også oprette et filter, der angiver, hvilket webstedsindhold der kan søges i. Dette gøres ved at oprette et filter, der bruger en søgbar webstedsegenskab.

Søgetilladelsesfiltre anvendes, når du søger efter indhold ved hjælp af indholdssøgning, grundlæggende eDiscovery og Advanced eDiscovery i Microsoft 365 Overholdelsescenter. Når et filter for søgetilladelser anvendes på en bestemt bruger, kan den pågældende bruger udføre følgende søgerelaterede handlinger:

- Søge efter indhold

- Få vist søgeresultater

- Eksportér søgeresultater

- Fjerne elementer, der returneres af en søgning

Du kan også bruge filtrering af søgetilladelser til at oprette logiske grænser (kaldet overholdelsesgrænser *) i* en organisation, der styrer brugernes indholdsplaceringer (f.eks. postkasser, SharePoint-websteder og OneDrive-konti), som bestemte eDiscovery-ledere kan søge efter. Få mere at vide under [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md).
  
Følgende fire cmdlet'er i Security & Compliance PowerShell giver dig mulighed for at konfigurere og administrere filtre for søgetilladelser:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Krav til konfiguration af filtrering af tilladelser

- For at køre cmdlet'er med overholdelsessikkerhedsfilteret skal du være medlem af rollegruppen organisationsadministration i Microsoft 365 Overholdelsescenter. Du kan finde flere [oplysninger i Tilladelser i sikkerheds- & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Du skal oprette forbindelse til både Exchange Online og Security & Compliance Center PowerShell for at bruge cmdlet'er med filteret til overholdelse af regler og standarder. Dette er nødvendigt, fordi disse cmdlet'er kræver adgang til postkasseegenskaber, hvilket er grunden til, at du skal oprette forbindelse Exchange Online PowerShell. Se trinnene i næste afsnit.

- Se afsnittet [Flere oplysninger](#more-information) , hvis du vil have mere at vide om filtre for søgetilladelser.

- Filtrering af søgetilladelser gælder for inaktive postkasser, hvilket betyder, at du kan bruge filtrering af postkasse- og postkasseindhold for at begrænse, hvem der kan søge i en inaktiv postkasse. Se afsnittet [Flere oplysninger](#more-information) , hvis du vil have mere at vide om tilladelsesfiltrering og inaktive postkasser.

- Filtrering af søgetilladelser kan ikke bruges til at begrænse, hvem der kan søge i offentlige mapper i Exchange.

- Der er ingen begrænsninger for antallet af søgetilladelsesfiltre, der kan oprettes i en organisation. En søgeforespørgsel kan dog maksimalt have 100 betingelser. I dette tilfælde defineres en betingelse som noget, der er forbundet til forespørgslen af en boolesk operator (f.eks. **OG**, **ELLER** og **NEAR**). Grænsen for antallet af betingelser omfatter selve søgeforespørgslen plus alle filtre til søgetilladelser, der anvendes til den bruger, der kører søgningen. Derfor gælder det, at jo flere filtre for søgetilladelser du har (især hvis disse filtre anvendes for den samme bruger eller gruppe af brugere), jo bedre mulighed for at overskride det maksimale antal betingelser for en søgning. Hvis du vil forhindre din organisation i at nå begrænsningen på betingelser, skal du holde antallet af søgetilladelsesfiltre i din organisation på få så få som muligt, så det opfylder virksomhedens krav. Få mere at vide under [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Forbind til Exchange Online og Security & Compliance Center PowerShell i en enkelt session

Før du kan køre scriptet uden problemer i dette afsnit, skal du downloade og installere Exchange Online PowerShell V2-modulet. Du kan finde flere [oplysninger under Om Exchange Online PowerShell V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Gem følgende tekst i en Windows PowerShell scriptfil ved hjælp af et filnavnsuffiks **af.ps1**. Du kan f.eks. gemme den i en fil med **navnetConnectEXO-SCC.ps1**.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. På din lokale computer skal du åbne Windows PowerShell, gå til den mappe, hvor scriptet, du oprettede i forrige trin, er placeret, og derefter køre scriptet, f.eks.:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Hvordan ved du, om det virkede? Når du har kørt scriptet, importeres cmdlet'er fra Exchange Online og Security & Compliance PowerShell til din lokale Windows PowerShell session. Hvis du ikke modtager nogen fejl, har du oprettet forbindelse. En hurtig test er at køre Exchange Online- & Compliance Center PowerShell-cmdletter. Du kan f.eks. køre **Get-Mailbox** og **Get-ComplianceSearch**.

Hvis du vil foretage fejlfinding af powerShell-forbindelsesfejl, skal du se:

- [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

**New-ComplianceSecurityFilter bruges** til at oprette et søgetilladelsesfilter. Her er den grundlæggende syntaks for denne cmdlet:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

I de følgende afsnit beskrives parametrene for denne cmdlet. Alle parametre er påkrævede for at oprette et søgetilladelsesfilter.

### <a name="filtername"></a>*FilterNavn*

_FilterName-parameteren_ angiver navnet på tilladelsesfilteret. Dette navn bruges til at identiteten af et filter, når du bruger cmdlet'erne **Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** og **Remove-ComplianceSecurityFilter** .

### <a name="filters"></a>*Filtre*

_Filterparameteren_ angiver søgekriterierne for filteret til overholdelse af regler og standarder. Du kan oprette tre forskellige typer filtre:  

- **Postkasse- eller OneDrive** filtrering: Denne type filter angiver postkasser og OneDrive-konti, som de tildelte brugere (angivet _af parameteren_ Brugere) kan søge i. Denne type filter kaldes et *indholdsplaceringsfilter* , fordi den definerer de indholdsplaceringer, som en bruger kan søge efter. Syntaksen for denne type filter er **Mailbox_** _MailboxPropertyName_, hvor _MailboxPropertyName_ angiver en postkasseegenskab, der bruges til at angive omfanget af postkasser og OneDrive konti, der kan søges i. For eksempel ville postkassefilteret give brugeren tildelt dette filter mulighed for kun at søge i de postkasser og OneDrive-konti, `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` der har værdien "OttawaUsers" i egenskaben CustomAttribute10.

  Alle understøttede filtrerbare modtageregenskab kan bruges til _egenskaben MailboxPropertyName_ i en postkasse eller OneDrive filter. Følgende tabel indeholder fire ofte anvendte modtageregenskaber, der bruges til at oprette en postkasse eller et OneDrive filter. Tabellen indeholder også et eksempel på brug af egenskaben i et filter.

  |Egenskabsnavn  |Eksempel  |
  |---------|---------|
  |Alias    |`"Mailbox_Alias -like 'v-'"`         |
  |Firma  |`"Mailbox_Company -eq 'Contoso'"`        |
  |LandEllerOmråde |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Afdeling |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Filtrering af postkasseindhold:** Denne type filter anvendes på det indhold, der kan søges i. Denne type filter kaldes et *indholdsfilter* , fordi det angiver postkassens indhold eller søgbare mailegenskaber, som de tildelte brugere kan søge efter. Syntaksen for denne type filter er **MailboxContent_** _SearchablePropertyName, hvor  _SearchablePropertyName_ angiver en KQL-egenskab (Keyword Query Language), der kan angives i en søgning. Eksempelvis ville filtreringen af postkasseindhold `"MailboxContent_Recipients  -like 'contoso.com'"` give den bruger, der har fået tildelt dette filter, mulighed for kun at søge efter meddelelser, der er sendt til modtagere contoso.com domænet. Du kan finde en liste over søgbare mailegenskaber [under Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Et enkelt søgefilter kan ikke indeholde et postkassefilter og et postkasseindholdsfilter. Hvis du vil kombinere disse i et enkelt filter, skal du bruge en [filterliste](#using-a-filters-list-to-combine-filter-types).  Men et filter kan indeholde en mere kompleks forespørgsel af samme type. For eksempel `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Filtrering af websteds- og webstedsindhold:** Der er to SharePoint- og OneDrive relaterede filtre, du kan bruge til at angive, hvilket websteds- eller webstedsindhold de tildelte brugere kan søge efter.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Disse to filtre kan udskiftes. F.eks. `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` og  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` returnere de samme resultater. Du kan finde en liste over søgbare egenskaber på webstedet under Nøgleordsforespørgsler og søgebetingelser [for eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties) Få en mere komplet liste under Oversigt over gennemsøgte og administrerede egenskaber [i SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Egenskaber, der er markeret **med et** Ja i kolonnen **Forespørgselsbare** , kan bruges til at oprette et websteds- eller webstedsindholdsfilter.  

  > [!IMPORTANT]
  > Konfiguration af et webstedsfilter med en af de understøttede egenskaber betyder ikke, at webstedsegenskaben i filteret overføres til alle dokumenter på webstedet. Det betyder, at brugeren stadig er ansvarlig for at udfylde de specifikke egenskabsfelter, der er knyttet til dokumenterne på webstedet, for at webstedsfilteret kan fungere og hente det rigtige indhold. Hvis brugeren f.eks. har et sikkerhedsfilter, anvendes "Site_RefineableString00 -eq 'abc'", og derefter kører brugeren en søgning ved hjælp af nøgleordsforespørgslen "xyz". Sikkerhedsfilteret føjes til forespørgslen, og den faktiske forespørgsel, der kører, er "xyz **OG RefineableString0:'abc'**". Brugeren skal sikre, at dokumenter på webstedet rent faktisk har værdier i feltet RefineableString00 som"abc". Hvis ikke, returnerer søgeforespørgslen ikke nogen resultater.

Husk følgende, når du konfigurerer *filterparameteren* for søgetilladelser:

- I modsætning til postkasser er der ikke et filter for indholdsplacering for websteder, selvom filteret *Websted ligner* et placeringsfilter. Alle filtre til SharePoint og OneDrive er indholdsfiltre (hvilket også er grunden til, *at Site_*- og *SiteContent_*-filtre kan udskiftes), fordi webstedsrelaterede egenskaber som f.eks. Sti  stemples direkte på dokumenterne. Hvorfor er dette? Det er resultatet af den måde, som SharePoint er designet på. I SharePoint er der ikke et "webstedsobjekt" med egenskaber, som der er med Exchange postkasser. Derfor er *egenskaben Sti* stemplet på dokumentet og indeholder URL-adressen på det websted, hvor dokumentet er placeret. Dette er grunden til, *at et* webstedsfilter betragtes som et indholdsfilter og ikke et filter for indholdsplacering.

- Du skal oprette et søgetilladelsesfilter for udtrykkeligt at forhindre brugere i at søge efter indholdsplaceringer i en bestemt tjeneste (f.eks. forhindre en bruger i at søge i en Exchange-postkasse eller et SharePoint websted). Med andre ord forhindrer oprettelse af et filter for søgetilladelser, der giver en bruger mulighed for at søge på alle SharePoint-websteder i organisationen, ikke, at brugeren kan søge i postkasser. Hvis du f.eks. SharePoint give administratorer tilladelse til kun at søge SharePoint websteder, skal du oprette et filter, der forhindrer dem i at søge i postkasser. På samme måde kan Exchange administratorer kun søge i postkasser, skal du oprette et filter, der forhindrer dem i at søge på websteder.

### <a name="users"></a>*Brugere*

_Parameteren_ Brugere angiver de brugere, der får dette filter anvendt på deres søgninger. Identificer brugere efter deres alias eller primære SMTP-adresse. Du kan angive flere værdier adskilt af kommaer, eller du kan tildele filteret til alle brugere ved hjælp af værdien **Alle**.

Du kan også bruge _parameteren Brugere_ til at angive en Microsoft 365 Overholdelsescenter rollegruppe. Dette giver dig mulighed for at oprette en brugerdefineret rollegruppe og derefter tildele den pågældende rollegruppe et søgetilladelsesfilter. Lad os f.eks. sige, at du har en brugerdefineret rollegruppe til eDiscovery-ledere for det amerikanske datterselskab til en multi national virksomhed. Du kan  _bruge parameteren_ Users til at angive denne rollegruppe (ved hjælp af egenskaben Navn for rollegruppen) og derefter bruge  _filterparameteren_ til kun at tillade, at der søges i postkasser i USA. Du kan ikke angive distributionsgrupper med denne parameter.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Brug af en filterliste til at kombinere filtertyper

En *filterliste er* et filter, der indeholder et postkassefilter, og et webstedsfilter adskilt af et komma. Dette komma fungerer også som en **ELLER-operator** . Brug af en filterliste er den eneste understøttede metode til at kombinere forskellige typer filtre. I følgende eksempel skal du bemærke, at et komma adskiller **filtrene Postkasse** **og** Websted:

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Når et filter, der indeholder en filterliste, behandles under kørsel af en søgning, oprettes der to filtre for søgetilladelser på listen over filtre: Et for hvert filter, der er adskilt af et komma. Så i det forrige eksempel blev der oprettet ét filter for postkassesøgetilladelser og ét filter til webstedssøgningstilladelser. Disse filtre forbindes af **operatoren ELLER** .

Et alternativ til at bruge en filterliste ville være at oprette to separate søgetilladelsesfiltre. Så i det forrige eksempel ville du oprette ét filter til postkasseattributten og ét filter til webstedsattributten. I begge tilfælde er resultaterne de samme. Det er en god ide at bruge en liste over filtre eller oprette separate søgetilladelsesfiltre.

Vær opmærksom på følgende, når du bruger en filterliste:

- Du skal bruge en filterliste til at oprette et filter, der indeholder et **postkassefilter** og et **MailboxContent-filter** .

- Hver komponent i en filterliste kan indeholde en kompleks filtersyntaksen. For eksempel kan postkasse- og webstedsfiltre indeholde flere filtre adskilt af en **-eller-operator** :

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Eksempler på oprettelse af filtre for søgetilladelser

Her er eksempler på brug af **New-ComplianceSecurityFilter-cmdlet'en** til at oprette et søgetilladelsesfilter.

I dette eksempel kan medlemmer af rollegruppen "US Discovery Managers" kun søge i postkasser OneDrive konti i USA.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
I dette eksempel kan annb@contoso.com udføre søgehandlinger for postkasser og OneDrive konti i Canada. Dette filter indeholder den trecifrede landekode for Canada fra ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

Dette eksempel giver brugerne mulighed for kun at søge i postkasser og OneDrive-konti, der har værdien "Marketing" for postkasseegenskaben CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

I dette eksempel kan medlemmer af rollegruppen "Fourth Coffee eDiscovery Managers" kun søge i postkasser og OneDrive-konti, der har værdien "FourthCoffee" for egenskaben afdelingspostkasse. Filteret giver også rollegruppens medlemmer mulighed for at søge efter dokumenter på webstedet Fourth Coffee SharePoint webstedet.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> I det forrige eksempel skal der medtages et ekstra webstedsindholdsfilter (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`), så rollegruppemedlemmer kan søge efter dokumenter OneDrive konti. Hvis dette filter ikke er inkluderet, tillader filteret kun rollegruppemedlemmer at søge efter dokumenter, der er placeret i `https://contoso.sharepoint.com/sites/FourthCoffee`.

I dette eksempel kan medlemmer af rollegruppen eDiscovery Manager kun søge i postkasser og OneDrive-konti for medlemmer af distributionsgruppen Ottawa-brugere. Cmdlet Get-DistributionGroup i Exchange Online PowerShell bruges til at finde medlemmer af gruppen Ottawa-brugere.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

I dette eksempel forhindres brugere i at udføre søgehandlinger i postkasser og OneDrive konti for medlemmer af distributionsgruppen lederteamet. Det betyder, at brugerne kan slette indhold fra disse postkasser. Cmdlet Get-DistributionGroup i Exchange Online PowerShell bruges til at finde medlemmerne af ledelsesteamets gruppe.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

I dette eksempel kan medlemmer af den brugerdefinerede rollegruppe OneDrive eDiscovery-ledere kun søge efter indhold OneDrive konti i organisationen.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
I dette eksempel begrænses brugeren til kun at udføre søgehandlinger på mails, der er sendt i løbet af kalenderåret 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Som i det forrige eksempel begrænser dette eksempel kun brugeren til at udføre søgehandlinger på dokumenter, der senest er blevet ændret i kalenderåret 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

I dette eksempel forhindres medlemmer af rollegruppen "OneDrive Discovery Managers" i at udføre søgehandlinger på alle postkasser i organisationen.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

I dette eksempel forhindres alle i organisationen i at udføre søgehandlinger på mails, der er blevet sendt eller modtaget af janets eller sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

I dette eksempel bruges en filterliste til at kombinere postkasse- og webstedsfiltre. I dette eksempel er postkassefilteret et indholdsplaceringsfilter, og webstedsfilteret er et indholdsfilter.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter bruges** til at returnere en liste over søgetilladelsesfiltre. Brug  _FilterName-parameteren_ til at returnere oplysninger om et bestemt søgefilter.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter bruges** til at ændre et eksisterende søgetilladelsesfilter. I de følgende afsnit beskrives parametrene for denne cmdlet. Den eneste påkrævede parameter er  _FilterName_.
  
### <a name="filtername"></a>*FilterNavn*

_FilterName-parameteren_ angiver navnet på tilladelsesfilteret.

### <a name="users"></a>*Brugere*

_Parameteren_ Brugere angiver de brugere, der får dette filter anvendt på deres søgninger. Da dette er en egenskab med flere værdier, der angiver en bruger eller gruppe af brugere med denne parameter, overskrives den eksisterende liste over brugere. Se følgende eksempler for syntaksen til at tilføje og fjerne udvalgte brugere.

Du kan også bruge _parameteren Brugere_ til at angive en Microsoft 365 Overholdelsescenter rollegruppe. Dette giver dig mulighed for at oprette en brugerdefineret rollegruppe og derefter tildele den pågældende rollegruppe et søgetilladelsesfilter. Lad os f.eks. sige, at du har en brugerdefineret rollegruppe til eDiscovery-ledere for det amerikanske datterselskab til en multi national virksomhed. Du kan  _bruge parameteren_ Users til at angive denne rollegruppe (ved hjælp af egenskaben Navn for rollegruppen) og derefter bruge  _filterparameteren_ til kun at tillade, at der søges i postkasser i USA. Du kan ikke angive distributionsgrupper med denne parameter.

### <a name="filters"></a>*Filtre*

_Filterparameteren_ angiver søgekriterierne for filteret til overholdelse af regler og standarder. Du kan oprette tre forskellige typer filtre:

- **Postkasse- OneDrive-filtrering:** Denne type filter angiver postkasser og OneDrive-konti, som de tildelte brugere (angivet af parameteren _Brugere)_ kan søge i. Syntaksen for denne type filter er **Mailbox_** _MailboxPropertyName_, hvor  _MailboxPropertyName_ angiver en postkasseegenskab, der bruges til at begrænse de postkasser, der kan søges i. For eksempel ville postkassefilteret give brugeren tildelt dette filter mulighed for kun at søge i de postkasser,  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` der har værdien "OttawaUsers" i egenskaben CustomAttribute10.  Alle understøttede filtrerbare modtageregenskab kan bruges til  _egenskaben MailboxPropertyName_ . Du kan finde en liste over understøttede egenskaber [under Filtrerbare egenskaber for parameteren -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **Filtrering af postkasseindhold:** Denne type filter anvendes på det indhold, der kan søges i. Den angiver det postkasseindhold, de tildelte brugere kan søge efter. Syntaksen for denne type filter er **MailboxContent_**_SearchablePropertyName_, hvor  _SearchablePropertyName_ angiver en KQL-egenskab (Keyword Query Language), der kan angives i en søgning. Eksempelvis ville filtreringen af postkasseindhold `"MailboxContent_Recipients  -like 'contoso.com'"` give den bruger, der har fået tildelt dette filter, mulighed for kun at søge efter meddelelser, der er sendt til modtagere contoso.com domænet.  Du kan finde en liste over søgbare mailegenskaber [under Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

- **Filtrering af websteds- og webstedsindhold:** Der er to SharePoint og OneDrive for Business webstedsrelaterede filtre, som du kan bruge til at angive, hvilket websteds- eller webstedsindhold de tildelte brugere kan søge efter:

  - **Site_** *SøgbareSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Disse to filtre kan udskiftes. F.eks.  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` og  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` returnere de samme resultater. Du kan finde en liste over søgbare egenskaber for webstedet [i Oversigt over gennemsøgte og administrerede egenskaber SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Egenskaber, der er markeret **med et** Ja i kolonnen **Forespørgselsbare** , kan bruges til at oprette et websteds- eller webstedsindholdsfilter.

### <a name="examples-of-changing-search-permissions-filters"></a>Eksempler på ændring af filtre for søgetilladelser

Disse eksempler viser, hvordan du bruger **Get-ComplianceSecurityFilter** - og **Set-ComplianceSecurityFilter-cmdlet'er** til at tilføje eller fjerne en bruger til den eksisterende liste over brugere, som filteret er tildelt til. Når du tilføjer eller fjerner brugere fra et filter, skal du angive brugeren ved hjælp af deres SMTP-adresse.
  
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

**Remove-ComplianceSecurityFilter bruges** til at slette et søgefilter. Brug  _FilterName-parameteren_ til at angive det filter, du vil slette.
  
## <a name="more-information"></a>Flere oplysninger

- **Hvordan fungerer filtrering af søgetilladelser?** Tilladelsesfilteret føjes til søgeforespørgslen, når der køres en søgning. Tilladelsesfilteret er forbundet til søgeforespørgslen af **AND** Boolean-operatoren. Forespørgselslogik for søgeforespørgslen og tilladelsesfilteret ville se sådan ud:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Du har f.eks. et tilladelsesfilter, der giver Bob mulighed for at udføre alle søgehandlinger på postkasser for medlemmer af distributionsgruppen Medarbejdere. Derefter kører Bob en søgning på alle postkasser i organisationen med søgeforespørgslen  `sender:jerry@adatum.com`. Da tilladelsesfilteret og søgeforespørgslen kombineres logisk af en **AND-operator** , returnerer søgningen alle meddelelser, der sendes af jerry@adatum.com til et medlem af distributionsgruppen Medarbejdere. 

- **Hvad sker der, hvis du har flere filtre for søgetilladelser?** I en søgeforespørgsel kombineres flere tilladelsesfiltre af  OR-booleske operatorer. Derfor returneres resultaterne, hvis nogle af filtrene er sande. I en søgning kombineres alle filtre (kombineret **af OR-operatorer** ) derefter med søgeforespørgslen af **OG-operatoren** .

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Lad os tage det forrige eksempel, hvor et søgefilter giver Bob mulighed for kun at søge i postkasser for medlemmer af distributionsgruppen Medarbejdere. Derefter opretter vi et andet filter, der forhindrer Bob i at søge i Phil's postkasse ("Mailbox_Alias -ne 'Phil'"). Og lad os også antage, at Phil er medlem af gruppen Medarbejdere. Når Bob kører en søgning (fra det forrige eksempel) på alle postkasser i organisationen, returneres søgeresultaterne for Phils postkasse, selvom du har anvendt filter for at forhindre Bob i at søge i Phils postkasse. Dette skyldes, at det første filter, der giver Bob mulighed for at søge i gruppen Medarbejdere, er sandt. Og fordi Phil er medlem af gruppen Medarbejdere, kan Bob søge i Phils postkasse.

- **Virker filtrering af søgetilladelser for inaktive postkasser?** Ja, du kan bruge indholdsfiltre for postkasser og postkasser til at begrænse, hvem der kan søge i inaktive postkasser i organisationen. Ligesom en almindelig postkasse skal en inaktiv postkasse konfigureres med den modtageregenskab, der bruges til at oprette et tilladelsesfilter. Hvis det er nødvendigt, kan du bruge **kommandoen Get-Mailbox -InactiveMailboxOnly** til at få vist egenskaberne for inaktive postkasser. Du kan få mere at vide under [Oprette og administrere inaktive postkasser](create-and-manage-inactive-mailboxes.md).
  
- **Virker filtrering af søgetilladelser for offentlige mapper?** Nej. Som tidligere beskrevet kan filtrering af søgetilladelser ikke bruges til at begrænse, hvem der kan søge i offentlige mapper Exchange. Elementer på offentlige mappeplaceringer kan f.eks. ikke udelades fra søgeresultaterne ved hjælp af et tilladelsesfilter.

- **Forhindrer det også en bruger at søge i alle indholdsplaceringer i en bestemt tjeneste, i at søge efter indholdsplaceringer i en anden tjeneste?** Nej. Som beskrevet tidligere skal du oprette et filter med søgetilladelser for udtrykkeligt at forhindre brugere i at søge efter indholdsplaceringer i en bestemt tjeneste (f.eks. forhindre en bruger i at søge i en Exchange-postkasse eller et SharePoint-websted). Med andre ord forhindrer oprettelse af et filter for søgetilladelser, der giver en bruger mulighed for at søge på alle SharePoint-websteder i organisationen, ikke, at brugeren kan søge i postkasser. Hvis du f.eks. SharePoint give administratorer tilladelse til kun at søge SharePoint websteder, skal du oprette et filter, der forhindrer dem i at søge i postkasser. På samme måde kan Exchange administratorer kun søge i postkasser, skal du oprette et filter, der forhindrer dem i at søge på websteder.

- **Tæller søgetilladelser med i tegnbegrænsninger for søgning?** Ja. Søgetilladelsers filtre tæller med i tegngrænsen for søgeforespørgsler. Du kan finde flere oplysninger [under Begrænsninger i Advanced eDiscovery](limits-ediscovery20.md).

**Hvad er det maksimale antal søgetilladelsesfiltre, der kan oprettes i en organisation?**
  
Der er ingen begrænsninger for antallet af søgetilladelsesfiltre, der kan oprettes i en organisation. En søgeforespørgsel kan dog maksimalt have 100 betingelser. I dette tilfælde defineres en betingelse som noget, der er forbundet til forespørgslen af en boolesk operator (f.eks. **OG**, **ELLER** og **NEAR**). Grænsen for antallet af betingelser omfatter selve søgeforespørgslen plus alle filtre for søgetilladelser, der anvendes til den bruger, der kører søgningen. Derfor gælder det, at jo flere filtre for søgetilladelser du har (især hvis disse filtre anvendes for den samme bruger eller gruppe af brugere), jo bedre mulighed for at overskride det maksimale antal betingelser for en søgning.

For at forstå, hvordan denne grænse fungerer, skal du forstå, at et søgetilladelsesfilter føjes til søgeforespørgslen, når der køres en søgning. En søgetilladelsesfilter er forbundet til søgeforespørgslen **af AND** boolesk operator. Forespørgselslogik for søgeforespørgslen og et enkelt søgetilladelsesfilter ville se sådan ud:

```text
<SearchQuery> AND <PermissionsFilter>
```

Filtre for flere søgetilladelser kombineres af OPERATOREN **OR** boolesk, og disse betingelser forbindes derefter til søgeforespørgslen af **operatoren AND** .

Forespørgselslogik for søgeforespørgslen og filtre for flere søgetilladelser ville se sådan ud:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Det er muligt, at selve søgeforespørgslen kan bestå af flere betingelser, der er forbundet af booleske operatorer. Hver betingelse i søgeforespørgslen vil også tælle med i forhold til grænsen på 100 betingelser.

Antallet af søgetilladelser, der føjes til en forespørgsel, afhænger også af den bruger, der kører søgningen. Når en bestemt bruger kører en søgning, føjes søgetilladelsesfiltrene, der anvendes til brugeren (som er defineret *af parameteren* Brugere i filteret), til forespørgslen. Din organisation kan have hundredvis af søgetilladelsesfiltre, men hvis der anvendes flere end 100 filtre på de samme brugere, er det sandsynligt, at grænsen på 100 betingelser overskrides, når disse brugere kører søgninger.

Der er én ting mere at huske på vedrørende betingelsesgrænsen. Antallet af bestemte websteder SharePoint, der er inkluderet i filtrene for søgeforespørgsel eller søgetilladelser, tæller også med i denne grænse. 

Hvis du vil forhindre din organisation i at nå begrænsningen på betingelser, skal du holde antallet af søgetilladelsesfiltre i din organisation på få så få som muligt, så det opfylder virksomhedens krav.