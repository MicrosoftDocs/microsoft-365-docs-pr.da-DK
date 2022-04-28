---
title: Vis status for katalogsynkronisering i Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: I denne artikel kan du få mere at vide om, hvordan du kontrollerer status for katalogsynkronisering i Office 365.
ms.openlocfilehash: 8f21985f8db3539e8dd1a839cc6cb499a425feeb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095548"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Vis status for katalogsynkronisering i Microsoft 365

Hvis du har integreret dit Active Directory i det lokale miljø Domænetjenester (AD DS) med Azure Active Directory (Azure AD) ved at synkronisere dit lokale miljø med Microsoft 365, kan du også kontrollere status for synkroniseringen.
  
## <a name="view-directory-synchronization-status"></a>Vis status for katalogsynkronisering

- Log på [Microsoft 365 Administration](https://admin.microsoft.com), og vælg **DirSync-status** på startsiden.
- Du kan også gå til **Brugere** \> **Aktive brugere**, og på siden **Aktive brugere** skal du vælge Synkronisering af **Flere** \> **mapper**. I ruden **Katalogsynkronisering** skal du vælge **Gå til DirSync-administration**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Oplysninger på siden Administrer katalogsynkronisering

I følgende tabel vises de funktioner, du kan få oplysninger om på siden.
  
Hvis der er problemer med katalogsynkroniseringen, vises fejlene også på denne side. Du kan finde flere oplysninger om forskellige fejl, du kan støde på, [under Identificer fejl i katalogsynkronisering i Microsoft 365](identify-directory-synchronization-errors.md).
  
|Element|Hvad det er til|
|:-----|:-----|
|**Domæner bekræftet** | Antallet af domæner i din Microsoft 365 lejer, som du har bekræftet, at du ejer. |
|**Domæner, der ikke er bekræftet** | Domæner, du har tilføjet, men ikke bekræftet. |
|**Katalogsynkronisering er aktiveret** |True eller False. Angiver, om du har aktiveret katalogsynkronisering. |
|**Seneste katalogsynkronisering** | Sidste gang katalogsynkronisering kørte. Viser en advarsel og et link til et fejlfindingsværktøj, hvis den seneste synkronisering var for mere end tre dage siden. |
|**Adgangskodesynkronisering er aktiveret** | True eller False. Angiver, om du har synkronisering af adgangskodehash mellem vores lokale miljø og din Microsoft 365 lejer. |
|**Seneste synkronisering af adgangskode** | Sidste gang synkronisering af adgangskodehash kørte. Viser en advarsel og et link til et fejlfindingsværktøj, hvis den seneste synkronisering var for mere end tre dage siden. |
|**Klientversion til katalogsynkronisering** | Indeholder et downloadlink, hvis der er udgivet en ny version af Azure AD Forbind. |
|**Konto til katalogsynkroniseringstjeneste** | Viser navnet på din Microsoft 365-katalogsynkroniseringstjenestekonto. |
|||

## <a name="monitor-synchronization-health"></a>Overvåg synkroniseringstilstand

I dette afsnit skal du installere en Azure AD Forbind Health agent på hver af dine AD DS-domænecontrollere i det lokale miljø for at overvåge din identitetsinfrastruktur og de synkroniseringstjenester, der leveres af Azure AD Forbind. Overvågningsoplysningerne er tilgængelige på en Azure AD Forbind Health-portal, hvor du kan få vist beskeder, overvågning af ydeevnen, forbrugsanalyse og andre oplysninger.

Den vigtigste designbeslutning for, hvordan du bruger Azure AD Forbind Health, er baseret på, hvordan du bruger Azure AD-Forbind:

- Hvis du bruger indstillingen **for administreret godkendelse**, skal du starte med [Brug af Azure AD Forbind Health med synkronisering](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) for at forstå og konfigurere Azure AD Forbind Health.
- Hvis du kun synkroniserer navnene på konti og grupper ved hjælp af **sammenkædet godkendelse** med Active Directory Federation Services (AD FS), skal du starte med [Brug af Azure AD Forbind Health med AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) for at forstå og konfigurere Azure AD Forbind Health.

Når du er færdig, har du:

- Azure AD Forbind Tilstandsagent, der er installeret på dine lokale identitetsudbyderservere.
- Azure AD Forbind Health Portal, der viser den aktuelle tilstand for infrastrukturen i det lokale miljø og synkroniseringsaktiviteter med Azure AD-lejeren for dit Microsoft 365 abonnement.