---
title: Administrere Microsoft 365 brugerkonti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Få mere at vide om, Microsoft 365 administrerer brugerkonti.
ms.openlocfilehash: 7f75c74984ce58a8b403f01948075b185047f260
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591603"
---
# <a name="manage-microsoft-365-user-accounts"></a>Administrere Microsoft 365 brugerkonti

Du kan administrere Microsoft 365 brugerkonti på flere forskellige måder, afhængigt af din konfiguration. Du kan administrere brugerkonti [på Microsoft 365 Administration](/admin), [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), i Active Directory-domæneservices (AD DS) eller i Azure Active Directory -administrationsportalen (Azure AD). 

Så snart du køber Microsoft 365, kan <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> og PowerShell bruges til at administrere konti. Når du administrerer skyidentiteter, har hver person i organisationen et separat brugernavn og adgangskode. Hvis du vil integrere med din lokale infrastruktur og har brugerkonti, der er synkroniseret med Microsoft 365, kan du bruge Azure AD Forbind til at levere synkronisering af identiteter og adgangskoder til enkelttegn-on-funktionalitet (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planlæg, hvor og hvordan du vil administrere dine brugerkonti

Hvor og hvordan du kan administrere dine brugerkonti afhænger af den identitetsmodel, du vil bruge til din Microsoft 365. De to overordnede modeller er kun skybaserede og hybride.
  
### <a name="cloud-only"></a>Kun i skyen

Du opretter og administrerer brugere i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Du kan også bruge PowerShell eller Azure AD Administration. 
    
### <a name="hybrid"></a>Hybrid

Brugerkonti synkroniseres med Microsoft 365 fra AD DS, så du skal bruge lokale AD DS til at administrere brugerkonti. 
    
## <a name="managing-accounts"></a>Administration af konti

Når du beslutter, hvordan din organisation skal oprette og administrere konti, skal du overveje følgende krav:
  
- Softwaren til katalogsynkronisering skal installeres på servere i dit lokale miljø for at forbinde identiteter mellem Microsoft 365 og AD DS.
    
- Enhver indstilling til katalogsynkronisering, herunder SSO-indstillinger, kræver, at AD DS attributter opfylder standarderne. De specifikke oplysninger om, hvilke attributter der bruges i biblioteket, og hvilken oprydning (hvis der er behov for), er beskrevet i Forbered katalogsynkronisering på [Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Planlæg, hvordan du vil oprette Microsoft 365 konti.
    
I følgende tabel vises de forskellige værktøjer til kontoadministration.
    
|Værktøj|Bemærkninger|
|:-----|:-----|
|Microsoft 365 Administration  <br/> |[Tilføj brugere enkeltvis eller flere af gangen](../admin/add-users/add-users.md) <br/>  Indeholder en enkel webgrænseflade til tilføjelse og ændring af brugerkonti.  <br/>  Kan ikke bruges til at ændre brugere, hvis katalogsynkronisering er aktiveret (placering og licenstildeling kan angives).  <br/>  Kan ikke bruges med SSO-indstillinger.  <br/> |
|Windows PowerShell  <br/> |[Administrer Microsoft 365 med Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Gør det muligt at tilføje flere brugere flere brugere ved hjælp af Windows PowerShell script.  <br/>  Kan bruges til at tildele placering og licenser til konti, uanset hvordan kontiene oprettes.  <br/> |
|Masseimport  <br/> |[Tilføj flere brugere på samme tid](add-several-users-at-the-same-time.md) <br/>  Giver dig mulighed for at importere en CSV-fil for at tilføje en gruppe af brugere Microsoft 365.  <br/>  Kan ikke bruges med SSO-indstillinger.  <br/> |
|Azure AD  <br/> |Du får en gratis udgave af Azure AD med dit Microsoft 365 abonnement. Du kan udføre funktioner som nulstilling af adgangskode via selvbetjening for brugere i skyen og tilpasning af siderne Logon og Adgangspanel ved hjælp af den gratis udgave. For at få forbedret funktionalitet kan du opgradere til Basic-versionen, Azure AD Premium P1 eller Azure AD Premium P2. Se [Azure AD-udgaver for at](/azure/active-directory/fundamentals/active-directory-whatis) få en liste over understøttede funktioner.  <br/> |
|Katalogsynkronisering  <br/> |[Integration af identiteter i det lokale miljø med Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  Til katalogsynkronisering med eller uden synkronisering af adgangskoder skal du [bruge Azure AD Forbind hurtig konfiguration](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  Til flere områder og SSO-indstillinger skal du bruge [Brugerdefineret installation af Azure AD Forbind](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  Indeholder den infrastruktur, der er nødvendig for at aktivere SSO.  <br/>  Påkrævet til mange hybridscenarier, f.eks. faseinddeindret migrering og Exchange  <br/>  Synkroniserer sikkerhed og mailaktiverede grupper fra AD DS.  <br/> |
|||
   
- Uanset hvordan du vil føje brugerkonti til Microsoft 365, skal du administrere flere kontofunktioner, f.eks. tildeling af licenser, angivelse af placering osv. Disse funktioner kan administreres langsigtet fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration eller du</a> kan også [oprette brugerkonti med PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Hvis du vælger at tilføje og administrere alle dine brugere via Administration, skal du angive placeringen og tildele licenser samtidig med, at du opretter den Microsoft 365 konto. Der kræves derfor ikke meget planlægning.
    
    > [!IMPORTANT]
    > Når du opretter konti i Microsoft 365 uden at tildele en licens (f.eks. til SharePoint Online), betyder det, at kontoejeren kan se Microsoft 365-center, men ikke få adgang til tjenesterne i virksomhedens abonnement. Når du tildeler en placering og licensen, replikeres kontoen til den eller de tjenester, du har tildelt. Brugeren kan logge på sin konto og bruge de tjenester, du har tildelt brugeren. 
  
## <a name="see-also"></a>Se også

[Microsoft 365 Administration](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)