---
title: Gendan en inaktiv postkasse
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
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
ms.assetid: 97e06a7a-ef9a-4ce8-baea-18b9e20449a3
description: Få mere at vide om, hvordan du gendanner (eller fletter) indholdet af en inaktiv postkasse til en eksisterende postkasse.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaf0ce7f67ae0146beceeeb667263908d7cff75d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63588968"
---
# <a name="restore-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

En inaktiv postkasse (som er en type blød-slettet postkasse) bruges til at bevare en tidligere medarbejders mail, når han eller hun forlader organisationen. Hvis en anden medarbejder påtager sig den fragåede medarbejders arbejdsansvarsområde, eller hvis den pågældende medarbejder returnerer til organisationen, er der to måder, hvorpå du kan gøre indholdet af den inaktive postkasse tilgængeligt for en bruger:

- **Gendan en inaktiv postkasse** Hvis en anden medarbejder påtager sig den fragåede medarbejders arbejdsansvarsområde, eller hvis en anden bruger skal have adgang til indholdet i den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse i en eksisterende postkasse. Du kan også gendanne arkivet fra en inaktiv postkasse. Når den er gendannet, bevares den inaktive postkasse og bevares som en inaktiv postkasse. I dette emne beskrives procedurerne for gendannelse af en inaktiv postkasse.

- **Gendan en inaktiv postkasse** Hvis den afgåede medarbejder returnerer til din organisation, eller hvis en ny medarbejder bliver ansat til at tage ansvaret for jobbet for den afgåede medarbejder, kan du gendanne indholdet i den inaktive postkasse. Denne metode konverterer den inaktive postkasse til en ny postkasse, der indeholder indholdet af den inaktive postkasse. Når den er gendannet, findes den inaktive postkasse ikke længere. Du kan finde en trinvis vejledning under Gendanne en [inaktiv postkasse i Office 365](recover-an-inactive-mailbox.md).

Se afsnittet [Flere oplysninger i](#more-information) denne artikel for at få mere at vide om forskellene mellem at gendanne og gendanne en inaktiv postkasse.

> [!NOTE]
> Du kan ikke gendanne en inaktiv postkasse, der er konfigureret med et automatisk udvidende arkiv. Hvis du har brug for at gendanne data fra en inaktiv postkasse med et automatisk udvidende arkiv, skal du bruge indholdssøgning til at eksportere dataene fra postkassen og derefter importere til en anden postkasse. Du kan finde instruktioner i følgende emner:
>
> - [Indholdssøgning](content-search.md)
> - [Eksportér resultater fra indholdssøgning](export-search-results.md)

## <a name="requirements-to-restore-an-inactive-mailbox"></a>Krav til gendannelse af en inaktiv postkasse

- Du skal bruge en Exchange Online PowerShell til at gendanne en inaktiv postkasse. Du kan ikke bruge Exchange Administration (EAC). Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Kør følgende kommando i Exchange Online PowerShell for at få identitetsoplysninger om de inaktive postkasser i organisationen.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Brug de oplysninger, der returneres af denne kommando, til at identificere og gendanne en bestemt inaktiv postkasse.

- Du kan finde flere oplysninger om inaktive [postkasser i Inaktive postkasser Office 365](inactive-mailboxes-in-office-365.md).

## <a name="restore-inactive-mailboxes"></a>Gendan inaktive postkasser

Brug **New-MailboxRestoreRequest-cmdlet'en** med  _parametrene SourceMailbox_ og  _TargetMailbox_ til at gendanne indholdet af en inaktiv postkasse til en eksisterende postkasse. Du kan finde flere oplysninger om brug af denne cmdlet [under New-MailboxRestoreRequest](/powershell/module/exchange/new-mailboxrestorerequest).

Før du kan gendanne en inaktiv postkasse, skal du føje LegacyExchangeDN for den inaktive postkasse til destinationspostkassen som en X500-proxyadresse for destinationspostkassen. Dette skal gøres, fordi **New-MailboxRestoreRestoreRequest-cmdlet'en** kontrollerer, at værdien af egenskaben **LegacyExchangeDN** på kilde- og målpostkasser er den samme. Når du gendanner den inaktive postkasse, kan du vælge at fjerne LegacyExchangeDN for den inaktive postkasse fra kildepostkassen. Sørg for at vente, indtil anmodningen om gendannelse af postkassen er fuldført, før du fjerner LegacyExchangeDN.

Følg disse trin for at gendanne en inaktiv postkasse til en eksisterende postkasse:

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > I den forrige kommando skal du bruge værdien af **egenskaben DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i organisationen, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have den samme primære SMTP-adresse.

2. Vis LegacyExchangeDN for den inaktive postkasse, så du kan tilføje den som en proxyadresse til målpostkassen i næste trin.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Tilføj LegacyExchangeDN for den inaktive postkasse som en X500-proxyadresse til destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Gendan indholdet af den inaktive postkasse til en eksisterende postkasse. Indholdet af den inaktive postkasse (kildepostkassen) flettes til de tilsvarende mapper i den eksisterende postkasse (destinationspostkasse).

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> 
   ```

   Du kan også angive en mappe på øverste niveau i målpostkassen, hvor indholdet fra den inaktive postkasse skal gendannes. Hvis den angivne målmappe eller målmappestruktur ikke allerede findes i målpostkassen, oprettes den under gendannelsesprocessen.

   I dette eksempel kopieres postkasseelementer og undermapper fra en inaktiv postkasse til en mappe med navnet "Inaktiv postkasse" i mappestrukturen på øverste niveau i målpostkassen.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> -TargetRootFolder "Inactive Mailbox"
   ```

5. Når gendannelsesanmodningen er fuldført, kan du vælge at fjerne LegacyExchangeDN for den inaktive postkasse fra destinationspostkassen. Når du forlader LegacyExchangeDN fra den inaktive postkasse, påvirker det ikke destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Gendan arkivet fra en inaktiv postkasse

Hvis en inaktiv postkasse har en arkivpostkasse, kan du også gendanne den til arkivpostkassen i en eksisterende postkasse. Hvis du vil gendanne arkivet fra en inaktiv postkasse, skal du føje _SourceIsArchive_ og _TargetIsArchive_ til den kommando, der bruges til at gendanne en inaktiv postkasse.

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!NOTE]
   > I den forrige kommando skal du bruge værdien af **egenskaben DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i organisationen, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have den samme primære SMTP-adresse.

