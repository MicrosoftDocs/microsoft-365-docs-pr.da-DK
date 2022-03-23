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
ms.assetid: 35d0ecdb-7cb0-44be-ad5c-69df2f8f8b25
ms.custom: seo-marvel-apr2020
description: Lær at gendanne indholdet af en inaktiv postkasse i Office 365 ved at konvertere den til en ny postkasse, der indeholder indholdet af den inaktive postkasse.
ms.openlocfilehash: ce09d218d86e7cd949da1df80cc75a19fce64159
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587745"
---
# <a name="recover-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

En inaktiv postkasse (som er en type blød-slettet postkasse) bruges til at bevare en tidligere medarbejders mail, når han eller hun forlader organisationen. Hvis den pågældende medarbejder vender tilbage til din organisation, eller hvis en anden medarbejder påtager sig den tidligere medarbejders arbejdsansvarsområde, er der to måder, hvorpå du kan gøre indholdet af den inaktive postkasse tilgængeligt for en bruger:

- **Gendanne en inaktiv postkasse.** Hvis den tidligere medarbejder vender tilbage til organisationen, eller hvis en ny medarbejder ansættes til at tage den tidligere medarbejders arbejdsansvarsområder, kan du gendanne indholdet i den inaktive postkasse. Denne metode konverterer den inaktive postkasse til en ny, aktiv postkasse, der indeholder indholdet af den inaktive postkasse. Når den er gendannet, findes den inaktive postkasse ikke længere. Fremgangsmåderne i dette emne beskriver denne metode.

- **Gendan en inaktiv postkasse.** Hvis en anden medarbejder påtager sig den tidligere medarbejders arbejdsansvarsområde, eller hvis en anden bruger skal have adgang til indholdet i den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse i en eksisterende postkasse. Du kan også gendanne arkivet fra en inaktiv postkasse. Du kan finde fremgangsmåderne for denne metode under [Gendan en inaktiv postkasse Office 365](restore-an-inactive-mailbox.md).

