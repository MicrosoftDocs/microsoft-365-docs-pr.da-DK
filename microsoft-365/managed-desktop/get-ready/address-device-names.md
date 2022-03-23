---
title: Afhængighed af adresseenhedsnavn
description: Fjern afhængigheden af enhedsnavne, eller anmod om en undtagelse
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: dc79cca2f68a80d9f7e7d9a09fd6d2be147d0199
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63593236"
---
# <a name="address-device-name-dependency"></a>Afhængighed af adresseenhedsnavn

Microsoft Managed Desktop anvender et standardiseret navneformat, når enhederne er tilmeldt. Microsoft Managed Desktop omdøber automatisk enheder, hvis navnet ændres senere. Du kan finde flere oplysninger [under Enhedsnavne](../service-description/device-names.md).

> [!IMPORTANT]
> Hvis dit miljø afhænger af bestemte enhedsnavne (f.eks. for at understøtte en bestemt netværkskonfiguration), skal du undersøge mulighederne for at fjerne denne afhængighed, før du tilmelder dig Microsoft Managed Desktop. Hvis du skal bevare navneafhængigheden, kan du sende en anmodning via administrationsportalen for at deaktivere funktionen til omdøbning og bruge det ønskede navneformat.[](../working-with-managed-desktop/admin-support.md)

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Adresseenhedsnavne (denne artikel).
