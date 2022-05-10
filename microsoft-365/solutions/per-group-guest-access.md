---
title: Undgå, at gæster føjes til en bestemt gruppe
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du forhindrer gæster i at blive føjet til en bestemt gruppe
ms.openlocfilehash: f050011427ceeeff8347c2acd5b6d3fbbcf11bec
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285308"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Undgå, at gæster føjes til en bestemt Microsoft 365 gruppe eller Microsoft Teams team

Hvis du vil tillade gæsteadgang til de fleste grupper og teams, men har et sted, hvor du vil forhindre gæsteadgang, kan du blokere gæsteadgang for individuelle grupper og teams. (Blokering af gæsteadgang til et team gøres ved at blokere gæsteadgang til den tilknyttede gruppe). Dette forhindrer nye gæster i at blive tilføjet, men fjerner ikke gæster, der allerede er i gruppen eller teamet.

Hvis du bruger følsomhedsmærkater i din organisation, anbefaler vi, at du bruger dem til at styre gæsteadgangen pr. gruppe. Du kan finde oplysninger om, hvordan du gør dette, [ved at bruge følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md). Dette er den anbefalede fremgangsmåde.

## <a name="change-group-settings-using-microsoft-powershell"></a>Skift gruppeindstillinger ved hjælp af Microsoft PowerShell

Du kan også forhindre, at nye gæster føjes til individuelle grupper ved hjælp af PowerShell. Husk, at teamets tilknyttede SharePoint websted har [separate gæstedelingskontrolelementer](/sharepoint/change-external-sharing-site).

Du skal bruge prøveversionen af [Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2) (modulnavn **AzureADPreview**) for at ændre indstillingen for gæsteadgang på gruppeniveau:

- Hvis du ikke har installeret nogen version af Azure AD PowerShell-modulet før, skal du se [Installér Azure AD-modulet](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) og følge vejledningen for at installere den offentlige prøveversion.

- Hvis du har version 2.0 til generel tilgængelighed af Azure AD PowerShell-modulet (AzureAD), skal du fjerne den ved at køre `Uninstall-Module AzureAD` i din PowerShell-session og derefter installere prøveversionen ved at køre `Install-Module AzureADPreview`.

- Hvis du allerede har installeret prøveversionen, skal du køre `Install-Module AzureADPreview` for at sikre, at det er den nyeste version af dette modul.

> [!NOTE]
> Du skal have globale administratorrettigheder for at kunne køre disse kommandoer. 

Kør følgende script, og skift *\<GroupName\>* til navnet på den gruppe, hvor du vil blokere gæsteadgang.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Kør denne kommando for at bekræfte indstillingerne:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Bekræftelsen ser sådan ud:
    
![Skærmbillede af PowerShell-vinduet, der viser, at adgang til gæstegrupper er angivet til falsk.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Hvis du vil slå indstillingen tilbage for at tillade gæsteadgang til en bestemt gruppe, skal du køre følgende script og skifte ```<GroupName>``` til navnet på den gruppe, hvor du vil tillade gæsteadgang.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$True
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
$id = (get-AzureADObjectSetting -TargetType groups -TargetObjectId $groupID).id
Set-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy -id $id
```

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Tillad eller bloker gæsteadgang baseret på deres domæne

Du kan tillade eller blokere gæster, der bruger et bestemt domæne. Hvis din virksomhed (Contoso) f.eks. har et partnerskab med en anden virksomhed (Fabrikam), kan du føje Fabrikam til din tilladelsesliste, så brugerne kan føje disse gæster til deres grupper.

Du kan få flere oplysninger under [Tillad eller bloker invitationer til B2B-brugere fra bestemte organisationer](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Føj gæster til den globale adresseliste

Gæster er som standard ikke synlige på Exchange globale adresseliste. Brug nedenstående trin til at gøre en gæst synlig på den globale adresseliste.

Find gæstens ObjectID ved at køre:

```PowerShell
get-AzureADUser -all $true | ?{$_.CreationType -eq "Invitation"}
```

Kør derefter følgende ved hjælp af de relevante værdier for ObjectID, GivenName, Surname, DisplayName og TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Administrer gruppemedlemskab i Microsoft 365 Administration](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[Azure Active Directory adgang til korrekturer](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
