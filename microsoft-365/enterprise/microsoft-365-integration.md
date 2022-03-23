---
title: Microsoft 365 integration med lokale miljøer
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
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: I denne artikel kan du lære, hvordan du Microsoft 365 med dine eksisterende katalogtjenester og lokale miljøer.
ms.openlocfilehash: ca407e6cb77f829b4c6e8de680772817659aeeec
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63590601"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365 integration med lokale miljøer

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan integrere Microsoft 365 med dine eksisterende lokale Active Directory-domæneservices (AD DS) og med lokale installationer af Exchange Server, Skype for Business Server 2015 eller SharePoint Server.
  
 - Når du integrerer AD DS, kan du synkronisere og administrere brugerkonti for begge miljøer. Du kan også tilføje synkronisering af adgangskodehash (PHS) eller enkeltlogo (SSO), så brugerne kan logge på begge miljøer med deres lokale legitimationsoplysninger.
 - Når du integrerer med serverprodukter i det lokale miljø, opretter du et hybridmiljø. Et hybridmiljø kan hjælpe, når du overfører brugere eller oplysninger til Microsoft 365, eller du kan fortsætte med at have nogle brugere eller nogle oplysninger lokalt og nogle i skyen. Du kan finde flere oplysninger om hybridmiljøer i [hybridsky.](../solutions/cloud-architecture-models.md#hybrid)

Du kan også bruge rådgiverne Azure Active Directory (Azure AD) for at få tilpasset konfigurationsvejledning i Microsoft 365 Administration (du skal være logget på Microsoft 365):

- [Azure AD-konfigurationsvejledning](https://aka.ms/aadpguidance)
- [Synkroniser brugere fra organisationens adresseliste](https://aka.ms/aadconnectpwsync)
- [Active Directory Federation Services-installationsrådgiver (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>Før du begynder

Før du integrerer Microsoft 365 og et lokalt miljø, skal du også foretage netværksplanlægning [og justering af ydeevnen](network-planning-and-performance.md). Det er også en ide at forstå de tilgængelige [identitetsmodeller](deploy-identity-solution-identity-model.md). 

Se [Administrer Microsoft 365-konti](manage-microsoft-365-accounts.md) for en liste over værktøjer, du kan bruge til at administrere Microsoft 365-brugerkonti. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>Integrer Microsoft 365 med AD DS

Hvis du har eksisterende brugerkonti i AD DS, ønsker du ikke at oprette alle disse konti i Microsoft 365 igen og risikerer at introducere forskelle eller fejl mellem miljøerne. Katalogsynkronisering hjælper dig med at spejle disse konti mellem dit lokale miljø og dine onlinemiljøer. Med katalogsynkronisering behøver dine brugere ikke at huske nye oplysninger for hvert miljø, og du behøver ikke at oprette eller opdatere konti to gange. Du skal forberede [dit lokale katalog til katalogsynkronisering](prepare-for-directory-synchronization.md) .
  
![Brug katalogsynkronisering til at holde lokale og online brugerkontooplysninger synkroniserede.](../media/microsoft-365-integration/directory-synchronization.png)
  
Hvis du ønsker, at brugerne skal kunne logge på Microsoft 365 med deres lokale legitimationsoplysninger, kan du også konfigurere SSO (SSO). Med SSO er Microsoft 365 konfigureret til at have tillid til det lokale miljø til brugergodkendelse.
  
![Med enkelt logon er den samme konto tilgængelig både lokalt og online.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>Katalogsynkronisering med eller uden synkronisering af adgangskodehash eller pass-through-godkendelse (PTA)

En bruger logger på sit lokale miljø med sin brugerkonto (domæne\brugernavn). Når brugeren går til Microsoft 365, skal han eller hun logge på igen med sin arbejds- eller skolekonto (user@domain.com). Brugernavnet er det samme i begge miljøer. Når du tilføjer PHS eller PTA, har brugeren den samme adgangskode til begge miljøer, men skal angive disse legitimationsoplysninger igen, når der logges på Microsoft 365. Katalogsynkronisering med PHS er den mest almindeligt anvendte katalogsynkronisering.

Du kan konfigurere katalogsynkronisering ved at bruge Azure AD Forbind. Du kan finde en vejledning [under Konfigurer katalogsynkronisering til Microsoft 365](set-up-directory-synchronization.md) [og Azure AD Forbind med hurtig konfiguration](/azure/active-directory/hybrid/how-to-connect-install-express).

Få mere at vide [om forberedelse til katalogsynkronisering med Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>Katalogsynkronisering med SSO

En bruger logger på sit lokale miljø med sin brugerkonto. Når brugeren går til Microsoft 365, logges der enten på automatisk, eller der logges på med de samme legitimationsoplysninger, der bruges til det lokale miljø (domæne\brugernavn).

Hvis du vil konfigurere SSO, skal du også bruge Azure AD Forbind. Du kan finde en vejledning [under Brugerdefineret installation af Azure AD Forbind](/azure/active-directory/hybrid/how-to-connect-install-custom).

Du kan finde flere oplysninger [i Single Sign-On](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Forbind ældre versioner af værktøjer til identitetsintegration som f.eks. DirSync og Azure AD Sync. Hvis du vil opdatere fra Azure Active Directory synkronisere til Azure AD Forbind, skal du se [opgraderingsvejledningen](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>Se også

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)