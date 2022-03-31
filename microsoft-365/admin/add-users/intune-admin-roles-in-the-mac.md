---
title: Om Intune-administratorroller i Microsoft 365 Administration
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
description: Administratorroller knyttes til forretningsfunktioner og giver tilladelse til at udføre bestemte opgaver i Administration. Tjenesteadministratoren åbner f.eks. supportbilletter hos Microsoft.
ms.openlocfilehash: 650a46c20acaf207f757ebbbe8f8b7179c29158f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63599870"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune-administratorroller i Microsoft 365 Administration

Dit Microsoft 365-Office 365-abonnement leveres med et sæt administratorroller, som du kan tildele til brugere i organisationen ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Hver administratorrolle tilknyttes almindelige forretningsfunktioner og giver personer i organisationen tilladelse til at udføre bestemte opgaver i Administration.

I Microsoft 365 Administration kan du administrere nogle Microsoft Intune roller. Disse roller er dog et undersæt af de roller, der er tilgængelige i Intune Administration. Leder du efter de detaljerede rollebeskrivelser for Microsoft Intune? Se [Rollebaseret adgangskontrol (RBAC) med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Du kan finde flere oplysninger om at tildele roller <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">i Microsoft 365 Administration</a> i [Tildel administratorroller](assign-admin-roles.md).

I Microsoft 365 Administration du gå til Roller og **derefter vælge en** hvilken som helst rolle for at åbne detaljeruden. Vælg fanen **Tilladelser for** at få vist den detaljerede liste over, hvad administratorer, der er tildelt den pågældende rolle, har tilladelse til at gøre. Vælg fanen **Tildelte** eller **Tildelte administratorer for** at føje brugere til roller.

## <a name="microsoft-intune-roles-available-in-the-microsoft-365-admin-center"></a>Microsoft Intune tilgængelige roller i Microsoft 365 Administration

|Administratorrolle     |Who have tildelt denne rolle?  |
|---------|---------|
|Programadministrator     |   Tildel rollen Programadministrator til brugere, der administrerer programlivscyklussen for mobilapps, konfigurerer politik-administrerede apps og får visning af enhedsoplysninger og konfigurationsprofiler.  |
|Helpdesk-operatør     |   Tildel rollen helpdesk-operatør til brugere, der tildeler apps og politikker til brugere og enheder. |
|Intune-rolleadministrator    |   Tildel Intune-rolleadministratoren til brugere, der kan tildele Intune-tilladelser til andre administratorer og kan administrere brugerdefinerede og indbyggede Intune-roller.   |
|Politik og profilstyring     |   Tildel politikken og profilstyringsrollen til brugere, som skal administrere overholdelsespolitik, konfigurationsprofiler og Apple-registrering.   |
|Skrivebeskyttet operator     |   Tildel den skrivebeskyttede operatorrolle til brugere, der kun kan se brugere, enheder, oplysninger om registrering og konfigurationer.   |
|Skoleadministrator     |   Tildel skoleadministratorrollen til brugerne for at få fuld adgang til at administrere Windows 10- og iOS-enheder, apps og konfigurationer i Intune for Education.   |

## <a name="delegated-administration-for-microsoft-partners"></a>Delegeret administration for Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele vedkommende administratorroller. De kan så tildele brugere i virksomheden – eller deres firma – administratorroller. Du kan f.eks. have dem til at gøre dette, hvis de konfigurerer og administrerer din onlineorganisation for dig.
  
En partner kan tildele disse roller:
  
- Fuld administration, som har rettigheder, der svarer til en global administrator, med undtagelse af administration af multifaktorgodkendelse via Partnercenter.

- Begrænset administration, som har rettigheder, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du tilføje partneren som delegeret administrator til din konto. Denne proces igangsættes af en autoriseret partner. Partneren sender dig en mail for at spørge, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde en vejledning [under Godkend eller fjern partnerrelationer](../misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365 administratorroller](about-admin-roles.md) (artikel)\
[Tildel administratorroller](assign-admin-roles.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../activity-reports/activity-reports.md) (artikel)