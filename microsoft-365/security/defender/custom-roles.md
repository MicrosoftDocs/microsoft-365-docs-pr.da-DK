---
title: Brugerdefinerede roller til rollebaseret adgangskontrol
description: Få mere at vide om, hvordan du administrerer brugerdefinerede roller på Microsoft 365 Defender-portalen
keywords: access, permissions, Microsoft 365 Defender, M365, security, MCAS, Cloud App Security, Microsoft Defender for Endpoint, scope, scoping, RBAC, roles-based access, custom roles-based access, roles-based auth, RBAC in MDO, roles, rolegroups, permissions nedarvning, detaljerede tilladelser
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 94330e319eeb44618c1e11b27da7b3d63c08d203
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731345"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Brugerdefinerede roller i rollebaseret adgangskontrol for Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Gælder for:**

- Microsoft 365 Defender
 
Der er to typer roller, der kan bruges til at få adgang til Microsoft 365 Defender:
- **Globale ad-Azure Active Directory-roller (Global Azure Active Directory)**
- **Brugerdefinerede roller**

Adgang til Microsoft 365 Defender kan administreres samlet ved hjælp af [globale roller i Azure Active Directory (AAD)](m365d-permissions.md)

Hvis du har brug for større fleksibilitet og kontrol over adgangen til specifikke produktdata, kan Microsoft 365 Defender adgang også administreres ved at oprette brugerdefinerede roller via hver enkelt respektive sikkerhedsportal.  

En brugerdefineret rolle, der oprettes via Microsoft Defender for Endpoint, giver f.eks. adgang til de relevante produktdata, herunder slutpunktsdata i Microsoft 365 Defender portalen. På samme måde vil en brugerdefineret rolle, der oprettes via Microsoft Defender for Office 365, give adgang til de relevante produktdata, herunder mail & samarbejdsdata på Microsoft 365 Defender-portalen.

Brugere med eksisterende brugerdefinerede roller kan få adgang til data på Microsoft 365 Defender-portalen i henhold til deres eksisterende arbejdsbelastningstilladelser, uden at der kræves yderligere konfiguration.

## <a name="create-and-manage-custom-roles"></a>Opret og administrer brugerdefinerede roller
Brugerdefinerede roller og tilladelser kan oprettes og administreres individuelt via hver af følgende sikkerhedsportaler: 

