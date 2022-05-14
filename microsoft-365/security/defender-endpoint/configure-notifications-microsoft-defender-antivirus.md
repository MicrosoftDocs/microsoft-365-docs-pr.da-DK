---
title: Konfigurer meddelelser om Microsoft Defender Antivirus
description: Få mere at vide om, hvordan du konfigurerer og tilpasser både standard- og andre Microsoft Defender Antivirus-meddelelser på slutpunkter.
keywords: meddelelser, defender, antivirus, slutpunkt, administration, administrator
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 6c9dfd603a128de4a94c9cf49faa6ba9ca940d9b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418176"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Konfigurer Microsoft Defender Antivirus meddelelser, der vises på slutpunkter

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

I Windows 10 og Windows 11 er programmeddelelser om registrering og afhjælpning af malware mere robuste, konsistente og præcise. Microsoft Defender Antivirus meddelelser vises på slutpunkter, når scanningerne er fuldført, og der registreres trusler. Meddelelser følger både planlagte og manuelt udløste scanninger. Disse meddelelser vises også i **Meddelelsescenter**, og der vises en oversigt over scanninger og trusselsregistreringer med jævne tidsintervaller.

Hvis du er en del af organisationens sikkerhedsteam, kan du konfigurere, hvordan meddelelser vises på slutpunkter, f.eks. meddelelser, der beder om en genstart af systemet, eller som angiver, at der er registreret og afhjælpet en trussel.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Konfigurer antivirusmeddelelser ved hjælp af Gruppepolitik eller Windows Sikkerhed-appen

Du kan konfigurere visningen af yderligere meddelelser, f.eks. de seneste oversigter over trusselsregistrering, i [appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md) og med Gruppepolitik.

> [!NOTE]
> I Windows 10 version 1607 blev funktionen kaldt **Udvidede meddelelser** og blev konfigureret under **Windows Indstillinger** \> **opdatering & sikkerheds Windows Defender**\>. I Gruppepolitik indstillinger for alle versioner af Windows 10 og Windows 11 kaldes meddelelsesfunktionen **Udvidede meddelelser**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Brug Gruppepolitik til at deaktivere yderligere meddelelser

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

4. Vælg **Administrative skabeloner**.

5. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** >  **Rapportering**.

6. Dobbeltklik på **Slå udvidede meddelelser fra**, og angiv indstillingen til **Aktiveret**. Vælg derefter **OK**. Dette forhindrer, at yderligere meddelelser vises.

> [!IMPORTANT]
> Deaktivering af yderligere meddelelser deaktiverer ikke kritiske meddelelser, f.eks. trusselsregistrering og afhjælpningsbeskeder.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Brug appen Windows Sikkerhed til at deaktivere yderligere meddelelser

1. Åbn appen Windows Sikkerhed ved at klikke på skjoldikonet på proceslinjen eller ved at søge i menuen Start for **Sikkerhed**.

2. Vælg Feltet **Virus & threat protection** (eller skjoldikonet på menulinjen til venstre), og vælg derefter **Indstillinger for virus & trusselsbeskyttelse**

3. Rul til sektionen **Meddelelser,** og vælg **Skift meddelelsesindstillinger**.

4. Skub kontakten til **Fra** eller **Til** for at deaktivere eller aktivere yderligere meddelelser.

> [!IMPORTANT]
> Deaktivering af yderligere meddelelser deaktiverer ikke kritiske meddelelser, f.eks. trusselsregistrering og afhjælpningsbeskeder.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Konfigurer standardmeddelelser på slutpunkter ved hjælp af Gruppepolitik

Du kan bruge Gruppepolitik til at:

- Vis yderligere brugerdefineret tekst på slutpunkter, når brugeren skal udføre en handling
- Skjul alle meddelelser på slutpunkter
- Skjul genstartsmeddelelser på slutpunkter

Det kan være nyttigt at skjule meddelelser i situationer, hvor du ikke kan skjule hele grænsefladen Microsoft Defender Antivirus. Se [Undgå, at brugerne får vist eller interagerer med den Microsoft Defender Antivirus brugergrænseflade](prevent-end-user-interaction-microsoft-defender-antivirus.md) for at få flere oplysninger. Skjulning af meddelelser sker kun på slutpunkter, som politikken er blevet installeret på. Meddelelser, der er relateret til handlinger, der skal udføres (f.eks. en genstart), vises stadig på [Microsoft Endpoint Manager Endpoint Protection overvågningsdashboard og -rapporter](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Hvis du vil føje brugerdefinerede kontaktoplysninger til meddelelser om slutpunkter, skal du se [Tilpas appen Windows Sikkerhed for din organisation](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Brug Gruppepolitik til at skjule meddelelser

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **Gruppepolitik Administrationseditor** skal du gå til **Computerkonfiguration** og derefter vælge **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **klientgrænsefladen**. 

5. Dobbeltklik på **Skjul alle meddelelser** , og angiv indstillingen til **Aktiveret**. 

6. Vælg **OK**. Dette forhindrer, at yderligere meddelelser vises.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Brug Gruppepolitik til at skjule meddelelser om genstart

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

2. Gå til **Computerkonfiguration** i **administrationseditoren Gruppepolitik**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **klientgrænsefladen**.

5. Dobbeltklik på **Undertrykker meddelelser om genstart** og angiver indstillingen til **Aktiveret**. 

5. Vælg **OK**. Dette forhindrer, at yderligere meddelelser vises.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)