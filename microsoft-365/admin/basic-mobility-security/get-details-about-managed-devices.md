---
title: Få mere at vide om enheder, der er administreret af Basic Mobility og Security
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
description: Brug Windows PowerShell til at få oplysninger om Enheder til grundlæggende mobilitet og sikkerhed i din organisation.
ms.openlocfilehash: 25c7f89dda32121306bfe2434620d17396f2e870
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591662"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>Få mere at vide om enheder, der er administreret af Basic Mobility og Security

I denne artikel beskrives det, hvordan du bruger Windows PowerShell til at få mere at vide om de enheder i din organisation, som du har konfigureret til Grundlæggende mobilitet og sikkerhed.

Her er en oversigt over de enhedsoplysninger, der er tilgængelige for dig.

|**Detaljer**|**Hvad du skal søge efter i PowerShell**|
|:----------------|:------------------------------------------------------------------------------|
|Enheden er tilmeldt Grundlæggende mobilitet og sikkerhed. Få mere at vide under [Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md)|Værdien af  *theisManagedparameter*  er:<br/>**True**=-enheden er tilmeldt.<br/>**False**= enhed er ikke tilmeldt. |
|Enheden er kompatibel med sikkerhedspolitikkerne for din enhed. Få mere at vide under [Opret sikkerhedspolitikker for enheder](create-device-security-policies.md)|Værdien af  *isCompliant-parameteret*  er:<br/>**Sand**  = enhed er kompatibel med politikker.<br/>**Falsk**  = enheden ikke er kompatibel med politikker.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="Parametre for Basic Mobility og Security PowerShell.":::

> [!NOTE]
> Kommandoerne og scripts i denne artikel returnerer også oplysninger om enheder, der administreres  [af Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>Før du begynder

Der er et par ting, du skal konfigurere for at køre de kommandoer og scripts, der er beskrevet i denne artikel.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>Trin 1: Download og installér Azure Active Directory-modulet til Windows PowerShell

Du kan finde flere oplysninger om disse  [trin Forbind Microsoft 365 med PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. Gå  [tilMicrosoft Online Services Sign-In assistent til it-fagfolk RTWlog](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi)  vælg  **Download til Logonassistent til Microsoft Online Services**.

2. Installér Microsoft Azure Active Directory modulet til Windows PowerShell med disse trin:

    1. Åbn en PowerShell-kommandoprompt på administratorniveau.

    2. `Install-Module MSOnline` Kør kommandoen.

    3. Hvis du bliver bedt om at installere nuGet-udbyderen, skal du skrive Y og trykke på Enter.

    4. Hvis du bliver bedt om at installere modulet fra PSGallery, skal du skrive Y og trykke på Enter.

    5. Efter installationen skal du lukke PowerShell-kommandovinduet.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>Trin 2: Forbind til dit Microsoft 365-abonnement

1. I Windows Azure Active Directory Module for Windows PowerShell skal du køre følgende kommando.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. I dialogboksen Windows PowerShell legitimationsanmodning skal du skrive brugernavnet og adgangskoden til din globale Microsoft 365 og derefter vælge **OK**.

3. Kør følgende kommando.

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>Trin 3: Sørg for, at du kan køre PowerShell-scripts

> [!NOTE]
> Du kan springe dette trin over, hvis du allerede er konfigureret til at køre PowerShell-scripts.

For at køre Get-MsolUserDeviceComplianceStatus.ps1 script skal du aktivere kørslen af PowerShell-scripts.

1. VælgStart Windows  **dit skrivebord,** og skriv derefter Windows PowerShell. Højreklik på en Windows PowerShell, og vælg  **derefter Kør som administrator**.

2. Kør følgende kommando.

   ```powershell
   Set-ExecutionPolicy  RemoteSigned
   ```

3. Når du bliver bedt om det, skal du skrive Y og derefter trykke på Enter.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>Kør cmdletten Get-MsolDevice for at få vist detaljer for alle enheder i organisationen

1. Åbn Microsoft Azure Active Directory modulet til Windows PowerShell.

2. Kør følgende kommando.

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

Du kan finde flere eksempler  [under Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>Kør et script for at få enhedsoplysninger

Først skal du gemme scriptet på din computer.

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

2. Gem den som en Windows PowerShell-scriptfil ved hjælp af filtypenavnet .ps1, f.eks. Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>Kør scriptet for at hente enhedsoplysninger for en enkelt brugerkonto

1. Åbn Microsoft Azure Active Directory modulet til Windows PowerShell.

2. Gå til den mappe, hvor du gemte scriptet. Hvis du f.eks. har gemt den på C:\PS-Scripts, skal du køre følgende kommando.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Kør følgende kommando for at identificere den bruger, du vil have enhedsoplysninger for. I dette eksempel får du oplysninger om bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. Kør følgende kommando for at starte scriptet.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Oplysningerne eksporteres til dit skrivebord Windows en CSV-fil. Du kan bruge yderligere parametre til at angive filnavnet og stien til CSV-filen.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>Kør scriptet for at få enhedsoplysninger for en gruppe af brugere

1. Åbn Microsoft Azure Active Directory modulet til Windows PowerShell.

2. Gå til den mappe, hvor du gemte scriptet. Hvis du f.eks. har gemt den på C:\PS-Scripts, skal du køre følgende kommando.

   ```powershell
   cd C:\PS-Scripts
   ```

3. Kør følgende kommando for at identificere den gruppe, du vil have enhedsoplysninger for. I dette eksempel får du oplysninger om brugere i gruppen FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. Kør følgende kommando for at starte scriptet.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

Oplysningerne eksporteres til dit skrivebord Windows en CSV-fil. Du kan bruge yderligere parametre til at angive filnavnet og stien til CSV-filen.

## <a name="related-topics"></a>Relaterede emner

[Microsoft Forbind er udgået](/collaborate/connect-redirect)

[Oversigt over Grundlæggende mobilitet og sikkerhed](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
