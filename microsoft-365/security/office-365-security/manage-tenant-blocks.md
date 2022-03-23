---
title: Administrer dine blokke på lejerens tilladelses-/blokeringsliste
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
description: Administratorer kan lære, hvordan de konfigurerer blokke i lejerens tilladelses-/blokeringsliste i sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cca466ce4862cc93ec7521bf6bd00fe960f06a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592303"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Tilføj blokke på lejerens tilladelses-/blokeringsliste

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender portalen 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Opret blokerede afsenderposter på lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. På siden **Lejers tilladelses-/blokeringsliste** skal du bekræfte, at **fanen** Afsendere er markeret og derefter klikke på ![Bloker ikon.](../../media/m365-cc-sc-create-icon.png) **Bloker**.

3. I pop **op-menuen Bloker** afsendere, der vises, skal du konfigurere følgende indstillinger:
   - **Afsendermailadresser eller domæner**: Angiv én afsender (mailadresse eller domæne) pr. linje, op til maksimalt 20.
   - **Udløber aldrig**: Gør et af følgende:
     - Kontrollér, at indstillingen er slået fra (![til/](../../media/scc-toggle-off.png)fra). Brug feltet **Fjern** til til at angive udløbsdatoen for posterne.

       eller

     - Flyt til/fra-knappen til højre for at konfigurere indtastningerne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv beskrivende tekst til posterne.

4. Klik på Tilføj, når du er **færdig**.

> [!NOTE]
> Mails fra disse afsendere blokeres som *spam*. 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Oprette blokerede URL-poster på lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. På siden **Lejers tilladelses-/blokeringsliste** skal du bekræfte, at **fanen URL-adresser** er markeret, og derefter skal du klikke på ![Bloker-ikon.](../../media/m365-cc-sc-create-icon.png) **Bloker**.

3. I pop **op-pop op-menuen** Bloker URL-adresser, der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj URL-adresser med jokertegn**: Angiv én URL-adresse pr. linje, op til maksimalt 20. Hvis du vil have mere at vide om syntaksen for URL-poster, skal du se afsnittet URL-syntaks [i Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).
   - **Udløber aldrig**: Gør et af følgende:
     - Kontrollér, at indstillingen er slået fra (![til/](../../media/scc-toggle-off.png)fra). Brug feltet **Fjern** til til at angive udløbsdatoen for posterne.

       eller

     - Flyt til/fra-knappen til højre for at konfigurere indtastningerne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv beskrivende tekst til posterne.

4. Klik på Tilføj, når du er **færdig**.

> [!NOTE]
> De mails, der indeholder disse URL-adresser, blokeres som *phish*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Oprette blokfilposter på lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. På siden **Lejers tilladelses-/blokeringsliste** skal du **vælge fanen** Filer og derefter klikke på ![Blokikon.](../../media/m365-cc-sc-create-icon.png) **Bloker**.

3. I pop **op-menuen** Bloker filer, der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj filhashes**: Angiv én SHA256-hash-værdi pr. linje, op til maksimalt 20.
   - **Udløber aldrig**: Gør et af følgende:
     - Kontrollér, at indstillingen er slået fra (![til/](../../media/scc-toggle-off.png)fra). Brug feltet **Fjern** til til at angive udløbsdatoen for posterne.

     eller

     - Flyt til/fra-knappen til højre for at konfigurere indtastningerne til aldrig at udløbe: ![Slå til.](../../media/scc-toggle-on.png).
   - **Valgfri note**: Angiv beskrivende tekst til posterne.

4. Klik på Tilføj, når du er **færdig**.

> [!NOTE]
> De mails, der indeholder disse filer, blokeres som *malware*. 

### <a name="create-spoofed-sender-block-entries"></a>Oprette uønskede afsenderblokeringsposter

**Bemærkninger**:

- Kun kombinationen _af_ den efterlignede bruger og afsendende infrastruktur som defineret i domæneparret er specifikt tilladt eller blokeret mod spoofing.
- Når du konfigurerer en tillad eller bloker indtastning for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i efterlignet intelligensindsigt.
- Poster for spoofed afsendere udløber aldrig.
- Spoof understøtter både tillad og blok.

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. På siden **Lejers tilladelses-/** blokliste skal du **vælge fanen Spoofing** og derefter klikke på ![Bloker ikon.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop **op-menuen Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje, op til maksimalt 20. Hvis du vil have mere at vide om syntaksen for efterlignede afsenderposter, skal du [se Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Internt**: Afsenderen er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Spoof-afsenderen er i et eksternt domæne.
   - **Handling**: Vælg **Tillad** eller **Bloker**.

4. Klik på Tilføj, når du er **færdig**.

## <a name="use-powershell"></a>Brug PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Føj poster for blokering af afsender, fil eller URL-adresse til lejerens tilladelses-/blokeringsliste

Hvis du vil tilføje poster for blokeret afsender, fil eller URL-adresse på lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

I dette eksempel tilføjes en post af uønsket mail for den angivne afsender, der udløber på en bestemt dato.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

I dette eksempel tilføjes en blokfilpost for de angivne filer, der aldrig udløber.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

I dette eksempel tilføjes en URL-post for contoso.com og alle underdomæner (f.eks. contoso.com, www.contoso.com og xyz.abc.contoso.com). Da vi ikke brugte parametrene ExpirationDate eller NoExpiration, udløber posten efter 30 dage.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Tilføj efterlignede afsenderblokeringsposter 

Hvis du vil tilføje efterlignede afsenderposter på listen Lejers tilladelse/blokering, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
