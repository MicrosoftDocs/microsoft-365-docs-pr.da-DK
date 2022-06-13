---
title: Forbind til alle Microsoft 365 tjenester i et enkelt PowerShell-vindue
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/23/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Oversigt: Forbind til alle Microsoft 365 tjenester i et enkelt PowerShell-vindue.'
ms.openlocfilehash: babb5c308310e1444a2ac20b6557f4f7a2050f79
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016894"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Forbind til alle Microsoft 365 tjenester i et enkelt PowerShell-vindue

Når du bruger PowerShell til at administrere Microsoft 365, kan du have flere PowerShell-sessioner åbne på samme tid. Du har muligvis forskellige PowerShell-vinduer til administration af brugerkonti, SharePoint Online, Exchange Online, Microsoft Teams, Microsoft Defender for Office 365 funktioner (sikkerhed) og funktioner til overholdelse af Microsoft Purview-overholdelse.

Dette scenarie er ikke optimalt til administration af Microsoft 365, fordi du ikke kan udveksle data mellem disse vinduer for administration på tværs af tjenester. I denne artikel beskrives det, hvordan du bruger en enkelt forekomst af PowerShell til at administrere Microsoft 365 konti, Exchange Online, SharePoint Online, Microsoft Teams og funktioner i Defender for Office 365 Microsoft Purview-overholdelse.

>[!Note]
>Denne artikel indeholder i øjeblikket kun kommandoerne til at oprette forbindelse til verdensomspændende cloud (+GCC). Noter indeholder links til artikler om oprettelse af forbindelse til andre Microsoft 365 cloudmiljøer.

## <a name="before-you-begin"></a>Før du begynder

Før du kan administrere alle Microsoft 365 fra en enkelt forekomst af PowerShell, skal du overveje følgende forudsætninger:

- Den Microsoft 365 arbejds- eller skolekonto, du bruger, skal være medlem af Microsoft 365 administratorrollen. Du kan få mere at vide under [Om administratorroller](../admin/add-users/about-admin-roles.md). Dette er et krav til PowerShell til Microsoft 365, men ikke nødvendigvis for alle andre Microsoft 365 tjenester.

- Du kan bruge følgende 64-bit versioner af Windows:
  - Windows 11
  - Windows 10
  - Windows 8.1 eller Windows 8
  - Windows Server 2019
  - Windows Server 2016
  - Windows Server 2012 R2 eller Windows Server 2012
  - Windows 7 Service Pack 1 (SP1)*
  - Windows Server 2008 R2 SP1*

    \*Du skal installere Microsoft .NET Framework 4.5.*x* og derefter Windows Management Framework 3.0 eller 4.0. Du kan få flere oplysninger under [Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).

- Du skal installere de moduler, der kræves til Azure Active Directory (Azure AD), Exchange Online, Defender for Office 365, Microsoft Purview-overholdelse, SharePoint Online og Teams:

  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Teams PowerShell-modul](/microsoftteams/teams-powershell-overview)
  - [Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Oversigt over Teams PowerShell](/microsoftteams/teams-powershell-overview)

- PowerShell skal være konfigureret til at køre signerede scripts for Exchange Online, Defender for Office 365 og Microsoft Purview-overholdelse. Kør følgende kommando i en PowerShell-session med administratorrettigheder (en PowerShell-session, som du **kører som administrator**).

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Forbindelsestrin, når du kun bruger en adgangskode

Følg disse trin for at oprette forbindelse til alle tjenesterne i et enkelt PowerShell-vindue, når du kun bruger en adgangskode til logon.

1. Åbn Windows PowerShell.

2. Kør denne kommando, og angiv dine legitimationsoplysninger til Microsoft 365 arbejds- eller skolekonto.

   ```powershell
   $credential = Get-Credential
   ```

3. Kør denne kommando for at oprette forbindelse til Azure AD ved hjælp af modulet Azure Active Directory PowerShell til Graph.

   ```powershell
   Connect-AzureAD -Credential $credential
   ```

   Eller hvis du bruger modulet Microsoft Azure Active Directory til Windows PowerShell modul, skal du køre denne kommando.

   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!NOTE]
   > PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med *Msol* i deres navn. Du skal køre disse cmdlet'er fra PowerShell.

4. Kør disse kommandoer for at oprette forbindelse til SharePoint Online. Angiv organisationsnavnet for dit domæne. For "litwareinc\.onmicrosoft.com" er værdien for organisationens navn f.eks. "litwareinc".

   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Kør disse kommandoer for at oprette forbindelse til Exchange Online.

   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > Hvis du vil oprette forbindelse til Exchange Online til Microsoft 365 cloudmiljøer, der ikke er over hele verden, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. Kør disse kommandoer for at oprette forbindelse til Security & Compliance PowerShell.

   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!NOTE]
   > Hvis du vil oprette forbindelse til PowerShell til sikkerhed & overholdelse af angivne standarder for Microsoft 365 cloudmiljøer ud over hele verden, skal du se [Forbind til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

7. Kør disse kommandoer for at oprette forbindelse til Teams PowerShell.

   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

   > [!NOTE]
   > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-version, behøver du ikke at installere Skype for Business Online Connector.
   >
   > Hvis du vil oprette forbindelse til Microsoft Teams cloudmiljøer ud over *hele verden*, skal du se [Forbind-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).

### <a name="azure-active-directory-powershell-for-graph-module-when-using-just-a-password"></a>Azure Active Directory PowerShell til Graph modul, når du kun bruger en adgangskode

Her er kommandoerne for alle tjenesterne i en enkelt blok, når du bruger modulet Azure Active Directory PowerShell til Graph. Angiv navnet på domæneværten og UPN'et for logon, og kør dem alle samtidig.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-AzureAD -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-just-a-password"></a>Microsoft Azure Active Directory modul til Windows PowerShell modul, når du kun bruger en adgangskode

Her er kommandoerne for alle tjenesterne i en enkelt blok, når du bruger Microsoft Azure Active Directory Module til Windows PowerShell modul. Angiv navnet på domæneværten og UPN'et for logon, og kør dem alle på én gang.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-MsolService -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Forbindelsestrin ved brug af multifaktorgodkendelse

### <a name="azure-active-directory-powershell-for-graph-module-when-using-mfa"></a>Azure Active Directory PowerShell til Graph modul, når du bruger MFA

Her er alle kommandoerne i en enkelt blok til at oprette forbindelse til flere Microsoft 365 tjenester, når du bruger multifaktorgodkendelse med Azure Active Directory PowerShell til Graph modul.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-mfa"></a>Microsoft Azure Active Directory modul til Windows PowerShell modul, når du bruger MFA

Her er alle kommandoerne i en enkelt blok til at oprette forbindelse til flere Microsoft 365-tjenester, når du bruger multifaktorgodkendelse med Microsoft Azure Active Directory Module til Windows PowerShell modul.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>Luk PowerShell-vinduet

Hvis du vil lukke PowerShell-vinduet, skal du køre denne kommando for at fjerne de aktive sessioner for at SharePoint Online, Teams, Defender for Office 365 og Microsoft Purview-overholdelse:

```powershell
Disconnect-SPOService; Disconnect-MicrosoftTeams; Disconnect-ExchangeOnline
```

## <a name="see-also"></a>Se også

- [Opret forbindelse til Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md)
- [Administrer SharePoint Online med PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
