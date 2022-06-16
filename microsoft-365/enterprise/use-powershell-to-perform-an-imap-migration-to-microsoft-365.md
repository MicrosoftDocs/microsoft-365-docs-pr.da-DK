---
title: Brug PowerShell til at udføre en IMAP-overførsel for at Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du bruger PowerShell til at udføre en IMAP-overførsel (Internet Mail Access Protocol) til Microsoft 365.
ms.openlocfilehash: e3375af79ce4332ebf8f44e88181d7d8dc0e430f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128783"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Brug PowerShell til at udføre en IMAP-overførsel for at Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Som en del af processen med at installere Microsoft 365 kan du vælge at overføre indholdet af brugerpostkasser fra en IMAP-mailtjeneste (Internet Mail Access Protocol) til Microsoft 365. I denne artikel gennemgås opgaverne for en IMAP-migrering via mail ved hjælp af Exchange Online PowerShell.

> [!NOTE]
> Du kan også bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at udføre en IMAP-overførsel. Se [Overfør dine IMAP-postkasser](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Anslået tid til at fuldføre denne opgave: 2-5 minutter for at oprette et overførselsbatch. Når overførselsbatchen er startet, varierer varigheden af overførslen afhængigt af antallet af postkasser i batchen, størrelsen på hver postkasse og din tilgængelige netværkskapacitet. Du kan få oplysninger om andre faktorer, der påvirker, hvor lang tid det tager at overføre postkasser til Microsoft 365, under [Overførselsydeevne](/Exchange/mailbox-migration/office-365-migration-best-practices).

Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Overførsel" i en tabel i emnet [Modtageres tilladelser](/exchange/recipients-permissions-exchange-2013-help) .

Hvis du vil bruge Exchange Online PowerShell-cmdlet'er, skal du logge på og importere cmdlet'erne i din lokale Windows PowerShell session. Se [Forbind til Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få vejledning.

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

Følgende begrænsninger gælder for IMAP-overførsler:

- Det er kun elementer i en brugers indbakke eller andre postmapper, der kan overføres. Du kan ikke overføre kontakter, kalenderelementer eller opgaver.

- Der kan maksimalt overføres 500.000 elementer fra en brugers postkasse.

- Den maksimale meddelelsesstørrelse, der kan overføres, er 35 MB.

## <a name="migration-steps"></a>Overførselstrin

### <a name="step-1-prepare-for-an-imap-migration"></a>Trin 1: Forbered en IMAP-migrering
<a name="BK_Step1"> </a>

- **Hvis du har et domæne til din IMAP-organisation, skal du tilføje det som et accepteret domæne for din Microsoft 365 organisation.** Hvis du vil bruge det samme domæne, som du allerede ejer til dine Microsoft 365 postkasser, skal du først tilføje det som et accepteret domæne for at Microsoft 365. Når du har tilføjet den, kan du oprette dine brugere i Microsoft 365. Du kan finde flere oplysninger under[Kontrollér dit domæne](../admin/setup/add-domain.md).

- **Føj hver bruger til Microsoft 365, så de har en postkasse.** Du kan finde instruktioner under[Føj brugere til Microsoft 365 til virksomheder](../admin/add-users/add-users.md).

- **Hent IMAP-serverens FQDN**. Du skal angive det fuldt kvalificerede domænenavn (FQDN) (også kaldet det fulde computernavn) for den IMAP-server, du vil overføre postkassedata fra, når du opretter et IMAP-overførselsslutpunkt. Brug en IMAP-klient eller kommandoen PING til at kontrollere, at du kan benytte FQDN til at kommunikere med IMAP-serveren via internettet.

- **Konfigurer firewallen for at tillade IMAP-forbindelser**. Du skal muligvis åbne porte i firewallen i den organisation, der er vært for IMAP-serveren, så netværkstrafik, der stammer fra Microsoft-datacenteret under migreringen, har tilladelse til at komme ind i den organisation, der er vært for IMAP-serveren. Du kan finde en liste over de IP-adresser, der bruges af Microsoft-datacentre, [under Exchange Online URL-adresser og IP-adresseområder](./urls-and-ip-address-ranges.md).

- **Tildel administratorkontotilladelserne for at få adgang til postkasser i din IMAP-organisation**. Hvis du bruger administratorlegitimationsoplysninger i CSV-filen, skal den konto, du bruger, have de nødvendige tilladelser til at oprette adgang til postkasser i det lokale miljø. De tilladelser, der kræves for at få adgang til brugerpostkasser, bestemmes af den pågældende IMAP-server.

- **Hvis du vil bruge Exchange Online PowerShell-cmdlet'er**, skal du logge på og importere cmdlet'erne i din lokale Windows PowerShell session. Se [Forbind til Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få vejledning.

    Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

- **Kontrollér, at du kan oprette forbindelse til IMAP-serveren**. Kør følgende kommando i Exchange Online PowerShell for at teste forbindelsesindstillingerne til din IMAP-server.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    For værdien af **portparameteren** er det typisk at bruge 143 til ukrypterede forbindelser eller TLS-forbindelser (Transport Layer Security) og at bruge 993 til SSL-forbindelser.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Trin 2: Opret en CSV-fil til et IMAP-overførselsbatch

Identificer den gruppe af brugere, hvis postkasser du vil overføre i et IMAP-overførselsbatch. Hver række i CSV-filen indeholder oplysninger, der er nødvendige for at oprette forbindelse til en postkasse i IMAP-meddelelsessystemet.

Følgende attributter kræves til hver bruger:

- **EmailAddress** angiver bruger-id'et for brugerens Microsoft 365 postkasse.

- **UserName** angiver logonnavnet på den konto, der skal bruges til at få adgang til postkassen på IMAP-serveren.

- **Adgangskoden** angiver adgangskoden til kontoen i kolonnen **UserName** .

Her er et eksempel på det korrekte format for CSV-filen. I dette eksempel overføres tre postkasser:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

For attributten **UserName** kan du ud over brugernavnet bruge legitimationsoplysningerne for en konto, der har fået tildelt de nødvendige tilladelser til at få adgang til postkasser på IMAP-serveren, og følgende er nogle af de specifikke formater, der bruges til nogle af IMAP-serverne:

 **Microsoft Exchange:**

Hvis du overfører mail fra IMAP-implementeringen til Microsoft Exchange, skal du bruge formatet **Domæne/Admin_UserName/User_UserName** for attributten **UserName** i CSV-filen. Lad os sige, at du overfører mail fra Exchange for Terry Adams, Ann Beebe og Paul Cannon. Du har en mailadministratorkonto, hvor brugernavnet er **mailadmin** , og adgangskoden er **P\@ssw0rd**. Sådan vil CSV-filen se ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

Til IMAP-servere, der understøtter SASL (Simple Authentication and Security Layer), f.eks. en Dovecot IMAP-server, skal du bruge formatet **User_UserName*Admin_UserName**, hvor stjernen ( * ) er et konfigurerbart separatortegn. Lad os sige, at du overfører de samme brugeres mail fra en Dovecot IMAP-server ved hjælp af administratorlegitimationsoplysninger **mailadmin** og **P\@ssw0rd**. Sådan vil CSV-filen se ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

Hvis du overfører mail fra Mirapoint Message Server, skal du bruge formatet **#user\@domain#Admin_UserName#** som administratorlegitimationsoplysninger. Hvis du vil overføre mail fra Mirapoint ved hjælp af administratorlegitimationsoplysninger **mailadmin** og **P\@ssw0rd**, vil din CSV-fil se sådan ud:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Nogle kildemailsystemer, f.eks. Courier IMAP, understøtter ikke brug af legitimationsoplysninger som postkasseadministrator til at overføre postkasser til Microsoft 365. Du kan i stedet konfigurere dit kildemailsystem til at bruge virtuelle delte mapper. Ved hjælp af virtuelle delte mapper kan du bruge legitimationsoplysningerne for postkasseadministratoren til at få adgang til brugerpostkasser i kildemailsystemet. Du kan få flere oplysninger om, hvordan du konfigurerer virtuelle delte mapper til Courier IMAP, under [Delte mapper](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Hvis du vil overføre postkasser, når du har konfigureret virtuelle delte mapper i kildemailsystemet, skal du medtage den valgfrie attribut **UserRoot** i overførselsfilen. Denne attribut angiver placeringen af hver brugers postkasse i den virtuelle delte mappestruktur i kildemailsystemet. Stien til Terrys postkasse er f.eks. /users/terry.adams.

Her er et eksempel på en CSV-fil, der indeholder attributten **UserRoot** :

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Trin 3: Opret et IMAP-overførselsslutpunkt

Hvis du vil overføre mails, skal Microsoft 365 oprette forbindelse til og kommunikere med kildemailsystemet. Det gør Microsoft 365 ved at bruge et overførselsslutpunkt. Overførselsslutpunktet definerer også antallet af postkasser, der skal overføres samtidig, og antallet af postkasser, der skal synkroniseres samtidig under trinvis synkronisering, hvilket sker én gang hver 24. time. Hvis du vil oprette et slutpunkt for overførsel af IMAP, skal du først [oprette forbindelse til Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Du kan se en komplet liste over overførselskommandoer under [Flyt og migrerings-cmdlet'er](/powershell/exchange/).

Hvis du vil oprette IMAP-overførselsslutpunktet "IMAPEndpoint" i Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Du kan også tilføje parametre for at angive samtidige migreringer, samtidige trinvise migreringer og den port, der skal bruges. Følgende Exchange Online PowerShell-kommando opretter et IMAP-overførselsslutpunkt med navnet "IMAPEndpoint", der understøtter 50 samtidige migreringer og op til 25 samtidige trinvise synkroniseringer. Det konfigurerer også slutpunktet til at bruge port 143 til TLS-kryptering.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Du kan finde flere oplysninger om **New-MigrationEndpoint-cmdlet'en** under [New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om "IMAPEndpoint":

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Trin 4: Opret og start en IMAP-overførselsbatch

Du kan bruge Cmdlet'en [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) til at oprette et overførselsbatch til en IMAP-overførsel. Du kan oprette et overførselsbatch og starte det automatisk ved at inkludere parameteren _AutoStart_ . Du kan også oprette overførselsbatchen og derefter starte den bagefter ved hjælp af cmdlet'en[Start-MigrationBatch](/powershell/module/exchange/start-migrationbatch) .

Følgende Exchange Online PowerShell-kommando starter automatisk overførselsbatchen med navnet "IMAPBatch1" ved hjælp af IMAP-slutpunktet kaldet "IMAPEndpoint":

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Kør [Get-MigrationBatch-cmdlet'en](/powershell/module/exchange/get-migrationbatch) for at få vist oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Du kan også kontrollere, at batchen er startet, ved at køre følgende kommando:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Trin 5: Distribuer din mail til Microsoft 365

Mailsystemer bruger en DNS-post kaldet en MX-post til at finde ud af, hvor de skal levere mails. Under mailoverførselsprocessen pegede din MX-post på dit kildemailsystem. Nu, hvor mailoverførslen til Microsoft 365 er fuldført, er det tid til at pege din MX-post på Microsoft 365. Dette hjælper med at sikre, at mail leveres til dine Microsoft 365 postkasser. Når du flytter MX-posten, kan du også slå dit gamle mailsystem fra, når du er klar.

For mange DNS-udbydere er der specifikke instruktioner til at ændre din MX-post. Hvis din DNS-udbyder ikke er inkluderet, eller hvis du vil have en fornemmelse af de generelle retninger, leveres der også [generelle MX-postinstruktioner](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide#add-an-mx-record-for-email-outlook-exchange-online) .

Det kan tage op til 72 timer, før dine kunders og partneres mailsystemer genkender den ændrede MX-post. Vent mindst 72 timer, før du fortsætter til næste opgave: Trin 6: Slet IMAP-overførselsbatch.

### <a name="step-6-delete-imap-migration-batch"></a>Trin 6: Slet IMAP-overførselsbatch

Når du har ændret MX-posten og bekræftet, at alle mails distribueres til Microsoft 365 postkasser, skal du give brugerne besked om, at deres mail vil Microsoft 365. Derefter kan du slette IMAP-overførselsbatchen. Kontrollér følgende, før du sletter overførselsbatchen.

- Alle brugere bruger Microsoft 365 postkasser. Når batchen er slettet, kopieres mails, der sendes til postkasser i det lokale miljø, Exchange Server ikke til de tilsvarende Microsoft 365 postkasser.

- Microsoft 365 postkasser blev synkroniseret mindst én gang, efter mailen begyndte at blive sendt direkte til dem. Det gør du ved at sikre, at værdien i feltet Senest synkroniseret tid for overførselsbatchen er nyere, end da mailen begyndte at blive distribueret direkte til Microsoft 365 postkasser.

Hvis du vil slette overførselsbatchen "IMAPBatch1" fra Exchange Online PowerShell, skal du køre følgende kommando:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Du kan få flere oplysninger om cmdlet'en **Remove-MigrationBatch** under [Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Kontrollér, at det virkede

Kør følgende kommando i Exchange Online PowerShell for at få vist oplysninger om "IMAPBatch1":

```powershell
Get-MigrationBatch IMAPBatch1"
```

Kommandoen returnerer enten overførselsbatchen med statussen **Fjerner**, eller den returnerer en fejl, der angiver, at overførselsbatchen ikke blev fundet, og kontrollerer, at batchen er slettet.

Du kan få flere oplysninger om **Get-MigrationBatch-cmdlet'en** under [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Se også

[Fejlfindingsværktøj til IMAP-overførsel](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)
