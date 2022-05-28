---
title: Aktivér arkivpostkasser for Microsoft 365
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
ms.openlocfilehash: f95da36b48389bba2bd640825071dbff5c6ddb3d
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772418"
---
# <a name="enable-archive-mailboxes-in-the-microsoft-purview-compliance-portal"></a>Aktivér arkivpostkasser i Microsoft Purview-overholdelsesportalen

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Arkivering i Microsoft 365 (også kaldet *Direkte arkivering*) giver brugerne mere lagerplads til postkassen. Du kan finde flere oplysninger under [Få mere at vide om arkivpostkasser](archive-mailboxes.md).

Brug oplysningerne i denne artikel til at aktivere eller deaktivere en arkivpostkasse på Microsoft Purview-overholdelsesportalen eller ved hjælp af PowerShell. Få også mere at vide om, hvordan du kører en automatiseret diagnosticeringskontrol af en brugers arkivpostkasse for at identificere eventuelle problemer og foreslåede løsninger.

## <a name="get-the-necessary-permissions"></a>Få de nødvendige tilladelser

Du skal have tildelt rollen Mailmodtagere i Exchange Online for at aktivere eller deaktivere arkivpostkasser. Denne rolle er som standard tildelt rollegrupperne Modtageradministration og Organisationsadministration på siden **Tilladelser** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. 

Hvis du ikke kan se siden **Arkiv** på Microsoft Purview-overholdelsesportalen, skal du bede administratoren om at tildele dig de nødvendige tilladelser.

## <a name="enable-an-archive-mailbox"></a>Aktivér en arkivpostkasse

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a> og log på.

2. Vælg **Administration af datalivscyklus** > **Arkiv** i venstre rude på overholdelsesportalen.

   På siden **Arkiv** identificerer kolonnen **Arkivpostkasse**, om en arkivpostkasse er aktiveret eller deaktiveret for hver bruger.

   > [!NOTE]
   > Siden **Arkiv** viser maksimalt 500 brugere. Brug søgefeltet, hvis du ikke straks kan se navnet på den ønskede bruger.

3. På listen over postkasser skal du vælge brugeren for at aktivere vedkommendes postkasse til arkiv og derefter vælge indstillingen **Aktivér arkiv**:
    
   ![Aktivér arkivindstilling for en valgt bruger.](../media/enable-archive-option.png)
    
   Der vises en advarsel om, at hvis du aktiverer arkivpostkassen, flyttes elementer i brugerens postkasse, der er ældre end den arkiveringspolitik, der er tildelt postkassen, til den nye arkivpostkasse. Standardarkivpolitikken, der er en del af den opbevaringspolitik, der er tildelt Exchange Online-postkasser, flytter elementer til arkivpostkassen to år efter den dato, hvor elementet blev leveret til postkassen eller oprettet af brugeren. Du kan finde flere oplysninger under [Få mere at vide om arkivpostkasser](archive-mailboxes.md).

5. Vælg **Aktivér** for at bekræfte.

   Det kan tage et øjeblik at oprette arkivpostkassen. Når den er oprettet, vises **Aktiveret** i kolonnen **Arkivpostkasse** for den valgte bruger, selvom du muligvis skal opdatere siden for at se statusændringen.

## <a name="disable-an-archive-mailbox"></a>Deaktiver en arkivpostkasse

På samme måde som du aktiverer en arkivpostkasse, kan du bruge siden **Arkiv** i Microsoft Purview-overholdelsesportalen til at deaktivere en brugers arkivpostkasse. Denne gang skal du vælge indstillingen **Deaktiver arkiv**, når du har valgt brugeren.

Når du har deaktiveret en arkivpostkasse, kan du genoprette forbindelsen til brugerens primære postkasse inden for 30 dage efter deaktivering af den. I dette tilfælde gendannes det oprindelige indhold i arkivpostkassen. Efter 30 dage slettes indholdet af den oprindelige arkivpostkasse permanent og kan ikke gendannes. Så hvis du genaktiverer arkivet mere end 30 dage efter deaktivering, oprettes der en ny arkivpostkasse.

Den standardarkivpolitik, der er tildelt brugernes postkasser, flytter elementer til arkivpostkassen to år efter den dato, hvor elementet leveres. Hvis du deaktiverer en brugers arkivpostkasse, udføres der ingen handling på postkasseelementer, og de forbliver i brugerens primære postkasse.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Brug Exchange Online PowerShell til at aktivere eller deaktivere arkivpostkasser

Du kan også bruge Exchange Online PowerShell til at aktivere arkivpostkasser. Den primære årsag til at bruge PowerShell er, at du hurtigt kan aktivere arkivpostkassen for alle brugere i organisationen.

Det første trin er at oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Når du har forbindelse til Exchange Online, kan du køre kommandoerne i følgende afsnit for at aktivere eller deaktivere arkivpostkasser.

### <a name="enable-archive-mailboxes"></a>Aktivér arkivpostkasse

Kør følgende kommando for at aktivere arkivpostkassen for en enkelt bruger.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at aktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkasse ikke er aktiveret i øjeblikket).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Deaktiver arkivpostkasser

Kør følgende kommando for at deaktivere arkivpostkassen for en enkelt bruger.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Kør følgende kommando for at deaktivere arkivpostkassen for alle brugere i organisationen (hvis arkivpostkassen er aktiveret i øjeblikket).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Kør diagnosticering på arkivpostkasser

Du kan også køre en automatiseret diagnosticeringskontrol af en brugers arkivpostkasse for at identificere eventuelle problemer og foreslåede løsninger.

Klik på knappen nedenfor for at køre diagnosticeringskontrollen. 

> [!div class="nextstepaction"]
> [Kør test: Arkivér postkasse](https://aka.ms/PillarArchiveMailbox)

![Kør diagnosticering på en arkivpostkasse.](../media/ArchiveMailboxDiagnostics.png)

Der åbnes en pop op-side i Microsoft 365 Administration. Angiv mailadressen på den postkasse, du vil kontrollere, og klik på **Kør test**.

> [!NOTE]
> Du skal være global Microsoft 365-administrator for at kunne bruge diagnosticeringskontrol af arkivpostkassen. Denne funktion er heller ikke tilgængelig i Microsoft 365 Government-skyer, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Tyskland.

## <a name="instructions-for-end-users"></a>Vejledning for slutbrugere

Forklar brugerne, hvordan deres arkivpostkasse fungerer, og hvordan de kan interagere med den i Outlook på Windows, macOS og internettet. Den mest effektive dokumentation tilpasses til din organisation. Men hvis du vil have grundlæggende instruktioner, skal du se [Administrer maillager med onlinearkivpostkasser](https://prod.support.services.microsoft.com/en-us/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

## <a name="next-steps"></a>Næste trin

Overvej at aktivere [automatisk udvidelse af arkivering](autoexpanding-archiving.md) for at få mere lagerplads. Du kan finde en vejledning under [Aktivér automatisk udvidelse af arkivering](enable-autoexpanding-archiving.md).
