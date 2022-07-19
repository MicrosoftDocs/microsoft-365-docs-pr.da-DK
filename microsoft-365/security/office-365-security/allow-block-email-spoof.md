---
title: Tillad eller bloker mails ved hjælp af listen Tillad/bloker lejer
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
- MET150
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om, hvordan de tillader eller blokerer mails og forfalskede afsenderposter på lejerlisten tillad/bloker på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a16a8234b1d0ff2a3647d7f66923faa66784ea72
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858858"
---
# <a name="allow-or-block-emails-using-the-tenant-allowblock-list"></a>Tillad eller bloker mails ved hjælp af listen Tillad/bloker lejer

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du kan bruge Microsoft 365 Defender-portalen eller PowerShell til at tillade eller blokere mails (herunder spoofing-mails) ved hjælp af lejerens tilladelses-/blokliste.

## <a name="create-block-sender-entries"></a>Opret afsenderposter for blok 

### <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender-portalen

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. På siden **Liste over tilladte/blokerede lejere** skal du kontrollere, at fanen **Afsendere** er valgt, og derefter klikke på ![ikonet Bloker.](../../media/m365-cc-sc-create-icon.png) **Blok.**

3. Konfigurer følgende indstillinger i pop op-vinduet **Bloker afsendere** , der vises:
   - **Afsendermailadresser eller domæner**: Angiv én afsender (mailadresse eller domæne) pr. linje op til maksimalt 20.
   - **Udløber aldrig**: Benyt en af følgende fremgangsmåder:
     - Kontrollér, at indstillingen er slået fra (![Til/fra](../../media/scc-toggle-off.png)), og brug feltet **Fjern den** til at angive udløbsdatoen for posterne.

       Eller

     - Flyt til/fra-knappen til højre for at konfigurere posterne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv en beskrivende tekst til posterne.

4. Klik på **Tilføj**, når du er færdig.

> [!NOTE]
> Mails fra disse afsendere vil blive blokeret som _spam med høj tillid_ (SCL = 9).

### <a name="use-powershell"></a>Brug PowerShell

Hvis du vil tilføje afsenderposter for bloker på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListItems -ListType <Sender> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

I dette eksempel tilføjes en post for afsenderblokering for den angivne afsender, der udløber på en bestemt dato.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-sender-entries"></a>Opret tillad afsenderposter 

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

Tillad afsendere (eller domæner) på siden **Indsendelser** i Microsoft 365 Defender.

Du kan ikke direkte ændre listen over tilladte lejere/blokeringer for at tilføje tilladte poster. Brug i stedet [administratorindsendelser](admin-submission.md) til at sende den blokerede meddelelse. Denne handling føjer den tilsvarende URL-adresse, fil, misvisende afsenderdomænepar, repræsenteret domæne (eller bruger) og/eller afsender til listen over tilladte/blokerede lejere. Hvis elementet ikke er blokeret, oprettes tilladn ikke. I de fleste tilfælde, hvor meddelelsen blev bestemt til at være en falsk positiv, der var blokeret forkert, fjernes den tilladte post på den angivne udløbsdato.

> [!IMPORTANT]
> - Da Microsoft administrerer de tilladte poster for dig, fjernes unødvendige afsendere, URL-adresser eller filer, der ikke er nødvendige. Denne funktionsmåde beskytter din organisation og hjælper med at forhindre forkert konfigurerede tilladte poster. Hvis du er uenig i dommen, skal du muligvis åbne en supportsag for at finde ud af, hvorfor en meddelelse stadig betragtes som dårlig.


1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du kontrollere, at fanen **Mails** er valgt, og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje netværksmeddelelses-id'et eller uploade mailfilen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Slå **Tillad meddelelser som denne** indstilling til.

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Tilføj, hvorfor du tilføjer tillad ved hjælp af feltet **Valgfri note** . 

8. Når du er færdig, skal du vælge knappen **Send** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Indsend malware til Microsoft til et analyseeksempel." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - Under mailflowet tilføjes , afhængigt af hvilke filtre der har bestemt, at mailen er skadelig. Afsenderen og URL-adressen bestemmes f.eks. til at være ugyldige. Der tilføjes en tilladelse for hver enkelt.
> - Når enheden (afsender, domæne, URL-adresse og fil) registreres igen, springes alle filtre, der er knyttet til objektet, over.
> - Hvis resten af filtrene under mailflowet finder, at den mail, der indeholder denne enhed, skal være ren, leveres mailen. En afsenders tilladelse (når godkendelse passerer) tilsidesætter f.eks. alle domme undtagen malware og phishing med høj tillid, der er knyttet til en vedhæftet fil eller URL-adresse.

