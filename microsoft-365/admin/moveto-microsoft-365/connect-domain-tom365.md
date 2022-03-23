---
title: Forbind dit domæne til Microsoft 365
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan du forbinder dit domæne Microsoft 365.
ms.openlocfilehash: d54b3bbf00dd0cf37006924e2884f2861c345d3e
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63594146"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Forbind dit domæne til Microsoft 365 til virksomheder

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Når du har konfigureret Microsoft 365 og flyttet dine maildata fra Google Workspace, kan du forbinde dit domæne Microsoft 365. 

Først skal du slette eksisterende DNS-poster fra Google, og derefter kan vi tilføje nye DNS-poster fra Microsoft 365.

## <a name="try-it"></a>Prøv det!

1. Log på din Google Workspace-administratorkonsol [admin.google.com](https://admin.google.com).
1. Vælg **Domæner**, **Administrer domæner, Vis** **detaljer**, **Administrer domæne** og derefter **DNS** i venstre navigationslinje.
1. Rul ned til **Vælgeposter**, åbn **Google Workspace**, **vælg Slet** og derefter **Slet** igen.
1. Rul ned til **Brugerdefinerede ressourceposter**, og slet eventuelle eksisterende DNS-poster, der vises, herunder eventuelle, du tidligere har oprettet til Microsoft 365.
1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. I venstre navigationslinje skal du **vælge Vis** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
1. Vælg derefter dit standarddomæne.
1. Vælg **Fortsæt konfiguration**, og vælg derefter Fortsæt for at oprette forbindelse til  **dit domæne**.
1. Rul ned for at se de DNS-poster, der skal kopieres til Google.
1. Åbn **MX Records**, og **kopiér posten under** Peger på adresse eller værdi.
1. Gå tilbage til Google, og åbn **rullemenuen** Posttype i sektionen Brugerdefinerede ressourceposter, og vælg **MX**.
1. Indsæt den **post** , du kopierede, i feltet Data.
1. Vælg derefter **Tilføj**.
1. Gentag processen for CNAME- og TXT-poster, og tilføj værdierne på google DNS-administrationssiden.
1. Gå tilbage til Microsoft 365 Administration og vælg **Fortsæt**.

    Konfigurationen af dit domæne er fuldført.