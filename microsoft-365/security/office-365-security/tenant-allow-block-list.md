---
title: Administrer dine tilladte og blokerer fra lejerens tilladelses-/blokeringsliste
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de administrerer tilladelses- og blokeringsblokke i lejerens tilladelses-/blokeringsliste i sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e27da44a38162955df252e29c1754c93a2dc8967
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590072"
---
# <a name="manage-the-tenant-allowblock-list"></a>Administrer lejerens tilladelses-/blokeringsliste

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Nogle af de funktioner, der er beskrevet i denne artikel, er i Preview, kan blive ændret og er ikke tilgængelige i alle organisationer.
>
> Hvis din organisation ikke har spoof-funktionerne som beskrevet i denne artikel, kan du se den ældre spoof-administrationsoplevelse i Administrer spoof-afsendere ved hjælp af efterlignet intelligenspolitik og [efterlignet intelligensindsigt i EOP](walkthrough-spoof-intelligence-insight.md).

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, kan du være uenig i EOP-filtreringskriteriet. En god meddelelse kan f.eks. være markeret som dårlig (en falsk positiv), eller en forkert meddelelse kan blive tilladt via (en falsk negativ).

Lejerens tilladelses-/blokeringsliste i Microsoft 365 Defender-portalen giver dig en metode til manuelt at tilsidesætte Microsoft 365 dine filtreringskriterier. Lejerens tilladelses-/blokeringsliste bruges under mailflow for indgående meddelelser (gælder ikke for meddelelser inden for organisationen) og på tidspunktet for brugerklik. Du kan angive følgende typer tilsidesættelser:

- URL-adresser, der skal blokeres.
- Filer, der skal blokeres.
- Afsendermails eller domæner, der skal blokeres.
- Spoofed afsendere at tillade eller blokere. Hvis du tilsidesætter tilladelses- eller blokeringsindsigt i efterlignet intelligensindsigt, bliver den [spoofede](learn-about-spoof-intelligence.md) afsender en manuel tilladelse eller blokering, der kun vises på fanen **Spoof** på lejerens tilladelses-/blokeringsliste. Du kan også manuelt oprette tillade eller blokere poster for efterlignede afsendere her, før de bliver registreret af efterlignet intelligens.
- URL-adresser til at tillade.
- Filer, der skal tillades.
- Afsendermails eller domæner, der skal tillades.

Denne artikel beskriver, hvordan du konfigurerer poster på listen over tilladte/blokerede lejere i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **med lejerens tilladelses-/blokeringslister** skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

