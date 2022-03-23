---
title: Forbind at Microsoft 365 med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Forbind din Microsoft 365 lejer ved hjælp af PowerShell Microsoft 365 at udføre administrationsopgaver fra kommandolinjen.
ms.openlocfilehash: 67c3a596d1b0d7acec2925f39c2f6bd8025d7d4a
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63591588"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Forbind at Microsoft 365 med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

PowerShell til Microsoft 365 giver dig mulighed for at Microsoft 365 indstillingerne fra kommandolinjen. For at oprette forbindelse til PowerShell skal du blot installere den nødvendige software og derefter oprette forbindelse til Microsoft 365 organisation.

Der findes to versioner af PowerShell-modulet, som du kan bruge til at oprette forbindelse til Microsoft 365 administrere brugerkonti, grupper og licenser:

- Azure Active Directory PowerShell til Graph, hvis cmdlet'er *indeholder AzureAD* i deres navn
- Microsoft Azure Active Directory modulet til Windows PowerShell, hvis cmdlet'er indeholder *Msol* i deres navn

I øjeblikket erstatter Azure Active Directory PowerShell til Graph-modulet ikke funktionaliteten i Microsoft Azure Active Directory-modulet til Windows PowerShell-modul til bruger-, gruppe- og licensadministration. I nogle tilfælde skal du bruge begge versioner. Du kan roligt installere begge versioner på den samme computer.

