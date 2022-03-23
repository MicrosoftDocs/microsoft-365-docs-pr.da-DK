---
title: Løse problemer med katalogsynkronisering til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Beskriver de almindelige årsager til problemer med katalogsynkronisering i Office 365 og indeholder et par metoder til at foretage fejlfinding af og løse dem.
ms.openlocfilehash: dba6626ead648928186f8fbeac646a2b52206bc0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589760"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Løse problemer med katalogsynkronisering til Microsoft 365

Med katalogsynkronisering kan du fortsætte med at administrere brugere og grupper lokalt og synkronisere tilføjelser, sletninger og ændringer i skyen. Men installationen er lidt kompliceret, og det kan sommetider være svært at identificere kilden til problemerne. Vi har ressourcer, der kan hjælpe dig med at identificere potentielle problemer og løse dem.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Hvordan ved jeg, om der er noget galt?

Det første tegn på, at noget er galt, er, når flisen Status for DirSync i feltet Microsoft 365 Administration angiver, at der er et problem.
  
Du vil også modtage en mail (til den alternative mail og din administratormail) fra Microsoft 365, der angiver, at din lejer har fundet fejl i katalogsynkronisering. Du kan finde flere [oplysninger i Identificer katalogsynkroniseringsfejl Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Hvordan får jeg Azure Active Directory Forbind værktøjet?

I [Microsoft 365 Administration skal](https://admin.microsoft.com) du gå til **Aktive** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**brugere for brugere**</a>. Klik på **menuen Flere** (tre prik), og vælg **Katalogsynkronisering**. 
  
Følg vejledningen [i guiden for at](set-up-directory-synchronization.md) downloade Azure AD-Forbind. 
  
Hvis du stadig bruger Azure Active Directory-synkronisering (Azure AD) (DirSync), skal du se Sådan foretager du fejlfinding [af Azure Active Directory](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors) installation af synkroniseringsværktøjet og fejlmeddelelser i guiden Konfiguration Microsoft 365  for at få oplysninger om systemkravene til installation af dirsync, de tilladelser, du skal bruge, og hvordan du foretager fejlfinding af almindelige fejl. 
  
Hvis du vil opdatere fra Azure AD-synkronisering til Azure AD Forbind, skal du [se opgraderingsvejledningen](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Løsning af almindelige årsager til problemer med katalogsynkronisering i Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Synkroniserede objekter vises ikke eller opdateres ikke online, eller jeg får synkroniseringsfejlrapporter fra tjenesten.

- [Tolerance for identitetssynkronisering og duplikerede attributter](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Jeg har en besked i Administration, eller jeg modtager automatiserede mails om, at der ikke har været en synkroniseringshændelse for nylig
- [Fejlfinding af forbindelsesproblemer med Azure AD-forbindelse](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect-konti og -tilladelser](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Azure AD Connect-synkronisering: Sådan administreres Azure AD-tjenestekontoen](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Katalogsynkronisering med Azure Active Directory stopper, eller du bliver advaret om, at synkronisering ikke er registreret i mere end én dag](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Adgangskodehashes synkroniseres ikke, eller jeg får vist en besked i Administration om, at der ikke har været en nylig synkronisering af adgangskodehash
- [Implementering af synkronisering af adgangskodehash med Azure AD Connect-synkronisering](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Jeg får vist en besked om, at objektkvoten er overskredet
- Vi har en indbygget objektkvote for at beskytte tjenesten. Hvis du har for mange objekter i biblioteket, der skal synkroniseres med Microsoft 365, skal du kontakte [support til](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) virksomhedsprodukter for at øge din kvote.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Jeg har brug for at vide, hvilke attributter der synkroniseres
- Du kan finde en liste over alle de attributter, der synkroniseres mellem det lokale miljø og skyen [, lige her](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Jeg kan ikke administrere eller fjerne objekter, der er synkroniseret til skyen
- Er du klar til kun at administrere objekter i skyen? Eller er der et objekt, der er blevet slettet lokalt, men er fastlåst i skyen? Se nærmere på denne Fejlfinding [under synkronisering og supportartikel](/azure/active-directory/hybrid/tshoot-connect-sync-errors) for at få [vejledning](/troubleshoot/azure/active-directory/cannot-manage-objects) til at løse disse problemer.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Jeg fik en fejlmeddelelse om, at mit firma har overskredet antallet af objekter, der kan synkroniseres
- Du kan læse mere om dette problem [her](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>Andre ressourcer

- [Script til løsning af duplikerede hovednavne på brugere](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Sådan forberedes et domæne, der ikke kan kan rous, (f.eks. domænet .local) til katalogsynkronisering](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script, der tæller det samlede antal synkroniserede objekter](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Fejlfinding af AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Brug PowerShell til at løse tomme attributter for Visningsnavn for mailaktiverede grupper](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Brug PowerShell til at rette duplikerede UPN'er](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Brug PowerShell til at rette duplikerede mailadresser](https://go.microsoft.com/fwlink/p/?LinkId=396731)
