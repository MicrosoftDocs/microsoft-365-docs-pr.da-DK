---
title: Administrer gæsteadgang i Microsoft 365 grupper
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
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
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Få mere at vide om, hvordan du føjer gæster Microsoft 365 gruppe, får vist gæster og bruger PowerShell til at kontrollere gæsteadgang.
ms.openlocfilehash: ea5986c4b9e0c5124abc581f9ed35391e0885633
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637934"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Administrer gæsteadgang i Microsoft 365 grupper

Som standard er gæsteadgang til Microsoft 365 grupper aktiveret for din organisation. Administratorer kan styre, om de vil give gæsteadgang til grupper i hele organisationen eller til individuelle grupper.

Når den er slået til, kan gruppemedlemmer invitere gæster til en Microsoft 365 via Outlook på internettet. Invitationer sendes til gruppeejeren til godkendelse.

Når gæsten er godkendt, føjes den til mappen og gruppen.

> [!Note]
> Yammer Enterprise netværk, der er i indbygget tilstand, eller [EU Geo](/yammer/manage-security-and-compliance/manage-data-compliance) understøtter ikke gæster på netværket.
> Microsoft 365 forbundne Yammer-grupper understøtter i øjeblikket ikke gæsteadgang, men du kan oprette eksterne grupper, der ikke er tilsluttede, Yammer dit netværk. Se [Opret og administrer eksterne grupper i Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) for vejledning.

Gæsteadgang i grupper bruges ofte som en del af et bredere scenarie, der SharePoint eller Teams. Disse tjenester har deres egne indstillinger for gæstedeling. Du kan finde en komplet vejledning til konfiguration af gæstedeling på tværs af grupper, SharePoint og Teams i:

- [Samarbejd med gæster på et websted](../../solutions/collaborate-in-site.md)
- [Samarbejd med gæster i et team](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Administrer gæsteadgang til grupper

Hvis du vil aktivere eller deaktivere gæsteadgang i grupper, kan du gøre det i <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupperne**</a>.

1. I Administration skal du gå til **Vis alle Indstillinger** \>  \> **Org-indstillingerne**, og på <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**fanen Tjenester** skal</a> du **vælge Microsoft 365-grupper**.
  
2. På siden **Microsoft 365-grupper du** vælge, om du vil give personer uden for organisationen adgang til grupperessourcer eller lade gruppeejere føje personer uden for organisationen til grupper.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Føj gæster til Microsoft 365 gruppe fra Administration

Hvis gæsten allerede findes i biblioteket, kan du føje vedkommende til dine grupper <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">fra Microsoft 365 Administration</a>. (Grupper med dynamisk medlemskab skal [administreres i Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. I Administration skal du gå til **GrupperGrupper** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Klik på den gruppe, du vil føje gæsten til, og vælg **Se alle og administrer** medlemmer på **fanen** Medlemmer. 
  
4. Vælg **Tilføj medlemmer**, og vælg navnet på den gæst, du vil tilføje.
    
5. Vælg **Gem**.

Hvis du vil føje en gæst til kataloget direkte, kan du tilføje Azure Active Directory [B2B-samarbejdsbrugere i Azure Portal](/azure/active-directory/b2b/add-users-administrator).

Hvis du vil redigere en gæsts oplysninger, kan du Tilføje eller opdatere en brugers profiloplysninger ved [hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>Relateret indhold

[Bloker gæster fra en bestemt gruppe](../../solutions/per-group-guest-access.md) (artikel)\
[Administrer gruppemedlemskab i Microsoft 365 Administration](add-or-remove-members-from-groups.md) (artikel)\
[Azure Active Directory access-anmeldelser](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (artikel)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (artikel)
