---
title: Overførsel af postkasse på tværs af lejere
description: Sådan flytter du postkasser mellem Microsoft 365 eller Office 365 lejere.
ms.author: kvice
author: kelleyvice-msft
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 09/21/2020
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: e9ec5c27f5dabfa2df0f12ca6daecfcef860547c
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499369"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Overførsel af postkasse på tværs af lejere (forhåndsvisning)

Under fusioner eller frasalg har du ofte brug for muligheden for at flytte din brugers postkasse Exchange Online en ny lejer. Overførsel af postkasser på tværs af lejere giver lejeradministratorer mulighed for at bruge velkendte grænseflader som f.eks. Remote PowerShell og MRS til at overgå brugere til deres nye organisation.

Administratorer kan bruge den New-MigrationBatch-cmdlet, der er tilgængelig via administrationsrollen Flyt postkasser, til at udføre flytninger på tværs af lejere.

Brugere, der overfører, skal være til stede i systemet til overførsel af Exchange Online som MailUsers, der er markeret med bestemte attributter for at aktivere flytninger på tværs af lejere. Systemet kan ikke flyttes for brugere, der ikke er korrekt konfigureret i mållejeren.

Når flytningen er fuldført, konverteres brugerpostkassen til en MailUser, og targetAddress (vist som ExternalEmailAddress i Exchange) er stemplet med routingadressen til destinationslejeren. Denne proces efterlader den ældre MailUser i kildelejeren og giver mulighed for sameksistens og videresendelse af mail. Når forretningsprocesser tillader det, kan kildelejeren fjerne mailbrugeren fra kilden eller konvertere dem til en mailkontakt.

Postkasseoverførsel på Exchange lejere i hybrid eller skyen eller enhver kombination af de to.

Denne artikel beskriver processen for flytning af postkasser på tværs af lejere og giver vejledning til, hvordan du forbereder kilde- og mållejere til Exchange Online flytte postkasseindhold.

   > [!NOTE]
   > Vi har for nylig opdateret vores konfigurationstrin til at aktivere overførsel af postkasser på tværs af lejere til ikke længere at kræve Azure Key Vault! Hvis dette er første gang, du onboarder til dette eksempel, kræves der ingen handling, og du kan gå videre og følge trinnene i dette dokument. Hvis du er begyndt at konfigurere dine lejere ved hjælp af den forrige AKV-metode, anbefaler vi, at du stopper eller fjerner denne konfiguration for at begynde at bruge denne nye metode. Hvis du har postkasseoverflytninger i gang med den forrige AKV-metode, skal du vente, indtil dine eksisterende migrering er fuldført og følge trinnene nedenfor for at aktivere den nye forenklede metode. De Key Vault Azure-konfigurationstrin arkiveres, men kan **[findes her](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)** som reference.

## <a name="preparing-source-and-target-tenants"></a>Forberedelse af kilde- og mållejere

### <a name="prerequisites-for-source-and-target-tenants"></a>Forudsætninger for kilde- og mållejere

Før du starter, skal du sikre dig, at du har de nødvendige tilladelser til at konfigurere programmet Flyt postkasse i Azure, EXO-overførselsslutpunktet og EXO-organisationsrelationen.

Desuden kræves der mindst én mailaktiveret sikkerhedsgruppe i kildelejeren. Disse grupper bruges til at begrænse listen over postkasser, som kan flyttes fra kildelejeren (eller nogle gange kaldet ressourcelejeren) til mållejeren. Dette giver kildelejeradministratoren mulighed for at begrænse eller begrænse det specifikke sæt postkasser, der skal flyttes, hvilket forhindrer utilsigtede brugere i at blive overført. Indlejrede grupper understøttes ikke.

Du skal også kommunikere med dit pålidelige partnerfirma (med hvem du skal flytte postkasser) for at få deres Microsoft 365-lejer-id. Dette lejer-id bruges i feltet Organization Relationship DomainName.

For at få lejer-id'et for et abonnement skal du logge [på Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) og gå til [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Klik på kopiikonet for egenskaben Lejer-id for at kopiere det til Udklipsholder.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>Konfigurationstrin til at aktivere dine lejere til overførsel af postkasser på tværs af lejere

   > [!NOTE]
   > Du skal konfigurere destinationen (destinationen) først. For at fuldføre disse trin behøver du ikke at have eller kender lejeradministratorens legitimationsoplysninger for både kilde- og mållejeren. Trin kan udføres enkeltvis for hver lejer af forskellige administratorer.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>Forbered mållejeren (destinationen) ved at oprette overførselsprogrammet og hemmeligheden

