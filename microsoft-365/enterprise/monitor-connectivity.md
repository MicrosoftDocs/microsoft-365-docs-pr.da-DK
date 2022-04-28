---
title: Overvåg Microsoft 365-forbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel får du mere at vide om de værktøjer og teknikker, du kan bruge til at overvåge og vedligeholde Microsoft 365 forbindelse.
ms.openlocfilehash: 0e7c18a10dc851596af6a652fb80c9c72852ee0d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093301"
---
# <a name="monitor-microsoft-365-connectivity"></a>Overvåg Microsoft 365-forbindelse

Når du har udrullet Microsoft 365, kan du bevare Microsoft 365 forbindelse ved hjælp af nogle af værktøjerne og teknikkerne nedenfor. Du skal forstå de officielle retningslinjer for [tjenestetilstand og kontinuitet](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) samt vores [bedste praksis for brug af Microsoft 365 på et langsomt netværk](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Du skal også hente [appen Microsoft 365 administrator](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) og angive et bogmærke [for vores Microsoft 365 til virksomheder – hjælp til administratorer](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Overvågning Microsoft 365 forbindelse

|Overvågningstype |Beskrivelse |
|:-----|:-----|
|**Få besked om nye Microsoft 365 slutpunkter** <br/> |Hvis du [administrerer Microsoft 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), skal du modtage meddelelser, når vi publicerer nye slutpunkter, du kan abonnere på vores RSS-feed ved hjælp af din foretrukne RSS-læser. Her er, hvordan [du abonnerer via Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) eller du kan [få RSS-feed opdateringer sendt til dig](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Brug System Center til at overvåge Microsoft 365** <br/> |Hvis du bruger Microsoft System Center, kan du downloade [Microsoft System Center Operations Manager Management Pack til Microsoft 365 for](https://www.microsoft.com/download/details.aspx?id=103379) at begynde at overvåge Microsoft 365 i dag. Du kan finde mere detaljeret vejledning i administrationspakkens driftsvejledning. <br/> |
|**Overvågning af tilstanden af Azure ExpressRoute** <br/> |Hvis du opretter forbindelse til Microsoft 365 ved hjælp af Azure ExpressRoute til Microsoft 365, skal du sikre dig, at du både bruger dashboardet for Microsoft 365 servicetilstand samt [fejlfindingstiden i Azure Reducer med Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Brug af Azure AD Forbind Health med AD FS** <br/> |Hvis du bruger AD FS til Enkelt Sign-On med Microsoft 365, skal du begynde at [bruge Azure AD Forbind Health til at overvåge din AD FS-infrastruktur](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**Overvåg Microsoft 365 ved hjælp af programmering** <br/> |Se vores vejledning om [API'en til Microsoft 365 administration](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Relaterede emner

[Konfigurer Microsoft 365 Enterprise tjenester og programmer](configure-services-and-applications.md)
  
[Gør din organisation klar til Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Netværksplanlægning og justering af ydeevnen for Microsoft 365](network-planning-and-performance.md)
  
[Microsoft 365 integration med lokale miljøer](microsoft-365-integration.md)
  
[Administration af Microsoft 365 slutpunkter](managing-office-365-endpoints.md)
