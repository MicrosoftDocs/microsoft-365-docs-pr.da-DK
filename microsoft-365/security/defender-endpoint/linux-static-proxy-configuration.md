---
title: Microsoft Defender til slutpunkt på statisk proxyregistrering på Linux
ms.reviewer: ''
description: Beskriver, hvordan du konfigurerer Microsoft Defender til slutpunkt på Linux til statisk proxyregistrering.
keywords: microsoft, defender, Microsoft Defender til slutpunkt, linux, installation, proxy
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3b5061f0230a9704cb0fb9b80752c4d38954ad12
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591241"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>Konfigurer Microsoft Defender til slutpunkt på Linux for statisk proxyregistrering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft Defender til slutpunkt kan finde en proxyserver ved hjælp af miljøvariablen `HTTPS_PROXY` . Denne indstilling skal konfigureres **både** på installationstid, og når produktet er installeret.

## <a name="installation-time-configuration"></a>Konfiguration af installationstid

Under installationen skal miljøvariablen `HTTPS_PROXY` overføres til pakkestyringen. Pakkeadministratoren kan læse denne variabel på følgende måder:

- Variablen `HTTPS_PROXY` er defineret på `/etc/environment` følgende linje:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- Variablen `HTTPS_PROXY` er defineret i den globale pakkestyringskonfiguration. I Ubuntu 18.04 kan du f.eks. tilføje følgende linje til `/etc/apt/apt.conf.d/proxy.conf`:

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > Bemærk, at over to metoder kan definere proxyen til brug for andre programmer på systemet. Brug denne metode med forsigtighed, eller kun hvis det er beregnet til at være en generelt global konfiguration.

- Variablen `HTTPS_PROXY` er forudstillet til installations- eller fjernelseskommandoerne. Med APT-pakkestyringen skal du f.eks. starte variablen på følgende måde, når du installerer Microsoft Defender til slutpunkt:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > Tilføj ikke sudo mellem definitionen af miljøvariablen og nr., da variablen ellers ikke vil blive overført.

Miljøvariablen `HTTPS_PROXY` kan på samme måde defineres under fjernelse af installationen.

Bemærk, at installation og fjernelse af installation ikke nødvendigvis mislykkes, hvis en proxy er påkrævet, men ikke konfigureret. Telemetri vil dog ikke blive sendt, og handlingen kan tage meget længere tid på grund af netværkstidsouts.

## <a name="post-installation-configuration"></a>Efter installation af konfiguration

Efter installationen skal miljøvariablen `HTTPS_PROXY` defineres i Defender for Endpoint-tjenestefilen. Det gør du ved at køre `sudo systemctl edit --full mdatp.service`.
Du kan derefter udbrede variablen til tjenesten på en af to måder:

- Fjern kommentering af linjen, `#Environment="HTTPS_PROXY=http://address:port"` og angiv din statiske proxyadresse.

- Tilføj en linje `EnvironmentFile=/path/to/env/file`. Denne sti kan pege på `/etc/environment` eller en brugerdefineret fil, hvor der skal tilføjes følgende linje:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

Når du har `mdatp.service`ændret , skal du gemme filen og genstarte tjenesten, så ændringerne kan anvendes ved hjælp af følgende kommandoer:

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
