---
title: Tilføj eller fjern medlemmer fra Microsoft 365 grupper
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
search.appverid:
- MET150
ms.assetid: e186d224-a324-4afa-8300-0e4fc0c3000a
description: Få mere at vide om, hvordan du føjer et medlem til en gruppe, fjerner medlemmer fra gruppen og administrerer status for gruppeejer Microsoft 365 Administration.
ms.openlocfilehash: 610da28d6282cb45cb43e086fb3f80acaf18bb05
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587651"
---
# <a name="add-or-remove-members-from-microsoft-365-groups-using-the-admin-center"></a>Tilføj eller fjern medlemmer fra Microsoft 365 grupper ved hjælp af Administration

I Microsoft 365 opretter gruppemedlemmer typisk deres egne grupper, føjer sig selv til grupper, de vil deltage i, eller de inviteres af gruppeejere. Hvis gruppeejerskabet ændres, eller hvis du finder ud af, at et medlem skal tilføjes eller fjernes, kan du som administrator også foretage denne ændring. Kun en global administrator, Exchange, gruppeadministrator eller brugeradministrator kan foretage disse ændringer. [Hvad er en Microsoft 365 gruppe?](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

> [!TIP]
> Hvis du ikke er administrator, kan du tilføje eller [fjerne medlemmer ved hjælp af Outlook](https://support.microsoft.com/office/3b650f4a-5c9b-4f94-a1bb-0cca4b1091de).
  
## <a name="add-a-member-to-a-group-in-the-admin-center"></a>Føj et medlem til en gruppe i Administration

1. I Administration skal du gå til [**siden Aktive**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupper.  

2. Klik på et gruppenavn.

3. Vælg Vis alle og administrer medlemmer **under** **fanen Medlemmer i** detaljeruden, og vælg derefter **Tilføj medlemmer**.

4. Søg efter eller vælg navnet på det medlem, du vil tilføje.

5. Vælg **Gem**.

## <a name="add-a-group-to-a-member-in-the-admin-center"></a>Føj en gruppe til et medlem i Administration

1. I Administration skal du gå til [**siden Aktive**](https://admin.microsoft.com/Adminportal/Home?#/users) brugere.  

2. Klik på en bruger.

3. Vælg Administrer grupper på fanen **Konto** i **detaljeruden**.

4. Søg efter eller vælg navnet på den gruppe, du vil tilføje.

5. Vælg **Gem**.

## <a name="remove-a-member-from-a-group-in-the-admin-center"></a>Fjern et medlem fra en gruppe i Administration

> [!NOTE]
> Når du fjerner et medlem fra en privat gruppe, tager det fem minutter, før personen er blokeret fra gruppen.

1. I Administration skal du gå til [**siden Aktive**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupper.  

2. Klik på et gruppenavn.

3. I detaljeruden under fanen Medlemmer **skal du** vælge **Vis alle og administrer medlemmer**.

4. Vælg X ud for det medlem, du vil fjerne.

5. Vælg **Gem** for at fjerne medlemmet.

## <a name="manage-group-owner-status"></a>Administrer status for gruppeejer

Som standard er den person, der oprettede gruppen, gruppeejeren. En gruppe har ofte flere ejere for at understøtte sikkerhedskopiering eller af andre årsager. Medlemmer kan promoveres til ejerstatus, og ejere kan gøres til medlemsstatus.
  
### <a name="promote-a-member-to-owner-status-in-the-admin-center"></a>Gøre et medlem til ejerstatus i Administration

1. I Administration skal du gå til [**siden Aktive**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupper.  

2. Klik på et gruppenavn.

3. I detaljeruden under fanen Medlemmer **skal du** vælge **Vis alle og administrer ejere**.

4. Vælg **Tilføj ejere**.

5. Markér afkrydsningsfeltet ud for navnet på det medlem, du vil tilføje.

6. Vælg **Gem**, og derefter **Luk**.

### <a name="remove-owner-status-in-the-admin-center"></a>Fjern ejerstatus i Administration

1. I Administration skal du gå til [**siden Aktive**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupper.  

2. Klik på et gruppenavn.

3. I detaljeruden under fanen Medlemmer **skal du** vælge **Vis alle og administrer ejere**.

4. Vælg X ud for ejerens navn.

5. Vælg **Gem**.

## <a name="next-steps"></a>Næste trin

- [Administrer grupper dynamisk Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) Gruppen: Se afsnittet "Hvordan kan jeg administrere medlemskabet af en gruppe dynamisk?"

- Hvis du vil føje hundred- eller tusindvis af brugere til grupper, skal [du bruge Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks).

- [Tildel en ny ejer til en uafhængig gruppe](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732)

## <a name="related-content"></a>Relateret indhold

[Opgrader distributionslister Microsoft 365 grupper i Outlook](../manage/upgrade-distribution-lists.md) (artikel)\
[Derfor skal du opgradere dine distributionslister til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188) (artikel)\
[Administrer gæsteadgang i Microsoft 365 (](manage-guest-access-in-groups.md)artikel)\
[Administrer Microsoft 365 grupper med PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md): Denne artikel introducerer dig til vigtige cmdlet'er og giver eksempler (artikel)\
[Microsoft 365 gruppenavngivningspolitik](../../solutions/groups-naming-policy.md) (artikel)