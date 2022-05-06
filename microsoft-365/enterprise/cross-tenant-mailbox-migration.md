---
title: Migrering af postkasse på tværs af lejere
description: Sådan flytter du postkasser mellem Microsoft 365 eller Office 365 lejere.
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 05/05/2022
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: 984df48edf4ba75569286618086d8be9ab684b60
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243046"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Overførsel af postkasse på tværs af lejere (prøveversion)

Normalt har du under fusioner eller frasalg brug for muligheden for at flytte din brugers Exchange Online postkasse til en ny lejer. Overførsel af postkasser på tværs af lejere giver lejeradministratorer mulighed for at bruge velkendte grænseflader, f.eks. Remote PowerShell og MRS, til at overføre brugere til deres nye organisation.

Administratorer kan bruge den New-MigrationBatch cmdlet, der er tilgængelig via administrationsrollen Flyt postkasser, til at udføre flytninger på tværs af lejere.

De brugere, der migrerer, skal være til stede i destinationslejeren Exchange Online systemet som MailUsers, markeret med specifikke attributter for at aktivere flytninger på tværs af lejere. Systemet vil ikke kunne flyttes for brugere, der ikke er konfigureret korrekt i destinationslejer.

Når flytningerne er fuldført, konverteres kildebrugerpostkassen til en MailUser, og destinationsadressen (vist som ExternalEmailAddress i Exchange) stemples med distributionsadressen til destinationslejeren. Denne proces efterlader den ældre MailUser i kildelejer og giver mulighed for sameksistens og postdistribution. Når forretningsprocesser tillader det, kan kildelejer fjerne kildemailbrugeren eller konvertere dem til en mailkontakt.

Overførsel af Exchange postkasser på tværs af lejere understøttes kun for lejere i hybride eller cloudbaserede lejere eller en hvilken som helst kombination af de to.

I denne artikel beskrives processen for flytning af postkasser på tværs af lejere, og den indeholder en vejledning i, hvordan du forbereder kilde- og destinationslejere for Exchange Online postkasseindhold flyttes.

   > [!NOTE]
   > Vi har for nylig opdateret vores konfigurationstrin for at aktivere overførsel af postkasser på tværs af lejere, så det ikke længere kræver Azure Key Vault! Hvis det er første gang, du onboarder til denne prøveversion, kræves der ingen handling, og du kan gå videre og følge de trin, der er beskrevet i dette dokument. Hvis du er begyndt at konfigurere dine lejere ved hjælp af den tidligere AKV-metode, anbefaler vi på det kraftigste, at du stopper eller fjerner konfigurationen for at begynde at bruge denne nye metode. Hvis du har overførsel af postkasser i gang med den tidligere AKV-metode, skal du vente, indtil dine eksisterende overførsler er fuldført, og følge nedenstående trin for at aktivere den nye forenklede metode. Azure Key Vault påkrævede konfigurationstrin arkiveres, men kan findes **[her](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)** som reference.

## <a name="preparing-source-and-target-tenants"></a>Forbereder kilde- og destinationslejere

### <a name="prerequisites-for-source-and-target-tenants"></a>Forudsætninger for kilde- og destinationslejere

Før du starter, skal du sørge for, at du har de nødvendige tilladelser til at konfigurere programmet Flyt postkasse i Azure, EXO Migration Endpoint og EXO-organisationsrelationen.

Derudover kræves der mindst én mailaktiveret sikkerhedsgruppe i kildelejer. Disse grupper bruges til at udvide listen over postkasser, der kan flyttes fra kildelejer (eller nogle gange kaldet ressourcelejer) til destinationslejer. Dette gør det muligt for kildelejeradministratoren at begrænse eller begrænse det specifikke sæt postkasser, der skal flyttes, så utilsigtede brugere ikke kan overføres. Indlejrede grupper understøttes ikke.

Du skal også kommunikere med dit partnerfirma, der er tillid til (med hvem du flytter postkasser) for at få deres Microsoft 365 lejer-id. Dette lejer-id bruges i feltet Domænenavn for organisationsrelation.

Hvis du vil hente lejer-id'et for et abonnement, [skal du](https://go.microsoft.com/fwlink/p/?linkid=2024339) logge på Microsoft 365 Administration og gå til [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Klik på kopieringsikonet for egenskaben Lejer-id for at kopiere den til Udklipsholder.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>Konfigurationstrin til aktivering af dine lejere for migrering af postkasser på tværs af lejere

   > [!NOTE]
   > Du skal konfigurere destinationen (destinationen) først. Hvis du vil fuldføre disse trin, behøver du ikke at have eller kende lejeradministratorens legitimationsoplysninger for både kilde- og destinationslejer. Trin kan udføres enkeltvist for hver lejer af forskellige administratorer.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>Forbered destinationslejer (destinationslejer) ved at oprette overførselsprogrammet og hemmeligheden

