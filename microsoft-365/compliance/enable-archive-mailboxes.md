---
title: Aktivere arkivpostkasser for at Microsoft 365 overholdelse af regler og standarder
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du aktiverer eller deaktiverer arkivpostkasser for at understøtte organisationens krav til opbevaring af meddelelser, eDiscovery og venteposition.
ms.openlocfilehash: be7939f11c6aea0161f76c3796ca2ff8bd515ba0
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587296"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Aktivér arkivpostkasser i overholdelsescenter

Arkivering i Microsoft 365 (også *kaldet direkte arkivering*) giver brugerne yderligere lagerplads til postkassen. Du kan få mere at vide [under Få mere at vide om arkivpostkasser](archive-mailboxes.md).

Brug oplysningerne i denne artikel til at aktivere eller deaktivere en arkivpostkasse i Microsoft 365 Overholdelsescenter eller ved hjælp af PowerShell. Få også mere at vide om, hvordan du kører en automatiseret diagnosticeringskontrol af en brugers arkivpostkasse for at identificere problemer og foreslåede løsninger.

## <a name="get-the-necessary-permissions"></a>Få de nødvendige tilladelser

Du skal have tildelt rollen Postmodtagere i en Exchange Online aktivere eller deaktivere arkivpostkasser. Som standard er denne rolle tildelt rollegrupperne Modtageradministration og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. 

Hvis du ikke kan se **arkivsiden** i Microsoft 365 Overholdelsescenter, skal du bede din administrator om at give dig de nødvendige tilladelser.

## <a name="enable-an-archive-mailbox"></a>Aktivere en arkivpostkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> og log på.

2. Klik på Microsoft 365 Overholdelsescenter i venstre rude **, og klik** derefter på **fanen** Arkivér.

   **Arkivsiden** vises. Kolonnen **Arkivpostkasse** angiver, om en arkivpostkasse er aktiveret eller deaktiveret for hver bruger.

   > [!NOTE]
   > **Arkivsiden** viser maksimalt 500 brugere.

3. På listen over postkasser skal du vælge den bruger, du vil aktivere arkivpostkassen for.

   ![Klik på Aktivér i detaljeruden for den valgte bruger for at aktivere arkivpostkassen.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)

4. Klik på Aktivér i detaljeruden for den valgte **bruger**.

   Der vises en advarsel, der fortæller, at hvis du aktiverer arkivpostkassen, flyttes elementer i brugerens postkasse, som er ældre end den arkiveringspolitik, der er tildelt postkassen, til den nye arkivpostkasse. Standardarkivpolitikken, der er en del af opbevaringspolitikken for Exchange Online-postkasser, flytter elementer til arkivpostkassen to år efter den dato, hvor elementet blev leveret til postkassen eller oprettet af brugeren. Du kan finde flere oplysninger i **afsnittet Flere** oplysninger i denne artikel.

