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
description: Når du har konfigureret en kundenøgle, kan du se, hvordan du administrerer den ved at gendanne AKV-nøgler og administrere tilladelser og oprette og tildele politikker for datakryptering.
ms.openlocfilehash: 9dd333064c9fa121f8f1c99ffcd048f6b977dbf2
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63589591"
---
# <a name="manage-customer-key"></a>Administrer kundenøgle

Når du har konfigureret en kundenøgle til Office 365, skal du oprette og tildele en eller flere politikker for datakryptering (DEP). Når du har tildelt dine IP'er, kan du administrere dine nøgler som beskrevet i denne artikel. Få mere at vide om kundenøgle i relaterede emner.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Opret en dep til brug med flere arbejdsbelastninger for alle lejerbrugere

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere kunde. Du kan få mere [at vide under Konfigurer kundenøgle](customer-key-set-up.md). Hvis du vil oprette DEP'en, skal du bruge de Key Vault-URI'er, du fik under installationen. Du kan få mere at [vide under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Hvis du vil oprette en DEP med flere arbejdsbelastninger, skal du følge disse trin:
  
1. På din lokale computer kan du ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation, oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue.

2. Hvis du vil oprette en dep, skal du New-M365DataAtRestEncryptionPolicy en cmdlet.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Hvor:

   - *PolicyName* er det navn, du vil bruge til politikken. Navne må ikke indeholde mellemrum. For eksempel Contoso_Global.

   - *KeyVaultURI1* er URI'en for den første nøgle i politikken. F.eks. <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* er URI'en for den anden nøgle i politikken. F.eks. <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. Adskid de to URI'er med et komma og et mellemrum.

   - *PolitikBeskrivelse* er en brugervenlig beskrivelse af politikken, der hjælper dig med at huske, hvad politikken bruges til. Du kan medtage mellemrum i beskrivelsen. F.eks. "Rodpolitik for flere arbejdsbelastninger for alle brugere i lejeren."

Eksempel:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Tildel politik for flere arbejdsbelastninger

Tildel dep ved hjælp af Set-M365DataAtRestEncryptionPolicyAssignment cmdlet. Når du tildeler politikken, krypterer Microsoft 365 dataene med den nøgle, der er identificeret i dep'en.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Hvor *PolicyName* er navnet på politikken. For eksempel Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Opret en dep til brug med Exchange Online postkasser

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere Azure Key Vault. Du kan få mere [at vide under Konfigurer kundenøgle](customer-key-set-up.md). Du kan udføre disse trin ved at oprette fjernforbindelse til Exchange Online med Windows PowerShell.

En dep er knyttet til et sæt nøgler, der er gemt i Azure Key Vault. Du tildeler en dep til en postkasse i Microsoft 365. Microsoft 365 bruger derefter de nøgler, der er identificeret i politikken, til at kryptere postkassen. Hvis du vil oprette DEP'en, skal du bruge de Key Vault-URI'er, du fik under installationen. Du kan få mere at [vide under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Husk! Når du opretter en dep, angiver du to nøgler i to forskellige Azure Key-bokse. Opret disse nøgler i to separate Azure-områder for at sikre geo-redundans.

Hvis du vil oprette en dep til brug med en postkasse, skal du følge disse trin:
  
1. Opret forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue på din lokale computer ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller Exchange Online-administratortilladelser i organisationen.

2. Hvis du vil oprette en dep, skal du New-DataEncryptionPolicy en cmdlet ved at skrive følgende kommando.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Hvor:

   - *PolicyName* er det navn, du vil bruge til politikken. Navne må ikke indeholde mellemrum. For eksempel USA_mailboxes.

   - *PolitikBeskrivelse* er en brugervenlig beskrivelse af politikken, der hjælper dig med at huske, hvad politikken bruges til. Du kan medtage mellemrum i beskrivelsen. "Rodnøgle for postkasser i USA og dets områder".

   - *KeyVaultURI1* er URI'en for den første nøgle i politikken. F.eks. <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* er URI'en for den anden nøgle i politikken. F.eks. <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. Adskid de to URI'er med et komma og et mellemrum.

   Eksempel:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Tildele en dep til en postkasse

Tildel dep til en postkasse ved hjælp af Set-Mailbox cmdlet. Når du tildeler politikken, kan Microsoft 365 kryptere postkassen med den nøgle, der er identificeret i dep.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Where *MailboxIdParameter* angiver en brugerpostkasse. Du kan finde flere oplysninger Set-Mailbox cmdlet'en [Set-Mailbox](/powershell/module/exchange/set-mailbox).

I hybridmiljøer kan du tildele en dep til de lokale postkassedata, der synkroniseres med din Exchange Online lejer. For at tildele en dep til denne synkroniserede postkassedata skal du bruge Set-MailUser cmdlet. Du kan finde flere oplysninger om postkassedata i hybridmiljøet i lokale postkasser, der bruger [Outlook til iOS og Android med hybrid moderne godkendelse](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Where *MailUserIdParameter* angiver en mailbruger (også kaldet en mailaktiveret bruger). Du kan finde flere oplysninger Set-MailUser cmdlet under [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>Opret en dep til brug med SharePoint Online-, OneDrive for Business- og Teams filer

Før du begynder, skal du sikre dig, at du har fuldført de opgaver, der kræves for at konfigurere Azure Key Vault. Du kan få mere [at vide under Konfigurer kundenøgle](customer-key-set-up.md).
  
Hvis du vil konfigurere en kundenøgle til SharePoint Online, OneDrive for Business og Teams-filer, skal du udføre disse trin ved at oprette fjernforbindelse til SharePoint Online med Windows PowerShell.
  
Du knytter en dep til et sæt nøgler, der er gemt i Azure Key Vault. Du anvender en dep på alle dine data i en geografisk placering, også kaldet et geo. Hvis du bruger funktionen multi-geo i Office 365, kan du oprette én dep pr. geo med mulighed for at bruge forskellige nøgler pr. geo. Hvis du ikke bruger multi-geo, kan du oprette en dep i din organisation til brug med SharePoint Online, OneDrive for Business og Teams filer. Microsoft 365 bruger de nøgler, der er identificeret i dataudbyderen, til at kryptere dine data i det pågældende geo. Hvis du vil oprette DEP'en, skal du bruge de Key Vault-URI'er, du fik under installationen. Du kan få mere at [vide under Hent URI'en for hver Azure Key Vault-nøgle](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Husk! Når du opretter en dep, angiver du to nøgler i to forskellige Azure Key-bokse. Opret disse nøgler i to separate Azure-områder for at sikre geo-redundans.
  
Hvis du vil oprette en dep, skal du oprette fjernforbindelse til SharePoint Online ved hjælp af Windows PowerShell.
  
1. På din lokale computer skal du bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, Forbind [at SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. I Microsoft Office SharePoint Online Management Shell skal du køre Register-SPODataEncryptionPolicy cmdlet på følgende måde:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Eksempel:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   Når du registrerer DEP, begynder krypteringen på dataene i geo. Kryptering kan tage lidt tid. Du kan finde flere oplysninger om brug af denne parameter [under Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Få vist de IP'er, du har oprettet til Exchange Online postkasser

Hvis du vil have vist en liste over alle de IP'er, du har oprettet til postkasser, skal du Get-DataEncryptionPolicy PowerShell-cmdlet'en.

1. Ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. For at returnere alle IP'er i organisationen skal du køre Get-DataEncryptionPolicy uden nogen parametre.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Du kan finde flere oplysninger Get-DataEncryptionPolicy cmdlet i [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Tildel en dep, før du overfører en postkasse til skyen

Når du tildeler DEP, krypterer Microsoft 365 indholdet af postkassen ved hjælp af den tildelte dep under overførslen. Denne proces er mere effektiv end at overføre postkassen, tildele DEP og derefter vente på, at krypteringen finder sted, hvilket kan tage timer eller dage.

For at tildele en dep til en postkasse, før du overfører den Office 365, skal du køre Set-MailUser cmdlet i Exchange Online PowerShell:

1. Ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-MailUser cmdlet'en.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Where *GeneralMailboxOrMailUserIdParameter* specifies a mailbox, and *DataEncryptionPolicyIdParameter* is the ID of the DEP. Du kan finde flere oplysninger Set-MailUser cmdlet under [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Fastslå deP, der er tildelt en postkasse

Du kan finde ud af, hvilken DEP der er tildelt til en postkasse, Get-MailboxStatistics en cmdlet. Cmdletten returnerer et entydig identifier (GUID).
  
1. Ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   Where *GeneralMailboxOrMailUserIdParameter specifies* a mailbox and DataEncryptionPolicyID returns the GUID of the DEP. Du kan finde flere oplysninger Get-MailboxStatistics cmdlet'en [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Kør Get-DataEncryptionPolicy-cmdlet'en for at finde ud af det fulde navn på den deP, som postkassen er tildelt til.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Hvor *GUID er* det GUID, der returneres af Get-MailboxStatistics-cmdlet'en i forrige trin.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Kontrollér, at kundenøglen er færdig med krypteringen

Uanset om du har rullet en kundenøgle, tildelt en ny dep eller overført en postkasse, skal du bruge trinnene i dette afsnit for at sikre, at krypteringen er fuldført.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Bekræft, at krypteringen er fuldført for Exchange Online postkasser

Det kan tage lidt tid at kryptere en postkasse. Ved første kryptering skal postkassen også flytte helt fra én database til en anden, før tjenesten kan kryptere postkassen.
  
Brug Get-MailboxStatistics-cmdlet'en til at afgøre, om en postkasse er krypteret.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

Egenskaben IsEncrypted returnerer værdien sand, hvis postkassen er krypteret, og værdien **falsk**, hvis postkassen ikke er krypteret. Tiden til at fuldføre postkassen flyttes, afhænger af antallet af postkasser, som du tildeler en dep for første gang, og størrelsen af postkasserne. Hvis postkasserne ikke er blevet krypteret efter en uge fra det tidspunkt, hvor du tildelte DEP, skal du kontakte Microsoft.

Cmdletten New-MoveRequest ikke længere tilgængelig ved flytning af lokale postkasser. Se denne [meddelelse for](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) at få flere oplysninger.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Bekræft, at krypteringen er SharePoint online-, OneDrive for Business- og Teams filer

Kontrollér status for kryptering ved at køre den Get-SPODataEncryptionPolicy cmdlet på følgende måde:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Outputtet fra denne cmdlet omfatter:
  
- Den primære nøgles URI.

- Den sekundære nøgles URI.

- Krypteringsstatus for geo. Mulige tilstande omfatter:

  - **Ikke registreret:** Kryptering af kundenøgler er endnu ikke blevet anvendt.

  - **Registrering:** Kryptering af kundenøgler er blevet anvendt, og dine filer er i gang med at blive krypteret. Hvis nøglen til geo registreres, får du også vist oplysninger om, hvilken procentdel af webstederne i geo er fuldstændige, så du kan overvåge status for kryptering.

  - **Registreret:** Kryptering af kundenøgle er blevet anvendt, og alle filer på alle websteder er blevet krypteret.

  - **Rolling:** En vigtig opdatering er i gang. Hvis nøglen til geo er rullet, får du også vist oplysninger om, hvilken procentdel af websteder der har fuldført nøglerullehandlingen, så du kan overvåge status.

- Den viser også procentdelen af websteder onboardet.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Få oplysninger om DEP'er, du bruger med flere arbejdsbelastninger

Hvis du vil have oplysninger om alle de LØSNING'er, du har oprettet til brug med flere arbejdsbelastninger, skal du udføre disse trin:

1. På din lokale computer kan du ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation, oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue.

   - Kør denne kommando for at returnere listen over alle DEL'er med flere arbejdsbelastninger i organisationen.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Kør denne kommando for at returnere oplysninger om en bestemt DEP. I dette eksempel returneres detaljerede oplysninger for deP med navnet "Contoso_Global".

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Få oplysninger om tildeling af flere arbejdsbelastninger

Følg disse trin for at finde ud af, hvilken DEP der aktuelt er tildelt til din lejer. 

1. På din lokale computer kan du ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation, oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue.

2. Skriv denne kommando.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Deaktivere en DEP med flere arbejdsbelastninger

Før du deaktiverer en DEP med flere arbejdsbelastninger, skal du fjerne tildelingen af DEP fra arbejdsbelastninger i din lejer. Hvis du vil deaktivere en deP, der bruges med flere arbejdsbelastninger, skal du udføre disse trin:

1. På din lokale computer kan du ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation, oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue.

2. Kør Set-M365DataAtRestEncryptionPolicy cmdlet'en.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Hvor *PolicyName* er politikkens navn eller entydige id. For eksempel Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Gendan Azure Key Vault-nøgler

Før du udfører en gendannelse, skal du bruge de genoprettelsesfunktioner, der leveres af blød sletning. Alle nøgler, der bruges sammen med kundenøgle, skal være aktiveret til blød sletning. Blød sletning fungerer som en papirkurv og tillader gendannelse i op til 90 dage uden behov for gendannelse. Gendannelse bør kun være påkrævet i ekstreme eller usædvanlige tilfælde, f.eks. hvis nøglen eller nøgleboksen går tabt. Hvis du skal gendanne en nøgle til brug med kundenøgle i Azure PowerShell, skal du køre Restore-AzureKeyVaultKey cmdlet'en på følgende måde:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Eksempel:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Hvis nøgleboksen allerede indeholder en nøgle med det samme navn, mislykkes gendannelseshandlingen. Restore-AzKeyVaultKey gendanner alle nøgleversioner og alle metadata for nøglen, herunder nøglenavnet.
  
## <a name="manage-key-vault-permissions"></a>Administrer tilladelser for nøgleboks

Der findes flere cmdlet'er, som du kan bruge til at få vist og, hvis det er nødvendigt, fjerne tilladelser til nøglelejer. Du skal muligvis fjerne tilladelser, f.eks. når en medarbejder forlader teamet. For hver af disse opgaver skal du bruge Azure PowerShell. Du kan finde Azure PowerShell under [Oversigt over Azure PowerShell](/powershell/azure/).

For at få vist tilladelser til nøgle boks skal du køre Get-AzKeyVault cmdlet.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Eksempel:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Hvis du vil fjerne en administrators tilladelser, skal du køre Remove-AzKeyVaultAccessPolicy cmdlet:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Eksempel:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Rul tilbage fra kundenøgle til Microsoft-administrerede nøgler

Hvis du har brug for at vende tilbage til Microsoft-administrerede taster, kan du gøre det. Når du offboard, krypteres dine data igen ved hjælp af standardkryptering, der understøttes af hver enkelt arbejdsbelastning. Eksempelvis understøtter Exchange Online standardkryptering ved hjælp af Microsoft-administrerede nøgler.

> [!IMPORTANT]
> Offboarding er ikke det samme som en data tømning. En dataforseendende permanent crypto-sletter din organisations data fra Microsoft 365, offboarding sletter ikke. Du kan ikke udføre en data tømning for en politik for flere arbejdsbelastninger.

Hvis du beslutter dig for ikke at bruge kundenøgle til at tildele MULTI-workload DEP'er længere, skal du kontakte Microsoft Support med en anmodning om at "offboard" fra kundenøgle. Bed supportteamet om at arkivere en serviceanmodning Microsoft 365 kundenøgleteamet. Kontakt os, m365-ck@service.microsoft.com du har spørgsmål.

Hvis du ikke længere vil kryptere individuelle postkasser ved hjælp af DEP'er på postkasseniveau, kan du fjerne tildeling af DEP'er på postkasseniveau fra alle dine postkasser.

Hvis du vil fjerne tildelingen af postkasse-IP'er, skal Set-Mailbox PowerShell-cmdlet'en.

1. Ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du [oprette forbindelse Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-Mailbox cmdlet'en.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

Kørsel af denne cmdlet tildeler ikke den aktuelt tildelte dep og krypterer postkassen igen ved hjælp af deP, der er knyttet til microsoft-administrerede standardnøgler. Du kan ikke fjerne den DEP, der bruges af Microsoft-administrerede nøgler. Hvis du ikke vil bruge Microsoft-administrerede nøgler, kan du tildele en anden dep om kundenøgle til postkassen.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Tilbagekald dine nøgler, og start processen med at slette datastien

Du styrer tilbagekaldelsen af alle rodnøgler, herunder tilgængelighedsnøglen. Kundenøgle giver kontrol over aspekterne af planlægning af udgang i forbindelse med de lovmæssige krav for dig. Hvis du beslutter dig for at tilbagekalde dine nøgler for at slette dine data og afslutte tjenesten, sletter tjenesten tilgængelighedsnøglen, når dataudrydelsesprocessen er fuldført. Dette understøttes for de kundenøgler, der er tildelt til individuelle postkasser.

Microsoft 365 og validerer stien til data tømning. Du kan finde flere oplysninger i SSAE 18 SOC 2-rapporten på [Service Trust Portal](https://servicetrust.microsoft.com/). Desuden anbefaler Microsoft følgende dokumenter:

- [Vejledning til risikovurdering og overholdelse af regler og standarder for finansielle institutioner i Microsoft Cloud](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [Overvejelser i forbindelse med planlægning af afslutning i O365](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

TØMning af flere arbejdsbelastninger understøttes ikke for Microsoft 365 kundenøgle. DEP med flere arbejdsbelastninger bruges til at kryptere data på tværs af flere arbejdsbelastninger på tværs af alle lejerbrugere. Hvis du fjerner en sådan DEP, medfører det, at data på tværs af flere arbejdsbelastninger ikke bliver tilgængelige. Hvis du beslutter dig for Microsoft 365 lukke alle tjenester, kan du følge stien til lejersletning pr. den dokumenterede proces. Se[, hvordan du sletter en lejer Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Tilbagekald dine kundenøgler og tilgængelighedsnøglen til Exchange Online og Skype for Business

Når du starter dataudtømningstien for data Exchange Online og Skype for Business, angiver du en permanent anmodning om at slette data på en dep. Dette sletter permanent krypterede data i de postkasser, som dep er tildelt til.

Da du kun kan køre PowerShell-cmdlet'en mod én dep ad gangen, bør du overveje at tildele en enkelt dep til alle dine postkasser igen, inden du påbegynder dataudvælgerstien.

> [!WARNING]
> Brug ikke data-slettestien til at slette et undersæt af dine postkasser. Denne proces er kun beregnet til kunder, der afslutter tjenesten.

Hvis du vil starte data tømningstien, skal du udføre disse trin:

1. Fjern ombryd og fjern tilladelser for "O365 Exchange Online" fra Azure Key Vaults.

2. Brug en arbejds- eller skolekonto, der har globale administratorrettigheder i din organisation, til [at oprette forbindelse Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

3. For hver deP, der indeholder postkasser, du vil slette, skal du køre [Set-DataEncryptionPolicy-cmdlet'en](/powershell/module/exchange/set-dataencryptionpolicy) på følgende måde.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Hvis kommandoen mislykkes, skal du sikre dig, at du har fjernet Exchange Online tilladelser fra begge nøgler i Azure-nøgle boks som angivet tidligere i denne opgave.Når du har indstillet parameteren PermanentDataPurgeRequested ved hjælp Set-DataEncryptionPolicy cmdlet'en, vil du ikke længere kunne tildele denne DEP til postkasser.

4. Kontakt Microsoft Support, og anmod om eDocument til data tømning.

    På din anmodning sender Microsoft dig et juridisk dokument for at godkende og godkende sletning af data. Den person i din organisation, der har tilmeldt sig som godkender i FastTrack under onboarding, skal signere dette dokument. Normalt er dette en leder eller en anden udpeget person i din virksomhed, der i henhold til lovgivningen har tilladelse til at signere papirerne på vegne af din organisation.

5. Når din repræsentant har signeret det juridiske dokument, skal du returnere det til Microsoft (som regel via en eDoc-signatur).

    Når Microsoft modtager det juridiske dokument, kører Microsoft cmdlet'er for at udløse dataudtømningen, som først sletter politikken, markerer postkasserne til permanent sletning og sletter derefter tilgængelighedsnøglen. Når data tømningsprocessen er fuldført, er dataene blevet fjernet, er utilgængelige for Exchange Online og kan ikke gendannes.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Tilbagekald dine kundenøgler og tilgængelighedsnøglen til SharePoint Online-, OneDrive for Business- og Teams filer

Hvis du vil starte datatømningstien for SharePoint Online-, OneDrive for Business- Teams filer, skal du udføre disse trin:

1. Tilbagekald Adgang til Azure-nøgleboks. Alle vigtige administratorer i bokse skal acceptere at tilbagekalde adgangen.

   Du sletter ikke Azure Key Vault for SharePoint Online. Nøgle bokse kan deles mellem flere forskellige SharePoint Online-lejere og IP'er.

2. Kontakt Microsoft for at slette tilgængelighedsnøglen.

    Når du kontakter Microsoft for at slette tilgængelighedsnøglen, sender vi dig et juridisk dokument. Den person i din organisation, der har tilmeldt sig som godkender i FastTrack under onboarding, skal signere dette dokument. Normalt er dette en leder eller en anden udpeget person i din virksomhed, der i henhold til lovgivningen har tilladelse til at signere papirer på vegne af din organisation.

3. Når din repræsentant signerer det juridiske dokument, skal du returnere det til Microsoft (som regel via en eDoc-signatur).

   Når Microsoft modtager det juridiske dokument, kører vi cmdlet'er for at udløse den dataudvending, der udfører cryptosletning af lejernøglen, webstedsnøglen og alle individuelle nøgler pr. dokument, hvilket uigenkaldeligt bryder nøglehierarkiet. Når data tømning-cmdletterne er fuldført, er dine data blevet fjernet.

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Kunde-lockbox](customer-lockbox-requests.md)

- [Tjenestekryptering](office-365-service-encryption.md)
