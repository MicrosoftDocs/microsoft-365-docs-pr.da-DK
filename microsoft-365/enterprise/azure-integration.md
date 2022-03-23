---
title: Integration af Azure med Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Integrer Microsoft 365 med Azure AD, hvis du vil have synkronisering af adgangskoder eller enkelt logon med dit lokale miljø.
ms.openlocfilehash: 2d560c2d94552b91c4325a74f99d2f34aa1af399
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63590373"
---
# <a name="azure-integration-with-microsoft-365"></a>Integration af Azure med Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 bruger Azure Active Directory (Azure AD) til at administrere brugeridentiteter i baggrunden. Dit Microsoft 365-abonnement omfatter et gratis Azure AD-abonnement, så du kan integrere din lokale Active Directory-domæneservices (AD DS) for at synkronisere brugerkonti og adgangskoder eller konfigurere enkelt logon. Du kan også købe avancerede funktioner for bedre at administrere dine konti.
  
Azure AD tilbyder også andre funktioner, f.eks. administration af integrerede apps, som du kan bruge til at udvide og tilpasse Microsoft 365 abonnementer.
  
Du kan bruge Azure AD-installationsrådgivere til en guidet konfigurations- og konfigurationsoplevelse i Microsoft 365 Administration (du skal være logget på Microsoft 365):

 - [Azure AD Forbind rådgiver](https://aka.ms/aadconnectpwsync)
 - [AD FS-installationsrådgiver](https://aka.ms/adfsguidance)
 - [Azure AD-konfigurationsvejledning](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Azure AD-versioner og administration Microsoft 365 identitet

Hvis du har et betalt abonnement på Microsoft 365, har du også et gratis Azure AD-abonnement. Du kan bruge Azure AD til at oprette og administrere bruger- og gruppekonti. For at aktivere dette abonnement skal du gennemføre en registrering én gang. Derefter kan du få adgang til Azure AD fra Microsoft 365 Administration. 

Du kan finde en vejledning til at registrere dit gratis Azure AD-abonnement [under Brug dit gratis Azure AD-abonnement](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). Gå ikke direkte til azure.microsoft.com for at tilmelde dig, da du ender med en prøveversion eller et betalt abonnement på Microsoft Azure, der er adskilt fra dit gratis Azure AD-abonnement med Microsoft 365. 
  
Med det gratis abonnement kan du synkronisere med lokale kataloger, konfigurere enkelt logon og synkronisere med mange software- og tjenesteprogrammer, f.eks. Salesforce, DropBox og mange flere.
  
Hvis du vil have AD DS funktionalitet, tovejs-synkronisering og andre administrationsfunktioner, kan du opgradere dit gratis abonnement til et betalt premium-abonnement. Du kan finde flere oplysninger [Azure Active Directory versioner](https://azure.microsoft.com/pricing/details/active-directory/).
  
Du kan finde flere oplysninger Microsoft 365 og Azure AD under Microsoft 365 [identitetsmodeller](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Udvid mulighederne for din Microsoft 365 lejer

|**Funktion**|**Beskrivelse**|
|:-----|:-----|
|Integrerede apps  <br/> |Du kan give individuelle apps adgang til dine Microsoft 365, f.eks. mail, kalendere, kontakter, brugere, grupper, filer og mapper. Du kan også godkende disse apps på **Azure AD DC-administratorniveau** eller **globalt administratorniveau** og gøre dem tilgængelige for hele virksomheden ved at registrere appsene i Azure AD. Du kan finde flere oplysninger [i Integrerede apps og Azure AD til Microsoft 365 administratorer](integrated-apps-and-azure-ads.md).<br/> Du kan få mere at vide [under Om administratorroller](/microsoft-365/admin/add-users/about-admin-roles?). <br/> Se [også Enkelt logon](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps er fokuserede apps til mobilenheder, der kan oprette forbindelse til dine eksisterende datakilder, f.eks. SharePoint lister og andre dataapps. Se [Opret en Power-app for en liste i SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) og siden Power Apps [for at](https://powerapps.microsoft.com/) få mere at vide.  <br/> |
   
## <a name="see-also"></a>Se også

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)