2. Vis LegacyExchangeDN for den inaktive postkasse, så du kan tilføje den som en proxyadresse til målpostkassen i næste trin.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Tilføj LegacyExchangeDN for den inaktive postkasse som en X500-proxyadresse til destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Gendan indholdet af arkivet fra den inaktive postkasse (kildearkivet) til arkivet for en eksisterende postkasse (destinationsarkiv). I dette eksempel kopieres indholdet fra kildearkivet til en mappe med navnet "Inaktiv postkassearkiv" i arkivet for destinationspostkassen.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox <identity of target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive"
   ```

5. Når gendannelsesanmodningen er fuldført, kan du vælge at fjerne LegacyExchangeDN for den inaktive postkasse fra destinationspostkassen. Når du forlader LegacyExchangeDN fra den inaktive postkasse, påvirker det ikke destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="more-information"></a>Flere oplysninger

- **Hvad er den største forskel mellem at gendanne og gendanne en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse. Indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen sammenkædes med en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere, og ændringer af indholdet i den nye postkasse påvirker det indhold, der oprindeligt var i venteposition i den inaktive postkasse. Hvis du derimod gendanner en inaktiv postkasse, kopieres indholdet blot til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. De ændringer, der foretages af indholdet i målpostkassen, påvirker ikke det oprindelige indhold, der opbevares i den inaktive postkasse. Den inaktive postkasse kan stadig søges ved hjælp af værktøjet Indholdssøgning [,](content-search.md) dens indhold kan gendannes til en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt.

- **Hvordan finder du inaktive postkasser?** Du kan køre denne kommando for at få en liste over de inaktive postkasser i organisationen og få vist oplysninger, der er nyttige ved gendannelse af en inaktiv postkasse.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Brug en Microsoft 365 opbevaringspolitik eller retslig tilbageholdelse eller til at bevare inaktiv postkasseindhold.** Hvis du vil bevare tilstanden for en inaktiv postkasse, efter den er gendannet, kan du anvende en [Microsoft 365-opbevaringspolitik](retention.md) på målpostkassen eller placere målpostkassen på [Litigation Hold](create-a-litigation-hold.md, før du gendanner den inaktive postkasse. Dette vil forhindre permanent sletning af elementer fra den inaktive postkasse, når de er gendannet til destinationspostkassen.

- **Aktivér opbevaringsposition på målpostkassen, før du gendanner en inaktiv postkasse.** Da postkasseelementer fra en inaktiv postkasse kan være gamle, kan du overveje at aktivere opbevaring af postkassen, før du gendanner en inaktiv postkasse. Når du sætter en postkasse i opbevaringsposition, behandles den opbevaringspolitik, der er tildelt den, ikke før opbevaringspositionen fjernes, eller indtil opbevaringsperioden udløber. Dette giver ejeren af målpostkassen tid til at administrere gamle meddelelser fra den inaktive postkasse. Ellers kan opbevaringspolitikken slette gamle elementer (eller flytte elementer til arkivpostkassen, hvis den er aktiveret), som er udløbet, baseret på de opbevaringsindstillinger, der er konfigureret for målpostkassen. Få mere at vide under [Placer en postkasse i venteposition i Exchange Online](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Du kan bruge andre parametre med New-MailboxRestoreRequest-cmdlet'en til at implementere forskellige gendannelsesscenarier for inaktive postkasser.** Du kan f.eks. køre denne kommando for at gendanne arkivet fra den inaktive postkasse i den primære postkasse i destinationspostkassen.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive"
  ```

  Du kan også gendanne den inaktive primære postkasse i arkivet for destinationspostkassen ved at køre denne kommando.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox"
  ```

- **Hvad gør parameteret TargetRootFolder?** Som beskrevet tidligere kan du bruge **parameteren TargetRootFolder** til at angive en mappe øverst i mappestrukturen (også kaldet roden) i målpostkassen, hvori indholdet af den inaktive postkasse gendannes. Hvis du ikke bruger denne parameter, flettes postkasseelementer fra den inaktive postkasse ind i de tilsvarende standardmapper i målpostkassen, og brugerdefinerede mapper oprettes igen i roden af destinationspostkassen. Følgende illustrationer fremhæver disse forskelle mellem ikke at bruge og brugen af **parameteren TargetRootFolder** .

  **Mappehierarki i målpostkassen, når parameteren TargetRootFolder ikke bruges**

  ![Skærmbillede, når parameteren TargetRootFolder ikke bruges.](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)

  **Mappehierarki i målpostkassen, når parameteren TargetRootFolder bruges**

  ![Skærmbillede, når parameteret TargetRootFolder bruges.](../media/300da592-7323-48db-b8a4-07012259d113.png)
