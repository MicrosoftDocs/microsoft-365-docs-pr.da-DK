---
title: Administrer kundenøgle
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Når du har konfigureret Kundenøgle, kan du få mere at vide om, hvordan du administrerer den ved at gendanne AKV-nøgler og administrere tilladelser samt oprette og tildele politikker for datakryptering.
ms.openlocfilehash: 08fae19a5f0f27ff530c734c46453f885ea9043e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015742"
---
# <a name="manage-customer-key"></a>Administrer kundenøgle

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har konfigureret kundenøgle, skal du oprette og tildele en eller flere politikker for datakryptering. Når du har tildelt dine dep'er, kan du administrere dine nøgler som beskrevet i denne artikel. Få mere at vide om Kundenøgle i de relaterede emner.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Opret en dep til brug med flere arbejdsbelastninger for alle lejerbrugere

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere kundenøglen. Du kan få flere oplysninger under [Konfigurer kundenøgle](customer-key-set-up.md). Du skal bruge de Key Vault URI'er, du fik under installationen, for at oprette programmet. Du kan finde flere oplysninger [under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Følg disse trin for at oprette en dep med flere arbejdsbelastninger:

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har tilladelser som global administrator eller overholdelsesadministrator i din organisation.

2. Hvis du vil oprette en forhindring af dataforbrug, skal du bruge cmdlet'en New-M365DataAtRestEncryptionPolicy.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Hvor:

   - *PolicyName* er det navn, du vil bruge til politikken. Navne må ikke indeholde mellemrum. Det kan f.eks. være Contoso_Global.

   - *KeyVaultURI1* er URI'en for den første nøgle i politikken. Det kunne f.eks. være <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* er URI'en for den anden nøgle i politikken. Det kunne f.eks. være <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Adskil de to URI'er med et komma og et mellemrum.

   - *Politikbeskrivelse* er en brugervenlig beskrivelse af politikken, der hjælper dig med at huske, hvad politikken er beregnet til. Du kan medtage mellemrum i beskrivelsen. For eksempel "Rodpolitik for flere arbejdsbelastninger for alle brugere i lejeren".

Eksempel:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Tildel politik for flere arbejdsbelastninger

Tildel forhindring af dataudløb ved hjælp af cmdlet'en Set-M365DataAtRestEncryptionPolicyAssignment. Når du har tildelt politikken, krypterer Microsoft 365 dataene med den nøgle, der er identificeret i forhindring af dataafklaring.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Hvor *PolicyName* er navnet på politikken. Det kan f.eks. være Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Opret en forhindring af dataforbrug til brug sammen med Exchange Online postkasser

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere Azure Key Vault. Du kan få flere oplysninger under [Konfigurer kundenøgle](customer-key-set-up.md). Du skal fuldføre disse trin i Exchange Online PowerShell.

En dep er knyttet til et sæt nøgler, der er gemt i Azure Key Vault. Du kan tildele en deaktiveringspostkasse i Microsoft 365. Microsoft 365 bruger derefter de nøgler, der er identificeret i politikken, til at kryptere postkassen. Du skal bruge de Key Vault URI'er, du fik under installationen, for at oprette programmet. Du kan finde flere oplysninger [under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Huske! Når du opretter en forhindring af dataafhænging, angiver du to nøgler i to forskellige Azure Key Vaults. Opret disse nøgler i to separate Azure-områder for at sikre georedundans.

Følg disse trin for at oprette en forhindring af dataforbrug, der skal bruges sammen med en postkasse:

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har globale administrator- eller Exchange Online administratortilladelser i din organisation.

