---
title: Konfigurere Microsoft Defender Antivirus ved hjælp af Microsoft Endpoint Manager
description: Brug Microsoft Endpoint Manager og Microsoft Intune til at konfigurere Microsoft Defender Antivirus og Endpoint Protection
keywords: scep, intune, endpoint protection, konfiguration
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 1eb126481cc9872c42906e0311d1c771da44c693
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/17/2021
ms.locfileid: "63592160"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug Microsoft Endpoint Manager til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Du kan bruge [Microsoft Endpoint Manager til](/mem/endpoint-manager-overview) at konfigurere Microsoft Defender Antivirus scanninger. [Microsoft Intune og](/mem/intune/fundamentals/what-is-intune) [Konfigurationsstyring er](/mem/configmgr/core/understand/introduction) nu en del af Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Konfigurer Microsoft Defender Antivirus scanninger i Endpoint Manager

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Gå til **Slutpunktssikkerhed**.

3. Vælg **Antivirus** under **Administrer**.

4. Vælg din Microsoft Defender Antivirus politik.

5. Vælg **Egenskaber** under **Administrer**.

6. Ud for **Konfigurationsindstillinger** skal du vælge **Rediger**.

   > [!IMPORTANT]
   > AllowOnAccessProtection og AllowIntrusionPreventionSystem antivirusindstillinger frarådes officielt og kan derfor ikke konfigureres. 

7. Udvid **sektionen Scanning** , og gennemse eller rediger dine scanningsindstillinger.

8. Vælg **Gennemse + gem**.

> [!TIP]
> Har du brug for hjælp? Se [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="related-articles"></a>Relaterede artikler

- [Referenceartikler til administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
