---
title: Angiv yderligere definitionssæt for inspektion af netværkstrafik for Microsoft Defender Antivirus
description: Angiv yderligere definitionssæt for netværkstrafikinspektion for Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, netværkstrafikinspektion
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: f7b940604272035dc37b170eb759fa0ec45582b6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592205"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>Angive yderligere definitionssæt til inspektion af netværkstrafik

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan angive yderligere definitionssæt til inspektion af netværkstrafik ved hjælp Gruppepolitik.

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>Brug Gruppepolitik til at angive yderligere definitionssæt til inspektion af netværkstrafik

1. På slutpunktet Gruppepolitik administration skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Gå til **Windows Components** \> **Microsoft Defender Antivirus** \> **Network Inspection System**.

3. Vælg **Angiv yderligere definitionssæt for inspektion af netværkstrafik**. Denne politik er som standard indstillet til **Ikke konfigureret**.

4. Hvis du vil redigere politikken, skal du vælge **linket rediger politikindstilling** .

5. Vælg **Aktiveret**, og vælg **derefter** Vis **... i sektionen Indstillinger**.

6. Føj poster til listen, og vælg derefter **OK**.

   Hver post skal være angivet som et navneværdi-par, hvor navnet er en strengrepræsentation af et definitionssæt GUID. Som et eksempel er det definitionssæt GUID, der skal aktivere testsikkerhedsintelligens, defineret som: `{b54b6ac9-a737-498e-9120-6616ad3bf590}`. Værdien bruges ikke, så vi anbefaler, at den angives til `0`.

7. Vælg **OK**, og installér derefter den opdaterede Gruppepolitik-objekt. Se [Gruppepolitik Administrationskonsol](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Bruger du Gruppepolitik lokale objekter? Se, hvordan de oversættes i skyen. [Analysér dine lokale gruppepolitikobjekter ved hjælp Gruppepolitik analyser i Microsoft Endpoint Manager – forhåndsvisning](/mem/intune/configuration/group-policy-analytics).

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Aktivér skybaseret leveringsbeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Sådan oprettes og installeres antimalwarepolitikker: Skybeskyttelsestjeneste](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)