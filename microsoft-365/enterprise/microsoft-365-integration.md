---
title: Microsoft 365 integration med lokale miljøer
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
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: I denne artikel kan du få mere at vide om, hvordan du integrerer Microsoft 365 med dine eksisterende katalogtjenester og lokale miljøer.
ms.openlocfilehash: a3ba75fd2f2b69e71d5b14b14e17827ed96e4dd4
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093893"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365 integration med lokale miljøer

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan integrere Microsoft 365 med din eksisterende AD DS (Active Directory i det lokale miljø Domain Services) og med installationer i det lokale miljø af Exchange Server, Skype for Business Server 2015 eller SharePoint Server.
  
 - Når du integrerer AD DS, kan du synkronisere og administrere brugerkonti for begge miljøer. Du kan også tilføje synkronisering af adgangskodehash (PHS) eller enkeltlogon (SSO), så brugerne kan logge på begge miljøer med deres legitimationsoplysninger i det lokale miljø.
 - Når du integrerer med serverprodukter i det lokale miljø, opretter du et hybridmiljø. Et hybridmiljø kan hjælpe, når du overfører brugere eller oplysninger til Microsoft 365, eller du kan fortsætte med at have nogle brugere eller nogle oplysninger i det lokale miljø og nogle i cloudmiljøet. Du kan få flere oplysninger om hybridmiljøer i [hybridskyen](../solutions/cloud-architecture-models.md#hybrid).

Du kan også bruge rådgiverne for Azure Active Directory (Azure AD) til tilpasset konfigurationsvejledning i Microsoft 365 Administration (du skal være logget på Microsoft 365):

- [Konfigurationsvejledning til Azure AD](https://aka.ms/aadpguidance)
- [Synkroniser brugere fra organisationens mappe](https://aka.ms/aadconnectpwsync)
- [udrulningsrådgiver for Active Directory Federation Services (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Før du begynder

Før du integrerer Microsoft 365 og et lokalt miljø, skal du også foretage [netværksplanlægning og justering af ydeevnen](network-planning-and-performance.md). Du vil også gerne forstå de tilgængelige [identitetsmodeller](deploy-identity-solution-identity-model.md). 

Se [Administrer Microsoft 365 konti](manage-microsoft-365-accounts.md) for at få vist en liste over værktøjer, du kan bruge til at administrere Microsoft 365 brugerkonti. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Integrer Microsoft 365 med AD DS

Hvis du har eksisterende brugerkonti i AD DS, vil du ikke genoprette alle disse konti i Microsoft 365 og risikere at introducere forskelle eller fejl mellem miljøerne. Katalogsynkronisering hjælper dig med at spejle disse konti mellem dine lokale og onlinemiljøer. Med katalogsynkronisering behøver brugerne ikke at huske nye oplysninger for hvert miljø, og du behøver ikke at oprette eller opdatere konti to gange. Du skal [forberede mappen i det lokale miljø](prepare-for-directory-synchronization.md) til katalogsynkronisering.
  
![Brug katalogsynkronisering til at synkronisere oplysninger om brugerkontoen i det lokale miljø og onlinebrugeren.](../media/microsoft-365-integration/directory-synchronization.png)
  
Hvis du ønsker, at brugerne skal kunne logge på Microsoft 365 med deres lokale legitimationsoplysninger, kan du også konfigurere SSO. Med SSO er Microsoft 365 konfigureret til at have tillid til det lokale miljø for brugergodkendelse.
  
![Med enkeltlogon er den samme konto tilgængelig både i det lokale miljø og onlinemiljøer.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Katalogsynkronisering med eller uden synkronisering af adgangskodehash eller pass-through-godkendelse (PTA)

En bruger logger på sit lokale miljø med sin brugerkonto (domæne\brugernavn). Når de går til Microsoft 365, skal de logge på igen med deres arbejds- eller skolekonto (user@domain.com). Brugernavnet er det samme i begge miljøer. Når du tilføjer PHS eller PTA, har brugeren den samme adgangskode til begge miljøer, men vedkommende skal angive disse legitimationsoplysninger igen, når vedkommende logger på Microsoft 365. Katalogsynkronisering med PHS er den mest anvendte katalogsynkronisering .

Hvis du vil konfigurere katalogsynkronisering, skal du bruge Azure AD Forbind. Du kan finde instruktioner under [Konfigurer katalogsynkronisering for Microsoft 365](set-up-directory-synchronization.md) og [Azure AD-Forbind med ekspresindstillinger](/azure/active-directory/hybrid/how-to-connect-install-express).

Få mere at vide om[, hvordan du forbereder katalogsynkronisering for at Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Katalogsynkronisering med SSO

En bruger logger på sit lokale miljø med sin brugerkonto. Når de går til Microsoft 365, logges de enten automatisk på, eller de logger på med de samme legitimationsoplysninger, som de bruger til deres lokale miljø (domæne\brugernavn).

Hvis du vil konfigurere SSO, skal du også bruge Azure AD Forbind. Du kan finde instruktioner under [Brugerdefineret installation af Azure AD-Forbind](/azure/active-directory/hybrid/how-to-connect-install-custom).

Du kan få flere oplysninger under [Enkeltlogon](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Forbind erstatter ældre versioner af værktøjer til identitetsintegration, f.eks DirSync og Azure AD Sync. Hvis du vil opdatere fra Azure Active Directory Synkroniser til Azure AD-Forbind, skal du se [instruktionerne til opgradering](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)