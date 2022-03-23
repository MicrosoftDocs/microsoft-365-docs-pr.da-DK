---
title: Tilladelser i Microsoft 365 Overholdelsescenter og sikkerhedscenter
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Ved hjælp Microsoft 365 eller sikkerhedscenteret Microsoft 365 Overholdelsescenter du administrere tilladelser centralt for alle opgaver relateret til sikkerhed eller overholdelse.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc2808ffe5d0acd3a5c3c3a6252503ee5e2cf94e
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2021
ms.locfileid: "63588735"
---
# <a name="permissions-in-the-microsoft-365-compliance-center-and-microsoft-365-security-center"></a>Tilladelser i Microsoft 365 Overholdelsescenter og Microsoft 365 sikkerhedscenter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Din organisation har brug for at administrere scenarier for overholdelse og sikkerhed, der omfatter alle Microsoft 365 tjenester. Og du har brug for fleksibilitet til at give de rette administratortilladelser til de rette personer i din organisations it-gruppe. Ved hjælp Microsoft 365 eller sikkerhedscenteret Microsoft 365 Overholdelsescenter du administrere tilladelser centralt for alle opgaver relateret til sikkerhed eller overholdelse.

Når en global administrator føjer brugere til disse administratorroller, har denne administrator adgang til funktioner og data, der omfatter alle tjenester i Microsoft 365, f.eks. Microsoft 365 Security Center, Microsoft 365 Overholdelsescenter, Azure, Office 365 og Enterprise Mobility + Security.

## <a name="what-the-microsoft-365-roles-are"></a>Hvad de Microsoft 365 er

De roller, der vises i Microsoft 365 Overholdelsescenter og Microsoft 365, er Azure Active Directory roller. Disse roller er designet til at justere efter jobfunktioner i organisationens it-gruppe, hvilket gør det nemt at give en person alle de nødvendige tilladelser for at få arbejdet gjort.

****

