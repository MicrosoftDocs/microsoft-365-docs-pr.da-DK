---
title: Administrer adgang til mailapp i Microsoft 365 Administration
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
ms.assetid: d00b6b83-1f14-4e9c-a2c5-dbd9a92816f4
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om, hvordan du vælger, hvilke mobilapps folk kan bruge til at få adgang til mail, kalender og kontakter.
ms.openlocfilehash: e3a7999900e85bde1bee7bf220b46a74a1151f57
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63590161"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Administrer adgang til mailapp i Microsoft 365 Administration

Brug indstillingerne for mobilmailadgang til at vælge, hvilke mobilapps personer i organisationen kan bruge til at få adgang til deres arbejds- eller skolekonto for at få adgang til mail, kalender og kontakter.
  
> [!IMPORTANT]
> Din organisation har adgang til denne indstilling, medmindre du bruger Microsoft Intune eller du har konfigureret indstillingerne for administration af mobilenheder <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. 
  
## <a name="manage-email-app-options"></a>Administrere indstillinger for mailapp

> [!IMPORTANT]
>  Hvis du ikke bruger denne funktion, vil der ikke være nogen ændringer i dine brugeres oplevelse. De vil kunne bruge en hvilken som helst mobilmailapp til at få adgang til deres arbejds- eller skolekonto til mail, kalender og kontakter fra deres mobilenhed. 
    
1. I Administration skal du gå til **siden Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services-tilføjelsesprogrammet&amp;</a>. 

2. På siden **Indstillinger for mobilmailadgang** skal du markere afkrydsningsfeltet og derefter vælge, hvordan brugerne i organisationen skal bruge mailapps på deres enheder:
  
Vælg indstillingen for at angive, hvordan brugerne i organisationen får adgang til deres arbejds- eller skolekonto fra deres mobilenheder
  
- **Outlook –** brugere i organisationen skal bruge appen Outlook til Android eller Outlook til iOS på deres mobilenhed. 
    
- **Enhver mailapp** – alle brugere i organisationen vil blive bedt om at bruge en Outlook, men de kan vælge at bruge en hvilken som helst mailapp. 
    
- **En mailapp** – nye brugere eller enheder i organisationen vil én gang blive bedt om at bruge Outlook, men de kan vælge at bruge en hvilken som helst mailapp. 
    
Du kan få mere at vide [under Indstillinger for adgang til mail fra din mobilenhed](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Ny bruger eller enhed er aktiveret i din organisation

Så snart en bruger i organisationen tilføjer sin arbejds- eller skolemail til en tredjepartsmailapp eller til en ny enhed, modtager brugeren en mail fra Microsoft på vegne af **din organisation**. Mailen giver dem besked om fordelene ved at bruge Outlook-mobilappen og indeholder et link til downloadplaceringen. Brugerne kan derefter vælge, om de vil fortsætte med at bruge tredjepartsappen, eller vælge at bruge Outlook-mobilappen. I løbet af de 24 timer, der går, efter brugeren først modtager denne mail, vil brugerens enhed være i karantæne, og mail-, kalender- og kontaktdata opdateres ikke. Hvis de vælger at bruge Outlook mobilappen, forbliver tredjepartsappen i karantæne, og data synkroniseres kun med Outlook mobilappen. Hvis de beslutter sig for at fortsætte med at bruge tredjepartsappen, begynder dataene at synkronisere med det samme. Hvis der ikke sker noget i løbet af de første 24 timer, fjernes mailen fra deres indbakke, og data begynder automatisk at blive synkroniseret fra serveren.
  
## <a name="previously-configured-users-in-your-organization"></a>Tidligere konfigurerede brugere i organisationen

Hvis du beslutter dig for at anbefale Outlook til alle i organisationen, vil brugere, ud over den oplevelse, der er beskrevet ovenfor for nye brugere, som tidligere har tilknyttet deres arbejds- eller skolemailkonto til en tredjepartsapp, modtage en mail fra **Microsoft** på vegne af din organisation inden for 48 timer efter, at denne indstilling er blevet aktiveret. Mailen giver dem besked om fordelene ved at bruge Outlook-mobilappen og indeholder et link til downloadplaceringen. Brugerne kan derefter vælge, om de vil fortsætte med at bruge tredjepartsappen, eller vælge at bruge Outlook-mobilappen. I løbet af de 24 timer, der går, efter brugeren først modtager denne mail, vil brugerens enhed være i karantæne, og mail-, kalender- og kontaktdata opdateres ikke. Hvis de vælger at bruge Outlook mobilappen, forbliver tredjepartsappen i karantæne, og data synkroniseres kun med Outlook mobilappen. Hvis de beslutter sig for at fortsætte med at bruge tredjepartsappen, begynder dataene at synkronisere med det samme. Hvis der ikke sker noget i løbet af de første 24 timer, fjernes mailen fra deres indbakke, og data begynder automatisk at blive synkroniseret fra serveren. 
  

