---
title: Administrer udeladelse af automatiseringsmapper
description: Tilføj udeladelse af automatiseringsmapper for at kontrollere de filer, der er udelukket fra en automatisk undersøgelse.
keywords: administrer, automatisering, udelukkelse, bloker, ren, skadelig
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
ms.openlocfilehash: 54c0f7f67b62216eae4264c8e7a55c0e34c82fb0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592636"
---
# <a name="manage-automation-folder-exclusions"></a>Administrer udeladelse af automatiseringsmapper

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

Udeladelse af automatiseringsmapper giver dig mulighed for at angive mapper, som automatiseret undersøgelse vil springe over.

Du kan styre følgende attributter for den mappe, som du gerne vil ignorere:

- Mapper: Du kan angive en mappe og dens undermapper, der skal **ignoreres**.

  > [!NOTE]
  > På nuværende tidspunkt understøttes brugen af jokertegn som en metode til at udelukke filer under en mappe endnu ikke.

- **Filtypenavne: Du kan** angive udvidelser, der skal udelades i en bestemt mappe. Udvidelserne er en metode til at forhindre en hacker i at bruge en ekskluderet mappe til at skjule en udnyttelse. Udvidelserne definerer udtrykkeligt, hvilke filer der skal ignoreres.

- **Filnavne**: Du kan angive de filnavne, der skal udelades i en bestemt mappe. Navnene er en metode til at forhindre en hacker i at bruge en ekskluderet mappe til at skjule en udnyttelse. Navnene definerer eksplicit, hvilke filer der skal ignoreres.

## <a name="add-an-automation-folder-exclusion"></a>Tilføje en udeladelse af automatiseret mappe

1. I navigationsruden skal du **vælge Indstillinger** \> **udeladelse af slutpunkter** \> **i** \> **mappen Regler for automatisering**.

2. Klik **på Udeladelse af ny mappe**.

3. Angiv mappedetaljerne:

    - Mappe
    - Udvidelser
    - Filnavne
    - Beskrivelse

4. Klik på **Gem**.

> [!NOTE]
> Live Response-kommandoer til at indsamle eller undersøge ekskluderede filer vil mislykkes med fejl: "Filen er udeladt". Desuden ignorerer automatiserede undersøgelser de udeladte elementer.

## <a name="edit-an-automation-folder-exclusion"></a>Redigere en udeladelse af en automatiseringsmappe

1. I navigationsruden skal du **vælge Indstillinger** \> **udeladelse af slutpunkter** \> **i** \> **mappen Regler for automatisering**.
2. Klik **på Rediger** ved udeladelse af mappen.
3. Opdater oplysningerne for reglen, og klik på **Gem**.

## <a name="remove-an-automation-folder-exclusion"></a>Fjern en udeladelse af en automatiseringsmappe

1. I navigationsruden skal du **vælge Indstillinger** \> **udeladelse af slutpunkter** \> **i** \> **mappen Regler for automatisering**.
2. Klik **på Fjern udeladelse**.

## <a name="related-topics"></a>Relaterede emner

- [Administrer automatiserede/blokerede lister](manage-indicators.md)
- [Administrer automatiske filuploads](manage-automation-file-uploads.md)
