---
title: Administration af Exchange Online postkasser i et multi-geo-miljø
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
description: Få mere at vide om, hvordan du administrerer Exchange Online multi-geo-indstillinger i dit Microsoft 365 miljø med PowerShell.
ms.openlocfilehash: 4b0b02fa9ea974784ec93efe83520faed5fd05bd
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130861"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administration af Exchange Online postkasser i et multi-geo-miljø

Exchange Online PowerShell er påkrævet for at få vist og konfigurere multi-geo-egenskaber i dit Microsoft 365 miljø. Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Du skal bruge [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 eller nyere i v1.x for at se egenskaben **PreferredDataLocation** for brugerobjekter. Brugerobjekter, der synkroniseres via AAD Forbind til AAD kan ikke have deres **PreferredDataLocation-værdi** ændret direkte via AAD PowerShell. Brugerobjekter, der kun er i cloudmiljøet, kan ændres via AAD PowerShell. Hvis du vil oprette forbindelse til Azure AD PowerShell, [skal du se Forbind til PowerShell](connect-to-microsoft-365-powershell.md).

I Exchange Online multi-geo-miljøer behøver du ikke at udføre manuelle trin for at føje geos til din lejer. Når du har modtaget Meddelelsescenter-indlægget, hvor der står, at multi-geo er klar til Exchange Online, er alle tilgængelige geos klar og konfigureret, så du kan bruge dem.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Forbind direkte til en geografisk placering ved hjælp af Exchange Online PowerShell

Exchange Online PowerShell opretter typisk forbindelse til den centrale geografiske placering. Men du kan også oprette forbindelse direkte til satellitgeoplaceringer. På grund af forbedringer af ydeevnen anbefaler vi, at du opretter direkte forbindelse til satellitplaceringen, når du kun administrerer brugere på den pågældende placering.

Kravene til installation og brug af EXO V2-modulet er beskrevet i [Installér og vedligehold EXO V2-modulet](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

Hvis du vil oprette forbindelse Exchange Online PowerShell til en bestemt geografisk placering, er *ConnectionUri-parameteren* anderledes end de almindelige forbindelsesinstruktioner. Resten af kommandoerne og værdierne er de samme.

Du skal specifikt føje værdien `?email=<emailaddress>` til slutningen af _ConnectionUri-værdien_ . `<emailaddress>` er mailadressen på **en hvilken som helst** postkasse i mållokationen. Dine tilladelser til postkassen eller relationen til dine legitimationsoplysninger er ikke en faktor. Mailadressen fortæller blot Exchange Online PowerShell, hvor der skal oprettes forbindelse.

Microsoft 365 eller Microsoft 365 GCC kunder behøver normalt ikke at bruge _ConnectionUri-parameteren_ for at oprette forbindelse til Exchange Online PowerShell. Men hvis du vil oprette forbindelse til en bestemt geografisk placering, skal du bruge _ConnectionUri-parameteren_ , så du kan bruge `?email=<emailaddress>` i værdien.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Forbind til en geografisk placering i Exchange Online PowerShell

Følgende forbindelsesinstruktioner fungerer for konti, der er eller ikke er konfigureret til multifaktorgodkendelse .

1. I et Windows PowerShell vindue skal du indlæse EXO V2-modulet ved at køre følgende kommando:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. I følgende eksempel er admin@contoso.onmicrosoft.com administratorkontoen, og målplaceringen for den geografiske placering er det sted, hvor postkassen olga@contoso.onmicrosoft.com er placeret.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Angiv adgangskoden til admin@contoso.onmicrosoft.com i den prompt, der vises. Hvis kontoen er konfigureret til MFA, skal du også angive sikkerhedskoden.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Få vist de tilgængelige geografiske placeringer, der er konfigureret i din Exchange Online organisation

Hvis du vil se en liste over konfigurerede geografiske placeringer i Microsoft 365 Multi-Geo, skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Få vist den centrale geografiske placering for din Exchange Online organisation

Hvis du vil have vist din lejers centrale geografiske placering, skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Find den geografiske placering af en postkasse

**Cmdlet'en Get-Mailbox** i Exchange Online PowerShell viser følgende multi-geo-relaterede egenskaber i postkasser:

- **Database**: De første tre bogstaver i databasenavnet svarer til den geografiske kode, som fortæller dig, hvor postkassen er placeret i øjeblikket. I forbindelse med onlinearkivpostkasser skal egenskaben **ArchiveDatabase** bruges.

- **MailboxRegion**: Angiver den geoplaceringskode, der blev angivet af administratoren (synkroniseret fra **PreferredDataLocation** i Azure AD).

- **MailboxRegionLastUpdateTime**: Angiver, hvornår MailboxRegion senest blev opdateret (enten automatisk eller manuelt).

Hvis du vil se disse egenskaber for en postkasse, skal du bruge følgende syntaks:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Hvis du f.eks. vil se oplysningerne om den geografiske placering for postkassen chris@contoso.onmicrosoft.com, skal du køre følgende kommando:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Outputtet af kommandoen ser ud som følger:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Hvis den geografiske placeringskode i databasenavnet ikke svarer til værdien **for MailboxRegion**, placeres postkassen automatisk i en flyttekø og flyttes til den geoplacering, der er angivet af værdien **MailboxRegion** (Exchange Online søger efter en uoverensstemmelse mellem disse egenskabsværdier).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Flyt en eksisterende postkasse kun i skyen til en bestemt geografisk placering

En skybaseret bruger er en bruger, der ikke synkroniseres med lejeren via AAD Forbind. Denne bruger blev oprettet direkte i Azure AD. Brug Cmdlet'erne **Get-MsolUser** og **Set-MsolUser** i Azure AD modulet til at Windows PowerShell få vist eller angive den geografiske placering, hvor en brugers postkasse kun er skyen.

Hvis du vil have vist værdien **PreferredDataLocation** for en bruger, skal du bruge denne syntaks i Azure AD PowerShell:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Hvis du f.eks. vil se værdien **PreferredDataLocation** for brugeren michelle@contoso.onmicrosoft.com, skal du køre følgende kommando:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Hvis du vil ændre værdien **preferredDataLocation** for et brugerobjekt, der kun er i skyen, skal du bruge følgende syntaks i Azure AD PowerShell:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Kør f.eks. følgende kommando for at angive værdien **PreferredDataLocation** til den europæiske union (EUR) geo for brugerens michelle@contoso.onmicrosoft.com:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Som tidligere nævnt kan du ikke bruge denne procedure til synkroniserede brugerobjekter fra Active Directory i det lokale miljø. Du skal ændre værdien **PreferredDataLocation** i Active Directory og synkronisere den ved hjælp af AAD Forbind. Du kan få flere oplysninger [under Azure Active Directory Forbind synkronisering: Konfigurer foretrukken dataplacering for Microsoft 365 ressourcer](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Hvor lang tid det tager at flytte en postkasse til en ny geografisk placering, afhænger af flere faktorer:
>
>   - Postkassens størrelse og type.
>   - Antallet af postkasser, der flyttes.
>   - Tilgængeligheden af flytteressourcer.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Flyt en inaktiv postkasse til en bestemt geografisk placering

Du kan ikke flytte inaktive postkasser, der bevares af hensyn til overholdelse af angivne standarder (f.eks. postkasser i stridsposition) ved at ændre deres **PreferredDataLocation-værdi** . Hvis du vil flytte en inaktiv postkasse til et andet geografisk område, skal du gøre følgende:

1. Gendan den inaktive postkasse. Du kan finde instruktioner under [Gendan en inaktiv postkasse](../compliance/recover-an-inactive-mailbox.md).

2. Undgå, at Assistent for administrerede mapper behandler den gendannede postkasse ved at erstatte \<MailboxIdentity\> med postkassens navn, alias, konto eller mailadresse og køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Tildel en **Exchange Online Plan 2-licens** til den gendannede postkasse. Dette trin er påkrævet for at placere postkassen tilbage i procesførelsesventeposition. Du kan finde instruktioner under [Tildel licenser til brugere](../admin/manage/assign-licenses-to-users.md).

4. Konfigurer værdien **PreferredDataLocation** i postkassen som beskrevet i forrige afsnit.

5. Når du har bekræftet, at postkassen er flyttet til den nye geografiske placering, skal du placere den gendannede postkasse i procesventeposition igen. Du kan finde en vejledning under [Placer en postkasse i venteposition for procesførelse](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Når du har bekræftet, at procesførelsesventepositionen er på plads, skal du give Assistent for administrerede mapper tilladelse til at behandle postkassen igen ved at erstatte \<MailboxIdentity\> postkassens navn, alias, konto eller mailadresse og køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Gør postkassen inaktiv igen ved at fjerne den brugerkonto, der er knyttet til postkassen. Du kan finde instruktioner under [Slet en bruger fra din organisation](../admin/add-users/delete-a-user.md). Dette trin frigiver også Exchange Online Plan 2-licensen til andre formål.

**Bemærk**! Når du flytter en inaktiv postkasse til en anden geografisk placering, kan det påvirke søgeresultaterne for indhold eller muligheden for at søge i postkassen fra den tidligere geografiske placering. Du kan finde flere oplysninger under [Søgning efter og eksport af indhold i Multi-Geo-miljøer](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Opret nye cloudpostkasser på en bestemt geografisk placering

Hvis du vil oprette en ny postkasse på en bestemt geografisk placering, skal du gøre et af følgende:

- Konfigurer værdien **PreferredDataLocation** som beskrevet i forrige afsnit [Flyt en eksisterende postkasse kun i skyen til en bestemt geografisk placering,](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) *før* du opretter postkassen i Exchange Online. Konfigurer f.eks. værdien **PreferredDataLocation** for en bruger, før du tildeler en licens.

- Tildel en licens samtidig med, at du angiver værdien **PreferredDataLocation** .

Hvis du vil oprette en ny skybaseret bruger med licens (ikke AAD Forbind synkroniseret) på en bestemt geografisk placering, skal du bruge følgende syntaks i Azure AD PowerShell:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

I dette eksempel oprettes der en ny brugerkonto for Elizabeth Brunner med følgende værdier:

- Brugerens hovednavn: ebrunner@contoso.onmicrosoft.com
- Fornavn: Elizabeth
- Efternavn: Brunner
- Vist navn: Elizabeth Brunner
- Adgangskode: tilfældigt genereret og vist i resultaterne af kommandoen (fordi vi ikke bruger parameteren *Password* )
- Licens: `contoso:ENTERPRISEPREMIUM` (E5)
- Placering: Australien (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Du kan finde flere oplysninger om oprettelse af nye brugerkonti og søgning efter LicenseAssignment-værdier i Azure AD PowerShell under [Opret brugerkonti med PowerShell](create-user-accounts-with-microsoft-365-powershell.md) og [Få vist licenser og tjenester med PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Hvis du bruger Exchange Online PowerShell til at aktivere en postkasse og skal oprette postkassen direkte på den geografiske placering, der er angivet i **PreferredDataLocation**, skal du bruge en Exchange Online cmdlet, f.eks **. Aktivér postkasse** eller **Ny postkasse** direkte i forhold til cloudtjenesten. Hvis du bruger cmdlet'en **Enable-RemoteMailbox** i det lokale miljø Exchange PowerShell, oprettes postkassen på den centrale geografiske placering.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Onboarder eksisterende postkasser i det lokale miljø på en bestemt geografisk placering

Du kan bruge standard onboardingværktøjer og -processer til at overføre en postkasse fra en Exchange organisation i det lokale miljø for at Exchange Online, herunder [migreringsdashboardet i EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) og Cmdlet'en [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) i Exchange Online PowerShell.

Det første trin er at bekræfte, at der findes et brugerobjekt for hver postkasse, der skal onboardes, og kontrollere, at den korrekte **PreferredDataLocation-værdi** er konfigureret i Azure AD. Onboardingværktøjerne respekterer værdien **PreferredDataLocation** og overfører postkasserne direkte til den angivne geoplacering.

Du kan også bruge følgende trin til at onboarde postkasser direkte på en bestemt geografisk placering ved hjælp af [New-MoveRequest-cmdlet'en](/powershell/module/exchange/new-moverequest) i Exchange Online PowerShell.

1. Kontrollér, at brugerobjektet findes for hver postkasse, der skal onboardes, og at **PreferredDataLocation** er angivet til den ønskede værdi i Azure AD. Værdien af **PreferredDataLocation** synkroniseres med attributten **MailboxRegion** for det tilsvarende mailbrugerobjekt i Exchange Online.

2. Forbind direkte til den specifikke geo-satellitplacering ved hjælp af forbindelsesinstruktionerne tidligere i dette emne.

3. I Exchange Online PowerShell skal du gemme de lokale administratorlegitimationsoplysninger, der bruges til at udføre en migrering af en postkasse, i en variabel ved at køre følgende kommando:

   ```powershell
   $RC = Get-Credential
   ```

4. I Exchange Online PowerShell skal du oprette en ny **New-MoveRequest** svarende til følgende eksempel:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Gentag trin 4 for hver postkasse, du skal overføre fra Exchange i det lokale miljø til den satellitplacering, du i øjeblikket har forbindelse til.

6. Hvis du har brug for at overføre yderligere postkasser til forskellige geografiske satellitplaceringer, skal du gentage trin 2 til 4 for hver bestemt placering.

## <a name="multi-geo-reporting"></a>Multi-Geo-rapportering

> [!NOTE]
> Multi-Geo-rapporteringsfunktionen er i øjeblikket tilgængelig som prøveversion, er ikke tilgængelig i alle organisationer og kan ændres.

**Multi-Geo-forbrugsrapporter** i Microsoft 365 Administration viser antallet af brugere efter geografisk placering. Rapporten viser brugerdistributionen for den aktuelle måned og indeholder historiske data for de seneste 6 måneder.

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
