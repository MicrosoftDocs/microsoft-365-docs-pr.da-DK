---
title: Brug eksportværktøjet eDiscovery i Microsoft Edge
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
description: Du skal aktivere ClickOnce-support for at bruge den nyeste version af Microsoft Edge til at downloade søgeresultater fra Indholdssøgning og eDiscovery i Sikkerheds- og overholdelsescenteret.
ms.openlocfilehash: bd42ebffce326e4abe4943ff4187fc2bd960ff65
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 09/12/2021
ms.locfileid: "63588758"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>Brug eksportværktøjet eDiscovery i Microsoft Edge

Som følge af de seneste ændringer af den nyeste version af Microsoft Edge er ClickOnce support ikke længere aktiveret som standard. Hvis du vil fortsætte med at bruge eDiscovery-eksportværktøjet til at downloade indholdssøgning eller eDiscovery-søgeresultater, skal du enten bruge [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) eller aktivere ClickOnce-support i den nyeste version af Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>Aktivér ClickOnce support i Microsoft Edge

1. I Microsoft Edge skal du gå til **edge://flags/#edge-click-once**.

2. Hvis den eksisterende værdi er angivet til **Standard eller** **Deaktiveret** på rullelisten, skal du ændre den til **Aktiveret**.

   ![Vælg Aktiveret på rullelisten.](../media/ClickOnceimage1.png)

3. Rul ned til bunden af browservinduet, og klik på Genstart **for** at genstarte Edge.

   ![Klik på Genstart.](../media/ClickOnceimage2.png)

**Bemærk!** Organisationer kan bruge Gruppepolitik til at deaktivere ClickOnce support. Hvis du vil kontrollere, om der er en organisationspolitik for ClickOnce, skal du gå **til edge://policy**. Følgende skærmbillede viser, at ClickOnce er aktiveret på tværs af hele organisationen. Hvis denne politikværdi er **indstillet til** falsk, skal du kontakte en administrator i organisationen.

![Liste over Edge-organisationspolitikker.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>Installere og køre eDiscovery-eksportværktøjet

1. Klik **på Hent resultater** på pop op-siden for en eksport i Indholdssøgning eller en eDiscovery-sag.

   ![Klik på Hent resultater på pop op-siden for at hente søgeresultater.](../media/ClickOnceExport1.png)

2. Du bliver bedt om at bekræfte, at du vil starte værktøjet. Klik på **Åbn**.

   ![Klik på Åbn for at starte eDiscovery-eksportværktøjet.](../media/ClickOnceimage4.png)

   Hvis eksportværktøjet eDiscovery ikke er installeret, bliver du bedt om at angive en sikkerhedsadvarsel. 

   ![Klik på Installer for at installere eDiscovery-eksportværktøjet.](../media/ClickOnceimage5.png)

3. Klik på **Installér**. Når eksportværktøjet er installeret, starter det automatisk.

Du kan finde flere oplysninger i følgende emner:

- [Eksportér resultater fra indholdssøgning](export-search-results.md)

- [Sådan aktiveres eksperimentflag i Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
