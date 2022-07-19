---
title: Tillad eller bloker filer ved hjælp af listen Tillad/bloker lejer
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
description: Administratorer kan få mere at vide om, hvordan de tillader eller blokerer filer på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a85af4beda791fb9cc2382a48a701406941d0325
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/21/2022
ms.locfileid: "66858771"
---
# <a name="allow-or-block-files-using-the-tenant-allowblock-list"></a>Tillad eller bloker filer ved hjælp af listen Tillad/bloker lejer

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du kan bruge Microsoft 365 Defender-portalen eller PowerShell til at tillade eller blokere filer på listen over tilladte/blokerede lejere.

## <a name="create-block-file-entries"></a>Opret blokfilposter 

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

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
> De mails, der indeholder disse filer, blokeres som _malware_.

### <a name="use-powershell"></a>Brug PowerShell

Hvis du vil tilføje blokfilposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListItems -ListType <FileHash> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

I dette eksempel tilføjes en blokfilpost for de angivne filer, der aldrig udløber.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-file-entries"></a>Opret tillad filposter

### <a name="use-microsoft-365-defender"></a>Brug Microsoft 365 Defender

Tillad filer på siden **Indsendelser** i Microsoft 365 Defender.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge fanen **Vedhæftede filer i mails** og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje filen eller filerne.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Aktivér indstillingen **Tillad filer som denne** .

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Tilføj, hvorfor du tilføjer Tillad ved hjælp af den **valgfri note**. 

8. Når du er færdig, skal du klikke på knappen **Send** .

  :::image type="content" source="../../media/submit-email-for-analysis.png" alt-text="Send mail til analyse." lightbox="../../media/submit-email-for-analysis.png":::

> [!NOTE]
>
> Når filen registreres igen, sendes den ikke til detonation eller kontrol af omdømme, og alle andre filbaserede filtre springes over. Hvis resten af filtrene under mailflowet finder den mail, der indeholder den fil, der skal renses, leveres mailen.

## <a name="view-file-entries"></a>Vis filposter 

Hvis du vil have vist blokfilposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Get-TenantAllowBlockListItems -ListType <FileHash> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

I dette eksempel returneres oplysninger om den angivne filhashværdi.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-file-entries"></a>Rediger filposter

Hvis du vil redigere tilladte eller blokere filposter på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-file-entries"></a>Fjern filposter 

Hvis du vil fjerne tillad eller blokere filposter fra listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN">
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>Relaterede artikler

- [Administratorindsendelser](admin-submission.md)
- [Rapportér falske positiver og falske negativer](report-false-positives-and-false-negatives.md)
- [Administrer dine tilladelser og blokke på listen over tilladte/blokerede lejere](manage-tenant-allow-block-list.md)
- [Tillad eller bloker mails på listen over tilladte/blokerede lejere](allow-block-email-spoof.md)
- [Tillad eller bloker URL-adresser på listen over tilladte/blokerede lejere](allow-block-urls.md)
