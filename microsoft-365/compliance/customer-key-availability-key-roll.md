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
description: Få mere at vide om, hvordan du kan rulle de kunderodnøgler, der er gemt i Azure Key Vault, som bruges sammen med kundenøglen. Tjenesterne omfatter filer af typen Exchange Online, Skype for Business, SharePoint Online, OneDrive for Business og Teams.
ms.openlocfilehash: 81d82f49c056f5a6ec9b8731b549aee68d5d658b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761345"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Rul eller roter en kundenøgle eller en tilgængelighedsnøgle

> [!CAUTION]
> Opløft kun en krypteringsnøgle, som du bruger sammen med Kundenøgle, når dine krav til sikkerhed eller overholdelse af angivne standarder kræver, at du skal rulle nøglen. Du må desuden ikke slette nogen nøgler, der er eller er knyttet til politikker. Når du ruller dine nøgler, vil der være indhold, der er krypteret med de forrige nøgler. Selvom aktive postkasser f.eks. krypteres igen ofte, kan inaktive, afbrudte og deaktiverede postkasser stadig krypteres med de forrige nøgler. SharePoint Online sikkerhedskopierer indhold til gendannelses- og gendannelsesformål, så der kan stadig være arkiveret indhold ved hjælp af ældre nøgler.

## <a name="about-rolling-the-availability-key"></a>Om at rulle tilgængelighedsnøglen

Microsoft fremviser ikke direkte kontrol over tilgængelighedsnøglen for kunder. Du kan f.eks. kun rulle (rotere) de nøgler, du ejer i Azure Key Vault. Microsoft 365 akkumulerer tilgængelighedsnøglerne efter en internt defineret tidsplan. Der er ingen serviceniveauaftale (SLA) på kundeniveau for disse vigtige kast. Microsoft 365 roterer tilgængelighedsnøglen ved hjælp af Microsoft 365 servicekode i en automatiseret, ikke-manuel proces. Microsoft-administratorer kan starte rulleprocessen. Nøglen rulles ved hjælp af automatiserede mekanismer uden direkte adgang til nøglelageret. Adgang til det hemmelige lager for tilgængelighedsnøgler er ikke klargjort til Microsoft-administratorer. Rullende tilgængelighedsnøgle udnytter den samme mekanisme, der bruges til indledningsvist at generere nøglen. Du kan få flere oplysninger om tilgængelighedsnøglen under [Forstå tilgængelighedsnøglen](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online og Skype for Business tilgængelighedsnøgler kan rulles effektivt af kunder, der opretter en ny dep, da der genereres en entydig tilgængelighedsnøgle for hver enkelt deP, du opretter. Tilgængelighedsnøgler til SharePoint Online-, OneDrive for Business- og Teams-filer findes på områdeniveau og deles på tværs af DEP'er og kunder, hvilket betyder, at rullende kun forekommer efter en internt defineret tidsplan fra Microsoft. Hvis du vil afhjælpe risikoen for ikke at rulle tilgængelighedsnøglen, hver gang der oprettes en ny forhindring af dataforbrug, skal du SharePoint, OneDrive og Teams rulle lejerens mellemliggende nøgle (TIK), den nøgle, der er ombrudt af kundens rodnøgle og tilgængelighedsnøgle, hver gang der oprettes en ny dep.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Anmod om en ny version af hver eksisterende rodnøgle, du vil rulle

Når du ruller en nøgle, anmoder du om en ny version af en eksisterende nøgle. Hvis du vil anmode om en ny version af en eksisterende nøgle, skal du bruge den samme cmdlet [, Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey), med den samme syntaks, som du brugte til at oprette nøglen i første omgang. Når du er færdig med at rulle en hvilken som helst nøgle, der er knyttet til en datakrypteringspolitik, kører du en anden cmdlet for at sikre, at kundenøglen begynder at bruge den nye nøgle. Gør dette trin i hver Azure Key Vault (AKV).

Eksempel:

1. Log på dit Azure-abonnement med Azure PowerShell. Du kan finde en vejledning under [Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør cmdlet'en Add-AzKeyVaultKey som vist i følgende eksempel:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Da der i dette eksempel findes en nøgle med navnet **Contoso-CK-EX-NA-VaultA1-Key001** i **contoso-CK-EX-NA-VaultA1** vault, opretter cmdlet'en en ny version af nøglen. Denne handling bevarer de tidligere nøgleversioner i versionshistorikken for nøglen. Du skal bruge den tidligere nøgleversion for at dekryptere de data, der stadig krypteres. Når du er færdig med at rulle en nøgle, der er knyttet til en forhindring af datakørsel, skal du køre en ekstra cmdlet for at sikre, at kundenøglen begynder at bruge den nye nøgle. I de følgende afsnit beskrives cmdlet'erne mere detaljeret.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Opdater nøglerne til DEP'er med flere arbejdsbelastninger

Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en forhindring af dataforbindelse, som bruges med flere arbejdsbelastninger, skal du opdatere programmet til at pege på den nye nøgle. Denne proces roterer ikke tilgængelighedsnøglen.

Hvis du vil instruere kundenøglen i at bruge den nye nøgle til at kryptere flere arbejdsbelastninger, skal du udføre disse trin:

1. Opret [forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) i et Windows PowerShell vindue ved hjælp af en arbejds- eller skolekonto på din lokale computer, der har globale administrator- eller overholdelsesadministratortilladelser i din organisation.

2. Kør cmdlet'en Set-M365DataAtRestEncryptionPolicy.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Hvor *PolicyName* er navnet eller det entydige id for politikken. Det kan f.eks. være Contoso_Global.

Eksempel:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Opdater nøglerne til Exchange Online DEP'er

Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en forhindring af dataforbindelse, som bruges sammen med Exchange Online og Skype for Business, skal du opdatere programmet til at pege på den nye nøgle. Dette roterer ikke tilgængelighedsnøglen.

Hvis du vil instruere kundenøglen i at bruge den nye nøgle til at kryptere postkasser, skal du køre cmdlet'en Set-DataEncryptionPolicy på følgende måde:

1. Kør Set-DataEncryptionPolicy-cmdlet'en i Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Hvis du vil kontrollere værdien for egenskaben DataEncryptionPolicyID for postkassen, skal du bruge trinnene i [Find den forhindring af dataoverførsel, der er tildelt en postkasse](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). Værdien for denne egenskab ændres, når tjenesten anvender den opdaterede nøgle.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Opdater nøglerne til SharePoint Online-, OneDrive for Business- og Teams-filer

SharePoint Online giver dig kun mulighed for at rulle én nøgle ad gangen. Hvis du vil rulle begge nøgler i en key vault, skal du vente på, at den første handling fuldføres. Microsoft anbefaler, at du forskyde dine handlinger for at undgå dette problem. Når du ruller en af de Azure Key Vault-nøgler, der er knyttet til en forhindring af dataforbindelse, som bruges sammen med SharePoint Online og OneDrive for Business, skal du opdatere programmet til at pege på den nye nøgle. Dette roterer ikke tilgængelighedsnøglen.

1. Kør Update-SPODataEncryptionPolicy-cmdlet'en på følgende måde:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Selvom denne cmdlet starter handlingen med nøglerullen for SharePoint Online og OneDrive for Business, fuldføres handlingen ikke med det samme.

2. Kør Get-SPODataEncryptionPolicy-cmdlet'en på følgende måde for at se status for handlingen til kast af nøgler:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle til Office 365](customer-key-overview.md)

- [Konfigurer kundenøgle til Office 365](customer-key-set-up.md)

- [Administrer kundenøgle for Office 365](customer-key-manage.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)
