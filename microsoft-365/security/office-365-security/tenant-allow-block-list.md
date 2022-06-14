---
title: Administrer dine tilladelser og blokke på listen over tilladte/blokerede lejere
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
description: Administratorer kan få mere at vide om, hvordan de administrerer tillader og blokke på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a25d1b7ad11c57bc63035086d9a043bcac504c16
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057599"
---
# <a name="manage-the-tenant-allowblock-list"></a>Administrer listen over tilladte/blokerede lejere

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online postkasser kan du være uenig i dommen om EOP-filtrering. En god meddelelse kan f.eks. være markeret som dårlig (et falsk positivt), eller der kan tillades en forkert meddelelse via (falsk negativ).

Listen over tilladte/blokerede lejere på Microsoft 365 Defender-portalen giver dig mulighed for manuelt at tilsidesætte de Microsoft 365 filtreringsdomme. Lejerlisten tillad/bloker bruges under mailflow til indgående meddelelser (gælder ikke for meddelelser i organisationen) og på tidspunktet for brugerens klik. Du kan angive følgende typer tilsidesættelser:

- URL-adresser, der skal blokeres.
- Filer, der skal blokeres.
- Afsendermails eller domæner, der skal blokeres.
- Forfalskede afsendere, der skal tillades eller blokeres. Hvis du tilsidesætter den tilladte eller blokerede dom i [indsigten spoof intelligence](learn-about-spoof-intelligence.md), bliver den spoofede afsender en manuel tilladelses- eller blokindtastning, der kun vises under fanen **Spoof** på listen Over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoofed afsendere her, før de registreres af spoof intelligence.
- URL-adresser, der skal tillades.
- Filer, der skal tillades.
- Sender mails eller domæner, der skal tillades.

I denne artikel beskrives det, hvordan du konfigurerer poster på listen over tilladte/blokerede lejere på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **med lister over tilladte/blokerede lejere** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

