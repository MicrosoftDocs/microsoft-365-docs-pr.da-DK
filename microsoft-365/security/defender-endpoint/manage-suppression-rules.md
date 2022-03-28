---
title: Administrer skjuleregler for Microsoft Defender til slutpunkter
description: Du skal muligvis forhindre, at beskeder vises i portalen ved hjælp af undertrykkende regler. Få mere at vide om, hvordan du administrerer dine undertrykkende regler i Microsoft Defender for Endpoint.
keywords: administrer skjule, regler, regelnavn, omfang, handling, beskeder, aktivere, deaktivere
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ee488256363cbb008f670bb8c88d3fb88d7c4090
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597553"
---
# <a name="manage-suppression-rules"></a>Administrer skjuleregler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Der kan være scenarier, hvor du er nødt til at undertrykke beskeder fra at blive vist på portalen. Du kan oprette undertrykkeregler for bestemte beskeder, der er kendt for at være besværlige, f.eks. kendte værktøjer eller processer i organisationen. Du kan finde flere oplysninger om, hvordan du undertrykker beskeder, [under Undertrykke beskeder](manage-alerts.md).

Du kan få vist en liste over alle reglerne for undertrykkelse og administrere dem på ét sted. Du kan også slå en regel for beskedundertrykning til eller fra.


1. I navigationsruden skal du **vælge Indstillinger** \> **besked om slutpunkter** \> **for** \> **besked om slutpunkter**. Listen over undertrykkende regler, som brugerne i organisationen har oprettet, vises.

2. Vælg en regel ved at klikke på afkrydsningsfeltet ud for regelnavnet.

3. Klik **på Aktiver** regel, **Rediger** regel eller  **Slet regel**. Når du foretager ændringer i en regel, kan du vælge at frigive beskeder om, at den allerede er blevet undertrykt, uanset om disse beskeder opfylder de nye kriterier eller ej. 


## <a name="view-details-of-a-suppression-rule"></a>Få vist oplysninger om en undertrykkende regel

1. I navigationsruden skal du **vælge Indstillinger** \> **besked om slutpunkter** \> **for** \> **besked om slutpunkter**. Listen over undertrykkende regler, som brugerne i organisationen har oprettet, vises.

2. Klik på et regelnavn. Oplysninger om reglen vises. Du får vist oplysninger om reglen, f.eks. status, omfang, handling, antal matchende beskeder, der er oprettet af, og den dato, hvor reglen blev oprettet. Du kan også få vist tilknyttede beskeder og regelbetingelserne.

## <a name="related-topics"></a>Relaterede emner

- [Administrer beskeder](manage-alerts.md)
