---
title: Slå definition-tilbagetrækning til for Microsoft Defender Antivirus
description: Slå definition af tilbagetrækning til for Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, definition af tilbagetrækning
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: dd9cd313dec962547acef85c6da326d3b6e5c58f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63606546"
---
# <a name="turn-on-definition-retirement"></a>Slå tilbagetrækning af definition til

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan konfigurere tilbagetrækning af definition ved hjælp Gruppepolitik. Tilbagetrækning af definition kontrollerer, om en computer har de nødvendige sikkerhedsopdateringer for at beskytte den mod en bestemt sikkerhedsrisiko. Hvis systemet ikke er sårbar over for den udnyttelse, der er registreret af en definition, er den pågældende definition "udgået". Hvis alle sikkerhedsintelligenser for en given protokol er udgået, fortolkes den pågældende protokol ikke længere. Aktivering af denne funktion er med til at forbedre ydeevnen. På en computer, der er opdateret med alle de nyeste sikkerhedsopdateringer, har netværksbeskyttelse ingen indflydelse på netværkets ydeevne.

## <a name="use-group-policy-to-configure-definition-retirement"></a>Brug Gruppepolitik at konfigurere tilbagetrækning af definition

1. På slutpunktet Gruppepolitik administration skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Gå til **Administrative skabeloner til** \> **computerkonfiguration** \> **Windows komponenter** \> **Microsoft Defender Antivirus dit** \> **netværksinspektionssystem**.

3. Vælg **Aktiver tilbagetrækning af definition**. Denne politik er som standard aktiveret. Hvis indstillet **til Ikke konfigureret**, aktiveres tilbagetrækning af definition.

4. Hvis du vil redigere politikken, skal du vælge **linket rediger politikindstilling** .

5. Vælg **Aktiveret**, og vælg derefter **OK**.

6. Installér den opdaterede Gruppepolitik-objekt. Se [Gruppepolitik Administrationskonsol](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Bruger du Gruppepolitik lokale objekter? Se, hvordan de oversættes i skyen. [Analysér dine lokale gruppepolitikobjekter ved hjælp Gruppepolitik analyser i Microsoft Endpoint Manager – forhåndsvisning](/mem/intune/configuration/group-policy-analytics).