1. Log på din Azure AD-portal (<https://portal.azure.com>) med dine legitimationsoplysninger som lejeradministrator for destinationen

   ![Azure Logon](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. Klik på Vis under Administrer Azure Active Directory.

   ![knappen Azure Active Directory](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. Vælg Appregistreringer på navigationslinjen til venstre.

4. Vælg Ny registrering

   ![Nyt program](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. På siden Registrer et program under Understøttede kontotyper skal du vælge Konti i en hvilken som helst organisationsmappe (Enhver Azure AD mappe – Multitenant). Vælg derefter Web under Omdirigerings-URI (valgfrit), og angiv <https://office.com>. Endelig skal du vælge Registrer.

   ![Programregistrering](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. I øverste højre hjørne af siden kan du se en pop op-meddelelse om, at appen blev oprettet.

7. Gå tilbage til startsiden, Azure Active Directory, og klik på Appregistreringer.

8. Find den app, du har oprettet, under Ejede programmer, og klik på den.

9. Under ^Essentials skal du kopiere program-id'et (klient-id'et) ned, da du skal bruge det senere for at oprette en URL-adresse til destinationslejer.

10. Klik på API-tilladelser på navigationslinjen til venstre for at få vist tilladelser, der er tildelt din app.

11. Som standard Bruger. Læsetilladelser tildeles til den app, du har oprettet, men vi kræver dem ikke til migrering af postkasser, du kan fjerne denne tilladelse.

    ![Programtilladelser](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. Nu skal vi tilføje tilladelse til overførsel af postkasse. Vælg Tilføj en tilladelse

13. I vinduet Anmod om API-tilladelser skal du vælge API'er, som min organisation bruger, søge efter Office 365 Exchange Online og vælge det.

    ![Vælg API](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. Vælg derefter Programtilladelser

15. Derefter skal du under Vælg tilladelser udvide Postkasse og kontrollere Mailbox.Migration og Tilføj tilladelser nederst på skærmen.

    ![Angiv API](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. Vælg nu Certifikater & hemmeligheder på navigationslinjen til venstre for programmet.

17. Under Klienthemmeligheder skal du vælge ny klienthemmelighed.

    ![Klienthemmeligheder](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. I vinduet Tilføj en klienthemmelighed skal du angive en beskrivelse og konfigurere de ønskede udløbsindstillinger.

      > [!NOTE]
      > Dette er den adgangskode, der bruges, når du opretter dit overførselsslutpunkt. Det er ekstremt vigtigt, at du kopierer denne adgangskode til udklipsholderen og eller kopierer denne adgangskode for at sikre/skjule adgangskoden. Dette er den eneste gang, du vil kunne se denne adgangskode! Hvis du på en eller anden måde mister den eller har brug for at nulstille den, kan du logge på vores Azure Portal igen, gå til Appregistreringer, finde din overførselsapp, vælge Hemmeligheder & certifikater og oprette en ny hemmelighed for din app.

19. Nu, hvor du har oprettet overførselsprogrammet og -hemmeligheden, skal du give dit samtykke til programmet. Hvis du vil give dit samtykke til programmet, skal du gå tilbage til landingssiden for Azure Active Directory, klikke på Virksomhedsprogrammer i den venstre navigationsrude, finde din overførselsapp, du har oprettet, vælge den og vælge Tilladelser i venstre navigationsrude.

20. Klik på knappen Tildel administratorsamtykke til [din lejer].

21. Der åbnes et nyt browservindue, og vælg Acceptér.

22. Du kan gå tilbage til portalvinduet og vælge Opdater for at bekræfte din accept.

23. Formulerer URL-adressen, der skal sendes til din partner, der er tillid til (kildelejeradministrator), så de også kan acceptere programmet for at aktivere overførsel af postkasser. Her er et eksempel på den URL-adresse, du skal angive for dem, og du skal bruge program-id'et for den app, du har oprettet:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet.
    >
    > Du skal erstatte sourcetenant.onmicrosoft.com i ovenstående eksempel med de korrekte kildelejere onmicrosoft.com navn.
    >
    > Du skal også erstatte [application_id_of_the_app_you_just_created] med program-id'et for den postkasseoverførselsapp, du lige har oprettet.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>Forbered destinationslejer ved at oprette slutpunktet for Exchange Online migrering og organisationsrelationen

1. Opret en Ekstern PowerShell-forbindelse til destinationen Exchange Online lejer.

2. Opret et nyt overførselsslutpunkt for flytninger af postkasser på tværs af lejere

   > [!NOTE]
   > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet, og adgangskoden (den hemmelighed), du konfigurerede under denne proces. Afhængigt af den Microsoft 365 cloudforekomst, du bruger dit slutpunkt, kan det også være anderledes. Se siden [Microsoft 365 slutpunkter](/microsoft-365/enterprise/microsoft-365-endpoints), vælg den korrekte forekomst for din lejer, og gennemse Exchange Online Optimer påkrævet adresse, og erstat efter behov.

   ```powershell

   # Enable customization if tenant is dehydrated
     $dehydrated=Get-OrganizationConfig | fl isdehydrated
     if ($dehydrated -eq $true) {Enable-OrganizationCustomization}

   $AppId = "[guid copied from the migrations app]"

   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)

   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. Opret nyt eller rediger dit eksisterende organisationsrelationsobjekt til din kildelejer.

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

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>Forbered kildelejer (aktuel postkasseplacering) ved at acceptere overførselsprogrammet og konfigurere organisationsrelationen

1. Gå til linket til URL-adressen fra din partner, der er tillid til, fra en browser for at give samtykke til overførselsprogrammet for postkassen. URL-adressen ser sådan ud:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > Du skal bruge program-id'et for den postkasseoverførselsapp, du lige har oprettet.
   > Du skal erstatte sourcetenant.onmicrosoft.com i ovenstående eksempel med de korrekte kildelejere onmicrosoft.com navn.
   > Du skal også erstatte [application_id_of_the_app_you_just_created] med program-id'et for den postkasseoverførselsapp, du lige har oprettet.

2. Acceptér programmet, når pop op-vinduet vises. Du kan også logge på din Azure Active Directory portal og finde programmet under Virksomhedsprogrammer.

3. Opret nyt eller rediger dit eksisterende organisationsrelationsobjekt til destinationslejer fra et Exchange Online Remote PowerShell-vindue.

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
> Det lejer-id, du angiver som $sourceTenantId og $targetTenantId, er GUID'et og ikke lejerdomænenavnet. Du kan finde et eksempel på et lejer-id og oplysninger om, hvordan du finder dit lejer-id, under [Find dit Microsoft 365 lejer-id](/onedrive/find-your-office-365-tenant-id).

### <a name="how-do-i-know-this-worked"></a>Hvordan gør jeg ved, det virkede?

Du kan bekræfte konfigurationen af migrering af postkasser på tværs af lejere ved at køre [Test-MigrationServerAvailability-cmdlet'en](/powershell/module/exchange/Test-MigrationServerAvailability) i forhold til det slutpunkt for overførsel på tværs af lejere, som du oprettede i din destinationslejer.

   > [!NOTE]
   >
   > - Destinationslejer:
   >
   > Test-MigrationServerAvailability -Slutpunkt "[navnet på dit slutpunkt for overførsel på tværs af lejere]"
   >
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
   >
   > - Kildelejer:
   >
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability

### <a name="move-mailboxes-back-to-the-original-source"></a>Flyt postkasser tilbage til den oprindelige kilde

Hvis der kræves en postkasse for at flytte tilbage til den oprindelige kildelejer, skal det samme sæt trin og scripts køres i både nye kildelejere og nye destinationslejere. Det eksisterende organisationsrelationsobjekt opdateres eller tilføjes, og det oprettes ikke igen

## <a name="prepare-target-user-objects-for-migration"></a>Forbered destinationsbrugerobjekter til overførsel

De brugere, der migrerer, skal være til stede i destinationslejeren og Exchange Online system (som MailUsers), der er markeret med bestemte attributter for at aktivere flytninger på tværs af lejere. Systemet vil ikke kunne flyttes for brugere, der ikke er konfigureret korrekt i destinationslejer. I følgende afsnit er der oplysninger om kravene til MailUser-objektet for destinationslejer.

### <a name="prerequisites-for-target-user-objects"></a>Forudsætninger for destinationsbrugerobjekter

Sørg for, at følgende objekter og attributter er angivet i destinationsorganisationen.

1. For alle postkasser, der flyttes fra en kildeorganisation, skal du klargøre et MailUser-objekt i destinationsorganisationen:

   - Destinationsmailbrugeren skal have disse attributter fra kildepostkassen eller tildelt det nye User-objekt:
      - ExchangeGUID (direkte flow fra kilde til destination): Postkassens GUID skal stemme overens. Flytteprocessen fortsætter ikke, hvis den ikke findes på destinationsobjektet.
      - ArchiveGUID (direkte flow fra kilde til destination): Arkiv-GUID'et skal stemme overens. Flytteprocessen fortsætter ikke, hvis den ikke findes i destinationsobjektet. Dette er kun påkrævet, hvis kildepostkassen er Arkiv aktiveret.
      - LegacyExchangeDN (flow som proxyAddress, "x500:\<LegacyExchangeDN>"): LegacyExchangeDN skal være til stede på destinationen MailUser som x500: proxyAddress. Derudover skal du også kopiere alle x500-adresser fra kildepostkassen til destinationsmailbrugeren. Flytteprocesserne fortsætter ikke, hvis disse ikke findes i destinationsobjektet.
      - UserPrincipalName: UPN justeres i forhold til brugerens NYE identitet eller målfirma (f.eks. user@northwindtraders.onmicrosoft.com).
      - Primær SMTP-adresse: Primær SMTP-adresse justeres i forhold til brugerens NYE firma (f.eks. user@northwind.com).
      - TargetAddress/ExternalEmailAddress: MailUser refererer til brugerens aktuelle postkasse, der hostes i kildelejeren (f.eks. user@contoso.onmicrosoft.com). Når du tildeler denne værdi, skal du kontrollere, at du har/også tildeler PrimarySMTPAddress, ellers angiver denne værdi PrimarySMTPAddress, hvilket medfører flytningsfejl.
      - Du kan ikke føje ældre smtp-proxyadresser fra kildepostkassen til destinationen MailUser. Du kan f.eks. ikke vedligeholde contoso.com på MEU i fabrikam.onmicrosoft.com lejerobjekter). Domæner er kun knyttet til én Azure AD eller Exchange Online lejer.

     Eksempel **på destinationens** MailUser-objekt:

     | Attribut            | Værdi                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | Alias                | LaraN                                                                                                                   |
     | Modtagertype        | Mailbruger                                                                                                                |
     | RecipientTypeDetails | Mailbruger                                                                                                                |
     | UserPrincipalName    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | LegacyExchangeDN     | /o=Første organisation/ou=Exchange administrativ gruppe                                                                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | Mailadresser       | x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |

     Eksempel **på kildepostkasseobjekt** :

     | Attribut            | Værdi                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | Alias                | LaraN                                                                   |
     | Modtagertype        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | UserPrincipalName    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | LegacyExchangeDN     | /o=Første organisation/ou=Exchange administrativ gruppe                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | Mailadresser       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |

   - Der kan allerede medtages yderligere attributter i Exchange hybrid tilbageførsel. Hvis ikke, bør de medtages.
   - msExchBlockedSendersHash – skriver online sikre og blokerede afsenderdata tilbage fra klienter til Active Directory i det lokale miljø.
   - msExchSafeRecipientsHash – skriver online sikre og blokerede afsenderdata tilbage fra klienter til Active Directory i det lokale miljø.
   - msExchSafeSendersHash – skriver online sikre og blokerede afsenderdata fra klienter tilbage til Active Directory i det lokale miljø.

2. Hvis kildepostkassen er på LitigationHold, og størrelsen på genoprettelige elementer i kildepostkassen er større end standarddatabasen (30 GB), fortsættes flytningen ikke, da målkvoten er mindre end størrelsen på kildepostkassen. Du kan opdatere destinationsobjektet MailUser for at overføre ELC-postkasseflagene fra kildemiljøet til destinationen, hvilket udløser destinationssystemet for at udvide kvoten for MailUser til 100 GB, hvilket gør det muligt at flytte til destinationen. Disse instruktioner fungerer kun for hybrididentitet, der kører Azure AD Forbind, da kommandoerne til at stemple ELC-flagene ikke eksponeres for lejeradministratorer.

    > [!NOTE]
    > EKSEMPEL – SOM DET ER, INGEN GARANTI
    >
    > Dette script forudsætter, at der er forbindelse til både kildepostkassen (for at hente kildeværdier) og mål-Active Directory i det lokale miljø (for at stemple ADUser-objektet). Hvis kilde har aktiveret procesførelse eller gendannelse af et enkelt element, skal du angive dette på destinationskontoen.  Dette vil øge destinationskontoens dumpsterstørrelse til 100 GB.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. Ikke-hybride destinationslejere kan ændre kvoten for mappen Gendanbare elementer for MailUsers før migreringen ved at køre følgende kommando for at aktivere Litigation Hold på MailUser-objektet og øge kvoten til 100 GB:

   ```powershell
   Set-MailUser -Identity <MailUserIdentity> -EnableLitigationHoldForMigration
   ```

   Bemærk, at dette ikke fungerer for lejere i hybrid.

4. Brugere i målorganisationen skal have licens med de relevante Exchange Online abonnementer, der gælder for organisationen. Du kan anvende en licens, før en postkasse flyttes, men kun når destinationsmailbrugeren er konfigureret korrekt med ExchangeGUID- og proxyadresser. Anvendelse af en licens, før ExchangeGUID anvendes, vil resultere i en ny postkasse, der er klargjort i destinationsorganisationen.

    > [!NOTE]
    > Når du anvender en licens på et postkasse- eller MailUser-objekt, renses alle SMTP-typeproxyAdresser for at sikre, at det kun er bekræftede domæner, der er inkluderet i matrixen Exchange EmailAddresses.

5. Du skal sikre, at destinationsmailbrugeren ikke har en tidligere ExchangeGuid, der ikke stemmer overens med kildeudvekslingsguid. Dette kan ske, hvis mål-MEU'en tidligere var licenseret til Exchange Online og klargjort en postkasse. Hvis destinationen MailUser tidligere er licenseret til eller havde en ExchangeGuid, der ikke stemmer overens med Kilde ExchangeGuid, skal du udføre en oprydning af cloud-MEU'en. For disse cloud-MEU'er kan du køre `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > Denne proces kan ikke fortrydes. Hvis objektet har en softDeleted-postkasse, kan det ikke gendannes efter dette punkt. Når det er ryddet, kan du dog synkronisere den korrekte ExchangeGuid med destinationsobjektet, og FRU forbinder kildepostkassen med den destinationspostkasse, der netop er oprettet. (Reference ehlo-blog om den nye parameter).

    Find objekter, der tidligere var postkasser, ved hjælp af denne kommando.

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

    Ryd den blød slettede postkasse ved hjælp af denne kommando.

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

### <a name="perform-mailbox-migrations"></a>Udfør migrering af postkasse

Overflytninger af postkasser på tværs af lejere Exchange startes fra destinationslejeren som overførselsbatch. Det er ligesom den måde, overførselsbatchs om bord fungerer på, når der migreres fra Exchange i det lokale miljø til Microsoft 365.

### <a name="create-migration-batches"></a>Opret overførselsbatch

Her er et eksempel på en batch-cmdlet til migrering til start af flytninger.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> Mailadressen i CSV-filen skal være den, der er angivet i destinationslejer, ikke kildelejer.
>
> [Klik her for at få flere oplysninger om cmdlet'en](/powershell/module/exchange/new-migrationbatch)
>
> [Klik her for et eksempel på en CSV-fil](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

Overførsel af batchafsendelse understøttes også fra det nye <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>, når du vælger indstillingen på tværs af lejere.

### <a name="update-on-premises-mailusers"></a>Opdater mailbrugere i det lokale miljø

Når postkassen flyttes fra kilde til destination, skal du sikre, at mailbrugerne i det lokale miljø i både kilden og destinationen opdateres med den nye targetAddress. I eksemplerne er det targetDeliveryDomain, der bruges i flytningen **, contoso.onmicrosoft.com**. Opdater mailbrugerne med denne targetAddress.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

**Skal vi opdatere RemoteMailboxes i kilden i det lokale miljø efter flytningen?**

Ja, du skal opdatere destinationsadressen (RemoteRoutingAddress/ExternalEmailAddress) for kildebrugerne i det lokale miljø, når kildelejerpostkassen flyttes til destinationslejeren.  Mens postdistribution kan følge henvisningerne på tværs af flere mailbrugere med forskellige destinationsadresser, skal ledig/optaget-opslag for mailbrugere være rettet mod postkassebrugerens placering. Ledig/optaget-opslag jagter ikke flere omdirigeringer.

**Overfører Teams møder på tværs af lejere?**

Møderne flyttes, men Teams møde-URL-adressen opdateres ikke, når elementer overføres på tværs af lejere. Da URL-adressen er ugyldig i destinationslejer, skal du fjerne og genoprette Teams møder.

**Overføres indholdet i Teams chatmappen på tværs af lejere?**

Nej, indholdet i den Teams chatmappe overføres ikke på tværs af lejere.

**Hvordan kan jeg se flytninger på tværs af lejere, ikke mine onboarding- og off-boarding-flytninger?**

Brug parameteren _Flags_ . Her er et eksempel.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

**Kan du angive eksempelscripts til kopiering af attributter, der bruges i test?**

> [!NOTE]
> EKSEMPEL – SOM DET ER, GARANTERER INGEN GARANTI Dette script forudsætter en forbindelse til både kildepostkassen (for at hente kildeværdier) og destinationen Active Directory i det lokale miljø Domænetjenester (for at stemple ADUser-objektet). Hvis kilde har aktiveret procesførelse eller gendannelse af et enkelt element, skal du angive dette på destinationskontoen.  Dette vil øge destinationskontoens dumpsterstørrelse til 100 GB.

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
   Start-ADSyncSyncCycle
   ```

**Hvordan får vi adgang til Outlook den 1. dag, når brugspostkassen er flyttet?**

Da kun én lejer kan eje et domæne, knyttes den tidligere primære SMTP-adresse ikke til brugeren i destinationslejeren, når flytningen af postkassen er fuldført. kun de domæner, der er knyttet til den nye lejer. Outlook bruger det nye UPN til at godkende til tjenesten, og den Outlook profil forventer at finde de ældre primære SMTPAddress, så de stemmer overens med postkassen i destinationssystemet. Da den ældre adresse ikke findes i destinationssystemet, opretter Outlook-profilen ikke forbindelse for at finde den nytilflyttede postkasse.

Til denne indledende installation skal brugerne genopbygge deres profil med deres nye UPN, primære SMTP-adresse og resynkront OST-indhold.

> [!NOTE]
> Planlæg i overensstemmelse hermed, efterhånden som du batcher dine brugere til fuldførelse. Du skal tage højde for netværksudnyttelse og -kapacitet, når der oprettes Outlook klientprofiler, og efterfølgende OST- og OAB-filer downloades til klienter.

**Hvilke Exchange RBAC-roller skal jeg være medlem af for at konfigurere eller fuldføre en flytning på tværs af lejere?**

Der er en matrix af roller, der er baseret på antagelse af delegerede opgaver, når du udfører flytning af en postkasse. Der kræves i øjeblikket to roller:

- Den første rolle er til en engangskonfigurationsopgave, der etablerer godkendelsen af flytning af indhold til eller fra din lejer-/organisationsgrænse. Da flytning af data uden for din organisations kontrol er en vigtig bekymring for alle virksomheder, valgte vi den højeste tildelte rolle som organisationsadministrator (OrgAdmin). Denne rolle skal ændre eller konfigurere et nyt OrganizationRelationship, der definerer -MailboxMoveCapability med den eksterne organisation. Det er kun OrgAdmin, der kan ændre indstillingen MailboxMoveCapability, mens andre attributter i OrganizationRelationship kan administreres af administratoren for deling i organisationsnetværket.

- Rollen for udførelse af de faktiske flyttekommandoer kan delegeres til en funktion på lavere niveau. Rollen flyt postkasser tildeles til muligheden for at flytte postkasser ind eller ud af organisationen.

**Hvordan målretter vi mod, hvilken SMTP-adresse der er valgt for targetAddress (TargetDeliveryDomain) på den konverterede postkasse (til MailUser-konvertering)?**

Exchange postkassen flyttes ved hjælp af FRU-håndværket targetAddress i den oprindelige kildepostkasse, når der konverteres til en MailUser ved at matche en mailadresse (proxyAddress) på destinationsobjektet. Processen tager værdien -TargetDeliveryDomain, der overføres til flyttekommandoen, og kontrollerer derefter, om der er en tilsvarende proxy for det pågældende domæne på destinationssiden. Når vi finder et match, bruges den tilsvarende proxyAddress til at angive ExternalEmailAddress (targetAddress) på det konverterede postkasseobjekt (nu MailUser).

**Hvordan overføres postkassetilladelser?**

Postkassetilladelser omfatter Send på vegne af og Postkasseadgang:

- Send på vegne af (AD:publicDelegates) gemmer DN'et for modtagere med adgang til en brugers postkasse som stedfortræder. Denne værdi er gemt i Active Directory og flyttes i øjeblikket ikke som en del af postkasseovergangen. Hvis der er angivet offentligeDelegates i kildepostkassen, skal du restampere de offentligeDelegates på målpostkassen, når meu-konverteringen til postkassen er fuldført i destinationsmiljøet ved at køre `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`.

- Postkassetilladelser, der er gemt i postkassen, flyttes sammen med postkassen, når både sikkerhedskontoen og stedfortræderen flyttes til destinationssystemet. Brugerens TestUser_7 tildeles f.eks. FullAccess til den postkasse, TestUser_8 i lejerens SourceCompany.onmicrosoft.com. Når flytningen af postkassen er fuldført til TargetCompany.onmicrosoft.com, oprettes de samme tilladelser i destinationsmappen. Eksempler på brug af *Get-MailboxPermission* for TestUser_7 i både kilde- og destinationslejere er vist nedenfor. Exchange cmdlet'er har en præfiks med kilde og destination i overensstemmelse hermed.

Her er et eksempel på outputtet af tilladelsen til postkassen, før der flyttes.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

Her er et eksempel på outputtet fra tilladelsen til postkassen efter flytningen.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> Tilladelser for postkasser og kalendere på tværs af lejere understøttes IKKE. Du skal organisere principaler og stedfortrædere i bundtede flyttebatch, så disse forbundne postkasser overføres samtidig fra kildelejer.

**Hvilken X500-proxy skal føjes til destinationens MailUser-proxyadresser for at aktivere overførsel?**

Overflytningen af postkassen på tværs af lejere kræver, at værdien LegacyExchangeDN for kildepostkasseobjektet stemples som en x500-mailadresse på destinationens MailUser-objekt.

Eksempel:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> Ud over denne X500-proxy skal du kopiere alle X500-proxyer fra postkassen i kilden til postkassen i destinationen.

**Kan kilde- og destinationslejer anvende det samme domænenavn?**

Nej. Domænenavnene for kilde- og destinationslejer skal være entydige. Et kildedomæne for contoso.com og destinationsdomænet for fourthcoffee.com.

**Vil delte postkasser blive flyttet og stadig fungere?**

Ja, men vi beholder kun lagertilladelserne som beskrevet i disse artikler:

- [Microsoft Docs | Administrer tilladelser for modtagere i Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [Microsoft Support | Sådan tildeler du Exchange og Outlook postkassetilladelser i Office 365 dedikeret](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**Har du nogen anbefalinger til batches?**

Må ikke overskride 2000 postkasser pr. batch. Vi anbefaler på det kraftigste, at du indsender batches to uger før cut-over-datoen, da der ikke er nogen indvirkning på slutbrugerne under synkroniseringen. Hvis du har brug for vejledning til postkassemængder på over 50.000, kan du kontakte distributionslisten for teknisk feedback på crosstenantmigrationpreview@service.microsoft.com.

**Hvad gør jeg, hvis jeg bruger tjenestekryptering med kundenøgle?**

Postkassen dekrypteres, før den flyttes. Sørg for, at kundenøglen er konfigureret i destinationslejer, hvis den stadig er påkrævet. Se [her](/microsoft-365/compliance/customer-key-overview) for at få flere oplysninger.

**Hvad er den anslåede overførselstid?**

For at hjælpe dig med at planlægge din migrering viser den tabel, der vises [her](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) , retningslinjerne for, hvornår du kan forvente, at massepostkasseoverførslen eller individuelle migreringer fuldføres. Disse estimater er baseret på en dataanalyse af tidligere kundemigreringer. Da hvert miljø er unikt, kan den nøjagtige migreringshastighed variere.

Husk, at denne funktion i øjeblikket er tilgængelig som prøveversion og SLA'en, og at eventuelle relevante tjenesteniveauer ikke gælder for problemer med ydeevnen eller tilgængeligheden under prøveversionsstatussen for denne funktion.

**Beskyttelse af dokumenter i kildelejer, der kan forbruges af brugere i destinationslejer.**

Overførsel på tværs af lejere overfører kun postkassedata og intet andet. Der er flere andre muligheder, som er dokumenteret i følgende blogindlæg, som kan hjælpe: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

**Kan jeg have de samme mærkater i destinationslejer, som du havde i kildelejer, enten som det eneste sæt mærkater eller et ekstra sæt mærkater for de migrerede brugere, afhængigt af justeringen mellem organisationerne.**

Da overflytninger på tværs af lejere ikke eksporterer mærkater, og det er ikke muligt at dele mærkater mellem lejere, kan du kun opnå dette ved at genskabe mærkaterne i destinationslejeren.

**Støtter du flytning af Microsoft 365-grupper?**

I øjeblikket understøtter overførselsfunktionen for postkasser på tværs af lejere ikke migrering af Microsoft 365-grupper.

**Kan en kildelejeradministrator udføre en eDiscovery-søgning mod en postkasse, når postkassen er blevet overført til den nye/destinationslejer?**

Nej, efter overførsel af en postkasse på tværs af lejere fungerer eDiscovery mod den migrerede brugers postkasse i kilden ikke. Det skyldes, at der ikke længere er en postkasse i kilden, der kan søges efter, da postkassen er blevet overført til destinationslejer og nu tilhører destinationslejer. eDiscovery, postpostkasseoverførslen kan kun udføres i destinationslejer (hvor postkassen findes nu). Hvis en kopi af kildepostkassen skal bevares i kildelejer efter migreringen, kan administratoren i kilden kopiere indholdet til en alternativ postkasse før migrering for fremtidige eDiscovery-handlinger mod dataene.

## <a name="known-issues"></a>Kendte problemer

- **Problem: Funktionaliteten efter overførsel Teams i kildelejer er begrænset.** Når postkassen er overført til destinationslejer, har Teams i kildelejer ikke længere adgang til brugerens postkasse. Så hvis en bruger logger på Teams med kildelejeroplysningerne, vil der være tab af funktionalitet, f.eks. manglende evne til at opdatere dit profilbillede, ingen kalenderprogram og manglende evne til at søge efter og deltage i offentlige teams.

- **Problem: Automatisk udvidede arkiver kan ikke overføres.** Overførselsfunktionen på tværs af lejere understøtter overflytninger af den primære postkasse og arkivpostkassen for en bestemt bruger. Hvis brugeren i kilden imidlertid har et automatisk udvidet arkiv – hvilket betyder, at der er mere end én arkivpostkasse, kan funktionen ikke overføre de ekstra arkiver og bør mislykkes.

- **Problem: Cloud MailUsers med ikke-ejet smtp-proxyAddress blokerer FRU flytter baggrund.** Når du opretter MailUser-objekter for destinationslejer, skal du sikre, at alle SMTP-proxyadresser tilhører destinationslejerorganisationen. Hvis der findes en SMTP-proxyAdresse på destinationsmailbrugeren, der ikke tilhører den lokale lejer, forhindres konverteringen af MailUser til Postkasse. Dette skyldes vores forsikring om, at postkasseobjekter kun kan sende mail fra domæner, som lejeren er autoritativ for (domæner, som lejeren har gjort krav på):

  - Når du synkroniserer brugere fra det lokale miljø ved hjælp af Azure AD Forbind, klargør du MailUser-objekter i det lokale miljø med ExternalEmailAddress, der peger på kildelejeren, hvor postkassen findes (LaraN@contoso.onmicrosoft.com), og du stempler PrimarySMTPAddress som et domæne, der er placeret i destinationslejeren (Lara.Newton@northwind.com). Disse værdier synkroniseres ned til lejeren, og en passende mailbruger klargøres og klar til overførsel. Der vises et eksempelobjekt her.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > Den _contoso.onmicrosoft.com_ adresse findes _ikke_ i matrixen EmailAddresses/proxyAddresses.

- **Problem: MailUser-objekter med "eksterne" primære SMTP-adresser ændres/nulstilles til "interne" virksomhedsdomæner, der er gjort krav på**

  MailUser-objekter er markørerne til ikke-lokale postkasser. I tilfælde af migrering af postkasser på tværs af lejere bruger vi MailUser-objekter til at repræsentere enten kildepostkassen (fra målorganisationens perspektiv) eller destinationspostkassen (fra kildeorganisationens perspektiv). MailUsers har en ExternalEmailAddress (targetAddress), der peger på smtp-adressen på den faktiske postkasse (ProxyTest@fabrikam.onmicrosoft.com) og den primæreSMTP-adresse, der repræsenterer den viste SMTP-adresse for postkassebrugeren i mappen. Nogle organisationer vælger at vise den primære SMTP-adresse som en ekstern SMTP-adresse, ikke som en adresse, der ejes/bekræftes af den lokale lejer (f.eks. fabrikam.com i stedet for som contoso.com).  Men når et Exchange serviceplanobjekt er anvendt på MailUser via licenshandlinger, ændres den primære SMTP-adresse, så den vises som et domæne, der er bekræftet af den lokale organisation (contoso.com). Der er to mulige årsager:

  - Når en Exchange serviceplan anvendes på en MailUser, begynder Azure AD processen at gennemtvinge proxy-rensning for at sikre, at den lokale organisation ikke kan sende mails ud, spoof eller mail fra en anden lejer. Alle SMTP-adresser på et modtagerobjekt med disse tjenesteplaner fjernes, hvis adressen ikke bekræftes af den lokale organisation. Som det er tilfældet i eksemplet, bekræftes det Fabikam.com domæne IKKE af den contoso.onmicrosoft.com lejer, så rensningen fjerner det fabrikam.com domæne. Hvis du vil bevare disse eksterne domæner på MailUser, enten før migreringen eller efter migreringen, skal du ændre dine overførselsprocesser for at fjerne licenser, når flytningen er fuldført, eller før flytningen for at sikre, at brugerne har anvendt den forventede eksterne branding. Du skal sikre, at postkasseobjektet er korrekt licenseret til ikke at påvirke posttjenesten.
  - Her vises et eksempelscript til fjernelse af tjenesteplaner på en MailUser i den contoso.onmicrosoft.com lejer.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTELLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION"
    Set-MsolUserLicense -UserPrincipalName ProxyTest@contoso.com LicenseOptions $lo
    ```

       Resultaterne i det sæt ServicePlans, der er tildelt, vises her.

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

    Brugerens PrimarySMTPAddress bliver ikke længere renset. Det fabrikam.com domæne ejes ikke af den contoso.onmicrosoft.com lejer og bevares som den primære SMTP-adresse, der vises i mappen.

    Her er et eksempel.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - Når msExchRemoteRecipientType er angivet til 8 (DeprovisionMailbox) for mailbrugere i det lokale miljø, der er migreret til destinationslejeren, fjerner proxy-scrubbing-logikken i Azure ikke-ejede domæner og nulstiller den primæreSMTP til et ejet domæne. Ved at rydde msExchRemoteRecipientType i MailUser i det lokale miljø gælder proxy-scrub-logikken ikke længere.

      Nedenfor er det fulde sæt af aktuelle serviceplaner, der omfatter Exchange Online.

      | Navn                                             |
      | ------------------------------------------------ |
      | eDiscovery(Premium) Storage (500 GB)             |
      | Kundelockbox                                 |
      | Forebyggelse af datatab                             |
      | Exchange Enterprise CAL Services (EOP, DLP)      |
      | Exchange Essentials                              |
      | Exchange Foundation                              |
      | Exchange Online (P1)                             |
      | Exchange Online (plan 1)                         |
      | Exchange Online (plan 2)                         |
      | Exchange Online-arkivering til Exchange Online    |
      | Exchange Online-arkivering til Exchange Server    |
      | Exchange Online tilføjelsesprogrammet Inaktiv bruger             |
      | Exchange Online-kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online Plan 1                           |
      | Exchange Online POP                              |
      | Exchange Online Protection                       |
      | Informationsbarrierer                             |
      | Information Protection til Office 365 - Premium  |
      | Information Protection til Office 365 – Standard |
      | Insights af MyAnalytics                          |
      | Microsoft 365 Avanceret overvågning                  |
      | Microsoft Bookings                               |
      | Microsoft Business Center                        |
      | Microsoft MyAnalytics (fuld)                     |
      | Office 365 eDiscovery (Premium)                   |
      | Microsoft Defender for Office 365 (plan 1)       |
      | Microsoft Defender for Office 365 (plan 2)       |
      | Office 365 privilegeret adgangsstyring          |
      | Premium kryptering i Office 365                 |
