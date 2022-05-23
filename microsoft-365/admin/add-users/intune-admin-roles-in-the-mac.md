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
description: Med Microsoft 365 Administration kan du administrere nogle Microsoft Intune roller, der knyttes til forretningsfunktioner og giver tilladelser til at udføre bestemte opgaver.
ms.openlocfilehash: 61c73ea49b132dee12839112bdc08624a750989f
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636256"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune administratorroller i Microsoft 365 Administration

Dit Microsoft 365- eller Office 365-abonnement leveres med et sæt administratorroller, som du kan tildele til brugere i din organisation ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. De enkelte administratorroller relaterer til almindelige forretningsfunktioner og giver personer tilladelse til at udføre bestemte opgaver i Administrationerne.

Med Microsoft 365 Administration kan du administrere nogle Microsoft Intune roller. Disse roller er dog en delmængde af de roller, der er tilgængelige i Intune Administration. Leder du efter de detaljerede rollebeskrivelser for Microsoft Intune? Se nærmere på [rollebaseret adgangskontrol med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Du kan få mere at vide om tildeling af roller i <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">Microsoft 365 Administration</a> under [Tildel administratorroller](assign-admin-roles.md).

I Microsoft 365 Administration kan du gå til **Roller** og derefter vælge en hvilken som helst rolle for at åbne detaljeruden. Vælg fanen **Tilladelser** for at få vist en detaljeret liste over, hvad administratorer, der er tildelt rollen, har tilladelser til at gøre. Vælg fanen **Tildelte** eller **Tildelte administratorer** for at føje brugere til roller.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune roller, der er tilgængelige i Microsoft 365 Administration

|Administratorrolle     |Hvem skal have tildelt denne rolle?  |
|---------|---------|
|Programstyring     |   Tildel rollen Programadministrator til brugere, der administrerer programlivscyklussen for mobilapps, konfigurerer politikadministrerede apps og får vist enhedsoplysninger og konfigurationsprofiler.  |
|Helpdesk-operatør     |   Tildel rollen helpdeskoperator til brugere, der tildeler apps og politikker til brugere og enheder. |
|Intune rolleadministrator    |   Tildel Intune rolleadministrator til brugere, der kan tildele Intune tilladelser til andre administratorer og kan administrere brugerdefinerede og indbyggede Intune roller.   |
|Politik- og profilstyring     |   Tildel rollen politik- og profiladministrator til brugere, der administrerer politik for overholdelse af angivne standarder, konfigurationsprofiler og Apple-tilmelding.   |
|Skrivebeskyttet operator     |   Tildel rollen skrivebeskyttet operator til brugere, der kun kan få vist brugere, enheder, tilmeldingsoplysninger og konfigurationer.   |
|Skoleadministrator     |   Tildel skoleadministratorrollen til brugere for at få fuld adgang til at administrere Windows 10- og iOS-enheder, apps og konfigurationer i Intune for Education.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Stedfortræderadministration til Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele vedkommende administratorroller. De kan til gengæld tildele brugere i din virksomhed - eller deres firma - administratorroller. Det kan f.eks. være, at de skal gøre det, hvis de konfigurerer og administrerer din onlineorganisation for dig.
  
En partner kan tildele disse roller: 
  
- Fuld administration, som har rettigheder, der svarer til en global administrator, bortset fra administration af multifaktorgodkendelse via Partnercenter.

- Begrænset administration, som har rettigheder, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du føje partneren til din konto, som delegeret administrator. Denne proces startes af en autoriseret partner. Partneren sender dig en mail for at spørge dig, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde en vejledning under [Godkend eller fjern partnerrelationer](../misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365 administratorroller](about-admin-roles.md) (artikel)\
[Tildel administratorroller](assign-admin-roles.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../activity-reports/activity-reports.md) (artikel)
