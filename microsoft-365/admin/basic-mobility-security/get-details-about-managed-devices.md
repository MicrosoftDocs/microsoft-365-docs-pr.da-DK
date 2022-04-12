---
title: Få oplysninger om administrerede enheder til Basic Mobility og Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Brug Windows PowerShell til at få oplysninger om Basic Mobility- og Security-enheder i din organisation.
ms.openlocfilehash: 4cac15e8377370e4bd2f8b359a39aaf830f13d10
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781067"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Få oplysninger om administrerede enheder til Basic Mobility og Security

I denne artikel kan du se, hvordan du bruger Windows PowerShell til at få oplysninger om de enheder i din organisation, du har konfigureret til Grundlæggende mobilitet og sikkerhed.

Her er en oversigt over de enhedsoplysninger, der er tilgængelige for dig.

|Detaljer|Hvad skal du kigge efter i PowerShell?|
|---|---|
|Enheden er tilmeldt Basic Mobility and Security. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility and Security](enroll-your-mobile-device.md)|Værdien af parameteren *isManaged* er:<br/>**True**= enheden er tilmeldt.<br/>**False**= enheden er ikke tilmeldt.|
|Enheden er kompatibel med dine politikker for enhedssikkerhed. Du kan finde flere oplysninger under [Opret politikker for enhedssikkerhed](create-device-security-policies.md)|Værdien af parameteren *isCompliant* er:<br/>**True** = enheden er kompatibel med politikker.<br/>**False** = enheden er ikke kompatibel med politikker.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="PowerShell-parametrene Basic Mobility og Security.":::

