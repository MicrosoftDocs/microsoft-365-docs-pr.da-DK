---
title: Microsoft Defender for Endpoint Device Control Flytbare Storage Protection
description: Forstå de "funktioner, der hjælper med at forhindre bruger eller maskine eller begge i at bruge uautoriserede flytbare lagermedier
keywords: flytbare lagermedier
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3d679cfa4f09b06e2c7923ee1fe6e47247d90f76
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665068"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender for Endpoint Device Control Flytbare Storage Protection


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Enhedskontrol af flytbare lagermedier i Microsoft Defender for Endpoint forhindrer brugere, slutpunkter eller begge dele i at bruge uautoriserede flytbare lagermedier.

## <a name="protection-policies"></a>Beskyttelsespolitikker

### <a name="removable-storage-access-control"></a>Adgangskontrol til flytbart lager

**Kapaciteter**

- *Revision* Læse- eller skriveadgang eller udføre adgang til flytbart lager baseret på forskellige enhedsegenskaber med eller uden en udeladelse.
- *Forhindre* Læse- eller skriveadgang eller udfør-adgang med eller uden en udeladelse – Tillad en bestemt enhed baseret på forskellige enhedsegenskaber.

**Windows 10 og Windows 11 supportoplysninger**:

- Anvendt på enten enhedsniveau, brugerniveau. eller begge dele. Tillad kun, at bestemte personer, der udfører læse-/skrive-/eksekveringsadgang, får adgang til et bestemt flytbart lager på en bestemt computer.
- Understøtter MEM OMA-URI og GPO.
- Understøttede '[Enhedsegenskaber](#device-properties)' som angivet.
- Du kan se en funktion i Windows under [Flytbare lagermedier Access Control](device-control-removable-storage-access-control.md).

**Understøttet platform** – Windows 10, Windows 11

**oplysninger om macOS-support**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på.
- Du kan få mere at vide om macOS-specifikke oplysninger under [Enhedskontrol til macOS](mac-device-control-overview.md).

**Understøttet platform** – macOS Catalina 10.15.4+ (med systemudvidelser aktiveret)


### <a name="device-installation"></a>Enhedsinstallation

**Capabilities** – Undgå installation med eller uden udeladelse baseret på forskellige enhedsegenskaber.

**Windows 10 og Windows 11 supportoplysninger**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på.
- Understøtter Microsoft Endpoint Manager og Gruppepolitik objekter.
- Understøttede '[Enhedsegenskaber](#device-properties)' som angivet.
- Du kan få flere oplysninger om Windows under [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

**Understøttet platform** – Windows 10, Windows 11

**oplysninger om macOS-support**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på
- Du kan få mere at vide om macOS-specifikke oplysninger under [Enhedskontrol til macOS](mac-device-control-overview.md).

**Understøttet platform** – macOS Catalina 10.15.4+ (med systemudvidelser aktiveret) eller nyere

### <a name="endpoint-dlp-removable-storage"></a>Slutpunkt DLP Flytbart lager

**Funktioner** – Overvågning, advarsel eller forhindre en bruger i at kopiere et element eller oplysninger til flytbare medier eller USB-enheder.

**Beskrivelse** – Du kan finde flere oplysninger om Windows under [Få mere at vide om Microsoft 365 forebyggelse af datatab for Slutpunkt](../../compliance/endpoint-dlp-learn-about.md).

**Understøttet platform** – Windows 10, Windows 11

### <a name="bitlocker"></a>Bitlocker

**Egenskaber**:

- Bloker data, der skal skrives til flytbare drev, der ikke er BitLocker-beskyttet.
- Bloker adgang til flytbare drev, medmindre de er krypteret på en computer, der ejes af din organisation

**Beskrivelse** – Du kan få flere oplysninger om Windows under [BitLocker - Indstillinger til flytbart drev](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Understøttet platform** – Windows 10, Windows 11

## <a name="device-properties"></a>Enhedsegenskaber

Microsoft Defender for Endpoint Device Control Flytbare Storage Protection giver dig mulighed for at begrænse adgangen til det flytbare lager baseret på de egenskaber, der er beskrevet i nedenstående tabel:

<br/><br/>

|Egenskabsnavn|Gældende politikker|Gælder for operativsystemer|Beskrivelse|
|---|---|---|---|
|Enhedsklasse|[Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|Windows|Du kan få oplysninger om enheds-id-formater under [Enhedskonfigurationsklasse](/windows-hardware/drivers/install/overview-of-device-setup-classes). Følgende to links indeholder en komplet liste over enhedsinstallationsklasser. Klasserne "Systemanvendelse" refererer hovedsageligt til enheder, der følger med en computer/maskine fra fabrikken, mens klasserne "Leverandør" for det meste henviser til enheder, der kan have forbindelse til en eksisterende computer/computer: [Systemdefinerede enhedsinstallationsklasser tilgængelige for leverandører - Windows drivere](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) og [systemdefinerede enhedsinstallationsklasser reserveret til systemanvendelse – Windows drivere](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Bemærk**! Enhedsinstallation kan anvendes på alle enheder, ikke kun Flytbare lagermedier.|
|Primært id|[Flytbart lager Access Control](device-control-removable-storage-access-control.md)|Windows|Det primære id omfatter flytbart lager og cd/dvd og Windows Portable Device/WPD.|
|Enheds-id|[Flytbart lagermedier Access Control](device-control-removable-storage-access-control.md); <p> [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|Windows|Du kan få oplysninger om formater for enheds-id [under Standard USB-id'er](/windows-hardware/drivers/install/standard-usb-identifiers), f.eks. USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Hardware-id|[Flytbart lager Access Control](device-control-removable-storage-access-control.md) <p> [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint](control-usb-devices-using-intune.md)|Windows|En streng identificerede enheden i systemet, f.eks. USBSTOR\DiskGeneric_Flash_Disk___8.07; **Bemærk**! Hardware-id'et er ikke entydigt. forskellige enheder kan dele den samme værdi.|
|Forekomst-id|[Flytbart lager Access Control](device-control-removable-storage-access-control.md) <p> Installation af enhed|Windows|En streng identificerer entydigt enheden i systemet, f.eks. USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Fuldt navn|[Flytbart lager Access Control](device-control-removable-storage-access-control.md)|Windows|En streng, der er knyttet til enheden, f.eks. Generic Flash Disk USB-enhed|
|Leverandør-id/produkt-id|[Flytbart lager Access Control](device-control-removable-storage-access-control.md)|Windows <p> Macos|Leverandør-id er den firecifrede leverandørkode, som USB-udvalget tildeler kreditoren. Produkt-id er den firecifrede produktkode, som leverandøren tildeler til enheden. Understøtter jokertegn.|
|Serielt tal-id|[Flytbart lager Access Control](device-control-removable-storage-access-control.md)|Windows <p> Macos |Det kan f.eks. `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
