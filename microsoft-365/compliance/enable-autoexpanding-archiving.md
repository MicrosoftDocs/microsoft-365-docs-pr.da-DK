---
title: Aktivere automatisk udvidende arkivering
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: e2a789f2-9962-4960-9fd4-a00aa063559e
description: 'For administratorer: Lær, hvordan du aktiverer automatisk udvidende arkivering, som giver brugerne ekstra lagerplads til deres Exchange Online postkasser. Du kan aktivere automatisk udvidende arkivering for hele organisationen eller kun for bestemte brugere.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c6f1514ed4bb9c12ac666b366cab91358216357a
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63600989"
---
# <a name="enable-auto-expanding-archiving"></a>Aktivere automatisk udvidende arkivering

Du kan bruge Exchange Online til automatisk udvidende arkivering for at aktivere yderligere lagerplads til arkivpostkasser. Når automatisk udvidende arkivering er slået til, føjes der automatisk ekstra lagerplads til en brugers arkivpostkasse, indtil lagergrænsen er 1,5 TB. Du kan aktivere automatisk udvidende arkivering for alle i organisationen eller kun for bestemte brugere. Du kan finde flere oplysninger om automatisk udvidende arkivering i [Få mere at vide om automatisk udvidende arkivering](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Før du aktiverer automatisk udvidende arkivering

- Når du har aktiveret automatisk udvidende arkivering for organisationen eller for en bestemt bruger, kan den ikke deaktiveres. Administratorer kan desuden ikke justere lagerkvoten for automatisk udvidende arkivering.

- Du skal være global administrator i din organisation eller være medlem af rollegruppen Organisationsadministration i din Exchange Online for at aktivere automatisk udvidende arkivering. Alternativt skal du være medlem af en rollegruppe, der har fået tildelt rollen Postmodtagere for at aktivere automatisk udvidende arkivering for bestemte brugere.

- En brugers arkivpostkasse skal aktiveres, før du kan aktivere automatisk udvidende arkivering. En bruger skal have tildelt en Exchange Online Plan 2-licens for at aktivere arkivpostkassen. Hvis en bruger er tildelt en Exchange Online Plan 1-licens, skal du tildele dem en separat Exchange Online-arkivering-licens for at aktivere deres arkivpostkasse. Se [Aktivér arkivpostkasser](enable-archive-mailboxes.md).

- Når du har aktiveret automatisk udvidende arkivering, konverteres en arkivpostkasse til et automatisk udvidende arkiv, når arkivpostkassen (herunder mappen genoprettelige elementer) når 90 GB. Det kan tage op til 30 dage, før den ekstra lagerplads er klargjort.

- Du kan også bruge PowerShell til at aktivere arkivpostkasser. Se afsnittet [Flere oplysninger](#more-information) for at få et eksempel på kommandoen PowerShell, som du kan bruge til at aktivere arkivpostkasser for alle brugere i organisationen.

- Automatisk udvidende arkivering understøtter også delte postkasser. For at aktivere arkivet for en delt postkasse skal du have en Exchange Online Plan 2-licens eller Exchange Online Plan 1-licens Exchange Online-arkivering licens.

- Automatisk udvidende arkivering forhindrer dig i at gendanne eller gendanne en [inaktiv postkasse](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Det betyder, at hvis du aktiverer automatisk udvidende arkivering for en postkasse, og postkassen gøres inaktiv på et senere tidspunkt, kan du ikke gendanne den inaktive [postkasse (ved](recover-an-inactive-mailbox.md) at konvertere den til en aktiv postkasse) eller gendanne [den (ved](restore-an-inactive-mailbox.md) at flette indholdet til en eksisterende postkasse). Hvis automatisk udvidende arkivering er aktiveret på en inaktiv postkasse, er den eneste måde at gendanne data på ved hjælp af værktøjet Indholdssøgning i Microsoft 365 Overholdelsescenter til at eksportere dataene fra postkassen og importere til en anden postkasse. Du kan finde flere oplysninger i afsnittet "Inaktive postkasser og automatisk udvide arkiver" i Få mere at vide [om inaktive postkasser](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Du kan ikke bruge Exchange Administration eller administration til Microsoft 365 Overholdelsescenter aktivere automatisk udvidende arkivering. Du skal bruge Exchange Online PowerShell. Hvis du vil oprette forbindelse Exchange Online din organisation ved hjælp af Remote PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Aktivere automatisk udvidende arkivering for hele organisationen

Du kan aktivere automatisk udvidende arkivering for hele organisationen. Når du har aktiveret den, bliver automatisk udvidende arkivering aktiveret for eksisterende brugerpostkasser og for nye brugerpostkasser, der oprettes. Når du opretter brugerpostkasser, skal du sørge for at aktivere brugerens primære arkivpostkasse, så den automatiske udvidende arkiveringsfunktion fungerer for den nye brugerpostkasse.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando i Exchange Online PowerShell for at aktivere automatisk udvidende arkivering for hele organisationen.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Aktivere automatisk udvidende arkivering for bestemte brugere

I stedet for at aktivere automatisk udvidende arkivering for alle brugere i organisationen kan du kun aktivere den for bestemte brugere. Det kan du gøre, fordi det kun er nogle brugere, der har behov for en stor arkivlagerkapacitet.
  
Når du aktiverer automatisk udvidende arkivering for en bestemt bruger og brugerens postkasse i venteposition eller tildelt en opbevaringspolitik, foretages følgende to konfigurationsændringer:
  
- Lagerkvoten for brugerens primære arkivpostkasse øges med 10 GB (fra 100 GB til 110 GB). Arkivadvarselskvoten øges også med 10 GB (fra 90 GB til 100 GB).

- Lagerkvoten for mappen genoprettelige elementer i brugerens primære postkasse øges med 10 GB (også fra 100 GB til 110 GB). Advarselskvoten for genoprettelige elementer øges også med 10 GB (fra 90 GB til 100 GB). Disse ændringer er kun gældende, hvis postkassen er sat i venteposition eller er tildelt en opbevaringspolitik.

Denne ekstra plads tilføjes for at forhindre eventuelle problemer med lagerplads, der kan opstå, før det automatisk udvidende arkiv klargøres. Der tilføjes  *ikke ekstra*  lagerplads, når du aktiverer automatisk udvidende arkivering for hele organisationen som beskrevet i forrige afsnit.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando i Exchange Online PowerShell for at aktivere automatisk udvidende arkivering for en bestemt bruger. Som beskrevet tidligere skal brugerens arkivpostkasse (hovedarkiv) aktiveres, før du kan aktivere automatisk udvidende arkivering for den pågældende bruger.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> I en Exchange-hybridinstallation kan du ikke bruge kommandoen **Enable-Mailbox -AutoExpandingArchive** til at aktivere automatisk udvidende arkivering for en bestemt bruger, hvis primære postkasse er lokal, og hvis arkivpostkasse er skybaseret. Hvis du vil aktivere automatisk udvidende arkivering for skybaserede arkivpostkasser i en Exchange-hybridinstallation, skal du køre kommandoen **Set-OrganizationConfig -AutoExpandingArchive** i Exchange Online PowerShell for at aktivere automatisk udvidende arkivering for hele organisationen. Hvis en brugers primære postkasser og arkivpostkasser begge er skybaserede, kan du bruge kommandoen **Enable-Mailbox -AutoExpandingArchive** til at aktivere automatisk udvidende arkivering for den bestemte bruger.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Kontrollér, at automatisk udvidende arkivering er aktiveret

For at bekræfte at automatisk udvidende arkivering er aktiveret for din organisation, skal du køre følgende kommando i Exchange Online PowerShell.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

En værdi af  `True` angiver, at automatisk udvidende arkivering er aktiveret for organisationen. 
  
For at bekræfte at automatisk udvidende arkivering er aktiveret for en bestemt bruger, skal du køre følgende kommando i Exchange Online PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

En værdi af  `True` angiver, at automatisk udvidende arkivering er aktiveret for brugeren.
  
For at finde ud af om automatisk udvidende arkivering er aktiveret for inaktive postkasser, skal du køre følgende kommando i Exchange Online PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

En værdi af angiver  `True` , at automatisk udvidende arkivering er aktiveret for den inaktive postkasse. En værdi af `False` angiver, at automatisk udvidende arkivering ikke er aktiveret.

Husk følgende, når du har aktiveret automatisk udvidende arkivering:
  
- Hvis du kører kommandoen **Set-OrganizationConfig -AutoExpandingArchive** for at aktivere automatisk udvidende arkivering for organisationen, behøver du ikke at køre **Enable-Mailbox -AutoExpandingArchive** på individuelle postkasser. Kørsel af cmdlet'en **Set-OrganizationConfig** for at aktivere automatisk udvidende arkivering for organisationen ændrer ikke egenskaben  *AutoExpandingArchiveEnabled*  på brugerpostkasser til `True`.

- På samme måde ændres værdierne for  *egenskaberne for ArchiveQuota*  og  *ArchiveWarningQuota*  ikke, når du aktiverer automatisk udvidende arkivering. Når du aktiverer automatisk udvidende arkivering for en brugerpostkasse, og egenskaben  *AutoUdvidendeArkiverAktiveret*  `True`er angivet til , ignoreres egenskaberne  *ArchiveQuota*  og  *ArchiveWarningQuota*  . Her er et eksempel på disse postkasseegenskaber, når automatisk udvidende arkivering er aktiveret for en brugers postkasse. 

    ![Egenskaberne ArchiveQuota og ArchiveWarningQuota ignoreres, når du aktiverer automatisk udvidende arkivering.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Flere oplysninger

- Du kan også bruge PowerShell til at aktivere arkivpostkasser. Du kan f.eks. køre følgende kommando i Exchange Online PowerShell for at aktivere arkivpostkasser for alle brugere, hvis arkivpostkasse ikke allerede er aktiveret.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Automatisk udvidende arkivering understøttes for skybaserede arkivpostkasser i en Exchange-hybridinstallation for brugere, der har en lokal primær postkasse. Når automatisk udvidende arkivering er aktiveret for en skybaseret arkivpostkasse, kan du dog ikke gå uden om den pågældende arkivpostkasse tilbage til den lokale Exchange organisation. Automatisk udvidende arkivering understøttes ikke for lokale postkasser i nogen version af Exchange Server.

- Du kan finde en liste over Outlook-klienter, som brugere kan bruge til at få adgang til elementer i det ekstra lagringsområde i deres arkivpostkasse, i afsnittet "Outlook-krav til adgang til elementer i et automatisk udvidet arkiv" i Få mere at vide om automatisk [udvidende arkivering](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive).

- Som beskrevet tidligere føjes 10 GB til lagerkvoten for brugerens primære arkivpostkasse (og til mappen Genoprettelige elementer, hvis postkassen er i venteposition), når du kører **kommandoen Enable-Mailbox -AutoExpandingArchive** . Dette giver yderligere lagerplads, indtil den automatisk udvidede lagerplads er klargjort (hvilket kan tage op til 30 dage). Denne ekstra lagerplads tilføjes ikke, når du kører **Set-OrganizationConfig -AutoExpandingArchive** for at aktivere automatisk udvidende arkivering for alle postkasser i organisationen. Hvis du har aktiveret automatisk udvidende arkivering for hele organisationen, men har brug for at tilføje yderligere 10 GB lagerplads for en bestemt bruger, kan du køre kommandoen **Enable-Mailbox -AutoExpandingArchive** på den pågældende postkasse. Du får en fejlmeddelelse om, at automatisk udvidende arkivering allerede er blevet aktiveret, men den ekstra lagerplads føjes til postkassen.

> [!IMPORTANT]
> Automatisk udvidende arkivering understøttes kun for postkasser, der bruges af individuelle brugere, eller for delte postkasser med en væksthastighed, der ikke overstiger 1 GB pr. dag. Journalisering, transportregler eller regler for automatisk videresendelse til at kopiere meddelelser til en arkivpostkasse med henblik på arkivering er ikke tilladt. En brugers arkivpostkasse er kun beregnet til den pågældende bruger. Microsoft forbeholder sig ret til at afvise yderligere arkivering i tilfælde, hvor en brugers arkivpostkasse bruges til at lagre arkivdata til andre brugere eller i andre tilfælde af upassende brug.
