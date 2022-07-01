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
description: Få mere at vide om, hvordan du opretter forbindelse mellem dit domæne og Microsoft 365.
ms.openlocfilehash: 2b02687e8d62a40272ffa5dad8ccabec4fbde368
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603854"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Opret forbindelse mellem dit domæne og Microsoft 365 til virksomheder

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>Se: Opret forbindelse mellem dit domæne og Microsoft 365

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198216).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Når du har konfigureret Microsoft 365 og flyttet dine maildata fra Google Workspace, kan du oprette forbindelse mellem dit domæne og Microsoft 365. 

Først skal du slette eksisterende DNS-poster fra Google, og derefter kan vi tilføje nye DNS-poster fra Microsoft 365.

1. Log på administrationskonsollen for Google Workspace på [admin.google.com](https://admin.google.com).
1. Vælg **Domæner**, **Administrer domæner**, **Få vist detaljer**, **Administrer domæne** og derefter **DNS** i venstre navigationsrude.
1. Rul ned til **Syntetiske poster**, åbn **Google Workspace**, vælg **Slet****, og slet** derefter igen.
1. Rul ned til **Brugerdefinerede ressourceposter** , og slet alle eksisterende DNS-poster, der vises, herunder alle de poster, du tidligere har oprettet til Microsoft 365.
1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. Vælg **Vis alle** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**indstillingsdomæner**</a> >  i venstre navigationsrude.
1. Vælg derefter dit standarddomæne.
1. Vælg **Fortsæt konfiguration**, og vælg  **Fortsæt** for at oprette forbindelse til dit domæne.
1. Rul ned for at få vist de DNS-poster, der skal kopieres til Google.
1. Åbn **MX-poster**, og kopiér posten under **Peger på adresse eller værdi**.
1. Gå tilbage til Google, og åbn rullelisten med posttypen i afsnittet **Brugerdefinerede ressourceposter** , og vælg **MX**.
1. Indsæt den post, du kopierede, i feltet **Data** .
1. Vælg derefter **Tilføj**.
1. Gentag processen for CNAME- og TXT-poster, og tilføj værdierne på administrationssiden for Google DNS.
1. Gå tilbage til Microsoft 365 Administration, og vælg **Fortsæt**.

    Domænekonfigurationen er fuldført.