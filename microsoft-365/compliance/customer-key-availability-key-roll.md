---
title: Rul eller roter en kundenøgle eller en tilgængelighedsnøgle
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
description: Få mere at vide om, hvordan du ruller kundens rodnøgler, der er gemt i Azure Key Vault, og som bruges sammen med kundenøglen. Tjenester omfatter Exchange Online, Skype for Business, SharePoint online, OneDrive for Business og Teams filer.
ms.openlocfilehash: 5f2de108d493e4b6d4233f4a932a24f524e468bb
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588767"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Rul eller roter en kundenøgle eller en tilgængelighedsnøgle

> [!CAUTION]
> Rul kun en krypteringsnøgle, som du bruger med kundenøgle, når dine sikkerheds- eller overholdelseskrav dikterer, at du skal rulle nøglen. Desuden må du ikke slette nogen nøgler, der er eller var knyttet til politikker. Når du ruller dine nøgler, vil der være indhold, der er krypteret med de forrige nøgler. Mens aktive postkasser f.eks. krypteres igen ofte, kan inaktive, frakoblede og deaktiverede postkasser stadig være krypteret med de forrige nøgler. SharePoint Online udfører sikkerhedskopiering af indhold til gendannelses- og genoprettelsesformål, så der kan stadig være arkiveret indhold ved hjælp af ældre nøgler.

## <a name="about-rolling-the-availability-key"></a>Om at rulle tilgængelighedsnøglen

Microsoft viser ikke direkte kontrol over tilgængelighedsnøglen til kunderne. Du kan f.eks. kun rulle (rotere) de taster, du ejer i Azure Key Vault. Microsoft 365 ruller tilgængelighedsnøglerne efter en internt defineret tidsplan. Der er ingen serviceaftale (SLA) på kundeniveau for disse nøglelister. Microsoft 365 roterer tilgængelighedsnøglen ved Microsoft 365 en tjenestekode i en automatiseret, ikke-manuel proces. Microsoft-administratorer kan starte processen. Nøglen rulles ved hjælp af automatiserede mekanismer uden direkte adgang til nøglelageret. Adgang til tilgængelighedsnøglen til hemmelig butik er ikke klargjort for Microsoft-administratorer. Når der rulles med tilgængelighedsnøgler, benyttes den samme mekanisme, som oprindeligt blev brugt til at generere nøglen. Du kan finde flere oplysninger om tilgængelighedsnøglen [under Forstå tilgængelighedsnøglen](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online og Skype for Business-tilgængelighedsnøgler kan effektivt opløftes af kunder, der opretter en ny dep, da der genereres en entydig tilgængelighedsnøgle for hver DEP, du opretter. Tilgængelighedstaster til SharePoint Online-, OneDrive for Business- og Teams-filer findes på skovniveau og deles på tværs af IP'er og kunder, hvilket betyder, at rulning kun forekommer i en internt defineret Microsoft-tidsplan. For at reducere risikoen for ikke at rulle tilgængelighedsnøglen, hver gang der oprettes en ny dep, ruller SharePoint, OneDrive og Teams lejerens mellemliggende nøgle (TIK), nøglen, der ombrudt af kundens rodnøgler og tilgængelighedsnøgle, hver gang der oprettes en ny dep.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Anmod om en ny version af hver eksisterende rodnøgle, du vil rulle

Når du ruller en nøgle, kan du anmode om en ny version af en eksisterende nøgle. Hvis du vil anmode om en ny version af en eksisterende nøgle, skal du bruge den samme cmdlet, [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey), med den samme syntaks, du brugte til at oprette nøglen i første omgang. Når du er færdig med at rulle en nøgle, der er knyttet til en politik for datakryptering (DEP), skal du køre en anden cmdlet for at sikre, at Kundenøgle begynder at bruge den nye nøgle. Gør dette trin i hver Azure Key Vault (AKV).

Eksempel:

1. Log på dit Azure-abonnement med Azure PowerShell. Du kan finde en vejledning [under Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør Add-AzKeyVaultKey som vist i følgende eksempel:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   I dette eksempel, da der findes en nøgle med navnet **Contoso-CK-EX-NA-VaultA1-Key001** i **Contoso-CK-EX-NA-VaultA1-boksen** , opretter cmdlet'en en ny version af nøglen. Denne handling bevarer de tidligere nøgleversioner i versionshistorikken for nøglen. Du skal bruge den forrige nøgleversion til at dekryptere de data, som den stadig krypterer. Når du er færdig med at rulle en tast, der er knyttet til en dep, skal du køre en ekstra cmdlet for at sikre, at kundenøglen begynder at bruge den nye nøgle. I de følgende afsnit beskrives cmdlet'erne mere detaljeret.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Opdater nøgler til BRUG AFP'er med flere arbejdsbelastninger

Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en deP, der bruges med flere arbejdsbelastninger, skal du opdatere datalisten, så den peger på den nye nøgle. Denne proces roterer ikke tilgængelighedsnøglen.

Hvis du vil bede kundenøglen om at bruge den nye nøgle til at kryptere flere arbejdsbelastninger, skal du udføre disse trin:

1. På din lokale computer kan du ved hjælp af en arbejds- eller skolekonto, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation, oprette forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell-vindue.

2. Kør Set-M365DataAtRestEncryptionPolicy cmdlet'en.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Hvor *PolicyName* er politikkens navn eller entydige id. For eksempel Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Opdater tasterne for Exchange Online IP'er

Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en deP, der bruges sammen med Exchange Online og Skype for Business, skal du opdatere DEP, så den peger på den nye nøgle. Dette roterer ikke tilgængelighedsnøglen.

For at instruere kundenøgle om at bruge den nye nøgle til at kryptere postkasser skal du køre Set-DataEncryptionPolicy cmdlet'en på følgende måde:

1. Kør Set-DataEncryptionPolicy cmdlet i Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Hvis du vil kontrollere værdien for egenskaben DataEncryptionPolicyID for postkassen, skal du følge trinnene i Finde [den DEP, der er tildelt en postkasse](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). Værdien for denne egenskab ændres, når tjenesten anvender den opdaterede nøgle.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Opdater tasterne for SharePoint Online-, OneDrive for Business- og Teams filer

SharePoint Online kan du kun rulle én tast ad gangen. Hvis du vil rulle begge taster i en nøgleboks, skal du vente på, at den første handling fuldføres. Microsoft anbefaler, at du forskudt dine handlinger for at undgå dette problem. Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en deP, der bruges sammen med SharePoint Online og OneDrive for Business, skal du opdatere dep'en, så den peger på den nye nøgle. Dette roterer ikke tilgængelighedsnøglen.

1. Kør Update-SPODataEncryptionPolicy følgende:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Mens denne cmdlet starter nøglerullehandlingen for SharePoint Online og OneDrive for Business, udføres handlingen ikke med det samme.

2. Hvis du vil se status for nøglerullehandlingen, skal du køre Get-SPODataEncryptionPolicy cmdlet'en på følgende måde:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle til Office 365](customer-key-overview.md)

- [Konfigurer kundenøgle til Office 365](customer-key-set-up.md)

- [Administrer kundenøgle for Office 365](customer-key-manage.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)