## <a name="view-sender-entries"></a>Vis afsenderposter 

Hvis du vil have vist afsenderblokeringsposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```
Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-sender-entries"></a>Rediger afsenderposter 

Hvis du vil ændre afsenderposter for tilladelse eller blokering på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-sender-entries"></a>Fjern afsenderposter 

Hvis du vil fjerne afsenderposter, der er tilladt eller blokeret, fra listen over tilladte lejere/blokeringer, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN">
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="domain-pair-syntax-for-spoofed-sender-entries"></a>Domæneparsyntaks for spoofede afsenderposter

Et domænepar for en spoofed afsender på listen over tilladte/blokerede lejere bruger følgende syntaks: `<Spoofed user>, <Sending infrastructure>`.

- **Spoofed bruger**: Denne værdi omfatter mailadressen på den spoofede bruger, der vises i feltet **Fra** i mailklienter. Denne adresse kaldes også adressen `5322.From` . Gyldige værdier omfatter:
  - En individuel mailadresse (f.eks. chris@contoso.com).
  - Et maildomæne (f.eks. contoso.com).
  - Jokertegnet (f.eks. \*).

- **Sender infrastruktur**: Denne værdi angiver kilden til meddelelser fra den spoofede bruger. Gyldige værdier omfatter:
  - Domænet, der blev fundet i et omvendt DNS-opslag (PTR-post) for kildemailserverens IP-adresse (f.eks. fabrikam.com).
  - Hvis kildens IP-adresse ikke har nogen PTR-post, identificeres den afsendende infrastruktur som \<source IP\>/24 (f.eks. 192.168.100.100/24).
  - Et bekræftet DKIM-domæne.

Her er nogle eksempler på gyldige domænepar, der identificerer spoofede afsendere:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Det maksimale antal spoofede afsenderposter er 1000.

Tilføjelse af et domænepar tillader eller blokerer kun *kombinationen* af den spoofede bruger *og* den afsendende infrastruktur. Den tillader ikke mail fra den spoofede bruger fra nogen kilde og tillader heller ikke mail fra den afsendende infrastrukturkilde for en spoofed bruger.

Du kan f.eks. tilføje en tilladelsespost for følgende domænepar:

- **Domæne**: gmail.com
- **Infrastruktur**: tms.mx.com

Det er kun meddelelser fra dette domæne _og_ det afsendende infrastrukturpar, der må spoof. Andre afsendere, der forsøger at spoof gmail.com, er ikke tilladt. Meddelelser fra afsendere i andre domæner, der stammer fra tms.mx.com kontrolleres af spoof intelligence.

## <a name="create-blocked-spoofed-sender-entries"></a>Opret blokerede spoofed afsenderposter

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

> [!NOTE]
> Mail fra disse afsendere blokeres som _phish_.
>
> Kun _kombinationen_ af den spoofede bruger _og_ den afsendende infrastruktur, som defineret i domæneparret, er specifikt tilladt eller blokeret fra spoofing.
>
> Når du konfigurerer en tilladelses- eller blokpost for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i indsigten spoof intelligence.
>
> Poster for spoofed afsendere udløber aldrig.

1. I Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker** \> **Regler** for \> **lejer tillad/bloker lister**.

2. På siden **Liste over tilladte/blokerede lejere** skal du vælge fanen **Spoofing** og derefter klikke på ![ikonet Bloker.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop op-vinduet **Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje op til maksimalt 20. Du kan finde flere oplysninger om syntaksen for spoofede afsenderposter under [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Intern**: Den spoofede afsender er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Den spoofede afsender er i et eksternt domæne.
   - **Handling**: Vælg **Blok**.

4. Klik på **Tilføj**, når du er færdig.

> [!NOTE]
> Mails fra disse afsendere blokeres som _phish_.

### <a name="use-powershell"></a>Brug PowerShell

Hvis du vil tilføje spoofede afsenderposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="create-allowed-spoofed-sender-entries"></a>Opret tilladte spoofed afsenderposter 

### <a name="use-the-tenant-allowblock-list-in-microsoft-365-defender"></a>Brug lejerlisten tillad/bloker i Microsoft 365 Defender

> [!NOTE]
>
> - Kun _kombinationen_ af den spoofede bruger _og_ den afsendende infrastruktur, som defineret i domæneparret, er specifikt tilladt eller blokeret fra spoofing.
> - Når du konfigurerer en tilladelses- eller blokpost for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i indsigten spoof intelligence.
> - Poster for spoofed afsendere udløber aldrig.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Med lejer-/bloklister** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. På siden **Liste over tilladte/blokerede lejere** skal du vælge fanen **Spoofing** og derefter klikke på ![Ikonet Tilføj.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop op-vinduet **Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje op til maksimalt 20. Du kan finde flere oplysninger om syntaksen for spoofede afsenderposter under [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Intern**: Den spoofede afsender er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Den spoofede afsender er i et eksternt domæne.
   - **Handling**: Vælg **Tillad**.

4. Klik på **Tilføj**, når du er færdig.

### <a name="use-admin-submission-in-microsoft-365-defender"></a>Brug Administration afsendelse i Microsoft 365 Defender

Du kan også tillade spoofede afsendere ved hjælp af siden **Indsendelser** i Microsoft 365 Defender.

Brug [administratorindsendelser](admin-submission.md) til at sende den blokerede meddelelse. Denne handling føjer den tilsvarende URL-adresse, fil, misvisende afsenderdomænepar, repræsenteret domæne (eller bruger) og/eller afsender til listen over tilladte/blokerede lejere. Hvis elementet ikke er blokeret, oprettes tilladn ikke. 

> [!IMPORTANT]
>
> - Spoof tillader at tage sig af intra-org, cross-org og DMARC spoofing.
> - Den valgfri note i indsendelsen af administratoren gælder ikke for spoof-tillader.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du kontrollere, at fanen **Mails** er valgt, og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje netværksmeddelelses-id'et eller uploade mailfilen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Slå **Tillad meddelelser som denne** indstilling til.

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere, selvom den ikke gælder for spoof allow, da de aldrig udløber.

7. Når du er færdig, skal du vælge knappen **Send** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Indsend malware til Microsoft til et analyseeksempel." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - Det spoofed afsenderdomænepar bliver oprettet og synligt på fanen **Spoofed** under **listesiden For lejer tillader/bloker** .


### <a name="use-powershell"></a>Brug PowerShell

Hvis du vil tilføje spoofede afsenderposter på listen over tilladte/blokerede lejere i [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell), skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

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

## <a name="modify-spoofed-sender-entries"></a>Rediger spoofed afsenderposter 

Hvis du vil ændre poster af typen Tillad eller bloker efterligning af afsendere på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

I dette eksempel ændres den spoofede afsenderpost fra Allow til Block.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

## <a name="remove-spoofed-sender-entries"></a>Fjern spoofed afsenderposter 

Brug følgende syntaks til at fjerne tilladelse til eller blokering af afsenderposter fra listen over tilladte/blokerede lejere:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).

## <a name="create-impersonated-sender-entries"></a>Opret repræsenterede afsenderposter

### <a name="use-admin-submission-in-microsoft-365-defender"></a>Brug Administration afsendelse i Microsoft 365 Defender

Du kan også tillade repræsenterede afsendere ved hjælp af siden **Indsendelser** i Microsoft 365 Defender.

Brug [administratorindsendelser](admin-submission.md) til at sende den blokerede meddelelse. Denne handling føjer den tilsvarende URL-adresse, fil, misvisende afsenderdomænepar, repræsenteret domæne (eller bruger) og/eller afsender til listen over tilladte/blokerede lejere. Hvis elementet ikke er blokeret, oprettes tilladn ikke. 

> [!IMPORTANT]
>
> - Repræsentation gør det muligt at tage sig af domæne- og bruger repræsentation.
> - Graph-repræsentation er ikke taget pleje herfra i øjeblikket.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du kontrollere, at fanen **Mails** er valgt, og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje netværksmeddelelses-id'et eller uploade mailfilen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Slå **Tillad meddelelser som denne** indstilling til.

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere, selvom den ikke gælder for repræsenterede tillad, da de aldrig udløber.

7. Når du er færdig, skal du vælge knappen **Send** .

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="Indsend malware til Microsoft til et analyseeksempel." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
> Det repræsenterede domæne (eller bruger) oprettes og er synligt i afsnittet **Afsendere og domæner, der er tillid til** i politikken til bekæmpelse af phishing på <https://security.microsoft.com/antiphishing>.

## <a name="related-articles"></a>Relaterede artikler

- [Administratorindsendelser](admin-submission.md)
- [Rapportér falske positiver og falske negativer](report-false-positives-and-false-negatives.md)
- [Administrer dine tilladelser og blokke på listen over tilladte/blokerede lejere](manage-tenant-allow-block-list.md)
- [Tillad eller bloker filer på listen over tilladte/blokerede lejere](allow-block-files.md)
- [Tillad eller bloker URL-adresser på listen over tilladte/blokerede lejere](allow-block-urls.md)
