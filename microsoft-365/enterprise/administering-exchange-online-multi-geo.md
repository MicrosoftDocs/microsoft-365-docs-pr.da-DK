---
title: Administration Exchange Online postkasser i et multi-geo-miljø
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.localizationpriority: medium
description: Lær at administrere Exchange Online indstillingerne for multi-geo i dit Microsoft 365-miljø med PowerShell.
ms.openlocfilehash: 2e4be2fd506f89579866c61bbf4a8a41aadc0d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590534"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration Exchange Online postkasser i et multi-geo-miljø

Exchange Online skal PowerShell vise og konfigurere multi geo-egenskaber i dit Microsoft 365 miljø. Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Du skal bruge [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 eller nyere i v1.x for at se **egenskaben PreferredDataLocation** for brugerobjekter. Brugerobjekter, der synkroniseres via AAD Forbind til AAD, kan ikke få deres **PreferredDataLocation-værdi** direkte ændret via AAD PowerShell. Brugerobjekter, der kun findes i skyen, kan ændres via AAD PowerShell. Hvis du vil oprette forbindelse til Azure AD PowerShell, [skal Forbind til PowerShell](connect-to-microsoft-365-powershell.md).

I Exchange Online med multi-geo-miljøer behøver du ikke at udføre nogen manuelle trin for at føje geos til din lejer. Når du har modtaget indlægget i Meddelelsescenter, hvor der står, at multi-geo er klar til Exchange Online, vil alle tilgængelige geos være klar og konfigureret til brug.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Forbind direkte til en geoplacering ved hjælp af Exchange Online PowerShell

Typisk vil Exchange Online PowerShell oprette forbindelse til den centrale geoplacering. Men du kan også oprette direkte forbindelse til satellit geoplaceringer. På grund af forbedringer af ydeevnen anbefaler vi, at du opretter forbindelse direkte til satellit-geoplaceringen, når du kun administrerer brugere på den pågældende placering.

Kravene til installation og brug af EXO V2-modulet er beskrevet i [Installér og vedligehold EXO V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

For at Exchange Online forbindelse Exchange Online PowerShell til en bestemt geoplacering er *ConnectionUri-parameteren* anderledes end den almindelige forbindelsesvejledning. Resten af kommandoerne og værdierne er de samme.

Specifikt skal du føje værdien til `?email=<emailaddress>` slutningen af _ConnectionUri-værdien_ . `<emailaddress>` er mailadressen til enhver **postkasse** i mål-geo-placeringen. Dine tilladelser til den pågældende postkasse eller relationen til dine legitimationsoplysninger er ikke en faktor; mailadressen fortæller blot Exchange Online PowerShell, hvor der skal oprettes forbindelse.

Microsoft 365 eller Microsoft 365 GCC kunder behøver typisk ikke at bruge _ConnectionUri-parameteren_ til at oprette forbindelse til Exchange Online PowerShell. Men hvis du vil oprette forbindelse til en bestemt geoplacering, skal du bruge _ConnectionUri-parameteren_ , så du kan `?email=<emailaddress>` bruge den i værdien.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Forbind en geoplacering i Exchange Online PowerShell

Følgende forbindelsesinstruktioner fungerer for konti, der er eller ikke er konfigureret til multifaktorgodkendelse (MFA).

1. I et Windows PowerShell-vindue skal du indlæse EXO V2-modulet ved at køre følgende kommando:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. I følgende eksempel er admin@contoso.onmicrosoft.com administratorkontoen, og mål-geoplaceringen er det sted, olga@contoso.onmicrosoft.com er placeret.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Angiv adgangskoden til den admin@contoso.onmicrosoft.com i den meddelelse, der vises. Hvis kontoen er konfigureret til MFA, skal du også angive sikkerhedskoden.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Få vist de tilgængelige geoplaceringer, der er konfigureret i din Exchange Online organisation

For at se listen over konfigurerede geoplaceringer i Microsoft 365 Multi-Geo skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Få vist den centrale geoplacering for din Exchange Online organisation

For at få vist din lejers centrale geoplacering skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Find en postkasses geografiske placering

**Get-Mailbox** cmdlet i Exchange Online PowerShell viser følgende multi-geo-relaterede egenskaber for postkasser:

- **Database**: De første 3 bogstaver i databasenavnet svarer til geokoden, der fortæller dig, hvor postkassen er placeret i øjeblikket. For Onlinearkivpostkasser **skal egenskaben ArchiveDatabase** anvendes.

- **MailboxRegion**: Angiver den geoplaceringskode, der blev angivet af administratoren (synkroniseret fra **PreferredDataLocation** i Azure AD).

- **MailboxRegionLastUpdateTime**: Angiver, hvornår postkasseområde sidst blev opdateret (enten automatisk eller manuelt).

Hvis du vil se disse egenskaber for en postkasse, skal du bruge følgende syntaks:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Hvis du f.eks. vil se geoplaceringsoplysningerne for chris@contoso.onmicrosoft.com, skal du køre følgende kommando:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Outputtet for kommandoen ser sådan ud:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Hvis geoplaceringskoden i databasenavnet ikke stemmer overens med værdien **MailboxRegion**, sættes postkassen automatisk i en kø og flyttes til den geoplacering, der er angivet af værdien **MailboxRegion** (Exchange Online søger efter en uoverensstemmelse mellem disse egenskabsværdier).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Flyt en eksisterende postkasse, der kun findes i skyen, til en bestemt geoplacering

En bruger, der kun er skybaseret, er en bruger, der ikke er synkroniseret med lejeren via AAD Forbind. Denne bruger blev oprettet direkte i Azure AD. Brug cmdlet'erne **Get-MsolUser** og **Set-MsolUser** i Azure AD-modulet til Windows PowerShell til at få vist eller angive den geoplacering, hvor en brugers postkasse, der kun findes i skyen, skal gemmes.

For at få vist **værdien PreferredDataLocation** for en bruger skal du bruge denne syntaks i Azure AD PowerShell:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Hvis du f.eks. **vil se værdien PreferredDataLocation** for michelle@contoso.onmicrosoft.com, skal du køre følgende kommando:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Hvis du vil ændre **værdien PreferredDataLocation** for et brugerobjekt, der kun findes i skyen, skal du bruge følgende syntaks i Azure AD PowerShell:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Hvis du f.eks. vil **angive værdien PreferredDataLocation** til DEN Europæiske Union (EUR)-geo for michelle@contoso.onmicrosoft.com, skal du køre følgende kommando:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Som nævnt tidligere kan du ikke bruge denne procedure til synkroniserede brugerobjekter fra Active Directory i det lokale miljø. Du skal ændre værdien **PreferredDataLocation** i Active Directory og synkronisere den ved hjælp AAD Forbind. Du kan finde flere oplysninger [Azure Active Directory Forbind synkronisering: Konfigurer foretrukken dataplacering for Microsoft 365 ressourcer](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Hvor lang tid det tager at flytte en postkasse til en ny geoplacering afhænger af flere faktorer:
>
>   - Postkassens størrelse og type.
>   - Antallet af postkasser, der flyttes.
>   - Tilgængeligheden af flytteressourcer.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Flyt en inaktiv postkasse til et bestemt geo

Du kan ikke flytte inaktive postkasser, der bevares af hensyn til overholdelse af regler (f.eks. postkasser i retslig venteposition) ved at ændre værdien for **PreferredDataLocation** . Hvis du vil flytte en inaktiv postkasse til et andet geografisk område, skal du gøre følgende:

1. Gendan den inaktive postkasse. Du kan finde en vejledning under [Gendanne en inaktiv postkasse](../compliance/recover-an-inactive-mailbox.md).

2. Undgå, at den \<MailboxIdentity\> administrerede mappeassistent behandler den gendannede postkasse ved at erstatte med navn, alias, konto eller mailadresse på postkassen og køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Tildel **en Exchange Online Plan 2-licens** til den gendannede postkasse. Dette trin er påkrævet for at placere postkassen i retslig venteposition igen. Du kan finde en vejledning [under Tildel licenser til brugere](../admin/manage/assign-licenses-to-users.md).

4. Konfigurer værdien **PreferredDataLocation** på postkassen som beskrevet i forrige afsnit.

5. Når du har bekræftet, at postkassen er flyttet til den nye geoplacering, skal du placere den gendannede postkasse tilbage i Retslig venteposition. Du kan finde en vejledning under [Placere en postkasse i retslig venteposition](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Når du har bekræftet, at retslig venteposition er på plads, \<MailboxIdentity\> skal du give den administrerede mappeassistent tilladelse til at behandle postkassen igen ved at erstatte med navn, alias, konto eller mailadresse på postkassen og køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Gør postkassen inaktiv igen ved at fjerne den brugerkonto, der er knyttet til postkassen. Du kan finde en vejledning [under Slet en bruger fra organisationen](../admin/add-users/delete-a-user.md). Dette trin frigiver også Exchange Online Plan 2-licens til andre formål.

**Bemærk**! Når du flytter en inaktiv postkasse til en anden geoplacering, kan det påvirke resultaterne af indholdssøgningen eller muligheden for at søge i postkassen fra den tidligere geoplacering. Få mere at vide under [Søgning og eksport af indhold i Multi-Geo-miljøer](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Opret nye postkasser i skyen på en bestemt geoplacering

Hvis du vil oprette en ny postkasse i en bestemt geoplacering, skal du gøre et af følgende:

- Konfigurer værdien **PreferredDataLocation** som beskrevet i forrige Flyt en eksisterende postkasse, der kun findes i skyen, til en  bestemt [geoplaceringssektion](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location), før du opretter postkassen Exchange Online. Konfigurer f.eks. **værdien PreferredDataLocation** på en bruger, før du tildeler en licens.

- Tildel en licens på samme tid, som du angiver **værdien PreferredDataLocation** .

Hvis du vil oprette en ny licens kun i skyen (ikke AAD Forbind synkroniseret) på en bestemt geoplacering, skal du bruge følgende syntaks i Azure AD PowerShell:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

I dette eksempel oprettes en ny brugerkonto til Elizabeth Brunner med følgende værdier:

- Brugerens hovednavn: ebrunner@contoso.onmicrosoft.com
- Fornavn: Elizabeth
- Efternavn: Brunner
- Visningsnavn: Elizabeth Brunner
- Adgangskode: tilfældigt genereret og vist i resultaterne af kommandoen (fordi vi ikke bruger *parameteren* Adgangskode)
- Licens: `contoso:ENTERPRISEPREMIUM` (E5)
- Placering: Australien (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Hvis du vil have mere at vide om at oprette nye brugerkonti og finde LicenseAssignment-værdier i Azure AD PowerShell, skal du se Opret brugerkonti med [PowerShell](create-user-accounts-with-microsoft-365-powershell.md) og Se licenser og tjenester [med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Hvis du bruger Exchange Online PowerShell til at aktivere en postkasse og har brug for, at postkassen oprettes direkte i den geoplacering, der er angivet i **PreferredDataLocation**, skal du bruge en Exchange Online-cmdlet, f.eks. **Enable-Mailbox** eller **New-Mailbox**, direkte mod skytjenesten. Hvis du bruger **Enable-RemoteMailbox-cmdlet'en** i en lokal Exchange PowerShell, oprettes postkassen på den centrale geoplacering.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Onboard eksisterende lokale postkasser i et bestemt geografisk sted

Du kan bruge standard onboardingværktøjer og processer til at overføre en postkasse fra en lokal Exchange-organisation til Exchange Online, herunder overførselsdashboardet i [EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) og [New-MigrationBatch-cmdlet'en](/powershell/module/exchange/new-migrationbatch) i Exchange Online PowerShell.

Det første trin er at bekræfte, at der findes et brugerobjekt for hver postkasse, der skal onboardes, og bekræfte, at den korrekte **preferredDataLocation-værdi** er konfigureret i Azure AD. Onboarding-værktøjerne respekterer **værdien PreferredDataLocation** og overfører postkasserne direkte til den angivne geoplacering.

Eller du kan bruge følgende trin til at onboarde postkasser direkte i en bestemt geoplacering ved hjælp af [New-MoveRequest-cmdlet'en](/powershell/module/exchange/new-moverequest) Exchange Online PowerShell.

1. Bekræft, at brugerobjektet findes for hver postkasse, der skal onboardes, og at **PreferredDataLocation** er indstillet til den ønskede værdi i Azure AD. Værdien af **PreferredDataLocation synkroniseres** med attributten **MailboxRegion** for det tilsvarende mailbrugerobjekt Exchange Online.

2. Forbind direkte til den specifikke satellits geoplacering ved hjælp af forbindelsesinstruktionerne fra tidligere i dette emne.

3. I Exchange Online PowerShell skal du gemme de lokale administratorlegitimationsoplysninger, der bruges til at udføre en postkasseoverførsel i en variabel ved at køre følgende kommando:

   ```powershell
   $RC = Get-Credential
   ```

4. I Exchange Online PowerShell skal du oprette en **ny New-MoveRequest**, der ligner følgende eksempel:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Gentag trin 4 for hver postkasse, du skal overføre fra lokalt Exchange til den satellit geoplacering, du aktuelt har forbindelse til.

6. Hvis du skal overføre flere postkasser til forskellige satellit geografiske placeringer, skal du gentage trin 2 til 4 for hver bestemt placering.

## <a name="multi-geo-reporting"></a>Multi-geo reporting

**Rapporter over multi-geoanvendelse** i Microsoft 365 Administration viser brugerens optælling efter geoplacering. Rapporten viser brugerfordelingen for den aktuelle måned og indeholder historiske data for de seneste 6 måneder.

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)