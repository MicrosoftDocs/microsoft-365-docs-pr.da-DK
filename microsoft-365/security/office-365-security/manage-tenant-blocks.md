---
title: Administrer dine blokke på listen over tilladte/blokerede lejere
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
description: Administratorer kan få mere at vide om, hvordan de konfigurerer blokke på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1ea87a29d93c43b89bcfb482d185bd4b397dcc5b
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862450"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Tilføj blokerede på listen over tilladte/blokerede lejere

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender-portalen 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Opret afsenderposter for blokering på listen over tilladte/blokerede lejere

1. I Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker** \> **Regler** for \> **lejer tillad/bloker lister**.

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
> Mails fra disse afsendere vil blive blokeret som *høj tillid spam (SCL = 9)*. 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Opret blokerings-URL-adresser på listen over tilladte/blokerede lejere

1. I Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker** \> **Regler** for \> **lejer tillad/bloker lister**.

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
> De mails, der indeholder disse URL-adresser, blokeres som *phish*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Opret blokfilposter på listen over tilladte/blokerede lejere

1. I Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker** \> **Regler** for \> **lejer tillad/bloker lister**.

2. På siden **Liste over tilladte/blokerede lejere** skal du vælge fanen **Filer** og derefter klikke på ![ikonet Bloker.](../../media/m365-cc-sc-create-icon.png) **Blok.**

3. Konfigurer følgende indstillinger i pop op-vinduet **Bloker filer** , der vises:
   - **Tilføj filhashes**: Angiv én SHA256-hashværdi pr. linje op til maksimalt 20.
   - **Udløber aldrig**: Benyt en af følgende fremgangsmåder:
     - Kontrollér, at indstillingen er slået fra (![Til/fra](../../media/scc-toggle-off.png)), og brug feltet **Fjern den** til at angive udløbsdatoen for posterne.

     Eller

     - Flyt til/fra-knappen til højre for at konfigurere posterne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv en beskrivende tekst til posterne.

4. Klik på **Tilføj**, når du er færdig.

> [!NOTE]
> De mails, der indeholder disse filer, blokeres som *malware*. 

### <a name="create-spoofed-sender-block-entries"></a>Opret spoofed afsenderblokposter

**Noter**:

- Kun _kombinationen_ af den spoofede bruger _og_ den afsendende infrastruktur, som defineret i domæneparret, er specifikt tilladt eller blokeret fra spoofing.
- Når du konfigurerer en tilladelses- eller blokpost for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i indsigten spoof intelligence.
- Poster for spoofed afsendere udløber aldrig.
- Spoof understøtter både tillad og blok.

1. I Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker** \> **Regler** for \> **lejer tillad/bloker lister**.

2. På siden **Liste over tilladte/blokerede lejere** skal du vælge fanen **Spoofing** og derefter klikke på ![ikonet Bloker.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop op-vinduet **Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje op til maksimalt 20. Du kan finde flere oplysninger om syntaksen for spoofede afsenderposter under [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Intern**: Den spoofede afsender er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Den spoofede afsender er i et eksternt domæne.
   - **Handling**: Vælg **Tillad** eller **Bloker**.

4. Klik på **Tilføj**, når du er færdig.

## <a name="use-powershell"></a>Brug PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Føj afsender-, fil- eller URL-adresser for blokering til listen over tilladte/blokerede lejere

Hvis du vil tilføje afsender-, fil- eller URL-adresser på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

I dette eksempel tilføjes en post for afsenderblokering for den angivne afsender, der udløber på en bestemt dato.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

I dette eksempel tilføjes en blokfilpost for de angivne filer, der aldrig udløber.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

I dette eksempel tilføjes en url-adressepost for blokering for contoso.com og alle underdomæner (f.eks. contoso.com, www.contoso.com og xyz.abc.contoso.com). Da vi ikke brugte parametrene ExpirationDate eller NoExpiration, udløber posten efter 30 dage.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Tilføj spoofed afsenderblokposter 

Hvis du vil tilføje spoofede afsenderposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
