---
title: Øg kvoten for genoprettelige elementer for postkasser i venteposition
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a8bdcbdd-9298-462f-b889-df26037a990c
description: Aktivér arkivpostkassen, og aktivér automatisk udvidende arkivering for at øge størrelsen på mappen genoprettelige elementer for en postkasse Microsoft 365.
ms.openlocfilehash: 6465a86bfbf2d7f4eaf933786d15a4747b84dd5f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587681"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Øg kvoten for genoprettelige elementer for postkasser i venteposition

Standardopbevaringspolitikken Exchange standard *MRM-politik*– der automatisk anvendes på nye postkasser i Exchange Online indeholder et opbevaringsmærke med navnet Genoprettelige elementer, som 14 dage flyttes til arkiv. Dette opbevaringsmærke flytter elementer fra mappen Genoprettelige elementer i brugerens primære postkasse til mappen Genoprettelige elementer i brugerens arkivpostkasse, efter at en opbevaringsperiode på 14 dage udløber for et element. For at dette kan ske, skal brugerens arkivpostkasse være aktiveret. Hvis arkivpostkassen ikke er aktiveret, sker der ikke noget, hvilket betyder, at elementer i mappen Genoprettelige elementer for en postkasse i venteposition ikke flyttes til arkivpostkassen efter den 14-dages opbevaringsperiode udløber. Da der ikke slettes noget fra en postkasse i venteposition, er det muligt, at lagerkvoten for mappen Genoprettelige elementer overskrides, især hvis brugerens arkivpostkasse ikke er aktiveret.

For at reducere risikoen for at overskride denne grænse øges lagerkvoten for mappen Genoprettelige elementer automatisk fra 30 GB til 100 GB, når der sættes en venteposition på en postkasse i Exchange Online. Hvis arkivpostkassen er aktiveret, øges lagerkvoten for mappen Genoprettelige elementer i arkivpostkassen også fra 30 GB til 100 GB. Hvis funktionen til automatisk udvidende arkivering i Exchange Online er aktiveret, er den samlede lagerkvote for brugerens arkivpostkasse, herunder mappen genoprettelige elementer, 1,5 TB.

 Følgende tabel opsummerer lagerkvoten for mappen Genoprettelige elementer.

| Placeringen af mappen Genoprettelige elementer | Postkasser ikke i venteposition | Postkasser i venteposition |
|:-----|:-----|:-----|
|Primær postkasse |30 GB |100 GB |
|Arkivpostkasse, herunder mappen Genoprettelige elementer <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Den oprindelige lagerkvote for arkivpostkassen er 100 GB for brugere med en Exchange Online (plan 2) licens. Når automatisk udvidende arkivering er slået til for postkasser, der er i venteposition, øges lagerkvoten for både arkivpostkassen og mappen med genoprettelige elementer til 110 GB. Ekstra arkivlagerplads (som omfatter mappen Genoprettelige elementer) på op til 1,5 TB bliver klargjort, når det er nødvendigt. Du kan finde flere oplysninger om automatisk udvidende arkivering i [Få mere at vide om automatisk udvidende arkivering](autoexpanding-archiving.md).

Når lagerkvoten for mappen Genoprettelige elementer i den primære postkasse i en venteposition er tæt på grænsen, kan du gøre følgende:

- **Aktivér arkivpostkassen, og aktivér automatisk udvidende arkivering.** Du kan aktivere en ekstra lagerkapacitet for mappen Genoprettelige elementer blot ved at aktivere arkivpostkassen og derefter aktivere den automatiske udvidende arkiveringsfunktion i Exchange Online. Dette resulterer i 110 GB til mappen Genoprettelige elementer i den primære postkasse og op til 1,5 TB kombineret lagerkapacitet til mappen Arkiv og Genoprettelige elementer. Få mere at vide under [Aktivér arkivpostkasser](enable-archive-mailboxes.md) [og Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Når du har aktiveret arkivet for en postkasse, der er tæt på at overskride lagerkvoten for mappen Genoprettelige elementer, kan du køre den administrerede mappeassistent for manuelt at udløse assistenten til at behandle postkassen, så udløbne elementer flyttes til mappen Genoprettelige elementer i arkivpostkassen. Se [Trin 4 for at](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) få vejledning. Bemærk, at andre elementer i brugerens postkasse muligvis flyttes til den nye arkivpostkasse. Overvej at fortælle brugeren, at dette kan ske, når du aktiverer arkivpostkassen.

- **Opret en brugerdefineret Exchange opbevaringspolitik for postkasser i venteposition.** Ud over at aktivere arkivpostkassen og automatisk udvide arkivering for postkasser i retslig tilbageholdelse eller In-Place Hold, kan du også oprette en brugerdefineret Exchange-opbevaringspolitik for postkasser i venteposition. Dette giver dig mulighed for at anvende en opbevaringspolitik på postkasser i venteposition, der er anderledes end standard MRM-politikken, der anvendes på postkasser, der ikke er i venteposition, og gør det muligt at anvende opbevaringsmærker, der er beregnet til postkasser i venteposition. Dette omfatter oprettelse af et nyt opbevaringsmærke til mappen Genoprettelige elementer.

Resten af dette emne beskriver de trinvise fremgangsmåder til at oprette en brugerdefineret Exchange for postkasser i venteposition.

[Trin 1: Opret et brugerdefineret opbevaringsmærke til mappen Genoprettelige elementer](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[Trin 2: Opret en ny Exchange opbevaringspolitik for postkasser i venteposition](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[Trin 3: Anvend den nye Exchange opbevaringspolitik på postkasser i venteposition](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(Valgfrit) Trin 4: Kør Administreret mappeassistent for at anvende de nye opbevaringsindstillinger](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>Trin 1: Opret et brugerdefineret opbevaringsmærke til mappen Genoprettelige elementer

Det første trin er at oprette et brugerdefineret opbevaringsmærke (kaldet et opbevaringspolitikmærke eller RPT) til mappen Genoprettelige elementer. Som beskrevet tidligere flytter dette RPT elementer fra mappen Genoprettelige elementer i brugerens primære postkasse til mappen Genoprettelige elementer i brugerens arkivpostkasse. Du skal bruge PowerShell til at oprette et RPT til mappen Genoprettelige elementer. Du kan ikke bruge Exchange Administration (EAC).

1. [Forbind at Exchange Online ved hjælp af Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando for at oprette et nyt RPT til mappen Genoprettelige elementer:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Eksempelvis opretter følgende kommando et RPT for mappen Genoprettelige elementer med navnet "Genoprettelige elementer 30 dage for postkasser i venteposition" med en opbevaringsperiode på 30 dage. Det betyder, at når et element har været i mappen Genoprettelige elementer i 30 dage, flyttes det til mappen Genoprettelige elementer i brugerens arkivpostkasse.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Vi anbefaler, at opbevaringsperioden (defineret af  _AgeLimitForRetention-parameteren_ ) for RPT for genoprettelige elementer er den samme som opbevaringsperioden for slettede elementer for de postkasser, RPT anvendes på. Dette giver en bruger hele opbevaringsperioden for slettede elementer mulighed for at gendanne slettede elementer, før de flyttes til arkivpostkassen. I det forrige eksempel blev opbevaringsperioden angivet til 30 dage baseret på den forudsætning, at opbevaringsperioden for slettede elementer for postkasser også er 30 dage. En Exchange Online postkasse er konfigureret til at bevare slettede elementer i 14 dage som standard. Men du kan ændre denne indstilling til maksimalt 30 dage. Du kan få mere at vide [under Ændre opbevaringsperioden for slettede elementer for en postkasse Exchange Online](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>Trin 2: Opret en ny Exchange opbevaringspolitik for postkasser i venteposition

Næste trin er at oprette en ny opbevaringspolitik og føje opbevaringsmærker til den, herunder RPT for genoprettelige elementer, som du oprettede i trin 1. Denne nye politik anvendes på postkasser, der er i venteposition i næste trin.

Før du opretter den nye opbevaringspolitik, skal du fastlægge de ekstra opbevaringsmærker, du vil tilføje. Du kan finde en liste over de opbevaringsmærker, der er føjet til MRM-standardpolitikken, og du kan finde oplysninger om oprettelse af nye opbevaringsmærker i følgende:

- [Standardopbevaringspolitik i Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Standardmapper, der understøtter opbevaringspolitikmærker](/exchange/security-and-compliance/messaging-records-management/default-folders)

- Afsnittet "Opret et opbevaringsmærke" i emnet [Opret en opbevaringspolitik](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) .

Du kan bruge EAC eller Exchange Online PowerShell til at oprette en opbevaringspolitik.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Brug EAC til at oprette en opbevaringspolitik

1. I EAC skal du gå til Opbevaringspolitikker **for overholdelse** \> af **regler og standarder** og derefter klikke **på** ![Tilføj ikon](../media/ITPro-EAC-AddIcon.gif).

2. På siden **Ny opbevaringspolitik** under **Navn skal du** skrive et navn, der beskriver formålet med opbevaringspolitikken. **MRM-politik for postkasser i venteposition**.

3. Klik **på Tilføj** tilføj ikon **under Opbevaringsmærker**![](../media/ITPro-EAC-AddIcon.gif).

4. På listen over opbevaringsmærker skal du vælge RPT for genoprettelige elementer, som du oprettede i trin 1, og derefter klikke på **Tilføj**.

    ![Vælg det brugerdefinerede opbevaringsmærke Genoprettelige elementer.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Vælg yderligere opbevaringsmærker, der skal føjes til opbevaringspolitikken. Du kan f.eks. tilføje de samme mærker, som er inkluderet i MRM-standardpolitikken.

6. Klik på OK, når du er færdig med at tilføje **opbevaringsmærker**.

7. Klik **på Gem** for at oprette den nye opbevaringspolitik.

    Bemærk, at de opbevaringsmærker, der er knyttet til opbevaringspolitikken, vises i detaljeruden.

    ![Opbevaringsmærker, der er knyttet til opbevaringspolitikken, vises i detaljeruden.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Brug Exchange Online PowerShell til at oprette en opbevaringspolitik

Kør følgende kommando for at oprette en ny opbevaringspolitik for postkasser i venteposition.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Eksempelvis opretter følgende kommando opbevaringspolitikken og sammenkædede opbevaringsmærker, der vises i den forrige illustration.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>Trin 3: Anvend den nye Exchange opbevaringspolitik på postkasser i venteposition

Det sidste trin er at anvende den nye opbevaringspolitik, du oprettede i trin 2, på postkasser i venteposition i organisationen. Du kan bruge EAC eller Exchange Online PowerShell til at anvende opbevaringspolitikken på en enkelt postkasse eller på flere postkasser.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Brug EAC til at anvende den nye opbevaringspolitik

1. Gå til **RecipientsMailboxes** > .

2. I listevisningen skal du vælge den postkasse, du vil anvende opbevaringspolitikken på, og derefter klikke **på Rediger** ![redigeringsikon.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

3. Klik på **Postkassefunktioner** på siden **Brugerpostkasse**.

4. Under **Opbevaringspolitik skal** du vælge den opbevaringspolitik, du oprettede i trin 2, og derefter klikke på **Gem**.

Du kan også bruge EAC til at anvende opbevaringspolitikken på flere postkasser.

1. Gå til **RecipientsMailboxes** > .

2. I listevisningen skal du bruge Skift- eller Ctrl-tasterne til at markere flere postkasser.

3. Klik på Flere indstillinger i **detaljeruden**.

4. Klik **på Opdater** under **Opbevaringspolitik**.

5. På siden **Massetildel opbevaringspolitik** skal du vælge den opbevaringspolitik, du oprettede i trin 2, og derefter klikke på **Gem**.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Brug Exchange Online PowerShell til at anvende den nye opbevaringspolitik

Du kan bruge Exchange Online PowerShell til at anvende en ny opbevaringspolitik på en enkelt postkasse. Men den reelle styrke ved PowerShell er, at du kan bruge den til hurtigt at identificere alle postkasser i din organisation, som enten er i retslig tilbageholdelse eller In-Place-venteposition, og derefter anvende den nye opbevaringspolitik på alle postkasser i venteposition i en enkelt kommando. Her er nogle eksempler på brug Exchange PowerShell til at anvende en opbevaringspolitik på en eller flere postkasser. Alle eksemplerne anvender opbevaringspolitikken, der blev oprettet i trin 2.

I dette eksempel anvendes den nye opbevaringspolitik på Pilar Pinillas postkasse.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

I dette eksempel anvendes den nye opbevaringspolitik på alle postkasser i organisationen, der er i retslig tilbageholdelse.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

I dette eksempel anvendes den nye opbevaringspolitik på alle postkasser i organisationen, der er i In-Place Hold.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Du kan bruge **Get-Mailbox cmdlet'en** til at bekræfte, at den nye opbevaringspolitik blev anvendt.

Her er nogle eksempler til at bekræfte, at kommandoerne i de forrige eksempler anvendte opbevaringspolitikken "MRM-politik for postkasser i venteposition" på postkasser i retslig tilbageholdelse og postkasser i In-Place Hold.

```powershell
Get-Mailbox "Pilar Pinilla" | Select RetentionPolicy
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'} | FT DisplayName,RetentionPolicy -Auto
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null} | FT DisplayName,RetentionPolicy -Auto
```

## <a name="optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings"></a>(Valgfrit) Trin 4: Kør Administreret mappeassistent for at anvende de nye opbevaringsindstillinger

Når du anvender den nye Exchange-opbevaringspolitik på postkasser i venteposition, kan det tage op til 7 dage i Exchange Online for den administrerede mappeassistent at behandle disse postkasser ved hjælp af indstillingerne i den nye opbevaringspolitik. I stedet for at vente på at den administrerede mappeassistent kører, kan du bruge **Start-ManagedFolderAssistant** cmdlet'en til manuelt at indstille assistenten til at behandle de postkasser, du har anvendt den nye opbevaringspolitik på.

Kør følgende kommando for at starte den administrerede mappeassistent for Pilar Pinillas postkasse.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Kør følgende kommandoer for at starte Administreret mappeassistent for alle postkasser i venteposition.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Flere oplysninger

- Når du har aktiveret en brugers arkivpostkasse, bør du overveje at fortælle brugeren, at andre elementer i brugerens postkasse (ikke kun elementer i mappen Genoprettelige elementer) kan flyttes til arkivpostkassen. Dette skyldes, at MRM-standardpolitikken, der er tildelt Exchange Online-postkasser, indeholder et opbevaringsmærke (kaldet Standard 2 år flyt til arkiv), der flytter elementer til arkivpostkassen to år efter den dato, hvor elementet blev leveret til postkassen eller oprettet af brugeren. Få mere at vide under [Standardopbevaringspolitik i Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- Når du har aktiveret en brugers arkivpostkasse, kan du også fortælle brugeren, at brugeren kan gendanne slettede elementer i mappen Genoprettelige elementer i brugerens arkivpostkasse. De kan gøre dette i Outlook ved at vælge mappen Slettet post i  arkivpostkassen og derefter klikke på Gendan slettede elementer fra **serveren** **på fanen** Hjem. Du kan finde flere oplysninger om at gendanne slettede elementer i Gendan [slettede elementer i Outlook for Windows](https://go.microsoft.com/fwlink/p/?LinkId=624829).