- Du kan angive filer ved hjælp af filens SHA256-hash-værdi. For at finde SHA256-hash-værdien for en fil i Windows skal du køre følgende kommando i en kommandoprompt:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  En eksempelværdi er `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Værdier for perceptuel hash (pHash) understøttes ikke.

- De tilgængelige URL-værdier er beskrevet i [URL-syntaksen for afsnittet Lejers tilladelses-/blokeringsliste](#url-syntax-for-the-tenant-allowblock-list) senere i denne artikel.

- Lejerens tilladelses-/blokeringsliste tillader maksimalt 500 poster for afsendere, 500 poster for URL-adresser, 500 poster for filhashes og 1024 poster til spoofing (spoofed afsendere).

- Det maksimale antal tegn for hver indtastning er:
  - Filhashes = 64
  - URL = 250

- En post bør være aktiv inden for 30 minutter.

- Som standard udløber posterne på lejerens tilladelses-/blokeringsliste efter 30 dage. Du kan angive en dato eller indstille den til aldrig at udløbe.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i Microsoft 365 Defender, før du kan udføre procedurerne i denne artikel:
  - **Afsendere, URL-adresser og filer**:
    - Hvis du vil tilføje og fjerne værdier fra lejerens tilladelses-/blokeringsliste, skal du være medlem af rollegrupperne  Organisationsadministration **, Sikkerhedsadministrator** eller Sikkerhedsoperator, eller du får tildelt rollen **Lejer AllowBlockList Manager**. 
    - For skrivebeskyttet adgang til lejerens tilladelses-/blokeringsliste skal du være medlem af rollegrupperne **Global læser** **eller** Sikkerhedslæser.
  - **Spoofing**: En af følgende kombinationer:
    - **Organisationsadministration**
    - **Sikkerhedsadministrator** <u>og</u> **kun visningskonfiguration eller** **kun visningsadministration af organisationen**.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

## <a name="configure-the-tenant-allowblock-list"></a>Konfigurer lejerens tilladelses-/blokeringsliste

### <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender portalen

I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til Politikker **& regler** \>  \> lejerens tilladelse **/blokeringslister** i **sektionen** Regler. For at gå direkte til siden **med lejerens tilladelses-/blokeringslister** skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

Hvis du vil tilføje alle blokke, [skal du se Tilføj blokke på lejerens tilladelses-/blokeringsliste](manage-tenant-blocks.md).

Hvis du vil tilføje alle, der tillader det, [skal du se Tilføj tillader i lejerens tilladelses-/blokeringsliste](manage-tenant-allows.md).

Hvis du vil ændre og fjerne alle blokke og tillader det, [skal du se Rediger og fjern poster på lejerens tilladelses-/blokeringsliste](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell

Hvis du vil administrere alle tilladte og blokerede elementer, skal du se Tilføj blokke på lejerens tilladelses- [/](manage-tenant-blocks.md)blokeringsliste, Tilføj tillader i lejerens tilladelses [-/](manage-tenant-allows.md)blokeringsliste og Rediger og fjern poster på lejerens tilladelses [-/blokeringsliste](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Få vist poster på lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til Politikker **& regler** \>  \> lejerens tilladelse **/blokeringslister** i **sektionen** Regler. For at gå direkte til siden **med lejerens tilladelses-/blokeringslister** skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den ønskede fane. De tilgængelige kolonner afhænger af den valgte fane:

   - **Afsendere**:
     - **Værdi**: Afsenderens domæne eller mailadresse.
     - **Handling**: Værdien **Tillad** eller **Bloker**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **URL-adresser**:
     - **Værdi**: URL-adressen.
     - **Handling**: Værdien **Tillad** eller **Bloker**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Filer**
     - **Værdi**: Filhash.
     - **Handling**: Værdien **Tillad** eller **Bloker**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Spoofing**
     - **Spoofed bruger**
     - **Afsendende infrastruktur**
     - **Spoof-type**: Værdien **Intern** eller **Ekstern**.
     - **Handling**: Værdien **Bloker** eller **Tillad**.

   Du kan klikke på en kolonneoverskrift for at sortere i stigende eller faldende rækkefølge.

   Du kan klikke på **Gruppe** for at gruppere resultaterne. De tilgængelige værdier afhænger af den valgte fane:

   - **Afsendere**: Du kan gruppere resultaterne efter **handling**.
   - **URL-adresser**: Du kan gruppere resultaterne efter **handling**.
   - **Filer**: Du kan gruppere resultaterne efter **handling**.
   - **Spoofing**: Du kan gruppere resultaterne efter **handlings-** **eller spoof-type**.

   Klik **på** Søg, angiv hele eller dele af en værdi, og tryk derefter på Enter for at finde en bestemt værdi. Klik på Ryd søgeikon, når du ![er færdig.](../../media/m365-cc-sc-close-icon.png) **Ryd søgning**.

   Klik **på Filtrer** for at filtrere resultaterne. De værdier, der er tilgængelige i pop **op-meddelelsesfilteret** , som vises, afhænger af den valgte fane:

   - **Afsendere**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **URL-adresser**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **Filer**
     - **Handling**
     - **Udløber aldrig**
     - **Senest opdateret**
     - **Fjern den**
   - **Spoofing**
     - **Handling**
     - **Spoof-type**

   Klik på Anvend, når du er **færdig**. Hvis du vil rydde eksisterende filtre, skal **du klikke på Filter**, og i pop **op-menuen** Filter, der vises, skal du klikke **på Ryd filtre**.

4. Klik på Tilføj, når du er **færdig**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Få vist afsender-, fil- eller URL-poster på lejerens tilladelses-/blokeringsliste

Hvis du vil have vist poster for blokeret afsender, fil eller URL-adresse på lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

I dette eksempel returneres oplysninger om den angivne filhashværdi.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

I dette eksempel returneres alle blokerede URL-adresser.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Få vist efterlignede afsenderposter

Hvis du vil have vist efterlignede afsenderposter på lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

I dette eksempel returneres alle efterlignede afsenderposter på lejerens liste over tilladte/blokerede afsendere.

```powershell
Get-TenantAllowBlockListSpoofItems
```

I dette eksempel returneres alle tilladte efterlignede afsenderposter, der er interne.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

I dette eksempel returneres alle blokerede efterlignede afsenderposter, der er eksterne.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>URL-syntaks for lejerens tilladelses-/blokeringsliste

- IPv4- og IPv6-adresser er tilladt, men TCP/UDP-porte er ikke.

- Filtypenavne er ikke tilladt (f.eks. test.pdf).

- Unicode understøttes ikke, men Punycode er.

- Værtsnavne er tilladt, hvis alle følgende sætninger er sande:
  - Værtsnavnet indeholder et punktum.
  - Der er mindst ét tegn til venstre for perioden.
  - Der er mindst to tegn til højre for perioden.

  er f.eks`t.co`. tilladt eller `contoso.` `.com` ikke tilladt.

- Understier er ikke underforståede for tillader.

  Omfatter f.eks `contoso.com` . ikke `contoso.com/a`.

- Jokertegn (*) er tilladt i følgende scenarier:

  - Et venstre jokertegn skal efterfølges af et punktum for at angive et underdomæne.

    Er f.eks `*.contoso.com` . tilladt, `*contoso.com` er ikke tilladt.

  - Et højre jokertegn skal følge en skråstreg (/) for at angive en sti.

    er f.eks`contoso.com/*`. tilladt eller `contoso.com/ab*` `contoso.com*` ikke tilladt.

  - `*.com*` er ugyldigt (ikke et domæne, der kan løses, og højre jokertegn følger ikke en skråstreg).

  - Jokertegn er ikke tilladt i IP-adresser.

- Tildetegnet (~) er tilgængeligt i følgende scenarier:

  - En venstre tilde angiver et domæne og alle underdomæner.

    For eksempel `~contoso.com` omfatter `contoso.com` og `*.contoso.com`.

- URL-poster, der indeholder protokoller (f.eks, `http://`, `https://`eller `ftp://`), vil mislykkes, fordi URL-poster gælder for alle protokoller.

- Et brugernavn eller en adgangskode understøttes ikke og er ikke påkrævet.

- Anførselstegn (' eller ") er ugyldige tegn.

- En URL-adresse skal indeholde alle omdirigeringer, hvor det er muligt.

### <a name="url-entry-scenarios"></a>Scenarier for URL-adresseindtastning

Gyldige URL-poster og deres resultater er beskrevet i de følgende afsnit.

#### <a name="scenario-no-wildcards"></a>Scenarie: Ingen jokertegn

**Post**: `contoso.com`

- **Tillad match**: contoso.com

- **Tillad ikke match:**

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Bloker match**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Bloker ikke tilsvarende**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scenarie: Venstre jokertegn (underdomæne)

**Post**: `*.contoso.com`

- **Tillad match og** **bloker match**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Tillad ikke matchet** og **Bloker ikke tilsvarende**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scenarie: Højre jokertegn øverst på stien

**Post**: `contoso.com/a/*`

- **Tillad match og** **bloker match**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Tillad ikke matchet** og **Bloker ikke tilsvarende**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scenarie: Venstre tilde

**Post**: `~contoso.com`

- **Tillad match og** **bloker match**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Tillad ikke matchet** og **Bloker ikke tilsvarende**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scenarie: Højre suffiks med jokertegn

**Post**: `contoso.com/*`

- **Tillad match og** **bloker match**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Tillad ikke matchet** **og Bloker ikke matchet**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scenarie: Venstre underdomæne med jokertegn og højre jokertegn

**Post**: `*.contoso.com/*`

- **Tillad match og** **bloker match**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Tillad ikke matchet** **og Bloker ikke tilsvarende**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scenarie: Venstre og højre tilde

**Post**: `~contoso.com~`

- **Tillad match og** **bloker match**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Tillad ikke matchet** og **Bloker ikke tilsvarende**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scenarie: IP-adresse

**Post**: `1.2.3.4`

- **Tillad match** og **Bloker match**: 1.2.3.4

- **Tillad ikke matchet** og **Bloker ikke tilsvarende**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>IP-adresse med højre jokertegn

**Post**: `1.2.3.4/*`

- **Tillad match og** **bloker match**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Eksempler på ugyldige indtastninger

Følgende indtastninger er ugyldige:

- **Manglende eller ugyldige domæneværdier**:

  - contoso
  - \*.contoso.\*
  - \*.com
  - \*.pdf

- **Jokertegn i tekst eller uden mellemrumstegn**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **IP-adresser med porte**:

  - contoso.com:443
  - abc.contoso.com:25

- **Ikke-beskrivende jokertegn**:

  - \*
  - \*.\*

- **Midterste jokertegn**:

  - conto\* so.com
  - conto~so.com

- **Dobbelt jokertegn**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Domænepars syntaks for efterlignede afsenderposter på lejerens liste over tilladte/blokerede afsendere

Et domænepar for en efterlignet afsender på lejerens tilladelses-/blokeringsliste anvender følgende syntaks: `<Spoofed user>, <Sending infrastructure>`.

- **Efterlignet bruger**: Denne værdi involverer mailadressen på den spoofede bruger, der vises i feltet **Fra** i mailklienter. Denne adresse kaldes også for `5322.From` adressen. Gyldige værdier omfatter:
  - En individuel mailadresse (f.eks. chris@contoso.com).
  - Et maildomæne (f.eks. contoso.com).
  - Jokertegnet (f.eks. \*).

- **Sender infrastruktur**: Denne værdi angiver kilden til meddelelser fra den spoofede bruger. Gyldige værdier omfatter:
  - Domænet, der findes i et omvendt DNS-opslag (PTR-post) på kildemailserverens IP-adresse (f.eks fabrikam.com).
  - Hvis kilde-IP-adressen ikke har en PTR-post, \<source IP\>identificeres den afsendende infrastruktur som /24 (f.eks. 192.168.100.100/24).

Her er nogle eksempler på gyldige domænepar til at identificere efterlignede afsendere:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Det maksimale antal spoof afsenderposter er 1000.

Tilføjelse af et domænepar tillader eller blokerer *kun kombinationen* af den efterlignede bruger *og* sendeinfrastrukturen. Det tillader ikke mail fra den efterlignede bruger fra nogen kilde, heller ikke mail fra den afsendende infrastrukturkilde for en spoof-bruger. 

Du kan f.eks. tilføje en tilladelsespost for følgende domænepar:

- **Domæne**: gmail.com
- **Infrastruktur**: tms.mx.com

Det er kun meddelelser fra det pågældende *domæne og* afsenderinfrastrukturpar, der har tilladelse til at efterligne. Andre afsendere, der forsøger at efterligne gmail.com, er ikke tilladt. Meddelelser fra afsendere på andre domæner, der stammer tms.mx.com, kontrolleres af efterlignet intelligens.
