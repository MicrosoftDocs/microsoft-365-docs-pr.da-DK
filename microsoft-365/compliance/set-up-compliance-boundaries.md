---
title: Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser
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
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1b45c82f-26c8-44fb-9f3b-b45436fe2271
description: Få mere at vide om, hvordan du bruger overholdelsesgrænser til at oprette logiske grænser, der styrer placeringer af brugerens indhold, som en eDiscovery-leder kan søge i Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5fe023391823abbde2cb289926863bbcbb98dfb2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589532"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser

Vejledningen i denne artikel kan anvendes, når du bruger enten Core eDiscovery eller Advanced eDiscovery til at administrere undersøgelser.

Overensstemmelsesgrænser opretter logiske grænser i en organisation, der styrer brugerens indholdsplaceringer (f.eks. postkasser, OneDrive-konti og SharePoint-websteder), som eDiscovery-ledere kan søge i. Desuden styrer overholdelsesgrænser, hvem der kan få adgang til eDiscovery-sager, der bruges til at administrere juridiske ressourcer, HR-ressourcer eller andre undersøgelser i din organisation. Behovet for overholdelsesgrænser er ofte nødvendigt for multi nationale virksomheder, der skal overholde geografiske tavler og bestemmelser, og for stater, som ofte er opdelt i forskellige myndigheder. Overholdelsesgrænser Microsoft 365 dig i Microsoft 365, når du udfører indholdssøgninger og administrerer undersøgelser med eDiscovery-sager.
  
Vi bruger eksemplet i følgende illustration til at forklare, hvordan overholdelsesgrænser fungerer.
  
