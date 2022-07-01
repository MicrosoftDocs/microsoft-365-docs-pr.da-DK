---
title: Tilføj dit Google Workspace-domæne
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
description: Få mere at vide om, hvordan du flytter dit domæne fra Google Workspace til Microsoft 365 til virksomheder.
ms.openlocfilehash: 06129811ea1d97b0ffb770843c58373427228559
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601130"
---
# <a name="add-your-google-workspace-domain-to-microsoft-365"></a>Føj dit Google Workspace-domæne til Microsoft 365

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

## <a name="watch-add-google-workspace-domain"></a>Se: Tilføj domæne for Google Workspace

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198105).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LWKT?autoplay=false]

Føj dit Google Workspace-domæne til Microsoft 365 til virksomheder, så du kan fortsætte med at bruge din virksomheds mailadresse.

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. Vælg **Vis alle** > **indstillinger** >  Domæner i venstre <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**navigationsrude**</a> i Microsoft 365 Administration.
1. Vælg **Tilføj domæne**, angiv dit domænenavn, og vælg derefter **Brug dette domæne**. 
1. Vælg, **Føj en TXT-post til dns-posterne for domæner**, vælg **Fortsæt**, og kopiér txt-værdien. 
1. Gå tilbage til [Google Administration Konsol](https://admin.google.com), vælg **Domæner**, **Administrer domæner**, **Vis detaljer**, **Administrer domæne**, **DNS**, og rul derefter ned til **Brugerdefinerede ressourceposter**. 
1. Åbn rullelisten med posttypen, vælg **TXT**, indsæt den TXT-værdi, du kopierede, og vælg derefter **Tilføj**. 

    Opdateringen tager normalt et faktum inden for nogle få minutter, men kan tage op til 48 timer. 
1. Gå tilbage til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Administration</a>, vælg **Bekræft** og derefter **Luk**. 
1. Hvis du vil angive dit domæne som den primære mail for dine brugere, skal du vælge **Aktive** > [**brugere**](https://go.microsoft.com/fwlink/p/?linkid=834822) i venstre navigationsrude. 
1. Vælg en bruger, vælg **Administrer brugernavn og mail**, **Rediger**, vælg dit domæne på rullelisten, og vælg derefter **Udført** og **Gem ændringer**. 
1. Gentag denne proces for hver bruger. 

    Når du er færdig, er du klar til at installere Office-apps og overføre dine mail- og kalenderelementer til Microsoft 365. 