---
title: Udrul, administrer og rapportér på Microsoft Defender Antivirus
description: Du kan udrulle og administrere Microsoft Defender Antivirus med Intune, Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell eller WMI
keywords: installere, administrere, opdatere, beskytte Microsoft Defender Antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 049c7a772c4c8dcf986efd310e4613423f33dcc9
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419126"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Udrul, administrer og rapportér på Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus 

**Platforme**
- Windows

Du kan udrulle, administrere og rapportere på Microsoft Defender Antivirus på flere måder.

Da Microsoft Defender Antivirus-klienten er installeret som en kernedel af Windows 10 og Windows 11, gælder traditionel udrulning af en klient til dine slutpunkter ikke.

I de fleste tilfælde skal du dog stadig aktivere beskyttelsestjeneste på dine slutpunkter med Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender for Cloud eller Gruppepolitik Objekter, som er beskrevet i følgende tabel.

Du kan også se yderligere links til:

- Administration af Microsoft Defender Antivirus beskyttelse, herunder administration af opdateringer af produkter og beskyttelse
- Rapportering om Microsoft Defender Antivirus beskyttelse

> [!IMPORTANT]
> I de fleste tilfælde deaktiverer Windows 10 eller Windows 11 Microsoft Defender Antivirus, hvis det finder et andet antivirusprogram, der kører og er opdateret. Du skal deaktivere eller fjerne antivirusprogrammer fra tredjepart, før Microsoft Defender Antivirus fungerer. Hvis du genaktiverer eller installerer antivirusprogrammer fra tredjepart, deaktiverer Windows 10 eller Windows 11 automatisk Microsoft Defender Antivirus.

