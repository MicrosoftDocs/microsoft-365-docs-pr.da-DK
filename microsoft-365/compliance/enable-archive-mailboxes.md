---
title: Aktivér arkivpostkasser for Microsoft 365 overholdelse af angivne standarder
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
description: Få mere at vide om, hvordan du aktiverer eller deaktiverer arkivpostkasser for at understøtte organisationens krav til meddelelsesopbevaring, eDiscovery og venteposition.
ms.openlocfilehash: 9e30178dcab731ae61a9db5374218a608e4e47af
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738378"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Aktivér arkivpostkasser i Overholdelsescenter

Arkivering i Microsoft 365 (også kaldet *direkte arkivering*) giver brugerne yderligere lagerplads på postkassen. Du kan finde flere oplysninger under [Få mere at vide om arkivpostkasser](archive-mailboxes.md).

Brug oplysningerne i denne artikel til at aktivere eller deaktivere en arkivpostkasse i Microsoft 365 Overholdelsescenter eller ved hjælp af PowerShell. Få også mere at vide om, hvordan du kører en automatiseret diagnosticeringskontrol på en brugers arkivpostkasse for at identificere eventuelle problemer og foreslåede løsninger.

## <a name="get-the-necessary-permissions"></a>Hent de nødvendige tilladelser

Du skal være tildelt rollen Postmodtagere i Exchange Online for at aktivere eller deaktivere arkivpostkasser. Denne rolle tildeles som standard til rollegrupperne Modtageradministration og Organisationsadministration på siden **Tilladelser** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. 

Hvis du ikke kan se siden **Arkiv** i Microsoft 365 Overholdelsescenter, skal du bede administratoren om at tildele dig de nødvendige tilladelser.

## <a name="enable-an-archive-mailbox"></a>Aktivér en arkivpostkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>, og log på.

2. Klik på **Styring af oplysninger** i venstre rude i Microsoft 365 Overholdelsescenter, og klik derefter på fanen **Arkiv**.

   Siden **Arkiv** vises. Kolonnen **Arkivpostkasse** angiver, om en arkivpostkasse er aktiveret eller deaktiveret for hver bruger.

   > [!NOTE]
   > På siden **Arkiv** vises maksimalt 500 brugere.

3. På listen over postkasser skal du vælge den bruger, du vil aktivere arkivpostkassen for, og vælge **Aktivér arkiv**.

   ![Klik på Aktivér i detaljeruden for den valgte bruger for at aktivere arkivpostkassen.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)


   Der vises en advarsel om, at hvis du aktiverer arkivpostkassen, flyttes elementer i brugerens postkasse, der er ældre end den arkiveringspolitik, der er tildelt postkassen, til den nye arkivpostkasse. Standardarkivpolitikken, der er en del af den opbevaringspolitik, der er tildelt Exchange Online postkasser, flytter elementer til arkivpostkassen to år efter den dato, hvor elementet blev leveret til postkassen eller oprettet af brugeren. Du kan finde flere oplysninger i afsnittet **Flere oplysninger** i denne artikel.

