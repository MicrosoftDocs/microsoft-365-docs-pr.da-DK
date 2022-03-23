---
title: Deaktiver adgang til Microsoft 365 tjenester, mens du tildeler brugerlicenser
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Få mere at vide om, hvordan du tildeler licenser til brugerkonti og deaktiverer bestemte serviceplaner på samme tid ved hjælp af PowerShell Microsoft 365.
ms.openlocfilehash: 5b7130930097970f5cfabc9a7599c211393b7c7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590562"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Deaktiver adgang til Microsoft 365 tjenester, mens du tildeler brugerlicenser

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365-abonnementer fås med serviceplaner for individuelle tjenester. Microsoft 365 administratorer har ofte brug for at deaktivere visse planer, når de tildeler licenser til brugere. Med instruktionerne i denne artikel kan du tildele en Microsoft 365-licens, mens du deaktiverer bestemte serviceplaner ved hjælp af PowerShell for en individuel brugerkonto eller flere brugerkonti.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Dernæst skal du oprette en liste over licensplaner for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Dernæst skal du hente logonnavnet på den konto, du vil føje en licens til, også kaldet brugerens hovednavn (UPN).

Dernæst skal du samle en liste over tjenester, der skal aktiveres. Du kan finde en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede serviceplaner og deres tilsvarende brugervenlige navne under Produktnavne og serviceplanidentifikatorer [for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

For kommandoblokken nedenfor skal du angive brugerens hovednavn på brugerkontoen, varenummeret for SKU'en og listen over serviceplaner \< and > for at aktivere og fjerne forklarende tekst og tegnene. Kør derefter de resulterende kommandoer ved PowerShell-kommandoprompten.

```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kør derefter denne kommando for at få vist dine aktuelle abonnementer:

```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Gør følgende i visningen af  `Get-MsolAccountSku` kommandoen:

- **AccountSkuId** er et abonnement til din organisation i \<OrganizationName>:\<Subscription> format. Det \<OrganizationName> er den værdi, du angivne, da du tilmeldte dig Microsoft 365, og er entydig for din organisation. Værdien \<Subscription> er for et bestemt abonnement. For litwareinc:ENTERPRISEPACK er organisationsnavnet litwareinc, og abonnementsnavnet er ENTERPRISEPACK (Office 365 Enterprise E3).

- **ActiveUnits** er antallet af licenser, du har købt til abonnementet.

- **WarningUnits** er antallet af licenser i et abonnement, du ikke har fornyet, og som udløber efter de 30 dage.

- **ConsumedUnits** er det antal licenser, du har tildelt til brugere for abonnementet.

Bemærk AccountSkuId for dit Microsoft 365, der indeholder de brugere, du vil licensere. Du skal også sikre dig, at der er tilstrækkeligt mange licenser til at tildele ( **subtrahere Forbrugteenheder** **fra ActiveUnits**).

Kør derefter denne kommando for at få vist oplysninger om de Microsoft 365 serviceabonnementer, der er tilgængelige i alle dine abonnementer:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

I visningen af denne kommando skal du bestemme, hvilke serviceplaner du vil deaktivere, når du tildeler licenser til brugere.

Her er en delvis liste over serviceplaner og deres tilsvarende Microsoft 365 tjenester.

Følgende tabel viser de Microsoft 365 og deres brugervenlige navne for de mest almindelige tjenester. Din liste over serviceplaner kan være anderledes.

|**Serviceplan**|**Beskrivelse**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(tidligere navngivet Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online plan 2  <br/> |

Du kan finde en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede serviceplaner og deres tilsvarende brugervenlige navne under Produktnavne og serviceplanidentifikatorer [for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Nu hvor du har AccountSkuId og serviceplanerne til at deaktivere, kan du tildele licenser til en enkelt bruger eller for flere brugere.

### <a name="for-a-single-user"></a>For en enkelt bruger

For en enkelt bruger skal du angive brugerens hovednavn på brugerkontoen, AccountSkuId'et og listen over serviceplaner \< and > for at deaktivere og fjerne forklarende tekst og tegnene. Kør derefter de resulterende kommandoer ved PowerShell-kommandoprompten.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Her er et eksempel på en kommandoblok for kontoen med navnet belindan@contoso.com, for contoso:ENTERPRISEPACK-licensen, og de serviceplaner, der skal deaktiveres, er RMS_S_ENTERPRISE, SWAY, INTUNE_O365 og YAMMER_ENTERPRISE:

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>For flere brugere

For at udføre denne administrationsopgave for flere brugere skal du oprette en kommasepareret tekstfil (CSV), der indeholder felterne UserPrincipalName og UsageLocation. Her er et eksempel:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Dernæst skal du angive placeringen for csv-filerne til input og output, konto-SKU-id'et og listen over serviceplaner, der skal deaktiveres, og derefter køre de resulterende kommandoer ved kommandoprompten i PowerShell.

```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Denne PowerShell-kommandoblok:

- Viser brugerens hovednavn for hver bruger.

- Tildeler tilpassede licenser til hver enkelt bruger.

- Opretter en CSV-fil med alle de brugere, der blev behandlet, og viser deres licensstatus.

## <a name="see-also"></a>Se også

[Deaktiver adgang til Microsoft 365-tjenester med PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)