![Overholdelsesgrænser består af søgetilladelsesfiltre, der styrer adgangen til myndigheder og administratorrollegrupper, der styrer adgangen til eDiscovery-sager.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
I dette eksempel er Contoso LTD en organisation, der består af to datterselskaber, Fourth Coffee og Coho Winery. Virksomheden kræver, at eDiscovery-ledere og -grafikere kun kan søge i Exchange-postkasser, OneDrive-konti og SharePoint websteder i deres agentur. Desuden kan eDiscovery-ledere og -administratorer kun se eDiscovery-sager i deres agentur, og de kan kun få adgang til de sager, de er medlem af. Desuden kan du i dette scenarie ikke placere indholdsplaceringer i venteposition eller eksportere indhold fra en sag. Her kan du se, hvordan overholdelsesgrænser opfylder disse krav.
  
- Funktionen til filtrering af søgetilladelser for eDiscovery styrer de indholdsplaceringer, som eDiscovery-ledere og -administratorer kan søge efter. Det betyder, at eDiscovery-ledere og -administratorer i Fourth Coffee-organisationen kun kan søge efter indholdsplaceringer i datterselskabet Fourth Coffee. Samme begrænsning gælder for Coho Winerys datterselskab.

- [Rollegrupper indeholder](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) følgende funktioner til overholdelse af regler og standarder:

  - Be kontrol, hvem der kan se eDiscovery-sager i Microsoft 365 Overholdelsescenter. Det betyder, at eDiscovery-ledere og -administratorer kun kan se eDiscovery-sager i deres agentur.

  - Be kontrol, hvem der kan tildele medlemmer til en eDiscovery-sag. Det betyder, at eDiscovery-ledere og -brugere kun kan tildele medlemmer til tilfælde, som de selv er medlem af.

  - Styr de eDiscovery-relaterede opgaver, som medlemmer kan udføre, ved at tilføje eller fjerne roller, der tildeler bestemte tilladelser.

- Når der anvendes et søgetilladelsesfilter på en rollegruppe, kan medlemmer af rollegruppen udføre følgende søgerelaterede handlinger, så længe tilladelserne til at udføre en handling tildeles rollegruppen:

  - Søge efter indhold

  - Få vist søgeresultater

  - Eksportér søgeresultater

  - Fjerne elementer, der returneres af en søgning

Her er processen til at konfigurere overensstemmelsesgrænser:
  
[Trin 1: Identificer en brugerattribut for at definere dine myndigheder](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Trin 2: Opret en rollegruppe for hvert agentur](#step-2-create-a-role-group-for-each-agency)

[Trin 3: Opret et søgetilladelsesfilter for at håndhæve overholdelsesrammen](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Trin 4: Opret en eDiscovery-sag til undersøgelser af en intra-agency](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Før du konfigurerer overholdelsesgrænser

- Brugere skal have tildelt en Exchange Online licens. For at bekræfte dette skal du [bruge Get-User-cmdlet'en](/powershell/module/exchange/get-user) Exchange Online PowerShell.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Trin 1: Identificer en brugerattribut for at definere dine myndigheder

Det første trin er at vælge en attribut til brug, der kan definere dine myndigheder. Denne attribut bruges til at oprette filteret for søgetilladelser, der begrænser en eDiscovery-leder til kun at søge på indholdsplaceringer for brugere, der er tildelt en bestemt værdi for denne attribut. Lad os f.eks. sige, at Contoso beslutter sig for at bruge **attributten** Afdeling. Værdien for denne attribut for brugere i det underordnede Fourth Coffee  `FourthCoffee`  ville være, og værdien for brugere i Coho Winery-datterselskabet ville være `CohoWinery`. I trin 3 bruger du dette par (f.eks. Afdeling *:FourthCoffee*) til at begrænse de placeringer af brugerindhold, `attribute:value` som eDiscovery-ledere kan søge efter. 
  
Her er nogle eksempler på brugerattributter, du kan bruge til at overholde regler og standarder:
  
- Firma

- CustomAttribute1 - CustomAttribute15

- Afdeling

- Office

- LandEllerOmråde (landekode på to bogstaver)

Se den komplette liste over understøttede postkassefiltre for at få [en komplet liste](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties).

## <a name="step-2-create-a-role-group-for-each-agency"></a>Trin 2: Opret en rollegruppe for hvert agentur

Det næste trin er at oprette rollegrupper i gruppen Microsoft 365 Overholdelsescenter, der vil være i overensstemmelse med dine myndigheder. Vi anbefaler, at du opretter en rollegruppe ved at kopiere den indbyggede eDiscovery-ledergruppe, tilføje de relevante medlemmer og fjerne roller, der muligvis ikke passer til dine behov. Du kan finde flere oplysninger om eDiscovery-relaterede roller i [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).
  
Hvis du vil oprette rollegrupperne, skal du gå til siden Tilladelser i Microsoft 365 Overholdelsescenter og oprette en rollegruppe for hvert team i hvert agentur, som vil bruge **overholdelsesgrænser** og eDiscovery-sager til at administrere undersøgelser.
  
Ved hjælp af scenariet Contoso-overholdelsesgrænser skal der oprettes fire rollegrupper, og de relevante medlemmer føjes til hver enkelt.
  
- Fourth Coffee eDiscovery Managers

- Fourth Coffee 2010-2016

- Coho Winery eDiscovery Managers

- Coho Winery Winerys
  
For at opfylde kravene i scenariet Contoso-overholdelsesgrænser skal du også fjerne rollerne  **Venteposition** og Eksportér fra rollegrupperne for at forhindre, at indholdsplaceringer placeres i venteposition, og at indhold eksporteres fra en sag.

> [!IMPORTANT]
> Hvis en rolle tilføjes eller fjernes fra en rollegruppe, du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller hvis rollegruppen er medlem af). Dette skyldes, at du beskytter din organisation mod utilsigtet at give ekstra tilladelser til medlemmer af en sag. På samme måde vil en rollegruppe, hvis den slettes, blive fjernet fra alle tilfælde, den var medlem af.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Trin 3: Opret et søgetilladelsesfilter for at håndhæve overholdelsesrammen

Når du har oprettet rollegrupper for hvert agentur, er næste trin at oprette filtre for søgetilladelser, der knytter hver rollegruppe til dens specifikke agentur og definerer selve overholdelsesrammen. Du skal oprette ét søgetilladelsesfilter for hvert agentur. Du kan finde flere oplysninger om at oprette filtre for [sikkerhedstilladelser under Konfigurere filtrering af tilladelser for indholdssøgning](permissions-filtering-for-content-search.md).
  
Her er den syntaks, der bruges til at oprette et søgetilladelsesfilter, der bruges til overholdelse af grænser for scenariet i denne artikel.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Her er en beskrivelse af hver parameter i kommandoen:
  
- `FilterName`: Angiver navnet på filteret. Brug et navn, der beskriver eller identificerer det agentur, som filteret bruges i.

- `Users`: Angiver de brugere eller grupper, der får dette filter anvendt på de søgehandlinger, de udfører. For overholdelsesgrænser angiver denne parameter rollegrupperne (som du oprettede i trin 3) i det agentur, du opretter filteret for. Bemærk, at dette er en parameter med flere værdier, så du kan medtage en eller flere rollegrupper adskilt af kommaer.

- `Filters`: Angiver søgekriterierne for filteret. For at sikre overholdelse af regler og standarder definerer du følgende filtre. Hver enkelt gælder for forskellige indholdsplaceringer.

  - `Mailbox`: Angiver de postkasser eller OneDrive, som rollegrupperne, der er defineret i parameteren, `Users` kan søge i. Dette filter gør det muligt for medlemmer af rollegruppen kun at søge i postkasser eller OneDrive-konti i et bestemt agentur, f.eks. `"Mailbox_Department -eq 'FourthCoffee'"`.

  - `SiteContent`: Dette filter indeholder to separate filtre. Den første `SiteContent_Path` angiver de SharePoint i organisationen, som rollegrupperne, der er defineret i `Users` parameteren, kan søge efter. F.eks. `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. Det andet `SiteContent_Path` filter (der er `SiteContent_Path` forbundet med det første filter `or` af operatoren) angiver bureauets OneDrive (også kaldet *domænet Mit* websted). F.eks. `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Du kan også bruge `Site_Path` filteret i stedet for `SiteContent` filteret. Filtrene `Site` `SiteContent` kan udskiftes og påvirker ikke filtre for søgetilladelser, der er beskrevet i denne artikel.

    > [!IMPORTANT]
    > Hvorfor er filteret `SiteContent` for OneDrive medtaget i det tidligere filter med søgetilladelser? Selvom filteret gælder for  både postkasser og OneDrive-konti, vil medtagelsen af SharePoint-filteret udelade OneDrive-konti, hvis du ikke også medtager filteret OneDrive `Site` filteret.`Mailbox` Hvis filteret for søgetilladelser ikke indeholder et SharePoint-filter, ville du ikke skulle inkludere et separat OneDrive-filter, da filteret Postkasse ville omfatte OneDrive-konti, som er omfattet af overholdelsesrammen. Med andre ord vil et filter med søgetilladelser, der `Mailbox` kun indeholder filteret, omfatte både postkasser og OneDrive konti.

Her er eksempler på de to søgetilladelsesfiltre, der oprettes for at understøtte scenariet contoso-overholdelsesgrænser. Begge disse eksempler omfatter en kommasepareret filterliste, hvor postkasse- og webstedsfiltre er inkluderet i det samme filter for søgetilladelser og er adskilt af et komma.
  
### <a name="fourth-coffee"></a>Fourth Coffee

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Syntaksen for parametrene `Filters` i de forrige eksempler omfatter en *liste over filtre*. En filterliste er et filter, der indeholder et postkassefilter, og et filter for webstedsstier adskilt af et komma. I det forrige eksempel skal du bemærke, at et komma adskiller `Mailbox` og `SiteContent` filtrerer: `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Når dette filter behandles under en eDiscovery-søgning, oprettes der to filtre for søgetilladelser på listen over filtre: ét postkassefilter og ét SharePoint/OneDrive filter. Et alternativ til at bruge en filterliste ville være at oprette to separate filtre for søgetilladelser for hvert agentur: ét søgetilladelsesfilter til postkasseattributten og ét filter for attributterne SharePoint og OneDrive webstedet. I begge tilfælde vil resultaterne være de samme. Det er en god ide at bruge en liste over filtre eller oprette separate søgetilladelsesfiltre.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Hvordan fungerer filtrene for søgetilladelser i dette scenarie?

Her kan du se, hvordan søgetilladelsesfiltrene anvendes for hvert agentur i dette scenarie.

1. Filteret `Mailbox` anvendes først til at definere de indholdsplaceringer, som eDiscovery-ledere kan søge efter. I dette tilfælde kan Coho Winery eDiscovery-ledere kun søge i postkasser og OneDrive konti for brugere, hvis afdelingspostkasseegenskab har værdien **FourthCoffee**; Coho Winery eDiscovery-ledere kan kun søge i postkasser og OneDrive konti for brugere, hvis afdelingspostkasseegenskab har **CohoWinerys værdi**. Filteret `Mailbox` er et *indholdsplaceringsfilter*, fordi det angiver de indholdsplaceringer, som eDiscovery-ledere kan søge efter. I begge filtre kan eDiscovery-ledere kun søge efter indholdsplaceringer med en bestemt egenskabsværdi for postkassen.

2. Når de indholdsplaceringer, der kan søges i, er defineret, definerer næste del af filteret det indhold, som eDiscovery-ledere kan søge efter. Med det første `SiteContent` filter kan Fourth Coffee eDiscovery-ledere kun søge efter dokumenter, der har en webstedsstiegenskab, der indeholder (eller starter med) `https://contoso.sharepoint.com/sites/FourthCoffee`; Coho Winery eDiscovery-ledere kan kun søge efter dokumenter, der har en egenskab for webstedsstien, der indeholder (eller starter med). `https://contoso.sharepoint.com/sites/CohoWinery` Derfor er de to `SiteContent` filtre *indholdsfiltre* , fordi de definerer det indhold, der kan søges efter. I begge filtre kan eDiscovery-ledere kun søge efter dokumenter med en bestemt dokumentegenskabsværdi. Alle SharePoint filtre er indholdsfiltre, fordi søgbare webstedsegenskaber er stemplet på alle dokumenter. Få mere at vide under [Konfigurer tilladelsesfiltrering for eDiscovery](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Selvom scenariet i denne artikel ikke bruger dem, kan du også bruge postkasseindholdsfiltre til at angive det indhold, som eDiscovery-ledere kan søge efter. Syntaksen for postkasseindholdsfiltre er `"MailboxContent_<property> -<comparison operator> '<value>'"`. Du kan oprette indholdsfiltre baseret på datointervaller, modtagere og domæner eller enhver søgbar mailegenskab. Dette filter gør det f.eks. muligt for eDiscovery-ledere kun at søge efter mailelementer, der er sendt eller modtaget af brugere på contoso.com domæne: `"MailboxContent_Participants -like 'contoso.com'"`. Du kan finde flere oplysninger om filtre til postkasseindhold [i Konfigurere filtrering af søgetilladelser](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Filteret for søgetilladelser er sammenføjet til søgeforespørgslen **af OG** boolesk operatoren. Det betyder, at når en eDiscovery-leder i en af styrerne kører en eDiscovery-søgning, skal de elementer, der returneres af søgningen, svare til søgeforespørgslen og de betingelser, der er defineret i filteret for søgetilladelser.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>Trin 4: Opret en eDiscovery-sag til undersøgelser af intra-agency

Det sidste trin er at oprette en Core eDiscovery-sag eller Advanced eDiscovery-sag i Microsoft 365 Overholdelsescenter og derefter tilføje den rollegruppe, du oprettede i trin 2, som medlem af sagen. Dette giver to vigtige egenskaber ved brug af overholdelsesgrænser:
  
- Kun medlemmer af rollegruppen, der er føjet til sagen, vil kunne se og få adgang til sagen Microsoft 365 Overholdelsescenter. Hvis f.eks. rollegruppen Fourth Coffee Billeder er det eneste medlem af en sag, vil medlemmer af rollegruppen Fourth Coffee eDiscovery-ledere (eller medlemmer af en anden rollegruppe) ikke kunne se eller få adgang til sagen.

- Når et medlem af den rollegruppe, der er tildelt til en sag, kører en søgning, der er knyttet til sagen, vil de kun kunne søge på indholdsplaceringerne i deres agentur (hvilket er defineret af det filter for søgetilladelser, du oprettede i trin 3).

Sådan opretter du en sag og tildeler medlemmer:

1. Gå til **core eDiscovery-** **eller Advanced eDiscovery-siden** i Microsoft 365 Overholdelsescenter og opret en sag.

2. Klik på navnet på den sag, du har oprettet, på listen over sager.

3. Føj rollegrupper som medlemmer til sagen. Du kan finde en vejledning i en af følgende artikler:

   - [Føj medlemmer til en Core eDiscovery-sag](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

   - [Føj medlemmer til en Advanced eDiscovery sag](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Når du føjer en rollegruppe til en sag, kan du kun tilføje de rollegrupper, du er medlem af.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Søgning og eksport af indhold i Multi-Geo-miljøer

Med søgetilladelser kan du også styre, hvor indhold dirigeres til eksport, og hvilket datacenter der kan søges i, når der søges i indholdsplaceringer i et [SharePoint Multi-Geo miljø](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).
  
- **Eksportér søgeresultater:** Du kan eksportere søgeresultaterne fra Exchange postkasser, SharePoint websteder og OneDrive konti fra et bestemt datacenter. Det betyder, at du kan angive den placering i datacenteret, som søgeresultaterne skal eksporteres fra.

    Brug *Område-parameteren* for **New-ComplianceSecurityFilter** eller **Set-ComplianceSecurityFilter-cmdlet'er** til at oprette eller ændre, hvilket datacenter eksporten skal distribueres gennem.
  
    |**Parameterværdi**|**Datacenterplacering**|
    |:-----|:-----|
    |NAM  <br/> |Nordamerika (datacentre findes i USA)  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Asien/Stillehavsområdet  <br/> |
    |CAN <br/> |Canada|
    |||

- **Distribuere indholdssøgninger:** Du kan dirigere indholdssøgninger af SharePoint-websteder og OneDrive-konti til et satellitdatacenter. Det betyder, at du kan angive den placering i datacenteret, hvor søgninger skal køres.

    Brug en af følgende værdier for *parameteren Område* til at styre den datacenterplacering, der søges i, når der søges efter SharePoint og OneDrive konti.
  
    |**Parameterværdi**|**Routingplaceringer for datacenter til SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |USA  <br/> |
    |EUR  <br/> |Europa  <br/> |
    |APC  <br/> |Asien/Stillehavsområdet  <br/> |
    |CAN  <br/> |USA  <br/> |
    |AUS  <br/> |Asien/Stillehavsområdet  <br/> |
    |KOR  <br/> |Organisationens standarddatacenter  <br/> |
    |GBR  <br/> |Europa  <br/> |
    |JPN  <br/> |Asien/Stillehavsområdet  <br/> |
    |IND  <br/> |Asien/Stillehavsområdet  <br/> |
    |1. 1  <br/> |USA  <br/> |
    |NOR  <br/> |Europa |
    |BRA  <br/> |Nordamerikanske datacentre |
    |||

   Hvis du ikke angiver *områdeparameteren* for et søgetilladelsesfilter, søges der i organisationens SharePoint søgeområde. Søgeresultaterne eksporteres til det nærmeste datacenter.

   For at forenkle begrebet styrer *områdeparameteren* det datacenter, der bruges til at søge efter indhold i SharePoint og OneDrive. Dette gælder ikke for søgning efter indhold i Exchange, Exchange-indholdssøgninger ikke er bundet af datacentres geografiske placering. Desuden kan den samme *Område-parameterværdi* også diktere det datacenter, som eksporter dirigeres gennem. Dette er ofte nødvendigt for at styre bevægelsen af data på tværs af geografiske boardere.

> [!NOTE]
> Hvis du bruger en Advanced eDiscovery *, styrer* parameteren Område ikke det område, som dataene eksporteres fra. Data eksporteres fra organisationens centrale placering. Endvidere er søgning efter indhold SharePoint indhold OneDrive ikke bundet af den geografiske placering af datacentre. Der søges i alle datacentre. Du kan finde flere Advanced eDiscovery i [Oversigt over Advanced eDiscovery løsningen i Microsoft 365](overview-ediscovery-20.md).

Her er eksempler på brug af parameteren *Område, når* du opretter søgetilladelsesfiltre for overholdelse af grænser. Det antages, at Fourth Coffee er placeret i Nordamerika, og at Coho Winery er i Europa.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Husk følgende, når du søger efter og eksporterer indhold i multi-geo-miljøer.
  
- *Parameteren* Område styrer ikke søgninger i Exchange postkasser. Der søges i alle datacentre, når du søger i postkasser. Hvis du vil begrænse omfanget af Exchange postkasser, der søges i, skal du *bruge* filterparameteren, når du opretter eller ændrer et filter for søgetilladelser.

- Hvis det er nødvendigt, at en eDiscovery Manager søger på tværs af flere SharePoint-områder, skal du oprette en anden brugerkonto, som den pågældende eDiscovery-leder skal bruge i filteret for søgetilladelser til at angive det område, hvor SharePoint-webstederne eller OneDrive-konti er placeret. Du kan finde flere oplysninger om konfiguration af dette i afsnittet "Søgning efter indhold SharePoint Multi-Geo et miljø" i [Indholdssøgning](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- Når du søger efter indhold i SharePoint og OneDrive, dirigerer områdeparameteren  søgninger til enten den primære eller satellitplacering, hvor eDiscovery-chefen vil udføre eDiscovery-undersøgelser. Hvis en eDiscovery-leder SharePoint og OneDrive websteder uden for det område, der er angivet i filteret for søgetilladelser, returneres der ingen søgeresultater.

- Når du eksporterer søgeresultater fra Core eDiscovery, uploades indhold fra alle placeringer med indhold (herunder Exchange, Skype for Business, SharePoint, OneDrive og andre tjenester, som du kan søge efter ved hjælp af værktøjet Indholdssøgning), til Azure Storage  placering i det datacenter, der er angivet af *parameteren Område*. Dette hjælper organisationer med at overholde reglerne ved ikke at tillade eksport af indhold på tværs af kontrollerede kanter. Hvis der ikke er angivet et område i filteret for søgetilladelser, uploades indhold til organisationens primære datacenter.

  Når du eksporterer indhold Advanced eDiscovery, kan du ikke styre, hvor indhold overføres, ved hjælp af *områdeparameteren*. Indhold uploades til Azure Storage placering i et datacenter på organisationens centrale placering. Du kan finde en liste over geoplaceringer, der er baseret på din centrale placering, [Microsoft 365 konfiguration af Multi-Geo eDiscovery](../enterprise/multi-geo-ediscovery-configuration.md).

- Du kan redigere et eksisterende søgetilladelsesfilter for at tilføje eller ændre området ved at køre følgende kommando:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Brug af overholdelsesgrænser for SharePoint hubwebsteder

[SharePoint-hubwebsteder](/sharepoint/dev/features/hub-site/hub-site-overview) opfylder ofte de samme geografiske grænser eller grænsen for overholdelse af regler og standarder, som eDiscovery-overholdelse følger. Det betyder, at du kan bruge egenskaben Websteds-id for hubwebstedet til at oprette en overholdelsesgrænse. For at gøre dette skal du bruge [Get-SPOHubSite-cmdlet'en](/powershell/module/sharepoint-online/get-spohubsite#examples) i SharePoint Online PowerShell til at hente Websteds-id'et for hubwebstedet og derefter bruge denne værdi for egenskaben afdelings-id til at oprette et søgetilladelsesfilter.

Brug følgende syntaks til at oprette et søgetilladelsesfilter for et SharePoint-hubwebsted:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Her er et eksempel på, hvordan du kan oprette et søgetilladelsesfilter for et hubwebsted for Coho Winery-bureauet:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Begrænsninger i overholdelsesgrænse

Husk følgende begrænsninger, når du administrerer eDiscovery-sager og undersøgelser, der bruger af overholdelsesgrænser.
  
- Når du opretter og kører en søgning, kan du vælge indholdsplaceringer, der er uden for dit agentur. Grundet filteret for søgetilladelser medtages indhold fra disse placeringer dog ikke i søgeresultaterne.

- Overholdelsesgrænser gælder ikke for ventende mails i eDiscovery-sager. Det betyder, at en eDiscovery-leder i ét agentur kan placere en bruger i et andet agentur i venteposition. Overholdelsesrammen håndhæves dog, hvis eDiscovery-chefen søger på indholdsplaceringen for den bruger, der er sat i venteposition. Det betyder, at eDiscovery-chefen ikke kan søge i brugerens indholdsplaceringer, selvom brugeren var i venteposition.

    Desuden gælder ventepositionsstatistik kun for indholdsplaceringer i organisationen.

- Hvis du har fået tildelt et søgetilladelsesfilter (enten en postkasse eller et webstedsfilter), og du forsøger at eksportere uindsiderede elementer til en søgning, der omfatter alle SharePoint-websteder i organisationen, får du vist følgende fejlmeddelelse: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Hvis du har fået tildelt et søgetilladelsesfilter, og du vil eksportere ikke-identificerede elementer fra SharePoint, skal du køre søgningen igen og medtage bestemte SharePoint-websteder, du vil søge efter. Ellers vil du kun kunne eksportere indekserede elementer fra en søgning, der omfatter alle SharePoint websteder. Du kan finde flere oplysninger om indstillingerne, når du eksporterer søgeresultater, under [Eksportér resultater fra indholdssøgning](export-search-results.md#step-1-prepare-search-results-for-export).

- Filtre for søgetilladelser anvendes ikke på Exchange offentlige mapper.

## <a name="more-information"></a>Flere oplysninger

- Hvis en postkasse de-licenserede eller blød-slettede, vil brugeren ikke længere blive taget i betragtning inden for overholdelsesrammen. Hvis der er sat en venteposition på postkassen, da den blev slettet, er det indhold, der bevares i postkassen, stadig underlagt en overholdelsesgrænse eller et filter med søgetilladelser.

- Hvis der er implementeret filtre for overholdelse af angivne grænser og søgetilladelser for en bruger, anbefaler vi, at du ikke sletter en brugers postkasse og ikke brugerens OneDrive konto. Med andre ord, hvis du sletter en brugers postkasse, skal du også fjerne brugerens OneDrive-konto, da mailbox_RecipientFilter bruges til at gennemtvinge filtrering af søgetilladelser for OneDrive.

- Overholdelsesgrænser og søgetilladelser for filtre afhænger af, at attributter bliver stemplet på indhold i Exchange, OneDrive og SharePoint og den efterfølgende indeksering af dette stemplede indhold.

- Vi anbefaler ikke at bruge udelukkelsesfiltre (f.eks `-not()` . brug i et søgetilladelsesfilter) til en indholdsbaseret overholdelsesgrænse. Brug af et udeladelsesfilter kan have uventede resultater, hvis indhold med nyligt opdaterede attributter ikke er blevet indekseret.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Who kan oprette og administrere filtre for søgetilladelser (ved hjælp New-ComplianceSecurityFilter og Set-ComplianceSecurityFilter cmdlet'er)?**
  
Hvis du vil oprette, få vist og redigere filtre for søgetilladelser, skal du være medlem af rollegruppen Organisationsadministration i Microsoft 365 Overholdelsescenter.
  
**Hvis en eDiscovery-leder er tildelt mere end én rollegruppe, der omfatter flere myndigheder, hvordan kan de så søge efter indhold i et agentur eller et andet?**
  
eDiscovery-chefen kan tilføje parametre til deres søgeforespørgsel, der begrænser søgningen til et bestemt agentur. Hvis en organisation f.eks. har specificeret **egenskaben CustomAttribute10** til at skelne mellem myndigheder, kan de tilføje følgende til deres søgeforespørgsel for at søge i postkasser og OneDrive-konti i et bestemt agentur: `CustomAttribute10:<value>`
  
**Hvad sker der, hvis værdien af den attribut, der bruges som overholdelsesattribut i et søgetilladelsesfilter, ændres?**
  
Det tager op til tre dage for et søgetilladelsesfilter at håndhæve overholdelsesrammen, hvis værdien af den attribut, der bruges i filteret, ændres. I Contoso-scenariet kan vi f.eks. sige, at en bruger i Fourth Coffee Agency overføres til Coho Winery-bureauet. Som resultat heraf ændres værdien af **attributten Afdeling** på brugerobjektet fra *FourthCoffee* *til CohoWinery*. I denne situation vil Fourth Coffee eDiscovery og investorer få søgeresultater for den pågældende bruger i op til tre dage, efter attributten er ændret. På samme måde tager det op til tre dage, før Coho Winery eDiscovery-ledere og administratorer får søgeresultater for brugeren.
  
**Kan en eDiscovery-leder se indhold fra to separate overholdelsesgrænser?**
  
Ja, det kan du gøre, når du søger i Exchange postkasser ved at føje eDiscovery-lederen til rollegrupper, der har synlighed til begge parter. Men når du søger SharePoint-websteder og OneDrive-konti, kan en eDiscovery-leder kun søge efter indhold inden for forskellige overholdelsesgrænser, hvis styrelserne er i samme område eller geografiske placering. **Bemærk!** Denne begrænsning for websteder gælder ikke i Advanced eDiscovery, fordi søgning efter indhold i SharePoint og OneDrive ikke er bundet af geografisk placering.
  
**Fungerer filtre for søgetilladelser for eDiscovery-sags hold, Microsoft 365 opbevaringspolitikker eller DLP?**
  
Nej, ikke på nuværende tidspunkt.
  
**Hvis jeg angiver et område, hvor indhold skal eksporteres, men jeg ikke har en SharePoint-organisation i det pågældende område, kan jeg så stadig SharePoint?**
  
Hvis det område, der er angivet i filteret for søgetilladelser, ikke findes i din organisation, søges der i standardområdet.
  
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
