---
title: Løsning af problemer med katalogsynkronisering for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Beskriver almindelige årsager til problemer med katalogsynkronisering i Office 365 og indeholder nogle metoder, der kan hjælpe med fejlfinding og løsning af dem.
ms.openlocfilehash: 248ccc888f047a57f474dfc55b501f4450cb116e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101001"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Løsning af problemer med katalogsynkronisering for Microsoft 365

Med katalogsynkronisering kan du fortsætte med at administrere brugere og grupper i det lokale miljø og synkronisere tilføjelser, sletninger og ændringer i cloudmiljøet. Men opsætningen er lidt kompliceret, og det kan nogle gange være svært at identificere kilden til problemer. Vi har ressourcer, der kan hjælpe dig med at identificere potentielle problemer og løse dem.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Hvordan gør jeg vide, om der er noget galt?

Den første indikation på, at der er noget galt, er, når feltet DirSync Status i Microsoft 365 Administration angiver, at der er et problem.
  
Du modtager også en mail (til den alternative mail og til din administratormail) fra Microsoft 365, der angiver, at din lejer har oplevet fejl under katalogsynkronisering. Du kan finde flere oplysninger [under Identificer fejl ved katalogsynkronisering i Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Hvordan gør jeg du Azure Active Directory Forbind værktøj?

I [Microsoft 365 Administration skal du](https://admin.microsoft.com) navigere til **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a>. Klik på menuen **Flere** (tre prikker), og vælg **Katalogsynkronisering**. 
  
Følg [vejledningen i guiden](set-up-directory-synchronization.md) for at downloade Azure AD-Forbind. 
  
Hvis du stadig bruger Azure Active Directory (Azure AD)-synkronisering (DirSync), kan du se, [hvordan du foretager fejlfinding af fejlmeddelelser i Azure Active Directory installation og konfiguration af guiden Synkroniseringsværktøj i Microsoft 365](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors)  for at få oplysninger om systemkravene til installation af dirsync, de tilladelser, du har brug for, og hvordan du foretager fejlfinding af almindelige fejl. 
  
Hvis du vil opdatere fra Azure AD Sync til Azure AD Forbind, skal du se [opgraderingsinstruktionerne](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Løsning af almindelige årsager til problemer med katalogsynkronisering i Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Synkroniserede objekter vises eller opdateres ikke online, eller jeg får synkroniseringsfejlrapporter fra tjenesten.

- [Tolerance for identitetssynkronisering og duplikerede attributter](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Jeg har en besked i Administration, eller jeg modtager automatiserede mails om, at der ikke har været en nylig synkroniseringshændelse
- [Fejlfinding af forbindelsesproblemer med Azure AD-forbindelse](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect-konti og -tilladelser](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Azure AD Connect-synkronisering: Sådan administreres Azure AD-tjenestekontoen](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Katalogsynkronisering med Azure Active Directory stopper, eller du bliver advaret om, at synkronisering ikke er registreret i mere end én dag](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Adgangskodehashs synkroniseres ikke, eller jeg får vist en besked i Administration om, at der ikke har været en nylig synkronisering af adgangskodehash
- [Implementering af synkronisering af adgangskodehash med Azure AD Connect-synkronisering](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Jeg får vist en besked om, at objektkvoten er overskredet
- Vi har en indbygget objektkvote, der hjælper med at beskytte tjenesten. Hvis du har for mange objekter i mappen, der skal synkroniseres til Microsoft 365, skal du [kontakte support til forretningsprodukter for](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) at øge din kvote.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Jeg har brug for at vide, hvilke attributter der er synkroniseret
- Du kan finde en liste over alle de attributter, der er synkroniseret mellem det lokale miljø og cloudmiljøet [lige her](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Jeg kan ikke administrere eller fjerne objekter, der er synkroniseret til skyen
- Er du klar til kun at administrere objekter i skyen? Eller er der et objekt, der er slettet i det lokale miljø, men som sidder fast i skyen? Se denne artikel [om fejlfinding af fejl under synkronisering](/azure/active-directory/hybrid/tshoot-connect-sync-errors) og [support](/troubleshoot/azure/active-directory/cannot-manage-objects) for at få hjælp til, hvordan du løser disse problemer.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Jeg fik en fejlmeddelelse om, at mit firma har overskredet antallet af objekter, der kan synkroniseres
- Du kan læse mere om dette problem [her](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>Andre ressourcer

- [Script til rettelse af dublerede hovednavne for brugeren](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Sådan forbereder du et domæne, der ikke kan sendes, f.eks. et .lokalt domæne, til katalogsynkronisering](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script til at tælle det samlede antal synkroniserede objekter](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Foretag fejlfinding af AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Brug PowerShell til at rette tomme DisplayName-attributter for mailaktiverede grupper](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Brug PowerShell til at løse dubletter af UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Brug PowerShell til at rette duplikerede mailadresser](https://go.microsoft.com/fwlink/p/?LinkId=396731)
