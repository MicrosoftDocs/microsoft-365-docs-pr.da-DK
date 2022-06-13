---
title: Øg kvoten for genoprettelige elementer for fastfrosne postkasser
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Aktivér arkivpostkassen, og aktivér automatisk udvidelse af arkivering for at øge størrelsen af mappen Gendanbare elementer for en postkasse i Microsoft 365.
ms.openlocfilehash: d426afffb1002e1187adafc794d5340d730cc7e7
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044132"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Øg kvoten for genoprettelige elementer for fastfrosne postkasser

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Standardpolitikken Exchange opbevaring – med navnet *Standard-MRM-politik* – der automatisk anvendes på nye postkasser i Exchange Online indeholder en opbevaringskode med navnet Gendanbare elementer 14 dages flytning til arkiv. Dette opbevaringsmærke flytter elementer fra mappen Gendanbare elementer i brugerens primære postkasse til mappen Gendanbare elementer i brugerens arkivpostkasse, når opbevaringsperioden på 14 dage udløber for et element. Mails i mappen Sletninger bevares baseret på parameteren **RetainDeletedItemsFor** og flyttes til andre mapper i slettede elementer, der kan gendannes, og derefter til arkivpostkassen. Hvis dette skal ske, skal brugerens arkivpostkasse være aktiveret. Hvis arkivpostkassen ikke er aktiveret, udføres der ingen handling, hvilket betyder, at elementer i mappen Gendanbare elementer for en postkasse, der er i venteposition, ikke flyttes til arkivpostkassen, når opbevaringsperioden på 14 dage udløber. Da intet slettes fra en postkasse i venteposition, er det muligt, at lagerkvoten for mappen Gendanbare elementer kan blive overskredet, især hvis brugerens arkivpostkasse ikke er aktiveret.

For at reducere risikoen for at overskride denne grænse øges lagerkvoten for mappen Gendanbare elementer automatisk fra 30 GB til 100 GB, når der sættes en venteposition på en postkasse i Exchange Online. Hvis arkivpostkassen er aktiveret, øges lagerkvoten for mappen Gendanbare elementer i arkivpostkassen også fra 30 GB til 100 GB. Hvis funktionen til automatisk udvidelse af arkivering i Exchange Online er aktiveret, er den samlede lagerkvote for brugerens arkivpostkasse, herunder mappen Genoprettelige elementer, 1,5 TB.

 I følgende tabel opsummeres lagerkvoten for mappen Gendanbare elementer.

| Placering af mappen Elementer, der kan gendannes | Postkasser, der ikke er i venteposition | Postkasser i venteposition |
|:-----|:-----|:-----|
|Primær postkasse |30 GB |100 GB |
|Arkivpostkasse, herunder mappen Elementer, der kan gendannes <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Den første lagerkvote for arkivpostkassen er 100 GB for brugere med en Exchange Online (plan 2) licens. Når automatisk udvidelse af arkivering er slået til for postkasser i venteposition, øges lagerkvoten for både arkivpostkassen og mappen Gendanbare elementer til 110 GB. Yderligere lagerplads til arkivet (som omfatter mappen Gendanbare elementer) op til 1,5 TB klargøres, når det er nødvendigt. Du kan finde flere oplysninger om automatisk udvidelse af arkivering under [Få mere at vide om automatisk udvidelse af arkivering](autoexpanding-archiving.md).

Når lagerkvoten for mappen Gendanbare elementer i den primære postkasse i en postkasse, der er i venteposition, er tæt på at nå grænsen, kan du gøre følgende:

