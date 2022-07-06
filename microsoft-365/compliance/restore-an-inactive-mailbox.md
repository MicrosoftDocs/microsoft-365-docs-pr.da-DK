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
ms.openlocfilehash: 7c1a976013f522e45b4e96d6b28653fa860fe16f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629217"
---
# <a name="restore-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

En inaktiv postkasse (som er en type blød slettet postkasse) bruges til at bevare en tidligere medarbejders mail, når vedkommende forlader din organisation. Hvis en anden medarbejder påtager sig ansvarsområderne for den fragåede medarbejder, eller hvis den pågældende medarbejder vender tilbage til din organisation, er der to måder, hvorpå du kan gøre indholdet af den inaktive postkasse tilgængeligt for en bruger:

- **Gendan en inaktiv postkasse** Hvis en anden medarbejder påtager sig den fraværende medarbejders ansvarsområder, eller hvis en anden bruger har brug for at få adgang til indholdet af den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse til en eksisterende postkasse. Du kan også gendanne arkivet fra en inaktiv postkasse. Når den er gendannet, bevares den inaktive postkasse og bevares som en inaktiv postkasse. I denne artikel beskrives procedurerne for gendannelse af en inaktiv postkasse.

- **Gendan en inaktiv postkasse** Hvis den fragåede medarbejder vender tilbage til din organisation, eller hvis en ny medarbejder hyres til at påtage sig den fragåede medarbejders ansvarsområder, kan du gendanne indholdet af den inaktive postkasse. Denne metode konverterer den inaktive postkasse til en ny postkasse, der indeholder indholdet af den inaktive postkasse. Når den er gendannet, findes den inaktive postkasse ikke længere. Du kan finde de trinvise procedurer under [Gendan en inaktiv postkasse i Office 365](recover-an-inactive-mailbox.md).

Se afsnittet [Flere oplysninger](#more-information) i denne artikel for at få flere oplysninger om forskellene mellem gendannelse og gendannelse af en inaktiv postkasse.

> [!NOTE]
> Du kan ikke gendanne eller gendanne en inaktiv postkasse, der er konfigureret med et arkiv, der automatisk udvides. Hvis du har brug for at gendanne data fra en inaktiv postkasse med et arkiv, der automatisk udvides, skal du bruge indholdssøgning til at eksportere dataene fra postkassen og derefter importere til en anden postkasse. Du kan finde instruktioner i følgende artikler:
>
> - [Indholdssøgning](content-search.md)
> - [Eksportér resultater af indholdssøgning](export-search-results.md)

## <a name="requirements-to-restore-an-inactive-mailbox"></a>Krav til gendannelse af en inaktiv postkasse

- Du skal bruge Exchange Online PowerShell til at gendanne en inaktiv postkasse. Du kan ikke bruge Exchange Administration eller Microsoft Purview-compliance-portal til denne procedure. Du kan finde en trinvis vejledning i at bruge Exchange Online PowerShell under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Kør følgende kommando i Exchange Online PowerShell for at få identitetsoplysninger for de inaktive postkasser i din organisation.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Brug de oplysninger, der returneres af denne kommando, til at identificere og gendanne en bestemt inaktiv postkasse.

- Du kan få flere oplysninger om inaktive postkasser [under Inaktive postkasser i Office 365](inactive-mailboxes-in-office-365.md).

## <a name="restore-inactive-mailboxes"></a>Gendan inaktive postkasser

Brug cmdlet'en **New-MailboxRestoreRequest** med parametrene  _SourceMailbox_ og  _TargetMailbox_ til at gendanne indholdet af en inaktiv postkasse til en eksisterende postkasse. Du kan få flere oplysninger om brug af denne cmdlet under [New-MailboxRestoreRequest](/powershell/module/exchange/new-mailboxrestorerequest).

Før du kan gendanne en inaktiv postkasse, skal du føje LegacyExchangeDN for den inaktive postkasse til målpostkassen som en X500-proxyadresse for destinationspostkassen. Dette skal gøres, fordi **cmdlet'en New-MailboxRestoreRestoreRequest** kontrollerer, at værdien af egenskaben **LegacyExchangeDN** for kilde- og destinationspostkasserne er den samme. Når du har gendannet den inaktive postkasse, kan du eventuelt fjerne LegacyExchangeDN for den inaktive postkasse fra kildepostkassen. Sørg for at vente, indtil anmodningen om gendannelse af postkassen er fuldført, før du fjerner LegacyExchangeDN.

Følg disse trin for at gendanne en inaktiv postkasse til en eksisterende postkasse:

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > I den forrige kommando skal du bruge værdien af egenskaben **DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i din organisation, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have samme primære SMTP-adresse.

2. Vis LegacyExchangeDN for den inaktive postkasse, så du kan føje den som en proxyadresse til destinationspostkassen i næste trin.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Føj LegacyExchangeDN for den inaktive postkasse som en X500-proxyadresse til destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Gendan indholdet af den inaktive postkasse til en eksisterende postkasse. Indholdet af den inaktive postkasse (kildepostkasse) flettes med de tilsvarende mapper i den eksisterende postkasse (destinationspostkasse).

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> 
   ```

   Du kan også angive en mappe på øverste niveau i destinationspostkassen, hvor indholdet skal gendannes fra den inaktive postkasse. Hvis den angivne målmappe eller målmappestruktur ikke allerede findes i destinationspostkassen, oprettes den under gendannelsen.

   I dette eksempel kopieres postkasseelementer og undermapper fra en inaktiv postkasse til en mappe med navnet "Inactive Mailbox" i målpostkassens mappestruktur på øverste niveau.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> -TargetRootFolder "Inactive Mailbox"
   ```

5. Når gendannelsesanmodningen er fuldført, kan du eventuelt fjerne LegacyExchangeDN for den inaktive postkasse fra destinationspostkassen. Hvis du forlader LegacyExchangeDN fra den inaktive postkasse, påvirker det ikke destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Gendan arkivet fra en inaktiv postkasse

Hvis en inaktiv postkasse har en arkivpostkasse, kan du også gendanne den til arkivpostkassen for en eksisterende postkasse. Hvis du vil gendanne arkivet fra en inaktiv postkasse, skal du føje parametrene _SourceIsArchive_ og _TargetIsArchive_ til den kommando, der bruges til at gendanne en inaktiv postkasse.

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!NOTE]
   > I den forrige kommando skal du bruge værdien af egenskaben **DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i din organisation, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have samme primære SMTP-adresse.

