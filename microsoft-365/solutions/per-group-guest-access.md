---
title: Forhindre gæster i at blive føjet til en bestemt gruppe
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
ms.openlocfilehash: 4b9ebc6366934db52c30d51091ac9991ff82d8c3
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570057"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Forhindre gæster i at blive føjet til en bestemt Microsoft 365 gruppe eller Microsoft Teams team

Hvis du vil tillade gæsteadgang til de fleste grupper og teams, men har nogle, hvor du gerne vil forhindre gæsteadgang, kan du blokere gæsteadgang for individuelle grupper og teams. Blokering af gæsteadgang til et team udføres ved at blokere gæsteadgang til den tilknyttede gruppe. Dette forhindrer, at nye gæster kan tilføjes, men fjerner ikke gæster, der allerede findes i gruppen eller teamet.

Hvis du bruger følsomhedsmærkater i din organisation, anbefaler vi, at du bruger dem til at kontrollere gæsteadgang pr. gruppe. Hvis du vil have mere at vide om, hvordan du gør dette, skal du bruge følsomhedsetiketter til at beskytte indhold [Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md). Dette er den anbefalede fremgangsmåde.

## <a name="change-group-settings-using-microsoft-powershell"></a>Skift gruppeindstillinger ved hjælp af Microsoft PowerShell

Du kan også forhindre, at der tilføjes nye gæster til individuelle grupper ved hjælp af PowerShell. Husk, at teamets tilknyttede websted SharePoint separate [kontrolelementer for gæstedeling](/sharepoint/change-external-sharing-site).

Du skal bruge prøveversionen af [Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2) (modulnavn **AzureADPreview**) for at ændre indstillingen for gæsteadgang på gruppeniveau:

- Hvis du ikke har installeret en version af Azure AD PowerShell-modulet før, skal du se Installation af [Azure AD-modulet](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) og følge vejledningen for at installere den offentlige prøveversion.

- Hvis du har 2.0-versionen af Azure AD PowerShell-modulet (AzureAD) installeret, `Uninstall-Module AzureAD` skal du fjerne den ved at køre i din PowerShell-session og derefter installere preview-versionen `Install-Module AzureADPreview`ved at køre .

- Hvis du allerede har installeret prøveversionen, skal du køre for `Install-Module AzureADPreview` at sikre, at det er den nyeste version af dette modul.

> [!NOTE]
> Du skal have globale administratorrettigheder for at køre disse kommandoer. 

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

Kør denne kommando for at bekræfte dine indstillinger:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Bekræftelsen ser sådan ud:
    
![Skærmbillede af PowerShell-vinduet, der viser, at gæstegruppeadgang er indstillet til falsk.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Hvis du vil slå indstillingen til igen for at tillade gæsteadgang til en bestemt gruppe, skal du køre følgende script og skifte til navnet på den gruppe, ```<GroupName>``` hvor du vil tillade gæsteadgang.

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

Få mere at vide under [Tillad eller bloker invitationer til B2B-brugere fra bestemte organisationer](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Føj gæster til den globale adresseliste

Gæster vises som standard ikke på den globale Exchange adresseliste. Brug nedenstående trin til at gøre en gæst synlig på den globale adresseliste.

Find gæstens objekt-id ved at køre:

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

Kør derefter følgende med de relevante værdier for ObjectID, GivenName, Efternavn, DisplayName og TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Administrer gruppemedlemskab i Microsoft 365 Administration](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[Azure Active Directory tilgå anmeldelser](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
