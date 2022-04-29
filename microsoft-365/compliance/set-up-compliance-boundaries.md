---
title: Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser
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
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1b45c82f-26c8-44fb-9f3b-b45436fe2271
description: Få mere at vide om, hvordan du bruger overholdelsesgrænser til at oprette logiske grænser, der styrer placeringen af brugerindhold, som en eDiscovery-leder kan søge i Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 52f4a66ffbab37109e7503181548b1de4ffac87a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128777"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vejledningen i denne artikel kan anvendes, når du bruger enten Microsoft Purview eDiscovery (Standard) eller Microsoft Purview eDiscovery (Premium) til at administrere undersøgelser.

Overholdelsesgrænser opretter logiske grænser i en organisation, der styrer placeringen af brugerindhold (f.eks. postkasser, OneDrive konti og SharePoint websteder), som eDiscovery-ledere kan søge efter. Overholdelsesgrænser styrer også, hvem der kan få adgang til eDiscovery-sager, der bruges til at administrere de juridiske, menneskelige ressourcer eller andre undersøgelser i din organisation. Behovet for overholdelsesgrænser er ofte nødvendigt for multinationale selskaber, der skal respektere geografiske bestyrelser og regler og for regeringer, som ofte er opdelt i forskellige agenturer. I Microsoft 365 hjælper overholdelsesgrænser dig med at opfylde disse krav, når du udfører indholdssøgninger og administrerer undersøgelser med eDiscovery-sager.
  
Vi bruger eksemplet i følgende illustration til at forklare, hvordan overholdelsesgrænser fungerer.
  