>[!Note]
>Du kan også oprette forbindelse til [Azure Cloud Shell](#connect-with-the-azure-cloud-shell) fra Microsoft 365 Administration.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?


**Operativsystem**

Du skal bruge en 64-bit version af Windows. Understøttelse af 32-bit versionen af Microsoft Azure Active Directory til Windows PowerShell udløb i 2014.

Du kan bruge følgende versioner af Windows:
    
  - Windows 10, Windows 8.1, Windows 8 eller Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1

>[!Note]
>Til Windows 8.1 skal du Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 og Windows Server 2008 R2 SP1, downloade og installere [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- Til Azure Active Directory PowerShell til Graph skal du bruge PowerShell version 5.1.

- Til Microsoft Azure Active Directory til Windows PowerShell skal du bruge PowerShell version 5.1 eller nyere, op til PowerShell version 6. Du kan ikke bruge PowerShell version 7.
       
>[!Note]
>Disse procedurer er beregnet til brugere, der er medlem af Microsoft 365 administratorrolle. Du kan få mere at vide [under Om administratorroller](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Forbind med det Azure Active Directory PowerShell til Graph modul

Kommandoer i Azure Active Directory PowerShell til Graph indeholder *AzureAD i* deres cmdlet-navn. Du kan installere Azure Active Directory [PowerShell til Graph eller](/powershell/azure/active-directory/install-adv2) [Azure PowerShell](/powershell/azure/install-az-ps).

For procedurer, der kræver de nye cmdlet'er i Azure Active Directory PowerShell til Graph-modulet, skal du følge disse trin for at installere modulet og oprette forbindelse til dit Microsoft 365-abonnement.

> [!Note]
> Du kan finde oplysninger om understøttelse af forskellige versioner Windows i [Azure Active Directory PowerShell til Graph modulet](/powershell/azure/active-directory/install-adv2) .

### <a name="step-1-install-the-required-software"></a>Trin 1: Installer den nødvendige software

Disse trin kræves kun én gang på computeren. Men du skal sandsynligvis opdatere softwaren med jævne mellemrum.
  
1. Åbn et administratorvindue Windows PowerShell administratorkommandoprompt (Windows PowerShell administrator).
    
2. Kør denne kommando:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  Som standard er PowerShell Gallery (PSGallery) ikke konfigureret som et pålideligt lager til **PowerShellGet**. Første gang du bruger PSGallery, får du vist følgende meddelelse:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Svar **Ja** eller **Ja til alle for** at fortsætte med installationen.

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Trin 2: Forbind til Azure AD for dit Microsoft 365 abonnement

Hvis du vil oprette forbindelse til Azure Active Directory (Azure AD) for dit Microsoft 365-abonnement med et kontonavn og en adgangskode eller med multifaktorgodkendelse, skal du køre en af disse kommandoer fra en Windows PowerShell-kommandoprompt. (Det behøver ikke at blive hævet).

| Office 365 skyen | Kommando |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-AzureAD` |
| Office 365 drevet af 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Tyskland | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 amerikanske Government DoD og Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

I dialogboksen **Log på din konto** skal du skrive brugernavn og Microsoft 365 din arbejds- eller skolekonto og adgangskode og derefter vælge **OK**.

Hvis du bruger multifaktorgodkendelse, skal du følge vejledningen for at angive yderligere godkendelsesoplysninger, f.eks. en bekræftelseskode.

Når du har forbindelse, kan du bruge cmdlet'erne til [Azure Active Directory PowerShell til Graph modul](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Forbind med Microsoft Azure Active Directory til Windows PowerShell

>[!Note]
>Cmdlet'er i Microsoft Azure Active Directory modulet til Windows PowerShell har *Msol* i deres navn.

PowerShell version 7 og nyere understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Til PowerShell version 7 og nyere skal du bruge Microsoft Graph PowerShell SDK.

PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>Trin 1: Installer den nødvendige software

Disse trin kræves kun én gang på computeren. Men du skal sandsynligvis opdatere softwaren med jævne mellemrum.
  
1.  Hvis du ikke kører Windows 10, skal du installere 32-bit versionen af Microsoft Online Services Logonassistent: [Microsoft Online Services Logonassistent for it-fagfolk RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. Følg disse trin for at installere Microsoft Azure Active Directory Module til Windows PowerShell:
    
   1. Åbn en kommandoprompt med Windows PowerShell administrator (kør Windows PowerShell administrator).
   1.  Kør **kommandoen Install-Module MSOnline** .
   1. Hvis du bliver bedt om at installere udbyderen NuGet, skal du skrive **Y** og trykke på Enter.
   1. Hvis du bliver bedt om at installere modulet fra PSGallery, skal du skrive **Y** og trykke på Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Trin 2: Forbind til Azure AD for dit Microsoft 365 abonnement

Hvis du vil oprette forbindelse til Azure AD for dit Microsoft 365-abonnement med et kontonavn og en adgangskode eller med multifaktorgodkendelse, skal du køre en af disse kommandoer fra en Windows PowerShell-kommandoprompt. (Det behøver ikke at blive hævet).

| Office 365 skyen | Kommando |
|:-------|:-----|
| Office 365 Worldwide (+GCC) | `Connect-MsolService` |
| Office 365 drevet af 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Tyskland | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 amerikanske Government DoD og Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

I dialogboksen **Log på din konto** skal du skrive brugernavn og Microsoft 365 din arbejds- eller skolekonto og adgangskode og derefter vælge **OK**.

Hvis du bruger multifaktorgodkendelse, skal du følge vejledningen for at angive yderligere godkendelsesoplysninger, f.eks. en bekræftelseskode.

### <a name="how-do-you-know-it-worked"></a>Hvordan ved du, at det fungerede?

Hvis du ikke får vist en fejlmeddelelse, har du oprettet forbindelse. For at få en hurtig test skal Microsoft 365 en cmdlet, **f.eks. Get-MsolUser**, og se resultaterne.
  
Hvis du får en fejlmeddelelse, skal du kontrollere følgende problemer:
  
- **Et almindeligt problem er en forkert adgangskode**. Kør [trin 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) igen, og vær opmærksom på det brugernavn og den adgangskode, du angiver.
    
- **Det Microsoft Azure Active Directory modul til Windows PowerShell kræver, at Microsoft .NET Framework 3.5.* x* er aktiveret på computeren**. Det er sandsynligt, at din computer har en nyere version installeret (f.eks. 4 eller 4.5.* x*). Men bagudkompatibilitet med ældre versioner af .NET Framework kan aktiveres eller deaktiveres. Du kan finde flere oplysninger i følgende artikler:
    
  - Hvis Windows server 2012 eller Windows Server 2012 R2, skal du se [Aktivér .NET Framework 3.5](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)) ved hjælp af guiden Tilføj roller og funktioner.
    
  - Hvis Windows 7 eller Windows Server 2008 R2, skal du se Du kan ikke åbne [Azure Active Directory-modulet til Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Du Windows 10 oplysninger Windows 8.1 og Windows 8 i Installere [.NET Framework 3.5 på Windows 10, Windows 8.1 og Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Din version af Microsoft Azure Active Directory til Windows PowerShell kan være forældet.** Du kan kontrollere det ved at køre følgende kommando i PowerShell til Microsoft 365 eller Microsoft Azure Active Directory-modulet til Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Hvis versionsnummeret, der returneres, er lavere end *1.0.8070.2*, skal du fjerne Microsoft Azure Active Directory-modulet til Windows PowerShell og installere fra trin [1](#step-1-install-the-required-software) ovenfor.

- **Hvis du får en forbindelsesfejl,** kan du se [fejlmeddelelsen "Forbind-MsolService: Undtagelse af type blev vist"](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **Hvis du får fejlmeddelelsen "Get-Item: Cannot find path"**, skal du køre denne kommando:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Forbind med Azure Cloud Shell

Hvis du vil oprette forbindelse til og bruge Azure Cloud Shell fra Microsoft 365 Administration, skal du vælge Vinduet PowerShell i øverste højre hjørne af proceslinjen. I **ruden Velkommen til Azure Cloud Shell** skal du vælge **PowerShell**.

Du skal bruge et aktivt Azure-abonnement til din organisation, der er knyttet til dit Microsoft 365 abonnement. Hvis du ikke allerede har en, kan du oprette en. Når du har et Azure-abonnement, åbnes et PowerShell-vindue, hvorfra du kan køre PowerShell-kommandoer og -scripts.

Du kan finde flere oplysninger i [Azure Cloud Shell](/azure/cloud-shell/overview).

## <a name="see-also"></a>Se også

- [Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Forbind til alle Microsoft 365 tjenester i et enkelt Windows PowerShell vindue](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
