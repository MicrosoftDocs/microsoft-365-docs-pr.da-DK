---
title: Aktivér automatisk udvidelse af arkiv
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
description: 'Administratorer: Få mere at vide om, hvordan du aktiverer automatisk udvidelse af arkivering, hvilket giver dine brugere ekstra lagerplads til deres Exchange Online postkasser. Du kan aktivere automatisk udvidelse af arkivering for hele organisationen eller kun for bestemte brugere.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 16fa0a1a53572d0680160441b237cc7ceb27f712
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622871"
---
# <a name="enable-auto-expanding-archiving"></a>Aktivér automatisk udvidelse af arkiv

Du kan bruge Exchange Online arkiveringsfunktion, der automatisk udvides, til at give ekstra lagerplads til arkivpostkasser. Når automatisk udvidelse af arkivering er slået til, føjes der automatisk ekstra lagerplads til en brugers arkivpostkasse, indtil den når lagergrænsen på 1,5 TB. Du kan aktivere automatisk udvidelse af arkivering for alle i din organisation eller kun for bestemte brugere. Du kan finde flere oplysninger om automatisk udvidelse af arkivering under [Få mere at vide om automatisk udvidelse af arkivering](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Før du aktiverer automatisk udvidelse af arkivering

- Når du har slået automatisk udvidelse af arkivering til for din organisation eller for en bestemt bruger, kan den ikke slås fra. Desuden kan administratorer ikke justere lagerkvoten for automatisk udvidelse af arkivering.

- Du skal være global administrator i din organisation eller medlem af rollegruppen Organisationsadministration i din Exchange Online organisation for at aktivere automatisk udvidelse af arkivering. Alternativt skal du være medlem af en rollegruppe, der har fået tildelt rollen Postmodtagere for at aktivere automatisk udvidelse af arkivering for bestemte brugere.

- En brugers arkivpostkasse skal aktiveres, før du kan aktivere automatisk udvidelse af arkivering. En bruger skal have tildelt en Exchange Online Plan 2-licens for at aktivere arkivpostkassen. Hvis en bruger har fået tildelt en Exchange Online Plan 1-licens, skal du tildele vedkommende en separat Exchange Online-arkivering licens for at aktivere vedkommendes arkivpostkasse. Se [Aktivér arkivpostkasser](enable-archive-mailboxes.md).

- Når du har aktiveret automatisk udvidelse af arkivering, konverteres en arkivpostkasse til et arkiv, der automatisk udvides, når arkivpostkassen (herunder mappen Gendanbare elementer) når 90 GB. Det kan tage op til 30 dage, før den ekstra lagerplads klargøres.

- Du kan også bruge PowerShell til at aktivere arkivpostkasser. Se afsnittet [Flere oplysninger](#more-information) for at få et eksempel på den PowerShell-kommando, du kan bruge til at aktivere arkivpostkasser for alle brugere i din organisation.

- Arkivering, der automatisk udvides, understøtter også delte postkasser. Hvis du vil aktivere arkivet for en delt postkasse, kræves der en Exchange Online Plan 2-licens eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering licens.

- Automatisk udvidelse af arkivering forhindrer dig i at gendanne eller gendanne en [inaktiv postkasse](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Det betyder, at hvis du aktiverer automatisk udvidelse af arkivering for en postkasse, og postkassen gøres inaktiv på et senere tidspunkt, kan du ikke [gendanne den inaktive postkasse](recover-an-inactive-mailbox.md) (ved at konvertere den til en aktiv postkasse) eller [gendanne den](restore-an-inactive-mailbox.md) (ved at flette indholdet til en eksisterende postkasse). Hvis automatisk udvidelse af arkivering er aktiveret i en inaktiv postkasse, kan du kun gendanne data ved at bruge søgeværktøjet Indhold i Microsoft Purview-compliance-portal til at eksportere dataene fra postkassen og importere dem til en anden postkasse. Du kan finde flere oplysninger i afsnittet "Inaktive postkasser og arkiver til automatisk udvidelse" i [Få mere at vide om inaktive postkasser](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Du kan ikke bruge Exchange Administration eller Microsoft Purview-compliance-portal til at aktivere automatisk udvidelse af arkivering. Du skal bruge Exchange Online PowerShell. Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Aktivér automatisk udvidelse af arkivering for hele organisationen

Du kan aktivere automatisk udvidelse af arkivering for hele organisationen. Når du har slået den til, aktiveres automatisk udvidelse af arkivering for eksisterende brugerpostkasser og for nye brugerpostkasser, der oprettes. Når du opretter brugerpostkasser, skal du sørge for at aktivere brugerens primære arkivpostkasse, så funktionen til automatisk udvidelse af arkivering fungerer for den nye brugerpostkasse.
  
1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando i Exchange Online PowerShell for at aktivere automatisk udvidelse af arkivering for hele organisationen.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Aktivér automatisk udvidelse af arkivering for bestemte brugere

I stedet for at aktivere automatisk udvidelse af arkivering for alle brugere i din organisation kan du kun aktivere den for bestemte brugere. Det kan du gøre, fordi det kun er nogle brugere, der har brug for en stor arkivlagerkapacitet.
  
Når du aktiverer automatisk udvidelse af arkivering for en bestemt bruger og brugerens postkasse i venteposition eller tildelt til en opbevaringspolitik, foretages følgende to konfigurationsændringer:
  
- Lagerkvoten for brugerens primære arkivpostkasse er steget med 10 GB (fra 100 GB til 110 GB). Arkivadvarselskvoten øges også med 10 GB (fra 90 GB til 100 GB).

- Lagerkvoten for mappen Gendanbare elementer i brugerens primære postkasse øges med 10 GB (også fra 100 GB til 110 GB). Advarselskvoten For genoprettelige elementer er også steget med 10 GB (fra 90 GB til 100 GB). Disse ændringer gælder kun, hvis postkassen er i venteposition eller tildelt en opbevaringspolitik.

Denne ekstra plads tilføjes for at forhindre eventuelle lagerproblemer, der kan opstå, før arkivet til automatisk udvidelse klargøres. Der  *tilføjes ikke*  ekstra lagerplads, når du aktiverer automatisk udvidelse af arkivering for hele organisationen, som beskrevet i forrige afsnit.
  
1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kør følgende kommando i Exchange Online PowerShell for at aktivere automatisk udvidelse af arkivering for en bestemt bruger. Som tidligere forklaret skal brugerens arkivpostkasse (hovedarkiv) være aktiveret, før du kan aktivere automatisk udvidelse af arkivering for den pågældende bruger.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> I en Exchange-hybridinstallation kan du ikke bruge kommandoen **Enable-Mailbox -AutoExpandingArchive** til at aktivere automatisk udvidelse af arkivering for en bestemt bruger, hvis primære postkasse er i det lokale miljø, og hvis arkivpostkasse er cloudbaseret. Hvis du vil aktivere automatisk udvidelse af arkivering for skybaserede arkivpostkasser i en Exchange-hybridinstallation, skal du køre kommandoen **Set-OrganizationConfig -AutoExpandingArchive** i Exchange Online PowerShell for at aktivere automatisk udvidelse af arkivering for hele organisationen. Hvis en brugers primære postkasser og arkivpostkasser begge er skybaserede, kan du bruge kommandoen **Enable-Mailbox -AutoExpandingArchive** til at aktivere automatisk udvidelse af arkivering for den pågældende bruger.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Kontrollér, at arkivering, der automatisk udvides, er aktiveret

Kør følgende kommando i Exchange Online PowerShell for at bekræfte, at automatisk udvidelse af arkivering er aktiveret for din organisation.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

Værdien angiver  `True` , at automatisk udvidelse af arkivering er aktiveret for organisationen. 
  
Hvis du vil kontrollere, at arkivering, der automatisk udvides, er aktiveret for en bestemt bruger, skal du køre følgende kommando i Exchange Online PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

`True` Værdien angiver, at automatisk udvidelse af arkivering er aktiveret for brugeren.
  
Hvis du vil finde ud af, om automatisk udvidelse af arkivering er aktiveret for inaktive postkasser, skal du køre følgende kommando i Exchange Online PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

Værdien angiver, at automatisk udvidelse af  `True` arkivering er aktiveret for den inaktive postkasse. `False` Værdien angiver, at arkivering, der automatisk udvides, ikke er aktiveret.

Vær opmærksom på følgende ting, når du har aktiveret automatisk udvidelse af arkivering:
  
- Hvis du kører kommandoen **Set-OrganizationConfig -AutoExpandingArchive** for at aktivere automatisk udvidelse af arkivering for din organisation, behøver du ikke at køre **Enable-Mailbox -AutoExpandingArchive** på individuelle postkasser. Hvis du kører **Set-OrganizationConfig-cmdlet'en** for at aktivere automatisk udvidelse af arkivering for din organisation, ændres egenskaben  *AutoExpandingArchiveEnabled*  ikke for brugerpostkasser til `True`.

- På samme måde ændres værdierne for egenskaberne  *for postkassen ArchiveQuota*  og  *ArchiveWarningQuota*  ikke, når du aktiverer automatisk udvidelse af arkivering. Når du aktiverer automatisk udvidelse af arkivering for en brugerpostkasse, og egenskaben  *AutoExpandingArchiveEnabled*  er angivet til  `True`, ignoreres egenskaberne  *ArchiveQuota*  og  *ArchiveWarningQuota*  . Her er et eksempel på disse egenskaber for postkassen, når automatisk udvidelse af arkivering er aktiveret for en brugers postkasse. 

    ![Egenskaberne ArchiveQuota og ArchiveWarningQuota ignoreres, når du har aktiveret automatisk udvidelse af arkivering.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Flere oplysninger

- Du kan også bruge PowerShell til at aktivere arkivpostkasser. Du kan f.eks. køre følgende kommando i Exchange Online PowerShell for at aktivere arkivpostkasser for alle brugere, hvis arkivpostkasse ikke allerede er aktiveret.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Automatisk udvidelse af arkivering understøttes for skybaserede arkivpostkasser i en Exchange-hybridinstallation for brugere, der har en primær postkasse i det lokale miljø. Men når automatisk udvidelse af arkivering er aktiveret for en skybaseret arkivpostkasse, kan du ikke gå uden for arkivpostkassen tilbage til Exchange-organisationen i det lokale miljø. Automatisk udvidelse af arkivering understøttes ikke for postkasser i det lokale miljø i nogen version af Exchange Server.

- Du kan finde en liste over Outlook-klienter, som brugerne kan bruge til at få adgang til elementer i det ekstra lagerområde i deres arkivpostkasse, i afsnittet "Outlook-krav til adgang til elementer i et automatisk udvidet arkiv" i [Få mere at vide om automatisk udvidelse af arkivering](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive).

- Som tidligere forklaret føjes 10 GB til lagerkvoten for brugerens primære arkivpostkasse (og til mappen Gendan elementer, hvis postkassen er i venteposition), når du kører kommandoen **Enable-Mailbox -AutoExpandingArchive** . Dette giver ekstra lagerplads, indtil den automatisk udvidede lagerplads er klargjort (hvilket kan tage op til 30 dage). Denne ekstra lagerplads tilføjes ikke, når du kører **Set-OrganizationConfig -AutoExpandingArchive** for at aktivere automatisk udvidelse af arkivering for alle postkasser i din organisation. Hvis du har aktiveret automatisk udvidelse af arkivering for hele organisationen, men har brug for at tilføje yderligere 10 GB lagerplads til en bestemt bruger, kan du køre kommandoen **Enable-Mailbox -AutoExpandingArchive** på den pågældende postkasse. Du får vist en fejlmeddelelse om, at automatisk udvidelse af arkivering allerede er aktiveret, men den ekstra lagerplads føjes til postkassen.

> [!IMPORTANT]
> Automatisk udvidelse af arkivering understøttes kun for postkasser, der bruges af individuelle brugere, eller for delte postkasser med en vækstrate, der ikke overstiger 1 GB pr. dag. Det er ikke tilladt at bruge journaling, transportregler eller regler for automatisk videresendelse til kopiering af meddelelser til en arkivpostkasse med henblik på arkivering. En brugers arkivpostkasse er kun beregnet til den pågældende bruger. Microsoft forbeholder sig ret til at nægte yderligere arkivering i tilfælde, hvor en brugers arkivpostkasse bruges til at gemme arkivdata for andre brugere eller i andre tilfælde af upassende brug.
