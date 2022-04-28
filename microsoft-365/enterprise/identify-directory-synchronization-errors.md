---
title: Vis fejl under synkronisering af mapper i Microsoft 365
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
description: Få mere at vide om, hvordan du får vist fejl i katalogsynkronisering og mulige rettelser i Microsoft 365 Administration.
ms.openlocfilehash: 1aa6a9208c9ae3091c2490a003eaabb841b78dc5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096496"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Vis fejl under synkronisering af mapper i Microsoft 365

Du kan få vist fejl under katalogsynkronisering i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Det er kun brugerobjektfejlene, der vises. Hvis du vil se fejl med PowerShell, skal du se [Identificer objekter med DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Vis fejl ved katalogsynkronisering i Microsoft 365 Administration

Sådan får du vist eventuelle fejl i Microsoft 365 Administration:
  
1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med en global administratorkonto. 
    
2. På siden **Startside** kan du se kortet **Brugeradministration** . 
    
    ![Kortet Brugeradministration i Microsoft 365 Administration.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. På kortet skal du vælge **Synkroniser fejl** under **Azure AD Forbind** for at se fejlene på siden **Synkroniseringsfejl i Mappe**.   
    
    ![Et eksempel på siden med synkroniseringsfejl i Mappe.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Vælg en af fejlene for at få vist detaljeruden med oplysninger om fejlen og tip til, hvordan du løser fejlen.

   ![Eksempel på detaljer om synkroniseringsfejl i en mappe.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Når du har fået vist, kan du se[, hvordan du løser problemer med katalogsynkronisering for at få Microsoft 365](fix-problems-with-directory-synchronization.md) til at løse eventuelle identificerede problemer.