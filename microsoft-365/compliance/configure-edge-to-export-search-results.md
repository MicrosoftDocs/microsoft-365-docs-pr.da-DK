---
title: Brug eDiscovery-eksportværktøjet i Microsoft Edge
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Du skal aktivere ClickOnce-understøttelse for at bruge den nyeste version af Microsoft Edge til at downloade søgeresultater fra Indholdssøgning og eDiscovery i sikkerheds- og overholdelsescenteret.
ms.openlocfilehash: cd20a35a0a6ee2518667d21fadbca4577342de36
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995772"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Brug eDiscovery-eksportværktøjet i Microsoft Edge

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Som følge af de seneste ændringer af den nyeste version af Microsoft Edge er ClickOnce-understøttelse ikke længere aktiveret som standard. Hvis du vil fortsætte med at bruge eDiscovery-eksportværktøjet til at downloade indholdssøgning eller eDiscovery-søgeresultater, skal du enten bruge [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) eller aktivere Understøttelse af ClickOnce i den nyeste version af Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Aktivér Understøttelse af ClickOnce i Microsoft Edge

1. I Microsoft Edge skal du gå til **edge://flags/#edge-click-once**.

2. Hvis den eksisterende værdi er angivet til **Standard** eller **Deaktiveret** på rullelisten, skal du ændre den til **Aktiveret**.

   ![Vælg Aktiveret på rullelisten.](../media/ClickOnceimage1.png)

3. Rul ned til bunden af browservinduet, og klik på **Genstart** for at genstarte Edge.

   ![Klik på Genstart.](../media/ClickOnceimage2.png)

**Bemærk:** Organisationer kan bruge Gruppepolitik til at deaktivere ClickOnce-support. Hvis du vil kontrollere, om der er en organisationspolitik for ClickOnce-support, skal du gå til **edge://policy**. På følgende skærmbillede kan du se, at ClickOnce er aktiveret på tværs af hele organisationen. Hvis denne politikværdi er angivet til **falsk**, skal du kontakte en administrator i din organisation.

![Liste over Edge-organisatoriske politikker.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installér og kør eDiscovery-eksportværktøjet

1. Klik på **Download resultater** på pop op-siden i en eksport i indholdssøgning eller i en eDiscovery-sag.

   ![Klik på Download resultater på pop op-siden for at downloade søgeresultater.](../media/ClickOnceExport1.png)

2. Du bliver bedt om at bekræfte, at du vil starte værktøjet ved at klikke på **Åbn**.

   ![Klik på Åbn for at starte eDiscovery-eksportværktøjet.](../media/ClickOnceimage4.png)

   Hvis eDiscovery-eksportværktøjet ikke er installeret, bliver du bedt om at angive en sikkerhedsadvarsel, 

   ![Klik på Installér for at installere eDiscovery-eksportværktøjet.](../media/ClickOnceimage5.png)

3. Klik på **Installér**. Når det er installeret, startes eksportværktøjet automatisk.

Du kan få flere oplysninger i følgende emner:

- [Eksportér resultater af indholdssøgning](export-search-results.md)

- [Sådan aktiverer du eksperimentflag i Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
