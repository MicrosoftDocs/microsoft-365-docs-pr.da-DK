---
title: Slå katalogsynkronisering fra for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: I denne artikel kan du finde oplysninger om, hvordan du bruger PowerShell til at deaktivere katalogsynkronisering for Microsoft 365.
ms.openlocfilehash: 83a3d66493994800a71a1910332a5eb2cdb003cd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594207"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Slå katalogsynkronisering fra for Microsoft 365
Du kan bruge PowerShell til at deaktivere katalogsynkronisering og konvertere dine synkroniserede brugere til kun at bruge skyen. Det anbefales dog ikke, at du deaktiverer katalogsynkronisering som et fejlfindingstrin. Hvis du har brug for hjælp til fejlfinding i forbindelse med katalogsynkronisering, kan du [se artiklen Løse problemer med katalogsynkronisering Microsoft 365](fix-problems-with-directory-synchronization.md) artikel. 
  
[Kontakt support til](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) forretningsprodukter, hvis det er nødvendigt.
  
## <a name="turn-off-directory-synchronization"></a>Slå katalogsynkronisering fra  
Sådan deaktiverer du katalogsynkronisering:
  
1. Du skal først installere den nødvendige software og oprette forbindelse til Microsoft 365 abonnement. Du kan finde en [vejledning Forbind vejledning Microsoft Azure Active Directory modulet til Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Brug [Set-MsolDirSyncEnabled til at](/previous-versions/azure/dn194097(v=azure.100)) deaktivere katalogsynkronisering: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Hvis du bruger denne kommando, skal du vente 72 timer, før du kan slå katalogsynkronisering til igen.
>
