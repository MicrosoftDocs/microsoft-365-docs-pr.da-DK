---
title: Microsoft 365 identitet kun i skyen
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
description: Beskrivelse af, hvordan du opretter brugere og grupper, når Microsoft 365 bruger en identitet, der kun findes i skyen.
ms.openlocfilehash: 81c13a6b7e32883d4cb846ef5956102f08fecd6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63601574"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 identitet kun i skyen

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du har valgt en identitetsmodel, der kun findes i skyen, har du allerede en Azure Active Directory-lejer (Azure AD) til dit Microsoft 365-abonnement for at gemme alle dine brugere, grupper og kontakter. Når du har konfigureret beskyttelsen for administratorkonti i trin [2](protect-your-global-administrator-accounts.md) og brugerkonti i trin [3](microsoft-365-secure-sign-in.md) til denne løsning, er du nu klar til at begynde at oprette de nye konti og grupper, som organisationen har brug for.

Her er de grundlæggende komponenter i en identitet, der kun findes i skyen.
 
![De grundlæggende komponenter i en identitet, der kun findes i skyen.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Brugere og deres brugerkonti i organisationer kan kategoriseres på flere forskellige måder. Nogle er f.eks. medarbejdere og har en permanent status. Nogle er leverandører, underleverandører eller partnere, der har en midlertidig status. Nogle er eksterne brugere, der ikke har nogen brugerkonti, men som stadig skal have tildelt adgang til bestemte tjenester og ressourcer for at understøtte interaktion og samarbejde. Eksempel:

- Lejerkonti repræsenterer brugere i din organisation, som du giver licens til skytjenester

- B2B-konti (Business to Business) repræsenterer brugere uden for organisationen, som du inviterer til at deltage i samarbejde

Gør status over typerne af brugere i organisationen. Hvad er grupperne? Du kan f.eks. gruppere brugere efter funktioner på højt niveau eller formål for organisationen.

Desuden kan nogle skytjenester deles med brugere uden for organisationen uden brugerkonti. Du skal også identificere disse grupper af brugere.

Du kan bruge grupper i Azure AD til flere formål, der forenkler administrationen af dit skymiljø. Med Azure AD-grupper kan du f.eks.:

- Brug gruppebaseret licensering til automatisk at tildele Microsoft 365 til dine brugerkonti, så snart de er tilføjet som medlemmer.
- Føj brugerkonti til bestemte grupper dynamisk baseret på brugerkontoattributter, f.eks. afdelingsnavn.
- Klargør automatisk brugere til Software as a Service-programmer (SaaS) og for at beskytte adgangen til disse programmer med multifaktorgodkendelse (MFA) og andre politikker for betinget adgang.
- Klargør tilladelser og adgangsniveauer for teams og SharePoint Online-teamwebsteder.

## <a name="next-steps-for-cloud-only-identity"></a>Næste trin for kun skyidentitet

- [Administrere brugerkonti](manage-microsoft-365-accounts.md)
- [Tildel licenser til brugerkonti](assign-licenses-to-user-accounts.md)
- [Administrere grupper og gruppemedlemskab](manage-microsoft-365-groups.md)
- [Administrere adgangskoder til brugerkonti](manage-microsoft-365-passwords.md)