2. Hvis du vil oprette en forhindring af dataforbrug, skal du bruge cmdlet'en New-DataEncryptionPolicy ved at skrive følgende kommando.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Hvor:

   - *PolicyName* er det navn, du vil bruge til politikken. Navne må ikke indeholde mellemrum. F.eks. USA_mailboxes.

   - *Politikbeskrivelse* er en brugervenlig beskrivelse af politikken, der hjælper dig med at huske, hvad politikken er beregnet til. Du kan medtage mellemrum i beskrivelsen. Det kan f.eks. være "Rodnøgle til postkasser i USA og dets områder".

   - *KeyVaultURI1* er URI'en for den første nøgle i politikken. Det kunne f.eks. være <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* er URI'en for den anden nøgle i politikken. Det kunne f.eks. være <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Adskil de to URI'er med et komma og et mellemrum.

   Eksempel:

   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-DataEncryptionPolicy](/powershell/module/exchange/new-dataencryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Tildel en deaktivering af data til en postkasse

Tildel programmet til en postkasse ved hjælp af cmdlet'en Set-Mailbox. Når du har tildelt politikken, kan Microsoft 365 kryptere postkassen med den nøgle, der er identificeret i programmet til forebyggelse af datadata.

```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Where *MailboxIdParameter* angiver en brugerpostkasse. Du kan få flere oplysninger om cmdlet'en Set-Mailbox i [Set-Mailbox](/powershell/module/exchange/set-mailbox).

I hybridmiljøer kan du tildele en forhindring af datatab til de lokale postkassedata, der synkroniseres med din Exchange Online lejer. Hvis du vil tildele en forhindringspostkasse til disse synkroniserede postkassedata, skal du bruge cmdlet'en Set-MailUser. Du kan få flere oplysninger om postkassedata i hybridmiljøet i [postkasser i det lokale miljø ved hjælp af Outlook til iOS og Android med hybrid moderne godkendelse](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Hvor *MailUserIdParameter* angiver en mailbruger (også kendt som en mailaktiveret bruger). Du kan få flere oplysninger om Set-MailUser cmdlet under [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Opret en deaktiveringsfil til brug sammen med SharePoint Online-, OneDrive for Business- og Teams-filer

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere Azure Key Vault. Du kan få flere oplysninger under [Konfigurer kundenøgle](customer-key-set-up.md).

Hvis du vil konfigurere kundenøglen til SharePoint Online, OneDrive for Business og Teams filer, skal du fuldføre disse trin i SharePoint Online PowerShell.

Du knytter en forhindring af dataforbindelse til et sæt nøgler, der er gemt i Azure Key Vault. Du anvender en forhindring af dataaf data på alle dine data på én geografisk placering, også kaldet et geografisk område. Hvis du bruger multi-geo-funktionen i Office 365, kan du oprette én DEP pr. geo med mulighed for at bruge forskellige nøgler pr. geo. Hvis du ikke bruger multi-geo, kan du oprette én forhindring af dataanvendelse i din organisation til brug sammen med SharePoint Online-, OneDrive for Business- og Teams-filer. Microsoft 365 bruger de nøgler, der er identificeret i forhindring af dataafklaring, til at kryptere dine data i det pågældende geografiske område. Du skal bruge de Key Vault URI'er, du fik under installationen, for at oprette programmet. Du kan finde flere oplysninger [under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Huske! Når du opretter en forhindring af dataafhænging, angiver du to nøgler i to forskellige Azure Key Vaults. Opret disse nøgler i to separate Azure-områder for at sikre georedundans.

Hvis du vil oprette en forhindring af datadata, skal du bruge SharePoint Online PowerShell.

1. Opret [forbindelse til SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har globale administratortilladelser i din organisation.

2. Kør Register-SPODataEncryptionPolicy-cmdlet'en på følgende måde i Microsoft Office SharePoint Online Management Shell:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Eksempel:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a'
   ```

   Når du registrerer forhindring af dataregistrering, starter krypteringen af dataene i det geografiske område. Kryptering kan tage noget tid. Du kan få flere oplysninger om brug af denne parameter under [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Få vist de DEP'er, du har oprettet for Exchange Online postkasser

Hvis du vil have vist en liste over alle de DEP'er, du har oprettet til postkasser, skal du bruge Get-DataEncryptionPolicy PowerShell-cmdlet'en.

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Hvis du vil returnere alle DEP'er i din organisation, skal du køre Get-DataEncryptionPolicy-cmdlet'en uden nogen parametre.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Du kan få flere oplysninger om Get-DataEncryptionPolicy cmdlet under [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Tildel en forhindring af datadata, før du overfører en postkasse til cloudmiljøet

Når du tildeler forhindring af dataoverførsel, krypterer Microsoft 365 indholdet af postkassen ved hjælp af den tildelte forhindring af dataoverførsel under overførslen. Denne proces er mere effektiv end overførsel af postkassen, tildeling af programmet til datalagring og derefter afventer kryptering, hvilket kan tage timer eller muligvis dage.

Hvis du vil tildele en dep til en postkasse, før du overfører den til Office 365, skal du køre Set-MailUser-cmdlet'en i Exchange Online PowerShell:

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør cmdlet'en Set-MailUser.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Hvor *GeneralMailboxOrMailUserIdParameter* angiver en postkasse, og *DataEncryptionPolicyIdParameter* er id'et for forhindring af dataoverførsel. Du kan få flere oplysninger om Set-MailUser cmdlet under [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Fastlæg den forhindring af dataafhænging, der er tildelt en postkasse

Brug cmdlet'en Get-MailboxStatistics til at bestemme, hvilken forhindringspakke der er tildelt til en postkasse. Cmdlet'en returnerer et entydigt id (GUID).

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Hvor *GeneralMailboxOrMailUserIdParameter* angiver en postkasse, og DataEncryptionPolicyID returnerer GUID for forhindring af dataoverførsel. Du kan få flere oplysninger om cmdlet'en Get-MailboxStatistics under [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).

2. Kør Get-DataEncryptionPolicy-cmdlet'en for at finde det brugervenlige navn på den forhindring af datakørsel, som postkassen er tildelt.

   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Hvor *GUID* er det GUID, der returneres af Get-MailboxStatistics-cmdlet'en i det forrige trin.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Kontrollér, at kundenøglen er færdig med krypteringen

Uanset om du har rullet en kundenøgle, tildelt en ny forhindringsliste eller migreret en postkasse, skal du følge trinnene i dette afsnit for at sikre, at krypteringen fuldføres.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Kontrollér, at krypteringen er fuldført for Exchange Online postkasser

Det kan tage noget tid at kryptere en postkasse. For første gang skal postkassen også flyttes helt fra én database til en anden, før tjenesten kan kryptere postkassen.

Brug cmdlet'en Get-MailboxStatistics til at bestemme, om en postkasse er krypteret.

```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

Egenskaben IsEncrypted returnerer værdien **true** , hvis postkassen krypteres, og værdien **false** , hvis postkassen ikke krypteres. Den tid, det tager at fuldføre postkasseflytninger, afhænger af antallet af postkasser, som du tildeler en deaktivering af programmet for første gang, og størrelsen af postkasserne. Hvis postkasserne ikke er blevet krypteret efter en uge fra det tidspunkt, du tildelte programmet, skal du kontakte Microsoft.

Cmdlet'en New-MoveRequest er ikke længere tilgængelig for flytning af lokale postkasser. Se [denne meddelelse](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) for at få flere oplysninger.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Kontrollér, at krypteringen er fuldført for SharePoint Online-, OneDrive for Business- og Teams-filer

Kontrollér krypteringsstatussen ved at køre Get-SPODataEncryptionPolicy-cmdlet'en på følgende måde:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Outputtet fra denne cmdlet indeholder:

- URI'en for den primære nøgle.

- URI'en for den sekundære nøgle.

- Krypteringsstatus for det geografiske område. Mulige tilstande omfatter:

  - **Uregistrerede:** Kryptering af kundenøgle er endnu ikke anvendt.

  - **Registrering:** Kryptering af kundenøgle er anvendt, og dine filer er ved at blive krypteret. Hvis nøglen til geo'et registreres, får du også vist oplysninger om, hvilken procentdel af websteder i det geografiske område der er fuldført, så du kan overvåge krypteringsstatus.

  - **Registreret:** Kryptering af kundenøgle er anvendt, og alle filer på alle websteder er krypteret.

  - **Rullende:** Et nøglekast er i gang. Hvis nøglen til geo'et ruller, får du også vist oplysninger om, hvilken procentdel af websteder der har fuldført nøglerullehandlingen, så du kan overvåge status.

- Det vil også output procentdelen af onboardede websteder.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Få oplysninger om DEP'er, du bruger med flere arbejdsbelastninger

Hvis du vil have oplysninger om alle de DEP'er, du har oprettet til brug med flere arbejdsbelastninger, skal du udføre disse trin:

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har tilladelser som global administrator eller overholdelsesadministrator i din organisation.

   - Kør denne kommando for at returnere listen over alle DEP'er med flere arbejdsbelastninger i organisationen.

     ```powershell
     Get-M365DataAtRestEncryptionPolicy
     ```

   - Hvis du vil returnere oplysninger om en bestemt forhindring af datakørsel, skal du køre denne kommando. I dette eksempel returneres detaljerede oplysninger om programmet til dataafsendelse med navnet "Contoso_Global".

     ```powershell
     Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Hent tildelingsoplysninger om dep-tildelinger med flere arbejdsbelastninger

Følg disse trin for at finde ud af, hvilken dep der i øjeblikket er tildelt din lejer.

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har tilladelser som global administrator eller overholdelsesadministrator i din organisation.

2. Skriv denne kommando.

   ```powershell
   Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Deaktiver en forhindring af databelastning med flere arbejdsbelastninger

Før du deaktiverer en dep med flere arbejdsbelastninger, skal du fjerne tildelingen af forhindring af datatab fra arbejdsbelastninger i din lejer. Hvis du vil deaktivere en forhindring af datamængde, der bruges sammen med flere arbejdsbelastninger, skal du udføre disse trin:

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har tilladelser som global administrator eller overholdelsesadministrator i din organisation.

2. Kør cmdlet'en Set-M365DataAtRestEncryptionPolicy.

   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Hvor *PolicyName* er navnet eller det entydige id for politikken. Det kan f.eks. være Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Gendan Azure Key Vault-nøgler

Før du udfører en gendannelse, skal du bruge de genoprettelsesfunktioner, der leveres af blød sletning. Alle nøgler, der bruges sammen med Kundenøgle, skal have blød sletning aktiveret. Blød sletning fungerer som en papirkurv og gør det muligt at gendanne i op til 90 dage, uden at det er nødvendigt at gendanne. Gendannelse bør kun være påkrævet under ekstreme eller usædvanlige omstændigheder, f.eks. hvis nøglen eller key vault går tabt. Hvis du skal gendanne en nøgle til brug sammen med kundenøglen, skal du i Azure PowerShell køre Restore-AzureKeyVaultKey-cmdlet'en på følgende måde:

```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Eksempel:

```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Hvis key vault allerede indeholder en nøgle med samme navn, mislykkes gendannelsen. Restore-AzKeyVaultKey gendanner alle nøgleversioner og alle metadata for nøglen, herunder nøglenavnet.

## <a name="manage-key-vault-permissions"></a>Administrer tilladelser til key vault

Der findes flere cmdlet'er, der giver dig mulighed for at få vist og om nødvendigt fjerne tilladelser til key vault. Du skal muligvis fjerne tilladelser, f.eks. når en medarbejder forlader teamet. For hver af disse opgaver skal du bruge Azure PowerShell. Du kan få flere oplysninger om Azure PowerShell under [Oversigt over Azure PowerShell](/powershell/azure/).

Kør cmdlet'en Get-AzKeyVault for at få vist key vault-tilladelser.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Eksempel:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Hvis du vil fjerne en administrators tilladelser, skal du køre cmdlet'en Remove-AzKeyVaultAccessPolicy:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Eksempel:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Gå tilbage fra kundenøgle til Microsoft-administrerede nøgler

Hvis du har brug for at vende tilbage til Microsoft-administrerede nøgler, kan du. Når du kommer ombord, krypteres dine data igen ved hjælp af standardkryptering, der understøttes af hver enkelt arbejdsbelastning. Exchange Online understøtter f.eks. standardkryptering ved hjælp af Microsoft-administrerede nøgler.

> [!IMPORTANT]
> Offboarding er ikke det samme som en datarensning. En datarensning sletter din organisations data permanent fra Microsoft 365, og det gør offboarding ikke. Du kan ikke udføre en datarensning for en politik for flere arbejdsbelastninger.

Hvis du beslutter ikke længere at bruge Kundenøgle til at tildele dep'er med flere arbejdsbelastninger, skal du kontakte Microsoft Support med en anmodning om at "offboard" fra Kundenøgle. Bed supportteamet om at sende en serviceanmodning til Microsoft Purview-kundenøgleteamet. Kontakt m365-ck@service.microsoft.com, hvis du har spørgsmål.

Hvis du ikke længere vil kryptere individuelle postkasser ved hjælp af DEP'er på postkasseniveau, kan du fjerne tildelingen af deP'er på postkasseniveau fra alle dine postkasser.

Hvis du vil fjerne tildelingen af deP'er til postkasser, skal du bruge PowerShell-cmdlet'en Set-Mailbox.

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør cmdlet'en Set-Mailbox.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $null
   ```

Når du kører denne cmdlet, ophæves tildelingen af den aktuelt tildelte forhindring af dataafgang, og postkassen krypteres igen ved hjælp af den DEP, der er knyttet til microsoft-administrerede standardnøgler. Du kan ikke fjerne tildelingen af den dep, der bruges af Microsoft-administrerede nøgler. Hvis du ikke vil bruge Microsoft-administrerede nøgler, kan du tildele en anden kundenøgle til postkassen.

> [!IMPORTANT]
> Gå tilbage fra kundenøgle til administrerede microsoft-nøgler understøttes ikke for filer af typen SharePoint Online, OneDrive for Business og Teams.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Tilbagekald dine nøgler, og start processen til fjernelse af data

Du styrer tilbagekaldelsen af alle rodnøgler, herunder tilgængelighedsnøglen. Customer Key giver dig kontrol over afslutningsplanlægningsaspektet af de lovmæssige krav til dig. Hvis du beslutter at tilbagekalde dine nøgler for at fjerne dine data og afslutte tjenesten, sletter tjenesten tilgængelighedsnøglen, når datarensningsprocessen er fuldført. Dette understøttes for kundenøgle-DEP'er, der er tildelt individuelle postkasser.

Microsoft 365 overvåger og validerer stien til datarensning. Du kan få flere oplysninger i SSAE 18 SOC 2-rapporten, der er tilgængelig på [Service Trust Portal](https://servicetrust.microsoft.com/). Derudover anbefaler Microsoft følgende dokumenter:

- [Vejledning til risikovurdering og overholdelse af angivne standarder for finansielle institutioner i Microsoft Cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Overvejelser i forbindelse med O365-afslutningsplanlægning](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Sletning af forhindring af dataafhænging med flere arbejdsbelastninger understøttes ikke for kundenøgle. Forhindring af datatab med flere arbejdsbelastninger bruges til at kryptere data på tværs af flere arbejdsbelastninger på tværs af alle lejerbrugere. Hvis du fjerner en sådan forhindring af data, vil det resultere i, at der ikke er adgang til data på tværs af flere arbejdsbelastninger. Hvis du beslutter dig for helt at afslutte Microsoft 365 tjenester, kan du forfølge stien til sletning af lejer i henhold til den dokumenterede proces. Se[, hvordan du sletter en lejer i Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Tilbagekald dine kundenøgler og tilgængelighedsnøglen for Exchange Online og Skype for Business

Når du starter stien til datarensning for Exchange Online og Skype for Business, angiver du en permanent anmodning om datarensning for en forhindring af data. Hvis du gør det, slettes krypterede data permanent i de postkasser, som den pågældende dep er tildelt til.

Da du kun kan køre PowerShell-cmdlet'en mod én forhindring af datakørsel ad gangen, kan du overveje at tildele en enkelt forhindring af datakørsel til alle dine postkasser, før du starter datarensningsstien.

> [!WARNING]
> Brug ikke stien til datarensning til at slette et undersæt af dine postkasser. Denne proces er kun beregnet til kunder, der forlader tjenesten.

Hvis du vil starte stien til datarensning, skal du udføre disse trin:

1. Fjern tilladelser til ombrydning og fjernelse af ombrydning for "O365 Exchange Online" fra Azure Key Vaults.

2. Hvis du bruger en arbejds- eller skolekonto, der har globale administratorrettigheder i din organisation, kan du [oprette forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. Kør [Cmdlet'en Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) for hver enkelt deP, der indeholder postkasser, som du vil slette.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Hvis kommandoen mislykkes, skal du kontrollere, at du har fjernet Exchange Online-tilladelserne fra begge nøgler i Azure Key Vault som angivet tidligere i denne opgave. Når du har angivet parameteren PermanentDataPurgeRequested ved hjælp af cmdlet'en Set-DataEncryptionPolicy, kan du ikke længere tildele denne dep til postkasser.

4. Kontakt Microsoft Support, og anmod om eDocument til datarensning.

    På din anmodning sender Microsoft dig et juridisk dokument for at bekræfte og godkende sletning af data. Den person i din organisation, der har tilmeldt sig som godkender i FastTrack tilbud under onboarding, skal signere dette dokument. Normalt er dette en leder eller en anden udpeget person i din virksomhed, der er lovligt autoriseret til at underskrive papirarbejdet på vegne af din organisation.

5. Når din repræsentant har signeret det juridiske dokument, skal du returnere det til Microsoft (normalt via en eDoc-signatur).

    Når Microsoft modtager det juridiske dokument, kører Microsoft cmdlet'er for at udløse datarensning, som først sletter politikken, markerer postkasserne til permanent sletning og sletter derefter tilgængelighedsnøglen. Når datarensningsprocessen er fuldført, er dataene blevet fjernet, de er ikke tilgængelige for Exchange Online og kan ikke genoprettes.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Tilbagekald dine kundenøgler og tilgængelighedsnøglen for SharePoint Online-, OneDrive for Business- og Teams-filer

Rensning af SharePoint, OneDrive til arbejde eller skole og Teams filer understøttes ikke i Kundenøgle. Disse dep'er med flere arbejdsbelastninger bruges til at kryptere data på tværs af flere arbejdsbelastninger på tværs af alle lejerbrugere. Hvis du fjerner en sådan forhindring af dataadgang, vil det medføre, at data på tværs af flere arbejdsbelastninger bliver utilgængelige. Hvis du beslutter dig for helt at afslutte Microsoft 365 tjenester, kan du forfølge stien til sletning af lejer i henhold til den dokumenterede proces. Se, hvordan [du sletter en lejer i Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med Microsoft Purview-kundenøgle](customer-key-overview.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Kundelockbox](customer-lockbox-requests.md)

- [Tjenestekryptering](office-365-service-encryption.md)
