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
ms.openlocfilehash: 03295989e1ee44ab43fe0cc53e4029a6c4307ea8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172642"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Tildel roller og tilladelser i Microsoft Defender til virksomheder

Hvis du vil udføre opgaver på Microsoft 365 Defender-portalen, f.eks. konfiguration af Microsoft Defender til virksomheder, visning af rapporter eller svarhandlinger på registrerede trusler, skal sikkerhedsteamet tildeles de relevante tilladelser. Tilladelser tildeles via roller, der er tildelt på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) eller i [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Sådan gør du

1. [Få mere at vide om roller i Defender for Business](#roles-in-defender-for-business).
2. [Få vist eller rediger rolletildelinger for dit sikkerhedsteam](#view-or-edit-role-assignments).
3. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="roles-in-defender-for-business"></a>Roller i Defender for Business

I følgende tabel beskrives de tre roller, der kan tildeles i Defender for Business. [Få mere at vide om administratorroller](../../admin/add-users/about-admin-roles.md).

| Tilladelsesniveau | Beskrivelse |
|:---|:---|
| **Globale administratorer** (også kaldet globale administratorer) <br/><br/> *Som bedste praksis skal du begrænse antallet af globale administratorer.* | Globale administratorer kan udføre alle slags opgaver. Den person, der har tilmeldt dit firma til Microsoft 365 eller Microsoft Defender til virksomheder, er som standard global administrator. <br/><br/> Globale administratorer kan få adgang til/ændre indstillinger på tværs af alle Microsoft 365 portaler, f.eks.: <br/>- Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Sikkerhedsadministratorer** (også kaldet sikkerhedsadministratorer) | Sikkerhedsadministratorer kan udføre følgende opgaver: <br/>- Få vist og administrer sikkerhedspolitikker <br/>– Få vist og administrer sikkerhedstrusler og -beskeder (disse aktiviteter omfatter at tage svarhandlinger på slutpunkter) <br/>- Få vist sikkerhedsoplysninger og -rapporter |
| **Sikkerhedslæser** | Sikkerhedslæsere kan udføre følgende opgaver: <br/>- Få vist sikkerhedspolitikker <br/>– Få vist sikkerhedstrusler og -beskeder <br/>- Få vist sikkerhedsoplysninger og -rapporter  |


## <a name="view-or-edit-role-assignments"></a>Få vist eller rediger rolletildelinger

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Tilladelser & roller** i navigationsruden, og vælg derefter **Roller** under **Azure AD**.

3. Vælg en af følgende roller for at åbne sideruden:

   - Global administrator
   - Sikkerhedsadministrator
   - Sikkerhedslæser

   > [!IMPORTANT]
   > Microsoft anbefaler, at personer kun får adgang til det, de har brug for til at udføre deres opgaver. Vi kalder dette begreb *færrest rettigheder* for tilladelser. Du kan få mere at vide under [Bedste praksis for mindst privilegeret adgang til programmer](/azure/active-directory/develop/secure-least-privileged-access). 

4. I sideruden skal du vælge linket **Administrer medlemmer i Azure AD**. Denne handling fører dig til Azure Active Directory (Azure AD), hvor du kan få vist og administrere dine rolletildelinger.

5. Vælg en bruger for at åbne vedkommendes profil, og vælg derefter **Tildelte roller**.

   - Hvis du vil tilføje en rolle, skal du vælge **+ Tilføj tildelinger**.
   - Hvis du vil fjerne en rolle, skal du vælge **X Fjern tildelinger**. 

## <a name="need-to-add-users"></a>Har du brug for at tilføje brugere?

Hvis du ikke allerede har føjet brugere til dit abonnement, skal du se [Tilføj brugere og tildel licenser på samme tid](mdb-add-users.md).

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 3: Konfigurer mailmeddelelser](mdb-email-notifications.md)
- [Trin 4: Onboard enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md)