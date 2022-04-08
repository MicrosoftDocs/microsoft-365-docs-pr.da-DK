---
title: Opret forbindelse til Microsoft 365 med PowerShell
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
description: Forbind til din Microsoft 365 lejer ved hjælp af PowerShell, så Microsoft 365 kan udføre administrationsopgaver fra kommandolinjen.
ms.openlocfilehash: 4083ffdf240664947b1d35e726a400f292b6d3bf
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713487"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Opret forbindelse til Microsoft 365 med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Med PowerShell til Microsoft 365 kan du administrere dine indstillinger for Microsoft 365 fra kommandolinjen. Hvis du vil oprette forbindelse til PowerShell, skal du blot installere den nødvendige software og derefter oprette forbindelse til din Microsoft 365 organisation.

Der er to versioner af PowerShell-modulet, som du kan bruge til at oprette forbindelse til Microsoft 365 og administrere brugerkonti, grupper og licenser:

- Azure Active Directory PowerShell til Graph, hvis cmdlet'er indeholder *AzureAD* i deres navn
- Microsoft Azure Active Directory Modul til Windows PowerShell, hvis cmdlet'er indeholder *Msol* i deres navn

I øjeblikket erstatter modulet Azure Active Directory PowerShell til Graph ikke helt funktionerne i Microsoft Azure Active Directory modulet for Windows PowerShell modul til bruger-, gruppe- og licensadministration. I nogle tilfælde skal du bruge begge versioner. Du kan sikkert installere begge versioner på den samme computer.

