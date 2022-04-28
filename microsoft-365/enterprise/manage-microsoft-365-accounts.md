---
title: Administrer Microsoft 365 brugerkonti
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du administrerer Microsoft 365 brugerkonti.
ms.openlocfilehash: dbd1c0a3c1c6fdb10d157299552e83a77f495e3c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098334"
---
# <a name="manage-microsoft-365-user-accounts"></a>Administrer Microsoft 365 brugerkonti

Du kan administrere Microsoft 365 brugerkonti på flere forskellige måder, afhængigt af din konfiguration. Du kan administrere brugerkonti på [Microsoft 365 Administration](/admin), [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md), i Active Directory-domæneservices (AD DS) eller på administrationsportalen Azure Active Directory (Azure AD). 

Så snart du køber Microsoft 365, kan <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> og PowerShell bruges til at administrere konti. Når du administrerer cloudidentiteter, har alle personer i din organisation et separat brugerkontonavn og en separat adgangskode. Hvis du vil integrere med infrastrukturen i det lokale miljø og synkronisere brugerkonti med Microsoft 365, kan du bruge Azure AD-Forbind til at synkronisere identiteter og adgangskoder for enkeltlogonfunktionalitet (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planlæg, hvor og hvordan du vil administrere dine brugerkonti

Hvor og hvordan du kan administrere dine brugerkonti, afhænger af den identitetsmodel, du vil bruge til dine Microsoft 365. De to overordnede modeller er cloudbaserede og hybride.
  
### <a name="cloud-only"></a>Kun i skyen

Du opretter og administrerer brugere i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Du kan også bruge PowerShell eller Azure AD Administration. 
    
### <a name="hybrid"></a>Hybrid

Brugerkonti synkroniseres med Microsoft 365 fra AD DS, så du skal bruge AD DS-værktøjer i det lokale miljø til at administrere brugerkonti. 
    
## <a name="managing-accounts"></a>Administration af konti

Når du beslutter, hvordan din organisation skal oprette og administrere konti, skal du overveje følgende krav:
  
- Softwaren til katalogsynkronisering skal installeres på servere i dit lokale miljø for at forbinde identiteterne mellem Microsoft 365 og AD DS.
    
- Alle indstillinger for katalogsynkronisering, herunder SSO-indstillinger, kræver, at dine AD DS-attributter opfylder standarderne. De specifikke oplysninger om, hvilke attributter der bruges i mappen, og hvilken oprydning (hvis der er behov for), er beskrevet i [Forbered synkronisering af mapper til Microsoft 365](prepare-for-directory-synchronization.md). 
    
- Planlæg, hvordan du vil oprette Microsoft 365 konti.
    
I følgende tabel vises de forskellige værktøjer til kontoadministration.
    
|Værktøj|Bemærkninger|
|:-----|:-----|
|Microsoft 365 Administration  <br/> |[Tilføj brugere enkeltvist eller samlet](../admin/add-users/add-users.md) <br/>  Indeholder en enkel webgrænseflade til tilføjelse og ændring af brugerkonti.  <br/>  Kan ikke bruges til at ændre brugere, hvis katalogsynkronisering er aktiveret (placering og licenstildeling kan angives).  <br/>  Kan ikke bruges sammen med SSO-indstillinger.  <br/> |
|Windows PowerShell  <br/> |[Administrer Microsoft 365 med Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  Giver dig mulighed for at tilføje brugere i massebrugere ved hjælp af et Windows PowerShell script.  <br/>  Kan bruges til at tildele konti placering og licenser, uanset hvordan kontiene oprettes.  <br/> |
|Masseimport  <br/> |[Tilføj flere brugere på samme tid](add-several-users-at-the-same-time.md) <br/>  Giver dig mulighed for at importere en CSV-fil for at føje en gruppe brugere til Microsoft 365.  <br/>  Kan ikke bruges sammen med SSO-indstillinger.  <br/> |
|Azure AD  <br/> |Du får en gratis udgave af Azure AD med dit abonnement på Microsoft 365. Du kan udføre funktioner som selvbetjent nulstilling af adgangskode for cloudbrugere og tilpasning af logon- og Adgangspanel-siderne ved hjælp af den gratis udgave. Hvis du vil have forbedret funktionalitet, kan du opgradere til den grundlæggende udgave, Azure AD Premium P1 eller Azure AD Premium P2. Se [Azure AD-udgaver](/azure/active-directory/fundamentals/active-directory-whatis) for at få vist en liste over understøttede funktioner.  <br/> |
|Katalogsynkronisering  <br/> |[Integration af dine identiteter i det lokale miljø med Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  Til katalogsynkronisering med eller uden synkronisering af adgangskode skal du bruge [Azure AD-Forbind med hurtig konfiguration](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  Hvis du vil have flere skove og SSO-indstillinger, skal du bruge [Brugerdefineret installation af Azure AD-Forbind](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  Leverer den infrastruktur, der er nødvendig for at aktivere SSO.  <br/>  Påkrævet til mange hybridscenarier, f.eks. faseindret migrering og hybride Exchange  <br/>  Synkroniserer sikkerheds- og mailaktiverede grupper fra dit AD DS.  <br/> |
|||
   
- Uanset hvordan du vil føje brugerkontiene til Microsoft 365, skal du administrere flere kontofunktioner, f.eks. tildeling af licenser, angivelse af placering osv. Disse funktioner kan administreres på lang sigt fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration,</a> eller du kan også [oprette brugerkonti med PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    Hvis du vælger at tilføje og administrere alle dine brugere via Administration, skal du angive placeringen og tildele licenser samtidig med oprettelsen af den Microsoft 365 konto. Derfor er det ikke meget planlægning, der kræves.
    
    > [!IMPORTANT]
    > Oprettelse af konti i Microsoft 365 uden at tildele en licens (f.eks. til SharePoint Online) betyder, at kontoejeren kan få vist Microsoft 365 center, men ikke kan få adgang til nogen af tjenesterne i firmaets abonnement. Når du har tildelt en placering og licensen, replikeres kontoen til den eller de tjenester, du har tildelt. Brugeren kan logge på sin konto og bruge de tjenester, du har tildelt til vedkommende. 
  
## <a name="see-also"></a>Se også

[Microsoft 365 Administration](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)