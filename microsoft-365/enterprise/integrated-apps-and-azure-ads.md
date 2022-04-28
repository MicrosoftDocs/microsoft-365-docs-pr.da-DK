---
title: Integrerede apps og Azure AD til Microsoft 365 administratorer
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
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
description: Få mere at vide om, hvordan du registrerer og administrerer Office 365 integrerede apps i Azure AD, hvilket giver mulighed for appgodkendelser hos **Azure AD DC-administratoren** eller **på globalt administratorniveau**.
ms.openlocfilehash: 63d88d5b39dd88fafa9bb874d7d0a9df11f89462
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091187"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Integrerede apps og Azure AD til Microsoft 365 administratorer

Der er mere at administrere integrerede apps end blot [at administrere brugersamtykke til apps](../admin/misc/user-consent.md). Med Microsoft 365 REST API'er kan brugerne give apps adgang til deres Microsoft 365 data, f.eks. mail, kalendere, kontakter, brugere, grupper, filer og mapper. Som standard skal brugerne individuelt tildele tilladelser til hver app. 

Men det skaleres ikke godt, hvis du vil godkende en app én gang på **Azure AD DC-administratoren** eller **på globalt administratorniveau** og udrulle den til hele organisationen via appstarteren. Hvis du vil gøre dette, skal du registrere appen i Azure Active Directory (Azure AD). Der er nogle trin, du skal udføre, før du kan registrere en app i Azure AD, og nogle baggrundsoplysninger, du bør vide, som kan hjælpe dig med at administrere apps i din Microsoft 365 organisation.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Azure AD-ressourcer til Microsoft 365 administratorer

Du skal udføre disse to opgaver, før du kan administrere dine Microsoft 365 apps i Azure AD.
  
|Forudsætninger|Kommentarer|
|:-----|:-----|
|[Brug dit gratis Azure AD-abonnement](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |Alle betalte abonnementer på Microsoft 365 leveres med et gratis abonnement på Azure AD. Du kan bruge Azure AD til at administrere dine apps og til at oprette og administrere bruger- og gruppekonti. Hvis du vil bruge Azure AD, skal du blot gå til Azure Portal på og logge på [https://portal.azure.com](https://portal.azure.com) med din Microsoft 365 konto.  <br/> |
|[Administrer brugersamtykke til apps](../admin/misc/user-consent.md) <br/> |Du skal administrere brugerens samtykke til apps for at give tredjepartsapps adgang til bruger Microsoft 365 oplysninger og for at du kan registrere apps i Azure AD. Når en person f.eks. bruger en tredjepartsapp, kan denne app bede om tilladelse til at få adgang til deres kalender og til at redigere filer, der findes i en OneDrive mappe.  <br/> |
   
Administration af Microsoft 365 apps kræver, at du har kendskab til apps i Azure AD. Brug disse artikler til at give dig den baggrund, du har brug for.
  
|Artikel|Kommentarer|
|:-----|:-----|
|[Mød Microsoft 365 appstarteren](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Hvis du ikke kender appstarteren før, undrer du dig måske over, hvad det er, og hvordan du bruger det. Appstarteren er designet til at hjælpe dig med at få fat i dine apps overalt i Microsoft 365.  <br/> |
|[oversigt over API'er til Office 365 administration](/office/office-365-management-api/office-365-management-apis-overview) <br/> |Med API'erne til Microsoft 365 administration kan du give adgang til dine Microsoft 365 data, herunder de ting, de interesserer sig mest for – deres mail, kalendere, kontakter, brugere og grupper, filer og mapper. <br/> |
|[Integration af programmer i Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Få mere at vide om programmer, der er integreret i Azure AD, og hvordan du registrerer dit program, forstår begreber bag et registreret program og får mere at vide om retningslinjer for branding for programmer med flere lejere.  <br/> |
|[Føj brugerdefinerede felter til appstarteren](/office365/admin/manage/customize-the-app-launcher)  <br/> |Appstarteren i Microsoft 365 gør det nemmere for brugerne at finde og få adgang til deres apps. I denne artikel beskrives, hvordan du som udvikler kan få dine apps vist i brugernes appstartere, og du kan også give dem en enkeltlogonoplevelse (SSO) ved hjælp af deres Microsoft 365 legitimationsoplysninger.  <br/> |
|[Selvstudier om integration af Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |Formålet med disse selvstudier er at vise dig, hvordan du konfigurerer Azure AD SSO til SaaS-tredjepartsprogrammer.  <br/> |
|[Godkendelsesscenarier for Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |Azure AD forenkler godkendelse for udviklere ved at levere identitet som en tjeneste med understøttelse af branchestandardprotokoller som OAuth 2.0 og OpenID Forbind samt åben kildekode biblioteker til forskellige platforme, der kan hjælpe dig med hurtigt at komme i gang med kodning. Dette dokument hjælper dig med at forstå de forskellige scenarier, som Azure AD understøtter, og viser dig, hvordan du kommer i gang.  <br/> |
|[Programadgang](/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD muliggør nem integration i mange af nutidens populære SaaS-programmer (Software As a Service). Den leverer identitets- og adgangsstyring og giver brugerne en Adgangspanel, hvor de kan finde ud af, hvilken programadgang de har, og hvor de kan bruge SSO til at få adgang til deres programmer. I denne artikel får du links til de relaterede ressourcer, der giver dig mulighed for at få mere at vide om forbedringer af programadgang til Azure AD, og hvordan du kan bidrage til dem.  <br/> |
|[Tilpas din Office 365 oplevelse](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Du kan få hurtig adgang til de apps, du bruger hver dag, ved at tilføje eller fjerne apps i Microsoft 365 appstarter.  <br/> |
