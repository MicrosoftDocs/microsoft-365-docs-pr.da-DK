---
title: Integrerede apps og Azure AD til Microsoft 365 administratorer
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Få mere at vide om, hvordan du registrerer Office 365 administrerer integrerede apps i Azure AD, hvilket muliggør appgodkendelser på **Azure AD DC-administratorniveau** eller **globalt administratorniveau**.
ms.openlocfilehash: 78092ae817708f0af19eaa85648c35a9c413d3fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590598"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Integrerede apps og Azure AD til Microsoft 365 administratorer

Der er mere at administrere integrerede apps end blot at [administrere brugersamtykke til apps](../admin/misc/user-consent.md). Med indførelsen af Microsoft 365 REST-API'er kan brugerne give apps adgang til deres Microsoft 365-data, f.eks. mail, kalendere, kontakter, brugere, grupper, filer og mapper. Som standard skal brugerne tildele tilladelser til hver enkelt app enkeltvis. 

Men det skaleres ikke godt, hvis du vil godkende en app én gang på **Azure AD DC-administratorniveau** eller **globalt** administratorniveau og udrulle den til hele organisationen via appstarteren. For at gøre dette skal du registrere appen i Azure Active Directory (Azure AD). Der er nogle trin, du skal følge, før du kan registrere en app i Azure AD, og nogle baggrundsoplysninger, som du bør vide, som kan hjælpe dig med at administrere apps i din Microsoft 365 organisation.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Azure AD-ressourcer til Microsoft 365 administratorer

Du skal udføre disse to opgaver, før du kan administrere dine Microsoft 365 apps i Azure AD.
  
|Forudsætninger|Kommentarer|
|:-----|:-----|
|[Brug dit gratis Azure AD-abonnement](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Alle betalte abonnementer på Microsoft 365 leveres med et gratis abonnement på Azure AD. Du kan bruge Azure AD til at administrere dine apps og oprette og administrere bruger- og gruppekonti. Hvis du vil bruge Azure AD, skal du blot gå til Azure-portalen [https://portal.azure.com](https://portal.azure.com) og logge på med din Microsoft 365 konto.  <br/> |
|[Administrer brugersamtykke til apps](../admin/misc/user-consent.md) <br/> |Du skal administrere brugersamtykke til apps for at give tredjepartsapps adgang til brugeroplysninger Microsoft 365 og for at du kan registrere apps i Azure AD. Når nogen f.eks. bruger en app fra en tredjepart, kan den pågældende app bede om tilladelse til at få adgang til sin kalender og til at redigere filer, der findes i en OneDrive mappe.  <br/> |
   
Administration Microsoft 365 apps kræver, at du har kendskab til apps i Azure AD. Brug disse artikler til at give dig den baggrund, du har brug for.
  
|Artikel|Kommentarer|
|:-----|:-----|
|[Mød Microsoft 365 i appstarteren](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Hvis du ikke kender appstarteren, undrer du dig måske over, hvad det er, og hvordan den bruges. Appstarteren er udviklet til at hjælpe dig med at få adgang til dine apps overalt Microsoft 365.  <br/> |
|[Office 365 oversigt over ADMINISTRATIONS-API'er](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Api'erne til Microsoft 365-administration giver dig adgang til dine Microsoft 365-data, herunder de ting, der er vigtigst for dem – deres mail, kalendere, kontakter, brugere og grupper, filer og mapper. <br/> |
|[Integration af programmer i Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Få mere at vide om programmer, der er integreret med Azure AD, og hvordan du kan registrere dit program, forstå begreberne bag et registreret program og få mere at vide om brandingretningslinjer for programmer med flere lejere.  <br/> |
|[Føj brugerdefinerede felter til appstarteren](/office365/admin/manage/customize-the-app-launcher)  <br/> |Appstarteren i en Microsoft 365 gør det nemmere for brugerne at finde og få adgang til deres apps. I denne artikel beskrives de måder, hvorpå du som udvikler kan få dine apps vist i brugernes appstartere og også give dem en single sign-on-oplevelse (SSO) med deres Microsoft 365 legitimationsoplysninger.  <br/> |
|[Selvstudier om Integration af Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |Formålet med disse selvstudier er at vise, hvordan du konfigurerer Azure AD SSO til SaaS-programmer fra tredjepart.  <br/> |
|[Godkendelsesscenarier for Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Azure AD forenkler godkendelse for udviklere ved at levere identitet som en tjeneste med understøttelse af branchestandardprotokoller som f.eks. OAuth 2.0 og OpenID Forbind samt open source-biblioteker til forskellige platforme, så du hurtigt kan komme i gang med at kode. Dette dokument hjælper dig med at forstå de forskellige scenarier, som Azure AD understøtter, og viser dig, hvordan du kommer i gang.  <br/> |
|[Programadgang](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD gør det nemt at integrere mange af dagens populære SaaS-programmer (software as a service). Det giver identitets- og adgangsstyring, og det leverer et adgangspanel til brugere, hvor de kan se, hvilken programadgang de har, og hvor de kan bruge SSO til at få adgang til deres programmer. Denne artikel indeholder links til relaterede ressourcer, der giver dig mulighed for at få mere at vide om forbedringerne af programadgang til Azure AD, og hvordan du kan bidrage til dem.  <br/> |
|[Tilpas din Office 365 oplevelse](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Du kan få hurtig adgang til de apps, du bruger hver dag, ved at tilføje eller fjerne apps Microsoft 365 i appstarteren.  <br/> |
