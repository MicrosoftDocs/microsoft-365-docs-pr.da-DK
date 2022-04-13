---
title: Få vist Microsoft 365 licenser og tjenester med PowerShell
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
description: Beskriver, hvordan du bruger PowerShell til at få vist oplysninger om de licensplaner, -tjenester og -licenser, der er tilgængelige i din Microsoft 365 organisation.
ms.openlocfilehash: 8b5ff01f15e4dea7a44b423609b6533cc5729a5f
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823888"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Få vist Microsoft 365 licenser og tjenester med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvert Microsoft 365 abonnement består af følgende elementer:

- **Licensplaner** Disse kaldes også licensplaner eller Microsoft 365 planer. Licensplaner definerer de Microsoft 365 tjenester, der er tilgængelige for brugerne. Dit Microsoft 365-abonnement kan indeholde flere licensplaner. Et eksempel på en licensplan ville være Microsoft 365 E3.
    
- **Tjenester** Disse kaldes også tjenesteplaner. Tjenester er de Microsoft 365 produkter, funktioner og funktioner, der er tilgængelige i hver licensplan, f.eks. Exchange Online og Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus). Brugerne kan have tildelt flere licenser fra forskellige licensplaner, der giver adgang til forskellige tjenester.
    
- **Licenser** Hver licensplan indeholder antallet af licenser, du har købt. Du tildeler licenser til brugere, så de kan bruge de Microsoft 365 tjenester, der er defineret i licensplanen. Alle brugerkonti kræver mindst én licens fra én licensplan, så de kan logge på Microsoft 365 og bruge tjenesterne.
    