> [!NOTE]
> Kommandoerne og scriptene i denne artikel returnerer også oplysninger om alle enheder, der administreres af [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Før du begynder

Der er et par ting, du skal konfigurere for at køre de kommandoer og scripts, der er beskrevet i denne artikel.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Trin 1: Download og installér Azure Active Directory-modulet til Windows PowerShell

Du kan finde flere oplysninger om disse trin under [Forbind at Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Gå til [Microsoft Online Services Sign-In Assistant for IT Professionals RTWl](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) , og vælg **Download for Logonassistent til Microsoft Online Services**.

2. Installér Microsoft Azure Active Directory modulet til Windows PowerShell ved hjælp af disse trin:

    1. Åbn en PowerShell-kommandoprompt på administratorniveau.

    2. Kør kommandoen `Install-Module MSOnline` .

    3. Hvis du bliver bedt om at installere NuGet-udbyderen, skal du skrive Y og trykke på ENTER.

    4. Hvis du bliver bedt om at installere modulet fra PSGallery, skal du skrive Y og trykke på ENTER.

    5. Luk PowerShell-kommandovinduet efter installationen.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Trin 2: Forbind til dit Microsoft 365-abonnement

1. Kør følgende kommando i Windows Azure Active Directory Module for Windows PowerShell.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. I dialogboksen Windows PowerShell anmodning om legitimationsoplysninger skal du skrive brugernavnet og adgangskoden for din Microsoft 365 globale administratorkonto og derefter vælge **OK**.

3. Kør følgende kommando.

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Trin 3: Sørg for, at du kan køre PowerShell-scripts

> [!NOTE]
> Du kan springe dette trin over, hvis du allerede er konfigureret til at køre PowerShell-scripts.

Hvis du vil køre Get-MsolUserDeviceComplianceStatus.ps1-scriptet, skal du aktivere kørsel af PowerShell-scripts.

1. Vælg **Start** i din Windows Desktop, og skriv derefter Windows PowerShell. Højreklik på Windows PowerShell, og vælg derefter **Kør som administrator**.

2. Kør følgende kommando.

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

3. Når du bliver bedt om det, skal du skrive Y og derefter trykke på Enter.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Kør cmdlet'en Get-MsolDevice for at få vist oplysninger om alle enheder i organisationen

1. Åbn Windows PowerShell Microsoft Azure Active Directory modulet.

2. Kør følgende kommando.

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Du kan få flere eksempler under [Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>Kør et script for at få enhedsoplysninger

Gem først scriptet på computeren.

1. Kopiér og indsæt følgende tekst i Notesblok.

   ```powershell
   param (
   [PSObject[]]$users = @(),
   [Switch]$export,
   [String]$exportFileName = "UserDeviceComplianceStatus_" + (Get-Date -Format "yyMMdd_HHMMss") + ".csv",
   [String]$exportPath = [Environment]::GetFolderPath("Desktop")
   )
   [System.Collections.IDictionary]$script:schema = @{
   DeviceId = ''
   DeviceOSType = ''
   DeviceOSVersion = ''
   DeviceTrustLevel = ''
   DisplayName = ''
   IsCompliant = ''
   IsManaged = ''
   ApproximateLastLogonTimestamp = ''
   DeviceObjectId = ''
   RegisteredOwnerUpn = ''
   RegisteredOwnerObjectId = ''
   RegisteredOwnerDisplayName = ''
   }
   function createResultObject
   {
   [PSObject]$resultObject = New-Object -TypeName PSObject -Property $script:schema
   return $resultObject
   }
   If ($users.Count -eq 0)
   {
   $users = Get-MsolUser
   }
   [PSObject[]]$result = foreach ($u in $users)
   {
   [PSObject]$devices = get-msoldevice -RegisteredOwnerUpn $u.UserPrincipalName
   foreach ($d in $devices)
   {
   [PSObject]$deviceResult = createResultObject
   $deviceResult.DeviceId = $d.DeviceId
   $deviceResult.DeviceOSType = $d.DeviceOSType
   $deviceResult.DeviceOSVersion = $d.DeviceOSVersion
   $deviceResult.DeviceTrustLevel = $d.DeviceTrustLevel
   $deviceResult.DisplayName = $d.DisplayName
   $deviceResult.IsCompliant = $d.GraphDeviceObject.IsCompliant
   $deviceResult.IsManaged = $d.GraphDeviceObject.IsManaged
   $deviceResult.DeviceObjectId = $d.ObjectId
   $deviceResult.RegisteredOwnerUpn = $u.UserPrincipalName
   $deviceResult.RegisteredOwnerObjectId = $u.ObjectId
   $deviceResult.RegisteredOwnerDisplayName = $u.DisplayName
   $deviceResult.ApproximateLastLogonTimestamp = $d.ApproximateLastLogonTimestamp
   $deviceResult
   }
   }
   If ($export)
   {
   $result | Export-Csv -path ($exportPath + "\" + $exportFileName) -NoTypeInformation
   }
   Else
   {
   $result
   }
   ```

2. Gem den som en Windows PowerShell scriptfil ved hjælp af filtypenavnet .ps1, f.eks. Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Kør scriptet for at hente enhedsoplysninger for en enkelt brugerkonto

1. Åbn Windows PowerShell Microsoft Azure Active Directory modulet.

2. Gå til den mappe, hvor du gemte scriptet. Hvis du f.eks. har gemt den i C:\PS-Scripts, skal du køre følgende kommando.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Kør følgende kommando for at identificere den bruger, du vil hente enhedsoplysninger for. Dette eksempel henter oplysninger om bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Kør følgende kommando for at starte scriptet.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Oplysningerne eksporteres til din Windows Desktop som en CSV-fil. Du kan bruge yderligere parametre til at angive filnavnet og stien til CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Kør scriptet for at hente enhedsoplysninger for en gruppe af brugere

1. Åbn Windows PowerShell Microsoft Azure Active Directory modulet.

2. Gå til den mappe, hvor du gemte scriptet. Hvis du f.eks. har gemt den i C:\PS-Scripts, skal du køre følgende kommando.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Kør følgende kommando for at identificere den gruppe, du vil hente enhedsoplysninger for. Dette eksempel henter oplysninger om brugere i gruppen FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Kør følgende kommando for at starte scriptet.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Oplysningerne eksporteres til din Windows Desktop som en CSV-fil. Du kan bruge yderligere parametre til at angive filnavnet og stien til CSV.

## <a name="related-topics"></a>Relaterede emner

[Microsoft Forbind er udgået](/collaborate/connect-redirect)

[Oversigt over Basic Mobility og Security](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
