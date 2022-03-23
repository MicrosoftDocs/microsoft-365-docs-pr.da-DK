---
title: Tildele Microsoft 365 licenser til brugerkonti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Beskriver, hvordan du tildeler Microsoft 365 licenser til brugerkonti, enten enkeltvis eller baseret på gruppemedlemskab.
ms.openlocfilehash: dd941be0d257aa356cf6e69bfdd59a8d1743ed93
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589717"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Tildele Microsoft 365 licenser til brugerkonti

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

For den kun skybaserede identitetsmodel kan du tildele Microsoft 365-licenser til brugerkonti, efterhånden som de oprettes, afhængigt af hvordan du opretter dem.

For hybrididentitetsmodellen er det sådan, at når Active Directory-domæneservices (AD DS) brugerkonti synkroniseres for første gang, tildeles de ikke automatisk en placering eller en Microsoft 365 licens. **Du skal konfigurere hver brugerkonto med en brugerplacering før eller sammen med tildeling af en licens.**

I begge tilfælde skal du tildele en licens til brugerkonti, så brugerne kan få adgang til Microsoft 365, f.eks. mail og Microsoft Teams.

Du kan tildele licenser til brugerkonti enten enkeltvis eller automatisk via gruppemedlemskab.

Hvis du Microsoft 365 licenser til individuelle brugerkonti, kan du bruge:

- [Den Microsoft 365 Administration](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- Azure AD Administration

## <a name="group-based-licensing"></a>Gruppebaseret licensering

Du kan konfigurere sikkerhedsgrupper i Azure AD til automatisk at tildele licenser fra et sæt abonnementer til alle gruppens medlemmer. Dette kaldes *gruppebaseret licensering*. Hvis en brugerkonto tilføjes eller fjernes fra gruppen, tildeles eller ophæves licenserne for gruppens abonnementer automatisk fra brugerkontoen.

Sørg for, at du har nok licenser til alle gruppemedlemmerne. Hvis du løber tør for licenser, vil nye brugere ikke få tildelt licenser, før licenser bliver tilgængelige.

>[!Note]
>Du bør ikke konfigurere gruppebaseret licensering for grupper, der indeholder B2B-konti (Azure Business to Business).
>

Du kan finde flere oplysninger i [gruppebaserede licenser i Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Næste trin

Med det relevante sæt brugerkonti, der er blevet tildelt licenser, er du nu klar til at:

- [Implementer sikkerhed](../security/office-365-security/security-roadmap.md)
- [Installér klientsoftware, f.eks. Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [Konfigurer enhedshåndtering](device-management-roadmap-microsoft-365.md)
- [Konfigurere tjenester og programmer](configure-services-and-applications.md)