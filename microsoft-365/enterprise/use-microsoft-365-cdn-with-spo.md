---
title: Brug Office 365 Content Delivery Network (CDN) med SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Lær at bruge Office 365 Content Delivery Network (CDN) til at sætte fart på leveringen af dine SharePoint Online-aktiver.
ms.openlocfilehash: f4279da3bba7647f2e99179acb0147fe5d002f57
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/14/2022
ms.locfileid: "63589715"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Brug Office 365 Content Delivery Network (CDN) med SharePoint Online

Du kan bruge den indbyggede Office 365 Content Delivery Network (CDN) til at hoste statiske aktiver for at sikre en bedre ydeevne for SharePoint onlinesider. Overførselsvinduet Office 365 CDN ydeevnen ved at cache statiske aktiver tættere på browserne, der anmoder om dem, hvilket hjælper dig med at sætte fart på overførsler og reducere ventetiden. Desuden bruger Office 365 CDN [HTTP/2-protokollen til](https://en.wikipedia.org/wiki/HTTP/2) forbedret komprimering og HTTP-pipelining. Tjenesten Office 365 CDN inkluderet som en del af dit SharePoint Online-abonnement.

> [!NOTE]
> Lejerne Office 365 CDN kun tilgængelige for lejere i **produktionsskyen** (hele verden). Lejere i den amerikanske stat, Kina og Tysklands skyer understøtter i øjeblikket ikke Office 365 CDN.

The Office 365 CDN består af flere CDN'er, der giver dig mulighed for at hoste statiske aktiver på flere placeringer eller _oprindelser og betjene_ dem fra globale højhastighedsnetværk. Afhængigt af den type indhold, du vil hoste i Office 365 CDN, kan du tilføje offentlige oprindelser, **private** oprindelser eller begge dele. Se [Vælg, om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for at få flere oplysninger om forskellen mellem offentlige og private oprindelser.

![Office 365 CDN konceptuelt diagram.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN begrebsmæssigt diagram")

Hvis du allerede er fortrolig med måden, CDN fungerer på, skal du kun udføre nogle få trin for at aktivere Office 365 CDN for din lejer. I dette emne beskrives det hvordan. Læs videre for at få oplysninger om, hvordan du kommer i gang med at hoste dine statiske aktiver.

> [!TIP]
> Der findes andre Microsoft-hostede CDN'er, der kan bruges med Office 365 til specialiserede brugsscenarier, men som ikke er nævnt i dette emne, fordi de ligger uden for Office 365 CDN. Du kan finde flere oplysninger [under Andre Microsoft-CDN'er](content-delivery-networks.md#other-microsoft-cdns).

 **Gå tilbage til [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Oversigt over arbejdet med Office 365 CDN i SharePoint Online

Hvis du vil konfigurere Office 365 CDN for organisationen, skal du følge disse grundlæggende trin:

+ [Planlæg udrulning af Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Fast afgør, hvilke statiske aktiver du vil hoste på CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Bestem, hvor du vil gemme aktiverne](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Denne placering kan være et SharePoint websted, et bibliotek eller en mappe og kaldes en _oprindelse_.
  + [Vælg, om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Du kan tilføje flere oprindelser af både offentlige og private typer.

+ Konfigurer og konfigurer CDN enten ved hjælp af PowerShell eller CLI for Microsoft 365

  + [Konfigurere og konfigurere CDN ved hjælp af SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Konfigurere programmet ved CDN PnP PowerShell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Konfigurer og konfigurer CDN ved hjælp af CLI for Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Når du har fuldført dette trin, har du:

  + Aktiverede CDN for organisationen.
  + Dine oprindelser er tilføjet, og hver oprindelse er identificeret som offentlig eller privat.

Når du er færdig med konfigurationen, kan [du administrere Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) over tid ved at:

+ Tilføje, opdatere og fjerne aktiver
+ Tilføje og fjerne oprindelser
+ Konfiguration af CDN politikker
+ Deaktiver om nødvendigt CDN

Til sidst skal du [se Brug dine CDN-aktiver](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) til at få mere at vide om at få CDN aktiver fra både offentlige og private oprindelser.

Se [Fejlfinding i Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) for at få vejledning i at løse almindelige problemer.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planlæg udrulning af Office 365 CDN

Før du installerer Office 365 CDN for din Office 365 lejer, bør du overveje følgende faktorer som en del af planlægningsprocessen.

  + [Fast afgør, hvilke statiske aktiver du vil hoste på CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Bestem, hvor du vil gemme aktiverne](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Vælg, om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Fast afgør, hvilke statiske aktiver du vil hoste på CDN

Generelt er CDN'er mest effektive til at _hoste statiske_ aktiver eller aktiver, der ikke ændres særlig ofte. En god tommelfingerregel er at identificere filer, der opfylder nogle af eller alle disse betingelser:

+ Statiske filer integreret i en side (f.eks. scripts og billeder), der kan have en betydelig trinvis indvirkning på sideindlæsningstider
+ Store filer som eksekverbare filer og installationsfiler
+ Ressourcebiblioteker, der understøtter kode på klientsiden

F.eks. kan små filer, der gentagne gange anmodes om, såsom webstedsbilleder og scripts, forbedre webstedsgengivelsesydeevnen betydeligt og gradvist reducere belastningen på dine SharePoint Online-websteder, når du føjer dem til en CDN-oprindelse. Større filer, f.eks. eks. eksekverbare filer til installation, kan downloades fra CDN, hvilket giver en positiv påvirkning af ydeevnen og efterfølgende reduktion af belastningen på dit SharePoint Online-websted, også selvom der ikke opnås adgang til dem så ofte.

Forbedring af ydeevnen pr. fil afhænger af mange faktorer, herunder klientens afstand til det nærmeste CDN-slutpunkt, midlertidige betingelser på det lokale netværk osv. Mange statiske filer er ret små og kan downloades fra Office 365 på mindre end et sekund. En webside kan dog indeholde mange integrerede filer med en samlet downloadtid på flere sekunder. Servering af disse filer fra CDN kan reducere den samlede sideindlæsningstid betydeligt. Se[, hvilke resultater en CDN giver?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for et eksempel.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Bestem, hvor du vil gemme aktiverne

Den CDN henter aktiverne fra en placering, der kaldes en _oprindelse_. En oprindelse kan være et SharePoint, et dokumentbibliotek eller en mappe, der er tilgængelig via en URL-adresse. Du har stor fleksibilitet, når du angiver oprindelser for din organisation. Du kan f.eks. angive flere oprindelser eller en enkelt oprindelse, hvor du vil placere alle dine CDN aktiver. Du kan vælge at have både offentlige eller private oprindelser for din organisation. De fleste organisationer vælger at implementere en kombination af de to.

Du kan oprette nye objektbeholdere til dine oprindelser, f.eks. mapper eller dokumentbiblioteker, og tilføje filer, du vil gøre tilgængelige fra CDN. Dette er en god fremgangsmåde, hvis du har et bestemt sæt aktiver, der skal være tilgængelige fra CDN, og du vil begrænse sættet af CDN-aktiver til kun disse filer i beholderen.

Du kan også konfigurere en eksisterende gruppe af websteder, et websted, et bibliotek eller en mappe som en oprindelse, hvilket gør alle berettigede aktiver i beholderen tilgængelige fra CDN. Før du tilføjer en eksisterende beholder som en oprindelse, er det vigtigt at sikre, at du er opmærksom på dens indhold og tilladelser, så du ikke ved et tilfælde udsætter aktiver for anonym adgang eller uautoriserede brugere.

Du kan definere _CDN for_ at udelukke indhold i dine oprindelser fra CDN. CDN politikker udelader aktiver i offentlige eller private oprindelser efter attributter som filtype og  webstedsklassificering _og anvendes_ på alle oprindelser af CdnType (privat eller offentlig), som du angiver i politikken. Hvis du f.eks. tilføjer en privat oprindelse bestående af et websted, der indeholder flere underordnede websteder, kan du definere en politik for at udelukke websteder, der er markeret som fortrolige, så indhold fra websteder, som har den pågældende klassificering anvendt, ikke kommer fra CDN. Politikken gælder for indhold fra alle _private oprindelser_, du har føjet til CDN.

Vær opmærksom på, at jo større antallet af oprindelser er, desto større indvirkning på den tid, det tager CDN behandle anmodninger. Vi anbefaler, at du begrænser antallet af oprindelser så meget som muligt.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Vælg, om hver oprindelse skal være offentlig eller privat

Når du identificerer en oprindelse, angiver du, om den skal gøres _offentlig_ eller _privat_. Adgang til CDN aktiver i offentlige oprindelser er anonymt, og CDN indhold i private oprindelser er sikret af dynamisk genererede tokens af hensyn til større sikkerhed. Uanset hvilken indstilling du vælger, gør Microsoft det hårde arbejde for dig, når det kommer til administrationen af selve CDN. Du kan også ændre mening senere, når du har konfigureret hovederne CDN identificeret dine oprindelser.

Både offentlige og private muligheder giver lignende ydeevnefordele, men de har hver unikke attributter og fordele.

**Offentlige** oprindelser i Office 365 CDN er anonymt tilgængelige, og tilknyttede aktiver kan tilgås af alle, der har URL-adressen til aktivet. Da adgang til indhold i offentlige oprindelser er anonymt, bør du kun bruge det til at cachelagre ikke-følsomt generisk indhold som f.eks. JavaScript-filer, scripts, ikoner og billeder.

**Private** oprindelser i Office 365 CDN giver privat adgang til brugerindhold som f.eks. SharePoint Online-dokumentbiblioteker, websteder og beskyttede billeder. Adgang til indhold i private oprindelser er sikret med dynamisk genererede tokens, så de kan kun åbnes af brugere med tilladelser til det oprindelige dokumentbibliotek eller den oprindelige lagerplacering. Private oprindelser i Office 365 CDN kan kun bruges til SharePoint Online-indhold, og du kan kun få adgang til aktiver i private oprindelser via omdirigering fra din SharePoint Online-lejer.

Du kan læse mere om, CDN adgang til aktiver i en privat oprindelse fungerer i [Brug af aktiver i private oprindelser](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attributter og fordele ved at hoste aktiver i offentlige oprindelser

+ Aktiver, der er tilgængelige i en offentlig oprindelse, kan tilgås anonymt af alle.
    > [!IMPORTANT]
    > Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som betragtes som følsomme for din organisation, i en offentlig oprindelse.

+ Hvis du fjerner et aktiv fra en offentlig oprindelse, kan det være, at aktivet fortsat er tilgængeligt i op til 30 dage fra cachen. vi gør dog links til aktivet ugyldige inden for CDN 15 minutter.

+ Når du hoster typografiark (CSS-filer) i en offentlig oprindelse, kan du bruge relative stier og URI'er inden for koden. Det betyder, at du kan henvise til placeringen af baggrundsbilleder og andre objekter i forhold til placeringen af det aktiv, der kalder det.

+ Selvom du kan konstruere en offentlig oprindelses URL-adresse, skal du gå forsigtigt videre og sikre, at du bruger sidekontekstegenskaben og følge vejledningen for at gøre dette. Dette skyldes, at hvis adgangen til CDN ikke længere er tilgængelig, så bliver URL-adressen ikke automatisk tilgængelig for din organisation i SharePoint Online, hvilket kan medføre brudte links og andre fejl. URL-adressen kan også ændres uden at blive ændret, hvilket er grunden til, at den ikke bare skal være hard coded til dens aktuelle værdi.

+ Standardfiltyperne, der er inkluderet til offentlige oprindelser, er .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff og .woff2. Du kan angive yderligere filtyper.

+ Du kan konfigurere en politik til at udelade aktiver, der er blevet identificeret af webstedsklassificeringer, som du angiver. Du kan f.eks. vælge at udelade alle aktiver, der er markeret som "fortrolige" eller "begrænsede", selvom de er en tilladt filtype og er placeret i en offentlig oprindelse.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attributter og fordele ved at hoste aktiver i private oprindelser

+ Private oprindelser kan kun bruges til SharePoint Online-aktiver.

+ Brugere kan kun få adgang til aktiverne fra en privat oprindelse, hvis de har tilladelse til at få adgang til beholderen. Anonym adgang til disse aktiver er forhindret.

+ Aktiver i private oprindelser skal henvises til fra SharePoint Online-lejer. Direkte adgang til private CDN fungerer ikke.

+ Hvis du fjerner et aktiv fra den private oprindelse, kan aktivet fortsat være tilgængeligt i op til en time fra cachen. vi gør dog links til aktivet ugyldige inden for CDN 15 minutter efter fjernelsen af aktivet.

+ Standardfiltyperne, der er inkluderet til private oprindelser, er .gif, .ico, .jpeg, .jpg, .js og .png. Du kan angive yderligere filtyper.

+ På samme måde som med offentlige oprindelser kan du konfigurere en politik for at udelade aktiver, der er blevet identificeret af webstedsklassificeringer, som du angiver, selvom du bruger jokertegn til at medtage alle aktiver i en mappe eller et dokumentbibliotek.

Du kan finde flere oplysninger om, hvorfor du skal bruge Office 365 CDN, generelle CDN-begreber og andre Microsoft-CDN'er, du kan bruge med din Office 365-lejer, under Netværk, der kan levere [indhold](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Standard CDN oprindelser

Medmindre du angiver noget andet, Office 365 konfigurerer nogle standard oprindelser for dig, når du aktiverer Office 365 CDN. Hvis du vælger ikke at klargøre dem, kan du tilføje disse oprindelser, når du har fuldført konfigurationen. Medmindre du forstår konsekvenserne af at springe installationen af standardoprindelse over og har en bestemt årsag til at gøre dette, skal du tillade, at de bliver oprettet, når du aktiverer CDN.

Private standard CDN oprindelser:

+ \*/userphoto.aspx
+ \*/siteassets

Offentlige standard CDN oprindelser:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ er en offentlig standardindrindelse, der blev føjet til Office 365 CDN i december 2017. Denne oprindelse skal være til stede, for at SharePoint Framework løsninger i CDN at fungere. Hvis du har aktiveret Office 365 CDN før december 2017, eller hvis du ignorerede konfigurationen af standardindtrindelse, da du aktiverede CDN, kan du tilføje denne oprindelse manuelt. Du kan finde flere [oplysninger i webdelen Min klientside eller SharePoint Framework-løsning fungerer ikke](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Konfigurere og konfigurere Office 365 CDN ved hjælp af SharePoint Online Management Shell

Fremgangsmåderne i dette afsnit kræver, at du bruger SharePoint Online Management Shell til at oprette forbindelse til SharePoint Online. Du kan finde en [vejledning Forbind at SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Fuldfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp SharePoint Online Management Shell.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Aktivér din organisation til at bruge Office 365 CDN

Før du foretager ændringer i lejerindstillingerne CDN, skal du hente den aktuelle status for den private CDN konfiguration i din Office 365 lejer. Forbind til din lejer ved hjælp af SharePoint Online Management Shell:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Brug nu **Get-SPOTenantCdnEnabled-cmdlet'en** til at hente CDN statusindstillingerne fra lejeren:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Status for den CDN for den angivne CdnType vil blive vist på skærmen.

Brug **Set-SPOTenantCdnEnabled-cmdlet'en** til at gøre det muligt for din organisation at bruge Office 365 CDN. Du kan aktivere din organisations adgang til at bruge offentlige oprindelser, private oprindelser eller begge på én gang. Du kan også konfigurere CDN at springe konfigurationen af standardindrindelse over, når du aktiverer den. Du kan altid tilføje disse oprindelser senere som beskrevet i dette emne.

I Windows PowerShell for SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Hvis du f.eks. vil aktivere din organisations adgang til at bruge både offentlige og private oprindelser, skal du indtaste følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Hvis du vil aktivere din organisations adgang til at bruge både offentlige og private oprindelser, men springe konfigurationen af standardindrindelse over, skal du skrive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Se [Standard-CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for at få oplysninger om de oprindelser, der er klargjort som standard, når du aktiverer Office 365 CDN, og den potentielle virkning af at springe installationen af standardindrindelse over.

Hvis du vil aktivere din organisations adgang til at bruge offentlige oprindelser, skal du indtaste følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Hvis du vil aktivere din organisations adgang til at bruge private oprindelser, skal du indtaste følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Du kan finde flere oplysninger om denne cmdlet under [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Rediger listen over filtyper, der skal medtages i Office 365 CDN (valgfrit)

> [!TIP]
> Når du definerer filtyper ved hjælp af **Set-SPOTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil føje yderligere filtyper til listen, skal du først bruge cmdlet'en til at finde ud af, hvilke filtyper der allerede er tilladte og medtage dem på listen sammen med de nye.

Brug **Set-SPOTenantCdnPolicy-cmdlet'en** til at definere statiske filtyper, der kan hostes af offentlige og private oprindelser i CDN. Som standard er almindelige aktivtyper tilladt, f.eks. .css, .gif, .jpg og .js.

I Windows PowerShell for SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Hvis du f.eks. vil CDN vært for .css og .png-filer, skal du indtaste kommandoen:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Hvis du vil se, hvilke filtyper der aktuelt tillades af CDN, skal du bruge **Get-SPOTenantCdnPolicies-cmdlet'en**:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Du kan finde flere oplysninger om disse cmdlet'er under [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) og [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Rediger listen over webstedsklassificeringer, du vil udelade fra Office 365 CDN (valgfrit)

> [!TIP]
> Når du udelader webstedsklassificeringer ved hjælp af **Set-SPOTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere webstedsklassificeringer, skal du først bruge cmdlet'en til at finde ud af, hvilke klassificeringer der allerede er udeladt, og derefter tilføje dem sammen med de nye.

Brug **set-SPOTenantCdnPolicy-cmdlet'en** til at udelade webstedsklassificeringer, du ikke vil gøre tilgængelige via CDN. Som standard er ingen webstedsklassificeringer udeladt.

I Windows PowerShell for SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Hvis du vil se, hvilke webstedsklassificeringer der i øjeblikket er begrænset, skal du bruge **Get-SPOTenantCdnPolicies-cmdlet'en** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

De egenskaber, der skal returneres, er _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ og _ExcludeIfNoScriptDisabled_.

Egenskaben _IncludeFileExtensions_ indeholder listen over filtypenavne, der skal betjenes fra CDN.

> [!NOTE]
> Standardfiludvidelserne er forskellige fra offentlige til private.

Egenskaben _ExcludeRestrictedSiteClassifications_ indeholder de webstedsklassificeringer, du vil udelukke fra CDN. Du kan f.eks. udelade websteder,  der er markeret som fortrolige, så indhold fra websteder med den pågældende klassificering ikke kommer fra CDN.

Egenskaben _ExcludeIfNoScriptDisabled_ udelukker indhold fra CDN baseret på _noScript-attributindstillingerne på_ webstedsniveau. _NoScript-attributten er som_ standard angivet til **Aktiveret** for _moderne_ websteder og **Deaktiveret** for _klassiske_ websteder. Dette afhænger af dine lejerindstillinger.

Du kan finde flere oplysninger om disse cmdlet'er under [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) og [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Tilføj en oprindelse for aktiverne

Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere en oprindelse. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint-bibliotek eller en mappe, der indeholder de aktiver, der skal være hostet af CDN.

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som betragtes som følsomme for din organisation, i en offentlig oprindelse.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Værdien af stien _er_ den relative sti til det bibliotek eller den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier. Origins understøtter jokertegn, der er afhængige af URL-adressen. Dette giver dig mulighed for at oprette oprindelser, der strækker sig over flere websteder. Hvis du f.eks. vil medtage alle aktiverne i hovedsidemappen for alle dine websteder som en offentlig oprindelse i CDN, skal du skrive følgende kommando:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Jokertegnsmodifikatoren ***/** kan kun bruges i starten af stien og matcher alle URL-segmenter under den angivne URL-adresse.
+ Stien kan pege på et dokumentbibliotek, en mappe eller et websted. Stien _*/websted1 matcher f.eks_ . alle dokumentbiblioteker under webstedet.

Du kan tilføje en oprindelse med en bestemt relativ sti. Du kan ikke tilføje en oprindelse ved hjælp af den fulde sti.

I dette eksempel tilføjes en privat oprindelse for webstedsassets-biblioteket på et bestemt websted:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

I dette eksempel tilføjes en privat oprindelse _af mappen mappe1_ i gruppen af websteders bibliotek over webstedsaktiver:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Hvis der er et mellemrum i stien, kan du enten omslutte stien med dobbelte anførselstegn eller erstatte mellemrummet med URL-adressen, der kodningen %20. Følgende eksempler tilføjer en privat oprindelse af mappen _mappe 1_ i gruppen af websteders bibliotek over webstedsaktiver:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Du kan finde flere oplysninger om denne kommando og dens syntaks [i Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> I private oprindelser skal aktiver, der deles fra en oprindelse, have en overordnede version publiceret, før de kan åbnes fra CDN.

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Eksempel: Konfigurer en offentlig oprindelse for dine mastersider og dit typografibibliotek til SharePoint Online

Normalt er disse oprindelser konfigureret for dig som standard, når du aktiverer Office 365 CDN. Men hvis du vil aktivere dem manuelt, skal du følge disse trin.

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere typografibiblioteket som en offentlig oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mastersiderne som en offentlig oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Du kan finde flere oplysninger om denne kommando og dens syntaks [i Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Eksempel: Konfigurer en privat oprindelse for webstedsaktiver, webstedssider og publiceringsbilleder for SharePoint Online

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedsaktiver som en privat oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedssider som en privat oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med publiceringsbilleder som en privat oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Du kan finde flere oplysninger om denne kommando og dens syntaks [i Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Eksempel: Konfigurer en privat oprindelse for en gruppe af websteder for SharePoint Online

Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere en gruppe af websteder som en privat oprindelse. Eksempel:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Du kan finde flere oplysninger om denne kommando og dens syntaks [i Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Du får muligvis vist _meddelelsen Konfiguration afventer_, som forventes, når SharePoint Online-lejeren opretter forbindelse til CDN-tjenesten. Det kan tage op til 15 minutter.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Administrer Office 365 CDN

Når du har konfigureret CDN, kan du foretage ændringer i konfigurationen, efterhånden som du opdaterer indholdet, eller dine behov ændres, som beskrevet i dette afsnit.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Tilføje, opdatere eller fjerne aktiver fra Office 365 CDN

Når du har gennemført konfigurationstrinnene, kan du tilføje nye aktiver og opdatere eller fjerne eksisterende aktiver, når du ønsker det. Du skal blot foretage dine ændringer af aktiverne i den mappe eller det SharePoint, du har identificeret som en oprindelse. Hvis du tilføjer et nyt aktiv, er det straks tilgængeligt via CDN. Men hvis du opdaterer aktivet, tager det op til 15 minutter, før den nye kopi er overført og tilgængelig i CDN.

Hvis du skal hente placeringen af oprindelsen, kan du bruge **Get-SPOTenantCdnOrigins-cmdlet'en** . Du kan finde oplysninger om, hvordan du bruger denne cmdlet under [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Fjerne en oprindelse fra Office 365 CDN

Du kan fjerne adgangen til en mappe eller et SharePoint, du har identificeret som en oprindelse. For at gøre dette skal du **bruge Remove-SPOTenantCdnOrigin-cmdlet'en** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Du kan finde oplysninger om, hvordan du bruger denne cmdlet under [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Rediger en oprindelse i Office 365 CDN

Du kan ikke ændre en oprindelse, du har oprettet. I stedet skal du fjerne oprindelsen og derefter tilføje en ny. Du kan finde flere oplysninger [i Fjerne en oprindelse fra Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) og [Tilføje en oprindelse for dine aktiver](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Brug **Set-SPOTenantCdnEnabled-cmdlet'en** til at deaktivere CDN for organisationen. Hvis du har både de offentlige og private oprindelser aktiveret for CDN, skal du køre cmdlet'en to gange, som vist i følgende eksempler.

Hvis du vil deaktivere brugen af offentlige oprindelser i CDN, skal du indtaste følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Hvis du vil deaktivere brugen af private oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Du kan finde flere oplysninger om denne cmdlet under [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Konfigurere Office 365 CDN ved hjælp af PnP PowerShell

Fremgangsmåderne i dette afsnit kræver, at du bruger PnP PowerShell til at oprette forbindelse til SharePoint Online. Du kan finde en vejledning [under Introduktion til PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).

Fuldfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp af PnP PowerShell.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Aktivér din organisation til at bruge Office 365 CDN

Før du foretager ændringer i lejerindstillingerne CDN, skal du hente den aktuelle status for den private CDN konfiguration i din Office 365 lejer. Forbind din lejer ved hjælp af PnP PowerShell:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Brug nu **Get-PnPTenantCdnEnabled-cmdlet'en** til at hente CDN-statusindstillingerne fra lejeren:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Status for den CDN for den angivne CdnType vil blive vist på skærmen.

Brug **Set-PnPTenantCdnEnabled-cmdlet'en** til at gøre det muligt for din organisation at bruge Office 365 CDN. Du kan aktivere din organisations adgang til at bruge offentlige oprindelser, private oprindelser eller begge dele på samme tid. Du kan også konfigurere CDN at springe konfigurationen af standardindrindelse over, når du aktiverer den. Du kan altid tilføje disse oprindelser senere som beskrevet i dette emne.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Hvis du f.eks. vil aktivere din organisations adgang til at bruge både offentlige og private oprindelser, skal du indtaste følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Hvis du vil aktivere din organisations adgang til at bruge både offentlige og private oprindelser, men springe konfigurationen af standardindrindelse over, skal du skrive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Se [Standard-CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for at få oplysninger om de oprindelser, der er klargjort som standard, når du aktiverer Office 365 CDN, og den potentielle virkning af at springe installationen af standardindrindelse over.

Hvis du vil aktivere din organisations adgang til at bruge offentlige oprindelser, skal du indtaste følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Hvis du vil aktivere din organisations adgang til at bruge private oprindelser, skal du indtaste følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Du kan finde flere oplysninger om denne cmdlet under [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Rediger listen over filtyper, der skal medtages i Office 365 CDN (valgfrit)

> [!TIP]
> Når du definerer filtyper ved hjælp af **Set-PnPTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil føje yderligere filtyper til listen, skal du først bruge cmdlet'en til at finde ud af, hvilke filtyper der allerede er tilladte og medtage dem på listen sammen med de nye.

Brug **Set-PnPTenantCdnPolicy-cmdlet'en** til at definere statiske filtyper, der kan hostes af offentlige og private oprindelser i CDN. Som standard er almindelige aktivtyper tilladt, f.eks. .css, .gif, .jpg og .js.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Hvis du f.eks. vil CDN vært for .css og .png-filer, skal du indtaste kommandoen:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Hvis du vil se, hvilke filtyper der aktuelt tillades af CDN, skal du bruge **Get-PnPTenantCdnPolicies-cmdlet'en**:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Du kan finde flere oplysninger om disse cmdlet'er under [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) og [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Rediger listen over webstedsklassificeringer, du vil udelade fra Office 365 CDN (valgfrit)

> [!TIP]
> Når du udelader webstedsklassificeringer ved hjælp af **Set-PnPTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere webstedsklassificeringer, skal du først bruge cmdlet'en til at finde ud af, hvilke klassificeringer der allerede er udeladt, og derefter tilføje dem sammen med de nye.

Brug **set-PnPTenantCdnPolicy-cmdlet'en** til at udelade webstedsklassificeringer, du ikke vil gøre tilgængelige via CDN. Som standard er ingen webstedsklassificeringer udeladt.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Hvis du vil se, hvilke webstedsklassificeringer der i øjeblikket er begrænset, skal du bruge **Get-PnPTenantCdnPolicies-cmdlet'en** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

De egenskaber, der skal returneres, er _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ og _ExcludeIfNoScriptDisabled_.

Egenskaben _IncludeFileExtensions_ indeholder listen over filtypenavne, der skal betjenes fra CDN.

> [!NOTE]
> Standardfiludvidelserne er forskellige fra offentlige til private.

Egenskaben _ExcludeRestrictedSiteClassifications_ indeholder de webstedsklassificeringer, du vil udelukke fra CDN. Du kan f.eks. udelade websteder,  der er markeret som fortrolige, så indhold fra websteder med den pågældende klassificering ikke kommer fra CDN.

Egenskaben _ExcludeIfNoScriptDisabled_ udelukker indhold fra CDN baseret på _noScript-attributindstillingerne på_ webstedsniveau. _NoScript-attributten er som_ standard angivet til **Aktiveret** for _moderne_ websteder og **Deaktiveret** for _klassiske_ websteder. Dette afhænger af dine lejerindstillinger.

Du kan finde flere oplysninger om disse cmdlet'er under [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) og [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Tilføj en oprindelse for aktiverne

Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere en oprindelse. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint-bibliotek eller en mappe, der indeholder de aktiver, der skal være hostet af CDN.

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som betragtes som følsomme for din organisation, i en offentlig oprindelse.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Værdien af stien _er_ den relative sti til det bibliotek eller den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier. Origins understøtter jokertegn, der er afhængige af URL-adressen. Dette giver dig mulighed for at oprette oprindelser, der strækker sig over flere websteder. Hvis du f.eks. vil medtage alle aktiverne i hovedsidemappen for alle dine websteder som en offentlig oprindelse i CDN, skal du skrive følgende kommando:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Jokertegnsmodifikatoren ***/** kan kun bruges i starten af stien og matcher alle URL-segmenter under den angivne URL-adresse.
+ Stien kan pege på et dokumentbibliotek, en mappe eller et websted. Stien _*/websted1 matcher f.eks_ . alle dokumentbiblioteker under webstedet.

Du kan tilføje en oprindelse med en bestemt relativ sti. Du kan ikke tilføje en oprindelse ved hjælp af den fulde sti.

I dette eksempel tilføjes en privat oprindelse for webstedsaktiversbiblioteket på et bestemt websted:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

I dette eksempel tilføjes en privat oprindelse _af mappen mappe1_ i gruppen af websteders bibliotek over webstedsaktiver:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Hvis der er et mellemrum i stien, kan du enten omslutte stien med dobbelte anførselstegn eller erstatte mellemrummet med URL-adressen, der kodningen %20. Følgende eksempler tilføjer en privat oprindelse af mappen _mappe 1_ i gruppen af websteders bibliotek over webstedsaktiver:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Du kan finde flere oplysninger om denne kommando og dens syntaks i [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> I private oprindelser skal aktiver, der deles fra en oprindelse, have en overordnede version publiceret, før de kan åbnes fra CDN.

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Eksempel: Konfigurer en offentlig oprindelse for dine mastersider og dit typografibibliotek til SharePoint Online

Normalt er disse oprindelser konfigureret for dig som standard, når du aktiverer Office 365 CDN. Men hvis du vil aktivere dem manuelt, skal du følge disse trin.

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere typografibiblioteket som en offentlig oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mastersiderne som en offentlig oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Du kan finde flere oplysninger om denne kommando og dens syntaks i [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Eksempel: Konfigurer en privat oprindelse for webstedsaktiver, webstedssider og publiceringsbilleder for SharePoint Online

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedsaktiver som en privat oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedssider som en privat oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med publiceringsbilleder som en privat oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Du kan finde flere oplysninger om denne kommando og dens syntaks i [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Det kan tage op til 15 minutter.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Eksempel: Konfigurer en privat oprindelse for en gruppe af websteder for SharePoint Online

Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere en gruppe af websteder som en privat oprindelse. Eksempel:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Du kan finde flere oplysninger om denne kommando og dens syntaks i [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Du får muligvis vist _meddelelsen Konfiguration afventer_, som forventes, når SharePoint Online-lejeren opretter forbindelse til CDN-tjenesten. Det kan tage op til 15 minutter.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Administrer Office 365 CDN

Når du har konfigureret CDN, kan du foretage ændringer i konfigurationen, efterhånden som du opdaterer indholdet, eller dine behov ændres, som beskrevet i dette afsnit.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Tilføje, opdatere eller fjerne aktiver fra Office 365 CDN

Når du har gennemført konfigurationstrinnene, kan du tilføje nye aktiver og opdatere eller fjerne eksisterende aktiver, når du ønsker det. Du skal blot foretage dine ændringer af aktiverne i den mappe eller det SharePoint, du har identificeret som en oprindelse. Hvis du tilføjer et nyt aktiv, er det straks tilgængeligt via CDN. Men hvis du opdaterer aktivet, tager det op til 15 minutter, før den nye kopi er overført og tilgængelig i CDN.

Hvis du skal hente placeringen af oprindelsen, kan du bruge **Get-PnPTenantCdnOrigin-cmdlet'en** . Du kan finde oplysninger om, hvordan du bruger denne cmdlet under [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Fjerne en oprindelse fra Office 365 CDN

Du kan fjerne adgangen til en mappe eller et SharePoint, du har identificeret som en oprindelse. For at gøre dette skal du **bruge Remove-PnPTenantCdnOrigin-cmdlet'en** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Du kan finde oplysninger om, hvordan du bruger denne cmdlet under [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Rediger en oprindelse i Office 365 CDN

Du kan ikke ændre en oprindelse, du har oprettet. I stedet skal du fjerne oprindelsen og derefter tilføje en ny. Du kan finde flere oplysninger [i Fjerne en oprindelse fra Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) og [Tilføje en oprindelse for dine aktiver](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Brug **Set-PnPTenantCdnEnabled-cmdlet'en** til at deaktivere CDN for organisationen. Hvis du har både de offentlige og private oprindelser aktiveret for CDN, skal du køre cmdlet'en to gange, som vist i følgende eksempler.

Hvis du vil deaktivere brugen af offentlige oprindelser i CDN, skal du indtaste følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Hvis du vil deaktivere brugen af private oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Du kan finde flere oplysninger om denne cmdlet under [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Konfigurere og konfigurere Office 365 CDN ved hjælp af CLI for Microsoft 365

Fremgangsmåderne i dette afsnit kræver, at du har installeret [CLI for Microsoft 365](https://aka.ms/cli-m365). Opret derefter forbindelse til din Office 365 lejer ved hjælp af [kommandoen logon](https://pnp.github.io/cli-microsoft365/cmd/login/).

Fuldfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp af CLI for Microsoft 365.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-the-office-365-cdn"></a>Aktivér Office 365 CDN

Du kan administrere tilstanden for lejerens Office 365 CDN ved hjælp af kommandoen [spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

For at aktivere Office 365 offentlige CDN din lejer skal du udføre:

```cli
spo cdn set --type Public --enabled true
```

For at aktivere Office 365 SharePoint CDN skal du udføre:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Få vist den aktuelle status for Office 365 CDN

Hvis du vil kontrollere, om den bestemte type Office 365 CDN er aktiveret eller deaktiveret, skal du bruge [kommandoen hent spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

Du kan kontrollere, Office 365 offentlig CDN er aktiveret, ved at udføre:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Få vist Office 365 CDN oprindelser

Sådan får du vist de aktuelt konfigurerede Office 365 offentlige CDN oprindelser:

```cli
spo cdn origin list --type Public
```

Se [Standard CDN for oplysninger](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) om de oprindelser, der er klargjort som standard, når du aktiverer Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Tilføj en Office 365 CDN oprindelse

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der betragtes som følsomme for din organisation, i SharePoint dokumentbibliotek, der er konfigureret som en offentlig oprindelse.

Brug [kommandoen spo cdn origin add](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) til at definere en CDN oprindelse. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint-bibliotek eller en mappe, der indeholder de aktiver, der skal være hostet af CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Hvor `path` er den relative sti til den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier.

Hvis du vil medtage alle aktiver i **mastersidegalleriet** for alle websteder som en offentlig oprindelse, skal du udføre:

```cli
spo cdn origin add --type Public --origin */masterpage
```

For at konfigurere en privat oprindelse for en bestemt gruppe af websteder skal du køre:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Når du har CDN en oprindelse, kan det tage op til 15 minutter, før du kan hente filer via CDN-tjenesten. Du kan kontrollere, om den bestemte oprindelse allerede er blevet aktiveret ved hjælp af [kommandoen spo cdn origin list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) .

### <a name="remove-an-office-365-cdn-origin"></a>Fjern en Office 365 CDN oprindelse

Brug [kommandoen fjern for spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) til at fjerne en CDN oprindelse for den angivne CDN type.

Hvis du vil fjerne en offentlig oprindelse fra konfigurationen CDN, skal du udføre:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Fjernelse af en CDN oprindelse påvirker ikke de filer, der er gemt i et dokumentbibliotek, der matcher den pågældende oprindelse. Hvis der refereres til disse aktiver ved hjælp SharePoint URL-adressen, SharePoint automatisk tilbage til den oprindelige URL-adresse, der peger på dokumentbiblioteket. Men hvis der refereres til aktiver ved hjælp af en offentlig CDN URL-adressen, brydes linket, hvis du fjerner oprindelsen, og du skal ændre dem manuelt.

### <a name="modify-an-office-365-cdn-origin"></a>Rediger en Office 365 CDN oprindelse

Det er ikke muligt at ændre en eksisterende CDN oprindelse. I stedet skal du fjerne de tidligere definerede CDN ved hjælp af kommandoen `spo cdn origin remove` og tilføje en ny ved hjælp af `spo cdn origin add` kommandoen.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Rediger de filtyper, der skal medtages i Office 365 CDN

Som standard er følgende filtyper inkluderet i CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff og .woff2_. Hvis du har brug for at medtage yderligere filtyper i CDN, kan du ændre CDN konfigurationen ved hjælp af kommandoen [spo cdn-politiksæt](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Når du ændrer listen over filtyper, overskriver du den aktuelt definerede liste. Hvis du vil medtage flere filtyper, skal du først bruge [kommandoen til spo cdn-politikliste](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) for at finde ud af, hvilke filtyper der aktuelt er konfigureret.

For at føje _JSON-filtypen_ til standardlisten over filtyper, der findes i den offentlige CDN, skal du udføre:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Rediger listen over webstedsklassificeringer, du vil udelade fra Office 365 CDN

Brug kommandoen [spo cdn-politiksæt](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) til at udelade webstedsklassificeringer, du ikke vil gøre tilgængelige via CDN. Som standard er ingen webstedsklassificeringer udeladt.

> [!NOTE]
> Når du ændrer listen over webstedsklassificeringer, der er udeladt, overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere klassificeringer, skal du først bruge [SPO CDN-politiklistekommandoen](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) for at finde ud af, hvilke klassificeringer der aktuelt er konfigureret.

Hvis du vil udelade websteder, _der er klassificeret som HBI_ CDN, skal du udføre

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Hvis du vil deaktivere Office 365 CDN bruge kommandoen`spo cdn set`, f.eks.:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Brug af dine CDN aktiver

Nu hvor du har aktiveret CDN og konfigurerede oprindelser og politikker, kan du begynde at bruge CDN aktiver.

Dette afsnit hjælper dig med at forstå, hvordan du bruger CDN-webadresser på dine SharePoint-sider og -indhold, så SharePoint omdirigerer anmodninger om aktiver i både offentlige og private oprindelser til CDN.

+ [Opdatere kæder CDN aktiver](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Brug af aktiver i offentlige oprindelser](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Brug af aktiver i private oprindelser](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Hvis du vil have mere at vide om, hvordan du bruger CDN til at hoste webdele på klientsiden, skal du se emnet Vær vært for webdelen på klientsiden [fra Office 365 CDN (Hello World part 4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

> [!NOTE]
> Hvis du føjer _mappen ClientSideAssets_ til den **private** liste CDN oprindelser, kan CDN-hostede brugerdefinerede webdele ikke gengives. Filer, der bruges af SPFX-webdele, kan kun bruge offentlige CDN og mappen ClientSideAssets er en standardindrindelse for offentlige CDN.

### <a name="updating-links-to-cdn-assets"></a>Opdatere kæder CDN aktiver

Hvis du vil bruge aktiver, du har føjet til en oprindelse, skal du blot opdatere links til den oprindelige fil med stien til filen i oprindelsen.

+ Rediger den side eller det indhold, der indeholder links til aktiver, du har føjet til en oprindelse. Du kan også bruge en af flere metoder til at søge og erstatte links globalt på tværs af et enter-websted eller en gruppe af websteder, hvis du vil opdatere linket til et bestemt aktiv overalt, hvor det vises.
+ For hvert link til et aktiv i en oprindelse skal du erstatte stien med stien til filen i CDN oprindelse. Du kan bruge relative stier.
+ Gem siden eller indholdet.

Overvej f.eks. billedet _/site/SiteAssets/images/image.png_, som du har kopieret til dokumentbiblioteksmappen _/site/CDN_origins/public/_. Hvis du vil bruge CDN-aktivet, skal du erstatte den oprindelige sti til billedfilplaceringen med stien til oprindelsen for at lave den nye URL-adresse _/site/CDN_origins/public/image.png_.

Hvis du vil bruge den fulde URL-adresse til aktivet i stedet for en relativ sti, skal du oprette linket således:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Generelt skal du ikke hardcode URL-adresser direkte til aktiver i CDN. Du kan dog oprette URL-adresser for aktiver i offentlige oprindelser manuelt, hvis det er nødvendigt. Få mere at vide under [Hardcoding CDN URL-adresser for offentlige aktiver](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Hvis du vil vide mere om, hvordan du bekræfter, at aktiverne betjenes fra CDN, skal du se Hvordan kan jeg bekræfte, at aktiverne betjenes af [CDN?](use-microsoft-365-cdn-with-spo.md#CDNConfirm) [i Fejlfinding af Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

### <a name="using-assets-in-public-origins"></a>Brug af aktiver i offentlige oprindelser

Publiceringsfunktionen i SharePoint Online omskriver automatisk URL-adresser for aktiver, der er gemt i offentlige oprindelser, til deres tilsvarende CDN, så aktiverne serveres fra CDN-tjenesten i stedet for SharePoint.

Hvis din oprindelse ligger på et websted med funktionen Publicering aktiveret, og de aktiver, du vil aflaste på CDN, er i en af følgende kategorier, vil SharePoint automatisk omskrive URL-adresser for aktiver i oprindelsen, hvis aktivet ikke er blevet udelukket af en CDN-politik.

Følgende er en oversigt over, hvilke links der automatisk omskrives af SharePoint Publicering:

+ IMG/LINK/CSS URL-adresser i klassisk udgivelsesside HTML-svar
  + Dette omfatter billeder, der er tilføjet af forfattere i HTML-indholdet på en side
+ URL-adresser for webdelen Slideshow i billedbibliotek
+ Billedfelter i resultater af SPList REST API (RenderListDataAsStream)
  + Brug den nye egenskab _ImageFieldsToTryRewriteToCdnUrls_ til at oprette en kommasepareret liste over felter
  + Understøtter hyperlinkfelter og udgivelsesfelter
+ SharePoint af billedgengivelser

Følgende diagram illustrerer arbejdsprocessen, når SharePoint modtager en anmodning om en side, der indeholder aktiver fra en offentlig oprindelse.

![Arbejdsprocesdiagram: Henter Office 365 CDN fra en offentlig oprindelse.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Arbejdsproces: Henter Office 365 CDN aktiver fra en offentlig oprindelse")

> [!TIP]
> Hvis du vil deaktivere automatisk omskrivning for bestemte URL-adresser på en side, kan du tjekke siden ud og tilføje forespørgselsstrengparameteren **? NoAutoReWrites=true** til slutningen af hvert link, du vil deaktivere.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Opbygning CDN URL-adresser for offentlige aktiver

Hvis publiceringsfunktionen ikke er aktiveret for en offentlig oprindelse, eller aktivet ikke er en af de linktyper, der understøttes af funktionen til automatisk omskrivning af CDN-tjenesten, kan du oprette URL-adresser manuelt på aktivernes CDN-placering og bruge disse URL-adresser i dit indhold.

> [!NOTE]
> Du kan ikke afkode eller konstruere CDN URL-adresser til aktiver i en privat oprindelse, fordi den nødvendige adgangstoken, der danner den sidste del af URL-adressen, genereres på det tidspunkt, hvor ressourcen anmodes om. Du kan konstruere URL-adressen til offentlige CDN og URL-adressen skal ikke være hard coded, da den er underlagt ændringer.

For offentlige CDN, ser URL-formatet således ud:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**Erstat TenantHostName** med dit lejernavn. Eksempel:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> Egenskaben sidekontekst skal bruges til at konstruere præfikset i stedet for hard coding "https://publiccdn.sharepointonline.com". URL-adressen kan ændres uden ændringer og bør ikke være hard coded. Hvis du bruger visningsskabeloner med klassisk SharePoint Online, kan du bruge egenskaben "window._spPageContextInfo.publicCdnBaseUrl" i visningsskabelonen til præfikset af URL-adressen. Hvis du er SPFx webdele til moderne og klassisk SharePoint kan du bruge egenskaben "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". Dette giver præfikset, så hvis det ændres, opdateres implementeringen med det. Som et eksempel på SPFx kan URL-adressen konstrueres ved hjælp af egenskaben "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL for elementet". Se Brug [af CDN i kode på klientsiden,](https://youtu.be/IH1RbQlbhIA) som er en del af [performanceserien for sæson 1](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Brug af aktiver i private oprindelser

Der kræves ingen yderligere konfiguration for at bruge aktiver i private oprindelser. SharePoint Online omskriver automatisk URL-adresser for aktiver i private oprindelser, så anmodninger om disse aktiver altid vil blive serveret fra CDN. Du kan ikke oprette URL-adresser manuelt til CDN-aktiver i private oprindelser, fordi disse URL-adresser indeholder tokens, der skal genereres automatisk af SharePoint Online på det tidspunkt, hvor aktivet anmodes om det.

Adgang til aktiver i private oprindelser er beskyttet af dynamisk genererede tokens baseret på brugertilladelser til oprindelsen med de advarselsforanstaltninger, der er beskrevet i de følgende afsnit. Brugere skal som minimum have **læseadgang** til oprindelserne for at CDN gengive indhold.

Følgende diagram illustrerer arbejdsprocessen, når SharePoint modtager en anmodning om en side, der indeholder aktiver fra en privat oprindelse.

![Arbejdsprocesdiagram: Henter Office 365 CDN fra en privat oprindelse.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Arbejdsproces: Henter Office 365 CDN aktiver fra en privat oprindelse")

#### <a name="token-based-authorization-in-private-origins"></a>Token-baseret godkendelse i private oprindelser

Adgang til aktiver i private oprindelser i Office 365 CDN ydes ved hjælp af tokens, der genereres af SharePoint Online. Brugere, der allerede har tilladelse til at få adgang til mappen eller biblioteket angivet af oprindelsen, får automatisk tildelt tokens, der giver brugeren mulighed for at få adgang til filen baseret på deres tilladelsesniveau. Disse adgangstokens er gyldige i 30 til 90 minutter, efter de er genereret, for at forhindre genafspilning af token-angreb.

Når adgangstokenet genereres, returnerer SharePoint Online en brugerdefineret URI til klienten, der indeholder to godkendelsesparametre _æder (_ godkendelsestokenet for kanten) og _oat_ (godkendelsestoken for oprindelse). Strukturen af hvert token _< udløbstidspunkt i epoketidsformatet >__< sikre signaturs >_. Eksempel:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Alle, der har adgang til tokenet, kan få adgang til ressourcen CDN. Men URL-adresser, der indeholder disse adgangstokens, deles kun via HTTPS, så medmindre URL-adressen udtrykkeligt deles af en slutbruger, før tokenet udløber, vil aktivet ikke være tilgængeligt for uautoriserede brugere.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Tilladelser på elementniveau understøttes ikke for aktiver i private oprindelser

Det er vigtigt at bemærke, SharePoint Online ikke understøtter tilladelser på elementniveau for aktiver i private oprindelser. Eksempelvis har brugerne i en fil, der er `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`placeret på , effektiv adgang til filen under følgende betingelser:

|Bruger  |Tilladelser  |Effektiv adgang  |
|---------|---------|---------|
|Bruger 1     |Har adgang til mappe1         |Kan få image1.jpg adgang fra CDN         |
|Bruger 2     |Har ikke adgang til mappe1         |Kan ikke image1.jpg adgang fra CDN         |
|Bruger 3     |Har ikke adgang til mappe1, men tildeles udtrykkelig tilladelse til at tilgå image1.jpg i SharePoint Online         |Kan få adgang til image1.jpg direkte fra SharePoint Online, men ikke fra CDN         |
|Bruger 4     |Har adgang til mappe1, men er udtrykkeligt blevet nægtet adgang til image1.jpg i SharePoint Online         |Aktivet kan ikke tilgås fra SharePoint Online, men kan få adgang til aktivet fra CDN på trods af nægtet adgang til filen i SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Fejlfinding af Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Hvordan kan jeg bekræfte, at aktiverne betjenes af CDN?

Når du har føjet links til CDN-aktiver til en side, kan du bekræfte, at aktivet modtages fra CDN ved at gå til siden og højreklikke på billedet, når det er gengivet, og gennemse billedets URL-adresse.

Du kan også bruge udviklerværktøjerne i din browser til at få vist URL-adressen for hvert aktiv på en side, eller du kan bruge et tredjepartsnetværkssporingsværktøj.

> [!NOTE]
> Hvis du bruger et netværksværktøj som f.eks. Fiddler til at teste aktiverne uden for gengivelse af aktivet fra en SharePoint-side, skal du manuelt tilføje refererhovedet "Referer: `https://yourdomain.sharepoint.com`" til ANMODNINGEN, hvor URL-adressen er rod-URL-adressen for din SharePoint Online-lejer.

Du kan ikke CDN URL-adresser direkte i en webbrowser, fordi der skal være en referer, der kommer fra SharePoint Online. Men hvis du føjer URL-adressen til CDN-aktiver til en SharePoint-side og derefter åbner siden i en browser, vises det CDN-aktiv, der gengives på siden.

Du kan finde flere oplysninger om brug af udviklerværktøjer i Microsoft Edge under [Microsoft Edge Udviklerværktøjer](/microsoft-edge/devtools-guide).

Hvis du vil se en kort video, der hostes på [YouTube-kanalen SharePoint Developer Patterns and Practices](https://aka.ms/sppnp-videos), der viser, hvordan du bekræfter, at din CDN fungerer, skal du se Bekræfte din CDN-brug og sikre [optimal netværksforbindelse](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Hvorfor er aktiver fra en ny oprindelse ikke tilgængelige?
Aktiver i nye oprindelser er ikke umiddelbart tilgængelige til brug, da det tager tid, før registreringen er overført via CDN, og før aktiverne kan uploades fra oprindelsen til CDN lagerplads. Den tid, det kræves, at aktiverne er tilgængelige i CDN, afhænger af, hvor mange aktiver og filstørrelser der er.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Min webdel på klientsiden eller SharePoint Framework-løsning fungerer ikke

Når du aktiverer Office 365 CDN for offentlige oprindelser, opretter CDN automatisk disse standardindrindelse:

+ */MASTERPAGE
+ */TYPOGRAFIBIBLIOTEK
+ */CLIENTSIDEASSETS

Hvis */clientsideassets-oprindelsen mangler, vil SharePoint Framework fejlløsninger, og der genereres ingen advarsel eller fejlmeddelelser. Denne oprindelse mangler muligvis, enten fordi CDN blev aktiveret med parameteren _-NoDefaultOrigins_ angivet til **$true**, eller fordi oprindelsen blev slettet manuelt.

Du kan kontrollere, hvilke oprindelser der findes med følgende PowerShell-kommando:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Eller du kan kontrollere Office 365 CLI:

```cli
spo cdn origin list
```

Tilføj oprindelsen i PowerShell:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Tilføj oprindelsen i Office 365 CLI:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Hvilke PowerShell-moduler og CLI-shells skal jeg bruge for at arbejde med Office 365 CDN?

Du kan vælge at arbejde med Office 365 CDN enten ved hjælp **af SharePoint Online Management Shell** PowerShell-modulet **eller Office 365 CLI**.

+ [Introduktion til SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Installation af Office 365 CLI](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Se også

[Content Delivery Networks](./content-delivery-networks.md)

[Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md)

[SharePoint Ydeevneserie – Office 365 CDN videoserie](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