5. Vælg **Aktivér** for at aktivere arkivpostkassen.

   Det kan tage et øjeblik at oprette arkivpostkassen. Når den er oprettet, vises **Arkivpostkasse: aktiveret** i detaljeruden for den valgte bruger. Du skal muligvis klikke på ikonet **Opdater** ![opdatering.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere oplysningerne i detaljeruden.

> [!TIP]
> Du kan også masseaktivere arkivpostkasser ved at vælge flere brugere med deaktiverede arkivpostkasser (brug Skift- eller Ctrl-tasterne). Når du har valgt flere postkasser, skal du klikke på **Aktivér** i detaljeruden.

## <a name="disable-an-archive-mailbox"></a>Deaktiver en arkivpostkasse

Du kan også bruge siden **Arkiv** i Microsoft 365 Overholdelsescenter til at deaktivere en brugers arkivpostkasse. Når du har deaktiveret en arkivpostkasse, kan du genoprette forbindelsen til brugerens primære postkasse inden for 30 dage efter deaktivering af den. I dette tilfælde gendannes det oprindelige indhold i arkivpostkassen. Efter 30 dage slettes indholdet af den oprindelige arkivpostkasse permanent og kan ikke gendannes. Så hvis du genaktiverer arkivet mere end 30 dage efter deaktivering af det, oprettes der en ny arkivpostkasse.

Den standardarkivpolitik, der er tildelt brugernes postkasser, flytter elementer til arkivpostkassen to år efter den dato, hvor elementet leveres. Hvis du deaktiverer en brugers arkivpostkasse, udføres der ingen handling på postkasseelementer, og de forbliver i brugerens primære postkasse.

Sådan deaktiverer du en arkivpostkasse:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>, og log på.

2. Klik på **Styring af oplysninger** i venstre rude i Microsoft 365 Overholdelsescenter, og klik derefter på fanen **Arkiv**.

   Siden **Arkiv** vises. Kolonnen **Arkivpostkasse** angiver, om en arkivpostkasse er aktiveret eller deaktiveret for hver bruger.

   > [!NOTE]
   > På siden **Arkiv** vises maksimalt 500 brugere.

3. På listen over postkasser skal du vælge den bruger, du vil deaktivere arkivpostkassen for, og vælge **Deaktiver arkiv**.


   Der vises en advarsel om, at du har 30 dage til at genaktivere arkivpostkassen, og at alle oplysninger i arkivet slettes permanent efter 30 dage.

5. Vælg **Deaktiver** for at deaktivere arkivpostkassen.

   Det kan tage et øjeblik at deaktivere arkivpostkassen. Når den er deaktiveret, vises **Arkivpostkasse: deaktiveret** i detaljeruden for den valgte bruger. Du skal muligvis klikke på ikonet **Opdater** ![opdatering.](../media/O365-MDM-Policy-RefreshIcon.gif) for at opdatere oplysningerne i detaljeruden.

> [!TIP]
> Du kan også masseaktivere arkivpostkasser ved at vælge flere brugere med aktiverede arkivpostkasser (brug Skift- eller Ctrl-tasterne). Når du har valgt flere postkasser, skal du klikke på **Deaktiver** i detaljeruden.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Brug Exchange Online PowerShell til at aktivere eller deaktivere arkivpostkasser

Du kan også bruge Exchange Online PowerShell til at aktivere arkivpostkasser. Den primære årsag til at bruge PowerShell er, at du hurtigt kan aktivere arkivpostkassen for alle brugere i din organisation.

Det første trin er at oprette forbindelse til Exchange Online PowerShell. Du kan finde instruktioner [under Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Når du har oprettet forbindelse til Exchange Online, kan du køre kommandoerne i følgende afsnit for at aktivere eller deaktivere arkivpostkasser.

### <a name="enable-archive-mailboxes"></a>Aktivér arkivpostkasse

Kør følgende kommando for at aktivere arkivpostkassen for en enkelt bruger.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at aktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkasse i øjeblikket ikke er aktiveret).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Deaktiver arkivpostkasser

Kør følgende kommando for at deaktivere arkivpostkassen for en enkelt bruger.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at deaktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkasse er aktiveret i øjeblikket).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Kør diagnosticering på arkivpostkasser

Du kan køre en automatisk diagnosticeringskontrol på en brugers arkivpostkasse for at identificere eventuelle problemer og forslag til løsninger.

Klik på knappen nedenfor for at køre diagnosticeringskontrollen. 

> [!div class="nextstepaction"]
> [Kør test: Arkivpostkasse](https://aka.ms/PillarArchiveMailbox)

![Kør diagnosticering på en arkivpostkasse.](../media/ArchiveMailboxDiagnostics.png)

Der åbnes en pop op-side i Microsoft 365 Administration. Angiv mailadressen på den postkasse, du vil kontrollere, og klik på **Kør test**.

> [!NOTE]
> Du skal være Microsoft 365 global administrator for at kunne bruge diagnosticeringskontrollen for arkivpostkassen. Denne funktion er heller ikke tilgængelig i Microsoft 365 Government-cloudmiljøer, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Tyskland.

## <a name="next-steps"></a>Næste trin

Overvej at aktivere [automatisk udvidelse af arkivering](autoexpanding-archiving.md) for at få mere lagerplads. Du kan finde instruktioner under [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).