2. Vis LegacyExchangeDN for den inaktive postkasse, så du kan føje den som en proxyadresse til destinationspostkassen i næste trin.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Føj LegacyExchangeDN for den inaktive postkasse som en X500-proxyadresse til destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Gendan indholdet af arkivet fra den inaktive postkasse (kildearkiv) til arkivet for en eksisterende postkasse (destinationsarkiv). I dette eksempel kopieres indholdet fra kildearkivet til en mappe med navnet "Inactive Mailbox Archive" i arkivet for destinationspostkassen.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox <identity of target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive"
   ```

5. Når gendannelsesanmodningen er fuldført, kan du eventuelt fjerne LegacyExchangeDN for den inaktive postkasse fra destinationspostkassen. Hvis du forlader LegacyExchangeDN fra den inaktive postkasse, påvirker det ikke destinationspostkassen.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="more-information"></a>Flere oplysninger

- **Hvad er hovedforskellen mellem gendannelse og gendannelse af en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse. Indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen er knyttet til en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere, og eventuelle ændringer af indholdet i den nye postkasse påvirker det indhold, der oprindeligt var i venteposition i den inaktive postkasse. Hvis du derimod gendanner en inaktiv postkasse, kopieres indholdet blot til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. Eventuelle ændringer af indholdet i målpostkassen påvirker ikke det oprindelige indhold, der opbevares i den inaktive postkasse. Der kan stadig søges i den inaktive postkasse ved hjælp af [indholdssøgeværktøjet](content-search.md), indholdet kan gendannes i en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt.

- **Hvordan finder du inaktive postkasser?** Hvis du vil hente en liste over de inaktive postkasser i din organisation og få vist oplysninger, der er nyttige til gendannelse af en inaktiv postkasse, kan du køre denne kommando.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Brug en Opbevaringspolitik for Microsoft 365 eller Procesvist bevarelse eller til at bevare inaktivt postkasseindhold.** Hvis du vil bevare tilstanden for en inaktiv postkasse, når den er gendannet, kan du anvende en [Microsoft 365-opbevaringspolitik](retention.md) på målpostkassen eller placere målpostkassen i [Litigation Venteposition](create-a-litigation-hold.md) , før du gendanner den inaktive postkasse. Dette forhindrer permanent sletning af elementer fra den inaktive postkasse, når de er gendannet til målpostkassen.

- **Aktivér bevarelse på målpostkassen, før du gendanner en inaktiv postkasse.** Da postkasseelementer fra en inaktiv postkasse kan være gamle, kan du overveje at aktivere opbevaringshold på målpostkassen, før du gendanner en inaktiv postkasse. Når du sætter en postkasse i opbevaringsventeposition, behandles den opbevaringspolitik, der er tildelt den, ikke, før opbevarings ventepositionen fjernes, eller indtil opbevaringsperioden udløber. Dette giver ejeren af målpostkassen tid til at administrere gamle meddelelser fra den inaktive postkasse. Ellers kan opbevaringspolitikken slette gamle elementer (eller flytte elementer til arkivpostkassen, hvis den er aktiveret), der er udløbet, baseret på de opbevaringsindstillinger, der er konfigureret for målpostkassen. Du kan få flere oplysninger under [Placer en postkasse i opbevaringsventeposition i Exchange Online](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Du kan bruge andre parametre sammen med New-MailboxRestoreRequest-cmdlet'en til at implementere forskellige gendannelsesscenarier for inaktive postkasser.** Du kan f.eks. køre denne kommando for at gendanne arkivet fra den inaktive postkasse til den primære postkasse i destinationspostkassen.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive"
  ```

  Du kan også gendanne den inaktive primære postkasse i arkivet for destinationspostkassen ved at køre denne kommando.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox"
  ```

- **Hvad gør parameteren TargetRootFolder?** Som tidligere forklaret kan du bruge parameteren **TargetRootFolder** til at angive en mappe øverst i mappestrukturen (også kaldet roden) i destinationspostkassen, hvor indholdet af den inaktive postkasse skal gendannes. Hvis du ikke bruger denne parameter, flettes postkasseelementer fra den inaktive postkasse med de tilsvarende standardmapper i målpostkassen, og brugerdefinerede mapper oprettes igen i roden af destinationspostkassen. Følgende illustrationer fremhæver disse forskelle mellem ikke at bruge og at bruge parameteren **TargetRootFolder** .

  **Mappehierarki i destinationspostkassen, når parameteren TargetRootFolder ikke bruges**

  ![Skærmbillede, når parameteren TargetRootFolder ikke bruges.](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)

  **Mappehierarki i destinationspostkassen, når parameteren TargetRootFolder bruges**

  ![Skærmbillede, når parameteren TargetRootFolder bruges.](../media/300da592-7323-48db-b8a4-07012259d113.png)