Du kan bruge PowerShell til Microsoft 365 til at få vist oplysninger om de tilgængelige licensplaner, licenser og tjenester i din Microsoft 365 organisation. Du kan få flere oplysninger om de produkter, funktioner og tjenester, der er tilgængelige i forskellige Office 365 abonnementer, under [Office 365 Planindstillinger](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-microsoft-graph-powershell-sdk"></a>Brug Microsoft Graph PowerShell SDK

Først [skal du oprette forbindelse til din Microsoft 365 lejer](/graph/powershell/get-started#authentication).

Hvis du vil læse licensplaner for abonnementer, skal du have området Organization.Read.All eller en af de andre tilladelser, der er angivet på [siden "List subscribedSkus" Graph API-referenceside](/graph/api/subscribedsku-list).

```powershell
Connect-Graph -Scopes Organization.Read.All
```

Hvis du vil have vist oversigtsoplysninger om dine aktuelle licensplaner og de tilgængelige licenser for hver plan, skal du køre denne kommando:
  
```powershell
Get-MgSubscribedSku | Select -Property Sku*, ConsumedUnits -ExpandProperty PrepaidUnits | Format-List
```

Resultaterne indeholder:
  
- **SkuPartNumber:** Viser de tilgængelige licensplaner for din organisation. Er f.eks`ENTERPRISEPACK`. navnet på licensplanen for Office 365 Enterprise E3.
    
- **Aktiveret:** Antal licenser, du har købt til en bestemt licensplan.
    
- **Forbrugte enheder:** Antal licenser, du har tildelt til brugere fra en bestemt licensplan.
    
Hvis du vil have vist oplysninger om de Microsoft 365 tjenester, der er tilgængelige i alle dine licensplaner, skal du først få vist en liste over dine licensplaner.

```powershell
Get-MgSubscribedSku
```

Gem derefter oplysningerne om licensplanerne i en variabel.

```powershell
$licenses = Get-MgSubscribedSku
```

Derefter skal du få vist tjenesterne i en bestemt licensplan.

```powershell
$licenses[<index>].ServicePlans
```

\<index> er et heltal, der angiver rækkenummeret for licensplanen fra visningen af `Get-MgSubscribedSku | Select SkuPartNumber` kommandoen minus 1.

Hvis visningen af `Get-MgSubscribedSku | Select SkuPartNumber` kommandoen f.eks. er følgende:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Kommandoen til visning af tjenesterne for ENTERPRISEPREMIUM-licensplanen er følgende:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM er den tredje række. Derfor er indeksværdien (3-1) eller 2.

Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Brug modulet Azure Active Directory PowerShell til Graph

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Hvis du vil have vist oversigtsoplysninger om dine aktuelle licensplaner og de tilgængelige licenser for hver plan, skal du køre denne kommando:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Resultaterne indeholder:
  
- **SkuPartNumber:** Viser de tilgængelige licensplaner for din organisation. Er f.eks`ENTERPRISEPACK`. navnet på licensplanen for Office 365 Enterprise E3.
    
- **Aktiveret:** Antal licenser, du har købt til en bestemt licensplan.
    
- **Forbrugte enheder:** Antal licenser, du har tildelt til brugere fra en bestemt licensplan.
    
Hvis du vil have vist oplysninger om de Microsoft 365 tjenester, der er tilgængelige i alle dine licensplaner, skal du først få vist en liste over dine licensplaner.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Gem derefter oplysningerne om licensplanerne i en variabel.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Derefter skal du få vist tjenesterne i en bestemt licensplan.

```powershell
$licenses[<index>].ServicePlans
```

\<index> er et heltal, der angiver rækkenummeret for licensplanen fra visningen af `Get-AzureADSubscribedSku | Select SkuPartNumber` kommandoen minus 1.

Hvis visningen af `Get-AzureADSubscribedSku | Select SkuPartNumber` kommandoen f.eks. er følgende:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Kommandoen til visning af tjenesterne for ENTERPRISEPREMIUM-licensplanen er følgende:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM er den tredje række. Derfor er indeksværdien (3-1) eller 2.

Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Brug Microsoft Azure Active Directory modulet til Windows PowerShell

Først [skal du oprette forbindelse til din Microsoft 365 lejer](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Der findes et PowerShell-script, der automatiserer de procedurer, der er beskrevet i dette emne. Scriptet giver dig især mulighed for at få vist og deaktivere tjenester i din Microsoft 365 organisation, herunder Sway. Du kan få flere oplysninger under [Deaktiver adgang til Sway med PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Hvis du vil have vist oversigtsoplysninger om dine aktuelle licensplaner og de tilgængelige licenser for hver plan, skal du køre følgende kommando:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.
>

Resultaterne indeholder følgende oplysninger:
  
- **AccountSkuId:** Vis de tilgængelige licensplaner for din organisation ved hjælp af syntaksen `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ er den værdi, du angav, da du tilmeldte Microsoft 365, og som er entydig for din organisation. Værdien _\<LicensingPlan>_ er den samme for alle. I værdien `litwareinc:ENTERPRISEPACK`er `litwareinc`firmanavnet f.eks. , og navnet på `ENTERPRISEPACK`licensplanen , som er systemnavnet på Office 365 Enterprise E3.
    
- **Aktive enheder:** Antal licenser, du har købt til en bestemt licensplan.
    
- **Advarselsenheder:** Antallet af licenser i en licensplan, som du ikke har fornyet, og som udløber efter den 30-dages respitperiode.
    
- **Forbrugte enheder:** Antal licenser, du har tildelt til brugere fra en bestemt licensplan.
    
Hvis du vil have vist oplysninger om de Microsoft 365 tjenester, der er tilgængelige i alle dine licensplaner, skal du køre følgende kommando:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

I følgende tabel vises Microsoft 365-tjenesteplaner og deres brugervenlige navne for de mest almindelige tjenester. Listen over tjenesteplaner kan være anderledes. 
  
|**Serviceplan**|**Beskrivelse**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(tidligere kaldet Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Du kan se en komplet liste over licensplaner (også kaldet produktnavne), deres inkluderede tjenesteplaner og deres tilsvarende brugervenlige navne under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Hvis du vil have vist oplysninger om de Microsoft 365 tjenester, der er tilgængelige i en bestemt licensplan, skal du bruge følgende syntaks.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

I dette eksempel vises de tjenester, der er tilgængelige i litwareinc:ENTERPRISEPACK(Office 365 Enterprise E3)-licensplanen.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Se også

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)