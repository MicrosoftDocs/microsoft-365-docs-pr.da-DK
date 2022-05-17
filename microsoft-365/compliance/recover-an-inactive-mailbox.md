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
description: Få mere at vide om, hvordan du gendanner indholdet af en inaktiv postkasse i Office 365 ved at konvertere den til en ny postkasse, der indeholder indholdet af den inaktive postkasse.
ms.openlocfilehash: 027abe49a6e517a783f6458013bdcb4d0faee78b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435385"
---
# <a name="recover-an-inactive-mailbox"></a>Gendan en inaktiv postkasse

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

En inaktiv postkasse (som er en type blød slettet postkasse) bruges til at bevare en tidligere medarbejders mail, når vedkommende forlader din organisation. Hvis medarbejderen vender tilbage til din organisation, eller hvis en anden medarbejder påtager sig ansvarsområderne for den tidligere medarbejder, er der to måder, hvorpå du kan gøre indholdet af den inaktive postkasse tilgængeligt for en bruger:

- **Gendan en inaktiv postkasse.** Hvis den tidligere medarbejder vender tilbage til din organisation, eller hvis en ny medarbejder hyres til at påtage sig den tidligere medarbejders ansvarsområder, kan du gendanne indholdet af den inaktive postkasse. Denne metode konverterer den inaktive postkasse til en ny aktiv postkasse, der indeholder indholdet af den inaktive postkasse. Når den er gendannet, findes den inaktive postkasse ikke længere. Procedurerne i denne artikel beskriver denne metode.

- **Gendan en inaktiv postkasse.** Hvis en anden medarbejder påtager sig ansvarsområderne for den tidligere medarbejder, eller hvis en anden bruger skal have adgang til indholdet i den inaktive postkasse, kan du gendanne (eller flette) indholdet af den inaktive postkasse til en eksisterende postkasse. Du kan også gendanne arkivet fra en inaktiv postkasse. Du kan finde procedurerne for denne metode under [Gendan en inaktiv postkasse i Office 365](restore-an-inactive-mailbox.md).

