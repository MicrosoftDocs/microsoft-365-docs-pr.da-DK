---
title: Slå katalogsynkronisering for Microsoft 365 fra
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 5082f89032c17e549f11f8397126f6d059937c48
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077341"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Slå katalogsynkronisering for Microsoft 365 fra
Du kan bruge PowerShell til at slå katalogsynkronisering fra og konvertere dine synkroniserede brugere til kun skyen. Det anbefales dog ikke, at du slår katalogsynkronisering fra som et fejlfindingstrin. Hvis du har brug for hjælp til fejlfinding af katalogsynkronisering, kan du se artiklen [Løs problemer med katalogsynkronisering for Microsoft 365](fix-problems-with-directory-synchronization.md). 
  
[Kontakt support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) til forretningsprodukter, hvis det er nødvendigt.
  
## <a name="turn-off-directory-synchronization"></a>Slå katalogsynkronisering fra  
Sådan slår du katalogsynkronisering fra:
  
1. Først skal du installere den nødvendige software og oprette forbindelse til dit Microsoft 365-abonnement. Du kan finde en vejledning [i Forbind med Microsoft Azure Active Directory modulet for Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Brug [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) til at deaktivere katalogsynkronisering: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Hvis du bruger denne kommando, skal du vente 72 timer, før du kan slå katalogsynkronisering til igen.
>
