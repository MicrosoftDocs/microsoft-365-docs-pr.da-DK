---
title: Konfigurer Microsoft Defender Antivirus ved hjælp af Microsoft Endpoint Manager
description: Brug Microsoft Endpoint Manager og Microsoft Intune til at konfigurere Microsoft Defender Antivirus og Endpoint Protection
keywords: scep, intune, slutpunktsbeskyttelse, konfiguration
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
ms.openlocfilehash: 892ab423d09aae9c02135bc569f1321dbab7fa0d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419500"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>Brug Microsoft Endpoint Manager til at konfigurere og administrere Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Du kan bruge [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) til at konfigurere Microsoft Defender Antivirus scanninger. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) og [Configuration Manager](/mem/configmgr/core/understand/introduction) er nu en del af Endpoint Manager.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>Konfigurer Microsoft Defender Antivirus scanninger i Endpoint Manager

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Gå til **Slutpunktssikkerhed**.

3. Under **Administrer** skal du vælge **Antivirus**.

4. Vælg din Microsoft Defender Antivirus politik.

5. Under **Administrer** skal du vælge **Egenskaber**.

6. Ud for **Konfigurationsindstillinger** skal du vælge **Rediger**.

   > [!IMPORTANT]
   > Indstillingerne allowOnAccessProtection og AllowIntrusionPreventionSystem frarådes officielt og kan derfor ikke konfigureres. 

7. Udvid afsnittet **Scan** , og gennemse eller rediger dine scanningsindstillinger.

8. Vælg **Gennemse + gem**.

> [!TIP]
> Har du brug for hjælp? Se [Administrer slutpunktssikkerhed i Microsoft Intune](/mem/intune/protect/endpoint-security).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="related-articles"></a>Relaterede artikler

- [Referenceartikler om administration og konfigurationsværktøjer](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
