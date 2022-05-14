---
title: Skybeskyttelse og Microsoft Defender Antivirus
description: Få mere at vide om skybeskyttelse og Microsoft Defender Antivirus
keywords: Microsoft Defender Antivirus, næste generations teknologier, næste generation af av, maskinel indlæring, antimalware, sikkerhed, defender, cloud, cloudbeskyttelse
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: d272a816b302ea0332422ff2324ca091e43cd7a4
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415986"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Skybeskyttelse og Microsoft Defender Antivirus

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Næste generations teknologier i Microsoft Defender Antivirus giver næsten øjeblikkelig, automatiseret beskyttelse mod nye og nye trusler. For at identificere nye trusler dynamisk arbejder næste generation af teknologier med store sæt forbundne data i Microsoft Intelligent Security-Graph og effektive AI-systemer (kunstig intelligens), der er baseret på avancerede modeller til maskinel indlæring. Cloudbeskyttelse arbejder sammen med Microsoft Defender Antivirus om at levere nøjagtig, realtids- og intelligent beskyttelse. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Diagram, der viser, hvordan skybeskyttelse fungerer sammen med Microsoft Defender Antivirus" lightbox="images/mde-cloud-protection.png":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Vi anbefaler, at skybeskyttelse er slået til. Du kan få mere at vide under [Hvorfor cloudbeskyttelse skal aktiveres for Microsoft Defender Antivirus](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>Sådan fungerer cloudbeskyttelse

Microsoft Defender Antivirus fungerer problemfrit sammen med Microsofts cloudtjenester. Disse cloudbeskyttelsestjenester, også kaldet Microsoft Advanced Protection Service (MAPS), forbedrer standardbeskyttelse i realtid. Med cloudbeskyttelse giver næste generations teknologier hurtig identifikation af nye trusler, nogle gange endda før et enkelt slutpunkt er inficeret. 

Følgende blogindlæg illustrerer, hvordan cloudbeskyttelse fungerer:

- [Lær de avancerede teknologier at kende i kernen af Microsoft Defender for Endpoint næste generations beskyttelse](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Hvorfor Microsoft Defender Antivirus er den mest udrullede i virksomheden](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [Overvågning af adfærd kombineret med maskinel indlæring ødelægger en massiv møntudvindingskampagne](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Hvordan kunstig intelligens stoppede et "Emotet"-udbrud](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Detonering af en dårlig kanin: Microsoft Defender Antivirus og lagdelt forsvar til maskinel indlæring](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Microsoft Defender Antivirus cloudbeskyttelsestjeneste: Avanceret forsvar i realtid mod aldrig før set malware](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> Den Microsoft Defender Antivirus cloudtjeneste er en mekanisme til levering af opdateret beskyttelse til dit netværk og dine slutpunkter. Som en cloudtjeneste er det ikke blot beskyttelse af filer, der er gemt i cloudmiljøet. Cloudtjenesten bruger i stedet distribuerede ressourcer og maskinel indlæring til at levere beskyttelse til dine slutpunkter i en hastighed, der er langt hurtigere end traditionelle sikkerhedsintelligensopdateringer.

## <a name="how-to-get-cloud-protection"></a>Sådan får du cloudbeskyttelse 

Cloudbeskyttelse er aktiveret som standard. Det kan dog være nødvendigt at aktivere den igen, hvis den er blevet deaktiveret som en del af tidligere organisatoriske politikker. Du kan få mere at vide under [Slå skybeskyttelse til](enable-cloud-protection-microsoft-defender-antivirus.md).

Hvis dit abonnement omfatter Windows 10 E5, kan du drage fordel af dynamiske efterretningsopdateringer i nødstilfælde, som giver beskyttelse næsten i realtid mod nye trusler. Når du slår cloudbeskyttelse til, kan rettelser til malwareproblemer leveres via clouden inden for få minutter i stedet for at vente på den næste opdatering. Se [Konfigurer Microsoft Defender Antivirus til automatisk at modtage nye beskyttelsesopdateringer, der er baseret på rapporter fra vores cloudtjeneste](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>Næste trin

Nu, hvor du har et overblik over skybeskyttelse i Microsoft Defender Antivirus, er her nogle af de næste trin:

1. Se [Hvorfor cloudbeskyttelse skal aktiveres for Microsoft Defender Antivirus](why-cloud-protection-should-be-on-mdav.md).

2. Fortsæt til [Aktivér skybeskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)