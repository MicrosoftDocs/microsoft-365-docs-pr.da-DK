---
title: Azure-integration med Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Integrer Microsoft 365 med Azure AD, hvis du vil have synkronisering af adgangskoden eller enkeltlogon med dit lokale miljø.
ms.openlocfilehash: bebbad10d0fb7a61437dcb24398ebb88d90db739
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096826"
---
# <a name="azure-integration-with-microsoft-365"></a>Azure-integration med Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 bruger Azure Active Directory (Azure AD) til at administrere brugeridentiteter i baggrunden. Dit Microsoft 365-abonnement omfatter et gratis Azure AD-abonnement, så du kan integrere dit AD DS (Active Directory i det lokale miljø Domain Services) for at synkronisere brugerkonti og adgangskoder eller konfigurere enkeltlogon. Du kan også købe avancerede funktioner for bedre at administrere dine konti.
  
Azure AD tilbyder også andre funktioner, f.eks. administration af integrerede apps, som du kan bruge til at udvide og tilpasse dine Microsoft 365 abonnementer.
  
Du kan bruge Azure AD-udrulningsrådgiverne til en guidet konfigurationsoplevelse i Microsoft 365 Administration (du skal være logget på Microsoft 365):

 - [Azure AD Forbind advisor](https://aka.ms/aadconnectpwsync)
 - [AD FS-udrulningsrådgiver](https://aka.ms/adfsguidance)
 - [Konfigurationsvejledning til Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>Azure AD-udgaver og Microsoft 365 identitetsstyring

Hvis du har et betalt abonnement på Microsoft 365, har du også et gratis Azure AD-abonnement. Du kan bruge Azure AD til at oprette og administrere bruger- og gruppekonti. Hvis du vil aktivere dette abonnement, skal du fuldføre en engangsregistrering. Derefter kan du få adgang til Azure AD fra din Microsoft 365 Administration. 

Du kan finde oplysninger om, hvordan du registrerer dit gratis Azure AD-abonnement, under [Brug dit gratis Azure AD-abonnement](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). Gå ikke direkte til azure.microsoft.com for at tilmelde dig, ellers får du en prøveversion eller et betalt abonnement på Microsoft Azure, der er adskilt fra dit gratis Azure AD-abonnement med Microsoft 365. 
  
Med det gratis abonnement kan du synkronisere med mapper i det lokale miljø, konfigurere enkeltlogon og synkronisere med mange programmer som tjenesteprogrammer, f.eks. Salesforce, DropBox og mange flere.
  
Hvis du vil have forbedret AD DS-funktionalitet, tovejssynkronisering og andre administrationsfunktioner, kan du opgradere dit gratis abonnement til et betalt Premium-abonnement. Du kan finde flere oplysninger i [Azure Active Directory udgaver](https://azure.microsoft.com/pricing/details/active-directory/).
  
Du kan få flere oplysninger om Microsoft 365 og Azure AD [under Microsoft 365 identitetsmodeller](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>Udvid egenskaberne for din Microsoft 365 lejer

|**Funktion**|**Beskrivelse**|
|:-----|:-----|
|Integrerede apps  <br/> |Du kan give individuelle apps adgang til dine Microsoft 365 data, f.eks. mail, kalendere, kontakter, brugere, grupper, filer og mapper. Du kan også godkende disse apps på **Azure AD DC-administrator-** eller **globalt administratorniveau** og gøre dem tilgængelige for hele virksomheden ved at registrere appsene i Azure AD. Du kan få flere oplysninger under [Integrerede apps og Azure AD til Microsoft 365 administratorer](integrated-apps-and-azure-ads.md).<br/> Du kan få mere at vide under [Om administratorroller](/microsoft-365/admin/add-users/about-admin-roles?). <br/> Se også [Enkeltlogon](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|Power Apps  <br/> | Power Apps er fokuserede apps til mobilenheder, der kan oprette forbindelse til dine eksisterende datakilder, f.eks. SharePoint lister og andre dataapps. Se [Opret en Power App for at få vist en liste i SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) og [på siden Power Apps](https://powerapps.microsoft.com/) for at få flere oplysninger.  <br/> |
   
## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)
