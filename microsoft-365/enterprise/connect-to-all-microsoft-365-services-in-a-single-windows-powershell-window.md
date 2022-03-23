---
title: Forbind til alle Microsoft 365-tjenester i et enkelt PowerShell-vindue
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
description: 'Oversigt: Forbind til alle Microsoft 365-tjenester i et enkelt PowerShell-vindue.'
ms.openlocfilehash: 4df9a16aba22587adbe289bca2d74e78a64db4ba
ms.sourcegitcommit: b51bfed24a9e3b7adf82d4918b76462cd40dffaf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63590976"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Forbind til alle Microsoft 365-tjenester i et enkelt PowerShell-vindue

Når du bruger PowerShell til at administrere Microsoft 365, kan du have flere PowerShell-sessioner åbne på samme tid. Du kan have forskellige PowerShell-vinduer til at administrere brugerkonti, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams og Security &amp; Compliance Center.
  
Dette scenarie er ikke optimalt til Microsoft 365, fordi du ikke kan udveksle data mellem disse vinduer med henblik på administration på tværs af tjenester. I denne artikel beskrives det, hvordan du kan bruge en enkelt forekomst af PowerShell til at administrere Microsoft 365-konti, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams og Security &amp; Compliance Center.

>[!Note]
>Denne artikel indeholder i øjeblikket kun kommandoer til at oprette forbindelse til Worldwide (+GCC)-skyen. Noter indeholder links til artikler om at oprette forbindelse til andre Microsoft 365 skyer.

## <a name="before-you-begin"></a>Før du begynder

Før du kan administrere alle Microsoft 365 fra en enkelt forekomst af PowerShell, skal du overveje følgende forudsætninger:
  
- Den Microsoft 365 arbejds- eller skolekonto, du bruger, skal være medlem af Microsoft 365 administratorrolle. Du kan få mere at vide [under Om administratorroller](../admin/add-users/about-admin-roles.md). Dette er et krav til PowerShell til Microsoft 365, men ikke nødvendigvis for alle Microsoft 365 tjenester.
    
- Du kan bruge følgende 64-bit versioner af Windows:
    
  - Windows 10
    
  - Windows 8.1 eller Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 eller Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Du skal installere Microsoft .NET Framework 4.5.*x*, og Windows Management Framework 3.0 eller 4.0. Du kan finde flere oplysninger [i Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).
    
    Du skal bruge en 64-bit version af Windows på grund af kravene til Skype for Business Online-modulet og et af Microsoft 365-modulerne.
    
- Du skal installere de moduler, der kræves til Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online og Teams:
    
  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Skype for Business Online, PowerShell-modul](/microsoftteams/teams-powershell-overview)
  - [Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Teams oversigt over PowerShell](/microsoftteams/teams-powershell-overview)
    
-  PowerShell skal konfigureres til at køre signerede scripts til Skype for Business Online og Security &amp; Compliance Center. Kør følgende kommando i en eleveret PowerShell-session (en PowerShell-session, som du **kører som administrator**).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Forbindelsestrin, når du kun bruger en adgangskode

Følg disse trin for at oprette forbindelse til alle tjenesterne i et enkelt PowerShell-vindue, når du kun bruger en adgangskode til at logge på.
  
1. Åbn Windows PowerShell.
    
2. Kør denne kommando, og angiv dine Microsoft 365 legitimationsoplysninger til din arbejds- eller skolekonto.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Kør denne kommando for at oprette forbindelse til Azure AD ved hjælp af Azure Active Directory PowerShell til Graph-modul.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Eller, hvis du bruger modulet Microsoft Azure Active Directory til Windows PowerShell, skal du køre denne kommando.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Du skal køre disse cmdlet'er fra PowerShell.

4. Kør disse kommandoer for at oprette forbindelse til SharePoint Online. Angiv organisationens navn for dit domæne. For "litwareinc\. onmicrosoft.com", er værdien af organisationens navn "litwareinc".
    
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
   > Hvis du vil oprette Exchange Online til Microsoft 365 andre skyer end Worldwide, skal [du Forbind to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. Kør disse kommandoer for at oprette forbindelse til Security &amp; Compliance Center.
    
   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!Note]
   > Hvis du vil oprette forbindelse til Security &amp; Compliance Center til Microsoft 365 andre skyer end Worldwide, skal [du Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

7. Kør disse kommandoer for at oprette forbindelse til Teams PowerShell (og Skype for Business Online).
    
   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-udgivelse, behøver du ikke at installere Skype for Business Online Connector.
  
   > [!Note]
   > Hvis du vil oprette Microsoft Teams til andre skyer end *Worldwide*, [skal Forbind-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).
  


### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory PowerShell til Graph modul

Her er kommandoerne for alle tjenesterne i en enkelt blok, når du bruger Azure Active Directory PowerShell til Graph modul. Angiv navnet på din domænevært og UPN for at logge på, og kør dem alle på samme tid.
  
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
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory modul til Windows PowerShell modul

Her er kommandoerne for alle tjenesterne i en enkelt blok, når du bruger Microsoft Azure Active Directory-modulet til Windows PowerShell modul. Angiv navnet på din domænevært og UPN for logon, og kør dem alle på én gang.
  
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
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Forbindelsestrin ved brug af multifaktorgodkendelse

### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory PowerShell til Graph modul

Her er alle kommandoerne i en enkelt blok til at oprette forbindelse til flere Microsoft 365-tjenester, når du bruger multifaktorgodkendelse med Azure Active Directory PowerShell til Graph-modulet.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
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
### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory modul til Windows PowerShell modul

Her er alle kommandoerne i en enkelt blok til at oprette forbindelse til flere Microsoft 365-tjenester, når du bruger multifaktorgodkendelse med Microsoft Azure Active Directory-modulet til Windows PowerShell-modulet.

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

Du lukker PowerShell-vinduet ved at køre denne kommando for at fjerne de aktive sessioner for at SharePoint Online og Teams:
  
```powershell
Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="see-also"></a>Se også

- [Forbind at Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md)
- [Administrer SharePoint Online med PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