![Overholdelsesgrænser består af søgetilladelsesfiltre, der styrer adgangen til agenturer og administratorrollegrupper, der styrer adgangen til eDiscovery-sager.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
I dette eksempel er Contoso LTD en organisation, der består af to datterselskaber, Fjerde Kaffe og Coho Winery. Virksomheden kræver, at eDiscovery-ledere og -efterforskere kun kan søge i de Exchange postkasser, OneDrive konti og SharePoint websteder i deres bureau. EDiscovery-ledere og -efterforskere kan også kun se eDiscovery-sager i deres agentur, og de kan kun få adgang til de sager, de er medlem af. I dette scenarie kan efterforskere heller ikke placere indholdsplaceringer i venteposition eller eksportere indhold fra en sag. Her kan du se, hvordan overholdelsesgrænser opfylder disse krav.
  
- Filtreringsfunktionen for søgetilladelser for eDiscovery styrer de indholdsplaceringer, som eDiscovery-ledere og -efterforskere kan søge efter. Det betyder, at eDiscovery-ledere og efterforskere i det fjerde kaffebureau kun kan søge efter indholdsplaceringer i datterselskabet Fjerde kaffe. Den samme begrænsning gælder for Coho Winery-datterselskabet.

- [Rollegrupper](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) indeholder følgende funktioner til overholdelse af regler og standarder:

  - Kontrollér, hvem der kan se eDiscovery-sager på Microsoft Purview-overholdelsesportalen. Det betyder, at eDiscovery-ledere og -efterforskere kun kan se eDiscovery-sager i deres agentur.

  - Kontrollér, hvem der kan tildele medlemmer til en eDiscovery-sag. Det betyder, at eDiscovery-ledere og efterforskere kun kan tildele medlemmer til sager, som de selv er medlem af.

  - Styr de eDiscovery-relaterede opgaver, som medlemmerne kan udføre, ved at tilføje eller fjerne roller, der tildeler bestemte tilladelser.

- Når der anvendes et filter for søgetilladelser på en rollegruppe, kan medlemmer af rollegruppen udføre følgende søgerelaterede handlinger, så længe tilladelserne til at udføre en handling tildeles til rollegruppen:

  - Søg efter indhold

  - Vis søgeresultater

  - Eksportér søgeresultater

  - Fjern elementer, der returneres af en søgning

Her er processen til konfiguration af overholdelsesgrænser:
  
[Trin 1: Identificer en brugerattribut for at definere dine agenturer](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Trin 2: Opret en rollegruppe for hvert agentur](#step-2-create-a-role-group-for-each-agency)

[Trin 3: Opret et filter for søgetilladelser for at gennemtvinge overholdelsesgrænsen](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Trin 4: Opret en eDiscovery-sag for en undersøgelse inden for bureauet](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Før du konfigurerer overholdelsesgrænser

- Brugerne skal tildeles en Exchange Online licens. Du kan bekræfte dette ved at bruge [cmdlet'en Get-User](/powershell/module/exchange/get-user) i Exchange Online PowerShell.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Trin 1: Identificer en brugerattribut for at definere dine agenturer

Det første trin er at vælge en attribut, der definerer dine agenturer. Denne attribut bruges til at oprette filteret for søgetilladelser, der begrænser en eDiscovery-administrator til kun at søge efter indholdsplaceringer for brugere, der har fået tildelt en bestemt værdi for denne attribut. Lad os f.eks. sige, at Contoso beslutter at bruge attributten **Afdeling** . Værdien for denne attribut for brugere i datterselskabet Fjerde kaffe vil være  `FourthCoffee`  , og værdien for brugerne i Coho Winery-datterselskabet vil være `CohoWinery`. I trin 3 skal du bruge dette  `attribute:value`  par (f.eks *. Afdeling:FourthCoffee*) til at begrænse de brugerindholdsplaceringer, som eDiscovery-ledere kan søge efter. 
  
Her er nogle eksempler på brugerattributter, som du kan bruge til overholdelse af angivne standarder:
  
- Virksomhed

- CustomAttribute1 – CustomAttribute15

- Institut

- Office

- CountryOrRegion (landekode på to bogstaver)

Du kan se en komplet liste på den komplette liste over understøttede [postkassefiltre](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties).

## <a name="step-2-create-a-role-group-for-each-agency"></a>Trin 2: Opret en rollegruppe for hvert agentur

Det næste trin er at oprette rollegrupperne på overholdelsesportalen, der passer til dine agenturer. Vi anbefaler, at du opretter en rollegruppe ved at kopiere den indbyggede gruppe eDiscovery-ledere, tilføje de relevante medlemmer og fjerne roller, der muligvis ikke passer til dine behov. Du kan finde flere oplysninger om eDiscovery-relaterede roller under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).
  
Hvis du vil oprette rollegrupperne, skal du gå til siden **Tilladelser på overholdelsesportalen** og oprette en rollegruppe for hvert team i hvert agentur, der skal bruge overholdelsesgrænser og eDiscovery-sager til at administrere undersøgelser.
  
Ved hjælp af scenariet contoso-overholdelsesgrænser skal der oprettes fire rollegrupper, og de relevante medlemmer skal føjes til hver enkelt.
  
- Fjerde kaffe-eDiscovery-ledere

- Fjerde kaffe efterforskere

- Coho Winery eDiscovery Managers

- Coho Winery Efterforskere
  
Hvis du vil opfylde kravene i scenariet med Contoso-overholdelsesgrænser, skal du også fjerne rollerne **Venteposition** og **Eksportér** fra undersøgelsesrollegrupperne for at forhindre efterforskere i at placere ventepositioner på indholdsplaceringer og eksportere indhold fra en sag.

> [!IMPORTANT]
> Hvis en rolle tilføjes eller fjernes fra en rollegruppe, som du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller i alle tilfælde rollegruppen er medlem af). Årsagen til dette er at beskytte din organisation mod utilsigtet at give yderligere tilladelser til medlemmer af en sag. Hvis en rollegruppe slettes, fjernes den på samme måde fra alle de sager, den var medlem af.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Trin 3: Opret et filter for søgetilladelser for at gennemtvinge overholdelsesgrænsen

Når du har oprettet rollegrupper for hvert agentur, er det næste trin at oprette filtre for søgetilladelser, der knytter hver rollegruppe til dens specifikke agentur og definerer selve overholdelsesgrænsen. Du skal oprette ét filter for søgetilladelser for hvert agentur. Du kan finde flere oplysninger om oprettelse af filtre for sikkerhedstilladelser under [Konfigurer filtrering af tilladelser for indholdssøgning](permissions-filtering-for-content-search.md).
  
Her er den syntaks, der bruges til at oprette et filter for søgetilladelser, der bruges til overholdelse af regler og standarder for scenariet i denne artikel.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Her er en beskrivelse af hver parameter i kommandoen:
  
- `FilterName`: Angiver navnet på filteret. Brug et navn, der beskriver eller identificerer det agentur, som filteret bruges i.

- `Users`: Angiver de brugere eller grupper, der anvender dette filter på de søgehandlinger, de udfører. I forbindelse med overholdelsesgrænser angiver denne parameter rollegrupperne (som du oprettede i trin 3) i det agentur, du opretter filteret for. Bemærk, at dette er en parameter med flere værdier, så du kan inkludere en eller flere rollegrupper adskilt af kommaer.

- `Filters`: Angiver søgekriterierne for filteret. I forbindelse med overholdelsesgrænser definerer du følgende filtre. Hver enkelt gælder for forskellige indholdsplaceringer.

  - `Mailbox`: Angiver de postkasser eller OneDrive konti, som de rollegrupper, der er defineret i parameteren, kan søge efter`Users`. Dette filter gør det muligt for medlemmer af rollegruppen kun at søge i postkasser eller OneDrive konti i et bestemt agentur, `"Mailbox_Department -eq 'FourthCoffee'"`f.eks. .

  - `SiteContent`: Dette filter indeholder to separate filtre. Den første `SiteContent_Path` angiver de SharePoint websteder i det agentur, som de rollegrupper, der er defineret i `Users` parameteren, kan søge efter. For eksempel `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. Det andet `SiteContent_Path` filter (forbundet til det første `SiteContent_Path` filter af operatoren`or`) angiver agenturets OneDrive domæne (også kaldet domænet *Mit websted*). For eksempel `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Du kan også bruge filteret `Site_Path` i stedet for `SiteContent` filteret. Filtrene `Site` og `SiteContent` er udskiftelige og påvirker ikke filtre for søgetilladelser, der er beskrevet i denne artikel.

    > [!IMPORTANT]
    > Hvorfor er filteret `SiteContent` for OneDrive inkluderet i det forrige filter for søgetilladelser? `Mailbox` Selvom filteret gælder *for både* postkasser og OneDrive konti, vil medtagelsen af filteret for SharePoint udelade OneDrive konti, hvis du ikke også medtager filteret OneDrive`Site`. Hvis filteret for søgetilladelser ikke indeholder et SharePoint filter, behøver du ikke at inkludere et separat OneDrive filter, fordi filteret Postkasse vil inkludere OneDrive konti inden for overholdelsesgrænsens område. Med andre ord omfatter et filter for søgetilladelser kun `Mailbox` filteret både postkasser og OneDrive konti.

Her er eksempler på de to filtre for søgetilladelser, der oprettes for at understøtte scenariet contoso-overholdelsesgrænser. Begge disse eksempler omfatter en kommasepareret filterliste, hvor postkasse- og webstedsfiltrene er inkluderet i det samme søgetilladelsesfilter og er adskilt af et komma.
  
### <a name="fourth-coffee"></a>Fjerde kaffe

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Syntaksen for parametrene `Filters` i de tidligere eksempler indeholder en *filterliste*. En filterliste er et filter, der indeholder et postkassefilter og et webstedsstifilter adskilt af et komma. I det forrige eksempel kan du se, at et komma adskiller og `SiteContent` filtrerer`Mailbox`: `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Når dette filter behandles under kørslen af en eDiscovery-søgning, oprettes der to filtre for søgetilladelser fra listen over filtre: ét postkassefilter og ét SharePoint/OneDrive filter. Et alternativ til at bruge en filterliste ville være at oprette to separate søgetilladelsesfiltre for hvert agentur: ét søgetilladelsesfilter for postkasseattributten og ét filter for SharePoint og OneDrive webstedsattributter. I begge tilfælde er resultaterne de samme. Det er en præference at bruge en filterliste eller oprette separate filtre for søgetilladelser.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Hvordan fungerer filtrene for søgetilladelser i dette scenarie?

Her kan du se, hvordan filtrene for søgetilladelser anvendes for hvert agentur i dette scenarie.

1. Filteret `Mailbox` anvendes først til at definere de indholdsplaceringer, som eDiscovery-ledere kan søge efter. I dette tilfælde kan Coho Winery eDiscovery-ledere kun søge i postkasser og OneDrive konti for brugere, hvis egenskab *afdelingspostkasse* har værdien **FourthCoffee**. EDiscovery-ledere i Coho Winery kan kun søge i postkasserne og OneDrive konti for brugere, hvis egenskab *for afdelingens* postkasse har værdien **CohoWinery**. Filteret `Mailbox` er et *filter for indholdsplacering*, fordi det angiver de indholdsplaceringer, som eDiscovery-ledere kan søge efter. I begge filtre kan eDiscovery-ledere kun søge efter indholdsplaceringer med en bestemt egenskabsværdi for postkassen.

2. Når de indholdsplaceringer, der kan søges efter, er defineret, definerer den næste del af filteret det indhold, som eDiscovery-ledere kan søge efter. Med det første `SiteContent` filter kan 4. kaffe-eDiscovery-ledere kun søge efter dokumenter, der har en egenskab for webstedsstien, som indeholder (eller starter med) `https://contoso.sharepoint.com/sites/FourthCoffee`; Coho Winery eDiscovery-ledere kan kun søge i dokumenter, der har en egenskab for webstedsstien, der indeholder (eller starter med) `https://contoso.sharepoint.com/sites/CohoWinery`. Derfor er de to `SiteContent` filtre *indholdsfiltre* , fordi de definerer det indhold, der kan søges efter. I begge filtre kan eDiscovery-ledere kun søge efter dokumenter med en bestemt dokumentegenskabsværdi. Alle SharePoint-relaterede filtre er indholdsfiltre, fordi søgbare webstedsegenskaber stemples på alle dokumenter. Du kan finde flere oplysninger under [Konfigurer filtrering af tilladelser for eDiscovery](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Selvom scenariet i denne artikel ikke bruger dem, kan du også bruge indholdsfiltre for postkasser til at angive det indhold, som eDiscovery-ledere kan søge efter. Syntaksen for indholdsfiltre for postkasser er `"MailboxContent_<property> -<comparison operator> '<value>'"`. Du kan oprette indholdsfiltre baseret på datointervaller, modtagere og domæner eller en hvilken som helst mailegenskab, der kan søges i. Dette filter gør det f.eks. muligt for eDiscovery-ledere kun at søge efter mailelementer, der sendes eller modtages af brugere i contoso.com domæne: `"MailboxContent_Participants -like 'contoso.com'"`. Du kan finde flere oplysninger om filtre for postkasseindhold under [Konfigurer filtrering af søgetilladelser](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Filteret for søgetilladelser er joinforbundet til søgeforespørgslen af operatoren **AND** boolesk. Det betyder, at når en eDiscovery-leder i et af bureauerne kører en eDiscovery-søgning, skal de elementer, der returneres af søgningen, matche søgeforespørgslen og de betingelser, der er defineret i filteret for søgetilladelser.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>Trin 4: Opret en eDiscovery-sag til undersøgelser inden for agenturet

Det sidste trin er at oprette en eDiscovery-sag (Standard)- eller eDiscovery-sag (Premium) i overholdelsesportalen og derefter tilføje den rollegruppe, du oprettede i trin 2 som medlem af sagen. Dette resulterer i to vigtige egenskaber ved at bruge overholdelsesgrænser:
  
- Det er kun medlemmer af rollegruppen, der er føjet til sagen, der kan se og få adgang til sagen på overholdelsesportalen. Hvis rollegruppen Fjerde kaffeforskere f.eks. er det eneste medlem af en sag, kan medlemmer af rollegruppen Fjerde kaffe eDiscovery-ledere (eller medlemmer af en anden rollegruppe) ikke se eller få adgang til sagen.

- Når et medlem af den rollegruppe, der er tildelt til en sag, kører en søgning, der er knyttet til sagen, kan de kun søge på indholdsplaceringerne i deres agentur (som er defineret af filteret for søgetilladelser, som du oprettede i trin 3).

Sådan opretter du en sag og tildeler medlemmer:

1. Gå til siden **eDiscovery (Standard)** eller **eDiscovery (Premium)** på overholdelsesportalen, og opret en sag.

2. Klik på navnet på den sag, du har oprettet, på listen over sager.

3. Føj rollegrupper som medlemmer til sagen. Du kan finde instruktioner i en af følgende artikler:

   - [Føj medlemmer til en eDiscovery-sag (Standard)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

   - [Føj medlemmer til en eDiscovery-sag (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Når du føjer en rollegruppe til en sag, kan du kun tilføje de rollegrupper, du er medlem af.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Søgning efter og eksport af indhold i Multi-Geo-miljøer

Med filtre for søgetilladelser kan du også styre, hvor indhold distribueres til eksport, og hvilket datacenter der kan søges i, når du søger efter indholdsplaceringer i et [SharePoint Multi-Geo miljø](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).
  
- **Eksportér søgeresultater:** Du kan eksportere søgeresultaterne fra Exchange postkasser, SharePoint websteder og OneDrive konti fra et bestemt datacenter. Det betyder, at du kan angive placeringen af det datacenter, som søgeresultaterne skal eksporteres fra.

    Brug parameteren *Region* for **New-ComplianceSecurityFilter** - eller **Set-ComplianceSecurityFilter-cmdlet'er** til at oprette eller ændre, hvilket datacenter eksporten dirigeres gennem.
  
    |**Parameterværdi**|**Placering af datacenter**|
    |:-----|:-----|
    |NAM  <br/> |Nordamerika (datacentre er i USA)  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Asien og Stillehavsområdet  <br/> |
    |CNA <br/> |Canada|
    |||

- **Ruteindholdssøgninger:** Du kan sende indholdssøgninger på SharePoint websteder og OneDrive konti til et satellitdatacenter. Det betyder, at du kan angive placeringen af det datacenter, hvor søgninger skal køres.

    Brug en af følgende værdier for parameteren *Region* til at styre den datacenterplacering, som søgninger skal køres på, når der søges SharePoint websteder og OneDrive konti.
  
    |**Parameterværdi**|**Datacenterdistributionsplaceringer for SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |OS  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Asien og Stillehavsområdet  <br/> |
    |CNA  <br/> |OS  <br/> |
    |AUS  <br/> |Asien og Stillehavsområdet  <br/> |
    |KOR  <br/> |Organisationens standarddatacenter  <br/> |
    |GBR  <br/> |Europa  <br/> |
    |JPN  <br/> |Asien og Stillehavsområdet  <br/> |
    |IND  <br/> |Asien og Stillehavsområdet  <br/> |
    |LAM  <br/> |OS  <br/> |
    |ELLER  <br/> |Europa |
    |BH  <br/> |Nordamerikas datacentre |
    |||

   Hvis du ikke angiver parameteren *Område* for et filter for søgetilladelser, søges der i organisationens primære SharePoint område. Søgeresultater eksporteres til det nærmeste datacenter.

   For at forenkle konceptet styrer parameteren *Region* det datacenter, der bruges til at søge efter indhold i SharePoint og OneDrive. Dette gælder ikke for søgning efter indhold i Exchange, fordi Exchange indholdssøgninger ikke er bundet af datacentrenes geografiske placering. Den samme parameterværdi *for Område* kan også diktere det datacenter, som eksporteres gennem. Dette er ofte nødvendigt for at kontrollere bevægelsen af data på tværs af geografiske tavler.

> [!NOTE]
> Hvis du bruger eDiscovery (Premium), styrer parameteren *Region* ikke det område, som dataene eksporteres fra. Data eksporteres fra organisationens centrale placering. Desuden er søgning efter indhold i SharePoint og OneDrive ikke bundet af datacentrenes geografiske placering. Der søges i alle datacentre. Du kan finde flere oplysninger om eDiscovery (Premium[) under Oversigt over eDiscovery-løsningen (Premium) i Microsoft 365](overview-ediscovery-20.md).

Her er eksempler på brug af parameteren *Region* , når du opretter søgetilladelsesfiltre for overholdelsesgrænser. Dette forudsætter, at det fjerde kaffe-datterselskab er placeret i Nordamerika, og at Coho Winery er i Europa.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Vær opmærksom på følgende ting, når du søger efter og eksporterer indhold i multi-geo-miljøer.
  
- Parameteren *Region* styrer ikke søgninger i Exchange postkasser. Der søges i alle datacentre, når du søger i postkasser. Hvis du vil begrænse omfanget af, hvilke Exchange postkasser der søges i, skal du bruge parameteren *Filtre*, når du opretter eller ændrer et filter for søgetilladelser.

- Hvis det er nødvendigt for en eDiscovery Manager at søge på tværs af flere SharePoint områder, skal du oprette en anden brugerkonto, som den pågældende eDiscovery-leder skal bruge i søgetilladelsesfilteret til at angive det område, hvor de SharePoint websteder eller OneDrive konti er placeret. Du kan finde flere oplysninger om, hvordan du konfigurerer dette, i afsnittet "Søgning efter indhold i et SharePoint Multi-Geo miljø" i [Indholdssøgning](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- Når du søger efter indhold i SharePoint og OneDrive, dirigerer parameteren *Region* søgninger til enten den primære placering eller satellitplaceringen, hvor eDiscovery-lederen skal foretage eDiscovery-undersøgelser. Hvis en eDiscovery-leder søger SharePoint og OneDrive websteder uden for det område, der er angivet i søgetilladelsesfilteret, returneres der ingen søgeresultater.

- Når du eksporterer søgeresultater fra eDiscovery (Standard), uploades indhold fra alle indholdsplaceringer (herunder Exchange, Skype for Business, SharePoint, OneDrive og andre tjenester, som du kan søge efter ved hjælp af værktøjet Indholdssøgning) til Azure Storage  placering i det datacenter, der er angivet af parameteren *Region*. Dette hjælper organisationer med at overholde angivne standarder ved ikke at tillade, at indhold eksporteres på tværs af kontrollerede grænser. Hvis der ikke er angivet et område i filteret for søgetilladelser, uploades indholdet til organisationens primære datacenter.

  Når du eksporterer indhold fra eDiscovery (Premium), kan du ikke styre, hvor indhold uploades ved hjælp af parameteren *Region*. Indhold uploades til en Azure Storage placering i et datacenter på din organisations centrale placering. Du kan finde en liste over geografiske placeringer, der er baseret på din centrale placering, [under Microsoft 365 Multi-Geo eDiscovery-konfiguration](../enterprise/multi-geo-ediscovery-configuration.md).

- Du kan redigere et eksisterende filter for søgetilladelser for at tilføje eller ændre området ved at køre følgende kommando:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Brug af overholdelsesgrænser for SharePoint hubwebsteder

[SharePoint hubwebsteder](/sharepoint/dev/features/hub-site/hub-site-overview) tilpasses ofte de samme geografiske grænser eller agenturgrænser, som eDiscovery-overholdelsesgrænserne følger. Det betyder, at du kan bruge egenskaben websteds-id for hubwebstedet til at oprette en overholdelsesgrænse. Det gør du ved at bruge cmdlet'en [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) i SharePoint Online PowerShell til at hente SiteId for hubwebstedet og derefter bruge denne værdi for egenskaben afdelings-id til at oprette et filter for søgetilladelser.

Brug følgende syntaks til at oprette et filter for søgetilladelser for et SharePoint hubwebsted:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Her er et eksempel på oprettelse af et filter for søgetilladelser for et hubwebsted for Coho Winery-bureauet:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Begrænsninger for overholdelsesgrænser

Vær opmærksom på følgende begrænsninger, når du administrerer eDiscovery-sager og undersøgelser, der bruger overholdelsesgrænser.
  
- Når du opretter og kører en søgning, kan du vælge indholdsplaceringer uden for dit bureau. Men på grund af filteret for søgetilladelser medtages indhold fra disse placeringer ikke i søgeresultaterne.

- Overholdelsesgrænser gælder ikke for ventepositioner i eDiscovery-sager. Det betyder, at en eDiscovery-leder i ét agentur kan placere en bruger i en anden instans i venteposition. Overholdelsesgrænsen gennemtvinges dog, hvis eDiscovery-styringen søger på indholdsplaceringerne for den bruger, der er sat i venteposition. Det betyder, at eDiscovery-administratoren ikke kan søge i brugerens indholdsplaceringer, selvom brugeren kunne sættes i venteposition.

- Hvis du har fået tildelt et filter for søgetilladelser (enten en postkasse eller et webstedsfilter), og du forsøger at eksportere ikke-indekserede elementer til en søgning, der indeholder alle SharePoint websteder i din organisation, får du vist følgende fejlmeddelelse: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Hvis du har fået tildelt et filter for søgetilladelser, og du vil eksportere ikke-indekserede elementer fra SharePoint, skal du køre søgningen igen og inkludere bestemte SharePoint websteder, der skal søges på. Ellers kan du kun eksportere indekserede elementer fra en søgning, der indeholder alle SharePoint websteder. Du kan finde flere oplysninger om indstillingerne, når du eksporterer søgeresultater, under [Eksportér søgeresultater for indhold](export-search-results.md#step-1-prepare-search-results-for-export).

- Filtre for søgetilladelser anvendes ikke på Exchange offentlige mapper.

## <a name="more-information"></a>Flere oplysninger

- Hvis en postkasse er fra licenseret eller slettet med blød licens, vil brugeren ikke længere blive taget i betragtning inden for overholdelsesgrænsen. Hvis en venteposition blev placeret på postkassen, da den blev slettet, er indholdet, der bevares i postkassen, stadig underlagt en overholdelsesgrænse eller et filter for søgetilladelser.

- Hvis der er implementeret filtre for overholdelsesgrænser og søgetilladelser for en bruger, anbefaler vi, at du ikke sletter en brugers postkasse og ikke brugerens OneDrive konto. Hvis du med andre ord sletter en brugers postkasse, skal du også fjerne brugerens OneDrive konto, da mailbox_RecipientFilter bruges til at gennemtvinge søgetilladelsesfilteret for OneDrive.

- Grænser for overholdelse og filtre for søgetilladelser afhænger af, at attributter stemples på indhold i Exchange, OneDrive og SharePoint og den efterfølgende indeksering af dette stemplede indhold.

- Vi anbefaler ikke, at du bruger udeladelsesfiltre (f.eks. brug `-not()` i et filter for søgetilladelser) til en indholdsbaseret overholdelsesgrænse. Brug af et udeladelsesfilter kan have uventede resultater, hvis indhold med nyligt opdaterede attributter ikke er blevet indekseret.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Who kan oprette og administrere filtre for søgetilladelser (ved hjælp af New-ComplianceSecurityFilter og Set-ComplianceSecurityFilter cmdlet'er)?**
  
Hvis du vil oprette, få vist og redigere filtre for søgetilladelser, skal du være medlem af rollegruppen Organisationsadministration på overholdelsesportalen.
  
**Hvis en eDiscovery-leder tildeles til mere end én rollegruppe, der strækker sig over flere bureauer, hvordan søger de efter indhold i ét bureau eller det andet?**
  
EDiscovery-administratoren kan føje parametre til deres søgeforespørgsel, der begrænser søgningen til et bestemt agentur. Hvis en organisation f.eks. har angivet egenskaben **CustomAttribute10** for at differentiere agenturer, kan de føje følgende til deres søgeforespørgsel til søgepostkasser og OneDrive konti i et bestemt agentur: `CustomAttribute10:<value>`.
  
**Hvad sker der, hvis værdien af den attribut, der bruges som attribut for overholdelse i et filter for søgetilladelser, ændres?**
  
Det tager op til tre dage for et filter for søgetilladelser at gennemtvinge overholdelsesgrænsen, hvis værdien af den attribut, der bruges i filteret, ændres. Lad os f.eks. i Contoso-scenariet sige, at en bruger i det fjerde kaffebureau overføres til Coho Winery-bureauet. Derfor ændres værdien af attributten **Department** for brugerobjektet fra *FourthCoffee* til *CohoWinery*. I denne situation får fjerde kaffe-eDiscovery og investorer søgeresultater for den pågældende bruger i op til tre dage, efter attributten er ændret. På samme måde tager det op til tre dage, før Coho Winery eDiscovery-ledere og efterforskere får søgeresultater for brugeren.
  
**Kan en eDiscovery-leder se indhold fra to separate overholdelsesgrænser?**
  
Ja, det kan du gøre, når du søger i Exchange postkasser ved at føje eDiscovery-administratoren til rollegrupper, der har synlighed for begge bureauer. Når en eDiscovery-administrator søger efter SharePoint websteder og OneDrive konti, kan vedkommende dog kun søge efter indhold i forskellige overholdelsesgrænser, hvis bureauerne befinder sig i det samme område eller på den samme geografiske placering. **Bemærk:** Denne begrænsning for websteder gælder ikke i eDiscovery (Premium), fordi søgning efter indhold i SharePoint og OneDrive ikke er bundet af geografisk placering.
  
**Fungerer filtre for søgetilladelser for ventepositioner for eDiscovery-sager, Microsoft 365 opbevaringspolitikker eller DLP?**
  
Nej, ikke på nuværende tidspunkt.
  
**Hvis jeg angiver et område til at styre, hvor indhold eksporteres, men jeg ikke har en SharePoint organisation i det pågældende område, kan jeg så stadig søge SharePoint?**
  
Hvis det område, der er angivet i filteret for søgetilladelser, ikke findes i din organisation, søges der i standardområdet.
  
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