Se afsnittet [Flere oplysninger](#more-information) for at få mere at vide om forskellene mellem at gendanne og gendanne en inaktiv postkasse og for at få en beskrivelse af, hvad der sker, når en inaktiv postkasse gendannes.

> [!NOTE]
> Du kan ikke gendanne en inaktiv postkasse, der er konfigureret med et automatisk udvidende arkiv. Hvis du har brug for at gendanne data fra en inaktiv postkasse med et automatisk udvidende arkiv, skal du bruge indholdssøgning til at eksportere dataene fra postkassen og derefter importere til en anden postkasse. Du kan finde instruktioner i følgende emner:
>
> - [Indholdssøgning](content-search.md)
> - [Eksportér resultater fra indholdssøgning](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Krav til gendannelse af en inaktiv postkasse

- Du skal bruge en Exchange Online PowerShell til at gendanne en inaktiv postkasse. Du kan ikke bruge Exchange Administration (EAC). Du kan finde en trinvis vejledning under Forbind [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Kør følgende kommando for at få identitetsoplysninger om de inaktive postkasser i organisationen.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Brug de oplysninger, der returneres af denne kommando, til at gendanne en bestemt inaktiv postkasse.

## <a name="recover-inactive-mailboxes"></a>Gendan inaktive postkasser

Brug **cmdlet'en New-Mailbox** med  *parameteren InactiveMailbox*  til at gendanne en inaktiv postkasse.

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > I den forrige kommando skal du bruge værdien af **egenskaben DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i organisationen, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have den samme primære SMTP-adresse.

2. I dette eksempel bruges de egenskaber, der blev hentet i den forrige kommando, og den inaktive postkasse gendannes til en aktiv postkasse for brugeren Ann Beebe. Sørg for, at de værdier, der er angivet for  *parametrene Name*  og  *MicrosoftOnlineServicesID*  , er entydige i organisationen.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Den primære SMTP-adresse for den gendannede inaktive postkasse har den samme værdi som den, der er angivet af  *parameteren MicrosoftOnlineServicesID*  .

Når du gendanner en inaktiv postkasse, oprettes der også en ny brugerkonto. Du skal aktivere denne brugerkonto ved at tildele en licens. Hvis du vil tildele en licens Microsoft 365 Administration, [skal du se Tilføje brugere og tildele licenser på samme tid](../admin/add-users/add-users.md).

## <a name="more-information"></a>Flere oplysninger

- **Hvad er den største forskel mellem at gendanne og gendanne en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse, indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen sammenkædes med en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere, og ændringer af indholdet i den nye postkasse påvirker det indhold, der oprindeligt var i venteposition i den inaktive postkasse. Hvis du derimod gendanner en inaktiv postkasse, kopieres indholdet blot til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. De ændringer, der foretages af indholdet i målpostkassen, påvirker ikke det oprindelige indhold, der opbevares i den inaktive postkasse. Den inaktive postkasse kan stadig søges ved hjælp af In-Place eDiscovery, dens indhold kan gendannes til en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt.

- **Hvad sker der, når du gendanner en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, sker følgende:

  - Den venteposition, der blev anvendt på en inaktiv postkasse, ændres eller fjernes baseret på den type venteposition, der blev anvendt på den inaktive postkasse, før den blev gendannet.

    - **Retslig venteposition.** Hvis Retslig venteposition er aktiveret for den inaktive postkasse, fjernes den fra den gendannede postkasse.

    - **In-Place Hold In-Place** hold fjernes fra den gendannede postkasse. Det betyder, at den gendannede postkasse fjernes som en kildepostkasse fra In-Place hold eller In-Place eDiscovery-søgning.

    - **Microsoft 365 opbevaringspolitik med Preservation Lock.** Hvis den inaktive postkasse blev tildelt en opbevaringspolitik med Preservation Lock (kaldet en låst opbevaringspolitik *),* tildeles den gendannede postkasse den samme låste opbevaringspolitik. Du kan finde flere oplysninger om låste opbevaringspolitikker i [[Brug Bevarelseslås til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

    - **Microsoft 365 opbevaringspolitik uden Preservation Lock.** Den inaktive postkasse fjernes fra enhver ulåst Microsoft 365 opbevaringspolitik, der blev anvendt på den. Retslig tilbageholdelse er dog aktiveret på den gendannede postkasse for at forhindre sletning af postkasseindhold baseret på opbevaringspolitikker for hele organisationen, der sletter indhold, der er ældre end en bestemt alder. Du kan beholde retslig venteposition eller fjerne den. Du kan få mere at vide [under Opret en retslig venteposition](create-a-litigation-hold.md).

  - Gendannelsesperioden for et enkelt element (som er defineret af **egenskaben RetainDeletedItemsFor for** postkasse) er angivet til 30 dage. Typisk når en ny postkasse oprettes om Exchange Online, er denne opbevaringsperiode indstillet til 14 dage. Hvis du angiver dette til den maksimale værdi på 30 dage, får du mere tid til at gendanne data, der er blevet slettet permanent (eller slettet) fra den inaktive postkasse. Du kan også deaktivere gendannelse af enkelte elementer eller indstille gendannelsesperioden for et enkelt element til standardperioden på 14 dage. Du kan få mere at vide [under Aktivér eller deaktiver gendannelse af enkeltelement for en postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Opbevaringsposition er aktiveret, og opbevaringsvarigheden er indstillet til 30 dage. Det betyder, at standardopbevaringspolitikken for Exchange og opbevaringspolitikker for hele organisationen eller Exchange for hele Microsoft 365, som er tildelt den nye postkasse, ikke behandles i 30 dage. Dette giver den tilbagevendende medarbejder eller den nye ejer af den gendannede inaktive postkasse tid til at administrere de gamle meddelelser. Ellers kan opbevaringspolitikken for Exchange eller Microsoft 365 slette gamle postkasseelementer (eller flytte elementer til arkivpostkassen, hvis den er aktiveret), som er udløbet, baseret på de indstillinger, der er konfigureret til Exchange- eller Microsoft 365-opbevaringspolitikker. Efter 30 dage udløber opbevaringspositionen, opbevaringspostkassens egenskab angives til **Falsk, og** den administrerede mappeassistent begynder at behandle de politikker, der er tildelt postkassen. Hvis du ikke har brug for denne ekstra tid, kan du blot fjerne opbevaringspositionen. Alternativt kan du øge varigheden af opbevaringspositionen ved hjælp af **kommandoen Set-Mailbox -EndDateForRetentionHold** . Få mere at vide under [Sæt en postkasse i venteposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Sæt den gendannede postkasse i venteposition, hvis du har brug for at bevare den oprindelige tilstand for den inaktive postkasse.** Hvis du vil forhindre den nye postkasseejer eller opbevaringspolitik i at slette meddelelser fra den gendannede inaktive postkasse permanent, kan du placere postkassen i Retslig tilbageholdelse. Du kan få mere at vide [under Opret en retslig venteposition](./create-a-litigation-hold.md).

- **Hvilket bruger-id kan du bruge, når du gendanner en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, kan den værdi, du angiver for  *MicrosoftOnlineServicesID-parameteren*  , være forskellig fra den oprindelige, der blev knyttet til den inaktive postkasse. Du kan også bruge det oprindelige bruger-id. Men som tidligere nævnt skal du sørge for, at de værdier, der bruges til  *Name*  og  *MicrosoftOnlineServicesID*  , er entydige i din organisation, når du gendanner den inaktive postkasse.

- **Hvad nu, hvis opbevaringsperioden for den inaktive postkasse ikke er udløbet?** Hvis en inaktiv postkasse blev blød-slettet for mindre end 30 dage siden, kan du ikke bruge kommandoen **New-Mailbox -InactiveMailbox** til at gendanne den. Du skal gendanne den ved at gendanne den tilsvarende brugerkonto. Du kan få mere at vide [under Slet en bruger fra organisationen](../admin/add-users/delete-a-user.md).

- **Hvordan ved du, om opbevaringsperioden for en blød-slettet postkasse for en inaktiv postkasse er udløbet?** Kør følgende kommando.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```

  Hvis der ikke er en værdi for egenskaben **ExternalDirectoryObjectId** , er postkassens opbevaringsperiode udløbet, og du kan gendanne den inaktive postkasse ved at køre kommandoen **Ny postkasse -InactiveMailbox** . Hvis der er en værdi for egenskaben **ExternalDirectoryObjectId** , er opbevaringsperioden for den blød-slettede postkasse ikke udløbet, og du er nødt til at gendanne postkassen ved at gendanne brugerkontoen. Se [Slet en bruger fra organisationen](../admin/add-users/delete-a-user.md).

- **Overvej at aktivere arkivpostkassen, når du gendanner en inaktiv postkasse.** Det gør det muligt for den tilbagevendende bruger eller nye medarbejder at flytte gamle meddelelser til arkivpostkassen. Og når opbevaringspositionen udløber, flytter arkiveringspolitikken, der er en del af Exchange-standardopbevaringspolitikken, der er tildelt Exchange Online-postkasser, elementer, der er to år eller ældre, til arkivpostkassen. Hvis du ikke aktiverer arkivpostkassen, forbliver elementer, der er ældre end to år, i brugerens primære postkasse. Få mere at vide under [Aktivér arkivpostkasser](enable-archive-mailboxes.md).