Se afsnittet [Flere oplysninger](#more-information) for at få flere oplysninger om forskellene mellem gendannelse og gendannelse af en inaktiv postkasse og en beskrivelse af, hvad der sker, når en inaktiv postkasse genoprettes.

> [!NOTE]
> Du kan ikke gendanne eller gendanne en inaktiv postkasse, der er konfigureret med et arkiv, der automatisk udvides. Hvis du har brug for at gendanne data fra en inaktiv postkasse med et arkiv, der automatisk udvides, skal du bruge indholdssøgning til at eksportere dataene fra postkassen og derefter importere til en anden postkasse. Du kan finde instruktioner i følgende artikler:
>
> - [Indholdssøgning](content-search.md)
> - [Eksportér resultater af indholdssøgning](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Krav til gendannelse af en inaktiv postkasse

- Du skal bruge Exchange Online PowerShell til at gendanne en inaktiv postkasse. Du kan ikke bruge Exchange Administration eller Microsoft Purview-compliance-portal til denne procedure. Du kan finde en trinvis vejledning i at bruge Exchange Online PowerShell under [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Kør følgende kommando for at hente identitetsoplysninger for de inaktive postkasser i din organisation.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Brug de oplysninger, der returneres af denne kommando, til at gendanne en bestemt inaktiv postkasse.

## <a name="recover-inactive-mailboxes"></a>Gendan inaktive postkasser

Brug **new-Mailbox-cmdlet'en** med parameteren  *InactiveMailbox*  til at gendanne en inaktiv postkasse.

1. Opret en variabel, der indeholder egenskaberne for den inaktive postkasse.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > I den forrige kommando skal du bruge værdien af egenskaben **DistinguishedName** eller **ExchangeGUID** til at identificere den inaktive postkasse. Disse egenskaber er entydige for hver postkasse i din organisation, hvorimod det er muligt, at en aktiv og en inaktiv postkasse kan have samme primære SMTP-adresse.

2. I dette eksempel bruges de egenskaber, der blev hentet i den forrige kommando, og den inaktive postkasse gendannes til en aktiv postkasse for brugeren Ann Beebe. Sørg for, at de værdier, der er angivet for parametrene  *Name*  og  *MicrosoftOnlineServicesID*  , er entydige i din organisation.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Den primære SMTP-adresse for den gendannede inaktive postkasse har samme værdi som den, der er angivet i parameteren  *MicrosoftOnlineServicesID*  .

Når du har gendannet en inaktiv postkasse, oprettes der også en ny brugerkonto. Du skal aktivere denne brugerkonto ved at tildele en licens. Hvis du vil tildele en licens i Microsoft 365 Administration, skal du se [Tilføj brugere og tildel licenser på samme tid](../admin/add-users/add-users.md).

## <a name="more-information"></a>Flere oplysninger

- **Hvad er hovedforskellen mellem gendannelse og gendannelse af en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, konverteres postkassen til en ny postkasse, indholdet og mappestrukturen for den inaktive postkasse bevares, og postkassen er knyttet til en ny brugerkonto. Når den er gendannet, findes den inaktive postkasse ikke længere, og eventuelle ændringer af indholdet i den nye postkasse påvirker det indhold, der oprindeligt var i venteposition i den inaktive postkasse. Hvis du derimod gendanner en inaktiv postkasse, kopieres indholdet blot til en anden postkasse. Den inaktive postkasse bevares og forbliver en inaktiv postkasse. Eventuelle ændringer af indholdet i målpostkassen påvirker ikke det oprindelige indhold, der opbevares i den inaktive postkasse. Der kan stadig søges i den inaktive postkasse ved hjælp af In-Place eDiscovery, indholdet kan gendannes til en anden postkasse, eller den kan gendannes eller slettes på et senere tidspunkt.

- **Hvad sker der, når du gendanner en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, sker følgende:

  - Den venteposition, der blev anvendt på en inaktiv postkasse, ændres eller fjernes på baggrund af den type venteposition, der blev anvendt på den inaktive postkasse, før den blev gendannet.
    
    - **Microsoft 365 opbevaringspolitik med bevarelseslås.** Hvis den inaktive postkasse er inkluderet i en opbevaringspolitik, der har [Bevarelseslås](retention-preservation-lock.md), tildeles den genoprettede postkasse til den samme opbevaringspolitik.
    
    - **Microsoft 365 opbevaringspolitik uden bevarelseslås.** Den inaktive postkasse fjernes fra Microsoft 365 opbevaringspolitik. Procesførelse er dog aktiveret for den gendannede postkasse for at forhindre sletning af postkasseindhold baseret på alle opbevaringspolitikker for hele organisationen, der sletter indhold, der er ældre end en bestemt alder. Du kan beholde procesførelsen eller fjerne den. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

    - **Procesførelse i venteposition.** Hvis Procesførelsesventeposition er aktiveret for den inaktive postkasse, fjernes den fra den gendannede postkasse.

    - **Bevarelse på stedet** In-Place Ventepositioner fjernes fra den gendannede postkasse. Det betyder, at den gendannede postkasse fjernes som en kildepostkasse fra alle In-Place venteposition eller In-Place eDiscovery-søgning.

  - Genoprettelsesperioden for et enkelt element (som er defineret af egenskaben **RetainDeletedItemsFor** postkasse) er angivet til 30 dage. Når der oprettes en ny postkasse i Exchange Online, angives denne opbevaringsperiode typisk til 14 dage. Hvis du angiver dette til den maksimale værdi på 30 dage, får du mere tid til at gendanne data, der er blevet slettet permanent (eller fjernet) fra den inaktive postkasse. Du kan også deaktivere genoprettelse af enkelt element eller angive genoprettelsesperioden for et enkelt element tilbage til standarden på 14 dage. Du kan få flere oplysninger under [Aktivér eller deaktiver genoprettelse af enkeltelement for en postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Opbevaringsbevaring er aktiveret, og varigheden af opbevaringsventetiden er angivet til 30 dage. Det betyder, at standardopbevaringspolitikken for Exchange og alle Exchange Microsoft 365 opbevaringspolitikker, der er tildelt den nye postkasse, ikke behandles i 30 dage. Dette giver den returnerende medarbejder eller den nye ejer af den gendannede inaktive postkasse tid til at administrere de gamle meddelelser. Ellers kan den Exchange eller Microsoft 365 opbevaringspolitik slette gamle postkasseelementer (eller flytte elementer til arkivpostkassen, hvis den er aktiveret), der er udløbet, på baggrund af de indstillinger, der er konfigureret for de Exchange eller Microsoft 365 opbevaringspolitikker. Efter 30 dage udløber opbevaringsventetiden, egenskaben **RetentionHoldEnabled** i postkassen er angivet til **Falsk**, og Assistent til administreret mappe starter behandlingen af de politikker, der er tildelt postkassen. Hvis du ikke har brug for denne ekstra tid, kan du blot fjerne opbevaringsventetiden. Du kan også øge varigheden af opbevaringen ved hjælp af kommandoen **Set-Mailbox -EndDateForRetentionHold** . Du kan få flere oplysninger under [Placer en postkasse i opbevaringsventeposition](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Sæt en venteposition på den gendannede postkasse, hvis du har brug for at bevare den oprindelige tilstand for den inaktive postkasse.** Hvis du vil forhindre den nye postkasseejer eller opbevaringspolitik i permanent at slette meddelelser fra den gendannede inaktive postkasse, kan du placere postkassen i procesventeposition. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](./create-a-litigation-hold.md).

- **Hvilket bruger-id kan du bruge, når du gendanner en inaktiv postkasse?** Når du gendanner en inaktiv postkasse, kan den værdi, du angiver for parameteren  *MicrosoftOnlineServicesID*  , være forskellig fra den oprindelige, der var knyttet til den inaktive postkasse. Du kan også bruge det oprindelige bruger-id. Men som tidligere angivet skal du sørge for, at de værdier, der bruges til  *Name*  og  *MicrosoftOnlineServicesID, er entydige*  i din organisation, når du gendanner den inaktive postkasse.

- **Hvad sker der, hvis opbevaringsperioden for postkassen for den inaktive postkasse ikke er udløbet?** Hvis en inaktiv postkasse blev slettet for mindre end 30 dage siden, kan du ikke bruge kommandoen **Ny postkasse -InactiveMailbox** til at gendanne den. Du skal gendanne den ved at gendanne den tilsvarende brugerkonto. Du kan få flere oplysninger under [Slet en bruger fra din organisation](../admin/add-users/delete-a-user.md).

- **Hvordan ved du, om opbevaringsperioden for blød slettede postkasser for en inaktiv postkasse er udløbet?** Kør følgende kommando:
    
  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```
    
    - Hvis der er en værdi for egenskaben **ExternalDirectoryObjectId** , er postkassens opbevaringsperiode udløbet, og du kan gendanne den inaktive postkasse ved at køre kommandoen **New-Mailbox -InactiveMailbox** .
    - Hvis der er en værdi for egenskaben **ExternalDirectoryObjectId** , er opbevaringsperioden for den slettede postkasse ikke udløbet, og du skal gendanne postkassen ved at [gendanne brugerkontoen](../admin/add-users/delete-a-user.md).

- **Overvej at aktivere arkivpostkassen, når du har gendannet en inaktiv postkasse.** Dette gør det muligt for den returnerende bruger eller nye medarbejder at flytte gamle meddelelser til arkivpostkassen. Og når opbevaringsventepositionen udløber, flytter den arkivpolitik, der er en del af standardpolitikken Exchange MRM-opbevaringspolitik, der er tildelt Exchange Online postkasser, elementer, der er to år eller ældre, til arkivpostkassen. Hvis du ikke aktiverer arkivpostkassen, forbliver elementer, der er ældre end to år, i brugerens primære postkasse. Du kan få flere oplysninger under [Aktivér arkivpostkasser](enable-archive-mailboxes.md).