- **Aktivér arkivpostkassen, og aktivér automatisk udvidelse af arkivering.** Du kan aktivere en ekstra lagerkapacitet for mappen Gendanbare elementer ved blot at aktivere arkivpostkassen og derefter aktivere funktionen til automatisk udvidelse af arkivering i Exchange Online. Dette resulterer i 110 GB for mappen Gendanbare elementer i den primære postkasse og op til 1,5 TB kombineret lagerkapacitet for mappen Arkiv og Gendanbare elementer. Du kan få flere oplysninger under [Aktivér arkivpostkasser](enable-archive-mailboxes.md) og [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Når du har aktiveret arkivet for en postkasse, der er tæt på at overskride lagerkvoten for mappen Gendanbare elementer, kan du køre Assistent til administrerede mapper for manuelt at udløse assistenten til at behandle postkassen, så udløbne elementer flyttes til mappen Gendanbare elementer i arkivpostkassen. Se [Trin 4](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) for at få vejledning. Bemærk, at andre elementer i brugerens postkasse kan blive flyttet til den nye arkivpostkasse. Overvej at fortælle brugeren, at dette kan ske, når du har aktiveret arkivpostkassen.

- **Opret en brugerdefineret Exchange opbevaringspolitik for postkasser i venteposition.** Ud over at aktivere arkivpostkassen og automatisk udvidelse af arkivering for postkasser i stridsposition eller In-Place venteposition kan du også oprette en brugerdefineret Exchange opbevaringspolitik for postkasser i venteposition. Dette giver dig mulighed for at anvende en opbevaringspolitik på postkasser i venteposition, der er forskellig fra standard-MRM-politikken, der anvendes på postkasser, der ikke er i venteposition, og giver dig mulighed for at anvende opbevaringskoder, der er designet til postkasser i venteposition. Dette omfatter oprettelse af en ny opbevaringskode for mappen Gendanbare elementer.

I resten af dette emne beskrives de trinvise procedurer til oprettelse af en brugerdefineret Exchange opbevaringspolitik for postkasser i venteposition.

[Trin 1: Opret en brugerdefineret opbevaringskode for mappen Elementer, der kan gendannes](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[Trin 2: Opret en ny Exchange opbevaringspolitik for postkasser i venteposition](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[Trin 3: Anvend den nye Exchange opbevaringspolitik på postkasser i venteposition](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(Valgfrit) Trin 4: Kør Assistent til administreret mappe for at anvende de nye opbevaringsindstillinger](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>Trin 1: Opret en brugerdefineret opbevaringskode for mappen Elementer, der kan gendannes

Det første trin er at oprette en brugerdefineret opbevaringskode (kaldet en opbevaringspolitikkode eller RPT) for mappen Genoprettelige elementer. Som tidligere forklaret flytter denne RPT elementer fra mappen Gendanbare elementer i brugerens primære postkasse til mappen Gendanbare elementer i brugerens arkivpostkasse. Du skal bruge PowerShell til at oprette en RPT til mappen Gendanbare elementer. Du kan ikke bruge Exchange Administration (EAC).

1. [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando for at oprette en ny RPT til mappen Gendanbare elementer:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Følgende kommando opretter f.eks. en RPT for mappen Gendanbare elementer med navnet "Genoprettelige elementer 30 dage for postkasser i venteposition" med en opbevaringsperiode på 30 dage. Det betyder, at når et element har været i mappen Gendanbare elementer i 30 dage, flyttes det til mappen Gendanbare elementer i brugerens arkivpostkasse.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Vi anbefaler, at opbevaringsperioden (defineret af parameteren  _AgeLimitForRetention_ ) for RPT for genoprettelige elementer er den samme som opbevaringsperioden for slettede elementer for de postkasser, som RPT anvendes på. Dette gør det muligt for en bruger at gendanne slettede elementer i hele opbevaringsperioden for slettede elementer, før de flyttes til arkivpostkassen. I det forrige eksempel blev opbevaringsperioden angivet til 30 dage baseret på den antagelse, at opbevaringsperioden for slettede elementer for postkasser også er 30 dage. En Exchange Online postkasse er som standard konfigureret til at bevare slettede elementer i 14 dage. Men du kan ændre denne indstilling til højst 30 dage. Du kan få flere oplysninger under [Skift opbevaringsperioden for slettede elementer for en postkasse i Exchange Online](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>Trin 2: Opret en ny Exchange opbevaringspolitik for postkasser i venteposition

Det næste trin er at oprette en ny opbevaringspolitik og føje opbevaringskoder til den, herunder RPT for genoprettelige elementer, som du oprettede i trin 1. Denne nye politik anvendes på postkasser, der er i venteposition i næste trin.

Før du opretter den nye opbevaringspolitik, skal du bestemme de ekstra opbevaringskoder, du vil tilføje. Du kan se en liste over de opbevaringskoder, der føjes til standard-MRM-politikken, og for at få oplysninger om oprettelse af nye opbevaringskoder, på følgende måde:

- [Standardopbevaringspolitik i Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Standardmapper, der understøtter opbevaringspolitikmærker](/exchange/security-and-compliance/messaging-records-management/default-folders)

- Afsnittet "Opret en opbevaringskode" i emnet [Opret en opbevaringspolitik](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) .

Du kan bruge EAC eller Exchange Online PowerShell til at oprette en opbevaringspolitik.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Brug EAC til at oprette en opbevaringspolitik

1. I EAC skal du gå til **Opbevaringspolitikker** for **overholdelse af** \> regler og standarder og derefter klikke på **Tilføj ikonet Tilføj**![.](../media/ITPro-EAC-AddIcon.gif)

2. På siden **Ny opbevaringspolitik** under **Navn** skal du skrive et navn, der beskriver formålet med opbevaringspolitikken. F.eks **. MRM-politik for postkasser i venteposition**.

3. Klik på **Tilføj ikonet Tilføj** ![under **Opbevaringskoder**.](../media/ITPro-EAC-AddIcon.gif)

4. På listen over opbevaringskoder skal du vælge RPT for gendanbare elementer, som du oprettede i trin 1, og derefter klikke på **Tilføj**.

    ![Vælg den brugerdefinerede kode for opbevaring af elementer, der kan genoprettes.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Vælg yderligere opbevaringskoder, der skal føjes til opbevaringspolitikken. Det kan f.eks. være, at du vil tilføje de samme mærker, som er inkluderet i standard-MRM-politikken.

6. Klik på **OK**, når du er færdig med at tilføje opbevaringskoder.

7. Klik på **Gem** for at oprette den nye opbevaringspolitik.

    Bemærk, at de opbevaringskoder, der er knyttet til opbevaringspolitikken, vises i detaljeruden.

    ![Opbevaringskoder, der er knyttet til opbevaringspolitikken, vises i detaljeruden.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Brug Exchange Online PowerShell til at oprette en opbevaringspolitik

Kør følgende kommando for at oprette en ny opbevaringspolitik for postkasser i venteposition.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Følgende kommando opretter f.eks. opbevaringspolitikken og sammenkædede opbevaringskoder, der vises i den forrige illustration.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>Trin 3: Anvend den nye Exchange opbevaringspolitik på postkasser i venteposition

Det sidste trin er at anvende den nye opbevaringspolitik, som du oprettede i trin 2, på postkasser, der er i venteposition i din organisation. Du kan bruge EAC eller Exchange Online PowerShell til at anvende opbevaringspolitikken på en enkelt postkasse eller på flere postkasser.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Brug EAC til at anvende den nye opbevaringspolitik

1. Gå til **Modtageres** > **postkasser**.

2. I listevisningen skal du vælge den postkasse, du vil anvende opbevaringspolitikken på, og **derefter klikke på** ![rediger ikonet Rediger.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

3. Klik på **Postkassefunktioner** på siden **Brugerpostkasse**.

4. Under **Opbevaringspolitik** skal du vælge den opbevaringspolitik, du oprettede i trin 2, og derefter klikke på **Gem**.

Du kan også bruge EAC til at anvende opbevaringspolitikken på flere postkasser.

1. Gå til **Modtageres** > **postkasser**.

2. I listevisningen skal du bruge Skift- eller Ctrl-tasterne til at vælge flere postkasser.

3. Klik på **Flere indstillinger** i detaljeruden.

4. Klik på **Opdater** under **Opbevaringspolitik**.

5. På siden **Massetildel opbevaringspolitik** skal du vælge den opbevaringspolitik, du oprettede i trin 2, og derefter klikke på **Gem**.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Brug Exchange Online PowerShell til at anvende den nye opbevaringspolitik

Du kan bruge Exchange Online PowerShell til at anvende en ny opbevaringspolitik på en enkelt postkasse. Men den reelle styrke ved PowerShell er, at du kan bruge den til hurtigt at identificere alle de postkasser i din organisation, der er i enten Litigation Venteposition eller In-Place Venteposition, og derefter anvende den nye opbevaringspolitik på alle postkasser i venteposition i en enkelt kommando. Her er nogle eksempler på brug af Exchange PowerShell til at anvende en opbevaringspolitik på en eller flere postkasser. Alle eksemplerne anvender den opbevaringspolitik, der blev oprettet i trin 2.

I dette eksempel anvendes den nye opbevaringspolitik på Pilar Pinillas postkasse.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

I dette eksempel anvendes den nye opbevaringspolitik på alle postkasser i organisationen, der er i procesventeposition.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

I dette eksempel anvendes den nye opbevaringspolitik på alle postkasser i organisationen, der er i In-Place venteposition.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Du kan bruge **cmdlet'en Get-Mailbox** til at bekræfte, at den nye opbevaringspolitik blev anvendt.

Her er nogle eksempler på bekræftelse af, at kommandoerne i de forrige eksempler anvendte opbevaringspolitikken "MRM-politik for postkasser i venteposition" på postkasser i procesretsventeposition og postkasser i venteposition In-Place.

```powershell
Get-Mailbox "Pilar Pinilla" | Select RetentionPolicy
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'} | FT DisplayName,RetentionPolicy -Auto
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null} | FT DisplayName,RetentionPolicy -Auto
```

## <a name="optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings"></a>(Valgfrit) Trin 4: Kør Assistent til administreret mappe for at anvende de nye opbevaringsindstillinger

Når du har anvendt den nye Exchange opbevaringspolitik på postkasser i venteposition, kan det tage op til syv dage i Exchange Online for Assistent til administrerede mapper at behandle disse postkasser ved hjælp af indstillingerne i den nye opbevaringspolitik. I stedet for at vente på, at Assistent til administrerede mapper kører, kan du bruge cmdlet'en **Start-ManagedFolderAssistant** til manuelt at udløse assistenten til at behandle de postkasser, du anvendte den nye opbevaringspolitik på.

Kør følgende kommando for at starte Assistent til administreret mappe for Pilar Pinillas postkasse.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Kør følgende kommandoer for at starte Assistent til administreret mappe for alle postkasser i venteposition.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Flere oplysninger

- Når du har aktiveret en brugers arkivpostkasse, kan du overveje at fortælle brugeren, at andre elementer i deres postkasse (ikke kun elementer i mappen Gendanbare elementer) kan flyttes til arkivpostkassen. Det skyldes, at standard-MRM-politikken, der er tildelt til Exchange Online postkasser, indeholder en opbevaringskode (med navnet Standard 2 års flytning til arkiv), der flytter elementer til arkivpostkassen to år efter den dato, hvor elementet blev leveret til postkassen eller oprettet af brugeren. Du kan få flere oplysninger under [Standardopbevaringspolitik i Exchange Online](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- Når du har aktiveret en brugers arkivpostkasse, kan du også fortælle brugeren, at brugeren kan gendanne slettede elementer i mappen Gendanbare elementer i deres arkivpostkasse. De kan gøre dette i Outlook ved at vælge mappen **Slettet post** i arkivpostkassen og derefter klikke på **Gendan slettet post fra server** under fanen **Hjem**. Du kan finde flere oplysninger om gendannelse af slettede elementer [under Gendan slettede elementer i Outlook for at få Windows](https://go.microsoft.com/fwlink/p/?LinkId=624829).
