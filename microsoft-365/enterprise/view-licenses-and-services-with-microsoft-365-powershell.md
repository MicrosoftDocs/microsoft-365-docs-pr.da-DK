---
title: Få Microsoft 365 licenser og tjenester med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Forklarer, hvordan du bruger PowerShell til at få vist oplysninger om de licensplaner, -tjenester og -licenser, der er tilgængelige i Microsoft 365 organisation.
ms.openlocfilehash: 3b90596c68e3beadcc2b33ef59ff9c3503b84f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601585"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Få Microsoft 365 licenser og tjenester med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hver Microsoft 365-abonnement består af følgende elementer:

- **Licensplaner** Disse er også kendt som licensplaner eller Microsoft 365-planer. Licensplaner definerer de Microsoft 365, der er tilgængelige for brugerne. Dit Microsoft 365-abonnement kan indeholde flere licensabonnementer. Et eksempel på en licensplan kunne Microsoft 365 E3.
    
- **Tjenester** Disse kaldes også for serviceplaner. Tjenester er de Microsoft 365-produkter, -funktioner og -egenskaber, der er tilgængelige i hver licensplan, f.eks. Exchange Online og Microsoft 365 Apps for enterprise (tidligere navngivet Office 365 ProPlus). Brugere kan have tildelt flere licenser fra forskellige licensplaner, der giver adgang til forskellige tjenester.
    
- **Licenser** Hver licensplan indeholder det antal licenser, du har købt. Du tildeler licenser til brugerne, så de kan bruge de Microsoft 365, der er defineret i licensplanen. Hver brugerkonto kræver mindst én licens fra én licensplan, så de kan logge på Microsoft 365 og bruge tjenesterne.
    
Du kan bruge PowerShell Microsoft 365 til at få vist oplysninger om de tilgængelige licensplaner, licenser og tjenester i din Microsoft 365 organisation. Du kan finde flere oplysninger om de produkter, funktioner og tjenester, der er tilgængelige Office 365 forskellige Office 365 [under Indstillinger for abonnementsplan](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug Azure Active Directory PowerShell til Graph modul

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Kør denne kommando for at få vist oversigtsoplysninger om dine aktuelle licensplaner og de tilgængelige licenser for hver plan:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Resultaterne indeholder:
  
- **SKUPartNumber:** Viser de tilgængelige licensplaner for din organisation. Er for eksempel `ENTERPRISEPACK` navnet på licensabonnementet til Office 365 Enterprise E3.
    
- **Aktiveret:** Antal licenser, du har købt til en bestemt licensplan.
    
- **ForbrugsvarerEnheder:** Antal licenser, du har tildelt til brugere fra en bestemt licensplan.
    
Hvis du vil have vist oplysninger Microsoft 365, der er tilgængelige i alle dine licensplaner, skal du først få vist en liste over dine licensplaner.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Gem derefter oplysningerne om licensplaner i en variabel.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Derefter skal du vise tjenesterne i et bestemt licensabonnement.

```powershell
$licenses[<index>].ServicePlans
```

\<index> er et heltal, der angiver rækkenummeret for licensplanen fra visningen af `Get-AzureADSubscribedSku | Select SkuPartNumber` kommandoen minus 1.

Hvis f.eks. visningen af `Get-AzureADSubscribedSku | Select SkuPartNumber` kommandoen er dette:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Derefter er kommandoen til at vise tjenesterne for ENTERPRISEPREMIUM-licensplanen:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM er den tredje række. Indeksværdien er derfor (3 - 1) eller 2.

Du kan finde en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede serviceplaner og deres tilsvarende brugervenlige navne under Produktnavne og serviceplanidentifikatorer [for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først skal [du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Der findes et PowerShell-script, der automatiserer de procedurer, der er beskrevet i dette emne. Med scriptet kan du få vist og deaktivere tjenester i din Microsoft 365, herunder Sway. Få mere at vide under [Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Kør følgende kommando for at få vist oversigtsoplysninger om dine aktuelle licensplaner og de tilgængelige licenser for hver plan:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Resultaterne indeholder følgende oplysninger:
  
- **AccountSkuId:** Vis de tilgængelige licensplaner for organisationen ved hjælp af syntaksen `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ er den værdi, du har angivet, da du tilmeldte Microsoft 365, og er unik for din organisation. Værdien _\<LicensingPlan>_ er den samme for alle. For eksempel er i værdien `litwareinc:ENTERPRISEPACK`, `litwareinc`firmanavnet , og navnet på licensplanen`ENTERPRISEPACK`, som er systemnavnet for Office 365 Enterprise E3.
    
- **ActiveUnits:** Antal licenser, du har købt til en bestemt licensplan.
    
- **WarningUnits:** Antal licenser i en licensplan, som du ikke har fornyet, og som udløber efter de 30 dage.
    
- **ForbrugsvarerEnheder:** Antal licenser, du har tildelt til brugere fra en bestemt licensplan.
    
Hvis du vil have vist oplysninger Microsoft 365 de tjenester, der er tilgængelige i alle dine licensplaner, skal du køre følgende kommando:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Følgende tabel viser de Microsoft 365 og deres brugervenlige navne for de mest almindelige tjenester. Din liste over serviceplaner kan være anderledes. 
  
|**Serviceplan**|**Beskrivelse**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(tidligere navngivet Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online plan 2  <br/> |
   
Du kan finde en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede serviceplaner og deres tilsvarende brugervenlige navne under Produktnavne og serviceplanidentifikatorer [for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Hvis du vil have vist oplysninger Microsoft 365 de tjenester, der er tilgængelige i en bestemt licensplan, skal du bruge følgende syntaks.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

I dette eksempel vises de tjenester, der er tilgængelige i abonnementsplanen litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)