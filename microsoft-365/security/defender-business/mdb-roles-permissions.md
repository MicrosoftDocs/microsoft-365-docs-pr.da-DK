---
title: Tildel roller og tilladelser i Microsoft Defender til virksomheder
description: Tildel roller til dit cybersikkerhedsteam. Få mere at vide om disse roller og tilladelser i Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: 0f0065a65595279ab67141f8d4ddf31fc045e305
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66970116"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Tildel roller og tilladelser i Microsoft Defender til virksomheder

Hvis du vil udføre opgaver på Microsoft 365 Defender-portalen, f.eks. konfiguration af Defender for Business, visning af rapporter eller svarhandlinger på registrerede trusler, skal sikkerhedsteamet tildeles de relevante tilladelser. Tilladelser tildeles via roller, der er tildelt i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) eller i [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Sådan gør du

1. [Få mere at vide om roller i Defender for Business](#roles-in-defender-for-business).
2. [Få vist eller rediger rolletildelinger for dit sikkerhedsteam](#view-or-edit-role-assignments).
3. [Fortsæt til de næste trin](#next-steps).


## <a name="roles-in-defender-for-business"></a>Roller i Defender for Business

I følgende tabel beskrives de tre roller, der kan tildeles i Defender for Business. [Få mere at vide om administratorroller](../../admin/add-users/about-admin-roles.md).

| Tilladelsesniveau | Beskrivelse |
|:---|:---|
| **Globale administratorer** (også kaldet globale administratorer) <p> *Som bedste praksis skal du begrænse antallet af globale administratorer.* | Globale administratorer kan udføre alle slags opgaver. Den person, der har tilmeldt sig din virksomhed til Microsoft 365 eller Defender for Business, er som standard global administrator. <p> Globale administratorer kan ændre indstillinger på tværs af alle Microsoft 365-portaler, f.eks.: <ul><li>Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))</li><li>Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com))</li></ul> |
| **Sikkerhedsadministratorer** (også kaldet sikkerhedsadministratorer) | Sikkerhedsadministratorer kan udføre følgende opgaver: <ul><li>Få vist og administrer sikkerhedspolitikker</li><li>Få vist og administrer sikkerhedstrusler og -beskeder (disse aktiviteter omfatter svarhandlinger på slutpunkter)</li><li>Få vist sikkerhedsoplysninger og -rapporter</li></ul> |
| **Sikkerhedslæser** | Sikkerhedslæsere kan udføre følgende opgaver:<ul><li>Vis sikkerhedspolitikker</li><li>Vis sikkerhedstrusler og -beskeder</li><li>Få vist sikkerhedsoplysninger og -rapporter</li></ul>  |


## <a name="view-or-edit-role-assignments"></a>Få vist eller rediger rolletildelinger

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Tilladelser & roller** i navigationsruden, og vælg derefter **Roller** under **Azure AD**.

3. Vælg en af følgende roller for at åbne sideruden:

   - Global administrator
   - Sikkerhedsadministrator
   - Sikkerhedslæser

   > [!IMPORTANT]
   > Microsoft anbefaler, at du kun giver personer adgang til det, de har brug for til at udføre deres opgaver. Vi kalder dette begreb *færrest rettigheder* for tilladelser. Du kan få mere at vide under [Bedste praksis for mindst privilegeret adgang til programmer](/azure/active-directory/develop/secure-least-privileged-access). 

4. I sideruden skal du vælge linket **Administrer medlemmer i Azure AD**. Denne handling fører dig til Azure Active Directory (Azure AD), hvor du kan få vist og administrere dine rolletildelinger.

5. Vælg en bruger for at åbne vedkommendes profil, og vælg derefter **Tildelte roller**.

   - Hvis du vil tilføje en rolle, skal du vælge **+ Tilføj tildelinger**.
   - Hvis du vil fjerne en rolle, skal du vælge **X Fjern tildelinger**. 

## <a name="need-to-add-users"></a>Har du brug for at tilføje brugere?

Hvis du ikke allerede har føjet brugere til dit abonnement, skal du se [Tilføj brugere og tildel licenser på samme tid](mdb-add-users.md).

## <a name="next-steps"></a>Næste trin

Gå til:

- [Trin 3: Konfigurer mailmeddelelser](mdb-email-notifications.md)
- [Trin 4: Onboarder enheder til Defender for Business](mdb-onboard-devices.md)