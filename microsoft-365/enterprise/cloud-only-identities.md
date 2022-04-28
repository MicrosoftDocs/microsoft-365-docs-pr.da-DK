---
title: Microsoft 365 identitet, der kun er skyen
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
description: Beskriver, hvordan du opretter brugere og grupper, når dit Microsoft 365-abonnement bruger identitet, der kun er skybaseret.
ms.openlocfilehash: 7b2ad2cee32f075302ea591806214b697fa9b206
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091363"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 identitet, der kun er skyen

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du har valgt identitetsmodellen kun i cloudmiljøet, har du allerede en Azure AD-lejer (Azure Active Directory) til dit Microsoft 365 abonnement, hvor du kan gemme alle dine brugere, grupper og kontakter. Når du har konfigureret beskyttelse af administratorkonti i [trin 2](protect-your-global-administrator-accounts.md) og brugerkonti i [trin 3](microsoft-365-secure-sign-in.md) i denne løsning, er du nu klar til at begynde at oprette de nye konti og grupper, som din organisation har brug for.

Her er de grundlæggende komponenter i identitet, der kun findes i cloudmiljøet.
 
![De grundlæggende komponenter i identitet, der kun er i cloudmiljøet.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Brugere og deres brugerkonti i organisationer kan kategoriseres på flere måder. Nogle er f.eks. medarbejdere og har en permanent status. Nogle er leverandører, kontraktansatte eller partnere, der har midlertidig status. Nogle er eksterne brugere, der ikke har nogen brugerkonti, men som stadig skal have adgang til bestemte tjenester og ressourcer for at understøtte interaktion og samarbejde. Eksempel:

- Lejerkonti repræsenterer brugere i din organisation, som du licenserer til cloudtjenester

- B2B-konti (Business to Business) repræsenterer brugere uden for din organisation, som du inviterer til at deltage i samarbejde

Gør status over typerne af brugere i din organisation. Hvad er grupperinger? Du kan f.eks. gruppere brugere efter funktion på højt niveau eller formål med din organisation.

Derudover kan nogle cloudtjenester deles med brugere uden for din organisation uden nogen brugerkonti. Du skal også identificere disse brugergrupper.

Du kan bruge grupper i Azure AD til flere formål, der forenkler administrationen af dit cloudmiljø. Med Azure AD-grupper kan du f.eks.:

- Brug gruppebaserede licenser til automatisk at tildele licenser til Microsoft 365 til dine brugerkonti, så snart de tilføjes som medlemmer.
- Føj brugerkonti til bestemte grupper dynamisk baseret på brugerkontoattributter, f.eks. afdelingsnavn.
- Klargør automatisk brugere til SaaS-programmer (Software as a Service) og for at beskytte adgangen til disse programmer med multifaktorgodkendelse (MFA) og andre politikker for betinget adgang.
- Klargør tilladelser og adgangsniveauer for teams og SharePoint onlineteamwebsteder.

## <a name="next-steps-for-cloud-only-identity"></a>Næste trin til identitet, der kun er i cloudmiljøet

- [Administrer brugerkonti](manage-microsoft-365-accounts.md)
- [Tildel licenser til brugerkonti](assign-licenses-to-user-accounts.md)
- [Administrer grupper og gruppemedlemskab](manage-microsoft-365-groups.md)
- [Administrer adgangskoder for brugerkonto](manage-microsoft-365-passwords.md)