- Du angiver filer ved hjælp af filens SHA256-hashværdi. Hvis du vil finde SHA256-hashværdien for en fil i Windows, skal du køre følgende kommando i en kommandoprompt:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  En eksempelværdi er `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Perceptuelle hashværdier (pHash) understøttes ikke.

- De tilgængelige URL-værdier er beskrevet i [URL-syntaksen for afsnittet Tillad/bloker](#url-syntax-for-the-tenant-allowblock-list) lejer senere i denne artikel.

- Listen over tilladte/blokerede lejere tillader maksimalt 500 poster for afsendere, 500 poster for URL-adresser, 500 poster for filhash og 1024 poster for spoofing (spoofede afsendere).

- Det maksimale antal tegn for hver post er:
  - Filhashes = 64
  - URL-adresse = 250

- En post skal være aktiv inden for 30 minutter.

- Poster på listen over tilladte/blokerede lejere udløber som standard efter 30 dage. Du kan angive en dato eller indstille dem til aldrig at udløbe.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i Exchange Online, før du kan udføre procedurerne i denne artikel:
    - Hvis du vil tilføje og fjerne værdier fra listen over tilladte/blokerede lejere, skal du være medlem af
      - **Rollegruppen Organisationsadministration** eller **Sikkerhedsadministrator** (**rolle som sikkerhedsadministrator**)
      - **Rollegruppe for sikkerhedsoperator** (**Lejer allowBlockList Manager**).
    - Hvis du vil have skrivebeskyttet adgang til listen over tilladte/blokerede lejere, skal du være medlem af
      - **Rollegruppe for global læser**
      - **Rollegruppe for sikkerhedslæser**
      - **Rollegruppen Kun visningskonfiguration** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser *og* tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  > - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

## <a name="configure-the-tenant-allowblock-list"></a>Konfigurer listen over tilladte/blokerede lejere

### <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender-portalen

I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **med lister over tilladte/blokerede lejere** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

Hvis du vil tilføje alle blokke, skal du se [Tilføj blokke på listen over tilladte/blokerede lejere](manage-tenant-blocks.md).

Hvis du vil tilføje alle tillader, skal du se [Tilføj tillader på listen over tilladte/blokerede lejere](manage-tenant-allows.md).

Hvis du vil redigere og fjerne alle blokke og tillader, skal du se [Rediger og fjern poster på listen over tilladte/blokerede lejere](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell

Hvis du vil administrere alle tilladelser og blokke, skal du se [Tilføj blokke på listen Over tilladte/blokerede lejere](manage-tenant-blocks.md), [Tilføj tillader på listen Over tilladte/blokerede lejere](manage-tenant-allows.md) og [Rediger og fjern poster på lejerlisten tillad/bloker](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Vis poster på listen over tilladte/blokerede lejere

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Med lejer-/bloklister** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den ønskede fane. De kolonner, der er tilgængelige, afhænger af den fane, du har valgt:

   - **Afsendere**:
     - **Værdi**: Afsenderens domæne eller mailadresse.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Spoofing**
     - **Poofed bruger**
     - **Sender infrastruktur**
     - **Spoof-type**: Værdien **Intern** eller **Ekstern**.
     - **Handling**: Værdien **Block** eller **Allow**.
   - **URL-adresser**:
     - **Værdi**: URL-adressen.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**
   - **Filer**
     - **Værdi**: Filhash.
     - **Handling**: Værdien **Allow** eller **Block**.
     - **Ændret af**
     - **Senest opdateret**
     - **Fjern den**
     - **Bemærkninger**

   Du kan klikke på en kolonneoverskrift for at sortere i stigende eller faldende rækkefølge.

   Du kan klikke på **Gruppér** for at gruppere resultaterne. De værdier, der er tilgængelige, afhænger af den fane, du har valgt:

   - **Afsendere**: Du kan gruppere resultaterne efter **handling**.
   - **Spoofing**: Du kan gruppere resultaterne efter **Handling** eller **Spoof-type**.
   - **URL-adresser**: Du kan gruppere resultaterne efter **handling**.
   - **Filer**: Du kan gruppere resultaterne efter **handling**.

   Klik på **Søg**, indtast hele eller en del af en værdi, og tryk derefter på ENTER for at finde en bestemt værdi. Når du er færdig, skal du klikke på ![Ikonet Ryd søgning.](../../media/m365-cc-sc-close-icon.png) **Ryd søgning**.

   Klik på **Filtrer** for at filtrere resultaterne. De værdier, der er tilgængelige i pop **op-vinduet Filter** , som vises, afhænger af den fane, du har valgt:

   - **Afsendere**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **Spoofing**
     - **Handling**
     - **Spoof-type**
   - **Webadresser**
     - **Handling**
     - **Udløber aldrig**
     - **Dato for seneste opdatering**
     - **Fjern den**
   - **Filer**
     - **Handling**
     - **Udløber aldrig**
     - **Senest opdateret**
     - **Fjern den**

   Klik på **Anvend**, når du er færdig. Hvis du vil rydde eksisterende filtre, skal du klikke på **Filter** og klikke på **Ryd filtre** i pop **op-vinduet Filter**, der vises.

3. Klik på **Tilføj**, når du er færdig.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Få vist afsender-, fil- eller URL-adresser på listen over tilladte/blokerede lejere

Hvis du vil have vist afsender-, fil- eller URL-adresser på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

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

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Vis spoofed afsenderposter

Hvis du vil have vist spoofede afsenderposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

I dette eksempel returneres alle spooferede afsenderposter på listen over tilladte/blokerede lejere.

```powershell
Get-TenantAllowBlockListSpoofItems
```

I dette eksempel returneres alle tilladte forfalskede afsenderposter, der er interne.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

I dette eksempel returneres alle blokerede spoofed afsenderposter, der er eksterne.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>URL-syntaks for listen over tilladte/blokerede lejere

- Adresserne IPv4 og IPv6 er tilladt, men det er TCP/UDP-porte ikke.

- Filtypenavne er ikke tilladt (f.eks. test.pdf).

- Unicode understøttes ikke, men Punycode er.

- Værtsnavne er tilladt, hvis alle følgende sætninger er sande:
  - Værtsnavnet indeholder et punktum.
  - Der er mindst ét tegn til venstre i punktumet.
  - Der er mindst to tegn til højre for punktum.

  Er f.eks `t.co` . tilladt, `.com` eller `contoso.` er ikke tilladt.

- Understier er ikke underforstået i forbindelse med tillad.

  Omfatter `contoso.com/a`f.eks. `contoso.com` ikke .

- Jokertegn (*) er tilladt i følgende scenarier:

  - Et venstre jokertegn skal efterfølges af et punktum for at angive et underdomæne. (gælder kun for blokke)

    Er f.eks `*.contoso.com` . tilladt. `*contoso.com` Er ikke tilladt.

  - Et jokertegn til højre skal følge en skråstreg (/) for at angive en sti.

    Er f.eks `contoso.com/*` . tilladt, `contoso.com*` eller `contoso.com/ab*` er ikke tilladt.

  - `*.com*` er ugyldigt (ikke et domæne, der kan isoleres, og det højre jokertegn følger ikke en skråstreg).

  - Jokertegn er ikke tilladt i IP-adresser.

- Tildetegnet (~) er tilgængeligt i følgende scenarier:

  - Et venstre tilde angiver et domæne og alle underdomæner.

    Omfatter `contoso.com` f.eks. `~contoso.com` og `*.contoso.com`.

- Et brugernavn eller en adgangskode understøttes eller kræves ikke.

- Anførselstegn (' eller ") er ugyldige tegn.

- En URL-adresse skal indeholde alle omdirigeringer, hvor det er muligt.

### <a name="url-entry-scenarios"></a>Url-adresseindtastningsscenarier

Gyldige URL-adresser og deres resultater er beskrevet i følgende afsnit.

#### <a name="scenario-no-wildcards"></a>Scenarie: Ingen jokertegn

**Indtastning**: `contoso.com`

- **Tillad match**: contoso.com

- **Tillad ikke matchet**:
  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blokmatch**:
  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blok, der ikke stemmer overens**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scenarie: Venstre jokertegn (underdomæne)

> [!NOTE]
> Dette scenarie gælder kun for blokke.

**Indtastning**: `*.contoso.com`

- **Blokmatch**:
  - www.contoso.com
  - xyz.abc.contoso.com

- **Blok, der ikke stemmer overens**:
  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scenarie: Højre jokertegn øverst på stien

**Indtastning**: `contoso.com/a/*`

- **Tillad match** og **blokmatch**:
  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:
  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scenarie: Venstre tilde

**Indtastning**: `~contoso.com`

- **Tillad match** og **blokmatch**:
  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:
  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Scenarie: Højre jokertegnsuffiks

**Indtastning**: `contoso.com/*`

- **Tillad match** og **blokmatch**:
  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Scenarie: Underdomæne for venstre jokertegn og højre jokertegnsuffiks

> [!NOTE]
> Dette scenarie gælder kun for blokke.

**Indtastning**: `*.contoso.com/*`

- **Blokmatch**:
  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Blok, der ikke stemmer overens**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scenarie: Venstre og højre tilde

**Indtastning**: `~contoso.com~`

- **Tillad match** og **blokmatch**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Scenarie: IP-adresse

**Indtastning**: `1.2.3.4`

- **Tillad match** og **blokmatch**: 1.2.3.4

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>IP-adresse med højre jokertegn

**Indtastning**: `1.2.3.4/*`

- **Tillad match** og **blokmatch**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Eksempler på ugyldige poster

Følgende poster er ugyldige:

- **Manglende eller ugyldige domæneværdier**:

  - Contoso
  - \*.contoso.\*
  - \*.com
  - \*.pdf

- **Jokertegn på tekst eller uden afstandstegn**:

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

  - conto\*so.com
  - conto~so.com

- **Dobbelte jokertegn**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Domæneparsyntaks for spoofede afsenderposter på listen over tilladte/blokerede lejere

Et domænepar for en spoofed afsender på listen over tilladte/blokerede lejere bruger følgende syntaks: `<Spoofed user>, <Sending infrastructure>`.

- **Spoofed bruger**: Denne værdi omfatter mailadressen på den spoofede bruger, der vises i feltet **Fra** i mailklienter. Denne adresse kaldes også adressen `5322.From` . Gyldige værdier omfatter:
  - En individuel mailadresse (f.eks. chris@contoso.com).
  - Et maildomæne (f.eks. contoso.com).
  - Jokertegnet (f.eks. \*).

- **Sender infrastruktur**: Denne værdi angiver kilden til meddelelser fra den spoofede bruger. Gyldige værdier omfatter:
  - Domænet, der blev fundet i et omvendt DNS-opslag (PTR-post) for kildemailserverens IP-adresse (f.eks. fabrikam.com).
  - Hvis kildens IP-adresse ikke har nogen PTR-post, identificeres den afsendende infrastruktur som \<source IP\>/24 (f.eks. 192.168.100.100/24).

Her er nogle eksempler på gyldige domænepar, der identificerer spoofede afsendere:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Det maksimale antal spoofede afsenderposter er 1000.

Tilføjelse af et domænepar tillader eller blokerer kun *kombinationen* af den spoofede bruger *og* den afsendende infrastruktur. Den tillader ikke mail fra den spoofede bruger fra nogen kilde og tillader heller ikke mail fra den afsendende infrastrukturkilde for en spoofed bruger.

Du kan f.eks. tilføje en tilladelsespost for følgende domænepar:

- **Domæne**: gmail.com
- **Infrastruktur**: tms.mx.com

Det er kun meddelelser fra dette domæne *og* det afsendende infrastrukturpar, der må spoof. Andre afsendere, der forsøger at spoof gmail.com, er ikke tilladt. Meddelelser fra afsendere i andre domæner, der stammer fra tms.mx.com kontrolleres af spoof intelligence.


## <a name="what-to-expect-after-you-add-an-allow-or-block-entry"></a>Hvad kan du forvente, når du har tilføjet en tilladelses- eller blokindtastning?

Når du har tilføjet en tilladelsespost via indsendelsesportalen eller en blokpost på lejerlisten tillad/bloker, skal posten begynde at fungere med det samme.

Vi anbefaler, at du lader poster udløbe automatisk efter 30 dage for at se, om systemet har lært om tillad eller blok. Hvis ikke, skal du angive en ny post for at give systemet yderligere 30 dage til at lære.