- Microsoft Defender for Endpoint – [rediger roller i Microsoft Defender for Endpoint](../defender-endpoint/user-roles.md)
- Microsoft Defender for Office 365 – [tilladelser i Security & Compliance Center](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps – [administrer administratoradgang](/cloud-app-security/manage-admins)

Hver brugerdefineret rolle, der oprettes via en individuel portal, giver adgang til dataene i den relevante produktportal. En brugerdefineret rolle, der er oprettet via Microsoft Defender for Endpoint, tillader f.eks. kun adgang til Defender for Endpoint-data.

> [!TIP]
> Du kan også få adgang til tilladelser og roller via Microsoft 365 Defender portalen ved at vælge Tilladelser & roller i navigationsruden. Adgang til Microsoft Defender for Cloud Apps administreres via Defender for Cloud Apps-portalen og styrer også adgang til Microsoft Defender for Identity.  Se [Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)

> [!NOTE]
> Brugerdefinerede roller, der er oprettet i Microsoft Defender for Cloud Apps har også adgang til Microsoft Defender for Identity data. Brugere med rollerne Brugergruppeadministrator eller App/instance-administrator Microsoft Defender for Cloud Apps kan ikke få adgang til Microsoft Defender for Cloud Apps data via Microsoft 365 Defender portalen.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Administrer tilladelser og roller på Microsoft 365 Defender-portalen
Tilladelser og roller kan også administreres på Microsoft 365 Defender-portalen:

1. Log på Microsoft 365 Defender-portalen på security.microsoft.com.
2. Vælg **Tilladelser & roller** i navigationsruden.
3. Under overskriften **Tilladelser** skal du vælge **Roller**.

> [!NOTE]
> Dette gælder kun for Defender for Office 365 og Defender for Endpoint. Andre arbejdsbelastninger skal have adgang til deres relevante portaler.


## <a name="required-roles-and-permissions"></a>Påkrævede roller og tilladelser
I følgende tabel beskrives de roller og tilladelser, der kræves for at få adgang til hver samlet oplevelse i hver arbejdsbelastning. Roller, der er defineret i nedenstående tabel, refererer til brugerdefinerede roller på individuelle portaler og er ikke forbundet til globale roller i Azure AD, selvom de har samme navn.

> [!NOTE]
> Administration af hændelser kræver administrationsrettigheder til alle produkter, der er en del af hændelsen.
 
| **En af følgende roller er påkrævet for Microsoft 365 Defender**  | **En af følgende roller er påkrævet for Defender for Endpoint**  | **En af følgende roller er påkrævet for Defender for Office 365** | **En af følgende roller er påkrævet for Defender for Cloud Apps** | 
|---------|---------|---------|---------|
| Viser undersøgelsesdata: <ul><li>Beskedside</li> <li>Beskedkøer</li> <li>Hændelser</li>  <li>Hændelseskø</li> <li>Handlingscenter</li></ul>| Få vist data – sikkerhedshandlinger | <ul><li>Administrer beskeder kun for visning </li> <li>Organisationskonfiguration</li><li>Overvågningslogge</li> <li>Overvågningslogge kun for visning</li> <li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li><li>Kun visningsmodtagere</li></ul>  | <ul><li>Global administrator</li> <li>Sikkerhedsadministrator</li> <li>Overholdelsesadministrator</li> <li>Sikkerhedsoperator</li> <li>Sikkerhedslæser</li> <li>Global læser</li></ul> |
| Visning af jagtdata | Få vist data – sikkerhedshandlinger | <ul><li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li> <li>Kun visningsmodtagere</li> | <ul><li>Global administrator</li> <li>Sikkerhedsadministrator</li> <li>Overholdelsesadministrator</li> <li>Sikkerhedsoperator</li> <li>Sikkerhedslæser</li> <li>Global læser</li></ul> |
| Administration af beskeder og hændelser | Undersøgelse af beskeder | <ul><li>Administrer beskeder</li> <li>Sikkerhedsadministrator</li> | <ul><li>Global administrator</li> <li>Sikkerhedsadministrator</li> <li>Overholdelsesadministrator</li> <li>Sikkerhedsoperator</li> <li>Sikkerhedslæser</li></ul> |
| Afhjælpning af handlingscenter | Aktive afhjælpningshandlinger – sikkerhedshandlinger | Søg og fjern | |
| Angivelse af brugerdefinerede registreringer | Administrer sikkerhedsindstillinger |<ul><li>Administrer beskeder</li> <li>Sikkerhedsadministrator</li></ul> | <ul><li>Global administrator</li> <li>Sikkerhedsadministrator</li> <li>Overholdelsesadministrator</li> <li>Sikkerhedsoperator</li> <li>Sikkerhedslæser</li> <li>Global læser</li></ul> |
| Threat Analytics | Beskeder og hændelsesdata: <ul><li>Få vist data – sikkerhedshandlinger</li></ul>TVM-afhjælpninger:<ul><li>Få vist data – trussel og håndtering af sikkerhedsrisici</li></ul> | Beskeder og hændelsesdata:<ul> <li>Administrer beskeder kun for visning</li> <li>Administrer beskeder</li> <li>Organisationskonfiguration</li><li>Overvågningslogge</li> <li>Overvågningslogge kun for visning</li><li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li><li>Kun visningsmodtagere</li> </ul> Forhindrede mailforsøg: <ul><li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li><li>Kun visningsmodtagere</li> | Ikke tilgængelig for Defender for Cloud Apps- eller MDI-brugere |

Hvis du f.eks. vil have vist jagtdata fra Microsoft Defender for Endpoint, skal du have tilladelse til at vise datasikkerhedshandlinger.  

På samme måde kræver brugerne en af følgende roller for at få vist jagtdata fra Microsoft Defender for Office 365:  

- Få vist datasikkerhedshandlinger
- Sikkerhedslæser
- Sikkerhedsadministrator
- Kun visningsmodtagere

## <a name="related-topics"></a>Relaterede emner
- [RBAC-roller](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Administrer adgang til Microsoft 365 Defender](m365d-permissions.md)
- [Administrer administratoradgang til Defender for Cloud Apps](/cloud-app-security/manage-admins)
