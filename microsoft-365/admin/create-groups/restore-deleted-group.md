---
title: Gendan en slettet Microsoft 365 gruppe
ms.reviewer: arvaradh
f1.keywords: CSH
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
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: En slettet gruppe bevares i 30 dage, og du kan stadig gendanne gruppen. Efter 30 dage slettes gruppen og dens indhold permanent.
ms.openlocfilehash: 926cfa18972a7ca72009258b02b565bd28a183be
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589921"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Gendan en slettet Microsoft 365 gruppe

Hvis du har slettet en gruppe, bevares den som standard i 30 dage. Denne periode på 30 dage betragtes som en "blød sletning", fordi du stadig kan gendanne gruppen. Efter 30 dage slettes gruppen og dens tilknyttede indhold permanent og kan ikke gendannes.

Når en gruppe gendannes, gendannes følgende indhold:
  
- Azure Active Directory (AD) Microsoft 365 gruppeobjekt, -egenskaber og -medlemmer.
    
- Gruppens mailadresser.
    
- Exchange Online delt indbakke og kalender.
    
- SharePoint Online-teamwebsted og -filer.
    
- OneNote notesbog
    
- Planner
    
- Teams

- Yammer gruppe- og gruppeindhold (hvis Microsoft 365 oprettet ud fra Yammer)

- Power BI [klassisk arbejdsområde](/power-bi/collaborate-share/service-create-workspaces)

> [!NOTE]
> I denne artikel beskrives det, at gendannelse kun Microsoft 365 grupper. Alle andre grupper kan ikke gendannes, når de er slettet.

## <a name="restore-a-group"></a>Gendan en gruppe

# <a name="outlook"></a>[Outlook](#tab/outlook)

Hvis du er ejer af en Microsoft 365 gruppe, kan du gendanne gruppen selv i Outlook på internettet ved at følge disse trin:

1. På siden [slettede grupper](https://outlook.office.com/people/group/deleted) skal du vælge **indstillingen Administrer** grupper **under noden** Grupper og derefter **vælge Slettet**.

2. Klik på fanen **Gendan** ud for den gruppe, du vil gendanne.

Hvis den slettede gruppe ikke vises her, skal du kontakte en administrator.

# <a name="admin-center"></a>[Administration](#tab/admin-center)

Hvis du er global administrator eller gruppeadministrator, kan du gendanne en slettet gruppe i Microsoft 365 Administration:

1. Gå til [Administration](https://admin.microsoft.com).
2. **Udvid Grupper**, og klik derefter **på Slettede grupper**.
3. Vælg den gruppe, du vil gendanne, og klik derefter på **Gendan gruppe**.

> [!NOTE]
> I nogle tilfælde kan det tage helt op til 24 timer, før gruppen og alle dens data er gendannet. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Har du spørgsmål Microsoft 365 grupper?

Besøg [Microsoft Tech Community for](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) at stille spørgsmål og deltage i samtaler om Microsoft 365 grupper. 
  
## <a name="related-content"></a>Relateret indhold

[Administrer Microsoft 365 grupper med PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (artikel)\
[Slet grupper ved Remove-UnifiedGroup en cmdlet](/powershell/module/exchange/remove-unifiedgroup) (artikel)\
[Administrer indstillingerne for teamwebsteder med forbindelse til grupper](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (artikel)\
[Slet en gruppe i Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (artikel)
