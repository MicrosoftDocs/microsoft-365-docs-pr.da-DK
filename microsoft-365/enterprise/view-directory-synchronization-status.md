---
title: Vis katalogsynkroniseringsstatus i Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel kan du lære, hvordan du kan kontrollere status for din katalogsynkronisering Office 365.
ms.openlocfilehash: 0cc5b5244c5809d3f1b13b15b200bd8cea585c7c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590353"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Vis katalogsynkroniseringsstatus i Microsoft 365

Hvis du har integreret dit lokale Active Directory-domæneservices (AD DS) med Azure Active Directory (Azure AD) ved at synkronisere dit lokale miljø med Microsoft 365, kan du også kontrollere status for din synkronisering.
  
## <a name="view-directory-synchronization-status"></a>Vis katalogsynkroniseringsstatus

- Log på siden [Microsoft 365 Administration](https://admin.microsoft.com) og vælg **DirSync-status** på startsiden.
- Alternativt  kan du gå til Aktive **brugere,** \> **og** på siden Aktive brugere **skal** du vælge \> Mere **katalogsynkronisering**. I **ruden Katalogsynkronisering** skal du **vælge Gå til administration af DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Oplysninger på siden Administrer katalogsynkronisering

I følgende tabel vises de funktioner, du kan få oplysninger om på siden.
  
Hvis der er et problem med din katalogsynkronisering, er fejlene også angivet på denne side. Du kan finde flere oplysninger om forskellige fejl, du kan støde på, [i Identificer katalogsynkroniseringsfejl Microsoft 365](identify-directory-synchronization-errors.md).
  
|Element|Hvad er det til?|
|:-----|:-----|
|**Bekræftede domæner** | Antal domæner i din Microsoft 365 lejer, som du har bekræftet, at du ejer. |
|**Ikke-bekræftede domæner** | Domæner, du har tilføjet, men ikke har bekræftet. |
|**Katalogsynkronisering aktiveret** |Sandt eller falsk. Angiver, om du har aktiveret katalogsynkronisering. |
|**Seneste mappesynkronisering** | Sidste gang katalogsynkronisering kørte. Viser en advarsel og et link til et fejlfindingsværktøj, hvis den seneste synkronisering skete for mere end tre dage siden. |
|**Synkronisering af adgangskoder er aktiveret** | Sandt eller falsk. Angiver, om du har synkronisering af adgangskodehash mellem vores lokale lejer og Microsoft 365 lejer. |
|**Sidste synkronisering af adgangskoder** | Sidste gang synkronisering af adgangskode-hash kørte. Viser en advarsel og et link til et fejlfindingsværktøj, hvis den seneste synkronisering skete for mere end tre dage siden. |
|**Klientversion af katalogsynkronisering** | Indeholder et downloadlink, hvis der er udgivet en ny version Forbind Azure AD. |
|**Tjenestekonto til katalogsynkronisering** | Viser navnet på din Microsoft 365-konto til katalogsynkronisering. |
|||

## <a name="monitor-synchronization-health"></a>Overvåge synkroniseringstilstanden

I dette afsnit skal du installere en Azure AD Forbind Health-agent på hver af dine lokale AD DS-domænecontrollere for at overvåge din identitetsinfrastruktur og de synkroniseringstjenester, der leveres af Azure AD Forbind. Overvågningsoplysningerne gøres tilgængelige i en Azure AD Forbind Health-portal, hvor du kan få vist beskeder, overvågning af ydeevne, forbrugsanalyse og andre oplysninger.

Den vigtige designbeslutning om, hvordan du bruger Azure AD Forbind Health, er baseret på, hvordan du bruger Azure AD Forbind:

- Hvis du bruger indstillingen administreret  godkendelse, skal du begynde med Brug [af Azure AD Forbind Health med synkronisering](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) for at forstå og konfigurere Azure AD Forbind Tilstand.
- Hvis du kun synkroniserer navnene på konti og grupper ved hjælp af sammensluttet godkendelse  med AD FS (Active Directory Federation Services), skal du starte med Brug af [Azure AD Forbind Health med AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) for at forstå og konfigurere Azure AD Forbind Health.

Når du er færdig, har du:

- Den Azure AD Forbind Health-agent, der er installeret på dine lokale identitetsudbyderservere.
- Portalen Azure AD Forbind Health, der viser den aktuelle tilstand af din lokale infrastruktur og synkroniseringsaktiviteter med Azure AD-lejeren for dit Microsoft 365 abonnement.