>[!Note]
>Du kan også oprette forbindelse til [Azure Cloud Shell](#connect-with-the-azure-cloud-shell) fra Microsoft 365 Administration.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?


**Operativsystem**

Du skal bruge en 64-bit version af Windows. Understøttelse af 32-bit versionen af Microsoft Azure Active Directory modulet for Windows PowerShell ophørt i 2014.

Du kan bruge følgende versioner af Windows:
    
  - Windows 10, Windows 8.1, Windows 8 eller Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 eller Windows Server 2008 R2 SP1

>[!Note]
>Hvis du vil have Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 og Windows Server 2008 R2 SP1, skal du hente og installere [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- Til modulet Azure Active Directory PowerShell til Graph skal du bruge PowerShell version 5.1.

- I forbindelse med modulet Microsoft Azure Active Directory til Windows PowerShell skal du bruge PowerShell version 5.1 eller nyere op til PowerShell version 6. Du kan ikke bruge PowerShell version 7.
       
>[!Note]
>Disse procedurer er beregnet til brugere, der er medlemmer af en Microsoft 365 administratorrolle. Du kan få flere oplysninger under [Om administratorroller](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Forbind med modulet Azure Active Directory PowerShell til Graph

Kommandoer i Azure Active Directory PowerShell til Graph modul har *AzureAD* i deres cmdlet-navn. Du kan installere [det Azure Active Directory PowerShell til Graph-modul](/powershell/azure/active-directory/install-adv2) eller [Azure PowerShell](/powershell/azure/install-az-ps).

I forbindelse med procedurer, der kræver de nye cmdlet'er i modulet Azure Active Directory PowerShell til Graph, skal du følge disse trin for at installere modulet og oprette forbindelse til dit Microsoft 365 abonnement.

> [!Note]
> Du kan få oplysninger om understøttelse af forskellige versioner af Windows under [Azure Active Directory PowerShell til Graph modul](/powershell/azure/active-directory/install-adv2) .

### <a name="step-1-install-the-required-software"></a>Trin 1: Installér den påkrævede software

Disse trin kræves kun én gang på computeren. Men du skal sandsynligvis opdatere softwaren med jævne mellemrum.
  
1. Åbn et kommandopromptvindue med administratorrettigheder Windows PowerShell (kør Windows PowerShell som administrator).
    
2. Kør denne kommando:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  PowerShell-galleriet (PSGallery) er som standard ikke konfigureret som et lager, der er tillid til, for **PowerShellGet**. Første gang du bruger PSGallery, får du vist følgende meddelelse:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Svar **ja** eller **Ja til alle** for at fortsætte installationen.

3.  Kør denne kommando for at importere modulet:
    
    ```powershell
    Import-Module  AzureAD
    ```
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Trin 2: Forbind til Azure AD for dit Microsoft 365-abonnement

Hvis du vil oprette forbindelse til Azure Active Directory (Azure AD) for dit Microsoft 365-abonnement med et kontonavn og en adgangskode eller med multifaktorgodkendelse, skal du køre en af disse kommandoer fra en kommandoprompt Windows PowerShell. (Det behøver ikke at blive forøget).

| Office 365 cloud | Kommando |
|:-------|:-----|
| Office 365 i hele verden (+GCC) | `Connect-AzureAD` |
| Office 365 drevet af 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Tyskland | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 amerikanske offentlige dod og Office 365 amerikanske GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

I dialogboksen **Log på din konto** skal du skrive brugernavnet og adgangskoden til din Microsoft 365 arbejds- eller skolekonto og derefter vælge **OK**.

Hvis du bruger multifaktorgodkendelse, skal du følge vejledningen for at angive yderligere godkendelsesoplysninger, f.eks. en bekræftelseskode.

Når du har oprettet forbindelse, kan du bruge cmdlet'erne til [modulet Azure Active Directory PowerShell til Graph](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Forbind Windows PowerShell med Microsoft Azure Active Directory modulet

>[!Note]
>Cmdlet'er i Microsoft Azure Active Directory module for Windows PowerShell har *Msol* i deres navn.

PowerShell version 7 og nyere understøtter ikke det Microsoft Azure Active Directory modul til Windows PowerShell modul og cmdlet'er med *Msol* i deres navn. Til PowerShell version 7 og nyere skal du bruge Microsoft Graph PowerShell SDK.

PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med *Msol* i deres navn. Kør disse cmdlet'er fra Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>Trin 1: Installér den påkrævede software

Disse trin kræves kun én gang på computeren. Men du skal sandsynligvis opdatere softwaren med jævne mellemrum.
  
1.  Hvis du ikke kører Windows 10, skal du installere 32-bit versionen af Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. Følg disse trin for at installere Microsoft Azure Active Directory modulet til Windows PowerShell:
    
   1. Åbn en kommandoprompt med administratorrettigheder Windows PowerShell (kør Windows PowerShell som administrator).
   1.  Kør kommandoen **Install-Module MSOnline** .
   1. Hvis du bliver bedt om at installere NuGet-udbyderen, skal du skrive **Y** og trykke på Enter.
   1. Hvis du bliver bedt om at installere modulet fra PSGallery, skal du skrive **Y** og trykke på Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>Trin 2: Forbind til Azure AD for dit Microsoft 365-abonnement

Hvis du vil oprette forbindelse til Azure AD for dit Microsoft 365-abonnement med et kontonavn og en adgangskode eller med multifaktorgodkendelse, skal du køre en af disse kommandoer fra en Windows PowerShell kommandoprompt. (Det behøver ikke at blive forøget).

| Office 365 cloud | Kommando |
|:-------|:-----|
| Office 365 i hele verden (+GCC) | `Connect-MsolService` |
| Office 365 drevet af 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Tyskland | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 amerikanske offentlige dod og Office 365 amerikanske GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

I dialogboksen **Log på din konto** skal du skrive brugernavnet og adgangskoden til din Microsoft 365 arbejds- eller skolekonto og derefter vælge **OK**.

Hvis du bruger multifaktorgodkendelse, skal du følge vejledningen for at angive yderligere godkendelsesoplysninger, f.eks. en bekræftelseskode.

### <a name="how-do-you-know-it-worked"></a>Hvordan ved du, det virkede?

Hvis du ikke får vist en fejlmeddelelse, har du oprettet forbindelse. Hvis du vil have en hurtig test, skal du køre en Microsoft 365 cmdlet, f.eks **Get-MsolUser**, og se resultaterne.
  
Hvis du får vist en fejlmeddelelse, skal du kontrollere følgende problemer:
  
- **Et almindeligt problem er en forkert adgangskode**. Kør [trin 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) igen, og vær opmærksom på det brugernavn og den adgangskode, du angiver.
    
- **Det Microsoft Azure Active Directory modul til Windows PowerShell kræver, at Microsoft .NET Framework 3.5.* x* er aktiveret på computeren**. Det er sandsynligt, at computeren har en nyere version installeret (f.eks. 4 eller 4.5.* x*). Men bagudkompatibilitet med ældre versioner af .NET Framework kan aktiveres eller deaktiveres. Du kan finde flere oplysninger i følgende artikler:
    
  - Hvis du vil have Windows Server 2012 eller Windows Server 2012 R2, skal du se [Aktivér .NET Framework 3.5 ved hjælp af guiden Tilføj roller og funktioner](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)).
    
  - Du kan se Windows 7 eller Windows Server 2008 R2 under [Du kan ikke åbne Azure Active Directory modulet til Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Hvis du vil have Windows 10, Windows 8.1 og Windows 8, skal du se [Installér .NET Framework 3.5 på Windows 10, Windows 8.1 og Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Din version af Microsoft Azure Active Directory modulet til Windows PowerShell er muligvis forældet.** Hvis du vil kontrollere det, skal du køre følgende kommando i PowerShell for Microsoft 365 eller Microsoft Azure Active Directory Module for Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Hvis det returnerede versionsnummer er lavere end *1.0.8070.2*, skal du fjerne Microsoft Azure Active Directory Module for Windows PowerShell og installere fra [trin 1](#step-1-install-the-required-software) ovenfor.

- **Hvis du får vist en forbindelsesfejlmeddelelse**, skal du se [fejlmeddelelsen "Forbind-MsolService: Undtagelse af typen blev udløst"](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **Hvis du får vist fejlmeddelelsen "Hent element: Stien blev ikke fundet"**, skal du køre denne kommando:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Forbind med Azure Cloud Shell

Hvis du vil oprette forbindelse til og bruge Azure Cloud Shell fra Microsoft 365 Administration, skal du vælge powershell-vinduesikonet i øverste højre hjørne af proceslinjen. I ruden **Velkommen til Azure Cloud Shell** skal du vælge **PowerShell**.

Du skal bruge et aktivt Azure-abonnement til din organisation, der er knyttet til dit Microsoft 365 abonnement. Hvis du ikke allerede har en, kan du oprette en. Når du har et Azure-abonnement, åbnes der et PowerShell-vindue, hvorfra du kan køre PowerShell-kommandoer og -scripts.

Du kan få flere oplysninger under [Azure Cloud Shell](/azure/cloud-shell/overview).

## <a name="see-also"></a>Se også

- [Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Opret forbindelse til alle Microsoft 365 tjenester i et enkelt Windows PowerShell vindue](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
