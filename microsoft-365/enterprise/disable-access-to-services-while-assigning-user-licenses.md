---
title: Deaktiver adgang til Microsoft 365 tjenester under tildeling af brugerlicenser
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du tildeler licenser til brugerkonti og deaktiverer specifikke tjenesteplaner på samme tid ved hjælp af PowerShell til Microsoft 365.
ms.openlocfilehash: 6c0c3a3860da8a1935152fcaefb29f2f355cfa49
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095724"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>Deaktiver adgang til Microsoft 365 tjenester under tildeling af brugerlicenser

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 abonnementer leveres med tjenesteplaner for individuelle tjenester. Microsoft 365 administratorer skal ofte deaktivere visse planer, når de tildeler licenser til brugere. Med vejledningen i denne artikel kan du tildele en Microsoft 365 licens, samtidig med at du deaktiverer bestemte tjenesteplaner ved hjælp af PowerShell for en individuel brugerkonto eller flere brugerkonti.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


Derefter skal du angive licensplanerne for din lejer med denne kommando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Derefter skal du hente logonnavnet på den konto, du vil føje en licens til, også kendt som brugerens hovednavn (UPN).

Derefter skal du kompilere en liste over tjenester, der skal aktiveres. Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

For kommandoblokken nedenfor skal du udfylde brugerens hovednavn på brugerkontoen, SKU-delnummeret og listen over tjenesteplaner, der skal aktiveres og fjernes den forklarende tekst og tegnene \< and > . Kør derefter de resulterende kommandoer ved PowerShell-kommandoprompten.

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

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Kør derefter denne kommando for at se dine aktuelle abonnementer:

```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

I visningen af kommandoen  `Get-MsolAccountSku` :

- **AccountSkuId** er et abonnement for din organisation i \<OrganizationName>:\<Subscription> format. \<OrganizationName> er den værdi, du angav, da du tilmeldte dig Microsoft 365, og er entydig for din organisation. Værdien \<Subscription> er for et bestemt abonnement. For litwareinc:ENTERPRISEPACK er organisationsnavnet litwareinc, og abonnementsnavnet er ENTERPRISEPACK (Office 365 Enterprise E3).

- **ActiveUnits** er antallet af licenser, du har købt til abonnementet.

- **WarningUnits** er antallet af licenser i et abonnement, som du ikke har fornyet, og som udløber efter den 30-dages respitperiode.

- **ConsumedUnits** er antallet af licenser, du har tildelt til brugere for abonnementet.

Bemærk AccountSkuId for dit Microsoft 365-abonnement, der indeholder de brugere, du vil licensere. Sørg også for, at der er nok licenser til at tildele (træk **Forbrugte enheder** fra **ActiveUnits**).

Kør derefter denne kommando for at få vist oplysninger om de Microsoft 365-tjenesteplaner, der er tilgængelige i alle dine abonnementer:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

I visningen af denne kommando skal du bestemme, hvilke tjenesteplaner du vil deaktivere, når du tildeler licenser til brugere.

Her er en delvis liste over tjenesteplaner og deres tilsvarende Microsoft 365 tjenester.

I følgende tabel vises Microsoft 365-tjenesteplaner og deres brugervenlige navne for de mest almindelige tjenester. Listen over tjenesteplaner kan være anderledes.

|**Serviceplan**|**Beskrivelse**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(tidligere kaldet Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |

Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Nu, hvor du har AccountSkuId og tjenesteplanerne til at deaktivere, kan du tildele licenser til en individuel bruger eller til flere brugere.

### <a name="for-a-single-user"></a>For en enkelt bruger

For en enkelt bruger skal du udfylde brugerens hovednavn på brugerkontoen, AccountSkuId og listen over tjenesteplaner til deaktivering og fjernelse af den forklarende tekst og tegnene \< and > . Kør derefter de resulterende kommandoer ved PowerShell-kommandoprompten.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

Her er et eksempel på en kommandoblok for den konto, der hedder belindan@contoso.com, for contoso:ENTERPRISEPACK-licensen, og de tjenesteplaner, der skal deaktiveres, er RMS_S_ENTERPRISE, SWAY, INTUNE_O365 og YAMMER_ENTERPRISE:

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

Hvis du vil udføre denne administrationsopgave for flere brugere, skal du oprette en tekstfil med kommaseparerede værdier (CSV), der indeholder felterne UserPrincipalName og UsageLocation. Her er et eksempel:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

Udfyld derefter placeringen af CSV-input- og outputfilerne, konto-SKU-id'et og listen over tjenesteplaner, der skal deaktiveres, og kør derefter de resulterende kommandoer ved PowerShell-kommandoprompten.

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

- Tildeler tilpassede licenser til hver bruger.

- Opretter en CSV-fil med alle de brugere, der er behandlet, og viser deres licensstatus.

## <a name="see-also"></a>Se også

[Deaktiver adgang til Microsoft 365-tjenester med PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)