---
title: Administrer automatiske filuploads
description: Aktivere indholdsanalyse og konfigurere filtypenavnet og udvidelser til vedhæftede filer, der skal sendes til analyse
keywords: automatisering, fil, uploads, indhold, analyse, fil, filtypenavn, mail, vedhæftet fil
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
ms.openlocfilehash: 21e7eb17759ff6127f3d91137023c058abe2715e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591311"
---
# <a name="manage-automation-file-uploads"></a>Administrer automatiske filuploads

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Aktivér funktionen til indholdsanalyse, så visse filer og vedhæftede filer i mails automatisk kan uploades til skyen for yderligere inspektion i Automatiseret undersøgelse.

Identificer filer og vedhæftede filer ved at angive filtypenavnet og navnene på vedhæftede filer i mails.

Hvis du f.eks. tilføjer *exe* og *bat* som filtypenavne for filer eller vedhæftede filer, så sendes alle filer eller vedhæftede filer med disse udvidelser automatisk til skyen til yderligere inspektion under automatiseret undersøgelse.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Tilføj filtypenavne og navne på vedhæftede filtypenavne.

1. I navigationsruden skal du **vælge Indstillinger** \> **slutpunkter, automatisering** \> **af** \> **slutpunkter skal uploades**.

2. Skift indstillingen for indholdsanalyse mellem **Til** og **Fra**.

3. Konfigurer følgende filtypenavne og separate filtypenavne med et komma:
   - **Filtypenavne – Mistænkelige** filer undtagen vedhæftede filer i mails sendes til yderligere inspektion

## <a name="related-topics"></a>Relaterede emner

- [Administrer udeladelse af automatiseringsmapper](manage-automation-folder-exclusions.md)