5. Klik **på Ja** for at aktivere arkivpostkassen.

   Det kan tage et øjeblik at oprette arkivpostkassen. Når den er oprettet, **vises Arkivpostkasse:** aktiveret i detaljeruden for den valgte bruger. Du skal muligvis klikke på **ikonet** ![Opdater opdatering.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere oplysningerne i detaljeruden.

> [!TIP]
> Du kan også masseaktivere arkivpostkasser ved at vælge flere brugere med deaktiverede arkivpostkasser (brug Skift- eller Ctrl-tasterne). Når du har valgt flere postkasser, skal du **klikke på** Aktivér i detaljeruden.

## <a name="disable-an-archive-mailbox"></a>Deaktivere en arkivpostkasse

Du kan også bruge **arkivsiden** i Microsoft 365 Overholdelsescenter til at deaktivere en brugers arkivpostkasse. Når du deaktiverer en arkivpostkasse, kan du genoprette forbindelsen til brugerens primære postkasse inden for 30 dage efter deaktivering af den. I dette tilfælde gendannes det oprindelige indhold i arkivpostkassen. Efter 30 dage slettes indholdet af den oprindelige arkivpostkasse permanent og kan ikke gendannes. Så hvis du genaktiverer arkivet mere end 30 dage efter deaktivering af det, oprettes der en ny arkivpostkasse.

Den standardarkivpolitik, der er tildelt brugernes postkasser, flytter elementer til arkivpostkassen to år efter, elementet blev leveret. Hvis du deaktiverer en brugers arkivpostkasse, sker der ikke noget med postkasseelementer, og de forbliver i brugerens primære postkasse.

Sådan deaktiverer du en arkivpostkasse:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> og log på.

2. Klik på Microsoft 365 Overholdelsescenter i venstre rude **, og klik** derefter på **fanen** Arkivér.

   **Arkivsiden** vises. Kolonnen **Arkivpostkasse** angiver, om en arkivpostkasse er aktiveret eller deaktiveret for hver bruger.

   > [!NOTE]
   > **Arkivsiden** viser maksimalt 500 brugere.

3. På listen over postkasser skal du vælge den bruger, du vil deaktivere arkivpostkassen for.

4. Klik på Deaktiver i **detaljeruden**.

   Der vises en advarselsmeddelelse om, at du har 30 dage til at genaktivere arkivpostkassen, og at efter 30 dage slettes alle oplysninger i arkivet permanent.

5. Klik **på Ja** for at deaktivere arkivpostkassen.

   Det kan tage et øjeblik at deaktivere arkivpostkassen. Når den er deaktiveret, **vises Arkivpostkasse:** deaktiveret i detaljeruden for den valgte bruger. Du skal muligvis klikke på **ikonet** ![Opdater opdatering.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere oplysningerne i detaljeruden.

> [!TIP]
> Du kan også masseaktivere arkivpostkasser ved at markere flere brugere med aktiverede arkivpostkasser (brug Skift- eller Ctrl-tasterne). Når du har valgt flere postkasser, skal du **klikke på** Deaktiver i detaljeruden.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Brug Exchange Online PowerShell til at aktivere eller deaktivere arkivpostkasser

Du kan også bruge Exchange Online PowerShell til at aktivere arkivpostkasser. Den primære årsag til at bruge PowerShell er, at du hurtigt kan aktivere arkivpostkassen for alle brugere i organisationen.

Det første trin er at oprette forbindelse til Exchange Online PowerShell. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Når du har forbindelse til en Exchange Online, kan du køre kommandoerne i følgende afsnit for at aktivere eller deaktivere arkivpostkasser.

### <a name="enable-archive-mailboxes"></a>Aktivere arkivpostkasser

Kør følgende kommando for at aktivere arkivpostkassen for en enkelt bruger.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at aktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkasse i øjeblikket ikke er aktiveret).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Deaktivere arkivpostkasser

Kør følgende kommando for at deaktivere arkivpostkassen for en enkelt bruger.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at deaktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkasse er aktiveret i øjeblikket).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Kør diagnosticering på arkivpostkasser

Du kan køre en automatiseret diagnosticeringskontrol af en brugers arkivpostkasse for at identificere eventuelle problemer og foreslåede løsninger.

Klik på knappen nedenfor for at køre den diagnostiske kontrol. 

> [!div class="nextstepaction"]
> [Kør test: Arkivpostkasse](https://aka.ms/PillarArchiveMailbox)

![Kør diagnosticering på en arkivpostkasse.](../media/ArchiveMailboxDiagnostics.png)

Der åbnes en pop op-side i Microsoft 365 Administration. Angiv mailadressen på den postkasse, du vil kontrollere, og klik på **Kør test**.

> [!NOTE]
> Du skal være global Microsoft 365 for at bruge den diagnostiske arkivpostkassekontrol. Desuden er denne funktion ikke tilgængelig i Microsoft 365 Government-skyer, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Germany.

## <a name="next-steps"></a>Næste trin

Overvej at aktivere [automatisk udvidende arkivering](autoexpanding-archiving.md) for yderligere lagerplads. Du kan finde en vejledning [under Aktivér automatisk udvidende arkivering](enable-autoexpanding-archiving.md).
