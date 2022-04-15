---
title: Om Intune administratorroller i Microsoft 365 Administration
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
description: Administratorroller knyttes til forretningsfunktioner og giver tilladelser til at udføre bestemte opgaver i Administration. Tjenesteadministratoren åbner f.eks. supportanmodninger med Microsoft.
ms.openlocfilehash: 6ee5c8410b64bffe66ee69e5c4468a9eda601cd8
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882192"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune administratorroller i Microsoft 365 Administration

Dit Microsoft 365- eller Office 365-abonnement leveres med et sæt administratorroller, som du kan tildele til brugere i din organisation ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Hver administratorrolle knyttes til almindelige forretningsfunktioner og giver personer i din organisation tilladelse til at udføre bestemte opgaver i administratorcentrene.

Med Microsoft 365 Administration kan du administrere nogle Microsoft Intune roller. Disse roller er dog en delmængde af de roller, der er tilgængelige i Intune Administration. Leder du efter de detaljerede rollebeskrivelser for Microsoft Intune? Se [rollebaseret adgangskontrol (RBAC) med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Du kan få flere oplysninger om tildeling af roller i <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">Microsoft 365 Administration</a> under [Tildel administratorroller](assign-admin-roles.md).

I Microsoft 365 Administration kan du gå til **Roller** og derefter vælge en hvilken som helst rolle for at åbne detaljeruden. Vælg fanen **Tilladelser** for at få vist en detaljeret liste over, hvad administratorer, der har tildelt rollen, har tilladelser til at gøre. Vælg fanen **Tildelte** eller **Tildelte administratorer** for at føje brugere til roller.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune roller, der er tilgængelige i Microsoft 365 Administration

|Administratorrolle     |Who skal tildeles denne rolle?  |
|---------|---------|
|Programstyring     |   Tildel rollen Programadministrator til brugere, der administrerer programlivscyklussen for mobilapps, konfigurerer politikadministrerede apps og får vist enhedsoplysninger og konfigurationsprofiler.  |
|Helpdesk-operatør     |   Tildel rollen helpdeskoperator til brugere, der tildeler apps og politikker til brugere og enheder. |
|Intune rolleadministrator    |   Tildel Intune rolleadministrator til brugere, der kan tildele Intune tilladelser til andre administratorer og kan administrere brugerdefinerede og indbyggede Intune roller.   |
|Politik- og profilstyring     |   Tildel rollen politik- og profiladministrator til brugere, der administrerer politik for overholdelse af angivne standarder, konfigurationsprofiler og Apple-tilmelding.   |
|Skrivebeskyttet operator     |   Tildel rollen skrivebeskyttet operator til brugere, der kun kan få vist brugere, enheder, tilmeldingsoplysninger og konfigurationer.   |
|Skoleadministrator     |   Tildel skoleadministratorrollen til brugere for at få fuld adgang til at administrere Windows 10- og iOS-enheder, apps og konfigurationer i Intune for Education.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Uddelegeret administration til Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele dem administratorroller. De kan til gengæld tildele brugere i din virksomhed - eller deres firma - administratorroller. Det kan f.eks. være, at de skal gøre dette, hvis de konfigurerer og administrerer din onlineorganisation for dig.
  
En partner kan tildele disse roller:
  
- Fuld administration, som har rettigheder, der svarer til en global administrator, med undtagelse af administration af multifaktorgodkendelse via Partnercenter.

- Begrænset administration, som har rettigheder, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du føje partneren som delegeret administrator til din konto. Denne proces startes af en autoriseret partner. Partneren sender dig en mail for at spørge dig, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde instruktioner under [Godkend eller fjern partnerrelationer](../misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365 administratorroller](about-admin-roles.md) (artikel)\
[Tildel administratorroller](assign-admin-roles.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../activity-reports/activity-reports.md) (artikel)
