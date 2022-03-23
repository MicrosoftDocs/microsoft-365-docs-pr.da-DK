---
title: Flytbar enhedsstyring på Microsoft Defender til slutpunkt Storage beskyttelse
description: Forstå de "funktioner, der er med til at forhindre bruger eller maskine eller begge i at bruge uautoriserede flytbare lagringsmedier
keywords: flytbare lagringsmedier
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
ms.openlocfilehash: cc1c2a5fc05b795c0fc69ebc8a3b50dbf556960b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592206"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Flytbar enhedsstyring på Microsoft Defender til slutpunkt Storage beskyttelse


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Enhedshåndtering af flytbart lager i Microsoft Defender til slutpunkt forhindrer brugere, slutpunkter eller begge i at bruge uautoriserede flytbare lagringsmedier.

## <a name="protection-policies"></a>Beskyttelsespolitikker

### <a name="removable-storage-access-control"></a>Kontrol af flytbare lageradgang

**Funktioner**

- *Overvågning* Læse- eller skrive- eller udføre adgang til flytbart lager baseret på forskellige enhedsegenskaber med eller uden udelukkelse.
- *Forebyd* Læse eller skrive eller udføre adgang med eller uden udelukkelse – Tillad bestemte enheder baseret på forskellige enhedsegenskaber.

**Windows 10 og Windows 11-supportoplysninger**:

- Anvendt på enhedsniveau og brugerniveau. eller begge dele. Tillad kun bestemte personer, der udfører læse-/skrive-/eksekveringsadgang til bestemte flytbare lager på bestemte maskiner.
- Understøttelse af MEM OMA-URI og gruppepolitikobjekt.
- Understøttede "[Enhedsegenskaber](#device-properties)" som angivet.
- For funktionen i Windows, se [Flytbare lager Access Control](device-control-removable-storage-access-control.md).

**Understøttet platform** – Windows 10, Windows 11

**supportoplysninger til macOS**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på.
- Du kan finde macOS-specifikke oplysninger [under Enhedsstyring til macOS](mac-device-control-overview.md).

**Understøttet platform** – macOS Catalina 10.15.4+ (med systemudvidelser aktiveret)


### <a name="device-installation"></a>Installation af enhed

**Funktioner –** Undgå installation med eller uden udelukkelse baseret på forskellige enhedsegenskaber.

**Windows 10 og Windows 11-supportoplysninger**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på.
- Understøtter Microsoft Endpoint Manager og Gruppepolitik objekter.
- Understøttede "[Enhedsegenskaber](#device-properties)" som angivet.
- Du kan finde flere Windows i Sådan styrer du [USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt](control-usb-devices-using-intune.md).

**Understøttet platform** – Windows 10, Windows 11

**supportoplysninger til macOS**:

- Anvendt på enhedsniveau: Den samme politik gælder for alle brugere, der er logget på
- Du kan finde macOS-specifikke oplysninger [under Enhedsstyring til macOS](mac-device-control-overview.md).

**Understøttet platform** – macOS Catalina 10.15.4+ (med systemudvidelser aktiveret) eller nyere

### <a name="endpoint-dlp-removable-storage"></a>Slutpunkt DLP Flytbart lager

**Funktioner –** Overvåge, advare eller forhindre en bruger i at kopiere et element eller oplysninger til flytbare medier eller USB-enheder.

**Beskrivelse** – Du kan finde flere Windows oplysninger om datatab [i Få mere Microsoft 365 om forebyggelse af datatab i slutpunkter](../../compliance/endpoint-dlp-learn-about.md).

**Understøttet platform** – Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Funktioner**:

- Bloker data, der skal skrives til flytbare drev, der ikke er BitLocker-beskyttede.
- Bloker adgang til flytbare drev, medmindre de er krypteret på en computer, der ejes af organisationen

**Beskrivelse** – Du kan finde flere Windows oplysninger under [BitLocker - Flytbart drev Indstillinger](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Understøttet platform** – Windows 10, Windows 11

## <a name="device-properties"></a>Enhedsegenskaber

Microsoft Defender for Endpoint Device Control Removable Storage Protection giver dig mulighed for at begrænse den flytbare lageradgang ud fra de egenskaber, der er beskrevet i nedenstående tabel:

<br/><br/>

|Egenskabsnavn|Gældende politikker|Gælder for operativsystemer|Beskrivelse|
|---|---|---|---|
|Enhedsklasse|[Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt](control-usb-devices-using-intune.md)|Windows|Du kan finde oplysninger om Enheds-id-formater under [Klasse til konfiguration af enhed](/windows-hardware/drivers/install/overview-of-device-setup-classes). Følgende to links indeholder en komplet liste over klasser til konfiguration af enheder. Klasserne "Systembrug" henviser mest til enheder, der leveres med en computer/computer fra [fabriksklassen](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors), mens klasserne "Leverandør" primært refererer til enheder, der kan være forbundet til en eksisterende computer/computer: Klasser til konfiguration af systemdefinerede enheder, der er tilgængelige for leverandører – Windows-drivere og systemdefinerede klasser for enhedskonfiguration reserveret til [systembrug – Windows-drivere](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Bemærk**! Enhedsinstallation kan anvendes på alle enheder, ikke kun Flytbart lager.|
|Primært id|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md)|Windows|Det primære id omfatter flytbart lager og cd/dvd og Windows Portable Device/WPD.|
|Enheds-id|[Flytbare lager Access Control](device-control-removable-storage-access-control.md); <p> [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt](control-usb-devices-using-intune.md)|Windows|Du kan finde oplysninger om enheds-id-formater under [Standard USB-id'er](/windows-hardware/drivers/install/standard-usb-identifiers), f.eks. USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|Hardware-id|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md) <p> [Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt](control-usb-devices-using-intune.md)|Windows|En streng identificeret enheden i systemet, f.eks. USBSTOR\DiskGeneric_Flash_Disk___8.07; **Bemærk**! Hardware-id er ikke entydigt. forskellige enheder kan have den samme værdi.|
|Forekomst-id|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md) <p> Installation af enhed|Windows|En streng identificerer enheden i systemet, f.eks. USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Brugervenligt navn|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md)|Windows|En streng, der er knyttet til enheden, f.eks. Generic Flash Disk USB-enhed|
|Leverandør-id/produkt-id|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md)|Windows <p> macOS|Leverandør-id er den firecifrede leverandørkode, som USB-udvalget tildeler til leverandøren. Produkt-id er den firecifrede produktkode, som leverandøren tildeler enheden. Understøttelse af jokertegn.|
|Serienummer-id|[Adgangskontrol til flytbart lager](device-control-removable-storage-access-control.md)|Windows <p> macOS |For eksempel <SerialNumberId>002324B534BCB431B000058A</SerialNumberId>|
