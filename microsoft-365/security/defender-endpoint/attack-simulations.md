---
title: Oplev Microsoft Defender til slutpunkt gennem simulerede angreb
description: Kør simuleringerne for angrebsscenariet for at opleve, hvordan Microsoft Defender til slutpunkt kan registrere, undersøge og reagere på brud.
keywords: test, scenarie, angreb, simulering, simuleret, diy, Microsoft Defender til slutpunkt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.technology: mde
ms.openlocfilehash: da02e1391b7624dc3e091ca1024a68c5756227a2
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63603119"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Oplev Microsoft Defender til slutpunkt gennem simulerede angreb 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-abovefoldlink)

> [!TIP]
>
> - Få mere at vide om de nyeste forbedringer i Microsoft Defender til slutpunkt: [Nyheder i Defender til Slutpunkt?](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/).
> - Defender til Slutpunkt demonstrerede brancheførende optik og registreringsfunktioner i den seneste MITRE-evaluering. Læs: [Insights fra den MITRE ATT&CK-baserede evaluering](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

Det kan være en god ide at opleve Defender til Slutpunkt, før du tager mere end nogle få enheder med til tjenesten. For at gøre dette kan du køre kontrolleret angrebssimulering på et par testenheder. Når du har kørt de simulerede angreb, kan du gennemgå, hvordan Defender til Slutpunkt viser skadelig aktivitet og undersøge, hvordan det muliggør en effektiv respons.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil køre en af de angivne simuleringer, skal du bruge mindst [én onboardingenhed](onboard-configure.md).

Læs gennemgangsdokumentet, der leveres med hvert angrebsscenarie. Hvert dokument indeholder krav til operativsystem og program samt detaljerede instruktioner, der er specifikke for et angrebsscenarie.

## <a name="run-a-simulation"></a>Kør en simulering

1. I **Endpoints** \> **Evaluation & selvstudier** \> **& simuleringerne** skal du vælge, hvilke af de tilgængelige angrebsscenarier du gerne vil simulere:
   - **Scenarie 1: Dokument går ned i backdoor** – simulerer leveringen af et manipuleret dokument. Dokumentet starter en særligt udformet bagdoor, der giver hackere kontrol.
   - **Scenarie 2: PowerShell-script** i filløse angreb – simulerer et filløst angreb, der afhænger af PowerShell, showcasing attack surface reduction and device learning detection of malicious memory activity.
   - **Scenarie 3:** Automatiseret hændelsesrespons – udløser automatisk undersøgelse, som automatisk registrerer og afhjælper brudsakter for at skalere din kapacitet for hændelsesrespons.

2. Download og læs det tilhørende gennemgangsdokument, der leveres sammen med det valgte scenarie.

3. Download simuleringsfilen, eller kopiér simuleringsscriptet \> ved at navigere **til & selvstudier** **og & simulering.** Du kan vælge at downloade filen eller scriptet på testenheden, men det er ikke obligatorisk.

4. Kør simuleringsfilen eller scriptet på testenheden som anvist i gennemgangsdokumentet.

> [!NOTE]
> Simuleringsfiler eller scripts efterligner angrebsaktivitet, men er faktisk bengalske og vil ikke skade eller kompromittere testenheden.
>
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Onboard-enheder](onboard-configure.md)
- [Onboard Windows-enheder](configure-endpoints.md)
