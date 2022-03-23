---
title: Administrer din tilladelse i lejerens tilladelses-/blokeringsliste
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
description: Administratorer kan lære, hvordan de konfigurerer tillader i lejerens tilladelses-/blokeringsliste i sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3823290e9f239b14e4bf97fe1ae8ef7020561697
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592509"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Tilføj giver tilladelse i lejerens tilladelses-/blokeringsliste

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorer kan ikke tilføje tilladelse direkte til lejerens tilladelses-/blokeringsliste. I stedet skal du bruge administratorindsendelsesprocessen til at sende den meddelelse, der blev blokeret, så den tilsvarende URL-adresse, fil og/eller afsendere bliver føjet til lejerens tilladelses-/blokeringsliste. Hvis en blok af filen, URL-adressen eller afsenderen ikke er sket, oprettes tillad ikke. I de fleste tilfælde, hvor meddelelsen blev fundet at være en falsk positiv, der blev blokeret forkert, bevares tilladelsen så længe, som det er nødvendigt, for at give systemet tid til at tillade dem naturligt.

> [!IMPORTANT]
> Da Microsoft administrerer tillader for dig, fjernes afsender, URL-adresse eller fil, der ikke er nødvendige eller betragtes som dårlige. Dette er for at beskytte dit miljø og forhindre en forkert konfiguration af tillader. I tilfælde, hvor du kan være uenig, kan der være brug for en støtte til at afgøre, hvorfor en meddelelse stadig opfattes som dårlig.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Tilføj afsender tillader brug af indsendelsesportalen 

Tillad afsendere (eller domæner) på **siden Indsendelser** i Microsoft 365 Defender. 

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå **til Handlinger & indsendelser** \> **Indsendelser**. Du kan også gå direkte til siden **Indsendelser** ved hjælp af <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du bekræfte, at **fanen Mails** er markeret, og derefter klikke på ![ikonet Send til Microsoft til analyse.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop **op-filen Send til Microsoft til** gennemsyn til at sende en meddelelse ved at tilføje netværksmeddelelses-id'et eller uploade mailfilen. 

4. I sektionen **Vælg en årsag til afsendelse til Microsoft skal** du vælge **Bør ikke have været blokeret (falsk positiv)**. 

5. Slå Tillad **meddelelser som denne indstilling** til. 

6. Angiv, **hvor længe** du vil have indstillingen Tillad til at fungere, på rullelisten Fjern efter.

7. Klik på knappen Send, når du **er** færdig.

> [!div class="mx-imgBorder"]
> ![Send malware til Microsoft for eksempel til analyse.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>Tilføj URL-adresse gør det muligt at bruge indsendelsesportalen

Tillad URL-adresser på **siden** Indsendelser i Microsoft 365 Defender.

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå **til Handlinger & indsendelser** \> **Indsendelser**. Du kan også gå direkte til siden **Indsendelser** ved hjælp af <https://security.microsoft.com/reportsubmission>.

2. Vælg fanen **URL-adresser** på siden **Indsendelser** , og klik derefter på ikonet ![Send til Microsoft til analyse.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop **op-meddelelsen Send til Microsoft til** gennemsyn til at sende en meddelelse ved at tilføje URL-adressen.

4. I sektionen **Vælg en årsag til afsendelse til Microsoft skal** du vælge **Bør ikke have været blokeret (falsk positiv)**.

5. Slå indstillingen Tillad **URL-adresser til** .

6. På **rullelisten Fjern** efter skal du angive, hvor længe du vil have indstillingen tillad til at fungere.

7. Klik på knappen Send, når du **er** færdig.

> [!div class="mx-imgBorder"]
> ![Send URL-adresse til analyse.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>Tilføj fil tillader brug af indsendelsesportalen

Tillad filer på **siden Indsendelser** i Microsoft 365 Defender.

I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå **til Handlinger & indsendelser** \> **Indsendelser**. Du kan også gå direkte til siden **Indsendelser** ved hjælp af <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser skal** du vælge fanen **Vedhæftede filer i mails** og derefter klikke på ikonet ![Send til Microsoft til analyse.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop **op-meddelelsen Send til Microsoft til** gennemsyn til at sende en meddelelse ved at tilføje filen eller filerne.

4. I sektionen **Vælg en årsag til afsendelse til Microsoft skal** du vælge **Bør ikke have været blokeret (falsk positiv)**.

5. Slå indstillingen **Tillad filer til.**

6. På **rullelisten Fjern** efter skal du angive, hvor længe du vil have indstillingen tillad til at fungere.

7. Klik på knappen Send, når du **er** færdig.

> [!div class="mx-imgBorder"]
> ![Sende mail til analyse.](../../media/submit-email-for-analysis.png)


## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Opret efterlignede afsendere tillader poster ved hjælp af Microsoft 365 Defender

> [!NOTE]
> 
> - Kun kombinationen _af_ den efterlignede bruger og afsendende infrastruktur som defineret i domæneparret er specifikt tilladt eller blokeret mod spoofing.
> - Når du konfigurerer en tillad eller bloker indtastning for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i efterlignet intelligensindsigt.
> - Poster for spoofed afsendere udløber aldrig.
> - Spoof understøtter både tillad og blok. URL-adressen understøtter kun tilladelse.

1. I portalen Microsoft 365 Defender på skal du   <https://security.microsoft.com>gå til Politikker **for** \> \> \> & samarbejde & politikker for sikkerhedstrusler **Lejerens tilladelse/** blokeringslister i **sektionen** Regler. Eller du kan bruge for at gå direkte til **siden med lejerens tilladelses-/** blokeringslister <https://security.microsoft.com/tenantAllowBlockList>.

2. På siden **Lejers tilladelses-/** blokliste skal du **vælge fanen Spoofing** og derefter klikke på ![Tilføj ikon.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop **op-menuen Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje, op til maksimalt 20. Hvis du vil have mere at vide om syntaksen for efterlignede afsenderposter, skal du [se Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Internt**: Afsenderen er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Spoof-afsenderen er i et eksternt domæne.
   - **Handling**: Vælg **Tillad** eller **Bloker**.

4. Klik på Tilføj, når du er **færdig**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>Tilføj efterlignede afsendere ved hjælp af PowerShell

Hvis du vil tilføje efterlignede afsenderposter på listen Lejers tilladelse/blokering [i Exchange Online PowerShell](/exchange/connect-to-exchange-online-powershell), skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>Relaterede artikler

- [Administratorindsendelser](admin-submission.md)
- [Rapportér falske positive og falske negativer](report-false-positives-and-false-negatives.md)
