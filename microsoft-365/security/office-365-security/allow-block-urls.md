---
title: Tillad eller bloker URL-adresser ved hjælp af listen Tillad/bloker lejer
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om, hvordan de tillader eller blokerer URL-adresser på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 69d9b4725e0a2c57dac8bb711655b9e0ff02e3e5
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/21/2022
ms.locfileid: "66858774"
---
# <a name="allow-or-block-urls-using-the-tenant-allowblock-list"></a>Tillad eller bloker URL-adresser ved hjælp af listen Tillad/bloker lejer

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du kan bruge Microsoft 365 Defender-portalen eller PowerShell til at tillade eller blokere URL-adresser på listen over tilladte/blokerede lejere.

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
  - contoso.com
  - contoso.com/q=a@contoso.com

- **Blokmatch**:
  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - contoso.com
  - contoso.com/q=a@contoso.com

- **Blok, der ikke stemmer overens**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Scenarie: Venstre jokertegn (underdomæne)

> [!NOTE]
> Dette scenarie gælder kun for blokke.

**Indtastning**: `*.contoso.com`

- **Blokmatch**:
  - contoso.com
  - xyz.abc.contoso.com

- **Blok, der ikke stemmer overens**:
  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Scenarie: Højre jokertegn øverst på stien

**Indtastning**: `contoso.com/a/*`

- **Tillad match** og **blokmatch**:
  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:
  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Scenarie: Venstre tilde

**Indtastning**: `~contoso.com`

- **Tillad match** og **blokmatch**:
  - contoso.com
  - contoso.com
  - xyz.abc.contoso.com

- **Tillad ikke matchet** , og **Blok stemmer ikke overens**:
  - 123contoso.com
  - contoso.com/abc
  - contoso.com/abc

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
  - contoso.com/a
  - contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Blok, der ikke stemmer overens**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Scenarie: Venstre og højre tilde

**Indtastning**: `~contoso.com~`

- **Tillad match** og **blokmatch**:

  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/b
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

## <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Opret blokerings-URL-adresser på listen over tilladte/blokerede lejere

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. På siden **Liste over tilladte/blokerede lejere** skal du kontrollere, at fanen **URL-adresser** er valgt, og derefter klikke på ![ikonet Bloker.](../../media/m365-cc-sc-create-icon.png) **Blok.**

3. Konfigurer følgende indstillinger i pop **op-vinduet Bloker URL-adresser** , der vises:
   - **Tilføj URL-adresser med jokertegn**: Angiv én URL-adresse pr. linje op til maksimalt 20. Du kan finde oplysninger om syntaksen for URL-adresser i afsnittet URL-syntaks i [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
   - **Udløber aldrig**: Benyt en af følgende fremgangsmåder:
     - Kontrollér, at indstillingen er slået fra (![Til/fra](../../media/scc-toggle-off.png)), og brug feltet **Fjern den** til at angive udløbsdatoen for posterne.

       Eller

     - Flyt til/fra-knappen til højre for at konfigurere posterne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv en beskrivende tekst til posterne.

4. Klik på **Tilføj**, når du er færdig.

> [!NOTE]
> De mails, der indeholder disse URL-adresser, blokeres som _phish_.

### <a name="use-powershell"></a>Brug PowerShell

Hvis du vil tilføje blokerings-URL-adresser på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListItems -ListType <Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

I dette eksempel tilføjes en url-adressepost for blokering for contoso.com og alle underdomæner (f.eks. contoso.com og xyz.abc.contoso.com). Da vi ikke brugte parametrene ExpirationDate eller NoExpiration, udløber posten efter 30 dage.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-url-entries"></a>Opret tilladte URL-adresser

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

Tillad URL-adresser på siden **Indsendelser** i Microsoft 365 Defender.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge fanen **URL-adresser** og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje URL-adressen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Aktivér indstillingen **Tillad URL-adresser som denne** .

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Tilføj, hvorfor du tilføjer Tillad ved hjælp af den **valgfri note**. 

8. Når du er færdig, skal du klikke på knappen **Send** .

    :::image type="content" source="../../media/submit-url-for-analysis.png" alt-text="Send URL-adresse til analyse" lightbox="../../media/submit-url-for-analysis.png":::

> [!NOTE]
>
> - Når URL-adressen registreres igen, sendes URL-adressen ikke til detonation eller kontrol af omdømme, og alle andre URL-baserede filtre springes over.
> - Så for en mail (der indeholder denne URL-adresse), under mailflowet, vil mailen blive leveret, hvis resten af filtrene finder, at mailen er ren.

## <a name="view-url-entries"></a>Vis URL-adresser

Hvis du vil have vist blokerede URL-adresser på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListItems -ListType <URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

I dette eksempel returneres alle blokerede URL-adresser.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-url-entries"></a>Rediger URL-adresser 

Hvis du vil ændre tilladte eller blokere URL-adresser på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

I dette eksempel ændres udløbsdatoen for den angivne blok-URL-adresse.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-url-entries"></a>Fjern URL-adresser 

Hvis du vil fjerne tilladte eller blokere URL-adresser fra listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN">
```
I dette eksempel fjernes den angivne url-adresse for blokering fra listen over tilladte/blokerede lejere.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>Relaterede artikler

- [Administratorindsendelser](admin-submission.md)
- [Rapportér falske positiver og falske negativer](report-false-positives-and-false-negatives.md)
- [Administrer dine tilladelser og blokke på listen over tilladte/blokerede lejere](manage-tenant-allow-block-list.md)
- [Tillad eller bloker filer på listen over tilladte/blokerede lejere](allow-block-files.md)
- [Tillad eller bloker mails på listen over tilladte/blokerede lejere](allow-block-email-spoof.md)
