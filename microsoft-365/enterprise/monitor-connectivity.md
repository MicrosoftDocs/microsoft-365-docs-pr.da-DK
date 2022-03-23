---
title: Overvåg Microsoft 365 forbindelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: I denne artikel får du mere at vide om de værktøjer og teknikker, du kan bruge til at overvåge og Microsoft 365 forbindelse.
ms.openlocfilehash: 783278ad69fbe47afd6ea85fdb70c8bb0057005c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590315"
---
# <a name="monitor-microsoft-365-connectivity"></a>Overvåg Microsoft 365 forbindelse

Når du har installeret Microsoft 365, kan du bevare forbindelsen Microsoft 365 ved hjælp af nogle af de værktøjer og teknikker nedenfor. Du bør forstå de officielle retningslinjer for [tjeneste](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) sundhed og kontinuitet samt vores bedste fremgangsmåder for brug af [Microsoft 365 på et langsomt netværk](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Det er også en ide at bruge [Microsoft 365 administratorappen](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) og bogmærke [vores Microsoft 365 for business – hjælp til administratorer](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Overvågning Microsoft 365 forbindelse

|Type overvågning |Beskrivelse |
|:-----|:-----|
|**Få besked om nye Microsoft 365 slutpunkter** <br/> |Hvis du administrerer [Microsoft 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), vil du gerne modtage meddelelser, når vi publicerer nye slutpunkter. Du kan abonnere på vores RSS-feed ved hjælp af din foretrukne RSS-læser. Her kan du se, hvordan [du abonnerer via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416), eller du kan [få RSS-feed-opdateringerne sendt til dig via mail](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Brug System Center til at overvåge Microsoft 365** <br/> |Hvis du bruger Microsoft System Center, kan du hente [Microsoft System Center Operations Manager Management Pack, så du Microsoft 365](https://www.microsoft.com/download/details.aspx?id=103379) i gang med at overvåge Microsoft 365 dags dato. Du kan finde en mere detaljeret vejledning i operationsvejledningen til administrationspakken. <br/> |
|**Overvågning af tilstand for Azure ExpressRoute** <br/> |Hvis du opretter forbindelse til Microsoft 365 ved hjælp af Azure ExpressRoute til Microsoft 365, skal du sikre dig, at du både bruger Microsoft 365 Service Health Dashboard samt Azure [Reducing troubleshooting time with Azure Resource health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Brug af Azure AD Forbind health med AD FS** <br/> |Hvis du bruger AD FS til single Sign-On med Microsoft 365, skal du begynde at bruge Azure AD Forbind Health til at overvåge din [AD FS-infrastruktur](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**Overvåge Microsoft 365 via et program** <br/> |Se vores vejledning til Microsoft 365 [Management API](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Relaterede emner

[Konfigurere Microsoft 365 Enterprise tjenester og programmer](configure-services-and-applications.md)
  
[Gør din organisation klar til Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)
  
[Microsoft 365 integration med lokale miljøer](microsoft-365-integration.md)
  
[Administrere Microsoft 365 slutpunkter](managing-office-365-endpoints.md)
