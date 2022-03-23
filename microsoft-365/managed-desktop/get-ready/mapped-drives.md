---
title: Forbered tilknyttede drev til Microsoft Managed Desktop
description: Vigtige trin til at sikre, at brugere kan få adgang til data på tilknyttede drev
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d8100323350b11cb2329d752892cd64b1bc764a0
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63587470"
---
# <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Forbered tilknyttede drev til Microsoft Managed Desktop

Mange virksomhedsmiljøer har ældre krav til tilknyttede drev, der gør det muligt for deres brugere eller teams at dele og gemme filer eller for programmer i det lokale miljø.

Microsoft anbefaler ikke brug af tilknyttede drev med Microsoft Managed Desktop. Vi anbefaler i stedet, at du moderniserer dine filadgangsløsninger på følgende måde:
  
- Overfør tilknyttede drev, der bruges af individuelle brugere, OneDrive for Business.
- Overfør tilknyttede drev, der bruges af teams til at dele filer SharePoint Online.
- Modernisere eller erstatte programmer, der bruger lokale filshares, for at fjerne dette krav.
  
Når du moderniserer disse tjenester, får du den bedste brugeroplevelse med Microsoft Managed Desktop. Microsoft FastTrack-tjenester kan hjælpe dig med at modernisere dit miljø ved hjælp af Microsofts skytjenester. Du kan kontrollere, om du er berettiget til FastTrack tjenester på [Berettigede tjenester og planer](/fasttrack/m365-eligible-services-and-plans). Kontakt dem derefter direkte for at forberede dig til Microsoft Managed Desktop. Du kan finde flere FastTrack OneDrive for Business eller SharePoint onlineoverførsel under [Dataoverførsel](/fasttrack/o365-data-migration).

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Tilknyttede drev på Microsoft Managed Desktop

Hvis du ikke kan fjerne eller erstatte tilknyttede drev i visse use cases, skal du sende en supportanmodning i Administrationsportalen for Microsoft Managed Desktop for at få dem installeret for brugere af Microsoft-administreret skrivebord.

Hvis du anmoder om en sådan anmodning, skal du angive følgende oplysninger i supportanmodningen:

- Alle UNC-stier til fildelingsplaceringer, der skal knyttes til Microsoft Managed Desktop-enheder.
- Brugergrupper, der kræver adgang til disse fildelingsplaceringer.
- Et bestemt drevbogstav, der skal tildeles (hvis det er nødvendigt).

Eksempel:

| Drevbogstav | UNC-sti | Brugergruppe |
|--------------|----------|------------|
| X:  | \\\server\share\Marketing | ContosoMarketing |

Det er helt dit ansvar at:

- Sørg for, at brugere og grupper har og vedligeholder de rette tilladelser til at få adgang til fildelingsplaceringer
- Gør de lokale filtjenester tilgængelige.

Du skal fjerne dine krav til sådanne filshares så hurtigt som muligt.

**Sådan har du tilknyttede drev installeret i Microsoft Managed Desktop:**

Sørg for, at tilknyttede drev ikke kan undgås, og at du nøje har gennemgået kravene, før du indsender en supportanmodning.

1. Gå til [Microsoft Endpoint Manager](https://endpoint.microsoft.com/), og vælg **Fejlfinding + support**.
1. I sektionen **Microsoft Managed Desktop skal** du vælge **Service requests**.
1. Indsend en supportanmodning med titlen "Installation af tilknyttede drev", og angiv alle de nødvendige filshareoplysninger.  
1. Microsofts administrerede it-handlinger til stationære computere anbefaler, at du opdaterer din anmodning ved hjælp af opdateringer, når anmodningen er afsluttet. I første omgang vil denne konfiguration kun blive installeret på enheder i gruppen Testinstallation.  
1. Du skal teste og bekræfte, om den konfiguration, der installeres af Microsoft Managed Desktop IT-handlinger, fungerer som forventet.
1. I den samme supportanmodning kan du svare ved hjælp af fanen **Diskussion** for at underrette Microsoft Managed Desktop IT-handlinger, når du har fuldført testen.  
1. Microsoft Managed Desktop IT Operations-teamet vil derefter installere konfigurationen for de andre installationsgrupper.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. Forbered tilknyttede drev (denne artikel).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
