---
title: Administrer adgang til mailapps i Microsoft 365 Administration
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
description: Få mere at vide om, hvordan du vælger, hvilke mobilapps personer kan bruge til at få adgang til mail, kalender og kontakter.
ms.openlocfilehash: 5f5a96a0ac44757cfe168db87deb494019759c36
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780231"
---
# <a name="manage-email-app-access-in-the-microsoft-365-admin-center"></a>Administrer adgang til mailapp i Microsoft 365 Administration

Brug indstillingerne for adgang til mobilmail til at vælge, hvilke mobilapps personer i din organisation kan bruge til at få adgang til deres arbejds- eller skolekonto for at få adgang til mail, kalender og kontakter.
  
> [!IMPORTANT]
> Din organisation har adgang til denne indstilling, medmindre du bruger Microsoft Intune, eller du har konfigureret indstillinger for administration af mobilenheder i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.
  
## <a name="manage-email-app-options"></a>Administrer indstillinger for mailapp

> [!IMPORTANT]
> Hvis du ikke bruger denne funktion, sker der ingen ændringer af brugernes oplevelse. De kan bruge en hvilken som helst mobilmailapp til at få adgang til deres arbejds- eller skolekonto til mail, kalender og kontakter fra deres mobilenhed.

1. I Administration skal du gå til siden **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Services-tilføjelsesprogrammer&amp;</a>.

2. På siden **Med indstillinger for mailadgang til mobilenheder** skal du markere afkrydsningsfeltet og derefter vælge, hvordan brugerne i din organisation bruger mailapps på deres enheder:
  
Vælg indstillingen for at angive, hvordan brugerne i din organisation skal få adgang til deres arbejds- eller skolekonto fra deres mobilenheder
  
- **kun Outlook** – brugere i din organisation skal bruge Outlook til Android eller Outlook til iOS-appen på deres mobilenhed.

- **Alle mailapps** – alle brugere i din organisation bliver bedt om at bruge Outlook, men de kan vælge at bruge en hvilken som helst mailapp.

- **Alle mailapps** – nye brugere eller enheder i din organisation bliver bedt om at bruge Outlook, men de kan vælge at bruge en hvilken som helst mailapp.

Du kan finde flere oplysninger under [Indstillinger for adgang til mail fra din mobilenhed](access-email-from-a-mobile-device.md).
  
## <a name="new-user-or-device-is-activated-in-your-organization"></a>Ny bruger eller enhed er aktiveret i din organisation

Så snart en bruger i din organisation føjer sin arbejds- eller skolemail til en tredjepartsmailapp eller til en ny enhed, modtager vedkommende en mail fra **Microsoft på vegne af din organisation**. Mailen giver dem besked om fordelene ved at bruge Outlook mobilappen og giver dem et link til downloadplaceringen. Brugerne kan derefter vælge, om de vil fortsætte med at bruge tredjepartsappen eller vælge at bruge Outlook-mobilappen. I løbet af de 24 timer, efter at brugeren første gang modtager denne mail, vil brugerens enhed være i karantæne, og mail-, kalender- og kontaktdata opdateres ikke. Hvis de vælger at bruge Outlook-mobilappen, forbliver tredjepartsappen sat i karantæne, og dataene synkroniseres kun med Outlook mobilapp. Hvis de beslutter at fortsætte med at bruge tredjepartsappen, synkroniseres data med det samme. Hvis der ikke udføres nogen handling i løbet af de første 24 timer, fjernes mailen fra deres indbakke, og dataene synkroniseres automatisk fra serveren.
  
## <a name="previously-configured-users-in-your-organization"></a>Tidligere konfigurerede brugere i din organisation

Hvis du beslutter dig for at anbefale Outlook til alle i din organisation, modtager brugere, der tidligere har oprettet forbindelse til deres arbejds- eller skolemailkonto til en tredjepartsapp, ud over den oplevelse, der er beskrevet ovenfor for nye brugere, en mail fra **Microsoft på vegne af din organisation** inden for 48 timer, efter at denne indstilling er aktiveret. Mailen giver dem besked om fordelene ved at bruge Outlook mobilappen og giver dem et link til downloadplaceringen. Brugerne kan derefter vælge, om de vil fortsætte med at bruge tredjepartsappen eller vælge at bruge Outlook-mobilappen. I løbet af de 24 timer, efter at brugeren første gang modtager denne mail, vil brugerens enhed være i karantæne, og mail-, kalender- og kontaktdata opdateres ikke. Hvis de vælger at bruge Outlook-mobilappen, forbliver tredjepartsappen sat i karantæne, og dataene synkroniseres kun med Outlook mobilapp. Hvis de beslutter at fortsætte med at bruge tredjepartsappen, synkroniseres data med det samme. Hvis der ikke udføres nogen handling i løbet af de første 24 timer, fjernes mailen fra deres indbakke, og dataene synkroniseres automatisk fra serveren.
