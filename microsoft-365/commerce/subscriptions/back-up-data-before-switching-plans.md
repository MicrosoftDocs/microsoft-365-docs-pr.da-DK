---
title: Sikkerhedskopiér data, før du ændrer planer
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
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
description: Backup Outlook, OneDrive, Yammer og SharePoint indhold, før du ændrer Microsoft 365 planer.
ms.date: 03/17/2021
ms.openlocfilehash: fd5239deb88fbf9b87df7e62d85a3d2cc18e1df7
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102498"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Sikkerhedskopiér data, før du skifter Microsoft 365 til virksomhedsplaner

Hvis en bruger skifter til et andet abonnement, der har færre datarelaterede tjenester, eller en bruger forlader organisationen, kan en kopi af vedkommendes data, der er gemt i Microsoft 365, downloades, før brugeren skifter til det nye abonnement.

Hvis du flytter en bruger til et abonnement, der har de samme eller flere tjenester, behøver du ikke at sikkerhedskopiere brugerdata. Se [Flyt brugere til et andet abonnement](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Gem en kopi af Outlook oplysninger

Hvis brugerne har Outlook, kan de [eksportere eller sikkerhedskopiere mails, kontakter og kalender til en Outlook .pst-fil,](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) før deres plan ændres.
  
Når skiftet til den nye plan er fuldført, kan brugerne [importere mail, kontakter og kalender fra en Outlook .pst-fil](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Gem filer, der er gemt i OneDrive for Business

Før brugerne skifter til et andet abonnement, kan de [downloade filer og mapper fra OneDrive eller SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) til en anden placering, f.eks. en mappe på computerens harddisk eller et filshare på organisationens netværk.
  
## <a name="save-yammer-information"></a>Gem Yammer oplysninger

Administratorer kan eksportere alle meddelelser, noter, filer, emner, brugere og grupper til en .zip fil. Du kan finde flere oplysninger under [Eksportér data fra Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Udviklere kan også bruge [Yammer API'en](https://go.microsoft.com/fwlink/p/?linkid=842495) til at gøre dette.
  
## <a name="how-to-save-sharepoint-information"></a>Sådan gemmer du SharePoint oplysninger

Hvis en bruger skifter fra et abonnement, der har SharePoint Online, til et abonnement, der ikke har det, vises det **SharePoint** felt ikke længere i menuen Microsoft 365.
  
Så længe det nye abonnement er inden for den samme organisation, som det, de skifter fra, vil brugerne dog stadig kunne få adgang til SharePoint teamwebsted. De kan få vist og opdatere notesbøger, dokumenter, opgaver og kalendere ved hjælp af den direkte URL-adresse til teamwebstedet.
  
> [!TIP]
> Vi anbefaler, at brugerne går til teamwebstedet, før deres abonnement ændres, og gemmer URL-adressen som en favorit eller et bogmærke i deres browser.
  
URL-adressen til teamwebstedet er som standard i denne form:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

hvor  _\<orgDomain\>_ er organisationens URL-adresse.
  
Hvis domænet for organisationen f.eks. er contoso.onmicrosoft.com, vil den direkte URL-adresse til teamwebstedet være `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Brugerne kan naturligvis også downloade SharePoint Online-dokumenter fra SharePoint teamwebsted til deres lokale computer eller til en anden placering når som helst.
