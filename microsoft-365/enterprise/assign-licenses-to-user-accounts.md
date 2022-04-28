---
title: Tildel Microsoft 365 licenser til brugerkonti
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Beskriver, hvordan du tildeler Microsoft 365 licenser til brugerkonti enten individuelt eller baseret på gruppemedlemskab.
ms.openlocfilehash: ab9769aa4dee6a9f7982f72f377b0c7e0d3f444e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091407"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Tildel Microsoft 365 licenser til brugerkonti

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

I forbindelse med identitetsmodellen kun i cloudmiljøet kan du tildele Microsoft 365 licenser til brugerkonti, efterhånden som de oprettes, afhængigt af hvordan du opretter dem.

Når ad DS-brugerkonti (Active Directory-domæneservices) synkroniseres første gang for hybrididentitetsmodellen, tildeles de ikke automatisk en placering eller en Microsoft 365 licens. **Du skal konfigurere hver brugerkonto med en brugerplacering, før eller sammen med tildeling af en licens.**

I begge tilfælde skal du tildele en licens til brugerkonti, så brugerne kan få adgang til Microsoft 365 tjenester, f.eks. mail og Microsoft Teams.

Du kan tildele licenser til brugerkonti enten individuelt eller automatisk via gruppemedlemskab.

Hvis du vil tildele Microsoft 365 licenser til individuelle brugerkonti, kan du bruge:

- [Microsoft 365 Administration](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Azure AD Administration

## <a name="group-based-licensing"></a>Gruppebaserede licenser

Du kan konfigurere sikkerhedsgrupper i Azure AD for automatisk at tildele licenser fra et sæt abonnementer til alle medlemmer af gruppen. Dette kaldes *gruppebaserede licenser*. Hvis en brugerkonto føjes til eller fjernes fra gruppen, tildeles eller ikke-tildeles licenserne til gruppens abonnementer automatisk fra brugerkontoen.

Sørg for, at du har tilstrækkelige licenser til alle gruppemedlemmerne. Hvis du løber tør for licenser, tildeles nye brugere ikke licenser, før licenser bliver tilgængelige.

>[!Note]
>Du bør ikke konfigurere gruppebaserede licenser for grupper, der indeholder B2B-konti (Azure Business to Business).
>

Du kan finde flere oplysninger under [gruppebaserede licenser i Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Næste trin

Med det relevante sæt brugerkonti, der er tildelt licenser, er du nu klar til at:

- [Implementer sikkerhed](../security/office-365-security/security-roadmap.md)
- [Udrul klientsoftware, f.eks. Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Konfigurer enhedshåndtering](device-management-roadmap-microsoft-365.md)
- [Konfigurer tjenester og programmer](configure-services-and-applications.md)