---
title: Sikkerhedskopier data, før du ændrer planer
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Sikkerhedskopiering Outlook, OneDrive, Yammer og SharePoint, før du ændrer Microsoft 365 planer.
ms.date: 03/17/2021
ms.openlocfilehash: 57f897b353cfe61d5c9cae56c1d367d5e57a29ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588485"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Sikkerhedskopier data, før du skifter Microsoft 365 for business-planer

Hvis en bruger skiftes til et andet abonnement, der har færre datarelaterede tjenester, eller en bruger forlader organisationen, kan der downloades en kopi af deres data, der er gemt i Microsoft 365, før de skiftes til det nye abonnement.

Hvis du flytter en bruger til et abonnement, der har de samme eller flere tjenester, behøver du ikke at sikkerhedskopire brugerdata. Se [Flyt brugere til et andet abonnement](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Gem en kopi af Outlook oplysninger

Hvis brugerne har Outlook, kan de eksportere eller sikkerhedskopiere mail, kontakter og kalender til en [Outlook .pst-fil](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91), før deres plan skiftes.
  
Når skiftet til den nye plan er afsluttet, kan brugerne Importere mail, kontakter og kalender [fra en Outlook .pst-fil](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Gem filer, der er gemt i OneDrive for Business

Før brugere skifter til et andet abonnement, kan de downloade filer og mapper fra OneDrive eller SharePoint til en anden placering, f.eks. en mappe på computerens harddisk eller et filshare på [organisationens](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) netværk.
  
## <a name="save-yammer-information"></a>Gem Yammer oplysninger

Administratorer kan eksportere alle meddelelser, noter, filer, emner, brugere og grupper til en .zip fil. Få mere at vide under [Eksportér data fra Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Udviklere kan også [Yammer API'en](https://go.microsoft.com/fwlink/p/?linkid=842495) til at gøre dette.
  
## <a name="how-to-save-sharepoint-information"></a>Sådan gemmes SharePoint oplysninger

Hvis en bruger er skiftet fra et abonnement, der har SharePoint Online, til et, der ikke har det, **vises SharePoint-feltet** ikke længere i deres Microsoft 365-menu.
  
Men så længe det nye abonnement er i den samme organisation, som det brugeren skiftede fra, vil brugerne stadig kunne få adgang til det SharePoint teamwebsted. De kan få vist og opdatere notesbøger, dokumenter, opgaver og kalendere ved hjælp af den direkte URL-adresse til teamwebstedet.
  
> [!TIP]
> Vi anbefaler, at brugerne går til teamwebstedet, før deres abonnement er skiftet, og gemmer URL-adressen som en favorit eller et bogmærke i deres browser.
  
Som standard er URL-adressen til teamwebstedet i denne formular:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

hvor  _\<orgDomain\>_ er organisationens URL-adresse.
  
Hvis f.eks. organisationens domæne er contoso.onmicrosoft.com, så er den direkte URL-adresse til teamwebstedet `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Brugerne kan selvfølgelig også downloade SharePoint Online-dokumenter fra SharePoint-teamwebstedet til deres lokale computer eller til et andet sted når som helst.
