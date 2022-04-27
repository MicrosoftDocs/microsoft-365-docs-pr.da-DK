---
title: Administrer dine tilladelser på listen over tilladte/blokerede lejere
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
description: Administratorer kan få mere at vide om, hvordan de konfigurerer tillad på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ad2ef693848b664be6ec9b48cc4fc320a8b4b9c2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090138"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Tilføj tilladte på listen over tilladte/blokerede lejere

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorer kan ikke føje tillad direkte til listen over tilladte/blokerede lejere. Du kan i stedet bruge indsendelsesprocessen for administratoren til at sende den meddelelse, der blev blokeret, så den tilsvarende URL-adresse, fil og/eller afsendere føjes til listen over tilladte/blokerede lejere. Hvis der ikke er sket en blokering af filen, URL-adressen eller afsenderen, oprettes tilladn ikke. I de fleste tilfælde, hvor meddelelsen blev bestemt til at være en falsk positiv, der blev blokeret forkert, bevares tillader så længe det er nødvendigt for at give systemet tid til at tillade dem naturligt.

> [!IMPORTANT]
> Da Microsoft administrerer giver dig mulighed for, vil afsender, URL-adresse eller fil tillader, der ikke er nødvendige eller anses for at være dårlige, blive fjernet. Dette er for at beskytte dit miljø og forhindre en forkert konfiguration af tillader. I de tilfælde, hvor du kan være uenig, kan det være nødvendigt med en supportsag for at fastslå, hvorfor en meddelelse stadig anses for at være dårlig.

## <a name="add-sender-allows-using-the-submissions-portal"></a>Tilføj afsender gør det muligt at bruge indsendelsesportalen

Tillad afsendere (eller domæner) på siden **Indsendelser** i Microsoft 365 Defender.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du kontrollere, at fanen **Mails** er valgt, og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje netværksmeddelelses-id'et eller uploade mailfilen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Slå **Tillad meddelelser som denne** indstilling til.

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Når du er færdig, skal du klikke på knappen **Send** .

> ![Indsend malware til Microsoft til et analyseeksempel.](../../media/admin-submission-allow-messages.png)

## <a name="add-url-allows-using-the-submissions-portal"></a>Tilføj URL-adresse gør det muligt at bruge portalen Indsendelser

Tillad URL-adresser på siden **Indsendelser** i Microsoft 365 Defender.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge fanen **URL-adresser** og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje URL-adressen.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Aktivér indstillingen **Tillad URL-adresser som denne** .

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Når du er færdig, skal du klikke på knappen **Send** .

> [!div class="mx-imgBorder"]
> ![Send URL-adresse til analyse.](../../media/submit-url-for-analysis.png)

## <a name="add-file-allows-using-the-submissions-portal"></a>Tilføj fil gør det muligt at bruge indsendelsesportalen

Tillad filer på siden **Indsendelser** i Microsoft 365 Defender.

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Handlinger & indsendelser** \> **.** Du kan også gå direkte til siden **Indsendelser** ved at bruge <https://security.microsoft.com/reportsubmission>.

2. På siden **Indsendelser** skal du vælge fanen **Vedhæftede filer i mails** og derefter klikke på ![Send til Microsoft til analyseikonet.](../../media/m365-cc-sc-create-icon.png) **Send til Microsoft til analyse**.

3. Brug pop op-vinduet **Send til Microsoft til gennemsyn til** at sende en meddelelse ved at tilføje filen eller filerne.

4. I afsnittet **Vælg en årsag til afsendelse til Microsoft** skal du vælge **Burde ikke være blokeret (falsk positiv)**.

5. Aktivér indstillingen **Tillad filer som denne** .

6. På rullelisten **Fjern efter** skal du angive, hvor længe indstillingen tillad skal fungere.

7. Når du er færdig, skal du klikke på knappen **Send** .

> [!div class="mx-imgBorder"]
> ![Send mail til analyse.](../../media/submit-email-for-analysis.png)

## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Opret spoofed afsender tillade poster ved hjælp af Microsoft 365 Defender

> [!NOTE]
>
> - Kun _kombinationen_ af den spoofede bruger _og_ den afsendende infrastruktur, som defineret i domæneparret, er specifikt tilladt eller blokeret fra spoofing.
> - Når du konfigurerer en tilladelses- eller blokpost for et domænepar, vises meddelelser fra det pågældende domænepar ikke længere i indsigten spoof intelligence.
> - Poster for spoofed afsendere udløber aldrig.
> - Spoof understøtter både tillad og blok. URL-adressen understøtter kun Tillad.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Lejer tillad/bloker lister** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Med lejer-/bloklister** , skal du bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. På siden **Liste over tilladte/blokerede lejere** skal du vælge fanen **Spoofing** og derefter klikke på ![Ikonet Tilføj.](../../media/m365-cc-sc-create-icon.png) **Tilføj**.

3. I pop op-vinduet **Tilføj nye domænepar** , der vises, skal du konfigurere følgende indstillinger:
   - **Tilføj nye domænepar med jokertegn**: Angiv ét domænepar pr. linje op til maksimalt 20. Du kan finde flere oplysninger om syntaksen for spoofede afsenderposter under [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
   - **Spoof-type**: Vælg en af følgende værdier:
     - **Intern**: Den spoofede afsender er i et domæne, der tilhører din organisation (et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Ekstern**: Den spoofede afsender er i et eksternt domæne.
   - **Handling**: Vælg **Tillad**.

4. Klik på **Tilføj**, når du er færdig.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>Tilføj tilladte poster for spoofed afsender ved hjælp af PowerShell

Hvis du vil tilføje spoofede afsenderposter på listen over tilladte/blokerede lejere i [Exchange Online PowerShell](/exchange/connect-to-exchange-online-powershell), skal du bruge følgende syntaks:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>Relaterede artikler

- [Administratorindsendelser](admin-submission.md)
- [Rapportér falske positiver og falske negativer](report-false-positives-and-false-negatives.md)
