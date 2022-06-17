---
title: Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du bruger Office 365 Content Delivery Network (CDN) til at fremskynde leveringen af dine SharePoint Online-aktiver.
ms.openlocfilehash: 8b106840133f5c690fd0df80700fdb79a3590d92
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139557"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Brug Office 365 Content Delivery Network (CDN) sammen med SharePoint Online

Du kan bruge de indbyggede Office 365 Content Delivery Network (CDN) til at hoste statiske aktiver for at opnå en bedre ydeevne for dine SharePoint Online-sider. Den Office 365 CDN forbedrer ydeevnen ved at cachelagring af statiske aktiver tættere på de browsere, der anmoder om dem, hvilket hjælper med at fremskynde downloads og reducere ventetiden. Office 365 CDN bruger også [HTTP/2-protokollen](https://en.wikipedia.org/wiki/HTTP/2) til forbedret komprimering og HTTP-pipelining. Office 365 CDN-tjenesten er inkluderet som en del af dit SharePoint Online-abonnement.

> [!NOTE]
> Den Office 365 CDN er kun tilgængelig for lejere i **produktionsskyen** (verden over). Lejere i cloudmiljøet US Government, Kina og Tyskland understøtter i øjeblikket ikke Office 365 CDN.

Den Office 365 CDN består af flere CDN'er, der giver dig mulighed for at hoste statiske aktiver på flere placeringer eller _oprindelser_ og betjene dem fra globale netværk med høj hastighed. Afhængigt af den type indhold, du vil hoste i Office 365 CDN, kan du tilføje **offentlige** oprindelser, **private** oprindelser eller begge dele. [Se Vælg, om hvert oprindelsessted skal være offentligt eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate), for at få flere oplysninger om forskellen mellem offentlig og privat oprindelse.

![Office 365 CDN konceptuelt diagram.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN konceptuelt diagram")

Hvis du allerede er bekendt med den måde, som CDN'er fungerer på, skal du kun udføre nogle få trin for at aktivere Office 365 CDN for din lejer. I dette emne beskrives, hvordan. Læs videre for at få oplysninger om, hvordan du kommer i gang med at hoste dine statiske aktiver.

> [!TIP]
> Der er andre Microsoft-hostede CDN'er, der kan bruges sammen med Office 365 til specialiserede brugsscenarier, men som ikke er beskrevet i dette emne, fordi de falder uden for Office 365 CDN område. Du kan få flere oplysninger under [Andre Microsoft CDN'er](content-delivery-networks.md#other-microsoft-cdns).

 **Gå tilbage til [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Oversigt over at arbejde med Office 365 CDN i SharePoint Online

Hvis du vil konfigurere Office 365 CDN for din organisation, skal du følge disse grundlæggende trin:

+ [Plan for udrulning af Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Find ud af, hvilke statiske aktiver du vil hoste på CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Find ud af, hvor du vil gemme dine aktiver](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Denne placering kan være et SharePoint websted, bibliotek eller mappe og kaldes et _oprindelsessted_.
  + [Vælg, om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Du kan tilføje flere oprindelser for både offentlige og private typer.

+ Konfigurer og konfigurer CDN ved hjælp af enten PowerShell eller kommandolinjegrænsefladen til Microsoft 365

  + [Konfigurer og konfigurer CDN ved hjælp af SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Konfigurer og konfigurer CDN ved hjælp af PnP PowerShell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Konfigurer og konfigurer CDN ved hjælp af kommandolinjegrænsefladen for Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Når du har fuldført dette trin, har du:

  + Aktiverede CDN for din organisation.
  + Du har tilføjet dine oprindelser og identificeret hver oprindelse som offentlig eller privat.

Når du er færdig med konfigurationen, kan du [administrere Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) over tid ved at:

+ Tilføjelse, opdatering og fjernelse af aktiver
+ Tilføjelse og fjernelse af oprindelser
+ Konfiguration af CDN politikker
+ Hvis det er nødvendigt, kan du deaktivere CDN

Endelig kan [du se Brug af dine CDN-aktiver](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) til at få mere at vide om adgang til dine CDN aktiver fra både offentlige og private oprindelser.

Se [Fejlfinding af Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) for at få hjælp til at løse almindelige problemer.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Plan for udrulning af Office 365 CDN

Før du udruller Office 365 CDN til din Office 365 lejer, skal du overveje følgende faktorer som en del af din planlægningsproces.

  + [Find ud af, hvilke statiske aktiver du vil hoste på CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Find ud af, hvor du vil gemme dine aktiver](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Vælg, om hver oprindelse skal være offentlig eller privat](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Find ud af, hvilke statiske aktiver du vil hoste på CDN

CDN'er er generelt mest effektive til hosting af _statiske aktiver_ eller aktiver, der ikke ændres særlig ofte. En god tommelfingerregel er at identificere filer, der opfylder nogle eller alle disse betingelser:

+ Statiske filer, der er integreret på en side (f.eks. scripts og billeder), som kan have en betydelig trinvis indvirkning på indlæsningstider for sider
+ Store filer som eksekverbare filer og installationsfiler
+ Ressourcebiblioteker, der understøtter kode på klientsiden

For eksempel kan små filer, der gentagne gange anmodes om, f.eks. webstedsbilleder og scripts, forbedre ydeevnen for gengivelse af websteder markant og gradvist reducere belastningen på dine SharePoint Online-websteder, når du føjer dem til et CDN oprindelse. Større filer, f.eks. eks. eksekverbare installationsfiler, kan downloades fra CDN, og det giver en positiv påvirkning af ydeevnen og en efterfølgende reduktion af belastningen på dit SharePoint Online-websted, selvom der ikke er adgang til dem så ofte.

Forbedring af ydeevnen pr. fil afhænger af mange faktorer, herunder klientens nærhed til det nærmeste CDN slutpunkt, midlertidige forhold på det lokale netværk osv. Mange statiske filer er ret små og kan downloades fra Office 365 på mindre end et sekund. En webside kan dog indeholde mange integrerede filer med en samlet downloadtid på flere sekunder. Servering af disse filer fra CDN kan reducere den samlede indlæsningstid for sider markant. Se [F.eks. Hvilke ydeevnegevinster giver en CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Find ud af, hvor du vil gemme dine aktiver

CDN henter dine aktiver fra en placering, der kaldes en _oprindelse_. Et oprindelsessted kan være et SharePoint websted, et dokumentbibliotek eller en mappe, der er tilgængelig for en URL-adresse. Du har stor fleksibilitet, når du angiver oprindelser for din organisation. Du kan f.eks. angive flere oprindelser eller et enkelt oprindelsessted, hvor du vil placere alle dine CDN aktiver. Du kan vælge at have både offentlig eller privat oprindelse for din organisation. De fleste organisationer vælger at implementere en kombination af de to.

Du kan oprette en ny objektbeholder til dine oprindelser, f.eks. mapper eller dokumentbiblioteker, og tilføje filer, du vil gøre tilgængelige fra CDN. Dette er en god fremgangsmåde, hvis du har et bestemt sæt aktiver, du vil være tilgængelig fra CDN, og du vil begrænse sættet af CDN aktiver til kun disse filer i objektbeholderen.

Du kan også konfigurere en eksisterende gruppe af websteder, et websted, et bibliotek eller en mappe som udgangspunkt, hvilket gør alle berettigede aktiver i objektbeholderen tilgængelige fra CDN. Før du tilføjer en eksisterende objektbeholder som oprindelse, er det vigtigt at sikre, at du er opmærksom på dens indhold og tilladelser, så du ikke utilsigtet eksponerer aktiver for anonym adgang eller uautoriserede brugere.

Du kan definere _CDN politikker_ for at udelade indhold i dine oprindelser fra CDN. CDN politikker ekskluderer aktiver i offentlige eller private oprindelser efter attributter, f.eks _. filtype_ og _webstedsklassificering_, og anvendes på alle oprindelser for den CdnType (privat eller offentlig), du angiver i politikken. Hvis du f.eks. tilføjer et privat oprindelsessted, der består af et websted, der indeholder flere underordnede websteder, kan du definere en politik, der udelukker websteder, der er markeret som **Fortrolige,** så indhold fra websteder, hvor klassificeringen er anvendt, ikke håndteres fra CDN. Politikken gælder for indhold fra _alle_ private oprindelser, du har føjet til CDN.

Vær opmærksom på, at jo større antallet af oprindelser er, jo større indflydelse har det på den tid, det tager CDN tjenesten at behandle anmodninger. Vi anbefaler, at du begrænser antallet af oprindelser så meget som muligt.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Vælg, om hver oprindelse skal være offentlig eller privat

Når du identificerer en oprindelse, angiver du, om den skal gøres _offentlig_ eller _privat_. Adgang til CDN aktiver i det offentlige rum er anonymt, og CDN indhold i privat oprindelse sikres af dynamisk genererede tokens for at øge sikkerheden. Uanset hvilken mulighed du vælger, udfører Microsoft alt det tunge arbejde for dig, når det kommer til administration af selve CDN. Du kan også ændre mening senere, når du har konfigureret CDN og identificeret din oprindelse.

Både offentlige og private indstillinger giver lignende ydeevnegevinster, men de har hver især unikke attributter og fordele.

**Offentlige** oprindelser i Office 365 CDN er tilgængelige anonymt, og hostede aktiver kan tilgås af alle, der har URL-adressen til aktivet. Da adgang til indhold med offentlig oprindelse er anonym, bør du kun bruge dem til at cachelagre ikke-følsomt generisk indhold, f.eks. JavaScript-filer, scripts, ikoner og billeder.

**Private** oprindelser i Office 365 CDN give privat adgang til brugerindhold, f.eks. SharePoint Online-dokumentbiblioteker, websteder og beskyttede billeder. Adgang til indhold i private oprindelser sikres af dynamisk genererede tokens, så brugere med tilladelser kun kan få adgang til det oprindelige dokumentbibliotek eller den oprindelige lagerplacering. Private oprindelser i Office 365 CDN kan kun bruges til SharePoint onlineindhold, og du kan kun få adgang til aktiver med privat oprindelse via omdirigering fra din SharePoint Online-lejer.

Du kan læse mere om, hvordan CDN adgang til aktiver i et privat oprindelse fungerer i [Brug af aktiver i private oprindelser](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attributter og fordele ved at hoste aktiver i offentlig oprindelse

+ Aktiver, der eksponeres i et offentligt rum, er anonyme tilgængelige for alle.
    > [!IMPORTANT]
    > Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som anses for at være følsomme over for din organisation i et offentligt miljø.

+ Hvis du fjerner et aktiv fra en offentlig oprindelse, kan aktivet fortsat være tilgængeligt i op til 30 dage fra cachen. Vi vil dog gøre links til aktivet ugyldige i CDN inden for 15 minutter.

+ Når du hoster typografiark (CSS-filer) i en offentlig oprindelse, kan du bruge relative stier og URI'er i koden. Det betyder, at du kan referere til placeringen af baggrundsbilleder og andre objekter i forhold til placeringen af det aktiv, der kalder det.

+ Selvom du kan konstruere URL-adressen for en offentlig oprindelse, skal du være forsigtig og sikre, at du bruger egenskaben sidekontekst og følger vejledningen til at gøre det. Årsagen til dette er, at hvis adgang til CDN bliver utilgængelig, vil URL-adressen ikke automatisk blive fortolket til din organisation i SharePoint Online og kan resultere i brudte links og andre fejl. URL-adressen kan også ændres, hvilket er grunden til, at den ikke kun skal være hardcoded til dens aktuelle værdi.

+ Standardfiltyperne for offentlige oprindelser er .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff og .woff2. Du kan angive flere filtyper.

+ Du kan konfigurere en politik til at udelade aktiver, der er identificeret af webstedsklassifikationer, som du angiver. Du kan f.eks. vælge at udelade alle aktiver, der er markeret som "fortrolige" eller "begrænsede", selvom de er en tilladt filtype og er placeret i en offentlig oprindelse.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attributter og fordele ved at hoste aktiver i privat oprindelse

+ Private oprindelser kan kun bruges til SharePoint Online-aktiver.

+ Brugerne kan kun få adgang til aktiverne fra et privat udgangspunkt, hvis de har tilladelse til at få adgang til objektbeholderen. Anonym adgang til disse aktiver forhindres.

+ Der skal henvises til aktiver med privat oprindelse fra lejeren SharePoint Online. Direkte adgang til private CDN aktiver fungerer ikke.

+ Hvis du fjerner et aktiv fra det private udgangspunkt, kan aktivet fortsat være tilgængeligt i op til en time fra cachen. Vi vil dog ugyldiggøre links til aktivet i CDN inden for 15 minutter efter aktivets fjernelse.

+ De standardfiltyper, der er inkluderet til private oprindelser, er .gif, .ico, .jpeg, .jpg, .js og .png. Du kan angive flere filtyper.

+ På samme måde som med offentlige oprindelser kan du konfigurere en politik til at udelade aktiver, der er identificeret af webstedsklassifikationer, som du angiver, selvom du bruger jokertegn til at inkludere alle aktiver i en mappe eller et dokumentbibliotek.

Du kan få flere oplysninger om, hvorfor du bruger de Office 365 CDN, generelle CDN begreber og andre Microsoft CDN'er, du kan bruge sammen med din Office 365 lejer, under [Netværk til levering af indhold](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Standard CDN oprindelser

Medmindre du angiver andet, konfigurerer Office 365 nogle standardoprindelser for dig, når du aktiverer Office 365 CDN. Hvis du fra starten vælger ikke at klargøre dem, kan du tilføje disse oprindelser, når du har fuldført konfigurationen. Medmindre du forstår konsekvenserne af at springe konfigurationen af standard oprindelser over og har en specifik årsag til at gøre det, skal du tillade, at de oprettes, når du aktiverer CDN.

Private CDN udgangspunkter som standard:

+ \*/userphoto.aspx
+ \*/siteassets

Standard offentlige CDN oprindelser:

+ \*/masterside
+ \*/style-bibliotek
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ er en standardbaseret offentlig oprindelse, der blev føjet til tjenesten Office 365 CDN i december 2017. Denne oprindelse skal være til stede, for at SharePoint Framework løsninger i CDN fungerer. Hvis du har aktiveret Office 365 CDN før december 2017, eller hvis du sprang konfigurationen af standard oprindelser over, da du aktiverede CDN, kan du tilføje dette oprindelse manuelt. Du kan få flere oplysninger under [Webdelen på klientsiden eller SharePoint Framework løsning fungerer ikke](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Konfigurer og konfigurer Office 365 CDN ved hjælp af SharePoint Online Management Shell

Procedurerne i dette afsnit kræver, at du bruger SharePoint Online Management Shell til at oprette forbindelse til SharePoint Online. Du kan finde instruktioner [under Forbind til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Udfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp af SharePoint Online Management Shell.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Giv din organisation mulighed for at bruge Office 365 CDN

Før du ændrer lejerens CDN indstillinger, skal du hente den aktuelle status for den private CDN konfiguration i din Office 365 lejer. Forbind til din lejer ved hjælp af shell'en SharePoint Online Management:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Brug nu **cmdlet'en Get-SPOTenantCdnEnabled** til at hente statusindstillingerne for CDN fra lejeren:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Status for CDN for den angivne CdnType vises på skærmen.

Brug **Set-SPOTenantCdnEnabled-cmdlet'en** til at gøre det muligt for din organisation at bruge Office 365 CDN. Du kan gøre det muligt for din organisation at bruge offentlige oprindelser, private oprindelser eller begge dele på én gang. Du kan også konfigurere CDN til at springe konfigurationen af standard oprindelser over, når du aktiverer den. Du kan altid tilføje disse oprindelser senere som beskrevet i dette emne.

I Windows PowerShell til SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Hvis du f.eks. vil gøre det muligt for din organisation at bruge både offentlige og private oprindelser, skal du skrive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Hvis du vil gøre det muligt for din organisation at bruge både offentlige og private oprindelser, men undlade at konfigurere standardoprindelse, skal du skrive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Se [Standard CDN oprindelser](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for at få oplysninger om de oprindelser, der klargøres som standard, når du aktiverer Office 365 CDN, og den potentielle virkning af at springe konfigurationen af standardoprindelse over.

Hvis du vil gøre det muligt for din organisation at bruge offentlige oprindelser, skal du skrive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Hvis du vil gøre det muligt for din organisation at bruge private oprindelser, skal du skrive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Du kan få flere oplysninger om denne cmdlet under [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Rediger listen over filtyper, der skal medtages i Office 365 CDN (valgfrit)

> [!TIP]
> Når du definerer filtyper ved hjælp af **Set-SPOTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil føje flere filtyper til listen, skal du først bruge cmdlet'en til at finde ud af, hvilke filtyper der allerede er tilladt, og inkludere dem på listen sammen med dine nye.

Brug **Cmdlet'en Set-SPOTenantCdnPolicy** til at definere statiske filtyper, der kan hostes af offentlige og private oprindelser i CDN. Almindelige aktivtyper er som standard tilladt, f.eks. .css, .gif, .jpg og .js.

I Windows PowerShell til SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Hvis du f.eks. vil gøre det muligt for CDN at hoste .css- og .png-filer, skal du angive kommandoen:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Hvis du vil se, hvilke filtyper der i øjeblikket er tilladt af CDN, skal du bruge cmdlet'en **Get-SPOTenantCdnPolicies**:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Du kan få flere oplysninger om disse cmdlet'er under [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) og [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Rediger listen over webstedsklassifikationer, du vil udelade fra Office 365 CDN (valgfrit)

> [!TIP]
> Når du udelader webstedsklassificeringer ved hjælp af **Set-SPOTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere webstedsklassifikationer, skal du først bruge cmdlet'en til at finde ud af, hvilke klassificeringer der allerede er udelukket, og derefter tilføje dem sammen med dine nye.

Brug **Cmdlet'en Set-SPOTenantCdnPolicy** til at udelade webstedsklassifikationer, som du ikke vil gøre tilgængelige via CDN. Som standard er ingen webstedsklassifikationer udeladt.

I Windows PowerShell til SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Hvis du vil se, hvilke webstedsklassificeringer der i øjeblikket er begrænset, skal du bruge cmdlet'en **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

De egenskaber, der returneres, er _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ og _ExcludeIfNoScriptDisabled_.

Egenskaben _IncludeFileExtensions_ indeholder listen over filtypenavne, der skal behandles fra CDN.

> [!NOTE]
> Standardfiludvidelserne er forskellige fra offentlige til private.

Egenskaben _ExcludeRestrictedSiteClassifications_ indeholder de webstedsklassifikationer, du vil udelade fra CDN. Du kan f.eks. udelade websteder, der er markeret som **Fortrolige**, så indhold fra websteder, hvor klassificeringen er anvendt, ikke håndteres fra CDN.

Egenskaben _ExcludeIfNoScriptDisabled_ udelukker indhold fra CDN baseret på indstillingerne for _NoScript-attributten_ på webstedsniveau. NoScript-attributten er som standard angivet til **Aktiveret** for _moderne_ websteder og **Deaktiveret** for _klassiske_ websteder. Dette afhænger af dine lejerindstillinger.

Du kan få flere oplysninger om disse cmdlet'er under [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) og [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Tilføj et udgangspunkt for dine aktiver

Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere et oprindelsessted. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint bibliotek eller en mappe, der indeholder de aktiver, som CDN skal hoste.

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som anses for at være følsomme over for din organisation i et offentligt miljø.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Værdien af _stien_ er den relative sti til det bibliotek eller den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier. Oprindelser understøtter jokertegn, der er forudberedt til URL-adressen. Dette giver dig mulighed for at oprette oprindelser, der strækker sig over flere websteder. Hvis du f.eks. vil medtage alle aktiverne i mastersidemappen for alle dine websteder som offentlig oprindelse i CDN, skal du skrive følgende kommando:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Jokertegnændringen ***/** kan kun bruges i starten af stien og svarer til alle URL-segmenter under den angivne URL-adresse.
+ Stien kan pege på et dokumentbibliotek, en mappe eller et websted. Stien _*/websted1_ vil f.eks. stemme overens med alle dokumentbiblioteker under webstedet.

Du kan tilføje et oprindelsessted med en bestemt relativ sti. Du kan ikke tilføje et oprindelsessted ved hjælp af hele stien.

I dette eksempel tilføjes et privat oprindelsessted for biblioteket for webstedsassetter på et bestemt websted:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

I dette eksempel tilføjes et privat oprindelsessted for _mappen folder1_ i biblioteket med webstedsaktiver for gruppen af websteder:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Hvis der er et mellemrum i stien, kan du enten omgive stien i dobbelte anførselstegn eller erstatte pladsen med URL-kodningen %20. Følgende eksempler tilføjer et privat udgangspunkt for _mappen 1_ i gruppens bibliotek med webstedsaktiver:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> I private oprindelser skal aktiver, der deles fra et oprindelsessted, have en overordnet version udgivet, før der kan opnås adgang til dem fra CDN.

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Eksempel: Konfigurer en offentlig oprindelse for dine mastersider og for dit typografibibliotek til SharePoint Online

Disse oprindelser er normalt konfigureret for dig som standard, når du aktiverer Office 365 CDN. Men hvis du vil aktivere dem manuelt, skal du følge disse trin.

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere typografibiblioteket som en offentlig oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Brug **add-SPOTenantCdnOrigin-cmdlet'en** til at definere mastersiderne som en offentlig oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Eksempel: Konfigurer et privat udgangspunkt for webstedets aktiver, webstedssider og udgivelse af billeder til SharePoint Online

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedsaktiver som et privat udgangspunkt.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedssider som et privat udgangspunkt.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere mappen med udgivelsesbilleder som en privat oprindelse.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Eksempel: Konfigurer et privat oprindelsessted for en gruppe af websteder for SharePoint Online

Brug **Add-SPOTenantCdnOrigin-cmdlet'en** til at definere en gruppe af websteder som en privat oprindelse. Eksempel:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Du får muligvis vist en meddelelse, der _afventer konfiguration_, som forventes, da SharePoint Online-lejeren opretter forbindelse til CDN-tjenesten. Dette kan tage op til 15 minutter.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Administrer Office 365 CDN

Når du har konfigureret CDN, kan du foretage ændringer i konfigurationen, når du opdaterer indhold, eller når dine behov ændres, som beskrevet i dette afsnit.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Tilføj, opdater eller fjern aktiver fra Office 365 CDN

Når du har fuldført konfigurationstrinnene, kan du tilføje nye aktiver og opdatere eller fjerne eksisterende aktiver, når du vil. Du skal blot foretage dine ændringer af aktiverne i mappen eller SharePoint bibliotek, som du har identificeret som oprindelse. Hvis du tilføjer et nyt aktiv, er det tilgængeligt via CDN med det samme. Men hvis du opdaterer aktivet, tager det op til 15 minutter, før den nye kopi overføres og bliver tilgængelig i CDN.

Hvis du har brug for at hente oprindelsens placering, kan du bruge cmdlet'en **Get-SPOTenantCdnOrigins** . Du kan få oplysninger om, hvordan du bruger denne cmdlet, under [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Fjern et oprindelsessted fra Office 365 CDN

Du kan fjerne adgangen til en mappe eller SharePoint bibliotek, som du har identificeret som oprindelse. Det gør du ved at bruge cmdlet'en **Remove-SPOTenantCdnOrigin** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Du kan få oplysninger om, hvordan du bruger denne cmdlet, under [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Rediger et oprindelsessted i Office 365 CDN

Du kan ikke ændre et oprindelsessted, du har oprettet. Fjern i stedet oprindelsen, og tilføj derefter en ny. Du kan finde flere oplysninger under [Sådan fjerner du en oprindelse fra Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) og [Sådan tilføjes en oprindelse for dine aktiver](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Brug **Set-SPOTenantCdnEnabled-cmdlet'en** til at deaktivere CDN for din organisation. Hvis du har både den offentlige og den private oprindelse aktiveret for CDN, skal du køre cmdlet'en to gange som vist i følgende eksempler.

Hvis du vil deaktivere brugen af offentlige oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Hvis du vil deaktivere brugen af private oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Du kan få flere oplysninger om denne cmdlet under [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Konfigurer og konfigurer Office 365 CDN ved hjælp af PnP PowerShell

Procedurerne i dette afsnit kræver, at du bruger PnP PowerShell til at oprette forbindelse til SharePoint Online. Du kan finde en vejledning under [Introduktion til PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).

Udfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp af PnP PowerShell.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Giv din organisation mulighed for at bruge Office 365 CDN

Før du ændrer lejerens CDN indstillinger, skal du hente den aktuelle status for den private CDN konfiguration i din Office 365 lejer. Forbind til din lejer ved hjælp af PnP PowerShell:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Brug nu **cmdlet'en Get-PnPTenantCdnEnabled** til at hente statusindstillingerne for CDN fra lejeren:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Status for CDN for den angivne CdnType vises på skærmen.

Brug **Set-PnPTenantCdnEnabled-cmdlet'en** til at gøre det muligt for din organisation at bruge Office 365 CDN. Du kan gøre det muligt for din organisation at bruge offentlige oprindelser, private oprindelser eller begge dele på samme tid. Du kan også konfigurere CDN til at springe konfigurationen af standard oprindelser over, når du aktiverer den. Du kan altid tilføje disse oprindelser senere som beskrevet i dette emne.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Hvis du f.eks. vil gøre det muligt for din organisation at bruge både offentlige og private oprindelser, skal du skrive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Hvis du vil gøre det muligt for din organisation at bruge både offentlige og private oprindelser, men undlade at konfigurere standardoprindelse, skal du skrive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Se [Standard CDN oprindelser](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for at få oplysninger om de oprindelser, der klargøres som standard, når du aktiverer Office 365 CDN, og den potentielle virkning af at springe konfigurationen af standardoprindelse over.

Hvis du vil gøre det muligt for din organisation at bruge offentlige oprindelser, skal du skrive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Hvis du vil gøre det muligt for din organisation at bruge private oprindelser, skal du skrive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Du kan få flere oplysninger om denne cmdlet under [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Rediger listen over filtyper, der skal medtages i Office 365 CDN (valgfrit)

> [!TIP]
> Når du definerer filtyper ved hjælp af **Set-PnPTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil føje flere filtyper til listen, skal du først bruge cmdlet'en til at finde ud af, hvilke filtyper der allerede er tilladt, og inkludere dem på listen sammen med dine nye.

Brug **Set-PnPTenantCdnPolicy-cmdlet'en** til at definere statiske filtyper, der kan hostes af offentlige og private oprindelser i CDN. Almindelige aktivtyper er som standard tilladt, f.eks. .css, .gif, .jpg og .js.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Hvis du f.eks. vil gøre det muligt for CDN at hoste .css- og .png-filer, skal du angive kommandoen:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Hvis du vil se, hvilke filtyper der i øjeblikket er tilladt af CDN, skal du bruge cmdlet'en **Get-PnPTenantCdnPolicies**:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Du kan få flere oplysninger om disse cmdlet'er under [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) og [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Rediger listen over webstedsklassifikationer, du vil udelade fra Office 365 CDN (valgfrit)

> [!TIP]
> Når du udelader webstedsklassificeringer ved hjælp af **Set-PnPTenantCdnPolicy-cmdlet'en** , overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere webstedsklassifikationer, skal du først bruge cmdlet'en til at finde ud af, hvilke klassificeringer der allerede er udelukket, og derefter tilføje dem sammen med dine nye.

Brug **Cmdlet'en Set-PnPTenantCdnPolicy** til at udelade webstedsklassifikationer, som du ikke vil gøre tilgængelige via CDN. Som standard er ingen webstedsklassifikationer udeladt.

I PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Hvis du vil se, hvilke webstedsklassificeringer der i øjeblikket er begrænset, skal du bruge cmdlet'en **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

De egenskaber, der returneres, er _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ og _ExcludeIfNoScriptDisabled_.

Egenskaben _IncludeFileExtensions_ indeholder listen over filtypenavne, der skal behandles fra CDN.

> [!NOTE]
> Standardfiludvidelserne er forskellige fra offentlige til private.

Egenskaben _ExcludeRestrictedSiteClassifications_ indeholder de webstedsklassifikationer, du vil udelade fra CDN. Du kan f.eks. udelade websteder, der er markeret som **Fortrolige**, så indhold fra websteder, hvor klassificeringen er anvendt, ikke håndteres fra CDN.

Egenskaben _ExcludeIfNoScriptDisabled_ udelukker indhold fra CDN baseret på indstillingerne for _NoScript-attributten_ på webstedsniveau. NoScript-attributten er som standard angivet til **Aktiveret** for _moderne_ websteder og **Deaktiveret** for _klassiske_ websteder. Dette afhænger af dine lejerindstillinger.

Du kan få flere oplysninger om disse cmdlet'er under [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) og [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Tilføj et udgangspunkt for dine aktiver

Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere et oprindelsessted. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint bibliotek eller en mappe, der indeholder de aktiver, som CDN skal hoste.

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der indeholder brugeroplysninger, eller som anses for at være følsomme over for din organisation i et offentligt miljø.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Værdien af _stien_ er den relative sti til det bibliotek eller den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier. Oprindelser understøtter jokertegn, der er forudberedt til URL-adressen. Dette giver dig mulighed for at oprette oprindelser, der strækker sig over flere websteder. Hvis du f.eks. vil medtage alle aktiverne i mastersidemappen for alle dine websteder som offentlig oprindelse i CDN, skal du skrive følgende kommando:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Jokertegnændringen ***/** kan kun bruges i starten af stien og svarer til alle URL-segmenter under den angivne URL-adresse.
+ Stien kan pege på et dokumentbibliotek, en mappe eller et websted. Stien _*/websted1_ vil f.eks. stemme overens med alle dokumentbiblioteker under webstedet.

Du kan tilføje et oprindelsessted med en bestemt relativ sti. Du kan ikke tilføje et oprindelsessted ved hjælp af hele stien.

I dette eksempel tilføjes et privat oprindelsessted for biblioteket med webstedsaktiver på et bestemt websted:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

I dette eksempel tilføjes et privat oprindelsessted for _mappen folder1_ i biblioteket med webstedsaktiver for gruppen af websteder:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Hvis der er et mellemrum i stien, kan du enten omgive stien i dobbelte anførselstegn eller erstatte pladsen med URL-kodningen %20. Følgende eksempler tilføjer et privat udgangspunkt for _mappen 1_ i gruppens bibliotek med webstedsaktiver:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

> [!NOTE]
> I private oprindelser skal aktiver, der deles fra et oprindelsessted, have en overordnet version udgivet, før der kan opnås adgang til dem fra CDN.

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Eksempel: Konfigurer en offentlig oprindelse for dine mastersider og for dit typografibibliotek til SharePoint Online

Disse oprindelser er normalt konfigureret for dig som standard, når du aktiverer Office 365 CDN. Men hvis du vil aktivere dem manuelt, skal du følge disse trin.

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere typografibiblioteket som en offentlig oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mastersiderne som en offentlig oprindelse.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Eksempel: Konfigurer et privat udgangspunkt for webstedets aktiver, webstedssider og udgivelse af billeder til SharePoint Online

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedsaktiver som et privat udgangspunkt.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med webstedssider som et privat udgangspunkt.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere mappen med udgivelsesbilleder som et privat udgangspunkt.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Dette kan tage op til 15 minutter.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Eksempel: Konfigurer et privat oprindelsessted for en gruppe af websteder for SharePoint Online

Brug **Add-PnPTenantCdnOrigin-cmdlet'en** til at definere en gruppe af websteder som en privat oprindelse. Eksempel:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Du kan få flere oplysninger om denne kommando og dens syntaks under [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Når du har kørt kommandoen, synkroniserer systemet konfigurationen på tværs af datacenteret. Du får muligvis vist en meddelelse, der _afventer konfiguration_, som forventes, da SharePoint Online-lejeren opretter forbindelse til CDN-tjenesten. Dette kan tage op til 15 minutter.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Administrer Office 365 CDN

Når du har konfigureret CDN, kan du foretage ændringer i konfigurationen, når du opdaterer indhold, eller når dine behov ændres, som beskrevet i dette afsnit.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Tilføj, opdater eller fjern aktiver fra Office 365 CDN

Når du har fuldført konfigurationstrinnene, kan du tilføje nye aktiver og opdatere eller fjerne eksisterende aktiver, når du vil. Du skal blot foretage dine ændringer af aktiverne i mappen eller SharePoint bibliotek, som du har identificeret som oprindelse. Hvis du tilføjer et nyt aktiv, er det tilgængeligt via CDN med det samme. Men hvis du opdaterer aktivet, tager det op til 15 minutter, før den nye kopi overføres og bliver tilgængelig i CDN.

Hvis du har brug for at hente oprindelsesplaceringen, kan du bruge cmdlet'en **Get-PnPTenantCdnOrigin** . Du kan få oplysninger om, hvordan du bruger denne cmdlet, under [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Fjern et oprindelsessted fra Office 365 CDN

Du kan fjerne adgangen til en mappe eller SharePoint bibliotek, som du har identificeret som oprindelse. Det gør du ved at bruge cmdlet'en **Remove-PnPTenantCdnOrigin** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Du kan få oplysninger om, hvordan du bruger denne cmdlet, under [Remove-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Remove-PnPTenantCdnOrigin.html).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Rediger et oprindelsessted i Office 365 CDN

Du kan ikke ændre et oprindelsessted, du har oprettet. Fjern i stedet oprindelsen, og tilføj derefter en ny. Du kan finde flere oplysninger under [Sådan fjerner du en oprindelse fra Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) og [Sådan tilføjes en oprindelse for dine aktiver](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Brug **Set-PnPTenantCdnEnabled-cmdlet'en** til at deaktivere CDN for din organisation. Hvis du har både den offentlige og den private oprindelse aktiveret for CDN, skal du køre cmdlet'en to gange som vist i følgende eksempler.

Hvis du vil deaktivere brugen af offentlige oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Hvis du vil deaktivere brugen af private oprindelser i CDN, skal du angive følgende kommando:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Du kan få flere oplysninger om denne cmdlet under [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Konfigurer Office 365 CDN ved hjælp af kommandolinjegrænsefladen for Microsoft 365

Procedurerne i dette afsnit kræver, at du har installeret [kommandolinjegrænsefladen til Microsoft 365](https://aka.ms/cli-m365). Opret derefter forbindelse til din Office 365 lejer ved hjælp af [logonkommandoen](https://pnp.github.io/cli-microsoft365/cmd/login/).

Udfør disse trin for at konfigurere CDN til at hoste dine aktiver i SharePoint Online ved hjælp af kommandolinjegrænsefladen for Microsoft 365.

<details>
  <summary>Klik for at udvide</summary>

### <a name="enable-the-office-365-cdn"></a>Aktivér Office 365 CDN

Du kan administrere tilstanden for Office 365 CDN i din lejer ved hjælp af kommandoen [spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

Sådan aktiverer du Office 365 offentlige CDN i din lejer:

```cli
spo cdn set --type Public --enabled true
```

Hvis du vil aktivere Office 365 SharePoint CDN, skal du udføre:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Få vist den aktuelle status for Office 365 CDN

Hvis du vil kontrollere, om den bestemte type Office 365 CDN er aktiveret eller deaktiveret, skal du bruge kommandoen [hent spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

Hvis du vil kontrollere, om Office 365 Offentlige CDN er aktiveret, skal du udføre:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Få vist de Office 365 CDN oprindelser

Sådan får du vist de aktuelt konfigurerede Office 365 Offentlige CDN oprindelser:

```cli
spo cdn origin list --type Public
```

Se [Standard CDN oprindelser](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for at få oplysninger om de oprindelser, der klargøres som standard, når du aktiverer Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Tilføj et Office 365 CDN oprindelse

> [!IMPORTANT]
> Du bør aldrig placere ressourcer, der anses for at være følsomme over for din organisation, i et SharePoint dokumentbibliotek, der er konfigureret som offentlig oprindelse.

Brug kommandoen [add for spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) til at definere et CDN oprindelse. Du kan definere flere oprindelser. Oprindelsen er en URL-adresse, der peger på et SharePoint bibliotek eller en mappe, der indeholder de aktiver, som CDN skal hoste.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Hvor `path` er den relative sti til den mappe, der indeholder aktiverne. Du kan bruge jokertegn ud over relative stier.

Hvis du vil medtage alle aktiver i **hovedsidegalleriet** for alle websteder som offentlig oprindelse, skal du udføre:

```cli
spo cdn origin add --type Public --origin */masterpage
```

Hvis du vil konfigurere et privat oprindelse for en bestemt gruppe af websteder, skal du udføre:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Når du har tilføjet en CDN oprindelse, kan det tage op til 15 minutter, før du kan hente filer via CDN-tjenesten. Du kan kontrollere, om det pågældende oprindelsessted allerede er aktiveret, ved hjælp af kommandoen [spo cdn origin list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) .

### <a name="remove-an-office-365-cdn-origin"></a>Fjern et Office 365 CDN oprindelse

Brug kommandoen [fjern spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) til at fjerne et CDN oprindelse for den angivne CDN type.

Hvis du vil fjerne en offentlig oprindelse fra CDN konfiguration, skal du udføre:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Fjernelse af et CDN oprindelse påvirker ikke de filer, der er gemt i et dokumentbibliotek, som svarer til det pågældende oprindelsessted. Hvis der er refereret til disse aktiver ved hjælp af deres SharePoint URL-adresse, skifter SharePoint automatisk tilbage til den oprindelige URL-adresse, der peger på dokumentbiblioteket. Hvis der er blevet refereret til aktiver ved hjælp af en offentlig CDN URL-adresse, brydes linket, hvis du fjerner oprindelsen, og du skal ændre dem manuelt.

### <a name="modify-an-office-365-cdn-origin"></a>Rediger et Office 365 CDN oprindelse

Det er ikke muligt at ændre et eksisterende CDN oprindelse. Du bør i stedet fjerne den tidligere definerede CDN oprindelse ved hjælp af `spo cdn origin remove` kommandoen og tilføje en ny ved hjælp af `spo cdn origin add` kommandoen .

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Rediger de filtyper, der skal medtages i Office 365 CDN

Følgende filtyper er som standard inkluderet i CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff og .woff2_. Hvis du har brug for at inkludere flere filtyper i CDN, kan du ændre konfigurationen af CDN ved hjælp af kommandoen [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Når du ændrer listen over filtyper, overskriver du den aktuelt definerede liste. Hvis du vil medtage flere filtyper, skal du først bruge kommandoen [spo cdn-politikliste](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) til at finde ud af, hvilke filtyper der er konfigureret i øjeblikket.

Hvis du vil føje _JSON-filtypen_ til standardlisten over filtyper, der er inkluderet i den offentlige CDN, skal du udføre:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Rediger listen over webstedsklassifikationer, du vil udelade fra Office 365 CDN

Brug kommandoen [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) til at udelade webstedsklassifikationer, som du ikke vil gøre tilgængelige for CDN. Som standard er ingen webstedsklassifikationer udeladt.

> [!NOTE]
> Når du ændrer listen over udeladte webstedsklassifikationer, overskriver du den aktuelt definerede liste. Hvis du vil udelade yderligere klassificeringer, skal du først bruge kommandoen [spo cdn-politikliste](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) til at finde ud af, hvilke klassificeringer der i øjeblikket er konfigureret.

Hvis du vil udelukke websteder, der er klassificeret som _HBI_, fra den offentlige CDN, skal du udføre

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Deaktiver Office 365 CDN

Hvis du vil deaktivere Office 365 CDN skal du bruge kommandoen `spo cdn set` , f.eks.:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Brug af dine CDN aktiver

Nu, hvor du har aktiveret CDN og konfigurerede oprindelser og politikker, kan du begynde at bruge dine CDN aktiver.

Dette afsnit hjælper dig med at forstå, hvordan du bruger CDN URL-adresser på dine SharePoint sider og indhold, så SharePoint omdirigerer anmodninger om aktiver i både offentlige og private oprindelser til CDN.

+ [Opdaterer kæder til CDN aktiver](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Brug af aktiver i offentlig oprindelse](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Brug af aktiver i privat oprindelse](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Du kan få oplysninger om, hvordan du bruger CDN til at hoste webdele på klientsiden, i emnet [Host din webdel på klientsiden fra Office 365 CDN (Hello World del 4).](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)

> [!NOTE]
> Hvis du føjer mappen _ClientSideAssets_ til listen over **private** CDN oprindelser, gengives CDN brugerdefinerede webdele ikke. Filer, der bruges af SPFX-webdele, kan kun bruge den offentlige CDN, og mappen ClientSideAssets er standard for offentlige CDN.

### <a name="updating-links-to-cdn-assets"></a>Opdaterer kæder til CDN aktiver

Hvis du vil bruge aktiver, du har føjet til et oprindelsessted, skal du blot opdatere kæder til den oprindelige fil med stien til filen i oprindelsen.

+ Rediger den side eller det indhold, der indeholder links til aktiver, du har føjet til et oprindelsessted. Du kan også bruge en af flere metoder til globalt at søge efter og erstatte links på tværs af et enter-websted eller en gruppe af websteder, hvis du vil opdatere linket til et bestemt aktiv overalt, hvor det vises.
+ For hvert link til et aktiv i et oprindelsessted skal du erstatte stien med stien til filen i CDN oprindelse. Du kan bruge relative stier.
+ Gem siden eller indholdet.

Overvej f.eks. billedet _/webstedet/SiteAssets/images/image.png_, som du har kopieret til dokumentbiblioteksmappen _/websted/CDN_origins/offentlig/_. Hvis du vil bruge CDN aktiv, skal du erstatte den oprindelige sti til billedfilens placering med stien til oprindelsen for at gøre den nye URL-adresse _/websted/CDN_origins/offentlig/image.png_.

Hvis du vil bruge hele URL-adressen til aktivet i stedet for en relativ sti, skal du oprette linket på følgende måde:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Generelt bør du ikke hardcode URL-adresser direkte til aktiver i CDN. Du kan dog manuelt konstruere URL-adresser for aktiver i offentlige oprindelser, hvis det er nødvendigt. Du kan få flere oplysninger under [Hardcoding CDN URL-adresser til offentlige aktiver](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Hvis du vil vide mere om, hvordan du kontrollerer, at aktiverne betjenes fra CDN, skal du se [Hvordan gør jeg bekræfte, at aktiverne betjenes af CDN?](use-microsoft-365-cdn-with-spo.md#CDNConfirm) i [Fejlfinding af Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

### <a name="using-assets-in-public-origins"></a>Brug af aktiver i offentlig oprindelse

**Publiceringsfunktionen** i SharePoint Online omskriver automatisk URL-adresser for aktiver, der er gemt i offentlig oprindelse, til de tilsvarende CDN, så aktiverne behandles fra CDN-tjenesten i stedet for SharePoint.

Hvis din oprindelse findes på et websted, hvor funktionen Udgivelse er aktiveret, og de aktiver, du vil overføre til CDN, er i en af følgende kategorier, omskriver SharePoint automatisk URL-adresser for aktiver i oprindelsen, forudsat at aktivet ikke er blevet udelukket af en CDN politik.

Følgende er en oversigt over, hvilke links der automatisk omskrives af funktionen SharePoint udgivelse:

+ IMG/LINK/CSS URL-adresser i klassiske HTML-svar til udgivelsessider
  + Dette omfatter billeder, der er tilføjet af forfattere i HTML-indholdet på en side
+ URL-adresser til billedbibliotekswebdelsbilleder
+ Billedfelter i SPList REST API-resultater (RenderListDataAsStream)
  + Brug den nye egenskab _ImageFieldsToTryRewriteToCdnUrls_ til at angive en kommasepareret liste over felter
  + Understøtter linkfelter og udgivelsesfelter
+ SharePoint billedgengivelser

I følgende diagram illustreres arbejdsprocessen, når SharePoint modtager en anmodning om en side, der indeholder aktiver fra en offentlig oprindelse.

![Arbejdsprocesdiagram: Henter Office 365 CDN aktiver fra en offentlig oprindelse.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Arbejdsproces: Henter Office 365 CDN aktiver fra en offentlig oprindelse")

> [!TIP]
> Hvis du vil deaktivere automatisk omskrivning for bestemte URL-adresser på en side, kan du tjekke siden ud og tilføje parameteren for forespørgselsstrengen **? NoAutoReWrites=true** til slutningen af hvert link, du vil deaktivere.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Oprettelse CDN URL-adresser for offentlige aktiver

Hvis _publiceringsfunktionen_ ikke er aktiveret for en offentlig oprindelse, eller hvis aktivet ikke er en af de linktyper, der understøttes af funktionen til automatisk omskrivning i CDN-tjenesten, kan du manuelt oprette URL-adresser til aktivernes CDN placering og bruge disse URL-adresser i dit indhold.

> [!NOTE]
> Du kan ikke hardcode eller konstruere CDN URL-adresser til aktiver i et privat oprindelse, fordi det påkrævede adgangstoken, der udgør den sidste sektion i URL-adressen, genereres på det tidspunkt, hvor der anmodes om ressourcen. Du kan oprette URL-adressen for offentlige CDN, og URL-adressen bør ikke være hardcoded, da den kan ændres.

For offentlige CDN aktiver vil URL-formatet se ud på følgende måde:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Erstat **TenantHostName** med dit lejernavn. Eksempel:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> Egenskaben for sidekontekst skal bruges til at konstruere præfikset i stedet for hardcodeing "https://publiccdn.sharepointonline.com". URL-adressen kan ændres og må ikke kodes hårdt. Hvis du bruger visningsskabeloner med Classic SharePoint Online, kan du bruge egenskaben "window._spPageContextInfo.publicCdnBaseUrl" i din visningsskabelon til præfikset for URL-adressen. Hvis du er SPFx webdele til moderne og klassiske SharePoint kan du bruge egenskaben "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". Dette giver præfikset, så hvis det ændres, opdateres din implementering med det. Som et eksempel på SPFx kan URL-adressen oprettes ved hjælp af egenskaben "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL for elementet". Se [Brug af CDN i kode på klientsiden](https://youtu.be/IH1RbQlbhIA), som er en del af [sæson 1-serien om ydeevne](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Brug af aktiver i privat oprindelse

Der kræves ingen yderligere konfiguration for at bruge aktiver i private oprindelser. SharePoint Online omskriver automatisk URL-adresser for aktiver med privat oprindelse, så anmodninger om disse aktiver altid behandles fra CDN. Du kan ikke manuelt oprette URL-adresser til CDN aktiver i private oprindelser, fordi disse URL-adresser indeholder tokens, der skal genereres automatisk af SharePoint Online på det tidspunkt, hvor der anmodes om aktivet.

Adgang til aktiver i private oprindelser beskyttes af dynamisk genererede tokens baseret på brugertilladelser til oprindelsen med advarslerne beskrevet i følgende afsnit. Brugerne skal som minimum have **læseadgang** til oprindelserne, for at CDN kan gengive indhold.

I følgende diagram illustreres arbejdsprocessen, når SharePoint modtager en anmodning om en side, der indeholder aktiver fra et privat udgangspunkt.

![Arbejdsprocesdiagram: Hentning Office 365 CDN aktiver fra et privat udgangspunkt.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Arbejdsproces: Henter Office 365 CDN aktiver fra et privat udgangspunkt")

#### <a name="token-based-authorization-in-private-origins"></a>Tokenbaseret autorisation i privat oprindelse

Adgang til aktiver med privat oprindelse i Office 365 CDN gives af tokens, der genereres af SharePoint Online. Brugere, der allerede har tilladelse til at få adgang til den mappe eller det bibliotek, der er angivet af oprindelsen, tildeles automatisk tokens, der giver brugeren adgang til filen på baggrund af deres tilladelsesniveau. Disse adgangstokens er gyldige i 30 til 90 minutter, efter de er genereret, for at forhindre tokenafspilningsangreb.

Når adgangstokenet er genereret, returnerer SharePoint Online en brugerdefineret URI til klienten, der indeholder to godkendelsesparametre _eat_ (kantgodkendelsestoken) og _havre_ (oprindelsesgodkendelsestoken). Strukturen af hvert token er _<'udløbsdato i Epoch-klokkeslætsformat'>__<'sikker signatur'>_. Eksempel:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Alle, der er i besiddelse af tokenet, kan få adgang til ressourcen i CDN. URL-adresser, der indeholder disse adgangstokens, deles kun via HTTPS, så medmindre URL-adressen udtrykkeligt deles af en slutbruger, før tokenet udløber, vil aktivet ikke være tilgængeligt for uautoriserede brugere.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Tilladelser på elementniveau understøttes ikke for aktiver med privat oprindelse

Det er vigtigt at bemærke, at SharePoint Online ikke understøtter tilladelser på elementniveau for aktiver med privat oprindelse. For en fil, der er placeret på `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, har brugerne f.eks. effektiv adgang til filen på baggrund af følgende betingelser:

|Bruger  |Tilladelser  |Effektiv adgang  |
|---------|---------|---------|
|Bruger 1     |Har adgang til mappe1         |Kan få adgang til image1.jpg fra CDN         |
|Bruger 2     |Har ikke adgang til mappe1         |Der er ikke adgang til image1.jpg fra CDN         |
|Bruger 3     |Har ikke adgang til folder1, men er tildelt eksplicit tilladelse til at få adgang til image1.jpg i SharePoint Online         |Kan få adgang til aktivet image1.jpg direkte fra SharePoint Online, men ikke fra CDN         |
|Bruger 4     |Har adgang til folder1, men har udtrykkeligt nægtet adgang til image1.jpg i SharePoint Online         |Det er ikke muligt at få adgang til aktivet fra SharePoint Online, men kan få adgang til aktivet fra CDN, selvom der er nægtet adgang til filen i SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Fejlfinding af Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Hvordan gør jeg bekræfte, at aktiverne betjenes af CDN?

Når du har føjet links til CDN aktiver til en side, kan du bekræfte, at aktivet betjenes fra CDN ved at gå til siden og højreklikke på billedet, når det er gengivet og gennemse billedets URL-adresse.

Du kan også bruge udviklerværktøjerne i din browser til at få vist URL-adressen for hvert aktiv på en side eller bruge et værktøj til netværkssporing fra tredjepart.

> [!NOTE]
> Hvis du bruger et netværksværktøj, f.eks. Fiddler, til at teste dine aktiver uden for at gengive aktivet fra en SharePoint side, skal du manuelt tilføje referenceheaderen "Referer: `https://yourdomain.sharepoint.com`" til GET-anmodningen, hvor URL-adressen er rod-URL-adressen for din SharePoint Online-lejer.

Du kan ikke teste CDN URL-adresser direkte i en webbrowser, fordi du skal have en referer, der kommer fra SharePoint Online. Men hvis du føjer URL-adressen til CDN til en SharePoint side og derefter åbner siden i en browser, kan du se det CDN aktiv, der gengives på siden.

Du kan få flere oplysninger om brug af udviklerværktøjer i Microsoft Edge browser under [Microsoft Edge Udviklerværktøjer](/microsoft-edge/devtools-guide).

Hvis du vil se en kort video, der hostes i [YouTube-kanalen SharePoint Udviklermønstre og -fremgangsmåder](https://aka.ms/sppnp-videos), der demonstrerer, hvordan du kan bekræfte, at dine CDN fungerer, skal du se [Kontrollér din CDN brug og sikre optimal netværksforbindelse](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Hvorfor er aktiver fra en ny oprindelse ikke tilgængelige?
Aktiver med nye oprindelser vil ikke umiddelbart være tilgængelige til brug, da det tager tid, før registreringen overføres via CDN, og at aktiverne uploades fra oprindelsen til CDN lager. Den tid, der kræves, for at aktiverne er tilgængelige i CDN, afhænger af, hvor mange aktiver og filer der størrelser.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Min webdel eller SharePoint Framework løsning på klientsiden fungerer ikke

Når du aktiverer Office 365 CDN for offentlige oprindelser, opretter tjenesten CDN automatisk disse standard oprindelser:

+ */MASTERSIDE
+ */TYPOGRAFIBIBLIOTEK
+ */CLIENTSIDEASSETS

Hvis oprindelsen */clientsideassets mangler, mislykkes SharePoint Framework løsninger, og der genereres ingen advarsler eller fejlmeddelelser. Dette oprindelsessted mangler muligvis enten, fordi CDN blev aktiveret med parameteren _-NoDefaultOrigins_ indstillet til **$true**, eller fordi oprindelsen blev slettet manuelt.

Du kan kontrollere, hvilke oprindelser der findes med følgende PowerShell-kommando:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Eller du kan kontrollere med Office 365 kommandolinjegrænsefladen:

```cli
spo cdn origin list
```

Sådan tilføjer du oprindelsen i PowerShell:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Sådan tilføjes oprindelsen i kommandolinjegrænsefladen i Office 365:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Hvilke PowerShell-moduler og CLI-shells skal jeg bruge for at arbejde med Office 365 CDN?

Du kan vælge at arbejde med Office 365 CDN enten ved hjælp af **modulet SharePoint Online Management Shell** PowerShell eller **kommandolinjegrænsefladen Office 365**.

+ [Introduktion til SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Installation af Office 365 kommandolinjegrænsefladen](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Se også

[Netværk til levering af indhold](./content-delivery-networks.md)

[Netværksplanlægning og justering af ydeevne for Office 365](./network-planning-and-performance.md)

[SharePoint - videoserie om Office 365 CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
