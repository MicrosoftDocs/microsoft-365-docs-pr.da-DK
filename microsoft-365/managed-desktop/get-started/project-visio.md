---
title: Installér Microsoft Project eller Microsoft Visio på Microsoft-administrerede stationære enheder
description: Oplysninger om installation af Microsoft Project eller Microsoft Visio på Microsoft-administrerede desktopenheder
keywords: Microsoft-administreret skrivebord, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: ab8a68ed17a8705c6e391371600d7b56660f6c57
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63589501"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Installér Microsoft Project eller Microsoft Visio på Microsoft-administrerede stationære enheder

Microsoft Project og Microsoft Visio kræver, at der installeres specifikke trin på Microsoft-administrerede skrivebordsenheder. I denne artikel beskrives forudsætningerne for og installationsprocessen for disse programmer.

## <a name="prerequisites"></a>Forudsætninger

Administratorer skal kontrollere, at de opfylder disse forudsætninger:

| Forudsætninger | Beskrivelse |
| ------ | ------ |
| Antal licenser | Den korrekte mængde licenser Microsoft Project Microsoft Visio licenser skal være tilgængelige for dine brugere. Microsoft Managed Desktop understøtter i øjeblikket kun 64-bit versioner af disse programmer. |
| Licensnavne | De korrekte licensnavne for disse programmer er: <ul><li>**Microsoft Project** – Project Online Professional eller Project Online Premium</li><li>**Microsoft Visio** – Visio Online Plan 2</li><ul> |
| Firmaportal | Licenserne Firmaportal være tilgængelige i din lejer, for at dine brugere kan installere disse programmer. Hvis Firmaportal ikke er installeret i din lejer, skal du [se Firmaportal](company-portal.md). |

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Installér Project og Visio til Microsoft-administrerede skrivebordsenheder

Microsoft Managed Desktop tilføjer Microsoft Project og Microsoft Visio to Win32-programmer i Microsoft Intune. Vi opretter også to grupper i Azure Active Directory. Grupperne tildeles til det tilsvarende program med formålet "Tilgængelig".

**Sådan installeres Project og Visio:**

Føj brugeren til den relevante gruppe, så bliver programmet tilgængeligt i Firmaportal. Det kan tage et par minutter at synkronisere, men derefter kan brugerne installere apps fra Firmaportal.

Azure AD-gruppenavn | Hvilke brugere skal tildeles?
 --- | ---
Moderne Workplace-Office-Project_Install | Brugere, der har Project
Moderne Workplace-Office-Visio_Install | Brugere, der har brug for Visio

## <a name="communicate-changes"></a>Kommunikere ændringer

Det er vigtigt, at it-administratorer giver deres brugere besked om, hvordan de installerer Project og Visio. Denne kommunikation omfatter:

- Underrette brugerne, når disse programmer er tilgængelige for dem.
- Vejledning i at installere disse programmer fra Firmaportal.