Værktøj|Installationsindstillinger (<a href="#fn2" id="ref2">2</a>)|Administrationsindstillinger (konfiguration og politik for hele netværket eller grundlæggende installation) ([3](#fn3))|Rapporteringsindstillinger
---|---|---|---
Microsoft Intune|[Tilføj beskyttelsesindstillinger for slutpunkter i Intune](/intune/endpoint-protection-configure)|[Konfigurer indstillinger for enhedsbegrænsning i Intune](/intune/device-restrictions-configure)| [Brug Intune konsollen til at administrere enheder](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Brug systemrollen [Endpoint Protection punktwebsted][] og [aktivér Endpoint Protection med brugerdefinerede klientindstillinger][]|Med [standard- og brugerdefinerede antimalwarepolitikker][] og [klientadministration][]|Med standarden [Configuration Manager Overvågning af arbejdsområde][] og [mailbeskeder][]
Gruppepolitik og Active Directory (domænetilsluttet)|Brug et Gruppepolitik objekt til at installere konfigurationsændringer og sikre, at Microsoft Defender Antivirus er aktiveret.|Brug Gruppepolitik objekter til [Konfigurer opdateringsindstillinger for Microsoft Defender Antivirus][] og [Konfigurer Windows Defender funktioner][]|Slutpunktsrapportering er ikke tilgængelig med Gruppepolitik. Du kan oprette en liste over [Gruppepolitikker for at bestemme, om der ikke anvendes nogen indstillinger eller politikker][]
PowerShell|Udrul med Gruppepolitik, Microsoft Endpoint Configuration Manager eller manuelt på individuelle slutpunkter.|Brug de [Set-MpPreference] og [Update-MpSignature]-cmdlet'er, der er tilgængelige i Defender-modulet.|Brug de relevante [Get-cmdlet'er, der er tilgængelige i Defender-modulet][]
Windows forvaltningsinstrumentering|Udrul med Gruppepolitik, Microsoft Endpoint Configuration Manager eller manuelt på individuelle slutpunkter.|Brug metoden [Set for MSFT_MpPreference class][] og metoden [Update for MSFT_MpSignature class][]|Brug klassen [MSFT_MpComputerStatus][] og metoden get for tilknyttede klasser i [Windows Defender WMIv2 Provider][]
Microsoft Azure|Udrul Microsoft Antimalware til Azure i [Azure Portal ved hjælp af Visual Studio konfiguration af virtuelle maskiner eller ved hjælp af Azure PowerShell cmdlet'er](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Du kan også [installere Endpoint Protection i Microsoft Defender for Cloud*](/azure/security-center/security-center-install-endpoint-protection)|Konfigurer [Microsoft Antimalware til Virtual Machines og Cloud Services med Azure PowerShell cmdlet'er](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets), eller [brug kodeeksempler](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Brug [Microsoft Antimalware til Virtual Machines og Cloud Services med Azure PowerShell-cmdlet'er](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) for at aktivere overvågning. Du kan også gennemse forbrugsrapporter i Azure Active Directory for at finde mistænkelig aktivitet, herunder rapporten [Muligvis inficerede enheder][], og konfigurere et SIEM-værktøj til at rapportere om [Microsoft Defender Antivirus hændelser][] og tilføje værktøjet som en app i AAD.

1. <span id="fn1" />Tilgængeligheden af nogle funktioner og funktioner, især relateret til skybaseret beskyttelse, varierer mellem Microsoft Endpoint Manager (Current Branch) og System Center 2012 Configuration Manager. I dette bibliotek har vi fokuseret på Windows 10, Windows 11, Windows Server 2016 og Microsoft Endpoint Manager (Aktuel forgrening). Se [Brug microsoft cloudbaseret beskyttelse i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md) for at få en tabel, der beskriver de største forskelle. [(Vend tilbage til tabel)](#ref2)

2. <span id="fn2" />I Windows 10 og Windows 11 er Microsoft Defender Antivirus en komponent, der er tilgængelig uden installation eller installation af en ekstra klient eller tjeneste. Den aktiveres automatisk, når antivirusprodukter fra tredjepart enten fjernes eller er forældede (undtagen på Windows Server 2016). Traditionel udrulning er derfor ikke påkrævet. Udrulning her refererer til at sikre, at den Microsoft Defender Antivirus komponent er tilgængelig og aktiveret på slutpunkter eller servere. [(Vend tilbage til tabel)](#ref2)

3. <span id="fn3" />Konfiguration af funktioner og beskyttelse, herunder konfiguration af opdateringer til produkter og beskyttelse, er yderligere beskrevet i afsnittet [Konfigurer Microsoft Defender Antivirus funktioner](configure-notifications-microsoft-defender-antivirus.md) i dette bibliotek. [(Vend tilbage til tabel)](#ref2)

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
---|---
[Udrul og aktivér Microsoft Defender Antivirus beskyttelse](deploy-microsoft-defender-antivirus.md) | Selvom klienten er installeret som en kernedel af Windows 10 eller Windows 11, og den traditionelle installation ikke gælder, skal du stadig aktivere klienten på dine slutpunkter med Microsoft Endpoint Configuration Manager, Microsoft Intune eller Gruppepolitik Objekter.
[Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](manage-updates-baselines-microsoft-defender-antivirus.md) | Der er to dele til opdatering af Microsoft Defender Antivirus: opdatering af klienten på slutpunkter (produktopdateringer) og opdatering af Sikkerhedsintelligens (beskyttelsesopdateringer). Du kan opdatere Security Intelligence på flere måder ved hjælp af Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell og WMI.
[Overvåg og rapportér om Microsoft Defender Antivirus beskyttelse](report-monitor-microsoft-defender-antivirus.md) | Du kan bruge Microsoft Intune, Microsoft Endpoint Configuration Manager, tilføjelsesprogrammet Opdateringsoverholdelse til Microsoft Operations Management Suite eller et SIEM-tredjepartsprodukt (ved at bruge Windows hændelseslogge) til at overvåge beskyttelsesstatus og oprette rapporter om beskyttelse af slutpunkter.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
    
