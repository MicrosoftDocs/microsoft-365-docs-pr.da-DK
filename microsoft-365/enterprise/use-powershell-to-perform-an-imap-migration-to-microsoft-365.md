---
title: Brug PowerShell til at udføre en IMAP-overførsel til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: Lær at bruge PowerShell til at udføre en IMAP-overførsel (Internet Mail Access Protocol) til Microsoft 365.
ms.openlocfilehash: 0c546782e81a399f092c8c7878b52c419adee799
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63590985"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en IMAP-overførsel til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Som en del af processen med at udrulle Microsoft 365 kan du vælge at overføre indholdet af brugerpostkasser fra en IMAP-mailtjeneste (Internet Mail Access Protocol) til en Microsoft 365. I denne artikel gennemgås opgaverne i forbindelse med en IMAP-mailoverførsel ved hjælp Exchange Online PowerShell.

> [!NOTE]
> Du kan også bruge Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange at</a> udføre en IMAP-overførsel. Se [Overfør dine IMAP-postkasser](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tidspunkt for at fuldføre denne opgave: 2-5 minutter til at oprette en overførselsbatch. Når overførselsbatchen startes, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan finde oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser Microsoft 365, under [Ydeevne for overførsel](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Hvis du vil se, hvilke tilladelser du skal bruge, skal du se posten "Overførsel" i en tabel [under emnet Modtagertilladelser](/exchange/recipients-permissions-exchange-2013-help) .

For at bruge Exchange Online PowerShell-cmdlet'er skal du logge på og importere cmdlet'er til din lokale Windows PowerShell session. Se [Forbind at Exchange Online bruge Remote PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få en vejledning.

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

Følgende begrænsninger gælder for IMAP-migrering:

- Det er kun elementer i en brugers indbakke eller andre mailmapper, der kan overføres. Du kan ikke overføre kontakter, kalenderelementer eller opgaver.

- Der kan maksimalt overføres 500.000 elementer fra en brugers postkasse.

- Den maksimale meddelelsesstørrelse, der kan overføres, er 35 MB.

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-an-imap-migration"></a>Trin 1: Forberede en IMAP-overførsel
<a name="BK_Step1"> </a>

- **Hvis du har et domæne for din IMAP-organisation, kan du tilføje det som et accepteret domæne for Microsoft 365 organisation.** Hvis du vil bruge det samme domæne, som du allerede ejer til dine Microsoft 365-postkasser, skal du først tilføje det som et accepteret domæne for at Microsoft 365. Når du har tilføjet den, kan du oprette dine brugere i Microsoft 365. Du kan finde flere oplysninger [i Bekræfte dit domæne](../admin/setup/add-domain.md).

- **Tilføj hver enkelt bruger Microsoft 365, så de har en postkasse.** Du kan finde en vejledning [underAdstrukser brugere Microsoft 365 til virksomheder](../admin/add-users/add-users.md).

- **Hent IMAP-serverens FQDN**. Du skal angive det fulde domænenavn (også kaldet det fulde computernavn) for den IMAP-server, som du vil overføre postkassedata fra, når du opretter et IMAP-overførselsslutpunkt. Brug en IMAP-klient eller kommandoen PING til at kontrollere, at du kan benytte FQDN til at kommunikere med IMAP-serveren via internettet.

- **Konfigurer firewallen for at tillade IMAP-forbindelser**. Du skal muligvis åbne porte i firewallen for den organisation, der hoster IMAP-serveren, så netværkstrafik, der stammer fra Microsoft-datacenteret under overførslen, har tilladelse til at gå ind i den organisation, der hoster IMAP-serveren. Du kan finde en liste over IP-adresser, der bruges af Microsoft-datacentre, [Exchange Online URL-adresser og IP-adresseintervaller](./urls-and-ip-address-ranges.md).

- **Tildele administratorkontoens tilladelser til at få adgang til postkasser i IMAP-organisationen**. Hvis du bruger administratorlegitimationsoplysninger i CSV-filen, skal den konto, du bruger, have de nødvendige tilladelser til at oprette adgang til postkasser i det lokale miljø. De tilladelser, der kræves for at få adgang til brugerpostkasser, bestemmes af den bestemte IMAP-server.

- **For at bruge Exchange Online PowerShell-cmdlet'er** skal du logge på og importere cmdlet'er til din lokale Windows PowerShell session. Se [Forbind at Exchange Online bruge Remote PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få en vejledning.

    Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

- **Kontrollér, at du kan oprette forbindelse til IMAP-serveren**. Kør følgende kommando i Exchange Online PowerShell for at teste forbindelsesindstillingerne til din IMAP-server.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    For værdien af **portparameteren** er det typisk at bruge 143 til ikke-krypterede eller TLS-forbindelser (Transport Layer Security) og bruge 993 til SSL-forbindelser.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Trin 2: Oprette en CSV-fil til en IMAP-overførselsbatch

Identificer den gruppe af brugere, hvis postkasser du vil overføre, i en IMAP-overførselsbatch. Hver række i CSV-filen indeholder oplysninger, der er nødvendige for at oprette forbindelse til en postkasse i IMAP-meddelelsessystemet.

Følgende attributter kræves til hver bruger:

- **EmailAddress** angiver bruger-id'et for brugerens Microsoft 365 postkasse.

- **UserName angiver** logonnavnet til den konto, der skal bruges til at få adgang til postkassen på IMAP-serveren.

- **Adgangskoden** angiver adgangskoden til kontoen i **kolonnen Brugernavn** .

Her er et eksempel på det korrekte format for CSV-filen. I dette eksempel overføres tre postkasser:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

For attributten **Brugernavn** kan du ud over brugernavnet bruge legitimationsoplysningerne fra en konto, der har fået tildelt de nødvendige tilladelser til at få adgang til postkasser på IMAP-serveren, følgende er nogle af de specifikke formater, der bruges til nogle af IMAP-serverne:

 **Microsoft Exchange:**

Hvis du overfører mail fra IMAP-implementeringen til Microsoft Exchange, skal du bruge formatet **Domæne/Admin_UserName/User_UserName** for **attributten UserName** i CSV-filen. Lad os antage, at du overfører mail fra Exchange for Terry Adams, Ann Beebe og Paul Cannon. Du har en mailadministratorkonto, hvor brugernavnet er **mailadmin**, og adgangskoden er **Pssw0rd\@**. Sådan ville CSV-filen se ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

For IMAP-servere, der understøtter SASL (Simple Authentication and Security Layer), f.eks. en Dovecot IMAP-server, skal du bruge formatet **User_UserName*Admin_UserName**, hvor stjernen ( * ) er et skilletegn, der kan konfigureres. Lad os sige, at du overfører de samme brugeres mail fra en Dovecot IMAP-server ved hjælp af administratorens legitimationsoplysninger **mailadmin** og **Pssw0rd\@**. Sådan ville CSV-filen se ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

Hvis du overfører mail fra Mirapoint Message Server, skal du bruge formatet **#user\@ domain#Admin_UserName#** som administratorens legitimationsoplysninger. Hvis du vil overføre mail fra Mirapoint ved hjælp af administratorens legitimationsoplysninger **mailadmin** og **Pssw0rd\@**, vil din CSV-fil se sådan ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Nogle kildemailsystemer, f.eks Courier IMAP, understøtter ikke brugen af postkasseadministratorens legitimationsoplysninger til at overføre postkasser til Microsoft 365. I stedet kan du konfigurere dit kildemailsystem til at bruge virtuelle delte mapper. Ved hjælp af virtuelle delte mapper kan du bruge postkasseadministratorens legitimationsoplysninger til at få adgang til brugerpostkasser i kildemailsystemet. Du kan finde flere oplysninger om, hvordan du konfigurerer virtuelle delte mapper for Courier IMAP [, under Delte mapper](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Hvis du vil overføre postkasser, efter at du har konfigureret virtuelle delte mapper på dit kildemailsystem, er du nødt til at medtage den valgfri attribut **UserRoot** i overførselsfilen. Denne attribut angiver placeringen af hver enkelt brugers postkasse i strukturen for den virtuelle delte mappe på kildemailsystemet. Stien til Terrys postkasse er f.eks. /users/terry.adams.

Her er et eksempel på en CSV-fil, der indeholder **attributten UserRoot** :

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Trin 3: Oprette et IMAP-overførselsslutpunkt

For at overføre mails korrekt skal Microsoft 365 oprette forbindelse til og kommunikere med kildemailsystemet. For at gøre dette Microsoft 365 et overførselsslutpunkt. Overførselsslutpunktet definerer også antallet af postkasser, der skal overføres samtidigt, samt antallet af postkasser, der skal synkroniseres samtidigt under trinvis synkronisering, hvilket sker én gang i døgnet. Hvis du vil oprette et overførselsslutpunkt til IMAP-overførsel, skal [du først oprette forbindelse Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Du kan se en komplet liste over overførselskommandoer [under Flyt- og overførsels-cmdlet'er](/powershell/exchange/).

For at oprette det IMAP-overførselsslutpunkt, der kaldes "IMAPEndpoint" Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Du kan også tilføje parametre for at angive samtidige migreringer, samtidige trinvise migreringer og den port, der skal bruges. Følgende Exchange Online PowerShell-kommando opretter et IMAP-overførselsslutpunkt ved navn "IMAPEndpoint", der understøtter 50 samtidige migreringer og op til 25 samtidige trinvise synkroniseringer. Det konfigurerer også slutpunktet til at bruge port 143 til TLS-kryptering.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Du kan finde flere oplysninger **om New-MigrationEndpoint-cmdlet'en** [iNew-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Kør følgende kommando i Exchange Online PowerShell for at vise oplysninger om "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Trin 4: Oprette og starte en IMAP-overførselsbatch

Du kan bruge [New-MigrationBatch-cmdlet'en](/powershell/module/exchange/new-migrationbatch) til at oprette en overførselsbatch til en IMAP-overførsel. Du kan oprette en overførselsbatch og starte den automatisk ved at medtage _autostartparameteren_ . Alternativt kan du oprette overførselsbatchen og derefter starte den bagefter ved hjælp af [cmdlet'enStart-MigrationBatch](/powershell/module/exchange/start-migrationbatch) .

Følgende Exchange Online PowerShell-kommando starter automatisk overførselsbatchen ved navn "IMAPBatch1" ved hjælp af IMAP-slutpunktet kaldet "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Kør [cmdlet'en Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) for at vise oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Du kan også kontrollere, at batchen er startet, ved at køre følgende kommando:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Trin 5: Omrute dine mails til Microsoft 365

Mailsystemer bruger en DNS-post, der kaldes en MX-post, til at finde ud af, hvor mails skal leveres. Under mailoverførselsprocessen pegede din MX-post på dit kildemailsystem. Nu hvor overførslen af mail til Microsoft 365 er fuldført, er det tid til at få din MX-post til at pege Microsoft 365. Dette er med til at sikre, at mail leveres til Microsoft 365 postkasser. Ved at flytte MX-posten kan du også deaktivere dit gamle mailsystem, når du er klar.

For mange DNS-udbydere er der specifikke instruktioner til at ændre din MX-post. Hvis din DNS-udbyder ikke er inkluderet, eller hvis du vil have en fornemmelse af de generelle retningslinjer, får du også en generel vejledning til [MX-poster](https://go.microsoft.com/fwlink/?LinkId=397449) .

Det kan tage op til 72 timer, før dine kunders og partneres mailsystemer genkender den ændrede MX-post. Vent mindst 72 timer, før du går videre til den næste opgave: Trin 6: Slet IMAP-overførselsbatch.

### <a name="step-6-delete-imap-migration-batch"></a>Trin 6: Slet IMAP-overførselsbatch

Når du har ændret MX-posten og bekræfter, at alle mails dirigeres til Microsoft 365-postkasser, skal du give brugerne besked om, at deres mail sendes Microsoft 365. Derefter kan du slette IMAP-overførselsbatchen. Kontrollér følgende, før du sletter overførselsbatchen.

- Alle brugere bruger Microsoft 365 postkasser. Når batchen slettes, kopieres de mails, der sendes til postkasser i det lokale Exchange Server, ikke til de tilsvarende Microsoft 365 postkasser.

- Microsoft 365 postkasser blev synkroniseret mindst én gang, efter at mails begyndte at blive sendt direkte til dem. For at gøre dette skal du sørge for, at værdien i feltet Seneste synkroniseringstid for overførselsbatchen er af nyere dato end tidspunktet, hvor mail begyndte at blive dirigeret direkte til Microsoft 365 postkasser.

Hvis du vil slette overførselsbatchen "IMAPBatch1" fra Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Du kan finde flere oplysninger **om cmdlet'en Remove-MigrationBatch** [underRemove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Bekræft, at det lykkedes

Kør følgende kommando i Exchange Online PowerShell for at vise oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

Kommandoen returnerer enten overførselsbatchen med statussen **Fjerner, eller** den returnerer en fejl om, at overførselsbatchen ikke blev fundet, og bekræfter, at batchen er blevet slettet.

Du kan finde flere oplysninger **om Get-MigrationBatch-cmdlet'en** [underGet-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Se også

[Fejlfinding af IMAP-overførsel](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)