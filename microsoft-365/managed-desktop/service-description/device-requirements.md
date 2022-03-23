---
title: Krav til enhed
description: Oversigt over minimumskrav til hardware og software, så enheder kan fungere sammen med Microsoft Managed Desktop
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 957203829bfcfeb36696a1a4c34888938712b471
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593391"
---
# <a name="device-requirements"></a>Krav til enhed

Microsoft Managed Desktop evaluerer regelmæssigt krav til enheder, der skal medtages i tjenesten. I denne artikel beskrives de hardware- og softwarekrav, en enhed skal opfylde for at kunne fungere med Microsoft Managed Desktop.

Du kan gennemgå en liste over bestemte enheder, der allerede er godkendt til brug, ud fra disse krav. Filtrer efter Microsoft-administreret skrivebord [på siden Windows Pro for virksomhedsenheder](https://www.microsoft.com/en-us/windows/business/devices).

> [!NOTE]
> Disse krav kan ændres når som helst, men vi giver dig 30 dages varsel om ændringer af hardwarekrav. De senest ændrede krav er markeret med <b>\*</b>.

## <a name="check-hardware-requirements"></a>Kontrollér hardwarekrav

Ud over at gennemgå specifikationer for enheder kan du også bruge bedømmelseskontrollen[](../get-ready/readiness-assessment-downloadable.md), der kan downloades, til at bekræfte, at enheden opfylder de nødvendige krav.

Dette værktøj kontrollerer også de netværksindstillinger og slutpunkter, der er nødvendige for, at tjenesten kan fungere.

## <a name="minimum-requirements"></a>Minimumskrav

Hvis en enhed skal være tilmeldt Microsoft Managed Desktop, skal den opfylde eller overskride alle disse krav.

### <a name="manufacturer"></a>Producent

Enheden skal være fremstillet af en af disse producenter:

- Dell
- HP
- Lenovo
- Microsoft

> [!NOTE]
> Fra og med den 1. marts 2022 skal enheder, der administreres af Microsoft Managed Desktop, være understøttet af OEM'en.<br><br>Arbejd sammen med din OEM for at finde ud af, hvornår enheder i din portefølje når understøttelsen af slutningen af levetiden. Kunder er ansvarlige for at sikre, at enheder udskiftes før ophør af levetidssupport. Alle enheder, der falder uden for OEM-support, vil fortsat blive administreret af Microsoft Managed Desktop, men understøttelse af disse enheder kan være begrænset, da de er i risiko for sikkerheds- og ydeevneproblemer, som ikke kan reduceres af vores tjeneste.
</b>

### <a name="installed-software"></a>Installeret software

Enheden skal have denne software forudinstalleret:

- <b>\*</b>Windows 10 or Windows 11: Enterprise, Pro eller Pro Workstation Edition.
- 64-bit version af Microsoft 365 Apps til Enterprise.
- Alle relevante enhedsdrivere.

### <a name="physical-features"></a>Fysiske funktioner

Enheder skal have disse egenskaber:

- Aktiveret til UEFI-sikker start.
- Platformsmodul 2.0, der er tillid til.
- Kan virtualiseringsbaseret sikkerhed.
- [Hypervisor-beskyttet kodeintegritet,](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) der understøttes af AFRÅR.

Du kan finde flere oplysninger om disse funktioner og de teknologier, der er relateret til dem, som tjenesten bruger, under [Microsoft Managed Desktop-teknologier](../intro/technologies.md).

> [!NOTE]
>- ARM-processorer understøttes ikke.
>- <b>\*</b>Windows 11 har yderligere [hardwarekrav](/windows/whats-new/windows-11-requirements).

Enheder skal opfylde eller overskride følgende grænser for lagerplads og hukommelse:

- Boot drive must be any type other than a hard disk. SSD-, NVMe- og eMMC-drev er f.eks. alle gyldige valgmuligheder.
- Startdrevet skal have en kapacitet på mindst 128 GB.
- RAM (Intern enheds hukommelse) skal være lig med eller større end 8 GB.

Hvis enheden blev lavet efter d. 1. juli 2020, skal den også have et IR-kamera, en fingeraftrykslæser eller begge dele for at [understøtte Windows Hello](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security).

## <a name="recommended-features"></a>Anbefalede funktioner

Brugerne får en meget bedre oplevelse, hvis du vælger enheder, der har disse funktioner:

- Enten en Intel vPro-platform processor eller en AMD Ryzen Pro processor.
- Startdrev for SSD-typen med en kapacitet på mindst 256 GB.
- RAM (intern enheds hukommelse) på mindst 16 GB.
- Understøttelse af moderne standby.
- Enheden er af pc-typen Sikret kerne.
- Understøtter Kernel DMA-beskyttelse.