|Rolle|Beskrivelse|
|---|---|
|**Global administrator**|Adgang til alle administrative funktioner i Microsoft 365 tjenester. Kun globale administratorer kan tildele andre administratorroller. Du kan finde flere oplysninger [under Global administrator/virksomhedsadministrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Dataadministrator for overholdelse af regler og standarder**|Hold styr på din organisations data på tværs af Microsoft 365, sørg for, at de er beskyttet, og få indsigt i eventuelle problemer for at reducere risici. Du kan få mere at vide under [Dataadministrator for overholdelse af regler og standarder](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Overholdelsesadministrator**|Hjælp din organisation med at overholde eventuelle lovmæssige krav, administrer eDiscovery-sager og vedligehold politikker for datastyring på tværs Microsoft 365 placeringer, identiteter og apps. Du kan få mere at vide under [Overholdelsesadministrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Sikkerhedsoperatør**|Få vist, undersøg og svar på aktive trusler mod Microsoft 365 brugere, enheder og indhold. Du kan finde flere oplysninger under [Sikkerhedsoperator](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Sikkerhedslæser**|Få vist og undersøg aktive trusler mod dine Microsoft 365-brugere, enheder og indhold, men (i modsætning til sikkerhedsoperatøren) har de ikke tilladelse til at reagere ved at gøre noget. Du kan finde flere oplysninger under [Sikkerhedslæser](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Sikkerhedsadministrator**|Styr din organisations overordnede sikkerhed ved at administrere sikkerhedspolitikker, gennemse sikkerhedsanalyser og rapporter på tværs af Microsoft 365-produkter og holde dig i gang med at arbejde i trusselsbilledet. Du kan finde flere oplysninger under [Sikkerhedsadministrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Global læser**|Den skrivebeskyttede version af **rollen Global** administrator. Få vist alle indstillinger og administrative oplysninger på tværs Microsoft 365. Du kan finde flere oplysninger [under Global læser](/azure/active-directory/roles/permissions-reference#global-reader).|
|

## <a name="global-administrators-can-manage-roles-in-azure-active-directory"></a>Globale administratorer kan administrere roller i Azure Active Directory

Når du Microsoft 365 Overholdelsescenter en Microsoft 365, kan du i sikkerhedscenteret se dens tildelinger. Men hvis du vil administrere disse opgaver, skal du gå til Azure Active Directory.

Få mere at vide under [Få vist og tildel administratorroller Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

![Link til at administrere tilladelser i Azure Active Directory](../../media/permissions-manage-in-azure-ad-link.png)

## <a name="managing-roles-in-a-service-instead-of-azure-active-directory"></a>Administrere roller i en tjeneste i stedet for Azure Active Directory

De roller, der vises i Microsoft 365 Overholdelsescenter og Microsoft 365, vises også i de tjenester, hvor de har tilladelser. Du kan f.eks. se disse roller i sikkerheds- & Compliance Center.

![Roller i Security & Compliance Center](../../media/m365-roles-in-o365-scc.png)

Du kan finde oplysninger om, hvordan disse roller bruges i Security & Compliance Center under Tilladelser i [Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).

### <a name="breaking-inheritance"></a>Bryde nedarvning

Det er vigtigt at forstå, at når du administrerer disse roller i Azure Active Directory, gør du det **centralt for alle** Microsoft 365 tjenester. Men når du administrerer en rolle i en bestemt tjeneste, f.eks Security & Compliance Center, administrerer du kun **rollen for den** bestemte tjeneste. Tildelinger og tilladelser for en rolle i en tjeneste tilsidesætter alle tilladelser, der er tildelt rollen Azure Active Directory rolle.

Dette kan være nyttigt. Hvis en person f.eks. er tildelt rollen som sikkerhedsadministrator, har vedkommende ikke tilladelse til at administrere hændelser. Men du kan bruge tilladelserne i Microsoft Defender for Endpoint til at give dem den specifikke tilladelse til hændelsesstyring i den pågældende tjeneste.

## <a name="where-to-find-role-information-for-each-microsoft-365-service"></a>Her finder du rolleoplysninger for hver Microsoft 365 tjeneste

Ved at tildele en bruger til en af Microsoft 365 overholdelses- eller sikkerhedsadministratorroller giver du den pågældende bruger rettigheder til en række Microsoft 365-tjenester. Brug nedenstående links til at finde flere oplysninger om de specifikke tilladelser for en rolle i hver tjeneste.

****

|Microsoft 365 tjeneste|Rolleoplysninger|
|---|---|
|Administratorroller i Office 365 og Microsoft 365 til virksomheder|[Microsoft 365 administratorroller](../../admin/add-users/about-admin-roles.md)|
|Azure Active Directory (Azure AD) og Azure AD Identity Protection|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Defender for Identity|[Microsoft Defender for Identity-rollegrupper](/azure-advanced-threat-protection/atp-role-groups)|
|Azure Information Protection|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Overholdelsesstyring|[Overholdelsesstyring](../../compliance/compliance-manager-setup.md#set-user-permissions-and-assign-roles)|
|Exchange Online|[Exchange rollebaseret adgangskontrol](/exchange/permissions-exo/permissions-exo)|
|Intune|[Rollebaseret adgangskontrol for Intune](/intune/role-based-access-control)|
|Administreret skrivebord|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Cloud App Security|[Rollebaseret adgangskontrol](/cloud-app-security/manage-admins)|
|Security & Compliance Center|[Microsoft 365 administratorroller](permissions-in-the-security-and-compliance-center.md)|
|Privileged Identity Management|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Secure Score|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|SharePoint Online|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) <p> [Om SharePoint administratorrolle i Office 365](/sharepoint/sharepoint-admin-role)|
|Teams/Skype for Business|[Administratorroller i Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Defender til Slutpunkt|[Rollebaseret adgangskontrol for Microsoft Defender for Slutpunkt](/windows/security/threat-protection/windows-defender-atp/rbac-windows-defender-advanced-threat-protection)|
|

## <a name="coming-soon"></a>Kommer snart

Vi arbejder stadig på tilladelser i Microsoft 365 Overholdelsescenter og Microsoft 365 Sikkerhedscenter. Vi arbejder f.eks. på at understøtte muligheden for at:

- Administrer roller i Microsoft 365 Overholdelsescenter og Microsoft 365 i stedet for at gå til Azure Active Directory.
- Tilpas roller ved at tilføje eller fjerne bestemte tilladelser.
- Opret brugerdefinerede roller med tilladelser, som du vælger.