1. Log på Azure AD-portalen (<https://portal.azure.com>) med administratorlegitimationsoplysninger for mållejeren

   ![Azure-logon](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. Klik på Vis under Azure Active Directory.

   ![Azure Active Directory knap](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. I venstre navigationslinje skal du vælge Appregistreringer.

4. Vælg Ny registrering

   ![Nyt program](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. På siden Registrer et program under Understøttede kontotyper skal du vælge Konti i en organisationsmappe (Enhver Azure AD-mappe – Multitenant). Derefter skal du under Redirect URI (valgfrit) vælge Web og angive <https://office.com>. Endelig skal du vælge Registrer.

   ![Programregistrering](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. I øverste højre hjørne på siden får du vist en pop op-meddelelse om, at appen blev oprettet.

7. Gå tilbage til Hjem, Azure Active Directory og klik på Appregistreringer.

8. Find den app, du har oprettet, under Ejet programmer, og klik på den.

9. Under ^Essentials skal du kopiere program-id'et (klienten), da du skal bruge det senere for at oprette en URL-adresse til mållejeren.

10. Nu skal du i venstre navigationslinje klikke på API-tilladelser for at få vist tilladelser, der er tildelt din app.

11. Som standard Bruger. Læsetilladelser tildeles den app, du har oprettet, men vi kræver dem ikke til postkasseoverførsel, du kan fjerne den pågældende tilladelse.

    ![Programtilladelser](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. Nu skal vi tilføje tilladelse til overførsel af postkasse, vælge Tilføj en tilladelse

13. I vinduet Request API-tilladelser skal du vælge API'er, som min organisation bruger, søge Office 365 Exchange Online og vælge den.

    ![Vælg API](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. Vælg derefter Programtilladelser

15. Derefter skal du under Vælg tilladelser udvide Postkasse og markere Mailbox.Migration og Tilføj tilladelser nederst på skærmen.

    ![Indstil API](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. Vælg nu Certifikater & hemmeligheder i venstre navigationslinje for dit program.

17. Under Klienthemmeligheder skal du vælge ny klienthemmelighed.

    ![Klienthemmeligheder](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. I vinduet Tilføj en klienthemmelighed skal du angive en beskrivelse og konfigurere dine ønskede udløbsindstillinger.

      > [!NOTE]
      > Dette er den adgangskode, der skal bruges, når du opretter overførselsslutpunktet. Det er meget vigtigt, at du kopierer denne adgangskode til udklipsholderen og kopierer denne adgangskode for at sikre/hemmelig placering for adgangskoden. Dette er det eneste tidspunkt, hvor du kan se denne adgangskode! Hvis du på en eller anden måde mister den eller har brug for at nulstille den, kan du logge på vores Azure Portal igen, gå til Appregistreringer, finde din overførselsapp, vælge Hemmeligheder &-certifikater og oprette en ny hemmelighed for din app.

19. Nu hvor du har oprettet overførselsprogrammet og er hemmelig, skal du give dit samtykke til programmet. For at give samtykke til programmet skal du gå tilbage til Azure Active Directory-landingssiden, klikke på Enterprise-programmer i venstre navigationsrude, finde den overførselsapp, du har oprettet, markere den og vælge Tilladelser i venstre navigationsrude.

20. Klik på knappen Giv administratorsamtykke til [din lejer].

21. Et nyt browservindue åbnes, og vælg Acceptér.

22. Du kan gå tilbage til portalvinduet og vælge Opdater for at bekræfte din accept.

23. Formel for url-adressen, der skal sendes til din partner, der er tillid til (kildelejeradministrator), så de også kan acceptere programmet for at aktivere postkasseoverførsel. Her er et eksempel på URL-adressen, så du skal bruge program-id'et for den app, du har oprettet:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet.
    >
    > Du skal erstatte sourcetenant.onmicrosoft.com i eksemplet ovenfor med dine kildelejere med det onmicrosoft.com navn.
    >
    > Du skal også erstatte [application_id_of_the_app_you_just_created] med program-id'et for den postkasseoverførselsapp, du lige har oprettet.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>Forbered mållejeren ved at oprette Exchange Online overførselsslutpunkt og organisationsrelation

1. Opret en Remote PowerShell-forbindelse til den Exchange Online lejer.

2. Opret et nyt overførselsslutpunkt for postkasseflytninger på tværs af lejere

   > [!NOTE]
   > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet, og den adgangskode (den hemmelig), du konfigurerede under denne proces. Afhængigt af den Microsoft 365 forekomst af skyen, du bruger, kan dit slutpunkt være anderledes. Se siden med [Microsoft 365](/microsoft-365/enterprise/microsoft-365-endpoints) slutpunkter, og vælg den korrekte forekomst for din lejer, og gennemgå adressen Exchange Online Optimer påkrævet og erstat efter behov.

   ```powershell
   
   # Enable customization if tenant is dehydrated
     $dehydrated=Get-OrganizationConfig | fl isdehydrated
     if ($dehydrated -eq $true) {Enable-OrganizationCustomization}
     
   $AppId = "[guid copied from the migrations app]"

   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)

   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. Opret ny eller rediger dit eksisterende organisationsrelationsobjekt til din kildelejer.

   ```powershell
   $sourceTenantId="[tenant id of your trusted partner, where the source mailboxes are]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of the new organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound -DomainNames $sourceTenantId
   }
   ```

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>Forbered kildelejeren (nuværende postkasseplacering) ved at acceptere overførselsprogrammet og konfigurere organisationsrelationen

1. Fra en browser skal du gå til linket til den URL-adresse, du har stillet til rådighed af din partner, som du har tillid til, for at give dit samtykke til postkasseoverførselsprogrammet. URL-adressen ser sådan ud:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet.
   > Du skal erstatte sourcetenant.onmicrosoft.com i eksemplet ovenfor med dine kildelejere med det onmicrosoft.com navn.
   > Du skal også erstatte [application_id_of_the_app_you_just_created] med program-id'et for den postkasseoverførselsapp, du lige har oprettet.

2. Acceptér programmet, når pop op-vindue vises. Du kan også logge på Azure Active Directory-portalen og finde programmet under Enterprise-programmer.

3. Opret ny eller rediger dit eksisterende organisationsrelationsobjekt til mållejeren (destinationen) fra Exchange Online Remote PowerShell-vindue.

   ```powershell
   $targetTenantId="[tenant id of your trusted partner, where the mailboxes are being moved to]"
   $appId="[application id of the mailbox migration app you consented to]"
   $scope="[name of the mail enabled security group that contains the list of users who are allowed to migrate]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $targetTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of your organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -DomainNames $targetTenantId -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   ```
   
> [!NOTE]
> Det lejer-id, du angiver som $sourceTenantId og $targetTenantId er GUID'et og ikke lejerdomænenavnet. Hvis du vil se et eksempel på et lejer-id og oplysninger om at finde dit lejer-id, skal du [se Finde Microsoft 365 lejer-id](/onedrive/find-your-office-365-tenant-id).
   
### <a name="how-do-i-know-this-worked"></a>Hvordan gør jeg du, at det lykkedes?

Du kan bekræfte overførselskonfigurationen for postkasser på tværs af lejere ved at køre [Test-MigrationServerAvailability](/powershell/module/exchange/Test-MigrationServerAvailability) cmdlet'en mod det slutpunkt for overførsel på tværs af lejere, som du har oprettet på din mållejer.

   > [!NOTE]
   >
   > - Mållejer:
   > 
   > Test-MigrationServerAvailability -Slutpunkt "[navnet på dit overførselsslutpunkt på tværs af lejer]"
   >
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
   >
   > - Kildelejer:
   > 
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability 

### <a name="move-mailboxes-back-to-the-original-source"></a>Flytte postkasser tilbage til den oprindelige kilde

Hvis en postkasse skal flyttes tilbage til den oprindelige kildelejer, skal det samme sæt trin og scripts køres i både den nye kilde og den nye mållejer. Det eksisterende Organisationsrelation-objekt opdateres eller tilføjes, ikke genoprettes

## <a name="prepare-target-user-objects-for-migration"></a>Forberede destinationsbrugerobjekter til overførsel

Brugere, der overfører, skal være i mållejeren og Exchange Online-systemet (som MailUsers) markeret med bestemte attributter for at aktivere flytning på tværs af lejere. Systemet kan ikke flyttes for brugere, der ikke er korrekt konfigureret i mållejeren. I det følgende afsnit finder du detaljerede oplysninger om objektkravene til MailUser for mållejeren.

### <a name="prerequisites-for-target-user-objects"></a>Forudsætninger for destinationsbrugerobjekter

Sørg for, at følgende objekter og attributter er angivet i destinationsorganisationen.

1. For alle postkasser, der flyttes fra en kildeorganisation, skal du klargøre et MailUser-objekt i organisationen Destination:

   - Target MailUser skal have disse attributter fra kildepostkassen eller tildelt med det nye Bruger-objekt:
      - ExchangeGUID (direkte flow fra kilde til destination): Postkasse-GUID'et skal svare til hinanden. Flytteprocessen fortsætter ikke, hvis dette ikke findes på destinationsobjektet.
      - ArchiveGUID (direkte flow fra kilde til destination): Det arkiverede GUID skal matche. Flytteprocessen fortsætter ikke, hvis dette ikke findes på destinationsobjektet. Dette er kun påkrævet, hvis kildepostkassen er arkiv aktiveret.
      - LegacyExchangeDN (flow som proxyAddress, "x500:\<LegacyExchangeDN>"): LegacyExchangeDN skal være til stede på målmailUser som x500: proxyAddress. Desuden skal du også kopiere alle x500-adresser fra kildepostkassen til målmailbrugeren. Flytningsprocesserne fortsætter ikke, hvis disse ikke findes på destinationsobjektet.
      - UserPrincipalName: UPN justeres efter brugerens nye identitet eller målfirma (f.eks user@northwindtraders.onmicrosoft.com).
      - Primær SMTPAddress: Primær SMTP-adresse justeres i forhold til brugerens nye firma (f.eks user@northwind.com).
      - TargetAddress/ExternalEmailAddress: MailUser refererer til brugerens aktuelle postkasse, der er hostet i kildelejeren (f.eks. user@contoso.onmicrosoft.com). Når du tildeler denne værdi, skal du kontrollere, at du har/også tildeler PrimarySMTPAddress, ellers indstiller denne værdi PrimarySMTPAddress, hvilket vil medføre flyttefejl.
      - Du kan ikke tilføje ældre smtp-proxyadresser fra kildepostkassen for at målrette MailUser. Du kan f.eks. ikke contoso.com på MEU'en i fabrikam.onmicrosoft.com-lejerobjekter). Domæner er kun knyttet til én Azure AD- eller Exchange Online-lejer.

     Eksempel **på destinationobjektet** MailUser:

     | Attribut            | Værdi                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | Alias                | LaraN                                                                                                                   |
     | RecipientType        | MailUser                                                                                                                |
     | RecipientTypeDetails | MailUser                                                                                                                |
     | UserPrincipalName    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | LegacyExchangeDN     | /o=First Organization/ou=Exchange Administrative Group                                                                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | Mailadresser       | x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |
     |                      |                                                                                                                         |

     Eksempel **på kildepostkasseobjekt** :

     | Attribut            | Værdi                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | Alias                | LaraN                                                                   |
     | RecipientType        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | UserPrincipalName    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | LegacyExchangeDN     | /o=First Organization/ou=Exchange Administrative Group                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | Mailadresser       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |
     |                      |                                                                         |

   - Yderligere attributter kan være inkluderet i Exchange hybrid tilbageskrivning allerede. Hvis de ikke er inkluderet, skal de medtages.
   - msExchBlockedSendersHash – skriver online igen sikre og blokerede afsenderdata fra klienter Active Directory i det lokale miljø.
   - msExchSafeRecipientsHash – skriver onlinesikkerhedssikrede og blokerede afsenderdata fra klienter Active Directory i det lokale miljø.
   - msExchSafeSendersHash – skriver onlinesikkerhedssikrede og blokerede afsenderdata fra klienter Active Directory i det lokale miljø.

2. Hvis kildepostkassen er på LitigationHold, og størrelsen af kildepostkassen genoprettelige elementer er større end vores databasestandard (30 GB), fortsætter flytninger ikke, da målkvoten er mindre end størrelsen på kildepostkassen. Du kan opdatere destinationsobjektet MailUser for at overgå ELC-postkasseflag fra kildemiljøet til destinationen, hvilket udløser destinationssystemet til at udvide kvoten for MailUser til 100 GB, hvilket gør det muligt at flytte til destinationen. Denne vejledning fungerer kun for hybrididentitet, der kører Azure AD Forbind, da kommandoerne til at stemple ELC-flagene ikke er blot for lejeradministratorer.

    > [!NOTE]
    > EKSEMPEL – SOM DET ER, INGEN GARANTI
    >
    > Dette script forudsætter en forbindelse til både kildepostkassen (for at hente kildeværdier) og destinationsobjektet Active Directory i det lokale miljø (for at stemple ADUser-objektet). Hvis kilden har aktiveret procesførelse eller gendannelse af enkelte elementer, skal du angive dette på destinationskontoen.  Dette øger dumpsterstørrelsen for destinationskontoen til 100 GB.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. Lejere, der ikke er hybride mål, kan ændre kvoten for mappen genoprettelige elementer for MailUsers før overførslen ved at køre følgende kommando for at aktivere Retslig venteposition på MailUser-objektet og øge kvoten til 100 GB: `Set-MailUser -EnableLitigationHoldForMigration`. Bemærk, at dette ikke fungerer for lejere i hybrid.

4. Brugere i destinationsorganisationen skal have licens med de Exchange Online abonnementer, der gælder for organisationen. Du kan anvende en licens forud for en postkasse bevægelse, men KUN når destinationen MailUser er korrekt konfigureret med ExchangeGUID og proxyadresser. Hvis du anvender en licens, før ExchangeGUID anvendes, oprettes en ny postkasse, der er klargjort i målorganisationen.

    > [!NOTE]
    > Når du anvender en licens på en postkasse eller et MailUser-objekt, renses alle SMTP-type proxyAddresses for at sikre, at kun bekræftede domæner er inkluderet i matrixen Exchange Mailadresser.

5. Du skal sikre dig, at destinationen MailUser ikke har nogen tidligere ExchangeGuid, der ikke svarer til Source ExchangeGuid. Dette kan forekomme, hvis mål-MEU'en tidligere var licenseret til Exchange Online og klargjort en postkasse. Hvis MailUser-destinationen tidligere var licenseret til eller havde en ExchangeGuid, der ikke stemmer overens med Kilde ExchangeGuid, skal du udføre en oprydning af den skybaserede MEU. For disse skybaserede MEUs kan du køre `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > Denne proces kan ikke fortrydes. Hvis objektet har en blødSlettet postkasse, kan den ikke gendannes efter dette punkt. Når den er ryddet, kan du dog synkronisere den korrekte ExchangeGuid til destinationsobjektet, og MRS opretter forbindelse mellem kildepostkassen og den nyoprettede destinationspostkasse. (Reference EHLO-bloggen på den nye parameter).

    Find objekter, der tidligere var postkasser ved hjælp af denne kommando.

    ```powershell
    Get-User <identity> | select Name, *recipient* | Format-Table -AutoSize
    ```

    Her er et eksempel.

    ```powershell
    Get-User John@northwindtraders.com |select name, *recipient*| Format-Table -AutoSize

    Name       PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails
    ----       ---------------------------- ------------- --------------------
    John       UserMailbox                  MailUser      MailUser
    ```

    Ryd den blød-slettede postkasse ved hjælp af denne kommando.

    ```powershell
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```

    Her er et eksempel.

    ```powershell
    Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo -Confirm
    
    Are you sure you want to perform this action?
    Delete all existing information about user "John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.
    Do you want to continue?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y
    ```

### <a name="perform-mailbox-migrations"></a>Udfør postkasseoverflytninger

Postkasseoverførsel på Exchange lejere startes fra mållejeren som overførselsbatch. Dette er ligesom måden, hvorpå overførselsbatchs fungerer, når du Exchange fra en lokal Microsoft 365.

### <a name="create-migration-batches"></a>Opret overførselsbatch

Her er et eksempel på overførselsbatch-cmdlet'en til at starte flytninger.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> Mailadressen i CSV-filen skal være den, der er angivet i mållejeren, ikke kildelejeren.
>
> [Du kan finde flere oplysninger om cmdlet'en ved at klikke her](/powershell/module/exchange/new-migrationbatch)
>
> [Klik her for et eksempel på en CSV-fil](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

Overførselsbatchindsendelse understøttes også <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">fra den nye Exchange Administration,</a> når du vælger indstillingen på tværs af lejere.

### <a name="update-on-premises-mailusers"></a>Opdater lokale MailUsers

Når postkassen flyttes fra kilde til destination, skal du sikre, at de lokale mailbrugere i både kilde- og målmails opdateres med den nye targetAddress. I eksemplerne er det targetDeliveryDomain, der bruges i flytningen **, contoso.onmicrosoft.com**. Opdater mailbrugere med denne targetAddress.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Har vi brug for at opdatere RemoteMailboxes i den lokale kilde efter flytningen?**

Ja, du bør opdatere targetAddress (RemoteRoutingAddress/ExternalEmailAddress) for kildebrugere i det lokale miljø, når kildelejerpostkassen flytter til mållejeren.  Mens mailrouting kan følge henvisninger på tværs af flere mailbrugere med forskellige targetAddresses, skal ledig/optaget-opslag for mailbrugere målrette postkassebrugerens placering. Ledig/Optaget-opslag vil ikke lede efter flere omdirigeringer.

**Overflyttes Teams mellem lejere?**

Møder flyttes, men URL-Teams til mødet opdateres ikke, når elementer overføres mellem lejere. Da URL-adressen er ugyldig i mållejeren, skal du fjerne og genoprette Teams-møder.

**Overføres indholdet Teams en chatmappe på tværs af lejere?**

Nej, indholdet Teams chatmappen overføres ikke på tværs af lejere.

**Hvordan kan jeg bare se flytninger, der flytter på tværs af lejere, ikke mine onboarding- og off-boarding-flytninger?**

Brug _parameteren Flag_ . Her er et eksempel.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

**Kan du angive eksempelscripts til kopiering af attributter, der bruges i test?**

> [!NOTE]
> EKSEMPEL – SOM DET ER, ANTAGER INGEN GARANTI Dette script forudsætter en forbindelse til både kildepostkassen (for at få kildeværdier) og destinationen Active Directory i det lokale miljø Domain Services (for at stemple ADUser-objektet). Hvis kilden har aktiveret procesførelse eller gendannelse af enkelte elementer, skal du angive dette på destinationskontoen.  Dette øger dumpsterstørrelsen for destinationskontoen til 100 GB.



   ```powershell
   # This will export users from the source tenant with the CustomAttribute1 = "Cross-Tenant-Project"
   # These are the 'target' users to be moved to the Northwind org tenant
   $outFileUsers = "$home\desktop\UsersToMigrate.txt"
   $outFileUsersXML = "$home\desktop\UsersToMigrate.xml"
   Get-Mailbox -Filter "CustomAttribute1 -like 'Cross-Tenant-Project'" -ResultSize Unlimited | Select-Object -ExpandProperty  Alias | Out-File $outFileUsers
   $mailboxes = Get-Content $outFileUsers
   $mailboxes | ForEach-Object {Get-Mailbox $_} | Select-Object PrimarySMTPAddress,Alias,SamAccountName,FirstName,LastName,DisplayName,Name,ExchangeGuid,ArchiveGuid,LegacyExchangeDn,EmailAddresses | Export-Clixml $outFileUsersXML
   ```

   ```powershell
   # Copy the file $outfile to the desktop of the target on-premises then run the below to create MEU in Target
   $mailboxes = Import-Clixml $home\desktop\UsersToMigrate.xml
   add-type -AssemblyName System.Web
   foreach ($m in $mailboxes) {
       $organization = "@contoso.onmicrosoft.com"
       $mosi = $m.Alias+$organization
       $Password = [System.Web.Security.Membership]::GeneratePassword(16,4) | ConvertTo-SecureString -AsPlainText -Force
       $x500 = "x500:" +$m.LegacyExchangeDn
       $tmpUser = New-MailUser -MicrosoftOnlineServicesID $mosi -PrimarySmtpAddress $mosi -ExternalEmailAddress $m.PrimarySmtpAddress -FirstName $m.FirstName -LastName $m.LastName -Name $m.Name -DisplayName $m.DisplayName -Alias $m.Alias -Password $Password
       $tmpUser | Set-MailUser -EmailAddresses @{add=$x500} -ExchangeGuid $m.ExchangeGuid -ArchiveGuid $m.ArchiveGuid -CustomAttribute1 "Cross-Tenant-Project"
       $tmpx500 = $m.EmailAddresses | ?{$_ -match "x500"}
       $tmpx500 | %{Set-MailUser $m.Alias -EmailAddresses @{add="$_"}}
       }
   ```

   ```powershell
   # Now sync the changes from On-Premises to Azure and Exchange Online in the Target tenant
   # This action should create the target mail enabled users (MEUs) in the Target tenant
   Start-ADSyncCycle
   ```

**Hvordan får vi adgang Outlook på dag 1, når postkassen er flyttet?**

Da kun én lejer kan eje et domæne, vil den tidligere primære SMTPAddress ikke være knyttet til brugeren i mållejeren, når postkassens flytning er fuldført. kun de domæner, der er knyttet til den nye lejer. Outlook bruger brugerens nye UPN til at godkende tjenesten, og Outlook-profilen forventer at finde den ældre primære SMTPAddress til at matche postkassen i destinationssystemet. Da den ældre adresse ikke er i destinationssystemet, kan Outlook-profilen ikke oprette forbindelse for at finde den nyligt flyttede postkasse.

For at installationsstart skal brugerne genopbygge deres profil med deres nye UPN-, primære SMTP-adresse og ost-indhold til gensynkronisering.

> [!NOTE]
> Planlæg derfor, mens du batcher dine brugere til fuldførelse. Du skal tage højde for udnyttelse af netværk og kapacitet, når Outlook oprettes, og efterfølgende OST- og OAB-filer downloades til klienter.

**Hvilke Exchange RBAC-roller skal jeg være medlem af for at konfigurere eller fuldføre et skifte mellem lejere?**

Der findes en matrix af roller, der er baseret på antagelse af delegerede pligter, når du udfører en flytning af en postkasse. I øjeblikket kræves der to roller:

- Den første rolle er til en engangskonfigurationsopgave, der etablerer autorisationen til at flytte indhold ind eller ud af din lejer/organisationsgrænse. Da det at flytte data ud af din organisations kontrol er et vigtigt problem for alle virksomheder, har vi valgt den højeste tildelte rolle som Organisationsadministrator (OrgAdmin). Denne rolle skal ændre eller konfigurere en ny OrganizationRelationship, der definerer -MailboxMoveCapability med den eksterne organisation. Kun OrgAdmin kan ændre indstillingen MailboxMoveCapability, mens andre attributter på OrganizationRelationship kan administreres af administratoren for organisationsdeling.

- Den rolle, som udfører de faktiske flytningskommandoer, kan uddelegeres til en funktion på lavere niveau. Rollen som Flyt postkasser er tildelt muligheden for at flytte postkasser ind eller ud af organisationen.

**Hvordan målretter vi den SMTP-adresse, der vælges for targetAddress (TargetDeliveryDomain) på den konverterede postkasse (til mailbrugerkonvertering)?**

Exchange postkasse flytter ved hjælp af MRS til at udforme targetAddress på den oprindelige kildepostkasse, når du konverterer til en MailUser ved at matche en mailadresse (proxyAddress) på destinationsobjektet. Processen tager værdien -TargetDeliveryDomain overført til kommandoen Flyt og kontrollerer derefter, om der er en tilsvarende proxy for det pågældende domæne på destinationssiden. Når vi finder et match, bruges den matchende proxyAddress til at angive ExternalEmailAddress (targetAddress) på det konverterede postkasseobjekt (nu MailUser).

**Hvordan overgås postkassetilladelser?**

Postkassetilladelser omfatter Send på vegne af og Postkasseadgang:

- Send på vegne af (AD:publicDelegates) gemmer DN for modtagere med adgang til en brugers postkasse som stedfortræder. Denne værdi gemmes i Active Directory og flyttes i øjeblikket ikke som en del af postkasseovergangen. Hvis kildepostkassen har publicDelegates angivet, skal du genoprette de offentligeDelegates på målpostkassen, når konverteringen af MEU til postkasse er fuldført i destinationsmiljøet ved at køre `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`.

- Postkassetilladelser, der er gemt i postkassen, flyttes sammen med postkassen, når både hovedstolen og stedfortræderen flyttes til destinationssystemet. Eksempelvis tildeles brugerens TestUser_7 FullAccess til TestUser_8 i lejerens SourceCompany.onmicrosoft.com. Når postkassens flytning fuldførte til TargetCompany.onmicrosoft.com, konfigureres de samme tilladelser i destinationsmappen. Eksempler på brug *af Get-MailboxPermission* til TestUser_7 både kilde- og mållejeren er vist nedenfor. Exchange-cmdletter har præfiks med kilde og destination i overensstemmelse hermed.

Her er et eksempel på outputtet fra postkassetilladelsen før en flytning.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

Her er et eksempel på outputtet fra postkassetilladelsen efter flytningen.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> Postkasse- og kalendertilladelser på tværs af lejere understøttes IKKE. Du skal organisere hovedstole og stedfortrædere i konsoliderede flytningsbatchs, så disse forbundne postkasser skiftes samtidigt fra kildelejeren.

**Hvilken X500-proxy skal føjes til mailbrugerproxyadresserne på destinationen for at aktivere overførslen?**

Overførslen af postkasser på tværs af lejere kræver, at LegacyExchangeDN-værdien for kildepostkassens objekt stemples som en x500-mailadresse på mailuser-objektet.

Eksempel:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> Ud over denne X500-proxy skal du kopiere alle X500-proxyer fra postkassen i kilden til postkassen i destinationen.

**Kan kilde- og mållejeren bruge det samme domænenavn?**

Nej. Domænenavnene for kilde- og mållejeren skal være entydige. Eksempelvis et kildedomæne med contoso.com og destinationsdomænet for fourthcoffee.com.

**Vil delte postkasser blive flyttet og stadig fungere?**

Ja, men vi beholder kun butikstilladelserne som beskrevet i følgende artikler:

- [Microsoft Docs | Administrer tilladelser for modtagere i Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [Microsoft Support | Sådan tildeler Exchange og Outlook postkassetilladelser i Office 365 dedikeret](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**Har du nogen anbefalinger til batches?**

Oversvarer ikke 2000 postkasser pr. batch. Vi anbefaler på det kraftigste at indsende batches to uger før skæringsdatoen, da det ikke har nogen indflydelse på slutbrugerne under synkroniseringen. Hvis du har brug for vejledning til postkasser med mere end 50.000 postkasser, kan du kontakte distributionslisten for teknisk feedback crosstenantmigrationpreview@service.microsoft.com.

**Hvad gør jeg, hvis jeg bruger tjenestekryptering med kundenøgle?**

Postkassen bliver dekrypteret, før den flyttes. Sørg for, at kundenøgle er konfigureret i mållejeren, hvis det stadig er påkrævet. Se [her for](/microsoft-365/compliance/customer-key-overview) at få flere oplysninger.

**Hvad er den anslåede overførselstid?**

Som en hjælp til at planlægge din overførsel viser tabellen [](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) her retningslinjerne for, hvornår du kan forvente masseflytninger af postkasser eller individuelle migreringer, der skal fuldføres. Disse estimater er baseret på en dataanalyse af tidligere kundeoverflytninger. Da alle miljøer er unikke, kan den nøjagtige overførselshastighed variere.

Husk, at denne funktion i øjeblikket er en prøveversion og SLA'en, og alle gældende serviceniveauer gælder ikke for eventuelle problemer med ydeevne eller tilgængelighed under forhåndsvisningsstatus for denne funktion.

**Beskyttelse af dokumenter i kildelejeren, der kan bruges af brugere i destinationslejeren.**

Overførsel på tværs af lejere overfører kun postkassedata og intet andet. Der er flere andre muligheder, som er dokumenteret i følgende blogindlæg, som kan hjælpe: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

**Kan jeg have de samme etiketter i destinationslejeren, som du havde i kildelejeren, enten som det eneste sæt etiketter eller et ekstra sæt etiketter for de overførte brugere, afhængigt af justeringen mellem organisationer.**

Da overførsel på tværs af lejere ikke eksporterer navne, og det ikke er muligt at dele navne mellem lejere, kan du kun gøre dette ved at genskabe etiketterne i destinationslejeren.

**Understøtter du flytning Microsoft 365-grupper?**

I øjeblikket understøtter funktionen til overførsel af postkasser på tværs af lejer ikke Microsoft 365-grupper.

**Kan en kildelejeradministrator udføre en eDiscovery-søgning mod en postkasse, når postkassen er blevet overført til den nye lejer/mål?**

Nej, efter en overførsel af en postkasse på tværs af lejeren fungerer eDiscovery mod den overførte brugers postkasse i kilden ikke. Dette skyldes, at der ikke længere er en postkasse i kilden at søge efter, da postkassen er blevet overført til mållejeren og nu tilhører mållejeren. eDiscovery, postpostkasseoverførsel kan kun udføres i mållejeren (hvor postkassen nu findes). Hvis en kopi af kildepostkassen skal bevares i kildelejeren efter overførslen, kan administratoren i kilden kopiere indholdet til en alternativ postkasse før fremtidige eDiscovery-handlinger mod dataene.

## <a name="known-issues"></a>Kendte problemer

- **Problem: Efter overførslen Teams kildelejeren begrænset.** Når postkassen er overført til mållejeren, vil Teams kildelejeren ikke længere have adgang til brugerens postkasse. Så hvis en bruger logger på Teams med kildelejerens legitimationsoplysninger, vil der være et tab af funktionalitet såsom manglende mulighed for at opdatere dit profilbillede, intet kalenderprogram og manglende mulighed for at søge efter og deltage i offentlige teams.

- **Problem: Automatisk udvidede arkiver kan ikke overføres.** Overførselsfunktionen på tværs af lejere understøtter overførsel af den primære postkasse og arkivpostkassen for en bestemt bruger. Hvis brugeren i kilden har et automatisk udvidet arkiv – dvs. mere end én arkivpostkasse, kan funktionen ikke overføre de ekstra arkiver og bør mislykkes.

- **Problem: Cloud MailUsers with non-owned smtp proxyAddress block MRS moves background.** Når du opretter PostUser-objekter for mållejeren, skal du sikre dig, at alle SMTP-proxyadresser tilhører mållejerorganisationen. Hvis der findes en SMTP-proxyAddress på målmailbrugeren, der ikke tilhører den lokale lejer, forhindres konvertering af MailUser til Postkasse. Dette skyldes vores forsikring om, at postkasseobjekter kun kan sende mails fra domæner, som lejeren er autoritativ (domæner, som lejeren har påstået):

  - Når du synkroniserer brugere fra det lokale miljø ved hjælp af Azure AD Forbind, klargør du lokale MailUser-objekter med ExternalEmailAddress, der peger på kildelejeren, hvor postkassen findes (LaraN@contoso.onmicrosoft.com), og du stempler PrimarySMTPAddress som et domæne, der er placeret i mållejeren (Lara.Newton@northwind.com). Disse værdier synkroniseres ned til lejeren, og en passende mailbruger klargøres og er klar til overførsel. Her vises et eksempelobjekt.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > *Adresselinjen contoso.onmicrosoft.com* ikke *findes* i matrixen Mailadresser/proxyAdresser.

- **Problem: MailUser-objekter med "eksterne" primære SMTP-adresser ændres/nulstilles til "interne" virksomheds påstået domæner**

  PostBruger-objekter er henvisninger til postkasser, der ikke er lokale. I forbindelse med migrering af postkasser på tværs af lejere bruger vi MailUser-objekter til at repræsentere enten kildepostkassen (set fra målorganisationens perspektiv) eller målpostkassen (set fra kildeorganisationens perspektiv). MailUsers har en ExternalEmailAddress (targetAddress), der peger på smtp-adressen for den faktiske postkasse (ProxyTest@fabrikam.onmicrosoft.com) og den primæreSMTP-adresse, der repræsenterer den viste SMTP-adresse for postkassebrugeren i kataloget. Nogle organisationer vælger at vise den primære SMTP-adresse som en ekstern SMTP-adresse og ikke som en adresse, der ejes/bekræftes af den lokale lejer (f.eks. fabrikam.com i stedet for som contoso.com).  Men når et Exchange-serviceabonnementobjekt anvendes på MailUser via licenshandlinger, ændres den primære SMTP-adresse til at blive vist som et domæne, der er bekræftet af den lokale organisation (contoso.com). Der er to mulige årsager:

  - Når en Exchange-serviceplan anvendes på en MailUser, begynder Azure AD-processen at gennemtvinge proxy rense for at sikre, at den lokale organisation ikke kan sende mails ud, spoof eller mail fra en anden lejer. Enhver SMTP-adresse på et modtagerobjekt med disse serviceplaner fjernes, hvis adressen ikke er bekræftet af den lokale organisation. Som det er tilfældet i eksemplet, er Fabikam.com domæne IKKE bekræftet af contoso.onmicrosoft.com lejer, så renselse fjerner dette fabrikam.com domæne. Hvis du vil bevare disse eksterne domæner på MailUser, enten før overførslen eller efter overførslen, skal du ændre dine overførselsprocesser til at fjerne licenser, når overførslen er fuldført, eller før flytningen for at sikre, at brugerne har den forventede eksterne branding anvendt. Du skal sikre dig, at postkasseobjektet har den rette licens til ikke at påvirke mailtjenesten.
  - Et eksempel på et script til at fjerne serviceplaner på en MailUser i contoso.onmicrosoft.com lejer vises her.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTELLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION"
    Set-MsolUserLicense -UserPrincipalName ProxyTest@contoso.com LicenseOptions $lo
    ```

       Resultaterne i det tildelte sæt ServicePlans vises her.

    ```powershell
    (Get-MsolUser -UserPrincipalName ProxyTest@contoso.com).licenses | Select-Object -ExpandProperty ServiceStatus |sort ProvisioningStatus -Descending

    ServicePlan           ProvisioningStatus
    -----------           ------------------
    ATP_ENTERPRISE        PendingProvisioning
    MICROSOFT_SEARCH      PendingProvisioning
    INTUNE_O365           PendingActivation
    PAM_ENTERPRISE        Disabled
    EXCHANGE_ANALYTICS    Disabled
    EQUIVIO_ANALYTICS     Disabled
    THREAT_INTELLIGENCE   Disabled
    LOCKBOX_ENTERPRISE    Disabled
    PREMIUM_ENCRYPTION    Disabled
    EXCHANGE_S_ENTERPRISE Disabled
    INFORMATION_BARRIERS  Disabled
    MYANALYTICS_P2        Disabled
    MIP_S_CLP1            Disabled
    MIP_S_CLP2            Disabled
    ADALLOM_S_O365        PendingInput
    RMS_S_ENTERPRISE      Success
    YAMMER_ENTERPRISE     Success
    PROJECTWORKMANAGEMENT Success
    BI_AZURE_P2           Success
    WHITEBOARD_PLAN3      Success
    SHAREPOINTENTERPRISE  Success
    SHAREPOINTWAC         Success
    KAIZALA_STANDALONE    Success
    OFFICESUBSCRIPTION    Success
    MCOSTANDARD           Success
    Deskless              Success
    STREAM_O365_E5        Success
    FLOW_O365_P3          Success
    POWERAPPS_O365_P3     Success
    TEAMS1                Success
    MCOEV                 Success
    MCOMEETADV            Success
    BPOS_S_TODO_3         Success
    FORMS_PLAN_E5         Success
    SWAY                  Success
    ```

    Brugerens PrimarySMTPAddress renses ikke længere. Domænet fabrikam.com ikke ejes af contoso.onmicrosoft.com-lejeren og bevares som den primære SMTP-adresse, der vises i mappen.

    Her er et eksempel.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - Når msExchRemoteRecipientType er indstillet til 8 (DeprovisionMailbox), for lokale MailUsers, der er overført til mållejeren, fjerner proxy renselogik i Azure ikke-ejet domæner og nulstiller primarySMTP til et ejet domæne. Når du rydder msExchRemoteRecipientType i den lokale MailUser, gælder proxy scrub-logik ikke længere.

      Nedenfor finder du det fulde sæt aktuelle serviceplaner, der Exchange Online.

      | Navn                                             |
      | ------------------------------------------------ |
      | Advanced eDiscovery Storage (500 GB)              |
      | Kunde-lockbox                                 |
      | Forebyggelse af datatab                             |
      | Exchange Enterprise CAL-tjenester (EOP, DLP)      |
      | Exchange Essentials                              |
      | Exchange Foundation                              |
      | Exchange Online (P1)                             |
      | Exchange Online (plan 1)                         |
      | Exchange Online (plan 2)                         |
      | Exchange Online-arkivering til Exchange Online    |
      | Exchange Online-arkivering til Exchange Server    |
      | Exchange Online inaktivt bruger-tilføjelsesprogrammet             |
      | Exchange Online-kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online plan 1                           |
      | Exchange Online POP                              |
      | Exchange Online Protection                       |
      | Informationsbarrierer                             |
      | Information Protection til Office 365 - Premium  |
      | Information Protection til Office 365 – Standard |
      | Insights af MyAnalytics                          |
      | Microsoft 365 avanceret overvågning                  |
      | Microsoft Bookings                               |
      | Microsoft Business Center                        |
      | Microsoft MyAnalytics (fuld)                     |
      | Office 365 Advanced eDiscovery                   |
      | Microsoft Defender for Office 365 (Plan 1)       |
      | Microsoft Defender for Office 365 (Plan 2)       |
      | Office 365 med adgangspriviligerede rettigheder          |
      | Premium kryptering i Office 365                 |
      |                                                  |
