---
title: Vis fejl i katalogsynkronisering i Microsoft 365
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
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Få mere at vide om, hvordan du får vist fejl i katalogsynkronisering og mulige løsninger Microsoft 365 Administration.
ms.openlocfilehash: 2b832cff65aad0ae7327f440a565e12c7cba66f4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590990"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Vis fejl i katalogsynkronisering i Microsoft 365

Du kan få vist fejl i katalogsynkronisering <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>. Kun fejl i objektet Bruger vises. Hvis du vil have vist fejl med PowerShell, [skal du se Identificere objekter med DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Vis fejl i katalogsynkronisering i Microsoft 365 Administration

Sådan får du vist eventuelle fejl i Microsoft 365 Administration:
  
1. Log [på Microsoft 365 Administration en](https://admin.microsoft.com) global administratorkonto. 
    
2. På **startsiden** får du vist kortet **Brugeradministration** . 
    
    ![Kortet Brugeradministration i Microsoft 365 Administration.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. På kortet skal du vælge **Synkroniseringsfejl** under **Azure AD Forbind** for at få vist fejlene på **siden Katalogsynkroniseringsfejl**.   
    
    ![Et eksempel på siden Katalogsynkroniseringsfejl.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Vælg en af fejlene for at få vist detaljeruden med oplysninger om fejlen og tip til at løse den.

   ![Eksempel på detaljer om en fejl i katalogsynkronisering.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Efter visningen kan du se[, hvordan du løser problemer med katalogsynkronisering Microsoft 365](fix-problems-with-directory-synchronization.md) at rette eventuelle identificerede problemer.